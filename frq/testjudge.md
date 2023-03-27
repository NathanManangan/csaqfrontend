<form>
  <textarea id="code"></textarea>
  <button type="button" onclick="runCode()">Run Code</button>
</form>

<script>
    function runCode() {
        var code = document.getElementById("code").value;
        new_code = window.btoa(code);
        var encoder = new TextEncoder();
        var codeBytes = encoder.encode(code);
        var base64Code = btoa(String.fromCharCode.apply(null, codeBytes));
        console.log(base64Code);
        
        const options = {
            method: 'POST',
            headers: {
                'content-type': 'application/json',
                'Content-Type': 'application/json',
                'X-RapidAPI-Key': 'cd81236483mshbc05c3041f1ca4cp1cfad3jsnb28e0b499ace',
                'X-RapidAPI-Host': 'judge0-ce.p.rapidapi.com'
            },
            body: {
            "source_code": base64Code, // Replace with the base64 encoded source code
            "language_id": 62 // Replace with the language ID for the programming language the user is using
            }
    };

    fetch('https://judge0-ce.p.rapidapi.com/submissions?base64_encoded=true&fields=*', options)
        .then(response => response.json())
        .then(data => {
            console.log(data);
            getOutput(data.token);
        })
        .catch(err => console.error(err));
    }

    function getOutput(token) {
        const options = {
            method: 'GET',
            headers: {
                'X-RapidAPI-Key': 'cd81236483mshbc05c3041f1ca4cp1cfad3jsnb28e0b499ace',
                'X-RapidAPI-Host': 'judge0-ce.p.rapidapi.com'
            }

        };

        fetch('https://judge0-ce.p.rapidapi.com/submissions/' + token +'?base64_encoded=true&fields=*', options)
            .then(response => response.json())
            .then(response => console.log(response))
            .then(data => {
                console.log(data);
                alert("Your output is " + data.stdout);
            })
            .catch(err => console.error(err));
    }

</script>

