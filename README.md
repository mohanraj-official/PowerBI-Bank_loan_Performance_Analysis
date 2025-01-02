<center><h1>Bank Loan Performance Analysis - Power BI</h1></center>

---

## Problem Statement
Understanding how borrower details and loan characteristics impact loan performance is vital for banks. This project analyzes borrower behavior (e.g., employment length, income, debt-to-income ratio) and loan characteristics (e.g., amount, term, interest rate) to reveal insights into loan statuses like fully paid, charged off, or late payments. These findings aim to help banks optimize lending strategies, reduce credit risk, and improve portfolio performance.

---

## Resources
- [Download Dataset](https://drive.google.com/uc?export=download&id=1yNL9gfv-DlD3cEW9o2GJvtJ9Bzbm37R7)  
- [Download Project](https://drive.google.com/file/d/1xfK02phXaq_j5dImedE2WvvPUQnBYTkh/view?usp=sharing)

---

## 1. Importing Data
- Import **LoanDetails** and **BorrowerDetails** sheets from the `bank loan.xlsx` file into Power BI.

### Loan Details

| Field Name      | Description                                      |
|-----------------|--------------------------------------------------|
| `id`            | Unique identifier for each loan.                |
| `loan_amnt`     | Loan amount requested by the borrower.           |
| `funded_amnt`   | Actual funded loan amount.                       |
| `term`          | Loan duration in months.                        |
| `int_rate`      | Interest rate of the loan.                       |
| `installment`   | Monthly payment owed by the borrower.            |
| `grade`         | Loan grade assigned by the lending company.      |
| `sub_grade`     | Loan subgrade assigned by the lending company.   |
| `issue_d`       | Month when the loan was funded.                  |
| `purpose`       | Reason for the loan.                             |

### Borrower Details

| Field Name        | Description                                      |
|-------------------|--------------------------------------------------|
| `id`              | Unique identifier for each loan.                |
| `member_id`       | Unique identifier for each borrower.            |
| `emp_length`      | Employment length in years.                     |
| `home_ownership`  | Borrower's home ownership status.               |
| `annual_inc`      | Annual income reported by the borrower.         |
| `verification_status` | Income verification status.                  |
| `dti`             | Debt-to-income ratio.                           |
| `delinq_2yrs`     | Past-due incidents in borrower's credit file.   |
| `last_pymnt_d`    | Month of the last payment received.             |
| `total_pymnt`     | Total payments received.                        |
| `out_prncp`       | Remaining principal amount of the loan.         |

---

## 2. Data Cleaning and Transformation

### Handling Missing Values and Duplicates
- Replace missing values in `emp_length` with "0 year".
- Remove rows with missing values in `last_pymnt_d` and `delinq_2yrs`.
- Remove duplicate rows in the `id` column of **LoanDetails**.

### Dealing with Inconsistencies
- Format `purpose` and `home_ownership` columns to proper case.
- Replace underscores in `purpose` with spaces (e.g., "credit card").

### Transformations
- Change `total_pymnt` to **Fixed Decimal Number**.
- Round off `funded_amnt` to 2 decimal places.
- Rename:
  - `issue_d` to `issue_date`.
  - `last_pymnt_d` to `last_pymnt_date`.
- Create:
  - `total_amount_paid` = `total_pymnt` - `out_prncp`.
  - `delinquency_status`: If `delinq_2yrs` > 0, "Delinquent"; otherwise, "Not Delinquent".
- Drop the `sub_grade` column.

---

## 3. Data Modeling
- Create relationships between **LoanDetails** and **BorrowerDetails** using the `id` column.
- Set cross-filter direction to **Both**.

---

## 4. Measures and Calculated Columns (DAX)
- **`remaining_installments`**: Calculate remaining installments by dividing `out_prncp` by `installment` and rounding up using `CEILING()`.
- **`Non-Verified Borrowers Count`**: Count loans with "Not Verified" status.
- **`Fully Paid Loan Percentage`**: Calculate the percentage of loans with "Fully Paid" status.

---

## 5. Reports and Visualizations
- Use slicers for dynamic filtering.
- Add tooltips for detailed data points.
- Include summary sections for key insights.

### Report 1
![Report 1](https://github.com/user-attachments/assets/e5b66e8f-f969-4306-a8c8-caca90120e36)

### Report 2
![Report 2](https://github.com/user-attachments/assets/ac157b1f-11a8-43c1-9291-615b9f45eb3a)

---
