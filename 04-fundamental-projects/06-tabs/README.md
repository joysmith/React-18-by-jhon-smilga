#### 202. [Tabs - Setup](#202)

#### 203. [Tabs - Fetch Jobs](#203)

#### 204. [Tabs - Display Job](#204)

#### 205. [Tabs - Duties and UUID Library](#205)

#### 206. [Tabs - Button Container](#206)

#### 207. [Tabs - Current Item](#207)

#### 208. [Tabs - CSS (Optional)](#208)

<br>

---

### 202. Tabs - Setup<a id="202"></a>

#### Figma URL

[Tabs](https://www.figma.com/file/FJC19b9eUWS62HKR8L9Dmn/Tabs?node-id=0%3A1&t=8Rio02EFK1r9ItDW-1)

- install deps

```sh
npm install
```

- spin up dev server

```sh
npm run dev
```

<br>

### 203. Tabs - Fetch Jobs<a id="203"></a>

#### Steps

#### Fetch Data

In App.jsx, use the fetch API to get job information from an external API. Use the useEffect hook to make the API call when the component mounts. While the data is being fetched, set up a loading state that displays a message to the user.

#### State Value

Once the data has been fetched, store it in a state variable using the useState hook. This will allow you to modify the data and have those changes automatically reflected in the rendered output.

---

- In src/App.jsx

```js
import { useState, useEffect } from "react";

const url = "https://course-api.com/react-tabs-project";

function App() {
  const [loading, setLoading] = useState(true);
  const [jobs, setJobs] = useState([]);

  const fetchJobs = async () => {
    const response = await fetch(url);
    const newJobs = await response.json();
    setJobs(newJobs);
    setLoading(false);
  };

  useEffect(() => {
    fetchJobs();
  }, []);

  if (loading) {
    return (
      <section className="jobs-center">
        <div className="loading"></div>
      </section>
    );
  }

  return <h2> Tabs Starter </h2>;
}

export default App;
```

<br>

### 204. Tabs - Display Job<a id="204"></a>

#### JobInfo

Create a JobInfo component to display the first job in the list. Use object destructuring to extract the relevant data from the job object. Display the company, dates, title, and duties, using the Duties component to render the list of duties.

---

- In src folder create Duties.jsx -rafce

- In src folder create JobInfo.jsx -rafce

```js
import Duties from "./Duties";

const JobInfo = ({ jobs }) => {
  // alternatives
  const { company, dates, duties, title } = jobs[0];

  return (
    <article className="job-info">
      <h3>{title}</h3>
      <span className="job-company">{company}</span>
      <p className="job-date">{dates}</p>
      <Duties duties={duties} />
    </article>
  );
};
export default JobInfo;
```

---

- In src/App.jsx

```js
import { useState, useEffect } from "react";
import JobInfo from "./JobInfo";

const url = "https://course-api.com/react-tabs-project";

function App() {
  const [loading, setLoading] = useState(true);
  const [jobs, setJobs] = useState([]);

  const fetchJobs = async () => {
    const response = await fetch(url);
    const newJobs = await response.json();
    setJobs(newJobs);
    setLoading(false);
  };

  useEffect(() => {
    fetchJobs();
  }, []);

  if (loading) {
    return (
      <section className="jobs-center">
        <div className="loading"></div>
      </section>
    );
  }

  return (
    <section className="jobs-center">
      {/* job info */}
      <JobInfo jobs={jobs} />
    </section>
  );
}

export default App;
```

---

<br>

### 205. Tabs - Duties and UUID Library<a id="205"></a>

#### JobDuties

In the Duties component, iterate over the array of duties and render each item. If you want to use icons, you will need to install the react-icons library.

#### UUID Library

```sh
npm install uuid
```

```js
import { v4 as uuidv4 } from "uuid";
```

Since the job data does not have an id, you can install the uuid library to generate unique ids for each job. Use these ids instead of the index to set the key prop for the JobInfo and Duties components.

---

- In src/Duties.jsx

```js
import { v4 as uuidv4 } from "uuid";

// importing icon from npm package
import { FaAngleDoubleRight } from "react-icons/fa";

const Duties = ({ duties }) => {
  return (
    <div>
      {duties.map((duty, index) => {
        const id = uuidv4();
        // console.log(id);
        return (
          <div key={id} className="job-desc">
            <FaAngleDoubleRight className="job-icon"></FaAngleDoubleRight>
            <p>{duty}</p>
          </div>
        );
      })}
    </div>
  );
};

export default Duties;
```

<br>

### 206. Tabs - Button Container<a id="206"></a>

#### BtnContainer

Set up a BtnContainer component and pass the jobs array, currentItem state variable, and setCurrentItem function down as props. In the BtnContainer component, create a button for each job in the jobs array,

---

- In src folder create BtnContainer.jsx

```js
const BtnContainer = ({ jobs }) => {
  return (
    <div className="btn-container">
      {jobs.map((item, index) => {
        return (
          <button
            key={item.id}
            className="job-btn"}
          >
            {item.company}
          </button>
        );
      })}
    </div>
  );
};
export default BtnContainer;
```

---

- In src/App.jsx

```js
import { useState, useEffect } from "react";
import JobInfo from "./JobInfo";
import BtnContainer from "./BtnContainer";

const url = "https://course-api.com/react-tabs-project";

function App() {
  const [loading, setLoading] = useState(true);
  const [jobs, setJobs] = useState([]);

  const fetchJobs = async () => {
    const response = await fetch(url);
    const newJobs = await response.json();
    setJobs(newJobs);
    setLoading(false);
  };

  useEffect(() => {
    fetchJobs();
  }, []);

  if (loading) {
    return (
      <section className="jobs-center">
        <div className="loading"></div>
      </section>
    );
  }

  return (
    <section className="jobs-center">
      {/* btn container */}
      <BtnContainer jobs={jobs} />
      {/* job info */}
      <JobInfo jobs={jobs} />
    </section>
  );
}

export default App;
```

<br>

### 207. Tabs - Current Item<a id="207"></a>

#### CurrentItem

Create a currentItem state variable in App.jsx and set it to 0 initially. Pass this state variable down to the JobInfo component as a prop, and use it to display the current job.

#### SetCurrentItem

Attach the setCurrentItem function to each button.
When the user clicks a button, the setCurrentItem function should be called with the index of the selected job. This function should update the currentItem state variable, causing the JobInfo component to render the selected job.

Overall, the flow of the application should look something like this:

- In App.jsx, use the fetch API to get job information from an external API, set up a loading state, and display a message to the user while the data is being fetched.
- Once the data has been fetched, store it in a state variable using the useState hook.
- Create a JobInfo component to display the first job in the list, using object destructuring to extract the relevant data from the job object.
- Use the Duties component to render the list of duties for each job.
- Use the uuid library to generate unique ids for each job, and use these ids instead of the index to set the key prop for the JobInfo and Duties components.
- Create a currentItem state variable in App.jsx and pass it down to the JobInfo component as a prop, using it to display the current job.
- Set up a BtnContainer component and pass the jobs array, currentItem state variable, and setCurrentItem function down as props.
- In the BtnContainer component, create a button for each job in the jobs array, and attach the setCurrentItem function to each button to change the currentItem state variable and render the selected job.

---

- In src/App.jsx

```js
import { useState, useEffect } from "react";
import BtnContainer from "./BtnContainer";
import JobInfo from "./JobInfo";

const url = "https://course-api.com/react-tabs-project";

function App() {
  const [loading, setLoading] = useState(true);
  const [jobs, setJobs] = useState([]);
  const [currentItem, setCurrentItem] = useState(0);

  const fetchJobs = async () => {
    const response = await fetch(url);
    const newJobs = await response.json();
    setJobs(newJobs);
    setLoading(false);
  };

  useEffect(() => {
    fetchJobs();
  }, []);

  if (loading) {
    return (
      <section className="jobs-center">
        <div className="loading"></div>
      </section>
    );
  }
  return (
    <section className="jobs-center">
      {/* btn container */}
      <BtnContainer
        jobs={jobs}
        currentItem={currentItem}
        setCurrentItem={setCurrentItem}
      />
      {/* job info */}
      <JobInfo jobs={jobs} currentItem={currentItem} />
    </section>
  );
}

export default App;
```

---

- In src/JobInfo.jsx

```js
import Duties from "./Duties";

const JobInfo = ({ jobs, currentItem }) => {
  // alternatives
  const { company, dates, duties, title } = jobs[currentItem];

  return (
    <article className="job-info">
      <h3>{title}</h3>
      <span className="job-company">{company}</span>
      <p className="job-date">{dates}</p>
      <Duties duties={duties} />
    </article>
  );
};
export default JobInfo;
```

---

- In src/BtnContainer.jsx

```js
const BtnContainer = ({ jobs, currentItem, setCurrentItem }) => {
  return (
    <div className="btn-container">
      {jobs.map((item, index) => {
        return (
          <button
            key={item.id}
            onClick={() => setCurrentItem(index)}
            className={index === currentItem ? "job-btn active-btn" : "job-btn"}
          >
            {item.company}
          </button>
        );
      })}
    </div>
  );
};
export default BtnContainer;
```

<br>

### 208. Tabs - CSS (Optional)<a id="208"></a>

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
  --primary-100: #ccfbf1;
  --primary-200: #99f6e4;
  --primary-300: #5eead4;
  --primary-400: #2dd4bf;
  --primary-500: #14b8a6;
  --primary-600: #0d9488;
  --primary-700: #0f766e;
  --primary-800: #115e59;
  --primary-900: #134e4a;

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

.jobs-center {
  width: 80vw;
  margin: 5rem auto;
  max-width: var(--max-width);
}

.btn-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
  margin-bottom: 4rem;
}

