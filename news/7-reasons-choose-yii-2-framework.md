> [原文地址：www.sitepoint.com/7-reasons-choose-yii-2-framework](http://www.sitepoint.com/7-reasons-choose-yii-2-framework/)  
原作者：Matthew Beaumont（马修·博蒙特）主翻译：@qiansen1386 (东方孤思子) 校对：尚未校对 发布自：2014年10月13

> 特别提醒：文中出现的全部链接均为原文链接，并未提供中文链接。如有需要可以自己找找大多数都有全世界的华人志愿者提供的汉化版本。如有特别需要，也可以给我们[提交翻译请求，不过最好是本身带 Markdown 格式的文件](https://github.com/yii2-chinesization/yii2-zh-cn/issues)。

选择易兔的 7 大理由
================

去年年底，SitePoint 发布了一篇[文章](http://www.sitepoint.com/best-php-frameworks-2014/)盘点了顶尖 PHP 
框架。并列第四的框架就是 Yii（读作**易**）框架。当时最新的版本是 1.1.14。而现在，Yii 2.0
也发布了，所以你也可以开始在生产环境中使用它了。

Late last year, SitePoint published an
[article](http://www.sitepoint.com/best-php-frameworks-2014/)
highlighting the top PHP frameworks. Tied for the number four spot was
the Yii (pronounced ***Yee***) Framework. At that time the latest
version of the framework available was 1.1.14. Recently, Yii 2.0 was
made available, so you can begin to use it in production.

最近，我们在它还在 RC 阶段的时候，发布[文章](http://www.sitepoint.com/expect-yii-2-0/)谈到了它。它目前已经到达了稳定发布的状态，并且我们觉得现在到时候再来谈谈这个话题，聊一聊它与其他类似产品相比有哪些独到之处。

While we did [cover it
recently](http://www.sitepoint.com/expect-yii-2-0/) when it was still in
RC status, it just reached full release status, and we feel like it’s
time to revisit the topic with some reasons for choosing it over
alternatives.

1. 易于安装 {#1-easy-to-install}
-------------------------------

对于很多 Web 开发者而言，时间就是金钱（我的朋友），况且没有人愿意为复杂的安装与配置过程，而浪费他们宝贵的人生。

For web developers, time is money, and no one wants to spend their
precious time on a complicated installation and configuration process.

安装过程是通过 [Composer](http://getcomposer.org) 进行的。如果你想看安装过程的详细描述，Sitepoint 
最近刚刚发表了一篇很棒的[文章](http://www.sitepoint.com/expect-yii-2-0/)。我倾向于使用基本应用模版，即使我的网站有分离的前台和后台组件。事实上，我选择用[模块(Module)](http://www.yiiframework.com/doc-2.0/guide-structure-modules.html)实现我网站的后台部分。（对 Yii 的模块的最佳描述应该是：放置在主应用内部的迷你应用）。

Installation is handled using [Composer](http://getcomposer.org). If you
want a description of the installation process, Sitepoint recently
published a great article
[here](http://www.sitepoint.com/expect-yii-2-0/). I tend to favor using
the basic application template, even when my site has a separate front-
and backend component. Instead, I opt to use a
[Module](http://www.yiiframework.com/doc-2.0/guide-structure-modules.html)
for the backend portion of my sites. (Yii Modules are best described as
mini-applications which reside inside your main application).

**注意**：下面的例子中的很多目录是引用自其简单模版的目录结构。

*Note*: Many of the directory references in later examples use the
directory structure from the simple template.

2. 应用最新科技 {#2-utilizes-modern-technologies}
-------------------------------

Yii 是完全的 OOP（面向对象编程）框架，并且利用了一些 PHP 更为先进的功能，比如
[延迟静态绑定（late static binding）](http://php.net/manual/en/language.oop5.late-static-bindings.php)
，[SPL（Standard PHP Library 标准PHP类库）类和接口](http://php.net/manual/en/book.spl.php)，以及
[匿名函数](http://php.net/manual/en/functions.anonymous.php)等。

Yii is a pure OOP framework, and takes advantage of some of PHP’s more
advanced features, including [late static
binding](http://php.net/manual/en/language.oop5.late-static-bindings.php),
[SPL classes and interfaces](http://php.net/manual/en/book.spl.php), and
[anonymous functions](http://php.net/manual/en/functions.anonymous.php).

所有的类都包含命名空间，这使得你可以享受他们所提供的 PSR-4 标准自动加载器。这意味着要包含 Yii 的
[HTML](http://www.yiiframework.com/doc-2.0/yii-helpers-basehtml.html)
助手类，就只需这样一句话：

All classes are namespaced, which allows you to take advantage of their
PSR-4 compliant autoloader. That means that including Yii’s
[HTML](http://www.yiiframework.com/doc-2.0/yii-helpers-basehtml.html)
helper class is as simple as:

```php
use yii\helpers\Html;
```

Yii 还允许你定义**别名**用以简化命名空间。在上面的例子中，`use` 语句会加载一个默认放置在 `/vendor/yiisoft/yii2/helpers` 
目录中的一个类的定义。这个别名是在 [BaseYii](http://www.yiiframework.com/doc-2.0/yii-baseyii.html)
类的第 79 行定义的：

Yii also allows you to define aliases to help simplify your namespaces.
In the above example, that `use` statement will load a class definition
which is located by default in the directory
`/vendor/yiisoft/yii2/helpers`. This alias is defined in the
[BaseYii](http://www.yiiframework.com/doc-2.0/yii-baseyii.html) class on
line 79:

```
public static $aliases = ['@yii' => __DIR__];
```

框架本身与其扩展一样均可采用 Composer 安装。甚至连发布扩展的过程，都跟创建你自己的 `composer.json` 一样简单，把你的代码发布到 
GitHub，然后把你的扩展注册到 Packagist。

The framework itself is installed using Composer, as are its extensions.
Even the process of publishing extensions is as easy as creating your
own `composer.json`, hosting your code at Github, and listing your
extension on Packagist.

3. 特别易于扩展 {#3-highly-extensible}
--------------------

Yii 就像一套西装，直接看来就很棒，还同样非常容易量体裁衣，以满足你的需求。事实上，该框架的每一个组件都是可以扩展的。举个简单的例来说，假如你要给你的视图添加一个额外的 body ID。（若你想要知道为什么你会想要这么做，可以看看这篇[文章](http://css-tricks.com/id-your-body-for-greater-css-control-and-specificity/)）。

Yii is like a suit that looks great off of the rack, but is also very
easy to tailor to fit your needs. Virtually every component of the
framework is extensible. A simple example is the addition of a unique
body ID to your views. (In case you’re interested in knowing why you
might want to do this, take a look at this
[article](http://css-tricks.com/id-your-body-for-greater-css-control-and-specificity/)).

首先，我会在我的 `app\components` 目录里创建一个名为 `View.php` 的文件，并写入一下内容：

First, I would create a file in my `app\components` directory with the
name `View.php`, and add the following:

```php
namespace app\components;
 
class View extends yii\web\View {
 
    public $bodyId;
 
    /* Yii 允许你通过给方法名加 'get' 前缀使其变为魔术 getter 方法*/
 
    public function getBodyIdAttribute() {
        return ($this->bodyId != '') ? 'id="' . $this->bodyId . '"' : '';
    }
 
}
```

之后，在我的主布局文件（`app\views\layouts\main.php`）里，我会添加以下<body>标签到我的 HTML 代码中：

Then, in my main layout file (`app\views\layouts\main.php`), I would add
the following to the body tag of my HTML:

```php
<body <?=$this->BodyIdAttribute?>>
```

最终，我会向主配置文件中加入以下代码，让 Yii 知道使用我扩展的 `View` 类替换掉其默认类：

And finally, I would add the following to my main configuration file to
let Yii know to use my extended `View` class instead of its own default:

```php
return [
    // ...
    'components' => [
        // ...
        'view' => [
            'class' => 'app\components\View'
        ]   
    ]
];
```

4. 鼓励测试 {#4-encourages-testing}
---------------------

Yii is tightly integrated with
[Codeception](http://www.sitepoint.com/ruling-the-swarm-of-tests-with-codeception/).
Codeception is a great PHP testing framework that helps simplify the
process of creating unit, functional and acceptance tests for your
application. Because you ARE writing automated tests for all your
applications, right?

The Codeception extension makes it simple to configure your application
during testing. Simply edit the provided `/tests/_config.php` file to
configure your test application. For example:

```php
return [
    'components' => [
        'mail' => [
            'useFileTransport' => true,
        ],
        'urlManager' => [
            'showScriptName' => true,
        ],
        'db' => [
                'dsn' => 'mysql:host=localhost;dbname=mysqldb_test',
        ],
    ],
];
```

Using this configuration, the following would happen:

1.  Any emails sent during your functional and acceptance tests would be
    written to a file instead of being sent.
2.  The URLs in your tests would take on the format
    `index.php/controller/action` rather than `/controller/action`
3.  Your tests would use your test database, rather than your production
    database.

A special module for the Yii Framework also exists within Codeception.
It adds several methods to the `TestGuy` class, which help you work with
[Active
Record](http://www.yiiframework.com/doc-2.0/guide-db-active-record.html)
(Yii’s ORM) during functional tests. For instance, if you wanted to see
if your registration form successfully created a new `User` with the
username “testuser”, you could do the following:

```php
$I->amOnPage('register');
$I->fillField('username', 'testuser');
$I->fillField('password', 'qwerty');
$I->click('Register');
$I->seeRecord('app\models\User', array('name' => 'testuser'));
```

5. 简化安全措施 {#5-simplifies-security}
----------------------

Security is a crucial part of any web application, and fortunately Yii
has some great features to help ease your mind.

Yii comes with a
[Security](http://www.yiiframework.com/doc-2.0/yii-base-security.html)
application component that exposes several methods to help assist in
creating a more secure application. Some of the more useful methods are:

-   [generatePasswordHash](http://www.yiiframework.com/doc-2.0/yii-base-security.html#generatePasswordHash%28%29-detail):
    Generates a secure hash from a password and a random salt. This
    method makes a random salt for you, and then creates a hash from the
    supplied string using PHP’s
    [crypt](http://php.net/manual/en/function.crypt.php "PHP Crypt Function")
    function.
-   [validatePassword](http://www.yiiframework.com/doc-2.0/yii-base-security.html#validatePassword%28%29-detail):
    This is the companion function to `generatePasswordHash`, and allows
    you to check whether the user supplied password matches your stored
    hash.
-   [generateRandomKey](http://www.yiiframework.com/doc-2.0/yii-base-security.html#generateRandomKey%28%29-detail):
    Allows you to create a random string of any length

Yii automatically checks for a valid CSRF token on all unsafe HTTP
request methods (PUT, POST, DELETE), and will generate and output a
token when you use the
[ActiveForm::begin()](http://www.yiiframework.com/doc-2.0/yii-base-widget.html#begin%28%29-detail)
method to create your opening form tag. This feature can be disabled by
editing your main configuration file to include the following:

```php
return [
    'components' => [
        'request' => [
            'enableCsrfValidation' => false,
        ]
];
```

In order to protect against XSS, Yii provides another helper class
called
[HtmlPurifier](http://www.yiiframework.com/doc-2.0/yii-helpers-basehtmlpurifier.html).
This class has a single static method named
[process](http://www.yiiframework.com/doc-2.0/yii-helpers-basehtmlpurifier.html#process%28%29-detail),
and will filter your output using the [popular filter
library](http://htmlpurifier.org/) of the same name.

Yii also includes ready-to-use classes for user authentication and
authorization. Authorization is broken into two types: ACF (Access
Control Filters) and RBAC (Role-Based Access Control).

The simpler of the two is ACF, and is implemented by adding the
following to the
[behaviors](http://www.yiiframework.com/doc-2.0/yii-base-component.html#behaviors%28%29-detail)
method of your controller:

```php
use yii\filters\AccessControl;
 
class DefaultController extends Controller {
    // ...
    public function behaviors() {
        return [
            // ...
            'class' => AccessControl::className(),
            'only' => ['create', 'login', 'view'],
                'rules' => [
                [
                    'allow' => true,
                    'actions' => ['login', 'view'],
                    'roles' => ['?']
                ],
                [
                    'allow' => true,
                    'actions' => ['create'],
                    'roles' => ['@']
                ]
            ]
        ];
    }
    // ...
}
```



The preceding code tells `DefaultController`to allow guest users to
access the `login` and `view` actions, but not the `create` action. (`?`
is an alias for anonymous users, and `@` refers to authenticated users).

RBAC is a more powerful method of specifying which users can perform
specific actions throughout your application. It involves creating roles
for your users, defining permissions for your app, and then enabling
those permissions for their intended roles. You could use this method if
you wanted to create a `Moderator` role, and allow all users assigned to
this role to approve articles.

You can also define rules using RBAC, which allow you, under specific
conditions, to grant access to certain aspects of your application. For
instance, you could create a rule that allows users to edit their own
articles, but not those created by others.

6. 缩短开发时长 {#6-shorten-development-time}
---------------------------

Most projects involve a certain amount of repetitive tasks that no one
wants to waste time with. Yii gives us a few tools to help you spend
less time on those tasks, and more time customizing your application to
suit your clients’ needs.

One of the most powerful of these tools is called “Gii”. Gii is a
web-based code scaffolding tool, which allows you to quickly create code
templates for:

-   Models
-   Controllers
-   Forms
-   Modules
-   Extensions
-   CRUD controller actions and views

Gii 有高度可定制性。你可以配置它为只在特定环境中加载。只需像这样简单修改下你的 web 配置文件：

Gii is highly configurable. You can set it to only load in certain
environments. Simply edit your web configuration file as follows:

```php
if (YII_ENV_DEV) {
    // ...
    $config['modules']['gii'] = [
        'class' => 'yii\gii\Module',
        'allowedIPs' => ['127.0.0.1', '::1']
    ]
}
```

This ensures that Gii will only load when the Yii environment variable
is set to *development*, and that it will only load when accessed via
localhost.

Now let’s take a look at the model generator:

![Gii Model
Generator](http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2014/10/1413153698gii-model-generator.jpg)

The table name uses a typeahead widget to try to guess which table your
model is associated with, and all fields have a rollover tooltip to
remind you how to fill them out. You can preview code before you ask Gii
to generate it, and all the code templates are completely customizable.

There are also several command-line tools available to help create code
templates for database migrations, message translations (I18N) and
database fixtures for your automated tests. For instance, you can create
a new [database
migration](http://www.yiiframework.com/doc-2.0/guide-db-migrations.html)
file with this command:

```php
yii migrate/create create_user_table
```

This will create a new migration template in {appdir}/migrations that
looks something like this:

```php
<?php
 
    use yii\db\Schema;
 
    class m140924_153425_create_user_table extends \yii\db\Migration
    {
        public function up()
        {
 
        }
 
        public function down()
        {
            echo "m140924_153425_create_user_table cannot be reverted.\n";
 
            return false;
        }
}
```

So let’s say I wanted to add a few columns to this table. I would simply
add the following to the `up` method:

```php
public function up()
{
    $this->createTable('user', [
        'id' => Schema::TYPE_PK,
        'username' => Schema::TYPE_STRING . ' NOT NULL',
        'password_hash' => Schema:: TYPE_STRING . ' NOT NULL'
    ], null);
}
```

And then to make sure I can reverse the migration, I would edit the
`down` method:

```php
public function down()
{
    $this->dropTable('user');
}
```

Creating the table would simply involve running a command on the command
line:

```php
./yii migrate
```

and to remove the table:

```php
./yii migrate/down
```

7. 便于性能调优 {#7-easy-to-tune-for-better-performance}
--------------------------------------

Everybody knows that a slow website creates disgruntled users, so Yii
provides you with several tools to help you squeeze more speed out of
your application.

All Yii’s cache components extend from
[yii/caching/Cache](http://www.yiiframework.com/doc-2.0/yii-caching-cache.html),
which allows you to choose whichever caching system you want while using
a common API. You can even register multiple cache components
simultaneously. Yii currently supports database and file system caching,
as well as APC, Memcache, Redis, WinCache, XCache and Zend Data Cache.

By default, if you’re using Active Record then Yii runs an extra query
to determine the schema of the table(s) involved in generating your
model. You can set the application to cache these schema by editing your
main configuration file as follows:

```php
return [
    // ...
    'components' => [
        // ...
        'db' => [
            // ...
            'enableSchemaCache' => true,
            'schemaCacheDuration' => 3600,
            'schemaCache' => 'cache',
        ],
        'cache' => [
            'class' => 'yii\caching\FileCache',
        ],
    ],
];
```

Finally, Yii has a command line tool to facilitate the minification of
frontend assets. Simply run the following command to generate a
configuration template:

```php
./yii asset/template config.php
```

Then edit the configuration to specify which tools you want to you
perform your minification (e.g. Closure Compiler, YUI Compressor, or
UglifyJS). The generated configuration template will look like this:

```php
<?php
    return [
        'jsCompressor' => 'java -jar compiler.jar --js {from} --js_output_file {to}',
        'cssCompressor' => 'java -jar yuicompressor.jar --type css {from} -o {to}',
        'bundles' => [
            // 'yii\web\YiiAsset',
            // 'yii\web\JqueryAsset',
        ],
        'targets' => [
            'app\config\AllAsset' => [
                'basePath' => 'path/to/web',
                'baseUrl' => '',
                'js' => 'js/all-{hash}.js',
                'css' => 'css/all-{hash}.css',
            ],
        ],
        'assetManager' => [
            'basePath' => __DIR__,
            'baseUrl' => '',
        ],
    ];
```

Next, run this console command in order to perform the compression.

```php
yii asset config.php /app/assets_compressed.php
```

And finally, edit your web application configuration file to use the
compressed assets.

```php
'components' => [
    // ...
    'assetManager' => [
        'bundles' => require '/app/assets_compressed.php'
    ]
]
```

**注意：** 你将必须手动下载并安装这些外部工具。  
You will have to download and install these external tools manually.

Conclusion
----------

和其他优秀框架一般，Yii 可以帮助你快速创建现在互联网应用程序，并且确保他们运行良好。他会通过把脏活累活都替你干了的方式极大地减轻你的负担，从而促使你创造出安全且易于测试的网站。你可以轻松地直接使用它所提供的大量功能，或者你也可以修改他们中的任何一个来配合你的需求。我真的建议你为你的下一个 Web 项目而好好了解一下这个框架。

Like any good framework, Yii helps you create modern web applications
quickly, and make sure they perform well. It pushes you to create secure
and testable sites by doing a lot of the heavy lifting for you. You can
easily use most of its features exactly as they are provided, or you can
modify each one to suit your needs. I really encourage you to check it
out for your next web project!

你试过 Yii 2 了咩？会试试咩？
要告诉我们哦！

Have you tried Yii 2? Will you? Let us know!


> **作者简介:**
马修大叔作为 PHP 开发者，在过去的 8 年里一直忠贞地享受着与 LAMP 技术栈的美妙恋（jian）情。虽然他们依旧爱着彼此，他最近也在摸♂索着他的小姨子—— MEAN 架构。在不编程的时候，他会跟着交响乐团在卡内基礼堂、林肯中心，无线电城音乐大厅或其他地方专业地演奏打击乐。