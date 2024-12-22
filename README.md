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

---

23. **What will be the output?**

```javascript
let x = "5";
let y = 2;

console.log(x + y);
console.log(x - y);
```
<details>
 <summary>Answer</summary>
<b>52</b><br/>
<b>3</b>
</details>
<details>
 <summary>Explanation</summary>
   <ol>
        <li>
            <strong><code>x + y</code></strong>:
            <ul>
                <li><code>x</code> is a string ("5"), and <code>y</code> is a number (2).</li>
                <li>The <code>+</code> operator performs <em>string concatenation</em> when one operand is a string.</li>
                <li>Result: <code>"5" + "2"</code> → <code>"52"</code> (string).</li>
            </ul>
        </li>
        <li>
            <strong><code>x - y</code></strong>:
            <ul>
                <li>The <code>-</code> operator attempts numeric conversion for both operands.</li>
                <li><code>"5"</code> is converted to the number <code>5</code>, and <code>2</code> remains as <code>2</code>.</li>
                <li>Result: <code>5 - 2</code> → <code>3</code> (number).</li>
            </ul>
        </li>
    </ol>
</details>

---

24. **What will be the output?**

```javascript
let a = () => {
  console.log(this);
};

a();
```
<details>
 <summary>Answer</summary>
<b>window</b>
</details>
<details>
 <summary>Explanation</summary>
  <h2>1. In the Browser (Global Scope):</h2>
  <ul>
    <li><code>this</code> in the global context refers to the <code>window</code> object.</li>
    <li><span class="output">Output:</span> <code>Window { ... }</code></li>
  </ul>
  <h2>2. In Node.js (Global Scope):</h2>
  <ul>
    <li><code>this</code> in the global context refers to an empty object (<code>{}</code>) in strict mode, which is the default for ES6 modules.</li>
    <li><span class="output">Output:</span> <code>{}</code></li>
  </ul>
  <p>Arrow functions inherit <code>this</code> from their surrounding scope, so its behavior varies based on where it is executed.</p>
</details>

---

25. **What will be the output?**

```javascript
let x = "hello";
let y = new String("hello");

console.log(x == y);
console.log(x === y);
```
<details>
 <summary>Answer</summary>
<b>true</b><br/><b>false</b>
</details>
<details>
 <summary>Explanation</summary>
 <h3>1. <code>x == y</code></h3>
    <p>The <code>==</code> operator performs type coercion. This means that the <code>String</code> object (<code>y</code>) is converted to a primitive string before comparison.</p>
    <p>After type coercion, both <code>x</code> and <code>y</code> are primitive strings with the value <code>"hello"</code>. Since their values are the same, the comparison returns <code>true</code>.</p>

    <h3>2. <code>x === y</code></h3>
    <p>The <code>===</code> operator does not perform type coercion. It checks for both value and type.</p>
    <p><code>x</code> is a primitive string, while <code>y</code> is a <code>String</code> object. Since their types are different, the comparison returns <code>false</code>.</p>
</body>
</details>

---

26. **What will be the output?**

```javascript
let x = [];
let y = [];
let z = x + y;

console.log(typeof z);
```
<details>
 <summary>Answer</summary>
<b>string</b>
</details>
<details>
 <summary>Explanation</summary>
 <ol>
        <li>
            <strong><code>x</code> and <code>y</code> are empty arrays (<code>[]</code>)</strong>: 
            When arrays are added using the <code>+</code> operator, JavaScript implicitly converts them to strings by calling their <code>toString()</code> method.
            <ul>
                <li><code>[].toString()</code> results in an empty string <code>""</code>.</li>
            </ul>
        </li>
        <li>
            <strong>Concatenation of two strings</strong>: 
            Adding two empty strings (<code>"" + ""</code>) results in another empty string <code>""</code>.
        </li>
        <li>
            <strong><code>typeof z</code></strong>: 
            The type of an empty string is <code>"string"</code>.
        </li>
    </ol>
