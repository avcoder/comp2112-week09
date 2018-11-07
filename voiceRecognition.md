# To setup voice recognition

1. Set up a webpage with the following code

```js
// set up speech detection
window.SpeechRecognition =
  window.SpeechRecognition || window.webkitSpeechRecognition;

const recognition = new SpeechRecognition();
recognition.interimResults = false;
recognition.lang = "en-US";

// global variable needed
recognition.addEventListener("result", e => {
  console.log(e);
});
recognition.addEventListener("end", recognition.start);
recognition.start();
```

1. Run it using a local server; view console; Where is the transcript data
   located?

   - Set `const transcript = ??` --what goes in here??
   - Add a `document.body.insertAdjacentHTML('beforeEnd', transcript)`

1. Try setting interimResults to true; view console

# Challenge

1. If you say 'erase all', the document.body will clear
1. If you say 'open google', the browser will open a new tab with google.ca
