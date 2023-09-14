#### 195. [Menu - Setup](#195)

#### 196. [Menu - Title Component](#196)

#### 197. [Menu - Render Items](#197)

#### 198. [Menu - Unique Categories](#198)

#### 199. [Menu - Display Categories](#199)

#### 200. [Menu - Filter Items](#200)

#### 201. [Menu - CSS (Optional)](#201)

<br>

---

### 195. Menu - Setup<a id="195"></a>

> **_Business Objective: Layout_**

<img src="notes/app.png" width="500">

- [Live App](https://react-vite-projects-5-menu.netlify.app/)

---

##### Figma URL

[Menu](https://www.figma.com/file/PwlnSJXCuo4qD2o6EJiuj9/Menu?node-id=0%3A1&t=oaKVwYVqc9Oon2Ts-1)

- install deps

```sh
npm install
```

- spin up dev server

```sh
npm run dev
```

<br>

### 196. Menu - Title Component<a id="196"></a>

##### Steps

#### Title Component

First, you need to create a Title component to display the main title of your app. This component can be a simple function that returns a heading element with the app title.

---

- In src folder create Title.jsx

```js
const Title = ({ text }) => {
  return (
    <div className="title">
      <h2>{text}</h2>
      <div className="title-underline"></div>
    </div>
  );
};
export default Title;
```

---

- In src/App.jsx

```js
import React, { useState } from "react";

import Title from "./Title";

function App() {
  return (
    <main>
      <section className="menu">
        <Title text="our menu" />
      </section>
    </main>
  );
}

export default App;
```

<br>

### 197. Menu - Render Items<a id="197"></a>

#### Explore and Import Data

Import the menu items data from data.js into your project. This data should be an array of objects, with each object representing a menu item and containing properties such as title, price, image URL, and description.

#### State Value

Set up the menu items data as a state variable in the App.jsx component using the useState hook. This will allow you to modify the data and have those changes automatically reflected in the rendered output.

#### Render Items

Pass the menu items state value down to the Menu.jsx component. In the Menu component, iterate over the list of menu items using the map method, and for every item, render a MenuItem component.

In the MenuItem component, render an image element, a title, a price, and a description. You can use the data from the menu items array to fill in the information for each component.

---

- In src folder create Menu.jsx -rafce, for iterating list

```js
import React from "react";
import MenuItem from "./MenuItem";

const Menu = ({ items }) => {
  return (
    <div className="section-center">
      {items.map((menuItem) => {
        return <MenuItem key={menuItem.id} {...menuItem} />;
      })}
    </div>
  );
};

export default Menu;
```

---

- In src/MenuItem.jsx -rafce, for single template

```js
const MenuItem = ({ img, title, price, desc }) => {
  return (
    <article className="menu-item">
      <img src={img} alt={title} className="img" />
      <div className="item-info">
        <header>
          <h5>{title}</h5>
          <span className="item-price">${price}</span>
        </header>
        <p className="item-text">{desc}</p>
      </div>
    </article>
  );
};
export default MenuItem;
```

---

- In src/App.jsx

```js
import React, { useState } from "react";
import Menu from "./Menu";
import Title from "./Title";
import items from "./data";

function App() {
  const [menuItems, setMenuItems] = useState(items);

  return (
    <main>
      <section className="menu">
        <Title text="our menu" />
        <Menu items={menuItems} />
      </section>
    </main>
  );
}

export default App;
```

<br>

### 198. Menu - Unique Categories<a id="198"></a>

#### Unique Categories

In the App.jsx component, set up functionality to get only the unique categories from the menu items data and store them in a separate array. Add an "all" category to this array to display all menu items.
Hint : new Set ()
You can find more info on Set Object below after all steps.

---

- In src/App/jsx

```js
import React, { useState } from "react";
import Menu from "./Menu";
import Title from "./Title";
import items from "./data";
const allCategories = ["all", ...new Set(items.map((item) => item.category))];

function App() {
  const [menuItems, setMenuItems] = useState(items);
  const [categories, setCategories] = useState(allCategories);

  return (
    <main>
      <section className="menu">
        <Title text="our menu" />
        <Menu items={menuItems} />
      </section>
    </main>
  );
}

export default App;
```

<br>

### 199. Menu - Display Categories<a id="199"></a>

#### State Value and Render Categories

Set up the categories array as a state variable in the App.jsx component using the useState hook. This will allow you to modify the data and have those changes automatically reflected in the rendered output.

Create a Categories component and pass the categories state value down to this component. In the Categories component, iterate over the categories array and render buttons for each category.

- In src folder create Categories.jsx

```js
import React from "react";

const Categories = ({ categories }) => {
  return (
    <div className="btn-container">
      {categories.map((category) => {
        return (
          <button type="button" className="btn" key={category}>
            {category}
          </button>
        );
      })}
    </div>
  );
};

export default Categories;
```

---

- In src/App.jsx

```js
import React, { useState } from "react";
import Menu from "./Menu";
import Categories from "./Categories";
import Title from "./Title";
import items from "./data";

const allCategories = ["all", ...new Set(items.map((item) => item.category))];

function App() {
  const [menuItems, setMenuItems] = useState(items);
  const [categories, setCategories] = useState(allCategories);

  return (
    <main>
      <section className="menu">
        <Title text="our menu" />
        <Categories categories={categories} />
        <Menu items={menuItems} />
      </section>
    </main>
  );
}

export default App;
```

<br>

### 200. Menu - Filter Items<a id="200"></a>

#### Filter Functionality

Set up filter functionality where once the user clicks on the button, only the menu items that belong to the selected category are displayed. To do this, define a function that takes a category as a parameter and updates the state to show only the menu items that belong to that category. You can then pass this function down to the Categories component as a prop, and attach it to the buttons.

When the user clicks on a category button, the filter function should be called with the selected category as a parameter. The function should then update the state to show only the menu items that belong to the selected category.

Overall, the flow of the application should look something like this:

- Create a Title component to display the app title.
- Import the menu items data from data.js into your project.
- Set up the menu items data as a state variable in the App.jsx component.
- Pass the menu items state value down to the Menu.jsx component and render a MenuItem component for each item in the menu items array.
- In the MenuItem component, display the image, title, price, and description.
- Set up functionality to get only the unique categories from the menu items data and store them in a separate array, including an "all" category to display all menu items.
- Set up the categories array as a state variable in the App.jsx component.
- Create a Categories component and render a button for each category in the categories array.
- Define a function that takes a category as a parameter and updates the state to show only the menu items that belong to that category.
- Attach the filter function to the category buttons in the Categories component.
- Repeat steps 9-10 until the user has selected a different category or chooses to exit the Menu component.

---

- In src/Categories

```js
import React from "react";

const Categories = ({ categories, filterItems }) => {
  return (
    <div className="btn-container">
      {categories.map((category) => {
        return (
          <button
            type="button"
            className="btn"
            key={category}
            onClick={() => filterItems(category)}
          >
            {category}
          </button>
        );
      })}
    </div>
  );
};

export default Categories;
```

---

- In src/App.jsx

```js
import React, { useState } from "react";
import Menu from "./Menu";
import Categories from "./Categories";
import Title from "./Title";
import items from "./data";
const allCategories = ["all", ...new Set(items.map((item) => item.category))];

function App() {
  const [menuItems, setMenuItems] = useState(items);
  const [categories, setCategories] = useState(allCategories);

  const filterItems = (category) => {
    if (category === "all") {
      setMenuItems(items);
      return;
    }
    const newItems = items.filter((item) => item.category === category);
    setMenuItems(newItems);
  };

  return (
    <main>
      <section className="menu">
        <Title text="our menu" />
        <Categories categories={categories} filterItems={filterItems} />
        <Menu items={menuItems} />
      </section>
    </main>
  );
}

export default App;
```

<br>

### 201. Menu - CSS (Optional)<a id="201"></a>

- src/index.css

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
  --primary-100: #fef3c7;
  --primary-200: #fde68a;
  --primary-300: #fcd34d;
  --primary-400: #fbbf24;
  --primary-500: #f59e0b;
  --primary-600: #d97706;
  --primary-700: #b45309;
  --primary-800: #92400e;
  --primary-900: #78350f;

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

.menu {
  padding: 5rem 0;
}

.btn-container {
  margin: 2rem 0 4rem 0;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 1rem;
}
.section-center {
  width: 90vw;
  margin: 0 auto;
  max-width: var(--max-width);
  display: grid;
  gap: 2rem;
}

.menu-item {
  background: var(--white);
  border-radius: var(--borderRadius);
}
.menu-item .img {
  height: 15rem;
  border-top-right-radius: var(--borderRadius);
  border-top-left-radius: var(--borderRadius);
}
.item-info {
  padding: 1.5rem;
}
.item-info header {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 1.25rem;
}

.item-info h5 {
  font-weight: 500;
}
.item-price {
  background: var(--primary-500);
  color: var(--white);
  padding: 0.25rem 0.5rem;
  letter-spacing: var(--letterSpacing);
  border-radius: var(--borderRadius);
}

.item-text {
  line-height: 2;
  color: var(--grey-500);
}

.section-center {
  justify-items: center;
}
.menu-item {
  max-width: 25rem;
}

@media screen and (min-width: 992px) {
  .section-center {
    grid-template-columns: 1fr 1fr;
    align-items: start;
  }
}
@media screen and (min-width: 1170px) {
  .section-center {
    width: 95vw;
    grid-template-columns: repeat(3, 1fr);
  }
}
```

<br>

---

### Ref. Set Object

[JS Nuggets - new Set()](https://www.youtube.com/watch?v=H4NnCItCZWE&list=PLnHJACx3NwAfRUcuKaYhZ6T5NRIpzgNGJ&index=26)

In JavaScript, the Set object is a collection of unique values. It allows you to store values of any type, such as primitive types (numbers, strings, booleans) and object references.

Here's a simple example of using a Set:

```js
// Create a new set
let mySet = new Set();

// Add values to the set
mySet.add(1);
mySet.add(2);
mySet.add(3);

// Add a duplicate value (ignored)
mySet.add(1);

// Get the size of the set (3)
console.log(mySet.size);

// Check if a value is in the set (true)
console.log(mySet.has(2));

// Remove a value from the set
mySet.delete(2);

// Get an array of all values in the set
let myArray = Array.from(mySet);
console.log(myArray); // [1, 3]
```

```js
const tempCategories = menu.map((item) => item.category);
const tempSet = new Set(tempCategories);
const tempItems = ["all", ...tempSet];
console.log(tempItems);
```
