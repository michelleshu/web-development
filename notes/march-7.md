# Notes: March 7, 2018

Code from our virtual meeting during the snow storm. Thanks to all who participated!

## Scratch Pad on How to Update State in React

```js
class MyComponent extends React.Component {
    constructor(props) {
        super(props);

        this.state = {
            course: {
                name: 'Intro to CS',
                department: 'Computer Science',
                term: '2018 Spring'
            }
        };
    }

    updateCourseName(newName) {
        //this.state.course.name = newName;
        // Copy current course
        const newCourse = Object.assign({}, this.state.course);

        // ES6 syntax
        const newCourse = {...this.state.course};
        newCourse.name = newName;

        this.setState({ course: newCourse });
    }

    render() {
        return (<button onClick={() => {this.updateCourseName()}}></button>);
    }
}
```


## Say Hello App

`App.js`

```js
import React, { Component } from 'react';
import NameField from './components/NameField';
import Hello from './components/Hello';
import logo from './logo.svg';
import './App.css';

class App extends Component {

  constructor(props) {
    super(props);
    this.state = {
      names: []
    };

    this.addName = this.addName.bind(this);
  }

  addName(name) {
    const names = this.state.names.concat(name);
    this.setState({ names: names });
  }

  render() {
    return (
      <div className="App">
        <NameField addName={this.addName} />
        {this.state.names.map((name, index) => {
          return (<Hello key={index} name={name} />);
        })}
      </div>
    );
  }
}

export default App;
```

`components/NameField.js`
```js
import React from 'react';

class NameField extends React.Component {

    constructor(props) {
        super(props);
        this.state = {
            nameValue: ''
        };

        this.keyUp = this.keyUp.bind(this);
        this.submitName = this.submitName.bind(this);
    }

    keyUp(event) {
        const nameValue = event.target.value;
        this.setState({ nameValue: nameValue });
    }

    submitName() {
        this.props.addName(this.state.nameValue);
    }

    render() {
        return (
            <div>
                <input type="text" onKeyUp={this.keyUp} />
                <button type="submit" onClick={this.submitName}>Submit</button>
            </div>
        );
    }
}

export default NameField;
```

`components/Hello.js`
```js
import React from 'react';

class Hello extends React.Component {
    render() {
        return (<div>Hello {this.props.name}</div>);
    }
}

export default Hello;
```