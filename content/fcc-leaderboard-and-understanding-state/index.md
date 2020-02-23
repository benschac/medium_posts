---
title: "FCC LeaderBoard and Understanding State"
description: "React forces you to think about data differently in general. I’ve made a couple of different small projects, but now it’s starting to…"
date: "2017-03-12T15:07:05.766Z"
categories: []
published: true
canonical_link: https://medium.com/@benschac/fcc-leaderboard-and-understanding-state-9bb9a46821f
redirect_from:
  - /fcc-leaderboard-and-understanding-state-9bb9a46821f
---

React forces you to think about data differently in general. I’ve made a couple of different small projects, but now it’s starting to click. I’m starting to understand how state works and what the advantages are to using it. Additionally Reacts lifecycle components further let you control your data and how it needs to flow. If you want to dig a little deeper into my code outside of the examples I show heres a link to my project on [github](https://github.com/benschac/25-react-projects/tree/master/recipe-box). While the app is only about 170 lines of code, using state probably saved me a whole bunch of code. So, let’s jump in.

State is the only data that _can_ change in a React application. State changes based of some kind of user interaction with the data on the application. The nice thing about React is once you embrace just changing the state and not manipulating the DOM that’s all you need to worry about. Changing and managing the state (or props, well data of the application). Sidenote: this application doesn’t use any components other than app so there won’t be any props in this example.

### Methods That Change State

First I wrote the methods that would manipulate the state. This is a pretty simple CRUD application.

#### Delete

```
// Delete Recipe!  
deleteRecipe = (recipe) => {    
   const recipes = {...this.state.recipes};    
   delete recipes[recipe];    
   this.setState({recipes});
}
```

I use this convention quite a bit. Copy your state, directly manipulating state is a no-no. Then use the key you’ll pass to the function to find the recipe you’re looking to delete and use the good old delete that javascript has for objects. After that set your state with your new recipes object that doesn’t have the object you removed. Notice, you have touched the previous state data. Just added new data.

#### Add

```
// Create recipe!  
addRecipe = (recipe) =>  {    
   const recipes = {...this.state.recipes};    
   const last = Date.now()    
   recipes[`recipe${last}`] = recipe;      
   this.setState({recipes});  
}
```

We’re basically doing the same thing here. New object, accept instead of deleting the object from state we add a new one using a unique key with the Date.now method which returns a number of milliseconds since sometime in like 1970 or something. The point is that it’ll be unique so you won’t accidentally overwrite a piece of state that’s all ready there. Then, place your new copied state back into the application. There’s an additional step here where we need to create an object to pass to create but I’m going to skip that for the moment.

#### Edit

```
// Edit Recipe!  
editRecipe = (event, key) => {     
    event.preventDefault();    
    const recipes = {...this.state.recipes}      
    recipes[key] = {  
            title: this.editTitle.value,
            items: this.editTextarea.value.split(',')   
    }       
    this.setState({recipes})   
}
```

Again, basically the same thing here. We sort of combine what we did with add here accept we take a key to update our state.

We didn’t have to grab anything from the DOM which makes the next part of the application cake. Reading the data in state is just a matter of looping through it all. Any time state changes the component is going to update and your data you’re looping through is going to reflect that. The state is your ultimate source of truth. Pass it to your props. Change it on use interactions with your methods. Change the object when you need it.

The last place where I saw this data driven approach really shine was saving the state to local storage. It was such a small about of code.

```
componentWillUpdate(nextProps, nextState) {

    if(storageAvailable('localStorage')) {

    const ref = localStorage.setItem('recipes',                JSON.stringify(nextState.recipes))

    } else {

    console.error('Your browser doesn\'t support local storage');

  }

}

componentWillMount() {

    if(storageAvailable('localStorage')) {

    const localRef = localStorage.getItem('recipes',      JSON.stringify(this.state.recipes))

    if(localRef) {

    this.setState({

    recipes: JSON.parse(localRef)

})

}

} else {

console.error('Your browser doesn\'t support local storage');

}

}
```

Because the state was changing I could let React’s lifecycle components do all of the heavy lifting for me. If the state changed, update local storage with a new state object.

This project has shown me how data should be managed in a react application (heh I think).

Wanna give it a try on your own? Check out [FreeCodeCamp](https://www.freecodecamp.com/challenges/build-a-recipe-box).