</body>
</details>

---

27. **What will be the output?**

```javascript
let x = true;
let y = false;
let z = x + y && x * y;

console.log(z);
```
<details>
 <summary>Answer</summary>
<b>0</b>
</details>
<details>
 <summary>Explanation</summary>
  <ol>
        <li><strong>Initial Values:</strong>
            <ul>
                <li><code>x = true</code></li>
                <li><code>y = false</code></li>
            </ul>
        </li>
        <li><strong>Evaluate <code>x + y</code>:</strong>
            <ul>
                <li><code>true</code> is coerced to <code>1</code> and <code>false</code> to <code>0</code>.</li>
                <li><code>x + y = 1 + 0 = 1</code></li>
            </ul>
        </li>
        <li><strong>Evaluate <code>x * y</code>:</strong>
            <ul>
                <li><code>true</code> is coerced to <code>1</code> and <code>false</code> to <code>0</code>.</li>
                <li><code>x * y = 1 * 0 = 0</code></li>
            </ul>
        </li>
        <li><strong>Logical AND (<code>&&</code>):</strong>
            <ul>
                <li>The result of <code>x + y</code> is <code>1</code> (truthy).</li>
                <li>The result of <code>x * y</code> is <code>0</code>.</li>
                <li><code>1 && 0</code> returns <code>0</code>.</li>
            </ul>
        </li>
        <li><strong>Final Value:</strong>
            <ul>
                <li><code>z = 0</code></li>
            </ul>
        </li>
    </ol>
</body>
</details>

---

28. **What will be the output?**

```javascript
function foo(a, b) {
  console.log(arguments[1]);
}

foo(3);
```
<details>
 <summary>Answer</summary>
<b>undefined</b>
</details>
<details>
 <summary>Explanation</summary>
<ol>
  <li>
    The function <code>foo</code> is called with only <strong>one argument</strong> (<code>3</code>), so <code>arguments[1]</code> does not exist.
  </li>
  <li>
    Since <code>arguments[1]</code> refers to the second argument passed to the function and no such argument was provided, its value is <code>undefined</code>.
  </li>
</ol>
</details>

---

29. **What will be the output?**

```javascript
let x = "false";
let y = !x;

console.log(y);
```
<details>
 <summary>Answer</summary>
<b>false</b>
</details>
<details>
 <summary>Explanation</summary>
In this code, x is a string containing the value “false”. When you use the logical NOT operator (!) with a non-Boolean value, JavaScript will first convert the value to a Boolean and then negate it. Since “false” is a non-empty string, it is considered a truthy value when converted to Boolean, so !x will be the same as !true, which is false.

Therefore, when y is logged into the console, it will output false.
</details>

---

30. **What will be the output?**

```javascript
let x = 1;
let y = "1";

console.log(++x, ++y);
```
<details>
 <summary>Answer</summary>
<b>2, 2</b>
</details>
<details>
 <summary>Explanation</summary>
<ol>
        <li>
            <strong><code>++x</code></strong>:
            <ul>
                <li>The <code>++</code> operator increments the value of <code>x</code> by 1.</li>
                <li>Since <code>x</code> is initially <code>1</code>, it becomes <code>2</code>.</li>
                <li>The result is <code>2</code>.</li>
            </ul>
        </li>
        <li>
            <strong><code>++y</code></strong>:
            <ul>
                <li>The <code>++</code> operator attempts to increment the value of <code>y</code>.</li>
                <li>Here, <code>y</code> is a string (<code>"1"</code>).</li>
                <li>JavaScript implicitly converts <code>"1"</code> to a number (<code>1</code>), increments it by 1, and then assigns the result back to <code>y</code>.</li>
                <li>So, <code>y</code> becomes the number <code>2</code>.</li>
                <li>The result is <code>2</code>.</li>
            </ul>
        </li>
    </ol>
    <h2>Final Values:</h2>
    <ul>
        <li><code>x = 2</code> (number)</li>
        <li><code>y = 2</code> (number)</li>
    </ul>
