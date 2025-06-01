---
layout: chapter
title: "Actions & Functions — Making Your Models Interactive"
---

*Alex and Byte discover how to add custom logic and operations to their data models!*

---

Alex and Byte entered a workshop filled with buttons and levers. "What do these do?" Alex asked.

Byte replied, "These are actions and functions! In CAP, you can define custom operations that go beyond simple CRUD. Actions can change data, and functions can return calculated results."

---

**What Are Actions and Functions?**

- **Actions**: Operations that may change data (side effects allowed)
- **Functions**: Operations that do not change data (side-effect free)

Both can be called from your service API, UI, or even other code.

---

**Defining Actions**

"You define actions inside a service or an entity. Actions can have parameters and return types."

```cds
service LibraryService {
  action markAsBestseller(bookID: Integer) returns Boolean;
}
```

"This action marks a book as a bestseller."

---

**Defining Functions**

"Functions are similar, but they don't change data."

```cds
service LibraryService {
  function getBookCountByAuthor(authorID: Integer) returns Integer;
}
```

---

**Actions and Functions on Entities**

"You can attach actions and functions directly to entities."

```cds
entity Book {
  key ID : Integer;
  title  : String;
  action rate(rating: Integer) returns String;
}
```

---

**Calling Actions and Functions**

"You can call actions and functions from your UI, from CAP handlers, or via OData/REST APIs."

Example OData call:
```
POST /LibraryService/markAsBestseller
{
  "bookID": 42
}
```

---

**Implementing Logic in JavaScript/ABAP**

"To make actions and functions do something, you implement their logic in your service handler (Node.js or ABAP)."

Example (Node.js):
```js
// ...existing code...
this.on('markAsBestseller', async (req) => {
  const { bookID } = req.data;
  // Custom logic here
  // ...
  return true;
});
// ...existing code...
```

---

**Best Practices**

- Use actions for operations that change data
- Use functions for calculations or lookups
- Keep logic in service handlers, not in the model
- Document your actions and functions for API consumers

---

Alex pressed a button, "Now my models can do things, not just store data!"

Byte smiled, "Exactly! Next, let's look at security and authorization—keeping your data safe."

---
