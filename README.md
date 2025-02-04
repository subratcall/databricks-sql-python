# Databricks SQL Connector for Python

[![PyPI](https://img.shields.io/pypi/v/databricks-sql-connector?style=flat-square)](https://pypi.org/project/databricks-sql-connector/)
[![Downloads](https://pepy.tech/badge/databricks-sql-connector)](https://pepy.tech/project/databricks-sql-connector)

The Databricks SQL Connector for Python allows you to develop Python applications that connect to Databricks clusters and SQL warehouses. It is a Thrift-based client with no dependencies on ODBC or JDBC. It conforms to the [Python DB API 2.0 specification](https://www.python.org/dev/peps/pep-0249/).

This connector uses Arrow as the data-exchange format, and supports APIs to directly fetch Arrow tables. Arrow tables are wrapped in the `ArrowQueue` class to provide a natural API to get several rows at a time.

You are welcome to file an issue here for general use cases. You can also contact Databricks Support [here](help.databricks.com).

## Requirements

A development machine running Python >=3.7, <3.10.

## Documentation

For the latest documentation, see

- [Databricks](https://docs.databricks.com/dev-tools/python-sql-connector.html)
- [Azure Databricks](https://docs.microsoft.com/en-us/azure/databricks/dev-tools/python-sql-connector)

## Quickstart

Install the library with `pip install databricks-sql-connector`

Example usage:

```python
from databricks import sql

connection = sql.connect(
  server_hostname='********.databricks.com',
  http_path='/sql/1.0/endpoints/****************',
  access_token='dapi********************************')


cursor = connection.cursor()

cursor.execute('SELECT * FROM RANGE(10)')
result = cursor.fetchall()
for row in result:
  print(row)

cursor.close()
connection.close()
```

In the above example:
- `server-hostname` is the Databricks instance host name.
- `http-path` is the HTTP Path either to a Databricks SQL endpoint (e.g. /sql/1.0/endpoints/1234567890abcdef),
or to a Databricks Runtime interactive cluster (e.g. /sql/protocolv1/o/1234567890123456/1234-123456-slid123)
- `personal-access-token` is the Databricks Personal Access Token for the account that will execute commands and queries


## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md)

## License

[Apache License 2.0](LICENSE)
