# Finance lab

| version | date         | status      |
| ------- | ------------ | ----------- |
| v0.1    | Jan 19, 2026 | in progress |

## 1. Problem

I currently do not have a centralized system for tracking and analyzing my **expenses**, **monthly income**, **investments**, and **savings goals**.  
This lack of visibility makes it difficult to understand the relationship between what I earn, what I spend, and what I can save, as well as to identify simple spending patterns that could help me make more informed financial decisions.

Existing solutions are often complex, closed-source, or focused on multiple use cases that do not necessarily fit my personal needs.

---

## 2. Project Goal

Build a simple web application that allows for recording personal financial information and generating **basic insights** from that data.

This project serves as a **practical lab** for:

- Small-scale system design
- Conscious architectural decision-making
- Simple data modeling
- Using AI as a support tool for analysis, not for total automation

The project is **open source** and designed so that anyone can run and adapt it locally.

---

## 3. Scope (what's IN)

- Manual expense entry
- Recording simple (manual) monthly income
- Recording basic investments
- Defining and tracking savings goals
- Basic data visualization (totals, simple comparisons)
- Generating simple insights with AI assistance
- Session management for a single user
- Data persistence

---

## 4. Out of Scope (what's OUT)

- Integration with banking entities
- Multi-user support
- Formal or tax accounting
- Advanced financial security
- Native mobile application
- Complex AI-based automations

---

## 5. MVP (v0.1)

The goal of the MVP is to **validate the product's complete flow**, from data entry to generating minimum user value. In this first version, the system must allow:

- Defining a base monthly income
- Manually recording expenses (date, category, amount, optional note)
- Viewing a simple summary:
  - Total spent in the month
  - Basic expense vs. income comparison
- Obtaining a simple AI-generated insight, for example:
  - A summary of the month's spending behavior
  - Detection of an obvious recurring expense

The MVP does not aim for optimization or depth, but to **close the complete loop**: data → system → interpretation.

---

## 6. Post-MVP

Once the MVP is validated and its real limitations are understood, the project could evolve towards:

- Savings goals with visual progress
- Month-to-month comparisons
- Automatic expense categorization
- More elaborate insights (trends, soft alerts)
- Data export

These ideas are not commitments, only **possible directions** that will be evaluated based on the product's actual use.

---

## 7. Project Principles

- **Simplicity over completeness**
- **Explicit decisions over generic solutions**
- **Real utility before features**
- **Readable code before "clever" code**

---

## 8. Learning Objectives

- Modeling simple financial data
- System design applied to a real case
- Frontend and backend architecture
- Integrating AI focused on analysis and insight generation
- Building an open-source project with a clear scope and boundaries
