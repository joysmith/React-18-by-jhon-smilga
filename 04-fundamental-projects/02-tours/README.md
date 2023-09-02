#### 174. [Tours - Setup](#174)

#### 175. [Tours - Fetch Tours](#175)

#### 176. [Tours - Render Tours](#176)

#### 177. [Tours - Remove Tour](#177)

#### 178. [Tours - Read More](#178)

#### 179. [Tours - Refetch](#179)

#### 180. [Tours - CSS (Optional)](#180)

---

<br>

### 174. Tours - Setup<a id='174'></a>

#### Figma URL

[Tours](https://www.figma.com/file/OnLoM3AzBFaHzSc2iolJS0/Tours?node-id=0%3A1&t=wiRXOlTLN5ehekYI-1)

- install deps

```sh
npm install
```

- spin up dev server

```sh
npm run dev
```

<br>

### 175. Tours - Fetch Tours<a id='175'></a>

#### Setup

First create - three components (Tours, Tour, and Loading), you can create three separate files in your project directory: Tours.jsx, Tour.jsx, and Loading.jsx. In each of these files, you will define a React functional component that returns JSX code for rendering the respective component.

#### Fetch Tours

The Tours component will be responsible for rendering a list of Tour components. In App.jsx, you will fetch the tours data from a URL using the fetch API. Before the data is loaded, you should show a loading spinner or message, which can be implemented using the Loading component.

- In src folder create Tour.jsx -rafce
- In src folder create Tours.jsx -rafce
- In src folder create Loading.jsx -rafce
- In src/App.jsx, setup useState, useEffect, fetchTours fuction to fetch data from url

```js
import React, { useState, useEffect } from "react";

const url = "https://course-api.com/react-tours-project";

const App = () => {
  const [loading, setLoading] = useState(true);
  const [tours, setTours] = useState([]);

  const fetchTours = async () => {
    // will use later
    setLoading(true);
    try {
      const response = await fetch(url);
      // turn http message into json
      const tours = await response.json();
      console.log(tours);
    } catch (error) {
      console.log(error);
    }
  };

  // useEffect func to invoke fetchTours only once
  useEffect(() => {
    fetchTours();
  }, []);

  return <h2>Tours Starter</h2>;
};
export default App;
```

<br>

### 176. Tours - Render Tours<a id='176'></a>

#### Render Tours

Once the data is loaded, you can set the state of your component to store the tours data. You can then map over the tours array and render a Tour component for each tour. Each Tour component will receive the tour data as props, including the tour's id, image, info, name, and price.

---

- In src/App.jsx,

```js
import React, { useState, useEffect } from "react";
import Loading from "./Loading";
import Tours from "./Tours";

const url = "https://course-api.com/react-tours-project";

const App = () => {
  const [loading, setLoading] = useState(true);
  const [tours, setTours] = useState([]);

  const fetchTours = async () => {
    // will use later
    setLoading(true);
    try {
      const response = await fetch(url);
      // turn http message into json
      const tours = await response.json();
      console.log(tours);
    } catch (error) {
      console.log(error);
    }
  };

  // useEffect func to invoke fetchTours only once
  useEffect(() => {
    fetchTours();
  }, []);

  // condition: if data is loading then,
  if (loading) {
    return (
      <main>
        <Loading />
      </main>
    );
  }

  // TODO

  return (
    <main>
      <Tours tours={tours} />
    </main>
  );
};
export default App;
```

---

- In src/Loading.jsx component

```js
import React from "react";

const Loading = () => {
  return <div className="loading"></div>;
};

export default Loading;
```

---

- In src/Tours.jsx, grab the data and iterate over the list

```js
import React from "react";
import Tour from "./Tour";

const Tours = ({ tours, removeTour }) => {
  return (
    <section>
      <div className="title">
        <h2>our tours</h2>
        <div className="title-underline"></div>
      </div>

      <div className="tours">
        {tours.map((tour) => {
          return <Tour key={tour.id} {...tour} />;
        })}
      </div>
    </section>
  );
};

export default Tours;
```

---

- In src/Tour.jsx,

```js
import React, { useState } from "react";

const Tour = ({ id, image, info, name, price }) => {
  return (
    <article className="single-tour">
      <img src={image} alt={name} className="img" />

      <span className="tour-price">${price}</span>

      <div className="tour-info">
        <h5>{name}</h5>

        <p>{info}</p>
      </div>
    </article>
  );
};

export default Tour;
```

<br>

### 177. Tours - Remove Tour<a id='177'></a>

#### Remove Tour

To implement the "remove tour" functionality, you can add a button to each Tour component that, when clicked, removes the tour from the list of tours. You can achieve this by updating the state of the Tours component to remove the tour from the tours array.

---

- In src/App.jsx, setup remove tour function, and pass in component

```js
import React, { useState, useEffect } from "react";
import Loading from "./Loading";
import Tours from "./Tours";

const url = "https://course-api.com/react-tours-project";

const App = () => {
  const [loading, setLoading] = useState(true);
  const [tours, setTours] = useState([]);

  // 1
  const removeTour = (id) => {
    const newTours = tours.filter((tour) => tour.id !== id);
    setTours(newTours);
  };

  const fetchTours = async () => {
    // will use later
    setLoading(true);
    try {
      const response = await fetch(url);
      // turn http message into json
      const tours = await response.json();
      console.log(tours);
    } catch (error) {
      console.log(error);
    }
  };

  // useEffect func to invoke fetchTours only once
  useEffect(() => {
    fetchTours();
  }, []);

  // condition: if data is loading then,
  if (loading) {
    return (
      <main>
        <Loading />
      </main>
    );
  }

  // TODO

  return (
    <main>
      {/* 2 */}
      <Tours tours={tours} removeTour={removeTour} />
    </main>
  );
};
export default App;
```

---

- In src/Tours.jsx,

```js
import React from "react";
import Tour from "./Tour";

const Tours = ({ tours, removeTour }) => {
  return (
    <section>
      <div className="title">
        <h2>our tours</h2>
        <div className="title-underline"></div>
      </div>

      <div className="tours">
        {tours.map((tour) => {
          {
            /* 3 */
          }
          return <Tour key={tour.id} {...tour} removeTour={removeTour} />;
        })}
      </div>
    </section>
  );
};

export default Tours;
```

---

- In src/Tour.jsx, add removeTour in function parameter, add remove button element

```js
import React, { useState } from "react";

const Tour = ({ id, image, info, name, price, removeTour }) => {
  return (
    <article className="single-tour">
      <img src={image} alt={name} className="img" />

      <span className="tour-price">${price}</span>

      <div className="tour-info">
        <h5>{name}</h5>

        <p>{info}</p>

        <button
          className="delete-btn btn-block btn"
          onClick={() => removeTour(id)}
        >
          not interested
        </button>
      </div>
    </article>
  );
};

export default Tour;
```

<br>

### 178. Tours - Read More<a id='178'></a>

#### Read More

To implement the "read more" functionality, you can add a button to each Tour component that, when clicked, expands the description of the tour. You can achieve this by updating the state of the Tour component to toggle a "read more" flag, and conditionally rendering the full description based on the flag.

---

- In src/Tour.jsx

```js
import React, { useState } from "react";

const Tour = ({ id, image, info, name, price, removeTour }) => {
  const [readMore, setReadMore] = useState(false);

  return (
    <article className="single-tour">
      <img src={image} alt={name} className="img" />

      <span className="tour-price">${price}</span>

      <div className="tour-info">
        <h5>{name}</h5>

        <p>
          {readMore ? info : `${info.substring(0, 200)}...`}

          <button className="info-btn" onClick={() => setReadMore(!readMore)}>
            {readMore ? "show less" : "  read more"}
          </button>
        </p>

        <button
          className="delete-btn btn-block btn"
          onClick={() => removeTour(id)}
        >
          not interested
        </button>
      </div>
    </article>
  );
};

export default Tour;
```

<br>

### 179. Tours - Refetch<a id='179'></a>

#### Re-fetch Tours

Finally, you can implement a "re-fetch" functionality by adding a button or other user interface element that, when clicked, re-fetches the tours data from the URL and updates the state of the Tours component. You may also want to add a loading state again during the re-fetching process.

Overall, the flow of the application should look something like this:

- App.jsx fetches tours data from a URL and sets the state of the Tours component to store the data.
- The Tours component maps over the tours array and renders a Tour component for each tour.
- Each Tour component has a "remove tour" button and a "read more" button.When the "remove tour" button is clicked, the Tours component updates its state to remove the tour from the tours array.

- When the "read more" button is clicked, the Tour component updates its state to toggle a "read more" flag and conditionally renders the full description.

- When the "re-fetch" button is clicked, the Tours component re-fetches the tours data from the URL and updates its state.

- In src/App.jsx

```js
import React, { useState, useEffect } from "react";
import Loading from "./Loading";
import Tours from "./Tours";

const url = "https://course-api.com/react-tours-project";

function App() {
  const [loading, setLoading] = useState(true);
  const [tours, setTours] = useState([]);

  const removeTour = (id) => {
    const newTours = tours.filter((tour) => tour.id !== id);
    setTours(newTours);
  };

  const fetchTours = async () => {
    // will use later
    setLoading(true);
    try {
      const response = await fetch(url);
      const tours = await response.json();
      setLoading(false);
      setTours(tours);
    } catch (error) {
      setLoading(false);
      console.log(error);
    }
  };
  useEffect(() => {
    fetchTours();
  }, []);

  if (loading) {
    return (
      <main>
        <Loading />
      </main>
    );
  }

  // condition:
  if (tours.length === 0) {
    return (
      <main>
        <div className="title">
          <h2>no tours left</h2>
          <button className="btn" onClick={() => fetchTours()}>
            refresh
          </button>
        </div>
      </main>
    );
  }
  return (
    <main>
      <Tours tours={tours} removeTour={removeTour} />
    </main>
  );
}

export default App;
```

<br>

### 180. Tours - CSS (Optional)<a id='180'></a>

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
  --primary-100: #d1fae5;
  --primary-200: #a7f3d0;
  --primary-300: #6ee7b7;
  --primary-400: #34d399;
  --primary-500: #10b981;
  --primary-600: #059669;
  --primary-700: #047857;
  --primary-800: #065f46;
  --primary-900: #064e3b;

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
  margin: 0 auto;
  border-top-color: var(--primary-500);
  animation: spinner 0.3s linear infinite;
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

main {
  width: 90vw;
  max-width: var(--max-width);
  margin: 5rem auto;
}

.tours {
  padding: 2rem 0;
  display: grid;
  gap: 2rem;
}

.single-tour {
  background: var(--white);
  border-radius: var(--borderRadius);
  box-shadow: var(--shadow-1);
  transition: var(--transition);
  position: relative;
}

.single-tour:hover {
  box-shadow: var(--shadow-3);
}

.tour-price {
  position: absolute;
  top: 0;
  right: 0;
  padding: 0.5rem;
  color: var(--white);
  letter-spacing: var(--letterSpacing);
  background: var(--primary-500);
  border-top-right-radius: var(--borderRadius);
}
.single-tour .img {
  height: 20rem;
  border-top-right-radius: var(--borderRadius);
  border-top-left-radius: var(--borderRadius);
}

.tour-info {
  padding: 2rem 1.5rem;
}

.tour-info h5 {
  text-align: center;
  margin-bottom: 1rem;
  font-weight: 500;
  line-height: 1.5;
}
.tour-info p {
  margin-bottom: 1.25rem;
  line-height: 1.5;
  color: var(--grey-500);
}
.info-btn,
.delete-btn {
  background: transparent;
  border: transparent;
  text-transform: capitalize;
  cursor: pointer;
}
.info-btn {
  color: var(--primary-500);
  font-weight: 600;
}

.delete-btn {
  border: 1px solid var(--primary-500);
  color: var(--primary-500);
}
.delete-btn:hover {
  background: var(--primary-500);
  color: var(--white);
}

@media screen and (min-width: 768px) {
  .tours {
    grid-template-columns: 1fr 1fr;
    align-items: start;
  }
}
@media screen and (min-width: 992px) {
  .tours {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
```

<br>
