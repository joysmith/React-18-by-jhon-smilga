#### 14. [Intro](#14)

#### 15. [Github Repository](#15)

#### 16. [Folder Structure](#16)

#### 17. [Remove Boilerplate](#17)

#### 18. [First Component](#18)

#### 19. [Extensions and Settings](#19)

#### 20. [Create Element Function](#20)

#### 21. [JSX Rules](#21)

#### 22. [Nest Components](#22)

#### 23. [React Developer Tools](#23)

#### 24. [BookList](#24)

#### 25. [CSS](#25)

#### 26. [Local Images (public folder)](#26)

#### 27. [JSX - CSS](#27)

#### 28. [JSX - Javascript](#28)

#### 29. [Props - Basic Setup](#29)

#### 30. [Props - Somewhat Dynamic Setup](#30)

#### 31. [Props - Multiple Approaches](#31)

#### 32. [Children Prop](#32)

#### 33. [Simple List](#33)

#### 34. [Proper List](#34)

#### 35. [Key Prop](#35)

#### 36. [Object as a Prop](#36)

#### 37. [Event Basics](#37)

#### 38. [Form Submission](#38)

#### 39. [Form Submission - Button Example](#39)

#### 40. [Anonymous Function (arrow)](#40)

#### 41. [Components Feature](#41)

#### 42. [Prop Drilling](#42)

#### 43. [Complex Example - Intro](#43)

#### 44. [Complex Example - Bug](#44)

#### 45. [Complex Example - Fix](#45)

#### 46. [ES6 Modules](#46)

#### 47. [Local Images (src folder)](#47)

#### 48. [Numbers Challenge](#48)

#### 49. [Title Challenge](#49)

#### 50. [Build Folder](#50)

#### 51. [Deployment](#51)

#### 73. [VITE - Intro](#73)

#### 74. [VITE - Install / Setup](#74)

<br>

---

### 14. Intro<a id="14"> </a>

<br>

### 15. Github Repository<a id="15"> </a>

<br>

### 16. Folder Structure<a id="16"> </a>

- In 01-fundamental install dependency and run dev server

```sh
npm install
npm start
```

---

- node_modules
  Contains all dependencies required by the app. Main dependencies also listed in package.json

- public
  Contains static assets including index.html (page template)

  - index.html
    - title
    - fonts
    - css
    - favicon
    - id="root" - our entire app

- src
  In simplest form it's the brain of our app. This is where we will do all of our work. src/index.js is the JavaScript entry point.
- .gitignore
  Specifies which files source control (Git) should ignore

- package.json
  Every Node.js project has a package.json and it contains info about our project, for example list of dependencies and scripts

- package-lock.json
  A snapshot of the entire dependency tree

- README
  The markdown file where you can share more info about the project for example build instructions and summary

- zoom 175%

<br>

### 17. Remove Boilerplate<a id="17"> </a>

- remove src folder
- create src folder

  - create index.js inside src

- toggle sidebar CMD + B
- shortcuts settings/keyboard shortcuts

<br>

### 18. First Component<a id="18"> </a>

> **_NOTE: Every time you need to create a component, think like I need to create function that return html/jsx_**

```js
function Greeting() {
  return <h2>My First Component</h2>;
}

// arrow function also works

const Greeting = () => {
  return <h2>My First Component</h2>;
};
```

- starts component name with capital letter
- must return JSX (html)
- always close tag <Greeting/>

---

##### Typical Component

```js
// imports or logic

const Greeting = () => {
  return <h2>My First Component</h2>;
};
export default Greeting;
```

---

##### Root Component (only one)

- In src/index.js

```js
import React from "react";
import ReactDOM from "react-dom/client";

function Greeting() {
  return <h2>My First Component</h2>;
}

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(<Greeting />);
```

- go to "http://localhost:3000/"

  <br>

### 19. Extensions and Settings<a id="19"> </a>

- Auto Rename Tag
- Highlight Matching Tag
  - customize in settings.json
- Prettier
  - format on save
  - format on paste
  - Default Formatter (Prettier - Code formatter)

settings.json

```json
  "editor.formatOnPaste": true,
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
    "prettier.singleQuote": true,
    "prettier.semi": false,
```

