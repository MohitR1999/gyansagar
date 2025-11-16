---
title: Database Design
---
So here I'll describe the database structure of the system. I'd highly recommend to check out the requirements [[Requirements|here]] and the system design [[SystemDesign|here]] before reading further on.

I'll be using a relational database (MySQL) for this project, so expect tables and joins and relationships :)

Here's a diagram representing the tables in the system:
![[database-design.png]]

We have 2 databases in the system, one that is manipulated by the *auth service*, and the other one that is handled by the *money handler service*.

- The **Users** table present in *auth-db* is concerned with the user specific properties, such as their email and password and their name
- The **CashFlows** and **CashFlowCategories** tables model the details of the expenses/income of the user, and they are linked by the `user_id` attribute which specifies the user to which the cash flow or the category belongs to.
- Each *CashFlowCategory* has 2 important properties, the `category` and the `sub_category`, `category` can be either **INCOME** or **EXPENSE** as these are the only two ways money can flow in or out from the user's account. The `sub_category` is essentially the type of **INCOME** or **EXPENSE**, which for example, can be `Income from salary` or expense towards `Food`.
- Each **CashFlow** has a `category` and `sub_category`, which are picked from the *CashFlowCategories*, and in addition to that, it has an `amount`, specifying the amount of money involved in the flow, and the `date` on which the transaction occurred. I've deliberately added some redundancy over here in order to reduce the number of joins we would encounter.
- This structure is very minimal and barebones in order to fulfil the goals of MVP. I'll enhance the structure in future as needed.