</details>

---

31. **What will be the output?**

```javascript
var num = 8;
var num = 10;

console.log(num);
```
<details>
 <summary>Answer</summary>
<b>10</b>
</details>
<details>
 <summary>Explanation</summary>
 <p>
        In JavaScript, when using <code>var</code>, variables can be re-declared within the same scope. Here's what happens in the given code:
    </p>
    <ol>
        <li><code>var num = 8;</code>: Declares the variable <code>num</code> and assigns it the value <code>8</code>.</li>
        <li><code>var num = 10;</code>: Redeclares the variable <code>num</code> and assigns it the value <code>10</code>.</li>
    </ol>
    <p>
        The final value of <code>num</code> is <code>10</code>, which is logged to the console.
    </p>
    <p>
        To prevent re-declaration, you can use <code>let</code> or <code>const</code> instead of <code>var</code>.
    </p>
</details>

---

32. **What will be the output?**

```javascript
let x = "b";
let y = "a";

console.log(x + y + + y + y);
```
<details>
 <summary>Answer</summary>
<b>baNaNa</b>
</details>
<details>
 <summary>Explanation</summary>
    <ol>
        <li><code>x</code> is assigned the string <code>"b"</code>, and <code>y</code> is assigned the string <code>"a"</code>.</li>
        <li><code>x + y</code>: Concatenates <code>"b"</code> and <code>"a"</code>, resulting in <code>"ba"</code>.</li>
        <li><code>+y</code>: The unary <code>+</code> operator attempts to convert <code>"a"</code> into a number. 
            Since <code>"a"</code> is not a valid number, the result is <code>NaN</code> (Not-a-Number).</li>
        <li><code>x + y + +y + y</code>: 
            <ul>
                <li>Expands to <code>"ba" + NaN + "a"</code>.</li>
                <li>String concatenation occurs, resulting in <code>"baNaN"</code>.</li>
            </ul>
        </li>
    </ol>
</details>

---

33. **What will be the output?**

```javascript
console.log(x);

var x;
```
<details>
 <summary>Answer</summary>
<b>undefined</b>
</details>
<details>
 <summary>Explanation</summary>
 <ol>
    <li><strong>Variable Hoisting:</strong> 
        In JavaScript, variable declarations using <code>var</code> are moved to the top of their scope during the compilation phase. However, the initialization (if any) remains in place.
    </li>
    <li><strong>Execution:</strong>
      <ul>
        <li>The declaration <code>var x;</code> is hoisted to the top.</li>
        <li>Before the variable is initialized, its value is <code>undefined</code>.</li>
        <li>When <code>console.log(x);</code> is executed, it logs <code>undefined</code>.</li>
      </ul>
    </li>
  </ol>
</details>

---

34. **What will be the output?**

```javascript
let x = true + true;
let y = x + false;

console.log(y);
```
<details>
 <summary>Answer</summary>
<b>2</b>
</details>
<details>
 <summary>Explanation</summary>
 <ol>
    <li>
      <strong>Step 1:</strong> <code>let x = true + true;</code><br>
      - The <code>+</code> operator converts boolean values to numbers.<br>
      - <code>true</code> becomes <code>1</code>, so <code>true + true</code> is equivalent to <code>1 + 1</code>.<br>
      - Result: <code>x = 2</code>.
    </li>
    <li>
      <strong>Step 2:</strong> <code>let y = x + false;</code><br>
      - <code>x</code> is <code>2</code> from Step 1.<br>
      - <code>false</code> is converted to <code>0</code>, so <code>x + false</code> is equivalent to <code>2 + 0</code>.<br>
      - Result: <code>y = 2</code>.
    </li>
    <li>
      <strong>Step 3:</strong> <code>console.log(y);</code><br>
      - The value of <code>y</code> is <code>2</code>, so it logs: <strong>2</strong>.
    </li>
  </ol>
</details>

---

35. **What will be the output?**

