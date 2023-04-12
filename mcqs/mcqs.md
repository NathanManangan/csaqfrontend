# List Of MC Questions

<body>
</body>

<script>
    url = "http://localhost:8085/api/mcq/get/";

    // set options for cross origin header request
    const options = {
        method: 'GET', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'include', // include, *same-origin, omit
        headers: {
            'Content-Type': 'application/json',
        },
    };
    const optionsPOST = {
        method: 'POST', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'include', // include, *same-origin, omit
        headers: {
            'Content-Type': 'application/json',
        },
    };

    function getAllObjects() {
    // fetch the API
        fetch(url, options)
        // response is a RESTful "promise" on any successful fetch
        .then(response => {
            // check for response errors and display
            if (response.status !== 200) {
                const errorMsg = 'Database response error: ' + response.status;
                console.log(errorMsg);
                const tr = document.createElement("tr");
                const td = document.createElement("td");
                td.innerHTML = errorMsg;
                tr.appendChild(td);
                cardholder.appendChild(tr);
                return;
            }
            // valid response will contain json data
            response.json().then(data => {
                console.log(data);

                //remove existing cardholder
                while(cardholder.firstChild) {
                    cardholder.removeChild(cardholder.firstChild);
                }

                for (const row of data) {
                    // create card and give classlist, add to cardholder
                    const card = document.createElement("div");
                    card.classList.add("objectcard");
                    cardholder.appendChild(card);

                    // create elements for card
                    const h3 = document.createElement("h3");
                    h3.innerHTML = "Object #" + row.id;
                    const breakElement = document.createElement("br");

                    card.appendChild(h3);
                    card.appendChild(breakElement);
                    card.appendChild(breakElement);
  
                    const buttonholder = document.createElement("div");
                    buttonholder.style.whiteSpace = "nowrap";

                    // create button and give classlist, add to card
                    const button = document.createElement("button");
                    button.addEventListener("click", function() {
                        selectObj(row.id);
                    });
                    card.appendChild(button);

                    // add deletebutton and give classlist
                    const deletebutton = document.createElement("button");
                    deletebutton.addEventListener("click", function() {
                        deleteObj(row.id);
                    });
                    card.appendChild(deletebutton);

                    const updatebutton = document.createElement("button");
                    updatebutton.addEventListener("click", function() {
                        updateObj(row.id);
                    });
                    card.appendChild(updatebutton);
                }

                storedinfo = data;
            });
        })
    }
</script>