## 1. prepare github repository
  1. register github account with email
  2. create a new repository
  3. create a new file: index.html using template from w3schools website
  4. goto settings and select Github Pages and enable Master branch
  5. open link in browser, add index.html if error 404

## 2. improve UI with [OnSen UI](https://onsen.io/v2/guide/#the-first-onsen-ui-app)
  1. copy code from **The First Onsen UI App** to index.html
  2. test with browser and mobile browser via [QR code](https://www.the-qrcode-generator.com/)
  3. copy top-right HTML content (24 lines) from **Making Your Web & Hybrid App Feel Native** to replace line between `<body>` and `</body>`
  4. make `<script>` and `</script>` before `</body>`
  5. copy bottom-right JavaScript code (11 lines) to fill between `<script>` and `</script>`
  6. test with browser and mobile browser

## 3. add code to read and print latitude and longitude
  1. add id to page2 content
```  
<p id="latlng">This is the second page.</p>
```
  2. add function to show location after `var page = event.target;` line
```  
function showPosition(position) {
    page.querySelector('#latlng').innerHTML = "Latitude: " + position.coords.latitude + "<br>Longitude: " + position.coords.longitude;
}
```
  3. add code to start reading and show location inside `if (page.id === 'page2') {`
```
navigator.geolocation.getCurrentPosition(showPosition);
```
  4.  test with browser and mobile browser

## 4. create Firebase database
  1. create a new [Firebase](https://firebase.google.com/) project at with Google account
  2. select Develop and create Realtime Database
  3. try to add `me: {'name':'???', 'age':??}` data into database
  4. test with browser and mobile browser to Database URL/me.json
  
## 5. add code to send data to Firebase
  1. add code to send data to Firebase after location is updated, **change ??? to your project**
```  
const Url = 'https://???.firebaseio.com/logs.json';
let Data = {
  latitude:position.coords.latitude,
  longitude:position.coords.longitude
};
const Params = {
  headers:{ 
    'Content-Type':'application/json'
  },
  body:JSON.stringify(Data),
  method:'POST'
};
console.log(JSON.stringify(Data));
fetch(Url, Params).then(data=>{return data.json();}).then(res=>{console.log(res);});
```
  2. click button and check Firebase database
