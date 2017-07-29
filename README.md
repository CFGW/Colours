## Colours
Type colour values into the input fields to have that colour displayed as the background. HTML, CSS, and a little Jquery - super simple.

Hexidecimal and RGBA only for the moment (plus, transparency tiles background for alpha reference).

[Click here to view a live demo](https://cfgw.github.io/colours "Colours by cfgw")

#### index.html:
```HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" type="text/css" href="styles.css">
    <link href="https://fonts.googleapis.com/css?family=Montserrat|Quicksand:700" rel="stylesheet">
    <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>

    <title>colours</title>

  </head>
<body>
<div class="wrap">
<div class="conatiner">
  <div class="panel">

  <input type="text" class="inputs" placeholder="hexidecimal" id="activate-hex" maxlength="6" />
  <input type="text" class="inputs" placeholder="rgba()" id="activate-rgb" maxlength="20" />
  <h2> Colours. </h2>
   <p class="test">er</p>
  </div>
</div>
</div>

<script src="scripts.js">
</script>
  </body>
</html>
```

#### styles.css:
```CSS
@keyframes ready {
  0% {
    width:0;
    min-width:0;
  }
  50% {
    width:0;
    min-width:0;
  }
  100% {
    width: 30vw;
    min-width: 200px;
  }
}
@keyframes current {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

body {
background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAAH0lEQVQYlWN49OjRf3T8798/DMwwFBRiE8SmeSgoBAAG23zs7FIe+AAAAABJRU5ErkJggg==) repeat;

}
.wrap {
width: 100%;
height: 100%;
top: 0;
left: 0;
position: absolute;
background: rgba(255,255,255,0);
z-index: 1;
animation: current 300ms cubic-bezier(1,0,1,1);
}
h2 {
margin-top: 20px;
margin-bottom: 0;
display: block;
margin-left: auto;
margin-right: auto;
width: 30vw;
min-width: 200px;
color: rgba(0,0,0,1);
mix-blend-mode: overlay;
font-family: 'Quicksand', sans-serif;
font-size: 2.4em;
animation: ready 850ms cubic-bezier(.6,.01,.55,1);
overflow: hidden;
}
p {
margin-top: 0;
padding-left: 10px;
display: block;
margin-left: auto;
margin-right: auto;
width: 30vw;
min-width: 200px;
color: rgba(0,0,0,.8);
mix-blend-mode: overlay;
font-family: 'Quicksand', sans-serif;
font-size: 1em;
animation: current 1200ms cubic-bezier(.6,.01,.55,1);
overflow: hidden;
}
.container {
width: 100%;
height: 100%;
text-align: center;
}
.inputs {
opacity: .5;
border: none;
font-size: 24px;
display: block;
margin-top: 2vh;
margin-right: auto;
margin-left: auto;
padding-top: 6px;
padding-bottom: 6px;
padding-left: 40px;
padding-right: 40px;
text-align: center;
color: rgba(0,0,0,.8);
mix-blend-mode: hard-light;
font-family: 'Montserrat', sans-serif;
width: 30vw;
min-width: 200px;
animation: ready 650ms cubic-bezier(.6,.01,.55,1);
}
.panel {
margin-top: 40vh;
}

```

#### scripts.js
```javascript
//listen for input, and return background-color if valid
$(document).ready(function() {
  $('#activate-hex').on('keyup', function() {
    $('.wrap').css('background', '#' + $(this).val());
});
$('#activate-rgb').on('keyup', function() {
  $('.wrap').css('background', 'rgba(' + $(this).val() + ')');
});

//pull random background-color from array
var bgs = ['245,123,100,1', '255,122,01,1', '123,222,222,1',
            '20,222,111,1', '120,50,255,1', '50,100,250,1',
            '50,200,100,1' ,'24,156,200,1', '190,200,90,1', '224,156,200,1', '224,60,30,1', '255,205,210,1',
            '175,113,100,1', '242,200,10,1', '242,200,210,1',
            '32,230,180,1',  '62,130,200,1', '202,130,200,1',
            '130,120,200,1', '200,40,80,1', '180,220,10,1'
          ];
$('.wrap').css('background', 'rgba('+bgs[Math.floor(Math.random() * bgs.length)]+')');
//display background color value as a string
var currentcolor = $('.wrap').css("background-color");
$('.test').text(currentcolor);

//remove the onload rgb string when inputs are clicked
$('input').on('click', function() {
  $('.test').fadeOut('slow');
});

});

```