- Emmet

settings.json

```json
"emmet.includeLanguages": {
    "javascript": "javascriptreact"
  },
```

- ES7 Snippets
  - rafce (arrow func with export)
  - rfce (regular func with export )
  - same as the file name
  - react auto import
    - Setting > React Snippets > Settings: Import React On Top
    - uncheck it, no loger need to import react, after version 17

<br>

### 20. Create Element Function<a id="20"> </a>

#### rules

- capital letter
- must return something
- JSX syntax (return html)
  - to make our lives easier
  - calling function under the hood

---

- In src/index.js

```js
function Greeting() {
  return (
    <div>
      <h2>hello world</h2>
    </div>
  );
}

const Greeting = () => {
  return React.createElement(
    "div",
    {},
    React.createElement("h2", {}, "hello world")
  );
};
```

<br>

### 21. JSX Rules (stuff that we are returning)<a id="21"> </a>

- return single element (one parent element)

  - semantics section/article
  - Fragment - let's us group elements without adding extra nodes

```js
return <React.Fragment>...rest of the return</React.Fragment>;

// shorthand for React.Fragment

return <>...rest of the return</>;
```

---

- camelCase property naming convention

```js
return (
  <div tabIndex={1}>
    <button onClick={myFunction}>click me</button>
    <label htmlFor='name'>Name</label>
    <input readOnly={true} id='name' />
  </div>
)

// in html
<div tabindex="1">
    <button onclick="myFunction()">click me</button>
    <label for='name'>Name</label>
    <input readonly id='name' />
</div>
```

- className instead of class

```js
return <div className="someValue">hello</div>;
```

---

- close every element

```js
return <img />;
// or
return <input />;
```

---

- formatting
  - opening tag in the same line as return or ()

```js
function Greeting() {
  return (
    <>
      <div className="someValue">
        <h3>hello people</h3>
        <ul>
          <li>
            <a href="#">hello world</a>
          </li>
        </ul>
      </div>
      <h2>hello world</h2>
      <input type="text" name="" id="" />
    </>
  );
}
```

<br>

### 22. Nest Components<a id="22"> </a>

- In src/index.js

```js
function Greeting() {
  return (
    <div>
      <Person />
      <Message />
    </div>
  );
}

const Person = () => <h2>john doe</h2>;
const Message = () => {
  return <p>this is my message</p>;
};
```

<br>

### 23. React Developer Tools<a id="23"> </a>

- top right corner
- more tools/extensions
- open chrome web store "react developer tool" install
- open dev tool > components

<br>

### 24. BookList: Amazon Best seller Books<a id="24"> </a>

- In src/index.js, setup structure

```js
import React from "react";
import ReactDOM from "react-dom/client";

function BookList() {
  return (
    <section>
      <Book />
      <Book />
      <Book />
      <Book />
    </section>
  );
}

const Book = () => {
  return (
    <article>
      <Image />
      <Title />
      <Author />
    </article>
  );
};

const Image = () => <h2>image placeholder</h2>;

const Title = () => {
  return <h2>Book Title</h2>;
};

const Author = () => <h4>Author</h4>;

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(<BookList />);
```

---

