# AJAX Soccer Team Widget

* in your Sites folder, create a folder called soccer-app
```
$ sites
$ mkdir soccer-app
```
* create an index.html file inside of the soccer-app folder
```
$ cd soccer-app
$ touch index.html
```
* paste the follwoing code into your index.html file
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Soccer Team Widget</title>
  <link href='http://fonts.googleapis.com/css?family=Varela+Round' rel='stylesheet' type='text/css'>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>
  <div class="grid-container centered">
    <div class="grid-100">
      <div class="contained">
        <div class="grid-100">
          <div class="heading">
            <h1>Soccer Team</h1>
          </div>
        </div>
        <section class="grid-70 main">
          <h2>Lorem Ipsum Headline</h2>
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Numquam, eius magnam aliquid doloremque quidem distinctio delectus earum natus incidunt. Molestias, ipsa ut deleniti mollitia, quibusdam alias deserunt sequi obcaecati sapiente?</p>
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quidem ad sunt ipsum quisquam vitae fugit mollitia illo tenetur, nisi impedit voluptatum vero. Cumque sunt neque consequuntur deleniti, quibusdam dolorum, nesciunt.</p>
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Officia voluptas natus nulla, dolore at libero. Aspernatur nesciunt repudiandae expedita vel, maxime reiciendis incidunt, vero officiis sit facere alias iusto deleniti?</p>
        </section>
        <aside class="grid-30 list">
          <h2>Employee Office Status</h2>
          <div id="employeeList">

          </div>
        </aside>
        <footer class="grid-100">
          <p>Copyright, The Intranet Corporation</p>
        </footer>
      </div>
    </div>
  </div>
  <script src="js/my-widget.js"></script>
</body>
</html>
```
* create css, js, and data folders inside of the soccer-app folder
```
$ mkdir css js data
```
* change into the js directory and create a my-widget.js file
```
$ cd js
$ touch my-widget.js
```
* paste the following code into my-widget.js
```html
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = function () {
    if (xhr.readyState === 4) {
      var employees = JSON.parse(xhr.responseText);
      // returns object
      //console.log(typeof employees);
      // returns an array of objects
      // console.log(employees);
    }
};
xhr.open('GET', 'data/team.json');
xhr.send();
```
* change into the data directory and create a team.json file and a fields.json file
```html
$ cd data
$ touch team.json fields.json
```
* paste the following code into team.json
```html
[
  {
    "name" : "Manny",
    "playing" : true
  },
  {
    "name" : "Moe",
    "playing" : true
  },
  {
    "name" : "Jack",
    "playing" : false
  }
]
```
* paste the following code into fields.json
```html
[
  {
   "field": "a",
   "available": false
  },
  {
   "field": "b",
   "available": true
  },
  {
   "field": "c",
   "available": false
  },
  {
   "field": "d",
   "available": false
  },
  {
   "field": "e",
   "available": true
  }
]
```
* change into the css directory and create a style.css file
```html
$ cd css
$ touch style.css
```
* paste the following code into style.css
```html
@charset "UTF-8";

.grid-container:before,
.grid-container:after {
  content: ".";
  display: block;
  overflow: hidden;
  visibility: hidden;
  font-size: 0;
  line-height: 0;
  width: 0;
  height: 0;
}

.grid-container:after {
  clear: both;
}

.grid-container {
  max-width: 1080px;
  position: relative;
}

.grid-30,
.grid-70,
.grid-100 {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  padding-left: 15px;
  padding-right: 15px;
}

body {
  min-width: 320px;
}

@media screen {
  .grid-container:before,
  .grid-container:after {
    content: ".";
    display: block;
    overflow: hidden;
    visibility: hidden;
    font-size: 0;
    line-height: 0;
    width: 0;
    height: 0;
  }

  .grid-container:after {
    clear: both;
  }

  .grid-container {
    max-width: 1080px;
    position: relative;
  }

  .grid-30,
  .grid-70,
  .grid-100 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    padding-left: 15px;
    padding-right: 15px;
  }

  body {
    min-width: 320px;
  }
}

@media screen and (min-width: 1080px) {
  .grid-container:before,
  .grid-100:before,
  .grid-container:after,
  .grid-100:after {
    content: ".";
    display: block;
    overflow: hidden;
    visibility: hidden;
    font-size: 0;
    line-height: 0;
    width: 0;
    height: 0;
  }

  .grid-container:after,
  .grid-100:after {
    clear: both;
  }

  .grid-container {
    max-width: 1080px;
    position: relative;
  }

  .grid-30,
  .grid-70,
  .grid-100 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    padding-left: 15px;
    padding-right: 15px;
  }

  .grid-30 {
    float: left;
    width: 30%;
  }

  .grid-70 {
    float: left;
    width: 70%;
  }

  .grid-100 {
    clear: both;
    width: 100%;
  }
}

@media screen and (max-width: 400px) {
  @-ms-viewport {
    width: 320px;
  }
}

@media screen and (max-width: 680px) {
  .grid-container:before,
  .grid-container:after {
    content: ".";
    display: block;
    overflow: hidden;
    visibility: hidden;
    font-size: 0;
    line-height: 0;
    width: 0;
    height: 0;
  }

  .grid-container:after {
    clear: both;
  }

  .grid-container {
    max-width: 1080px;
    position: relative;
  }

  .grid-30,
  .grid-70,
  .grid-100 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    padding-left: 15px;
    padding-right: 15px;
  }
}

