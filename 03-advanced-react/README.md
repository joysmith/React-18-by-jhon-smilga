#### 75. [Intro](#75)

#### 76. [Github Repository](#76)

#### 77. [Setup](#77)

#### 78. [Overview](#78)

#### 79. [Error Example](#79)

#### 80. [UseState Fundamentals](#80)

#### 81. [Initial Render and Re-renders](#81)

#### 82. [General Rules of React Hooks](#82)

#### 83. [UseState Array Example - Setup](#83)

#### 84. [UseState Array Example - Complete](#84)

#### 85. [UseState - Extra Info](#85)

#### 86. [UseState Object Example - Setup](#86)

#### 87. [Auto Batching Info](#87)

#### 88. [UseState Object Example - Complete](#88)

#### 89. [UseState Set Function "Gotcha"](#89)

#### 90. [UseState Functional Update Form](#90)

#### 91. [UseState - SetTimeout Example](#91)

#### 92. [Matching Project](#92)

#### 93. [Code Example](#93)

#### 94. [UseEffect - Fundamentals](#94)

#### 95. [UseEffect - Multiple Effects](#95)

#### 96. [UseEffect Fetch Challenge - Intro](#96)

#### 97. [UseEffect Fetch Challenge - Complete](#97)

#### 98. [UseEffect Clean Up Info](#98)

#### 99. [Multiple Returns](#99)

#### 100. [Multiple Returns - Fetch Data Setup](#100)

#### 101. [Multiple Returns - Fetch Data](#101)

#### 102. [Fetch Error "Gotcha"](#102)

#### 103. [Order Matters](#103)

#### 104. [Fetch Function Location](#104)

#### 105. [React Hooks Rules](#105)

#### 106. [Vanilla.js (Optional)](#106)

#### 107. [Short Circuit - Overview](#107)

#### 108. [Short Circuit - Examples](#108)

#### 109. [Ternary Operator](#109)

#### 110. [Toggle Challenge](#110)

#### 111. [User Challenge](#111)

#### 112. [UseEffect Cleanup Function - Setup/Challenge](#112)

#### 113. [UseEffect - Timer Example](#113)

#### 114. [UseEffect - Event Listeners Example](#114)

#### 115. [You Might Not Need an Effect](#115)

#### 116. [Matching Projects](#116)

#### 117. [Project Structure - Folder Example](#117)

#### 118. [Project Structure - Named Exports](#118)

#### 119. [Project Structure - Export Group](#119)

#### 120. [Leverage Javascript - Intro](#120)

#### 121. [Leverage Javascript - Challenge](#121)

#### 122. [Leverage Javascript - Complete](#122)

#### 123. [Forms - Setup](#123)

#### 124. [Controlled Inputs](#124)

#### 125. [User Challenge - Setup](#125)

#### 126. [User Challenge - Add New User](#126)

#### 127. [User Challenge - Remove User](#127)

#### 128. [Multiple Inputs](#128)

#### 129. [Checkbox Input](#129)

#### 130. [Select Input](#130)

#### 131. [FormData API](#131)

#### 132. [Matching Projects](#132)

#### 133. [useRef - DOM Node](#133)

#### 134. [useRef - Initial Render](#134)

#### 135. [Matching Projects](#135)

#### 136. [Custom Hooks - Toggle](#136)

#### 137. [Custom Hooks - Fetch Person](#137)

#### 138. [Custom Hooks - Generic Fetch](#138)

#### 139. [Context API - Challenge](#139)

#### 140. [Context API - Prop Drilling](#140)

#### 141. [Context API - Solution](#141)

#### 142. [Context API - Custom Hook](#142)

#### 143. [Context API - Global Setup](#143)

#### 144. [Matching Projects](#144)

#### 145. [UseReducer - Intro](#145)

#### 146. [UseReducer - Challenge](#146)

#### 147. [UseReducer - Setup](#147)

#### 148. [Reducer Basics](#148)

#### 149. [Actions and Default State](#149)

#### 150. [Reset List](#150)

#### 151. [Remove Person](#151)

#### 152. [Import/Export](#152)

#### 153. [Matching Projects](#153)

#### 154. [Performance - Intro](#154)

#### 155. [Component Re-renders](#155)

#### 156. [React Dev Tools](#156)

#### 157. [Lower State](#157)

#### 158. [Lower State - Challenge](#158)

#### 159. [React.memo()](#159)

#### 160. [Mind Grenade](#160)

#### 161. [UseCallback Hook](#161)

#### 162. [UseCallback Hook - Common Use Case](#162)

