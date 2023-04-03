<head>
<meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <script src="https://kit.fontawesome.com/b33dd8950a.js" crossorigin="anonymous"></script>
  <title>Editor</title>
  <style type="text/css" media="screen">

	::-webkit-scrollbar {
	width: 8px;
	}

	/* Track */
	::-webkit-scrollbar-track {
	background: #141414;
	}
	
	/* Handle */
	::-webkit-scrollbar-thumb {
	background: #232323; 
	border-radius: 4px;
	}

	/* Handle on hover */
	::-webkit-scrollbar-thumb:hover {
	background: #323232; 
	}

    #editor {
        margin: 0;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
		width: 80vw; 
		height: 500px;
		font-size: 14px;
		border-radius: 10px;
		resize: vertical;
		overflow-x: auto;
    }

	#outputBox {
		margin: 0;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		width: 80vw;
		text-align: left;
		font-size: 16px;
		border-radius: 10px;
	}

	button {
		background-color: white; 
		border: none;
		color: black;
		padding: 15px 32px;
		width: 80%;
		text-align: center;
		text-decoration: none;
		display: inline-block;
		font-size: 16px;
		margin: 4px 2px;
		border-radius: 10px;
		cursor: pointer;
		transition: all 0.2s ease-in-out;
	}

	button:hover {
		background-color: #808080;
		color: white;
		transform: translateY(-2px);
	}

	h1 {
		text-align: center;
	}

	select {
		width: 80%;
		padding: 16px 20px;
		margin: 16px;
		border: none;
		border-radius: 4px;
		background-color: #232323;
		color: white;
	}
  </style>
</head>

<h1> Code Editor </h1>

<form>
	<center>
	<select id="preset-select">
		<option value="">Select a preset</option>
		<option value="frq-1">FRQ 1</option>
		<option value="hello-world">Hello World</option>
	</select>
	<div id="editor">public class Main {
	public static void main(String[] args) {
		System.out.println("Hello World!");
	}
}</div>
    <!-- <textarea id="code" style="width: 500px; height: 500px;"></textarea> -->
    <br/>
    <button id="runButton" type="button">Run Code</button>
    </center>
</form>
<br/>
<center>
<pre id="outputBox">Code Output Here</pre>
</center>

<!-- https://github.com/ajaxorg/ace-builds/blob/master/src-noconflict/ace.js -->
<script src="https://cdn.jsdelivr.net/npm/ace-builds@1.4.13/src-min/ace.js"></script>
<script>
    var editor = ace.edit("editor");
    editor.setTheme("ace/theme/twilight");
    editor.session.setMode("ace/mode/java");
</script>

<script>
  const select = document.getElementById('preset-select');
  document.getElementById('editor').addEventListener("mouseup", function() {
	resizableElement.style.height = resizableElement.clientHeight + "px";
	});

  select.addEventListener('change', function() {
    // Get the selected option value
    const selectedPreset = select.value;

    // Update the editor content based on the selected preset
    if (selectedPreset === 'frq-1') {
      editor.setValue(`public class Main {  

	// Distance in inches from the starting position to the goal.
	private int goalDistance;

	// Maximum number of hops allowed to reach the goal.
	private int maxHops;

	public Main(int dist, int numHops) {
		goalDistance = dist;
		maxHops = numHops;
	}

	// Returns an integer representing the distance, in inches, to be moved when the frog hops.
	private int hopDistance() {
		/* Implementation not shown */
	}

	// Simulates a frog attempting to reach the goal as described in part (a).
	// Returns true if the frog successfully reached or passed the goal during the simulation;
	// false otherwise.
	public boolean simulate() {
		/* to be implemented in part (a) */
	}

	// Runs num simulations and returns the proportion of simulations in which the frog
	// successfully reached or passed the goal.
	public double runSimulations(int num) {
		/* to be implemented in part (b) */
	}

	public static void main(String[] args) {
		Main sim = new Main(24, 5);
	}
}`);
    } else if (selectedPreset === 'hello-world') {
      editor.setValue(`public class Main {  
	public static void main(String[] args) {
		System.out.println("Hello World!");
	}
}`)
    } else {
      // If no preset is selected, reset the editor content
      editor.textContent = 'public class Main {\n  public static void main(String[] args) {\n    System.out.println("Hello World!");\n  }\n}';
    }
  });
</script>


<script>

	const button = document.querySelector('#runButton');
	const outputBox = document.getElementById("outputBox");

	function runCode() {
		const API_URL = 'https://judge0-ce.p.rapidapi.com/';
		var code = editor.getValue();

		button.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Running Code...';
		button.disabled = true;

		const headers = {
			'content-type': 'application/json',
			'x-rapidapi-key': 'cd81236483mshbc05c3041f1ca4cp1cfad3jsnb28e0b499ace',
			'x-rapidapi-host': 'judge0-ce.p.rapidapi.com',
		};

		const data = {
			source_code: code,
			language_id: 62, // Java language ID
			stdin: '',
		};

		fetch(API_URL + 'submissions', {
			method: 'POST',
			headers: headers,
			body: JSON.stringify(data),
		})
			.then((response) => response.json())
			.then((data) => {
				const submissionId = data.token;
				// Poll for submission status until it's completed
				let interval = setInterval(() => {
					fetch(API_URL + `submissions/${submissionId}?base64_encoded=true`, {
						headers: headers,
					})
						.then((response) => response.json())
						.then((data) => {
							if (data.status.id <= 2) {
								// Status is either "queued" or "processing"
								console.log('Status: ' + data.status.description);
							} else {
								// Status is "completed"
								outputBox.style.color = 'white';
								clearInterval(interval);
								const output = atob(data.stdout);
								console.log('Output: ' + output);
								outputBox.innerHTML = output;
								button.innerHTML = 'Run Code';
								button.disabled = false;
							}
						})
						.catch((error) => {
							console.error(error);
							outputBox.style.color = 'red';
							outputBox.innerHTML = error;
							button.innerHTML = 'Run Code';
							button.disabled = false;
						});
				}, 1000);
			})
			.catch((error) => {
				console.error(error);
				outputBox.style.color = 'red';
				outputBox.innerHTML = error;
				button.innerHTML = 'Submit';
				button.disabled = false;
			});
	}

	button.addEventListener('click', runCode);
</script>

