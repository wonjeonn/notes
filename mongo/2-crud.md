# MongoDB CRUD Operations

## Create

Add new documents to a collection

- **Insert One**: Adds a single document to a collection.
  ```javascript
  db.collection.insertOne(document)
  ```

- **Insert Many**: Adds multiple documents to a collection.
  ```javascript
  db.collection.insertMany([document1, document2, ...])
  ```

### Example
```javascript
db.students.insertOne({ firstname: "Ganu", age: 1 })
db.students.insertMany([
  { name: "Shiva", age: 34 },
  { name: "Manu", age: 2 },
  { name: "Myra", class: "KG1", age: 5 }
])
```

## Read

Retrieve documents from a collection

- **Find**: Retrieves multiple documents.
  ```javascript
  db.collection.find(query, options)
  ```

- **Find One**: Retrieves a single document.
  ```javascript
  db.collection.findOne(query, options)
  ```

### Example
```javascript
db.posts.find()
db.posts.findOne()
```

### Queries

- **Count Documents**: Get the number of documents that match a query.
  ```javascript
  db.studlist.find({}).count()
  ```

- **Print Documents**: Iterate and print documents.
  ```javascript
  db.studlist.find().forEach(printjson)
  ```

- **Limit Results**: Limit the number of documents returned.
  ```javascript
  db.studlist.find().limit(5)
  ```

- **Range Queries**: Query for documents within a range.
  ```javascript
  db.studlist.find({ age: { $gt: 5, $lt: 12 } })
  ```

## Update

Modify existing documents

- **Update One**: Updates a single document.
  ```javascript
  db.collection.updateOne(filter, update, options)
  ```

- **Update Many**: Updates multiple documents.
  ```javascript
  db.collection.updateMany(filter, update, options)
  ```

- **Replace One**: Replaces a single document.
  ```javascript
  db.collection.replaceOne(filter, replacement, options)
  ```

### Example
```javascript
db.studlist.updateOne({ name: "Tim" }, { $set: { age: 10 } })
db.students.updateMany({}, { $inc: { age: 1 } })
db.students.updateOne({ name: "John" }, { $set: { age: 15 } })
db.students.updateMany({ age: { $gte: 5 } }, { $set: { isEligibleForSchool: true } })
```

## Delete

Remove documents

- **Delete One**: Removes a single document.
  ```javascript
  db.collection.deleteOne(filter)
  ```

- **Delete Many**: Removes multiple documents.
  ```javascript
  db.collection.deleteMany(filter)
  ```

### Example
```javascript
db.students.deleteOne({ name: "Tom" })
db.students.deleteMany({ age: 1 })
db.students.deleteMany({})
```

- **Drop Database**: Deletes the current database.
  ```javascript
  use testdatabase
  db.dropDatabase()
  ```

## Document Structure

MongoDB documents are field-and-value pairs and can include nested structures

```json
{
  "_id": ObjectId("..."),
  "name": { "first": "Alan", "last": "Turing" },
  "birth": new Date("1912-06-23"),
  "death": new Date("1954-06-07"),
  "contribs": ["Turing machine", "Turing test", "Turingery"]
}
```

## Operators

- **$inc**: Increments the value of a field.
  ```javascript
  db.collection.updateMany({}, { $inc: { fees: 100 } })
  ```

- **$min**: Updates the value if the specified value is less.
  ```javascript
  db.collection.updateOne({ name: "Teena" }, { $min: { fees: 500 } })
  ```

- **$max**: Updates the value if the specified value is greater.
  ```javascript
  db.collection.updateOne({ name: "Teena" }, { $max: { fees: 10000 } })
  ```

- **$mul**: Multiplies the value by a specified amount.
  ```javascript
  db.collection.updateOne({ name: "Teena" }, { $mul: { fees: 2 } })
  ```

- **$unset**: Removes a field from a document.
  ```javascript
  db.collection.updateOne({ name: "Teena" }, { $unset: { fees: "" } })
  ```

- **$rename**: Renames a field.
  ```javascript
  db.collection.updateOne({}, { $rename: { fees: "CourseFee" } })
  ```

- **Upsert**: Creates a new document if no document matches the filter.
  ```javascript
  db.collection.updateOne(filter, update, { upsert: true })
  ```
