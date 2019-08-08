### React Component Code Review

- What does the following component do?
  The following component will show list of items and and red back-ground and onclick it shows the index of the item.
  
- Are there any problems with it? If so, what are they?
  Yes, there are many issues with this code and everything is mention in code.
  
- Are there any improvements/changes you would make?
  yes, Done you can see the code for the change which i have made.

import React from 'react';

//This is the child component with class type component.

class SomeListComponent extends React.Component {
  constructor (props) {
    super(props);// super() is required when we use constructor
    this.state = { items: this.props.items } //it should be 'this.props' beacuse it is the child component and parent is class component so we have to use this way
  }

  shouldComponentUpdate (nextProps) {
    return nextProps.items !== this.props.items // when props are not same then update the state
  }

  handleClick (index) {
    this.props.onClick(index) // it takes onclick event from the parent and show the index of the items listed
  }

  renderElement (item, index) {
    return <li onClick={() => this.handleClick(index)}>{item.text}</li>
  }

  render () {
    return (
      <ul style={{ backgroundColor: 'red', height: 100 }}>
        {this.state.items.map((item, i) => this.renderElement(item, i))}
      </ul>
    )
  }
}

export default SomeListComponent
```
