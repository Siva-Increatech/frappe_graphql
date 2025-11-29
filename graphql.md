# 🧩 Frappe GraphQL Queries and Variables

This document provides a collection of GraphQL mutations and variable examples for managing Parent and Child Doctypes in Frappe using the bulkUpdate mutation.

## ⚙️ Frappe Option: Table

### ➕ Create and Update Child and Parent Doctypes

#### QUERY

``` GRAPHQL 
mutation BulkUpdate(
    $doctype: String!
    $update_child: [UpdateChildInput!]
    $create_child: [CreateChildInput!]
    $fields:[UpdateParentListJsonInput!]
) {
    bulkUpdate(
        doctype: $doctype
        update_child: $update_child
        create_child: $create_child
        fields: $fields
    ) {
        status
        doctype
    }
}

```
#### VARIBLES

``` GRAPHQL

{
    "doctype": "Child Link Item",
    "update_child": [
        {
            "parent": "cijrmf0s14",
            "fields": "{\"child_item_table\": [{\"name\": \"cijrcincdg\", \"item__name\": \"ITEM-0001\", \"review\": \"its wow 1\"}]}"
        }
    ],
    "create_child": [
        {
            "parent": "cijrmf0s14",
            "fields": "{\"child_item_table\": [{\"item\": \"ITEM-0003\", \"review\": \"its wow 3\"}]}"
        }
    ],
    "fields": [
        {
            "name": "cijrmf0s14",
            "fields": "{ \"child_name\": \"test child 1\"}"
        }
    ]
}

```

### ✏️ Update Parent Doctype

#### QUERY

``` GRAPHQL 

mutation BulkUpdate(
    $doctype: String!
    $fields:[UpdateParentListJsonInput!]
) {
    bulkUpdate(
        doctype: $doctype
        fields: $fields
    ) {
        status
        doctype
    }
}

```

#### VARIBLES

``` GRAPHQL

{
    "doctype": "Child Link Item",
    "fields": [
        {
            "name": "cijrmf0s14",
            "fields": "{ \"child_name\": \"test update child 1\"}"
        }
    ]
}

```

#### 🗑️ Delete Child Doctype 

#### QUERY

``` GRAPHQL 

mutation BulkUpdate($doctype: String!, $delete_child: [DeleteChildInput!]) {
  bulkUpdate(doctype: $doctype, delete_child: $delete_child) {
    status
    doctype
   
  }
}

```

#### VARIBLES

``` GRAPHQL

{
  "doctype": "Child Link Item",
  "delete_child": [
    {
      "parent": "cijrmf0s14",
      "fields": [
        { "child_item_table": ["cijrcincdg"] }
      ]
    }
  ]
}

```

## 🔗 Frappe Option: Link

### ➕ Create Child Doctype

#### QUERY

``` GRAPHQL 

mutation BulkUpdate($doctype: String!, $create_child: [CreateChildInput!]) {
    bulkUpdate(doctype: $doctype, create_child: $create_child) {
        status
        doctype
    }
}

```

#### VARIBLES

``` GRAPHQL

{
    "doctype": "Child Link Item",
    "create_child": [
        {
            "parent": "cijrmf0s14",
            "fields": {
                "child_link_item__name": [
                    {
                        "item_name": "update child name",
                        "item__name": "ITEM-00012"
                    }
                ]
            }
        }
    ]
}

```

### 🧭 Update Child Doctype

#### QUERY

``` GRAPHQL 

mutation BulkUpdate(
    $doctype: String!
    $update_child: [UpdateChildInput!]
) {
    bulkUpdate(
        doctype: $doctype
        update_child: $update_child
    ) {
        status
        doctype
    }
}

```

#### VARIBLES

``` GRAPHQL
{
    "doctype": "Child Link Item",
    "update_child": [
        {
            "parent": "cijrmf0s14",
            "fields": {"child_link_item__name":[{"name":"3p59ig42ov",
            "item_name":"update child name",
            "item__name":"ITEM-00012"}]}
        }
    ]
}

```

### 🔗 Unlink Child Doctype


#### QUERY

``` GRAPHQL 
mutation BulkUpdate($doctype: String!, $delete_child: [DeleteChildInput!]) {
  bulkUpdate(doctype: $doctype, delete_child: $delete_child) {
    status
    doctype
   
  }
}
```

#### VARIBLES

``` GRAPHQL
{
  "doctype": "Child Link Item",
  "delete_child": [
    {
      "parent": "cijrmf0s14",
      "fields": [
        { "child_link_item": ["217hus971j"] }
      ]
    }
  ]
}
```

## 🧮 Frappe Option: Table Multiselect

### ❌ Remove Table Multiselect 

#### QUERY

``` GRAPHQL 
mutation BulkUpdate($doctype: String!, $delete_child: [DeleteChildInput!]) {
  bulkUpdate(doctype: $doctype, delete_child: $delete_child) {
    status
    doctype
   
  }
}
```

#### VARIBLES

``` GRAPHQL
{
  "doctype": "Child Link Item",
  "delete_child": [
    {
      "parent": "cijrmf0s14",
      "fields": [
        { "multi_select_item": ["9gtoha0f44"] }
      ]
    }
  ]
}
```

### ➕ Create Table Multiselect 

#### QUERY

``` GRAPHQL 
mutation BulkUpdate($doctype: String!, $create_child: [CreateChildInput!]) {
  bulkUpdate(doctype: $doctype, create_child: $create_child) {
    status
    doctype
   
  }
}

```

#### VARIBLES

``` GRAPHQL
{
  "doctype": "Child Link Item",
  "create_child": [
    {
      "parent": "cijrmf0s14",
      "fields": {
        "multi_select_item":[{"item":"ITEM-0001"}] 
      }
    }
  ]
}
```

### 🔁 Update Table Multiselect 

#### QUERY

``` GRAPHQL 
mutation BulkUpdate($doctype: String!, $update_child: [UpdateChildInput!]) {
  bulkUpdate(doctype: $doctype, update_child: $update_child) {
    status
    doctype
   
  }
}
```

#### VARIBLES

``` GRAPHQL
{
  "doctype": "Child Link Item",
  "update_child": [
    {
      "parent": "cijrmf0s14",
      "fields": {
        "multi_select_item":[{"name":"95v4h87o1l","item__name":"ITEM-0001"}] 
      }
    }
  ]
}
```





