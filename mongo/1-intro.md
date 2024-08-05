# Introduction to MongoDB

MongoDB is a document-oriented NoSQL database designed for handling large volumes of unstructured data. Unlike traditional relational databases, MongoDB uses flexible, JSON-like documents rather than fixed tables and rows.

## Key Concepts

- **Database**: The highest-level container in MongoDB, which houses collections.
- **Collection**: A grouping of MongoDB documents, analogous to tables in relational databases. Collections are schema-less, allowing for flexible data structures.
- **Document**: The basic unit of data in MongoDB, stored in a JSON-like format (BSON). Documents can contain various data types and structures, including nested documents and arrays.

### Example Document

```json
{
  "Name": "Mitt",
  "age": 27,
  "city": "Toronto",
  "identity": {
    "id": 123456,
    "Healthcardno": "9675478HC"
  }
}
```

## Deployment Options

- **MongoDB Atlas**: A fully managed cloud database service available on AWS, Azure, and Google Cloud. It simplifies deployment, scaling, and management.
- **Enterprise Advanced**: A comprehensive solution for large-scale deployments, offering advanced security and management features.
- **Community Edition**: A free, open-source version suitable for smaller deployments and development environments.

## SQL vs. MongoDB

- **SQL Databases**: Store data in structured tables with rows and columns. They use SQL for querying and often involve complex joins to fetch related data.
- **MongoDB**: Uses a schema-less document model, allowing for flexible and nested data storage. Queries are performed directly on documents within collections, reducing the need for joins.

## CRUD Operations

### Create

- **Database**: Select or create a database:
  ```javascript
  use mydatabase
  ```

- **Collection**:
  - **Explicit Creation**:
    ```javascript
    db.createCollection("posts")
    ```
  - **Implicit Creation**:
    ```javascript
    db.posts.insertOne({ ... })
    ```

### Read

- **Find All Documents**:
  ```javascript
  db.posts.find()
  ```

- **Find One Document**:
  ```javascript
  db.posts.findOne({ _id: ObjectId("someid") })
  ```

### Insert

- **Single Document**:
  ```javascript
  db.posts.insertOne({
    title: "Post Title 1",
    body: "Body of post.",
    category: "News",
    likes: 1,
    tags: ["news", "events"],
    date: new Date()
  })
  ```

- **Multiple Documents**:
  ```javascript
  db.posts.insertMany([
    { title: "Post Title 2", body: "Body of post.", category: "Event", likes: 2, tags: ["news", "events"], date: new Date() },
    { title: "Post Title 3", body: "Body of post.", category: "Technology", likes: 3, tags: ["news", "events"], date: new Date() }
  ])
  ```

### Update

- **Update Single Document**:
  ```javascript
  db.posts.updateOne(
    { _id: ObjectId("someid") },
    { $set: { title: "Updated Title" } }
  )
  ```

- **Update Multiple Documents**:
  ```javascript
  db.posts.updateMany(
    { category: "Event" },
    { $set: { status: "archived" } }
  )
  ```

### Delete

- **Delete Single Document**:
  ```javascript
  db.posts.deleteOne({ _id: ObjectId("someid") })
  ```

- **Delete Multiple Documents**:
  ```javascript
  db.posts.deleteMany({ category: "Old" })
  ```

## MongoDB Shell (mongosh)

- **Install**: Download and install from the official MongoDB website or package managers.
- **Connect**: Use the connection string to connect via terminal:
  ```bash
  mongosh "mongodb+srv://cluster0.mongodb.net/myFirstDatabase" --apiVersion 1
  ```

## Example Command

- **Import Data**:
  ```bash
  mongoimport --db inventory --collection products --file "c:\dataset\products.json"
  ```
