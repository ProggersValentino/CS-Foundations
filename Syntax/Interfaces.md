[ref](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/interfaces)

Interfaces in C# can be defined by the following syntax

```cs

interface "name of interface"
{
	//define functions with no implementation
	void func();
}

interface IVisual
{
	float VisualiseCamera(); //<-- in interfaces we cannot have an implementation for the defined function that is the responsibility of the class that implements the interface 
}
```

When it comes to inheritance for classes and interfaces, unlike base classes, you can inherit and implement as many interfaces as your heart desires. If implementing an interface, the C# compilers reinforces the need to implement the functions by throwing an error if not done:

```run-cs
//When we dont implement the interfaces we want to inherit form

interface IPrintable
{
	void Print();
}

interface IDamagable
{
	float ApplyDamage(float dmg);
}

public class Player : IPrintable, IDamagable
{
	public int health {get; private set;}
	string name;

	public Player(string nameINP, int healthINP)
	{
		name = nameINP;
		health = healthINP;
	}
}

Player pp = new Player("bob rose", 100);

Console.WriteLine($"player's health: {pp.health}");
```

```run-cs
//When we do implement the interfaces we inherit from
interface IPrintable
{
	void Print();
}

interface IDamagable
{
	int ApplyDamage(int dmg);
}

public class Player : IPrintable, IDamagable
{
	public int health {get; private set;}
	string name;

	public Player(string nameINP, int healthINP)
	{
		name = nameINP;
		health = healthINP;
	}
	
	public void Print()
	{
		Console.WriteLine($"This player is named: {name}, with a current health of: {health}");
	}
	
	public int ApplyDamage(int dmg)
	{
		health -= dmg;
		
		return health;
	}
	
}

Player pp = new Player("Bob rose", 80);
Console.WriteLine($"player's health: {pp.health}");

//assigning the player object to specific interface types which can be used when creating generic code and we don't need to know concrete object classes but just if its part of the interface or not
IDamagable dObj = pp;
IPrintable pObj = pp;

dObj.ApplyDamage(12);
pObj.Print();
```
