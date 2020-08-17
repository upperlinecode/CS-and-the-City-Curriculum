# React

### Navbar.js
```jsx
import React from 'react';
import {link} from 'react-router-dom';

funciton Navbar(props) {
  const activeStyle = {background: 'blue', color: 'white'}
  return(
    <nav>
      <ul>
        <li><Link to="/" style={props.active == 'home' ? activeStyle : {}} href="index.html">Home</Link></li>
        <li><Link to="/" style={props.active == 'about' ? activeStyle : {}} href="index.html">About</Link></li>
        <li><Link to="/" style={props.active == 'contact' ? activeStyle : {}} href="index.html">Contact</Link></li>
      </ul>
    </nav>
  );
}

export default Navbar;
```

### Home.js
```jsx
import React from 'react';
import Navbar from './components/Navbar.js';

class Home() extends React.Component {
  render() {
    return (
      <div className="Home">
        <Navbar active="home" />
      </div>
    );
  }
}

export default Home;
```

### About.js
```jsx
import React from 'react';
import Navbar from './components/Navbar.js';

function About() {
  return (
    <div className="About">
      <Navbar active="about" />
    </div>
  );
}

export default About;
```

### Contact.js
```jsx
import React from 'react';
import Navbar from './components/Navbar.js';

function Contact() {
  return (
    <div className="Contact">
      <Navbar active="contact" />
    </div>
  );
}

export default Contact;
```