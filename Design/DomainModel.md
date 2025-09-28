# Domain Model

Jaydon Buckler
9/28/25
Version 1.0 
(Will be subject to change as we continue project)

## UML Class Diagram

```mermaid
classDiagram
direction LR

%% Actors / Parties
class Advisor {
    +advisorId: UUID
    +name: string
    +firm: string
    +email: string
}

class Client {
    +clientId: UUID
    +primaryName: string
    +householdType: enum
    +dateOfBirthPrimary: date
    +dateOfBirthSecondary?: date
}

Advisor "1" --> "0..*" Plan : manages >
Client "1" --> "1..*" Plan : owns >

%% Plan & Inputs
class Plan {
    +planId: UUID
    +name: string
    +createdAt: datetime
    +retirementAge: int
    +lifeExpectancy: int
}

class Assumptions {
    +inflationRate: decimal
    +taxRegime: string
    +capitalReturnTaxable: decimal
    +capitalReturnTaxDeferred: decimal
    +capitalReturnRoth: decimal
}

Plan o-- Assumptions : uses >

%% Accounts
class Account {
    <<abstract>>
    +accountId: UUID
    +name: string
    +startBalance: money
    +expectedReturn: decimal
}

class TaxableAccount
class TaxDeferredAccount {
    +rmdStartAge: int
}
class RothAccount

Account <|-- TaxableAccount
Account <|-- TaxDeferredAccount
Account <|-- RothAccount

Plan *-- "0..*" Account : includes >

%% Cash Flows
class CashFlow {
    <<abstract>>
    +year: int
    +amount: money
    +description?: string
}

class Income
class Expense

CashFlow <|-- Income
CashFlow <|-- Expense
Plan *-- "0..*" CashFlow : schedules >

%% Baseline + Objectives / Guardrails
class BaselineResult {
    +baselineId: UUID
    +lifetimeTaxNPV: money
    +endingAfterTaxAssets: money
    +peakMarginalBracket: percent
    +irmaaTiersHit: int
}

Plan o-- BaselineResult : computes >

class Objective {
    +primary: enum // MIN_TAX | MAX_ASSETS
    +tieBreaker?: enum
    +weights?: json
}

class Guardrails {
    +maxMarginalBracket?: percent
    +maxIrmaaTier?: int
    +annualConverstionCap?: money
    +notes?: string
}

Plan o-- Objective
Plan o-- Guardrails

%% Conversion Schedule
class ConverstionSchedule {
    +scheduleId: UUID
    +startAge: int
    +lengthYears: int
}

class ConversionYear {
    +age: int
    +amountFromTaxDeferred: money
}

ConversionSchedule *-- "1..*" ConversionYear
Plan o-- ConversionSchedule : candidate/optimal >

%% Optimization Run & Results
class OptimizationRun {
    +runId: UUID
    +status: enum // QUEUED|RUNNING|COMPLETED|FAILED
    +startedAt: datetime
    +finishedAt?: datetime
    +bestScore: decimal
}

class KPIResult {
    +lifetimeTaxNPV: money
    +endingAfterTaxAssets: money
    +peakMarginalBracket: percent
    +irmaaTiersHit: int
}

OptimizationRun o-- ConversionSchedule : evaluates >
OptimizationRun o-- KPIResult : outputs >
Plan *-- "0..*" OptimizationRun : tracks >

%% External Engine Boundary
class MoneytreeEngine {
    <<external>>
    +evaluate(plan, schedule): KPIResult
}

OptimizationRun ..> MoneytreeEngine : calls >
```

## Class Glossary

- **Advisor** - Professional user (financial planner) operating RothScope; used for access control and attribution.
- **Client** - The household being planned for; demographics drive retirement and life expectancy modeling.
- **Plan** - Scenario container linking assumptions, accounts, cash flows, objectives/guardrails, and results.
- **Assumptions** - Economic/tax parameters (inflation, returns per account type, tax regime) independent of decisions.
- **Account / TaxableAccount / TaxDeferredAccount / RothAccount** - Financial buckets with different tax behaviors (RMDs for tax-deferred; tax-free growth in Roth).
- **CashFlow / Income / Expense** - Time-indexed inflows/outflows shaping taxable income and feasibility.
- **BaselineResult** - KPIs for the "as-is" plan (no conversions) used as comparison.
- **Objective** - Optimization goal (minimize taxes or maximize ending after-tax assets).
- **Guardrails** - Advisors constraints (cap bracket, annual conversion cap).
- **ConversionSchedule / ConversionYear** - Year-by-year Roth conversion plan (when/how much).
- **OptimizationRun** - One optimization execution tracking status, best score, and outputs.
- **KPIResult** - Metrics returned by the engine for a schedule (lifetime taxes NPV, ending assets, peak bracket).
- **MoneytreeEngine** - External calculator evaluating a plan + schedule.


