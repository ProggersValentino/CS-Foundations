[ref](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/enums)

Enums in C# can be defined by the following syntax:

```cs
<access modifier> enum "name of enum"
{
	//enum values
	None,
}

enum "name of enum" : <integral type>
{
	//enum values
	None = <integral-value>
}

enum Season
{
	Summer,
	Autumn,
	Winter,
	Spring,
}

//enum with explicit values tied to the underlying type to give meaning to values
enum TaxableIncome : ushort
{
	NONE = 0,
	MiddleClass = 1,
	FirstClass = 2,
	RICH = 3,
}

```


When declaring an enum, you must define the enum's access modifier to be higher or equal to the overall intention of it use otherwise the compiler will error 

```run-cs
enum Season
{
	Summer,
	Autumn,
	Winter,
	Spring,
}

public class Calender
{
	public Season season; //<-- because we've defined this variable as public and the enum is private, the compiler will not compile and throw an error
	
	Calender() 
	{
		season = Season.Summer;
	}
}
```

