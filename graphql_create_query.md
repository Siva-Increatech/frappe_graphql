# 🧩 Frappe GraphQL Queries and Variables

This document provides a collection of GraphQL mutations and variable examples for managing Parent and Child Doctypes in Frappe using the bulkcreate mutation.

## ⚙️ Bulk Create Query (Table MultiSelect)

#### QUERY

``` 
mutation {
  bulkCreate(
    doctype: "ToDo"
    fields: [
      {
        fields: "{ \"priority\": \"Medium\", \"description\": \"create Multiselect 1\", \"child_table\": [ { \"fields\": \"skkkom4kbt\" }, { \"fields\": \"nk2la9mvu3\" }, { \"fields\": \"tl8aq6urbt\" } ] }"
      },
      {
        fields: "{ \"priority\": \"Medium\", \"description\": \"create Multiselect 2\", \"child_table\": [ { \"fields\": \"skkkom4kbt\" }, { \"fields\": \"nk2la9mvu3\" }, { \"fields\": \"tl8aq6urbt\" } ] }"
      },
      {
        fields: "{ \"priority\": \"Medium\", \"description\": \"create Multiselect 3\", \"child_table\": [ { \"fields\": \"skkkom4kbt\" }, { \"fields\": \"nk2la9mvu3\" }, { \"fields\": \"tl8aq6urbt\" } ] }"
      }
    ]
  ) {
    status
    doctype
    docs {
      name
      fields
    }
  }
}

```

#### RESPONSE

```
{
    "data": {
        "bulkCreate": {
            "status": true,
            "doctype": "ToDo",
            "docs": [
                {
                    "name": "pkigh2a9kg",
                    "fields": "{ \"priority\": \"Medium\", \"description\": \"create Multiselect 1\", \"child_table\": [ { \"fields\": \"3ps2tfa3ga\" }, { \"fields\": \"3psbe59pnd\" } ] }"
                },
                {
                    "name": "pki8ifkdft",
                    "fields": "{ \"priority\": \"Medium\", \"description\": \"create Multiselect 2\", \"child_table\": [  { \"fields\": \"3ps2tfa3ga\" }, { \"fields\": \"3psbe59pnd\" } ] }"
                },
                {
                    "name": "pkibbnnnhu",
                    "fields": "{ \"priority\": \"Medium\", \"description\": \"create Multiselect 3\", \"child_table\": [  { \"fields\": \"3ps2tfa3ga\" }, { \"fields\": \"3psbe59pnd\" } ] }"
                }
            ]
        }
    }
}
```


## ⚙️ Bulk Create Query (LINK)

#### QUERY

``` 
mutation {
    bulkCreate(
        doctype: "Item"
        fields: [
            {
                fields: "{ \"item_code\": \"ITEM-0001\", \"item_name\": \"Test Product 1\", \"item_group\": \"Products\",\"stock_uom\": \"Nos\"}"
            }
            {
                fields: "{ \"item_code\": \"ITEM-0002\", \"item_name\": \"Test Product 2\", \"item_group\": \"Products\",\"stock_uom\": \"Nos\"}"
            }
            {
                fields: "{ \"item_code\": \"ITEM-0003\", \"item_name\": \"Test Product 3\", \"item_group\": \"Products\",\"stock_uom\": \"Nos\"}"
            }
        ]
    ) {
        status
        doctype
        docs {
            name
            fields
        }
    }
}

```

#### RESPONSE

```
{
    "data": {
        "bulkCreate": {
            "status": true,
            "doctype": "Item",
            "docs": [
                {
                    "name": "ITEM-0001",
                    "fields": "{ \"item_code\": \"ITEM-0001\", \"item_name\": \"Test Product 1\", \"item_group\": \"Products\",\"stock_uom\": \"Nos\"}"
                },
                {
                    "name": "ITEM-0002",
                    "fields": "{ \"item_code\": \"ITEM-0002\", \"item_name\": \"Test Product 2\", \"item_group\": \"Products\",\"stock_uom\": \"Nos\"}"
                },
                {
                    "name": "ITEM-0003",
                    "fields": "{ \"item_code\": \"ITEM-0003\", \"item_name\": \"Test Product 3\", \"item_group\": \"Products\",\"stock_uom\": \"Nos\"}"
                }
            ]
        }
    }
}

```

## ⚙️ Bulk Create Query (Table)

#### QUERY
``` 
mutation {
    bulkCreate(
        doctype: "ToDo"
        fields: [
            {
                fields: """
                {
                    "priority": "Medium",
                    "description": "create table 1",
                    "child_table": [
                        { "test": "111", "nametest": "111" },
                        { "test": "222", "nametest": "222" }
                    ]
                }
                """
            },
            {
                fields: """
                {
                    "priority": "Medium",
                    "description": "create table 2",
                    "child_table": [
                        { "test": "333", "nametest": "333" },
                        { "test": "444", "nametest": "444" }
                    ]
                }
                """
            },
            {
                fields: """
                {
                    "priority": "Medium",
                    "description": "create table 3",
                    "child_table": [
                        { "test": "555", "nametest": "555" },
                        { "test": "666", "nametest": "666" }
                    ]
                }
                """
            }
        ]
    ) {
        status
        doctype
        docs {
            name
            fields
        }
    }
}
```

#### RESPONSE

```
{
    "data": {
        "bulkCreate": {
            "status": true,
            "doctype": "ToDo",
            "docs": [
                {
                    "name": "h8tb0nisre",
                    "fields": "{ \"priority\": \"Medium\", \"description\": \"create table 1\", \"child_table\": [ { \"test\": \"111\", \"nametest\": \"111\" }, { \"test\": \"222\", \"nametest\": \"222\" } ] }"
                },
                {
                    "name": "h8t68e6ahv",
                    "fields": "{ \"priority\": \"Medium\", \"description\": \"create table 2\", \"child_table\": [ { \"test\": \"333\", \"nametest\": \"333\" }, { \"test\": \"444\", \"nametest\": \"444\" } ] }"
                },
                {
                    "name": "h8ukjufb10",
                    "fields": "{ \"priority\": \"Medium\", \"description\": \"create table 3\", \"child_table\": [ { \"test\": \"555\", \"nametest\": \"555\" }, { \"test\": \"666\", \"nametest\": \"666\" } ] }"
                }
            ]
        }
    }
}


```