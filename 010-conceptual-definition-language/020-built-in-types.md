---
layout: chapter
title: "Built-in Types — The Secret Ingredients of CDL"
---

*Alex and Byte return, ready to cook up some data magic!*

---

Alex and Byte strolled into the bustling kitchen of CDL Land, where pots bubbled and spoons clattered. Byte wore a chef’s hat (slightly askew), and Alex looked around, wide-eyed.

"Byte, what are all these jars and bottles?" Alex asked, peering at a shelf labeled `String`, `Integer`, `UUID`, and more.

Byte twirled a wooden spoon. "These are the built-in types, Alex! Think of them as the secret ingredients for every recipe you’ll ever make in CDL. Want to store a name? Use `String`. Counting books? That’s `Integer`. Need a unique code? Grab a `UUID`!"

Alex grinned. "So, every field in my entity gets one of these types?"

"Exactly!" Byte nodded. "Let’s look at some of the most popular ones."

---

**Byte’s Top Picks:**

- `UUID` — A globally unique identifier. Like a secret code for every row!
- `Boolean` — True, false, or null. Great for yes/no questions.
- `Integer`, `Int16`, `Int32`, `Int64`, `UInt8` — All sorts of numbers, big and small.
- `Decimal`, `Double` — For prices, measurements, and anything with fractions.
- `Date`, `Time`, `DateTime`, `Timestamp` — For all your time-traveling needs.
- `String`, `LargeString` — Words, sentences, or even whole books!
- `Binary`, `LargeBinary` — For files, images, or secret codes.
- `Map`, `Vector` — For advanced wizards (and Byte’s favorite experiments).

---

Alex picked up a jar labeled `String (111)`. "What’s with the number?"

Byte explained, "You can set the length for strings and binaries. For example, `String(111)` means the field can hold up to 111 characters. If you don’t specify, it defaults to 255 (or 5000 on HANA)."

Alex nodded, then pointed to a jar marked `Decimal(10,3)`. "And this one?"

"That’s for numbers with decimal places! `Decimal(10,3)` means up to 10 digits, with 3 after the decimal point. Perfect for prices."

---

Byte waved his spoon. "Let’s see these types in action!"

```cds
entity Books {
  key ID : UUID;
  title  : String(111);
  stock  : Integer;
  price  : Price;
}
type Price : Decimal;
```

"Here, `ID` is a UUID, `title` is a string, `stock` is an integer, and `price` uses a custom type called `Price`, which is a decimal."

Alex scribbled in his notebook. "So I can make my own types, too?"

"Absolutely!" Byte beamed. "You can define custom types for reuse, like this:"

```cds
type Amount {
  value    : Decimal(10,3);
  currency : Currency;
}
```

---

Alex peeked at a mysterious jar labeled `Map`. "What’s this for?"

Byte whispered, "That’s for storing JSON data—like a treasure chest for anything you want! But be careful: not every database supports every type."

Alex nodded, then spotted a jar labeled `Vector`. "And this?"

"That’s for advanced stuff, like AI and machine learning. Only available on the latest SAP HANA Cloud!"

---

Byte handed Alex a handy chart:

| CDS Type         | Remarks                                 | Example Usage         |
|------------------|-----------------------------------------|----------------------|
| UUID             | Unique identifier (RFC 4122)            | key ID : UUID;       |
| Boolean          | true, false, null, 0, 1                 | isActive : Boolean;  |
| Integer          | 32-bit integer                          | stock : Integer;     |
| Decimal(10,3)    | Decimal with precision and scale         | price : Decimal(10,3);|
| String(255)      | String with max length                   | name : String(255);  |
| Date             | Date only                               | published : Date;    |
| Time             | Time only                               | startTime : Time;    |
| Timestamp        | Date and time with microseconds         | createdAt : Timestamp;|
| LargeString      | Unlimited text                          | description : LargeString;|
| Binary(255)      | Binary data                             | image : Binary(255); |
| Map              | JSON object                             | metadata : Map;      |
| Vector           | AI/ML vectors (HANA only)               | embedding : Vector(128);|

---

Alex asked, "What about default values?"

Byte replied, "You can set them like this:"

```cds
entity Foo {
  bar : String default 'bar';
  boo : Integer default 1;
}
```

---

Alex stretched. "Anything else I should know?"

Byte winked. "Just remember: built-in types are your foundation. Use them wisely, and your data models will be strong and flexible!"

Alex grinned. "Ready for the next adventure!"

Byte spun his chef’s hat. "Next up: Literals and how to use them to spice up your models!"
