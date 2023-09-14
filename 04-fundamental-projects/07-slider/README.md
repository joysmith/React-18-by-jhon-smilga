#### 209. [Slider - Setup](#209)

#### 210. [Slider - Structure](#210)

#### 211. [Slider - CSS](#211)

#### 212. [Slider - Initial Logic](#212)

#### 213. [Slider - Current Item and Prev/Next](#213)

#### 214. [Slider - Autoslide (autoplay)](#214)

#### 215. [Slider - Library Info](#215)

#### 216. [Slider - React Slick Setup](#216)

#### 217. [Slider - React Slick Complete](#217)

<br>

---

### 209. Slider - Setup<a id="209"></a>

> **_Business Objective: Layout_**

<img src="notes/app.gif" width="500">

- [Live App](https://react-vite-project-7-slider.netlify.app/)

---

#### Figma URL

[Slider](https://www.figma.com/file/QfMzzThSYmgabSvn4t8Yfe/Slider?node-id=0%3A1&t=IpsYjMUn3Xj3Hs3N-1)

- install deps

```sh
npm install
```

- spin up dev server

```sh
npm run dev
```

<br>

### 210. Slider - Structure<a id="210"></a>

##### Steps

#### Explore Data

Explore arrays in data.js

#### Import Data and Set State Value

Create Carousel.jsx, import all arrays from data.js and set up state value using the useState hook, use shortList as default value (for now).

#### Setup Container and Prev/Next Buttons

In the return statement, set up a container element to hold all the slides. Inside the container, iterate over the people state value to create each slide.

Set up prev and next buttons outside the container element. You can use the onClick event to trigger functions that will change the current slide.

---

- In src folder create Carousel.jsx -rafce
- In src/App.jsx,

```js
import Carousel from "./Carousel";
import SlickCarousel from "./SlickCarousel";

const App = () => {
  return (
    <main>
      <Carousel />
      {/* <SlickCarousel /> */}
    </main>
  );
};
export default App;
```

---

- In src Carousel.jsx

```js

```

<br>

### 211. Slider - CSS<a id="211"></a>

<br>

### 212. Slider - Initial Logic<a id="212"></a>

<br>

### 213. Slider - Current Item and Prev/Next<a id="213"></a>

<br>

### 214. Slider - Autoslide (autoplay)<a id="214"></a>

<br>

### 215. Slider - Library Info<a id="215"></a>

<br>

### 216. Slider - React Slick Setup<a id="216"></a>

<br>

### 217. Slider - React Slick Complete<a id="217"></a>

<br>
