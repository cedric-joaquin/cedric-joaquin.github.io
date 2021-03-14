---
layout: post
title:      "The React Lifecycle"
date:       2021-03-14 19:47:55 +0000
permalink:  the_react_lifecycle
---


Important understanding of the React Lifecycle will go a long way in building fluid and efficient apps.

![](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/ogimage.png)
<div align="center">https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/ogimage.png</div>

You likely already know `render` as it is a requirement for any React component to work. But the two other important lifecycle methods are `componentDidMount` and `componentWillUnmount`

# `componentDidMount`

When including `componentDidMount` React will invoke this method once your component is first mounted into the DOM. Best applications for this is for any asynchronous code such as fetch requests to your server. Or setting any timers/intervals needed for your application. For example:
```
import React, { Component } from 'react';
import { BoxSeam } from 'react-bootstrap-icons'
import Items from '../components/items/Items'
import { Link } from 'react-router-dom'

export default class ItemsContainer extends Component {

  componentDidMount() {
    this.props.fetchItems();
  }
  
  render() {

    return (
        <>
        <header class="navbar border-bottom pb-0">
            <h1><BoxSeam size={30}/> Inventory</h1> <Link to='/inventory/new'><button class="btn btn-primary">Add Item</button></Link>
        </header>
        <Items items={this.props.items} deleteItem={this.props.deleteItem} editItem={this.props.editItem} addItem={this.props.addItem}/>
        </>
    );
  }
}
```
For my inventory tracking app, I placed a `componentDidMount` in my `ItemsContainer` that would fetch the items stored in the server. 

Another common use is to initialize any timers for your app. Your app could have functionality where it needs to track the time a user has spent on the page.

```
...

componentDidMount() {
    let count = 0

    addCount() {
        count += 1
    }

    let interval = setInterval(addCount, 1000)
}
```

The function above will create an interval and increase the counter by 1 for each second that has passed.

# `componentWillUnmount`

This lifecycle method is useful for clearing any ongoing actions that were set in your `componentDidMount` method. For instance, in the example above if we want to remove this component we need to clear the interval to avoid any errors. 

```
...

componentWillUnmount() {
    clearInterval(interval)
}
```

# `constructor`

Another common Lifecycle method is `constructor()`. This method gets invoked before the component is even mounted. Think of it like creating an instance of your component. This is where you can set initial state for your component. For example, when creating a controlled form:

```
export default class ItemInput extends Component {

    constructor(props) {
        super(props);
        
        
        if (this.props.items) {
            const filteredItem = this.props.items.filter(item => item.id == this.props.match.params.itemId)
            let item = {...filteredItem[0]}
            this.state = {
                item,
                editingItem: true
            }
        } else {
            this.state = {
                item: {
                    purchase_date: "",
                    name: "",
                    brand: "",
                    size: "",
                    cost: ""
                },
                addingItem: true
            }
        }
    }
...
```

While these lifecycle methods are not generally required to be used. When implemented correctly, they provide great functionality to your app and provides a fluid experience for the user. 
