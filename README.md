## **🗓️ Week 1: JavaScript Foundations for DSA**

### **Day 1: Variables, Data Types, and I/O**

#### **Core Concepts**
* ✅ Learn `var`, `let`, `const`
* ✅ Understand primitive data types (number, string, boolean, null, undefined, symbol, bigint)
* ✅ Practice `prompt()` and `console.log()`
* ✅ Convert between data types (type coercion vs type conversion)
* ✅ Understand hoisting behavior
* ✅ Learn about temporal dead zone (TDZ)

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **What's the difference between `var`, `let`, and `const`?**
   - **Scope**: `var` is function-scoped, `let`/`const` are block-scoped
   - **Hoisting**: All are hoisted, but `var` initialized with `undefined`, `let`/`const` stay uninitialized (TDZ)
   - **Re-declaration**: `var` allows re-declaration, `let`/`const` don't
   - **Re-assignment**: `var`/`let` allow it, `const` doesn't
   - **Global object**: `var` creates property on global object, `let`/`const` don't
   - **Temporal Dead Zone**: `let`/`const` have TDZ, `var` doesn't

2. **What are the primitive data types in JavaScript?**
   - **7 Primitives**: Number, String, Boolean, Undefined, Null, Symbol, BigInt
   - **Immutable**: Cannot be changed, only replaced
   - **Passed by value**: Copy of value is passed
   - **vs Reference types**: Objects, Arrays, Functions (passed by reference)
   - **Wrapper objects**: Primitives have temporary wrapper objects (String, Number, Boolean)

3. **What is hoisting? How does it work with variables?**
   - **Definition**: Moving declarations to top of scope during compilation
   - **Variable hoisting**: Declarations hoisted, initializations stay in place
   - **`var` behavior**: Hoisted and initialized with `undefined`
   - **`let`/`const` behavior**: Hoisted but not initialized (TDZ)
   - **Function hoisting**: Function declarations fully hoisted
   - **Class hoisting**: Classes are hoisted but not initialized

4. **What's the difference between `null` and `undefined`?**
   - **`undefined`**: Variable declared but not assigned, missing property, no return value
   - **`null`**: Intentional absence of value, must be assigned explicitly
   - **`typeof undefined`**: `'undefined'`
   - **`typeof null`**: `'object'` (JavaScript bug)
   - **Equality**: `null == undefined` is `true`, `null === undefined` is `false`

5. **What is type coercion? Explain implicit vs explicit conversion**
   - **Implicit coercion**: JavaScript automatically converts types
     - `'5' + 3` → `'53'` (number to string)
     - `'5' - 3` → `2` (string to number)
     - `true + 1` → `2` (boolean to number)
   - **Explicit conversion**: Manual conversion using constructors
     - `Number('5')`, `String(123)`, `Boolean(0)`
   - **Common pitfalls**: `[] + []` → `''`, `[] + {}` → `'[object Object]'`

