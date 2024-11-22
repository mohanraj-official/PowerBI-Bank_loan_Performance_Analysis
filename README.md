<center><h1>Bank Loan Performance Analysis - Power BI</h1></center>

|Problem Statement|
|-----|
|In today's data-driven world, understanding how borrower details and loan characteristics impact loan performance, is very important for banking institutions. This project seeks to delve deep into a lending loan dataset to uncover the relationship between borrower behavior (such as employment length, income, and debt-to-income ratio) and loan characteristics (including amount, term, and interest rate) to unearth critical insights into loan performance metrics. By examining patterns in loan statuses such as fully paid, charged off, or late payments, this analysis aims to empower banking institutions with actionable insights to optimize loan lending strategies, mitigate credit risk, and enhance overall portfolio performance.|

<br>

[Download Dataset](https://drive.google.com/uc?export=download&id=1yNL9gfv-DlD3cEW9o2GJvtJ9Bzbm37R7) - [Download my Project](https://drive.google.com/file/d/1xfK02phXaq_j5dImedE2WvvPUQnBYTkh/view?usp=sharing) 
<br>

|1 - Importing Data|
|--------------------|
|➢ Import the "LoanDetails" and "BorrowerDetails" sheets from the "bank loan.xlsx" file into Power BI.|

<br>

<center><h3>Loan Details</h3></center>
  
|Field Name |Description|
|--------------|----------------|
|id| Unique identifier for each loan.|
|loan_amnt| The amount of money requested by the borrower.|
|funded_amnt| The actual amount of money funded for the loan.|
|term| The duration of the loan in months.|
|int_rate |The interest rate of the loan.|
|installment| The monthly payment owed by the borrower.|
|grade |The loan grade assigned by the lending company.|
|sub_grade| The loan subgrade assigned by the lending company.|
|issue_d |The month in which the loan was funded.|
|purpose |The reason provided by the borrower for the loan.|

<br>

<center><h3>Borrower Details</h3></center>

|Field Name |Description|
|--------------|----------------|
|id |Unique identifier for each loan.|
|member_id| Unique identifier for each borrower.|
|emp_length| Employment length in years.|
|home_ownership| The status of home ownership reported by the borrower.|
|annual_inc |The annual income reported by the borrower.|
|verification_status |Indicates if the borrower's income was verified.|
|dti| The debt-to-income ratio of the borrower.|
|delinq_2yrs| The number of past-due incidences in the borrower's credit file.|
|last_pymnt_d| The month of the last payment received.|
|total_pymnt |The total amount received in payments.|
|out_prncp |The remaining outstanding principal amount of the loan.|

# 2 - Transformation Using Power Query
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


### Data Transformation
<table>
  <thead>
    <tr>
      <td>Column Transformation</td>
      <td>Column Renaming</td>
      <td>Creating New Columns</td>
      <td>Column Dropping</td>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>➢ Change the data type of the 'total_pymnt' column to 'Fixed decimal number'.</td>
      <td>➢ Rename the column 'issue_d' to 'issue_date'.</td>
      <td>➢ Create a new custom column named 'total_amount_paid' to calculate the total amount paid by each borrower by subtracting 'out_prncp' from 'total_pymnt'.</td>
      <td>➢ Remove the 'sub_grade' column as that does not significantly contribute to the analysis.</td>
    </tr>
    <tr>
      <td>➢ Round off the numbers in the 'funded_amnt' column to 2 decimal places.</td>
      <td>➢ Rename the column 'last_pymnt_d' to 'last_pymnt_date'.</td>
      <td>➢ Add a new conditional column named 'delinquency_status' to identify if the borrower has any delinquencies. If the number of delinquencies in 'delinq_2yrs' is greater than 0, the status should be "Delinquent", otherwise "Not Delinquent".</td>
      <td></td>
    </tr>
  </tbody>
</table>

|3 - Data Modeling|
|----|
|➢ Identify the common column between both tables and establish relationships between the two tables. Ensure the cross-filter direction is set to "Both". This step is crucial for enabling cross-table analysis and ensuring data integrity within the dataset.|

<br>

|4 - Creating Measures and Calculated Columns using DAX|
|-------------------------|
|➢ Create a new calculated column named 'remaining_installments' using DAX in the "BorrowerDetails" table to calculate the number of remaining installments by dividing the remaining principal amount ('out_prncp') by the monthly installment amount ('installment') and round up the result using the CEILING() function to account for any partial payments.|
|➢ Create a measure named 'Non-Verified Borrowers Count' using DAX to count the number of loans that have been 'Not Verified'.|
|➢ Create a measure named 'Fully Paid Loan Percentage' to calculate the percentage of fully paid loans. Divide the number of loans with a "Fully Paid" loan status by the total number of loans and then format this measure as Percentage.|

<br>

|5 - Creating Comprehensive Reports|
|-----------------------------|
|➢ Ensure each report and its charts are titled appropriately for easy identification.|
|➢ Maintain a clean and professional layout throughout both reports.|
|➢ Format and customize the charts to enhance visual appeal and comprehension.|
|➢ Utilize slicers for dynamic data exploration and filtering.|
|➢ Add tooltips to provide additional context and details for data points when hovered over.|
|➢ Include a summary or key insights section in each report to highlight main findings and observations.|






|Report - 1|
|----------------|
|![report -1](https://github.com/user-attachments/assets/e5b66e8f-f969-4306-a8c8-caca90120e36)|



|Report - 2|
|---|
|![Screenshot 2024-10-22 205139](https://github.com/user-attachments/assets/ac157b1f-11a8-43c1-9291-615b9f45eb3a)|


