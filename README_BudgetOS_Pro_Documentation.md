# BudgetOS Pro — Personal Budget Tracker

A modern offline-first personal finance analytics web app built with **HTML, CSS, JavaScript, Chart.js, LocalStorage, and XLSX import support**.

This project turns raw transaction data into an interactive personal finance operating system with dashboards, expense tracking, income analysis, spending history, category analysis, budget planning, wishlist tracking, emergency fund logic, investment forecasting, and smart import tools.

The public demo uses **fake English financial data** for portfolio presentation.

---

## Live Demo

Add your GitHub Pages link here after publishing:

```text
https://yourusername.github.io/personal-budget-tracker/
```

---

## Project Summary

**BudgetOS Pro** is designed to answer one main question:

> How can transaction-level financial data become clear financial decisions?

Instead of only recording expenses, the app analyzes financial behavior across income, spending, saving, investing, wishlist planning, emergency fund usage, and future financial growth.

---

## Key Features

- Modern OS-style finance dashboard
- Expense Log with editable transactions
- Smart Import Center for CSV, Excel text, TSV, TXT, and messy table imports
- Income Analysis by income stream
- Spending History with month-by-month comparison
- Category and subcategory spending analysis
- Customizable Budget Plan
- Emergency Fund tracking and spending source logic
- Wishlist page for planned purchases
- Forecast page for 1, 5, 10, and 20 years
- Investment Calculator with compounding
- Privacy mode to hide sensitive numbers
- Multiple modern themes
- Theme-aware charts
- Mobile-friendly layout
- Local browser storage using LocalStorage

---

## Tools and Technologies

| Area | Tools |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Charts | Chart.js |
| Data Import | XLSX parser, CSV/TSV/text parsing |
| Storage | LocalStorage |
| UI Style | Modern dashboard / finance OS layout |
| Data Model | Transaction-level financial records |

---

## Data Privacy

This is an offline-first demo project.

- The public version uses fake demo data.
- Data is stored locally in the browser using LocalStorage.
- No financial data is sent to a server.
- The app does not include authentication or cloud database storage.
- This project is for portfolio/demo purposes and is not financial advice.

---

## Data Model

The app is mainly built around transaction-level records.

Each transaction includes:

| Field | Description |
|---|---|
| `date` | Transaction date |
| `description` | Transaction name or short explanation |
| `amount` | Transaction amount |
| `category` | Main category such as Essentials, Wants, Guilt-free, Investment, Emergency Fund, Income |
| `type` | Income, Expense, or Transfer |
| `incomeStream` | Salary, Freelance, Investment Return, Unexpected, or Previous Month Balance |
| `fundingSource` | Main Budget or Emergency Fund |
| `notes` | Optional notes |

---

# Page-by-Page Documentation

## 1. Dashboard

The Dashboard is the main financial snapshot.

### Main purpose

To show the current month’s financial position at a glance.

### Main functions

- Shows monthly income
- Shows monthly spending
- Shows invested amount
- Shows surplus or deficit
- Shows budget progress by category
- Shows spending split by category
- Shows monthly income vs spending
- Shows spent percentage trend
- Shows cumulative wealth trend
- Shows recent transactions
- Shows card/bank balance and calculated cash

### Important logic

The dashboard calculates monthly surplus as:

```text
Monthly Surplus = Income - Expenses - Transfers
```

Cash is calculated as:

```text
Cash = Monthly Surplus - Card / Bank Balance
```

This helps separate money available as cash from money currently stored in a card or bank account.

### Screenshot to take

Take a full desktop screenshot showing:

- KPI cards
- Cash & card balance section
- Budget progress
- Spending split chart

Suggested file name:

```text
screenshots/dashboard.png
```

---

## 2. Summary View

The Summary View gives a filtered high-level overview.

### Main purpose

To summarize overall performance across a selected date range.

### Main functions

- Date range filter
- Total income
- Total expenses
- Net cashflow
- All-time invested
- Emergency fund balance
- Top expenses
- Best and worst months
- Financial health scorecard
- Net cashflow trend
- Category stack trend
- Expense frequency by category
- Investment rate month by month

