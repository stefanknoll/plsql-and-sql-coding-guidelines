# Introduction to the Primus Solutions PL/SQL and SQL Coding Guidelines

SQL and PL/SQL code is fundamentally some of the most important code that Insum writes for our customers and partners. The difference between SQL and PL/SQL that performs well and that doesn't can be the difference between a successful system (our customers and partners) and a huge disappointment (Healthcare.gov's rollout for example, not done by Insum...).

For a PDF version of these guidelines use [Primus-PLSQL-and-SQL-Coding-Guidelines.pdf](Primus-PLSQL-and-SQL-Coding-Guidelines.pdf)

This documentation is created upon a fork of the [Insum-Styleguide](https://github.com/insum-labs/plsql-and-sql-coding-guidelines) which in turn has been a fork of the [Trivadis guidelines](https://trivadis.github.io/plsql-and-sql-coding-guidelines/).
Currently we are on our way of adapting it to our companie's requirements.

### Why are standards important

For a machine executing a program, code formatting is of no importance. However, for the human eye, well-formatted code is much easier to read. Modern tools can help to implement format and coding rules.

Implementing formatting and coding standards has the following advantages for PL/SQL development:

* Well-formatted code is easier to read, analyze and maintain (not only for the author but also for other developers).
* The developers do not have to define their own guidelines - it is already defined.
* The code has a structure that makes it easier to avoid making errors.
* The code is more efficient concerning performance and organization of the whole application.
* The code is more modular and thus easier to use for other applications.

This document only defines possible standards. These standards are not written in stone, but are meant as guidelines. If standards already exist, and they are different from those in this document, it makes no sense to change them unless the existing standards have fundamental flaws that would decrease performance and/or significantly decrease the maintainability of code. Almost every system has a mixture of "code that follows the standards" and "code that doesn't follow the standards". Gentle migration over time to follow a good set of reasonable standards will always be much better than giving up because standards were not followed in the past.

Overall, the most important thing when writing good code is that you must be able to defend your work.

## License

The Primus Solutions PL/SQL &amp; SQL Coding Guidelines are licensed under the Apache License, Version 2.0. You may obtain a copy of the License at <http://www.apache.org/licenses/LICENSE-2.0>.

### Trademarks

All terms that are known trademarks or service marks have been capitalized. All trademarks are the property of their respective owners.

### Disclaimer

The authors and publisher shall have neither liability nor responsibility to any person or entity with respect to the loss or damages arising from the information contained in this work. This work may include inaccuracies or typographical errors and solely represent the opinions of the authors. Changes are periodically made to this document without notice. The authors reserve the right to revise this document at any time without notice.

## Revision History

Version | Who         | Date         | Comment
--------|-------------|--------------|--------
1.0     | Stefan Knoll         | 2024.01.26   | Forked from the [Insum-Styleguide](https://github.com/insum-labs/plsql-and-sql-coding-guidelines/) standards with many updates due to coding style and minor updates to grammar, removal of some sections, changes to titles of other sections, etc.

