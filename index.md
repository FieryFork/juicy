<head><link rel="stylesheet" href="juicy/assets/css/style.css"></head>
This is a website dedicated to documenting the juiciness of different pens.<br>
<hr>
**1 = Not juicy at all**<br>
**10 = The juiciest pen ever**
<br>
<br>
<table id="penTable">
  <thead>
    <tr>
      <th onclick="sortTable(0)">Name of Pen ↕</th>
      <th onclick="sortTable(1)">Juiciness (1-10) ↕</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Papermate Inkjoy Gel Pen</td>
      <td>9</td>
    </tr>
    <tr>
      <td>Pilot G2 05</td>
      <td>4</td>
    </tr>
    <tr>
      <td>Pilot G2 07</td>
      <td>8</td>
    </tr>
    <tr>
      <td>Kaweco Sport Fountain Pen</td>
      <td>5</td>
    </tr>
    <tr>
      <td>Papermate Flair Felt Tip Pen</td>
      <td>6</td>
    </tr>
    <tr>
      <td>BIC Round Stic M</td>
      <td>6</td>
    </tr>
    <tr>
      <td>FriXon 07 Ball Clicker Erasable</td>
      <td>5</td>
    </tr>
    <tr>
      <td>BIC Gelocity 07</td>
      <td>9</td>
    </tr>
    <tr>
      <td>Zebra Z-Grip Medium</td>
      <td>4</td>
    </tr>
    <tr>
      <td>Vience GP6464 05</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Pigma Micron 08 Archival Ink 05</td>
      <td>9</td>
    </tr>
    <tr>
      <td>Sharpie Permanent Marker Ultra Fine Point</td>
      <td>4</td>
    </tr>
  </tbody>
</table>

<script>
function sortTable(colIndex) {
  const table = document.getElementById("penTable");
  const tbody = table.tBodies[0];
  const rows = Array.from(tbody.rows);
  

  let direction = table.getAttribute("data-sort-dir") === "asc" ? "desc" : "asc";
  if (table.getAttribute("data-sort-col") !== colIndex.toString()) {
    direction = "asc";
  }
  
  rows.sort((a, b) => {
    let valA = a.cells[colIndex].textContent.trim();
    let valB = b.cells[colIndex].textContent.trim();
    
    const numA = parseFloat(valA);
    const numB = parseFloat(valB);
    if (!isNaN(numA) && !isNaN(numB)) {
      return direction === "asc" ? numA - numB : numB - numA;
    }
    
    return direction === "asc" 
      ? valA.localeCompare(valB) 
      : valB.localeCompare(valA);
  });
  rows.forEach(row => tbody.appendChild(row));
  
  // Save current sorting state
  table.setAttribute("data-sort-col", colIndex);
  table.setAttribute("data-sort-dir", direction);
}
</script>
