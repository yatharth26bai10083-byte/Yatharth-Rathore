# Simple Electronics Shop

A small, menu-driven command-line shopping program written in pure Python. You can browse phones and laptops, add items to a cart, view the cart with a running total, and check out.

The program demonstrates core beginner Python concepts: `input()`, `if/elif/else`, `while` loops, lists, and dictionaries.

- **Main file:** `project2.py`
- **Language:** Python 3
- **External dependencies:** None (standard library only)
- **Configuration required:** None

---

## Table of Contents

1. [Prerequisites](#1-prerequisites)
2. [Get the Code](#2-get-the-code)
3. [Environment Setup](#3-environment-setup)
4. [Install Dependencies](#4-install-dependencies)
5. [Configuration](#5-configuration)
6. [Run the Project](#6-run-the-project)
7. [How to Use the Program](#7-how-to-use-the-program)
8. [Example Session](#8-example-session)
9. [Product Catalog](#9-product-catalog)
10. [Troubleshooting](#10-troubleshooting)
11. [Project Structure](#11-project-structure)
12. [Known Limitations](#12-known-limitations)

---

## 1. Prerequisites

You only need **Python 3.6 or newer** (any current Python 3 release works).

Check whether Python is already installed by opening a terminal (Command Prompt / PowerShell on Windows, Terminal on macOS/Linux) and running:

```bash
python --version
```

If that fails, try:

```bash
python3 --version
```

You should see something like `Python 3.11.5`. If neither command works, install Python from https://www.python.org/downloads/.

> **Windows tip:** During installation, tick **"Add Python to PATH"**.

> **Note:** On macOS and Linux, the command is usually `python3`. On Windows it is usually `python` (or `py`). Use whichever one worked above in all commands below.

You will also need **Git** to clone the repository (https://git-scm.com/downloads). If you do not want to install Git, you can instead download the code as a ZIP (see Step 2, Option B).

---

## 2. Get the Code

### Option A: Clone with Git (recommended)

```bash
git clone https://github.com/yatharth26bai10083-byte/Yatharth-Rathore.git
cd Yatharth-Rathore
```

### Option B: Download as ZIP

1. Open https://github.com/yatharth26bai10083-byte/Yatharth-Rathore
2. Click the green **Code** button, then **Download ZIP**.
3. Extract the ZIP file.
4. Open a terminal and move into the extracted folder:
   ```bash
   cd path/to/Yatharth-Rathore
   ```

Confirm you are in the right folder by listing its contents. You should see `project2.py`:

```bash
# macOS / Linux
ls

# Windows (Command Prompt)
dir
```

---

## 3. Environment Setup

A virtual environment is **optional** for this project because it uses no third-party packages. It is still good practice and keeps your system Python clean. If you want to skip it, go straight to [Step 6](#6-run-the-project).

### Create the virtual environment

```bash
# macOS / Linux
python3 -m venv venv

# Windows
python -m venv venv
```

### Activate it

```bash
# macOS / Linux
source venv/bin/activate

# Windows (Command Prompt)
venv\Scripts\activate.bat

# Windows (PowerShell)
venv\Scripts\Activate.ps1
```

When active, your terminal prompt will start with `(venv)`.

> **PowerShell error about scripts being disabled?** Run this once, then activate again:
> ```powershell
> Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
> ```

To leave the virtual environment later, run `deactivate`.

---

## 4. Install Dependencies

**There is nothing to install.** `project2.py` uses only built-in Python features (`print`, `input`, lists, dictionaries, loops) and imports no external modules. There is no `requirements.txt` because none is needed.

---

## 5. Configuration

**No configuration is required.** There are no environment variables, API keys, config files, or databases.

If you want to change the products or prices, edit the `phones` and `laptops` lists at the top of `project2.py`. Each item is a dictionary:

```python
{"name": "Product Name", "price": 12345}
```

Prices are whole numbers in Indian Rupees (Rs.).

---

## 6. Run the Project

From inside the project folder (the one containing `project2.py`), run:

```bash
# macOS / Linux
python3 project2.py

# Windows
python project2.py
```

You should see:

```
Welcome to the Electronics Shop!

What do you want to do?
1. Buy a phone
2. Buy a laptop
3. See my cart
4. Checkout
5. Exit
Enter 1, 2, 3, 4, or 5:
```

The program is now waiting for your input.

---

## 7. How to Use the Program

Type a number and press **Enter** at each prompt.

| Option | Action | What happens |
|--------|--------|--------------|
| `1` | Buy a phone | Lists phones. Enter a phone's number to add it to your cart. |
| `2` | Buy a laptop | Lists laptops. Enter a laptop's number to add it to your cart. |
| `3` | See my cart | Shows every item in your cart and the running total. |
| `4` | Checkout | Shows the final total, prints a thank-you message, and empties the cart. |
| `5` | Exit | Ends the program. |

Notes:

- You can add the same item more than once. Each addition is a separate entry in the cart.
- After each action, the main menu is shown again until you choose `5`.
- You can also stop the program at any time with **Ctrl + C**.

---

## 8. Example Session

Lines starting with `>` show what the user typed.

```
Welcome to the Electronics Shop!

What do you want to do?
1. Buy a phone
2. Buy a laptop
3. See my cart
4. Checkout
5. Exit
Enter 1, 2, 3, 4, or 5: > 1

Phones:
1. iPhone 15 - Rs. 109999
2. Samsung Galaxy S24 - Rs. 49998
3. iQOO Z10 - Rs. 35000
4. Redmi Note 14 - Rs. 20000
Choose a phone number: > 3
iQOO Z10 added to your cart.

What do you want to do?
...
Enter 1, 2, 3, 4, or 5: > 3

Your cart:
iQOO Z10 - Rs. 35000
Total: Rs. 35000

What do you want to do?
...
Enter 1, 2, 3, 4, or 5: > 4
Your total is Rs. 35000
Thank you for shopping with us!

What do you want to do?
...
Enter 1, 2, 3, 4, or 5: > 5
Goodbye!
```

### Quick test checklist for evaluators

Run through these to verify everything works:

1. Choose `3` on a fresh start. Expect: `Your cart is empty.`
2. Choose `4` on a fresh start. Expect: `Your cart is empty. Add something before checkout.`
3. Choose `1`, then enter `2`. Expect: `Samsung Galaxy S24 added to your cart.`
4. Choose `2`, then enter `1`. Expect: `MacBook Air M1 added to your cart.`
5. Choose `3`. Expect a two-item cart with total `Rs. 149997`.
6. Choose `1`, then enter `99`. Expect: `That number is not in the list.`
7. Choose `1`, then enter `abc`. Expect: `Please enter a number.`
8. Enter `9` at the main menu. Expect: `Please choose a number from 1 to 5.`
9. Choose `4`. Expect the total and the thank-you message; choosing `3` afterwards shows an empty cart.
10. Choose `5`. Expect `Goodbye!` and the program exits.

---

## 9. Product Catalog

**Phones**

| # | Name | Price (Rs.) |
|---|------|-------------|
| 1 | iPhone 15 | 109,999 |
| 2 | Samsung Galaxy S24 | 49,998 |
| 3 | iQOO Z10 | 35,000 |
| 4 | Redmi Note 14 | 20,000 |

**Laptops**

| # | Name | Price (Rs.) |
|---|------|-------------|
| 1 | MacBook Air M1 | 99,999 |
| 2 | MacBook Pro M3 | 179,999 |
| 3 | Lenovo LOQ RTX 3050 | 99,999 |

---

## 10. Troubleshooting

| Problem | Likely cause | Fix |
|---------|--------------|-----|
| `python: command not found` | Python not installed, or the command is `python3` | Install Python, or use `python3` (macOS/Linux) or `py` (Windows). |
| `'python' is not recognized...` (Windows) | Python not on PATH | Reinstall Python and tick **Add Python to PATH**, or use `py project2.py`. |
| `can't open file '...project2.py'` | You are in the wrong folder | Run `cd Yatharth-Rathore`, then confirm with `ls` / `dir` that `project2.py` is listed. |
| `SyntaxError` | Very old Python (2.x) | Use Python 3. Check with `python --version`. |
| Program seems to hang | It is waiting for your input | Type a menu number and press Enter. |
| Virtual environment will not activate in PowerShell | Script execution policy | See the PowerShell tip in [Step 3](#3-environment-setup). |

---

## 11. Project Structure

```
Yatharth-Rathore/
├── project2.py   # The complete Electronics Shop program
└── README.md     # This file
```

The repository may contain other files unrelated to this project; only `project2.py` is needed to run it.

---

## 12. Known Limitations

- The cart lives only in memory. Closing the program clears it.
- Checkout is simulated: no payment, receipt, or order history is created.
- There is no option to remove a single item from the cart.
- Prices and products are hard-coded in the source file.
- Only whole-number menu input is supported.

---

## Author

Yatharth Rathore
GitHub: https://github.com/yatharth26bai10083-byte
