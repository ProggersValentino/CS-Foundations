
## Arrays 
[ref](https://learn.microsoft.com/en-us/dotnet/api/system.array?view=net-10.0)

an array follows the set syntax for declaration:
```cs
<type>[] arrayName;
```

```run-cs
int[] numArr = new int[5] {5, 7, 8, 1, 8};

foreach (int num in numArr)
{
	Console.WriteLine(num);
}

//another way to set an array 
string[] officeNames = ["Bob", "Jim", "Yelp"];

string selectedName = officeNames[2]; //<-- you can extract an element from the array by applying [] and the element index you want

Console.WriteLine($"the selected name for the office cat is: {selectedName}");


```

You can also have a multidimension array
```run-cs
int[,] multDimenArr = new int[2, 4] {{3,4,68,21}, {6, 70, 12, 71}}; //<-- here the array will be two rows with 4 columns


//here to access an element you supply two numbers, one to determine which subarray to access and the other for which specific element 
//i.e. multDimenArr[0, 3] = 21
Console.WriteLine(multDimenArr[1, 2]);

Console.WriteLine("Printing values using for loop");
for (int i = 0; i < 2; i++)
{
	Console.WriteLine(multDimenArr[i,i]);
}

Console.WriteLine("Printing values using foreach loop");
//here in the foreach loop we can print a whole set of numbers per subarray
foreach(int numSet in multDimenArr)
{
	Console.WriteLine(numSet);
}
```

In arrays you cannot modify the size of the array after initialization, so if you want it to be bigger you must 
## Lists
[ref](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/collections), [syntax](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1?view=net-11.0)

In C# lists are defined by the following syntax

```cs
List<type> listName = new List<type> {data};
List<type> listName = [data];

//syntax to add and remove elements
listName.Add(value);
listName.Remove(value);

listName.Count //<-- get the current size of the list
```

```run-cs
List<int> numLis = [0, 50, 20];

//access list elements like an array with the square braces and index number
Console.WriteLine(numLis[2]);

//adding element to the end of the list
numLis.Add(67);

Console.WriteLine("For Loop print:");

for (int i = 0; i < numLis.Count; i++)
{
	Console.Write($"{numLis[i]}, ");
}

//removing an element within the list, generally 
numLis.Remove(50);
Console.WriteLine("For Loop print with one less element:");

for (int i = 0; i < numLis.Count; i++)
{
	Console.WriteLine(numLis[i]);
}
```

## Dictionary 
[ref](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=net-10.0)

```cs
//defining new uninitialized dictionary
Dictionary<type, type> dictionaryName = new Dictionary<type, type>();

//initializing a new dictionary
Dictionary<type, type> dictionaryName = new Dictionary<type, type>()
{
	{key, value},
	{key, value},	
};


//adding key/value pairs to an existing dictionary
dictionaryName.Add(key, value)

//removing key/value pairs from an existing dictionary
dictionaryName.Remove(key, value)

//checks to see if key is within dictionary O(1)
bool containKey = dictionaryName.ContainsKey(key)

//check to see if dictionary has value - this search is O(n)
bool containValue = dictionaryName.ContainsKey(value)

//trys to find value and assigns an out value to it upon succession O(1) 
dictionaryName.TryGetValue(key, out value);

```

```run-cs
Dictionary<char, string> keyBinds = new Dictionary<char, string>
{
	{'s', "sillySnake"},
	{'p', "PrancingPillow"},
	{'a', "AnsyAnaconda"}
};
 
keyBinds.Add('z', "zleepingZebra");

string thing = ""; 

if(keyBinds.TryGetValue('z', out thing))
{
	Console.WriteLine($"keybind outputted from dictionary: {thing}");
}

//getting all the keys into a iterable collection
Dictionary<char, string>.KeyCollection keyColl = keyBinds.Keys;

foreach(var key in keyColl)
{
	Console.WriteLine(key);
}

```


## Queue
[ref](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.queue-1?view=net-10.0)

## Stack
[ref](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.stack-1?view=net-10.0)

