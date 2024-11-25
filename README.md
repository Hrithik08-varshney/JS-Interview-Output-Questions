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

---

6. **What will be the output?**

```javascript
console.log(a);
console.log(b);
var a = b = 5;

```
<details>
 <summary>Answer</summary>
<b>undefined</b><br/>
<b>5</b>
</details>
<details>
 <summary>Explanation</summary>
 <ul>
    <li><code>var a = b = 5;</code> assigns <code>5</code> to <code>b</code> first, making <code>b</code> a global variable. Then, <code>a</code> is declared as a local variable (if inside a function) with <code>var</code> and also assigned <code>5</code>.</li>
    <li><code>console.log(a);</code> tries to log <code>a</code> before it's defined, so it outputs <code>undefined</code> due to variable hoisting.</li>
    <li><code>console.log(b);</code> logs <code>5</code> because <code>b</code> is assigned a value before it's accessed.</li>
  </ul>
</details>

---

7. **What will be the output?**

```javascript
var a = 5;
console.log(a++);
console.log(a);

```
<details>
 <summary>Answer</summary>
<b>5</b><br/>
<b>6</b>
</details>
<details>
 <summary>Explanation</summary>
 <ol>
        <li>
            <p><code>console.log(a++);</code>:</p>
            <ul>
                <li>The <code>a++</code> operation is a <strong>post-increment</strong>. This means the current value of <code>a</code> (which is 5) is first used in the expression, then <code>a</code> is incremented by 1.</li>
                <li>So, <code>console.log(a++)</code> will print <strong>5</strong> and then increment <code>a</code> to <strong>6</strong>.</li>
            </ul>
        </li>
        <li>
            <p><code>console.log(a);</code>:</p>
            <ul>
                <li>By this point, <code>a</code> has been incremented to <strong>6</strong>, so this line will print <strong>6</strong>.</li>
            </ul>
        </li>
    </ol>
</details>

---

8. **What will be the output?**

```javascript
console.log(1 < 2 < 3);
console.log(3 > 2 > 1);

```
<details>
 <summary>Answer</summary>
<b>true</b><br/>
<b>false</b>
</details>
<details>
 <summary>Explanation</summary>
<h4>1. <code>1 &lt; 2 &lt; 3</code>:</h4>
  <ul>
    <li>This is evaluated as <code>(1 &lt; 2) &lt; 3</code>.</li>
    <li>First, <code>1 &lt; 2</code> is <code>true</code>.</li>
    <li>Then, <code>true</code> is implicitly converted to <code>1</code> in the comparison <code>1 &lt; 3</code>, which is also <code>true</code>.</li>
  </ul>
  <p><strong>Output:</strong> <code>true</code></p>
  
  <h4>2. <code>3 &gt; 2 &gt; 1</code>:</h4>
  <ul>
    <li>This is evaluated as <code>(3 &gt; 2) &gt; 1</code>.</li>
    <li>First, <code>3 &gt; 2</code> is <code>true</code>.</li>
    <li>Then, <code>true</code> is implicitly converted to <code>1</code> in the comparison <code>1 &gt; 1</code>, which is <code>false</code>.</li>
  </ul>
  <p><strong>Output:</strong> <code>false</code></p>

</details>

---

9. **What will be the output?**

```javascript
const foo = () => {
  console.log(this.name);
};

foo.call({ name: 'John' });

```
<details>
 <summary>Answer</summary>
<b>undefined</b>
</details>
<details>
 <summary>Explanation</summary>
<ul>
  <li>Arrow functions do <strong>not have their own <code>this</code></strong> context; they inherit <code>this</code> from their <strong>enclosing lexical scope</strong>.</li>
  <li><code>.call()</code> does not change the value of <code>this</code> for arrow functions.</li>
  <li>In strict mode, <code>this</code> is <code>undefined</code>, causing a <strong>TypeError</strong>.</li>
  <li>In non-strict mode, <code>this</code> refers to the global object (<code>window</code> in browsers), and <code>this.name</code> is <code>undefined</code>.</li>
</ul>
</details>

---

10. **What will be the output?**

```javascript
const foo = function () {
  const bar = () => {
    console.log(this.name);
  };
  bar();
};

foo.call({ name: 'John' });
```
<details>
 <summary>Answer</summary>
<b>John</b>
</details>
<details>
 <summary>Explanation</summary>
<p>
The function <code>foo</code> is called using <code>.call()</code> with an object <code>{ name: 'John' }</code>. This sets the <code>this</code> context inside <code>foo</code> to the provided object.
</p>
<p>
Within <code>foo</code>, there is an arrow function <code>bar</code>. Arrow functions do not have their own <code>this</code>; they inherit <code>this</code> from their surrounding context. Here, the surrounding context is <code>foo</code>, which has its <code>this</code> set to <code>{ name: 'John' }</code>.
</p>
<p>
When <code>bar()</code> is called, it accesses <code>this.name</code>, which refers to <code>'John'</code>, and logs it to the console.
</p>
</details>

---

11. **What will be the output?**

```javascript
var output = (function(x) {
    delete x;
    return x;
})({ x: 100 });

console.log(output);

```
<details>
 <summary>Answer</summary>
