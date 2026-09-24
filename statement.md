# Project Statement: Console-Based Electronics Shopping System

## 1. Problem Statement

Beginners learning Python often practise `input()`, `print()` and `if` statements on tiny, unconnected exercises. These rarely show how those pieces combine into a complete program with menus, data, validation and state.

An earlier version of this project, a single notebook cell of nested `if`/`elif` branches, showed the idea but had clear weaknesses:

- Product names and prices were repeated inside many branches, so changing a price meant editing code in several places.
- Input was compared as exact text, so `mobile` and `Mobile` were treated as different answers, and invalid entries were not handled helpfully.
- A user could pick only one product per run. There was no cart, no total and no way to change their mind.

This project solves that by providing a small, realistic console shop in which a user can browse products, build a cart, correct mistakes and check out. The code is organised into separate modules so a learner can read, test and extend each part on its own.

## 2. Scope of the Project

### In scope

- A text-based, single-session shopping flow that runs in any terminal.
- Two product categories, **Phones** (4 products) and **Laptops** (3 products), stored in a JSON data file rather than in the code.
- Browsing products with prices shown in Indian digit grouping (for example, `Rs. 1,09,999`).
- A cart that merges repeated products into one line with a quantity (maximum 10 per product), shows line totals and a grand total, and lets the user remove items.
- Validated input: every menu re-prompts until the entry is valid.
- Checkout with an order summary and a yes/no confirmation.
- Startup validation of the catalogue file, with a clear error message if it is missing or malformed.
- Unit tests for the cart logic, price formatting, input helpers, checkout and catalogue validation.

### Out of scope

- Graphical or web interface.
- Payment processing, user accounts and authentication.
- Stock levels, tax, shipping, discounts.
- Saving carts or orders between runs (the cart exists only during one session).
- Product variants such as storage sizes.
- Verified real-world prices. Catalogue prices are **sample data** and are not checked against any retailer.

## 3. Target Users

| User | How they use the project |
|---|---|
| **Beginner Python learners and students** (primary) | Run it to see how menus, loops, functions, dictionaries and validation fit together, then extend it (for example, add a category by editing `data/catalogue.json`). |
| **Instructors and evaluators** | Review a small but complete, modular and tested example of a console application. |
| **Simulated shoppers** | Use the console interface as an end user would: browse, add, remove and check out. This is a demonstration, not a live store. |

Users need only Python 3.6 or later. No third-party libraries are required.

## 4. High-Level Features

1. **Category browsing.** The main menu is generated from the catalogue, so each category in the data file becomes a menu option automatically.
2. **Product listing.** Numbered products with formatted prices, and a `0` option to go back.
3. **Shopping cart.** Adding the same product again increases its quantity. The cart shows each line total and the overall total.
4. **Item removal.** Remove one unit of an item; the line disappears when its quantity reaches zero.
5. **Checkout.** Order summary, then y/n confirmation. The cart is cleared only if the user confirms.
6. **Input validation.** Whole-number menu choices are range-checked, yes/no answers accept `y`, `yes`, `n`, `no` in any capitalisation, and invalid entries are re-prompted instead of failing.
7. **Safe exit.** The program warns before exiting with items in the cart and exits cleanly on Ctrl+C or end of input.
8. **Data-driven catalogue.** Products and prices are edited in `data/catalogue.json`, and the file is validated when the program starts.
9. **Configuration.** The currency label and the per-item quantity limit are set in `shop/config.py`.
10. **Automated tests.** Run with `python -m unittest discover`.

## 5. Project Structure

```
electronics_shop/
├── main.py                 # Entry point and main menu loop
├── statement.md            # This document
├── README.md               # How to run and test
├── data/
│   └── catalogue.json      # Product data (categories, names, prices)
├── shop/
│   ├── __init__.py
│   ├── config.py           # Settings: currency label, quantity limit, file path
│   ├── catalogue.py        # Load and validate the catalogue file
│   ├── cart.py             # Cart logic (no input/print, easy to test)
│   └── ui.py               # Console input, formatting and menus
└── tests/
    ├── test_cart.py
    ├── test_catalogue.py
    └── test_ui.py
```
