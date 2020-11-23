# jsdom cheat sheet
jsdom cheat sheet with the most needed stuff..

<br>
<br>

# Usage
```javascript
// CJS
const jsdom = require("jsdom");
const { JSDOM } = jsdom;

// ESM
import jsdom from 'jsdom';
const { JSDOM } = jsdom;
```


<br>
<br>

 _____________________________________________________
 _____________________________________________________
 

<br>
<br>


# virtualConsole

## share logs with main script
```javascript
const virtualConsole = new jsdom.VirtualConsole();
virtualConsole.sendTo(console);

dom = new JSDOM(`
  <!DOCTYPE html>
  <script>console.log("hello world");</script>`,
  { runScripts: "dangerously" },
  { virtualConsole }
);
```

<br>
<br>

 _____________________________________________________
 _____________________________________________________
 

<br>
<br>
