[ref](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods)

Functions in C# are declared within Classes, structs and interfaces with the following syntax:

```cs
<access modifier> <return-type> "name"(<param type> "param name", ...)
{
	//insert code for function
}

//function that returns a type
public float GetExplosionRadius(string exploType)
{
	//insert code to calculate 
}

//function that returns nothing
public void PrintText(string text)
{

}
```

If given no access modifier then the function defaults to `private` 

```run-cs
public class Something
{
	public Something(){}
	
	public void PrintText(string text)
	{
		Console.WriteLine($"Some cool text: {text}");
	}
}

Something sg = new Something();

sg.PrintText("I Am Something");
```

## Ref or value

when it comes to parsing data through to functions, you can parse data through two ways, 

either parse a value to the function which creates a copy of the data you parsed to for the function call meaning any changes that happen to the value don't affect the original

Or you can parse by reference which is done by prefixing the param type with a `ref` operator functioning as a pointer to the original value meaning any changes to that value will directly affect the original

```run-cs
public class Thing
{
	public Thing() {}
	
	//parsing by value therefore will create a copy of a string specifically for this function
	public void PrintText(string text)
	{
		Console.WriteLine(text);
	}
	
	//parsing by reference therefore you must parse the function with a variable it can refer to, does not work with literals
	public void PrintRefText(ref string text)
	{
		Console.WriteLine(text);
	}
}

Thing th = new Thing();

string refStr = "This is a string stored by a variable";

th.PrintText("This is a string literal");
th.PrintRefText(ref refStr); //<-- cannot use a string literal


```

## Polymorphism 
[ref](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/polymorphism)

You can also create abstract functions that can be redefined (overrode) by other derived classes from that base class 

This is done by postfixing the access modifier with a `virtual` or `abstract` keyword on the function allowing you to define a base implementation for a function or fully leave it up to the derived class to create a definition

```run-cs
public class BaseCool
{
	public BaseCool() {}
	
	public virtual float FindArea(float x, float y)
	{
		return x * y;
	}
}

public class DerivCool : BaseCool
{
	public DerivCool() {}
	public override float FindArea(float x, float y)
	{
		x *= 2;
		y *= 4;
		
		return x * y;
	}
}

BaseCool bc = new BaseCool();
DerivCool dc = new DerivCool();

float x = 3;
float y = 2;

Console.WriteLine(bc.FindArea(x,y));
Console.WriteLine(dc.FindArea(x,y));
```


As shown, you can override the base implementation by postfixing the desired function's access modifier with a `override` keyword allowing you to define in the child class a new implementation

You can also use the `base` keyword to invoke a base class's function within the overrode function allowing you to add on the base functionality with new functionality in the overrode function.

```run-cs
public class BCool
{
	public BCool() {}
	
	public virtual void PrintFace()
	{
		Console.WriteLine("This is a neutral face: :/");
	}
}

public class DBCool : BCool
{
	public DBCool() {}
	
	public override void PrintFace()
	{
		base.PrintFace();
		
		Console.WriteLine("This is happy face: :D");
	}
}

DBCool dbc = new DBCool();

dbc.PrintFace();
```

## References
[ref](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/method-parameters#ref-parameter-modifier)

within method parameters you can add the `ref` or `out` keyword modifier which now you're passing by reference meaning that any changes made to the parameter directly affect the original value which was parsed from outside the local scope of the function.

This prevents unnecessary data from being copied into the function call wasting a lot of memory.

```run-cs
public class RefClass
{
	public RefClass() {}
	
	//using a ref to parse a variable reference to the method
	public void ChangeNumber(ref int numToChange)
	{
		numToChange *= 2; //change will carry into the original variable like a left-hand ref
	}
}

RefClass rc = new RefClass();

int someNum = 23;

Console.WriteLine($"The number is: {someNum}");

rc.ChangeNumber(ref someNum); //<-- number changed globally because ref affects the variable outside its local scope

Console.WriteLine($"The number is: {someNum}");
```

```run-cs
public class OutClass
{
	public OutClass() {}
	
	//whatever variable we pass will be a reference to that variable so that any changes made directly impact the referred variable
	public void MultiReturn(ref int numINP, out string wordMsg)
	{
		int numStart = numINP;
		
		Random rnd = new Random();
		numINP *= rnd.Next(-13, 13);
		
		if(numINP > numStart)
		{
			//the assignment of the wordMsg carries on beyond the function scope into the variable that is getting referenced to assign it
			wordMsg = $"Number increased to {numINP} from {numStart}";
		}
		else
		{
			wordMsg = $"Number decreased from {numStart} to {numINP}";
		}
	}
}

OutClass oc = new OutClass();

int num = 43;
string resultMsg;

oc.MultiReturn(ref num, out resultMsg);

Console.WriteLine(resultMsg);

```