.job-btn {
  background: transparent;
  border-color: transparent;
  letter-spacing: var(--letterSpacing);
  cursor: pointer;
  transition: var(--transition);
}
.job-btn:hover {
  color: var(--primary-500);
  box-shadow: 0 2px var(--primary-500);
}
.active-btn {
  color: var(--primary-500);
  box-shadow: 0 2px var(--primary-500);
}

.job-company {
  text-transform: uppercase;
  color: var(--grey-700);
  background: var(--grey-300);
  display: inline-block;
  padding: 0.375rem 0.75rem;
  border-radius: var(--borderRadius);
  margin: 0.75rem 0;
}
.job-date {
  color: var(--grey-500);
  letter-spacing: var(--letterSpacing);
  margin-bottom: 2rem;
}

.job-desc {
  display: grid;
  grid-template-columns: auto 1fr;
  column-gap: 2rem;
  align-items: center;
  margin-bottom: 1.25rem;
}

.job-icon {
  color: var(--primary-500);
}

.job-desc p {
  color: var(--grey-700);
  line-height: 1.5;
}

@media screen and (min-width: 992px) {
  .jobs-center {
    width: 90vw;
    display: grid;
    grid-template-columns: 200px 1fr;
    column-gap: 4rem;
  }
  .btn-container {
    flex-direction: column;
    justify-content: flex-start;
  }
  .job-btn {
    margin-bottom: 1rem;
  }
  .job-btn:hover {
    box-shadow: -2px 0px var(--primary-500);
  }
  .active-btn {
    box-shadow: -2px 0px var(--primary-500);
  }
}
```

<br>
