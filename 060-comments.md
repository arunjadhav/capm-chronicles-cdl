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

**Best Practices**

- Use comments to explain why, not just what
- Keep comments up to date
- Remove obsolete comments

---

Alex smiled, "Now my future self will thank me!"

Byte nodded, "Exactly! Next, let's build some entities and types."

---
