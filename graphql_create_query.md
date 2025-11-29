# 🧩 Frappe GraphQL Queries and Variables

This document provides a collection of GraphQL mutations and variable examples for managing Parent and Child Doctypes in Frappe using the bulkcreate mutation.


# 🔗 Frappe Option: Link

## ⚙️ Bulk create parent records and update child names  query

#### QUERY

``` GRAPHQL
mutation BulkCreateItems($fields: [CreateDocInput!]!) {
  bulkCreate(
    doctype: "Item"
    fields: $fields
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

#### VARIBLES


``` GRAPHQL

{
  "fields": [
    {
      "fields": "{ \"item_code\": \"ITEM-0111\", \"item_name\": \"Test Product 1\", \"item_group\": \"Products\", \"stock_uom\": \"Nos\" }"
    },
    {
      "fields": "{ \"item_code\": \"ITEM-0112\", \"item_name\": \"Test Product 2\", \"item_group\": \"Products\", \"stock_uom\": \"Nos\" }"
    },
    {
      "fields": "{ \"item_code\": \"ITEM-0113\", \"item_name\": \"Test Product 3\", \"item_group\": \"Products\", \"stock_uom\": \"Nos\" }"
    }
  ]
}

```

OR 

``` GRAPHQL 
{
  "fields": [
    {
      "fields": {
    "item_code": "ITEM-0211",
    "item_name": "Test Product 1",
    "item_group": "Products",
    "stock_uom": "Nos"  # update child use name
  }
    },
    {
      "fields":  {
    "item_code": "ITEM-0212",
    "item_name": "Test Product 3",
    "item_group": "Products",
    "stock_uom": "Nos"  # update child use name  
  }
    },
    {
      "fields":  {
    "item_code": "ITEM-0213",
    "item_name": "Test Product 3",
    "item_group": "Products",
    "stock_uom": "Nos" # update child use name 
  }
    }
  ]
}

```

### NOTE : Both JSON strings and JSON objects will be supported 

#### RESPONSE 

``` GRAPHQL
{
    "data": {
        "bulkCreate": {
            "status": true,
            "doctype": "Item",
            "docs": [
                {
                    "name": "ITEM-0111",
                    "fields": "{ \"item_code\": \"ITEM-0111\", \"item_name\": \"Test Product 1\", \"item_group\": \"Products\", \"stock_uom\": \"Nos\" }"
                },
                {
                    "name": "ITEM-0112",
                    "fields": "{ \"item_code\": \"ITEM-0112\", \"item_name\": \"Test Product 2\", \"item_group\": \"Products\", \"stock_uom\": \"Nos\" }"
                },
                {
                    "name": "ITEM-0113",
                    "fields": "{ \"item_code\": \"ITEM-0113\", \"item_name\": \"Test Product 3\", \"item_group\": \"Products\", \"stock_uom\": \"Nos\" }"
                }
            ]
        }
    }
}

```


## ⚙️ Bulk create parent records with child query

#### QUERY

``` GRAPHQL

mutation BulkCreateItems($fields: [CreateDocInput!]!) {
    bulkCreate(doctype: "Item", fields: $fields) {
        status
        doctype
        docs {
            name
            fields
        }
    }
}

```

#### VARIBLES


``` GRAPHQL

{
    "fields": [
        {
            "fields": {
                "item_code": "ITEM-0311",
                "item_name": "Test Product 1",
                "item_group": "Products",
                "stock_uom": "Nos",
                "child_table": [
                    {
                        "item_details": "test item_details", # create child table 
                        "review": "test review"
                    }
                ]
            }
        },
        {
            "fields": {
                "item_code": "ITEM-0312",
                "item_name": "Test Product 3",
                "item_group": "Products",
                "stock_uom": "Nos",
                "child_table": [
                    {
                        "item_details": "test item_details", # create child table 
                        "review": "test review"
                    }
                ]
            }
        },
        {
            "fields": {
                "item_code": "ITEM-0313",
                "item_name": "Test Product 3",
                "item_group": "Products",
                "stock_uom": "Nos",
                "child_table": [
                    {
                        "item_details": "test item_details",
                        "review": "test review"                 # create child table 
                    }
                ]
            }
        }
    ]
}

