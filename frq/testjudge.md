<form>
  <textarea id="code"></textarea>
  <button type="button" onclick="runCode()">Run Code</button>
</form>

<script>
    function runCode() {
	const API_URL = 'https://judge0-ce.p.rapidapi.com/';
	var code = document.getElementById("code").value;

	const headers = {
		'content-type': 'application/json',
		'x-rapidapi-key': 'cd81236483mshbc05c3041f1ca4cp1cfad3jsnb28e0b499ace',
		'x-rapidapi-host': 'judge0-ce.p.rapidapi.com',
	};

	const data = {
		source_code: `public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}`,
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

