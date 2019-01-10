**Challenge: is a string a palindrome?**

Base case #1

In this challenge, you'll make it so the isPalindrome() function returns true if the provided string is a palindrome, and false otherwise.

Start by implementing the first base case:
if the length of the string is 0 or 1, isPalindrome() should return true. 

Once implemented, uncomment the first Program.assertEqual() for isPalindrome("a") at the bottom to verify that the test assertion passes.

Finally, write the recursive case.

Use the provided function middleCharacters to remove the first and last characters from the string.

Check that the console output from the checkPalindrome function is correct.

Once implemented, uncomment the Program.assertEqual() for isPalindrome("rotor") at the bottom to verify that the test assertion passes.

Test it out!

Add two more checks (for a total of 5 checks) using Program.assertEqual() to make sure your palindrome checking algorithm consistently finds the correct answer. Try it out with numbers and spaces, perhaps.

**My Code:**
```javascript
// Returns the first character of the string str
var firstCharacter = function(str) {
    return str.slice(0, 1);
};

// Returns the last character of a string str
var lastCharacter = function(str) {
    return str.slice(-1);
};

// Returns the string that results from removing the first
//  and last characters from str
var middleCharacters = function(str) {
    return str.slice(1, -1);
};

var isPalindrome = function(str) {
    // base case #1
    
    if(str.length <= 0 || str.length <= 1){
        return true;
    }
    // base case #2
    if(firstCharacter(str) !== lastCharacter(str)){
        return false;
    }
    // recursive case
    return isPalindrome(middleCharacters(str));
};

var checkPalindrome = function(str) {
    println("Is this word a palindrome? " + str);
    println(isPalindrome(str));
};

checkPalindrome("a");
Program.assertEqual(isPalindrome("a"), true);
checkPalindrome("motor");
Program.assertEqual(isPalindrome("motor"), false);
checkPalindrome("rotor");
Program.assertEqual(isPalindrome("rotor"), true);
checkPalindrome("LEvEL");
Program.assertEqual(isPalindrome("LEvEL"), true);
checkPalindrome("6996");
Program.assertEqual(isPalindrome("6996"),true );

```