#### 163. [UseMemo Hook](#163)

#### 164. [UseTransition Hook](#164)

#### 165. [React Suspense](#165)

<br>

---

### 75. Intro<a id="75"></a>

<br>

### 76. Github Repository<a id="76"></a>

<br>

### 77. Setup<a id="77"></a>

- In 03-Advanced-react run the cmd

```sh
npm install && npm run dev
```

- http://localhost:5173/

<br>

### 78. Overview<a id="78"></a>

- Preset, Dont need to change anything

- traditional Vite app
  - removed boilerplate
  - provided some assets (css, data)
    - just so we can focus on important stuff
  - removed <StrictMode>, so it's less logs

---

#### Advanced Topics

- src/tutorial/01-useState directory
- work in the starter folder
- complete code in the final folder
- in order to work on topic import component from 'starter' to src/App.jsx
- in order to test final import component from 'final' to src/App.jsx
- setup challenges
- in the beginning examples with numbers and buttons :):):)

- In src/App.jsx

```js
import Starter from "./tutorial/1-useState/starter/1-error-example";
import Final from "./tutorial/1-useState/final/1-error-example";

function App() {
  return (
    <div className="container">
      <Starter />
      <Final />
    </div>
  );
}

export default App;
```

<br>

### 79. Error Example<a id="79"></a>

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/01-useState/starter/01-error-example.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

Setup Challenge for src/tutorial/01-useState/starter/01-error-example.jsx :

- create count variable
- display value in the JSX
- add button and increase the value
- the reason for bug - we don't trigger re-render (reference next lecture)

- In src/tutorial/01-useState/starter/01-error-example.jsx

```js
const ErrorExample = () => {
  let count = 0;

  const handleClick = () => {
    count = count + 1;
    console.log(count);
    // preserve value between renders
    // trigger re-render
  };
  return (
    <div>
      <h2>{count}</h2>
      <button type="button" className="btn" onClick={handleClick}>
        increment
      </button>
    </div>
  );
};

export default ErrorExample;
```

<br>

### 80. UseState Fundamentals<a id="80"></a>

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/01-useState/starter/02-useState-basics.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

Setup Challenge for src/tutorial/01-useState/starter/02-useState-basics.jsx :

