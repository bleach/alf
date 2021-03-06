
Alf - A log filter
==================

This is my log filter. There are many like it, but this one is mine.

Alf is intended to be a convenient way of performing common extraction
and processing tasks on webserver log files:

- Selecting lines based on field contents such as url or status code.
- Extracting only certain fields from logfiles.
- Counting the number of lines that match a pattern.

It currently parses some of the more commonly used apache formats, but it
could parse many others, with a little work.

I am currently not very happy with the command line options, so it is likely
that I will change both their names and the defaults in future commits.

Installing
----------

You will need Python >= 2.4 installed.

- Download the file 'alf' either 
 - from https://github.com/bleach/alf/raw/master/alf
 - or via git by doing "git clone git@github.com:bleach/alf.git"
- Copy the file alf into your $PATH

If you have the psyco pythom module installed, alf will use it in an attempt to
improve performance. 

Examples
--------

1. Extract all the logged requests which had the status code 404:

    alf --status-regex='404' logfile

2. Extract all the requests to /robots.txt:

    alf --url-regex='^/robots.txt' logfile

TODO
----

Tech debt:

- Make a log format a more structured thing including:
  - regex for parsing the log
  - knowledge of how to translate timestamp fields into a python datetime
- Address the confusion when you --print-invalid and --print-lines at the same time

Features:

- Detect log formats automatically.
- Query on fields which are in non-default log formats.
- Add an option to sort output by date.
- Configuration file to add more log formats.
- Make it easier to call alf from other scripts.

Internals:

- Testing:
 - Unit tests.
 - Test runner to run tests on all supported python versions.
 - Simple integration tests against sample logfiles.
 - Performance benchmarks.

