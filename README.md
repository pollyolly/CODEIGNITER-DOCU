# CodeIgniter-Docu
```
Code igniter 
1. copy code igniter - htdocs
	https://github.com/CodeIgniter4/framework/releases/tag/v4.4.2
2. access http://localhost/login_ci/public/
3. install or enable libraries (xampp config--php.ini)
	intl
	mbstring
	json
4.Edit Database C:\xampp\htdocs\login_ci\app\Config\Database.php
```
```php
public array $default = [
        'DSN'          => '',
        'hostname'     => 'localhost',
        'username'     => 'root',
        'password'     => '',
        'database'     => 'login_ci',
        'DBDriver'     => 'MySQLi',
        'DBPrefix'     => '',
        'pConnect'     => false,
        'DBDebug'      => true,
        'charset'      => 'utf8',
        'DBCollat'     => 'utf8_general_ci',
        'swapPre'      => '',
        'encrypt'      => false,
        'compress'     => false,
        'strictOn'     => false,
        'failover'     => [],
        'port'         => 3306,
        'numberNative' => false,
    ];
```
login_ci
```sql
CREATE TABLE `user_role_tbl` (
  `id` int(11) NOT NULL,
  `user_type` varchar(50) NOT NULL
)

CREATE TABLE `user_tbl` (
  `id` int(11) NOT NULL,
  `first_name` varchar(50) NOT NULL,
  `middle_name` varchar(50) DEFAULT NULL,
  `last_name` varchar(50) NOT NULL,
  `email` varchar(100) NOT NULL,
  `user_name` varchar(50) DEFAULT NULL,
  `user_password` varchar(255) NOT NULL,
  `user_role_id` int(11) DEFAULT NULL
)
```
