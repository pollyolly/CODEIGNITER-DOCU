# CodeIgniter-4-Docu
```
Code igniter 
1. copy code igniter - htdocs
	https://github.com/CodeIgniter4/framework/releases/tag/v4.4.2
- change the base URL -> app -> config -> App
	public string $baseURL = 'http://localhost/ProjectCAP_ci4';
2. access http://localhost/login_ci/public/
3. install or enable libraries (xampp config--php.ini)
	intl
	mbstring
	json
- check Running Development Server, Open Command Promt -> "C:\xampp\htdocs\ProjectCAP_ci4" -> "php spark serve"
	
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
5. login_ci/app->Config->App.php
```
public string $baseURL = "http://localhost/login_ci/";
```
6. Routing C:\xampp\htdocs\login_ci\app\Config\Routes
```php
<?php

use CodeIgniter\Router\RouteCollection;

/**
LoginForm = URL name (http://localhost/login_ci/public/LoginForm) 
LoginController = controller (C:\xampp\htdocs\login_ci\app\Controllers\LoginController)
Login = public function Login()
**/
$routes->get('LoginForm', 'LoginController::Login');
```
7. Model C:\xampp\htdocs\login_ci\app\Models\LoginModel
```php
<?php

namespace App\Models;

use CodeIgniter\Model;

class LoginModel extends Model
{
    protected $table = 'user_role_tbl';
    public function checkUserRole ($slug = false){
        // if ($slug == false ){
            return $this->findAll();
        // }
        // return $this->where(['user_type' => 'Patient'])->first();
    }
}
```
8. Controller C:\xampp\htdocs\login_ci\app\Controllers\LoginController
```php
<?php

namespace App\Controllers;

use App\Models\LoginModel;

class LoginController extends BaseController
{
    public function Login()
    {
        $model = model(LoginModel::class);
        $data['role'] = $model->checkUserRole();
        // $data['role'] = 'Patient';
        return view('LoginView', $data);
    }
}
```
9. View C:\xampp\htdocs\login_ci\app\Views\LoginView
```html
<!DOCTYPE html>
<html lang="en">
<head>
<body>
    <p><?php var_dump($role) ?></p>
    <h1>Hello</h1>
</body>
</html>
```
10. Base url config
```vim
login_ci->app
login_ci->config->App
```
```php
public string $baseURL = 'http://localhost/login_ci/';
```
11. Resources
```vim
login_ci->app
login_ci->assets->css
	  assets->js
	  assets->images
```
```html
<link href="<?php base_url('assets/images/background.png') ?>" type="text/css" rel="stylesheet" />
<a href="<?php site_url('Controller/Function') ?>">Click Me</a>
```