### Important logic

Summary calculations are based on the selected date range.

It separates:

- real income
- expenses
- investment transfers
- emergency fund transfers
- remaining balance

### Screenshot to take

Take a screenshot showing:

- date filter
- hero KPIs
- financial health scorecard
- one chart section

Suggested file name:

```text
screenshots/summary-view.png
```

---

## 3. Income Analysis

The Income Analysis page breaks down income by source.

### Main purpose

To understand income stability and dependency on each stream.

### Income streams

- Salary
- Freelance
- Investment Return
- Unexpected
- Previous Month Balance

### Main functions

- Filter by date range
- Filter by income stream
- Compare income streams over time
- Show income mix
- Compare income vs expenses vs saved
- Measure income volatility
- Show income stream table
- Generate income insights

### Important logic

Previous Month Balance is treated as carryover, not true income.

```text
Total Income = Salary + Freelance + Investment Return + Unexpected
Available Funds = Total Income + Previous Month Balance
```

This prevents carryover money from inflating real income.

### Screenshot to take

Take a screenshot showing:

- income stream filters
- income streams over time chart
- income mix chart
- income insights

Suggested file name:

```text
screenshots/income-analysis.png
```

---

## 4. Expense Log

The Expense Log is the transaction management page.

### Main purpose

To add, edit, delete, filter, and export transactions.

### Main functions

- Add new transaction
- Edit transaction
- Delete transaction
- Search transactions
- Filter by category
- Filter by month
- Export CSV
- Add income stream for income records
- Choose funding source for expenses
- Use quick add suggestions

### Editable fields

- Date
- Amount
- Description
- Category
- Income stream
- Funding source
- Notes

### Important logic

Expenses can be paid from:

```text
Main Budget
Emergency Fund
```

If an expense is paid from Emergency Fund, it reduces emergency balance instead of increasing normal monthly budget pressure.

### Screenshot to take

Take a screenshot showing:

- add entry form
- quick add section
- transaction list
- filters/search

Suggested file name:

```text
screenshots/expense-log.png
```

---

## 5. Import Center

The Import Center converts external data into valid Expense Log entries.

### Main purpose

To import data from different table formats and convert it into the tracker’s transaction format.

### Supported import sources

- CSV
- TSV
- TXT
- Pasted Excel tables
- Excel files through XLSX parser
- Messy bank-statement-like text

### Main functions

- Upload file
- Paste table/text
- Detect columns automatically
- Preview rows before importing
- Detect dates
- Detect amount columns
- Detect debit/credit columns
- Detect income vs expense
- Predict category
- Predict income stream
- Detect duplicates
- Import valid rows into Expense Log

### Important logic

The import parser attempts to map messy columns into:

```text
Date
Description
Amount
Category
Type
Income Stream
Funding Source
Notes
```

It is a smart rule-based parser, not a cloud AI model.

### Screenshot to take

Take a screenshot showing:

- file upload area
- paste area
- detected mapping
- preview table

Suggested file name:

```text
screenshots/import-center.png
```

---

## 6. Spending History

The Spending History page compares financial behavior month by month.

### Main purpose

To show how spending, income, saving, and category behavior change over time.

### Main functions

- Monthly comparison table
- Income vs expenses line chart
- Category trends
- Saved vs remaining
- 100% category share chart
- Spent percentage risk line
- Monthly category pressure chart
- Smart insights

### Monthly comparison fields

- Month
- Guilt-free
- Essentials
- Wants
- Total Spent
- Income
- Spent %
- Saved
- Remaining

### Important logic

```text
Saved = Investment Transfers + Emergency Fund Transfers
Remaining = Income - Total Spent - Saved
```

### Screenshot to take

Take a screenshot showing:

- monthly comparison table
- income vs expenses chart
- category trend chart

Suggested file name:

```text
screenshots/spending-history.png
```

---

## 7. Category Analysis

The Category Analysis page analyzes spending using both category and description.

