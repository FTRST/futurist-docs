# Input
This section covers the **Input** component, its use, capabilities, and style variations.

***
## Purpose
***
```Input``` is a field for users to type in, just like your standard HTML input.

The Input component takes a function to update a value (either directly or within a state), and uses a standard onChange to modify it.

***
## Usage
***
Input expects the following to be passed as parameters:

* **action**: The function used to update the value
* **value**: A reference for the current value of the Input

Since Inputs are used to update values, a function must be passed along with a value reference.

***
## Core Example
***
```
import Input from "futurist-components";

function App() {
  let mystring = "";
  function updateString(value) {
    mystring = value;
  }
  return (
    <>
      <Input action={updateString} value={mystring} />
    </>
  );
}
```

***
## Optional Parameters
***
Inputs also can accept the following optional paramters:

* **placeholder**: An example value for user to reference