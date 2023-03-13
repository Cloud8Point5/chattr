Programming
===========

Chattr has basic programming functionality
including variables, functions, and control flow.


Variables
---------

There are no variable declarations.
Simply assign to it and it will declare itself.
Variables are untyped, but you can do type checking with
the ``is`` keyword.

Assignment is done with the standard ``=`` operator.
These compound assignment operators are also supported:
``+=``, ``-=``, ``*=``, ``/=``, ``%=``. 

Supported data types are ``number`` (stored as ``float`` in Godot),
``string``, ``bool``, ``callable``, ``view``, and ``null``.
Callables are anonymous functions, and views, if you haven't
gotten this that far yet, are a way to do asynchronous dialogue.
String literals must use single quotes ``'hello'``. Double
quotes are for dialogue and nicknames.

Variables are scoped to the current block.

.. code-block::
    
    x = 12
    x += 2
    # x is 14.
    y = 'Hello World'

    function = func(arg) {...}

Expressions
-----------

Since chattr doesn't care about white space,
but also doesn't have statement delimiters,
all expressions must be wrapped in parentheses.
Standard math operations are present: ``+ - * / %``.
Logical operators also exist: ``&& || !``.
You can also write logical operators as full words
if you prefer: ``and or not``.
Order of operations is followed.

.. code-block::

    x = (3 + 3 * 3)
    # x is 18


Control Flow
------------

If statements are accomplished like this:

.. code-block::

    if (expression) {
        ...
    } else if (...) {
        ...
    } else {
        ...
    }

If you'd like, you can use ``elif`` instead of ``else if``.

Match statements also exist:

.. code-block::

    match num [
        1 {"num is 1"}
        (6-1) {"num is 5"}
        default {"num is {num}"}
    ]

You can use ``switch`` in place of ``match`` if you prefer.

Loops don't presently exist, but they can be emulated with ``goto``.


Functions
---------

Function declarations can only exist at the root of
the file, and they're hoisted so you can use them from anywhere.

.. code-block::

    func name(param1, param2) {
        ...
    }

You can call them like this:

.. code-block::
    
    name('hello', 1)

If hoisting isn't what you want, or you wish to
define a function somewhere that isn't at the root,
use a function literal.


Imports
-------

You can import functions and labels from
another file with ``import``.
You type the name of the variable you want
to store the contents in, followed by
the path of the target file (.chattr is optional).

.. code-block::

    import Name from './file'
    Name.function()