```javascript
let x = [2];
let y = 2;

console.log(x == y);
```
<details>
 <summary>Answer</summary>
<b>true</b>
</details>
<details>
 <summary>Explanation</summary>
   <ul>
        <li><code>x</code> is an array with a single element <code>[2]</code>.</li>
        <li><code>y</code> is a number <code>2</code>.</li>
        <li>
            When using <code>==</code> (loose equality), JavaScript performs type coercion to compare the values.
            <ul>
                <li>The array <code>[2]</code> is converted to a string <code>"2"</code> (via <code>.toString()</code>).</li>
                <li>The string <code>"2"</code> is then coerced into a number <code>2</code>.</li>
            </ul>
        </li>
        <li>As a result, the comparison <code>2 == 2</code> evaluates to <code>true</code>.</li>
    </ul>
</details>

---

36. **What will be the output?**

```javascript
const a = { b: { c: 2 } };
const b = { ...a };
a.b.c = 3;

console.log(b.b.c);
```
<details>
 <summary>Answer</summary>
<b>3</b>
</details>
<details>
 <summary>Explanation</summary>
   <ol>
        <li>
            <strong>Object Spread (<code>{ ...a }</code>):</strong>
            <p>The spread operator creates a <strong>shallow copy</strong> of the <code>a</code> object. 
            This means only the first level of properties is copied, and deeper levels (nested objects) 
            are still referenced.</p>
        </li>
        <li>
            <strong>Modification of <code>a.b.c</code>:</strong>
            <p>The <code>b</code> property of <code>a</code> is an object. Since <code>b</code> is a reference 
            to the same object in both <code>a</code> and <code>b</code> (due to the shallow copy), modifying 
            <code>a.b.c</code> also affects <code>b.b.c</code>.</p>
        </li>
    </ol>
    <p>Thus, when you log <code>b.b.c</code>, it reflects the updated value (<code>3</code>).</p>
</details>

---

37. **What will be the output?**

```javascript
let x = [1, 2, 3];
let [, , y] = x;

console.log(y);
```
<details>
 <summary>Answer</summary>
<b>3</b>
</details>
<details>
 <summary>Explanation</summary>
    <ul>
        <li><code>let x = [1, 2, 3];</code> initializes an array <code>x</code> with the values <code>[1, 2, 3]</code>.</li>
        <li><code>let [, , y] = x;</code> uses <b>array destructuring</b> to assign the third element of <code>x</code> to the variable <code>y</code>. 
            The commas <code>, ,</code> are used to skip the first two elements.
        </li>
        <li><code>console.log(y);</code> prints the value of <code>y</code>, which is <code>3</code>.</li>
    </ul>
</details>

---

38. **What will be the output?**

```javascript
let x = { a: 1, b: 2 };
let y = { b: 3 };
let z = { ...x, ...y };

console.log(z);
```
<details>
 <summary>Answer</summary>
<b>{ a: 1, b: 3 }</b>
</details>
<details>
 <summary>Explanation</summary>
  <ul>
        <li>The <code>...</code> (spread operator) copies properties from one object into another.</li>
        <li>When <code>z</code> is created, the properties from <code>x</code> (<code>{ a: 1, b: 2 }</code>) are spread into it first.</li>
        <li>Next, the properties from <code>y</code> (<code>{ b: 3 }</code>) are spread into <code>z</code>. Since <code>b</code> already exists in <code>z</code>, it gets overwritten by the value from <code>y</code> (<code>3</code>).</li>
        <li>The final object is <code>{ a: 1, b: 3 }</code>.</li>
    </ul>
</details>

---

39. **What will be the output?**

```javascript
let x = [1, 2, 3, 5];

x.forEach((e) => {
  if (e > 2 && e < 5) return;
  console.log(e);
});
```
<details>
 <summary>Answer</summary>
