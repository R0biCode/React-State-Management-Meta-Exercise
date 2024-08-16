The original code in the exercise, the tasks, and then my solution:

-------------------------------------------------------------------------------------------------------------------------
# Task

In the starter code of this code lab, you are given a Fruits component that has its own state. Based on this state, it outputs three fruits on the screen. Additionally, you have a FruitsCounter component which shows a message that reads: "Total fruits: 2".

Y​our task is to lift state up from the Fruits component to the App component, so that you can then pass the state information to both the Fruits component and the FruitsCounter component. This change to the app should fix the previously incorrect message of "Total fruits: 2".  The new message should be "Total fruits: 3".  However, the new message will not be just a hard-coded string. Instead, it should reflect the number of fruits that exist in the state variable, so based on how many fruits there are in the state array, this information should affect the output of the total number of fruits - as returned from the FruitsCounter component.

## Steps

**Step 1.** This task’s starting point is the stateless App component’s code:
```jsx
import Fruits from "./Fruits";
import FruitsCounter from "./FruitsCounter";

function App() {
  return (
    <div className="App">
      <h1>Where should the state go?</h1>
      <Fruits />
      <FruitsCounter />
    </div>
  );
}

export default App;
```

The first step of this task is to move the state from the Fruits component:
```jsx
import React from "react";

function Fruits() {
    const [fruits] = React.useState([
        {fruitName: 'apple', id: 1},
        {fruitName: 'apple', id: 2},
        {fruitName: 'plum', id: 3},
    ]);

    return (
        <div>
            {fruits.map(f => <p key={f.id}>{f.fruitName}</p>)}
        </div>
    )
}

export default Fruits
```

T​he state should be moved to the App component. That is the first step of this task.

**Step 2.** AOnce you've moved the state up from the Fruits component to the App component, you need to update the FruitsCounter component so that it accepts that state from the App component, and then uses it to display the number of the available fruits using the length property of the array of fruits from the fruits state variable that comes from App and is received in FruitsCounter as a prop.utton tags, add the following text: Guess the number between 1 and 3. 

**Step 3.** Save your updates and serve the app so that it shows the correct count of fruits, while the rest of the output should remain unchanged.


-------------------------------------------------------------------------------------------------------------------------

My solution:

First, I had to find the problem, which was that the counter didn't work as planned. Why didn't it work as planned? Because App.js was stateless, and it's children ( whom FruitsCounter.js didn't have access to, because it's also a children of the App.js ), Fruits.js, had a defined state. The state had to move up the
coding family ladder, and make App.js stateful. What I did was take the state defined in the Fruits.js function, and moved it inside the App.js app. This allowed me to then add props to both elements, Fruits & FruitsCounter. At first I didn't understand what it wanted me to solve, but after stumbling for a while, I managed to figure it out. It wanted me to find the length of the array, aka how many fruits are in the basket. After assigning the defined state array "fruits" to Fruits.js, I used props to use the information to find exactly what I need, which in this example was to say the right name for each fruit. Next on my problem solving list was the Counter that didn't work. This was really simple, I just exported a function that counted the length of the array, aka how many elements are in the said array by using the .length array procedure.

