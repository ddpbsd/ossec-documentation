.. _manual_regex:

===============================
OSSEC Regular Expression Syntax
===============================

Currently OSSEC supports three regex syntaxes: `OS_Regex`, `OS_Match`, and
`pcre2`.
`OS_Regex/regex`_ is an OSSEC specific subset of regular expressions.
This syntax is considered legacy, and is being replaced by the `pcre2`
variant.
`pcre2` is provided by the `pcre2 <http://pcre.org>`_ library.
It is much more complete and more widely tested than OS_Regex.
`pcre2` will be the preferred syntax moving forward.
`OS_Match/sregex` is an even smaller subset of regular expressions.
It provides some very basic mechanisms used in matching, and is widely available
inside OSSEC.

.. _regex_pcre2:

pcre2
^^^^^

Information on the syntax for pcre2 can be found in the
`pcre <http://www.pcre.org/current/doc/html/>`_ documentation.

.. _os_regex:

OS_Regex/regex
^^^^^^^^^^^^^^

Fast and simple library for regular expressions in C.

This library is designed to be simple, but support the most common regular
expressions. It was designed with intrusion detection systems in mind, where
having all options is not crucial, but speed is.

.. _os_regex_exp:

**Supported expressions**::

    \w  ->  A-Z, a-z, 0-9, '-', '@' characters
    \d  ->  0-9 characters
    \s  ->  For spaces " "
    \t  ->  For tabs.
    \p  ->  ()*+,-.:;<=>?[]!"'#$%&|{} (punctuation characters)
    \W  ->  For anything not \w
    \D  ->  For anything not \d
    \S  ->  For anything not \s
    \.  ->  For anything

.. _os_regex_mod:

**Modifiers**::

    +  ->  To match one or more times (eg \w+ or \d+)
    *  ->  To match zero or more times (eg \w* or \p*)

.. _os_regex_schar:

**Special Characters**::

    ^ -> To specify the beginning of the text.
    $ -> To specify the end of the text.
    | -> To create an "OR" between multiple patterns.

.. _os_regex_escape:

**Characters Escaping**

To utilize the following characters they must be escaped::

    $ -> \$
    ( -> \(
    ) -> \)
    \ -> \\
    | -> \|

.. _os_match:

OS_Match/sregex
^^^^^^^^^^^^^^^

Faster than the OS_Regex/regex, but only supports simple string matching and the
following special characters.

.. _os_match_schar:

**Special Characters**::

    ^ -> To specify the beginning of the text.
    $ -> To specify the end of the text.
    | -> To create an "OR" between multiple patterns.

