---
layout: chapter
title: "Advanced Queries & Calculated Fields — Getting More from Your Data"
---

*Alex and Byte dive into the world of advanced queries, calculated fields, and expressions in CDL!*

---

Alex and Byte found a room filled with spinning gears and calculators. "What are all these for?" Alex asked.

Byte replied, "This is where we make our data smarter! With advanced queries and calculated fields, you can create new values, filter data, and even join information from different entities—all in your model."

---

**Calculated Fields**

"A calculated field is a field whose value is computed from other fields or associations."

```cds
entity Author {
  key ID : Integer;
  name   : String;
  books  : Association to many Book on books.author = $self;
  numBooks : Integer = count(books);
}
```

"Here, `numBooks` automatically counts how many books each author has."

---

**Expressions in Fields**

"You can use expressions to set default values, perform calculations, or even concatenate strings."

```cds
entity Book {
  key ID : Integer;
  title  : String;
  price  : Decimal(9,2);
  tax    : Decimal(4,2) = 0.07;
  priceWithTax : Decimal(9,2) = price * (1 + tax);
}
```

---

**Filtering and Projections**

"You can create views (projections) that filter or transform data from other entities."

```cds
entity Book {
  key ID : Integer;
  title  : String;
  price  : Decimal(9,2);
}

@cds.persistence.skip
view ExpensiveBooks as select from Book {
  ID,
  title,
  price
} where price > 50;
```

"This view only shows books with a price greater than 50."

---

**Joins and Associations in Queries**

"You can use associations in your queries to bring in related data."

```cds
view BookWithAuthor as select from Book {
  ID,
  title,
  author.name as authorName
};
```

---

**Virtual and Calculated Elements**

- `virtual` elements exist only in the model, not in the database table
- Calculated elements can be used in projections and services

```cds
entity Book {
  key ID : Integer;
  title  : String;
  @readonly
  virtual discountedPrice : Decimal(9,2) = price * 0.9;
}
```

---

**Best Practices**

- Use calculated fields for values that can be derived from other data
- Use projections to create reusable, filtered, or transformed views
- Mark fields as `virtual` if they shouldn't be stored in the database
- Keep calculations simple for maintainability

---

Alex grinned, "Now I can make my data do the hard work for me!"

Byte winked, "Exactly! Next, let's explore actions and functions—making your models interactive!"

---
