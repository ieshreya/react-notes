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
```jsx
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

`Info.js`

```jsx
import React from 'react';

  

export default function Info(){

return (

<>

<div className="info">

<img src="https://64.media.tumblr.com/47c605a155779569f5154e624613138b/11d03c1595b7f8c7-b1/s1280x1920/31a0fdddd8c56435ec53096aaae7c7658e4502db.jpg"/>

<h2>Shreya Purohit</h2>

<h4>Front End Developer</h4>

<a href="shreyapurohit.now.sh">shreyapurohit.now.sh</a>

<div className="btns">

<button><i class="far fa-envelope"></i> Email</button>

<button><i class="fab fa-twitter"></i> Twitter</button>

</div>

</div>

</>

)

}
```


`About.js`


```jsx
import React from 'react';

  

export default function About(){

return (

<>

<h3>About</h3>

<p>I am a frontend developer with a particular interest in making things simple and automating daily tasks. I try to keep up with security and best practices, and am always looking for new things to learn.</p>

</>

)

}

```

`Interests.js`


```jsx
import React from 'react';

  

export default function Interests(){

return (

<>

<h3>Interests</h3>

<p>Food expert. Music scholar. Reader. Internet fanatic. Bacon buff. Entrepreneur. Travel geek. Pop culture ninja. Coffee fanatic.</p>

</>

)

}
```

`Footer.js`


```jsx
import React from 'react';

  

export default function Footer(){

return (

<>

<h3>Footer Page</h3>

<div className="footer">

<a href="mailto:shreya.purohit002@gmail.com"><i class="far fa-envelope"></i></a>

<a href="https://www.twitter.com/eyeshreya"><i class="fab fa-twitter"></i> </a>

<a href="https://www.github.com/ieshreya"><i class="fab fa-github"></i> </a>

<a href="https://www.instagram.com/ieshreya"><i class="fab fa-instagram"></i> </a>

</div> </>

)

}
```