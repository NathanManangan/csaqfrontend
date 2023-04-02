<head>
<meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <title>Editor</title>
  <style type="text/css" media="screen">

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
	}

	h1 {
		text-align: center;
	}
  </style>
</head>

<h1> Code Editor </h1>

<form>
	<center>
	<div id="editor">public class Main {
	public static void main(String[] args) {
		System.out.println("Hello World!");
	}
}</div>
    <!-- <textarea id="code" style="width: 500px; height: 500px;"></textarea> -->
    <br/>
    <button type="button" onclick="runCode()">Run Code</button>
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

    document.getElementById("code").style.width = "80vw";

    function runCode() {
	const API_URL = 'https://judge0-ce.p.rapidapi.com/';
	var code = editor.getValue();

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
							clearInterval(interval);
							const output = atob(data.stdout);
							console.log('Output: ' + output);
							document.getElementById("outputBox").innerHTML = output;
						}
					})
					.catch((error) => {
						console.error(error);
					});
			}, 1000);
		})
		.catch((error) => {
			console.error(error);
		});
}
</script>

