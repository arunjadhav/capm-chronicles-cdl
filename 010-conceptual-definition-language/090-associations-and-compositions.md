---
layout: chapter
title: "Associations & Compositions — Connecting Your Data Together"
---
*Alex and Byte discover how to model relationships and document structures in CDL!*

---

Alex and Byte entered the Hall of Connections, where bridges and tunnels linked every room. Byte pointed to a sign: "Associations & Compositions."

"Byte, how do I connect my entities together?" Alex asked, looking at a model of a city with roads and buildings.

Byte replied, "With associations and compositions! Associations are like roads between entities, and compositions are like buildings with rooms inside."

---

**Associations: Making Connections**

"Associations let you define relationships between entities. You can have one-to-one, one-to-many, or even many-to-many connections."

```cds
entity Book {
  key ID : Integer;
  title  : String;
  author : Association to Author;
}

entity Author {
  key ID : Integer;
  name   : String;
}
```

"Here, each Book is linked to an Author."

*When to use:* Use associations when you want to reference another entity, like linking a book to its author, an order to a customer, or a product to a category.

---

**To-Many and Many-to-Many Associations**

"You can also have associations to many entities, or model many-to-many relationships with a link entity."

```cds
entity Author {
  key ID : Integer;
  name   : String;
  // This association finds all Book records where Book.author points to this Author
  books  : Association to many Book on books.author = $self;
  // You can add more associations or fields as needed
  // For example, let's add a managed association to Country
  country : Association to Country;
  // And a calculated field for the number of books
  numBooks : Integer = count(books);
}

entity BookGenreLink {
  key book   : Association to Book;
  key genre  : Association to Genre;
}

entity Country {
  key code : String(2);
  name    : String;
}
```

// What does $self mean?
//
// Byte explained: "$self is a special keyword in CDL that always refers to the current instance of the entity you are defining the association in. Think of it as 'this' in many programming languages. In the example above, books.author = $self means: link all Book entities whose author field points to this Author. This is how you set up a backlink or a relationship that connects the right records together."
//
// Use $self whenever you want to refer to the current entity instance in an ON condition, especially for to-many or many-to-many associations.

---

**Compositions: Containment and Document Structures**

"Compositions are special associations that represent contained-in relationships, like an order with its items, or a book with its reviews."

```cds
entity Book {
  key ID : Integer;
  title  : String;
  reviews: Composition of many Review on reviews.book = $self;
}

entity Review {
  key ID   : Integer;
  book     : Association to Book;
  content  : String;
}
```

*When to use:* Use compositions when the child entity (like Review) should only exist as part of the parent (like Book), and should be deleted if the parent is deleted.

---

**Managed Associations: Implicit Foreign Keys**

"Alex, what if I want to link an Author to a single Book, but I don't want to write an ON condition?" Alex asked.

Byte replied, "That's a managed association! If you define an association without an ON condition, CDL automatically adds a foreign key field for you."

```cds
entity Author {
  key ID : Integer;
  name  : String;
  // Managed association to Book (no ON condition)
  favoriteBook : Association to Book;
}
```

"Here, each Author can have a favorite Book. Even though you only see the association in the code, the framework treats it as if you had written this expanded version:"

```cds
entity Author {
  key ID : Integer;
  name  : String;
  favoriteBook : Association to Book on favoriteBook.ID = favoriteBook_ID;
  favoriteBook_ID : Integer;
}
```

"So, the field 'favoriteBook_ID' is added automatically, and the association is wired up to use it as a foreign key!"

*How does this look in the compiled model (CSN)?*

```json
{
  "Author": {
    "elements": {
      "ID": { "type": "cds.Integer", "key": true },
      "name": { "type": "cds.String" },
      "favoriteBook": {
        "type": "cds.Association",
        "target": "Book",
        "keys": [ { "ref": ["favoriteBook_ID"] } ]
      },
      "favoriteBook_ID": { "type": "cds.Integer" }
    }
  }
}
```

Byte explained: "See? The compiled model includes both the association and the implicit foreign key field. You can use managed associations for simple, automatic foreign key handling—no ON condition needed!"

---

**Best Practices**

- Use associations for flexible links between entities
- Use compositions for strong containment (document) relationships
- Always define clear ON conditions for unmanaged associations
- Use managed associations for simpler, automatic foreign key handling

---

Alex smiled, "Now I can connect all my data together, just like a real city!"

Byte nodded, "Exactly! Next up: Annotations—adding extra meaning and metadata to your models!"

---

// Expanded Author entity explanation:
// - ID: Primary key for Author
// - name: Author's name
// - books: Unmanaged to-many association, finds all Book records where Book.author points to this Author (using $self)
// - country: Managed association to Country entity (Author's country)
// - numBooks: Calculated field, counts the number of books for this Author
//
// This shows how you can combine managed and unmanaged associations, calculated fields, and regular fields in one entity.
