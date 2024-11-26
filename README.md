# MongoDB Library Management System
### This project demonstrates the use of MongoDB to manage a simple library system. It includes collections for books, authors, and patrons, along with operations to query and manipulate data.

## Features
## Book Collection

Stores information about books including title, author, genres, published year, and availability status.
Author Collection

Stores details of authors such as name, nationality, and lifespan.
Patrons Collection

Tracks patrons' information and the books they have borrowed.
Query Operations

Query books based on availability and publication year.
Update books' availability status.
Perform advanced queries such as finding books with specific criteria.
Prerequisites
Install MongoDB.
Access MongoDB via the terminal or a GUI client like Compass.
Ensure the MongoDB server is running locally or remotely.
Collections
## 1. BookCollection
### Example document:

json

{
  "_id": 1,
  "title": "1984",
  "author_id": 1,
  "genres": ["Dystopian", "Political Fiction"],
  "published_year": 1949,
  "available": "true"
}


## 2. AuthorCollection
### Example document:


{
  "_id": 1,
  "name": "George Orwell",
  "nationality": "British",
  "birth_year": 1903,
  "death_year": 1950
}
## 3. PatronsCollection
### Example document:


{
  "_id": 1,
  "name": "Alice Johnson",
  "email": "alice@example.com",
  "borrowed_books": []
}

db.BookCollection.insertMany([
  { _id: 1, title: "1984", author_id: 1, genres: ["Dystopian", "Political Fiction"], published_year: 1949, available: true },
  { _id: 2, title: "To Kill a Mockingbird", author_id: 2, genres: ["Southern Gothic", "Bildungsroman"], published_year: 1960, available: true },
  ...
]);
## Insert Authors

db.AuthorCollection.insertMany([
  { _id: 1, name: "George Orwell", nationality: "British", birth_year: 1903, death_year: 1950 },
  { _id: 2, name: "Harper Lee", nationality: "American", birth_year: 1926, death_year: 2016 },
  ...
]);
## Insert Patrons

db.PatronsCollection.insertMany([
  { _id: 1, name: "Alice Johnson", email: "alice@example.com", borrowed_books: [] },
  { _id: 2, name: "Bob Smith", email: "bob@example.com", borrowed_books: [1, 2] },
  ...
]);
![Book](/images/book1.jpg)

## 1. Find Books Published After 1950

db.BookCollection.find({ published_year: { $gt: 1950 } });
[!Book](/images/book%202.jpg)

## 2. Find All American Authors

db.AuthorCollection.find({ nationality: "American" });
## 3. Set All Books To Available

db.BookCollection.updateMany({}, { $set: { available: "true" } });
## 4. Find All Available Books Published After 1950

db.BookCollection.find({
  $and: [
    { available: "true" },
    { published_year: { $gt: 1950 } }
  ]
});
5. Find Authors Whose Names Contain "George"

db.AuthorCollection.find({ name: { $regex: "George", $options: "i" } });
6. Increment Published Year of "1869" by 1

db.BookCollection.updateMany(
  { published_year: 1869 },
  { $inc: { published_year: 1 } }
);
Tools Used
MongoDB: Database management system for storing collections.
MongoDB Shell: For executing database commands.
Notes
Make sure field names match exactly (case-sensitive) when querying.
Always test queries to ensure they return expected results.
License
This project is open-source and free to use for educational purposes.