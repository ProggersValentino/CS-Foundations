[microslop ref](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/classes)

Classes in C# can be created by the following syntax:

```cs
//base class
<access modifier> class "name"
{
	public <constructor>() {} //the constructor is the initializer 
}

//inheritance with another class, there can ONLY BE ONE inherited class
<access modifier> class "name": "inherited base class name"
{
	public <constructor>() {} //the constructor is the initializer 
}

//inheritance with interfaces, there can be an unlimited amount of interface classes that a base class can implement from
<access modifier> class "name": "interface name", "interface name"
{
	public <constructor>() {} //the constructor is the initializer 
}
```

```cs
public class SomethingCool
{
	public SomethingCool()
	{
	 //insert initialization code here 
	}
}
```

When a class is created, by default it retains a private access modifier if non is specified 

## Structs

structs in C# follow the same definition declaration except the keyword `struct` is used instead of `class`

```cs
<access modifier> struct "name"
{
	<constructor>() {}
}

struct SomeStruct
{
	public SomeStruct() {}
}
```

Another difference is that by default structs retain a `public` access modifier unless specified 

## Constructors
[ref](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/constructors)

constructors in classes and structs is the overall initializer used to set up a class or struct instance when created using the `new` operator.

A constructor is defined by function that has the **same name** as its class or struct with parameters to define default values that require input upon creation of the object. this is mostly used to either initialize  

Constructors can be overloaded to have many different signatures 

```run-cs
public class CCool
{
	public int age {get; private set;}
	public int daysTillDeath {get; private set;}
	public string name {get; private set;}
	
	//default initialization
	public CCool(string nameINP, int ageINP, int daysINP)
	{
		name = nameINP;
		age = ageINP;
		daysTillDeath = daysINP;
	}
	
	//no name inp overload
	public CCool(int ageINP, int daysINP)
	{
		name = "Unknown"; //<-- hard code the name to a default value 
		age = ageINP;
		daysTillDeath = daysINP;
	}
}


CCool cc = new CCool("Bob", 32, 1000);
CCool cc1 = new CCool(32, 6);

Console.WriteLine($"Person: {cc.name}, age: {cc.age}, days till death: {cc.daysTillDeath}");
Console.WriteLine($"Person: {cc1.name}, age: {cc1.age}, days till death: {cc1.daysTillDeath}");

```

### Destroying Class instances

When it comes to destroying the class instances, the C#'s **garbage collector** handles everything but you can customize how the garbage collector destroys the object by creating a **Deconstructor** within by:

```cs
public class SC
{
	public SC(){}
	
	
	~SC() {} //<-- deconstructor on how we want to destroy the object
}
```

this is generally used when you need to safely disconnect or destroy any instances that may cause the program to crash if not handled

## Inheritance
[ref](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/inheritance)


