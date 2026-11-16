[ref](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)


## Access Modifiers
When declaring or defining new variables and/or functions, you must prefix each one an access modifier which determines the level of freedom that code can be accessed, used, modified throughout the codebase.

If not access modifier is provided the default scope that it gives to the definition is `private`

```cs
public int num = 1; //<-- can be accessed by other classes

int privNum = 2; //<-- cannot be accessed by other classes
```

| Modifier    | Meaning                                                   |
| ----------- | --------------------------------------------------------- |
| `private`   | can only be accessed by the class its defined in          |
| `public`    | can be accessed by **external classes**                   |
| `protected` | can only be accessed by **derived classes**               |
| `internal`  | can only be accessed by classes within the same namespace |

## Polymorphism Modifiers

