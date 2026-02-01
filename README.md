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

## 5. Simple, Lovable, Complete (SLC)

The goal of the SLC is creating a simple, lovable, and complete system to track and analyze personal financial information. In this iteration, the system must allow:

- Defining a base monthly income
- Manually recording expenses (date, category, amount, optional note)
- Viewing a simple summary:
  - Total Spent in the month
  - Total Income in the month
  - Total Spents in the month
  - The most spent category and the most item spent
- Obtaining a simple AI-generated insight, for example:
  - A summary of the month's spending behavior
  - Detection of an obvious recurring expense

The SLC does not aim for optimization or depth, but to **close the complete loop**: data → system → interpretation.

| Simple | Lovable | Complete |
| :--- | :--- | :--- |
| The system focuses on a single main action: logging income and expenses one-by-one.<br>• No prior setup or unnecessary fields.<br>• Adding an expense or income is immediate and doesn't interrupt the user's flow.<br>• No hidden steps, mandatory configurations, or visible technical decisions. | After each entry, the system provides immediate clarity.<br>• The user can see how their money is distributed, quickly identify the largest monthly expense, and recognize their main source of income.<br>• The app doesn't judge or overwhelm with metrics; it translates data into simple signals that aid reflection.<br>• The value lies in the feeling of understanding, not in the amount of information displayed. | The experience is a closed loop from start to finish.<br>• The user can:<br>  1. Register their information.<br>  2. See its financial impact.<br>  3. Understand their current situation.<br>  4. Make a conscious decision.<br>• This happens without extra steps, payments, or reliance on external integrations.<br>• When the interaction ends, the user knows where their money is going and what most affects their monthly balance. |

## 6. Project Principles

- **Simplicity over completeness**
- **Explicit decisions over generic solutions**
- **Real utility before features**
- **Readable code before "clever" code**

---

## 7. Learning Objectives

- Modeling simple financial data
- System design applied to a real case
- Frontend and backend architecture
- Integrating AI focused on analysis and insight generation
- Building an open-source project with a clear scope and boundaries
