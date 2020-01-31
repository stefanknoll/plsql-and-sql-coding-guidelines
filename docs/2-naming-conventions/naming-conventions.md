# Naming Conventions

## General Guidelines

1. Never use names with a leading numeric character.
2. Always choose meaningful and specific names.
3. Avoid using abbreviations. 
4. If abbreviations are used, they must be widely known and accepted. 
5. Create a glossary with all accepted abbreviations.
6. Never use ORACLE keywords as names. A list of ORACLEs keywords may be found in the dictionary view `V$RESERVED_WORDS`.
7. Avoid adding redundant or meaningless prefixes and suffixes to identifiers.<br/>Example: `CREATE TABLE emp_table`.
8. Always use one spoken language (e.g. English, German, French) for all objects in your application.
9. Always use the same names for elements with the same meaning.

## Naming Conventions for PL/SQL

In general, ORACLE is not case sensitive with names. A variable named personname is equal to one named PersonName, as well as to one named PERSONNAME. Some products (e.g. TMDA by Trivadis, APEX, OWB) put each name within double quotes (&quot;) so ORACLE will treat these names to be case sensitive. Using case sensitive variable names force developers to use double quotes for each reference to the variable. Our recommendation is to write all names in lowercase and to avoid double quoted identifiers.

A widely used convention is to follow a `{prefix}variablecontent{suffix}` pattern.

The following table shows a possible set of naming conventions. 

Identifier                   | Prefix | Suffix  | Example
---------------------------- | ------ | ------- | --------
Global Variable              | `g_`   |         | `g_version`
Local Variable               | `l_`   |         | `l_version`
Constants *                  | `k_`   |         | `k_employee_permanent`
Record                       | `r_`   |         | `r_employee`
Array / Table                | `t_`   |         | `t_employee`
Object                       | `o_`   |         | `o_employee`
Cursor Parameter             | `p_`   |         | `p_empno`
In Parameter                 | `in_`  |         | `in_empno`
Out Parameter                | `out_` |         | `out_ename`
In/Out Parameter             | `io_`  |         | `io_employee`
Record Type Definitions      | `r_`   | `_type` | `r_employee_type`
Array/Table Type Definitions | `t_`   | `_type` | `t_employee_type`
Exception                    | `e_`   |         | `e_employee_exists`
Subtypes                     |        | `_type` | `big_string_type`
Cursor                       |        | `_cur`  | `employee_cur`

\* Why k_ instead of c_ for constants? A k is hard (straight lines, hard sound when pronouced in English) while a c is soft (curved lines and soft sound when pronounced in English). C also has the possibility of being vague (some folks use c_ for cursors) and sounds changable... Also, very big companies (like Google in their coding standards) use k as a prefix for constants.

## Database Object Naming Conventions

Never enclose object names (table names, column names, etc.) in double quotes to enforce mixed case or lower case object names in the data dictionary.

Edition Based Redefinition (EBR) is one major exception to this guideline. When naming tables that will be covered by editioning views, it is preferable to name the covered table in lower case begining with an underscore (for example: `"_employee"`). The base table will be covered by an editioning view that has the name `employee`. This greatly simplifies migration from non-EBR systems to EBR systems since all existing code already references data stored in `employee`. "Embracing the abomination of forced lower case names" highlights the fact that these objects shouldn't be directly referenced (execpt, obviously, by forward and reverse cross edition triggers during edition migration, and simple auditing/surrogate key triggers, if they are used). Since developers and users should only be referencing data through editioning views (which to them are effectively the tables of the applications) they won't be tempted to use the base table. In addition, when using tools to look at the list of tables, all editioning view covered tables will be aligned together and thus clearly delinated from non-covered tables.

### Collection Type

A collection type should include the name of the collected objects in their name. Furthermore, they should have the suffix `_ct` to identify it as a collection.

Optionally prefixed by a project abbreviation.

Examples:

* `employee_ct`
* `order_ct`

### Column

Singular name of what is stored in the column (unless the column data type is a collection, in this case you use plural names)

Add a useful comment to the database dictionary for every column.

### DML / Instead of Trigger

Choose a naming convention that includes:

either

* the name of the object the trigger is added to,
* the activity done by the trigger,
* the suffix `_trg`

or

* the name of the object the trigger is added to,
* any of the triggering events:
    * `_br_iud` for Before Row on Insert, Update and Delete
    * `_io_id` for Instead of Insert and Delete

Examples:

* `employee_br_iud`
* `order_audit_trg`
* `order_journal_trg`

### Foreign Key Constraint

Table name followed by referenced table name followed by a `_fk` and an optional number suffix. If working on a pre-12.2 database, then you will probably end up being forced into abbreviations due to short object name lengths in older databases.

Examples:

* `employee_department_fk`
* `sct_icmd_ic_fk1` --Pre 12.2 database

### Function

Name is built from a verb followed by a noun in general. Nevertheless, it is not sensible to call a function `get_...` as a function always gets something.

The name of the function should answer the question “What is the outcome of the function?”

