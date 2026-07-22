# FlowState | Finance Tracker

A sleek, responsive, and intuitive single-page web application designed for real-time income tracking, expense categorization, budget monitoring, and financial report generation.

---

## 🚀 Live Demo & Preview
 
> **Live Demo Link:** (https://sprint2-phi-six.vercel.app/)


![FlowState Preview Screenshot]<img width="1896" height="1082" alt="Screenshot 2026-07-23 040251" src="https://github.com/user-attachments/assets/3a8eb2ce-df9c-4e20-bb2c-8b37df3a56c4" />


---

## ✨ Features

* **Real-Time Balance Tracking:** Set your monthly income and dynamically monitor your remaining balance with an interactive progress bar.
* **Smart Threshold Alerts:** Receive visual warnings when your remaining balance drops below 25%, and critical banner alerts when it drops below 10% or if you overspend.
* **Categorized Expense Logging:** Add expenses that automatically map to contextual emojis (e.g., Rent 🏠, Food 🍔, Travel ✈️) based on keyword recognition.
* **Interactive Data Visualization:** View a dynamic doughnut chart breakdown of your remaining vs. spent allocation, powered by Chart.js.
* **Multi-Currency Support:** Convert values dynamically between `INR (₹)`, `USD ($)`, `EUR (€)`, `GBP (£)`, and `JPY (¥)` using live exchange rates via `ExchangeRate-API`.
* **PDF Report Generation:** Download comprehensive PDF summary reports of your financial status and itemized expense log, formatted cleanly with `jsPDF` and `jspdf-autotable`.
* **Local Data Persistence:** Uses `localStorage` to save your salary, selected currency, and logged expenses securely across browser sessions.
* **Responsive Dark UI:** A meticulously crafted Slate & Cyan dark theme optimized for mobile, tablet, and desktop viewing.

---

## 🛠️ Tech Stack & Libraries

| Technology / Library | Purpose |
| :--- | :--- |
| **HTML5 / CSS3** | Semantic structure, flexbox/grid layout, CSS variables, and modern responsive design |
| **Vanilla JavaScript** | State management, DOM manipulation, and event handling |
| **[Chart.js v4.4.3](https://www.chartjs.org/)** | Interactive data visualization |
| **[jsPDF v2.5.1](https://github.com/parallax/jsPDF)** | Client-side PDF document creation |
| **[jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable)** | Tabular data formatting for exported PDF reports |
| **[ExchangeRate-API](https://open.er-api.com/)** | Live currency conversion rates |

---

## 📂 Project Structure

```text
├── index.html        # Main HTML structure and UI components
├── style.css         # Styling, CSS variables, animations, and media queries
├── script.js         # Core application logic and state management
└── README.md         # Project documentation
