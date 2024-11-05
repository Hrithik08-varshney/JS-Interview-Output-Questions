# JS INTERVIEW OUTPUT QUESTIONS

1. **What will be the output?**

```javascript
for (var i=0;i<3;i++){
    setTimeout(()=>console.log(i),1);
}
```
<details>
  <summary>Answer</summary>
  <b>3 3 3</b>
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
     <b>0 1 2</b> 
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

---

4. **What will be the output?**

```javascript
   const object1 = {
    a: 10,
    b: 20,
    c: function() {
        console.log(this.a + this.b);
    }
};

const func = object1.c;
func();

```
<details>
 <summary>Answer</summary>
<b>NaN</b>
</details>
<details>
 <summary>Explanation</summary>
<h4>Step-by-Step Breakdown</h4>

<ol>
    <li><code>object1</code> is an object with three properties:
        <ul>
            <li><code>a</code> with a value of <code>10</code>.</li>
            <li><code>b</code> with a value of <code>20</code>.</li>
            <li><code>c</code>, a function that logs the sum of <code>this.a</code> and <code>this.b</code>.</li>
        </ul>
    </li>
    <li><code>const func = object1.c;</code> assigns a reference of <code>object1.c</code> to <code>func</code>. However, this reference no longer retains <code>object1</code> as its context.</li>
    <li>When <code>func()</code> is called, it executes <code>object1.c</code> as a standalone function, with <code>this</code> no longer bound to <code>object1</code>. As a result:
        <ul>
            <li>In <strong>strict mode</strong>, <code>this</code> is <code>undefined</code>, causing an error.</li>
            <li>In <strong>non-strict mode</strong>, <code>this</code> refers to the global object, where <code>a</code> and <code>b</code> are undefined, resulting in <code>NaN</code> (since <code>undefined + undefined</code> is <code>NaN</code>).</li>
        </ul>
    </li>
</ol>
</details>

---

5. **What will be the output?**

```javascript
const object1 = {
    a: 10,
    b: 20,
    c: function() {
        console.log(this.a + this.b);
    }
};

const func = object1.c.bind(object1);
func();

```
<details>
 <summary>Answer</summary>
<b>30</b>
</details>
<details>
 <summary>Explanation</summary>
 <p>This code defines an object, <code>object1</code>, with three properties:</p>
    <ul>
        <li><code>a</code>: A property with the value <code>10</code>.</li>
        <li><code>b</code>: A property with the value <code>20</code>.</li>
        <li><code>c</code>: A function that, when called, logs the sum of <code>a</code> and <code>b</code> using <code>this.a + this.b</code>.</li>
    </ul>
    <p>Next, we create a new variable, <code>func</code>, which stores the <code>c</code> function bound to <code>object1</code> using <code>bind</code>. Binding ensures that the value of <code>this</code> inside <code>c</code> always refers to <code>object1</code>.</p>
    <p>When <code>func()</code> is called, it invokes the bound function, logging <code>this.a + this.b</code>, which is <code>10 + 20</code>, resulting in <code>30</code>.</p>
</details>
