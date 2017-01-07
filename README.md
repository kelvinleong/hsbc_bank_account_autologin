This script is a bot to auto login your HSBC account which free you from the tedious two way authentication!

## New Feature

* Support to auto login and download eStatement from HSBC credit card account
* Support Saving account and Credit card account statements download
* Visualize process schedule by threading
* Support statement type (credit and/or debit card) download configuration

## Prerequisite

- Python2.7 or above
- selenium (python library)
- chrome browser (above v51.0 update-to-date version is recommended)
- [Chrome Driver](https://sites.google.com/a/chromium.org/chromedriver/downloads)

## Setup

Replace Username, first password, second password to yours in the "Src/Scrapper".

For example,

```Python
    sec_pwd ="some_second_password"

    usr_name_input.send_keys("your_usr_name")

    firstPassword.send_keys("your_pass_word")
```

Specify the location of your chromedriver

```Python
  # Create a new instance of the Firefox driver
  driver = webdriver.Chrome("your_path/chromedriver")
```

Change the location where you want to save statements

```Python
  local_filename = "Your_path" + filename + ".pdf"
```

## Usage

To download all statements (both credit and debit card) from your account:

```
  Python AutoDownload.py -a -t cd
```

If you just want to download current monthly credit card statement,

```
  Python AutoDownload.py -d -t c
```

To retrieve a specific monthly debit card statement, you can type (currently, HSBC only stores the latest 24 months' statements for their client):

```
Python AutoDownload.py -m Mon-YYYY -t d(e.g., Python AutoDownload.py -m Jun-2016)
```

New:

-Set saving account statements issue day & credit card statement issue day
 ```
 line 63: if _day < 15 and _type == 'd (15 is my credit card statement issue day)
 line 159: if _day < 23 and _type == 'd' (23 is my saving account statements issue day)
 ```
-Download type setting

```
 Syntax
    [-t type]

 Flags
    Item
          Description
    -t    type
          specify download type for credit and/or debit card statement. ("c" for credit card, "d" for debit card)
          for example,
          -t cd (download both credit and debit card statement)
          -t c (only download credit card statement)
```