6. **What does `typeof null` return and why?**
   - Returns `'object'` (bug from JavaScript's first version)
   - In JavaScript's initial implementation, values were represented by type tag + value
   - Objects had type tag 0, and `null` was represented as NULL pointer (0x00)
   - This bug was never fixed for backwards compatibility

7. **Explain truthy and falsy values in JavaScript**
   - **Falsy (8 values)**: `false`, `0`, `-0`, `0n`, `''`, `null`, `undefined`, `NaN`
   - **Truthy**: Everything else (including `'0'`, `'false'`, `[]`, `{}`, `function(){}`)
   - **Use in conditions**: `if (value)` checks truthiness
   - **Double negation**: `!!value` converts to boolean

8. **What is NaN? How do you check for it?**
   - **Meaning**: "Not a Number" - result of invalid numeric operation
   - **Type**: `typeof NaN` is `'number'`
   - **Unique property**: `NaN !== NaN` (only value not equal to itself)
   - **Checking**: `Number.isNaN(value)` (recommended) or `isNaN(value)`
   - **Difference**: `isNaN()` coerces, `Number.isNaN()` doesn't
   - **Examples**: `0/0`, `parseInt('abc')`, `Math.sqrt(-1)`

**Intermediate Level:**
9. **What is the Temporal Dead Zone (TDZ)?**
   - Time between entering scope and variable declaration
   - Accessing variable in TDZ throws ReferenceError
   - Only applies to `let`, `const`, and `class`
   - Exists to catch errors and ensure predictable behavior

10. **Explain the difference between `==` and `===`**
    - **`==` (loose equality)**: Compares with type coercion
    - **`===` (strict equality)**: Compares without type coercion
    - **Common pitfalls**: `'0' == 0` is `true`, `null == undefined` is `true`
    - **Best practice**: Always use `===` unless you specifically need coercion

11. **What is the difference between primitive and reference types?**
    - **Primitives**: Stored in stack, immutable, compared by value
    - **References**: Stored in heap, mutable, compared by reference
    - **Assignment**: Primitives copy value, references copy reference
    - **Equality**: `[1] === [1]` is `false`, `1 === 1` is `true`

12. **Explain `undefined` vs `not defined` vs `undeclared`**
    - **`undefined`**: Variable declared but not assigned a value
    - **`not defined`**: ReferenceError - variable not declared
    - **`undeclared`**: Variable used without declaration in non-strict mode

13. **What are JavaScript's special numeric values?**
    - **`Infinity`**: Result of division by zero (positive)
    - **`-Infinity`**: Negative infinity
    - **`NaN`**: Invalid numeric operation
    - **`Number.MAX_VALUE`**: Largest representable number
    - **`Number.MIN_VALUE`**: Smallest positive number
    - **`Number.EPSILON`**: Smallest difference between two numbers

14. **What is the difference between `Number()` and `parseInt()`?**
    - **`Number()`**: Strict conversion, `Number('123abc')` → `NaN`
    - **`parseInt()`**: Parses until non-digit, `parseInt('123abc')` → `123`
    - **Radix**: `parseInt()` accepts radix parameter
    - **Whitespace**: Both ignore leading/trailing whitespace

15. **Explain variable shadowing**
    - Inner variable with same name as outer variable
    - Inner variable "shadows" outer one in its scope
    - Can lead to confusion and bugs
    - `let` prevents accidental shadowing in same scope

**Advanced Level:**
16. **What happens with duplicate variable declarations?**
    - **`var`**: Ignored (no error), keeps existing value
    - **`let`/`const`**: SyntaxError in same scope
    - **Different scopes**: Creates new variable in inner scope

17. **Explain JavaScript's number precision issues**
    - Uses IEEE 754 double-precision floating-point
    - `0.1 + 0.2 !== 0.3` (precision error)
    - Use `Number.EPSILON` for comparison
    - BigInt for large integers beyond `Number.MAX_SAFE_INTEGER`

18. **What is the difference between `isNaN()` and `Number.isNaN()`?**
    - **`isNaN()`**: Coerces to number first, `isNaN('hello')` → `true`
    - **`Number.isNaN()`**: No coercion, `Number.isNaN('hello')` → `false`
    - **Recommendation**: Use `Number.isNaN()` for accurate checking

19. **How does JavaScript handle automatic semicolon insertion (ASI)?**
    - Parser automatically inserts semicolons in certain situations
    - Can lead to unexpected behavior
    - Example: `return\n{value: 1}` becomes `return;`
    - Best practice: Always use explicit semicolons

20. **What is `use strict` and how does it affect variables?**
    - Enables strict mode - catches common errors
    - Prevents accidental global variables
    - Disallows duplicate parameter names
    - Makes `this` undefined in functions (not global object)
    - Cannot delete variables

#### **Behavioral & Experience-Based Questions**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Behavioral Questions:**
1. **"Tell me about a time a type-related bug caused an issue in your project. How did you find and fix it?"**
   - *STAR hint*: Think about API returning `"true"` (string) instead of `true` (boolean), or `null` breaking `.length`. Describe the user impact, how you debugged it (console, breakpoints), what you changed (type guard / explicit conversion), and what you added to prevent it (validation layer, unit test).

2. **"Describe a situation where you had to refactor code because of poor variable scoping. What was the impact?"**
   - *STAR hint*: Classic `var` in a loop causing closure/stale-value bugs, or a `let` declared in wrong scope. Mention the specific symptom, how you traced it to a scope issue, and how the refactor improved predictability.

3. **"Have you ever had a production crash caused by `null` or `undefined`? Walk me through what happened."**
   - *STAR hint*: Optional chaining (`?.`) came up, or a missing API field. Describe the symptom (crash/error), how you found the root cause, the fix (null check / default value), and process improvement (add input validation at API boundary).

**Experience-Based Conceptual:**
4. **"In your React projects, how do you ensure API response data has the right type before rendering a component?"**
   - *Answer framework*: Runtime validation function at fetch layer, optional chaining for safe access, default props / default values, TypeScript if used. Mention a specific case from Shopify or Airtable work.

5. **"Shopify webhook sends `total_price` as a string like `"29.99"`. How do you handle this safely across your codebase without scattered `parseFloat()` calls everywhere?"**
   - *Answer framework*: Centralized API response transformer/normalizer function called once at the boundary (e.g., `normalizeOrder(rawWebhookPayload)`), converts types before data enters state/components.

6. **"You're integrating Airtable API and a field expected to be a number comes back as `null` for some records. How do you handle this at scale?"**
   - *Answer framework*: Nullish coalescing (`?? 0`), a field-level validator that runs on all records, logs a warning for unexpected nulls, never lets `null` propagate into arithmetic or `.toString()` calls.

#### **Programming Tasks (Basic)**
* ✅ Task 1: Create a user info prompt
* ✅ Task 2: Swap two numbers (with and without temp variable)
* ✅ Task 3: Convert Celsius to Fahrenheit
* ✅ Task 4: Sum of two numbers from prompt
* ✅ Task 5: Check if a number is even
* ✅ Task 6: Calculate area of a circle
* ✅ Task 7: String interpolation with variables
* ✅ Task 8: Use `typeof` to check types
* ✅ Task 9: Create a simple interest calculator
* ✅ Task 10: Create a BMI calculator

#### **Interview Coding Tasks**

**Hoisting & Scope:**
* ✅ Task 11: Demonstrate hoisting with `var`, `let`, and `const`
* ✅ Task 12: Show Temporal Dead Zone with practical examples
* ✅ Task 13: Demonstrate variable shadowing in nested scopes
* ✅ Task 14: Create examples showing function vs block scope

**Type Coercion & Conversion:**
* ✅ Task 15: Show 10 examples of type coercion edge cases (tricky ones)
* ✅ Task 16: Demonstrate difference between `==` and `===` with 10 examples
* ✅ Task 17: Write a program to safely convert string to number with validation
* ✅ Task 18: Create a function that handles all falsy values differently
* ✅ Task 19: Implement a type checker that categorizes primitive vs reference types
* ✅ Task 20: Show examples of implicit type coercion in arithmetic operations

**NaN & Special Values:**
* ✅ Task 21: Check if a variable is NaN without using isNaN() (hint: use NaN !== NaN)
* ✅ Task 22: Demonstrate difference between `isNaN()` and `Number.isNaN()`
* ✅ Task 23: Handle `Infinity`, `-Infinity`, and `NaN` in calculations
* ✅ Task 24: Write a safe division function that handles edge cases

**Truthy/Falsy & Boolean:**
* ✅ Task 25: Create a function to check if a value is truthy or falsy
* ✅ Task 26: Implement custom truthiness checker with explanations
* ✅ Task 27: Use `!!` operator to convert various values to boolean
* ✅ Task 28: Short-circuit evaluation examples (`&&` and `||`)

**Number Operations:**
* ✅ Task 29: Demonstrate floating-point precision issues (0.1 + 0.2)
* ✅ Task 30: Use `Number.EPSILON` to compare floating-point numbers
* ✅ Task 31: Work with `BigInt` for large number calculations
* ✅ Task 32: Check if number is safe integer using `Number.isSafeInteger()`

**Type Conversion Challenges:**
* ✅ Task 33: Implement `parseInt()` with different radix values
* ✅ Task 34: Compare `Number()`, `parseInt()`, and `parseFloat()` behaviors
* ✅ Task 35: Convert various data types to string (explicit vs implicit)
* ✅ Task 36: Handle edge cases in type conversion (null, undefined, objects)

**Practical Challenges:**
* ✅ Task 37: Find the data type of multiple values and store in an array
* ✅ Task 38: Swap two numbers (with and without temp variable)
* ✅ Task 39: Swap three variables in a circular manner (a→b, b→c, c→a)
* ✅ Task 40: Create a temperature converter (C↔F↔K) with validation
* ✅ Task 41: Parse and validate user input (handle all edge cases)
* ✅ Task 42: Implement a calculator that handles type coercion correctly
* ✅ Task 43: Create a value comparator that explains why values are equal/unequal
* ✅ Task 44: Build a type coercion visualizer/debugger
* ✅ Task 45: Handle `null` and `undefined` gracefully in operations

**Advanced Challenges:**
* ✅ Task 46: Demonstrate automatic semicolon insertion (ASI) pitfalls
* ✅ Task 47: Create strict mode vs non-strict mode comparison examples
* ✅ Task 48: Show memory difference between primitives and references
* ✅ Task 49: Implement Object.is() polyfill (handles NaN and -0)
* ✅ Task 50: Create a comprehensive type-checking utility function

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Build a contact form that collects name, email, phone — validate each field's data type before submission (no empty strings, phone must be numeric)
* ⬜ RW-2: Read a Shopify product JSON response and `console.log` the JS type of each field (`price` as string, `available` as boolean, `images` as array)

**React / Next.js:**
* ⬜ RW-3: Create a React component that accepts a `product` prop — use type guards (`typeof`, nullish check) to avoid rendering errors when `product` is `null`/`undefined`
* ⬜ RW-4: In a Next.js API route, validate incoming query params — ensure `page` coerces to a number, `q` defaults to empty string if missing

**Airtable API:**
* ⬜ RW-5: Fetch Airtable records and log the JS type of each field (linked record = array, date = string, checkbox = boolean) — build a field-type report object
* ⬜ RW-6: Write a type normalizer — convert Airtable field values to correct JS types before storing in state (`"true"` → `true`, `"42"` → `42`)

**Shopify:**
* ⬜ RW-7: Parse a Shopify webhook payload — verify types of `total_price` (comes as string!), `line_items` (array), `customer` (object or null), handle each safely
* ⬜ RW-8: Build a price formatter: input may be string `"29.99"` or number `29.99` — output a consistent `"$29.99"` currency string using explicit type conversion

**Laravel / Python Flask:**
* ⬜ RW-9: Simulate a Laravel JSON API response in pure JS — parse it and validate all expected fields exist and have correct types before using them
* ⬜ RW-10: Build a Flask-style input validator in pure JS: check request body fields have correct types, return `{field, error}` array for any that fail

### **Day 2: Loops and Conditionals**

#### **Core Concepts**
* ✅ Learn `if`, `else`, `else if`, ternary operator
* ✅ Understand `for`, `while`, `do...while` loops
* ✅ Practice nested loops
* ✅ Learn `break` and `continue` statements
* ✅ Understand `switch` statement
* ✅ Learn `for...in` and `for...of` loops

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **What's the difference between `==` and `===`?**
   - **`==` (Abstract Equality)**: Compares with type coercion
   - **`===` (Strict Equality)**: Compares without type coercion
   - **Examples**: `5 == '5'` → `true`, `5 === '5'` → `false`
   - **Coercion rules**: Complex algorithm (check both types, convert, compare)
   - **Best practice**: Always use `===` to avoid unexpected behavior

2. **Explain the difference between `for`, `while`, and `do...while` loops**
   - **`for` loop**: Use when iterations are known, compact syntax
   - **`while` loop**: Condition checked before execution, may never run
   - **`do...while` loop**: Condition checked after execution, runs at least once
   - **Use cases**: `for` (arrays), `while` (unknown iterations), `do...while` (user input)

3. **What is the difference between `break` and `continue`?**
   - **`break`**: Exits loop entirely, control goes to next statement after loop
   - **`continue`**: Skips current iteration, continues with next iteration
   - **Labeled statements**: Can break/continue outer loops with labels
   - **Switch**: `break` prevents fall-through in switch cases

4. **What is a switch statement and when would you use it?**
   - **Purpose**: Multiple conditions on same variable
   - **Syntax**: `switch(expr) { case val: ... break; default: ... }`
   - **Fall-through**: Without `break`, execution continues to next case
   - **When to use**: Multiple discrete values, more readable than if-else chains
   - **Limitations**: Only equality check, no complex conditions

5. **Explain short-circuit evaluation in logical operators**
   - **`&&` (AND)**: Returns first falsy value or last value if all truthy
   - **`||` (OR)**: Returns first truthy value or last value if all falsy
   - **Short-circuit**: Stops evaluation once result is determined
   - **Use cases**: Default values, conditional execution, guard clauses
   - **Examples**: `user && user.name`, `value || 'default'`

6. **What's the difference between `for...in` and `for...of`?**
   - **`for...in`**: Iterates over enumerable property **keys** (including prototype)
   - **`for...of`**: Iterates over iterable object **values** (arrays, strings, maps, sets)
   - **Arrays**: Use `for...of` for values, avoid `for...in` (gets indices + inherited)
   - **Objects**: Use `for...in` (objects not iterable by default)
   - **Performance**: `for...of` generally faster for arrays

7. **Explain the ternary operator and when to use it**
   - **Syntax**: `condition ? expressionIfTrue : expressionIfFalse`
   - **Returns value**: Unlike if-else, ternary is an expression
   - **When to use**: Simple conditions, inline assignments
   - **When to avoid**: Nested ternaries (hard to read), complex logic
   - **Example**: `const status = age >= 18 ? 'adult' : 'minor'`

8. **What happens when you compare different data types?**
   - **With `===`**: Always false if types differ
   - **With `==`**: Type coercion occurs (complex algorithm)
   - **Common cases**: String to number, boolean to number, null to undefined
   - **Pitfalls**: `[] == ![]` → `true`, `'' == 0` → `true`

**Intermediate Level:**
9. **What are labeled statements in JavaScript?**
   - Label any statement to reference it with `break` or `continue`
   - Useful for breaking out of nested loops
   - Syntax: `labelName: statement`
   - Example: `outerLoop: for(...) { innerLoop: for(...) { break outerLoop; } }`

10. **Explain the difference between prefix and postfix increment**
    - **Prefix (`++i`)**: Increment first, then return value
    - **Postfix (`i++`)**: Return value first, then increment
    - **In expressions**: `let x = ++i` (x gets incremented value), `let x = i++` (x gets old value)
    - **In loops**: Usually no difference in `for(let i=0; i<10; i++)`

11. **What is the nullish coalescing operator (`??`)?**
    - Returns right operand when left is `null` or `undefined`
    - Different from `||`: `0`, `''`, `false` are not nullish
    - Example: `count ?? 0` (only 0 if count is null/undefined)
    - Use case: Default values when 0 and '' are valid

12. **What is optional chaining (`?.`) and how does it work?**
    - Safely access nested properties without checking each level
    - Returns `undefined` if reference is nullish, doesn't throw error
    - Syntax: `obj?.prop`, `obj?.[expr]`, `func?.(args)`
    - Example: `user?.address?.street` vs `user && user.address && user.address.street`

13. **Explain the logical assignment operators (`&&=`, `||=`, `??=`)**
    - **`x &&= y`**: Assigns only if x is truthy
    - **`x ||= y`**: Assigns only if x is falsy
    - **`x ??= y`**: Assigns only if x is nullish
    - Shorthand for conditional assignment

14. **What is the comma operator?**
    - Evaluates each operand, returns last one
    - Example: `let x = (1, 2, 3)` → `x` is `3`
    - Use in for loops: `for(let i=0, j=10; i<j; i++, j--)`
    - Generally avoid (reduces readability)

15. **How do `if` statements handle non-boolean values?**
    - Coerces to boolean using `ToBoolean` abstract operation
    - Falsy: `false`, `0`, `-0`, `0n`, `''`, `null`, `undefined`, `NaN`
    - Truthy: Everything else
    - Same rules for `while`, `for`, ternary

**Advanced Level:**
16. **What is the performance difference between loop types?**
    - **Traditional for**: Fastest (simple counter)
    - **`for...of`**: Slightly slower (iterator protocol)
    - **`forEach`**: Function call overhead
    - **`for...in`**: Slowest (prototype chain lookup)
    - Modern engines optimize most loops similarly

17. **Explain loop unrolling and when it's beneficial**
    - Manually expanding loop iterations
    - Reduces loop overhead (fewer jumps, comparisons)
    - Example: Process 4 items per iteration instead of 1
    - Modern compilers often do this automatically

18. **What are the pitfalls of using `switch` statements?**
    - **Fall-through**: Forgetting `break` leads to bugs
    - **Type coercion**: Uses `===` but can be confusing
    - **No expressions**: Can't use ranges or complex conditions
    - **Solution**: Consider object lookup or if-else for complex cases

19. **How does JavaScript optimize loops internally?**
    - **Inline caching**: Remembers object shapes for fast property access
    - **Loop unrolling**: Combines multiple iterations
    - **Dead code elimination**: Removes unreachable code
    - **Hoisting invariant code**: Moves unchanging calculations outside loop

20. **What is the difference between imperative and declarative loops?**
    - **Imperative**: `for`, `while` (how to do it)
    - **Declarative**: `map`, `filter`, `reduce` (what to do)
    - **Readability**: Declarative often clearer for array operations
    - **Performance**: Imperative sometimes faster (no function calls)
    - **Use case**: Imperative for performance-critical, declarative for clarity

#### **Behavioral & Experience-Based Questions**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Behavioral Questions:**
1. **"Tell me about a time you optimized a slow loop that was degrading performance in a real app."**
   - *STAR hint*: A nested loop O(n²) scanning a product list or cart on every render/input. Describe the visible symptom (lag, freeze), profiling step (DevTools Performance tab), the fix (convert inner loop to a Map/Set lookup), measured improvement.

2. **"Describe a complex conditional logic you wrote for a real business requirement. How did you keep it maintainable?"**
   - *STAR hint*: Shopify discount rules, Airtable record status routing, pricing tiers. Mention how you started with nested if/else, the readability problem, and how you refactored to an object lookup / strategy pattern or early returns.

3. **"Has a loop ever caused your browser to freeze or an infinite loop to appear in production? What happened?"**
   - *STAR hint*: A `while` loop with a wrong exit condition. Describe the user impact, how you identified it (browser tab unresponsive, Error Boundary, DevTools), the fix (correct exit condition, max iteration guard), and what you learned.

**Experience-Based Conceptual:**
4. **"When fetching all Airtable records (which can be hundreds), how do you efficiently loop through paginated responses without blocking the UI?"**
   - *Answer framework*: Async loop with `do...while` or `for` using `await`, accumulate into array, show loading state, avoid `Promise.all` with too many concurrent calls due to rate limits.

5. **"In React, when would you choose a `for` loop inside a function vs `.map()` in JSX? Is there a performance difference?"**
   - *Answer framework*: `.map()` for rendering (JSX expects an array), `for`/`for...of` for imperative logic (building a value, early exit with `break`). `.map()` slightly more overhead due to array creation but negligible at normal scales.

6. **"How do you handle early exit when searching through a Shopify product array — for example, 'find the first product under $20'?"**
   - *Answer framework*: Use `.find()` which short-circuits on first match (O(n) worst but exits early), avoid `.filter()[0]` which scans the whole array. For sorted data, binary search. Demonstrate awareness of short-circuit efficiency.

#### **Programming Tasks (Basic)**
* ✅ Task 1: Print numbers from 1 to 100
* ✅ Task 2: FizzBuzz problem
* ✅ Task 3: Print even numbers up to 50
* ✅ Task 4: Sum of digits in a number
* ✅ Task 5: Factorial of a number
* ✅ Task 6: Check for prime number
* ✅ Task 7: Reverse a number
* ✅ Task 8: Count digits in a number
* ✅ Task 9: Print a star triangle pattern
* ✅ Task 10: Calculate power using loop

#### **Interview Coding Tasks**

**Loop Fundamentals:**
* ✅ Task 11: Print all prime numbers between 1 to N (Sieve of Eratosthenes)
* ✅ Task 12: Print all prime numbers using optimized loop (√n optimization)
* ✅ Task 13: Check if number is palindrome using loops
* ✅ Task 14: Reverse a number using while loop
* ✅ Task 15: Count digits in a number without converting to string

**Number Theory & Mathematics:**
* ✅ Task 16: Armstrong number checker (153 = 1³ + 5³ + 3³)
* ✅ Task 17: Print all Armstrong numbers between 1 to 1000
* ✅ Task 18: Find GCD (Greatest Common Divisor) using Euclidean algorithm
* ✅ Task 19: Find LCM using GCD relationship
* ✅ Task 20: Check if a number is perfect number (sum of divisors = number)
* ✅ Task 21: Find all divisors of a number efficiently
* ✅ Task 22: Find trailing zeros in factorial (without calculating factorial)
* ✅ Task 23: Calculate factorial using loop with overflow check
* ✅ Task 24: Calculate power (a^b) using fast exponentiation
* ✅ Task 25: Check if number is strong number (sum of factorial of digits)

**Fibonacci & Sequences:**
* ✅ Task 26: Print Fibonacci sequence up to N terms
* ✅ Task 27: Check if a number is in Fibonacci sequence
* ✅ Task 28: Find Nth Fibonacci number optimized (O(n))
* ✅ Task 29: Print sum of even Fibonacci numbers up to limit
* ✅ Task 30: Generate triangular number sequence

**Pattern Printing (Important for Interviews):**
* ✅ Task 31: Print right-angled triangle pattern with stars
* ✅ Task 32: Print inverted triangle pattern
* ✅ Task 33: Print pyramid pattern (centered)
* ✅ Task 34: Print diamond pattern with stars
* ✅ Task 35: Print hollow square pattern
* ✅ Task 36: Print number patterns: 1, 12, 123, 1234, 12345
* ✅ Task 37: Print Floyd's triangle (1, 2 3, 4 5 6, ...)
* ✅ Task 38: Print Pascal's triangle up to N rows
* ✅ Task 39: Print butterfly pattern
* ✅ Task 40: Print hourglass pattern

**String Processing with Loops:**
* ✅ Task 41: Count vowels and consonants using loops
* ✅ Task 42: Count frequency of each character
* ✅ Task 43: Remove duplicate characters from string
* ✅ Task 44: Check if string is palindrome (ignoring spaces/case)
* ✅ Task 45: Reverse words in a sentence

**Number Conversions:**
* ✅ Task 46: Convert decimal to binary using loops
* ✅ Task 47: Convert decimal to hexadecimal
* ✅ Task 48: Convert decimal to octal
* ✅ Task 49: Convert binary to decimal
* ✅ Task 50: Convert between any base (2-36)

**Advanced Loop Challenges:**
* ✅ Task 51: Find sum of all even numbers in range [a, b]
* ✅ Task 52: Find sum of all odd numbers in range
* ✅ Task 53: Print multiplication table using nested loops (1-10)
* ✅ Task 54: Find sum of digits raised to consecutive powers
* ✅ Task 55: Generate all prime numbers up to N efficiently

**Break & Continue:**
* ✅ Task 56: Use break to exit loop on first negative number
* ✅ Task 57: Use continue to skip even numbers
* ✅ Task 58: Use labeled break to exit nested loops
* ✅ Task 59: Find first number divisible by both 3 and 5

**Switch Statement Challenges:**
* ✅ Task 60: Create a calculator using switch (with fall-through handling)
* ✅ Task 61: Day of week name using switch
* ✅ Task 62: Month name and days in month using switch
* ✅ Task 63: Grade calculator with switch (A-F based on score)
* ✅ Task 64: Convert switch to object lookup pattern

**Conditional Logic:**
* ✅ Task 65: Find largest of three numbers using nested if-else
* ✅ Task 66: Check leap year with proper conditions
* ✅ Task 67: Calculate electricity bill with slab rates
* ✅ Task 68: Grade students with multiple criteria
* ✅ Task 69: Categorize age groups (child, teen, adult, senior)
* ✅ Task 70: Implement FizzBuzz with variations (FizzBuzzJazz)

**Short-Circuit & Modern Operators:**
* ✅ Task 71: Use `&&` for conditional execution
* ✅ Task 72: Use `||` for default values
* ✅ Task 73: Use `??` (nullish coalescing) vs `||`
* ✅ Task 74: Use optional chaining (`?.`) in loops
* ✅ Task 75: Demonstrate all logical assignment operators

**Performance & Optimization:**
* ✅ Task 76: Compare performance: for vs for...of vs forEach
* ✅ Task 77: Optimize nested loops to reduce time complexity
* ✅ Task 78: Cache array length in loop vs accessing each time
* ✅ Task 79: Unroll loop for performance gain
* ✅ Task 80: Break early vs full iteration comparison

**Real-World Scenarios:**
* ✅ Task 81: Validate password with multiple conditions
* ✅ Task 82: Process transaction records (loop through data)
* ✅ Task 83: Find second largest number in array using loops
* ✅ Task 84: Count positive, negative, and zero in array
* ✅ Task 85: Find all pairs with given sum using nested loops

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Loop through a Shopify product list array and build `<li>` HTML strings — break after first 5 featured products using `break`
* ⬜ RW-2: Display a pricing table: use a `for` loop over plan tiers `[{name, price, features[]}]`, use nested loop to render each feature row

**React / Next.js:**
* ⬜ RW-3: Render a product catalog in React using `.map()` — use conditional rendering to show "Out of Stock" badge if `stock === 0`, "Low Stock" if `stock < 5`
* ⬜ RW-4: Build a Next.js FAQ accordion — loop through a `faq` array, use `if` to check which item is open, toggle with a boolean flag per item

**Airtable API:**
* ⬜ RW-5: Loop through Airtable records with `for...of` — use `if/else if/else` to bucket each record as "New", "In Progress", "Done", or "Unknown"
* ⬜ RW-6: Fetch Airtable records and display only those where `Status === "Active"` AND `Priority === "High"` — combine conditions with `&&`

**Shopify:**
* ⬜ RW-7: Loop through Shopify `line_items` and calculate order total — apply a `while` loop to keep applying discount codes until total stops decreasing
* ⬜ RW-8: Build a variant size selector: use `switch` to map Shopify size codes (`"S"`, `"M"`, `"L"`, `"XL"`) to full labels and stock status messages

**Laravel / Python Flask:**
* ⬜ RW-9: Loop through a paginated API response — use `do...while` to keep fetching next pages while `data.nextPage !== null`, collect all results
* ⬜ RW-10: Process form submissions from Flask API: loop through entries, separate valid from invalid using conditionals, log a summary count for each category

### **Day 3: Functions and Scope**

#### **Core Concepts**
* ✅ Learn function declaration and expression
* ✅ Arrow functions and their differences
* ✅ Parameters, return values, default parameters
* ✅ Rest parameters and spread operator
* ✅ Function scope vs block scope
* ✅ Closures and lexical scope
* ✅ Higher-order functions
* ✅ Pure vs impure functions
* ✅ IIFE (Immediately Invoked Function Expression)
* ✅ Callback functions

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **What's the difference between function declaration and function expression?**
   - **Function Declaration**: `function foo() {}` - hoisted completely
   - **Function Expression**: `const foo = function() {}` - only variable hoisted
   - **Availability**: Declarations available before definition, expressions aren't
   - **Naming**: Expressions can be anonymous, declarations must be named
   - **Use case**: Declarations for general functions, expressions for conditional assignment

2. **Explain arrow functions and their differences from regular functions**
   - **Lexical `this`**: Inherits `this` from enclosing scope, can't be changed
   - **No `arguments`**: Doesn't have `arguments` object (use rest parameters)
   - **No constructor**: Can't use `new` with arrow functions
   - **No `prototype`**: Arrow functions don't have prototype property
   - **Implicit return**: Single expression returns automatically without `{}`
   - **Syntax**: Shorter, cleaner for simple functions
   - **Use case**: Callbacks, array methods, avoiding `this` confusion

3. **What is a closure? Provide an example**
   - **Definition**: Function bundled with its lexical environment
   - **Access**: Inner function can access outer function's variables
   - **Persistence**: Variables persist even after outer function returns
   - **Use cases**: Data privacy, factory functions, event handlers, callbacks
   - **Example**: Counter function that maintains private state
   - **Memory**: Closures can cause memory leaks if not careful

4. **Explain function scope, block scope, and lexical scope**
   - **Function Scope**: Variables declared with `var`, visible throughout function
   - **Block Scope**: Variables with `let`/`const`, limited to `{}` block
   - **Lexical Scope**: Scope determined by code structure, not runtime
   - **Scope Chain**: Inner scopes can access outer scopes
   - **Global Scope**: Variables accessible everywhere

5. **What are higher-order functions?**
   - **Definition**: Functions that operate on other functions
   - **Take functions**: Accept functions as arguments (callbacks)
   - **Return functions**: Return new functions
   - **Examples**: `map`, `filter`, `reduce`, `forEach`
   - **Benefits**: Abstraction, code reuse, functional programming
   - **Custom**: Can create your own (debounce, throttle, compose)

6. **What is the difference between parameters and arguments?**
   - **Parameters**: Variables listed in function definition
   - **Arguments**: Actual values passed when calling function
   - **Default parameters**: ES6 allows default values
   - **Rest parameters**: `...args` collects extra arguments
   - **`arguments` object**: Array-like object with all arguments (not in arrow)

7. **Explain rest parameters and spread operator**
   - **Rest (`...args`)**: Collects remaining arguments into array
   - **Spread (`...arr`)**: Expands array/object into individual elements
   - **Syntax**: Both use `...` but different contexts
   - **Rest**: Must be last parameter
   - **Spread**: Can copy arrays/objects, merge, pass to functions

8. **What is recursion? When would you use it?**
   - **Definition**: Function calling itself
   - **Base case**: Condition to stop recursion (prevents infinite loop)
   - **Recursive case**: Function calls itself with modified input
   - **Use cases**: Tree traversal, factorial, Fibonacci, divide-and-conquer
   - **Drawbacks**: Stack overflow, performance overhead
   - **Alternatives**: Iteration, tail recursion optimization

**Intermediate Level:**
9. **What are pure functions and why are they important?**
   - **Definition**: Same input always produces same output
   - **No side effects**: Doesn't modify external state
   - **Benefits**: Predictable, testable, cacheable, parallelizable
   - **Examples**: `Math.max()`, string methods
   - **Impure**: Random, Date.now(), console.log, modifying arguments
   - **Functional programming**: Core concept in FP

10. **Explain callback functions with example**
    - **Definition**: Function passed as argument to another function
    - **Async operations**: Used for handling async results
    - **Event handlers**: Responding to user interactions
    - **Array methods**: `forEach`, `map`, `filter` use callbacks
    - **Callback hell**: Nested callbacks become hard to read
    - **Solutions**: Promises, async/await

11. **What is an IIFE and why use it?**
    - **Definition**: Immediately Invoked Function Expression
    - **Syntax**: `(function() { })()` or `(function() {}())`
    - **Purpose**: Creates private scope, avoids polluting global
    - **Use cases**: Module pattern, initialization code, closures
    - **ES6**: Less needed with `let`/`const` and modules
    - **Arrow IIFE**: `(() => {})()` also works

12. **What is the difference between `call()`, `apply()`, and `bind()`?**
    - **All**: Change `this` context of function
    - **`call(thisArg, arg1, arg2)`**: Invoke immediately, args separately
    - **`apply(thisArg, [args])`**: Invoke immediately, args as array
    - **`bind(thisArg, arg1, arg2)`**: Returns new function, doesn't invoke
    - **Use cases**: Borrowing methods, setting `this`, partial application

13. **What is function currying?**
    - **Definition**: Transform f(a, b, c) into f(a)(b)(c)
    - **Partial application**: Create specialized functions
    - **Use cases**: Configuration, reusable logic, functional composition
    - **Implementation**: Return functions until all args collected
    - **Example**: `add(2)(3)` → `5`

14. **Explain the concept of first-class functions**
    - **Definition**: Functions treated as values
    - **Assign**: Can assign to variables
    - **Pass**: Can pass as arguments
    - **Return**: Can return from functions
    - **Store**: Can store in data structures
    - **JavaScript**: Fully supports first-class functions

15. **What is the `arguments` object?**
    - **Definition**: Array-like object with all arguments
    - **Availability**: Only in regular functions (not arrow)
    - **Array-like**: Has length, indexed, but not an array
    - **Convert**: `Array.from(arguments)` or `[...arguments]`
    - **Modern**: Use rest parameters instead

**Advanced Level:**
16. **Explain lexical scoping and scope chain**
    - **Lexical**: Scope determined by code location, not call location
    - **Scope chain**: Series of scopes from inner to outer
    - **Lookup**: Search variable in current scope, then outer, until global
    - **Closures**: Result of lexical scoping
    - **Performance**: Fewer scope levels = faster lookup

17. **What is a thunk and when would you use it?**
    - **Definition**: Function that wraps an expression to delay evaluation
    - **Lazy evaluation**: Compute only when needed
    - **Async thunks**: Common in Redux for async actions
    - **Example**: `const thunk = () => 2 + 2`

18. **Explain function composition and pipe**
    - **Composition**: Combine multiple functions into one
    - **Right-to-left**: `compose(f, g, h)(x)` = `f(g(h(x)))`
    - **Pipe**: Left-to-right composition
    - **Benefits**: Reusability, readability, functional style
    - **Implementation**: Using `reduce`

19. **What is tail call optimization (TCO)?**
    - **Definition**: Optimize recursive calls in tail position
    - **Tail position**: Last operation before return
    - **Benefit**: Prevents stack overflow, uses constant stack space
    - **JavaScript**: Limited support, ES6 spec includes it
    - **Alternative**: Convert recursion to iteration

20. **Explain memoization and how to implement it**
    - **Definition**: Cache function results for same inputs
    - **Purpose**: Performance optimization for expensive calculations
    - **Implementation**: Use closure to store cache object
    - **Use cases**: Recursive functions, API calls, computations
    - **Trade-off**: Memory vs speed

21. **What are generator functions?**
    - **Definition**: Functions that can pause and resume execution
    - **Syntax**: `function* name()` with `yield` keyword
    - **Iterator**: Returns iterator object
    - **Use cases**: Lazy sequences, async iteration, state machines
    - **Control**: Better control over execution flow

22. **Explain function hoisting in detail**
    - **Declarations**: Fully hoisted (definition + initialization)
    - **Expressions**: Only variable hoisted, not function
    - **Arrow**: Same as expressions (variable hoisted only)
    - **Order**: Declarations hoisted before variables
    - **Best practice**: Declare functions before use for clarity

23. **What is partial application?**
    - **Definition**: Fix some arguments, create new function
    - **vs Currying**: Currying transforms to single arg, partial fixes any number
    - **Use `bind()`**: `bind` can partially apply arguments
    - **Custom**: Can create custom partial application function
    - **Use cases**: Configuration, specialization

24. **Explain the Module Pattern**
    - **Definition**: Use IIFE and closures to create private variables
    - **Public API**: Return object with public methods
    - **Private**: Variables in IIFE scope remain private
    - **Revealing**: Return object reveals selected methods
    - **ES6 Modules**: Modern alternative with import/export

25. **What is function borrowing?**
    - **Definition**: Use method from one object on another
    - **`call`/`apply`**: Borrow methods dynamically
    - **Example**: `Array.prototype.slice.call(arguments)`
    - **Use cases**: Array-like objects, method reuse
    - **Modern**: Spread operator often better alternative

#### **Behavioral & Experience-Based Questions**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Behavioral Questions:**
1. **"Tell me about a situation where you used closures to solve a real problem in your codebase."**
   - *STAR hint*: Caching an API result between component renders without Redux, or an event handler that needed to capture a value at creation time. Describe the specific need, why a closure fit better than passing a param, the implementation, and the outcome.

2. **"Describe how you've organized utility/helper functions across a large React or Next.js project. What was your structure?"**
   - *STAR hint*: Project getting messy, utils scattered everywhere. Created a `/utils` or `/lib` folder with domain-specific modules (`api.js`, `format.js`, `validate.js`). All pure functions — no side effects, easy to import anywhere and unit test independently.

3. **"Has the `this` keyword ever caused a production bug for you? Walk me through what happened."**
   - *STAR hint*: A class method or event listener losing its `this` context (returns `undefined`). Describe identifying it with `console.log(this)`, the fix (arrow function or `.bind()`), and how you now avoid the pattern.

**Experience-Based Conceptual:**
4. **"How do you share utility functions between your React client components and Next.js API routes without duplication?"**
   - *Answer framework*: `/lib` or `/utils` folder with pure functions that have no DOM dependencies. Import in both client and server contexts. For server-only utils (DB access, secrets), keep in `/lib/server/` and never import in client components.

5. **"When calling the Airtable API or Shopify API, how do you manage the API key — where does it live in your code and why?"**
   - *Answer framework*: `.env` file → `process.env.AIRTABLE_API_KEY`. Never in global scope, never in client-side JS bundle. Server-side only (Next.js API routes, Laravel, Flask). Accessed via a module-level constant at the top of the service file, not inline in each function.

6. **"What's the difference between a pure function and a function with side effects? Give an example of each from your actual projects."**
   - *Answer framework*: Pure = `formatPrice(amount) → string` (same input, same output, no external changes). Side effect = `saveToAirtable(data)` (modifies external state). In practice, keep business logic in pure functions and push side effects to the edges of the codebase.

#### **Programming Tasks (Basic)**
* ✅ Task 1: Create a reusable `isEven()` function
* ✅ Task 2: Check palindrome using function
* ✅ Task 3: Create a calculator function
* ✅ Task 4: Recursive factorial
* ✅ Task 5: GCD of two numbers
* ✅ Task 6: LCM of two numbers
* ✅ Task 7: Create a function to capitalize words
* ✅ Task 8: Use default parameters
* ✅ Task 9: Create a simple counter using closure
* ✅ Task 10: Write a function to reverse string

#### **Interview Coding Tasks**

**Closures:**
* ✅ Task 11: Create a function factory that generates multiplier functions
* ✅ Task 12: Implement a private counter using closures (increment, decrement, value)
* ✅ Task 13: Create a function that generates unique IDs using closures
* ✅ Task 14: Build a timer function using closures
* ✅ Task 15: Create a bank account with private balance (deposit, withdraw, getBalance)
* ✅ Task 16: Implement a rate limiter using closures
* ✅ Task 17: Create a closure that remembers previous function calls
* ✅ Task 18: Build a shopping cart with closure-based privacy

**Arrow Functions & this:**
* ✅ Task 19: Demonstrate `this` difference between regular and arrow functions
* ✅ Task 20: Fix `this` binding issue in setTimeout using arrow function
* ✅ Task 21: Convert regular functions to arrow functions (when appropriate)
* ✅ Task 22: Show when NOT to use arrow functions (methods, constructors)

**Rest & Spread:**
* ✅ Task 23: Write a function that returns sum of arguments (any number) using rest
* ✅ Task 24: Create a merge function using spread operator
* ✅ Task 25: Clone arrays and objects using spread
* ✅ Task 26: Use rest parameters to find max of unlimited numbers

**Higher-Order Functions:**
* ✅ Task 27: Create custom `map` function
* ✅ Task 28: Create custom `filter` function
* ✅ Task 29: Create custom `reduce` function
* ✅ Task 30: Implement `forEach` from scratch
* ✅ Task 31: Create a function that takes a predicate and returns filtered array
* ✅ Task 32: Build a function that chains array operations

**Currying & Partial Application:**
* ✅ Task 33: Implement function currying for add(a)(b)(c)
* ✅ Task 34: Create a curry function that works for any function
* ✅ Task 35: Implement partial application using `bind`
* ✅ Task 36: Create a custom partial function
* ✅ Task 37: Build a logging function with currying
* ✅ Task 38: Curry a function to calculate volume(l)(w)(h)

**Function Composition:**
* ✅ Task 39: Write a function to compose multiple functions (right-to-left)
* ✅ Task 40: Implement a pipe function (left-to-right composition)
* ✅ Task 41: Create a compose function for unlimited functions
* ✅ Task 42: Build a data transformation pipeline

**Memoization:**
* ✅ Task 43: Create a memoization function for expensive calculations
* ✅ Task 44: Implement memoized Fibonacci function
* ✅ Task 45: Create a generic memoize function that works with any function
* ✅ Task 46: Memoize factorial calculation
* ✅ Task 47: Build a cache with size limit for memoization

**Recursion:**
* ✅ Task 48: Implement factorial using recursion
* ✅ Task 49: Calculate power (a^b) recursively
* ✅ Task 50: Write recursive binary search function
* ✅ Task 51: Flatten nested array recursively
* ✅ Task 52: Find all permutations of a string recursively
* ✅ Task 53: Implement recursive array sum
* ✅ Task 54: Count down from N to 0 recursively
* ✅ Task 55: Reverse a string using recursion
* ✅ Task 56: Calculate GCD using recursive Euclidean algorithm
* ✅ Task 57: Traverse nested object recursively
* ✅ Task 58: Generate all subsets of array recursively
* ✅ Task 59: Solve Tower of Hanoi recursively
* ✅ Task 60: Implement tail-recursive factorial

**Callbacks:**
* ✅ Task 61: Create a function that accepts callback and executes after delay
* ✅ Task 62: Implement a custom `setTimeout` wrapper
* ✅ Task 63: Build an async operation handler with callbacks
* ✅ Task 64: Create event emitter with callback registration
* ✅ Task 65: Handle callback hell by refactoring to named functions

**IIFE & Modules:**
* ✅ Task 66: Create an IIFE that creates a private module
* ✅ Task 67: Build a module pattern with public/private methods
* ✅ Task 68: Create a revealing module pattern
* ✅ Task 69: Use IIFE to avoid global namespace pollution
* ✅ Task 70: Create a singleton using IIFE

**call, apply, bind:**
* ✅ Task 71: Use `call` to borrow array methods for array-like objects
* ✅ Task 72: Use `apply` with Math.max for array of numbers
* ✅ Task 73: Use `bind` to create bound functions
* ✅ Task 74: Implement custom `call` method (polyfill)
* ✅ Task 75: Implement custom `apply` method (polyfill)
* ✅ Task 76: Implement custom `bind` method (polyfill)
* ✅ Task 77: Method borrowing example with objects

**Utility Functions:**
* ✅ Task 78: Create a debounce function (delays execution)
* ✅ Task 79: Implement a throttle function (limits execution rate)
* ✅ Task 80: Build an `once` function (executes only once)
* ✅ Task 81: Create a `retry` function that retries failed operations
* ✅ Task 82: Implement a `delay` function with promises
* ✅ Task 83: Build a function to measure execution time
* ✅ Task 84: Create a function validator/type checker

**Pure vs Impure:**
* ✅ Task 85: Write examples of pure functions
* ✅ Task 86: Write examples of impure functions
* ✅ Task 87: Refactor impure function to pure function
* ✅ Task 88: Demonstrate side effects in functions

**Advanced Challenges:**
* ✅ Task 89: Implement function to check if parentheses are balanced
* ✅ Task 90: Deep clone an object (handle nested objects/arrays)
* ✅ Task 91: Convert callback-based function to promise
* ✅ Task 92: Implement a function pipeline (chainable operations)
* ✅ Task 93: Create a function that converts array of functions to promises
* ✅ Task 94: Build a queue system using closures
* ✅ Task 95: Implement a cache with TTL (time to live)
* ✅ Task 96: Create a function that executes functions in sequence
* ✅ Task 97: Build a transaction rollback system
* ✅ Task 98: Implement a state machine using closures
* ✅ Task 99: Create a function that converts recursive to iterative
* ✅ Task 100: Build a custom `Promise.all` implementation

**Real-World Applications:**
* ✅ Task 101: Create an API request handler with retry logic
* ✅ Task 102: Build a search with debounce
* ✅ Task 103: Implement infinite scroll with throttle
* ✅ Task 104: Create a form validator using closures
* ✅ Task 105: Build a middleware pattern for function execution

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Write a reusable `formatCurrency(amount, currency = 'USD')` function — use it across a GoDaddy product page for consistent price display
* ⬜ RW-2: Create a `debounce(fn, delay)` utility and attach it to a search input — prevents API call on every keystroke

**React / Next.js:**
* ⬜ RW-3: Build a `useLocalStorage(key, defaultValue)` custom hook using closures — persists cart or filter state across page refreshes without Redux
* ⬜ RW-4: Write a `withAuth(Component)` higher-order component — use function scope to check if a JWT token exists in `localStorage` before rendering protected pages

**Airtable API:**
* ⬜ RW-5: Create an `airtableFetch(tableName, filterFormula)` function that encapsulates base URL, API key, and headers in a closure — call it from multiple components
* ⬜ RW-6: Build `createRecord(table, data)` and `updateRecord(table, id, data)` as pure functions — keep the API key in module scope, not global

**Shopify:**
* ⬜ RW-7: Write a `calculateCartTotal(items, discountCode = null)` function — use default parameters, handle free shipping threshold inside
* ⬜ RW-8: Create a `buildShopifyURL(handle, ...params)` utility using rest parameters and template literals — generates clean product/collection URLs

**Laravel / Python Flask:**
* ⬜ RW-9: Build an `apiRequest(endpoint, method = 'GET', body = null)` wrapper — use closure over base URL and auth token, works for both Laravel and Flask endpoints
* ⬜ RW-10: Implement a function pipeline: `validateInput → sanitize → sendToAPI` — each is a pure function, compose them with `pipe(f1, f2, f3)(data)`

---

## **🗓️ Week 2: Arrays and Strings**

### **Day 4: Arrays Basics**

#### **Core Concepts**
* ✅ Understand arrays: push, pop, shift, unshift
* ✅ Array indexing (0-based, negative indexing)
* ✅ Iterating arrays (for, for...of, forEach)
* ✅ Array length property
* ✅ Sparse arrays and holes
* ✅ Array-like objects
* ✅ Arrays are objects (reference type)
* ✅ Copying arrays (shallow vs deep)
* ✅ Multi-dimensional arrays

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **How do arrays work in JavaScript? Are they true arrays?**
   - Arrays are special objects with numeric keys
   - Length property automatically updated
   - Not true arrays like C/Java (dynamic, can hold mixed types)
   - Internally optimized for sequential numeric keys
   - Can have non-numeric properties (but not recommended)

2. **What's the difference between `push/pop` and `shift/unshift`?**
   - **`push()`**: Add to end, O(1), returns new length
   - **`pop()`**: Remove from end, O(1), returns removed element
   - **`shift()`**: Remove from start, O(n), returns removed element
   - **`unshift()`**: Add to start, O(n), returns new length
   - **Performance**: push/pop faster than shift/unshift

3. **How do you copy an array in JavaScript?**
   - **Shallow copy**: `[...arr]`, `arr.slice()`, `Array.from(arr)`
   - **Deep copy**: `JSON.parse(JSON.stringify(arr))` (limitations)
   - **structuredClone()**: Modern deep copy method
   - **Assignment**: `arr2 = arr1` copies reference, not array

4. **What are array-like objects? Give examples**
   - Objects with length property and indexed elements
   - Examples: `arguments`, NodeList, strings
   - Not true arrays (no array methods)
   - Convert: `Array.from()`, `[...arrayLike]`, `Array.prototype.slice.call()`

5. **Explain array indexing in JavaScript**
   - **0-based**: First element at index 0
   - **Negative**: Not natively supported (unlike Python)
   - **Out of bounds**: Returns `undefined` (no error)
   - **Setting**: Can set any index, creates sparse array
   - **Length**: Based on highest index + 1

6. **What happens when you access an array out of bounds?**
   - Returns `undefined` (no error thrown)
   - Setting creates sparse array with "holes"
   - Length updates to highest index + 1
   - Holes are different from `undefined` elements

7. **What is a sparse array?**
   - Array with "holes" (empty slots)
   - Created by: `new Array(5)`, `arr[10] = 'x'` when length is 5
   - Holes vs undefined: `0 in [undefined]` is true, `0 in [,]` is false
   - Iteration: Some methods skip holes, others don't

8. **Explain array length property**
   - Not count of elements, but highest index + 1
   - Writable: Can manually set length
   - Truncate: Setting lower length removes elements
   - Extend: Setting higher length creates holes

**Intermediate Level:**
9. **What's the difference between `splice()` and `slice()`?**
   - **`splice()`**: Mutates array, removes/adds elements, returns removed
   - **`slice()`**: Returns shallow copy, doesn't mutate, extracts portion
   - **Confusion**: Easy to mix up due to similar names
   - **Use cases**: splice for modification, slice for copying

10. **How do you check if a value is an array?**
    - **`Array.isArray()`**: Recommended, works across iframes
    - **`instanceof Array`**: Doesn't work across different contexts
    - **`Object.prototype.toString.call(arr)`**: Returns `[object Array]`
    - **Why not `typeof`**: Returns `'object'` for arrays

11. **What are the different ways to create an array?**
    - **Literal**: `[1, 2, 3]` (recommended)
    - **Constructor**: `new Array(1, 2, 3)`
    - **Constructor with size**: `new Array(5)` (creates sparse array)
    - **`Array.of()`**: `Array.of(5)` creates `[5]` not array of 5 holes
    - **`Array.from()`**: From iterable or array-like object

12. **Explain the difference between `delete arr[i]` and `arr.splice(i, 1)`**
    - **`delete`**: Creates hole, doesn't change length, leaves gap
    - **`splice()`**: Removes and shifts elements, updates length
    - **Use splice**: To actually remove elements
    - **Delete**: Rarely needed for arrays

13. **What is the difference between `concat()` and spread operator?**
    - **`concat()`**: `arr1.concat(arr2)`, returns new array
    - **Spread**: `[...arr1, ...arr2]`, more flexible, modern
    - **Both**: Don't mutate, create shallow copy
    - **Spread**: Can also use in function calls, object literals

14. **How do you flatten a nested array?**
    - **`flat()`**: `arr.flat(depth)`, modern method
    - **`flat(Infinity)`**: Flattens all levels
    - **Recursive**: Custom function for older browsers
    - **`concat()` + spread**: `[].concat(...arr)` (one level only)

15. **What is the time complexity of common array operations?**
    - **Access by index**: O(1)
    - **push/pop**: O(1)
    - **shift/unshift**: O(n) - requires re-indexing
    - **splice**: O(n) - shifts elements
    - **Search (indexOf)**: O(n)

**Advanced Level:**
16. **Explain how JavaScript engines optimize arrays**
    - **Continuous arrays**: Sequential elements, highly optimized
    - **Holey arrays**: Sparse, slower access
    - **Packed vs holey**: Engine differentiates types
    - **Type specialization**: Arrays with same type are faster
    - **Avoid**: Mixing types, creating holes, using large indices

17. **What are typed arrays and when would you use them?**
    - Fixed-length, same-type elements (Int8Array, Float32Array, etc.)
    - Use for: Binary data, WebGL, audio processing, ArrayBuffer
    - Better performance for numeric operations
    - Can't change length after creation

18. **How do you create a multi-dimensional array?**
    - **2D**: `Array.from({length: rows}, () => Array(cols).fill(0))`
    - **Incorrect**: `Array(3).fill([])` - creates references to same array
    - **Access**: `matrix[i][j]`
    - **Iteration**: Nested loops

19. **Explain the difference between `Array(3)` and `Array.of(3)`**
    - **`Array(3)`**: Creates array with 3 holes, length 3
    - **`Array.of(3)`**: Creates `[3]`, array with one element
    - **Gotcha**: `Array(1,2,3)` creates `[1,2,3]` but `Array(3)` creates holes
    - **Solution**: Use `Array.of()` for consistency

20. **What happens with arrays in memory?**
    - Arrays are reference types, stored in heap
    - Variable holds reference (pointer) to array
    - Assignment copies reference, not array
    - Multiple variables can reference same array
    - Changes reflect in all references

#### **Behavioral & Experience-Based Questions**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Behavioral Questions:**
1. **"Tell me about a time you had to manage a complex array-based state in a React app. What were the challenges?"**
   - *STAR hint*: Cart state with add/remove/update qty operations. The mutation trap (`push()` on state directly didn't trigger re-render). How you fixed it (spread, `map`, `filter`). How you structured the state update functions for readability.

2. **"Describe a performance problem caused by incorrect array operations that affected your app. How did you diagnose it?"**
   - *STAR hint*: A large array passed as a prop being recreated on every render (e.g., `const x = [...]` inside a component body), causing child re-renders. Profiled with React DevTools, fixed with `useMemo`, explained the shallow equality issue.

3. **"Have you ever accidentally mutated state in React? What was the symptom and how did you fix it?"**
   - *STAR hint*: Used `arr.push()` or `arr.sort()` (mutates in-place) on state array. State didn't update visually. Fixed by creating a new array with spread `[...arr, newItem]` or `.slice()`. Added an ESLint rule or code review note to prevent recurrence.

**Experience-Based Conceptual:**
4. **"When you receive a paginated list of Airtable records (100 per page), how do you combine all pages into a single array for client-side operations?"**
   - *Answer framework*: Recursive or loop-based fetch, accumulate with spread `[...allRecords, ...pageRecords]`, or `Array.prototype.concat()`. Store in state or cache. Mention handling the `offset` field Airtable provides for pagination.

5. **"In a Shopify cart, you have `line_items` as an array of objects. How do you add a product if it doesn't exist, or increment quantity if it does?"**
   - *Answer framework*: `findIndex()` to check if exists, if `-1` → spread + new item, if found → `map()` to create new array with updated qty on matched item. Never mutate the original array.

6. **"How would you implement undo/redo for a content editor using only arrays? No external libraries."**
   - *Answer framework*: `history = [state0, state1, state2]`, `pointer = currentIndex`. Undo = `pointer--`, redo = `pointer++`, new action = `history.slice(0, pointer+1).concat([newState])` (truncates forward history). Classic approach shown in interviews.

#### **Programming Tasks (Basic)**
* ✅ Task 1: Sum of array elements
* ✅ Task 2: Find max/min in array
* ✅ Task 3: Count even and odd numbers
* ✅ Task 4: Reverse an array (in-place and new array)
* ✅ Task 5: Filter positive numbers
* ✅ Task 6: Remove duplicates (loop method)
* ✅ Task 7: Rotate array by 1 position
* ✅ Task 8: Check if array is sorted (ascending/descending)
* ✅ Task 9: Count frequency of elements
* ✅ Task 10: Linear search for element

#### **Interview Coding Tasks**

**Array Manipulation:**
* ✅ Task 11: Rotate array by K positions (left and right)
* ✅ Task 12: Reverse array in-place without using reverse()
* ✅ Task 13: Move all zeros to end while maintaining order
* ✅ Task 14: Move all negative numbers to left, positive to right
* ✅ Task 15: Rearrange array in alternating positive-negative
* ✅ Task 16: Separate even and odd numbers
* ✅ Task 17: Cyclically rotate array by one

**Array Searching:**
* ✅ Task 18: Find second largest element in array
* ✅ Task 19: Find second smallest element
* ✅ Task 20: Find missing number in array from 1 to N
* ✅ Task 21: Find duplicate number in array
* ✅ Task 22: Find all pairs with given sum
* ✅ Task 23: Find element that appears once (others appear twice)
* ✅ Task 24: Find majority element (appears > n/2 times)
* ✅ Task 25: Find leaders in array (greater than all to right)

**Array Operations:**
* ✅ Task 26: Merge two sorted arrays
* ✅ Task 27: Find intersection of two arrays
* ✅ Task 28: Find union of two arrays
* ✅ Task 29: Remove duplicates from sorted array
* ✅ Task 30: Remove duplicates from unsorted array
* ✅ Task 31: Check if arrays are equal
* ✅ Task 32: Find common elements in 3 sorted arrays

**Sliding Window & Subarray:**
* ✅ Task 33: Maximum sum subarray of size K (fixed window)
* ✅ Task 34: Find subarray with given sum
* ✅ Task 35: Longest subarray with sum K
* ✅ Task 36: Count subarrays with sum K
* ✅ Task 37: Maximum sum of contiguous subarray (Kadane's algorithm)

**Array Sorting Related:**
* ✅ Task 38: Sort array of 0s, 1s, and 2s (Dutch National Flag)
* ✅ Task 39: Sort array without using sort method (implement bubble sort)
* ✅ Task 40: Check if array can be sorted by reversing subarray
* ✅ Task 41: Find kth smallest/largest element

**Frequency & Counting:**
* ✅ Task 42: Find first repeating element
* ✅ Task 43: Find first non-repeating element
* ✅ Task 44: Count frequency of each element using object/map
* ✅ Task 45: Find element with maximum frequency
* ✅ Task 46: Find elements that appear more than n/3 times

**Array Transformation:**
* ✅ Task 47: Create array of squares of elements
* ✅ Task 48: Create cumulative sum array
* ✅ Task 49: Create product array except self
* ✅ Task 50: Replace every element with greatest on right side

**Two Pointer Technique:**
* ✅ Task 51: Remove duplicates from sorted array (two pointers)
* ✅ Task 52: Check if array is palindrome
* ✅ Task 53: Container with most water problem
* ✅ Task 54: Trapping rainwater problem

**Advanced Challenges:**
* ✅ Task 55: Stock buy and sell to maximize profit (one transaction)
* ✅ Task 56: Stock buy and sell (multiple transactions)
* ✅ Task 57: Find equilibrium index (sum left = sum right)
* ✅ Task 58: Rearrange array to form largest number
* ✅ Task 59: Find triplets with sum equal to target
* ✅ Task 60: Longest consecutive sequence

**Array Creation & Copying:**
* ✅ Task 61: Deep clone array with nested arrays
* ✅ Task 62: Create 2D array (matrix) and fill with values
* ✅ Task 63: Transpose a matrix
* ✅ Task 64: Rotate matrix 90 degrees
* ✅ Task 65: Flatten nested array (multi-level)

**Edge Cases & Validation:**
* ✅ Task 66: Handle empty array in all operations
* ✅ Task 67: Validate array input before processing
* ✅ Task 68: Handle arrays with one element
* ✅ Task 69: Handle sparse arrays properly
* ✅ Task 70: Compare array copying methods (performance)

**Real-World Scenarios:**
* ✅ Task 71: Implement shopping cart (add, remove, update quantities)
* ✅ Task 72: Implement undo/redo using arrays
* ✅ Task 73: Pagination - split array into pages
* ✅ Task 74: Group array elements by property
* ✅ Task 75: Implement queue using array (FIFO)
* ✅ Task 76: Implement stack using array (LIFO)
* ✅ Task 77: Circular buffer implementation
* ✅ Task 78: Priority queue basics with arrays
* ✅ Task 79: Find median of sorted arrays
* ✅ Task 80: Implement array-based LRU cache

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Build a shopping cart: store items as `[{id, name, price, qty}]` — implement `addItem`, `removeItem`, `updateQty`, `clearCart` using array operations
* ⬜ RW-2: Create a "Recently Viewed" products list (max 5 items) using an array — if already exists move to front, remove oldest if limit exceeded

**React / Next.js:**
* ⬜ RW-3: Build React cart state with `useState`: array of products — `addToCart` checks for duplicates by ID, `removeFromCart` filters by ID, renders count badge
* ⬜ RW-4: Implement a Next.js image gallery — store image URLs in array, support prev/next navigation with index, wrap around at boundaries

**Airtable API:**
* ⬜ RW-5: Fetch all Airtable records into an array — implement `getById(id)` using `find()`, `getByIndex(i)` with bounds check, display "Not Found" gracefully
* ⬜ RW-6: Store Airtable linked record IDs in an array — loop through to fetch each related record separately and build a joined display object

**Shopify:**
* ⬜ RW-7: Parse a Shopify order's `line_items` array — extract `{productId, title, qty, price}` into a clean summary, calculate subtotal per item
* ⬜ RW-8: Build a product variant matrix: store all size × color combinations in a 2D array — look up availability by `[sizeIndex][colorIndex]`

**Laravel / Python Flask:**
* ⬜ RW-9: Receive an array of records from a Laravel API — shallow copy before sorting/filtering so the original response is never mutated
* ⬜ RW-10: Implement client-side pagination: get all records from Flask API into one array, then slice by `(page - 1) * pageSize` to get current page

### **Day 5: String Basics**

#### **Core Concepts**
* ✅ String methods: split, join, slice, substring, substr
* ✅ String immutability
* ✅ String indexing and charAt()
* ✅ Template literals and string interpolation
* ✅ String comparison and localeCompare()
* ✅ Regular expressions basics
* ✅ String searching: indexOf, lastIndexOf, includes, search
* ✅ String modification: replace, replaceAll, trim, pad
* ✅ Case conversion: toLowerCase, toUpperCase
* ✅ Unicode and character codes

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **Are strings mutable or immutable in JavaScript?**
   - **Immutable**: Cannot modify existing string
   - **New string**: All operations create new strings
   - **Original unchanged**: `str.toUpperCase()` doesn't modify `str`
   - **Memory**: Excessive string operations can be costly
   - **StringBuilder pattern**: For many concatenations, use array + join

2. **What's the difference between `slice()`, `substring()`, and `substr()`?**
   - **`slice(start, end)`**: Can use negative indices, end not included
   - **`substring(start, end)`**: No negative (treats as 0), swaps if start > end
   - **`substr(start, length)`**: Deprecated, second param is length not end
   - **Recommendation**: Use `slice()` for consistency

3. **How do you access characters in a string?**
   - **Bracket notation**: `str[0]` - modern, concise
   - **charAt()**: `str.charAt(0)` - returns empty string for out of bounds
   - **Bracket**: Returns `undefined` for out of bounds
   - **Iteration**: Both work in loops, for...of iterates characters

4. **What's the difference between `indexOf()` and `search()`?**
   - **`indexOf()`**: Simple string search, returns index or -1
   - **`search()`**: Accepts regex, returns index or -1
   - **Performance**: `indexOf()` faster for simple strings
   - **Cannot start from**: `search()` can't specify start position

5. **How do template literals work?**
   - **Syntax**: Backticks `` `text` ``
   - **Interpolation**: `${expression}` embedded
   - **Multi-line**: Supports line breaks naturally
   - **Tagged templates**: Custom string processing
   - **Raw strings**: `String.raw` for escapes

6. **What is the difference between `==` and `===` for strings?**
   - **Same behavior**: For primitive strings, both compare values
   - **Type**: Strings are same type, no coercion needed
   - **Best practice**: Use `===` consistently
   - **Object strings**: `new String('a')` vs `'a'` differ with `===`

7. **How do you convert between strings and arrays?**
   - **String to array**: `str.split('')`, `[...str]`, `Array.from(str)`
   - **Array to string**: `arr.join('')`, `arr.join(' ')`
   - **Split by delimiter**: `str.split(',')`, `str.split(' ')`
   - **Spread**: Modern, handles Unicode better

8. **Explain string concatenation methods**
   - **`+` operator**: Simple, creates new string each time
   - **`concat()`**: `str.concat(str2, str3)`, not commonly used
   - **Template literals**: `` `${str1}${str2}` ``, modern approach
   - **Array join**: For many strings, `[str1, str2].join('')`
   - **Performance**: Array join faster for many concatenations

**Intermediate Level:**
9. **What is the difference between `trim()`, `trimStart()`, and `trimEnd()`?**
   - **`trim()`**: Removes whitespace from both ends
   - **`trimStart()`** / **`trimLeft()`**: Removes from start only
   - **`trimEnd()`** / **`trimRight()`**: Removes from end only
   - **Whitespace**: Spaces, tabs, newlines, etc.

10. **How do `replace()` and `replaceAll()` differ?**
    - **`replace()`**: Replaces first occurrence (or all with global regex)
    - **`replaceAll()`**: Replaces all occurrences (ES2021)
    - **Regex**: `replace(/pattern/g, replacement)` for all
    - **String**: `replaceAll()` simpler than regex for strings

11. **What are the different ways to check if a string contains a substring?**
    - **`includes()`**: Returns boolean, ES6
    - **`indexOf() !== -1`**: Traditional method
    - **`search()` !== -1**: With regex support
    - **`match()`**: Returns array or null
    - **Regex `test()`**: `/pattern/.test(str)`

12. **How does `localeCompare()` work?**
    - Compares strings according to locale
    - Returns: -1 (before), 0 (equal), 1 (after)
    - Use for: Sorting with accents, different languages
    - Example: `'ä'.localeCompare('z', 'de')` // -1

13. **What is the difference between `match()` and `matchAll()`?**
    - **`match()`**: Returns array of matches or null
    - **`matchAll()`**: Returns iterator of all match objects
    - **Global flag**: `match()` returns simple array with /g
    - **Capture groups**: `matchAll()` preserves groups

14. **How do you pad strings in JavaScript?**
    - **`padStart(length, str)`**: Pads at beginning
    - **`padEnd(length, str)`**: Pads at end
    - **Use cases**: Formatting numbers, aligning text
    - **Default**: Pads with spaces if no string provided

15. **Explain Unicode and string encoding**
    - JavaScript strings are UTF-16 encoded
    - Some characters take 2 code units (surrogates)
    - `length` counts code units, not characters
    - Use: `[...str].length` for actual character count
    - **charCodeAt()**: Returns UTF-16 code unit
    - **codePointAt()**: Returns Unicode code point

**Advanced Level:**
16. **What are the performance implications of string operations?**
    - **Immutability**: Each operation creates new string
    - **Concatenation**: `+` in loop is O(n²), use array + join
    - **Large strings**: Memory overhead from intermediate strings
    - **Optimization**: Modern engines optimize simple cases

17. **How do regular expressions work with strings?**
    - **test()**: Regex method, returns boolean
    - **exec()**: Returns match details or null
    - **match()**: String method, returns matches
    - **replace()**: String method with regex
    - **Flags**: g (global), i (ignore case), m (multiline)

18. **What is string interning and how does it work?**
    - Engine stores one copy of identical string literals
    - Saves memory for duplicate strings
    - Happens automatically for literals
    - Not guaranteed for runtime-created strings

19. **How do you handle special characters and escaping?**
    - **Escape sequences**: `\n`, `\t`, `\\`, `\'`, `\"`
    - **Unicode escape**: `\uXXXX` for 4-digit hex
    - **Hex escape**: `\xXX` for 2-digit hex
    - **String.raw**: Ignores escape sequences
    - **JSON**: Use `JSON.stringify()` to escape

20. **What are tagged template literals?**
    - Function that processes template literal
    - Receives: strings array + values
    - Use cases: Sanitization, i18n, styled-components
    - Example: ``sql`SELECT * FROM ${table}` ``
    - Can transform or validate interpolated values

#### **Behavioral & Experience-Based Questions**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Behavioral Questions:**
1. **"Tell me about a time string manipulation was critical to a feature you built. What was the trickiest part?"**
   - *STAR hint*: SEO slug generation for Next.js dynamic routes — edge cases with apostrophes, accented characters, double spaces, leading/trailing hyphens. Built a robust `generateSlug()` utility, wrote 10 test cases for edge cases, now used across the codebase.

2. **"Have you ever had a security vulnerability related to user-input strings (XSS, injection)? How was it caught and fixed?"**
   - *STAR hint*: User input rendered with `innerHTML` or `dangerouslySetInnerHTML` without sanitization. Discovered in code review or security scan. Fixed with DOMPurify / `textContent`, added CSP headers, made it a PR checklist item.

3. **"Describe a time you had to parse or transform data from an external API where everything came as strings."**
   - *STAR hint*: Shopify `total_price: "29.99"`, Airtable dates as ISO strings `"2024-03-15T10:30:00.000Z"`. Built a centralized `parseApiResponse()` normalizer — runs once at the API layer, converts types, formats dates, so components always receive clean data.

**Experience-Based Conceptual:**
4. **"How do you generate SEO-friendly URL slugs for Next.js dynamic product/blog pages? What edge cases do you handle?"**
   - *Answer framework*: Lowercase → trim → replace spaces with `-` → remove special chars with regex `[^a-z0-9-]` → collapse double hyphens → strip leading/trailing hyphens. Handle accented chars with `normalize('NFD')`. Make it a shared `/utils/slug.js` function.

5. **"In a Shopify storefront, product descriptions often contain HTML tags. How do you handle this when you need to truncate to 100 characters?"**
   - *Answer framework*: Strip HTML first (`replace(/<[^>]*>/g, '')`) then truncate, OR use a DOM parser. Never truncate raw HTML mid-tag. For full display, use `dangerouslySetInnerHTML` with sanitization.

6. **"When building a search feature over Airtable data, how do you implement case-insensitive partial matching on the client side?"**
   - *Answer framework*: `record.name.toLowerCase().includes(query.toLowerCase().trim())`. For better UX: debounce the query, normalize accents, handle empty query (show all). For larger datasets: consider Airtable's `filterByFormula` with `SEARCH()` to offload to server.

#### **Programming Tasks (Basic)**
* ✅ Task 1: Reverse a string (multiple methods)
* ✅ Task 2: Count vowels and consonants
* ✅ Task 3: Check for anagram
* ✅ Task 4: Replace vowels with numbers
* ✅ Task 5: Capitalize each word in sentence
* ✅ Task 6: Find longest word in a sentence
* ✅ Task 7: Check if string is palindrome
* ✅ Task 8: Remove extra spaces (trim + reduce)
* ✅ Task 9: Compress string (e.g. aaabb → a3b2)
* ✅ Task 10: Create character frequency map

#### **Interview Coding Tasks**

**String Reversal & Palindrome:**
* ✅ Task 11: Reverse string without built-in methods
* ✅ Task 12: Reverse words in a sentence
* ✅ Task 13: Reverse each word individually
* ✅ Task 14: Check palindrome (ignore spaces, case, punctuation)
* ✅ Task 15: Find longest palindromic substring
* ✅ Task 16: Check if string can form palindrome (permutation)

**Character Operations:**
* ✅ Task 17: Count occurrences of each character
* ✅ Task 18: Find first non-repeating character
* ✅ Task 19: Find first repeating character
* ✅ Task 20: Remove all duplicates from string
* ✅ Task 21: Remove duplicates while maintaining order
* ✅ Task 22: Count uppercase and lowercase letters

**Anagrams:**
* ✅ Task 23: Check if two strings are anagrams
* ✅ Task 24: Group anagrams from array of strings
* ✅ Task 25: Find all anagrams of a pattern in text
* ✅ Task 26: Check if strings are anagrams (optimize with frequency)

**String Matching & Searching:**
* ✅ Task 27: Check if string contains all vowels
* ✅ Task 28: Find all substrings of a string
* ✅ Task 29: Check if string is rotation of another (e.g., "waterbottle" and "erbottlewat")
* ✅ Task 30: Find longest common prefix in array of strings
* ✅ Task 31: Pattern matching without regex (naive approach)
* ✅ Task 32: Check if parentheses/brackets are balanced

**String Transformation:**
* ✅ Task 33: Convert string to title case
* ✅ Task 34: Convert string to camelCase
* ✅ Task 35: Convert string to snake_case
* ✅ Task 36: Convert string to kebab-case
* ✅ Task 37: Toggle case of each character
* ✅ Task 38: Capitalize first letter of each sentence

**Substring Operations:**
* ✅ Task 39: Find all permutations of a string
* ✅ Task 40: Find longest substring without repeating characters
* ✅ Task 41: Find longest substring with K unique characters
* ✅ Task 42: Find smallest window containing all characters of pattern
* ✅ Task 43: Find all substrings that are palindromes

**String Compression & Encoding:**
* ✅ Task 44: Run-length encoding (aaabbc → a3b2c1)
* ✅ Task 45: Run-length decoding (a3b2c1 → aaabbc)
* ✅ Task 46: Remove all spaces from string
* ✅ Task 47: Replace all spaces with %20 (URL encoding)
* ✅ Task 48: Encode string using Caesar cipher
* ✅ Task 49: Decode Caesar cipher

**Validation & Formatting:**
* ✅ Task 50: Validate email address (basic)
* ✅ Task 51: Validate phone number format
* ✅ Task 52: Check if string is valid number
* ✅ Task 53: Format number with commas (1234567 → 1,234,567)
* ✅ Task 54: Validate credit card number (Luhn algorithm)

**Word Operations:**
* ✅ Task 55: Count words in a string
* ✅ Task 56: Find most frequent word
* ✅ Task 57: Find shortest word
* ✅ Task 58: Remove specific word from string
* ✅ Task 59: Sort words alphabetically
* ✅ Task 60: Find words with specific length

**Advanced String Challenges:**
* ✅ Task 61: Implement indexOf() from scratch
* ✅ Task 62: Implement strStr() (needle in haystack)
* ✅ Task 63: Check if one string is subsequence of another
* ✅ Task 64: Find edit distance (Levenshtein distance)
* ✅ Task 65: Implement wildcard pattern matching (* and ?)

**Character Encoding:**
* ✅ Task 66: Convert string to ASCII array
* ✅ Task 67: Convert ASCII array to string
* ✅ Task 68: Find character with highest ASCII value
* ✅ Task 69: Sort string characters by ASCII value
* ✅ Task 70: Handle Unicode characters correctly

**String Parsing:**
* ✅ Task 71: Parse CSV string to array
* ✅ Task 72: Parse query string to object
* ✅ Task 73: Extract numbers from string
* ✅ Task 74: Extract URLs from text
* ✅ Task 75: Parse JSON string safely

**Edge Cases:**
* ✅ Task 76: Handle empty strings in all operations
* ✅ Task 77: Handle strings with special characters
* ✅ Task 78: Handle very long strings efficiently
* ✅ Task 79: Trim whitespace including unicode spaces
* ✅ Task 80: Compare strings case-insensitively

**Real-World Applications:**
* ✅ Task 81: Create a simple template engine
* ✅ Task 82: Implement string sanitization for SQL injection
* ✅ Task 83: Create a simple markdown parser
* ✅ Task 84: Implement autocomplete/search suggestions
* ✅ Task 85: Build a simple text diff algorithm
* ✅ Task 86: Implement string masking (e.g., for credit cards)
* ✅ Task 87: Create slug from title (for URLs)
* ✅ Task 88: Implement text truncation with ellipsis
* ✅ Task 89: Highlight search terms in text
* ✅ Task 90: Create initials from full name

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Generate a URL-safe filename from a product title: `"Men's Blue T-Shirt #1"` → `"mens-blue-t-shirt-1"` (for GoDaddy media uploads)
* ⬜ RW-2: Build an email template system: replace `{{name}}`, `{{orderNumber}}`, `{{total}}` placeholders with real values using `.replace()` or template literals

**React / Next.js:**
* ⬜ RW-3: Create a Next.js `generateSlug(title)` utility: convert blog post or product titles into SEO-friendly URL segments (lowercase, hyphens, no special chars)
* ⬜ RW-4: Build a `truncateText(text, maxLength)` component for product cards — append `"..."` if truncated, add a "Read more" toggle

**Airtable API:**
* ⬜ RW-5: Parse Airtable ISO date strings (`"2024-03-15T10:30:00.000Z"`) — format for display as `"March 15, 2024"` and relative time like `"3 days ago"`
* ⬜ RW-6: Build a case-insensitive record search: use `.toLowerCase().includes(query.toLowerCase())` on Airtable name fields to filter results

**Shopify:**
* ⬜ RW-7: Parse a Shopify product handle back to a readable title: `"mens-blue-t-shirt"` → `"Mens Blue T Shirt"` — capitalize each word
* ⬜ RW-8: Extract and display domain from a full Shopify store URL: `"https://my-store.myshopify.com/products/item"` → `"my-store.myshopify.com"`

**VPS / Server:**
* ⬜ RW-9: Build a server log line parser: given `"[2024-03-15 10:30:22] ERROR: DB connection failed"` — extract timestamp, log level, and message using string methods
* ⬜ RW-10: Create a `.env` string parser: given a multiline string of `KEY=value` pairs, convert to a JS object `{KEY: value}` using split/trim

### **Day 6: Array Methods**

#### **Core Concepts**
* ✅ Higher-order array methods: map, filter, reduce
* ✅ Search methods: find, findIndex, findLast, findLastIndex
* ✅ Test methods: some, every, includes
* ✅ Iteration methods: forEach, entries, keys, values
* ✅ Transformation: flat, flatMap
* ✅ Sorting: sort, reverse, toSorted, toReversed
* ✅ Modification: fill, copyWithin
* ✅ Array to value: join, toString, toLocaleString
* ✅ Method chaining patterns
* ✅ Immutability with array methods

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **What is the difference between `map()` and `forEach()`?**
   - **`map()`**: Returns new array with transformed elements
   - **`forEach()`**: Returns undefined, just iterates (side effects)
   - **Use map**: When transforming data
   - **Use forEach**: When performing actions (logging, DOM updates)
   - **Chaining**: `map()` can be chained, `forEach()` cannot

2. **How does `filter()` work?**
   - Creates new array with elements passing test
   - Callback returns truthy/falsy value
   - Original array unchanged (immutable)
   - Returns empty array if no matches
   - Time complexity: O(n)

3. **Explain `reduce()` and its use cases**
   - Reduces array to single value
   - Accumulator + current value → new accumulator
   - Takes: callback(accumulator, current, index, array) + initial value
   - Use cases: Sum, product, grouping, flattening, counting
   - Can replace many map + filter combinations

4. **What's the difference between `find()` and `filter()`?**
   - **`find()`**: Returns first matching element or undefined
   - **`filter()`**: Returns array of all matching elements
   - **Performance**: `find()` stops at first match (faster)
   - **Use find**: When expecting single result
   - **Use filter**: When needing all matches

5. **How do `some()` and `every()` differ?**
   - **`some()`**: Returns true if ANY element passes test
   - **`every()`**: Returns true if ALL elements pass test
   - **Short-circuit**: Both stop early when result determined
   - **Empty array**: `some()` returns false, `every()` returns true
   - **Use cases**: Validation, checking conditions

6. **What does `findIndex()` do and how is it different from `indexOf()`?**
   - **`findIndex()`**: Uses callback function, returns index or -1
   - **`indexOf()`**: Uses strict equality, returns index or -1
   - **Flexibility**: `findIndex()` for complex conditions
   - **Simple values**: `indexOf()` faster for primitives
   - **Objects**: `findIndex()` needed for object properties

7. **How does `sort()` work in JavaScript?**
   - Sorts array in-place (mutates original)
   - Default: Converts to strings, sorts lexicographically
   - Problem: `[1, 10, 2]` → `[1, 10, 2]` (string order)
   - Solution: Provide comparator: `(a, b) => a - b`
   - **Stable**: Since ES2019, maintains relative order

8. **What is the difference between `slice()` and `splice()`?**
   - **`slice(start, end)`**: Returns shallow copy, immutable
   - **`splice(start, deleteCount, ...items)`**: Mutates, can add/remove
   - **Return**: slice returns portion, splice returns deleted elements
   - **Use slice**: For copying or extracting
   - **Use splice**: For modifying array

**Intermediate Level:**
9. **How does `reduce()` work with an initial value vs without?**
   - **With initial**: Starts from first element, uses initial as accumulator
   - **Without initial**: Uses first element as accumulator, starts from second
   - **Empty array**: Without initial throws TypeError
   - **Best practice**: Always provide initial value for safety

10. **What is the difference between `flat()` and `flatMap()`?**
    - **`flat(depth)`**: Flattens nested arrays to specified depth
    - **`flatMap(callback)`**: Maps then flattens one level
    - **Equivalent**: `arr.map(fn).flat()` but more efficient
    - **Use flatMap**: When mapping produces arrays to flatten

11. **Explain method chaining with array methods**
    - Multiple methods called in sequence
    - Each method returns array (or value for reduce)
    - Example: `arr.filter(...).map(...).reduce(...)`
    - **Performance**: Each creates intermediate array
    - **Readability**: Very clear, declarative code

12. **What are the "new" immutable array methods in ES2023?**
    - **`toSorted()`**: Like sort() but returns new array
    - **`toReversed()`**: Like reverse() but returns new array
    - **`toSpliced()`**: Like splice() but returns new array
    - **`with(index, value)`**: Returns new array with element replaced
    - **Why**: Enable functional programming, avoid mutations

13. **How does `Array.from()` work?**
    - Converts array-like or iterable to array
    - Takes optional mapping function (second argument)
    - Can create arrays with specific length and values
    - Example: `Array.from({length: 5}, (_, i) => i)` → `[0,1,2,3,4]`
    - Better than `Array.prototype.slice.call()` for readability

14. **What is the difference between `includes()` and `indexOf()`?**
    - **`includes()`**: Returns boolean, can find NaN
    - **`indexOf()`**: Returns index or -1, cannot find NaN
    - **Readability**: `includes()` clearer for existence check
    - **Performance**: Similar, both O(n)
    - **Use includes**: For boolean checks, use indexOf for position

15. **Explain the callback parameters in array methods**
    - **Standard**: `(element, index, array) => {}`
    - **element**: Current item being processed
    - **index**: Current index (optional)
    - **array**: Original array being processed (optional)
    - **Usually**: Only first parameter needed

**Advanced Level:**
16. **What are the performance implications of array methods?**
    - **map/filter/reduce**: O(n), create new arrays (memory)
    - **Chaining**: Multiple passes through array
    - **Alternative**: Single reduce for multiple operations
    - **forEach**: No new array, but can't break/return early
    - **for loop**: Faster for performance-critical code

17. **How does `sort()` work internally?**
    - Engine-dependent algorithm (V8 uses TimSort)
    - Stable sort since ES2019
    - Comparator: return negative (a first), 0 (equal), positive (b first)
    - **Mutates**: Original array changed
    - **Time**: O(n log n) typically

18. **Explain the difference between mutating and non-mutating methods**
    - **Mutating**: push, pop, shift, unshift, splice, sort, reverse, fill
    - **Non-mutating**: map, filter, slice, concat, flat, spread
    - **ES2023**: toSorted, toReversed, toSpliced (non-mutating versions)
    - **Best practice**: Prefer non-mutating for predictability

19. **How can you use `reduce()` to implement other array methods?**
    - Can replicate map, filter, find, some, every
    - Example map: `arr.reduce((acc, x) => [...acc, x * 2], [])`
    - **Powerful**: Single iteration for multiple operations
    - **Tradeoff**: Readability vs performance

20. **What is transducing and how does it relate to reduce?**
    - Composing multiple transformations into single reduce
    - Avoids intermediate arrays from chaining
    - More efficient but less readable
    - Libraries: Ramda, Lodash/fp support transducers

#### **Behavioral & Experience-Based Questions**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Behavioral Questions:**
1. **"Tell me about a data transformation task where chaining `map/filter/reduce` was key to your solution."**
   - *STAR hint*: Transforming raw Airtable records for a chart/table — needed to filter active records, reshape field names to camelCase, then reduce to totals. Chained in one pipeline. Readable, no temp variables. Showed in PR as the "right way" for the team.

2. **"Describe a time you improved the readability of some code by replacing loops with array methods. What feedback did you get?"**
   - *STAR hint*: Replaced nested `for` loops computing totals/groupings with a single `.reduce()`. PR reviewer commented on clarity. Became a team convention. (Have an example ready — even from a side project.)

3. **"Have you ever written a `.map().filter().map()` chain that caused performance issues with a large dataset? How did you optimize it?"**
   - *STAR hint*: Three chained array methods creating three intermediate arrays on 10k+ records. Used a single `.reduce()` that did all three operations in one pass. Or switched to server-side filtering to reduce the dataset before it reaches the client.

**Experience-Based Conceptual:**
4. **"How do you use `reduce()` to transform an array of Shopify orders into an object grouped by fulfillment status?"**
   - *Answer framework*: `orders.reduce((acc, order) => { const key = order.fulfillment_status || 'pending'; acc[key] = [...(acc[key] || []), order]; return acc; }, {})`. Result: `{pending: [...], fulfilled: [...]}`. Classic reduce-to-object pattern, expect to write this in an interview.

5. **"When should you add `useMemo` around a `.filter()` or `.sort()` in a React component? When is it overkill?"**
   - *Answer framework*: Add `useMemo` when: the array has 100+ items AND the sort/filter is O(n log n) AND the component re-renders frequently for unrelated reasons. Overkill when: array is small (< 20 items), or the component rarely re-renders. Measure first with React Profiler, don't premature-optimize.

6. **"What happens if you call `.map()` on an Airtable record's linked-field that might be `null` or `undefined`? How do you guard against it?"**
   - *Answer framework*: `record.linkedField?.map(fn) ?? []` — optional chaining prevents TypeError, nullish coalescing ensures you always get an array. Alternative: `(record.linkedField || []).map(fn)`. Make this a habit for all API data. Never assume any field is always present.

#### **Programming Tasks (Basic)**
* ✅ Task 1: Double each element using `map`
* ✅ Task 2: Filter even numbers using `filter`
* ✅ Task 3: Use `reduce` to sum array
* ✅ Task 4: Count words starting with specific letter
* ✅ Task 5: Convert array to object using reduce
* ✅ Task 6: Find first even number using `find`
* ✅ Task 7: Check if all elements are positive using `every`
* ✅ Task 8: Use `sort` to order elements
* ✅ Task 9: Group elements by type
* ✅ Task 10: Flatten a 2D array using `flat`

#### **Interview Coding Tasks**

**map() Challenges:**
* ✅ Task 11: Extract specific property from array of objects
* ✅ Task 12: Convert array of numbers to strings
* ✅ Task 13: Transform array of temperatures (C to F)
* ✅ Task 14: Add index to each element
* ✅ Task 15: Create new objects with additional properties

**filter() Challenges:**
* ✅ Task 16: Filter objects by property value
* ✅ Task 17: Remove falsy values from array
* ✅ Task 18: Filter array based on another array (whitelist)
* ✅ Task 19: Filter prime numbers
* ✅ Task 20: Filter strings by length

**reduce() Challenges:**
* ✅ Task 21: Find maximum value using reduce
* ✅ Task 22: Find minimum value using reduce
* ✅ Task 23: Calculate product of all numbers
* ✅ Task 24: Flatten array of arrays using reduce
* ✅ Task 25: Count occurrences of each element (frequency map)
* ✅ Task 26: Group objects by property
* ✅ Task 27: Remove duplicates using reduce
* ✅ Task 28: Create object from two arrays (keys and values)
* ✅ Task 29: Implement map() using reduce
* ✅ Task 30: Implement filter() using reduce
* ✅ Task 31: Build a pipeline of transformations
* ✅ Task 32: Calculate average using reduce

**find() & findIndex():**
* ✅ Task 33: Find first element greater than value
* ✅ Task 34: Find object by id
* ✅ Task 35: Find index of first negative number
* ✅ Task 36: Find last occurrence (using findLast)
* ✅ Task 37: Find element closest to target value

**some() & every():**
* ✅ Task 38: Check if array contains any negative numbers
* ✅ Task 39: Check if all elements are strings
* ✅ Task 40: Validate form data (all fields filled)
* ✅ Task 41: Check if any element matches pattern
* ✅ Task 42: Check if array is sorted

**sort() Challenges:**
* ✅ Task 43: Sort numbers in ascending order
* ✅ Task 44: Sort numbers in descending order
* ✅ Task 45: Sort strings alphabetically (case-insensitive)
* ✅ Task 46: Sort objects by property
* ✅ Task 47: Sort by multiple criteria (primary, secondary)
* ✅ Task 48: Custom sort (odds first, then evens)
* ✅ Task 49: Sort by string length
* ✅ Task 50: Stable sort demonstration

**flat() & flatMap():**
* ✅ Task 51: Flatten nested array (all levels)
* ✅ Task 52: Flatten array with specific depth
* ✅ Task 53: Use flatMap to transform and flatten
* ✅ Task 54: Split strings and flatten results
* ✅ Task 55: Remove empty arrays while flattening

**Method Chaining:**
* ✅ Task 56: Filter, map, then reduce in chain
* ✅ Task 57: Transform data through multiple steps
* ✅ Task 58: Clean and process data pipeline
* ✅ Task 59: Chain with error handling
* ✅ Task 60: Optimize chained operations

**forEach() & Iteration:**
* ✅ Task 61: Log each element with index
* ✅ Task 62: Modify external variable (side effect)
* ✅ Task 63: Update DOM elements with forEach
* ✅ Task 64: Compare forEach vs for loop performance
* ✅ Task 65: Demonstrate when forEach cannot be used

**includes() & indexOf():**
* ✅ Task 66: Check if array includes NaN
* ✅ Task 67: Find all indices of an element
* ✅ Task 68: Check multiple values exist in array
* ✅ Task 69: Use includes for validation
* ✅ Task 70: Custom includes for objects

**Advanced reduce():**
* ✅ Task 71: Compose functions using reduce
* ✅ Task 72: Pipe functions using reduce
* ✅ Task 73: Deep flatten using reduce
* ✅ Task 74: Build nested object from flat array
* ✅ Task 75: Implement partition (split by condition)
* ✅ Task 76: Calculate running totals (cumulative sum)
* ✅ Task 77: Find unique values using reduce
* ✅ Task 78: Merge array of objects

**Immutability Patterns:**
* ✅ Task 79: Use toSorted() instead of sort()
* ✅ Task 80: Use toReversed() instead of reverse()
* ✅ Task 81: Use toSpliced() for immutable splice
* ✅ Task 82: Use with() to replace element
* ✅ Task 83: Compare mutable vs immutable approaches

**Combining Methods:**
* ✅ Task 84: Filter then map (method chain)
* ✅ Task 85: Map then reduce (sum of squares)
* ✅ Task 86: Filter, map, sort combination
* ✅ Task 87: Find then transform result
* ✅ Task 88: Use every() with complex condition

**Real-World Applications:**
* ✅ Task 89: Process shopping cart (total price)
* ✅ Task 90: Filter and sort products by price
* ✅ Task 91: Group transactions by date
* ✅ Task 92: Calculate statistics (min, max, avg, median)
* ✅ Task 93: Implement search with multiple filters
* ✅ Task 94: Paginate results
* ✅ Task 95: Transform API response data
* ✅ Task 96: Build aggregation pipeline
* ✅ Task 97: Implement custom array method (polyfill)
* ✅ Task 98: Create utility functions using array methods
* ✅ Task 99: Optimize nested loops with array methods
* ✅ Task 100: Build a data transformation library

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Filter a product list by category and price range using `.filter()` — update the DOM dynamically on input change, no page reload
* ⬜ RW-2: Use `.reduce()` to calculate cart subtotal, tax (8%), and grand total from `[{price, qty}]` — display each value separately

**React / Next.js:**
* ⬜ RW-3: Build a Next.js product listing page: chain `.filter()` (search) + `.sort()` (price) + `.map()` (render cards) in one clean pipeline
* ⬜ RW-4: Create a React analytics dashboard: `.reduce()` Airtable records to get `totalSales`, `avgOrderValue`, and `countByStatus` in one pass

**Airtable API:**
* ⬜ RW-5: Transform raw Airtable records with `.map()` — normalize field names from `"Order Total (USD)"` to `orderTotal`, rename all fields to camelCase
* ⬜ RW-6: Use `.filter()` to show only Airtable records modified in the last 7 days — compare ISO date string field with `new Date(Date.now() - 7 * 86400000)`

**Shopify:**
* ⬜ RW-7: Use `.map()` to transform raw Shopify products into `{id, title, price, image}` shape — feed directly into a product card component
* ⬜ RW-8: Use `.reduce()` on Shopify orders to group by fulfillment status: output `{pending: [...], fulfilled: [...], cancelled: [...]}`

**Laravel / Python Flask:**
* ⬜ RW-9: Handle a Laravel paginated response: `.flatMap()` all pages into one array, then chain `.filter().sort()` for client-side data manipulation
* ⬜ RW-10: Build a report generator from Flask API data: chain `.filter().map().reduce()` to produce a formatted summary — total revenue, top product, avg order

---

## **🗓️ Week 3: Core DSA – Searching & Sorting**

### **Day 7: Searching Algorithms**

#### **Core Concepts**
* ✅ Linear Search - O(n) time complexity
* ✅ Binary Search - O(log n) time complexity, requires sorted array
* ✅ Binary Search variations (iterative & recursive)
* ✅ Search space reduction technique
* ✅ Two-pointer technique
* ✅ Modified binary search patterns

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **What is Linear Search and when to use it?**
   - Sequential search through array
   - Time: O(n), Space: O(1)
   - Works on unsorted arrays
   - Simple but inefficient for large datasets

2. **How does Binary Search work?**
   - Divide and conquer on sorted array
   - Compare middle element, eliminate half
   - Time: O(log n), Space: O(1) iterative, O(log n) recursive
   - Requires sorted input

3. **What are the prerequisites for Binary Search?**
   - Array must be sorted
   - Random access (array-like structure)
   - Comparable elements

4. **Iterative vs Recursive Binary Search?**
   - Iterative: Better space complexity O(1)
   - Recursive: More intuitive, O(log n) stack space
   - Both same time complexity

5. **How to find first and last occurrence?**
   - Modified binary search
   - For first: Continue left even after finding
   - For last: Continue right even after finding

**Intermediate Level:**
6. **How to search in rotated sorted array?**
   - Find pivot point or use modified binary search
   - Check which half is sorted
   - Decide which half to search

7. **How to find square root using binary search?**
   - Search space: 0 to n
   - Find largest number whose square ≤ n
   - Binary search on answer

8. **What is the difference between floor and ceiling?**
   - Floor: Largest element ≤ target
   - Ceiling: Smallest element ≥ target
   - Both use modified binary search

**Advanced Level:**
9. **How to search in 2D matrix?**
   - Treat as 1D array: mid = row * cols + col
   - Or start from top-right/bottom-left
   - Time: O(log(m*n)) or O(m+n)

10. **What is binary search on answer?**
    - Search space is range of possible answers
    - Check if mid value is valid answer
    - Used in optimization problems

#### **Behavioral & Experience-Based Questions**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Behavioral Questions:**
1. **"Tell me about a time you implemented a search feature in a production app. What approach did you take and why?"**
   - *STAR hint*: Product or record search in Shopify/Airtable. Started with linear search (fine for < 200 items). As data grew, added debounce + server-side filtering. Or sorted the list once and used binary search for instant client-side lookups. Explain the decision boundary.

2. **"Have you ever had a search feature that was too slow or causing too many API calls? How did you fix it?"**
   - *STAR hint*: Search triggering an API call on every keystroke. Added `debounce(fn, 300)` — reduced calls by 90%. Also added a loading spinner so users knew it was working. If still slow, cached results in a Map keyed by query string.

3. **"Describe a situation where you had to choose between client-side and server-side search. How did you make the decision?"**
   - *STAR hint*: Rule of thumb: < 500 records = client-side (fetch once, filter locally, instant UX). > 500 records or sensitive data = server-side (Airtable `filterByFormula`, Shopify API search, or database query). Describe a specific project where you applied this.

**Experience-Based Conceptual:**
4. **"For a Shopify storefront with 500+ products, how would you implement a fast product search? Walk through your full approach."**
   - *Answer framework*: On page load, fetch all products into a cached array. Sort by title alphabetically. Use binary search for exact match lookups (O(log n)). For partial/fuzzy search, linear scan with `.includes()` + debounce (acceptable for 500 items). Cache results per query in a Map.

5. **"How would you build real-time search for an Airtable-backed app while respecting the 5 requests/second rate limit?"**
   - *Answer framework*: Debounce user input (300ms delay), cancel previous pending request if new query arrives. Cache results: if query was searched before within 60 seconds, return cached. Use Airtable `filterByFormula` with `SEARCH()` to do server-side filtering — return only matching records, not all 1000.

6. **"When is binary search appropriate in a real frontend app, and when would you just use a database or API query instead?"**
   - *Answer framework*: Binary search is appropriate for: static sorted data already on the client (e.g., country list, pre-fetched sorted products), repeated lookups in a session (build index once, search many times). Use API/DB query when: data is too large for client, data changes frequently, or search needs full-text/fuzzy matching.

#### **Programming Tasks (Basic)**
* ✅ Task 1: Implement linear search
* ✅ Task 2: Implement binary search (iterative)
* ✅ Task 3: Implement binary search (recursive)
* ✅ Task 4: Find first and last occurrence
* ✅ Task 5: Count occurrences of element
* ✅ Task 6: Search in rotated sorted array
* ✅ Task 7: Find square root using binary search
* ✅ Task 8: Find peak element
* ✅ Task 9: Find floor and ceil
* ✅ Task 10: Search in 2D matrix

#### **Interview Coding Tasks**
* ✅ Task 11: Search insert position
* ✅ Task 12: Find minimum in rotated sorted array
* ✅ Task 13: Search in row-wise and column-wise sorted matrix
* ✅ Task 14: Find peak element in 2D array
* ✅ Task 15: Median of two sorted arrays
* ✅ Task 16: Find K closest elements
* ✅ Task 17: Find first bad version (binary search)
* ✅ Task 18: Single element in sorted array
* ✅ Task 19: Capacity to ship packages within D days
* ✅ Task 20: Koko eating bananas
* ✅ Task 21: Minimize max distance to gas station
* ✅ Task 22: Aggressive cows problem
* ✅ Task 23: Book allocation problem
* ✅ Task 24: Painter's partition problem
* ✅ Task 25: Find nth root using binary search

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Build a product search bar for a static HTML/JS site — linear search through a product array on keyup, highlight matching text in results
* ⬜ RW-2: Create a country/city autocomplete input — sort the list alphabetically first, then use binary search to find suggestions as user types

**React / Next.js:**
* ⬜ RW-3: Build a Next.js `/search` page — client-side binary search on sorted product titles cached from Shopify API, instant results with no re-fetch
* ⬜ RW-4: Implement a "Jump to Record" feature in a React data table — binary search sorted records by ID to scroll directly to that row

**Airtable API:**
* ⬜ RW-5: Fetch all Airtable records once, sort by record ID, then use binary search client-side for instant lookup — avoid repeated API calls
* ⬜ RW-6: Build a search-as-you-type feature over cached Airtable data — linear search on name/title field, debounced to prevent excessive re-renders

**Shopify:**
* ⬜ RW-7: Given a sorted Shopify product price list, use binary search to find the cheapest product at or above a user's minimum budget
* ⬜ RW-8: Implement SKU lookup: linear search through Shopify `line_items` to find a product by exact SKU code, return `null` with a friendly message if not found

**VPS / Server:**
* ⬜ RW-9: Parse sorted server access logs — use binary search to find the first log entry after a given timestamp (e.g., "show all errors after 3:00 PM")
* ⬜ RW-10: Build an IP blocklist checker — given a sorted array of blocked IP ranges, use binary search to check if an incoming request IP should be blocked

### **Day 8: Sorting Algorithms**

#### **Core Concepts**
* ✅ Bubble Sort - O(n²), stable, in-place
* ✅ Selection Sort - O(n²), unstable, in-place
* ✅ Insertion Sort - O(n²), stable, in-place, efficient for small/nearly sorted
* ✅ Merge Sort - O(n log n), stable, not in-place
* ✅ Quick Sort - O(n log n) average, O(n²) worst, unstable, in-place
* ✅ Counting Sort - O(n+k), stable, not in-place
* ✅ Stable vs Unstable sorting
* ✅ In-place vs Out-of-place sorting

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **What is a stable sort?**
   - Maintains relative order of equal elements
   - Stable: Bubble, Insertion, Merge
   - Unstable: Selection, Quick, Heap

2. **What is in-place sorting?**
   - Sorts with O(1) extra space
   - In-place: Bubble, Selection, Insertion, Quick
   - Not in-place: Merge, Counting

3. **Compare Bubble, Selection, and Insertion Sort**
   - All O(n²) time complexity
   - Bubble: Repeatedly swap adjacent
   - Selection: Find min, place at beginning
   - Insertion: Build sorted array one by one

4. **When to use Insertion Sort?**
   - Small datasets (n < 10-20)
   - Nearly sorted arrays
   - Online sorting (data comes one at a time)

5. **How does Merge Sort work?**
   - Divide array into halves recursively
   - Sort each half
   - Merge sorted halves
   - Time: O(n log n), Space: O(n)

**Intermediate Level:**
6. **How does Quick Sort work?**
   - Choose pivot element
   - Partition array around pivot
   - Recursively sort left and right
   - Average: O(n log n), Worst: O(n²)

7. **How to choose a good pivot in Quick Sort?**
   - Random pivot: Avoid worst case
   - Median-of-three: First, middle, last
   - Avoid already sorted arrays causing O(n²)

8. **What is the Dutch National Flag problem?**
   - Sort array of 0s, 1s, 2s
   - Use three pointers (low, mid, high)
   - One pass, O(n) time, O(1) space

9. **How does Counting Sort work?**
   - Count frequency of each element
   - Calculate cumulative count
   - Place elements in correct position
   - Time: O(n+k), works for integers in range

10. **What is the difference between comparison and non-comparison sorts?**
    - Comparison: Compare elements (Bubble, Merge, Quick)
    - Non-comparison: Use other properties (Counting, Radix, Bucket)
    - Lower bound for comparison: O(n log n)

**Advanced Level:**
11. **How does JavaScript's Array.sort() work?**
    - V8 uses TimSort (Merge + Insertion)
    - Stable since ES2019
    - Default: Converts to strings (lexicographic)

12. **What is TimSort?**
    - Hybrid of Merge Sort and Insertion Sort
    - Used in Python, Java, V8
    - Optimized for real-world data
    - Time: O(n log n), Space: O(n)

13. **How to sort with custom comparator?**
    - Comparator function: (a, b) => number
    - Return negative: a before b
    - Return 0: maintain order
    - Return positive: b before a

14. **What is external sorting?**
    - Sorting data that doesn't fit in memory
    - Use merge sort on chunks
    - Read/write from disk

15. **How to find Kth largest/smallest element efficiently?**
    - QuickSelect: O(n) average, O(n²) worst
    - Min/Max Heap: O(n log k)
    - Don't sort entire array

#### **Behavioral & Experience-Based Questions**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Behavioral Questions:**
1. **"Tell me about a time you implemented a custom sort for a complex business requirement. What was the sorting criteria?"**
   - *STAR hint*: Sorting Shopify products by discount percentage, then by rating for ties, then alphabetically. Built a chained comparator function. In code review, the team asked "why not sort server-side?" — explain your reasoning (avoid extra API call, already have data client-side).

2. **"Have you ever had a sorting bug in production — items appearing in the wrong order? How did you identify and fix it?"**
   - *STAR hint*: JavaScript's `.sort()` converts to strings by default — `[10, 9, 2].sort()` gives `[10, 2, 9]`. Classic numeric sort bug. Fix: always pass a comparator `(a, b) => a - b`. Discovered by testing with numbers > 9 in QA. Added test for this case.

3. **"Describe how you've handled sorting a large dataset that was too big to load all at once."**
   - *STAR hint*: 5000+ Airtable or Shopify records. Server-side sort via API query params (`sortField`, `sortDirection`). Client-side sort only for the current page. Paginated display. Explain the UX tradeoff: server-sort = correct global order; client-sort = only sorts current page.

**Experience-Based Conceptual:**
4. **"Shopify API returns products in a random order. How do you implement a 'Sort by: Price Low to High / High to Low / Newest' dropdown on your storefront?"**
   - *Answer framework*: Create a `sortProducts(products, sortKey)` function with a `switch`: `price-asc` → `(a,b) => a.price - b.price`, `price-desc` → reverse, `newest` → compare `createdAt` dates. Store the current sort key in state, re-sort the cached array on change — no re-fetch needed.

5. **"Why is stability important when sorting a list of orders, and how do you ensure stable sort in JavaScript?"**
   - *Answer framework*: Stability = equal elements keep their original relative order. Matters when sorting by status then by date — you want same-status orders in their original time order. Modern JS `.sort()` is stable (guaranteed since V8 7.0 / Node 11+). For older environments, use a stable sort library or add a tiebreaker key.

6. **"You have Airtable records with timestamps and you want to sort by date descending. What pitfalls should you watch for?"**
   - *Answer framework*: Airtable returns dates as ISO strings — compare as `new Date(b.createdAt) - new Date(a.createdAt)`. Pitfall 1: string comparison of dates only works if format is consistent ISO. Pitfall 2: `null` dates crash the comparator — add null check (`a.createdAt ? ... : -1`). Pitfall 3: `.sort()` mutates the array — spread/copy first.

#### **Programming Tasks (Basic)**
* ✅ Task 1: Implement Bubble Sort
* ✅ Task 2: Implement Selection Sort
* ✅ Task 3: Implement Insertion Sort
* ✅ Task 4: Implement Merge Sort
* ✅ Task 5: Implement Quick Sort
* ✅ Task 6: Sort array of strings
* ✅ Task 7: Sort numbers descending
* ✅ Task 8: Sort by frequency
* ✅ Task 9: Dutch National Flag problem (0s, 1s, 2s)
* ✅ Task 10: Merge two sorted arrays

#### **Interview Coding Tasks**
* ✅ Task 11: Find K largest elements
* ✅ Task 12: Find K smallest elements
* ✅ Task 13: Find Kth largest element (QuickSelect)
* ✅ Task 14: Sort colors (similar to Dutch flag)
* ✅ Task 15: Sort array by parity (even first, then odd)
* ✅ Task 16: Sort array by absolute difference from target
* ✅ Task 17: Wiggle sort (arr[0] ≤ arr[1] ≥ arr[2] ≤ arr[3]...)
* ✅ Task 18: Pancake sorting
* ✅ Task 19: Minimum number of swaps to sort
* ✅ Task 20: Count inversions in array
* ✅ Task 21: Merge K sorted arrays
* ✅ Task 22: Sort linked list using merge sort
* ✅ Task 23: Sort array with squares of sorted array
* ✅ Task 24: Largest number from array (arrange to form largest)
* ✅ Task 25: Custom sort with multiple criteria
* ✅ Task 26: Sort matrix diagonally
* ✅ Task 27: Sort array based on another array
* ✅ Task 28: Minimum absolute difference
* ✅ Task 29: Relative sort array
* ✅ Task 30: Height checker (minimum students not in positions)

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Sort a product list on a static HTML page by price ascending/descending when user clicks a button — use `.sort()` with a comparator, re-render the list
* ⬜ RW-2: Build a sortable admin table for order history — toggle ascending/descending sort on any column header (name, date, amount)

**React / Next.js:**
* ⬜ RW-3: Build a React product grid with sort controls: "Price: Low to High", "Price: High to Low", "Newest First", "Best Seller" using custom comparator functions
* ⬜ RW-4: Create a Next.js admin orders page: sort by `createdAt` descending; for same-day orders, secondary sort by `totalAmount` largest first

**Airtable API:**
* ⬜ RW-5: Fetch Airtable inventory records and sort client-side by `stockCount` ascending — highlight items where `stockCount < 5` as "Low Stock" in red
* ⬜ RW-6: Sort Airtable form submissions by submission date and render as a chronological activity timeline

**Shopify:**
* ⬜ RW-7: Sort Shopify products by discount amount (`compareAtPrice - price`) descending — display as "Best Deals" section showing highest savings first
* ⬜ RW-8: Multi-level sort on Shopify orders: primary = fulfillment status order (`pending → processing → fulfilled`), secondary = order total descending

**Laravel / Python Flask:**
* ⬜ RW-9: Receive an unsorted list from Flask API with identical timestamps — use merge sort (stable) to preserve original insertion order for ties
* ⬜ RW-10: Build a leaderboard: fetch user scores from Laravel API, sort descending by score; for tied scores, sort alphabetically by name (stable sort required)

---

## **🗓️ Week 4: Intermediate DSA – Recursion and Hashing**

### **Day 9: Recursion**

* ✅ Basics of recursion, base cases

* ✅ Task 1: Sum of array using recursion

* ✅ Task 2: Fibonacci sequence

* ✅ Task 3: Print numbers from N to 1

* ✅ Task 4: Count digits recursively

* ✅ Task 5: Binary search using recursion

* ✅ Task 6: Reverse string recursively

* ✅ Task 7: Check palindrome

* ✅ Task 8: Tower of Hanoi

* ✅ Task 9: Subsets of a string

* ✅ Task 10: Generate all permutations

#### **Interview Questions & Behavioral**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Conceptual Questions:**
1. **What is recursion and when would you prefer it over a loop?**
   - When the problem is naturally self-similar (trees, nested structures, divide & conquer). Use recursion for clarity on hierarchical data. Use iteration when stack depth is a concern (deep nesting) or for simple sequential tasks.

2. **What is a base case? What happens if you forget it?**
   - The condition that stops recursion. Without it, the function calls itself forever → call stack overflow → `RangeError: Maximum call stack size exceeded`. Every recursive function MUST have a base case.

3. **What is "call stack overflow" and how do you prevent it in real projects?**
   - Happens when recursion depth exceeds the engine's stack limit (~10k-15k calls in V8). Prevention: add a depth/max guard parameter, convert to iterative with an explicit stack, or use tail-call optimization (limited browser support).

4. **What is memoization in recursion? How does it improve performance?**
   - Caching results of expensive recursive calls. `memo[n]` stores already-computed values. Converts exponential O(2ⁿ) to linear O(n). Essential for Fibonacci, DP problems. Real-world: cache API responses, avoid redundant tree traversals.

5. **Depth-First Search (DFS) vs Breadth-First Search (BFS) — when to use each in a real app?**
   - DFS: Go deep first. Good for: finding paths, checking if a path exists, tree traversal (pre/in/post-order). Uses recursion or a stack. BFS: Level by level. Good for: shortest path, nearest neighbor, level-order rendering. Uses a queue.

**Behavioral Questions:**
6. **"Tell me about a real feature where you used recursion. Could you have done it iteratively? Why did you choose recursion?"**
   - *STAR hint*: Rendering a nested category menu or nested comments. Recursion was more natural than manually managing a stack. The data had unknown depth. Mention any base case you almost forgot, or a stack overflow you hit in testing with deeply nested data.

7. **"Have you ever hit a stack overflow in a real project? What caused it and how did you debug it?"**
   - *STAR hint*: Recursive function without a proper base case, or accidentally calling a function that called itself indirectly. Browser console showed `RangeError`. Added `console.log(depth)` to trace call depth. Fixed with a depth limit or converted to iterative.

8. **"Describe a time you had to traverse or render nested/hierarchical data (categories, menus, comments). What was your approach?"**
   - *STAR hint*: Shopify category tree, nested Airtable records, or a comment thread with replies. Used a recursive React component or recursive function. Handled unknown depth, set a max level, styled each level with indentation.

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Recursively build an HTML `<ul>/<li>` nested menu from a JS category tree `{name, children[]}` — no hardcoded depth limit
* ⬜ RW-2: Write a recursive `deepClone(obj)` function — use it to safely clone Shopify product config objects before modifying, avoid reference mutation bugs

**React / Next.js:**
* ⬜ RW-3: Build a recursive React `<TreeNode>` component that renders a Shopify collections hierarchy with collapsible expand/collapse per node
* ⬜ RW-4: Write a recursive `getAllRoutes(pagesDir)` function for a Next.js sitemap generator — traverse nested page folder structure, return all valid URL paths

**Airtable API:**
* ⬜ RW-5: Airtable linked records can be deeply nested (Task → Project → Client → Account) — write a recursive `resolveLinks(recordId, depth)` function (max 3 levels)
* ⬜ RW-6: Recursively flatten a grouped Airtable view (records grouped by field, sub-grouped by another field) into a flat `[record]` array

**Shopify:**
* ⬜ RW-7: Shopify collections can have sub-collections — recursively traverse a mocked collection tree to collect all leaf-level product handles into a flat list
* ⬜ RW-8: Build a recursive discount calculator: `applyDiscount(price, rules[])` — each rule may trigger sub-rules (buy X get Y), apply them recursively

**VPS / Server:**
* ⬜ RW-9: Write a recursive directory scanner using a nested JS object (simulating VPS file system) — output all file paths like `ls -R`, sorted by folder depth
* ⬜ RW-10: Recursively calculate total size from `{name, size, children[]}` file tree — mirrors `du -sh` on a Linux VPS, display human-readable KB/MB

### **Day 10: Hashing and Frequency Maps**

* ✅ Use `Map`, `Set`, objects for hashing

* ✅ Task 1: Frequency of characters

* ✅ Task 2: Detect duplicates

* ✅ Task 3: Intersection of arrays

* ✅ Task 4: Union of arrays

* ✅ Task 5: Two Sum problem

* ✅ Task 6: Longest subarray with 0 sum

* ✅ Task 7: Count pairs with given sum

* ✅ Task 8: Group anagrams

* ✅ Task 9: First non-repeating character

* ✅ Task 10: Check isomorphic strings

#### **Interview Questions & Behavioral**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Conceptual Questions:**
1. **What is a hash map? What are the time complexities for get, set, and delete?**
   - Key-value store with O(1) average for get/set/delete. JavaScript's `Map` is an ordered hash map. Plain objects `{}` are also hash maps but with prototype chain quirks. Collisions are handled internally — you don't manage them manually in JS.

2. **When would you use a `Map` vs a plain object `{}`? Is there a performance difference?**
   - `Map`: keys can be any type (not just strings), maintains insertion order reliably, has `.size`, better for frequent add/delete. Object `{}`: simpler syntax, JSON-serializable, slightly faster for string keys. Use `Map` for dynamic lookup tables, use `{}` for fixed-shape config/data.

3. **When is a `Set` more appropriate than an array? What's the performance difference?**
   - `Set`: O(1) `.has()`, automatically deduplicates, better for membership checks. Array: O(n) `.includes()`, maintains order with duplicates, supports indexing. Use `Set` when uniqueness matters and you don't need index access. Convert back to array with `[...set]`.

4. **What is the time complexity of common `Map` operations? What can degrade it to O(n)?**
   - Average: O(1) for get/set/delete/has. Worst case: O(n) if many keys hash to the same bucket (hash collision). In practice, JS engines handle this well. Don't use non-primitive objects as keys unless you need identity-based lookup.

5. **How would you implement a simple in-memory cache with a TTL (time-to-live) using a Map?**
   - Store: `cache.set(key, {data, expiresAt: Date.now() + ttl})`. Get: check if `Date.now() < entry.expiresAt`, return data or delete + refetch. Optional: periodic cleanup or cleanup on access. This pattern is common in real apps.

**Behavioral Questions:**
6. **"Tell me about a time you used a hash map to significantly speed up a slow operation in your code."**
   - *STAR hint*: Replaced an O(n) `.find()` in a loop (O(n²) total) with a `Map` for O(1) lookup. Built the map once before the loop. Classic interview answer. Mention the specific data — e.g., building a `productMap` keyed by SKU for cart item lookup.

7. **"Have you ever needed to deduplicate data from an API? How did you handle it?"**
   - *STAR hint*: Airtable sometimes returns duplicate records across paginated calls, or Shopify webhooks fire twice. Used a `Set` of IDs to track seen records. Filter before processing: `if (seen.has(id)) continue; seen.add(id);`.

8. **"Describe a time you implemented a client-side caching layer to reduce redundant API calls. What was the structure?"**
   - *STAR hint*: Caching Airtable table data in a `Map` with `{data, fetchedAt}`. Check cache before every API call. If `Date.now() - fetchedAt < 60000`, serve from cache. Reduced API calls from 50/session to 3/session. Mention the Airtable rate limit as the motivation.

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Use a `Map` to cache GoDaddy static site API responses by URL — serve cached response if called again within 60 seconds, otherwise refetch
* ⬜ RW-2: Use a `Set` to collect unique product category tags across all displayed products — render as a filter tag cloud with click-to-filter

**React / Next.js:**
* ⬜ RW-3: Implement a React data-fetch cache using `Map` — key = Airtable table name, value = `{data, fetchedAt}` — invalidate after 5 minutes
* ⬜ RW-4: Build a visited-pages tracker in Next.js with a `Set` — count unique page views per session, display as "X pages visited" without counting duplicates

**Airtable API:**
* ⬜ RW-5: Build a frequency dashboard from Airtable records — count how many records exist per `Status` value using a `Map`, display as a bar-chart-style summary
* ⬜ RW-6: Deduplicate Airtable customer records by email using a `Set` — log duplicate emails and count how many were found

**Shopify:**
* ⬜ RW-7: Build a Shopify product tag frequency map — given products each with `tags[]`, count tag frequency with a `Map`, sort by popularity for a tag cloud
* ⬜ RW-8: Create a product SKU lookup table using `Map` — build once from product list for O(1) lookup by SKU instead of O(n) array search on every cart add

**Laravel / Python Flask:**
* ⬜ RW-9: Cache Laravel API responses in a `Map` with TTL — if `Date.now() - cachedAt > 60000` ms, refetch; otherwise return cached data immediately
* ⬜ RW-10: Detect duplicate form submissions: use a `Set` of `email+timestamp` strings — flag and count re-submissions from the Flask API response

---

## **🗓️ Week 5: Advanced DSA – Linked List, Stack, Queue**

### **Day 11: Linked List**

* ✅ Singly Linked List implementation

* ✅ Task 1: Create a linked list

* ✅ Task 2: Insert at beginning/end

* ✅ Task 3: Delete node by value

* ✅ Task 4: Find middle of list

* ✅ Task 5: Reverse a list

* ✅ Task 6: Detect cycle

* ✅ Task 7: Merge two sorted lists

* ✅ Task 8: Remove duplicates

* ✅ Task 9: Palindrome check

* ✅ Task 10: Linked list to number

#### **Interview Questions & Behavioral**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Conceptual Questions:**
1. **What is a linked list and how does it differ from an array?**
   - Array: contiguous memory, O(1) index access, O(n) insert/delete at middle. Linked list: non-contiguous nodes with pointers, O(n) access by index, O(1) insert/delete at head. In JS, arrays are the go-to; linked lists are used when you need efficient front-insertion or as building blocks for stacks/queues.

2. **What is the time complexity of insertion at head, tail, and middle in a singly linked list?**
   - Head: O(1) — just update the head pointer. Tail: O(n) without tail pointer, O(1) with a tail pointer. Middle: O(n) to find the position, O(1) to actually insert. Compare to array: tail = O(1) amortized, middle = O(n) shift.

3. **What is a doubly linked list? When would you use one over a singly linked list?**
   - Each node has both `next` and `prev` pointers. Use when you need to traverse backwards (undo/redo, browser history, LRU cache). Cost: double the pointer storage, more complex insertion/deletion. Most real-world use cases for "linked list" in frontend apps are doubly linked.

4. **How would you detect a cycle in a linked list?**
   - Floyd's cycle detection (two-pointer / tortoise & hare): fast pointer moves 2 steps, slow moves 1. If they meet, there's a cycle. Time: O(n), Space: O(1). Alternative: use a `Set` of visited nodes — simpler but O(n) space.

5. **What is an LRU cache and how is a doubly linked list used in it?**
   - Least Recently Used cache: evicts the least recently accessed item when full. Doubly linked list + HashMap: list maintains access order (most recent at head, least at tail), hashmap provides O(1) lookup. On access: move node to head. On evict: remove tail. Standard interview question — be ready to code it.

**Behavioral Questions:**
6. **"Tell me about a time you needed a data structure that allowed efficient insertion or removal from both ends. How did you solve it?"**
   - *STAR hint*: A "Recently Viewed" products list where you add to front and remove from back (deque behavior). Or a request queue needing front removal. Explain why array `shift()` was O(n) and why a linked list (or deque) was more efficient at scale.

7. **"Have you ever built an undo/redo feature? How did you structure the history data?"**
   - *STAR hint*: Used a doubly linked list (or array with a pointer). Each node = form state snapshot. Undo = traverse to prev node, redo = traverse to next. When user makes a new change after undo = truncate forward history. Explain time/space tradeoffs.

8. **"Describe how you would design a 'recently viewed products' feature with a maximum of 10 items. What data structure fits best?"**
   - *STAR hint*: Linked list (or deque): O(1) prepend, O(1) tail trim. Add to head on view, remove from tail when size > 10, move to head if already exists (avoid duplicates). Store in `localStorage` for persistence. Explain why array `unshift()` works for small N but linked list is theoretically better.

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Implement browser-style Back/Forward navigation for a GoDaddy single-page site using a doubly linked list of page URLs — Back pops, Forward re-appends
* ⬜ RW-2: Build a "Recently Played" media queue (max 10 items) as a linked list — prepend new plays to head, auto-trim tail when length exceeds 10

**React / Next.js:**
* ⬜ RW-3: Implement undo/redo for a React rich-text editor using a doubly linked list — each node stores a full form snapshot; undo = prev, redo = next
* ⬜ RW-4: Build a Next.js in-app breadcrumb navigator using a linked list — each link pushes to the list, "Go Back" traverses to previous node

**Airtable API:**
* ⬜ RW-5: Model an Airtable "linked records" chain as a JS linked list — traverse Task → linked Project → linked Client to build a context breadcrumb display
* ⬜ RW-6: Build a batch-update queue for Airtable (5 requests/sec limit) — enqueue pending updates as linked list nodes, process sequentially with 200ms delay

**Shopify:**
* ⬜ RW-7: Model a Shopify checkout flow as a doubly linked list — steps: Cart → Address → Shipping → Payment → Confirmation — support prev/next navigation
* ⬜ RW-8: Build a "Customers also bought" product chain — each product node links to a recommended next product, traverse to build a recommendations strip

**VPS / Server:**
* ⬜ RW-9: Simulate a VPS process list as a linked list — each node = `{pid, name, memory}` — implement `killProcess(pid)` to remove by PID in O(n)
* ⬜ RW-10: Model a server request log as a linked list (prepend = O(1)) — traverse to find all requests from a specific IP, count them, return most recent 5

### **Day 12: Stack and Queue**

* ✅ Stack using array and linked list

* ✅ Task 1: Implement push/pop

* ✅ Task 2: Infix to postfix

* ✅ Task 3: Valid parenthesis

* ✅ Task 4: Evaluate postfix expression

* ✅ Task 5: Queue using two stacks

* ✅ Task 6: Implement circular queue

* ✅ Task 7: Sliding window maximum

* ✅ Task 8: LRU cache

* ✅ Task 9: Stack using two queues

* ✅ Task 10: Next greater element

#### **Interview Questions & Behavioral**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Conceptual Questions:**
1. **What is a stack? What are its core operations and time complexities?**
   - LIFO: Last In, First Out. Operations: `push` O(1), `pop` O(1), `peek/top` O(1), `isEmpty` O(1). Used for: undo/redo, function call stack, expression parsing, browser history (back button), DFS traversal.

2. **What is a queue? How does it differ from a stack?**
   - FIFO: First In, First Out. Operations: `enqueue` O(1), `dequeue` O(1) (with head pointer), `front` O(1). Used for: task processing, print queues, BFS traversal, API request queues, notification systems. Stack = plates pile; Queue = checkout line.

3. **How would you implement a queue using two stacks? What's the time complexity?**
   - Two stacks: `inbox` and `outbox`. Enqueue: push to `inbox`. Dequeue: if `outbox` empty, pour all from `inbox` to `outbox`, then pop from `outbox`. Amortized O(1) dequeue. Common interview question — explain the amortized analysis.

4. **What is a monotonic stack? Give a real-world example of when you'd use one.**
   - A stack that maintains elements in strictly increasing or decreasing order. Use case: "Next Greater Element" problem — find the next larger value for each element. Also used for: largest rectangle in histogram, stock span, temperature problems. Time: O(n).

5. **What is a priority queue? When would you use one in a real app?**
   - A queue where each element has a priority; highest priority dequeues first. Use cases: task scheduler (urgent tasks first), Dijkstra's algorithm, notification priority (errors before info). Usually implemented with a binary heap. JS has no built-in — use a library or implement a min-heap.

**Behavioral Questions:**
6. **"Tell me about a feature you built that naturally fit a queue or stack data structure. What was it and why did that structure fit?"**
   - *STAR hint*: A multi-step form wizard (stack — push completed steps, pop on back), a notification display queue (FIFO — show oldest first, auto-remove after 5s), or an API rate-limiter queue (FIFO — process requests at a controlled rate). Describe the specific business need.

7. **"Have you ever had to manage rate limiting when calling external APIs? How did you prevent hitting the limits?"**
   - *STAR hint*: Airtable 5 req/sec or Shopify API limits. Built a queue of pending API calls, processed from front of queue with `setTimeout` delays between each. Or used a debounce/throttle on user-triggered calls. Describe the symptom (429 errors), the solution, and the result.

8. **"Describe a multi-step checkout or wizard you've built. How did you manage navigation between steps and prevent skipping?"**
   - *STAR hint*: Checkout flow (Cart → Address → Shipping → Payment → Confirmation). Used an array of step components with an `activeStep` index — could only advance if current step was valid. Optionally used a stack so "Back" was reliable. Describe validation between steps.

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Build a browser history stack for a GoDaddy single-page app — push URL on navigate, pop on back button, clear forward history when new page loads
* ⬜ RW-2: Implement undo/redo for a plain JS canvas drawing tool — use two stacks (undo stack, redo stack), each node is an ImageData snapshot

**React / Next.js:**
* ⬜ RW-3: Build a multi-step checkout wizard in React using a stack — push completed steps, pop on "Back" button, validate current step before pushing "Next"
* ⬜ RW-4: Create a Next.js toast notification queue — new notifications enqueue at the back, display one at a time, auto-dequeue after 4 seconds

**Airtable API:**
* ⬜ RW-5: Build an Airtable API request queue — Airtable rate limit is 5 req/sec — enqueue all `PATCH` update calls, process from front of queue with 200ms delay
* ⬜ RW-6: Implement a task processing pipeline as a queue: when new Airtable records are created, enqueue them — dequeue one at a time to send email + update status

**Shopify:**
* ⬜ RW-7: Build a Shopify order processing queue — new webhook orders enqueue, a processor dequeues and calls fulfillment API one-by-one to prevent race conditions
* ⬜ RW-8: Implement "Recently Viewed Products" as a stack in Shopify storefront JS — push product ID on view, pop duplicates, display top 5 as "Recently Viewed"

**Laravel / Python Flask:**
* ⬜ RW-9: Simulate a Flask background job queue — enqueue tasks (send email, resize image), process FIFO, display queue length and current job in a status panel
* ⬜ RW-10: Build a formula parentheses validator for a Laravel input field — use a stack to check balanced `()`, `[]`, `{}` in user-entered formula strings

---

## **🗓️ Week 6: Trees, Graphs, Dynamic Programming**

### **Day 13: Trees**

* ✅ Binary Tree Basics

* ✅ Task 1: Inorder traversal

* ✅ Task 2: Preorder traversal

* ✅ Task 3: Postorder traversal

* ✅ Task 4: Level-order traversal

* ✅ Task 5: Height of tree

* ✅ Task 6: Count nodes

* ✅ Task 7: Check symmetric

* ✅ Task 8: Mirror a tree

* ✅ Task 9: Lowest common ancestor

* ✅ Task 10: Convert tree to sum tree

#### **Interview Questions & Behavioral**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Conceptual Questions:**
1. **What is a binary tree vs a binary search tree (BST)? What's the key invariant of a BST?**
   - Binary tree: each node has at most 2 children, no ordering rule. BST: left child < parent < right child (all descendants, not just immediate). BST enables O(log n) search if balanced. Real-world: BSTs power database indexes and auto-complete sorted data.

2. **What is the difference between BFS and DFS tree traversal? When would you use each?**
   - DFS: Go deep before wide. Traversal types: pre-order (visit → left → right), in-order (left → visit → right = sorted for BST), post-order (left → right → visit). Uses a stack (recursive or explicit). BFS: Level by level, uses a queue. Use BFS for shortest path, level-order rendering, "find all nodes at depth N."

3. **What is a balanced tree? Why does balance matter for performance?**
   - A tree where the height of left and right subtrees differs by at most 1 (AVL) or the tree restructures to stay O(log n) (Red-Black). An unbalanced BST can degrade to O(n) for all operations (essentially a linked list). In practice, database B-trees and self-balancing structures keep operations fast.

4. **How would you represent a tree structure in JavaScript for a UI (e.g., a category menu)?**
   - As nested objects: `{id, name, children: [{id, name, children: [...]}]}`. This maps directly to recursive React component rendering. For flat data from an API (like Airtable), build the tree by creating a map of `id → node`, then assign children by iterating and linking `parentId`.

5. **What is the height/depth of a tree and why does it affect performance?**
   - Height = longest path from root to a leaf. Affects time complexity of all operations: a balanced tree of n nodes has height O(log n). Unbalanced can have height O(n). When interviewer asks "what's the time complexity?", always consider the worst case (skewed tree = O(n), balanced = O(log n)).

**Behavioral Questions:**
6. **"Tell me about a UI feature that involved rendering hierarchical/nested data. How did you structure both the data and the component?"**
   - *STAR hint*: Nested navigation menu, category tree for e-commerce, organizational chart, or nested comment threads. Describe data shape (parent-child JSON), recursive React component (`TreeNode` calling itself), base case (no children = render leaf), styling each depth level.

7. **"Describe how you built a multi-level navigation menu in a real project. What were the technical challenges?"**
   - *STAR hint*: Mobile responsiveness, unknown depth, active state tracking across levels, accessibility (keyboard navigation). Describe data structure choice (nested JSON vs flat with parentId), recursion for render, and how you handled the "currently active" path highlight.

8. **"Have you worked with hierarchical data from a CMS, database, or API? How did you transform and display it?"**
   - *STAR hint*: Shopify navigation, WordPress categories, Airtable linked records, or a headless CMS. Data came flat (with parentId) or nested. Built a `buildTree(flatArray)` function to convert flat to nested, then rendered with a recursive component.

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Build a nested dropdown nav menu from a JS category tree `{name, children[]}` — recursively render `<ul>/<li>`, expand/collapse on click
* ⬜ RW-2: Create a file explorer for a GoDaddy hosting panel mock — display folders/files as a tree, support expand/collapse of directories

**React / Next.js:**
* ⬜ RW-3: Build a Shopify-style category tree in React — render root → sub-categories → products as a collapsible `<TreeView>` component, highlight selected node
* ⬜ RW-4: Create a Next.js dynamic breadcrumb component — parse the URL path `/shop/mens/t-shirts` as a tree traversal, render each node as a clickable link

**Airtable API:**
* ⬜ RW-5: Model Airtable linked records (Client → Projects → Tasks) as a tree in JS — render as a React org-chart style tree, show count per level
* ⬜ RW-6: Build a category assignment UI — display Airtable categories as a tree with checkboxes, auto-check parent when all children are selected

**Shopify:**
* ⬜ RW-7: Parse Shopify's `menu` navigation object (tree-structured) — render a responsive multi-level nav bar with mobile hamburger toggle
* ⬜ RW-8: Build a product filter tree — top level = category, second level = subcategory, leaf = product count — clicking a node filters the product grid

**VPS / Server:**
* ⬜ RW-9: Model your VPS directory structure as a tree object — implement DFS traversal to list all files sorted by last modified date, display indented
* ⬜ RW-10: Build a server permission tree — root = admin, branches = departments, leaves = users — `hasPermission(userId, action)` traverses tree to check access

### **Day 14: Graphs \+ Dynamic Programming**

* ✅ DFS, BFS, Adjacency List

* ✅ Task 1: Represent graph with adjacency list

* ✅ Task 2: Implement DFS

* ✅ Task 3: Implement BFS

* ✅ Task 4: Detect cycle

* ✅ Task 5: Topological sort

* ✅ Task 6: Shortest path in unweighted graph

* ✅ Task 7: Dijkstra's algorithm

* ✅ Task 8: DP \- Fibonacci with memoization

* ✅ Task 9: DP \- Coin change

* ✅ Task 10: DP \- Longest common subsequence

#### **Interview Questions & Behavioral**

> 💼 3 years experience — Use **STAR format**: Situation → Task → Action → Result

**Conceptual Questions:**
1. **What is a graph? How does it differ from a tree?**
   - Graph: nodes (vertices) connected by edges. Can have cycles, multiple paths between nodes, disconnected components. Tree is a special graph: connected, acyclic, exactly one path between any two nodes. Real-world graphs: social networks, road maps, dependencies, recommendation engines.

2. **What is the difference between DFS and BFS? What data structure does each use internally?**
   - DFS: Stack (recursive call stack or explicit). Goes deep before wide. Good for: path existence, topological sort, connected components. BFS: Queue. Goes wide before deep. Good for: shortest path (unweighted), level-by-level traversal, nearest nodes. Both O(V + E).

3. **What is a DAG (Directed Acyclic Graph)? Give a real-world example.**
   - Directed graph with no cycles. Examples: build/task dependency systems (task A must run before B), course prerequisites, spreadsheet cell dependencies. Topological sort gives a valid execution order. If a cycle exists, topological sort is impossible (deadlock).

4. **What is dynamic programming? How is it different from plain recursion?**
   - DP = recursion + memoization (top-down) or building up from base cases (bottom-up). Solves overlapping subproblems by storing results. Without DP, Fibonacci is O(2ⁿ); with DP it's O(n). Key insight: if a problem has overlapping subproblems and optimal substructure, DP applies.

5. **What is the difference between top-down (memoization) and bottom-up (tabulation) DP?**
   - Top-down: recursive + cache results as you go. More intuitive, starts from the final problem. Bottom-up: iterative, build from base cases upward. No recursion stack. Better space efficiency. For interviews: top-down (memoization) is often easier to derive; bottom-up is often what interviewers want to see next.

**Behavioral Questions:**
6. **"Tell me about a complex problem you solved that involved interconnected data — not just a list, but relationships between items."**
   - *STAR hint*: Related products ("customers also bought"), user permission dependencies, service startup order. Describe how you modeled the data as a graph (nodes + edges), what traversal you used, and the specific value it delivered (recommendations, correct boot order, access control).

7. **"Have you ever implemented a 'recommended items' or 'related content' feature? How did you approach the data model and algorithm?"**
   - *STAR hint*: Related products based on shared tags (graph: products = nodes, shared tag = edge), related Airtable records, or "other customers also viewed." Describe how you built the relationship model, how you traversed it (BFS for nearest neighbors), and how you limited results to top 3-5.

8. **"Describe a situation where caching/memoization dramatically improved the performance of a calculation or data operation in your app."**
   - *STAR hint*: A price calculator with nested discount rules recalculating on every render, or resolving Airtable linked records repeatedly. Added memoization with a `Map` or `useMemo` in React. Describe the before/after performance and how you measured the improvement (React Profiler, timer).

#### **Real-World Tasks (Your Tech Stack)**

> 🕐 Pick 1-2 per session. Each task = 15–30 min of focused practice.

**HTML/CSS/JS:**
* ⬜ RW-1: Model a static site navigation as a graph — nodes = pages, edges = internal links — use BFS to find the shortest click-path between any two pages
* ⬜ RW-2: Build a "related articles" feature using a graph — pages share edges if they share tags — DFS from current page to suggest 3 related pages

**React / Next.js:**
* ⬜ RW-3: Build a Next.js "related products" section using a graph — products are nodes, shared tags/categories are edges — recommend top 3 connected products
* ⬜ RW-4: Use DP (memoization) to optimize a React product pricing calculator — `getBestPrice(productId, qty, coupon)` caches results so repeated renders are instant

**Airtable API:**
* ⬜ RW-5: Model Airtable table relationships as a graph — tables = nodes, linked record fields = edges — detect circular references (e.g., Task linked to itself via Project)
* ⬜ RW-6: Use DP with memoization to resolve Airtable linked records — cache already-fetched records by ID to avoid re-fetching the same record multiple times

**Shopify:**
* ⬜ RW-7: Use DP to find the optimal set of discount codes to minimize total cart price — given `n` coupons with different rules, find the best non-conflicting combination
* ⬜ RW-8: Model Shopify product upsell/cross-sell relationships as a graph — given a product in cart, use BFS to find the best complementary product (2 hops away)

**VPS / Server:**
* ⬜ RW-9: Model VPS server dependencies as a DAG (directed acyclic graph) — services = nodes, dependencies = edges — use topological sort to find startup order
* ⬜ RW-10: Use DP to calculate the optimal deployment plan for a GoDaddy VPS — given N files with sizes and a bandwidth limit, maximize files deployed per deploy (0/1 knapsack)

---

## **🚀 React.js (v18 & v19) - DSA & Interview Prep**

### **React Fundamentals & Modern Features**

#### **Core Concepts**
* ✅ Components (Functional vs Class)
* ✅ JSX and rendering
* ✅ Props and State
* ✅ Hooks (useState, useEffect, useContext, useReducer, useMemo, useCallback)
* ✅ React 18 features (Concurrent rendering, Automatic batching, Transitions)
* ✅ React 19 features (Actions, use API, useFormStatus, useOptimistic)
* ✅ Virtual DOM and Reconciliation
* ✅ Component lifecycle
* ✅ Event handling
* ✅ Conditional rendering and lists

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **What is React and why use it?**
   - JavaScript library for building UIs
   - Component-based architecture
   - Virtual DOM for performance
   - Declarative programming
   - Rich ecosystem

2. **What is JSX?**
   - JavaScript XML syntax extension
   - Looks like HTML but compiles to JavaScript
   - `React.createElement()` under the hood
   - Can embed expressions with `{}`

3. **Difference between functional and class components?**
   - Functional: Simpler, use hooks, modern approach
   - Class: Older, use lifecycle methods, more verbose
   - Functional components are preferred in modern React

4. **What are Props?**
   - Short for "properties"
   - Read-only data passed from parent to child
   - Immutable in child component
   - Enable component reusability

5. **What is State?**
   - Mutable data managed within component
   - Triggers re-render when updated
   - Use `useState` hook in functional components
   - Should not be modified directly

**Intermediate Level:**
6. **How does Virtual DOM work?**
   - In-memory representation of real DOM
   - React compares Virtual DOM snapshots (diffing)
   - Updates only changed parts of real DOM
   - Improves performance

7. **What is reconciliation?**
   - Process of updating DOM to match Virtual DOM
   - React's diffing algorithm
   - Uses keys to identify elements
   - Minimizes DOM manipulations

8. **Explain useState hook**
   - Returns state value and setter function
   - Functional updates for prev state dependency
   - Lazy initialization for expensive computations
   - State updates are asynchronous

9. **Explain useEffect hook**
   - Side effects in functional components
   - Runs after render (by default)
   - Dependency array controls when it runs
   - Cleanup function for unmounting

10. **What is useContext?**
    - Access context without prop drilling
    - Share data across component tree
    - Alternative to Redux for simple state
    - Use with `createContext` and `Provider`

**Advanced Level:**
11. **What are React 18 Concurrent Features?**
    - **Concurrent Rendering**: Interruptible rendering
    - **Automatic Batching**: Multiple state updates batched
    - **Transitions**: Mark updates as non-urgent with `startTransition`
    - **Suspense for SSR**: Better server-side rendering

12. **What's new in React 19?**
    - **Actions**: Async transitions with automatic handling
    - **`use` API**: Read resources in render
    - **`useFormStatus`**: Access form submission status
    - **`useOptimistic`**: Optimistic UI updates
    - **Document Metadata**: Built-in `<title>`, `<meta>` support
    - **Ref as prop**: No more `forwardRef` needed

13. **Explain useMemo and useCallback**
    - **useMemo**: Memoize computed values
    - **useCallback**: Memoize function references
    - Prevent unnecessary re-computations/re-renders
    - Use when child components are optimized with `React.memo`

14. **What is useReducer?**
    - Alternative to useState for complex state logic
    - Similar to Redux pattern
    - Takes reducer function and initial state
    - Returns state and dispatch function

15. **Explain React Fiber**
    - New reconciliation engine (React 16+)
    - Enables incremental rendering
    - Allows pausing and resuming work
    - Foundation for Concurrent Mode

**React 18/19 Specific:**
16. **What is `startTransition`?**
    - Mark state updates as non-urgent
    - Keeps UI responsive during updates
    - Use for expensive renders (filtering, searching)
    - Part of Concurrent Features

17. **How does Automatic Batching work in React 18?**
    - Groups multiple state updates into single re-render
    - Works in timeouts, promises, native events (new in 18)
    - Previously only worked in event handlers
    - Can opt-out with `flushSync`

18. **What are Server Components?**
    - Components that render on server only
    - Reduce bundle size
    - Direct database access
    - Stream to client
    - Experimental in React 18, stable in 19

19. **Explain the `use` API in React 19**
    - Read promises and context in render
    - Unlike hooks, can be used conditionally
    - Simplifies data fetching
    - Works with Suspense

20. **What is `useOptimistic` in React 19?**
    - Show optimistic state while waiting for response
    - Auto-reverts on error
    - Better UX for mutations
    - Use with Server Actions

21. **What is prop drilling and how to avoid it?**
    - Passing props through multiple levels
    - Makes code hard to maintain
    - Solutions: Context API, component composition, state management
    - Redux/Zustand for complex state

22. **Explain React.memo and when to use it**
    - HOC for performance optimization
    - Memoizes component output
    - Prevents re-render if props unchanged
    - Compare function for custom equality

23. **What is lazy loading in React?**
    - Load components on demand
    - `React.lazy()` for code splitting
    - Use with Suspense boundary
    - Reduces initial bundle size

24. **Explain error boundaries**
    - Catch JavaScript errors in component tree
    - Display fallback UI
    - Only work in class components (for now)
    - Cannot catch errors in event handlers

25. **What are portals in React?**
    - Render children outside parent DOM hierarchy
    - `ReactDOM.createPortal()`
    - Use for modals, tooltips, dropdowns
    - Maintains React event bubbling

26. **What is the key prop and why is it important?**
    - Unique identifier for list elements
    - Helps React identify changes
    - Should be stable, unique, predictable
    - Never use index for dynamic lists

27. **Explain controlled vs uncontrolled components**
    - **Controlled**: React state controls input value
    - **Uncontrolled**: DOM controls input value (refs)
    - Controlled preferred for forms
    - Uncontrolled for simple cases

28. **What is React StrictMode?**
    - Development mode tool
    - Highlights potential problems
    - Double-invokes lifecycle methods
    - Detects unsafe side effects

29. **How does React handle events?**
    - Synthetic events (cross-browser wrapper)
    - Event delegation to root
    - Event pooling (removed in React 17)
    - camelCase naming convention

30. **What is the difference between createElement and cloneElement?**
    - `createElement`: Create new React element
    - `cloneElement`: Clone existing element with new props
    - Used for element manipulation
    - Common in HOCs and render props

**Performance & Optimization:**
31. **How to optimize React performance?**
    - Use React.memo for expensive components
    - useMemo/useCallback for memoization
    - Code splitting with React.lazy
    - Virtualization for long lists
    - Avoid inline functions in JSX
    - Proper key usage

32. **What is the Profiler API?**
    - Measure rendering performance
    - Identifies slow components
    - `<Profiler>` component with onRender callback
    - Available in DevTools

33. **Explain batching in React**
    - Group multiple state updates
    - Single re-render
    - Automatic in React 18 (all scenarios)
    - Use `flushSync` to opt-out

34. **What is code splitting?**
    - Split code into smaller bundles
    - Load on demand
    - `React.lazy()` + `import()`
    - Route-based or component-based

35. **How to prevent unnecessary re-renders?**
    - React.memo
    - useMemo for expensive calculations
    - useCallback for function references
    - Proper state structure
    - Move state down

**Hooks Deep Dive:**
36. **What are the rules of hooks?**
    - Only call at top level (no loops/conditions)
    - Only call in React functions
    - ESLint plugin enforces rules
    - Ensures consistent hook order

37. **Explain useRef hook**
    - Persist value across renders
    - Doesn't trigger re-render
    - Access DOM elements
    - Store mutable values

38. **What is useLayoutEffect?**
    - Fires synchronously after DOM mutations
    - Before browser paint
    - Use for DOM measurements
    - Blocks visual updates (use sparingly)

39. **Explain useImperativeHandle**
    - Customize ref value exposed to parent
    - Use with forwardRef
    - Control what parent can access
    - Rarely needed

40. **What is useDebugValue?**
    - Display custom label in DevTools
    - Only for custom hooks
    - Format function for expensive computations
    - Helps debugging

**Advanced Concepts:**
41. **What are Higher-Order Components (HOC)?**
    - Function that takes component, returns new component
    - Reuse component logic
    - Convention: `withSomething` naming
    - Modern alternative: hooks

42. **Explain render props pattern**
    - Share code using prop whose value is function
    - Function returns React element
    - Inversion of control
    - Less common with hooks

43. **What is React Suspense?**
    - Declarative loading states
    - Works with lazy loading
    - Data fetching (experimental)
    - Streaming SSR in React 18

44. **Explain React Context API best practices**
    - Split contexts by concern
    - Memoize provider value
    - Use multiple contexts
    - Consider performance implications

45. **What is React DevTools?**
    - Browser extension for debugging
    - Component tree inspection
    - Props/state viewing
    - Performance profiling

**React 18/19 Advanced:**
46. **What is Suspense for Data Fetching?**
    - Declarative data loading
    - Works with `use` API (React 19)
    - Streaming architecture
    - Better UX with loading states

47. **Explain Selective Hydration**
    - React 18 SSR improvement
    - Hydrate parts of page independently
    - Prioritize interactive components
    - Better Time to Interactive

48. **What are Server Actions in React 19?**
    - Server-side functions callable from client
    - Integrated with forms
    - Automatic serialization
    - Works with useOptimistic

49. **Explain React Compiler (React 19)**
    - Automatic optimization
    - No need for manual memoization
    - Compiles React code
    - Still experimental

50. **What is the `use` hook in React 19?**
    - Read promises/context during render
    - Can be used conditionally (unlike other hooks)
    - Suspends component until resolved
    - Simplifies async patterns

#### **DSA-Related React Tasks**

**Component Design Patterns:**
* ✅ Task 1: Implement virtualized list (render only visible items)
* ✅ Task 2: Infinite scroll with pagination
* ✅ Task 3: Search with debouncing
* ✅ Task 4: Autocomplete component with trie data structure
* ✅ Task 5: Tree view component (recursive rendering)
* ✅ Task 6: Nested comments system (tree traversal)
* ✅ Task 7: Multi-level dropdown menu (recursion)
* ✅ Task 8: Accordion component with single/multiple open
* ✅ Task 9: Carousel/slider with infinite loop
* ✅ Task 10: Modal with focus trap (accessibility)

**State Management & Performance:**
* ✅ Task 11: Todo app with CRUD operations
* ✅ Task 12: Shopping cart with total calculation
* ✅ Task 13: Form validation with complex rules
* ✅ Task 14: Undo/Redo functionality using stack
* ✅ Task 15: Implement memoization with useMemo
* ✅ Task 16: Multi-step form with state preservation
* ✅ Task 17: Complex filter system (multiple criteria)
* ✅ Task 18: Real-time search with result highlighting
* ✅ Task 19: Form with dependent fields
* ✅ Task 20: Wizard component with validation

**Data Structures in React:**
* ✅ Task 21: Binary tree visualizer
* ✅ Task 22: Graph visualization component
* ✅ Task 23: Sorting algorithm visualizer
* ✅ Task 24: Implement LRU cache for component memoization
* ✅ Task 25: Priority queue for task management
* ✅ Task 26: Linked list visualizer
* ✅ Task 27: Hash table visualization
* ✅ Task 28: Stack operations visualizer
* ✅ Task 29: Queue simulation component
* ✅ Task 30: Heap visualizer (min/max heap)

**Advanced Patterns & Hooks:**
* ✅ Task 31: Custom hook for debounce
* ✅ Task 32: Custom hook for throttle
* ✅ Task 33: Custom hook for previous value
* ✅ Task 34: Implement useReducer for complex forms
* ✅ Task 35: Context + useReducer for state management
* ✅ Task 36: Custom hook for localStorage sync
* ✅ Task 37: Custom hook for API data fetching
* ✅ Task 38: Custom hook for window resize
* ✅ Task 39: Custom hook for intersection observer
* ✅ Task 40: Custom hook for media queries

**React 18/19 Features:**
* ✅ Task 41: Use startTransition for heavy list filtering
* ✅ Task 42: Implement Suspense for code splitting
* ✅ Task 43: Use useOptimistic for form submissions
* ✅ Task 44: Create Server Component for data fetching
* ✅ Task 45: Implement streaming SSR
* ✅ Task 46: Use useDeferredValue for search
* ✅ Task 47: Implement concurrent rendering
* ✅ Task 48: Server Actions with form handling
* ✅ Task 49: Use `use` hook for async data
* ✅ Task 50: Implement useFormStatus for loading states

**Real-World Projects:**
* ✅ Task 51: Build a kanban board (drag & drop)
* ✅ Task 52: Chat application (message history)
* ✅ Task 53: Data table with sorting, filtering, pagination
* ✅ Task 54: File explorer (tree structure)
* ✅ Task 55: Code editor with syntax highlighting
* ✅ Task 56: Calendar component with event management
* ✅ Task 57: Image gallery with lazy loading
* ✅ Task 58: Music player with playlist (queue)
* ✅ Task 59: Notification system with queue
* ✅ Task 60: Dashboard with real-time updates

**Advanced Algorithms:**
* ✅ Task 61: Pathfinding visualizer (Dijkstra, A*)
* ✅ Task 62: Recursive maze generator
* ✅ Task 63: Sudoku solver visualizer
* ✅ Task 64: N-Queens problem visualizer
* ✅ Task 65: Backtracking algorithm visualizer
* ✅ Task 66: Dynamic programming visualizer
* ✅ Task 67: Breadth-first search visualizer
* ✅ Task 68: Depth-first search visualizer
* ✅ Task 69: Binary search visualizer
* ✅ Task 70: Merge sort step-by-step visualizer

**Performance & Optimization:**
* ✅ Task 71: Implement window virtualization for huge datasets
* ✅ Task 72: Optimize re-renders with React.memo
* ✅ Task 73: Code splitting by route
* ✅ Task 74: Image lazy loading with intersection observer
* ✅ Task 75: Memoize expensive calculations
* ✅ Task 76: Debounced API calls
* ✅ Task 77: Throttled scroll handler
* ✅ Task 78: Progressive image loading
* ✅ Task 79: Request deduplication
* ✅ Task 80: Component lazy loading with retry logic

---

## **🟢 Node.js - DSA & Interview Prep**

### **Node.js Fundamentals**

#### **Core Concepts**
* ✅ Event Loop and Non-blocking I/O
* ✅ Modules (CommonJS vs ES Modules)
* ✅ NPM and package management
* ✅ File System operations
* ✅ Streams and Buffers
* ✅ Events and Event Emitter
* ✅ HTTP/HTTPS modules
* ✅ Express.js framework
* ✅ Middleware pattern
* ✅ Error handling

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **What is Node.js?**
   - JavaScript runtime built on V8 engine
   - Single-threaded, event-driven, non-blocking I/O
   - Used for server-side applications
   - NPM - largest package ecosystem

2. **How does the Event Loop work?**
   - Single-threaded event loop
   - Call stack → Task queues → Event loop
   - Microtasks (Promises) vs Macrotasks (setTimeout)
   - Non-blocking for I/O operations

3. **What are Streams in Node.js?**
   - Handle reading/writing data in chunks
   - Types: Readable, Writable, Duplex, Transform
   - Memory efficient for large data
   - Use with pipes for data flow

4. **Explain Buffers in Node.js**
   - Handle binary data
   - Fixed-size chunks of memory
   - Used with streams, files, network
   - Methods: `Buffer.from()`, `Buffer.alloc()`

5. **What is the difference between `require` and `import`?**
   - `require`: CommonJS, synchronous
   - `import`: ES Modules, asynchronous
   - ES Modules are the standard
   - Node.js supports both

**Intermediate Level:**
6. **Explain Event Emitter**
   - Core module for event-driven programming
   - `on()` to listen, `emit()` to trigger
   - Asynchronous event handling
   - Foundation for many Node.js modules

7. **What is middleware in Express?**
   - Functions with access to req, res, next
   - Execute in order they're defined
   - Can modify req/res objects
   - Types: Application, Router, Error-handling

8. **How to handle errors in Node.js?**
   - Try-catch for synchronous code
   - Error-first callbacks: `(err, data) => {}`
   - Promise `.catch()` and `try-catch` with async/await
   - Centralized error middleware in Express

9. **What is clustering in Node.js?**
   - Spawn multiple processes (workers)
   - Utilize multi-core systems
   - Load balancing across workers
   - Master process manages workers

10. **Explain Promise vs Callback**
    - Callback: Function passed as argument
    - Promise: Object representing async operation
    - Promises avoid callback hell
    - Async/await built on Promises

**Advanced Level:**
11. **How does Node.js handle concurrency?**
    - Single-threaded event loop
    - Non-blocking I/O for concurrency
    - Worker threads for CPU-intensive tasks
    - Cluster for scaling

12. **What is the difference between process.nextTick() and setImmediate()?**
    - `nextTick()`: Executes before event loop continues
    - `setImmediate()`: Executes in next event loop iteration
    - `nextTick()` has higher priority
    - Use `setImmediate()` for deferring work

13. **Explain memory leaks in Node.js**
    - Unclosed connections/streams
    - Circular references
    - Global variables
    - Event listeners not removed
    - Use heap snapshots to debug

14. **What is the V8 engine?**
    - Chrome's JavaScript engine
    - Compiles JS to machine code (JIT)
    - Garbage collection
    - Optimizations (Hidden classes, Inline caching)

15. **How to optimize Node.js performance?**
    - Use clustering
    - Enable gzip compression
    - Caching (Redis)
    - Connection pooling
    - Async operations
    - Profiling and monitoring

**Express.js & Middleware:**
16. **What is Express.js?**
    - Minimal web framework for Node.js
    - Routing, middleware, template engines
    - HTTP utility methods
    - Most popular Node.js framework

17. **How does routing work in Express?**
    - Define routes with HTTP methods
    - Route parameters (`:id`)
    - Query strings
    - Route handlers and middleware

18. **What is CORS and how to handle it?**
    - Cross-Origin Resource Sharing
    - Security feature in browsers
    - Use `cors` middleware in Express
    - Configure allowed origins

19. **Explain body parsing in Express**
    - Parse incoming request bodies
    - `express.json()` for JSON
    - `express.urlencoded()` for form data
    - Size limits and validation

20. **What is helmet.js?**
    - Security middleware for Express
    - Sets HTTP headers
    - Prevents common vulnerabilities
    - XSS, clickjacking, etc.

**Async Patterns:**
21. **What are async/await best practices?**
    - Always use try-catch
    - Avoid mixing with callbacks
    - Parallel execution with `Promise.all()`
    - Handle rejections

22. **Explain Promise.all() vs Promise.race() vs Promise.allSettled()**
    - `all()`: Waits for all, fails if one fails
    - `race()`: First settled promise wins
    - `allSettled()`: Waits for all, never rejects
    - `any()`: First fulfilled promise wins

23. **What is callback hell and how to avoid it?**
    - Deeply nested callbacks
    - Hard to read and maintain
    - Solutions: Promises, async/await
    - Modular functions

24. **How to handle async errors?**
    - Try-catch with async/await
    - `.catch()` with Promises
    - Error-first callbacks
    - Centralized error handler

25. **What is Promise chaining?**
    - Chain `.then()` calls
    - Each returns new Promise
    - Pass data down chain
    - Single `.catch()` at end

**Streams & Buffers:**
26. **When to use streams vs reading entire file?**
    - Streams for large files
    - Memory efficient
    - Real-time processing
    - File uploads/downloads

27. **What are Transform streams?**
    - Duplex stream (readable + writable)
    - Modify data while piping
    - Examples: compression, encryption
    - Implement `_transform()` method

28. **How to handle backpressure in streams?**
    - When write faster than read
    - `pipe()` handles automatically
    - Manual: check `write()` return value
    - Use `drain` event

29. **What is the difference between readFile() and createReadStream()?**
    - `readFile()`: Loads entire file to memory
    - `createReadStream()`: Reads in chunks
    - Stream better for large files
    - Stream allows processing while reading

30. **How to convert Buffer to String?**
    - `buffer.toString('utf8')`
    - Encoding options: utf8, base64, hex
    - `Buffer.from(string, encoding)`
    - Handle character encodings

**Database & ORM:**
31. **What is connection pooling?**
    - Reuse database connections
    - Avoid overhead of creating connections
    - Set max/min pool size
    - Handle connection errors

32. **How to prevent SQL injection in Node.js?**
    - Use parameterized queries
    - ORM libraries (Sequelize, Prisma)
    - Input validation
    - Escape user input

33. **What is Mongoose in Node.js?**
    - MongoDB ODM (Object Data Modeling)
    - Schema definition
    - Validation and middleware
    - Query building

34. **Explain transactions in databases**
    - Group operations as single unit
    - ACID properties
    - Rollback on failure
    - Use with `BEGIN`, `COMMIT`, `ROLLBACK`

35. **What are database indexes?**
    - Speed up queries
    - Trade-off: slower writes
    - B-tree, Hash indexes
    - Index frequently queried fields

**Security:**
36. **How to implement authentication in Node.js?**
    - JWT (JSON Web Tokens)
    - Session-based auth
    - OAuth 2.0
    - Passport.js middleware

37. **What is JWT and how does it work?**
    - JSON Web Token
    - Stateless authentication
    - Header.Payload.Signature
    - Store in httpOnly cookies

38. **How to store passwords securely?**
    - Never store plain text
    - Use bcrypt for hashing
    - Salt rounds (10-12)
    - Verify with `bcrypt.compare()`

39. **What is CSRF and how to prevent it?**
    - Cross-Site Request Forgery
    - Attacker tricks user into action
    - Use CSRF tokens
    - SameSite cookie attribute

40. **How to implement rate limiting?**
    - Prevent abuse/DoS
    - Sliding window algorithm
    - Libraries: express-rate-limit
    - Redis for distributed systems

**Testing & Debugging:**
41. **How to test Node.js applications?**
    - Unit tests: Jest, Mocha
    - Integration tests: Supertest
    - E2E tests: Cypress, Playwright
    - Mocking with sinon

42. **What is the difference between unit and integration tests?**
    - Unit: Test individual functions
    - Integration: Test modules together
    - Unit: Fast, isolated
    - Integration: More realistic

43. **How to debug Node.js applications?**
    - `console.log()` for quick checks
    - Node Inspector (`--inspect` flag)
    - VS Code debugger
    - Chrome DevTools

44. **What is the purpose of package.json?**
    - Project metadata
    - Dependencies management
    - Scripts definition
    - Version control

45. **Explain semantic versioning (semver)**
    - MAJOR.MINOR.PATCH
    - Breaking.Feature.BugFix
    - `^` allows minor updates
    - `~` allows patch updates

**Advanced Topics:**
46. **What are Worker Threads?**
    - Run JavaScript in parallel
    - CPU-intensive tasks
    - Separate V8 instances
    - Share memory with `SharedArrayBuffer`

47. **What is child_process module?**
    - Spawn child processes
    - `exec`, `spawn`, `fork`
    - Run system commands
    - Inter-process communication

48. **Explain PM2 and its benefits**
    - Process manager for Node.js
    - Auto-restart on crash
    - Load balancing
    - Log management
    - Zero-downtime deployment

49. **What is GraphQL and how to implement in Node.js?**
    - Query language for APIs
    - Single endpoint
    - Client specifies data needs
    - Apollo Server, Express GraphQL

50. **How to handle file uploads in Node.js?**
    - Use multer middleware
    - Validate file type and size
    - Store in filesystem or cloud
    - Streams for large files

#### **DSA-Related Node.js Tasks**

**File System & Data Processing:**
* ✅ Task 1: Read large file using streams
* ✅ Task 2: Implement file-based queue
* ✅ Task 3: Process CSV file (millions of rows)
* ✅ Task 4: Build LRU cache for API responses
* ✅ Task 5: Implement rate limiting using sliding window
* ✅ Task 6: File watcher with event emitter
* ✅ Task 7: Batch processing with streams
* ✅ Task 8: Parse and transform JSON streaming data
* ✅ Task 9: Implement file compression/decompression
* ✅ Task 10: Build log rotation system

**API & Server:**
* ✅ Task 11: Build RESTful API with CRUD operations
* ✅ Task 12: Implement pagination for large datasets
* ✅ Task 13: Create middleware for request throttling
* ✅ Task 14: Build URL shortener (hashing)
* ✅ Task 15: Implement search API with trie
* ✅ Task 16: Create API versioning system
* ✅ Task 17: Build OAuth 2.0 authentication server
* ✅ Task 18: Implement JWT refresh token mechanism
* ✅ Task 19: Create GraphQL API with resolvers
* ✅ Task 20: Build request/response caching middleware

**Real-Time & Events:**
* ✅ Task 21: WebSocket server for chat
* ✅ Task 22: Event-driven notification system
* ✅ Task 23: Pub/Sub pattern implementation
* ✅ Task 24: Real-time leaderboard (sorted set)
* ✅ Task 25: Task queue with priority
* ✅ Task 26: Server-Sent Events (SSE) for live updates
* ✅ Task 27: Build event bus for microservices
* ✅ Task 28: Implement message broker pattern
* ✅ Task 29: Real-time collaborative editing
* ✅ Task 30: Live activity feed system

**Data Structures:**
* ✅ Task 31: Implement bloom filter for cache
* ✅ Task 32: Build in-memory database (hash table)
* ✅ Task 33: Implement consistent hashing for load balancing
* ✅ Task 34: Create circular buffer for logging
* ✅ Task 35: Build graph for social network
* ✅ Task 36: Implement trie for autocomplete
* ✅ Task 37: Build min/max heap for job scheduling
* ✅ Task 38: Create doubly linked list for cache
* ✅ Task 39: Implement skip list for sorted data
* ✅ Task 40: Build B-tree for indexing

**Performance & Optimization:**
* ✅ Task 41: Implement connection pooling
* ✅ Task 42: Build caching layer with Redis
* ✅ Task 43: Optimize image processing with streams
* ✅ Task 44: Implement worker threads for CPU tasks
* ✅ Task 45: Build clustering for scalability
* ✅ Task 46: Create memory-efficient data pipeline
* ✅ Task 47: Implement request batching
* ✅ Task 48: Build database query optimizer
* ✅ Task 49: Create lazy loading for large datasets
* ✅ Task 50: Implement response compression

**Authentication & Security:**
* ✅ Task 51: Build password reset flow
* ✅ Task 52: Implement 2FA (Two-Factor Authentication)
* ✅ Task 53: Create RBAC (Role-Based Access Control)
* ✅ Task 54: Build session management system
* ✅ Task 55: Implement API key authentication
* ✅ Task 56: Create secure file upload with validation
* ✅ Task 57: Build CSRF protection middleware
* ✅ Task 58: Implement XSS sanitization
* ✅ Task 59: Create secure password hashing
* ✅ Task 60: Build IP whitelisting/blacklisting

**Database Operations:**
* ✅ Task 61: Implement transaction handling
* ✅ Task 62: Build database migration system
* ✅ Task 63: Create data seeding scripts
* ✅ Task 64: Implement soft delete functionality
* ✅ Task 65: Build full-text search
* ✅ Task 66: Create database backup scheduler
* ✅ Task 67: Implement read/write replicas
* ✅ Task 68: Build aggregation pipeline
* ✅ Task 69: Create database sharding logic
* ✅ Task 70: Implement optimistic locking

**Testing & Error Handling:**
* ✅ Task 71: Write unit tests with Jest
* ✅ Task 72: Create integration tests with Supertest
* ✅ Task 73: Build error logging system
* ✅ Task 74: Implement global error handler
* ✅ Task 75: Create custom error classes
* ✅ Task 76: Build API mocking for tests
* ✅ Task 77: Implement test coverage reporting
* ✅ Task 78: Create performance benchmarks
* ✅ Task 79: Build health check endpoints
* ✅ Task 80: Implement graceful shutdown

---

## **🗄️ Databases - DSA & Interview Prep**

### **SQL Databases (PostgreSQL, MySQL)**

#### **Core Concepts**
* ✅ Relational model and normalization
* ✅ SQL queries (SELECT, JOIN, GROUP BY)
* ✅ Indexes (B-Tree, Hash)
* ✅ Transactions and ACID properties
* ✅ Primary keys, Foreign keys
* ✅ Query optimization
* ✅ Database design and schema

#### **Interview Questions (Conceptual)**

**Basic Level:**
1. **What is a relational database?**
   - Data stored in tables (rows and columns)
   - Relationships via foreign keys
   - ACID properties
   - SQL for querying

2. **What are indexes and why use them?**
   - Data structure for fast lookups
   - Common: B-Tree, Hash
   - Speed up SELECT queries
   - Slow down INSERT/UPDATE/DELETE

3. **Explain different types of JOINs**
   - INNER JOIN: Matching rows only
   - LEFT JOIN: All from left, matching from right
   - RIGHT JOIN: All from right, matching from left
   - FULL OUTER JOIN: All rows from both
   - CROSS JOIN: Cartesian product

4. **What are ACID properties?**
   - Atomicity: All or nothing
   - Consistency: Valid state
   - Isolation: Concurrent transactions don't interfere
   - Durability: Committed data persists

5. **What is normalization?**
   - Organize data to reduce redundancy
   - 1NF, 2NF, 3NF, BCNF
   - Reduce data anomalies
   - Trade-off: More joins needed

**Intermediate Level:**
6. **How do B-Tree indexes work?**
   - Balanced tree structure
   - O(log n) search, insert, delete
   - Good for range queries
   - Used by default in most databases

7. **Explain query execution plan**
   - Shows how database executes query
   - Use EXPLAIN command
   - Identify slow operations
   - Optimize based on plan

8. **What are database transactions?**
   - Unit of work (multiple operations)
   - BEGIN, COMMIT, ROLLBACK
   - Isolation levels
   - Prevent race conditions

9. **Explain database sharding**
   - Horizontal partitioning across servers
   - Distribute data by key (user_id, region)
   - Scale reads and writes
   - Challenges: Cross-shard queries

10. **What is the N+1 query problem?**
    - One query + N additional queries
    - Common with ORMs
    - Solution: Eager loading, JOIN

**Advanced Level:**
11. **How does PostgreSQL implement MVCC?**
    - Multi-Version Concurrency Control
    - Each transaction sees snapshot
    - No read locks
    - Garbage collection (VACUUM)

12. **Explain different isolation levels**
    - READ UNCOMMITTED: Dirty reads
    - READ COMMITTED: No dirty reads
    - REPEATABLE READ: No non-repeatable reads
    - SERIALIZABLE: No anomalies

13. **What is a covering index?**
    - Index contains all queried columns
    - No table lookup needed (index-only scan)
    - Faster queries
    - Larger index size

14. **How to optimize slow queries?**
    - Add indexes on filtered/joined columns
    - Avoid SELECT *
    - Use LIMIT for pagination
    - Analyze with EXPLAIN
    - Denormalize if needed

15. **What is database replication?**
    - Copy data to multiple servers
    - Master-slave: Write to master, read from slaves
    - Multi-master: Write to any
    - Improves read performance and availability

### **NoSQL Databases (MongoDB, Redis)**

#### **Core Concepts**
* ✅ Document model (MongoDB)
* ✅ Key-value store (Redis)
* ✅ Schema-less design
* ✅ Horizontal scaling
* ✅ CAP theorem
* ✅ Eventual consistency

#### **Interview Questions (Conceptual)**

**MongoDB:**
1. **When to use MongoDB vs SQL?**
   - MongoDB: Flexible schema, nested data, rapid development
   - SQL: Structured data, complex relationships, ACID critical
   - MongoDB: Better for hierarchical data
   - SQL: Better for many-to-many relationships

2. **How does MongoDB store data?**
   - Documents (BSON - Binary JSON)
   - Collections (like tables)
   - No fixed schema
   - Embedded documents vs references

3. **What are indexes in MongoDB?**
   - Similar to SQL indexes
   - Types: Single field, Compound, Text, Geospatial
   - Improve query performance
   - Use explain() to analyze

**Redis:**
4. **What is Redis and its use cases?**
   - In-memory key-value store
   - Use cases: Caching, sessions, pub/sub, leaderboards
   - Data structures: Strings, Lists, Sets, Sorted Sets, Hashes
   - Extremely fast (microsecond latency)

5. **How does Redis handle persistence?**
   - RDB: Point-in-time snapshots
   - AOF: Append-only file (log every write)
   - Both can be enabled together
   - Trade-off: Performance vs durability

#### **DSA-Related Database Tasks**

**SQL & Query Optimization:**
* ✅ Task 1: Design schema for e-commerce (normalized)
* ✅ Task 2: Write complex JOIN query (orders + users + products)
* ✅ Task 3: Optimize slow query with indexes
* ✅ Task 4: Implement pagination efficiently
* ✅ Task 5: Write query for hierarchical data (comments)
* ✅ Task 6: Calculate running totals with window functions
* ✅ Task 7: Find N most frequent items (GROUP BY)
* ✅ Task 8: Implement full-text search
* ✅ Task 9: Design leaderboard table with ranking
* ✅ Task 10: Handle concurrent transactions

**MongoDB:**
* ✅ Task 11: Design document schema for blog
* ✅ Task 12: Aggregate pipeline for analytics
* ✅ Task 13: Implement text search
* ✅ Task 14: Handle one-to-many relationships
* ✅ Task 15: Optimize queries with indexes

**Redis:**
* ✅ Task 16: Implement cache with expiration
* ✅ Task 17: Build leaderboard with sorted sets
* ✅ Task 18: Implement rate limiting
* ✅ Task 19: Session management
* ✅ Task 20: Pub/Sub messaging system

**System Design:**
* ✅ Task 21: Design URL shortener database
* ✅ Task 22: Design social media feed storage
* ✅ Task 23: Implement search autocomplete
* ✅ Task 24: Design analytics event storage
* ✅ Task 25: Build distributed cache system

---

## **🚀 COMPREHENSIVE FULL-STACK PROJECTS**

### **Three Complete Projects Covering All Concepts**

---

## **📚 PROJECT 1: Online Code Compiler & Judge System (Vanilla JavaScript)**

### **Project Overview**
Build a complete online code compilation and judging platform like LeetCode/HackerRank where users can write code, compile it, run test cases, and get instant feedback. This project covers all JavaScript DSA concepts in a real-world application.

### **Core Features**
1. **Multi-language Code Editor**
   - Syntax highlighting
   - Auto-completion
   - Code formatting
   - Multiple themes (dark/light)
   - Line numbers and error indicators

2. **Code Execution Engine**
   - Run JavaScript code in sandboxed environment
   - Memory and time limit enforcement
   - Test case validation
   - Output comparison

3. **Problem Library System**
   - Browse problems by difficulty
   - Filter by tags (Array, String, DP, Graph, etc.)
   - Search with autocomplete (Trie)
   - Sort by acceptance rate, difficulty

4. **Submission History**
   - Store all submissions in IndexedDB
   - Track success rate
   - Time/space complexity analysis
   - Code diff viewer

5. **Visual Algorithm Debugger**
   - Step-by-step execution
   - Variable tracking
   - Call stack visualization
   - Recursion tree viewer

### **Step-by-Step Implementation**

#### **Phase 1: Project Setup & Data Structures (Week 1)**

**Step 1.1: Project Structure**
```
code-judge/
├── index.html
├── css/
│   ├── main.css
│   ├── editor.css
│   ├── themes.css
│   └── animations.css
├── js/
│   ├── main.js
│   ├── core/
│   │   ├── CodeExecutor.js         (Execute & sandbox code)
│   │   ├── TestRunner.js           (Run test cases)
│   │   └── MemoryManager.js        (Track memory usage)
│   ├── data-structures/
│   │   ├── Trie.js                 (Autocomplete search)
│   │   ├── PriorityQueue.js        (Test case priority)
│   │   ├── LinkedList.js           (Submission history)
│   │   ├── Stack.js                (Undo/Redo)
│   │   └── HashMap.js              (Problem caching)
│   ├── algorithms/
│   │   ├── BinarySearch.js         (Search problems)
│   │   ├── MergeSort.js            (Sort by difficulty)
│   │   └── DiffAlgorithm.js        (Code comparison)
│   ├── ui/
│   │   ├── Editor.js               (Code editor component)
│   │   ├── ProblemList.js          (Problem browser)
│   │   ├── Visualizer.js           (Algorithm visualizer)
│   │   └── Modal.js                (Modals & dialogs)
│   └── utils/
│       ├── IndexedDB.js            (Local storage)
│       ├── Debounce.js             (Search optimization)
│       └── Validator.js            (Input validation)
└── data/
    └── problems.json               (Problem dataset)
```

**Step 1.2: Implement Trie for Problem Search**
```javascript
// js/data-structures/Trie.js
class TrieNode {
    constructor() {
        this.children = new Map();
        this.isEndOfWord = false;
        this.problems = []; // Store problem IDs
        this.frequency = 0;
    }
}

class Trie {
    constructor() {
        this.root = new TrieNode();
    }

    // Insert problem title/tag
    insert(word, problemId) {
        let node = this.root;
        word = word.toLowerCase();

        for (const char of word) {
            if (!node.children.has(char)) {
                node.children.set(char, new TrieNode());
            }
            node = node.children.get(char);
        }

        node.isEndOfWord = true;
        node.problems.push(problemId);
        node.frequency++;
    }

    // Search with autocomplete
    search(prefix) {
        let node = this.root;
        prefix = prefix.toLowerCase();

        for (const char of prefix) {
            if (!node.children.has(char)) {
                return [];
            }
            node = node.children.get(char);
        }

        return this._getAllWords(node, prefix);
    }

    _getAllWords(node, prefix) {
        const results = [];

        if (node.isEndOfWord) {
            results.push({
                word: prefix,
                problems: node.problems,
                frequency: node.frequency
            });
        }

        for (const [char, childNode] of node.children) {
            results.push(...this._getAllWords(childNode, prefix + char));
        }

        return results;
    }

    // Get suggestions sorted by frequency
    getSuggestions(prefix, limit = 10) {
        const results = this.search(prefix);
        return results
            .sort((a, b) => b.frequency - a.frequency)
            .slice(0, limit);
    }
}

export default Trie;
```

**Step 1.3: Implement LinkedList for Submission History**
```javascript
// js/data-structures/LinkedList.js
class SubmissionNode {
    constructor(data) {
        this.data = data; // { problemId, code, result, timestamp }
        this.next = null;
        this.prev = null;
    }
}

class DoublyLinkedList {
    constructor(maxSize = 50) {
        this.head = null;
        this.tail = null;
        this.size = 0;
        this.maxSize = maxSize;
    }

    // Add submission (most recent at head)
    addSubmission(submission) {
        const newNode = new SubmissionNode({
            ...submission,
            timestamp: Date.now(),
            id: this._generateId()
        });

        if (!this.head) {
            this.head = this.tail = newNode;
        } else {
            newNode.next = this.head;
            this.head.prev = newNode;
            this.head = newNode;
        }

        this.size++;

        // Remove oldest if exceeds limit
        if (this.size > this.maxSize) {
            this._removeTail();
        }

        return newNode.data;
    }

    // Get recent submissions
    getRecent(count = 10) {
        const results = [];
        let current = this.head;
        let i = 0;

        while (current && i < count) {
            results.push(current.data);
            current = current.next;
            i++;
        }

        return results;
    }

    // Get submissions for specific problem
    getByProblem(problemId) {
        const results = [];
        let current = this.head;

        while (current) {
            if (current.data.problemId === problemId) {
                results.push(current.data);
            }
            current = current.next;
        }

        return results;
    }

    // Remove submission by id
    removeById(id) {
        let current = this.head;

        while (current) {
            if (current.data.id === id) {
                if (current.prev) current.prev.next = current.next;
                if (current.next) current.next.prev = current.prev;
                if (current === this.head) this.head = current.next;
                if (current === this.tail) this.tail = current.prev;
                this.size--;
                return true;
            }
            current = current.next;
        }

        return false;
    }

    _removeTail() {
        if (!this.tail) return;

        if (this.tail.prev) {
            this.tail = this.tail.prev;
            this.tail.next = null;
        } else {
            this.head = this.tail = null;
        }

        this.size--;
    }

    _generateId() {
        return `sub_${Date.now()}_${Math.random().toString(36).substr(2, 9)}`;
    }

    // Get statistics
    getStats() {
        let accepted = 0;
        let total = 0;
        const problemsAttempted = new Set();

        let current = this.head;
        while (current) {
            total++;
            if (current.data.result === 'Accepted') accepted++;
            problemsAttempted.add(current.data.problemId);
            current = current.next;
        }

        return {
            total,
            accepted,
            acceptanceRate: total ? (accepted / total * 100).toFixed(2) : 0,
            problemsAttempted: problemsAttempted.size
        };
    }

    toArray() {
        const results = [];
        let current = this.head;

        while (current) {
            results.push(current.data);
            current = current.next;
        }

        return results;
    }
}

export default DoublyLinkedList;
```

**Step 1.4: Implement Stack for Undo/Redo**
```javascript
// js/data-structures/Stack.js
class EditorStack {
    constructor(maxSize = 100) {
        this.undoStack = [];
        this.redoStack = [];
        this.maxSize = maxSize;
    }

    // Push code state for undo
    pushState(code, cursorPosition) {
        const state = {
            code,
            cursorPosition,
            timestamp: Date.now()
        };

        this.undoStack.push(state);

        // Clear redo stack on new change
        this.redoStack = [];

        // Limit stack size
        if (this.undoStack.length > this.maxSize) {
            this.undoStack.shift();
        }
    }

    // Undo operation
    undo(currentCode, currentCursor) {
        if (this.undoStack.length === 0) return null;

        // Save current state to redo
        this.redoStack.push({
            code: currentCode,
            cursorPosition: currentCursor,
            timestamp: Date.now()
        });

        return this.undoStack.pop();
    }

    // Redo operation
    redo(currentCode, currentCursor) {
        if (this.redoStack.length === 0) return null;

        // Save current state to undo
        this.undoStack.push({
            code: currentCode,
            cursorPosition: currentCursor,
            timestamp: Date.now()
        });

        return this.redoStack.pop();
    }

    canUndo() {
        return this.undoStack.length > 0;
    }

    canRedo() {
        return this.redoStack.length > 0;
    }

    clear() {
        this.undoStack = [];
        this.redoStack = [];
    }
}

export default EditorStack;
```

#### **Phase 2: Code Execution Engine (Week 1-2)**

**Step 2.1: Safe Code Executor**
```javascript
// js/core/CodeExecutor.js
class CodeExecutor {
    constructor(options = {}) {
        this.timeLimit = options.timeLimit || 5000; // 5 seconds
        this.memoryLimit = options.memoryLimit || 256 * 1024 * 1024; // 256MB
    }

    // Execute code safely with test cases
    async execute(code, testCases) {
        const results = [];

        for (const testCase of testCases) {
            try {
                const result = await this._runSingleTest(code, testCase);
                results.push(result);
            } catch (error) {
                results.push({
                    status: 'Runtime Error',
                    error: error.message,
                    input: testCase.input,
                    expected: testCase.output
                });
            }
        }

        return this._aggregateResults(results);
    }

    async _runSingleTest(code, testCase) {
        const startTime = performance.now();
        const startMemory = performance.memory?.usedJSHeapSize || 0;

        // Create sandboxed execution environment
        const sandbox = this._createSandbox(testCase.input);

        // Wrap code in async function for timeout control
        const wrappedCode = `
            (async function() {
                ${code}
                return solution(${JSON.stringify(testCase.input)});
            })()
        `;

        let result;
        let timedOut = false;

        // Execute with timeout
        const timeoutPromise = new Promise((_, reject) => {
            setTimeout(() => {
                timedOut = true;
                reject(new Error('Time Limit Exceeded'));
            }, this.timeLimit);
        });

        const executePromise = (async () => {
            try {
                // Evaluate code in controlled scope
                const func = new Function('sandbox', `
                    with (sandbox) {
                        return ${wrappedCode};
                    }
                `);
                return await func(sandbox);
            } catch (error) {
                throw new Error(`Runtime Error: ${error.message}`);
            }
        })();

        try {
            result = await Promise.race([executePromise, timeoutPromise]);
        } catch (error) {
            if (timedOut) {
                return {
                    status: 'Time Limit Exceeded',
                    error: error.message,
                    input: testCase.input,
                    expected: testCase.output,
                    executionTime: this.timeLimit
                };
            }
            throw error;
        }

        const executionTime = performance.now() - startTime;
        const memoryUsed = (performance.memory?.usedJSHeapSize || 0) - startMemory;

        // Check memory limit
        if (memoryUsed > this.memoryLimit) {
            return {
                status: 'Memory Limit Exceeded',
                input: testCase.input,
                expected: testCase.output,
                memoryUsed: this._formatMemory(memoryUsed)
            };
        }

        // Compare result with expected output
        const passed = this._compareOutputs(result, testCase.output);

        return {
            status: passed ? 'Accepted' : 'Wrong Answer',
            input: testCase.input,
            expected: testCase.output,
            actual: result,
            executionTime: executionTime.toFixed(2),
            memoryUsed: this._formatMemory(memoryUsed)
        };
    }

    _createSandbox(input) {
        // Provide safe environment with utilities
        return {
            console: {
                log: (...args) => console.log('[User Code]:', ...args),
                error: (...args) => console.error('[User Code]:', ...args)
            },
            // Block dangerous APIs
            eval: undefined,
            Function: undefined,
            // Provide helpers
            Array,
            Object,
            Map,
            Set,
            Math,
            Date,
            JSON,
            parseInt,
            parseFloat,
            isNaN,
            isFinite
        };
    }

    _compareOutputs(actual, expected) {
        // Deep comparison
        return JSON.stringify(actual) === JSON.stringify(expected);
    }

    _aggregateResults(results) {
        const totalTests = results.length;
        const passedTests = results.filter(r => r.status === 'Accepted').length;

        const allPassed = passedTests === totalTests;
        const status = allPassed ? 'Accepted' : results[0]?.status || 'Failed';

        const avgTime = results.reduce((sum, r) =>
            sum + (parseFloat(r.executionTime) || 0), 0) / totalTests;

        return {
            status,
            totalTests,
            passedTests,
            testResults: results,
            averageTime: avgTime.toFixed(2),
            message: this._getStatusMessage(status, passedTests, totalTests)
        };
    }

    _getStatusMessage(status, passed, total) {
        switch (status) {
            case 'Accepted':
                return `All test cases passed! (${passed}/${total})`;
            case 'Wrong Answer':
                return `Wrong Answer on test ${passed + 1}`;
            case 'Time Limit Exceeded':
                return `Time limit exceeded. Optimize your solution.`;
            case 'Memory Limit Exceeded':
                return `Memory limit exceeded. Use more efficient data structures.`;
            case 'Runtime Error':
                return `Runtime error occurred. Check your code for bugs.`;
            default:
                return `${passed}/${total} test cases passed`;
        }
    }

    _formatMemory(bytes) {
        if (bytes < 1024) return `${bytes} B`;
        if (bytes < 1024 * 1024) return `${(bytes / 1024).toFixed(2)} KB`;
        return `${(bytes / (1024 * 1024)).toFixed(2)} MB`;
    }
}

export default CodeExecutor;
```

**Step 2.2: IndexedDB Manager for Persistence**
```javascript
// js/utils/IndexedDB.js
class IndexedDBManager {
    constructor(dbName = 'CodeJudgeDB', version = 1) {
        this.dbName = dbName;
        this.version = version;
        this.db = null;
    }

    async init() {
        return new Promise((resolve, reject) => {
            const request = indexedDB.open(this.dbName, this.version);

            request.onerror = () => reject(request.error);
            request.onsuccess = () => {
                this.db = request.result;
                resolve(this.db);
            };

            request.onupgradeneeded = (event) => {
                const db = event.target.result;

                // Create object stores
                if (!db.objectStoreNames.contains('submissions')) {
                    const submissionStore = db.createObjectStore('submissions', {
                        keyPath: 'id',
                        autoIncrement: true
                    });
                    submissionStore.createIndex('problemId', 'problemId', { unique: false });
                    submissionStore.createIndex('timestamp', 'timestamp', { unique: false });
                    submissionStore.createIndex('status', 'status', { unique: false });
                }

                if (!db.objectStoreNames.contains('problems')) {
                    const problemStore = db.createObjectStore('problems', {
                        keyPath: 'id'
                    });
                    problemStore.createIndex('difficulty', 'difficulty', { unique: false });
                    problemStore.createIndex('category', 'category', { unique: false });
                }

                if (!db.objectStoreNames.contains('userProgress')) {
                    db.createObjectStore('userProgress', { keyPath: 'problemId' });
                }
            };
        });
    }

    // Save submission
    async saveSubmission(submission) {
        const transaction = this.db.transaction(['submissions'], 'readwrite');
        const store = transaction.objectStore('submissions');

        return new Promise((resolve, reject) => {
            const request = store.add({
                ...submission,
                timestamp: Date.now()
            });

            request.onsuccess = () => resolve(request.result);
            request.onerror = () => reject(request.error);
        });
    }

    // Get all submissions for a problem
    async getSubmissionsByProblem(problemId) {
        const transaction = this.db.transaction(['submissions'], 'readonly');
        const store = transaction.objectStore('submissions');
        const index = store.index('problemId');

        return new Promise((resolve, reject) => {
            const request = index.getAll(problemId);
            request.onsuccess = () => resolve(request.result);
            request.onerror = () => reject(request.error);
        });
    }

    // Get recent submissions
    async getRecentSubmissions(limit = 20) {
        const transaction = this.db.transaction(['submissions'], 'readonly');
        const store = transaction.objectStore('submissions');
        const index = store.index('timestamp');

        return new Promise((resolve, reject) => {
            const request = index.openCursor(null, 'prev');
            const results = [];

            request.onsuccess = (event) => {
                const cursor = event.target.result;
                if (cursor && results.length < limit) {
                    results.push(cursor.value);
                    cursor.continue();
                } else {
                    resolve(results);
                }
            };

            request.onerror = () => reject(request.error);
        });
    }

    // Save problem
    async saveProblem(problem) {
        const transaction = this.db.transaction(['problems'], 'readwrite');
        const store = transaction.objectStore('problems');

        return new Promise((resolve, reject) => {
            const request = store.put(problem);
            request.onsuccess = () => resolve(request.result);
            request.onerror = () => reject(request.error);
        });
    }

    // Get all problems
    async getAllProblems() {
        const transaction = this.db.transaction(['problems'], 'readonly');
        const store = transaction.objectStore('problems');

        return new Promise((resolve, reject) => {
            const request = store.getAll();
            request.onsuccess = () => resolve(request.result);
            request.onerror = () => reject(request.error);
        });
    }

    // Update user progress
    async updateProgress(problemId, data) {
        const transaction = this.db.transaction(['userProgress'], 'readwrite');
        const store = transaction.objectStore('userProgress');

        return new Promise((resolve, reject) => {
            const request = store.put({
                problemId,
                ...data,
                lastAttempt: Date.now()
            });
            request.onsuccess = () => resolve(request.result);
            request.onerror = () => reject(request.error);
        });
    }

    // Get statistics
    async getStats() {
        const submissions = await this.getRecentSubmissions(1000);

        const stats = {
            totalSubmissions: submissions.length,
            accepted: submissions.filter(s => s.status === 'Accepted').length,
            problemsSolved: new Set(
                submissions
                    .filter(s => s.status === 'Accepted')
                    .map(s => s.problemId)
            ).size,
            averageTime: 0,
            languageBreakdown: {}
        };

        stats.acceptanceRate = stats.totalSubmissions > 0
            ? ((stats.accepted / stats.totalSubmissions) * 100).toFixed(2)
            : 0;

        return stats;
    }
}

export default IndexedDBManager;
```

#### **Phase 3: UI Components (Week 2-3)**

**Step 3.1: Code Editor Component**
```javascript
// js/ui/Editor.js
class CodeEditor {
    constructor(containerId, options = {}) {
        this.container = document.getElementById(containerId);
        this.code = options.defaultCode || '';
        this.language = options.language || 'javascript';
        this.theme = options.theme || 'dark';
        this.undoStack = new EditorStack();
        this.init();
    }

    init() {
        this.render();
        this.attachEventListeners();
        this.setupSyntaxHighlighting();
    }

    render() {
        this.container.innerHTML = `
            <div class="editor-container theme-${this.theme}">
                <div class="editor-toolbar">
                    <div class="toolbar-left">
                        <button id="runCode" class="btn btn-primary">
                            <i class="icon-play"></i> Run Code
                        </button>
                        <button id="submitCode" class="btn btn-success">
                            <i class="icon-check"></i> Submit
                        </button>
                    </div>
                    <div class="toolbar-right">
                        <button id="undo" class="btn btn-icon" title="Undo (Ctrl+Z)">
                            <i class="icon-undo"></i>
                        </button>
                        <button id="redo" class="btn btn-icon" title="Redo (Ctrl+Y)">
                            <i class="icon-redo"></i>
                        </button>
                        <button id="formatCode" class="btn btn-icon" title="Format Code">
                            <i class="icon-format"></i>
                        </button>
                        <select id="themeSelector" class="theme-select">
                            <option value="dark">Dark Theme</option>
                            <option value="light">Light Theme</option>
                            <option value="monokai">Monokai</option>
                        </select>
                    </div>
                </div>
                <div class="editor-main">
                    <div class="line-numbers" id="lineNumbers"></div>
                    <textarea
                        id="codeArea"
                        class="code-area"
                        spellcheck="false"
                        autocorrect="off"
                        autocapitalize="off"
                    >${this.code}</textarea>
                </div>
                <div class="editor-footer">
                    <span id="cursorPosition">Ln 1, Col 1</span>
                    <span id="charCount">0 characters</span>
                </div>
            </div>
        `;

        this.codeArea = this.container.querySelector('#codeArea');
        this.lineNumbers = this.container.querySelector('#lineNumbers');
    }

    attachEventListeners() {
        // Code change tracking
        let typingTimer;
        this.codeArea.addEventListener('input', () => {
            clearTimeout(typingTimer);
            this.updateLineNumbers();
            this.updateFooter();

            // Save state for undo after 500ms of no typing
            typingTimer = setTimeout(() => {
                this.saveState();
            }, 500);
        });

        // Keyboard shortcuts
        this.codeArea.addEventListener('keydown', (e) => {
            // Tab key
            if (e.key === 'Tab') {
                e.preventDefault();
                this.insertTab();
            }

            // Ctrl+Z (Undo)
            if (e.ctrlKey && e.key === 'z') {
                e.preventDefault();
                this.undo();
            }

            // Ctrl+Y (Redo)
            if (e.ctrlKey && e.key === 'y') {
                e.preventDefault();
                this.redo();
            }

            // Ctrl+/ (Comment)
            if (e.ctrlKey && e.key === '/') {
                e.preventDefault();
                this.toggleComment();
            }

            // Auto-close brackets
            this.handleBracketPairing(e);
        });

        // Scroll sync
        this.codeArea.addEventListener('scroll', () => {
            this.lineNumbers.scrollTop = this.codeArea.scrollTop;
        });

        // Cursor position tracking
        this.codeArea.addEventListener('click', () => this.updateFooter());
        this.codeArea.addEventListener('keyup', () => this.updateFooter());

        // Toolbar buttons
        document.getElementById('runCode')?.addEventListener('click', () => {
            this.onRun?.(this.getCode());
        });

        document.getElementById('submitCode')?.addEventListener('click', () => {
            this.onSubmit?.(this.getCode());
        });

        document.getElementById('undo')?.addEventListener('click', () => this.undo());
        document.getElementById('redo')?.addEventListener('click', () => this.redo());
        document.getElementById('formatCode')?.addEventListener('click', () => this.formatCode());

        document.getElementById('themeSelector')?.addEventListener('change', (e) => {
            this.changeTheme(e.target.value);
        });
    }

    updateLineNumbers() {
        const lines = this.codeArea.value.split('\n').length;
        this.lineNumbers.innerHTML = Array.from({ length: lines }, (_, i) =>
            `<div class="line-number">${i + 1}</div>`
        ).join('');
    }

    updateFooter() {
        const textarea = this.codeArea;
        const text = textarea.value;
        const cursorPos = textarea.selectionStart;

        // Calculate line and column
        const textBeforeCursor = text.substring(0, cursorPos);
        const line = textBeforeCursor.split('\n').length;
        const col = cursorPos - textBeforeCursor.lastIndexOf('\n');

        document.getElementById('cursorPosition').textContent = `Ln ${line}, Col ${col}`;
        document.getElementById('charCount').textContent = `${text.length} characters`;
    }

    insertTab() {
        const start = this.codeArea.selectionStart;
        const end = this.codeArea.selectionEnd;
        const value = this.codeArea.value;

        this.codeArea.value = value.substring(0, start) + '    ' + value.substring(end);
        this.codeArea.selectionStart = this.codeArea.selectionEnd = start + 4;
    }

    handleBracketPairing(e) {
        const pairs = {
            '(': ')',
            '[': ']',
            '{': '}',
            '"': '"',
            "'": "'"
        };

        if (pairs[e.key]) {
            e.preventDefault();
            const start = this.codeArea.selectionStart;
            const end = this.codeArea.selectionEnd;
            const value = this.codeArea.value;
            const selectedText = value.substring(start, end);

            this.codeArea.value =
                value.substring(0, start) +
                e.key + selectedText + pairs[e.key] +
                value.substring(end);

            this.codeArea.selectionStart = start + 1;
            this.codeArea.selectionEnd = end + 1;
        }
    }

    toggleComment() {
        const start = this.codeArea.selectionStart;
        const value = this.codeArea.value;
        const lineStart = value.lastIndexOf('\n', start - 1) + 1;
        const lineEnd = value.indexOf('\n', start);
        const line = value.substring(lineStart, lineEnd === -1 ? undefined : lineEnd);

        let newLine;
        if (line.trim().startsWith('//')) {
            newLine = line.replace(/\/\/\s?/, '');
        } else {
            newLine = '// ' + line;
        }

        this.codeArea.value =
            value.substring(0, lineStart) +
            newLine +
            value.substring(lineEnd === -1 ? value.length : lineEnd);
    }

    saveState() {
        this.undoStack.pushState(
            this.getCode(),
            this.codeArea.selectionStart
        );
    }

    undo() {
        const state = this.undoStack.undo(
            this.getCode(),
            this.codeArea.selectionStart
        );

        if (state) {
            this.setCode(state.code);
            this.codeArea.selectionStart = this.codeArea.selectionEnd = state.cursorPosition;
        }
    }

    redo() {
        const state = this.undoStack.redo(
            this.getCode(),
            this.codeArea.selectionStart
        );

        if (state) {
            this.setCode(state.code);
            this.codeArea.selectionStart = this.codeArea.selectionEnd = state.cursorPosition;
        }
    }

    formatCode() {
        // Basic code formatting
        let code = this.getCode();
        let formatted = code;
        let indentLevel = 0;
        const lines = code.split('\n');

        formatted = lines.map(line => {
            line = line.trim();
            if (line.includes('}') || line.includes(']') || line.includes(')')) {
                indentLevel = Math.max(0, indentLevel - 1);
            }
            const indentedLine = '    '.repeat(indentLevel) + line;
            if (line.includes('{') || line.includes('[') || line.includes('(')) {
                indentLevel++;
            }
            return indentedLine;
        }).join('\n');

        this.setCode(formatted);
    }

    setupSyntaxHighlighting() {
        // Simplified syntax highlighting (use library like Prism.js for production)
        // This is just a basic example
    }

    changeTheme(theme) {
        this.theme = theme;
        const container = this.container.querySelector('.editor-container');
        container.className = `editor-container theme-${theme}`;
    }

    getCode() {
        return this.codeArea.value;
    }

    setCode(code) {
        this.codeArea.value = code;
        this.code = code;
        this.updateLineNumbers();
        this.updateFooter();
    }

    // Callback setters
    onRun(callback) {
        this.onRun = callback;
    }

    onSubmit(callback) {
        this.onSubmit = callback;
    }
}

export default CodeEditor;
```

#### **Phase 4: Algorithm Visualizer (Week 3-4)**

**Step 4.1: Sorting Visualizer**
```javascript
// js/ui/Visualizer.js
class AlgorithmVisualizer {
    constructor(containerId) {
        this.container = document.getElementById(containerId);
        this.canvas = null;
        this.ctx = null;
        this.animationSpeed = 50;
        this.currentStep = 0;
        this.steps = [];
        this.isPlaying = false;
        this.init();
    }

    init() {
        this.render();
        this.setupCanvas();
    }

    render() {
        this.container.innerHTML = `
            <div class="visualizer-container">
                <div class="visualizer-controls">
                    <button id="playBtn" class="btn">Play</button>
                    <button id="pauseBtn" class="btn">Pause</button>
                    <button id="resetBtn" class="btn">Reset</button>
                    <button id="stepBtn" class="btn">Step</button>
                    <label>
                        Speed:
                        <input type="range" id="speedSlider" min="1" max="100" value="50">
                    </label>
                </div>
                <canvas id="visualCanvas" width="800" height="400"></canvas>
                <div class="visualizer-info">
                    <div id="stepInfo">Step: 0 / 0</div>
                    <div id="complexity">Time Complexity: O(n log n)</div>
                    <div id="currentOperation"></div>
                </div>
            </div>
        `;

        this.canvas = document.getElementById('visualCanvas');
        this.ctx = this.canvas.getContext('2d');
        this.attachEventListeners();
    }

    setupCanvas() {
        const dpr = window.devicePixelRatio || 1;
        const rect = this.canvas.getBoundingClientRect();

        this.canvas.width = rect.width * dpr;
        this.canvas.height = rect.height * dpr;
        this.ctx.scale(dpr, dpr);
    }

    attachEventListeners() {
        document.getElementById('playBtn').addEventListener('click', () => this.play());
        document.getElementById('pauseBtn').addEventListener('click', () => this.pause());
        document.getElementById('resetBtn').addEventListener('click', () => this.reset());
        document.getElementById('stepBtn').addEventListener('click', () => this.step());
        document.getElementById('speedSlider').addEventListener('input', (e) => {
            this.animationSpeed = 101 - parseInt(e.target.value);
        });
    }

    // Visualize sorting algorithm
    visualizeSort(array, algorithm = 'mergeSort') {
        this.steps = [];
        this.currentStep = 0;

        switch (algorithm) {
            case 'mergeSort':
                this.recordMergeSort([...array]);
                break;
            case 'quickSort':
                this.recordQuickSort([...array]);
                break;
            case 'bubbleSort':
                this.recordBubbleSort([...array]);
                break;
        }

        this.updateInfo();
        this.drawCurrentStep();
    }

    recordMergeSort(arr) {
        const record = (description) => {
            this.steps.push({
                array: [...arr],
                description,
                highlighted: []
            });
        };

        const merge = (left, right) => {
            const result = [];
            let i = 0, j = 0;

            while (i < left.length && j < right.length) {
                if (left[i] < right[j]) {
                    result.push(left[i++]);
                } else {
                    result.push(right[j++]);
                }
                record(`Merging: comparing ${left[i - 1] || left[i]} and ${right[j - 1] || right[j]}`);
            }

            return result.concat(left.slice(i)).concat(right.slice(j));
        };

        const mergeSort = (array) => {
            if (array.length <= 1) return array;

            const mid = Math.floor(array.length / 2);
            const left = array.slice(0, mid);
            const right = array.slice(mid);

            record(`Dividing: [${array}] into [${left}] and [${right}]`);

            return merge(mergeSort(left), mergeSort(right));
        };

        mergeSort(arr);
    }

    recordBubbleSort(arr) {
        const n = arr.length;

        for (let i = 0; i < n - 1; i++) {
            for (let j = 0; j < n - i - 1; j++) {
                this.steps.push({
                    array: [...arr],
                    description: `Comparing arr[${j}]=${arr[j]} and arr[${j + 1}]=${arr[j + 1]}`,
                    highlighted: [j, j + 1],
                    comparing: true
                });

                if (arr[j] > arr[j + 1]) {
                    [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
                    this.steps.push({
                        array: [...arr],
                        description: `Swapped ${arr[j + 1]} and ${arr[j]}`,
                        highlighted: [j, j + 1],
                        swapped: true
                    });
                }
            }
        }

        this.steps.push({
            array: [...arr],
            description: 'Sorting complete!',
            highlighted: [],
            completed: true
        });
    }

    drawCurrentStep() {
        if (this.currentStep >= this.steps.length) return;

        const step = this.steps[this.currentStep];
        const { array, highlighted, comparing, swapped, completed } = step;

        this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);

        const barWidth = this.canvas.width / array.length;
        const maxValue = Math.max(...array);

        array.forEach((value, index) => {
            const barHeight = (value / maxValue) * (this.canvas.height - 50);
            const x = index * barWidth;
            const y = this.canvas.height - barHeight;

            // Determine bar color
            let color = '#4A90E2';
            if (completed) color = '#27AE60';
            else if (highlighted.includes(index)) {
                color = swapped ? '#E74C3C' : '#F39C12';
            }

            this.ctx.fillStyle = color;
            this.ctx.fillRect(x, y, barWidth - 2, barHeight);

            // Draw value
            this.ctx.fillStyle = '#fff';
            this.ctx.font = '12px Arial';
            this.ctx.textAlign = 'center';
            this.ctx.fillText(value, x + barWidth / 2, y - 5);
        });

        // Draw description
        this.ctx.fillStyle = '#333';
        this.ctx.font = '14px Arial';
        this.ctx.textAlign = 'left';
        this.ctx.fillText(step.description, 10, 20);
    }

    play() {
        if (this.isPlaying) return;
        this.isPlaying = true;
        this.animate();
    }

    pause() {
        this.isPlaying = false;
    }

    reset() {
        this.currentStep = 0;
        this.isPlaying = false;
        this.drawCurrentStep();
        this.updateInfo();
    }

    step() {
        if (this.currentStep < this.steps.length - 1) {
            this.currentStep++;
            this.drawCurrentStep();
            this.updateInfo();
        }
    }

    animate() {
        if (!this.isPlaying || this.currentStep >= this.steps.length - 1) {
            this.isPlaying = false;
            return;
        }

        this.currentStep++;
        this.drawCurrentStep();
        this.updateInfo();

        setTimeout(() => this.animate(), this.animationSpeed);
    }

    updateInfo() {
        document.getElementById('stepInfo').textContent =
            `Step: ${this.currentStep + 1} / ${this.steps.length}`;
        document.getElementById('currentOperation').textContent =
            this.steps[this.currentStep]?.description || '';
    }
}

export default AlgorithmVisualizer;
```

#### **Phase 5: Main Application Logic (Week 4)**

**Step 5.1: Main App**
```javascript
// js/main.js
import CodeEditor from './ui/Editor.js';
import CodeExecutor from './core/CodeExecutor.js';
import Trie from './data-structures/Trie.js';
import DoublyLinkedList from './data-structures/LinkedList.js';
import IndexedDBManager from './utils/IndexedDB.js';
import AlgorithmVisualizer from './ui/Visualizer.js';

class CodeJudgeApp {
    constructor() {
        this.db = new IndexedDBManager();
        this.executor = new CodeExecutor();
        this.searchTrie = new Trie();
        this.submissionHistory = new DoublyLinkedList();
        this.problems = [];
        this.currentProblem = null;
        this.init();
    }

    async init() {
        await this.db.init();
        await this.loadProblems();
        this.setupUI();
        this.buildSearchIndex();
    }

    async loadProblems() {
        // Load from IndexedDB or fetch from JSON
        this.problems = await this.db.getAllProblems();

        if (this.problems.length === 0) {
            // Load initial problem set
            this.problems = await this.fetchProblemsFromJSON();
            for (const problem of this.problems) {
                await this.db.saveProblem(problem);
            }
        }
    }

    async fetchProblemsFromJSON() {
        const response = await fetch('./data/problems.json');
        return await response.json();
    }

    buildSearchIndex() {
        this.problems.forEach(problem => {
            // Index by title
            this.searchTrie.insert(problem.title, problem.id);
            // Index by tags
            problem.tags.forEach(tag => {
                this.searchTrie.insert(tag, problem.id);
            });
        });
    }

    setupUI() {
        // Initialize code editor
        this.editor = new CodeEditor('editor', {
            defaultCode: this.getDefaultCode(),
            theme: 'dark'
        });

        // Set up callbacks
        this.editor.onRun((code) => this.runCode(code));
        this.editor.onSubmit((code) => this.submitCode(code));

        // Initialize visualizer
        this.visualizer = new AlgorithmVisualizer('visualizer');

        // Set up problem list
        this.renderProblemList();
        this.setupSearch();
        this.setupFilters();
    }

    renderProblemList() {
        const listContainer = document.getElementById('problemList');
        const html = this.problems.map(problem => `
            <div class="problem-card" data-id="${problem.id}">
                <div class="problem-header">
                    <h3>${problem.title}</h3>
                    <span class="difficulty ${problem.difficulty}">${problem.difficulty}</span>
                </div>
                <div class="problem-stats">
                    <span>Acceptance: ${problem.acceptance}%</span>
                    <span>Submissions: ${problem.submissions}</span>
                </div>
                <div class="problem-tags">
                    ${problem.tags.map(tag => `<span class="tag">${tag}</span>`).join('')}
                </div>
            </div>
        `).join('');

        listContainer.innerHTML = html;

        // Add click handlers
        listContainer.querySelectorAll('.problem-card').forEach(card => {
            card.addEventListener('click', () => {
                const problemId = card.dataset.id;
                this.loadProblem(problemId);
            });
        });
    }

    setupSearch() {
        const searchInput = document.getElementById('searchInput');
        const resultsContainer = document.getElementById('searchResults');

        // Debounced search
        let searchTimer;
        searchInput.addEventListener('input', (e) => {
            clearTimeout(searchTimer);
            searchTimer = setTimeout(() => {
                const query = e.target.value.trim();
                if (query.length < 2) {
                    resultsContainer.innerHTML = '';
                    return;
                }

                const suggestions = this.searchTrie.getSuggestions(query, 10);
                this.displaySearchResults(suggestions);
            }, 300);
        });
    }

    displaySearchResults(suggestions) {
        const resultsContainer = document.getElementById('searchResults');
        const problemIds = new Set();

        suggestions.forEach(s => s.problems.forEach(id => problemIds.add(id)));

        const problems = Array.from(problemIds)
            .map(id => this.problems.find(p => p.id === id))
            .filter(Boolean);

        resultsContainer.innerHTML = problems.map(problem => `
            <div class="search-result" data-id="${problem.id}">
                <strong>${problem.title}</strong>
                <span class="difficulty ${problem.difficulty}">${problem.difficulty}</span>
            </div>
        `).join('');
    }

    async loadProblem(problemId) {
        this.currentProblem = this.problems.find(p => p.id === problemId);
        if (!this.currentProblem) return;

        // Update UI
        document.getElementById('problemTitle').textContent = this.currentProblem.title;
        document.getElementById('problemDescription').innerHTML = this.currentProblem.description;
        document.getElementById('problemExamples').innerHTML = this.renderExamples();
        document.getElementById('problemConstraints').innerHTML = this.currentProblem.constraints;

        // Load template code
        this.editor.setCode(this.currentProblem.template);

        // Load submission history for this problem
        const submissions = await this.db.getSubmissionsByProblem(problemId);
        this.displaySubmissionHistory(submissions);
    }

    renderExamples() {
        return this.currentProblem.examples.map((ex, i) => `
            <div class="example">
                <strong>Example ${i + 1}:</strong>
                <pre>Input: ${JSON.stringify(ex.input)}
Output: ${JSON.stringify(ex.output)}
Explanation: ${ex.explanation || ''}</pre>
            </div>
        `).join('');
    }

    async runCode(code) {
        if (!this.currentProblem) return;

        this.showLoader('Running code...');

        try {
            const result = await this.executor.execute(
                code,
                this.currentProblem.testCases.slice(0, 3) // Run sample tests
            );

            this.displayResults(result, false);
        } catch (error) {
            this.showError(error.message);
        } finally {
            this.hideLoader();
        }
    }

    async submitCode(code) {
        if (!this.currentProblem) return;

        this.showLoader('Submitting code...');

        try {
            const result = await this.executor.execute(
                code,
                this.currentProblem.testCases // Run all tests
            );

            // Save submission
            await this.db.saveSubmission({
                problemId: this.currentProblem.id,
                code,
                status: result.status,
                passedTests: result.passedTests,
                totalTests: result.totalTests,
                executionTime: result.averageTime
            });

            this.submissionHistory.addSubmission({
                problemId: this.currentProblem.id,
                result: result.status
            });

            this.displayResults(result, true);
            this.updateStats();
        } catch (error) {
            this.showError(error.message);
        } finally {
            this.hideLoader();
        }
    }

    displayResults(result, isSubmission) {
        const resultContainer = document.getElementById('results');
        const statusClass = result.status === 'Accepted' ? 'success' : 'error';

        resultContainer.innerHTML = `
            <div class="result-header ${statusClass}">
                <h2>${result.status}</h2>
                <p>${result.message}</p>
            </div>
            <div class="result-stats">
                <div class="stat">
                    <span>Test Cases</span>
                    <strong>${result.passedTests}/${result.totalTests}</strong>
                </div>
                <div class="stat">
                    <span>Runtime</span>
                    <strong>${result.averageTime} ms</strong>
                </div>
            </div>
            <div class="test-results">
                ${this.renderTestResults(result.testResults, isSubmission)}
            </div>
        `;

        if (result.status === 'Accepted' && isSubmission) {
            this.showCelebration();
        }
    }

    renderTestResults(testResults, showAll) {
        const resultsToShow = showAll ? testResults : testResults.slice(0, 3);

        return resultsToShow.map((test, i) => `
            <div class="test-case ${test.status === 'Accepted' ? 'passed' : 'failed'}">
                <div class="test-header">
                    <strong>Test Case ${i + 1}</strong>
                    <span class="${test.status === 'Accepted' ? 'success' : 'error'}">
                        ${test.status}
                    </span>
                </div>
                <div class="test-details">
                    <div><strong>Input:</strong> ${JSON.stringify(test.input)}</div>
                    ${test.status !== 'Accepted' ? `
                        <div><strong>Expected:</strong> ${JSON.stringify(test.expected)}</div>
                        <div><strong>Actual:</strong> ${JSON.stringify(test.actual)}</div>
                    ` : ''}
                    <div><strong>Time:</strong> ${test.executionTime} ms</div>
                </div>
            </div>
        `).join('');
    }

    async updateStats() {
        const stats = await this.db.getStats();
        const historyStats = this.submissionHistory.getStats();

        document.getElementById('totalSolved').textContent = stats.problemsSolved;
        document.getElementById('totalSubmissions').textContent = stats.totalSubmissions;
        document.getElementById('acceptanceRate').textContent = `${stats.acceptanceRate}%`;
    }

    showCelebration() {
        // Show confetti animation or celebration modal
        const celebration = document.createElement('div');
        celebration.className = 'celebration';
        celebration.innerHTML = `
            <div class="celebration-content">
                <h2>🎉 Accepted! 🎉</h2>
                <p>Great job solving this problem!</p>
            </div>
        `;
        document.body.appendChild(celebration);

        setTimeout(() => celebration.remove(), 3000);
    }

    getDefaultCode() {
        return `/**
 * @param {number[]} nums
 * @return {number}
 */
function solution(nums) {
    // Write your code here

}`;
    }

    showLoader(message) {
        const loader = document.getElementById('loader');
        loader.textContent = message;
        loader.classList.add('visible');
    }

    hideLoader() {
        document.getElementById('loader').classList.remove('visible');
    }

    showError(message) {
        const errorEl = document.getElementById('error');
        errorEl.textContent = message;
        errorEl.classList.add('visible');
        setTimeout(() => errorEl.classList.remove('visible'), 5000);
    }
}

// Initialize app when DOM is ready
document.addEventListener('DOMContentLoaded', () => {
    window.app = new CodeJudgeApp();
});
```

### **Key Concepts Covered in Project 1**

**Data Structures:**
- ✅ Trie (autocomplete search)
- ✅ Doubly Linked List (submission history)
- ✅ Stack (undo/redo)
- ✅ HashMap (caching)
- ✅ Priority Queue (test execution)

**Algorithms:**
- ✅ Binary Search (problem search)
- ✅ Merge Sort (sorting problems)
- ✅ Diff Algorithm (code comparison)
- ✅ Debouncing (search optimization)
- ✅ Time complexity analysis

**JavaScript Concepts:**
- ✅ Closures & Lexical Scope
- ✅ Promises & Async/Await
- ✅ Event Loop
- ✅ IndexedDB API
- ✅ Web Workers (code execution)
- ✅ Performance API
- ✅ Error Handling
- ✅ Regular Expressions
- ✅ Array Methods
- ✅ String Manipulation
- ✅ OOP & Classes
- ✅ Modules (import/export)

**Advanced Features:**
- ✅ Code sandboxing
- ✅ Memory management
- ✅ Performance monitoring
- ✅ Syntax highlighting
- ✅ Canvas rendering
- ✅ Local storage
- ✅ State management

---

## **⚛️ PROJECT 2: Real-Time Collaborative Workspace Platform (React.js + Redux Toolkit)**

### **Project Overview**
Build a real-time collaborative workspace similar to Notion/Trello/Miro combined - where teams can create boards, manage documents with rich text editing, visualize data with interactive charts, collaborate in real-time, and organize work with advanced filtering and search capabilities.

### **Technology Stack**
- **Frontend**: React 18/19, Redux Toolkit, React Router, TypeScript
- **State Management**: Redux Toolkit with RTK Query, Redux Persist
- **Real-time**: WebSocket integration
- **UI**: Tailwind CSS, Framer Motion (animations)
- **Rich Text**: Lexical/Slate.js editor
- **Charts**: D3.js/Recharts
- **Testing**: Jest, React Testing Library

### **Core Features**

#### **1. Workspace & Board Management**
- Multi-workspace support with role-based access
- Create/edit/delete boards (Kanban, Timeline, Calendar, List views)
- Drag-and-drop interface for cards/tasks
- Board templates and duplication
- Archive and restore functionality
- Nested folder structure for organization

#### **2. Rich Document Editor**
- Real-time collaborative editing
- Rich text formatting (bold, italic, headings, lists)
- Code blocks with syntax highlighting
- Embeds (images, videos, links)
- Mentions and tagging (@user, #tag)
- Version history and time-travel
- Export to PDF/Markdown

#### **3. Advanced Search & Filtering**
- Global search across all workspaces (Trie-based autocomplete)
- Filter by tags, assignees, dates, status
- Saved search queries
- Full-text search with highlighting
- Recent searches history (Doubly Linked List)

#### **4. Real-Time Collaboration**
- Live cursors showing other users
- Presence indicators (who's online)
- Real-time updates via WebSocket
- Optimistic UI updates (useOptimistic - React 19)
- Conflict resolution for concurrent edits
- Activity feed with notifications

#### **5. Data Visualization Dashboard**
- Interactive charts (productivity metrics, burndown charts)
- Customizable widgets
- Real-time data updates
- Export charts as images
- Drill-down analytics

#### **6. Performance Optimizations**
- Virtual scrolling for large lists
- Code splitting by route
- Image lazy loading
- Memoization strategies
- Server Components for static content (React 19)
- Streaming SSR

### **Step-by-Step Implementation Plan**

---

#### **PHASE 1: Project Setup & Architecture (Week 1)**

**Step 1.1: Initialize Project Structure**
```
workspace-platform/
├── src/
│   ├── app/
│   │   ├── store.ts                    (Redux store configuration)
│   │   └── rootReducer.ts              (Combine all reducers)
│   ├── features/
│   │   ├── auth/
│   │   │   ├── authSlice.ts           (Authentication state)
│   │   │   ├── authAPI.ts             (API calls)
│   │   │   └── components/
│   │   ├── workspaces/
│   │   │   ├── workspacesSlice.ts     (Workspace state)
│   │   │   ├── workspacesAPI.ts
│   │   │   └── components/
│   │   ├── boards/
│   │   │   ├── boardsSlice.ts         (Boards state)
│   │   │   ├── boardsAPI.ts
│   │   │   └── components/
│   │   ├── documents/
│   │   │   ├── documentsSlice.ts      (Documents state)
│   │   │   ├── documentsAPI.ts
│   │   │   └── components/
│   │   ├── search/
│   │   │   ├── searchSlice.ts         (Search state)
│   │   │   ├── SearchTrie.ts          (Trie data structure)
│   │   │   └── components/
│   │   └── collaboration/
│   │       ├── collaborationSlice.ts  (Real-time state)
│   │       ├── WebSocketManager.ts
│   │       └── components/
│   ├── components/
│   │   ├── common/                    (Reusable components)
│   │   ├── layout/
│   │   └── ui/
│   ├── hooks/
│   │   ├── useDebounce.ts
│   │   ├── useThrottle.ts
│   │   ├── useIntersectionObserver.ts
│   │   ├── useWebSocket.ts
│   │   └── useVirtualScroll.ts
│   ├── utils/
│   │   ├── dataStructures/
│   │   │   ├── Trie.ts
│   │   │   ├── DoublyLinkedList.ts
│   │   │   ├── PriorityQueue.ts
│   │   │   └── LRUCache.ts
│   │   ├── algorithms/
│   │   │   ├── conflictResolution.ts
│   │   │   ├── diffAlgorithm.ts
│   │   │   └── searchRanking.ts
│   │   └── helpers/
│   ├── types/
│   └── styles/
└── package.json
```

**Step 1.2: Setup Redux Toolkit Store**
- Configure Redux store with middleware
- Setup Redux Persist for offline capability
- Configure RTK Query for API calls
- Setup Redux DevTools
- Implement slice pattern for each feature

**Step 1.3: Setup Routing**
- Configure React Router v6
- Protected routes with authentication
- Lazy load route components
- Setup nested routes for workspaces/boards
- Implement breadcrumb navigation

**Step 1.4: Setup TypeScript**
- Configure strict TypeScript settings
- Define types for all entities (User, Workspace, Board, Card, Document)
- Create type definitions for Redux state
- Setup type-safe API calls

---

#### **PHASE 2: Data Structures Implementation (Week 1-2)**

**Step 2.1: Implement Trie for Search**
- Create Trie class with insert, search, autocomplete methods
- Index all searchable content (board names, card titles, document text)
- Implement fuzzy search with edit distance
- Add search ranking based on frequency and recency
- Cache search results with LRU eviction

**Step 2.2: Implement Doubly Linked List for History**
- Track recent searches (most recent at head)
- Maximum size limit with automatic cleanup
- Quick access to recent items
- Support for removing specific items
- Serialize/deserialize for persistence

**Step 2.3: Implement LRU Cache**
- Cache API responses to reduce network calls
- Cache rendered components
- Cache computed values (memoization)
- Automatic eviction based on size/time
- Track cache hit/miss metrics

**Step 2.4: Implement Priority Queue**
- Manage notification queue by priority
- Schedule background tasks
- Process real-time updates in order
- WebSocket message queue

**Step 2.5: Implement Graph for Relationships**
- Model workspace/board/card relationships
- Track user connections and permissions
- Implement breadth-first search for navigation
- Calculate shortest path for related items

---

#### **PHASE 3: Redux Toolkit State Management (Week 2-3)**

**Step 3.1: Authentication Slice**
- Actions: login, logout, register, refreshToken
- Reducers: handle auth state, user profile, permissions
- Selectors: get current user, check permissions, auth status
- Thunks: async login/logout operations
- Persist auth token in localStorage
- Auto-refresh token before expiry

**Step 3.2: Workspaces Slice**
- Actions: create, update, delete, switch workspace
- Reducers: manage workspace list, active workspace, members
- Selectors: get workspaces, active workspace, workspace permissions
- Implement normalization (entities pattern)
- Handle optimistic updates

**Step 3.3: Boards Slice**
- Actions: create, update, delete, reorder boards
- Reducers: manage boards, views (Kanban/List/Calendar), filters
- Implement drag-and-drop state updates
- Handle real-time board updates from WebSocket
- Virtual list state for large boards

**Step 3.4: Documents Slice**
- Actions: create, update, delete, version history
- Reducers: manage document content, metadata, collaborators
- Handle collaborative editing conflicts
- Implement undo/redo with command pattern
- Track cursor positions of all users

**Step 3.5: Search Slice**
- Actions: search, filter, save query, clear history
- Reducers: manage search results, filters, recent searches
- Integrate with Trie data structure
- Debounce search input
- Cache search results

**Step 3.6: RTK Query API Endpoints**
- Define API endpoints for all features
- Implement caching strategies
- Handle optimistic updates
- Error handling and retry logic
- Prefetch data for better UX

---

#### **PHASE 4: Core Features Implementation (Week 3-4)**

**Step 4.1: Kanban Board Component**
- Create draggable card components
- Implement column management
- Use react-beautiful-dnd or custom drag-and-drop
- Virtual scrolling for large lists of cards
- Inline editing for card titles
- Quick actions (duplicate, archive, move)
- Keyboard shortcuts

**Step 4.2: Rich Text Editor**
- Integrate Lexical or Slate.js
- Custom toolbar with formatting options
- Implement mentions (@user) with autocomplete
- Code blocks with syntax highlighting
- Image upload with drag-and-drop
- Link previews
- Save drafts automatically

**Step 4.3: Search Component**
- Global search bar with keyboard shortcut (Cmd+K)
- Real-time search as you type (debounced)
- Autocomplete suggestions from Trie
- Display results by category (Boards, Cards, Documents)
- Highlight matching text
- Navigate results with keyboard
- Recent searches dropdown

**Step 4.4: Real-Time Collaboration**
- WebSocket connection management
- Broadcast user actions (typing, moving cursor)
- Display live cursors with user avatars
- Show presence indicators
- Handle connection/disconnection
- Implement heartbeat for connection health
- Queue messages when offline

**Step 4.5: Filtering System**
- Multi-criteria filters (tags, assignees, dates, status)
- Combine filters with AND/OR logic
- Save filter presets
- Quick filters for common queries
- Filter count badges
- Clear all filters button

---

#### **PHASE 5: Advanced Features (Week 4-5)**

**Step 5.1: Version History & Time Travel**
- Save document snapshots on significant changes
- Use doubly linked list to navigate history
- Display diff view between versions
- Restore to previous version
- Branch from historical version

**Step 5.2: Notifications System**
- Priority queue for notification display
- Real-time notifications via WebSocket
- Push notifications (Web Push API)
- Group similar notifications
- Mark as read/unread
- Notification preferences

**Step 5.3: Data Visualization Dashboard**
- Create reusable chart components with D3.js/Recharts
- Productivity metrics (cards completed, time tracking)
- Burndown charts for sprints
- User activity heatmaps
- Custom dashboard layouts (drag-and-drop widgets)
- Export charts as PNG/SVG

**Step 5.4: Offline Support**
- Service Worker for offline functionality
- Redux Persist for state persistence
- Queue mutations when offline
- Sync when back online
- Conflict resolution for offline edits
- Offline indicator UI

**Step 5.5: Performance Optimizations**
- Implement React.memo for expensive components
- useMemo for computed values
- useCallback for event handlers
- Code splitting with React.lazy and Suspense
- Route-based code splitting
- Image lazy loading with Intersection Observer
- Virtual scrolling for large lists (react-window)
- Debounce/throttle expensive operations

---

#### **PHASE 6: React 18/19 Features Integration (Week 5)**

**Step 6.1: Concurrent Rendering**
- Use startTransition for non-urgent updates
- Mark heavy operations as transitions
- Keep UI responsive during updates
- Show loading states for transitions

**Step 6.2: Suspense for Data Fetching**
- Wrap components in Suspense boundaries
- Show loading skeletons
- Streaming SSR for initial page load
- Progressive hydration

**Step 6.3: Server Components (React 19)**
- Convert static content to Server Components
- Reduce client bundle size
- Direct database access from Server Components
- Stream data to client

**Step 6.4: useOptimistic Hook (React 19)**
- Implement optimistic UI for mutations
- Auto-revert on error
- Better UX for card moves, updates
- Form submissions with optimistic feedback

**Step 6.5: use Hook for Async Data (React 19)**
- Replace useEffect for data fetching
- Conditional data fetching
- Simpler async patterns
- Better error handling

---

#### **PHASE 7: Testing & Quality Assurance (Week 6)**

**Step 7.1: Unit Tests**
- Test Redux reducers and selectors
- Test utility functions and algorithms
- Test data structures (Trie, LinkedList, etc.)
- Test custom hooks
- Achieve 80%+ code coverage

**Step 7.2: Component Tests**
- Test component rendering
- Test user interactions
- Test prop changes and re-renders
- Mock Redux store and API calls
- Snapshot testing for UI components

**Step 7.3: Integration Tests**
- Test complete user flows
- Test real-time collaboration
- Test WebSocket integration
- Test form submissions
- Test navigation and routing

**Step 7.4: Performance Testing**
- Measure render performance
- Profile with React DevTools
- Test with large datasets (1000+ cards)
- Measure bundle size
- Lighthouse audits

---

### **Key DSA Concepts Covered in Project 2**

**Data Structures:**
- ✅ Trie (search autocomplete, indexing)
- ✅ Doubly Linked List (history navigation, undo/redo)
- ✅ LRU Cache (API response caching, memoization)
- ✅ Priority Queue (notifications, task scheduling)
- ✅ Graph (workspace relationships, permissions)
- ✅ HashMap (entity normalization, lookups)
- ✅ Stack (undo/redo operations)
- ✅ Set (tracking unique items, tags)

**Algorithms:**
- ✅ Fuzzy Search (edit distance algorithm)
- ✅ Diff Algorithm (version comparison)
- ✅ Conflict Resolution (operational transformation)
- ✅ Search Ranking (scoring algorithms)
- ✅ Breadth-First Search (navigation, relationships)
- ✅ Debouncing/Throttling (performance optimization)
- ✅ Virtual Scrolling (windowing algorithm)

**React Concepts:**
- ✅ All Hooks (useState, useEffect, useContext, useReducer, useMemo, useCallback, useRef, useLayoutEffect)
- ✅ Custom Hooks (reusable logic)
- ✅ Context API (theme, auth)
- ✅ React.memo (performance)
- ✅ Code Splitting (React.lazy, Suspense)
- ✅ Error Boundaries
- ✅ Portals (modals, tooltips)
- ✅ React 18 Concurrent Features
- ✅ React 19 New APIs (useOptimistic, use, useFormStatus)

**Redux Toolkit Concepts:**
- ✅ Slices (state management)
- ✅ RTK Query (data fetching, caching)
- ✅ Selectors (memoized state selection)
- ✅ Thunks (async actions)
- ✅ Entity Normalization
- ✅ Optimistic Updates
- ✅ Redux Persist
- ✅ Redux DevTools

**Advanced Features:**
- ✅ WebSocket Real-time Communication
- ✅ Operational Transformation
- ✅ Offline-First Architecture
- ✅ Service Workers
- ✅ Virtual Scrolling
- ✅ Drag and Drop
- ✅ Rich Text Editing
- ✅ Data Visualization

---

## **🟢 PROJECT 3: Multi-Tenant SaaS API Platform (Node.js + Express + MongoDB)**

### **Project Overview**
Build a complete multi-tenant SaaS platform backend similar to Stripe/Twilio - providing RESTful and GraphQL APIs for various services, with advanced features like rate limiting, caching, real-time analytics, job queuing, and comprehensive monitoring.

### **Technology Stack**
- **Runtime**: Node.js (LTS version)
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose ODM
- **Cache**: Redis (caching, rate limiting, sessions)
- **Queue**: Bull (job queue with Redis)
- **Real-time**: Socket.io
- **Search**: Elasticsearch (optional, or MongoDB full-text)
- **API**: REST + GraphQL (Apollo Server)
- **Authentication**: JWT, OAuth 2.0, API Keys
- **Testing**: Jest, Supertest
- **Documentation**: Swagger/OpenAPI
- **Monitoring**: Winston (logging), Prometheus metrics

### **Core Features**

#### **1. Multi-Tenancy**
- Organization-based isolation
- Tenant-specific databases/collections
- Resource quotas per tenant
- Usage tracking and billing

#### **2. Authentication & Authorization**
- Multiple auth strategies (JWT, OAuth 2.0, API Keys)
- Role-Based Access Control (RBAC)
- Permission system with granular controls
- 2FA support
- Session management
- Token refresh mechanism

#### **3. API Gateway**
- Request routing
- Rate limiting (per user, per endpoint, per tenant)
- Request validation
- Response caching
- API versioning
- Request/Response logging

#### **4. Data Processing Pipeline**
- Stream processing for large files
- Batch processing jobs
- Data transformation and validation
- Export/Import functionality
- Data aggregation

#### **5. Real-Time Features**
- WebSocket connections
- Pub/Sub messaging
- Live notifications
- Real-time analytics dashboard
- Presence tracking

#### **6. Advanced Search**
- Full-text search across entities
- Autocomplete with Trie
- Fuzzy matching
- Faceted search
- Search analytics

### **Step-by-Step Implementation Plan**

---

#### **PHASE 1: Project Architecture & Setup (Week 1)**

**Step 1.1: Project Structure**
```
saas-api-platform/
├── src/
│   ├── config/
│   │   ├── database.js              (MongoDB connection)
│   │   ├── redis.js                 (Redis connection)
│   │   ├── env.js                   (Environment variables)
│   │   └── constants.js
│   ├── models/
│   │   ├── User.js
│   │   ├── Organization.js          (Tenant)
│   │   ├── ApiKey.js
│   │   ├── Subscription.js
│   │   ├── Usage.js
│   │   └── AuditLog.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── userController.js
│   │   ├── organizationController.js
│   │   └── apiController.js
│   ├── services/
│   │   ├── authService.js
│   │   ├── cacheService.js          (Redis caching)
│   │   ├── queueService.js          (Bull jobs)
│   │   ├── searchService.js         (Search with Trie)
│   │   ├── notificationService.js
│   │   └── analyticsService.js
│   ├── middleware/
│   │   ├── auth.js                  (JWT verification)
│   │   ├── rateLimit.js             (Rate limiting)
│   │   ├── validation.js            (Request validation)
│   │   ├── tenantIsolation.js
│   │   ├── errorHandler.js
│   │   └── logging.js
│   ├── routes/
│   │   ├── v1/                      (API v1)
│   │   │   ├── auth.js
│   │   │   ├── users.js
│   │   │   └── organizations.js
│   │   └── v2/                      (API v2)
│   ├── graphql/
│   │   ├── schema.js
│   │   ├── resolvers.js
│   │   └── directives.js
│   ├── utils/
│   │   ├── dataStructures/
│   │   │   ├── Trie.js              (Autocomplete)
│   │   │   ├── BloomFilter.js       (Cache optimization)
│   │   │   ├── ConsistentHash.js    (Load balancing)
│   │   │   ├── CircularBuffer.js    (Logging)
│   │   │   ├── PriorityQueue.js     (Job scheduling)
│   │   │   └── LRUCache.js
│   │   ├── algorithms/
│   │   │   ├── slidingWindow.js     (Rate limiting)
│   │   │   ├── leakyBucket.js
│   │   │   └── tokenBucket.js
│   │   └── helpers/
│   ├── jobs/
│   │   ├── emailJob.js
│   │   ├── dataExportJob.js
│   │   ├── analyticsJob.js
│   │   └── cleanupJob.js
│   ├── websocket/
│   │   ├── handlers/
│   │   └── socketManager.js
│   └── app.js
├── tests/
├── docs/
└── package.json
```

**Step 1.2: Database Setup**
- Configure MongoDB connection with Mongoose
- Setup connection pooling
- Implement database sharding strategy
- Create indexes for frequently queried fields
- Setup database migrations

**Step 1.3: Redis Setup**
- Configure Redis for caching
- Setup Redis for session management
- Configure Redis for rate limiting
- Setup Redis pub/sub for real-time features
- Implement Redis cluster for high availability

**Step 1.4: Environment Configuration**
- Setup dotenv for environment variables
- Configure different environments (dev, staging, prod)
- Secrets management
- Feature flags

---

#### **PHASE 2: Data Structures for Performance (Week 1-2)**

**Step 2.1: Implement Trie for Autocomplete**
- Build Trie for product/user name search
- Insert all searchable entities
- Implement prefix search with ranking
- Add fuzzy search support
- Cache frequent searches

**Step 2.2: Implement Bloom Filter**
- Check API key existence without DB query
- Cache membership testing
- Reduce database lookups
- Handle false positives gracefully

**Step 2.3: Implement Consistent Hashing**
- Distribute load across multiple servers
- Minimize redistribution when scaling
- Use for cache key distribution
- Handle node failures

**Step 2.4: Implement Circular Buffer for Logs**
- Fixed-size log buffer
- Automatic old log removal
- Memory-efficient logging
- Real-time log streaming

**Step 2.5: Implement LRU Cache**
- Cache frequently accessed data
- Automatic eviction of old entries
- Track cache hit/miss ratio
- Redis-backed distributed cache

**Step 2.6: Implement Priority Queue for Jobs**
- Schedule jobs by priority
- Process high-priority jobs first
- Delay low-priority jobs
- Job retry mechanism

---

#### **PHASE 3: Authentication & Authorization (Week 2)**

**Step 3.1: JWT Authentication**
- Generate JWT tokens on login
- Verify tokens on protected routes
- Implement refresh token rotation
- Handle token expiration
- Blacklist revoked tokens (Redis)

**Step 3.2: OAuth 2.0 Integration**
- Setup OAuth providers (Google, GitHub)
- Authorization code flow
- Handle OAuth callbacks
- Link OAuth accounts to users

**Step 3.3: API Key Authentication**
- Generate secure API keys (UUID + hash)
- Store hashed keys in database
- Validate API keys on requests
- Track API key usage
- Support key rotation

**Step 3.4: Role-Based Access Control**
- Define roles (Admin, User, Guest)
- Assign permissions to roles
- Check permissions on routes
- Implement middleware for permission checks
- Support custom permissions

**Step 3.5: Two-Factor Authentication**
- Generate TOTP secrets
- Verify TOTP codes
- Backup codes generation
- SMS/Email OTP option

---

#### **PHASE 4: Rate Limiting & Caching (Week 2-3)**

**Step 4.1: Sliding Window Rate Limiter**
- Track requests in time windows
- Use Redis sorted sets
- Implement per-user limits
- Implement per-endpoint limits
- Return rate limit headers

**Step 4.2: Token Bucket Algorithm**
- Maintain token buckets per user
- Refill tokens at fixed rate
- Allow burst requests
- Handle bucket overflow

**Step 4.3: Leaky Bucket Algorithm**
- Process requests at constant rate
- Queue excess requests
- Prevent traffic spikes
- Graceful degradation

**Step 4.4: Multi-Layer Caching**
- In-memory cache with LRU
- Redis cache for distributed systems
- Cache invalidation strategies
- Cache warming on startup
- Cache-aside pattern

**Step 4.5: Response Caching**
- Cache GET request responses
- Set cache TTL based on data volatility
- Conditional requests (ETag, Last-Modified)
- Cache busting strategies

---

#### **PHASE 5: Data Processing Pipeline (Week 3-4)**

**Step 5.1: Stream Processing**
- Use Node.js streams for file uploads
- Process large CSV files without loading to memory
- Transform data on-the-fly
- Handle backpressure
- Error handling in streams

**Step 5.2: Batch Processing with Bull Queue**
- Create job queue for async tasks
- Process jobs in batches
- Implement job retry logic
- Job priority and delays
- Monitor job progress

**Step 5.3: Data Aggregation Pipeline**
- MongoDB aggregation for analytics
- Group, sort, limit operations
- Calculate metrics (counts, averages, sums)
- Time-based aggregations
- Cache aggregation results

**Step 5.4: Export/Import Features**
- Export data to CSV/JSON/Excel
- Use streams for large exports
- Queue export jobs
- Import validation
- Handle import errors

**Step 5.5: Real-Time Data Processing**
- Process incoming events in real-time
- Use event-driven architecture
- Publish events to subscribers
- Track event metrics

---

#### **PHASE 6: Real-Time Features with WebSocket (Week 4)**

**Step 6.1: Socket.io Setup**
- Initialize Socket.io server
- Handle connection/disconnection
- Implement authentication for sockets
- Manage socket rooms
- Handle socket errors

**Step 6.2: Pub/Sub Messaging**
- Redis pub/sub for multi-server support
- Publish events to channels
- Subscribe to channels
- Broadcast to specific rooms
- Handle message ordering

**Step 6.3: Live Notifications**
- Send real-time notifications
- Queue notifications with priority
- Mark notifications as read
- Notification preferences
- Push notifications to offline users (queue)

**Step 6.4: Presence Tracking**
- Track online/offline users
- Show user status
- Last seen timestamp
- Typing indicators

**Step 6.5: Real-Time Analytics**
- Stream metrics to dashboard
- Update charts in real-time
- WebSocket-based updates
- Historical data + live updates

---

#### **PHASE 7: Search & Indexing (Week 4-5)**

**Step 7.1: Full-Text Search with MongoDB**
- Create text indexes
- Implement search queries
- Search across multiple fields
- Search relevance scoring
- Pagination for search results

**Step 7.2: Autocomplete with Trie**
- Build Trie index on server startup
- Update Trie on data changes
- Return top suggestions
- Fuzzy matching support
- Cache popular searches

**Step 7.3: Advanced Filtering**
- Multi-field filters
- Range queries (dates, numbers)
- Combine filters with AND/OR
- Faceted search
- Filter result counts

**Step 7.4: Search Analytics**
- Track search queries
- Popular searches
- No-result searches
- Search performance metrics

---

#### **PHASE 8: Monitoring & Observability (Week 5)**

**Step 8.1: Logging with Winston**
- Configure log levels (error, warn, info, debug)
- Log to files with rotation
- Log to external services
- Structured logging (JSON)
- Correlation IDs for request tracking

**Step 8.2: Error Tracking**
- Centralized error handler
- Log errors with stack traces
- Alert on critical errors
- Error analytics
- Integration with error tracking services

**Step 8.3: Performance Monitoring**
- Track request/response times
- Database query performance
- Cache hit/miss ratios
- Memory usage
- CPU usage

**Step 8.4: Health Checks**
- Endpoint for health status
- Check database connectivity
- Check Redis connectivity
- Check external services
- Graceful shutdown

**Step 8.5: Metrics with Prometheus**
- Export metrics in Prometheus format
- Track custom business metrics
- Request counts and latencies
- Visualize with Grafana

---

#### **PHASE 9: GraphQL API (Week 5-6)**

**Step 9.1: Apollo Server Setup**
- Initialize Apollo Server
- Define GraphQL schema
- Create type definitions
- Integrate with Express

**Step 9.2: Resolvers**
- Query resolvers
- Mutation resolvers
- Subscription resolvers (real-time)
- Resolver composition
- DataLoader for batching/caching

**Step 9.3: Authentication & Authorization**
- Extract user from context
- Protect resolvers with auth check
- Field-level permissions
- Custom directives for auth

**Step 9.4: Subscriptions for Real-Time**
- WebSocket subscriptions
- Publish/subscribe pattern
- Filter subscriptions
- Subscription authentication

---

#### **PHASE 10: Testing & Deployment (Week 6)**

**Step 10.1: Unit Tests**
- Test services and utilities
- Test data structures
- Test algorithms
- Mock external dependencies
- Test coverage > 80%

**Step 10.2: Integration Tests**
- Test API endpoints with Supertest
- Test database operations
- Test authentication flows
- Test rate limiting
- Test WebSocket connections

**Step 10.3: Load Testing**
- Simulate concurrent users
- Test rate limits under load
- Identify bottlenecks
- Test cache effectiveness
- Stress test database

**Step 10.4: Security Audits**
- Test for SQL injection (NoSQL injection)
- Test for XSS vulnerabilities
- Test authentication bypasses
- Test rate limit bypasses
- Dependency vulnerability scanning

**Step 10.5: Documentation**
- API documentation with Swagger
- GraphQL playground
- Code comments and JSDoc
- README with setup instructions
- Architecture diagrams

**Step 10.6: Deployment**
- Dockerize application
- Setup CI/CD pipeline
- Deploy to cloud (AWS/GCP/Azure)
- Configure load balancer
- Setup monitoring and alerts
- Database backups
- Zero-downtime deployment

---

### **Key DSA Concepts Covered in Project 3**

**Data Structures:**
- ✅ Trie (autocomplete, search indexing)
- ✅ Bloom Filter (cache optimization, API key checks)
- ✅ Consistent Hashing (load distribution)
- ✅ Circular Buffer (logging, rate limiting)
- ✅ LRU Cache (response caching, memoization)
- ✅ Priority Queue (job scheduling, notifications)
- ✅ Hash Table (fast lookups, indexing)
- ✅ Sorted Set (Redis for rate limiting, leaderboards)

**Algorithms:**
- ✅ Sliding Window (rate limiting)
- ✅ Token Bucket (rate limiting)
- ✅ Leaky Bucket (traffic shaping)
- ✅ Consistent Hashing (load balancing)
- ✅ LRU Eviction (cache management)
- ✅ Graph Traversal (permissions, relationships)
- ✅ Binary Search (sorted data queries)
- ✅ String Matching (search, fuzzy search)

**Node.js Concepts:**
- ✅ Event Loop & Non-blocking I/O
- ✅ Streams (Readable, Writable, Transform)
- ✅ Buffers (binary data handling)
- ✅ Event Emitters (custom events)
- ✅ Clustering (multi-core utilization)
- ✅ Worker Threads (CPU-intensive tasks)
- ✅ Child Processes
- ✅ Promises & Async/Await

**Express.js Concepts:**
- ✅ Middleware pattern
- ✅ Routing
- ✅ Error handling
- ✅ Request/Response lifecycle
- ✅ Template engines
- ✅ Static file serving

**Database Concepts:**
- ✅ Mongoose schemas and models
- ✅ Indexing strategies
- ✅ Aggregation pipelines
- ✅ Transactions
- ✅ Population (JOINs)
- ✅ Virtuals and methods
- ✅ Hooks and middleware

**Advanced Features:**
- ✅ Multi-tenancy architecture
- ✅ API versioning
- ✅ Rate limiting strategies
- ✅ Caching layers
- ✅ Job queues
- ✅ Real-time communication
- ✅ Pub/Sub messaging
- ✅ Authentication strategies
- ✅ Authorization patterns
- ✅ Monitoring and logging
- ✅ Performance optimization
- ✅ Security best practices

---

## **🎯 PROJECT COMPLETION CHECKLIST**

### **For All Three Projects:**

**✅ Code Quality**
- [ ] Follow consistent code style (ESLint, Prettier)
- [ ] Write meaningful comments
- [ ] Use descriptive variable and function names
- [ ] Handle all error cases
- [ ] Implement proper validation

**✅ Performance**
- [ ] Optimize bundle size (< 500KB initial)
- [ ] Achieve Lighthouse score > 90
- [ ] Measure and optimize render times
- [ ] Implement proper caching
- [ ] Use production builds

**✅ Testing**
- [ ] Unit test coverage > 80%
- [ ] Integration tests for critical flows
- [ ] E2E tests for user journeys
- [ ] Performance tests
- [ ] Security tests

**✅ Documentation**
- [ ] README with setup instructions
- [ ] API documentation
- [ ] Code comments
- [ ] Architecture diagrams
- [ ] Deployment guide

**✅ Security**
- [ ] Input validation
- [ ] Output sanitization
- [ ] Secure authentication
- [ ] HTTPS only
- [ ] Security headers
- [ ] Dependency audits

**✅ Accessibility**
- [ ] Keyboard navigation
- [ ] Screen reader support
- [ ] ARIA labels
- [ ] Color contrast
- [ ] Focus indicators

**✅ Portfolio Presentation**
- [ ] Live demo deployed
- [ ] GitHub repository with clean commit history
- [ ] Screenshots and GIFs
- [ ] Video walkthrough
- [ ] Highlight technical challenges solved
- [ ] Showcase DSA concepts used

---

## **📊 Learning Outcomes**

After completing all three projects, you will have:

**✅ Mastered Data Structures:**
- Implemented Trie, Doubly Linked List, Stack, Queue, Priority Queue, Heap, Graph, Hash Table, Bloom Filter, LRU Cache, Circular Buffer

**✅ Mastered Algorithms:**
- Search (Binary Search, DFS, BFS, Trie Search)
- Sorting (Merge Sort, Quick Sort, Heap Sort)
- Dynamic Programming
- Graph algorithms
- String algorithms
- Rate limiting algorithms
- Caching strategies

**✅ Mastered JavaScript:**
- Closures, Promises, Async/Await
- Event Loop, Call Stack
- Prototypes, Classes, OOP
- Functional Programming
- Modules, Import/Export
- Error Handling
- Performance Optimization

**✅ Mastered React:**
- All Hooks (useState, useEffect, useContext, useReducer, useMemo, useCallback, etc.)
- Redux Toolkit (Slices, RTK Query, Middleware)
- Performance optimization (React.memo, code splitting, lazy loading)
- React 18/19 features (Concurrent rendering, Suspense, Server Components, useOptimistic)
- Testing (Jest, React Testing Library)

**✅ Mastered Node.js:**
- Express.js framework
- MongoDB with Mongoose
- Redis for caching
- WebSocket/Socket.io
- Authentication (JWT, OAuth)
- API design (REST, GraphQL)
- Job queues
- Streams and Buffers
- Security best practices
- Deployment and DevOps

**✅ Ready for Interviews:**
- Can explain and implement all major data structures
- Can solve algorithm problems efficiently
- Can architect full-stack applications
- Can discuss trade-offs and design decisions
- Can demonstrate production-ready code
- Portfolio with three impressive projects

---


## Advanced HTML Interview Questions

### 1. What is the difference between `<script>`, `<script defer>`, and `<script async>`, and when would you use each?

**Answer:** Regular `<script>` blocks HTML parsing until the script downloads and executes. `<script defer>` downloads in parallel with HTML parsing but executes only after parsing completes, maintaining order between multiple deferred scripts. `<script async>` downloads in parallel and executes immediately upon completion, potentially interrupting HTML parsing, with no guaranteed execution order. Use `defer` for scripts that depend on DOM or other scripts; use `async` for independent scripts like analytics.

### 2. Why is `<button type="button">` important inside a form, and what happens if you omit the type attribute?

**Answer:** Without an explicit `type` attribute, buttons default to `type="submit"` inside forms. This means clicking the button will submit the form, which is often unintended for buttons meant to perform client-side actions like opening modals or adding form fields. Always specify `type="button"` for non-submit buttons to prevent accidental form submissions and unexpected page reloads.

### 3. Explain the security implications of using `target="_blank"` and how to mitigate them.

**Answer:** When using `target="_blank"`, the opened page gains access to the original window via `window.opener`, enabling potential phishing attacks where the new page redirects the original tab to a malicious site. Mitigate this by adding `rel="noopener noreferrer"` to the link, which prevents the new page from accessing `window.opener` and blocks the referrer header from being sent.

### 4. What is the purpose of the `loading="lazy"` attribute on images, and what are its limitations?

**Answer:** The `loading="lazy"` attribute enables native lazy loading, deferring image downloads until they're near the viewport, improving initial page load performance and reducing bandwidth usage. Limitations include: it shouldn't be used on above-the-fold images (causes layout shift), browser support varies, and the exact threshold for "near viewport" is browser-dependent. Critical images should use `loading="eager"` or omit the attribute.

### 5. How does the `<picture>` element differ from `srcset`, and when should you use each?

**Answer:** `srcset` is for resolution switching (serving different resolutions of the same image based on device pixel ratio or viewport width), while `<picture>` enables art direction (serving completely different images based on media queries, format support, or other conditions). Use `srcset` when you have the same image at different sizes; use `<picture>` when you need different crops, aspect ratios, or want to provide modern formats like WebP with fallbacks.

### 6. What happens when you nest a `<button>` inside an `<a>` tag, or vice versa, and why is this problematic?

**Answer:** Nesting interactive elements violates HTML specifications and creates accessibility issues because screen readers cannot properly convey nested interactive roles, and keyboard navigation becomes ambiguous. Browsers may render it inconsistently, and the behavior of which element's action fires (link navigation vs button click) is unpredictable. Always use one interactive element and style it appropriately, or use JavaScript to handle the interaction separately.

### 7. Explain the difference between `contenteditable="true"` and a `<textarea>`, including use cases and limitations.

**Answer:** `contenteditable` allows any element to become editable and preserves rich formatting (bold, links, nested elements), making it suitable for WYSIWYG editors. `<textarea>` only accepts plain text but provides better form integration, automatic serialization, and consistent behavior. `contenteditable` has security risks (can execute scripts if not sanitized), inconsistent browser behavior, and complex state management. Use `<textarea>` for simple text input; use `contenteditable` only when rich formatting is essential.

### 8. What is the purpose of `<link rel="preconnect">`, `<link rel="dns-prefetch">`, and `<link rel="preload">`, and how do they differ?

**Answer:** `dns-prefetch` only resolves DNS early, `preconnect` performs DNS lookup, TCP handshake, and TLS negotiation, while `preload` actually fetches the resource. `preload` is highest priority and should be used sparingly for critical resources needed immediately (fonts, critical CSS). `preconnect` is for third-party origins you'll use soon. `dns-prefetch` is a lightweight hint for potential connections. Overusing these directives wastes bandwidth and can degrade performance.

### 9. How does the browser determine which `<source>` to use in a `<video>` or `<audio>` element?

**Answer:** The browser evaluates `<source>` elements in order from top to bottom, checking each against its codec support and the `type` attribute (MIME type with optional codecs parameter). It selects the first source it can play and ignores the rest. If no sources are supported, it falls back to content inside the `<video>`/`<audio>` tags. The order matters significantly—place preferred formats (like WebM or AV1) first, then fallbacks (like MP4).

### 10. What is the difference between `aria-label`, `aria-labelledby`, and `aria-describedby`?

**Answer:** `aria-label` provides a direct text label for screen readers, overriding any visible text. `aria-labelledby` references one or more element IDs whose text content becomes the label, allowing reuse of existing visible text and supporting multiple sources. `aria-describedby` provides supplementary information (like help text or error messages) read after the label. Use `aria-labelledby` when visible labels exist, `aria-label` for icon-only buttons, and `aria-describedby` for additional context.

### 11. Explain the security model of the `sandbox` attribute on iframes and its different flag values.

**Answer:** The `sandbox` attribute applies restrictions to iframe content, treating it as from a unique origin by default. Without flags, it blocks scripts, forms, popups, same-origin access, and more. Flags like `allow-scripts`, `allow-forms`, `allow-same-origin`, `allow-popups` selectively enable features. Never combine `allow-scripts` and `allow-same-origin` for untrusted content, as this essentially removes sandboxing. Use `sandbox` for embedding third-party content to mitigate XSS and clickjacking risks.

### 12. What is the difference between `required`, `aria-required`, and using `pattern` for validation?

**Answer:** `required` is native HTML5 validation that prevents form submission and triggers browser validation UI, working without JavaScript. `aria-required="true"` only announces the requirement to screen readers but doesn't enforce it—use it for custom validation. `pattern` validates input against a regex but doesn't indicate empty fields are invalid unless combined with `required`. Always use native `required` for enforcement, add `aria-required` only if using custom validation, and use `pattern` for format validation.

### 13. How do `<meta>` tags with `http-equiv` differ from HTTP headers, and which takes precedence?

**Answer:** `<meta http-equiv>` simulates HTTP headers but is processed by the browser after the HTML document starts parsing, while actual HTTP headers are processed before any content. HTTP headers generally take precedence and are more secure (can't be injected via XSS). Critical headers like `Content-Security-Policy` or `X-Frame-Options` should be sent as real HTTP headers, not meta tags, because meta tags are evaluated too late to protect against some attacks.

### 14. What is the purpose of the `autocomplete` attribute, and how does it differ from `autocorrect` and `autocapitalize`?

**Answer:** `autocomplete` controls browser autofill behavior with standardized tokens (like `email`, `tel`, `cc-number`) that help browsers provide accurate suggestions and enable proper keyboard types on mobile. `autocorrect` (iOS Safari) controls spell-checking corrections, while `autocapitalize` controls automatic capitalization of user input. Use proper `autocomplete` values to improve form UX and help password managers; use `autocorrect="off"` for code, emails, or usernames.

### 15. Explain the difference between `<datalist>`, `<select>`, and `<input type="text">` with suggestions.

**Answer:** `<select>` restricts users to predefined options only. `<datalist>` provides suggestions for an `<input>` but allows freeform text entry—users can type anything or choose from suggestions. A plain `<input>` with JavaScript-powered suggestions offers more control but requires custom implementation. Use `<select>` for strict choices, `<datalist>` for flexible input with hints (like city names), and custom implementations when you need advanced features like async search or custom rendering.

### 16. What happens when you set `display: none` via CSS versus `hidden` attribute versus `aria-hidden="true"`?

**Answer:** `display: none` removes the element from both visual and accessibility trees—screen readers won't announce it. The `hidden` attribute does the same (equivalent to `display: none` in browser default styles). `aria-hidden="true"` hides the element only from screen readers but keeps it visually rendered and interactive. Use `hidden` for truly hidden content, use `aria-hidden` to hide decorative elements from screen readers while keeping them visible, and never hide focusable elements with `aria-hidden`.

### 17. How does the browser handle `<base>` tag, and what are the risks of using it?

**Answer:** The `<base>` tag sets the base URL for all relative URLs in the document, affecting links, images, scripts, and stylesheets. If an attacker can inject a `<base>` tag (via XSS), they can redirect all relative resources to malicious servers, stealing credentials or injecting malicious code. Use it cautiously, only in controlled environments, always validate/sanitize if the base URL comes from user input, and prefer absolute URLs or configure resources at the server level.

### 18. What is the difference between `<template>`, `<script type="text/template">`, and innerHTML for client-side templates?

**Answer:** `<template>` is the proper HTML5 element for inert markup—its content is parsed but not rendered, doesn't execute scripts, and can be efficiently cloned via `content.cloneNode()`. `<script type="text/template">` keeps content as text (not parsed DOM) and requires innerHTML parsing, which is slower and can't contain scripts. Using innerHTML directly is fastest for simple cases but has XSS risks if content isn't sanitized. Use `<template>` for complex, reusable templates in modern applications.

### 19. Explain how `inputmode` differs from `type` on input elements and when to use each.

**Answer:** The `type` attribute defines the input's semantic meaning, validation rules, and default appearance (e.g., `type="email"` validates email format). `inputmode` only affects the virtual keyboard shown on mobile devices (e.g., `inputmode="numeric"` shows a number pad). Use both together: `type="text" inputmode="numeric"` for inputs like credit cards that need number keyboards but shouldn't use `type="number"` (which adds spinners and has limitations). This separation provides better control over validation vs. input method.

### 20. What are the implications of using `formnovalidate` on a submit button?

**Answer:** `formnovalidate` on a submit button bypasses all HTML5 validation for that specific submission, ignoring `required`, `pattern`, `min`, `max`, etc. This is useful for "Save as Draft" or "Cancel" buttons that shouldn't block submission due to incomplete data. However, server-side validation is still essential since client-side validation can be bypassed. Use it intentionally for alternate submission flows, not as a shortcut around proper validation.

### 21. How does the `enterkeyhint` attribute improve mobile UX, and what are the available values?

**Answer:** `enterkeyhint` customizes the label on the Enter key of mobile virtual keyboards to match the action context, improving clarity and UX. Values include `enter` (default), `done` (close keyboard), `go` (navigate/submit), `next` (move to next field), `previous`, `search` (perform search), and `send` (send message). Use `search` on search inputs, `next` on forms to guide users through fields, and `done` on the last field to close the keyboard—these visual hints significantly improve mobile form completion rates.

### 22. What is the security risk of using `<iframe>` without `sandbox`, and how does `allow-same-origin` impact security?

**Answer:** Without `sandbox`, an iframe has full capabilities including executing scripts, accessing cookies, and potentially accessing the parent window if same-origin. Adding `allow-same-origin` to a sandboxed iframe that also has `allow-scripts` is dangerous because the iframe can remove its own sandbox attribute via JavaScript, effectively bypassing all restrictions. For untrusted content, use `sandbox` without `allow-same-origin`, or if you need same-origin, don't include `allow-scripts`.

### 23. Explain the difference between `<dialog>` with `show()` versus `showModal()`, and the importance of the `::backdrop` pseudo-element.

**Answer:** `show()` displays the dialog as a regular element without trapping focus, allowing interaction with the rest of the page. `showModal()` creates a modal dialog with a `::backdrop` overlay that blocks interaction with the rest of the page, traps focus within the dialog, and can be closed with the Esc key. The `::backdrop` pseudo-element can be styled to create overlays. Always use `showModal()` for dialogs requiring user attention, and implement proper focus management and keyboard accessibility.

### 24. How does the `inert` attribute affect an element and its descendants?

**Answer:** The `inert` attribute makes an element and all its descendants non-interactive—they can't receive focus, clicks, or selection, and are ignored by assistive technologies. It's useful for temporarily disabling sections of the page (like content behind a modal) without removing them from the DOM or managing individual element states. Unlike `disabled`, which only works on form elements, `inert` works on any element and properly handles accessibility by removing the entire subtree from the accessibility tree.

### 25. What is the purpose of `<link rel="modulepreload">`, and how does it differ from regular `<link rel="preload">`?

**Answer:** `rel="modulepreload"` is specifically for ES modules, fetching the module and its entire dependency tree efficiently. Unlike `rel="preload" as="script"`, which only fetches a single file, `modulepreload` parses the module to discover imports and preloads those too, and stores the result in the module cache. It also applies CORS by default. Use it for critical JavaScript modules in modern applications to reduce waterfall requests and improve startup performance.

### 26. How do `<link rel="prefetch">` and `<link rel="prerender">` differ in browser behavior and resource usage?

**Answer:** `prefetch` downloads resources at low priority during idle time for likely future navigations but doesn't process them. `prerender` (deprecated but replaced by Speculation Rules API) would fully load and render the page invisibly, consuming significant memory and CPU. `prefetch` is safe for loading next-page resources; prerendering should be used extremely sparingly due to resource costs. Modern approaches use Navigation Preload API or Speculation Rules API with `prefetch`/`prerender` rules for more controlled predictive loading.

### 27. What is the difference between `rel="nofollow"`, `rel="ugc"`, and `rel="sponsored"` on links?

**Answer:** These `rel` attributes provide hints to search engines about link trust and purpose. `nofollow` indicates the link shouldn't pass ranking credit (general distrust). `ugc` (user-generated content) identifies links from untrusted sources like comments or forums. `sponsored` marks paid placements or advertising links. Using appropriate attributes helps search engines understand your site's link structure and avoids penalties for unnatural link patterns. You can combine them: `rel="nofollow ugc"` for user-submitted links.

### 28. Explain how `<meta name="viewport">` affects page rendering and what `width=device-width, initial-scale=1` means.

**Answer:** The viewport meta tag controls how mobile browsers render and scale pages. Without it, mobile browsers assume desktop layouts (~980px) and zoom out. `width=device-width` sets the viewport width to match the device's screen width in CSS pixels. `initial-scale=1` prevents auto-zoom and sets 1 CSS pixel = 1 device-independent pixel. Together, they enable responsive design. Avoid `user-scalable=no` or `maximum-scale=1` as these prevent accessibility zoom and violate WCAG guidelines.

### 29. What is the purpose of the `blocking="render"` attribute on `<link>` and `<script>` elements?

**Answer:** The `blocking` attribute explicitly marks resources as render-blocking, giving developers control over what the browser should wait for before displaying content. The default value `blocking="render"` blocks rendering until the resource loads. This is useful for ensuring critical CSS or fonts load before initial paint, preventing Flash of Unstyled Content (FOUC). You can remove render-blocking behavior by omitting the attribute or handling resources differently (async, defer), but use it intentionally for truly critical resources.

### 30. How does `<form method="dialog">` work with the `<dialog>` element, and what is its practical use?

**Answer:** When a form inside a `<dialog>` has `method="dialog"`, submitting the form closes the dialog instead of making an HTTP request. The submitting button's `value` becomes the dialog's return value (accessible via `dialog.returnValue`). This is useful for confirmation dialogs, modal forms, or selection interfaces where you want to capture user choice without page navigation. Combined with the `formmethod="dialog"` attribute on individual buttons, you can have some buttons close the dialog while others submit normally.

### 31. What is the security implication of using `target="_blank"` with `download` attribute, and how should downloads be handled securely?

**Answer:** The `download` attribute forces files to download rather than navigate, but combined with `target="_blank"` on untrusted URLs, it can still create `window.opener` access issues. Additionally, downloading files from user-controlled URLs risks malware distribution or phishing. Always add `rel="noopener"`, validate file types and sources server-side, implement Content-Security-Policy headers, use `Content-Disposition: attachment` in HTTP headers, and consider using blob URLs with verified content for sensitive downloads.

### 32. Explain the difference between `<input type="search">` and `<input type="text">` beyond styling.

**Answer:** Beyond the different appearance (rounded corners, clear button on many browsers), `type="search"` fields don't record history in form autocomplete by default, making them better for privacy-sensitive searches. They also trigger the search keyboard on mobile devices (with a "search" button instead of "enter"). The `incremental` attribute (WebKit) fires input events as you type. For accessibility, they're announced differently by screen readers. Use `type="search"` specifically for search inputs to provide appropriate UX signals.

### 33. How does `<link rel="canonical">` affect SEO, and what happens when there are multiple canonical tags?

**Answer:** The canonical tag tells search engines which URL is the preferred version when duplicate content exists across multiple URLs (pagination, tracking parameters, HTTP/HTTPS variants). Search engines consolidate ranking signals to the canonical URL. If multiple canonical tags exist, search engines choose one (usually the first or most authoritative) or may ignore them entirely. Self-referencing canonicals are good practice even on original pages to prevent parameter pollution. Always use absolute URLs and ensure the canonical URL is actually accessible.

### 34. What is the purpose of `<input type="hidden">`, and what are its security considerations?

**Answer:** Hidden inputs store data that's submitted with forms but not visible to users, commonly used for CSRF tokens, IDs, or state information. However, they're not secure—users can view and modify them via DevTools or by intercepting requests. Never store sensitive data or rely on them for authentication. Always validate hidden input values server-side, use them only for non-sensitive reference data, and employ proper CSRF protection separately. For security-critical data, use server-side sessions instead.

### 35. Explain how `<meta name="theme-color">` works and its impact on user experience.

**Answer:** The theme-color meta tag sets the color of the browser UI (address bar, task switcher) on mobile browsers and PWAs, creating a more immersive app-like experience. You can use media queries to set different colors for light/dark mode: `<meta name="theme-color" content="#fff" media="(prefers-color-scheme: light)">`. The color should match your site's header or dominant brand color. This improves perceived performance and polish but only works on supporting browsers (primarily mobile Chrome, Safari, Edge).

### 36. What is the difference between `role="button"` on a `<div>` versus using an actual `<button>` element?

**Answer:** Using `role="button"` on a div provides the semantic button role to screen readers but doesn't add keyboard functionality—you must manually implement Enter and Space key handling, focus management, and disabled states. A native `<button>` includes all this functionality automatically, is focusable by default, works with form submission, and provides consistent cross-browser behavior. Only use `role="button"` on non-button elements when you have no alternative and then implement complete keyboard and focus support.

### 37. How do `<input type="date">`, `<input type="datetime-local">`, and `<input type="time">` handle time zones?

**Answer:** These inputs have no time zone information—they represent local times in the user's system time zone. `datetime-local` appears to include time but doesn't store or transmit zone data. This causes issues when users in different zones submit forms. For true time zone handling, use `<input type="datetime-local">` with a separate time zone selector, or use JavaScript libraries to convert to UTC before submission. Server-side, always store times in UTC and convert based on user's known time zone.

### 38. What is the purpose of `<link rel="alternate">` with `hreflang`, and how does it affect international SEO?

**Answer:** `rel="alternate" hreflang` tells search engines about translated or regional versions of pages, helping serve the right language version to users. Each page should link to all its variants including itself. Format: `<link rel="alternate" hreflang="es-MX" href="https://example.com/es-mx/page">`. Use ISO 639-1 language codes and optional ISO 3166-1 Alpha 2 country codes. Include `hreflang="x-default"` for a default catch-all page. Incorrect implementation can hurt SEO—ensure reciprocal links exist on all language versions.

### 39. Explain the security risks of `<meta http-equiv="refresh">` and why it's problematic for accessibility.

**Answer:** Meta refresh redirects or reloads pages after a delay, which is problematic for accessibility (users lose context, screen readers can't navigate properly, violates WCAG Success Criterion 2.2.1). It's also a security risk because attackers can use it for phishing (quick redirects to malicious sites) or can inject it via XSS to cause denial-of-service through infinite reload loops. Use HTTP 301/302 redirects for permanent/temporary redirects, and JavaScript with user consent for delayed actions.

### 40. What is the difference between `<abbr>`, `<acronym>`, and when should you use the `title` attribute?

**Answer:** `<abbr>` is the semantic element for abbreviations and acronyms (note: `<acronym>` is obsolete in HTML5). The `title` attribute on `<abbr>` provides the full expansion. However, `title` has accessibility issues—it's not reliably exposed to screen readers and isn't keyboard-accessible. Better practice: spell out the full term on first use followed by abbreviation in parentheses, then use `<abbr>` for subsequent instances. For critical expansions, use `aria-label` on the `<abbr>` element instead of `title`.

### 41. How does the `importance` attribute (now `fetchpriority`) affect resource loading, and when should you use it?

**Answer:** `fetchpriority` (formerly `importance`) hints to browsers which resources are critical, with values `high`, `low`, or `auto`. Use `fetchpriority="high"` on above-the-fold images or critical CSS to prioritize their download, and `fetchpriority="low"` on below-the-fold or less important resources. However, overuse negates its purpose—use it sparingly only on resources that truly impact Largest Contentful Paint (LCP). Browsers already have good prioritization heuristics; this attribute is for fine-tuning specific bottlenecks identified through performance profiling.

### 42. What is the purpose of `<input type="color">`, and what are its limitations across browsers?

**Answer:** `type="color"` provides a native color picker UI, returning hex values. However, it has significant limitations: no alpha/transparency support (only RGB hex), no recent color history in some browsers, inconsistent UI across platforms, and no native support for color palettes or custom value entry. For professional applications requiring alpha channels, palettes, or precise input, use JavaScript color picker libraries. For simple use cases where basic colors suffice, the native picker provides good UX without external dependencies.

### 43. Explain how `<textarea>` handles `maxlength`, `minlength`, and `wrap` attributes.

**Answer:** `maxlength` restricts character count (preventing further input), `minlength` sets minimum characters for validation (not preventing submission attempts, but triggering validation messages). The `wrap` attribute controls how line breaks are submitted: `wrap="soft"` (default) doesn't send line breaks in the value, while `wrap="hard"` includes them (requires `cols` attribute). For visual line breaks without `<br>` in submitted data, use `soft`. For preserving formatting (like poetry or code), use `hard` or handle formatting server-side from `soft` data.

### 44. What are the security implications of `<embed>`, `<object>`, and when should you use them?

**Answer:** `<embed>` and `<object>` can embed arbitrary file types including plugins (Flash, PDF), creating security risks—plugins may have vulnerabilities, can execute code, and access local resources. Modern best practice avoids them: use native HTML5 video/audio, embed PDFs via `<iframe>` with sandboxing, or use JavaScript libraries for document viewing. If necessary, always implement Content-Security-Policy headers to restrict sources, sandbox iframes containing these elements, and validate MIME types server-side.

### 45. How does `<input type="file" accept>` work, and why shouldn't you rely on it for security?

**Answer:** The `accept` attribute filters which files appear in the file picker dialog (by MIME type or extension like `accept=".jpg,.png"` or `accept="image/*"`). However, it's purely client-side convenience—users can bypass it by switching the picker to "All Files" or by sending requests directly. Never rely on `accept` for security or validation. Always validate file types, sizes, and contents server-side by checking magic bytes (file signatures), not just extensions or MIME types, which can be spoofed.

### 46. What is the purpose of `<meta name="robots">`, and how does it differ from `robots.txt`?

**Answer:** `<meta name="robots" content="noindex,nofollow">` controls how search engines index and follow links on a specific page. `robots.txt` controls crawler access to URLs before they're fetched. Meta robots take precedence for indexed pages but require the page to be crawled first. Use `robots.txt` to block resource-intensive crawling or private sections entirely; use meta tags for public pages you don't want indexed. Combining both provides defense in depth, but remember meta tags won't prevent determined users from accessing content.

### 47. Explain the difference between `<output>` and `<input readonly>` for displaying calculated values.

**Answer:** `<output>` is semantically designed for displaying calculation results or form action outcomes, typically populated via JavaScript. It's implicitly live region for screen readers and can use the `for` attribute to reference inputs used in calculation, establishing semantic relationships. `<input readonly>` is focusable, included in form submissions, and part of the form's validation context. Use `<output>` for displaying derived values not submitted (totals, conversions); use `<input readonly>` for pre-filled data that should be submitted but not edited.

### 48. What is the impact of using `<table role="presentation">` versus properly structured data tables?

**Answer:** `role="presentation"` (or `role="none"`) removes table semantics from the accessibility tree, treating it as a layout hack. This should only be used for legacy layouts, never for actual tabular data. Properly structured data tables with `<thead>`, `<tbody>`, `<th scope="col/row">`, and `<caption>` are essential for screen reader users to navigate and understand data relationships. Misusing `role="presentation"` on data tables destroys accessibility, while using tables for layout (even with the role) is outdated—use CSS Grid/Flexbox instead.

### 49. How does `<input type="range">` handle accessibility, and what's required for proper implementation?

**Answer:** Range inputs lack visible value indicators and have poor default accessibility—screen readers announce position but not context. For proper implementation, always include: a `<label>`, `min`/`max`/`step` attributes, `aria-valuetext` to announce user-friendly values (e.g., "$50" not "50"), a connected `<output>` element displaying current value, and consider `list` attribute with `<datalist>` for tick marks. For critical applications, consider custom accessible sliders with proper ARIA labels and keyboard support.

### 50. What is the purpose and risk of `<meta http-equiv="Content-Security-Policy">`?

**Answer:** This meta tag allows implementing CSP without server configuration, useful for static sites or when you can't control headers. However, it's less secure than HTTP headers—it can't protect against certain attacks that occur during HTML parsing before the meta tag is reached, can't use frame-ancestors directive, and can be injected or modified via XSS if not in a secured template. Always prefer HTTP headers for CSP; use meta tags only as a fallback or for additional layered security on pages where header control is impossible.



## Advanced CSS Interview Questions

### 1. Your layout shifts on page load due to images loading — what's the CSS solution to prevent cumulative layout shift (CLS)?

**Answer:** Use the `aspect-ratio` property on image containers or directly on `<img>` tags to reserve space before the image loads: `img { aspect-ratio: 16/9; width: 100%; height: auto; }`. Alternatively, set explicit `width` and `height` attributes in HTML which modern browsers use to calculate aspect ratio automatically. For background images, use `padding-bottom` percentage trick on the container. These techniques ensure the browser reserves correct space during initial render, preventing layout shifts.

### 2. Two elements with z-index values of 100 and 10 overlap, but the element with z-index: 10 appears on top. Why, and how do you diagnose this?

**Answer:** This occurs due to stacking context issues. The element with `z-index: 10` likely belongs to a different (higher) stacking context than the one with `z-index: 100`. Stacking contexts are created by positioned elements with z-index, `opacity < 1`, `transform`, `filter`, `will-change`, or other properties. To diagnose, inspect parent elements for stacking context triggers, and use browser DevTools' 3D view (Firefox) or Layers panel (Chrome). Fix by ensuring both elements are in the same stacking context or adjusting parent stacking contexts.

### 3. Explain the difference between `width: 100%`, `width: 100vw`, and `width: 100dvw` in terms of behavior and when to use each.

**Answer:** `width: 100%` is relative to the parent element's content box (excluding padding unless `box-sizing: border-box` on parent). `width: 100vw` is 100% of the viewport width, potentially causing horizontal scrollbars if scrollbars consume space (Windows) or when padding exists on body. `width: 100dvw` (dynamic viewport width) accounts for dynamic toolbars on mobile browsers that hide/show during scroll. Use `100%` for contained layouts, `100vw` for full-width overlays (with care), and `100dvw` for mobile-first full-viewport sections that should respond to toolbar changes.

### 4. A flexbox container has three items with `flex: 1`, but one item is visibly wider than the others despite identical flex values. What causes this and how do you fix it?

**Answer:** This occurs because `flex: 1` is shorthand for `flex: 1 1 0%`, but the items' min-content size (longest word, image, or intrinsic content) acts as a minimum width. If one item contains wider content (long unbreakable text, image), it won't shrink below its min-content size. Fix by setting `min-width: 0` on flex items to allow shrinking below content size, or use `overflow: hidden` which also establishes a new BFC and resets min-width behavior.

### 5. Your CSS animation causes battery drain on mobile devices. What properties should you animate, and which should you avoid?

**Answer:** Only animate `transform` and `opacity` as these trigger compositing and run on the GPU without triggering layout or paint. Avoid animating `width`, `height`, `top`, `left`, `margin`, `padding`, or any property that triggers reflow/repaint. These force the browser to recalculate layout and repaint on every frame, causing CPU spikes and battery drain. Use `will-change: transform` sparingly before animations to promote elements to their own compositing layer, but remove it after animation completes to free memory.

### 6. Scrolling on your mobile site is janky. What CSS properties could be causing this, and how do you identify them?

**Answer:** Jank is typically caused by properties triggering layout/paint during scroll: fixed positioning with complex children, `background-attachment: fixed`, excessive shadows/filters, animations on scroll, or lack of hardware acceleration. Use Chrome DevTools Performance panel to record scroll and check for long frames, excessive paint operations, or layout thrashing. Fix by using `transform: translateZ(0)` or `will-change` to create compositing layers, simplifying visual effects, using `content-visibility: auto` for long lists, and replacing fixed backgrounds with transforms.

### 7. Explain the difference between `contain: layout`, `contain: paint`, and `contain: strict`, including practical use cases for each.

**Answer:** `contain: layout` isolates the element's internal layout from external layout (prevents internal changes affecting ancestors), useful for widgets or components. `contain: paint` ensures descendants can't paint outside boundaries (like `overflow: hidden` but creates stacking context), useful for cards or panels. `contain: strict` combines layout, paint, and size containment, telling the browser the element's size won't depend on descendants—useful for virtualized lists or off-screen content. Each optimization helps browser skip recalculation work for better performance.

### 8. You have a CSS Grid with `grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))`. Items overflow instead of wrapping when viewport is very narrow. Why and how do you fix it?

**Answer:** The `minmax(250px, 1fr)` function sets a hard minimum of 250px, so when the viewport is narrower than 250px, items can't shrink further and overflow. The `auto-fit` creates zero-width columns when items don't fit. Fix by using `minmax(min(250px, 100%), 1fr)` which makes the minimum responsive—below 250px, items shrink to 100% of container width. Alternatively, use `grid-template-columns: repeat(auto-fill, minmax(250px, 1fr))` with proper container constraints.

### 9. What is a Block Formatting Context (BFC), how is it created, and what are three practical problems it solves?

**Answer:** A BFC is an isolated layout region where floats, margins, and positioning are contained. Created by: `overflow: hidden/auto/scroll`, `display: flow-root`, `float: left/right`, `position: absolute/fixed`, flexbox/grid items, or `contain: layout/paint`. It solves: (1) containing floats without clearfix hacks, (2) preventing margin collapse between parent and children, (3) preventing content wrapping around external floats. `display: flow-root` is the modern semantic way to create a BFC purely for layout containment.

### 10. Your `position: sticky` element isn't sticking. What are five possible causes and how do you debug each?

**Answer:** (1) Parent has `overflow: hidden/auto/scroll`—sticky requires overflow visible on ancestors. (2) No threshold set—need `top`, `bottom`, `left`, or `right` value. (3) Sticky container isn't tall enough—element needs room to scroll within container. (4) Parent has `height: 100%` chain broken—sticky positioning requires a defined scroll container. (5) Stacking context issues—z-index may position it behind other content. Debug using computed styles panel, checking parent overflow values, ensuring container height exceeds viewport, and validating position thresholds.

### 11. Explain the cascade layers feature (`@layer`) and when you would use it over traditional specificity management.

**Answer:** `@layer` allows explicit ordering of CSS rule precedence independent of specificity or source order. Layers declared first have lowest priority: `@layer base, components, utilities;`. Rules in utilities layer always override components, even with lower specificity. This solves the specificity wars problem in large codebases, making framework integration cleaner (put frameworks in lower layers), and allows easy overrides without !important. Use it for design systems, CSS architecture, or when integrating third-party styles where you need predictable override patterns without specificity hacks.

### 12. You need a responsive font size between 16px and 24px based on viewport width. Compare `clamp()`, `calc() + vw`, and `min()/max()` approaches.

**Answer:** `clamp(16px, 4vw, 24px)` is cleanest—sets minimum 16px, scales at 4vw, caps at 24px in one declaration. `font-size: calc(16px + (24 - 16) * ((100vw - 320px) / (1200 - 320)))` offers precise control over breakpoint range but is verbose and less readable. `min(max(16px, 4vw), 24px)` is equivalent to clamp but nested. Use `clamp()` for readability and browser optimization; use `calc()` when you need exact breakpoint mapping; avoid nested `min/max` as it's harder to maintain than clamp.

### 13. Your CSS custom properties aren't inheriting as expected in a component. Explain the scoping rules and how Shadow DOM affects them.

**Answer:** CSS custom properties follow normal inheritance rules—defined on an element, available to descendants. In Shadow DOM, custom properties penetrate the shadow boundary (inherit through) but regular CSS rules don't. This is by design for theming. If properties aren't inheriting: (1) check if they're defined on `:root` or appropriate ancestor, (2) verify no local redefinition shadows them, (3) confirm you're not trying to inherit non-inherited properties. For Shadow DOM components, define theme variables on `:host` or document root, and reference them inside shadow styles.

### 14. An element has `opacity: 0.99` applied for a fade effect, and suddenly child z-index stacking breaks. What happened and how do you fix it?

**Answer:** `opacity` values less than 1 create a new stacking context, isolating all children's z-index values within it. Children can no longer stack relative to external elements—only relative to siblings within the stacking context. This breaks previous z-index arrangements that relied on document-level stacking. Fix by: (1) restructuring DOM so elements needing different stacking aren't in the opacity element, (2) applying opacity to pseudo-elements instead of parent, (3) using `visibility` or `display` transitions if appropriate, or (4) accepting the stacking context and adjusting child z-indexes accordingly.

### 15. Explain the difference between `flex-basis: 0`, `flex-basis: auto`, and `flex-basis: content`, including impact on flex shrinking and growing.

**Answer:** `flex-basis: auto` uses the item's width/height or content size as the starting point before growing/shrinking. `flex-basis: 0` ignores content size, distributes space purely based on flex-grow ratios (e.g., `flex: 1` creates equal widths regardless of content). `flex-basis: content` (newer) uses the max-content size, sizing based on content without wrapping. For equal-width columns despite varying content, use `flex: 1 1 0%`. For proportional sizing respecting content, use `flex: 1 1 auto`. The basis determines how available space is distributed.

### 16. You're implementing dark mode with CSS custom properties. How do you handle the flash of unstyled content (FOUC) when theme loads?

**Answer:** Prevent FOUC by: (1) inlining critical theme CSS or properties in `<head>` before body renders, (2) setting theme class on `<html>` tag via blocking script in `<head>` that reads localStorage/system preference before render, (3) using `color-scheme` meta tag for instant browser UI adaptation, (4) applying `transition: none !important` temporarily via class during initial load to prevent visible theme transitions. Never rely on JavaScript after page load—theme must be set synchronously during HTML parsing to avoid visible flash.

### 17. Your absolutely positioned element is positioning relative to an unexpected ancestor. Explain the containing block rules for positioned elements.

**Answer:** Absolutely positioned elements use the nearest positioned ancestor (position: relative/absolute/fixed/sticky) as their containing block, not their DOM parent. If none exists, they position relative to the initial containing block (viewport/html). For `position: fixed`, containing block is always viewport unless an ancestor has `transform`, `perspective`, `filter`, or `will-change` on these properties—then that ancestor becomes the containing block. Debug by inspecting computed position values and checking ancestors for positioning or transform properties that create new containing blocks.

### 18. Compare `object-fit: cover`, `object-fit: contain`, and `object-fit: fill` for images. When does each cause layout issues?

**Answer:** `cover` scales image to fill container while maintaining aspect ratio, cropping excess—useful for thumbnails but may cut important content. `contain` fits entire image within container maintaining aspect ratio, potentially leaving gaps—safe but may waste space. `fill` stretches image to fill container, distorting aspect ratio—rarely desirable. Layout issues: all require explicit container dimensions (width/height). Without dimensions, containers collapse or behave unexpectedly. Always set container size and use `object-position` to control crop/alignment. For responsive images, combine with aspect-ratio on container.

### 19. You have a grid with `grid-template-columns: 1fr 2fr 1fr`, but columns don't follow the 1:2:1 ratio. What factors affect fr unit distribution?

**Answer:** `fr` units distribute available space after fixed sizes, but respect content min-content size by default. If the 2fr column contains wide content (long word, image), it won't shrink below min-content, breaking the ratio. Also, `grid-auto-flow: dense` can affect perceived sizing. Fix by: (1) setting `min-width: 0` on grid items to allow shrinking below content, (2) using `minmax(0, 2fr)` instead of just `2fr` to explicitly allow zero minimum, (3) applying `overflow: hidden` to items, or (4) using fixed sizes for predictable columns: `grid-template-columns: minmax(0, 1fr) minmax(0, 2fr) minmax(0, 1fr)`.

### 20. Explain when and why you would use `will-change`, and what the performance risks are if misused.

**Answer:** `will-change` hints to browsers which properties will animate, allowing preemptive optimization (creating compositing layers, allocating GPU memory). Use it: (1) just before expensive animations/transitions on `transform`/`opacity`, (2) on scroll containers with many children, (3) for elements that frequently change. Risks: creates layers consuming GPU memory, can cause more harm if applied to many elements simultaneously, wastes resources if element never changes. Always remove it after animation completes (`transitionend` event), never set it globally or on too many elements, and only use for properties that benefit from layerization.

### 21. A text element has `white-space: nowrap`, but text still wraps. What CSS properties on the element or parents could cause this?

**Answer:** Despite `nowrap`, text wraps if: (1) parent has explicit `width` smaller than text, forcing overflow behavior—need `overflow: hidden/scroll/auto` to see effect, (2) `word-break: break-all` or `overflow-wrap: anywhere` override the nowrap intent, (3) element is a flex or grid item with default `min-width: auto` which doesn't respect nowrap—add `min-width: 0`, (4) `width: 100%` on element conflicts with nowrap. Debug by checking computed width values, overflow settings, and flex/grid item behaviors. Ensure container width accommodates text or handle overflow explicitly.

### 22. What's the difference between `visibility: hidden`, `opacity: 0`, and `display: none` regarding layout, accessibility, and events?

**Answer:** `display: none` removes element from layout (no space occupied), accessibility tree (screen readers ignore), and event handling (no clicks). `visibility: hidden` maintains layout space, removes from accessibility tree, and disables events but children can override with `visibility: visible`. `opacity: 0` maintains layout and events (clickable), and remains in accessibility tree (announced by screen readers). Use `display: none` for truly hidden content, `visibility: hidden` for space-preserving hiding, and `opacity: 0` for fade animations where interactive states need to remain. For a11y hiding, use `aria-hidden="true"` with `display: none`.

### 23. Your font loads late, causing a flash of invisible or unstyled text. Explain `font-display` values and when to use each.

**Answer:** `font-display: swap` shows fallback immediately then swaps when custom font loads (FOUT—Flash of Unstyled Text)—best for body text prioritizing readability. `auto` lets browser decide (usually similar to block). `block` hides text up to 3s then swaps (FOIT—Flash of Invisible Text)—risky for performance. `fallback` has short block period (~100ms) then shows fallback, swapping only if font loads quickly (~3s)—balanced approach. `optional` shows fallback immediately and only uses custom font if cached—prioritizes performance, good for slow connections. For critical text, use `swap`; for optional decorative fonts, use `optional`.

### 24. Explain the stacking order rules within a stacking context, considering positioned elements, floats, and z-index.

**Answer:** Within a stacking context (bottom to top): (1) background/borders of context root, (2) positioned elements with negative z-index, (3) non-positioned block-level descendants in source order, (4) non-positioned floats, (5) non-positioned inline descendants, (6) positioned elements with `z-index: auto` or `z-index: 0`, (7) positioned elements with positive z-index (higher values on top). Only positioned elements participate in z-index stacking; floats and normal flow elements always render below positioned elements regardless of z-index. Understanding this resolves 90% of stacking issues.

### 25. You have a sidebar with `position: sticky` and a main content area. The sidebar doesn't span the full viewport height. How do you fix this with CSS Grid or Flexbox?

**Answer:** With Grid: `display: grid; grid-template-columns: 250px 1fr; grid-template-rows: 100vh;` on container forces full height. Sidebar gets `position: sticky; top: 0; align-self: start;` to stick within its grid cell. With Flexbox: container gets `display: flex; min-height: 100vh;`, sidebar gets `position: sticky; top: 0; align-self: flex-start;`. Key insight: sticky elements need a tall scroll container—without explicit height, the container is only as tall as content. Alternative: use `height: 100vh; overflow-y: auto;` on a parent wrapper to create scrolling context.

### 26. Compare margin collapse in normal flow versus flexbox versus grid. When does margin collapse not occur?

**Answer:** Normal flow: vertical margins collapse between adjacent siblings and between parent and first/last child if no border/padding separates them. Flexbox/Grid: margins never collapse—flex and grid items are in different formatting contexts. Margins also don't collapse: (1) inside BFC elements, (2) with floated elements, (3) with absolutely positioned elements, (4) with inline-block elements, (5) when parent has border, padding, or creates BFC. To prevent margin collapse without layout changes, use padding instead, add transparent borders, or use `display: flow-root` on parent.

### 27. You're animating height from 0 to auto but the animation doesn't work. What are three CSS-based solutions?

**Answer:** (1) Animate `max-height` to a value larger than expected content height: `transition: max-height 0.3s; max-height: 0; &.open { max-height: 500px; }`—simple but causes timing issues if max-height is much larger than actual. (2) Use grid with `grid-template-rows: 0fr` to `1fr`—modern, smooth, but requires wrapper. (3) Use scale transforms: `transform: scaleY(0); transform-origin: top;` to `scaleY(1)`—smooth but distorts content during animation. Best modern approach: Grid track animation with `calc-size(auto)` in cutting-edge browsers, or JavaScript to measure and set explicit heights.

### 28. Explain the difference between logical properties (`margin-inline-start`) and physical properties (`margin-left`), including RTL implications.

**Answer:** Physical properties are direction-agnostic: `margin-left` always means left regardless of reading direction. Logical properties adapt to writing mode: `margin-inline-start` means left in LTR languages, right in RTL languages (Arabic, Hebrew). Similarly, `padding-block-start` is top in horizontal writing, left in vertical. Using logical properties makes layouts automatically adapt to `dir="rtl"` or different writing modes without additional CSS. For internationalized sites, prefer logical properties: `inline` (horizontal axis), `block` (vertical axis), `start`/`end` instead of `left`/`right`/`top`/`bottom`.

### 29. Your pseudo-element (`::before` or `::after`) isn't appearing. What are the five essential requirements?

**Answer:** (1) Must have `content` property, even if empty (`content: ""`). (2) Parent must not be a replaced element (img, input, video can't have pseudo-elements). (3) Must have `display` other than `none` (default is inline). (4) Check z-index/stacking context—may be behind parent. (5) Verify parent has dimensions—if parent is 0x0, pseudo-element may be invisible even if it exists. Debug using DevTools elements inspector which shows pseudo-elements, check computed styles for content property, verify display value, and ensure parent layout accommodates the pseudo-element.

### 30. Describe three different techniques for creating equal-height columns in a layout, comparing their use cases.

**Answer:** (1) Flexbox: `display: flex` on container, children auto-stretch to equal height—simplest, works for most cases, handles unknown content. (2) CSS Grid: `display: grid; grid-auto-flow: column; grid-auto-columns: 1fr;`—best for explicit column structures, handles complex layouts. (3) Table display: `display: table` on container, `display: table-cell` on columns—legacy approach, works everywhere but less semantic. For modern layouts, use Flexbox for flexible content-driven columns or Grid for structured layouts. Only use table display for extremely old browser support.

### 31. You have overlapping elements with `mix-blend-mode: multiply`. One element has `opacity: 0.5`. Why does the blend mode stop working?

**Answer:** `opacity < 1` creates a new stacking context, which isolates blend modes. Blend modes only work within their stacking context and cannot blend across stacking context boundaries. When opacity creates a stacking context, the element's blending is composited first within its context, then the entire context is composited with opacity. Fix by: (1) removing opacity and using `rgba()` colors instead for transparency, (2) restructuring DOM so blend mode elements are siblings without opacity parents, (3) applying opacity to the final composited result if possible, or (4) accepting the limitation and adjusting the design.

### 32. Explain how `transform-style: preserve-3d` works and a practical scenario where it's essential.

**Answer:** By default, transformed elements flatten children into the element's plane (`transform-style: flat`). `preserve-3d` maintains 3D positioning of children, allowing them to exist at different z-depths. Essential for: (1) 3D card flips where front and back have different z-positions, (2) 3D carousels with items rotated around a central axis, (3) nested 3D transformations like folding animations. Without `preserve-3d` on parents, children would render flat regardless of their `translateZ()` or `rotateX/Y()` values. Note: it creates stacking context and can cause issues with overflow, filters, or blend modes on the same element.

### 33. Your `:focus-visible` styles aren't applying when clicking buttons with a mouse, but work with keyboard. Explain this behavior and accessibility implications.

**Answer:** `:focus-visible` is specifically designed to show focus indicators only for keyboard navigation (or when browser heuristics determine the user needs visible focus), hiding them for mouse/touch interactions. This is intentional UX behavior—mouse users can see where they clicked, but keyboard users need visible focus indication to know their position. Always style `:focus-visible` for accessibility compliance (WCAG 2.4.7), and don't override it with `:focus { outline: none }` without providing alternative visible focus indicators. Use `:focus-within` for parent containers needing focus awareness.

### 34. You're using `backdrop-filter: blur(10px)` for glassmorphism, but performance is poor. What's the cause and how do you optimize?

**Answer:** `backdrop-filter` forces the browser to re-render all content behind the element on every frame, which is expensive. Causes: (1) large blur radius (higher = more expensive), (2) many overlapping backdrop-filter elements, (3) animated backdrop-filter values, (4) complex content behind filter. Optimize by: (1) reducing blur radius to 5-8px, (2) limiting number of glassmorphic elements, (3) avoiding animation of backdrop-filter itself, (4) using `will-change: backdrop-filter` on scroll containers, (5) considering simpler alternatives like solid colors with opacity, or (6) using static blurred background images instead of live backdrop-filter.

### 35. Explain the difference between `auto`, `min-content`, `max-content`, and `fit-content` for width values, with practical examples.

**Answer:** `auto` uses available space respecting margins (default block behavior). `min-content` shrinks to the smallest possible width without overflow (longest word/element width). `max-content` expands to content width without wrapping. `fit-content` is essentially `min(max-content, available-space)`—expands up to content but respects container. Use cases: `min-content` for sizing to longest word in buttons, `max-content` for dropdown menus that shouldn't wrap, `fit-content` for centered elements that grow with content but don't exceed container, `auto` for normal layout flow. Critical for intrinsic sizing in Grid and Flex contexts.

### 36. Your CSS Grid layout has unexpected gaps. You haven't set `gap` property. What could be causing spacing between items?

**Answer:** Whitespace (newlines/spaces) in HTML source creates text nodes, but Grid ignores these—not the cause. Likely causes: (1) margins on grid items (margins don't collapse in Grid), (2) default browser styles on specific elements (ul/li have default margins), (3) inherited padding/margin from global styles, (4) `justify-content` or `align-content` distributing extra space, (5) explicit track sizes with leftover space being distributed. Debug using DevTools grid overlay, check computed margins on items, inspect grid container's justify/align properties, and verify track sizing doesn't create extra space.

### 37. Compare `overflow: auto`, `overflow: scroll`, and `overflow: overlay` in terms of scrollbar behavior and layout impact.

**Answer:** `overflow: auto` shows scrollbars only when content overflows, adding them dynamically (can cause layout shift as scrollbars take space). `overflow: scroll` always shows scrollbars even if content fits, reserving space (prevents layout shift but wastes space). `overflow: overlay` (deprecated/removed) showed scrollbars overlaying content without taking layout space—best of both worlds but non-standard. Modern approach: use `scrollbar-gutter: stable` with `overflow: auto` to always reserve space for scrollbars without showing them until needed, preventing layout shifts while not wasting space.

### 38. You have a rotated element (`transform: rotate(45deg)`) that's being clipped by its parent's `overflow: hidden`. How do you prevent this?

**Answer:** Transforms happen after layout, so rotated content can extend beyond the element's layout box even though visually it appears larger. Parent's `overflow: hidden` clips based on original layout box. Solutions: (1) add padding to parent equal to expected overflow distance, (2) set `overflow: visible` on parent (or use `overflow-x: visible` if only horizontal overflow is an issue), (3) use `transform-origin` to rotate around a different point keeping content within bounds, (4) increase child's explicit width/height to accommodate rotation, or (5) restructure DOM so rotated element isn't child of overflow container.

### 39. Explain CSS containment (`contain`) and when each value (`size`, `layout`, `paint`, `style`) provides performance benefits.

**Answer:** Containment tells browsers which properties are isolated, enabling optimization. `contain: size` means element's size doesn't depend on children (browser can skip measuring children during layout). `contain: layout` isolates internal layout from external (changes inside don't trigger parent relayout). `contain: paint` ensures descendants don't render outside bounds and creates stacking context. `contain: style` isolates CSS counter and quote effects. Use `content` (layout + paint + style) for independent widgets, `strict` (all four) for off-screen virtualized content, and `inline-size` for width-only containment preserving height dynamics.

### 40. Your SVG icon in CSS (`background-image: url("data:image/svg+xml...`)`) doesn't change color with `color` property. How do you create theme-aware SVG icons in CSS?

**Answer:** Inline SVG respects `fill: currentColor` but background SVG doesn't have access to CSS properties. Solutions: (1) Use inline SVG in HTML with `fill="currentColor"` in SVG elements—inherits text color. (2) Use CSS mask: `mask-image: url(icon.svg); background-color: currentColor;` creates monochrome icon that respects color property. (3) Use multiple background images with different colored versions, switching via media queries. (4) Use CSS custom properties with embedded SVG: `url("data:image/svg+xml,<svg fill='var(--icon-color)'>")` but has encoding limitations. Mask approach is most flexible.

### 41. You're using `position: fixed` for a modal overlay, but on iOS Safari, the layout breaks when the address bar hides. Why and how do you fix it?

**Answer:** iOS Safari's viewport changes as the address bar shows/hides, making `100vh` unreliable—it doesn't account for dynamic UI. Fixed elements using `height: 100vh` resize, causing jank. Fix using: (1) new viewport units: `height: 100dvh` (dynamic vh) or `100svh` (small viewport—address bar shown), (2) JavaScript to set CSS custom property: `document.documentElement.style.setProperty('--vh', window.innerHeight/100)` then `height: calc(var(--vh) * 100)`, (3) `position: fixed; inset: 0;` which often behaves better than explicit height, or (4) for overlays, use `min-height: 100vh` with `height: 100%` allowing growth.

### 42. Explain the performance difference between `transform: translate()` and changing `top/left` properties, including what happens at the rendering layer.

**Answer:** Changing `top/left` triggers layout recalculation (reflow) because it affects document flow, then repaint, then composite—expensive. `transform: translate()` only triggers composite because transforms happen after layout/paint on the GPU as a separate layer. The browser doesn't recalculate positions of other elements. For animations: always use transforms. Performance pipeline: Layout → Paint → Composite. Layout (most expensive) recalculates geometry of all affected elements. Paint rasterizes pixels. Composite (cheapest) combines layers on GPU. Only transform and opacity skip layout/paint stages.

### 43. You have a CSS counter for numbered headings, but it resets unexpectedly. Explain counter scoping and how to fix hierarchical counters.

**Answer:** Counters are scoped to their containing element—each `counter-reset` creates a new counter scope. For nested lists or hierarchical headings, if you reset at each level, child counters are independent. For hierarchical numbering (1, 1.1, 1.2, 2, 2.1), use multiple counters: `counter-reset: section subsection; counter-increment: section;` on h2, then reference both: `content: counter(section) "." counter(subsection);`. Ensure reset happens at appropriate ancestor level. For lists, use `counter-reset: list-item` on ol, and increment on li to maintain proper nesting across multiple levels.

### 44. Your `aspect-ratio: 16/9` container has an image inside, but the image distorts or doesn't respect the ratio. What's the issue?

**Answer:** `aspect-ratio` sets the container's ratio but doesn't control children's sizing. If the image has explicit width/height, its own dimensions, or default sizing, it won't respect parent's aspect ratio. Fix by: (1) making image responsive: `img { width: 100%; height: 100%; object-fit: cover; }` to fill container while maintaining its own ratio, (2) using `object-fit: contain` to fit entirely within container, or (3) using image as background: `background: url(img.jpg); background-size: cover;`. The aspect-ratio creates the container shape; object-fit controls how content fills it.

### 45. Explain how `isolation: isolate` works and when it's useful for controlling blend modes and stacking contexts.

**Answer:** `isolation: isolate` creates a new stacking context without requiring positioning, z-index, or opacity changes. It isolates the element's content so blend modes and effects don't interact with content outside the stacking context. Use cases: (1) limiting `mix-blend-mode` effects to specific areas without affecting entire page, (2) creating clean stacking boundaries in components without using opacity tricks, (3) preventing z-index conflicts from propagating to parent contexts. Unlike other stacking context triggers, `isolation` has no side effects—no opacity changes, no transform behavior, just clean isolation.

### 46. Your `text-overflow: ellipsis` isn't working. What three CSS properties are required for ellipsis to appear?

**Answer:** Ellipsis requires: (1) `overflow: hidden` to clip overflowing text, (2) `white-space: nowrap` to prevent wrapping, (3) a constrained width—element must have a width that's smaller than content (explicit `width`, `max-width`, or flex/grid constraints). Without all three, ellipsis won't display. For multi-line ellipsis, use `-webkit-line-clamp` with `display: -webkit-box` and `-webkit-box-orient: vertical`. In flex/grid items, add `min-width: 0` to allow shrinking below content size, as default `min-width: auto` prevents ellipsis from triggering.

### 47. Explain the difference between `revert`, `revert-layer`, `initial`, `inherit`, and `unset` CSS keywords.

**Answer:** `initial` sets property to its CSS-defined default (not user-agent styles). `inherit` forces inheritance from parent even for non-inherited properties. `unset` acts as `inherit` for inherited properties, `initial` for others—undoes author styles. `revert` rolls back to user-agent stylesheet (browser defaults), skipping author styles—useful for resetting to native browser behavior. `revert-layer` (newest) rolls back to previous cascade layer, ignoring current layer's rules. Use `revert` to restore native button/form styles, `unset` for component resets, and `revert-layer` when working with `@layer` architecture.

### 48. Your modal dialog has `backdrop-filter`, but clicking the backdrop doesn't close the modal, and focus escapes. How do you implement proper modal accessibility?

**Answer:** Proper modal requires: (1) focus trap using JavaScript to cycle Tab within modal, (2) backdrop click handler checking `event.target === backdropElement` to close, (3) `aria-modal="true"` and `role="dialog"` on modal, (4) `aria-labelledby` pointing to title, (5) Esc key handler to close, (6) focus management—save last focused element, move focus to modal on open, restore on close, (7) prevent body scroll with `overflow: hidden` on body, (8) use `<dialog>` element with `showModal()` method for native behavior. Never rely only on backdrop-filter for backdrop—use separate overlay element.

### 49. You have a CSS Grid with `grid-auto-rows: minmax(100px, auto)`. Some rows are shorter than 100px. Why doesn't the minimum apply?

**Answer:** `grid-auto-rows` only affects implicitly created rows (rows beyond those defined in `grid-template-rows`). If you've defined explicit rows with `grid-template-rows: repeat(3, 1fr)` or similar, those take precedence and `grid-auto-rows` doesn't apply to them. To apply minmax to all rows: (1) use `grid-template-rows: repeat(auto-fill, minmax(100px, auto))`, (2) remove explicit `grid-template-rows` letting all rows be auto-generated, or (3) define explicit rows with the minmax: `grid-template-rows: repeat(3, minmax(100px, auto))`. Also check if items have `grid-row` spanning that affects row sizing.

### 50. Your animation has `animation-fill-mode: forwards`, but styles revert when another animation starts. Explain the cascade behavior and how to maintain styles.

**Answer:** When a new animation starts on the same element, it overrides the previous animation's fill-mode styles because animations have higher cascade priority than base styles, and later animations override earlier ones. If the new animation doesn't specify the same properties, those properties revert to non-animated states. Fix by: (1) combining animations using `animation: anim1, anim2` to run both, (2) setting final state in base CSS styles (not relying on fill-mode), (3) using CSS classes to apply final state alongside animation, (4) chaining animations with `animationend` event listener to apply styles via class, or (5) using Web Animations API with explicit persistence options for better control.


**🎉 Good luck with your interview preparation! These projects will make you stand out!**


