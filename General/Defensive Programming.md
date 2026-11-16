


## Asserts
[ref](https://learn.microsoft.com/en-us/visualstudio/debugger/assertions-in-managed-code?view=visualstudio&tabs=csharp)****

C# has dedicated classes for applying some defensive programming, one of which is using asserts

```run-cs
using System.Diagnostics;

int someNumber = 8;

Trace.Assert(someNumber == 2, "Number did not equal to set number");

Console.WriteLine(someNumber);
```

Which when ran, the compiler will throw an error during runtime and stop the program in its tracks. This is generally used for code you know that for certain the condition will always be true 

## Try Catch Statement
[try catch](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/exception-handling), [exception keywords](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/exception-handling-statements)

if C# you can use a `try catch` statement to attempt to run a section of code and catch any unexpected error that you the programmer did not account for.

```cs
try
{
	//input code to try
}
catch (<exception type> e)
{
	//insert code of how you want to handle the exception
	throw new <exception>
}
//optional
finally
{
	//insert code that you want to run after being tested through try
}
```

```run-cs

int[] array = [2, 5, 7, 100, 21];

try
{
	Console.WriteLine(array[6]); //will be caught 
}
catch (IndexOutOfRangeException e) //catches any error involving an index out of range. will stop the program completely and throw it to the compiler
{
	throw new ArgumentOutOfRangeException("The index provided exceeded the array's size and therefore could not find an element", e);
}





```

