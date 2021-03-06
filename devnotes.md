Current State
=============

SQL92 support is, AFAIK, complete. Anything missing is a bug.

MySQL support should be complete except for those (and COLLATE <collation>
suffixes).  This includes full support for alterable delimiters.  Also
should document outside of code the one way it differs from MySQL in
handling DELIMITER.

SQLite support is new, but appears to be complete.  Their documentation is
not easy to translate into a lexer without going through it methodically so
I won't feel that SQLite support is solid until I write a parser for it.

Next up
-------

A transform that emits arrays of tokens making up commands, buffering up
till a delimiter or EOF.

A transform that takes chunks as above and pushes them out as SQL.

A writable that takes strings and executes them via node-mysql2 (tied to the
mysql dialect for now).

A commandline tool that uses these to execute SQL from a file a'la `modyllic
apply`.


Other Notes
-----------

Lexical level limits to check, in SQL92:

identifiers no greater then 128 characters
national chars in N'' strings
bits only in B'' strings
hexits only in X'' strings
