**Challenge: Implement partition**

Implement partition

The partition function should partition the subarray array[p..r] so that all elements in array[p..q-1] are less than or equal to array[q] (the pivot) and all elements in array[q+1..r] are greater than array[q], and it returns the index q of where the pivot ends up.

Use the provided swap() function for swapping.

Once implemented, uncomment the Program.assertEqual() at the bottom to verify that the test assertion passes.

Test it out!

Make up another array and try partioning it. Maybe one with negative numbers or 0 in it?

**Solution:**
```javascript
// Swaps two items in an array, changing the original array
var swap = function(array, firstIndex, secondIndex) {
    var temp = array[firstIndex];
    array[firstIndex] = array[secondIndex];
    array[secondIndex] = temp;
};

var partition = function(array, p, r) {
    // Compare array[j] with array[r], for j = p, p+1,...r-1
    // maintaining that:
    //  array[p..q-1] are values known to be <= to array[r]
    //  array[q..j-1] are values known to be > array[r]
    //  array[j..r-1] haven't been compared with array[r]
    // If array[j] > array[r], just increment j.
    // If array[j] <= array[r], swap array[j] with array[q],
    //   increment q, and increment j. 
    // Once all elements in array[p..r-1]
    //  have been compared with array[r],
    //  swap array[r] with array[q], and return q.
    
    var q = p;
    for (var j = p; j < r; j++) {
          if (array[j] <= array[r]){
            swap(array, j, q);
            q++;
        }
    }
     swap(array,j,q);
    return q;
};

var array = [9, 7, 5, 11, 12, 2, 14, 3, 10, 4, 6];
var q = partition(array, 0, array.length-1);
println("Array after partitioning: " + array);
Program.assertEqual(q, 4);
Program.assertEqual(array, [5, 2, 3, 4, 6, 7, 14, 9, 10, 11, 12]);
 
 var array = [,9,7, 5, 11, 12, 2, 14, 3, 10, 4, 6];
var q = partition(array, 0, array.length-1);
println("Array after partitioning: " + array);
Program.assertEqual(q, 4);
Program.assertEqual(array, [5, 2, 4, 6, 7, 14, 9, 10, 11, 12]);
```
