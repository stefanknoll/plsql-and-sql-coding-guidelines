# Introduction to the Insum PL/SQL and SQL Coding Guidelines

SQL and PL/SQL code is fundamentally some of the most important code that Insum writes for our customers and partners. The difference between SQL and PL/SQL that performs well and that doesn't can be the difference between a successful system (our customers and partners) and a huge disappointment (Healthcare.gov's rollout for example, not done by Insum...).

For a PDF version of these guidelines use [Insum-PLSQL-and-SQL-Coding-Guidelines.pdf](Insum-PLSQL-and-SQL-Coding-Guidelines.pdf)

In 2019, Rich Soule of Insum forked these guidelines from the [Trivadis guidelines](https://trivadis.github.io/plsql-and-sql-coding-guidelines/) and changed most of the rules to comply with Insum coding standards and added many new guidelines. New rules were also suggested in the Trivadis Issues, and while many were adopted, some (and some we consider very important) were not.

Originally, Trivadis published their guidelines for PL/SQL &amp; SQL in 2009 in the context of the DOAG conference in Nuremberg. Since then these guidelines have been continuously extended and improved. Now they are managed as a set of markdown files. This makes the the guidelines more adaptable for individual application needs and simplifies the continous improvement.

We all stand in the shoulders of giants. Many people have participated in the creation and refinement of these guidelines. Without the efforts from Roger Troller, Jörn Kulessa, Daniela Reiner, Richard Bushnell, Andreas Flubacher, Thomas Mauch, and Philipp Salvisberg, and, more recently, many folks from the Insum Team, these guidelines wouldn't be what they are today.

### Why are standards important

For a machine executing a program, code formatting is of no importance. However, for the human eye, well-formatted code is much easier to read. Modern tools can help to implement format and coding rules.

Implementing formatting and coding standards has the following advantages for PL/SQL development:

* Well-formatted code is easier to read, analyze and maintain (not only for the author but also for other developers).
* The developers do not have to define their own guidelines - it is already defined.
* The code has a structure that makes it easier to avoid making errors.
* The code is more efficient concerning performance and organization of the whole application.
* The code is more modular and thus easier to use for other applications.

This document only defines possible standards. These standards are not written in stone, but are meant as guidelines. If standards already exist, and they are different from those in this document, it makes no sense to change them unless the existing standards have fundamental flaws that would decrease performance and/or significantly decrease the maintainability of code. Almost every system has a mixture of "code that follows the standards" and "code that doesn't follow the standards". Gental migration over time to follow a good set of reasonable standards will always be much better than giving up because standards were not followed in the past.

Overall, the most important thing when writing good code is that you must be able to defend your work.

## License

The Insum PL/SQL &amp; SQL Coding Guidelines are licensed under the Apache License, Version 2.0. You may obtain a copy of the License at <http://www.apache.org/licenses/LICENSE-2.0>.

### Trademarks

All terms that are known trademarks or service marks have been capitalized. All trademarks are the property of their respective owners.

### Disclaimer

The authors and publisher shall have neither liability nor responsibility to any person or entity with respect to the loss or damages arising from the information contained in this work. This work may include inaccuracies or typographical errors and solely represent the opinions of the authors. Changes are periodically made to this document without notice. The authors reserve the right to revise this document at any time without notice.

## Revision History

Version | Who         | Date         | Comment
--------|-------------|--------------|--------
1.0     | Soule       | 2020.02.05   | Forked from the [Trivadis](https://trivadis.github.io/plsql-and-sql-coding-guidelines/) standards with many updates due to coding style and minor updates to grammar, removal of some sections, changes to titles of other sections, etc.