```

#### RESPONSE 

``` GRAPHQL
{
    "data": {
        "bulkCreate": {
            "status": true,
            "doctype": "Item",
            "docs": [
                {
                    "name": "ITEM-0311",
                    "fields": {
                        "item_code": "ITEM-0311",
                        "item_name": "Test Product 1",
                        "item_group": "Products",
                        "stock_uom": "Nos",
                        "doctype": "Item"
                    }
                },
                {
                    "name": "ITEM-0312",
                    "fields": {
                        "item_code": "ITEM-0312",
                        "item_name": "Test Product 3",
                        "item_group": "Products",
                        "stock_uom": "Nos",
                        "doctype": "Item"
                    }
                },
                {
                    "name": "ITEM-0313",
                    "fields": {
                        "item_code": "ITEM-0313",
                        "item_name": "Test Product 3",
                        "item_group": "Products",
                        "stock_uom": "Nos",
                        "doctype": "Item"
                    }
                }
            ]
        }
    }
}
```

# 🔗 Frappe Option: Table

## ⚙️ Bulk create parent records and create child query


#### QUERY

``` GRAPHQL
mutation BulkCreateItems($fields: [CreateDocInput!]!) {
  bulkCreate(
    doctype: "Item"
    fields: $fields
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

#### VARIBLES


``` GRAPHQL
{
    "fields": [
        {
            "fields": {
                "item_code": "ITEM-0411",
                "item_name": "Test Product 1",
                "item_group": "Products",
                "stock_uom": "Nos",
                "child_table": [
                    {
                        "item_details": "test item_details",
                        "review": "test review"
                    }
                ]
            }
        },
        {
            "fields": {
                "item_code": "ITEM-0412",
                "item_name": "Test Product 3",
                "item_group": "Products",
                "stock_uom": "Nos",
                "child_table": [
                    {
                        "item_details": "test item_details",
                        "review": "test review"
                    }
                ]
            }
        },
        {
            "fields": {
                "item_code": "ITEM-0413",
                "item_name": "Test Product 3",
                "item_group": "Products",
                "stock_uom": "Nos",
                "child_table": [
                    {
                        "item_details": "test item_details",
                        "review": "test review"
                    },
                    {
                        "item_details": "test item_details",
                        "review": "test review"
                    }
                ]
            }
        }
    ]
}

```

#### RESPONSE 

``` GRAPHQL
{
    "data": {
        "bulkCreate": {
            "status": true,
            "doctype": "Item",
            "docs": [
                {
                    "name": "ITEM-0411",
                    "fields": {
                        "item_code": "ITEM-0411",
                        "item_name": "Test Product 1",
                        "item_group": "Products",
                        "stock_uom": "Nos",
                        "doctype": "Item"
                    }
                },
                {
                    "name": "ITEM-0412",
                    "fields": {
                        "item_code": "ITEM-0412",
                        "item_name": "Test Product 3",
                        "item_group": "Products",
                        "stock_uom": "Nos",
                        "doctype": "Item"
                    }
                },
                {
                    "name": "ITEM-0413",
                    "fields": {
                        "item_code": "ITEM-0413",
                        "item_name": "Test Product 3",
                        "item_group": "Products",
                        "stock_uom": "Nos",
                        "doctype": "Item"
                    }
                }
            ]
        }
    }
}

```


# 🔗 Frappe Option: Table MultiSelect

## ⚙️ Bulk create parent records and update child names


#### QUERY

``` GRAPHQL
mutation BulkCreateToDo($fields: [CreateDocInput!]!) {
    bulkCreate(doctype: "ToDo", fields: $fields) {
        status
        doctype
        docs {
            name
            fields
        }
    }
}

```


#### VARIBLES


``` GRAPHQL
{
    "fields": [
        {
            "fields": {
                "priority": "Medium",
                "description": "create Multiselect 1",
                "child_table": [
                    {
                        "fields": "3ps2tfa3ga"
                    },
                    {
                        "fields": "3psbe59pnd"
                    }
                ]
            }
        },
        {
            "fields": {
                "priority": "Medium",
                "description": "create Multiselect 2",
                "child_table": [
                    {
                        "fields": "3ps2tfa3ga"
                    },
                    {
                        "fields": "3psbe59pnd"
                    }
                ]
            }
        }
    ]
}
```

#### RESPONSE 

```GRAPHQL
{
    "data": {
        "bulkCreate": {
            "status": true,
            "doctype": "ToDo",
            "docs": [
                {
                    "name": "e8q3biuu4t",
                    "fields": {
                        "priority": "Medium",
                        "description": "create Multiselect 1",
                        "doctype": "ToDo"
                    }
                },
                {
                    "name": "e8rokh32kr",
                    "fields": {
                        "priority": "Medium",
                        "description": "create Multiselect 2",
                        "doctype": "ToDo"
                    }
                }
            ]
        }
    }
}

```
