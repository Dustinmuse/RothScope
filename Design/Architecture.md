
<img width="5475" height="2213" alt="Roth_Conversion_Architecture_1_0" src="https://github.com/user-attachments/assets/ea925fcc-08d3-41a7-8432-6430a461327d" />

### Module Choices
- Webpage
  * Existing client webpage that allows the user to interact with processes easier.
    
- Controller
  * Quintessential design for backend control. It takes in the inputs of the user through the webpage and allows us to interact with processes.
    
- Report Creator
  * Client requested, user optional and needing interaction with multiple sources to generate report means it should be separated.
    
- Visualization
  * Client requested, needing various information that cannot be locked into one process means it needs to be separated.
    
- PostgreSQL Database
  * Easy access to neat data.
    
- Conversion API
  * Required to convert user data + parameters into an optimal conversion strategy.

### Field Interaction
These are expected and will be discussed further in meetings.

- User -> Webpage
  * Customer Identification (i.e. information for database retrieval)
  * Optimization Criterion
 
- Webpage -> Controller
  * Customer Identification
  * Optimization Criterion
 
- Controller -> DB
  * Customer Identification

- DB -> Controller
  * Customer Information (e.g. existing assets balance, total annual expenses, etc.)
 
- Controller -> Conversion API
  * Customer Information
  * Retirement Age
  * Life Expectancy
  * Optimization Criterion

- Conversion API -> Controller
  * Converted Data

- Controller -> Visualization
  * Converted Data
  * Retirement Age
  * Life Expectancy (?)
  * Customer Information

- Visualization -> Controller
  * Graphs

- Controller -> Report Creator
  * Graphs
  * Customer Information
  * Converted Data
  * Retirement Age (?)

- Report Cretor -> Controller
  * Report

- Controller -> Webpage
  * Graphs
  * Report
  * Customer Infromation
  * Retirement Age (?)
  * Life Expectancy (?)

### Visual Indicators
- Grey - Dependencies not created or maintained by this project.
- Green - User Interface/Vue.js
- Purple - Logic/.NET Framework
- Blue - Data/PostgreSQL

### User Interface Interaction
  - User makes request via webpage, giving parameters that then acesses the DB via the Controller (optional?). The user can then alter this data. It then gets sent to the API which then gets sent to visualization. These numbers and graphs are sent back to the webpage. Then, at user request, it creates a report (Excel/PDF) that contains the numbers and graphs.
