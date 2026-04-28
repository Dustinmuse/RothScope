# Project Description

## Summary

RothScope is a Roth conversion optimization tool being built for Moneytree and integrated into their existing financial planning platform. The system helps financial advisors (primary users) and potentially independent users (secondary users) evaluate when and how much to convert from tax-deferred retirement accounts into Roth accounts.

The tool combines user-provided financial data (income, expenses, account balances, assets, and retirement timelines) with Moneytree's calculation engine to evaluate baseline and conversion scenarios. It is designed to support strategy decisions by optimizing for outcomes such as minimizing cumulative taxes and maximizing ending after-tax assets, while preserving comparison, reporting, and long-term planning workflows.

## High-level Features

- Capture and manage client financial planning inputs, including retirement age, life expectancy, income, expenses, account balances

- Create and manage client scenarios with editable assumptions (retirement age and life expectancy) and assets

- Run baseline tax and capital calculations before any Roth conversions

- Define optimization objectives, including minimizing cumulative tax burden or maximizing ending total assets

- Execute iterative Roth conversion optimization using length of conversion, amount each year to convert, and what age to start converting combinations to determine an optimal strategy

- Compare optimized outcomes against alternative scenarios and saved runs

- Visualize results through summary metrics, conversion/tax graphs, and year-by-year breakdown table

- Save and reload optimization results for future planning sessions

- Export results for advisor/client communication (PDF and CSV export is supported)

## Non-Functional Requirements

- Security: encrypt sensitive financial data in transit and at rest

- Usability: provide clear, user-friendly forms and outputs with input validation

- Data safety: save user inputs after they go to the next page to reduce data loss risk

- Maintainability: use modular architecture and maintain at least 90% test coverage (unit + integration)

## Constraints

- Must integrate with Moneytree's existing software and use Moneytree's calculation engine/API for core evaluation logic

- Must align with advisor-centric workflows first (desktop-focused web experience), with mobile considerations treated as future scope

- Must operate with restricted external data access (Moneytree database/API access may be limited and controlled)
