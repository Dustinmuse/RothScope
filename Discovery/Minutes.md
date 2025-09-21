# Client Discovery Meeting on 09/18/2025

## Meeting Start Time

**2025/09/18/19:02** 

## Meeting End Time

**2025/09/18/19:30**

## Location/Medium

Zoom

## Present

Alex, Gabe, Dustin, Alli, Jaydon, Noah

## Minute Recorder

Gabe, Zoom AI Companion

## Topics Discussed:

Introductions:
- Alex has been at Moneytree for 8 years and this is his second student group led project

General idea:
- Create a tool to optimize Roth conversion; you have money in a 401k or IRA and want to convert to a Roth, which is a tax-deferred account where you pay taxes when you put it in so you don’t have to when you take it out. Popular among people who don’t want  to worry about paying the taxes later on
- We will find out ways to optimize money so they don’t get hit with tax liabilities, maximize output/capitol/investments, and minimize total tax payments over time
- Evaluation criteria is subject to the clients, used alongside advisors who are the main target audience
- Focus on balancing tax payments and investment potential, considering the differences between Roth (after-tax) and traditional (pre-tax) accounts

Is it alright if we take a screenshot of this call for our assignment? 
- Yes, also used AI companion for note transcribing

How often would you like to meet?
- Up to us, perhaps biweekly if necessary, at least once a month though for requirements
- We can always email Alex if we need clarification on anything
- May want to set up Jira for tracking work progress

How did Moneytree do the simpler Roth calculations before? What is the existing system like? Should our format be similar with more additions?
- User enters information; balance, start age, how long they want calculation to go on for, and conversion method (flat rate or percentage based)
- They have an existing software, ours will be an addition to theirs
- Ours will give new functionality in the form of optimization for specific outcomes

Do you want this to be a website, application, or other?
- Will want to implement this into their planning tools, desktop focused first; web application
- Mobile can be added on later if we have time

Should all of the output be on one page/screen? Or should there be some sort of menu to go to different tools (tax calculation, Roth conversion, data entry if going that route)
- One page for gathering information, another page for input/output, potentially split these up; at least 2 pages

Will this software call Moneytree’s calculation engine via an API?
- Yes, we can call their API for calculation purposes

Are we building a predictive model for the optimal timing and amount, or is there existing logic/data/algorithms that just need to be implemented into software?
- Yes, we will be coming up with the optimization model

Will this only be used by financial advisors/planners?
- Financial advisors are the main target group, depending on ease of use it could be provided to individual clients

Is it mandatory to have 2-factor authentication, or optional for the user? If mandatory, are you just using their email/phone number, or do you have a subscription to a 2-factor authentication platform like Duo Mobile?
- Optional for each user

Should the input of data into the calculation be automatic through a database pull or done explicitly by the financial advisors/planners?
- Both, their information may come from a pull but there are specifications they will need to make for each individual calculation

Do you have a preference between Microsoft SQL Server and PostgreSQL for the database, or is it up to how well they can be implemented?
- Probably will use PostgreSQL, but ultimately up to us

Is there an existing MoneyTree database that we should fill our SQL server with for client information, or will it be built through usage?
- Will get back to us about how much access we get to the Moneytree database; if we do get access it will likely be restricted

Do you want the ability to import/export data or reports (Excel or PDF, etc.)?
- PDF for reports would be nice
- They are moving more digitally in terms of visualizations for charts and things, may want Excel functionality

What kind of budget do you have set for this project?
- Alex does not know, will let us know if we need additional things
- Everything we need should be given to us already

What is the requirement priority order? i.e., what should we do first?
- Minimizing cumulative taxes optimization is the most important thing to start off with; can move from there

## Things Clarified:

- Alex will send a more detailed list of priorities; quote “he is a bit rusty on communicating his ideas for the project”
- We will get on initial planning and designing on how to do the calculations in a proof of concept before implementation
- Will reach out for further clarification/with questions as needed
