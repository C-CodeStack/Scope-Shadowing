# JavaScript Scope & Shadowing

Now that you have functions, loops, if, else if and else, you have created inner and outer scope. That means that variables created on the outside of those blocks are visible from everywhere inside that block.
```javascript
let varOut = 10
console.log(varOut)//->10

if (true) {//beginning of block
  console.log(varOut)//->10
}//end of block

console.log(varOut)//->10
```

In this case `varOut` is visible everywhere in the code even inside the if block. You can say that this varOut is a `global variable`.

```javascript
console.log(varIn)//throws error... variable has not been declared
if (true) {//beginning of block
  let varIn = 5
  console.log(varIn)//->5
}//end of block

console.log(varIn)//throws error... variable has not been declared
```

As you can see the above code will not work. It will throw errors. It makes sense how the first log says `variable has not been declared` because you don't actually declared it until line 3. This declaration occurs inside the `if block` and can be read on line 4 which is also inside the `if block`. However, the last log throws the same error even though it occurs after the declaration on line 3. This is a `scope` issue. `varIn` only exists within the scope or block that it was initially defined. 

## Task 1
The following code throws an error related to scope. Copy this code into index.js and fix the scope error. When you are done it should log the number 4

```javascript
if (false) {
  let answer = 4
  console.log(answer)
}
else {
  console.log(answer)
}
```
#

`Shadowing` occurs when you declare a variable within multiple scopes.

```javascript
let num = 10
console.log(num)//->10
if (true) {
  console.log(num)//->10...I can only see the first num
  let num = 5 //this is shadowing the initial num within this scope only
  console.log(num)//->5... I can see the first and second num but choose the second because it is in my scope
}
else {
  console.log(num)//->10...I can only see the first num
  let num = 20 //this is shadowing the initial num within this scope only
  console.log(num)//->20 I can see the first and the third num but choose the third because it is in my scope
}

console.log(num)//->10...I cannot see the second and third nums because they are not in my scope. So I choose the first num
```

## Task 2
Copy and modify the following code so that it prints out `breeze` one letter at a time. You cannot move any code. You can only add let letter = "z", let letter = "b" and let letter = "r" in the proper locations.
#

```javascript
let letter = "e"

const helper1 = () => {
  if (true) {
    console.log(letter)
  }
  
  if (false) {
    
  }
  else {
    console.log(letter)
  }
  
  let i = 0
  do {
    console.log(letter)
    i++
  } while (i < 2)
}

const helper2 = () => {
  console.log(letter)
}

const helper3 = (letter) => {
  console.log(letter)
}

helper1()

helper2()

helper3(letter)