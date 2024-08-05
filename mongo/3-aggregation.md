# MongoDB Aggregation

MongoDB's aggregation framework is designed to process data records and return computed results. It is commonly used for operations such as grouping values, calculating sums, averages, and more. Aggregation can be performed using pipelines or single-purpose methods.

## Aggregation Pipeline

An aggregation pipeline is a sequence of stages that process data records, with each stage performing a specific operation on the data. Documents pass through these stages in sequence, with each stage transforming the data in some way.

### Pipeline Stages

1. **$match**: Filters documents based on the specified condition.
   ```javascript
   { $match: { status: "active" } }
   ```

2. **$group**: Groups documents by a specified field and performs aggregation operations on the grouped data.
   ```javascript
   { $group: { _id: "$category", total: { $sum: "$amount" } } }
   ```

3. **$project**: Reshapes documents by including or excluding fields and creating new ones.
   ```javascript
   { $project: { name: 1, total: { $multiply: ["$quantity", "$price"] } } }
   ```

4. **$sort**: Sorts documents based on specified fields.
   ```javascript
   { $sort: { age: -1 } }
   ```

5. **$limit**: Limits the number of documents passed to the next stage.
   ```javascript
   { $limit: 10 }
   ```

6. **$skip**: Skips a specified number of documents and returns the rest.
   ```javascript
   { $skip: 5 }
   ```

7. **$lookup**: Performs a left outer join with another collection to include documents from the joined collection.
   ```javascript
   { $lookup: { from: "orders", localField: "customer_id", foreignField: "customer_id", as: "orderDetails" } }
   ```

8. **$unwind**: Deconstructs an array field to output a document for each element in the array.
   ```javascript
   { $unwind: "$items" }
   ```

### Example Pipeline

This example filters documents where `age` is 50, groups them by `age`, and counts the number of documents in each group:

```javascript
db.collection.aggregate([
  { $match: { age: 50 } },          // Stage 1: Filter documents
  { $group: { _id: "$age", count: { $sum: 1 } } } // Stage 2: Group by age and count
])
```

## Common Aggregation Operators

- **$group**: Groups documents by a specified field and performs aggregations.
  ```javascript
  db.collection.aggregate([
    { $group: { _id: "$age", names: { $push: "$name" } } }
  ])
  ```

- **$project**: Reshapes documents to include or exclude specific fields.
  ```javascript
  db.collection.aggregate([
    { $project: { title: 1, author: 1 } } // Includes only title and author fields
  ])
  ```

- **$sort**: Sorts documents by specified fields.
  ```javascript
  db.collection.aggregate([
    { $sort: { age: -1 } } // Sorts documents by age in descending order
  ])
  ```

- **$limit**: Limits the number of documents returned.
  ```javascript
  db.collection.aggregate([
    { $limit: 5 } // Returns the first 5 documents
  ])
  ```

- **$skip**: Skips a specified number of documents.
  ```javascript
  db.collection.aggregate([
    { $skip: 10 } // Skips the first 10 documents
  ])
  ```

## SQL to MongoDB Aggregation Mapping

| SQL Term                | MongoDB Aggregation Operator |
|-------------------------|------------------------------|
| WHERE                   | $match                       |
| GROUP BY                | $group                       |
| HAVING                  | $match                       |
| SELECT                  | $project                     |
| ORDER BY                | $sort                        |
| LIMIT                   | $limit                       |
| SUM()                   | $sum                         |
| COUNT()                 | $sum or $count               |
| JOIN                    | $lookup                      |
| SELECT INTO NEW_TABLE   | $out                         |
| MERGE INTO TABLE        | $merge                       |
| UNION ALL               | $unionWith                   |

## Comparison Operators

- **$eq**: Equal to
- **$ne**: Not equal to
- **$gt**: Greater than
- **$gte**: Greater than or equal to
- **$lt**: Less than
- **$lte**: Less than or equal to
- **$in**: Value is in an array

## Logical Operators

- **$and**: Logical AND
- **$or**: Logical OR
- **$nor**: Logical NOR
- **$not**: Logical NOT

### Example Usage

- **Find documents where the `type` is 'phone':**
  ```javascript
  db.products.find({ type: 'phone' })
  ```

- **Group documents by `type` and count occurrences:**
  ```javascript
  db.products.aggregate([
    { $group: { _id: "$type", count: { $sum: 1 } } }
  ])
  ```

- **Project only specific fields:**
  ```javascript
  db.products.aggregate([
    { $project: { type: 1, _id: 0 } }
  ])
  ```
