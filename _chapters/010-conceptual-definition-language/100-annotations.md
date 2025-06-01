---
layout: chapter
title: "Annotations — Adding Meaning and Metadata"
---

*Alex and Byte unlock the power of annotations to enrich their data models!*

---

Alex and Byte entered a room filled with glowing symbols and sticky notes. "What are all these extra notes for?" Alex wondered.

Byte grinned, "These are annotations! In CDL, annotations let you add extra meaning, metadata, and instructions to your models. They help tools, frameworks, and even other developers understand how to use your entities, fields, and services."

---

**What Are Annotations?**

Annotations are like sticky notes or tags you attach to parts of your model. They can:
- Control how data is exposed in services
- Add descriptions and labels
- Influence UI generation
- Define validation rules
- And much more!

---

**Basic Syntax**

"You add annotations with an `@` sign, right before the thing you want to annotate."

```cds
@title: 'Book'
@description: 'A book in the library'
entity Book {
  key ID : Integer;
  title  : String;
  @mandatory
  author : Association to Author;
}
```

"Here, the Book entity has a title and description, and the author association is marked as mandatory."

---

**Common Annotations**

- `@title` and `@description`: Add human-readable names and explanations
- `@readonly`: Make a field or entity read-only in generated UIs
- `@mandatory`: Require a value for a field
- `@default`: Set a default value
- `@Capabilities.Insertable`, `@Capabilities.Updatable`, etc.: Control OData service behavior

---

**Annotations on Elements and Entities**

"You can annotate almost anything: entities, fields, associations, even services!"

```cds
@title: 'Author'
entity Author {
  key ID : Integer;
  @title: 'Full Name'
  name   : String;
  @readonly
  country: Association to Country;
}
```

---

**Annotations for UI and Services**

"Some annotations are used by SAP Fiori Elements or OData services to generate smart UIs or control API behavior."

```cds
@UI: {
  headerInfo: {
    typeName: 'Book',
    typeNamePlural: 'Books',
    title: { type: 'Main', value: 'title' }
  }
}
entity Book {
  key ID : Integer;
  title  : String;
  author : Association to Author;
}
```

---

**Custom Annotations**

"You can invent your own annotations for use in your project or tooling!"

```cds
@myCompany.audit: true
entity Book {
  key ID : Integer;
  title  : String;
}
```

---

**Best Practices**

- Use annotations to make your models self-explanatory
- Prefer standard annotations for compatibility with tools
- Document custom annotations for your team
- Use annotations to drive UI and API behavior, not just for documentation

---

Alex smiled, "Annotations are like magic notes that make my models smarter!"

Byte nodded, "Exactly! Next, let's explore advanced queries and calculated fields."

---
