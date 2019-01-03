**Challenge: Implement Swap**

Swap function

A key step in many sorting algorithms (including selection sort) is swapping the location of two items in an array. Here's a swap function that looks like it might work, but doesn't:
-the code prints out [9, 9, 4] when it should print out [9, 7, 4].

Fix the swap function.

Hint: Work through the code line by line, writing down the values of items in the array after each step. Could you use an extra temporary variable to solve the problem that shows up? 

Once implemented, uncomment the Program.assertEqual() at the bottom to verify that the test assertion passes.

**My Code:**
```javascript
var swap = function(array, firstIndex, secondIndex) {
    
    var temp = array[firstIndex];
    array[firstIndex] = array[secondIndex];
    array[secondIndex] = temp;
};

var testArray = [7, 9, 4];
swap(testArray, 0, 1);

println(testArray);

Program.assertEqual(testArray, [9, 7, 4]);
var testArray = [8, 2, 6];
swap(testArray, 1, 2);
println(testArray);
Program.assertEqual(testArray, [8, 6, 2]);

var testArray = [2, 3, 1];
swap(testArray, 0, 1);
println(testArray);
Program.assertEqual(testArray, [3, 2, 1]);
```