<b>1</b>
<b>2</b>
<b>5</b>
</details>
<details>
 <summary>Explanation</summary>
  <ul>
    <li>
      For <code>e = 1</code> and <code>e = 2</code>, the condition <code>(e > 2 && e < 5)</code> is <code>false</code>,
      so <code>console.log(e)</code> runs, and the values <strong>1</strong> and <strong>2</strong> are logged.
    </li>
    <li>
      For <code>e = 3</code>, the condition <code>(e > 2 && e < 5)</code> is <code>true</code>, so <code>return</code>
      is executed, skipping <code>console.log(e)</code> for this iteration.
    </li>
    <li>
      For <code>e = 5</code>, the condition <code>(e > 2 && e < 5)</code> is <code>false</code>, so <code>console.log(e)</code>
      runs, logging <strong>5</strong>.
    </li>
  </ul>
</details>

---

40. **What will be the output?**

```javascript
let x = 10;
let y = 20;

console.log("total = " + x + y);
```
<details>
 <summary>Answer</summary>
<b>total = 1020</b>
</details>
<details>
 <summary>Explanation</summary>
     <ol>
        <li>
            In the expression <code>"total = " + x + y</code>, JavaScript performs 
            <strong>string concatenation</strong>.
        </li>
        <li>
            <code>"total = "</code> is a string. When the <code>+</code> operator is used 
            with a string and a number, the number is converted to a string and concatenated.
        </li>
        <li>
            First, <code>"total = " + x</code> results in the string <code>"total = 10"</code>.
        </li>
        <li>
            Then, <code>"total = 10" + y</code> results in the string <code>"total = 1020"</code>.
        </li>
    </ol>
</details>

---

41. **What will be the output?**

```javascript
let x = 5;
let y = 6;
x += x > y ? x : y;

console.log(x);
```
<details>
 <summary>Answer</summary>
<b>total = 1020</b>
</details>
<details>
 <summary>Explanation</summary>
 <ol>
        <li><strong>Initialization:</strong>
            <ul>
                <li><code>x</code> is initialized to <code>5</code>.</li>
                <li><code>y</code> is initialized to <code>6</code>.</li>
            </ul>
        </li>
        <li><strong>Conditional (ternary) operator:</strong>
            <ul>
                <li>The condition <code>x > y</code> is evaluated:</li>
                <li><code>x</code> is <code>5</code>, <code>y</code> is <code>6</code>.</li>
                <li>Since <code>5 > 6</code> is <strong>false</strong>, the result of the ternary expression is <code>y</code>, which is <code>6</code>.</li>
            </ul>
        </li>
        <li><strong>Update <code>x</code>:</strong>
            <ul>
                <li>The <code>+=</code> operator means <code>x = x + (result of ternary expression)</code>.</li>
                <li>Substitute the values: <code>x = 5 + 6</code>.</li>
                <li>Now, <code>x</code> becomes <code>11</code>.</li>
            </ul>
        </li>
    </ol>
</details>

---

42. **What will be the output?**

```javascript
let a = [1, 2, 3];
a.push(a[2]++);

console.log(a);
```
<details>
 <summary>Answer</summary>
<b>[ 1, 2, 4, 3 ]</b>
</details>
<details>
 <summary>Explanation</summary>
 <ol>
        <li>
            <strong>Initial value of <code>a</code>:</strong>
            <pre>a = [1, 2, 3]</pre>
        </li>
        <li>
            <strong>Expression <code>a.push(a[2]++)</code>:</strong>
            <ul>
                <li>
                    <code>a[2]++</code> retrieves the value of <code>a[2]</code> (which is <code>3</code>) 
                    <strong>before</strong> incrementing it. So, <code>a[2]++</code> evaluates to <code>3</code>.
                </li>
                <li>The <code>push</code> method adds this value (<code>3</code>) to the end of the array.</li>
            </ul>
        </li>
        <li>
            <strong>After <code>a.push(a[2]++)</code>:</strong>
            <pre>a = [1, 2, 3, 3]</pre>
        </li>
        <li>
            <strong>Increment operation:</strong>
            <ul>
                <li>The value of <code>a[2]</code> is incremented from <code>3</code> to <code>4</code>.</li>
            </ul>
        </li>
        <li>
            <strong>Final value of <code>a</code>:</strong>
            <pre>a = [1, 2, 4, 3]</pre>
        </li>
    </ol>
