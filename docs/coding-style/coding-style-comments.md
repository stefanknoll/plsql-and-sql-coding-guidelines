## Commenting Goals

Code comments are there to help future readers of the code (there is a good chance that future reader is you... Any code that you wrote six months to a year ago might as well have been written by someone else) understand how to use the code (especially in PL/SQL package specs) and how to maintain the code (especially in PL/SQL package bodies).

## The JavaDoc Template

Use the JavaDoc style comments, as seen in the example below and read more here [JavaDoc Template](https://plsql-md-doc.readthedocs.io/en/latest/javadoc-template/) and [JavaDoc for the Oracle Database a la DBDOC](https://www.thatjeffsmith.com/archive/2012/03/javadoc-for-the-database-a-la-dbdoc-via-sql-developer/).

```sql
/**
 * Description
 *
 *
 * @example
 * 
 * @issue
 *
 * @author
 * @created
 * @param
 * @return
 */
```

## Commenting Tags

Tag      | Meaning                                                 | Example
-------- | ------------------------------------------------------- | -------
`example`| Code snippet that shows how the procedure or function can be called. |
`issue`  | Ticketing system issue or ticket that explains the code functionality | `@issue IE-234`
`param`  | Description of a parameter.                             | `@param in_string input string`
`return` | Description of the return value of a function.          | `@return result of the calculation`
`throws` | Describe errors that may be raised by the program unit. | `@throws no_data_found`


## Generated Documentation

If you used the JavaDoc syntax then you can use [plsql-md-doc](https://github.com/OraOpenSource/plsql-md-doc) to generate an easy to read document.

Alternatively, [Oracle SQL Developer](https://www.oracle.com/database/technologies/appdev/sql-developer.html) or PL/SQL Developer include documentation functionality based on a javadoc-like tagging. 


## Commenting Conventions

Inside a program unit only use the line commenting technique `--` unless you temporarly deactivate code sections for testing.

To comment the source code for later document generation, comments like `/** ... */` are used. Within these documentation comments, tags may be used to define the documentation structure.

## Code Instrumentation

Code Instrumentation refers, among other things, to an ability to monitor, measure, and diagnose errors. In short, we'll call them debug messages or log messages.

By far, the best logging framework available is <a href="https://github.com/OraOpenSource/Logger" target="_blank">Logger</a> from <a href="https://github.com/OraOpenSource/" target="_blank">OraOpenSource</a>.

Consider using logger calls **instead** of comments when the information will, explain the logic, help diagnose errors, and monitor execution flow.

For example:

```sql hl_lines="8 11"
procedure verify_valid_auth
is
  l_scope  logger_logs.scope%type := k_scope_prefix || 'verify_valid_auth';
begin
  logger.log('BEGIN', l_scope);

  if is_token_expired then
    logger.log('Time to renew the expired token, and set headers.', l_scope);
    hubspot_auth;
  else
    logger.log('We have a good token, set headers.', l_scope);
    set_rest_headers;
  end if; 

  logger.log('END', l_scope);

exception
  when OTHERS then
    logger.log_error('Unhandled Exception', l_scope);
    raise;
end verify_valid_auth;
```