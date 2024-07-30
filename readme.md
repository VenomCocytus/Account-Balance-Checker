# Account Balance Checker

This is a Python script that checks the account balance consistency for users in a MongoDB database.

## Description

The `account_balance_checker.py` script is designed to audit the account balances of users in a MongoDB database. It performs the following tasks:

1. Establishes a connection to a MongoDB database using the provided connection string.
2. Filters the `clt_user` collection to get users with specific currencies (**CAD**, **USD**, **EUR**).
3. For each user, it collects their wallet account IDs from the `accountWrapper` field.
4. For each wallet account, it queries the `clt_accounting_journal` collection to fetch the transaction history.
5. It then checks the consistency of the account balances by comparing the `balanceAfter` value of one transaction to the `balanceBefore` value of the next transaction, as well as checking if the `balanceAfter` value matches the `balanceBefore` value for the same transaction.
6. Any inconsistencies found are reported in an output file named `balance_check_results_{current_date}.txt`.
7. The script displays a progress bar using the `tqdm` library to show the progress of the balance checks.
8. Finally, it closes the MongoDB client connection.

## Installation

1. Clone the repository: `git clone [https://github.com/your-username/account-balance-checker.git](https://github.com/your-username/account-balance-checker.git)`

2. Install the required Python packages

```shell
pip install -r requirement.txt
```

## Usage

1. Update the MongoDB connection string in the `account_balance_checker.py` file with your own credentials.
2. Run the script using the command:

```shell
python account_balance_checker.py
```

1. The script will create an output file named `balance_check_results_{current_date}.txt` in the same directory, containing any detected balance inconsistencies.

## Dependencies

- `pymongo`: for interacting with MongoDB
- `bson`: for handling MongoDB document IDs and references
- `urllib.parse`: for handling URL encoding
- `datetime`: for working with dates and times
- `tqdm`: for displaying progress bars

## Contributing

If you find any issues or have suggestions for improvements, feel free to create a new issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
