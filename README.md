One-Page-PHP-Fundamentals
=========================
Comments
=========
1. // This is a one-line comment
2. #  This is another one-line comment style
3. /* This is how you
      can create a multi-line
      comment 
  */
Outputting data with echo and print
===================================
print "Hello, world";
echo "Hello, world";

The difference between print and echo is that echo can output more than one parameter, each separated by a comma whereas print not.

echo "The answer is ", 42;(valid)
print "The answer is ", 42;(invalid)

Parentheses make no difference to the behavior of print.
However, when they are used with echo, only one output parameter can be provided.

escape sequences
================================
White space characters \t, \n, \$, \”, \’ and \r are often useful.

Variable Substitution
==============================
Variable substitution provides a convenient way to embed data held in a variable directly into string literals. PHP examines, or parses , double-quoted strings and replaces variable names with the variable's value

$number = 45;
$vehicle = "bus";
$message = "This $vehicle holds $number of people”;
Echo $message;

When the name of the variable is ambiguous, braces {} can delimit the name as shown in the following example:

$memory = 256;
$message = "My computer has $memoryMbytes of RAM";( invalid)
$message = "My computer has {$memory}Mbytes of RAM";

Variables
====================
Variable names are case-sensitive in PHP.
Variables in PHP are identified by a dollar sign followed by the variable name. Variables don't need to be declared before you use them.

$var;
$var=15;

When they are used, the type is implicitly defined—or redefined—and the variable implicitly declared.

Data Types
========================
PHP has four scalar types:

boolean,
float, 
integer, 
string
And two compound types:
array 
object

PHP also supports:
null— a special type that is used when a variable doesn't have a value

Constants
=========================
It's also common to declare constants in a script.

define("PI", 3.14159);

PHP has a large number of built-in constants. The library of mathematical functions already includes a definition of M_PI to hold the constant pi:
print M_PI;

Expression, Operators 
=============================
Expression syntax in PHP is similar to C and all the basic Mathematical and C Operators are supported in PHP.
Strings are concatenated with dot (.) operator. 

Conditions and Branches
===============================
There are two branching statements in PHP:
1. if
2. switch

if Statement

if(condition)
{
   //statements
}
elseif (condition)
{
   //statements
}
else
{
    //statements
}

switch Statement

switch ($menu)

{
    case 1:

        print "You picked one";

        break;

    case 2:

        print "You picked two";

        break;

    default:

        print "You picked another option";

 }




Loops
=====================
1. while loop
2. do-while loop
3. for loop

While loop

$counter = 1;
while ($counter < 11)
{
 print $counter . " ";
 $counter++;
}
Do-while loop
$counter = 1;
do
{
 print $counter . " ";
 $counter++;

} while ($counter < 11);

for loop

for($counter=1; $counter<11; $counter++)
{
 print $counter;
 print " ";
}


Functions
===========================
Functions are called in PHP scripts. 
Two types of functions used in PHP.

1. User-Defined Functions
2. Built-in Functions

Parts of function in PHP

Function prototype
Function definition
Function call

The parameter and return types of a function aren't declared when the function is defined. PHP allows parameters of any type to be passed to the function, and as with variables, the return type is determined when a result is actually returned.
function divide($a, $b)

{

    return ($a/$b);     			       //function definition

}

$c = divide(4, 2);  // assigns an integer value = 2
                                                     //function call
$c = divide(3, 2);  // assigns a float value = 1.5

By default, variables are passed to functions by value, not by reference
An alternative to returning a result or using a global variable is to pass a reference to a variable as a parameter to the function. This means that any changes to the variable within the function affect the original variable. Consider this example:
function doublevalue(&$var)

{

    $var = $var * 2;

}



$variable = 5;

doublevalue($variable);

Function in PHP also supports default parameters.


