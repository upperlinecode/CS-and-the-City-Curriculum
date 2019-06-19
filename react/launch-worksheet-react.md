# React

### Navbar.js
```jsx
import React from 'react'
import {link} from 'react-router-dom'

const Navbar = (props) => {
  const activeStyle = {background: 'blue', color: 'white'}
  return(
    <nav>
      <ul>
        <li><Link to="/" style={props.active == 'home' ? activeStyle : {}} href="index.html">Home</Link></li>
        <li><Link to="/" style={props.active == 'about' ? activeStyle : {}} href="index.html">About</Link></li>
        <li><Link to="/" style={props.active == 'contact' ? activeStyle : {}} href="index.html">Contact</Link></li>
      </ul>
    </nav>
  )
}

export default Navbar
```

### Home.js
```jsx
import React from 'react'
import Navbar from './components/Navbar.js'

const Home = () => {
  const component = new React.Component()

  component.render = () => {
    return (
      <div className="Home">
        <Navbar active="home" />
      </div>
    )
  }

  return component
}

export default Home
```

### About.js
```jsx
import React from 'react'
import Navbar from './components/Navbar.js'

const About = () => {
  const component = new React.Component()

  component.render = () => {
    return (
      <div className="About">
        <Navbar active="about" />
      </div>
    )
  }

  return component
}

export default About
```

### Contact.js
```jsx
import React from 'react'
import Navbar from './components/Navbar.js'

const Contact = () => {
  const component = new React.Component()

  component.render = () => {
    return (
      <div className="Contact">
        <Navbar active="contact" />
      </div>
    )
  }

  return component
}

export default Contact
```