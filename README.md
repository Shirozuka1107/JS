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

11/13/2024

Using the implicit return of an arrow function, you can directly return the value of the .reduce() method divided by the length of the array, without having to assign any variables.
array.reduce((acc, el) => acc + el, 0) / array.length; 

To display the value of mean, your app has a #mean element ready to go.
Use a .querySelector to find that element, and then set its .textContent to the value of mean.
document.querySelector("#mean").textContent = mean;

The first step in calculating the median is to ensure the list of numbers is sorted from least to greatest. Once again, there is an array method ideal for this – the .sort() method.
const sorted = array.sort();

To sort your numbers from smallest to largest, pass a callback function that takes parameters a and b, and returns the result of subtracting b from a.
const sorted = array.sort((a,b) => {a-b})

Create a variable called isEven. Then use the modulus operator to check if the length of the testArr2 array is even. Assign that expression to the isEven variable.
const testArr1 = [1, 2, 3, 4, 5];
const testArr2 = [1, 2, 3, 4, 5, 6];
const isEven = testArr2.length % 2 === 0;
console.log(isEven);

Here is how to find the middle number of an array with an odd number of elements:
Example Code
arr[Math.floor(arr.length / 2)];

Declare an oddListMedian variable and assign it the result of finding the middle number of the testArr1. Then log the oddListMedian variable to the console.
const oddListMedian = testArr1[Math.floor(testArr1.length /2)];
console.log(oddListMedian);

// first middle number
arr[arr.length / 2];
// second middle number
arr[(arr.length / 2) - 1];
Create an evenListMedian variable and assign it the result of finding the median of the testArr2.
const firstMiddleNumber = testArr2[testArr2.length / 2];
const secondMiddleNumber = testArr2[(testArr2.length / 2) - 1];
const evenListMedian = getMean([firstMiddleNumber, secondMiddleNumber])
console.log(evenListMedian);

//Important//
Inside your getMedian function, check if the length of sorted is even. If it is, find the middle two numbers, calculate their mean, and return the result. If the length of sorted is odd, return the middle number.
   const median = 
   sorted.length % 2 === 0 ? getMean([sorted[sorted.length / 2 - 1], sorted[sorted.length / 2]]) : sorted[Math.floor(sorted.length / 2)];
   return median

//Mode Function Code//
Inside the array.forEach() callback function, check if the current element is inside the counts object. If the element can be found, increment the value of counts[el] by 1. Otherwise, assign the number 1 to counts[el].
const getMode = (array) => {
  const counts = {};
  array.forEach(el => {
if (counts[el]) {
  counts[el] += 1;
} else {
  counts[el] = 1;
}
  })
  return counts;

//Simplified method//

Convert the forEach callback to use an expression body and replace the statements with a ternary.
const getMode = (array) => {
  const counts = {};
array.forEach(el => counts[el] = counts[el] ? counts[el] + 1 : 1)
  return counts;

11/14/2024

To calculate this, you will use a Set. A Set is a data structure that only allows unique values. If you pass an array into the Set constructor, it will remove any duplicate values.
Start by creating an if statement. In the condition, create a Set with new Set() and pass it the Object.values() of your counts object. If the size property of this Set is equal to 1, that tells you every value appears the same number of times. In this case, return null from your function.
if (new Set(Object.values(counts)).size === 1) {
    return null;
  }

Now you need to find the value that occurs with the highest frequency. You'll use the Object.keys() method for this.
Start by declaring a highest variable, and assigning it the value of the counts object's Object.keys() method.
const highest = Object.keys(counts);

Now you need to sort the values properly. Chain the .sort() method to your Object.keys() call.
For the callback, you'll need to use the counts object to compare the values of each key. You can use the a and b parameters to access the keys. Then, return the value of counts[b] minus the value of counts[a].
Finally, access the first element in the array using bracket notation to complete your highest variable.
const highest = Object.keys(counts).sort((a,b) => counts[b]-counts[a])[0];

Now chain the filter method to your latest Object.keys() call. The callback function should return whether the value of counts[el] is equal to your counts[highest].
const mode = Object.keys(counts).filter((el) => counts[el] === counts[highest])

Declare a getRange function that takes the same array parameter you have been using. Using Math.min(), Math.max(), and the spread operator, return the difference between the largest and smallest numbers in the list.
const getRange = (array) => {
  Math.min(...array), Math.max(...array);
  return Math.max(...array) - Math.min(...array)
};

The next step is to square each of the differences. To square a value, you can use the ** operator. For example, 3 ** 2 would return 9.
Declare a squaredDifferences variable, and assign it the value of differences.map(). For the callback, return the value of el squared.
const squaredDifferences = differences.map ((el) => el ** 2)[0]

Declare a sumSquaredDifferences variable, and assign it the value of squaredDifferences.reduce(). For the callback, return the sum of acc and el. Remember to set the initial value to 0.
const sumSquaredDifferences = squaredDifferences.reduce((acc,el) => acc + el,0)

Declare a variance variable, and assign it the value of array.reduce(). For the callback, pass in your standard acc and el parameters, but leave the function body empty for now. Don't forget to set the initial value to 0.
const variance = array.reduce((acc,el) => {},0)

Divide your .reduce() call by the length of the array (in your variance declaration). Then, return variance.
const variance = array.reduce((acc, el) => {
const difference = el - mean;
const squared = difference ** 2;
return acc + squared;
}, 0) / array.length;
return variance;

Start by setting the onload property of window to an arrow function with no parameters. In the function, declare a container variable and assign it the value of getting the element by the id of "container".
window.onload = () => {
const container = document.getElementById("container")

Set the className of the label element to "label", and set the textContent to the name parameter.
label.className = "label";
label.textContent = name;

Finally, use the .appendChild() method to add your label element to the container element.
container.appendChild(label)

Declare an empty range function which takes a start and end parameter. Use the Array() constructor and implicitly return an empty array.
const range = (start,end) => Array()