Reusing Functions with Include and Require Files
===================================================
It's valuable to be able to reuse functions in many scripts. PHP provides the include and require statements that allow you to reuse PHP scripts containing statements, function definitions, and even static HTML.

<?php
include "functions.inc";
?>

If you decide to reuse the bold( ) function  in more than one script, you can store it in a separate include file . For example, you can create a file called functions.inc and put the bold() function in this file:
Include files can also be used to incorporate resources such as static HTML or a set of variable initializations. The following example could be written to the file release.inc and included in all the scripts of an application:

<?php

    $showDebug = true;

?>

Both include and require read external include files, the only difference is in the behavior when a file can't be included: include provides a warning whereas require terminates the script with a fatal error
The include and require statements can be treated in the same way as other statements. For example, you can conditionally include different files using the following code fragment:

if ($netscape == true)

{

    require "netscape.inc";

}

else

{

    require "other.inc";

}

Scripts can include more than one include file, and include files can themselves include other files. Writing scripts that use include or require can lead to an include file being included and evaluated twice. To avoid problems with variable reassignments and function redefinitions, PHP provides the include_once or require_once constructs statements that ensure that the contents of the file are included only once.

Managing include files
==========================
// a relative file path

require "../inc/myFunctions.php";

// an absolute file path

require "/library/database/db.inc";

A more sophisticated, and flexible alternative to accessing include files is to set the include_path parameter defined in the php.ini configuration file. One or more directories can be specified in the include_path parameter, and when set, PHP will search for include files relative to those directories. The following extract from the php.ini file shows how to set the include_path parameter:

include_path = ".;c:\php\includes;d:\php\projectx"

Type Conversion
==============================
PHP provides several mechanisms to allow variables of one type to be considered as another type. Variables can be explicitly converted to another type with the following functions:
string strval(mixed variable) 
integer intval(mixed variable [, integer base]) 
float floatval(mixed variable)

Example:
$year = 2003;

// Sets $yearString to the string value "2003"

$yearString = strval($year);

PHP also supports type conversion with type-casting

$firsttype = (type) $secondtype;

Example

$int = (int) $var;
$int = (integer) $var;
$int = intval($var);
$arr = (array) $var;
$obj = (object) $var;

Automatic Type Conversion
================================
Automatic type conversion occurs when two differently typed variables are combined in an expression or when a variable is passed as an argument to a library function that expects a different type.
// $var is set as an integer = 115

$var = "100" + 15;

Examining Variable Type and Content
Because PHP is flexible with types, it provides the following functions that can check a variable's type:

boolean is_int(mixed variable) 
boolean is_float(mixed variable) 
boolean is_bool(mixed variable) 
boolean is_string(mixed variable) 
boolean is_array(mixed variable) 
boolean is_object(mixed variable)

Is-identical and is-not-identical operators

PHP provides the is-identical operator === that tests not only values, but types also.
PHP also provides the is-not-identical operator, !==

Debugging with gettype( ), print_r( ), and var_dump( )

string gettype(mixed expression) 
print_r(mixed expression) 
var_dump(mixed expression [, mixed expression ...])

Testing, setting, and unsetting variables
boolean isset(mixed var) 
boolean empty(mixed var)
unset(mixed var [, mixed var [, ...]]) // destroys the  variable

Variable Scope
===================================
Variables used inside a function are different from those used outside a function.Global variablesA variable declared as global keyword is used everywhere even within function.

function doublevalue( )
{
global $temp;	//used everywhere in same way
$temp = $temp * 2;
}

Static variables

Variables can also be declared within a function as static. The static variable is available only in the scope of the function, but the value is not lost between function calls

function doublevalue( )
{
static $temp;	//only within function but remain persistence
$temp = $temp * 2;
}

Arrays, Strings, and Advanced Data Manipulation in PHP
=========================================================
Creating Arrays
PHP provides the array( ) language construct that creates arrays.

