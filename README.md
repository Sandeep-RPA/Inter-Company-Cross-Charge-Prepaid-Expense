# Inter-Company-Cross-Charge-Prepaid-Expense
Repository to store UiPath Agent Hackathon use case on Maestro

#Inter Company Cross Charge :
This is an accounting process where one legal entity with in a parent company charges the other entities for shared expenses, Goods , Services.

#Prepaid Expense :
A Prepaid expense is a future expense that a company pays for in advance. Examples of Prepaid expense can be Office Rent, Health Insurance for employees, Software subscriptions.

#EscalationApp_JEReview.Uis
This is an Action app created for the review of journal entries

#EscalationApp_JournalMap.uis
This is an Action App created for Missing Journal account Mapping entries

#HeadCountReport.csv
Contains schema of the Head count mapping used in data fabric. This file contains Employee Id and Business unit data

#Journal Entry Sample Schema.csv
Contains schema of data fabric entity for Journal Entry

#Solmaestro_ICOPrepaidExpense.uis
This is a maestro solution connecting all the agents & workflows.

#Sol_AgentInvoiceReader.uis
Agent to extract the prepaid expense invoice and format the data in the structured format. This agent also maps the employee to its entity

#sol_FxRateFetcher.uis
Agent to extract the real time exchange rate information from google finance. The Fx rates are fetched first through RPA , if the rpa fails agent makes use of web search tool for the extraction

#Sol_JECreator.uis
This Agent formats the charges into balanced journal entries and creates Action task for user review. Upon validation journal entries are uploaded into Table

#Sol_JEMapChecker.uis
This agent checks if the entities have account mapping available in the table
