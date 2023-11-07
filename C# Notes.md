# C# Notes

## Basics

### Data types
There are mainly three types in C#. based on how they store their value in the memory
1. Value Types (stores value in itself)
2. Reference Types(points to the memory where the value is stored)
3. Null Types

**Common Data Types**:
```cs

//explicit typed 
int intVar = 100;
float floatVar = 10.2f;
double doubleVar = 12345678912345.5d;
char charVar = 'A';
bool boolVar = true;
string name = "Name"

//implicit typed
var j = 2;
```
-- --

### String
- / - escape character
- @ - verbatim string, used also for multiline strings
- ${} - string interpolation
  
to use special characters or keywords in a string, use escaping character (/) or verbatim string(@)
```cs
string example = "This is a \"string\" in C#."
//or
string example2 = @"This is a "string" in C#";
```
To use string interpolation, prefix the string with $ and cover the variable with {}. 
```cs
string fullName = $"Mr. {firstName} {lastName};
```

-- --

## Operators

Most used operators
```cs
+ //add
- //sub
/ //quotient
* //multiply
% //remainder

|| //or 
&& //and
! //not

//equality operators
> , <
>= <=
==
```

-- --

## Conditionals

### If, if else
Checks for the condition and executes based on it
```cs
Syntax
if(condition){
    //code block
}else if(condition){
    //code block
}else{
    //code block
}
```

### Ternary operator ( ?: )

it's a short form for If else conditionals

```cs
var x = 2;
var y = 3;
string result = x > y ? "x greater" : "y greater";
```

### Switch statement
It can be used as an alternative for if else statement

```cs
//syntax
switch(match expression/variable)
{
    case constant-value:
        statement(s) to be executed;
        break;
    default: 
        statement(s) to be executed;
        break;
}

//example
int x = 10;

switch (x)
{ 
    case 5:
        Console.WriteLine("Value of x is 5");
        break;
    case 10:
        Console.WriteLine("Value of x is 10");
        break;
    default:
        Console.WriteLine("Neither 10 or 5")
        break;
```

-- --

## Loops

### For loops
To run a code for predetermined number of times
```cs
//syntax
for (initializer; condition; iterator)
{
    //code block 
}
//example
for(int i = 0; i < 10; i++)
{
    Console.WriteLine("Value of i: {0}", i);
}
```

### While loop
Till the condition is returned true, the loops goes on.
```cs
//syntax
While(condition)
{
    //code block
}
//example
var x = 1 
while (x == 10 ){
    Console.WriteLine(x);
    x++;
}
```
### do while loop
runs the loop atleast once , before checking for condition
```cs
do{
    //something
}while(condition);
```

-- --

## Classes and objects

### Class
A Class is a blueprint which contains properties, fields and methods
- Fields: it's a variable which holds a value
- Properties: Encapsulates Field and gets and sets value
- Methods: It's a function that does something
- Constructor: Initializes the class for every new object. Defaulted if none provided

Note: After C# 3, fields are hidden by compiler and only Properties are used. 
```cs
public class Student{
    //fields
    private string name;

    //property
    public string Name{
        get{return name;}
        set{name=value;}
    }

    //simplified modern approach
    public string Name{get;set;}

    //Constructor
    public Name{
        //do something or nothing
    }
}
```

### Access Modifiers
- **Public** : Anyone can access it. Like a park
- **Private**: Only the class that contains it can access it. It's like a private room in a house where only family members can enter
- **Protected**: Only the class that contains it and its subclasses (inheritors) can access it. 
- **Internal**: Only code within the same assembly (a compiled unit like a DLL or EXE) can access it. It's like a building where only people inside that building can access certain rooms.

### Objects
One can create an object through the new() keyword
```cs
public class Main(){
    Student newStudent = new Student();
}
```

### Partial classes
with "partial" keyword one can implement classes, structs, interfaces in different .cs files and the compiler will join them.
It's useful for separation of concerns and extending the default class's functionality.
The class must be in same assembly and namespace

```cs
// in Employee.cs file
public partial class Employee
{
    public int EmpId { get; set; }
    public string Name { get; set; }
}
// in another .cs file
public partial class Employee{
    //constructor
    public Employee(int id, string name){
        this.EmpId = id;
        this.Name = name;
    }
}
```


### Namespaces

Classes can be grouped under a Namespace and be accessed in another namespace/file with the "using" keyword.

## Intermediate

### Structs
it's like a grouping of commonly used data. It's like a Class but doesn't support initialization

```cs
struct Coordinate
{
    public int x { get; set; }
    public int y { get; set; }

    public void SetOrigin()
    {
        this.x = 0;
        this.y = 0;
    }
}

```

### Enums 
Enums are used as custom Variable names instead of the default data types. The compiler assigns an integer Value(can be byte, float, etc.) to each of the Enum value
```cs
enum WeekDays
{
    Monday,     // 0
    Tuesday,    // 1
    Wednesday,  // 2
    //
}
Console.WriteLine(WeekDays.Monday); 
Console.WriteLine((int)WeekDays.Monday); //0

```

-- --

## Static

### Static classes
They can't be initialized and can only contain Static methods and fields.
The methods and fields can be directly accessed in the namespace
```cs
// in program.cs
static void Main(string[] args){
    Calculator.Add(3,5)
    Console.WriteLine(Calculator.result)
}
//in Calculator.cs
static class Calculator{
    //fields
    static int result = 0;

    static void Add(int x, int y){
        result = x + y;
    }
}
```

### Static methods and constructors
- A normal class can contain static methods and constructors. 
- Static methods can't access or call non-static variables
- Static constructors are run only once. Good for initializing seed or a base value.


-- --


## Extras

### Anonymous classes
basically a Class but without properties, methods and initialization

```
var Student = new{id= 1, name="kay", subject="Elektro"};
```