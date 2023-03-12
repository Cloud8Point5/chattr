Character Directives
====================

Character directives are Chattr's stage directions.
Use them to have characters leave, join, start talking,
speak to specific characters, and more.

Referencing a Character
-----------------------
Just type their name. You can also use a comma-separared
list to reference multiple characters in a group.
You can use an expression with parentheses.

::
    Grahm:
    Lisa, Jake:
    ('Li'+'ly'):
    (playerName), Lisa:


Changing Speakers
-----------------
Use a colon after a character reference to make them speak:

::
    Lisa: "I'm talking!"
    Grahm: "Now I'm Talking!"

You can have them speak to another character with the `to` keyword.

::
    Lisa to Grahm: "Hey, don't steal my thunder like that."
    Lisa, Grahm to Lily, Jake: "We, as multiple people, are talking to multiple people."

Revert to speaking as or to no one with `!:`

::
    !: "Now no one is talking."
    Lisa to !: "Now I'm talking to no one."

Automatic back-and-forth happens then the person 
the previous speaker was talking to starts talking.

::
    Lisa to Grahm: "Hey, I'm talking to you, you know!"
    Grahm: "Huh? Even though it wasn't explicitly written, I'm talking back to you."

Use an explicit `to !:` to prevent this.

::
    Lisa to Grahm: "Hey, I'm talking to you, you know!"
    Grahm to !: "And I'm ignoring you by talking to the whole group."


Join, Leave, and Stay
---------------------

To have characters join the game, use a reference followed by `join` or `joins`.

::
    Lisa joins
    Lily, Grahm join

They can leave using `leave` or `leaves`.

::
    Lisa leaves
    Lily, Grahm leave

Using the `stay` command causes the referenced characters to
join if they aren't there yet, as well as causing everyone else
to leave.

::
    Lisa stays
    Lily, Grahm stay

Nicknames
---------

Nicknames can be changed with the `as` keyword
They can be combined with a colon to cause that character to start speaking.
They can also be used after a `join` directive.

::
    Lisa as "The Darkness Whisperer"
    Grahm as "Not Grahm":
    Lily joins as "Lilith"

To revert to the default display name for a character, use an
empty set of quotes.

::
    Lisa as "":
    "I'm actually not The Darkness Whisperer."

