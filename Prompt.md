# FlowState | AI Prompt Guide (`prompt.md`)

Use this document to quickly copy and paste highly contextualized prompts into your AI assistant (ChatGPT, Claude, Gemini, etc.). By providing the AI with the exact code snippets from our codebase, you will get much more accurate and drop-in ready solutions.

---

## 🎨 1. UI & Styling Prompts (Using `style.css`)

### Prompt: Fixing Mobile Chart Responsiveness
> "On mobile devices (under 600px), my Chart.js container is shrinking too much. 
> 
> Here is the relevant CSS from my media query:
> ```css
> @media (max-width: 600px) {
>   .chart-container { max-width: 200px; }
> }
> ```
> How can I modify this CSS so the chart takes up 100% of the container width on mobile, but maintains its aspect ratio?"

---

## ⚙️ 2. Logic & State Prompts (Using `script.js`)

### Prompt: Adding 'Edit Expense' Functionality
> "My app currently allows users to add and delete expenses, but not edit them. 
> 
> Here is my `AppState` and the `deleteExpense` function from `script.js`:
> ```javascript
>   let AppState = {
>     salary: 0,
>     expenses: [],
>     currency: "INR",
>     exchangeRate: 1,
>   };
>
>   function deleteExpense(id) {
>     const exp = AppState.expenses.find((e) => e.id === id);
>     if (!exp) return;
>     AppState.expenses = AppState.expenses.filter((e) => e.id !== id);
>     saveState();
>     renderAll();
>     checkThreshold();
>     showToast(`"${exp.name}" removed.`, "info");
>   }
> ```
> Please write a new function called `editExpense(id)` that populates the `#expense-name` and `#expense-amount` inputs with the selected expense's data, removes the old entry, and allows the user to re-save it."

### Prompt: Improving API Error Handling & Fallbacks
> "My app uses the ExchangeRate-API to handle currency conversions. 
>
> Here is my current `handleCurrencyChange` function:
> ```javascript
>   async function handleCurrencyChange(newCurrency) {
>     // ... (setup code)
>     try {
>       const res = await fetch('[https://open.er-api.com/v6/latest/INR](https://open.er-api.com/v6/latest/INR)');
>       if (!res.ok) throw new Error(`HTTP error! status: ${res.status}`);
>       const data = await res.json();
>       const rate = data.rates[newCurrency];
>       // ... (apply rate)
>     } catch (error) {
>       console.error("Currency API Failure:", error); 
>       AppState.exchangeRate = 1;
>       DOM.rateBadge.textContent = "rate error";
>       showToast("Exchange rate API unavailable. Defaulting to 1:1 ratio.", "error");
>       renderAll();
>     }
>   }
> ```
> How can I implement a 5-second timeout on this `fetch` request, and how do I cache the last known exchange rates in `localStorage` so the app still works offline if the API fails?"

---

## 📊 3. Chart & PDF Export Prompts (Using `script.js` & `index.html`)

### Prompt: Modifying Chart.js Colors Based on Thresholds
> "I am using Chart.js in my app. Right now, the doughnut chart uses static colors: `#0891b2` for remaining and `#e11d48` for spent. 
> 
> Here is my dataset configuration in `renderChart()`:
> ```javascript
>   datasets: [
>     {
>       data: spent > sal ? [0, spent] : [Math.max(0, sal - spent), spent],
>       backgroundColor: ["#0891b2", "#e11d48"],
>       hoverBackgroundColor: ["#0e7490", "#be123c"],
>       borderWidth: 0,
>       hoverOffset: 4,
>     },
>   ],
> ```
> How can I write a conditional block that changes the 'remaining' color to a warning color (like orange/amber) if the `getBalancePct()` is 25% or lower?"

### Prompt: Adding a New Column to the PDF Export
> "My app exports financial data to a PDF using `jsPDF` and `jspdf-autotable`. 
> 
> Here is the configuration for the table in my `downloadReport()` function:
> ```javascript
>       doc.autoTable({
>         startY: 75,
>         head: [["#", "Expense Name", "Date", "Amount"]],
>         body: tableData,
>         // ...
>       });
> ```
> I want to add a 5th column titled 'Category Icon' that displays the emoji stored in `e.icon`. How do I update `tableData` mapping and the `doc.autoTable` configuration to include this new column?"

---

## 🏗️ 4. Architecture Prompts

### Prompt: Modularizing the Application
> "My `script.js` file is currently a single Monolith using the Module Pattern:
> ```javascript
> const FlowStateApp = (function () {
>   // ... all logic, state, and DOM caching
>   return { init: () => { ... } };
> })();
> document.addEventListener("DOMContentLoaded", FlowStateApp.init);
> ```
> I want to move to modern ES6 modules. What is the best way to break this single file into `state.js` (for AppState), `ui.js` (for DOM manipulation and rendering), and `api.js` (for the exchange rate fetch)? Please provide the structure and show how to `import` and `export` the necessary methods."
