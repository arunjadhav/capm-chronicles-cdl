---
layout: chapter
title: "Entities & Type Definitions — Building Blocks of Your Data Model"
---

*Alex and Byte roll up their sleeves to create real-world data structures in CDL!*

---

Alex and Byte entered the Workshop of Wonders, where every tool and blueprint was ready for building. Byte handed Alex a shiny hammer. "Ready to create your own entities and types?"

"Let’s do it!" Alex grinned.

---

**What is an Entity?**

Byte explained, "An entity is like a table in a database. It’s a structured type with named and typed elements, representing sets of data you can read and manipulate. Entities usually have one or more primary keys."

He showed Alex an example:

```cds
define entity Book {
  key ID : Integer;
  title  : String;
  author : String;
}
```

"The `key` marks the primary key. You can use `define entity` or just `entity`—the `define` is optional!"

---

**Custom Type Definitions**

"Want to reuse a type? Define your own! Types can be simple, structured, or even associations."

```cds
define type ISBN : String(13);
define type Price {
  value    : Decimal(10,2);
  currency : String(3);
}
```

"Now you can use `ISBN` or `Price` in your entities."

---

**Structured Types and Inline Structs**

"You can declare and use custom struct types, or even define them inline:"

```cds
type Address {
  street : String;
  city   : String;
  zip    : String;
}

entity Customer {
  address : Address;
}

// Or inline:
entity Customer {
  address : {
    street : String;
    city   : String;
    zip    : String;
  };
}
```

---

**Arrayed Types**

"Need a list of something? Use `many` or `array of`:"

```cds
entity Book {
  genres : many String;
}
```

---

**Virtual and Calculated Elements**

"Sometimes you want fields that aren’t stored in the database, or are calculated on the fly. Use `virtual` or calculated elements!"

```cds
entity Book {
  title : String;
  virtual summary : String; // This is a virtual element, not stored in the database
  fullTitle : String = (title || ' by ' || author); // This is a calculated element, computed on the fly
}
```

// Note: Only fields with the 'virtual' prefix are true virtual elements (not stored in the DB). Fields defined with '=' are calculated elements, which are computed on read (and may or may not be virtual depending on the context and database support). In this example, 'summary' is a virtual element, while 'fullTitle' is a calculated element.

---

**Default Values and Constraints**

"You can set default values and constraints, too!"

```cds
entity Book {
  status : String default 'available';
  price  : Decimal not null;
}
```

---

**Enums**

"Want to restrict values? Use enums!"

```cds
type BookStatus : String enum { available; checked_out; lost; };
entity Book {
  status : BookStatus default #available;
}
```

---

Alex smiled, "Now I can build any data structure I need!"

Byte nodded, "Exactly! Next up: Views & Projections—see your data from every angle!"
