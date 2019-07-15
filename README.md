## csv_utils

A small utility to display some metadata about the fields available in a "csv" (or otherwise delimited) data file.  This came about because I got tired of trying to determine the field lengths in a source data file that was very large and also wanted to learn some Rust.

[![Build Status](https://travis-ci.com/sullivant/csv_utils.svg?branch=master)](https://travis-ci.com/sullivant/csv_utils)

### Reminder

This is just here while I tinker with some "applied" learning of Rust - don't trust it to do what it says on the tin.

### Usage
```bash
$ ./csv_utils --help
CSV Utils 0.2.0
Thomas Sullivan <sullivan.t@gmail.com>
Shows some info on CSV files.

USAGE:
    csv_utils [FLAGS] [OPTIONS] <file>

FLAGS:
    -h, --help       Prints help information
    -q, --quotes     When passed, data is quoted.
    -s, --skip       When used, skips the first record (header)
    -V, --version    Prints version information

OPTIONS:
    -d, --delim <delim>        Sets the field delimiter to use, default is ','
    -m, --max <max_records>    When provided, will stop gathering data after N records

ARGS:
    <file>    Sets the input file to use
```
### Output
```bash
$ ./csv_utils ../tmp/file_of_data.csv -d'|'
175646 records in file (| delim).
Field	Max	Types % (i, f, c)			Title
1	9	(99.9994, 0.0000, 0.0006)		PK_ID
2	9	(99.9994, 0.0000, 0.0006)		EMPLOYEE
3	9	(99.9994, 0.0000, 0.0006)		BADGE_ID
4	9	(99.9989, 0.0000, 0.0011)		LOCATION
5	10	(0.0000, 0.0000, 100.0000)		START_DATE
```

### TODO
- [X] Use the crate "clap" as a way to pass CLI parameters
- [X] Allow for any single char passed as parameter
- [X] Allow for quoted values
- [X] Allow for field names to be gathered from header data instead of "field 1, field 2..."
- [ ] Test cases
- [ ] Prettier looking CLI output
###  Content of the fields
- [ ] Add more "metadata" to the output; instead of all the fields, maybe bucket them into sizes? ( wide files look odd in the results )
- [X] Which are always numeric?
- [ ] Which have no empty vals?
- [X] Trim extra spaces (eg: ```"Name", "Age","Location"```)