<b>{ x: 100 }</b>
</details>
<details>
 <summary>Explanation</summary>
<ol>
    <li>
        <strong>Input:</strong>
        <p>You are passing an object <code>{ x: 100 }</code> to the function as the parameter <code>x</code>.</p>
    </li>
    <li>
        <strong>Delete Operation:</strong>
        <p><code>delete x;</code> tries to delete the entire <code>x</code> parameter. However, the <code>delete</code> operator only works on object properties, not function parameters.</p>
    </li>
    <li>
        <strong>Return Value:</strong>
        <p>The function returns <code>x</code>, which is still the original object <code>{ x: 100 }</code> because <code>delete x;</code> had no effect.</p>
    </li>
    <li>
        <strong>Output:</strong>
        <p class="output">{ x: 100 }</p>
    </li>
</ol>
</details>

---

12. **What will be the output?**

```javascript
const arr1 = [1, 2, 3, 4, 5, 6, 7, 8];
delete arr1[5];
console.log(arr1.length, arr1);
```
<details>
 <summary>Answer</summary>
<b>8</b> <b>[1, 2, 3, 4, 5, <1 empty item>, 7, 8]</b>
</details>
<details>
 <summary>Explanation</summary>
<ul>
  <li>The <code>delete</code> operator removes the value at the specified index but <strong>does not update the length</strong> of the array.</li>
  <li>It creates an <strong>empty (undefined) slot</strong> at the deleted index, making it a <em>sparse array</em>.</li>
</ul>
</details>

---

13. **How to empty this array?**

```javascript
const arr2 = [1, 2, 3, 4, 5, 6, 7, 8];
```
<details>
 <summary>Answer</summary>
<b>arr2.length = 0</b><br/>
<b>arr2.splice(0, arr2.length)</b><br/>
</details>

---

14. **What will be the output?**

```javascript
console.log(typeof([]));
console.log(typeof(typeof(3)))
```
<details>
 <summary>Answer</summary>
<h2>Example 1: <code>typeof([])</code></h2>
  <p>
    The expression <code>typeof([])</code> returns <strong>"object"</strong>.
    In JavaScript, arrays are a type of object, so <code>typeof</code> will return "object" for arrays.
  </p>
  <pre>
    <code>
      console.log(typeof([])); // Output: "object"
    </code>
  </pre>

  <h2>Example 2: <code>typeof(typeof(3))</code></h2>
  <p>
    The expression <code>typeof(typeof(3))</code> returns <strong>"string"</strong>.
    Here's why:
    <ul>
      <li><code>typeof(3)</code> evaluates to <code>"number"</code> because <code>3</code> is a number.</li>
      <li><code>typeof("number")</code> evaluates to <code>"string"</code> because the result of the first <code>typeof</code> is a string.</li>
    </ul>
  </p>
  <pre>
    <code>
      console.log(typeof(typeof(3))); // Output: "string"
    </code>
  </pre>
</details>

---

15. **What will be the output?**

```javascript
Promise.resolve(1)
  .then((x) => x + 1)
  .then((x) => {
    throw new Error('My Error');
  })
  .catch(() => 1)
  .then((x) => x + 1)
  .then((x) => console.log(x))
  .catch((error) => console.log(error));

```
<details>
 <summary>Answer</summary>
<b>2</b>
</details>
<details>
 <summary>Explanation</summary>
<p>
  This code demonstrates a chain of <code>Promise</code> methods:
</p>
<ol>
  <li>
    It starts with <code>Promise.resolve(1)</code>, which resolves with the value <code>1</code>.
  </li>
  <li>
    The first <code>then</code> handler adds <code>1</code> to the resolved value, making it <code>2</code>.
  </li>
  <li>
    The next <code>then</code> handler throws an error with the message <code>'My Error'</code>.
  </li>
  <li>
    The <code>catch</code> block handles this error and returns <code>1</code>.
  </li>
  <li>
    The next <code>then</code> handler adds <code>1</code> again, making the value <code>2</code>.
  </li>
  <li>
    Finally, <code>console.log</code> outputs <code>2</code> to the console.
  </li>
</ol>
<p>
  If there were any error not caught earlier, the final <code>catch</code> would log it to the console.
</p>
</details>

---

16. **What will be the output?**

```javascript
console.log("1");

setTimeout(() => {
  console.log("2");
}, 10);

setTimeout(() => {
  console.log("3");
}, 0);

setTimeout(() => {
  console.log("4");
});

Promise.resolve()
  .then(() => {
    console.log("5");
  })
  .then(() => {
    console.log("6");
  });

console.log("7");


```
<details>
 <summary>Answer</summary>
