<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
   #myTable {
  margin: 0 auto;
}
* {
  box-sizing: border-box;
}
#myInput {
  background-image: url('/css/searchicon.png');
  background-position: 10px 10px;
  background-repeat: no-repeat;
  width: 100%;
  font-size: 16px;
  padding: 12px 20px 12px 40px;
  border: 1px solid #ddd;
  margin-bottom: 12px;
}
#myTable {
  border-collapse: collapse;
  width: 100%;
  border: 1px solid #ddd;
  font-size: 18px;
  margin: 0 auto; /* add this rule to center the table */
}
#myTable th, #myTable td {
  text-align: left;
  padding: 12px;
}
#myTable tr {
  border-bottom: 1px solid #ddd;
}
#myTable tr.header, #myTable tr:hover {
  background-color: #F1F1F1;
}
.button {
  background-color: #8491A3;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  font-family:Ubuntu;
  margin: 4px 2px;
  cursor: pointer;
  border-radius:5px;
}
</style>
</head>
<body>
<h2>FRQ List</h2>
<input type="text" id="input" onkeyup="searchYear()" placeholder="Search for year" title="Type in a year">
<table id="myTable">
  <tr class="header">
    <th scope="col">Year</th>
    <th scope="col">Difficulty</th>
    <th scope="col">Our Version</th>
    <th scope="col">College Board</th>
  </tr>
  <tr>
    <td>2010</td>
    <td>Easy</td>
    <td>Link</td>
    <td><a href='https://secure-media.collegeboard.org/apc/ap10_frq_computer_science_a.pdf'><button class="button">CB 2010</button></a>
  <tr>
    <td>2011</td>
    <td>Medium</td>
    <td>Link</td>
    <td><a href='https://secure-media.collegeboard.org/apc/ap11_frq_comp_sci_a.pdf'><button class="button">CB 2011</button></a>
  <tr>
    <td>2012</td>
    <td>Easy</td>
    <td>Link</td>
    <td><a href='https://secure-media.collegeboard.org/apc/ap_frq_computerscience_12.pdf'><button class="button">CB 2012</button></a>
  <tr>
    <td>2013</td>
    <td>Hard</td>
    <td>Link</td>
    <td><a href='https://secure-media.collegeboard.org/digitalServices/pdf/ap/apcentral/ap13_frq_comp_sci.pdf'><button class="button">CB 2013</button></a>
  <tr>
    <td>2014</td>
    <td>Medium</td>
    <td>Link</td>
    <td><a href='https://secure-media.collegeboard.org/digitalServices/pdf/ap/ap14_frq_computer_science_a.pdf'><button class="button">CB 2014</button></a>
  <tr>
    <td>2015</td>
    <td>Easy</td>
    <td>Link</td>
    <td><a href='https://secure-media.collegeboard.org/digitalServices/pdf/ap/ap15_frq_computer_science_a.pdf'><button class="button">CB 2015</button></a>
  <tr>
    <td>2016</td>
    <td>Medium</td>
    <td>Link</td>
    <td><a href='https://secure-media.collegeboard.org/digitalServices/pdf/ap/ap16_frq_computer_science_a.pdf'><button class="button">CB 2016</button></a>
  <tr>
    <td>2017</td>
    <td>Medium</td>
    <td>Link</td>
    <td><a href='https://apcentral.collegeboard.org/media/pdf/ap-computer-science-a-frq-2017.pdf'><button class="button">CB 2017</button></a>
  <tr>
    <td>2018</td>
    <td>Easy</td>
    <td>Link</td>
    <td><a href='https://secure-media.collegeboard.org/apc/ap18-frq-computer-science-a.pdf'><button class="button">CB 2018</button></a>
  <tr>
    <td>2019</td>
    <td>Medium</td>
    <td>Link</td>
    <td><a href='https://secure-media.collegeboard.org/apc/ap19-frq-computer-science-a.pdf'><button class="button">CB 2019</button></a>
<script>
function searchYear() {
  var input, filter, table, tr, td, i, txtValue;
  input = document.getElementById("input");
  filter = input.value.toUpperCase();
  table = document.getElementById("myTable");
  tr = table.getElementsByTagName("tr");
  for (i = 0; i < tr.length; i++) {
    td = tr[i].getElementsByTagName("td")[0];
    if (td) {
      txtValue = td.textContent || td.innerText;
      if (txtValue.toUpperCase().indexOf(filter) > -1) {
        tr[i].style.display = "";
      } else {
        tr[i].style.display = "none";
      }
    }
  }
}
</script>