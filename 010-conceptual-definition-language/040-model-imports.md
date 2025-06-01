---
layout: chapter
title: "Model Imports — Bringing in Ingredients from Other Kitchens"
---

*Alex and Byte discover how to reuse and combine models in CDL Land!*

---

Alex and Byte wandered into a bustling bazaar, where chefs from every corner of CDL Land traded their secret ingredients. Byte pointed to a sign: "Model Imports."

"Byte, what’s a model import?" Alex asked, eyeing a jar labeled `using`.

Byte grinned, "It’s how you bring in definitions—like types, entities, or aspects—from other files or packages. It’s like borrowing a spice from your neighbor’s kitchen!"

---

**How to Import in CDL**

Byte showed Alex a recipe card:

```cds
using foo.bar.scoped.Bar from './contexts';
using foo.bar.scoped.nested from './contexts';
using foo.bar.scoped.nested as specified from './contexts';
```

"You can import single definitions, several with a common namespace, or even give them a local alias!" Byte explained.

---

**Multiple Named Imports**

"Want to import several things at once? Use curly braces!"

```cds
using { Foo as Moo, sub.Bar } from './base-model';
entity Boo : Moo { /*...*/ } // Boo inherits all fields from Moo, and you can add more inside the braces
entity Car : Bar {
  color : String;      // New field: color of the car
  wheels: Integer;     // New field: number of wheels
  electric: Boolean;   // New field: is the car electric?
} // Car inherits all fields from Bar, plus these custom fields
```

"This is called entity inheritance or includes. The colon (:) means 'inherits from' or 'includes.' Boo gets all of Moo’s fields, and Car gets all of Bar’s fields. You can then add new fields or override properties inside the curly braces. For example, here Car adds its own fields: `color`, `wheels`, and `electric`, in addition to everything it inherits from Bar. It’s a great way to reuse and extend your models!"

"You can also use fully qualified names if you want to be extra clear," Byte added.

---

**How Imports Are Resolved**

Byte spun a globe. "CDL resolves imports much like Node.js or ES6 modules:"
- Paths starting with `./` or `../` are relative to the current file.
- Paths starting with `/` are absolute.
- Names like `@sap/cds/common` are fetched from `node_modules`.
- The compiler looks for `.cds`, `.csn`, or `.json` files, or for a folder with a `package.json` or `index.cds`.

"Pro tip: Omit the `.cds` suffix in your import statements for best compatibility!"

---

**Why Use Imports?**

Alex asked, "Why not just copy everything into one file?"

Byte shook his head, "That’s like dumping every spice into one pot! Imports help you keep your models organized, reusable, and easy to maintain. You can share types, entities, and aspects across projects."

---

**Example: Using an Imported Type**

```cds
using { managed } from '@sap/cds/common';

entity Books : managed {
  title  : String;
  author : Association to Authors;
}
```

"Here, `managed` is imported from the standard CAP library, giving your entity built-in fields like `createdAt` and `modifiedAt`!"

---

Alex smiled, "So, with imports, I can build on top of what others have created, and keep my own models neat and tidy."

Byte nodded, "Exactly! Next up: Namespaces and how to keep your definitions organized in the world of CDL."
