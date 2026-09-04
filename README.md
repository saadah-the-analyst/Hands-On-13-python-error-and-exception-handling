# Hands-On-13-python-error-and-exception-handling

# Lesson 13: Python Errors, Exceptions, Debugging & Exception Handling

## Executive Summary
This repository contains production-ready Python exception handling patterns across industry workflows in Healthcare, E-Commerce, and Banking. The project demonstrates defensive input parsing, data type casting, business logic validations, custom exception raising (`raise ValueError`), and `try-except` blocks to prevent unhandled runtime crashes during pipeline execution.

---

## Project Background & Problem Statement
Raw user inputs from web interfaces, enterprise applications, and transactional systems frequently contain invalid entries—such as missing text fields, unexpected characters, negative numerical values, and non-numeric strings—which cause application crashes (`ValueError`, `TypeError`).

Unprotected script failures disrupt system operations:
* **Healthcare Record Validation:** Non-numeric age or negative weight values lead to corrupted electronic health records or system crashes.
* **E-Commerce Order Processing:** Invalid quantity inputs (e.g., negative values or text entries like `"five"`) break subtotal calculations and order pipelines.
* **Banking Transaction Systems:** Unchecked withdrawals leading to account overdrafts or negative amounts introduce financial reporting discrepancies.

This project addresses these stability issues by implementing error handling frameworks using structured `try-except` blocks, explicit boundary checks, and descriptive error logging.

---

## Real-World Business & Operational Impact

* **Healthcare System Resilience:** Validates patient records during input, eliminating data entry errors and protecting downstream database integrity.
* **E-Commerce Transaction Safety:** Standardizes price and quantity parsing, enforces minimum order thresholds, and calculates percentage-based discounts (`10%` for orders over ₦100,000) while failing gracefully on invalid input.
* **Financial Integrity & Overdraft Protection:** Enforces withdrawal boundary checks and automated fee deductions (₦100 per transaction) to prevent account overdrafts.
* **Improved User Experience:** Replaces unhandled tracebacks with readable error messages (e.g., `[Validation Failed]: Age Error: Age must be a whole number.`), guiding users without stopping execution.

---

## Tools & Technical Environment

* **Core Language:** Python 3.x
* **Development Environment:** Jupyter Notebook / JupyterLab
* **Core Concepts Applied:**
* **Control Flow & Exception Handling:** `try`, `except ValueError as e`, `raise ValueError()`
* **String Sanitization:** Method chaining (`.strip()`)
* **Type Casting & Defensive Conversion:** `int()`, `float()`
* **Business Rule Validation:** Non-empty checks, boundary validations (`age < 0`, `quantity <= 0`, `withdrawal > balance`)
* **Financial Formatting:** F-string currency formatting (`₦{total_cost:,.2f}`)

---

## Technical Capabilities & Concepts Mastered

* **Defensive Input Parsing:** Applied `.strip()` to string inputs to clean whitespace prior to type conversion.
* **Custom Exception Raising:** Utilized `raise ValueError("Descriptive Error Message")` to enforce domain-specific validation rules.
* **Layered Try-Except Architecture:** Embedded nested conversion validation blocks within parent exception handlers to deliver precise error context.
* **Transaction Fee & Discount Mechanics:** Calculated fee structures and conditional order discounts while safeguarding total balance deductions.

---

## Detailed Exercise Breakdown

### Hands-On Exercise 1: Hospital Patient Data Validator (Healthcare)
* Prompted for patient inputs: `patient_name`, `patient_id`, `age_input`, `weight_input`.
* Converted age to `int` and weight to `float` inside a `try-except` block.
* Raised `ValueError` for negative age inputs.
* Displayed validated patient summaries and captured invalid inputs gracefully.
* **Bonus Challenge:** Modularized validation inside a main function `validate_patient_record()`, enforcing non-empty string checks for `patient_name` and `patient_id`, isolated exception handling for age (`Age Error: Age must be a whole number.`), and non-zero/non-negative weight checks (`Weight Error: Weight must be greater than zero.`).

### Hands-On Exercise 2: E-Commerce Order Processing System (E-Commerce)
* Captured `customer_name`, `product_name`, `price_input`, and `quantity_input`.
* Converted product price to `float` and order quantity to `int`.
* Enforced positive quantity boundaries (`quantity <= 0` raises `ValueError`).
* Computed order total (`total_cost = price * quantity`) and printed formatted receipts.
* **Bonus Challenge:** Implemented discount logic providing a `10%` discount for total orders exceeding ₦100,000 (`discount = total_cost * 0.10`), displaying itemized subtotal, discount, and final total metrics.

### Hands-On Exercise 3: Banking Transaction Validator (Banking & Finance)
* Defined initial account balance (`balance = 150000`).
* Captured `withdrawal_input` and converted input to `float`.
* Validated withdrawal limits: rejected zero or negative withdrawals (`withdrawal <= 0`) and insufficient funds (`withdrawal > balance`).
* Deducted approved funds and printed remaining balances.
* **Bonus Challenge:** Integrated a mandatory flat transaction fee (`transaction_fee = 100`), evaluated total deductions (`total_deduction = withdrawal + transaction_fee`), and verified that account balances covered both withdrawal and fee expenses.

---

## Key Output Artifacts

```text
--- EXERCISE 1: PATIENT DATA VALIDATOR OUTPUT ---
Enter patient's name: David
Enter patient's ID: PT001
Enter patient's age: 25
Enter patient's weight: 68.5

========== PATIENT RECORD ==========
Patient Name: David
Patient ID: PT001
Age: 25
Weight: 68.5 kg
Status: Validated
====================================


--- EXERCISE 1 (BONUS): MODULAR PATIENT VALIDATION ---
Enter Patient Name: Praise
Enter Patient ID: PT002
Enter Age: 29
Enter Weight: 79

========== PATIENT RECORD ==========
Patient Name: Praise
Patient ID: PT002
Age: 29
Weight: 79.0 kg
Status: Validated
====================================


--- EXERCISE 2: E-COMMERCE ORDER PROCESSING ---
Enter Customer Name: Sarah
Enter Product Name: Wireless Mouse
Enter Product Price: 15000
Enter Quantity: 3

========== ORDER SUMMARY ==========
Customer: Sarah
Product: Wireless Mouse
Unit Price: ₦15,000.0
Quantity: 3
Total Cost: ₦45,000.0
Order Status: Approved
===================================


--- EXERCISE 2 (BONUS): DISCOUNT LOGIC OUTPUT ---
Enter Customer Name: Sa'adah
Enter Product Name: Wireless Mouse
Enter Product Price: 45000
Enter Quantity: 5

========== ORDER SUMMARY ==========
Customer: Sa'adah
Product: Wireless Mouse
Unit Price: ₦45,000.0
Quantity: 5
Subtotal: ₦225,000.0
Discount: ₦22,500.0
Final Total: ₦202,500.0
Order Status: Approved
===================================


--- EXERCISE 3: BANKING TRANSACTION VALIDATOR ---
Enter withdrawal amount: 50000

========== TRANSACTION SUMMARY ==========
Account Balance: ₦150,000.00
Withdrawal: ₦50,000.00
Transaction Status: Successful
Remaining Balance: ₦100,000.00
=========================================


--- EXERCISE 3 (BONUS): WITH TRANSACTION FEE ---
Enter withdrawal amount: 50000

========== TRANSACTION SUMMARY ==========
Starting Balance: ₦150,000
Withdrawal: ₦50,000.0
Transaction Fee: ₦100
Transaction Status: Successful
Remaining Balance: ₦99,900.0
=========================================

```

## Author: Muhyideen Saadah
