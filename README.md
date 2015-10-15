# MySQL Partition Manager

A Node.js library for streamlining the backup and restore of MySQL partitions.

## Alpha

This library is in alpha. It works but it's not tested extensively.

## Installation

```
$ npm install node-mysqlpm --save
```

## Usage

```javascript
// core deps
var
    path = require('path');

// module deps
var
    MySQLPartitionManager = require('node-mysqlpm');

var
    options = {
        connection: {
            host: 'localhost',
            user: 'root'
        },
        backupDir: path.resolve(__dirname, './backup') // must be on the same machine that hosts MySQL instance,
        isDebug: true
    },
    pm = MySQLPartitionManager.forge(options);

pm.backup({
    schema: 'database_name',
    table: 'table_name',
    partition: 'partition_name'
}, function (error) {
    if (error) {
        throw error;
    }
});

pm.restore({
    schema: 'database_name',
    table: 'table_name',
    partition: 'partition_name'
}, function (error) {
    if (error) {
        throw error;
    }
});
```
