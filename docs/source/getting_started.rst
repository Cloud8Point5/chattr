Getting Started
===============

This article will teach you the basics of Chattr through
a quick example script that increases in complexity as you progress.
Before starting, make sure you're familiar with the :doc:`editor`.

.. code-block::

    "Hello"

This is about the most basic script you can write.
The dialogue "Hello" will be shown with no speaker, and then
the conversation ends when the user continues.

.. code-block::

    Lisa: "Hello"
    Grahm: "What's up?"
    Lisa: 
    "Not much."
    "How 'bout you?"

You can change who's speaking by writing their name, followed by a colon.

.. code-block::

    Lisa joins
    Lisa: "Hello"
    Grahm: "What's up?" # Grahm hasn't joined yet, so right now he's
    # talking as if he's "off-screen".
    Lisa: 
    "Not much."
    "How 'bout you?"
    Grahm joins: # Grahm enters the scene, and starts talking due to the colon.
    "Not much going on here either."
    Lisa: "You're boring."
    Lisa leaves # Lisa exits
    Grahm: "...what?"

Participants can leave and join the conversation. 
They don't need to be present to speak, though.

.. code-block::

    Lisa joins
    Lisa to Grahm: "Hello"
    Grahm: "What's up?" # Grahm is still talking to Lisa, but it
    # doesn't need to be explicitly written because it's a
    # back-and-forth
    Lisa:
    "Not much."
    "How 'bout you?"
    Grahm joins
    Gram:
    "Not much going on here either."
    Lisa: "You're boring."
    Lisa leaves
    Grahm to !: "...what?" # A '!:' means Grahm is no longer
    # talking to anyone.

Characters can talk to each other.
Characters will automatically talk back to each other
if the new speaker is the character the previous speaker 
was speaking to. This can be overridden wit a ``to !:``

.. code-block::

    Lisa joins
    Lisa to Grahm: "Hello"
    Grahm to Lisa: "What's up?"
    Lisa:
    "Not much."
    "How 'bout you?"
    Grahm joins
    Gram:
    "Not much going on here either."
    Lisa: "You're boring."
    Lisa leaves
    Grahm to :: "...what?"
    You to Grahm: "Yeah, what was that about?"
    Grahm: *startled* "Who are you?" 

The player is a character in the story, so characters can talk to them.
Signals are emitted with asterisks.
Signal emissions are connected to the current speaker,
so your game can optionally treat them like emotes.

.. code-block::

    Lisa joins
    Lisa to Grahm: "Hello"
    Grahm to Lisa: "What's up?"
    Lisa:
    "Not much."
    "How 'bout you?"
    Grahm joins
    Gram:
    "Not much going on here either."
    Lisa: "You're boring."
    Lisa leaves
    Grahm to !: "...what?"
    You to Grahm: "Yeah, what was that about?"
    Grahm to You: *startled* "Who are you?">> # Continue to the next instruction
    # without pausing.
    choice [ # Define a choice for the player to make.
        {"Nunya" goto @nunya}
        {"Why do you ask?" goto @why}
        {"..." goto @continue}
    ]

    @nunya
    Grahm:
    "I'm not an idiot, dude."
    goto @continue # skip over the @why section

    @why
    Grahm:
    "You just came up to me and acted like we know each other."

    @continue
    Grahm:
    "You're weird."
    Grahm leaves

Labels are declared with an at-symbol, and can be jumped to with ``goto``.
You can automatically continue to the next instruction 
(without pausing for player input) with ``>>``.
You can define choices with the ``choice`` keyword, followed by a set of options
for players to choose from.