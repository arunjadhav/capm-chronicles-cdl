---
layout: chapter
title: "Security & Authorization — Keeping Your Data Safe"
---

*Alex and Byte learn how to protect their data models with roles, restrictions, and authorization checks!*

---

Alex and Byte entered a vault with heavy doors and security cameras. "Why all the locks?" Alex asked.

Byte replied, "This is where we keep our data safe! In CAP and RAP, you can control who can see or change data using roles and authorization rules."

---

**Why Security Matters**

- Protect sensitive data from unauthorized access
- Ensure only the right users can perform certain actions
- Meet compliance and audit requirements

---

**Defining Roles**

"You define roles in your application and assign them to users."

Example roles:
- `admin`
- `editor`
- `viewer`

---

**Restricting Access with Annotations**

"You can use annotations to restrict access to entities, fields, or actions."

```cds
@restrict: [
  { grant: 'READ', to: 'viewer' },
  { grant: ['READ', 'WRITE'], to: 'editor' },
  { grant: '*', to: 'admin' }
]
entity Book {
  key ID : Integer;
  title  : String;
  price  : Decimal(9,2);
}
```

---

**Authorization in Services**

"You can also check roles in your service handlers (Node.js/ABAP) for custom logic."

Example (Node.js):
```js
// ...existing code...
this.before('UPDATE', 'Book', (req) => {
  if (!req.user.is('editor')) {
    req.reject(403, 'Only editors can update books.');
  }
});
// ...existing code...
```

---

**Field-Level Restrictions**

"You can restrict access to specific fields, not just whole entities."

```cds
entity Author {
  key ID : Integer;
  name   : String;
  @restrict: [ { grant: 'READ', to: 'admin' } ]
  salary : Decimal(9,2);
}
```

---

**Best Practices**

- Use roles and restrictions to enforce least privilege
- Prefer annotations for simple, declarative security
- Use service handler checks for complex or dynamic rules
- Regularly review and test your security setup

---

Alex locked the vault, "Now our data is safe from prying eyes!"

Byte nodded, "Exactly! Next, let's explore extensibility—how to adapt your models for the future."

---