$numbers = array(5, 4, 3, 2, 1);
$words = array("Web", "Database", "Applications");
$shopping = array( );
$array = array("first"=>1, "second"=>2, "third"=>3);
$oddNumbers = array(1=>"one", 3=>"three", 5=>"five");
$numbers = array(1=>"one", "two", "three", "four");

Removing elements from an array
$favorites = array("PHP", "Ace", "COBOL", "Java", "C++");

// remove COBOL from the array

unset($favorites[2]);
To destroy a whole array, call unset( ) on the array variable:
// destroy the whole array

unset($favorites);


Heterogeneous arrays
$mixedBag = array("cat", 42, 8.5, false);

Multi Dimensional Array
we can create a multidimensional array like this:
$table = array(

    1 => array(1 => 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12),

    2 => array(1 => 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24),

    3 => array(1 => 3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36),

... 

);

// A two dimensional array using integer indexes

  $planets = array(array("Mercury", 0.39, 0.38),

                   array("Venus",   0.72, 0.95),

                   array("Earth",   1.0,  1.0),

                   array("Mars",    1.52, 0.53) );



  // prints "Earth" 
print $planets[2][0];
Using foreach Loops with Arrays


foreach(array_expression as $value)

{

    // body of loop

}
Functions that create arrays
PHP provides two functions that create new arrays with pre-filled values:
array array_fill(integer start, integer count, mixed value) 
array range(mixed low, mixed high [, integer step])

Strings
==============================


Length of a String
integer strlen(string subject)
Printing and Formatting Strings
Creating formatted output with sprintf( ) and printf( )
string sprintf (string format [, mixed args...]) 
integer printf (string format [, mixed args...])

The difference between sprintf( ) and printf( ) is that the output of printf( ) goes directly to the output buffer that PHP uses to build a HTTP response, whereas the output of sprintf( ) is returned $variable = 3.14159;


 $variable=3.1516154;
// prints "Result: 3.14"
printf("Result: %.2f\n", $variable);
.$message = sprintf("%c = %x (Hex) %o (Octal)", $c, $c, $c);
// prints "õ = f5 (Hex) 365 (Octal)"
 print($message);


Changing case
string strtolower(string subject) 
string strtoupper(string subject) 
string ucfirst(string subject) 
string ucwords(string subject)
Trimming whitespace
PHP provides three functions that trim leading or trailing whitespace characters from strings: 
string ltrim(string subject [, string character_list]) 
string rtrim(string subject [, string character_list]) 
string trim(string subject [, string character_list])

