**Challenge: Implement merge**

Implement merge

The merge function should merge the sorted subarrays in array[p..q] and array[q+1..r] into a single sorted subarray in array[p..r]. The function starts by allocating two temporary arrays, lowHalf and highHalf, and copying array[p..q] into lowHalf and array[q+1..r] into highHalf.

You should complete the function:
-Make it repeatedly compare the lowest untaken element in lowHalf with the lowest untaken element in highHalf and copy the lower of the two back into array, starting at array[p].
-Once one of lowHalf and highHalf has been fully copied back into array, the remaining elements in the other temporary array are copied back into array.
Note: use indexes i,j and k to access elements in lowHalf,highHalf,and array.

Once implemented, uncomment the Program.assertEqual() at the bottom to verify that the test assertion passes.

**Solution:**
```javascript
// Takes in an array that has two sorted subarrays,
//  from [p..q] and [q+1..r], and merges the array
var merge = function(array, p, q, r) {
    var lowHalf = [];
    var highHalf = [];

    var k = p;
    var i;
    var j;
    for (i = 0; k <= q; i++, k++) {
        lowHalf[i] = array[k];
    }
    for (j = 0; k <= r; j++, k++) {
        highHalf[j] = array[k];
    }

    k = p;
    i = 0;
    j = 0;
    
     while (i < lowHalf.length && j < highHalf.length) {
    if (lowHalf[i] < highHalf[j]) {
      array[k] = lowHalf[i];
      i += 1;
    } else {
      array[k] = highHalf[j];
      j += 1;
    }
    k += 1;
  }
  
  while (i < lowHalf.length) {
    array[k] = lowHalf[i];
    k += 1;
    i += 1;
  }
  while (j < highHalf.length) {
    array[k] = highHalf[j];
    k += 1;
    j += 1;
  }

    // Repeatedly compare the lowest untaken element in
    //  lowHalf with the lowest untaken element in highHalf
    //  and copy the lower of the two back into array
    
    
    // Once one of lowHalf and highHalf has been fully copied
    //  back into array, copy the remaining elements from the
    //  other temporary array back into the array
    
};


var array = [3, 7, 12, 14, 2, 6, 9, 11];
merge(array, 0,
    Math.floor((0 + array.length-1) / 2),
    array.length-1);
println("Array after merging: " + array);
Program.assertEqual(array, [2, 3, 6, 7, 9, 11, 12, 14]);


var array = [1,3, 7, 12, 14, 2, 6, 9, 11,];
merge(array, 0,
    Math.floor((0 + array.length-1) / 2),
    array.length-1);
println("Array after merging: " + array);
Program.assertEqual(array, [1,2, 3, 6,7, 9, 11, 12, 14]);
```