[Javascript Nuggets - Destructuring (Array)](https://www.youtube.com/watch?v=qhECs40xMec&list=PLnHJACx3NwAfRUcuKaYhZ6T5NRIpzgNGJ&index=7&t=9s)

- useState hook, which is function that react library provide
- returns an array with two elements: the current state value, and a function that we can use to update the state
- accepts default value as an argument
- state update triggers re-render

- In src/tutorial/01-useState/starter/02-useState-basics.jsx

```js
import { useState } from "react";

const UseStateBasics = () => {
  // console.log(useState());
  // console.log(useState('jo koy'));
  // const value = useState()[0];
  // const handler = useState()[1];
  // console.log(value, handler);

  // destructure array and set default value 0
  const [count, setCount] = useState(0);

  const handleClick = () => {
    // console.log(count)
    setCount(count + 1);
    // be careful, we can set any value
    // setCount('pants');
  };
  return (
    <div>
      <h4>You clicked {count} times</h4>
      <button className="btn" onClick={handleClick}>
        Click me
      </button>
    </div>
  );
};

export default UseStateBasics;
```

<br>

### 81. Initial Render and Re-renders<a id="81"></a>

In a React application, the initial render is the first time that the component tree is rendered to the DOM. It happens when the application first loads, or when the root component is first rendered. This is also known as "mounting" the components.

Re-renders, on the other hand, happen when the component's state or props change, and the component needs to be updated in the DOM to reflect these changes. React uses a virtual DOM to optimize the process of updating the actual DOM, so that only the necessary changes are made.

There are a few ways that you can trigger a re-render in a React component:

- By changing the component's state or props. When the component's state or props change, React will re-render the component to reflect these changes.

- When the parent element re-renders, even if the component's state or props have not changed.

<br>

### 82. General Rules of React Hooks<a id="82"></a>

- all hooks starts with "use" (both -react and custom hooks)
- to work with hooks, component must be uppercase
- invoke hooks inside function/component body
- don't call hooks conditionally (cover later), means dont call hooks inside if-else
- set functions don't update state immediately (cover later)

<br>

### 83. UseState Array Example - Setup<a id="83"></a>

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/01-useState/starter/03-useState-array.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

Setup Challenge : 1. render the list

- import data
- setup a state value
  - people - default value equal to data
- display list(people) in the browser

- In src/tutorial/01-useState/starter/03-useState-array.jsx

```js
import React from "react";
import { data } from "../../../data";
const UseStateArray = () => {
  const [people, setPeople] = React.useState(data);

  return (
    <div>
      {people.map((person) => {
        const { id, name } = person;
        return (
          <div key={id} className="item">
            <h4>{name}</h4>
          </div>
        );
      })}
    </div>
  );
};

export default UseStateArray;
```

<br>

### 84. UseState Array Example - Complete<a id="84"></a>

2. remove items

- create two functions

  - one that removes single item from the list
  - one that clears entire list

[Javascript Nuggets - Filter and Find](https://www.youtube.com/watch?v=KeYxsev737s&list=PLnHJACx3NwAfRUcuKaYhZ6T5NRIpzgNGJ&index=4)

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/01-useState/starter/03-useState-array.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

- In src/tutorial/01-useState/starter/03-useState-array.jsx

```js
import React from "react";
import { data } from "../../../data";
const UseStateArray = () => {
  const [people, setPeople] = React.useState(data);

  // ref callback function
  const removeItem = (id) => {
    // id does not match
    // return ture: only return match item i.e id
    // return false: return all items except unmatch one i.e id
    let newPeople = people.filter((person) => person.id !== id);
    setPeople(newPeople);
  };

  // empty array -old ref
  // const clearAllItems = () => {
  //   setPeople([]);
  // };

  return (
    <div>
      {people.map((person) => {
        const { id, name } = person;
        return (
          <div key={id} className="item">
            <h4>{name}</h4>
            <button onClick={() => removeItem(id)}>remove</button>
          </div>
        );
      })}

      <button
        className="btn"
        style={{ marginTop: "2rem" }}
        onClick={() => setPeople([])}
      >
        clear items
      </button>
    </div>
  );
};

export default UseStateArray;
```

<br>

### 85. UseState - Extra Info<a id="85"></a>

<br>

### 86. UseState Object Example - Setup<a id="86"></a>

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/01-useState/starter/04-useState-object.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

Setup Challenge :

- setup three state values
  - name(string)
  - age(number)
  - hobby(string)
- render in the browser
- create a button
  - setup a function
    - update all three state values
- as a result once the user clicks the button,
  new person is displayed in the browser

<br>

- In src/tutorial/01-useState/starter/04-useState-object.jsx

```js
import { useState } from "react";

// 1. setup details
const UseStateObject = () => {
  const [name, setName] = useState("peter");
  const [age, setAge] = useState(24);
  const [hobby, setHobby] = useState("read books");

  // 3. setup callback function to change useState
  const displayPerson = () => {
    setName("john");
    setAge(28);
    setHobby("scream at the computer");
  };
  return (
    // 2. setup JSX display
    <>
      <h3>{name}</h3>
      <h3>{age}</h3>
      <h4>Enjoys To: {hobby}</h4>
      <button className="btn" onClick={displayPerson}>
        show john
      </button>
    </>
  );
};

export default UseStateObject;
```

<br>

### 87. Auto Batching Info<a id="87"></a>

In React, "batching" refers to the process of grouping multiple state updates into a single update. This can be useful in certain cases because it allows React to optimize the rendering of your components by minimizing the number of DOM updates that it has to perform.

By default, React uses a technique called "auto-batching" to group state updates that occur within the same event loop into a single update. This means that if you call the state update function multiple times in a short period of time, React will only perform a single re-render for all of the updates.

React 18 ensures that state updates invoked from any location will be batched by default. This will batch state updates, including native event handlers, asynchronous operations, timeouts, and intervals.

<br>

### 88. UseState Object Example - Complete<a id="88"></a>

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/01-useState/starter/04-useState-object.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

- In src/tutorial/01-useState/starter/04-useState-object.jsx

```js
import { useState } from "react";

// 1. setup person default value as obj, using usestate
const UseStateObject = () => {
  const [person, setPerson] = useState({
    name: "peter",
    age: 24,
    hobby: "read books",
  });

  // 2. setup setPerson obj using useState
  const displayPerson = () => {
    setPerson({ name: "john", age: 28, hobby: "scream at the computer" });
    // be careful, don't overwrite
    // setPerson('shakeAndBake');
    // setPerson({ name: 'susan' });
    // setPerson({ ...person, name: 'susan' });   // only change name, and dont touch age, hobby
  };

  return (
    // 3. modigy jsx to access property -without destructure
    <>
      <h3>{person.name}</h3>
      <h3>{person.age}</h3>
      <h4>Enjoys To: {person.hobby}</h4>
      <button className="btn" onClick={displayPerson}>
        show john
      </button>
    </>
  );
};

export default UseStateObject;
```

<br>

### 89. UseState Set Function "Gotcha"<a id="89"></a>

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/01-useState/starter/05-useState-gotcha.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

Setup Challenge :

- setup a state value and the button
- add functionality to increase value by 1
- log a state value, right after setFunction

Keep in mind that the state update function setState does not immediately mutate the state. Instead, it schedules an update to the state and tells React that it needs to re-render the component. The actual state update will be performed as part of the next rendering cycle. Be mindful when you need to set state value based on a different state value.

trivial example

- In src/tutorial/01-useState/starter/05-useState-gotcha.jsx

```js
import { useState } from "react";

const UseStateGotcha = () => {
  const [value, setValue] = useState(0);

  const handleClick = () => {
    setValue(value + 1);
    //  be careful it's the old value
    console.log(value);
    //  so if you have any functionality
    // that relies on the latest value
    // it will be wrong !!!
  };
  return (
    <div>
      <h1>{value}</h1>
      <button className="btn" onClick={handleClick}>
        increase
      </button>
    </div>
  );
};

export default UseStateGotcha;
```

<br>

### 90. UseState Functional Update Form<a id="90"></a>

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/01-useState/starter/05-useState-gotcha.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

- In src/tutorial/01-useState/starter/05-useState-gotcha.jsx

```js
import { useState } from "react";

const UseStateGotcha = () => {
  const [value, setValue] = useState(0);

  const handleClick = () => {
    setValue((currentState) => {
      const newState = currentState + 1;
      return newState;
    });

    console.log(value);
  };
  return (
    <div>
      <h1>{value}</h1>
      <button className="btn" onClick={handleClick}>
        increase
      </button>
    </div>
  );
};

export default UseStateGotcha;
```

<br>

### 91. UseState - SetTimeout Example<a id="91"></a>

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/01-useState/starter/05-useState-gotcha.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

- In src/tutorial/01-useState/starter/05-useState-gotcha.jsx

```js
import { useState } from "react";

const UseStateGotcha = () => {
  const [value, setValue] = useState(0);

  const handleClick = () => {
    // setTimeout(() => {
    // console.log('clicked the button');
    //   setValue(value + 1);
    // }, 3000);
    setTimeout(() => {
      console.log("clicked the button");
      setValue((currentState) => {
        return currentState + 1;
      });
    }, 3000);
  };

  return (
    <div>
      <h1>{value}</h1>
      <button className="btn" onClick={handleClick}>
        increase
      </button>
    </div>
  );
};

export default UseStateGotcha;
```

<br>

### 92. Matching Project<a id="92"></a>

<br>

### 93. Code Example<a id="93"></a>

- In src/App.jsx setup import and container div

```js
import Starter from "./tutorial/02-useEffect/starter/01-code-example.jsx";

function App() {
  return (
    <div className="container">
      <Starter />
    </div>
  );
}

export default App;
```

---

- In src/tutorial/02-useEffect/starter/01-code-example.jsx

```js
import { useState } from "react";

const ComponentExample = () => {
  const [value, setValue] = useState(0);
  const sayHello = () => {
    console.log("hello there");
    // be careful
    // setValue(value + 1);
  };
  sayHello();
  return (
    <div>
      <h1>value : {value}</h1>
      <button className="btn" onClick={() => setValue(value + 1)}>
        click me
      </button>
    </div>
  );
};
export default ComponentExample;
```

- the problem starts when we update the state

```js
const [value, setValue] = useState(0);

const sayHello = () => {
  console.log("hello there");
  // be careful, you will have infinite loop
  setValue(value + 1);
};
sayHello();
```

- initial render - setup state value and invoke sayHello
- in the sayHello update state, trigger re-render

- re-render - setup state value and invoke sayHello
- in the sayHello update state, trigger re-render

- repeat
- repeat
- repeat
  ..................................................

- but what about fetching data?

<br>

### 94. UseEffect - Fundamentals<a id="94"></a>

<br>

### 95. UseEffect - Multiple Effects<a id="95"></a>

<br>

### 96. UseEffect Fetch Challenge - Intro<a id="96"></a>

<br>

### 97. UseEffect Fetch Challenge - Complete<a id="97"></a>

<br>

### 98. UseEffect Clean Up Info<a id="98"></a>

<br>

### 99. Multiple Returns<a id="99"></a>

<br>

### 100. Multiple Returns - Fetch Data Setup<a id='100'></a>

<br>

### 101. Multiple Returns - Fetch Data<a id='101'></a>

<br>

### 102. Fetch Error "Gotcha"<a id='102'></a>

<br>

### 103. Order Matters<a id='103'></a>

<br>

### 104. Fetch Function Location<a id='104'></a>

<br>

### 105. React Hooks Rules<a id='105'></a>

<br>

### 106. Vanilla.js (Optional)<a id='106'></a>

<br>

### 107. Short Circuit - Overview<a id='107'></a>

<br>

### 108. Short Circuit - Examples<a id='108'></a>

<br>

### 109. Ternary Operator<a id='109'></a>

<br>

### 110. Toggle Challenge<a id='110'></a>

<br>

### 111. User Challenge<a id='111'></a>

<br>

### 112. UseEffect Cleanup Function - Setup/Challenge<a id='112'></a>

<br>

### 113. UseEffect - Timer Example<a id='113'></a>

<br>

### 114. UseEffect - Event Listeners Example<a id='114'></a>

<br>

### 115. You Might Not Need an Effect<a id='115'></a>

<br>

### 116. Matching Projects<a id='116'></a>

<br>

### 117. Project Structure - Folder Example<a id='117'></a>

<br>

### 118. Project Structure - Named Exports<a id='118'></a>

<br>

### 119. Project Structure - Export Group<a id='119'></a>

<br>

### 120. Leverage Javascript - Intro<a id='120'></a>

<br>

### 121. Leverage Javascript - Challenge<a id='121'></a>

<br>

### 122. Leverage Javascript - Complete<a id='122'></a>

<br>

### 123. Forms - Setup<a id='123'></a>

<br>

### 124. Controlled Inputs<a id='124'></a>

<br>

### 125. User Challenge - Setup<a id='125'></a>

<br>

### 126. User Challenge - Add New User<a id='126'></a>

<br>

### 127. User Challenge - Remove User<a id='127'></a>

<br>

### 128. Multiple Inputs<a id='128'></a>

<br>

### 129. Checkbox Input<a id='129'></a>

<br>

### 130. Select Input<a id='130'></a>

<br>

### 131. FormData API<a id='131'></a>

<br>

### 132. Matching Projects<a id='132'></a>

<br>

### 133. useRef - DOM Node<a id='133'></a>

<br>

### 134. useRef - Initial Render<a id='134'></a>

<br>

### 135. Matching Projects<a id='135'></a>

<br>

### 136. Custom Hooks - Toggle<a id='136'></a>

<br>

### 137. Custom Hooks - Fetch Person<a id='137'></a>

<br>

### 138. Custom Hooks - Generic Fetch<a id='138'></a>

<br>

### 139. Context API - Challenge<a id='139'></a>

<br>

### 140. Context API - Prop Drilling<a id='140'></a>

<br>

### 141. Context API - Solution<a id='141'></a>

<br>

### 142. Context API - Custom Hook<a id='142'></a>

<br>

### 143. Context API - Global Setup<a id='143'></a>

<br>

### 144. Matching Projects<a id='144'></a>

<br>

### 145. UseReducer - Intro<a id='145'></a>

<br>

### 146. UseReducer - Challenge<a id='146'></a>

<br>

### 147. UseReducer - Setup<a id='147'></a>

<br>

### 148. Reducer Basics<a id='148'></a>

<br>

### 149. Actions and Default State<a id='149'></a>

<br>

### 150. Reset List<a id='150'></a>

<br>

### 151. Remove Person<a id='151'></a>

<br>

### 152. Import/Export<a id='152'></a>

<br>

### 153. Matching Projects<a id='153'></a>

<br>

### 154. Performance - Intro<a id='154'></a>

<br>

### 155. Component Re-renders<a id='155'></a>

<br>

### 156. React Dev Tools<a id='156'></a>

<br>

### 157. Lower State<a id='157'></a>

<br>

### 158. Lower State - Challenge<a id='158'></a>

<br>

### 159. React.memo()<a id='159'></a>

<br>

### 160. Mind Grenade<a id='160'></a>

<br>

### 161. UseCallback Hook<a id='161'></a>

<br>

### 162. UseCallback Hook - Common Use Case<a id='162'></a>

<br>

### 163. UseMemo Hook<a id='163'></a>

<br>

### 164. UseTransition Hook<a id='164'></a>

<br>

### 165. React Suspense<a id='165'></a>

<br>
```
