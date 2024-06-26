A very lightweight package that provides functions to convert between Gregorian and Solar Hijri calendars.
Solar Hijri is the official calendar being used in Iran.

Installation
------------
Requires Python 3.12+

``pip install gshconverter``

Usage
-----
The main functions are:

* ``solar_hijri_to_gregorian(sh_year: int, sh_month: int, sh_day: int) -> tuple[int, int, int]``
* ``gregorian_to_solar_hijri(g_year: int, g_month: int, g_day: int) -> tuple[int, int, int]``
* ``is_g_leap(year: int) -> bool``
* ``is_sh_leap(year: int) -> bool``

**Example:**

.. code-block:: python

    >>> from gshconverter import *
    >>> is_sh_leap(1403)
    True
    >>> solar_hijri_to_gregorian(1403, 12, 30)
    (2025, 3, 20)
    >>> gregorian_to_solar_hijri(2025, 3, 20)
    (1403, 12, 30)

Notes
-----
This library currently assumes 33-year cycles which means it will get inaccurate for dates too far in the future (the first known incorrect year is 1502 SH) or too far in the past (the results are known to be correct at least until 1210 SH according to `University of Tehran astronomical calculation`_).

The output of converter functions are the same as the ones in `FarsiWeb's jalali.c`_ , but ``gshconverter`` uses a different algorithm and is written from scratch. It also is faster than the `current Python implementation used in jdatetime library`_ .

.. _FarsiWeb's jalali.c: http://www.farsiweb.info/jalali/jalali.c
.. _University of Tehran astronomical calculation: https://calendar.ut.ac.ir/Fa/News/Data/Doc/KabiseShamsi1206-1498-new.pdf
.. _current Python implementation used in jdatetime library: https://github.com/slashmili/jalali-core/blob/36559e50b1c2cf5c866bc193aeb0c35a4db9fad6/jalali_core/__init__.py
