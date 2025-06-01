---
layout: chapter
title: "Extensibility — Adapting Your Models for the Future"
---

*Alex and Byte discover how to extend, override, and adapt their data models without breaking what already works!*

---

Alex and Byte entered a room with building blocks and extension kits. "Why so many add-ons?" Alex asked.

Byte replied, "That's extensibility! In CAP, you can adapt your models for new requirements, customers, or projects—without changing the original code."

---

**Why Extensibility?**

- Add new fields or entities for specific customers
- Override or enhance existing logic
- Keep core models clean and upgradeable

---

**Extending Entities**

"You can add fields to existing entities using extensions."

```cds
extend entity Book with {
  genre : String;
  publishedYear : Integer;
}
```

---

**Extending Services**

"You can also add new actions, functions, or projections to services."

```cds
extend service LibraryService with {
  action recommendBooks(userID: Integer) returns many Book;
}
```

---

**Overriding Logic**

"You can override or enhance logic in your service handlers (Node.js) without touching the original implementation."

Example (Node.js):
```js
// ...existing code...
this.after('READ', 'Book', (books) => {
  // Add custom logic after reading books
});
// ...existing code...
```

---

**Best Practices**

- Use extensions for customer- or project-specific changes
- Avoid modifying core models directly
- Document all extensions and overrides
- Test extensions to ensure compatibility with upgrades

---

Alex stacked some new blocks, "Now I can build on top of what I already have!"

Byte nodded, "Exactly! With extensibility, your models are ready for anything the future brings."

---
