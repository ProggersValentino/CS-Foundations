[ref](https://learn.microsoft.com/en-us/dotnet/standard/generics/)

Generics in C# are the equivalent to C++ templates with less features.

Generics can come in form of classes, variables, functions and interfaces

```cs
//generic class 
public class GenClass<T>
{
	T value; // generic variable 
	
	public GenClass(T valINP)
	{
		value = valINP;
	}
	
	//generic function with multiple input params that can potentially be anything
	public A SomeFunc<A,F>(A val1, F val2)
	{
		Console.WriteLine(val2);
		return val1;
	}
}
```

The code is then generated automatically by the compiler.

```run-cs
//generic class 
public class GenClass<T>
{
	T val; // generic variable 
	
	public GenClass(T valINP)
	{
		val = valINP;
	}
	
	public A SomeFunc<A,F>(A val1, F val2)
	{
		Console.WriteLine(val2);
		return val1;
	}
	
	public void PrintVal()
	{
		Console.WriteLine($"The value is: {val}");
	}
}

GenClass<int> gic = new GenClass<int>(42);
GenClass<string> gsc = new GenClass<string>("Dumb Memes");

gic.PrintVal();

gsc.PrintVal();

string ss = gic.SomeFunc<string, int>("Cool String to priint", 465123);

Console.WriteLine(ss);

```

