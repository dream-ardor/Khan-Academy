Challenge: Recursive factorial

Base case

In this challenge you will write a recursive function that returns the value of n!.

Start by writing the base case:
if n is zero, then factorial should just return the value 1.

Once implemented, uncomment the Program.assertEqual() for factorial(0) at the bottom to verify that the test assertion passes.

**My Code:**
```javascript
var factorial = function(n) {
// base case: 
if(n===0){
    return 1;
}
// recursive case:
return factorial(n-1) * n;	
}; 

println("The value of 0! is " + factorial(0) + ".");
println("The value of 5! is " + factorial(5) + ".");

Program.assertEqual(factorial(0), 1);
Program.assertEqual(factorial(5), 120);
Program.assertEqual(factorial(4), 24);
Program.assertEqual(factorial(9), 362880);
```