@media screen and (min-width: 680px) and (max-width: 1080px) {
  .grid-container:before,
  .grid-container:after {
    content: ".";
    display: block;
    overflow: hidden;
    visibility: hidden;
    font-size: 0;
    line-height: 0;
    width: 0;
    height: 0;
  }

  .grid-container:after {
    clear: both;
  }

  .grid-container {
    max-width: 1080px;
    position: relative;
  }

  .grid-30,
  .grid-70,
  .grid-100 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    padding-left: 15px;
    padding-right: 15px;
  }
}

.grid-container:before,
.grid-container:after {
  content: ".";
  display: block;
  overflow: hidden;
  visibility: hidden;
  font-size: 0;
  line-height: 0;
  width: 0;
  height: 0;
}

.grid-container:after {
  clear: both;
}

.grid-container {
  max-width: 1080px;
  position: relative;
}

.grid-30,
.grid-70,
.grid-100 {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  padding-left: 15px;
  padding-right: 15px;
}

html,
body,
div,
h1,
h2,
p,
ul,
li,
aside,
footer,
section {
  margin: 0;
  padding: 0;
  border: 0;
  font: inherit;
  font-size: 100%;
  vertical-align: baseline;
}

html {
  line-height: 1;
}

ul {
  list-style: none;
}

aside,
footer,
section {
  display: block;
}

body {
  background: #edeff0;
  padding: 50px 0 0;
  font-family: "Varela Round", "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 62.5%;
}

.centered {
  margin: 0 auto;
}

.contained {
  background: white;
  padding: 30px 15px;
  margin-bottom: 30px;
  position: relative;
  overflow: hidden;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  -ms-border-radius: 5px;
  -o-border-radius: 5px;
  border-radius: 5px;
  -webkit-box-shadow: 0 1px 0 0 rgba(0, 0, 0, 0.1);
  -moz-box-shadow: 0 1px 0 0 rgba(0, 0, 0, 0.1);
  box-shadow: 0 1px 0 0 rgba(0, 0, 0, 0.1);
}

.heading {
  margin-bottom: 20px;
}

h1,
h2 {
  font-size: 2.4em;
  font-weight: 500;
  margin-bottom: 8px;
  color: #384047;
  line-height: 1.2;
}

h2 {
  font-size: 1.8em;
}

aside h2 {
  margin-bottom: 15px;
}

p {
  color: #8d9aa5;
  font-size: 1.4em;
  margin-bottom: 15px;
  line-height: 1.4;
}

ul li {
  margin: 15px 0 0;
  font-size: 1.6em;
  color: #8d9aa5;
  position: relative;
}

ul.bulleted li {
  padding-left: 40px;
}

ul.bulleted li:before {
  position: absolute;
  top: 0;
  left: 0;
  color: white;
  font-size: .5em;
  padding: 3px 2px 2px;
  border-radius: 2px;
  text-align: center;
  width: 25px;
}

ul.bulleted .in {
  color: #5A6772;
}

ul.bulleted .in:before {
  content: "IN";
  background-color: #5fcf80;
}

ul.bulleted .out {
  color: #A7B4BF;
}

ul.bulleted .out:before {
  content: "OUT";
  background-color: #ed5a5a;
}
ul.fields {
  margin-bottom: 30px;
}

ul.fields li {
  font-size: 1em;
  display: inline-block;
  width: 10%;
  padding: 3px 2px 2px;
  border-radius: 2px;
  margin: 0 3px 3px 3px;
  color: white;
    text-align: center;
}

ul.fields li.empty {
  background-color: #5fcf80;
}
ul.fields li.full {
  background-color: #ed5a5a;
}

footer p {
  color: #b2bac2;
  font-size: 1.15em;
  margin: 0;
}

```
* paste the following code in the aside
```html
<h2>Team Player List</h2>
<div id="playerList">
</div>
<h2>Field Availability</h2>
<div id="fieldList">
</div>
```
* replace our my-widget.js code with the following
```html
// pull in the players with AJAX
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = function () {
    if (xhr.readyState === 4) {
      var players = JSON.parse(xhr.responseText);
      // console.log(typeof employees);
      //console.log(employees);
      var statusHTML = '<ul class="bulleted">';
      for (var i = 0; i < players.length; i += 1) {
        if (players[i].playing === true) {
            statusHTML += '<li class="in">';
        } else {
            statusHTML += '<li class="out">';
        }
        statusHTML += players[i].name;
        statusHTML += '</li>';
      }
      statusHTML += '</ul>';
      document.getElementById('playerList').innerHTML = statusHTML;
    }
};
xhr.open('GET', 'data/team.json');
xhr.send();
// pull in the fields with AJAX
var fieldRequestXHR = new XMLHttpRequest();
fieldRequestXHR.onreadystatechange = function () {
    if (fieldRequestXHR.readyState === 4) {
      var myFields = JSON.parse(fieldRequestXHR.responseText);
      // console.log(typeof employees);
      //console.log(employees);
      var fieldStatusHTML = '<ul class="fields">';
      for (var i = 0; i < myFields.length; i += 1) {
        if (myFields[i].available === true) {
            fieldStatusHTML += '<li class="empty">';
        } else {
            fieldStatusHTML += '<li class="full">';
        }
        fieldStatusHTML += myFields[i].field;
        fieldStatusHTML += '</li>';
      }
      fieldStatusHTML += '</ul>';
      document.getElementById('fieldList').innerHTML = fieldStatusHTML;
    }
};
fieldRequestXHR.open('GET', 'data/fields.json');
fieldRequestXHR.send();

```
* refresh your browser to see the final app
