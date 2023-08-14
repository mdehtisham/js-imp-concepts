> What are the core differences of call, apply and bind?

Certainly! `call()`, `apply()`, and `bind()` are three methods in JavaScript that are used to manipulate the `this` value and call functions in different ways. Here are the core differences between them:

1.  **this Value and Invocation:**
    
    *   `call(thisArg, arg1, arg2, ...)`:
        *   Immediately invokes the function with the provided `thisArg` as the `this` value and any subsequent arguments as function arguments.
    *   `apply(thisArg, [argsArray])`:
        *   Immediately invokes the function with the provided `thisArg` as the `this` value and an array or array-like object (`argsArray`) as function arguments.
    *   `bind(thisArg, arg1, arg2, ...)`:
        *   Returns a new function with the provided `thisArg` as the `this` value and optional preset arguments. The new function can be invoked later.
2.  **Invocation Time:**
    
    *   `call()` and `apply()` invoke the function immediately.
    *   `bind()` returns a new function, which can be invoked later.
3.  **Arguments Passing:**
    
    *   `call()` and `bind()` allow you to pass individual arguments directly.
    *   `apply()` requires you to pass arguments in an array or array-like object.
4.  **Immediate vs Deferred Invocation:**
    
    *   `call()` and `apply()` immediately call the function with the specified arguments and `this` value.
    *   `bind()` returns a new function with the `this` value and optional arguments bound, allowing you to invoke the function at a later time.
5.  **Function Reusability:**
    
    *   `call()` and `apply()` are used for immediate function invocation and don't provide a reusable function like `bind()` does.
6.  **Usage Scenarios:**
    
    *   `call()` and `apply()` are useful when you want to invoke a function with a specific `this` value and a set of arguments, typically in scenarios where you are calling functions with different contexts or argument lists, such as with methods that are not directly tied to a specific object.
    *   `bind()` is commonly used when you want to create a new function with a specific `this` value and optionally preset arguments. This is useful for creating reusable functions or when passing functions as callbacks.
7.  **Examples:**
    
    javascript
    
    ```javascript
    const obj = { value: 42 };
    
    function displayValue(prefix) {
      console.log(prefix + this.value);
    }
    
    const boundDisplay = displayValue.bind(obj, "Value: ");
    boundDisplay();  // Outputs: Value: 42
    
    displayValue.call(obj, "Value: ");  // Outputs: Value: 42
    displayValue.apply(obj, ["Value: "]); // Outputs: Value: 42
    ```
    

In summary, `call()` and `apply()` are used for immediate invocation with specific `this` and arguments, while `bind()` is used to create new functions with a specific `this` context and optional arguments, which can be invoked later. Each method has its own use cases based on the desired behavior and requirements of your code.