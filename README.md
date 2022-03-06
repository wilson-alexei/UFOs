# UFOs
Building a table using data stored in a JavaScript array and creating filters to make this table fully dynamic and then place the table into an HTML file for easy viewing

## Overview 
Dana’s webpage and dynamic table are working as intended, but she’d like to provide a more in-depth analysis of UFO sightings by allowing users to filter for multiple criteria at the same time. In addition to the date, you’ll add table filters for the city, state, country, and shape. With this addition, it will enhance our webpage so that we can filter UFO sightings on multiple criterias to display the needed results from the datasets. We will be utilizing `HTML` and `JavaScript` through `Visual Studio Code` and working with JSON datasets. 

## Results
**Here is the Code for adding more  filter criterias:**
`````
// from data.js
const tableData = data;

// get table references
var tbody = d3.select("tbody");

function buildTable(data) {
  // First, clear out any existing data
  tbody.html("");

  // Next, loop through each object in the data
  // and append a row and cells for each value in the row
  data.forEach((dataRow) => {
    // Append a row to the table body
    let row = tbody.append("tr");

    // Loop through each field in the dataRow and add
    // each value as a table cell (td)
    Object.values(dataRow).forEach((val) => {
      let cell = row.append("td");
      cell.text(val);
    });
  });
}

// 1. Create a variable to keep track of all the filters as an object.
var clearEntries = d3.select("#clear-btn");
clearEntries.on("click", function() {
  location.reload();
});

var filters = {
  };

// 3. Use this function to update the filters. 
function updateFilters() {

    // 4a. Save the element that was changed as a variable.
  let inputElement = d3.select(this)
    // 4b. Save the value that was changed as a variable.
  let inputValue = inputElement.property("value");
    // 4c. Save the id of the filter that was changed as a variable.
  let inputID = inputElement.attr("id");
  
    // 5. If a filter value was entered then add that filterId and value
    // to the filters list. Otherwise, clear that filter from the filters object.
    if (inputValue) {
      filters[inputID] = inputValue;
    } else{filters ={};};
  
    // 6. Call function to apply all filters and rebuild the table
  filterTable(filters);
  
};
  
  // 7. Use this function to filter the table when data is entered.
function filterTable(obj) {
  
    // 8. Set the filtered data to the tableData.
    let filteredData = tableData;
  
    // 9. Loop through all of the filters and keep any data that
    // matches the filter values
    Object.entries(obj).forEach(([fkey, fval]) =>{

      filteredData = filteredData.filter((row) => row[fkey] === fval)
    });
  
    // 10. Finally, rebuild the table using the filtered data
    buildTable(filteredData);
  };
  
  // 2. Attach an event to listen for changes to each filter
  d3.selectAll("input").on("change", updateFilters);
  
  // Build the table when the page loads
  buildTable(tableData);
  `````
  
The above codes will produce this webpage (with newly added filters): 
<img width="1440" alt="UFO Webs" src="https://user-images.githubusercontent.com/95068439/156906232-197b1902-0e7f-45de-a627-514abec882ea.png">

* Here is the Extra Filter Criterias: 
<img width="1440" alt="New Filter Table" src="https://user-images.githubusercontent.com/95068439/156906275-cd72792b-0a3e-45b2-bcae-da2540662388.png">

Here are the directions on how to perform a search: 
> Filter the City: Click the Input Area under *"Enter City"* and for this example we will filter the city of Fairfield in the state of California and the click the *Filter Table* right below the **Filter Search** 
<img width="1426" alt="City Filter" src="https://user-images.githubusercontent.com/95068439/156906517-6cef12f0-3e62-48f7-8706-c0578e27ef54.png">

> Then, it will filter for the city of Fairfield and will display the result/data
<img width="1362" alt="Screen Shot 2022-03-05 at 21 29 29" src="https://user-images.githubusercontent.com/95068439/156906624-2fe05a43-e721-4e03-b804-78020c571630.png">

> If you change your mind and want to filter a different criteria, you can click the *Clear Table* and it will return to display the Default dataset
<img width="376" alt="Clear Table" src="https://user-images.githubusercontent.com/95068439/156906731-09920cd2-d1bd-4f50-a5a5-3b3e74bfce7f.png">

> Here is the Default dataset and you can filter out whatever criterias that are in your mind: 
<img width="1440" alt="Back to Default" src="https://user-images.githubusercontent.com/95068439/156906857-c6ef6532-a57f-4648-9bf0-ebacdf1d8313.png">

## Summary 
* One drawback that this new design encounter is that the information and datasets is publicly exposed so we need to compile them into one place such as a GitHub pages where we can create a site to share a static content. 
* Two additional recommendations for further development: 
  1. Create a GitHub Pages where we can create a website for the projects from our repository to make live updates and changes
  2. 





`LinkedIn: /www.linkedin.com/in/wilson-alexei/`

`Email: wils.alexei@gmail.com`


 
 
 
 
