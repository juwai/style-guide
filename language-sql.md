## MySQL Style Guideline

### Minimum Requirements

- MySQL keywords in uppercase
    E.g.: 
    ```
    UPDATE `consumer` SET `PASSWORD` = MD5(`PASSWORD`);
    ```

- Database table names must be plural. 
    E.g.: 
    `users`, `subscriptions`
    
    for Linking tables :
    `users_subscriptions`

- Column names in lowercase and must be singular. Avoid using MySQL reserved words such as order, status, etc.
    E.g.: `username`, `is_active`, `created_by`, `created_at`
    
    - Foreign keys must be prefix with parent table.
    E.g.:
    `country_id`
    
- Table and column names must be enclosed with ` (backtick operator)
    E.g.:
    ```
    SELECT `id`, `name`, `name_sc` FROM `area` WHERE `country_id` = 1 AND `region_id` = 5;
    ```

### Database table naming convention

Prefix application name to table name. E.g.: `app1_users`, `app2_log_meta`.

If the table is for multiple applications (normally this should be avoided), it's ok to leave it without the application name prefix.
