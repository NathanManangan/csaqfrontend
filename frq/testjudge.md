<form>
  <textarea id="code"></textarea>
  <button type="button" onclick="runCode()">Run Code</button>
</form>

<script>
    function runCode() {
        var code = document.getElementById("code").value;
        
        // Set up the request data
        var request_data = {
            "source_code": code,
            "language_id": 62, // Replace with the language ID for the programming language the user is using
            "stdin": "",
            "expected_output": ""
        };
        
        // Make an HTTP POST request to the Judge0 API endpoint
        fetch("https://judge0.com/api/v5/submissions", {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(request_data)
        })
        .then(response => response.json())
        .then(data => {
            console.log(data);
            // Handle the response data
            // ...
        })
        .catch(error => console.error(error));
        }.then(data => {
            console.log(data);
            alert("Your submission ID is " + data.id);
        })


</script>

