[microslop ref](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types)

A variable in C# is generally defined by the following syntax:

```cs
//format
<scope level> <type> "name" = value

string coolName = "Bob" //private variable typed string

public string coolName = "Bob" //public variable typed string
```

by default, when no equal operation is assigned, depending on the type, the default initialization is `null` or a default value built in like `int` will be set to 0

```run-cs
int? num;
string s;
string sc = "";

Console.WriteLine(num);
Console.WriteLine(s);
Console.WriteLine($"s is null with no initializer: {s == null}");
Console.WriteLine($"sc is null with initializer: {sc == null}");
Console.WriteLine($"integer is null with no initializer: {num == null}");
```

## `?` Operator
  By default the compiler will warn you about variables that have not been initialized with default values unless you give that variable permission to be nullable with the `?` operator after specifying the type:
```cs
string name; //<-- compiler will warn against uninitialized variable

string? name; //<-- compiler will accept
```

## Built in types

```cs

bool bIsTrue = false;

//numbers
int iNum = 1; //positive and negative numbers
uint unum = 23; //only positive numbers

float fnum = 1.0f;
double dnum = 1.0d;

//binary
byte b = 0b_0010_0100;
sbyte sb = 0b_0010_0100;

var hexLit = 0x2A;

//characters
char c = 's';
```

## C# Specific Types

```cs
string s = "this is a string";
object obj = new object();

public delegate int GetTotal(int val1, int val2);
```

## Delegates
[ref](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/reference-types#the-delegate-type), [using delegates](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/delegates/using-delegates)

delegates operate the same as **function pointers** in c++ where you can assign functions as a variable which can be called upon without needing reference to the original function. 

```cs
public delegate int SomeDelegate(int x); //<-- initialization of delegate

SomeDelegate del; //<-- can be stored as its own variable type for functions that resemble the same function signature

public void SomeFunc(SomeDelegate delINP) {} //<-- can be used as a parameter for other functions and called within that function
```

### Action<> & Func<>

`Action<>` and `Func<>` are generic type of delegates where for `Action<>` the function signatures will always have a `void` return type whereas the `Func<>` will always have a specific return type which can be void but is redundant 

