---
layout: chapter
title: "Literals — The Spices of CDL"
---

*Alex and Byte are back, ready to add flavor to their data models!*

---

Alex and Byte wandered into the bustling spice market of CDL Land. The air was filled with the scent of adventure—and a hint of cinnamon.

Alex picked up a tiny jar labeled `true`. "Byte, what are these little things?"

Byte grinned, juggling a handful of jars. "These are literals! Think of them as the raw ingredients you sprinkle into your models—actual values like numbers, text, dates, and more."

Alex sniffed a jar labeled `'A string\'s literal'`. "So, I can use these to set values in my entities?"

"Exactly!" Byte nodded. "Let’s check out the most common types of literals you’ll use in CDL."

---

**Byte’s Literal Sampler Platter:**

- `true`, `false`, `null` — For booleans and empty spots.
- `11`, `2.4`, `1e3`, `1.23e-11` — Numbers, big and small, even scientific!
- `'A string\'s literal'` — Text, with single quotes. Escape a quote with another quote.
- `` `A string\n paragraph` `` — Strings with escape sequences, like newlines or Unicode.
- `{ foo:'boo', bar:'car' }` — Records (like little objects).
- `[ 1, 'two', {three:4} ]` — Arrays (lists of things).

---

Alex asked, "What about dates and times?"

Byte produced a jar labeled `date'2025-06-01'`. "You can use type-prefixed strings for date and time literals!"

- `date'2025-06-01'`
- `time'16:11:32'`
- `timestamp'2025-06-01T12:34:56.789Z'`

"Perfect for time-traveling data!" Byte winked.

---

Alex found a jar with three backticks. "What’s this?"

Byte explained, "That’s a multiline string! In CDL, you can use triple backticks (```) to write long text, code, or even XML as the value of any annotation. The annotation name can be anything you like—@multiline, @data, @myContent, or whatever makes sense for your documentation or metadata."

He showed Alex some examples:

```cds
@multiline: ```
    This is a CDS multiline string attached as metadata.
    - Use this for long descriptions, instructions, or notes.
    - Indentation is stripped, so it always looks neat.
    - You can use escapes like \n (newline), \t (tab), or Unicode like \u{1F336} for 🌶️!
```

@data: ```xml
    <main>
      This XML is just metadata for documentation or tooling.
      The 'xml' after the backticks helps editors with syntax highlighting.
    </main>
```

@myContent: ```json
    {
      "example": "You can use any annotation name and any content you want!"
    }
```

"Remember," Byte added, "these annotations are just metadata. The core-compiler ignores them unless a tool or process is looking for them. Use them to keep your models well-documented and easy for others to understand!"

"Inside triple backticks, you can use escapes, and indentation is stripped. If you want to avoid a line ending, just end the line with a backslash (\)!"

---

Alex sprinkled some literals into a model:

```cds
entity Spices {
  key ID : Integer;
  name   : String default 'Cinnamon';
  spicy  : Boolean default true;
  added  : Date default date'2025-06-01';
}
```

---

Byte handed Alex a recipe card:

- Use single quotes for strings, double them up to escape: `'It''s spicy'`
- Use backticks for escape sequences: `` `Line\nBreak` ``
- Use curly braces for records, square brackets for arrays
- Use type-prefixed strings for dates and times
- Use triple backticks for multiline text

---

Alex grinned. "With all these spices, my models will be delicious!"

Byte spun, sending a cloud of glittering literals into the air. "Next up: Model Imports—how to bring in ingredients from other kitchens and reuse the best recipes in CDL Land!"