### Main purpose

To identify the exact things that consume the most money.

### Main functions

- Uses description as subcategory
- Shows top spending descriptions
- Shows subcategory trend over time
- Shows frequency vs average amount
- Shows spending table by subcategory
- Highlights repeated habits
- Highlights high-ticket items
- Highlights biggest spending leak

### Important logic

The app treats the transaction description as a subcategory.

Example:

```text
Category: Guilt-free
Subcategory / Description: Coffee
```

This allows the user to see not only that they spent on Guilt-free, but exactly what items caused the spending.

### Screenshot to take

Take a screenshot showing:

- top subcategories
- subcategory trend chart
- subcategory table
- insight cards

Suggested file name:

```text
screenshots/category-analysis.png
```

---

## 8. Budget Plan

The Budget Plan page manages planned allocation percentages.

### Main purpose

To define how income should be distributed across budget buckets.

### Main functions

- Customize budget allocations
- Update sliders
- Show planned vs actual
- Show allocation donut chart
- Track spending pressure

### Default budget buckets

- Investment
- Emergency Fund
- Essentials
- Wants
- Guilt-free
- Giving

### Important logic

Some buckets are calculated directly from salary, while others can be calculated from spendable money after investment and emergency allocation.

### Screenshot to take

Take a screenshot showing:

- allocation sliders
- budget cards
- allocation donut

Suggested file name:

```text
screenshots/budget-plan.png
```

---

## 9. Emergency Fund Logic

Emergency Fund is treated as a dedicated safety balance.

### Main purpose

To separate true emergency savings from normal monthly spending.

### Main functions

- Emergency Fund increases when a transaction is added with category Emergency Fund
- Emergency Fund decreases when an expense is paid from Emergency Fund
- Emergency expenses can be excluded from normal monthly spending pressure
- Prevents accidental double-counting

### Important logic

```text
Emergency Fund Balance =
Emergency Fund Transfers
- Expenses Paid From Emergency Fund
```

This keeps emergency money separate from the main budget.

### Screenshot to take

Take a screenshot showing:

- Expense Log funding source option
- Emergency Fund balance in dashboard/summary

Suggested file name:

```text
screenshots/emergency-fund-logic.png
```

---

## 10. Wishlist

The Wishlist page manages planned purchases.

### Main purpose

To plan future purchases before they become actual expenses.

### Main functions

- Add wishlist item
- Add expected price
- Add category
- Add priority
- Add target month
- Add notes
- Edit any wishlist item
- Delete wishlist item
- Filter by status, category, and priority
- Show wishlist KPI cards
- Show cost by category chart
- Show priority pressure chart
- Mark item as bought
- Automatically add bought item to Expense Log

### Important logic

When a wishlist item is marked as bought:

1. The app asks for the actual paid amount.
2. It creates a transaction in the Expense Log.
3. The wishlist item is marked as Bought.
4. The item cannot be added twice by mistake.

### Screenshot to take

Take a screenshot showing:

- add wishlist form
- wishlist cards
- edit options
- Bought → Log button
- wishlist charts

Suggested file name:

```text
screenshots/wishlist.png
```

---

## 11. Forecast

The Forecast page projects financial outcomes.

### Main purpose

To estimate future financial growth based on current behavior and assumptions.

### Forecast horizons

- 1 year
- 5 years
- 10 years
- 20 years

### Main functions

- Choose forecast basis
- Edit annual investment return
- Edit income growth
- Edit expense growth
- Show projected net worth
- Show scenarios
- Show forecast table
- Show forecast insights

### Important logic

The forecast uses historical averages and compounds investments monthly.

```text
Monthly Return = (1 + Annual Return) ^ (1/12) - 1
```

Scenario logic:

```text
Base Case = annual return entered by user
Worst Case = annual return - 10 percentage points
Best Case = annual return + 10 percentage points
```

### Screenshot to take

Take a screenshot showing:

- forecast assumption inputs
- 1/5/10/20 year cards
- forecast chart
- forecast table

