[microslop ref](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/new-operator)

`new` in C# is similar to how you would use it in C++, which is to create new object instances however, when it comes to the destruction, the C# **garbage collector** handles all destruction of objects created with the `new` operator

```run-cs
	public class SomeC
	{
		public SomeC() {}
		public void PrintCoolThing(string thing)
		{
			Console.WriteLine(thing);
		}
	}
	
	//'new' keyword used to create a new instance of an object
	SomeC sc = new SomeC();
	
	sc.PrintCoolThing("My cool thing");
	
	//garbage collector handles cleanup once object exits its scope
```


