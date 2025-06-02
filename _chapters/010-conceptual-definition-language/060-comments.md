---
layout: chapter
title: "Comments — Talking to Future You"
---

*Alex and Byte discover the power of comments in CDL!*

---

Alex and Byte entered a room full of sticky notes and scribbles. "Why all the notes?" Alex asked.

Byte replied, "Those are comments! Comments help you and others understand your code later. They're ignored by the system, but priceless for humans."

---

**Single-Line Comments**

"Use double slashes for single-line comments."

```cds
// This is a single-line comment
entity Book {
  key ID : Integer;
  title  : String;
}
```

---

**Multi-Line Comments**

"Use /* ... */ for longer comments."

```cds
/*
  This is a multi-line comment
  describing the Book entity
*/
entity Book {
  key ID : Integer;
  title  : String;
}
```

---
# Welcome to Byte-Sized CAPsules: The Bookshop Tales

Whether you’re a seasoned developer or just starting your journey with SAP’s Cloud Application Programming Model (CAP), this book is your companion for building and securing modern cloud applications. Join Alex, Emma, and Byte as they navigate real-world challenges, share practical tips, and inject a bit of fun into every chapter. Let’s make your CAP adventure secure, insightful, and enjoyable!

---

## Doc Comments: Making Your Models Self-Explaining

Alex and Byte entered a room full of sticky notes and scribbles.

"Why all the notes?" Alex asked.

Byte replied, "Those are comments! Comments help you and others understand your code later. They're ignored by the system, but priceless for humans."

Emma chimed in, "But did you know CAP supports special doc comments that become part of your service metadata?"

---

**Doc Comments in CAP**

A multi-line comment of the form `/** ... */` at an annotation position is considered a doc comment and used as a documentation of the that element where it is written:

```js
/**
 * I am the description for "Employee"
 */
entity Employees {
  key ID : Integer;
  /**
   * I am the description for "name"
   */
  name : String;
}

The text of a doc comment is stored in CSN in the property doc.
When generating OData EDM(X), it appears as the value for the annotation @Core.Description.


**Best Practices**

- Use comments to explain why, not just what
- Keep comments up to date
- Remove obsolete comments

---

Alex smiled, "Now my future self will thank me!"

Byte nodded, "Exactly! Next, let's build some entities and types."

---
