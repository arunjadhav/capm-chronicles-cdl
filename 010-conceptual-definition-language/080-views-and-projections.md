---
layout: chapter
title: "Views & Projections — Seeing Your Data from Every Angle"
---

*Alex and Byte learn how to create new perspectives on their data using views and projections!*

---

Alex and Byte entered the Observatory, where giant lenses and mirrors let them see the world in new ways. Byte pointed to a telescope labeled "Views & Projections."

"Byte, what’s a view?" Alex asked, peering through the lens.

Byte replied, "A view is like a virtual table. It lets you define a new way to look at your data, based on existing entities. You can select, filter, and even join data, all without changing the underlying tables!"

---

**Creating a View with `as select from`**

Byte showed Alex an example:

```cds
entity AvailableBooks as select from Book {
  ID,
  title,
  author
} where status = 'available';
```

"This creates a view called `AvailableBooks` that only shows books with status 'available'."

*When to use:* Use `as select from` when you need to create a virtual table that combines, filters, or transforms data from one or more entities. Great for reporting, analytics, or simplifying complex queries. Example: Showing only available books, joining books with authors, or aggregating sales data.

---

**Projections: The `as projection on` Variant**

"Projections are a special kind of view. They let you expose only certain fields or associations, and are especially useful for services."

```cds
entity PublicBooks as projection on Book {
  ID,
  title
}
```

"Now, `PublicBooks` only exposes the ID and title of each book."

*When to use:* Use `as projection on` when you want to expose only a subset of fields or associations from an entity, especially in a service. This is ideal for controlling what data is available to consumers (like APIs or UIs), hiding sensitive fields, or customizing the shape of your data for different consumers. Example: OData services, REST APIs, or Fiori apps where you want to control the data contract.

---

**Views with Parameters**

"You can even create views that take parameters!"

```cds
entity BooksByAuthor ( authorName : String )
as select from Book {
  ID,
  title
} where author = :authorName;
```

"When you query `BooksByAuthor`, you provide an author name, and get only their books."

*When to use:* Use parameterized views when you want to create a reusable query that takes input from the user or another system. Perfect for search screens, filtered reports, or any scenario where the result depends on a parameter (like filtering books by author, date, or category). Example: search endpoints, user-driven filters, or dynamic data retrieval in applications.

---

**Why Use Views and Projections?**

- To simplify complex queries
- To expose only the data you want in a service
- To create reusable, readable models

---

**Best Practices**

- Use views for complex data transformations or filtering
- Use projections to control what’s exposed in your APIs
- Name your views and projections clearly

---

Alex smiled, "With views and projections, I can give everyone just the right perspective on my data!"

Byte nodded, "Exactly! Next up: Associations & Compositions—connecting your data together!"
