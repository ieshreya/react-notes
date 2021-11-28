### Folder Structure:
![[Pasted image 20211128192932.png]]
---
`index.html:`
```html
<html>
   <head>
      <link rel="preconnect" href="https://fonts.googleapis.com">
      <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
      <link href="https://fonts.googleapis.com/css2?family=Inter:wght@500;600;700&display=swap" rel="stylesheet">
      <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" integrity="sha512-Fo3rlrZj/k7ujTnHg4CGR2D7kSs0v4LLanw2qksYuRlEzO+tcaEPQogQ0KaoGN26/zrn20ImR1DfuLWnOo7aBA==" crossorigin="anonymous" referrerpolicy="no-referrer" />
      <link rel="stylesheet" href="style.css">
   </head>
   <body>
      <div id="root">
      </div>
      <script src="index.pack.js"></script>
   </body>
</html>


```

`index.js`
```js

import React from "react"

import ReactDOM from "react-dom"

import App from "./App"

ReactDOM.render(<App />, document.getElementById("root"))

```

`style.css`

```css
* {

box-sizing: border-box;

}

  

body {

font-family: 'Inter', sans-serif;

}

  

.info {

display: flex;

align-items: center;

justify-content: center;

flex-direction: column;

}

  

.info > img {

width: 300px;

height: auto;

}

  

.info > h2 {

font-family: Inter;

font-size: 25px;

font-weight: 700;

}

  
  

/* Footer */

.footer > a:link {

text-decoration-style: none;

color: black;

}

```

`App.js`:
```js
import React from "react"

import Info from './components/Info.js'

import About from './components/About.js'

import Interests from './components/Interests.js'

import Footer from './components/Footer.js'

  

export default function App() {

return (

<div className="container">

<Info/>
<About/>
<Interests/>
<Footer/>
</div>

)

}
```


### COMPONENTS:

