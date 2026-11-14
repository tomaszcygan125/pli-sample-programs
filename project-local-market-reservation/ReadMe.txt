Marketplace Reservation System

This is a console-based marketplace reservation application written in
PL/I. It provides account management and reservation processing using
local text files.

Main features

Users can create an account, log in, change their password, make
reservations, and view their own reservations.

Administrators can view all reservations, cancel a reservation, and
block normal user accounts with a reason.

The application displays the marketplace layout and information about
available spots, including their size and daily price.

Data files

marketplace_login_data.txt stores account details: login, password,
account type, blocked status, and blockade message. Each record is 110
characters long.

marketplace_reservations.txt stores reservation details: spot number,
username, start date, end date, and reservation duration. Each record is
66 characters long.

marketplace_layout.txt contains the marketplace layout displayed to the
user.

marketplace_spots.txt contains information about the available spots.

Reservation rules

A reservation date must use the YYYY.MM.DD format and must not be in the
past. The end date cannot be earlier than the start date. The
reservation duration cannot exceed 50 days. Both the start and end dates
are counted when calculating the duration.

A spot cannot be reserved when an existing reservation for the same spot
overlaps the requested date range.

Account types

A normal account has access to personal reservation functions and
password changes.

An administrator can manage reservations and block normal user accounts.

Implementation notes

The application uses sequential access to flat files and fixed-size
in-memory tables. The login file and reservation file must exist and
contain records in the expected fixed-length format. The application is
intended as a small demonstration project rather than a production-ready
reservation service.

Security and reliability limitations

Passwords are stored as plain text and should not be used this way in a
real application. File updates rewrite the complete data file, and the
fixed-size tables have a capacity of 1000 records. The current
implementation should be reviewed and tested carefully before use,
especially date validation, end-of-file handling, and file update
operations.