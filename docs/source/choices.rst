Choices
=======

Choices allow players to branch the story depending on which option they choose.
Choices are only given to the currently speaking characters, or if there is no speaker, 
every character currently being controlled by a player.

Set Up a Choice
---------------

.. code-block::

    choice [
        "Option 1"
        "Option 2"
        "Option 3"
    ]

This setup displays 3 options ("Option 1", "Option 2", and "Option 3"), 
but right now they won't do anything special when chosen.
If we want to branch, we need to put each option in its own set of braces.
This allows us to change option settings.

.. code-block::

    choice [
        {
            "Option 1"
            goto @Option1
        }
        {
            "Option 2"
            goto @Option2
        }
        {
            "Option 3"
            goto @Option3
        }
    ]

Now, each option will jump to the specified label when chosen.

Let's say we don't want option 1 to jump to an entirely different section. 
Instead, we just want to display some unique flavor text and continue normally.
Every option can have a code block associated with it. Just open another
set of braces:

.. code-block::

    choice [
        {
            "Option 1"
            {
                "Option 1 flavor text"
            }
        }
        {
            "Option 2"
            goto @Option2
        }
        {
            "Option 3"
            goto @Option3
        }
    ]

If you want, you can add any valid Chattr code in that block.

Conditional Options
-------------------

Sometimes, an option should only be available if a condition is met.
For this reason, there exists the ``when`` keyword.

.. code-block::

    choice [
        {
            "Option 1"
            when (apples_collected == 3)
        }
        {
            "Option 2"
            goto @Option2
        }
        {
            "Option 3"
            goto @Option3
        }
    ]

Now, option 1 will appear as disabled when the player doesn't have 3 apples.

Hiding Options
--------------

If an option should be completely invisible (as opposed to just disabled) when it isn't available, use the ``hidden`` keyword.

.. code-block::

    choice [
        {
            "Option 1"
            when (apples_collected == 3)
            hidden
        }
        {
            "Option 2"
            goto @Option2
        }
        {
            "Option 3"
            goto @Option3
        }
    ]

Alternate Option Text When Disabled
-----------------------------------

If you want to show different text when an option is disabled, use the ``disabled`` keyword, 
followed by the alternative text.

.. code-block::

    choice [
        {
            "Option 1"
            when (apples_collected == 3)
            disabled "Option 1 (requires 3 apples)"
        }
        {
            "Option 2"
            goto @Option2
        }
        {
            "Option 3"
            goto @Option3
        }
    ]

Vanishing Options
-----------------

Say you have a choice that the player returns to after each option is picked.
This loop continues until all the options are exhausted.
Use the ``vanishing`` keyword to hide options on subsequent revisits to the same choice.

.. code-block::

    choice [
        {
            "Option 1"
            {
                "Option 1 flavor text"
            }
            vanishing
        }
        {
            "Option 2"
            {
                "Option 2 flavor text"
            }
            vanishing
        }
        {
            "Option 3"
            goto @Option3
        }
    ]

Override
--------

By default, if multiple characters are participating in a choice,
the option with the most votes will be executed.
If we want an option to automatically execute, ignoring the vote, 
use the ``override`` option. This is useful for special options only 
one player has access to.
The override keyword can be used like this:

.. code-block::

    choice [
        {
            "Option 1"
            when ($.is_special)
            override
        }
        {
            "Option 2"
            goto @Option2
        }
        {
            "Option 3"
            goto @Option3
        }
    ]

