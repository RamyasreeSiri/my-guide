# TypeScript

## Topics to cover

Design priciples
Best practices

## Quiz

* Define a function which adds two numbers and returns the result after given time using promises

 <details>
 <summary>Solution</summary>

 function timer(n) {
   return new Promise((resolve) => setTimeout(resolve, n));
 }
 async function add(a, b) {
   await timer(500);
   return a+b;
 }
 (async function() {
 console.log(await add(2,3));
 })()
 </details>

## Notes
