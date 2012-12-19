Wings
---------------
`Wings` is a very lightweight easy-to-use non-orm ORM library for PHP to make your database abstraction faster and simple with just one shot.

Requirements
---------------
* **PDO** Extension for PHP
* At least one **PDO** driver
* PHP **5.3** or higher

Code
---------------
Using `Wings` is a very easy and simple task. You just need to **require/include** the Wings files, configure the DSN, make the authentication and fly!

### Simple usage:

```php
use Wings\ORM;

// If you're NOT using an Autoload script, you must to require/include the Exceptions Cases and the ORM class
// require 'path/to/Wings/Exceptions/ExecutionException.php';
// require 'path/to/Wings/Exceptions/FetchException.php';
// require 'path/to/Wings/Exceptions/FlyingException.php';
// require 'path/to/Wings/ORM.php';

// We need to configure the Wings to make it "flyable" :)
ORM::configure('mysql:host=localhost;dbname=wings');
ORM::authenticate('username', 'password');

// Let's fly! :)
$wings = ORM::fly('table_name');
$wings->select(array('field1', 'field2'), '`id` = 1', 1);
// The above example will return the result for this query:
// SELECT `field1`, `field2` FROM `table_name` WHERE (`id` = '1') LIMIT 0,1

// How many rows has been selected?
echo "Selected rows: " . (int) $wings->count() . "\n<br />\n";

// Executed queries
echo "Executed queries so far: " . (int) $wings->queries() . "\n";

// Prints the selected data
echo "<pre>";
print_r($wings->fetch());
echo "</pre>";

// Close the connection
$wings->close();
```

### The Class Constants
There's a few constants in this class, which are:
* `VERSION`         => Current library version
* `VERSION_ID`      => Current version ID (like: `05000`)

* `FETCH_ASSOC`     => Used on the fetch() method. Fetches the data as an associative array.
* `FETCH_ARRAY`     => Used on the fetch() method. Fetches the data as an indexed array (0, 1, ...).
* `FETCH_BOTH`      => Used on the fetch() method. Fetches the data using the two methods above.
* `FETCH_OBJECT`    => Used on the fetch() method. Fetches the data into a stdClass object.
* `FETCH_LAZY`      => Used on the fetch() method. Fetches the data into a PDORow object.

If you don't know any of these FETCH constants, read the [PHP Documentation](http://php.net/manual/en/pdo.constants.php#pdo.constants.fetch-lazy).

License
---------------
Wings is licensed under the [MIT License](http://www.opensource.org/licenses/mit-license.php "MIT License"), so you can do whatever you want, since you maintain a link to this repository and leave a mention of my name as the original author of the Wings library.

License message
---------------
Permission is hereby granted, free of charge, to any person obtaining a > copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.