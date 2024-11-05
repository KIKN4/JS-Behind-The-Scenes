---
theme: seriph
background: "/js.photo.jpeg"
---

---

# Overview of the slides

<br>
🌐 An High-Level Overview of Javascript
<br>
<br>

🚀 The JavaScript Engine and Runtime
<br>
<br>

🧠 Execution Contexts and the Call Stack
<br>
<br>

🔗 Scope and The Scope Chain
<br>
<br>

🔄 Variable Environment
<br>
<br>

⚖️ Dynamic vs Static Memory
<br>

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/features/slide-scope-style
-->

<style>
h1 {
  background-color: #F0C808;
  background-image: linear-gradient(45deg, #F7DF1E 10%, #D4A017 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---

<img src="/public/js.photo2.jpg" style="height: 100%">

---

<div class="scrollable-container">

|                                                    |                             |
| -------------------------------------------------- | --------------------------- |
| <kbd>High-level </kbd>                | რესურსების მართვა ჩვენ არ გვჭირდება, Javascriopt-ის ძრავა ამას ავტომატურად აკეთებს    |
| <kbd>Garbage-collected</kbd> | მეხსიერების მართვა. ალგორითმი JavaScript ძრავაში, რომელიც ავტომატურად შლის ძველ და გამოუყენებელ ობიექტებს |
| <kbd>Interpreted or just-in-time compiled</kbd> | კოდი კომპილირდება შესრულებისას, რაც უზრუნველყოფს უფრო სწრაფ შესრულებას. |
| <kbd>Multi-paradigm</kbd>  | პროცედურული პროგრამირება, ობიექტზე ორიენტირებული პროგრამირება, ფუნქციური პროგრამირება. შეგვიძლია გამოვიყენოთ ნებისმიერი პარადიგმა, რომელიც გვსურს |
| <kbd>Prototype-based object-oriented</kbd> | ``` const arr = [1,2,3] ``` ```array.push(4)``` ```->``` ``` Array.prototype.push```|
| <kbd>First-class functions</kbd>                                    | ფუნქციები განიხილება როგორც "ცვლადები". შეგვიძლია გამოვიყენოთ ისინი სხვა ფუნქციებში ან დავაბრუნოთ სხვა ფუნქციებიდან. ```overlay.addEventListener("click", someFunctionName)```|
| <kbd>Dynamic Memory</kbd> | JavaScript-ში ცვლადებს არ ვანიჭებთ მონაცემთა ტიპებს.მეხსიერება გამოიყოფა შესრულების დროს, რაც უზრუნველყოფს უფრო მოქნილ და ეფექტურ მეხსიერების მართვას. |
| <kbd>Static Memory</kbd> |	მეხსიერება წინასწარ არის განსაზღვრული და მისი ზომა არ იცვლება პროგრამის შესრულებისას|
| <kbd>Single-threaded</kbd>  | როგორ უმკლავდება JavaScript ძრავა მრავალ ამოცანას ერთდროულად? 👉 JavaScript მუშაობს ერთი single thread-ით, ამიტომ ერთდროულად მხოლოდ ერთ ამოცანას ასრულებს |
| <kbd>Non-blocking event loop</kbd>                                    | ```Event Loop``` არის უწყვეტი პროცესი, რომელიც მართავს კოდის შესრულებას, ახორციელებს call stack-ის, microtask queue-ის და callback queue-ის მართვას, რათა უზრუნველყოს ასინქრონული ოპერაციების ეფექტური და არაბლოკირებული შესრულება JavaScript-ში|

</div>

<style>
.scrollable-container {
  max-height: 400px; /* განუსაზღვრეთ სიმაღლე */
  overflow-y: auto; /* ვერტიკალური სქროლის გააქტიურება */
}

kbd {
  font-size: 10px;
  display: inline-block;
  margin-bottom: 2px;
  margin: 0px;
}

td {
  font-size: 12px; 
  padding: 8.5px;
  margin: 0px;
}

</style>

---

<img src="/public/js.photo3.jpg" style="height: 100%; width: 100%;">

---

<img src="/public/JS.ENGINGE.png" style="height: 100%; width: 100%;">

---
layout: two-cols
---

```ts 

const name = 'Jonas';

const first = () => {
  let a = 1;
  const b = second(7, 9);
  a = a + b;
  return a;
};

function second(x, y) {
  var c = 2;
  return c;
}

const x = first();
```

::right::

```mermaid
graph TD
    GlobalContext[Global Execution Context]
```

---
layout: two-cols
---

````md magic-move {lines: true}
```ts {1}

const name = 'Jonas';

const first = () => {
  let a = 1;
  const b = second(7, 9);
  a = a + b;
  return a;
};

function second(x, y) {
  var c = 2;
  return c;
}

const x = first();
```
````

::right::

```mermaid
graph TD
    GlobalContext[Global Execution Context]
    subgraph Global[Global]
        nameVariable[name =  John]
    end
    GlobalContext -->|Creates| Global
```

---
layout: two-cols
---

````md magic-move {lines: true}
```ts {3}

const name = 'Jonas';

const first = () => {
  let a = 1;
  const b = second(7, 9);
  a = a + b;
  return a;
};

function second(x, y) {
  var c = 2;
  return c;
}

const x = first();
```
````

::right::

```mermaid
graph TD
    GlobalContext[Global Execution Context]
    subgraph Global[Global]
        nameVariable[name =  John]
        firstFN[first = function ]
    end
    GlobalContext --> Global
```

---
layout: two-cols
---

````md magic-move {lines: true}
```ts {10}

const name = 'Jonas';

const first = () => {
  let a = 1;
  const b = second(7, 9);
  a = a + b;
  return a;
};

function second(x, y) {
  var c = 2;
  return c;
}

const x = first();
```
````

::right::

```mermaid
graph TD
    GlobalContext[Global Execution Context]
    subgraph Global[Global]
        nameVariable[name =  John]
        firstFN[first = function ]
        secondFN[second = function ]
    end
    GlobalContext --> Global
```

---
layout: two-cols
---

````md magic-move {lines: true}
```ts {15}

const name = 'Jonas';

const first = () => {
  let a = 1;
  const b = second(7, 9);
  a = a + b;
  return a;
};

function second(x, y) {
  var c = 2;
  return c;
}

const x = first();
```
````

::right::

```mermaid
graph TD
    GlobalContext[Global Execution Context]
    subgraph Global[Global]
        nameVariable[name =  John]
        firstFN[first = function ]
        secondFN[second = function ]
        x[x = unknown ]
    end
    GlobalContext --> Global
```

---
layout: two-cols
---

````md magic-move {lines: true}
```ts {4-7}

const name = 'Jonas';

const first = () => {
  let a = 1;
  const b = second(7, 9);
  a = a + b;
  return a;
};

function second(x, y) {
  var c = 2;
  return c;
}

const x = first();
```
````

::right::

```mermaid
graph TD
    GlobalContext[Global Execution Context]
   
    subgraph LocalContext1[local execution context1]
        aVariable[a = 1]
        bVariable[b = unknown]
    end

    GlobalContext --->|Creates| LocalContext1
```

---
layout: two-cols
---

````md magic-move {lines: true}
```ts {11-12}

const name = 'Jonas';

const first = () => {
  let a = 1;
  const b = second(7, 9);
  a = a + b;
  return a;
};

function second(x, y) {
  var c = 2;
  return c;
}

const x = first();
```
````

::right::

```mermaid
graph TD
    GlobalContext[Global Execution Context]
   
    subgraph LocalContext1[local execution context1]
        aVariable[a = 1]
        bVariable[b = unknown]
    end

    subgraph LocalContext2[second function]
        cVariable[c = 2]
        arguments[arguments = 7, 9]
    end

    GlobalContext --->|Creates| LocalContext1
    GlobalContext --->|Creates| LocalContext2
```

---

```mermaid
graph TD
    GlobalContext[Global Execution Context]
    subgraph Global[Global]
        nameVariable[name =  John]
        firstFN[first = function ]
        secondFN[second = function ]
        x[x = unknown ]
    end

    subgraph LocalContext1[first function]
        aVariable[a = 1]
        bVariable[b = unknown]
    end

    subgraph LocalContext2[second function]
        cVariable[c = 2]
        arguments[arguments = 7, 9]
    end

    GlobalContext --> Global
    GlobalContext --> LocalContext1
    GlobalContext --> LocalContext2
```

---


<img src="/public/js.excontext1.png" style="height: 100%; width: 100%;">

---

<img src="/public/js.callstack1.png" style="height: 100%; width: 100%;">

---

<img src="/public/js.callstack2.png" style="height: 100%; width: 100%;">

---

<img src="/public/js.callstack3.png" style="height: 100%; width: 100%;">

---

<img src="/public/js.callstack5.png" style="height: 100%; width: 100%;">

---

<img src="/public/js.callstack6.png" style="height: 100%; width: 100%;">

---

<img src="/public/js.callstack7.png" style="height: 100%; width: 100%;">

---

<img src="/public/js.callstack8.png" style="height: 100%; width: 100%;">

---

<img src="/public/js.callstack9.png" style="height: 100%; width: 100%;">

---

<img src="/public/js.callstack10.png" style="height: 100%; width: 100%;">

---
layout: two-cols
---

```mermaid
graph TD
    EventLoop[Event Loop] -->|Checks Call Stack| CallStack
    EventLoop -->|Processes Microtasks| MicrotaskQueue
    EventLoop -->|Processes Task Queue if Call Stack is empty| TaskQueue
    CallStack --> Execution[Execution]
    MicrotaskQueue --> CallStack
    TaskQueue --> CallStack
```

::right::

- Event Loop: მართავს კოდის შესრულებას, ამოწმებს Call Stack-ს და ამუშავებს Microtask Queue-სა და Task Queue-ს.

- Microtask Queue: შეიცავს მაღალი პრიორიტეტით ასინქრონულ ოპერაციებს (Promises და სხვ..). აქ მოთავსებული ფუნქციები გადადის Call Stack-ში პირველი ვიდრე Task Queue-ში მოთავსებული ფუნქციები

- Task Queue: შეიცავს სხვა ტიპის ასინქრონულ ოპერაციებს (setTimeout, I/O). აქ მოთავსებული ფუნქციები გადადის Call Stack-ში მხოლოდ მას შემდეგ, რაც Microtask Queue  და Call Stack ცარიელია.

- Call Stack: ასრულებს კოდს თანმიმდევრულად.

- Execution: კოდის საბოლოო შესრულება Call Stack-ში

---
layout: two-cols
---

```mermaid
graph TD
    subgraph WebAPIs[Web APIs]
        DOM[DOM]
        Timers[Timers]
        FetchAPI[Fetch API]
    end
    subgraph Queue[Callback Queue]
        
    end
    CallStack[Call Stack]
    WebAPIs --> Queue
    Queue --> CallStack
```

::right::

- Web APIs-ში მოთავსებულია სხვადასხვა ფუნქციები

- როგორიცაა DOM, Timers და Fetch API

- Callback Queue ცარიელია

- Call Stack ელოდება ახალ ამოცანებს.

---
layout: two-cols
---

```mermaid
graph TD
    subgraph WebAPIs[Web APIs]
        DOM[DOM]
        Timers[Timers]
        FetchAPI[Fetch API]
    end
    subgraph Queue[Callback Queue]
        OnClick[onClick]
    end
    CallStack[Call Stack]
    WebAPIs --> Queue
    Queue --> CallStack
```

::right::

- ხდება DOM მოვლენა (click)  

- შესაბამისი callback გადადის Callback Queue-ში.

- Event Loop ამოწმებს, რომ Call Stack ცარიელია და მზად არის Callback Queue-დან ელემენტების გადასატანად call stack ში.

---
layout: two-cols
---

```mermaid
graph TD
    subgraph WebAPIs[Web APIs]
        DOM[DOM]
        Timers[Timers]
        FetchAPI[Fetch API]
    end
    subgraph Queue[Callback Queue]
    end
    subgraph CallStack[Call Stack]
        OnClick[onClick]
    end
    WebAPIs --> Queue
    Queue --> CallStack
```

::right::

- onClick callback გადადის Call Stack-ში და იწყებს შესრულებას

- Callback Queue დაცარიელდა 

- Call Stack მუშაობს, სანამ ფუნქცია არ დასრულდება და სტეკიდან ამოიშლება.

---
layout: two-cols
---

```mermaid
graph TD
    subgraph WebAPIs[Web APIs]
        DOM[DOM]
        Timers[Timers]
        FetchAPI[Fetch API]
    end
    subgraph Queue[Callback Queue]
        
    end
    CallStack[Call Stack]
    WebAPIs --> Queue
    Queue --> CallStack
```

::right::

- შესრულდა ყველაფერი და callstack იც გაცარიელდა