<b>1</b><br/>
<b>7</b><br/>
<b>5</b><br/>
<b>6</b><br/>
<b>3</b><br/>
<b>4</b><br/>
<b>2</b><br/>
</details>
<details>
 <summary>Explanation</summary>
  <ol>
    <li><strong>Synchronous Code Execution:</strong>
      <ul>
        <li><code>console.log("1")</code> → Prints <code>1</code>.</li>
        <li><code>console.log("7")</code> → Prints <code>7</code>.</li>
      </ul>
    </li>
    <li><strong>Microtasks (Promises):</strong>
      <ul>
        <li><code>Promise.resolve().then(...)</code> queues a microtask.</li>
        <li><code>console.log("5")</code> → Prints <code>5</code>.</li>
        <li><code>console.log("6")</code> → Prints <code>6</code>.</li>
      </ul>
    </li>
    <li><strong>Macrotasks (setTimeout):</strong>
      <ul>
        <li><code>setTimeout(..., 0)</code> and <code>setTimeout(...)</code> (default 0) are macrotasks.</li>
        <li><code>console.log("3")</code> → Prints <code>3</code> (queued with <code>0ms</code> delay).</li>
        <li><code>console.log("4")</code> → Prints <code>4</code> (queued with <code>0ms</code> delay).</li>
        <li><code>console.log("2")</code> → Prints <code>2</code> (queued with <code>10ms</code> delay).</li>
      </ul>
    </li>
  </ol>
</details>

---

17. **What will be the output?**

```javascript
let x = { b: 1, c: 2 };
let y = Object.keys(x);
console.log(y.length);

```
<details>
 <summary>Answer</summary>
<b>2</b>
</details>
<details>
 <summary>Explanation</summary>
The code first creates an object x with two properties b and c, and assigns it to the variable x. Then, the Object.keys() method is used to retrieve an array of the keys of x, which are “b” and “c”. This array is assigned to the variable y.

Finally, the length of the array y (which is the number of keys in x) is printed to the console using console.log(). Since y has two elements, the output of y.length will be 2.
</details>

---

18. **What will be the output?**

```javascript
let x = '{ "b": 1, "c": 2 }';
let y = JSON.parse(x);
console.log(typeof y);

```
<details>
 <summary>Answer</summary>
<b>object</b>
</details>
<details>
 <summary>Explanation</summary>
<p>
  <strong>Explanation:</strong>
  The <code>JSON.parse(x)</code> method parses the JSON string <code>x</code> into a JavaScript object.
  The <code>typeof</code> operator applied to an object returns <code>"object"</code>.
</p>
</details>

---

19. **What will be the output?**

```javascript
let x = 0.1 + 0.2;
let y = 0.3;
console.log(x == y);

```
<details>
 <summary>Answer</summary>
<b>false</b>
</details>
<details>
 <summary>Explanation</summary>
<p>In JavaScript, numbers are represented as 64-bit floating-point numbers, which can lead to precision errors when performing arithmetic operations.</p>
    <ul>
        <li><code>0.1 + 0.2</code> results in <code>0.30000000000000004</code> due to floating-point precision issues.</li>
        <li><code>x == y</code> evaluates <code>0.30000000000000004 == 0.3</code>, which is <code>false</code>.</li>
    </ul>
</details>

---

20. **What will be the output?**

```javascript
let x = false;
let y = "0";
let z = 0;

console.log(x == y);
console.log(x == z);

```
<details>
 <summary>Answer</summary>
<b>true</b><br/>
<b>true</b>
</details>
<details>
 <summary>Explanation</summary>
   <ul>
        <li><strong>x == y (false == "0"):</strong>
            <ul>
                <li>Loose equality (<code>==</code>) causes type coercion.</li>
                <li><code>false</code> is coerced to the number <code>0</code>.</li>
                <li>The string <code>"0"</code> is also coerced to the number <code>0</code>.</li>
                <li>Now, the comparison becomes <code>0 == 0</code>, which is <code>true</code>.</li>
            </ul>
        </li>
        <li><strong>x == z (false == 0):</strong>
            <ul>
                <li><code>false</code> is coerced to the number <code>0</code>.</li>
                <li>The comparison becomes <code>0 == 0</code>, which is <code>true</code>.</li>
            </ul>
        </li>
    </ul>
</details>

---

21. **What will be the output?**

```javascript
let x = [];
console.log(Boolean(x));

```
<details>
 <summary>Answer</summary>
<b>true</b>
</details>
<details>
 <summary>Explanation</summary>
   <ul>
        <li>In JavaScript, an empty array <code>[]</code> is considered a <strong>truthy</strong> value.</li>
        <li>When converted to a boolean using <code>Boolean(x)</code>, it evaluates to <code>true</code>.</li>
        <li>This happens because arrays in JavaScript are objects, and all objects are truthy, regardless of their content.</li>
    </ul>
    <h3>Key Points:</h3>
    <ul>
        <li>An empty array <code>[]</code> is not <code>false</code> or <code>null</code>.</li>
        <li>It is treated as a valid object and hence is truthy.</li>
    </ul>
</details>

---

22. **What will be the output?**

```javascript
let x = Infinity;
console.log(typeof x);

```
<details>
 <summary>Answer</summary>
<b>number</b>
</details>
<details>
 <summary>Explanation</summary>
 In JavaScript, Infinity is a special numeric value that represents positive infinity. It is a primitive value of the number data type. When you use the typeof operator to check the type of x, it will return “number” because Infinity is a number value, albeit a special one.
</details>

