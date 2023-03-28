<style>
    .editor {
        width: 80vw;
        height: 600px;
        background-color: black;
        border-radius: 6px;
        box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12), 0 3px 1px -2px rgba(0, 0, 0, 0.2);
        font-family: 'Source Code Pro', monospace;
        font-size: 14px;
        font-weight: 400;
        height: 340px;
        letter-spacing: normal;
        line-height: 20px;
        padding: 10px;
        tab-size: 4;
    }
    
</style>

<script type="module">
  import {CodeJar} from 'https://medv.io/codejar/codejar.js'
</script>

<form>
    <center>
    <div id="editor" class="editor"></div>
    <script>
    let jar = CodeJar(document.querySelector('.editor'), hljs.highlightElement)
    </script>
    <textarea id="code" style="width: 500px; height: 500px;"></textarea>
    <br/><br/>
    <button type="button" onclick="runCode()">Run Code</button>
    </center>
</form>

<script>

    document.getElementById("code").style.width = "80vw";

    function runCode() {
	const API_URL = 'https://judge0-ce.p.rapidapi.com/';
	var code = document.getElementById("code").value;

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

