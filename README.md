# Personal Expense Tracker

A command-line application written in Python that helps you record daily expenses,
set a monthly budget, and see where your money goes. Data is stored locally in a
SQLite database, so no internet connection or third-party packages are needed.

## Features

- Add expenses with amount, category, date and an optional note
- Seven categories: Food, Transport, Bills, Shopping, Health, Fun, Other
- Set a budget per month and see how much is left (or how much you overspent)
- Monthly summary with a text bar chart for each category
- List and filter expenses by month and category
- Delete a wrong entry by its id
- Export expenses to a CSV file (opens in Excel or Google Sheets)
- Input validation with clear error messages

## Requirements

- Python 3.8 or newer
- No external libraries (standard library only: `sqlite3`, `argparse`, `csv`, `datetime`)

## Project structure

```
expense_tracker_project/
├── main.py                  # entry point
├── expense_tracker/
│   ├── __init__.py
│   ├── db.py                # database and validation logic
│   └── cli.py               # command-line interface
├── tests/
│   └── test_db.py           # unit tests
├── requirements.txt
├── README.md
└── REPORT.md                # full project report
```

## How to run

Open a terminal in the project folder and run commands with `python main.py`
(use `python3` on Mac/Linux).

```bash
# set a budget for the month
python main.py budget 15000 -m 2026-09

# add expenses (date defaults to today)
python main.py add 450 food -n "Lunch with friends" -d 2026-09-03
python main.py add 1200 bills -n "Electricity"

# list expenses (optionally filter)
python main.py list -m 2026-09
python main.py list -c food

# monthly summary
python main.py summary -m 2026-09

# delete an expense by id
python main.py delete 3

# export to CSV
python main.py export september.csv -m 2026-09
```

Run `python main.py --help` or `python main.py <command> --help` for all options.

By default the database is saved as `.expense_tracker.db` in your home folder.
Use `--db path/to/file.db` to store it somewhere else.

## Example output

```
Summary for 2026-09
--------------------------------------------
Spent : Rs 4,450.00
Budget: Rs 15,000.00
[#########.....................] 30%
Left  : Rs 10,550.00

By category
  Shopping   [#################.............] Rs 2,500.00
  Bills      [########......................] Rs 1,200.00
  Food       [###...........................] Rs 450.00
  Transport  [##............................] Rs 300.00
```

## Running the tests

```bash
python -m unittest discover -s tests -v
```

## Possible improvements

Recurring expenses, custom categories, charts, a Tkinter or web interface,
and multi-currency support. See `REPORT.md` for the full list.
