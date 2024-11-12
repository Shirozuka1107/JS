# JS
My notes
11/12/2024
To do this, use a .querySelector to locate the input field and then use the .value property to get the number entered.
Store this in a value variable.
const value = document.querySelector('numbers').value; 

The .split() method takes a string and splits it into an array of strings. You can pass it a string of characters or a RegEx to use as a separator. 
const array = value.split(/,\s*/g); 

Remember that .map() creates a new array, instead of mutating the original array.
const numbers = array.map();

Add a callback function to your .map() method that converts each element to a number.
const numbers = array.map(el => Number(el));

The .filter() method will allow you to filter elements out of an array, creating a new array in the process.
const filtered = numbers.filter();

The callback function needs to return a Boolean value, which indicates whether the element should be included in the new array. In this case, you want to return true if the element is not NaN (not a number).
const filtered = numbers.filter(el => 
!isNaN(el));

The .reduce() method takes an array and applies a callback function to condense the array into a single value.
const sum = array.reduce();

The first is the accumulator, and the second is the current element in the array. The return value for the callback becomes the value of the accumulator on the next iteration.
const sum = array.reduce((acc,el) => acc + el);

The next step in calculating the mean is to divide the sum of numbers by the count of numbers in the list.
const mean = sum / array.length;

