🟢 Python datetime Module — Detailed Explanation

The datetime module in Python provides classes for manipulating dates and times in both simple and complex ways. It allows working with dates, times, intervals, formatting, and parsing.

🔹 1. Importing the datetime Module
import datetime
from datetime import date, time, datetime, timedelta


You can import the module or individual classes.

🔹 2. Date Objects
a) Creating a date object
from datetime import date

d = date(2025, 10, 17)  # year, month, day
print(d)  # Output: 2025-10-17

b) Current Date
today = date.today()
print(today)  # e.g., 2025-10-17

c) Date Components
print(today.year)   # 2025
print(today.month)  # 10
print(today.day)    # 17
print(today.weekday())  # 4 (Monday=0, Sunday=6)

d) Formatting Dates
print(today.strftime("%d-%m-%Y"))  # 17-10-2025
print(today.strftime("%A, %B %d, %Y"))  # Friday, October 17, 2025

🔹 3. Time Objects
a) Creating a time object
from datetime import time

t = time(14, 30, 15)  # hour, minute, second
print(t)  # 14:30:15

b) Time Components
print(t.hour)    # 14
print(t.minute)  # 30
print(t.second)  # 15

c) Formatting Time
print(t.strftime("%H:%M:%S"))  # 14:30:15

🔹 4. Datetime Objects

datetime combines date and time into a single object.

a) Creating a datetime object
from datetime import datetime

dt = datetime(2025, 10, 17, 14, 30, 15)
print(dt)  # 2025-10-17 14:30:15

b) Current Date & Time
now = datetime.now()
print(now)  # e.g., 2025-10-17 09:15:30

c) Components
print(now.year, now.month, now.day)
print(now.hour, now.minute, now.second)

d) Formatting datetime
print(now.strftime("%d/%m/%Y %H:%M:%S"))  # 17/10/2025 09:15:30

🔹 5. Timedelta — Working with Intervals

timedelta represents a duration, difference between two dates/times.

a) Creating Timedelta
from datetime import timedelta

delta = timedelta(days=5, hours=3, minutes=30)
print(delta)  # 5 days, 3:30:00

b) Adding/Subtracting Time
future_date = datetime.now() + timedelta(days=10)
past_date = datetime.now() - timedelta(weeks=2)
print(future_date)
print(past_date)

c) Difference Between Dates
d1 = date(2025, 10, 17)
d2 = date(2025, 11, 1)
diff = d2 - d1
print(diff.days)  # 15

🔹 6. Parsing Strings into Dates
date_str = "2025-10-17"
dt_obj = datetime.strptime(date_str, "%Y-%m-%d")
print(dt_obj)  # 2025-10-17 00:00:00


strptime() → String to datetime

strftime() → Datetime to string

🔹 7. Common Formats (strftime / strptime codes)
Code	Meaning
%Y	Year (4 digits)
%y	Year (2 digits)
%m	Month (01-12)
%B	Full month name
%b	Short month name
%d	Day of the month (01-31)
%A	Full weekday name
%a	Short weekday name
%H	Hour (00-23)
%I	Hour (01-12)
%M	Minute (00-59)
%S	Second (00-59)
%p	AM / PM
🔹 8. Time Comparison & Operations
from datetime import datetime

dt1 = datetime(2025, 10, 17, 10, 0, 0)
dt2 = datetime(2025, 10, 17, 15, 0, 0)

print(dt2 > dt1)   # True
print(dt2 - dt1)   # 5:00:00


Datetime objects support comparison operators and arithmetic with timedelta.

🔹 9. Best Practices

Always use datetime for operations involving both date and time.

Use strftime() and strptime() for converting between strings and datetime objects.

Prefer timedelta for adding/subtracting durations instead of manually manipulating date/time.

Handle timezones carefully (consider pytz or zoneinfo in Python 3.9+).