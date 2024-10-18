# README: Library Management System

## Project Title: Library Management System

### Objective
This project aims to create a Library Management System that enables the management of a collection of books, authors, and patrons using MongoDB.



### Getting Started with MongoDB Shell (Mongosh)

To work with MongoDB using the MongoDB shell (Mongosh), follow these steps:

1. **Install MongoDB**: Ensure that you have MongoDB installed on your system. You can download it from the [MongoDB official website](https://www.mongodb.com/try/download/community).
  
2. **Start MongoDB**: Start the MongoDB server by running the following command in your terminal (usually):
 
   mongod


3. **Open MongoDB Shell (Mongosh)**: Open another terminal window and start the MongoDB shell by entering:

   mongosh
  

4. **Use Database**: To start working in your database, you need to switch to the desired database (in this case, `LibraryDB`). You can do so by executing:
  
   use LibraryDB
 

### MongoDB Commands

Below are the specific MongoDB shell commands used in this project.

#### 1. **Create Database**

use LibraryDB


#### 2. **Create Collections and Insert Documents**

- **Books Collection:**

db.Books.insertMany([ { _id: 1, title: "1984", author_id: 1, genres: ["Dystopian", "Political Fiction"], published_year: 1949, available: true }, { _id: 2, title: "To Kill a Mockingbird", author_id: 2, genres: ["Southern Gothic", "Bildungsroman"], published_year: 1960, available: true }, { _id: 3, title: "The Great Gatsby", author_id: 3, genres: ["Tragedy"], published_year: 1925, available: true }, { _id: 4, title: "Brave New World", author_id: 4, genres: ["Dystopian", "Science Fiction"], published_year: 1932, available: true }, { _id: 5, title: "The Catcher in the Rye", author_id: 5, genres: ["Realist Novel", "Bildungsroman"], published_year: 1951, available: true }, { _id: 6, title: "Moby-Dick", author_id: 6, genres: ["Adventure Fiction"], published_year: 1851, available: true }, { _id: 7, title: "Pride and Prejudice", author_id: 7, genres: ["Romantic Novel"], published_year: 1813, available: true }, { _id: 8, title: "War and Peace", author_id: 8, genres: ["Historical Novel"], published_year: 1869, available: true }, { _id: 9, title: "Crime and Punishment", author_id: 9, genres: ["Philosophical Novel"], published_year: 1866, available: true }, { _id: 10, title: "The Hobbit", author_id: 10, genres: ["Fantasy"], published_year: 1937, available: true } ])


 **Authors Collection:**

db.Authors.insertMany([ { _id: 1, name: "George Orwell", nationality: "British", birth_year: 1903, death_year: 1950 }, { _id: 2, name: "Harper Lee", nationality: "American", birth_year: 1926, death_year: 2016 }, { _id: 3, name: "F. Scott Fitzgerald", nationality: "American", birth_year: 1896, death_year: 1940 }, { _id: 4, name: "Aldous Huxley", nationality: "British", birth_year: 1894, death_year: 1963 }, { _id: 5, name: "J.D. Salinger", nationality: "American", birth_year: 1919, death_year: 2010 }, { _id: 6, name: "Herman Melville", nationality: "American", birth_year: 1819, death_year: 1891 }, { _id: 7, name: "Jane Austen", nationality: "British", birth_year: 1775, death_year: 1817 }, { _id: 8, name: "Leo Tolstoy", nationality: "Russian", birth_year: 1828, death_year: 1910 }, { _i
_id: 9, name: "Fyodor Dostoevsky", nationality: "Russian", birth_year: 1821, death_year: 1881 }, { _id: 10, name: "J.R.R. Tolkien", nationality: "British", birth_year: 1892, death_year: 1973 } ])


 **Patrons Collection:**

db.Patrons.insertMany([ { _id: 1, name: "George Orwell", nationality: "British", birth_year: 1903, death_year: 1950 }, { _id: 2, name: "Harper Lee", nationality: "American", birth_year: 1926, death_year: 2016 }, { _id: 3, name: "F. Scott Fitzgerald", nationality: "American", birth_year: 1896, death_year: 1940 }, { _id: 4, name: "Aldous Huxley", nationality: "British", birth_year: 1894, death_year: 1963 }, { _id: 5, name: "J.D. Salinger", nationality: "American", birth_year: 1919, death_year: 2010 }, { _id: 6, name: "Herman Melville", nationality: "American", birth_year: 1819, death_year: 1891 }, { _id: 7, name: "Jane Austen", nationality: "British", birth_year: 1775, death_year: 1817 }, { _id: 8, name: "Leo Tolstoy", nationality: "Russian", birth_year: 1828, death_year: 1910 }, { _i_id: 9, name: "Fyodor Dostoevsky", nationality: "Russian", birth_year: 1821, death_year: 1881 }, { _id: 10, name: "J.R.R. Tolkien", nationality: "British", birth_year: 1892, death_year: 1973 } ])


#### 3. **CRUD Operations**

 **READ**

// Find All Books
db.books.find()

// Find a Specific Book by Title
db.books.find([{ title: "To Kill a Mockingbird" }])

// Find All Books by a Specific Author
db.books.find({ author_id: 5 })

// Find All Available Books
db.books.find({ available: true })


 **UPDATE**

// Update Book Availability
db.books.updateOne([{ _id: 3 }, { $set: { available: false } }])

// Add a Genre to a Book
db.books.updateOne([{ _id: 8 }, { $addToSet: { genres: "Adventure" } }])

// Add a borrowed book to a patron’s record
db.patrons.updateOne([{ _id: 5 }, { $addToSet: { borrowed_books: 1 } }])


 **DELETE**

// Delete a Book by Title
db.books.deleteOne([{ title: "Brave New World" }])

// Delete an Author
db.authors.deleteOne({ _id: 3 })


#### 4. **Advanced Queries with Operators**

// Find Books Published After 1950
db.books.find([{ published_year: { $gt: 1950 } }])

// Find All American Authors
db.authors.find([{ nationality: { $eq: "American" } }])

// Set All Books To Available
db.books.updateMany([{}, { $set: { available: true } }])

// Find All Books That Are Available And Published After 1950
db.books.find([{ available: true, published_year: { $gt: 1950 } }])

// Find authors whose names contain "George"
db.authors.find([{ name: { $regex: "George" } }])

// Increment the published year of 1869 by 1
db.books.updateOne([{ published_year: 1869 }, { $inc: { published_year: 1 } }])


### Conclusion

This README outlines the essential commands for setting up, managing, and querying a simple Library Management System using MongoDB. Follow the instructions to execute CRUD operations and run advanced queries effectively.