---
title: How to make a SQL Server Database Read-Only and Read-Write
description: 
published: true
date: 2021-04-27T15:06:07.855Z
tags: 
editor: markdown
dateCreated: 2021-04-27T15:06:07.855Z
---

When you need to ensure that the data is a database is not modified by any users or automated processes, it is useful to set the database into a read-only mode. Once read-only, the data can be read normally but any attempts to create, updated or delete table rows is disallowed. This makes the read-only mode ideal when preparing for data migration, performing data integrity checking or when the data is only required for historical reporting purposes.

To make a database read-only, the following command is used:

```
ALTER DATABASE database-name SET READ_ONLY

```

If the read-only requirements for the database are temporary, you will need to reset the configuration option. This is achieved with a small modification to the ALTER DATABASE statement to indicate that the database should return to a writeable mode.

```
ALTER DATABASE database-name SET READ_WRITE
```

