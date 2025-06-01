---
layout: chapter
title: "Namespaces — Keeping Your Definitions Organized in CDL Land"
---

*Alex and Byte learn how to keep their models tidy and avoid naming chaos!*

---

Alex and Byte strolled into the grand Hall of Names, where every shelf was neatly labeled and nothing ever got lost. Byte pointed to a golden plaque: "Namespaces."

"Byte, what’s a namespace?" Alex asked, admiring the tidy rows of jars.

Byte replied, "A namespace is like a label you put on all your definitions—entities, types, aspects—so you always know where they belong. It helps you avoid name clashes and keeps your models organized, especially in big projects!"

---

**How to Use Namespaces in CDL**

Byte showed Alex a scroll:

```cds
namespace bookstore.inventory;
entity Book {}
entity Author {}
```

"Now, both Book and Author are part of the bookstore.inventory namespace. Their full names are bookstore.inventory.Book and bookstore.inventory.Author!"

---

**Contexts: Nested Namespaces**

"Want to organize things even more? Use contexts for nested sections!"

```cds
namespace bookstore.inventory;
entity Book {}
context suppliers {
  entity Supplier {}
  context contacts {
    entity Contact {}
  }
}
```

"This way, you can have bookstore.inventory.Book, bookstore.inventory.suppliers.Supplier, and bookstore.inventory.suppliers.contacts.Contact. It’s like folders inside folders!"

---

**Scoped Definitions and Fully Qualified Names**

"You can also define types and entities with other definitions’ names as prefixes:"

```cds
namespace bookstore.inventory;
entity Book {}
entity Book.Review {}
type Book.Review.Rating {}
```

"This gives you bookstore.inventory.Book, bookstore.inventory.Book.Review, and bookstore.inventory.Book.Review.Rating."

---

**Why Use Namespaces?**

Alex asked, "Why not just use simple names?"

Byte explained, "In big projects, you might have lots of entities called 'Order' or 'User.' Namespaces make sure each one is unique and easy to find. They also help when you import models from other teams or packages!"

---

**How Namespaces Work**

- A namespace is not an object of its own—just a prefix for all following definitions.
- There’s no corresponding definition in the compiled model (CSN), but all names are fully qualified.
- You can use contexts for even more structure, like subfolders.

---

**Example: Compiled Names**

Byte showed Alex a peek at the compiled model and explained:

"When you write your CDL files, the CAP tools automatically generate a compiled model behind the scenes. This is called CSN (Core Schema Notation), and it's a machine-readable JSON representation of all your definitions. You never write this by hand—it's created for you when you build or deploy your project."

He showed Alex an example:

```json
{
  "definitions":{
    "bookstore.inventory.Book": { "kind": "entity" },
    "bookstore.inventory.suppliers": { "kind": "context" },
    "bookstore.inventory.suppliers.Supplier": { "kind": "entity" },
    "bookstore.inventory.suppliers.contacts": { "kind": "context" },
    "bookstore.inventory.suppliers.contacts.Contact": { "kind": "entity" }
  }
}
```

"This compiled model is what the CAP framework, deployment tools, and code generators use to understand and process your data model. For most developers, you only work with CDL—the compiled model is for the framework and advanced scenarios."

---

Alex smiled, "With namespaces, I’ll never lose track of my definitions again!"

Byte nodded, "Exactly! Next up: Comments and how to make your models easy for everyone to understand."