Comparing Strings
PHP provides the string comparison functions strcmp( ) and strncmp( ) that compare two strings in alphabetical order, str1 and str2:
integer strcmp(string str1, string str2) 
integer strncmp(string str1, string str2, integer length
string substr(string source, integer start [, integer length])



Dates and Times
=================================
PHP provides several functions that generate a Unix timestamp. The simplest:
integer time( )
int mktime(int hour, int minute, int second, int month, int day, int year [, int is_dst]) 
int gmmktime(int hour, int minute, int second, int month, int day, int year [, int is_dst])
integer strtotime(string time)
      $var = strtotime("now");

string date(string format [, integer timestamp]) 
string gmdate(string format [, integer timestamp])

// "24/08/1974"

print date('d/m/Y', $var);

Absolute Value
The absolute value of an integer or a float can be found with the abs( ) function:
integer abs(integer number) 
float abs(float number)


Ceiling and Floor
The ceil( ) and floor( ) functions return the integer value above and below a fractional value, respectively:
float ceil(float value) 
float floor(float value)
Number Systems
PHP provides the following functions that convert numbers between integer decimal and the commonly used number systems, binary, octal, and hexadecimal:
string decbin(integer number) 
integer bindec (string binarystring) 
string dechex(integer number) 
integer hexdec(string hexstring) 
string decoct(integer number) 
integer octdec(string octalstring)

OOP in PHP
================================
Classes and Objects

Definition of the user-defined class UnitCounter
<?php
// Definition of the class UnitCounter
class UnitCounter

{
    // Member variables

    var $units = 0;

    var $weightPerUnit = 1.0;


    // Add $n to the total number of units, default $n to 1

    function add($n = 1)

    {

        $this->units = $this->units + $n;

    }

    // Member function that calculates the total weight

    function totalWeight( )

    {

        return $this->units * $this->weightPerUnit;

   }
}

?>

// Create a new UnitCounter object

$bottles = new UnitCounter;
$bottles->units = 24;
// prints "There are 24 units"
print "There are {$bottles->units} units";

Using include Files for Class Definitions
By placing the definition into a file—for example UnitCounter.inc—you can include or require the UnitCounter class in other scripts.
<?php

    require "UnitCounter.inc";

     // Create a new UnitCounter object

    $bottles = new UnitCounter;
?>
Constructors
PHP5 allows you to declare a constructor method by including the member function _ _construct( ) in the class definition—the function name _ _construct( ) is reserved for this purpose (the characters preceding the word construct are two consecutive underscores).
function _  _construct($unitWeight = 1.0)

    {

        $this->weightPerUnit = $unitWeight;

        $this->units = 0;

    }
Destructors
Destructors are available in PHP5.
A destructor function is defined by including the function _ _destruct( ) in the class definition
Private member variables are available in PHP5.
Private member functions are available in PHP5.
Static member variables are available in PHP5.
Static member functions are declared using the static keyword, and like static member variables, aren't accessed via objects but operate for the whole class and are accessed using a class referencereturn Donation::$totalDonated;//Donation class’stotalDonated variable
static functions Donation::total( )// calling technique
Cloning Objects
Objects can optionally be cloned in PHP5, and are always cloned in PHP4. We explain how this works in this section.
The _ _clone( ) method is available if you want to create an independent copy of an object. PHP5 provides a default _ _clone( ) function that creates a new, identical object by copying each member variable. Consider the following fragment:
$a = new UnitCounter( );



$a->add(5);

$b = $a->_  _clone( );

$b->add(5);
Inheritance
Inheritance is available in PHP4 and PHP5.
class CaseCounter extends UnitCounter //keyword extends is used to inherit 
The CaseCounter class shown in Example 4-8 solves this problem by defining a _ _construct( ) function that calls the UnitCounter _ _construct( ) function using the parent:: reference.
function _  _construct($caseCapacity, $unitWeight)

    {

        parent::_  _construct($unitWeight);

        $this->unitsPerCase = $caseCapacity;

    }
The parent:: reference operator only allows access to the immediate parent class. PHP allows access to any known ancestor class using a class reference operator
Protected Member Variables and Functions
Protected members are available in PHP5.

Throwing and Catching Exceptions
=========================================
PHP 5 has introduced an exception model that allows objects to be thrown and caught using the throw and try...catch statements same as c++

Opening and Using a Database Connection
===================================================
  (1) Open the database connection

   $connection = mysql_connect("localhost","fred","shhh");

  (2) Select the winestore database

   mysql_select_db("winestore", $connection);

  (3) Run the query on the winestore through the connection

   $result = mysql_query ("SELECT * FROM wine", $connection);

  (4) While there are still rows in the result set, fetch the current
      row into the array $row

   while ($row = mysql_fetch_array($result, MYSQL_NUM))
    {     
//MYSQL_NUM is a PHP constant that tells the function to return a numerically accessed array;

      (5) Print out each element in $row, that is, print the values of        
         the attributes

      foreach ($row as $attribute)

         print "{$attribute} ";

      // Print a carriage return to neaten the output

      print "\n";

   }

// How many attributes are there?

   $x = mysql_num_fields($result);

Security and User Data
================================

Starting a Session
The session_start( ) function is used to create a new session
// This call either creates a new session or finds an existing one.

  session_start( );

