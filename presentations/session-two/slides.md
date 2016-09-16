title: beerjs/lala #1
author:
  name: Conlin Durbin
  twitter: ohmfox
  url: http://conlin.xyz
style: basic.css
output: index.html
controls: false
--
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.5.1/themes/prism-tomorrow.css" />

![js](http://3.bp.blogspot.com/-PTty3CfTGnA/TpZOEjTQ_WI/AAAAAAAAAeo/KeKt_D5X2xo/s1600/js.jpg)
## beerjs/lala

--
>beerjs is about bringing together the community. there is not, and never will be, an obligation to drink at our events

--

### wat
![wat](img/wat.gif)
- - - 
* Speaker Notes: 
* what even is this? 
* beerjs is a global meetup for people interested in Javascript.
* we focus on speakers, beer, awesome companies and javascript (duh)

-- bg
![background](http://i.giphy.com/l0MYResEdNIyniuL6.gif)
# We need sponsors
## event space? buy some beer? maybe pizza?

-- bg light
![background](http://i.giphy.com/bb2KrhhHeY6Dm.gif)
# We need speakers
## talk about javascript? something awesome you made?
- - -
* Speaker Notes:
* seriously, anything you want to talk about
* talks are about 30 min and should somehow relate to JS (but how is up to you!)

--
<iframe width="560" height="315" src="https://www.youtube.com/embed/JY8eNSu6HrU" frameborder="0" allowfullscreen></iframe>

-- bg light
![kitteh](http://i.giphy.com/3o72EX5QZ9N9d51dqo.gif)
# let's make some music
- - -
*


-- code
```
var audioContext = new AudioContext();
var osc = audioContext.createOscillator();
osc.connect(audioContext.destination);
osc.frequency.value = 440;
osc.start();
setTimeout(()=> {
   osc.stop();
}, 3000);
```
- - -
* Speaker Notes:

-- code
```
var audioContext = new AudioContext();
var osc = audioContext.createOscillator();
osc.connect(audioContext.destination);
osc.frequency.value = 440;
window.addEventListener('keydown', ({key}) => {
   osc.start();
});
window.addEventListener('keyup', ({target}) => {
   osc.stop();
})
```
- - -
* Speaker Notes:

-- code
```
var audioContext = new AudioContext();
window.addEventListener('keydown', ({key}) => {
   var osc = audioContext.createOscillator();
   osc.connect(audioContext.destination);
   osc.frequency.value = 440;
   osc.start();
});
window.addEventListener('keyup', ({target}) => {
   osc.stop();
})
```
- - -
* Speaker Notes:

-- code
```
var audioContext = new AudioContext();
var oscs = {};
window.addEventListener('keydown', ({key}) => {
   var osc = audioContext.createOscillator();
   osc.connect(audioContext.destination);
   osc.frequency.value = 440;
   oscs[key] = osc;
   osc.start();
});
window.addEventListener('keyup', ({key}) => {
   oscs[key].stop();
})
```
- - -
* Speaker Notes:

-- code
```
const audioContext = new AudioContext();
const oscs = {};
const keys = {
    'a': 440,
    's': 500
};
window.addEventListener('keydown', ({key}) => {
   var osc = audioContext.createOscillator();
   osc.connect(audioContext.destination);
   osc.frequency.value = keys[key];
   oscs[key] = osc;
   osc.start();
});
window.addEventListener('keyup', ({key}) => {
   oscs[key].stop();
});
```
- - -
* Speaker Notes:

-- code
```
const audioContext = new AudioContext();
const oscs = {};
const getFreq = (power) => 440 * Math.pow(1.05946, power)
const keys = {
    'q': getFreq(0),
    'w': getFreq(2),
    'e': getFreq(3),
    'r': getFreq(5),
    't': getFreq(7),
    'y': getFreq(9),
    'u': getFreq(10),
    'i': getFreq(12),
};
window.addEventListener('keydown', ({key}) => {
   var osc = audioContext.createOscillator();
   osc.connect(audioContext.destination);
   osc.frequency.value = keys[key];
   oscs[key] = osc;
   osc.start();
});
window.addEventListener('keyup', ({key}) => {
   oscs[key].stop();
});
```

-- code
```
const audioContext = new AudioContext();
const oscs = {};
const getFreq = (power) => 440 * Math.pow(1.05946, power)
const keys = {
    'q': getFreq(0),
    'w': getFreq(2),
    'e': getFreq(3),
    'r': getFreq(5),
    't': getFreq(7),
    'y': getFreq(9),
    'u': getFreq(10),
    'i': getFreq(12),
};
window.addEventListener('keydown', ({key}) => {
   var osc = audioContext.createOscillator();
   osc.type = "square";
   osc.connect(audioContext.destination);
   osc.frequency.value = keys[key];
   oscs[key] = osc;
   osc.start();
});
window.addEventListener('keyup', ({key}) => {
   oscs[key].stop();
});
```

-- bg light
![headroom](http://i.giphy.com/ld797IzRhlZew.gif)
#thx for coming

--
<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.5.1/prism.min.js"></script>
<script> 
   document.body.classList.add("language-js");
   var snippets = document.querySelectorAll("code");
   for(let snippet of snippets) {
      var button = document.createElement("button");
      button.classList.add("snippet-button")
      button.innerHTML = "Run Snippet";
      button.addEventListener('click', function() {
         var snipRun = new Function(`${snippet.textContent}`);
         snipRun();
      });
      let snipWrap = document.createElement("div");
      snipWrap.classList.add("snippet-wrapper");

      let snipParent = snippet.parentNode;
      snipParent.parentNode.insertBefore(snipWrap, snipParent);
      snipParent.parentNode.removeChild(snipParent);
      snipWrap.appendChild(snipParent);
      snipWrap.appendChild(button);
   }
</script>
