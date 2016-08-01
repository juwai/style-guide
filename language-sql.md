## MySQL Style Guideline

### Minimum Requirements

- MySQL keywords in uppercase.

    Example:

    VALID
    ```SQL
        UPDATE `consumer` SET `email` = 'john.doe@juwai.com';
    ```
    NOT VALID:
    ```SQL
        update `consumer` set `email` = 'john.doe@juwai.com';
    ```

- Database table names **MUST BE** singular and **SHOULD** be short and meaningful.

    Example:
    `user`, `subscription`
    
    For linking tables:
    
    Example: 
    `user_subscription`, `user_property`

    We use the form `<left_table><underscore><right_table>` (example: user_subscription) when naming relationship tables to make it easy to show which tables are being linked. We don’t use the plural form of the tables when naming their corresponding relationship tables since, regardless of relationship type (many-to-many or one-to-many), every record still contains only one foreign key to the left and right tables respectively.

- Column names **MUST** be lowercase and **MUST** be singular.

    Example:
    ```SQL
        `username`, `is_active`, `created_by`, `created_at`
    ```

- Column names **MUST NOT** be MySQL reserved words: order, status, etc. (https://dev.mysql.com/doc/refman/5.7/en/keywords.html)

- Foreign keys **MUST** be prefixed with the name of their parent’s table.

    Example:
    `country_id`, `property_id`, `inventory_id`
    
- Table and column names **MUST** be enclosed with <code>`</code> (backtick operator)

    Example:

    VALID:
    ```SQL
    SELECT `id`, `name`, `name_sc` FROM `area` WHERE `country_id` = 1 AND `region_id` = 5;
    ```
    NOT VALID:
    ```SQL
    SELECT id, name, name_sc FROM area WHERE country_id = 1 AND region_id = 5;
    ```

### Database table naming convention

Prefix application name to table name. E.g.: `app1_users`, `app2_log_meta`.

If the table is for multiple applications (normally this should be avoided), it's ok to leave it without the application name prefix.
