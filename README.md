# Ex06 BMI Calculator
## Date: 01/09/26

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM
App.jsx
```
import React, { useState } from "react";
import "./App.css";

function App() {
  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    if (!height || !weight) {
      alert("Please enter valid values");
      return;
    }

    const heightInMeters = height / 100;
    const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(2);

    setBmi(bmiValue);

    if (bmiValue < 18.5) {
      setCategory("Underweight");
    } else if (bmiValue >= 18.5 && bmiValue < 24.9) {
      setCategory("Normal Weight");
    } else if (bmiValue >= 25 && bmiValue < 29.9) {
      setCategory("Overweight");
    } else {
      setCategory("Obese");
    }
  };

  return (
    <div className="container">
      <h1>BMI Calculator</h1>

      <input
        type="number"
        placeholder="Enter Height (cm)"
        value={height}
        onChange={(e) => setHeight(e.target.value)}
      />

      <input
        type="number"
        placeholder="Enter Weight (kg)"
        value={weight}
        onChange={(e) => setWeight(e.target.value)}
      />

      <button onClick={calculateBMI}>Calculate BMI</button>

      {bmi && (
        <div className="result">
          <h2>Your BMI: {bmi}</h2>
          <h3>Category: {category}</h3>
        </div>
      )}
    </div>
  );
}

export default App;
```
App.css
```
body {
  font-family: Arial, sans-serif;
  background: #f0f4f8;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.container {
  background: white;
  padding: 30px;
  border-radius: 10px;
  width: 350px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}

input {
  width: 90%;
  padding: 10px;
  margin: 10px 0;
}

button {
  padding: 10px 20px;
  background: #0077b6;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background: #023e8a;
}

.result {
  margin-top: 20px;
}
```



## OUTPUT

<img width="1919" height="1015" alt="image" src="https://github.com/user-attachments/assets/739f1a51-c375-4004-8b1c-d242571aa5fc" />



## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
