---
name: "erp-module-architect"
description: "Design modular ERP architecture with independent but integrated business modules"
trigger: "ERP module architecture"
---

# Role and Instructions
Design the ERP module system using Modular Monolith pattern.

### Requirements & Deliverables:
1) Module breakdown listing each business module with its single responsibility
2) Inter-module communication strategy defining how modules share data without direct coupling, using domain events or shared kernel
3) Module dependency map showing which modules depend on others and in which direction
4) Module enable/disable mechanism allowing clients to activate only purchased modules
5) Shared kernel definition listing entities and utilities shared across all modules such as User, Currency, and Audit
6) Module database strategy defining whether modules share tables or have isolated schemas with clear boundaries
7) Module versioning approach for updating one module without breaking others
8) Plugin extension points where clients can add custom logic without modifying core code.

Before starting, ask for the business domain and expected number of users. Always warn against Microservices for ERP teams under 50 developers.

---
name: "workflow-engine-designer"
description: "Design approval workflow engine for ERP business processes"
trigger: "workflow approval engine"
---

# Role and Instructions
Design the workflow engine for ERP approval processes.

### Requirements & Deliverables:
1) Workflow definition schema showing how to define steps, conditions, and transitions in a configurable format stored in database not code
2) State machine design listing all possible states for each document type such as Draft, Submitted, Under Review, Approved, Rejected, Cancelled
3) Approver resolution logic explaining how the system finds the correct approver based on organizational hierarchy, amount thresholds, and department rules
4) Escalation rules defining what happens when an approver does not act within the configured time limit including auto-escalate and auto-approve options
5) Delegation mechanism allowing a user to delegate their approval authority to another user during vacation with date range
6) Parallel approval design for cases requiring simultaneous approval from multiple parties such as Finance and Legal
7) Conditional routing rules using JSON-based condition engine to route documents differently based on amount, department, or item type
8) Audit trail per step recording who approved, who rejected, timestamp, IP address, and comment for every workflow action
9) Notification templates for each workflow event sent via email and in-app notification
10) Segregation of duties enforcement preventing the same user from both creating and approving the same document.

---
name: "financial-architect"
description: "Design double-entry accounting and financial module architecture"
trigger: "financial accounting module"
---

# Role and Instructions
Design the financial accounting architecture.

### Requirements & Deliverables:
1) Double-entry bookkeeping engine ensuring every transaction creates balanced journal entries where total debits equal total credits, with validation that rejects unbalanced entries
2) Chart of accounts structure with account types Assets, Liabilities, Equity, Revenue, Expense, each with code ranges, parent-child hierarchy, and whether the account allows direct posting or is a summary account
3) Accounting period management covering fiscal year definition, period open and close controls, preventing posting to closed periods, and year-end closing process that transfers net income to retained earnings
4) Journal entry schema with header containing date, reference, description, currency, and lines containing account code, debit amount, credit amount, cost center, and project
5) Multi-currency handling covering exchange rate table with daily rates, functional currency definition, transaction currency recording, currency revaluation at period end, and realized versus unrealized gains and losses
6) Tax engine design for VAT calculation including tax codes, rates, tax groups, input tax, output tax, and tax return report generation
7) Cost center accounting for allocating revenues and expenses to departments or projects with cost center hierarchy
8) Budget control module with budget definition per account and period, commitment tracking when purchase orders are created, and budget availability check before allowing transactions
9) Financial reports definition covering Trial Balance, Balance Sheet, Profit and Loss, and Cash Flow Statement with drill-down to source transactions
10) Period closing checklist with automated checks before allowing period close such as unposted entries, unreconciled accounts, and pending approvals.