Suggested file name:

```text
screenshots/forecast.png
```

---

## 12. Investment Calculator

The Investment Calculator tests custom investment scenarios.

### Main purpose

To simulate long-term investment growth with compounding.

### Main inputs

- Initial amount
- Monthly contribution
- Annual return %
- Number of years
- Contribution growth %

### Main functions

- Calculate future investment value
- Calculate total contributions
- Calculate investment growth
- Show value over time
- Show contribution vs growth
- Show milestone table

### Important logic

Investment value is calculated monthly using compound growth.

```text
Investment Balance =
Previous Balance × (1 + Monthly Return) + Monthly Contribution
```

### Screenshot to take

Take a screenshot showing:

- calculator inputs
- final value cards
- growth chart
- milestone table

Suggested file name:

```text
screenshots/investment-calculator.png
```

---

## 13. Settings

The Settings page controls customization.

### Main purpose

To customize the app’s appearance and budget settings.

### Main functions

- Change theme
- Change currency
- Adjust budget allocations
- Export data
- Clear entries

### Theme system

The app includes multiple modern themes. Charts and dashboard colors adapt to the selected theme.

### Screenshot to take

Take a screenshot showing:

- theme library
- budget allocation settings

Suggested file name:

```text
screenshots/settings.png
```

---

## 14. Privacy Mode

Privacy Mode hides sensitive numbers.

### Main purpose

To allow the user to screen-share or take screenshots without revealing financial values.

### Main functions

- Blur financial numbers
- Blur chart data
- Toggle visibility with an eye icon
- Reveal temporarily on hover

### Screenshot to take

Take one optional screenshot with Privacy Mode enabled.

Suggested file name:

```text
screenshots/privacy-mode.png
```

---

# Recommended Screenshot List

For the strongest portfolio documentation, take these screenshots:

| Priority | Screenshot | Why it matters |
|---|---|---|
| 1 | Dashboard | First impression and project value |
| 2 | Spending History | Shows analytical depth |
| 3 | Category Analysis | Shows behavior-level insights |
| 4 | Import Center | Shows data cleaning/import logic |
| 5 | Income Analysis | Shows income stream thinking |
| 6 | Wishlist | Shows product thinking |
| 7 | Forecast | Shows financial modeling |
| 8 | Investment Calculator | Shows compounding logic |
| 9 | Expense Log | Shows CRUD functionality |
| 10 | Settings/Themes | Shows customization and UX polish |
| Optional | Privacy Mode | Shows thoughtful UX for sensitive data |

---

# Suggested Portfolio Case Study Structure

## 1. Project Title

**BudgetOS Pro — Personal Budget Tracker**

## 2. One-line Description

An offline-first finance analytics web app that turns transaction-level data into dashboards, spending insights, budget planning, wishlist tracking, and investment forecasts.

## 3. Problem

Most budgeting tools record transactions, but they do not clearly explain spending behavior or connect daily expenses to future financial planning.

## 4. Solution

I built a browser-based finance analytics app that organizes financial transactions, analyzes patterns, tracks income streams, manages planned purchases, and forecasts long-term wealth growth.

## 5. My Role

I designed and built the full app logic, UI layout, dashboard structure, data model, import workflow, KPI calculations, and forecasting model.

## 6. Skills Demonstrated

- Data cleaning
- KPI design
- Dashboard storytelling
- Financial analysis
- JavaScript logic
- Data modeling
- Chart design
- LocalStorage persistence
- UX design
- Forecast modeling
- Product thinking

## 7. Business Value

The app helps users understand where money goes, identify spending leaks, track income quality, control planned purchases, and forecast investment growth.

---

# Future Improvements

- Convert the app to React or Next.js
- Add secure backend storage
- Add user accounts
- Add cloud backup
- Add AI-assisted import through a backend API
- Add recurring transactions
- Add goal-based savings plans
- Add PWA installation support
- Add multi-currency support
- Add real bank statement templates

---

# Disclaimer

This project is for portfolio and educational purposes only. It is not financial advice.
