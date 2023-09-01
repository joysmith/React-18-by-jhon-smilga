#### 166. [Intro](#166)

#### 167. [Setup](#167)

#### 168. [Setup - Figma File](#168)

#### 169. [Birthday Buddy- Setup](#169)

#### 170. [Birthday Buddy - Import List](#170)

#### 171. [Birthday Buddy - Render List](#171)

#### 172. [Birthday Buddy - Clear List](#172)

#### 173. [Birthday Buddy - CSS (Optional)](#173)

<br>

---

### 166. Intro<a id='166'></a>

> Que: How should I work on project <br>
> Ans: There are Three ways

- 1. For small project, try to build project by reading notes provided before watching the video
- 2. Instead of completing entire project build specific feature and then watch video if stuck
- 3. ✅ watch the full video, then try to recreate/clone same project as it is.
  - Or try to implement one or more functionality in your own project

<br>

### 167. Setup<a id='167'></a>

- ref. 04-Fundamental-Projects/README.md

<br>

### 168. Setup - Figma File<a id='168'></a>

[Birthday Buddy](https://www.figma.com/file/e2vsLe9DMnXZIygNHkwGL1/Birthday-buddy?node-id=0%3A1&t=AGNWdO5QQGOoNCfD-1)

<br>

### 169. Birthday Buddy- Setup<a id='169'></a>

- Install dependency

```sh
npm install
```

- Spin up dev server

```sh
npm run dev
```

- Open localhost
- don't worry about CSS, checkout example image

<br>

### 170. Birthday Buddy - Import List<a id='170'></a>

- In 01-birthday-buddy/starter/src/App.jsx,

#### Import Data

import the data (from data.js) to be rendered as an array of objects. Each object should represent a person and contain properties such as name, age, and image URL.

#### Setup State Variable

Then, set up the data as a state variable using the useState hook. This will allow the data to be modified and have those changes automatically reflected in the rendered output.

```js
import { useState } from "react";
import data from "./data";

const App = () => {
  const [people, setPeople] = useState(data);
  console.log(people);

  return <h2>Birthday Reminder - Starter</h2>;
};
export default App;
```

<br>

### 171. Birthday Buddy - Render List<a id='171'></a>

Display the number of items in the list by using the length property of the state variable. This information can be displayed using plain text or added to a message or heading element.

To render the list of people, iterate over the data array using the map method. For each item in the array, render an image element (hint : use inline styles to make width smaller).Additionally, render the person's name and age as plain text.

Create a List component to hold the rendered items. This component can be a simple div element containing the list of Person components.

Create a Person component to render the information for each person. This component should receive the person data as props and render the image, name, and age information.

<br>

- In src folder create List.jsx, component -rafce, import on App.jsx

```js
import React from "react";

const List = () => {
  return <div>List</div>;
};

export default List;
```

---

- In 01-birthday-buddy/starter/src/App.jsx,

```js
import { useState } from "react";
import data from "./data";
import List from "./List";

const App = () => {
  const [people, setPeople] = useState(data);

  return (
    <main>
      <section className="container">
        <h3>{people.length} birthdays today</h3>
        <List people={people} />
      </section>
    </main>
  );
};
export default App;
```

---

- In src folder create Person.jsx, import on List.jsx

```js
import React from "react";

const Person = () => {
  return <div>Person</div>;
};

export default Person;
```

---

- In src/List.jsx

```js
import React from "react";
import Person from "./Person";

const List = ({ people }) => {
  return (
    <section>
      {people.map((person) => {
        return <Person key={person.id} {...person} />;
      })}
    </section>
  );
};

export default List;
```

---

- In src/Person.jsx, create the template

```js
const Person = ({ image, name, age }) => {
  return (
    <article className="person">
      <img src={image} alt={name} className="img" />
      <div>
        <h4>{name}</h4>
        <p>{age} years</p>
      </div>
    </article>
  );
};
export default Person;
```

<br>

### 172. Birthday Buddy - Clear List<a id='172'></a>

In App.jsx, add a button to clear the list, and set up the functionality by defining a function that resets the state variable to an empty array.

Overall, the flow of the application should look something like this:

- Import the data you want to render in App.jsx.
- Set up the data as a state variable using useState.
- Use the map method to iterate over the data array and render a Person component for each person.
- Each Person component should render an image with a style prop to control the width, the person's name, and the person's age.
- Create a List component that holds the rendered items.
- Create a button with functionality to clear the list.
- Display the number of items in the list using the length property of the state variable. This can be rendered using plain text or added to a message or heading element.

- In 01-birthday-buddy/starter/src/App.jsx,

```js
import { useState } from "react";
import data from "./data";
import List from "./List";

const App = () => {
  const [people, setPeople] = useState(data);

  return (
    <main>
      <section className="container">
        <h3>{people.length} birthdays today</h3>
        <List people={people} />

        <button
          type="button"
          className="btn btn-block"
          onClick={() => setPeople([])}
        >
          clear all
        </button>
      </section>
    </main>
  );
};
export default App;
```

---

<br>

### 173. Birthday Buddy - CSS (Optional)<a id='173'></a>

- In src/index.css

```css
/* ============= GLOBAL CSS =============== */

*,
::after,
::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 100%;
} /*16px*/

:root {
  /* colors */
  --primary-100: #fae8ff;
  --primary-200: #f5d0fe;
  --primary-300: #f0abfc;
  --primary-400: #e879f9;
  --primary-500: #d946ef;
  --primary-600: #c026d3;
  --primary-700: #a21caf;
  --primary-800: #86198f;
  --primary-900: #701a75;

  /* grey */
  --grey-50: #f8fafc;
  --grey-100: #f1f5f9;
  --grey-200: #e2e8f0;
  --grey-300: #cbd5e1;
  --grey-400: #94a3b8;
  --grey-500: #64748b;
  --grey-600: #475569;
  --grey-700: #334155;
  --grey-800: #1e293b;
  --grey-900: #0f172a;
  /* rest of the colors */
  --black: #222;
  --white: #fff;
  --red-light: #f8d7da;
  --red-dark: #842029;
  --green-light: #d1e7dd;
  --green-dark: #0f5132;

  --small-text: 0.875rem;
  --extra-small-text: 0.7em;
  /* rest of the vars */
  --backgroundColor: var(--grey-50);
  --textColor: var(--grey-900);
  --borderRadius: 0.25rem;
  --letterSpacing: 1px;
  --transition: 0.3s ease-in-out all;
  --max-width: 1120px;
  --fixed-width: 600px;

  /* box shadow*/
  --shadow-1: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
  --shadow-2: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  --shadow-3: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  --shadow-4: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
}

body {
  background: var(--backgroundColor);
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  font-weight: 400;
  line-height: 1;
  color: var(--textColor);
}
p {
  margin: 0;
}
h1,
h2,
h3,
h4,
h5 {
  margin: 0;
  font-family: var(--headingFont);
  font-weight: 400;
  line-height: 1;
  text-transform: capitalize;
  letter-spacing: var(--letterSpacing);
}

h1 {
  font-size: 3.052rem;
}

h2 {
  font-size: 2.441rem;
}

h3 {
  font-size: 1.953rem;
}

h4 {
  font-size: 1.563rem;
}

h5 {
  font-size: 1.25rem;
}

.text {
  margin-bottom: 1.5rem;
  max-width: 40em;
}

small,
.text-small {
  font-size: var(--small-text);
}

a {
  text-decoration: none;
}
ul {
  list-style-type: none;
  padding: 0;
}

.img {
  width: 100%;
  display: block;
  object-fit: cover;
}
/* buttons */

.btn {
  cursor: pointer;
  color: var(--white);
  background: var(--primary-500);
  border: transparent;
  border-radius: var(--borderRadius);
  letter-spacing: var(--letterSpacing);
  padding: 0.375rem 0.75rem;
  box-shadow: var(--shadow-1);
  transition: var(--transition);
  text-transform: capitalize;
  display: inline-block;
}
.btn:hover {
  background: var(--primary-700);
  box-shadow: var(--shadow-3);
}
.btn-hipster {
  color: var(--primary-500);
  background: var(--primary-200);
}
.btn-hipster:hover {
  color: var(--primary-200);
  background: var(--primary-700);
}
.btn-block {
  width: 100%;
}

/* alerts */
.alert {
  padding: 0.375rem 0.75rem;
  margin-bottom: 1rem;
  border-color: transparent;
  border-radius: var(--borderRadius);
}

.alert-danger {
  color: var(--red-dark);
  background: var(--red-light);
}
.alert-success {
  color: var(--green-dark);
  background: var(--green-light);
}
/* form */

.form {
  width: 90vw;
  max-width: var(--fixed-width);
  background: var(--white);
  border-radius: var(--borderRadius);
  box-shadow: var(--shadow-2);
  padding: 2rem 2.5rem;
  margin: 3rem auto;
}
.form-label {
  display: block;
  font-size: var(--small-text);
  margin-bottom: 0.5rem;
  text-transform: capitalize;
  letter-spacing: var(--letterSpacing);
}
.form-input,
.form-textarea {
  width: 100%;
  padding: 0.375rem 0.75rem;
  border-radius: var(--borderRadius);
  background: var(--backgroundColor);
  border: 1px solid var(--grey-200);
}

.form-row {
  margin-bottom: 1rem;
}

.form-textarea {
  height: 7rem;
}
::placeholder {
  font-family: inherit;
  color: var(--grey-400);
}
.form-alert {
  color: var(--red-dark);
  letter-spacing: var(--letterSpacing);
  text-transform: capitalize;
}
/* alert */

@keyframes spinner {
  to {
    transform: rotate(360deg);
  }
}

.loading {
  width: 6rem;
  height: 6rem;
  border: 5px solid var(--grey-400);
  border-radius: 50%;
  border-top-color: var(--primary-500);
  animation: spinner 0.6s linear infinite;
  margin: 0 auto;
}

/* title */

.title {
  text-align: center;
}

.title-underline {
  background: var(--primary-500);
  width: 7rem;
  height: 0.25rem;
  margin: 0 auto;
  margin-top: 1rem;
}

/* ============= PROJECT CSS =============== */

/* optional overwrite */

body {
  background: var(--primary-100);
}

/* * {
  border: 2px solid red;
} */

/* parent container of screen size */
main {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* child container */
.container {
  /* border: 2px solid red; */
  width: 90vw;
  max-width: var(--fixed-width);
  margin: 5rem 0;
  background: var(--white);
  border-radius: var(--borderRadius);
  padding: 1.5rem 2rem;
  box-shadow: var(--shadow-1);
}
.container h3 {
  margin-bottom: 2rem;
}

/* person component  */
.person {
  display: grid;
  /* set 2 column */
  grid-template-columns: auto 1fr;
  column-gap: 0.75rem;
  margin-bottom: 1.5rem;
  align-items: center;
}

/* set image size small, round, with shadow */
.person img {
  width: 75px;
  height: 75px;
  border-radius: 50%;
  box-shadow: var(--shadow-3);
}
.person h4 {
  font-weight: 500;
  margin-bottom: 0.5rem;
}
.person p {
  color: var(--grey-500);
}
```

<br>