Optionally prefixed by a project abbreviation.

Example: `employee_by_id`

If more than one function provides the same outcome, you have to be more specific with the name.

### Index

Indexes serving a constraint (primary, unique or foreign key) are named accordingly. 

Other indexes should have the name of the table and columns (or their purpose) in their name and should also have `_idx` as a suffix.

### Object Type

The name of an object type is built by its content (singular) followed by a `_ot` suffix.

Optionally prefixed by a project abbreviation.

Example: `employee_ot`

### Package

Name is built from the content that is contained within the package.

Optionally prefixed by a project abbreviation.

Examples:

* `employee_api` - API for the employee table
* `logger` - Utilities including logging support
* `constants` - Constants for use across a project
* `types` - Types for use across a project

### Primary Key Constraint

Table name or table abbreviation followed by the suffix `_pk`.

Examples:

* `employee_pk`
* `department_pk`
* `contract_pk`

### Procedure

Name is built from a verb followed by a noun. The name of the procedure should answer the question “What is done?” 

Procedures and functions are often named with underscores between words because some editors write all letters in uppercase in the object tree, so it is difficult to read them.

Optionally prefixed by a project abbreviation.

Examples:

* `calculate_salary`
* `set_hiredate`
* `check_order_state`

### Sequence
Version: Pre 12 only, 12 and later use identity columns, or potentially even better, use a default of `to_number(sys_guid(), 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX')`.

Name is built from the table name the sequence serves as primary key generator and the suffix `_seq` or the purpose of the sequence followed by a `_seq`.

Optionally prefixed by a project abbreviation.

Examples:

* `employee_seq`
* `order_number_seq`

### Synonym

Synonyms should share the name with the object referenced in another schema.

### System Trigger

Name of the event the trigger is based on.

* Activity done by the trigger
* Suffix `_trg`

Examples:

* `ddl_audit_trg`
* `logon_trg`

### Table

Singular name of what is contained in the table.

Add a comment to the database dictionary for every table and every column in the table.

Optionally prefixed by a project abbreviation.

Examples:

* `employee`
* `department`
* `sct_contract`
* `sct_contract_line`
* `sct_incentive_module`

Reason: Singular names have the following advantages over plural names:
1. In general, tables represent entities. Entities are singular. This encourages the art of Entity-Relationship modeling.
2. If all table names are singular, then you don't have to know if a table has a single row or multiple rows before you use it.
3. Plural names can be vastly different from singular names. What is the plural of news? lotus? knife? cactus? nucleus? There are so many words that are difficult and nonstandard to pluralize that it can add significant work to a project to 'figure out the plurals'.
4. For non-native speakers of whatever language is being used for table names, point number 3 is magnified significantly.
5. Plurals add extra unnecessary length to table names.
6. By far the biggest reason: There is no value in going through all the work to plural a table name. SQL statements often deal with a single row from a table with multiple rows, so you can't make the argument that `employees` is better than `employee` 'because the SQL will read better'.

Example (bad):
```
well_bores
well_bore_completions
well_bore_completion_components
well_bore_studies
well_bore_study_results
wells
```
Example (good):
```
well
well_bore
well_bore_completion
well_bore_completion_component
well_bore_study
well_bore_study_result
```
### Surrogate Key Columns

Surrogate primary key columns should be the table name with an underscore and id appended. For example: `employee_id`

Reason: Naming the surrogate primary key column the same name that it would have (at least 99% of the time) when used as a foreign key allows the use of the `using` clause in SQL which greatly increases readability and maintainability of SQL code. When each table has a surrogate primary key column named `id`, then `select` clauses that select multiple id columns will need aliases (more code, harder to read and maintain). Additionaly, the `id` surrogate key column means that every join will be forced into the `on` syntax which is more error-prone and harder to read than the `using` clause.

Example (bad):
```
select e.id as employee_id
      ,d.id as department_id
      ,e.last_name
      ,d.name
  from employee e
  join department d on (e.department_id = d.id);
```

Example (good):
```
select e.employee_id
      ,department_id
      ,e.last_name
      ,d.name
  from employee e
  join department d using (department_id);
```    

### Temporary Table (Global Temporary Table)

Naming as described for tables.

Ideally suffixed by `_gtt`

Optionally prefixed by a project abbreviation.

Examples:

* `employee_gtt`
* `contract_gtt`

### Unique Key Constraint

Table name followed by the role of the unique key constraint, a `_uk` and an optional number suffix, if necessary.

Examples:

* `employee_name_uk`
* `department_deptno_uk`
* `sct_contract_uk`

### View

Singular name of what is contained in the view.

Ideally, suffixed by an indicator identifying the object as a view like `_v` or `_vw` (mostly used, when a 1:1 view layer lies above the table layer, but *not* used for editioning views)

Add a comment to the database dictionary for every view and every column.

Optionally prefixed by a project abbreviation.

Examples:

* `active_order` -- A view that selects only active orders from the order table
* `order_v` -- A view to the order table
* `order` -- An editioning view that covers the `"_order"` base table
