# Iteration 1 – Features

## Functional Requirements (FR)

- **FR1 (HIGH, UC1):** The system shall allow the user to enter basic client financial parameters (retirement age, life expectancy, current income, annual expenses).  
- **FR2 (HIGH, UC1):** The system shall allow the user to enter current asset balances across qualified and non-qualified accounts.  
- **FR3 (HIGH, UC2):** The system shall allow the user to enter expected performance rates on assets.  
- **FR4 (HIGH, UC3):** The system shall perform a baseline “as-is” tax calculation using provided client parameters.  
- **FR5 (HIGH, UC3):** The system shall display the results of the baseline tax calculation to the user in a clear format.  

---

## Non-Functional Requirements (NRs)

- **NR2 (HIGH, UC1–UC5):** The system shall encrypt sensitive financial data both in transit (TLS 1.2+) and at rest.  
- **NR4 (HIGH, UC1–UC5):** The system shall present all input forms and outputs in a clear, user-friendly interface with error validation.  

---

## Justification
These requirements were chosen because they establish a **functional foundation** for Iteration 1:
- Users can **enter financial data**.  
- The system can **run a baseline tax calculation**.  
- The system can **display meaningful results** securely and clearly.  

This ensures immediate value delivery and sets the groundwork for future iterations (Roth conversion optimization, reporting/export features, etc.).

---

## Project Management Setup
- Create GitHub Project board with **To Do, In Progress, and Done** columns.  
- Add cards for each of the following requirements in the **To Do** column:
  - FR1: Enter basic financial parameters  
  - FR2: Enter current asset balances  
  - FR3: Enter expected performance rates  
  - FR4: Perform baseline tax calculation  
  - FR5: Display baseline tax results  
  - NR2: Encrypt sensitive data  
  - NR4: User-friendly interface with error validation  

---
