SQLite based Minesweeper Field Renderer
=======================================

This repository contains a solution for the "Minesweeper" exercise as described in Exercism's Kotlin track, but in sqlite.

Introduction
-----------

The task is to transform an ASCII-Art representation of the mine locations in a minesweeper field to a full render of the field including the mine-counts.

e.g.:
Given input:
```
+-----+
| * * |
|  *  |
|  *  |
|     |
+-----+
```

Produce output:
```
+-----+
|1*3*1|
|13*31|
| 2*2 |
| 111 |
+-----+
```

The input board is provided line-by-line, in the form of INSERTs into the "input" view.  
Output is provided, again line-by-line as the "output" view.  
To reset the board, insert the line 'RESET' into input.

Repository contents:
--------------------
```
| tests        Unit tests
| schema.sql   The minesweeper-renderer implementation (views, tables, triggers)
| test.sh      Runner script for the unit tests
```

Tests:
------
The `tests` directory contains several SQL files to insert example board input, as well as the expected output.

Examples
--------
```sql
INSERT INTO input(line) VALUES 
    ('RESET'),
    (' * * '),
    ('  *  '),
    ('  *  '),
    ('     ')
;
SELECT display FROM output ORDER BY rownum;
```
This should yield the output as described in the introduction.


```sql
INSERT INTO input(line) VALUES
    ('RESET'),
    ('     '),
    ('   ');
```
Since the rows in the field don't have the same length, this will fail with an error message.  
Additionally, the table field_info should contain a more detailled error message.


How it works:
-------------
TODO!