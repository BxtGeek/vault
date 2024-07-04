# How to Create Tables in Linux

Follow the below commands:

```sh
yum install python
yum install pip
pip install prettytable
python

The above commands will install Python, pip, and PrettyTable. Now follow the below commands to create tables in Python:

from prettytable import PrettyTable

table = PrettyTable()
table.field_names = ["City name", "Area", "Population", "Annual Rainfall"]
table.add_row(["Adelaide", 1295, 1158259, 600.5])
print(table)

The output will look something like this:

+-----------+------+------------+----------------+
| City name | Area | Population | Annual Rainfall|
+-----------+------+------------+----------------+
| Adelaide  | 1295 |   1158259  |      600.5     |
+-----------+------+------------+----------------+
