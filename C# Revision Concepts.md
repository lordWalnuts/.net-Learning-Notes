# C# Revision Notes

## Basics

### Datatypes
There are mainly three types in C#. based on how they store their value in the memory
1. Value Types (stores value in itself)
2. Reference Types(points to the memory where the value is stored)
3. Null Types

**Common Data Types**:
```cs
int intVar = 100;
float floatVar = 10.2f;
double doubleVar = 12345678912345.5d;
char charVar = 'A';
bool boolVar = true;
string name = "Name"
```

## Classes and objects

### Class
A Class is a blueprint which contains properties, fields and methods
- Fields: it's a variable which holds a value
- Properties: Encapsulates Field and gets and sets value
- Methods: It's a function that does something
- Constructor: Initializes the class for every new object. defaulted if none provided

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
- **Private**:  Only the class that contains it can access it. It's like a private room in a house where only family members can enter
- **Protected**: Only the class that contains it and its subclasses (inheritors) can access it. 
- **Internal**:  Only code within the same assembly (a compiled unit like a DLL or EXE) can access it. It's like a building where only people inside that building can access certain rooms.

### Object
One can create an object through the new() keyword
```cs
public class Main(){
    Student newStudent = new Student();
}
```