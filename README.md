# JS INTERVIEW OUTPUT QUESTIONS

1. **What will be the output?**

```javascript
for (var i=0;i<3;i++){
    setTimeout(()=>console.log(i),1);
}
```
<details>
  <summary>Answer</summary>
  3 3 3
</details>
<details>
  <summary>Explanation</summary>
 In this code, var is function-scoped, so i is not block-scoped and is shared across all iterations of the loop. By the time the setTimeout callbacks execute, the loop has completed, and i has been incremented to 3. As a result, each console.log(i) outputs 3.
</details>

---

2. **What will be the output?**

```javascript
    for (let i=0; i<3; i++) {
        setTimeout(() => console.log(i), 1);
    }
```
<details>
      <summary>Answer</summary>
      0 1 2
</details>
<details>
      <summary>Explanation</summary>
      Here, `let` is block-scoped, so each iteration of the loop creates a new block scope for `i`. Each `setTimeout` callback captures the correct `i` value for that iteration, resulting in 0, 1, and 2 being logged sequentially.
</details>

---

3. **What will be the output?**

```javascript
    function Person(firstName,lastName){
this.firstName = firstName;
this.lastName = lastName;
};
const js = new Person('Js','react');
const coder = Person('coder','angular');
console.log(js);
console.log(coder);
```
<details>
 <summary>Answer</summary>
<b>Person { firstName: 'Js', lastName: 'react' }</b> <br/>
<b>undefined</b>
</details>
<details>
 <summary>Explanation</summary>
-> Because js is created with the new keyword, it is an instance of the Person class, and the properties firstName and lastName are assigned to it. <br/>
-> Since Person is called without the new keyword for coder, it is executed as a regular function, and this refers to the global object (window in browsers or global in Node.js). As a result, firstName and lastName are assigned to the global scope, and coder itself is undefined.
</details>
