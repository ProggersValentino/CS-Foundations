[ref](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/iteration-statements)

C# comes with the standard 4 types of loops 

## For Loop

```cs
for(int i = 0; <condition>; <increment/decrement i var>)
{
	//insert loopable code
}
```

```run-cs

Console.WriteLine("Default For Loop");

//The default for loop 
for(int i = 0; i < 10; i++)
{
	Console.WriteLine(i);
}


Console.WriteLine("Infinite For Loop");
int num = 0;

//infinite for loop where the only way to break out is using a check with break
for (; ;)
{
	if(num > 10)
	{
		break;
	}
	Console.WriteLine(num);
	
	num++;
}
```

## Foreach Loop

Generally used for looping through a collection of items

```run-cs
string[] nameArr = new string[4] {"Bob", "Gemma", "Chris", "Ben"};

foreach (string name in nameArr)
{
	Console.WriteLine(name);
}
```


## While loop

Will loop forever until condition is true
```cs
while(<condition thats currently true>)
{
	//execute loopable code
}
```

 ```run-cs
 
 int incre = 0;
 
 //default while loop which checks the condition first before executing the code below
 while(incre < 10)
 {
	 Console.WriteLine($"While Loop Incrementation: {incre}");
	 incre++;
 }
 
 ```


## Do While Loop

Do while loops are like while loops except they execute the code body first **THEN** check the condition to see if it still remains

```cs
do
{
	//insert code here
}
while(<condition>)
```