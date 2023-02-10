# Context_Api_Setup

# Setup Context API

**Step 1:** Make a new file named "context.js" inside the "src" folder and write the following code in it\
```
import React, { Component } from "react";

const ProductContext = React.createContext();

class ProductProvider extends Component {
  state = {};
  render() {
    return (
      <ProductContext.Provider
        value={{
          ...this.state,
        }}
      >
        {this.props.children}
      </ProductContext.Provider>
    );
  }
}

const ProductConsumer = ProductContext.Consumer;

export { ProductConsumer, ProductProvider };


```

**Step 2:** Make your app.js look like the following:\
```
import { Fragment } from "react";
import { Routes, Route } from "react-router-dom";

function App() {
  return (
    <Fragment>
      <Routes>
        <Route />
      </Routes>
    </Fragment>
  );
}

export default App;
```
**Step 3:** Make your "index.js" look like the following:\
```
import React from "react";
import ReactDOM from "react-dom/client";
import { BrowserRouter as Router } from "react-router-dom";
import "./index.css";
import App from "./App";
import reportWebVitals from "./reportWebVitals";
import { ProductProvider } from "./context";

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(
  <ProductProvider>
    <Router>
      <App />
    </Router>
  </ProductProvider>
);
reportWebVitals();

```

## Example of usage of context api inside component:\
```
import React, { Component } from "react";
import { ProductConsumer } from "../context";

export default class Tax extends Component {
  render() {
    return (
      <ProductConsumer>
        {(value) => {
          const { initialTax } = value;
          return (
            <div className="tax">
              <h1>Est. taxes & fees : </h1>
              <h1>${initialTax}</h1>
            </div>
          );
        }}
      </ProductConsumer>
    );
  }
}
```