- in search engine type - 'amazon best selling books'
  [Amazon Best Sellers](https://www.amazon.com/Best-Sellers-Books/zgbs/books/)
- DON'T NEED TO BUY ANYTHING !!!
- NOT AN AFFILIATE LINK !!!!
- choose a book
- copy image, title and author

- In src/index.js, provide value to Image, Title, Author component

```js
import React from "react";
import ReactDOM from "react-dom/client";

function BookList() {
  return (
    <section>
      <Book />
      <Book />
      <Book />
      <Book />
    </section>
  );
}

const Book = () => {
  return (
    <article className="book">
      <Image />
      <Title />
      <Author />
    </article>
  );
};

const Image = () => (
  <img
    src="https://images-na.ssl-images-amazon.com/images/I/71m+Qtq+HrL._AC_UL900_SR900,600_.jpg"
    alt="Interesting Facts For Curious Minds"
  />
);

const Title = () => {
  return <h2>Interesting Facts For Curious Minds</h2>;
};

const Author = () => <h4>Jordan Moore </h4>;

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(<BookList />);
```

<br>

### 25. CSS<a id="25"> </a>

- In src-folder create index.css

```css
/* default setup universal selector */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  background: #f1f5f8;
  color: #222;
}
```

- In src/index.js, import css file with file extension and add classes

```js
// import style
import "./index.css";

function BookList() {
  return (
    <section className="booklist">
      <Book />
      <Book />
      <Book />
      <Book />
    </section>
  );
}

const Book = () => {
  return (
    <article className="book">
      <Image />
      <Title />
      <Author />
    </article>
  );
};
```

---

- In src/index.css, complete css

```css
.booklist {
  width: 90vw;
  max-width: 1170px;
  margin: 5rem auto;
  display: grid;
  gap: 2rem;
}

@media screen and (min-width: 768px) {
  .booklist {
    grid-template-columns: repeat(3, 1fr);
  }
}
.book {
  background: #fff;
  border-radius: 1rem;
  padding: 2rem;
  text-align: center;
}
.book img {
  width: 100%;
  object-fit: cover;
}
.book h2 {
  margin-top: 1rem;
  font-size: 1rem;
}
```

<br>

### 26. Local Images (public folder)<a id="26"> </a>

> **_Three ways to import images in our project_**

- 1 external images (hosted on different server) - just need an url
- 2 local images (public folder) - less performant
- 3 local images (src folder) - better solution for assets,
  since under the hood they get optimized.

- download image from internet, save image (Save Image As....)
- create images folder in public
- copy/paste image
- rename image (optional)
- replace url in the src - './images/imageName.extension'
- './' because assets are on the same server

```js
const Image = () => (
  <img src="./images/book-1.jpg" alt="Interesting Facts For Curious Minds" />
);
```

- whatever assets we place in public - instantly available
- go to "domain(localhost)/asset"

<br>

### 27. JSX - CSS<a id="27"> </a>

- In src/index.js, look for Author component, then
- use "style" prop
- {} in JSX means going back to JS Land
- value is an object with key/value pairs - capitalized and with ''

```js
const Author = () => (
  <h4 style={{ color: "#617d98", fontSize: "0.75rem", marginTop: "0.5rem" }}>
    Jordan Moore
  </h4>
);
```

---

- css rules still apply (inline vs external css)

```css
.book h4 {
  /* won't work */
  color: red;
  /* will work */
  letter-spacing: 2px;
}
```

---

> **_external libraries use inline css, so if you want to make some changes, reference the library docs and elements tab_**

- alternative option to write inline css style
- NOTE: we can create css inline js-object inside/outside the component, and pass the reference in JSX return

```js
const Author = () => {
  const inlineHeadingStyles = {
    color: "#617d98",
    fontSize: "0.75rem",
    marginTop: "0.5rem",
  };
  return <h4 style={inlineHeadingStyles}>Jordan Moore </h4>;
};
```

- FOR THE MOST PART, MULTIPLE APPROACHES AVAILABLE !!!
- AS LONG AS THE RESULT IS THE SAME, REALLY COMES DOWN TO PREFERENCE !!!!

<br>

### 28. JSX - Javascript<a id="28"> </a>

- In src/index.js
  - refactor to single book component (personal preference)
  - remove inline css

```js
const Book = () => {
  return (
    <article className="book">
      <img
        src="./images/book-1.jpg"
        alt="Interesting Facts For Curious Minds"
      />
      <h2>Interesting Facts For Curious Minds</h2>
      <h4>Jordan Moore </h4>
    </article>
  );
};
```

---

- In src/index.css, move inline code there

```css
.book h4 {
  color: #617d98;
  font-size: 0.75rem;
  margin-top: 0.5rem;
  letter-spacing: 2px;
}
```

- {} in JSX means going back to JS Land
- value inside must be an expression (return value),
  can't be a statement

- In src/index.js

```js
// author outside the component
const author = "Jordan Moore";

const Book = () => {
  // title inside the component
  const title = "Interesting Facts For Curious Mindssssss";

  return (
    <article className="book">
      <img
        src="./images/book-1.jpg"
        alt="Interesting Facts For Curious Minds"
      />

      {/* reference title */}
      <h2>{title}</h2>

      {/* reference author */}
      <h4>{author.toUpperCase()} </h4>

      {/* This is a statement ⬇️ */}
      {/* <p>{let x = 6}</p> */}

      <p>{6 + 6}</p>
    </article>
  );
};
```

- toggle line comment Edit/Toggle Line Comment

<br>

### 29. Props - Basic Setup<a id="29"> </a>

- In src/index.js
  - refactor/clean up

```js
const author = "Jordan Moore";
const title = "Interesting Facts For Curious Minds";
const img = "./images/book-1.jpg";

function BookList() {
  return (
    <section className="booklist">
      <Book />
      <Book />
    </section>
  );
}

const Book = () => {
  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>
      <h4>{author} </h4>
    </article>
  );
};
```

---

- function with input, only for reference

```js
// parameters
const someFunc = (param1, param2) => {
  console.log(param1, param2);
};
// arguments
someFunc("job", "developer");
```

---

- function with props, only for reference

```js
const Book = (props) => {
  console.log(props);
  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>
      <h4>{author} </h4>
      {console.log(props)}
    </article>
  );
};
```

- props object, convention to call props, 'shakeAndBake' is an excellent alternative

- pass as key/value pairs
- if the prop exists it will return value, otherwise no value

---

- In src/index.js, setup props in Book component

```js
function BookList() {
  // passing props
  return (
    <section className="booklist">
      <Book job="developer" />
      <Book title="random title" number={22} />
    </section>
  );
}

// props setup
const Book = (props) => {
  console.log(props);
  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>
      <h4>{author} </h4>
      <p>{props.job}</p>
      <p>{props.title}</p>
      <p>{props.number}</p>
    </article>
  );
};
```

---

- In src/index.js, provide actual value

```js
const author = "Jordan Moore";
const title = "Interesting Facts For Curious Minds";
const img = "./images/book-1.jpg";

function BookList() {
  return (
    <section className="booklist">
      <Book author={author} title={title} img={img} />
      <Book title={title} img={img} />
    </section>
  );
}

const Book = (props) => {
  console.log(props);
  return (
    <article className="book">
      <img src={props.img} alt={props.title} />
      <h2>{props.title}</h2>
      <h4>{props.author} </h4>
    </article>
  );
};
```

<br>

### 30. Props - Somewhat Dynamic Setup<a id="30"> </a>

- In src/index.js
  - create book object, and setup with properties
  - refactor hardcoded variables to properties in object
  - copy/paste and rename
  - get values for second book
  - setup props

```js
const firstBook = {
  author: "Jordan Moore",
  title: "Interesting Facts For Curious Minds",
  img: "./images/book-1.jpg",
};

const secondBook = {
  author: "James Clear",
  title: "Atomic Habits",
  img: "https://images-na.ssl-images-amazon.com/images/I/81wgcld4wxL._AC_UL900_SR900,600_.jpg",
};

function BookList() {
  // accessing book obj
  return (
    <section className="booklist">
      <Book
        author={firstBook.author}
        title={firstBook.title}
        img={firstBook.img}
      />

      <Book
        author={secondBook.author}
        title={secondBook.title}
        img={secondBook.img}
      />
    </section>
  );
}

const Book = (props) => {
  console.log(props);
  return (
    <article className="book">
      <img src={props.img} alt={props.title} />
      <h2>{props.title}</h2>
      <h4>{props.author} </h4>
    </article>
  );
};
```

<br>

### 31. Props - Multiple Approaches<a id="31"> </a>

- there is no right or wrong - again preference !!!

- Destructuring (object)
  [JS Nuggets - Destructuring (object)](https://www.youtube.com/watch?v=i4vhNKihfto&list=PLnHJACx3NwAfRUcuKaYhZ6T5NRIpzgNGJ&index=8&t=1s)

- destructuring in Vanilla JS
- saves time/typing
- pull out the properties
- don't need to reference object anymore

- ref

```js
const someObject = {
  name: "john",
  job: "developer",
  location: "florida",
};

console.log(someObject.name);
const { name, job } = someObject;
console.log(job);
```

- no need for all the props.propName
- destructure inside component

---

- Ref. Approach 1: destructure props outside fuction signature

```js
const Book = (props) => {
  // destructure props
  const { img, title, author } = props;
  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>
      <h4>{author} </h4>
    </article>
  );
};
```

---

- Ref. Approach 2: destructure inside function signature
- destructure in function parameters (in our case props)
- if you have console.log(props) - it won't be defined

```js
const Book = ({ img, title, author }) => {
  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>
      <h4>{author} </h4>
    </article>
  );
};
```

<br>

### 32. Children Prop<a id="32"> </a>

- everything we render between component tags
- during the course we will mostly use it Context API
- special prop, has to be "children"
- can place anywhere in JSX
- In src/index.js

```js
function BookList() {
  return (
    <section className="booklist">
      <Book
        author={firstBook.author}
        title={firstBook.title}
        img={firstBook.img}
      >
        {/* How to pass children props */}
        <p>
          Lorem ipsum dolor, sit amet consectetur adipisicing elit. Itaque
          repudiandae inventore eos qui animi sed iusto alias eius ea sapiente.
        </p>
        <button>click me</button>
      </Book>

      <Book
        author={secondBook.author}
        title={secondBook.title}
        img={secondBook.img}
      />
    </section>
  );
}

const Book = ({ img, title, author, children }) => {
  // rest of the logic
};
const Book = (props) => {
  const { img, title, author, children } = props;
  console.log(props);
  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>
      <h4>{author} </h4>

      {/* access children props */}
      {children}
    </article>
  );
};
```

---

- optional

```css
@media screen and (min-width: 768px) {
  .booklist {
    grid-template-columns: repeat(3, 1fr);
    /* Strech card depending on card content */
    align-items: start;
  }
}
.book p {
  margin: 1rem 0 0.5rem;
}
```

<br>

### 33. Simple List<a id="33"> </a>

- [Javascript Nuggets - Map ](https://www.youtube.com/watch?v=80KX6aD9R7M&list=PLnHJACx3NwAfRUcuKaYhZ6T5NRIpzgNGJ&index=1)

- In src/index.js
  - refactor

```js
const books = [
  {
    author: "Jordan Moore",
    title: "Interesting Facts For Curious Minds",
    img: "./images/book-1.jpg",
  },
  {
    author: "James Clear",
    title: "Atomic Habits",
    img: "https://images-na.ssl-images-amazon.com/images/I/81wgcld4wxL._AC_UL900_SR900,600_.jpg",
  },
];

function BookList() {
  return <section className="booklist"></section>;
}

const Book = (props) => {
  const { img, title, author } = props;

  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>
      <h4>{author} </h4>
    </article>
  );
};
```

- can't render objects in React

```js
function BookList() {
  return <section className="booklist">{books}</section>;
}
```

---

- ref map method - creates a new array from calling a function for every array element.

```js
const names = ["john", "peter", "susan"];

const newNames = names.map((name) => {
  console.log(name);
  return <h1>{name}</h1>;
});

function BookList() {
  return <section className="booklist">{newNames}</section>;
}
```

<br>

### 34. Proper List<a id="34"> </a>

- In src/index.js
  - remove names and newNames

```js
function BookList() {
  return (
    <section className="booklist">
      {books.map((book) => {
        console.log(book);

        // return 'hello';
        return (
          <div>
            <h2>{book.title}</h2>
          </div>
        );
      })}
    </section>
  );
}
```

- render component
- pass properties one by one

```js
function BookList() {
  return (
    <section className="booklist">
      {books.map((book) => {
        console.log(book);
        const { img, title, author } = book;
        return <Book img={img} title={title} author={author} />;
      })}
    </section>
  );
}
```

<br>

### 35. Key Prop<a id="35"> </a>

- typically it's going to be id

```js
const books = [
  {
    author: "Jordan Moore",
    title: "Interesting Facts For Curious Minds",
    img: "./images/book-1.jpg",
    id: 1,
  },
  {
    author: "James Clear",
    title: "Atomic Habits",
    img: "https://images-na.ssl-images-amazon.com/images/I/81wgcld4wxL._AC_UL900_SR900,600_.jpg",
    id: 2,
  },
];

function BookList() {
  return (
    <section className="booklist">
      {books.map((book) => {
        console.log(book);
        const { img, title, author, id } = book;
        return <Book book={book} key={id} />;
      })}
    </section>
  );
}
```

- you will see index,but it's not advised if the list is changing

```js
function BookList() {
  return (
    <section className="booklist">
      {books.map((book, index) => {
        console.log(book);
        const { img, title, author, id } = book;
        return <Book book={book} key={index} />;
      })}
    </section>
  );
}
```

<br>

### 36. Object as a Prop<a id="36"> </a>

<br>

### 37. Event Basics<a id="37"> </a>

- Vanilla JS setup

```js
const btn = document.getElementById("btn");

btn.addEventListener("click", function (e) {
  // access event object
  // do something when event fires
});
```

---

- similar approach
- element, event, callback-function
- again camelCase

```js
const EventExamples = () => {
  // 3. callback function
  const handleButtonClick = () => {
    alert("handle button click");
  };

  return (
    <section>
      {/* 1. button element,  2. event onCLick  */}
      <button onClick={handleButtonClick}>click me</button>
    </section>
  );
};
```

- [React Events](https://reactjs.org/docs/events.html)
- no need to memorize them(idea is the same)
- most common
  - onClick (click events)
  - onSubmit (submit form )
  - onChange (input change )

---

- In src/index.js, example

```js
function BookList() {
  return (
    <section className="booklist">
      <EventExamples />
      {books.map((book) => {
        return <Book {...book} key={book.id} />;
      })}
    </section>
  );
}

const EventExamples = () => {
  //3. reference callback function
  const handleFormInput = () => {
    console.log("handle form input");
  };
  //3. reference callback function
  const handleButtonClick = () => {
    alert("handle button click");
  };

  return (
    <section>
      <form>
        <h2>Typical Form</h2>
        {/* 1. input element,  2. event onChange  */}
        <input
          type="text"
          name="example"
          onChange={handleFormInput}
          style={{ margin: "1rem 0" }}
        />
      </form>

      {/* 1. button element,  2. event onCLick  */}
      <button onClick={handleButtonClick}>click me</button>
    </section>
  );
};
```

<br>

### 38. Form Submission<a id="38"> </a>

- The giant event object
- In src/index.js

```js
const EventExamples = () => {
  const handleFormInput = (e) => {
    console.log(e);
    // e.target - element
    console.log(`Input Name : ${e.target.name}`); // key
    console.log(`Input Value : ${e.target.value}`); //user entery value
    // console.log('handle form input');
  };

  const handleButtonClick = () => {
    alert("handle button click");
  };

  const handleFormSubmission = (e) => {
    e.preventDefault();
    console.log("form submitted");
  };

  return (
    <section>
      {/* add onSubmit Event Handler */}
      <form onSubmit={handleFormSubmission}>
        <h2>Typical Form</h2>
        <input
          type="text"
          name="example"
          onChange={handleFormInput}
          style={{ margin: "1rem 0" }}
        />
        {/* add button with type='submit' */}
        <button type="submit">submit form</button>
      </form>
      <button onClick={handleButtonClick}>click me</button>
    </section>
  );
};
```

<br>

### 39. Form Submission - Button Example<a id="39"> </a>

- alternative approach

```js
<button type="submit" onClick={handleFormSubmission}>
  submit form
</button>
```

<br>

### 40. Anonymous Function (arrow)<a id="40"> </a>

#### Mind Grenade

- alternative approach
- pass anonymous function (in this case arrow function) directly
- one liner - less code

```js
const EventExamples = () => {
  return (
    <section>
      {/* passing arrow function directly to onClick event */}
      <button onClick={() => console.log("hello there")}>click me</button>
    </section>
  );
};
```

---

- also can access event object

```js
const EventExamples = () => {
  return (
    <section>
      <form>
        <h2>Typical Form</h2>
        <input
          type="text"
          name="example"
          onChange={(e) => console.log(e.target.value)}
          style={{ margin: "1rem 0" }}
        />
      </form>
      <button onClick={() => console.log("you clicked me")}>click me</button>
    </section>
  );
};
```

<br>

### 41. Components Feature<a id="41"> </a>

#### Mind Grenade #2

- remove EventsExamples
- components are independent by default

```js
function BookList() {
  return (
    <section className="booklist">
      {books.map((book) => {
        return <Book {...book} key={book.id} />;
      })}
    </section>
  );
}

const Book = (props) => {
  const { img, title, author } = props;
  // reference callback function
  const displayTitle = () => {
    console.log(title);
  };

  return (
    <article className="book">
      <img src={img} alt={

      <button onClick={displayTitle}>display title</button>
      <h4>{author} </h4>
    </article>
  );
};
```

<br>

### 42. Prop Drilling<a id="42"> </a>

- remove button

- react data flow - can only pass props down
- alternatives Context API, redux, other state libraries
- In src/index.js

```js
function BookList() {
  const someValue = "shakeAndBake";

  const displayValue = () => {
    console.log(someValue);
  };

  return (
    <section className="booklist">
      {books.map((book) => {
        {
          /* passing displayValue function as props */
        }
        return <Book {...book} key={book.id} displayValue={displayValue} />;
      })}
    </section>
  );
}

const Book = (props) => {
  const { img, title, author, displayValue } = props;

  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>

      {/* passing displayValue function as props */}
      <button onClick={displayValue}>click me</button>
      <h4>{author} </h4>
    </article>
  );
};
```

<br>

### 43. Complex Example - Intro<a id="43"> </a>

- initial setup
- create getBook function in booklist
- accepts id as an argument and finds the book
- [Javascript Nuggets - Filter and Find](https://www.youtube.com/watch?v=KeYxsev737s&list=PLnHJACx3NwAfRUcuKaYhZ6T5NRIpzgNGJ&index=4)
- pass the function down to Book Component and invoke on the button click
- in the Book Component destructure id and function
- invoke the function when user clicks the button, pass the id
- the goal : you should see the same book in the console

```js
const BookList = () => {
  const getBook = (id) => {
    const book = books.find((book) => book.id === id);
    console.log(book);
  };

  return (
    <section className="booklist">
      {books.map((book) => {
        return <Book {...book} key={book.id} getBook={getBook} />;
      })}
    </section>
  );
};

const Book = (props) => {
  const { img, title, author, getBook, id } = props;
  // console.log(props);

  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>
      {/* this is not going to work */}
      <button onClick={getBook(id)}>display title</button>
      <h4>{author}</h4>
    </article>
  );
};
```

<br>

### 44. Complex Example - Bug<a id="44"> </a>

<br>

### 45. Complex Example - Fix<a id="45"> </a>

- two fixes
- first option - setup wrapper

```js
const Book = (props) => {
  const { img, title, author, getBook, id } = props;
  // console.log(props);
  const getSingleBook = () => {
    getBook(id);
  };
  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>
      <button onClick={getSingleBook}>display title</button>
      <h4>{author}</h4>
    </article>
  );
};
```

- two fixes
- second option - wrap in the anonymous arrow function

```js
const Book = (props) => {
  const { img, title, author, getBook, id } = props;
  // console.log(props);
  const getSingleBook = () => {
    getBook(id);
  };
  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>

      <button onClick={() => getBook(id)}>display title</button>
      <h4>{author}</h4>
    </article>
  );
};
```

<br>

### 46. ES6 Modules<a id="46"> </a>

- In src/index.js remove all getBook code

```js
function BookList() {
  return (
    <section className="booklist">
      {books.map((book) => {
        return <Book {...book} key={book.id} />;
      })}
    </section>
  );
}

const Book = (props) => {
  const { img, title, author } = props;

  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>

      <h4>{author} </h4>
    </article>
  );
};
```

---

- setup two files in src books.js and Book.js
- cut books array i.e our data from index.js, add to books.js

- In src/books.js

```js
const books = [
  {
    author: "Jordan Moore",
    title: "Interesting Facts For Curious Minds",
    img: "./images/book-1.jpg",
    id: 1,
  },
  {
    author: "James Clear",
    title: "Atomic Habits",
    img: "https://images-na.ssl-images-amazon.com/images/I/81wgcld4wxL._AC_UL900_SR900,600_.jpg",
    id: 2,
  },
];
```

---

- two flavors named and default exports

  - with named exports names MUST match
  - with default exports,can rename but only one per file

- use named export

```js
export const books = [
  {
    author: "Jordan Moore",
    title: "Interesting Facts For Curious Minds",
    img: "./images/book-1.jpg",
    id: 1,
  },
  {
    author: "James Clear",
    title: "Atomic Habits",
    img: "https://images-na.ssl-images-amazon.com/images/I/81wgcld4wxL._AC_UL900_SR900,600_.jpg",
    id: 2,
  },
];
```

---

- In src/index.js, import books

```js
import { books } from "./books";
```

---

- Move component from index.js to Book.js
- use default export

```js
const Book = (props) => {
  const { img, title, author } = props;

  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>

      <h4>{author} </h4>
    </article>
  );
};

export default Book;
```

---

- In src/index.js import Book component

```js
import Book from "./Book";
```

<br>

### 47. Local Images (src folder)<a id="47"> </a>

- better performance because optimized
- add one more book to array
- download all three images (rename)
- setup images folder in the src
- import all three images in the books.js one by one
- and yes each image requires new import
- set image property equal to import in each book-obj

- In src/book.js

```js
import img1 from "./images/book-1.jpg";
import img2 from "./images/book-2.jpg";
import img3 from "./images/book-3.jpg";

export const books = [
  {
    author: "Jordan Moore",
    title: "Interesting Facts For Curious Minds",
    img: img1,
    id: 1,
  },
  {
    author: "James Clear",
    title: "Atomic Habits",
    img: img2,
    id: 2,
  },
  {
    author: "Stephen King",
    title: "Fairy Tale",
    img: img3,
    id: 3,
  },
];
```

<br>

### 48. Numbers Challenge<a id="48"> </a>

- setup numbers
- don't worry about css
- hint - index (second parameter in map)

- In src/index.js

```js
const BookList = () => {
  return (
    <section className="booklist">
      {/* passing down number */}
      {books.map((book, index) => {
        return <Book {...book} key={book.id} number={index} />;
      })}
    </section>
  );
};
```

---

- In src/Book.js

```js
const Book = (props) => {
  // destructuring number
  const { img, title, author, number } = props;

  return (
    <article className="book">
      <img src={img} alt={title} />
      <h2>{title}</h2>

      <h4>{author}</h4>
      <span className="number">{`# ${number + 1}`}</span>
    </article>
  );
};
```

---

- In src/index.css

```css
.book {
  background: #fff;
  border-radius: 1rem;
  padding: 2rem;
  text-align: center;
  /* set relative */
  position: relative;
}

.number {
  position: absolute;
  top: 0;
  left: 0;
  font-size: 1rem;
  padding: 0.75rem;
  border-top-left-radius: 1rem;
  border-bottom-right-radius: 1rem;
  background: #c35600;
  color: #fff;
}
```

<br>

### 49. Title Challenge<a id="49"> </a>

- add a title to our app (css optional)
- change page title

- In src/index.js

```js
function BookList() {
  return (
    <>
      <h1>amazon best sellers</h1>
      <section className="booklist">
        {books.map((book) => {
          return <Book {...book} key={book.id} />;
        })}
      </section>
    </>
  );
}
```

---

- In src/index.css

```css
h1 {
  text-align: center;
  margin-top: 4rem;
  text-transform: capitalize;
}
```

---

- In public/index.html, change page title

```html
<title>Best Sellers</title>
```

<br>

### 50. Build Folder<a id="50"> </a>

- stop the dev server "ctrl + c"
- run "npm run build"
- build folder gets created

<br>

### 51. Deployment<a id="51"> </a>

- sign up
- add new site--> deploy manually
- choose build folder from file system
- rename site - site settings/change site name

<br>

### 73. VITE - Intro<a id="73"> </a>

- (Vite)[https://vitejs.dev/]

<br>

### 74. VITE - Install / Setup<a id="74"> </a>

```sh
npm create vite@latest app-name -- --template react
npm install
npm run dev
```

- http://localhost:5173/

#### Vite Setup

- need to use .jsx extension for naming component
- index.html in the source instead of public
- assets still in public
- instead of index.js, need to use main.jsx
- to spin up dev server - "npm run dev"

- rest the same - imports/exports, deployment, assets, etc...
- to build project, then look into dist-folder

```sh
npm run build
```

<br>
