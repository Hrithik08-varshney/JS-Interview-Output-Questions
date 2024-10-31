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
  <summary>Reason</summary>
 In this code, var is function-scoped, so i is not block-scoped and is shared across all iterations of the loop. By the time the setTimeout callbacks execute, the loop has completed, and i has been incremented to 3. As a result, each console.log(i) outputs 3.
</details>
