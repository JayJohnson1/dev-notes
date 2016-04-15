# AJAX & Bootstrap

* in your Sites folder, create a folder called ajaxstrap
* change directory into ajaxstrap
* create index.html and sidebar.html files:
```
$ touch index.html sidebar.html
```
* inside your index.html file add the following code:
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <link href='//fonts.googleapis.com/css?family=Varela+Round' rel='stylesheet' type='text/css'>
  <link rel="stylesheet" href="css/main.css">
  <title>AJAX with JavaScript</title>
  <script>
    // 1. Create an XMLHTTP Request object
    var xhr = new XMLHttpRequest();
    // 2. Create a callback function
    xhr.onreadystatechange = function () {
      if (xhr.readyState === 4) {
       document.getElementById('ajax').innerHTML = xhr.responseText; 
      }
    };
    // 3. Open a request
    xhr.open('GET', 'sidebar.html');
    // 4. Send request
    xhr.send();
    
  </script>
</head>
<body>
  <div class="grid-container centered">
    <div class="grid-100">
      <div class="contained">
        <div class="grid-100">
          <div class="heading">
            <h1>Bring on the AJAX</h1>
          </div>
          <div id="ajax">

          </div>
        </div>
      </div>
    </div>
  </div>
</body>
</html>
```
* inside your sidebar.html file add the following code:
```html
<section>
<h2>Welcome to the wonderful world of AJAX</h2>
<p>This content provided to you dynamically by the XMLHTTP Request Object</p>
</section>
```
* open Mamp and click on Open WebStart page
* go to localhost/
* click on the ajaxstrap folder
* right click to inspect an element and click on the Console tab
* open Settings and check "Log XMLHttpRequests"
* refresh your page with Console still open and you'll see "XHR finished loading" message
* replace lines 8-22 in index.html with the following to add a button that when clicked loads a function and makes the button disappear
```html
<script>
    // 1. Create an XMLHTTP Request object
    var xhr = new XMLHttpRequest();
    // 2. Create a callback function
    xhr.onreadystatechange = function () {
      if (xhr.readyState === 4) {
       document.getElementById('ajax').innerHTML = xhr.responseText; 
      }
    };
    // 3. Open a request
    xhr.open('GET', 'sidebar.html');
    // 4. Send request
    function sendAJAX() {
        xhr.send();
        document.getElementById('load').style.display = "none";
    }

  </script>
```
* add the following line under the "h1" tag on line 33 of index.html
```html
<button id="load" onclick="sendAJAX()">Load text Now</button>

```
* refresh your page to see the button, click on it to reveal the text
* go to http://getbootstrap.com/getting-started/ or copy the Bootstrap CDN below, paste the code after the main.css link in index.html
```html
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" integrity="sha384-1q8mTJOASx8j1Au+a5WDVnPi2lkFfwwEAa8hDDdjZlpLegxhjVME1fgjWPGmkzs7" crossorigin="anonymous">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap-theme.min.css" integrity="sha384-fLW2N01lMqjakBkx3l/M9EahuwpSfeNvV63J5ezn3uZzapT0u7EYsXMjQV+0En5r" crossorigin="anonymous">

<!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js" integrity="sha384-0mSbJDEHialfmuBBQP6A4Qrprq5OVfW37PRR3j5ELqxss1yVqOtnepnHVP9aJ7xS" crossorigin="anonymous"></script>
```
* refresh your page to see the beginnings of Bootstrap
* in index.html change
```html
<div class="grid-container centered">
```
to
```html
<div class="container">
```
* add this class to the button
```html
class="btn btn-primary"
```
* refresh your page to see the button styled with Bootstrap
* paste the jquery cdn below right above the bootstrap.min.js script in index.html
```html
<!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>

```

