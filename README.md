                    Bank Loan Performance Analysis - POWER BI
## Problem Statement:
In today's data-driven world, understanding how borrower details and loan
characteristics impact loan performance, which is very important for banking institutions. This
the project seeks to delve deep into a lending loan dataset to uncover the relationship
between borrower behavior (such as employment length, income, and debt-to-income
ratio) and loan characteristics (including amount, term, and interest rate) to unearth
critical insights into loan performance metrics. By examining patterns in loan statuses
such as fully paid, charged off, or late payments, this analysis aims to empower banking
institutions with actionable insights to optimize loan lending strategies, mitigate credit
risk, and enhance overall portfolio performance.

<br>

![Screenshot 2024-10-22 204132](https://github.com/user-attachments/assets/bcb99948-145b-4e5d-a57b-0eb36bc79db7)

<br>

![Screenshot 2024-10-22 204113](https://github.com/user-attachments/assets/dc62d9da-ce07-4441-a2a1-8117133e2663)

<br>

# 1 - Importing Data

<br>

➢ Import the "LoanDetails" and "BorrowerDetails" sheets from the "bank loan.xlsx" file into Power BI.

<br>

# 2 - Transformation Using Power Query

<br>

### Data Cleaning:

<br>

<table>
  <thead>
    <tr>
      <td><b>Handling Missing Values and Duplicates<b/></td>
      <td><b>Dealing with Inconsistencies<b/></td>
    </tr>
        <tr>
          <td>➢ Replace missing values (null) in the 'emp_length' column of the "BorrowerDetails" table with '0 year'.</td>
          <td>➢ Ensure words in the 'purpose' column are separated by spaces instead of underscores (e.g., "credit card" instead of "credit_card").</td>
        </tr>
        <tr>
          <td>➢ Remove rows with missing values in the 'last_pymnt_d' and 'delinq_2yrs' columns.</td>
          <td>➢ Format the 'purpose' and 'home_ownership' columns to proper case.</td>
        </tr>
        <tr>
          <td>➢ Remove duplicate rows in the 'id' column of the "LoanDetails" table.</td>
          <td></td>
        </tr>
  </thead>
</table>






Report - 1



![report -1](https://github.com/user-attachments/assets/e5b66e8f-f969-4306-a8c8-caca90120e36)



Report - 2
![Screenshot 2024-10-22 205139](https://github.com/user-attachments/assets/ac157b1f-11a8-43c1-9291-615b9f45eb3a)

<br>

Given Data
