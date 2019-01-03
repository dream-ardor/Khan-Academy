**Challenge:Write selection sort.**

Selection sort loops over positions in the array. For each position, it finds the index of the minimum value in the subarray starting at that position. Then it swaps the values at the position and at the minimum index. Write selection sort, making use of the swap and indexOfMinimum functions. 

Once implemented, uncomment the Program.assertEqual() at the bottom to verify that the test assertion passes.

**My Code:**
```javascript
var swap = function(array, firstIndex, secondIndex) {
	var temp = array[firstIndex];
	array[firstIndex] = array[secondIndex];
	array[secondIndex] = temp;
};
var indexOfMinimum = function(array, startIndex) {
	var minValue = array[startIndex];
	var minIndex = startIndex;
	for (var i = minIndex + 1; i < array.length; i++) {
		if (array[i] < minValue) {
			minIndex = i;
			minValue = array[i];
		}
	}
	return minIndex;
};
var selectionSort = function(array) {
	var length = array.length;
	for (var i = 0; i < length; i++) {
		var min = indexOfMinimum(array, i);
		swap(array, i, min);
	}
};
var array = [22, 11, 99, 88, 9, 7, 42];
selectionSort(array);
println("Array after sorting: " + array);
Program.assertEqual(array, [7, 9, 11, 22, 42, 88, 99]);
var array = [21, , 99, 88, 9, 7, 42];
selectionSort(array);
println("Array after sorting: " + array);
Program.assertEqual(array, [7, 9, 21, 69, 42, 88, 99]);
```
