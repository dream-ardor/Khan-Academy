Challenge: Implement quicksort

Implement quicksort

The quickSort function should recursively sort the subarray array[p..r].
- If the subarray has size 0 or 1, then it's already sorted, and so nothing needs to be done.
- Otherwise, quickSort uses divide-and-conquer to sort the subarray.

The divide step should partition the array, the conquer step should recursively quicksort the partitioned subarrays, and the combine step should do nothing.

Once implemented, uncomment the Program.assertEqual() at the bottom to verify that the test assertion passes.

Add another check, using Program.assertEqual(), to make sure your sorting algorithm consistently returns the correct order.

Place the code for your check under the provided check.

Try it on arrays with negative numbers or 0 to make sure it still works in those cases.

**Solution:**
```javascript
// This function partitions given array and returns 
//  the index of the pivot.
var partition=function(array, p, r){
    // This code has been purposefully obfuscated,
    // as you will implement it yourself in next challenge
    var e=array,t=p,n=r;var r=function(e,t,n){var r=e[t];e[t]=e[n];e[n]=r;};var i=t;for(var s=t;s<n;s++){if(e[s]<=e[n]){r(e,s,i);i++;}}r(e,n,i);return i;
};


var quickSort = function(array, p, r) {
    if (p < r) {
        var q = partition(array, p, r);
        quickSort(array, p, q - 1);
        quickSort(array, q + 1, r);
    }
};

var array = [9, 7, 5, 11, 12, 2, 14, 3, 10, 6];
quickSort(array, 0, array.length-1);
println("Array after sorting: " + array);
Program.assertEqual(array, [2,3,5,6,7,9,10,11,12,14]);

var array = [9, 7, 5, 11, 12, 2, 14, 3, 10, 6,0];
quickSort(array, 0, array.length-1);
println("Array after sorting: " + array);
Program.assertEqual(array, [0,2,3,5,6,7,9,10,11,12,14]);
```
