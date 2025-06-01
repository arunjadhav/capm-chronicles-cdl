---
layout: chapter
title: "Keywords & Identifiers — The First Steps in CDL Land"
---

*Starring Alex, Byte, and the magical world of Core Data Services!*

---

## Scene: The Library of CDL Land

Alex tiptoed into the grand Library of CDL Land, eyes wide with wonder. Byte, his ever-curious robot companion, zipped around him, making little beeping noises.

Alex twirled a strand of hair. "Byte, I keep seeing words like `entity`, `type`, and `namespace` in these books. Are they some kind of secret code?"

Byte spun in a circle, lights blinking. "Secret code? More like magic spells! In CDL, those are called keywords. They tell the system what you want to do. For example, `entity` is like saying, 'Hey, make me a table!' and `type` is for creating your own special building blocks."

Alex grinned. "So, keywords are the magic words, and I’m the wizard?"

"Exactly!" Byte did a little dance. "But every wizard needs to name their spells and potions. That’s where identifiers come in. You get to invent names for your entities, types, and fields. It’s like naming your pet dragon or your favorite book."

Alex giggled. "I’d call my dragon 'Fluffy'."

Byte pretended to breathe fire. "Just don’t name your entity 'Fluffy' unless you really mean it!"

Alex plopped down on a beanbag. "So, what exactly are keywords?"

Byte hovered closer. "Keywords are special words reserved by CDL. They start statements—like `entity`, `type`, `namespace`, `using`, and more. They’re not case-sensitive, so you can shout them, whisper them, or even write them upside down—well, maybe not upside down. But lowercase is the most stylish!"

Alex scribbled in his notebook. "ENTITY, Entity, entity... all the same?"

"You got it!" Byte beeped approvingly.

Alex tapped his pen. "And identifiers?"

Byte nodded. "Identifiers are the names you give to your creations. For example, in `entity Books { ... }`, 'Books' is an identifier."

Alex thought for a moment. "Can I name something '1Book'?"

Byte shook his head, making a silly buzzing sound. "Bzzz! Identifiers must start with a letter or underscore. So, 'Book1' and '_author' are cool, but '1Book' is a no-go."

Alex tried to write '1Book' in the air, and Byte playfully erased it with a laser pointer. "Nope!"

Alex whispered, "What if I want to use a really weird name? Like, with spaces or emojis?"

Byte’s eyes widened. "Whoa, slow down, emoji king! If you really must, you can use delimited identifiers by wrapping the name in `![ ... ]`. Like this:"

```cds
type ![Delimited Identifier] : String;
```

"But trust me," Byte said, lowering his voice, "avoid delimited identifiers unless you’re feeling especially rebellious. They can cause trouble with other tools and databases."

Alex nodded, making a mental note: *No dragons, no emojis, no trouble.*

Alex stretched. "Are identifiers case-sensitive?"

Byte did a handstand (or the robot equivalent). "Absolutely! 'Book' and 'book' are as different as night and day. So be careful with your naming!"

Suddenly, Byte conjured a hologram. "Let’s see a real example!"

```cds
namespace capire.bookshop;
using { managed } from `@sap/cds/common`;
aspect entity : managed { key ID: Integer }

entity Books : entity {
  title  : String;
  author : Association to Authors;
}

entity Authors : entity {
  name   : String;
}
```

Alex pointed. "So here, `namespace`, `using`, `aspect`, and `entity` are keywords. `capire.bookshop`, `managed`, `Books`, and `Authors` are identifiers."

Byte gave a thumbs up. "You’re catching on fast!"

Byte handed Alex a golden scroll titled 'Best Practices'.

- Use lowercase for keywords (it’s the cool way).
- Pick clear, meaningful names for identifiers.
- Avoid delimited identifiers and special characters (unless you’re feeling wild).
- Remember: keywords are not case-sensitive, but identifiers are!

Byte grinned mischievously. "Pop quiz! Which of these are valid identifiers?"

1. Book_1
2. 1Book
3. _author
4. bookTitle

Alex tapped his chin. "Hmm... 1, 3, and 4 are valid. But 2 isn’t, because it starts with a number!"

"Ding ding ding!" Byte spun in celebration. "You’re ready to start naming things in CDL."

Alex yawned. "What’s next, Byte?"

Byte winked. "Next, we’ll discover the magical world of Built-in Types—where you learn to shape your data like a true wizard! But first, snack break?"

Alex laughed. "Snack break!"
