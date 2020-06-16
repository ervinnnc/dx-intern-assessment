**Task 1**
---

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