</details>

---

43. **What will be the output?**

```javascript
let x = {
  y: "z",
  print: () => {
    return this.y === "z";
  },
};

console.log(x.print());
```
<details>
 <summary>Answer</summary>
<b>false</b>
</details>
<details>
 <summary>Explanation</summary>
<ul>
    <li><strong>Arrow Functions and `this`:</strong> Arrow functions in JavaScript do not have their own `this` context. Instead, they inherit `this` from the surrounding lexical scope where the function was created. In this case, the arrow function inside the object `x` inherits the `this` from the global scope.</li>
    <li><strong>Global `this`:</strong> In a browser (non-strict mode), `this` inside the arrow function refers to the global object (the `window` object). In strict mode or in Node.js, `this` would be `undefined`.</li>
  </ul>

  <h2>Why the Code Outputs `false`:</h2>
  <p>In non-strict mode (browser), `this` inside the arrow function refers to the global `window` object, which doesn't have a property `y`. Therefore, `this.y === "z"` evaluates to <code>false</code>.</p>
  
  <p>In strict mode or in Node.js, `this` would be `undefined`, and attempting to access <code>this.y</code> would result in a <code>TypeError</code>.</p>
</details>

---

44. **What will be the output?**

```javascript
let x = 1;

console.log(x + x++);
```
<details>
 <summary>Answer</summary>
<b>2</b>
</details>
<details>
 <summary>Explanation</summary>
    <ol>
        <li><strong>Initial value of <code>x</code>:</strong> The variable <code>x</code> is initialized to <code>1</code>.</li>
        <li><strong>Expression evaluation:</strong>
            <ul>
                <li>The <code>x++</code> is a <span class="highlight">post-increment operator</span>, meaning it returns the value of <code>x</code> <strong>before</strong> incrementing.</li>
                <li>The expression <code>x + x++</code> is evaluated as:
                    <ul>
                        <li>Take the current value of <code>x</code> (<code>1</code>).</li>
                        <li>Add the value of <code>x</code> <strong>before</strong> it is incremented (<code>1</code>).</li>
                        <li>So, the result is <code>1 + 1 = 2</code>.</li>
                    </ul>
                </li>
            </ul>
        </li>
        <li><strong>Post-expression value of <code>x</code>:</strong> After the evaluation, <code>x</code> is incremented by <code>1</code>, so its new value becomes <code>2</code>.</li>
    </ol>
</details>

---

45. **What will be the output?**

```javascript
let x = 6;
let y = typeof (x == 6);

console.log(y);
```
<details>
 <summary>Answer</summary>
<b>boolean</b>
</details>
<details>
 <summary>Explanation</summary>
   In this code, the expression (x == 6) uses the equality operator == to compare the value of x with the number 6. Since x has the value 6, the expression evaluates to true. 

The typeof operator is then used to determine the data type of the result of the expression (x == 6), which is a boolean value. The typeof operator returns a string that represents the data type of its operand. 

The string “boolean” has a length of 7. Therefore, the value of y is “boolean”. 

Therefore, the output of console.log(y) will be “boolean”.
</details>

---

46. **What will be the output?**

```javascript
let x = "5";
let y = 3;

console.log(x - y);
```
<details>
 <summary>Answer</summary>
<b>2</b>
</details>
<details>
 <summary>Explanation</summary>
In this code, the – operator is used to subtract the value of y from the value of x. When the – operator is used with a string and a number, the string is automatically converted to a number before the subtraction operation is performed. So the string “5” is converted to the number 5. Then, the expression x – y evaluates to 5 – 3, which is 2. 

Therefore, the output of console.log(x – y) will be 2.
</details>
