# autocat
Using GnuCash and piecash, replace the downloaded bank tranasction descriptions with one of your choosing and assign a different split account automatically.
## Usage

```
py autocat --config <yaml.config> --gnucashfile <you gnucash file>
```

## Format of config file
### YAML
This file contains the garbled description you get from the bank, the new description that you want in you GnuCash file, and optionally the new category you want for you transaction (ie, 'Expenses:Charity').

Ex:

```
---
# Format:
# -
#   payee: "<the name you want to read in reports"
#   orig_regex: "<a regex of the name that appears when you download transactions, could be just a substring>"
#   imbalance_new_account: "<the name of the new category you want instead of 'Imbalance'>"
#   only_in_account: '<account name>' # optional, only do the transformation for this particular account'
  - 
    payee: "Springfield Utilities"
    orig_regex: 'SPRINGFUTIL'
    imbalance_new_account: 'Expenses:Utilities'
```
### CSV
This file is just a plain text CSV file. If you give a *.csv file to the --config option, this is the format:

```
payee,orig_regex,imbalance_new_account
Springfield Utilities,SPRINGFUTIL,Expenses:Utilities
AT&T,ACH DEBIT ATT PHONE,Expenses:Phone
```

## Motivation
I wanted to stop paying Quicken's subscription fees. I didn't use any of the new features, and the only features I cared about were downloading bank/credit card transactions, renaming payees, and automatically categoriezing transactions. None of these warranted paying Quicken every year.

I found GnuCash. It doesn't do all the things I want, but it does have a way to make them happen.