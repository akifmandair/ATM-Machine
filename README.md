💳 README: ATM Machine Application
This document outlines the functional requirements and system interactions for the Automated Teller Machine (ATM) Application, based on the provided UML Use Case Diagrams.

📝 Overview
The ATM Machine system provides customers with self-service financial transaction capabilities and includes administrative functions for maintaining the machine and monitoring activity.

👥 Actors
The primary entities interacting with the ATM System are:

Customer: The bank account holder who performs financial transactions.

Technician: The staff responsible for physical maintenance and replenishing supplies.

Bank Admin: The staff responsible for monitoring system activity and generating reports.

Bank System: The critical external system that handles all account validation, authorization, and balance updates.

🛠️ Key Use Cases (Functional Requirements)
A. Customer-Initiated Functions (Transaction Flow)
Use Case	Description	Relationship/Dependency
Perform Transaction	An abstract, high-level use case representing the overall goal of the customer session (Withdrawal, Deposit, etc.).	Generalizes specific transaction types (Withdrawal, Deposit, Transfer, Check Balance).
Cash withdrawal	Dispenses cash to the customer.	Specialization of Perform Transaction.
Deposit	Accepts cash/checks for deposit.	Specialization of Perform Transaction.
Transfer funds	Moves money between two accounts.	Specialization of Perform Transaction.
Check balance	Retrieves and displays the current account balance.	Specialization of Perform Transaction.
Authentication	Verifies the card and PIN to grant access to transactions.	Includes the mandatory step Validation.
Print recipt	Provides a physical record of the transaction.	Associated with the completion of a transaction.
Eject card	Returns the card to the customer, typically at the end of the session.	Associated with the completion of a session.

B. System and External Bank Functions
Use Case	Description	Initiated By	Relationship/Dependency
Validation	The system checks the card status (e.g., active, expired) against the Bank System.	Included by Authentication.	
Update balance	Sends transaction data (e.g., amount withdrawn) to the external server to debit/credit the account.	Bank System receives data from Perform Transaction flow.	
Authorize transaction	The external Bank System approves or denies a transaction request based on funds and limits.	Bank System is involved in all financial transactions.	

C. Maintenance and Administrative Functions
Use Case	Description	Actor
Maintain ATM Machine	General administrative and physical upkeep of the machine.	Technician
Refill cash	Replenishes the cash dispenser with currency.	Technician
Monitor transactions	Tracks and reviews the activity log for security, usage, and fraud detection.	Bank Admin
Generate reports	Compiles summaries of transactions, cash levels, and errors for audit and business intelligence.	Bank Admin

🔗 Key Relationships (UML Notation)
Generalization (Hierarchy): Specific transaction types (Cash withdrawal, Deposit, etc.) are a kind of (Perform Transaction).

Inclusion (<<include>>): The Authentication process is required for every session and includes the step of Validation by the Bank System.

Association: The Customer uses the main transaction functions, while the Bank System is associated with all financial use cases to handle the account status.
