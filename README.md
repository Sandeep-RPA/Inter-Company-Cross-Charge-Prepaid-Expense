# Inter-Company-Cross-Charge-Prepaid-Expense
This repository houses an automated end-to-end Maestro solution designed to manage, calculate, and process inter-company cross-charges for prepaid expenses. 

## Project Overview
In corporate accounting, managing shared expenses across multiple legal entities can be highly manual and error-prone. This project automates the entire lifecycle of **Inter-Company Cross-Charges** (where one legal entity charges another for shared goods or services) specifically for **Prepaid Expenses** (future expenses paid for in advance, such as office rent, health insurance, or software subscriptions).

The system integrates robotic process automation (RPA), data fabric schemas, AI agents, and human-in-the-loop validation apps to ensure balanced journal entries are accurately generated and uploaded.

# Inter Company Cross Charge :
This is an accounting process where one legal entity with in a parent company charges the other entities for shared expenses, Goods , Services.

# Prepaid Expense :
A Prepaid expense is a future expense that a company pays for in advance. Examples of Prepaid expense can be Office Rent, Health Insurance for employees, Software subscriptions.

## UiPath Components :

### Agents : 
Below are the list of Low-code Agents developed in Studio web.This Project contains only low-code agents.

* **`Sol_AgentInvoiceReader.uis`**: Extracts data from prepaid expense invoices, transforms it into a structured format, and maps employees to their respective legal entities.
* **`Sol_FxRateFetcher.uis`**: Fetches real-time foreign exchange rates from Google Finance using RPA. If the RPA process fails, it fallback-searches via a web tool to ensure continuous operation.
* **`Sol_JEMapChecker.uis`**: Verifies if the involved legal entities have valid account mapping rules configured in the system.
* **`Sol_JECreator.uis`**: Formats the cross-charge data into balanced journal entries and triggers action tasks for manual review. Once validated, it uploads the journal entries into the central database.

### Maestro Workflow
* **`SolMaestro_ICOPrepaidExpense.uis`**: The core master orchestrator connecting all AI agents and user review action apps.

### Human-in-the-Loop Action Apps
* **`EscalationApp_JEReview.uis`**: An Action App for reviewing and approving generated journal entries before final posting.
* **`EscalationApp_JournalMap.uis`**: An Action App to resolve missing journal account mapping entries.

## Data Fabric Schema
* **`HeadCountReport.csv`**
Contains schema and data for data fabric entity Head count mapping. This file contains Employee Id and Business unit data
* **`Journal Entry Sample Schema.csv`**
Contains schema of data fabric entity for Journal Entry
* **`JE Map.csv`**
Contains Schema and data for data fabric entity JE Map. This file contains Entity and its relevant account code mapping

# Setup Instructions:

## Orchestrator setup
* Create a Folder AgentHackathon in Default Tenant
* Add Uipath Datafabric and Gmail integration services in Connections.
* Add a Storage Bucket HeadCountReport and upload the HeadCountReport.csv file
* Create an Index HeadCountIndex pointing to the above created storage bucket.

## Data Fabric setup
* Import the Data Fabric schema from file DataFabricSchema.json file in the repo
* Import data in Head Count Mapping entity using the HeadCountReport.csv file in the repo
* Import data in Entity JE Map using the JE MAP.csv file in the Repo

## Studio Web:
* Import all the Agent Solution files(.uis) into studio web
* Import all the escalation files(.uis) into studio web
* Fix Connection issues if any and deploy the solution
* Import the maestro solution files(Solmaestro_ICOPrepaidExpense.uis) 
