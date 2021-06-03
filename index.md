## Lab 6

``` markdown
Goals and Outcomes

  - Join GitHub and work through Introduction to GitHub course
  - Create lab file
  - Classes overview
  - Create and test Book class
  - Create and test Library class
  - Add at least two more books to the library
  - Add ISBN and a delete book method

```

Lab-06.js

```rouge
  /*
    CIT 281 Lab 6
    Name: Emily Deng
  */

  class Book {
      constructor(title, author, pubDate, isbn) {
        this.title = title;
        this.author = author;
        this.pubDate = pubDate;
        this.isbn = isbn;
      }
    }

    class Library {
      constructor(name) {
        this._name = name;
        this._books = [];
      }
      get books() {
        // Return copy of books
        return JSON.parse(JSON.stringify(this._books));
      }
      get count() {
        return this._books.length;
      }
      addBook(book = {}) {
        const { title = "", author = "", pubDate = "", isbn = ""} = book;
        if (title.length > 0 && author.length > 0) {
          const newBook = { title, author, pubDate, isbn};
          this._books.push(newBook);
        }
      }
      listBooks() {
        for (const book of this._books) {
          const {title, author, pubDate, isbn} = book;
          console.log(`Title: ${title}, Author: ${author}, PubDate: ${pubDate}, ISBN: ${isbn}`);
        }
      }
      deleteBook(isbn) {
          // 1) Find the book to remove (via ISBN) from "this._books"
          // a) Loop over all books
          // b) Filter
          // c) Move to step 2 once a condition has been met (this condition may be equal to the filter)
          // 2) Remove the book from "this._books"

          // 1) initialize some variable to null (or zero)
          // 2) Iterate over a collection/array of objects
          //      3) Filter these objects 
          //          4) Update the variables in (1)
          //          4*) (optionally) break out of the iteration early
          // 5) Variable in (1) is now good to go

          let indexOfBookToRemove = null; // step 1
          for (let index = 0; index < this._books.length; index++) {  //step 2
              if (this._books[index].isbn == isbn) { // step 3
                  indexOfBookToRemove = index; // step 4
                  break; // step 4*
              }
          }
          // Move on and use indexOfBookToRemove in the subsequent removal process
          this._books.splice(indexOfBookToRemove, 1);

      }
    }

  const myBook = new Book('AP Calc Crash Course','Banu et al.', '01/01/2013', '123456789');
  const atomicHabits = new Book('Atomic Habits', 'James Clear', '10/16/2018', '0987654');
  // add two new books
  const jjkVolume = new Book('Jujutsu Kaisen', 'Gege Akutami', '12/04/2018', '4567890');
  const spyFamily = new Book('Spy x Family', 'Tatsuya Endo', '06/02/2020', '2350867');


  const uoLibrary = new Library('Knight Library');
  uoLibrary.addBook(myBook);
  uoLibrary.addBook(atomicHabits);
  uoLibrary.addBook(jjkVolume);
  uoLibrary.addBook(spyFamily);
  uoLibrary.listBooks();

  console.log('Deleting Book');
  uoLibrary.deleteBook('123456789');
  uoLibrary.listBooks();

  ```
