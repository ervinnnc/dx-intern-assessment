# Task 1

The code had both logical and syntax issues. Firstly, the buttons and corresponding `onclick` actions were not matched properly;

The minus button was assigned the `addValue()` function:
`<button type='button' class='btn btn-primary btn-large' id='leftBtn' onclick='addValue()'> - </button>`

and vice versa, where the add button was assigned the `minusValue()` function:
`<button type='button' class='btn btn-primary btn-large' id='rightBtn' onclick='minusValue()'> + </button>`

**These have to be swapped, where the add button would have the `addValue()` function and the minus button will have the `minusValue()` function.**


counterValue field declaration
---
The field `counterValue` was assigned a **`const`**, which would not allow writing to the field;
`const counterValue = 0`

Thus, this has to be changed to a global **`var`** instead, or by using a local **`let`** variable. The semicolon was also omitted, so it has to be added as well;
**`let counterValue = 0;`**


addValue() function
---
The semicolon was omitted;
`let addBtn = document.getElementById("rightBtn").innerHTML`

Thus we will add the semicolon;
**`let addBtn = document.getElementById("rightBtn").innerHTML;`**

--
This logic **does not** translate into the requirement that states that the add button should increase by 1 every time it is pressed. Instead, this implements the logic that if the current value is a multiple of 3, then it will increase by 5, otherwise, it will increase by 1.
```
if (counterValue % 3) {
    counterValue += 5
} else {
    counterValue++
}
```

The correct logic should be simply as below;
**``counterValue++;``**


minusValue() function
---
The semicolon was omitted;
`let minusBtn = document.getElementById("leftBtn").innerHTML`

Thus we will add the semicolon;
**`let minusBtn = document.getElementById("leftBtn").innerHTML;`**

--
The current logic will allow for unconditional reduction of the counter value (even negative numbers);
`counterValue--`

We will have to implement logic to check if the counterValue is equal to or less than 0 before reducing the value;
```
if (counterValue <= 0) {
	return;
}

counterValue--;
document.getElementById("countValue").innerHTML = counterValue;
 ```
 The if statement simply checks if the counterValue is less than or equal to zero. If it is, the `return` statement will be fired, preventing further execution of the function. If the condition of the if statement is not fulfilled, then the rest of the code block will be executed, reducing the value and changing the innerHTML of the element.


reset() function
---
The semicolon was omitted;
`counterValue = 0`

Thus, we will include the semicolon;
**`counterValue = 0;`**

In the provided code, the logic only reduced the JavaScript variable of `counterValue`. In order to reflect this on the HTML page, the innerHTML of the element must be manually set to the value of `counterValue`;
**`document.getElementById("countValue").innerHTML = counterValue;`**


---

**End.** Attempted and written by Ervin Chai.  
  
  
  
  
# Task 2

There are a few simple components, one text field for the input of weight in KG, ``id="weightInput"``. A button that does the conversion, ``onclick="convert()"`` and a button that resets the form, ``onclick="reset()"``. There is also a results section which displays the results when the convert button is clicked, and disappears when the reset button is clicked, this div has ``id="resultsDisplay"`` and default style ``style="display: none;``.

convert() function
---
Reads in the value that is present in the text box; and parses into a float (decimal)
```
let input = parseFloat(document.getElementById("weightInput").value);
```
Checks if the value is NaN. If it is a NaN, that means the input is invalid *(parseFloat returns NaN if a non-numeric string is provided)*.
```
if (Number.isNaN(input)) {
	alert("Please enter a valid input! Enter a whole number or a decimal.");
	return;
}
```

If input is valid, then do the calculations;
```
let  kg = input;
let  lbs = kg * 2.205;
let  mg = kg * 1000000;
```
Finally, assign the calculated values to the innerHTML and show the div;
```
document.getElementById("weightKg").innerHTML = kg;
document.getElementById("weightLbs").innerHTML = lbs;
document.getElementById("weightMg").innerHTML = mg;

document.getElementById("resultsDisplay").style.display = "block";
```


reset() function
---
Resets the value of the text field and hides the results div;
```
document.getElementById("weightInput").value = "";
document.getElementById("resultsDisplay").style.display = "none";
```

---
**End.** Attempted and written by Ervin Chai.
