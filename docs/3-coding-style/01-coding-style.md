# General Style

## Formatting

### Rules

Rule | Description
:--: | -----------
1    | All code is written in lowercase.
2    | 3 space indention.
3    | One command per line.
4    | Keywords `loop`, `else`, `elseif`, `end if`, `when` on a new line.
5    | Commas in front of separated elements.
6    | Call parameters aligned, operators aligned, values aligned.
7    | SQL keywords are right aligned within a SQL command.
8    | Within a program unit only line comments `--` are used.
9    | Brackets are used when needed or when helpful to clarify a construct. 

### Example

```sql
procedure set_salary(in_employee_id IN employee.employee_id%type)
is
   cursor c_employee(p_employee_id IN employee.employee_id%type) is 
      select last_name
           , first_name
           , salary
        from employee
       where employee_id = p_employee_id
    order by last_name
           , first_name;

   r_employee     c_employee%rowtype;
   l_new_salary   employee.salary%type;
begin
   open  c_employee(p_employee_id => in_employee_id);
   fetch c_employee into r_employee;
   close c_employee;

   new_salary (in_employee_id => in_employee_id
             , out_salary     => l_new_salary);

   -- Check whether salary has changed
   if r_employee.salary <> l_new_salary then
      update employee
         set salary = l_new_salary
       where employee_id = in_employee_id;
   end if;
end set_salary;
```

### Package Version Function

When version control is not available, each package could have a `package_version` function that returns a varchar2. 

Note: If you are using a version control system (like Git for example) to track all code changes and you feel that you'll be able to track everything below using your version control system, and everyone that might need to figure out 'what is happening', from all developers to purely operational DBAs, knows how to use the version control system to figure out the below, then you might consider the below redundant and '_extra work_'. If so, feel free not implement this function.

#### Package Spec
```sql
--This function returns the version number of the package using the following rules:
-- 1. If there is a major change that impacts multiple packages, increment the first digit, e.g. 03.05.09 -> 04.00.00
-- 2. If there is a change to the package spec, increment the first dot, e.g. 03.02.05 -> 03.03.00
-- 3. If there is a minor change, only to the package body, increment the last dot e.g. 03.02.05 -> 03.02.06
-- 4. If the function returns a value ending in WIP, then the package is actively being worked on by a developer.
function package_version return varchar2;
```

#### Package Body

```sql
-- Increment the version number based upon the following rules
-- 1. If there is a major change that impacts multiple packages, increment the first digit, e.g. 03.05.09 -> 04.00.00
-- 2. If there is a change to the package spec, increment the first dot, e.g. 03.02.05 -> 03.03.00
-- 3. If there is a minor change, only to the package body, increment the last dot e.g. 03.02.05 -> 03.02.06
-- 4. If a developer begins work on a package, increment the comment version and include the words 'IN PROGRESS' in 
--    the new version line. Increment the return value and add WIP to the return value. Example:  return '01.00.01 WIP'  
--    And then IMMEDIATELY push/commit & compile the package.
--   As you are working on the package and make updates to lines, use the version number at the end of the line to indicate when 
--  the line was changed. Example: l_person := 'Bob';  -- 01.00.01 Bob is the new person, was Joe.
-- 5. Once work is complete, remove 'IN PROGRESS' from the comment and remove WIP from the return value.
-- 6. If your work crosses the boundary of a sprint, having WIP in the return value will indicate that the package should not be promoted.
function package_version return varchar2
is
begin
  -- 01.00.00 YYYY-MM-DD First & Last Name  Initial Version
  -- 01.00.01 YYYY-MM-DD First & Last Name  Fixed issue number 72 documented in Jira ticket 87: https://ourjiraurl.com/f?p=87
   return '01.00.01' ;
end package_version;
```

Some notes on the above: We are computer scientists, we write dates as YYYY-MM-DD, not DD-MON-RR or MON-DD-YYYY or any other way.

If you are in the middle of an update, then the function would look like this:

```sql
[snip]
  -- 01.00.00 YYYY-MM-DD First & Last Name  Initial Version
  -- 01.00.01 YYYY-MM-DD First & Last Name  Fixed issue documented in Jira ticket 87: https://ourjiraurl.com/f?p=87
  -- 01.00.02 2019-10-25 Rich Soule         IN PROGRESS Fixing issue documented in Jira ticket 90: https://ourjiraurl.com/f?p=90
   return '01.00.02 WIP' ;
end package_version;
```

