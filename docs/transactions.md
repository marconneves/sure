# Transactions Documentation

This document provides a comprehensive guide to managing transactions within the application.

## Introduction

A transaction represents a single financial event, such as a purchase, an income deposit, or a transfer between accounts. Each transaction is associated with an account and has various attributes that describe it in detail.

## Transaction Kinds

Transactions are categorized into different kinds, which affect how they are treated in budget analytics and reports.

- `standard`: A regular transaction, such as a purchase or an income deposit. These are included in budget analytics.
- `funds_movement`: Movement of funds between your own accounts. These are excluded from budget analytics.
- `cc_payment`: A payment to a credit card account. These are excluded from budget analytics as they offset the sum of expense transactions.
- `loan_payment`: A payment to a loan account. These are treated as an expense in budgets.
- `one_time`: A one-time expense or income that is not part of your regular budget. These are excluded from budget analytics.

## Creating a Transaction

To create a new transaction, you need to provide the following information:

### Required Fields

- `name`: A description of the transaction (e.g., "Groceries", "Salary").
- `account_id`: The ID of the account to which the transaction belongs.
- `amount`: The monetary value of the transaction.
- `date`: The date on which the transaction occurred.

### Optional Fields

- `category_id`: The ID of the category to which the transaction belongs.
- `merchant_id`: The ID of the merchant where the transaction took place.
- `tag_ids`: An array of tag IDs to associate with the transaction.
- `notes`: Any additional notes or details about the transaction.

Transactions can be created through the user interface by navigating to an account and clicking the "New Transaction" button.

## Reading Transactions

You can view a list of all transactions on the main "Transactions" page. The page provides various filters to narrow down the list of transactions:

- **Date Range:** Filter transactions by a specific start and end date.
- **Search:** Search for transactions by name.
- **Amount:** Filter transactions by amount using operators like "greater than," "less than," or "equal to."
- **Accounts:** Filter transactions by one or more accounts.
- **Categories:** Filter transactions by one or more categories.
- **Merchants:** Filter transactions by one or more merchants.
- **Types:** Filter transactions by their `kind`.
- **Tags:** Filter transactions by one or more tags.

## Updating a Transaction

To update an existing transaction, you can click on the transaction in the list to open the edit view. You can modify any of the transaction's attributes and save the changes.

## Deleting a Transaction

To delete a transaction, you can find the transaction in the account view and use the delete option.

## Recurring Transactions

If you have a transaction that occurs regularly (e.g., a monthly subscription), you can mark it as a recurring transaction. The application will then automatically create future occurrences of the transaction for you. To do this, find the transaction you want to mark as recurring and select the "Mark as Recurring" option.
