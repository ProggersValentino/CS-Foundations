
unit testing in C# is a bit different to setting it up within C++, for C#, it is recommended you create a new project dedicated to just testing. Once created you must link the new with your console app you're wanting to test and only then you can create and run tests for your code

this can be done two ways, 

1. using the [dotnet cli to create and link the project](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-csharp-with-nunit) to your main
	1. ensure the project is laid out with the following structure:
	```
	/projectName
	    projectName.sln
	    /Project_Src
	        Source Files
	        Project_Src.csproj
	    /Project_Src.Tests
	        Test Source Files
	        Project_Src.Tests.csproj
	```
	2. run the following power shell commands to create and link the unit test project to the source code
	```.net
	cd Project_Src.Tests
	dotnet new nunit
	dotnet add reference ../Project_Src.csproj 
	```

	3. Run the final command to make link the unit test's `.csproj` with the overall project `.sln` file
	```dotnet
	cd ../
	dotnet sln add ./Project_Src.Tests/Project_Src.Tests.csproj 
	```

2. Use the [GUI to initialize and set up the unit testing project](https://learn.microsoft.com/en-us/visualstudio/test/getting-started-with-unit-testing?view=visualstudio&tabs=dotnet%2Cxunit)


## Assertion - NUnit Framework

Assertions is how we test whether the code we want to test can pass or fail. 

There are many different ways to use an assertion to test code which involves using:

- [Assertion class](https://learn.microsoft.com/en-us/dotnet/api/nunit.framework.assert) which has a bunch of static methods to use
- [Is class](https://learn.microsoft.com/en-us/dotnet/api/nunit.framework.is) to combine with the Assertion class to create many different results to test for

Generally, the assertion class is used under the **constraint model** which means that you would normally use:

```cs
Assert.That(<condition>, Is.<what to test for>, "error message")
```

to cover the use of all the static methods it lists, so the `Is` class will be the main determiner of how you want to test a result from your code

## General Wrappers - NUnit Framework

| Attribute       | Purpose                                                         |
| --------------- | --------------------------------------------------------------- |
| `[SetUp]`       | Indicates an initializer method for when the test gets executed |
| `[TestFixture]` | A class that contains a group unit tests                        |
| `[Test]`        | Indicates a single method for unit testing                      |
| `[TestCase()]`  | to create a suit of tests for a single unit test method         |

