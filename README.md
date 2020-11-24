# jsdom cheat sheet
jsdom cheat sheet with the most needed stuff..

<br>
<br>

# install
```javascript
// CJS
const jsdom = require("jsdom");
const { JSDOM } = jsdom;

// ESM
import jsdom from 'jsdom';
const { JSDOM } = jsdom;
```



<br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>

# window

## Access global variables
```javascript
const load = name => new Promise( resolve => { log( 'LOAD - name: ' + name );
    name.onload = () => resolve(true);
});

var dom = new JSDOM(`
  <!DOCTYPE html>
  <script>window.test = true</script>
`,
 { runScripts: "dangerously",
    url: link,
    resources: 'usable',
    virtualConsole
  });
  
  global.window = dom.window;
  global.document = dom.window.document;

  await load(window);
  console.log("test: " + window.test);
```


<br><br>
 _____________________________________________________
 _____________________________________________________
<br><br>


# Usage

```javascript
const dom = new JSDOM(`<!DOCTYPE html><body><p id="main">My First JSDOM!</p></body>`);
console.log(dom.window.document.getElementById("main").textContent);
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
