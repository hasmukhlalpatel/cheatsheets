# C# 7 cheatsheet
## Out Variables
```csharp
    public void PrintCoordinates(Point p)
    {
        p.GetCoordinates(out int x, out int y);
        WriteLine($"({x}, {y})");
    }
```
### out is used to declare a variable at the point where it is passed as an argument.

## Tuples
### Tuple type
```csharp
(string, string, string) LookupName(long id) // tuple return type
{
    ... // retrieve first, middle and last from data storage
    return (first, middle, last); // tuple literal
}
var names = LookupName(id);
	WriteLine($"found {names.Item1} {names.Item3}.");
```
### Tuple elements with name
```csharp
	(string first, string middle, string last) LookupName(long id) // tuple elements have names
	var names = LookupName(id);
	WriteLine($"found {names.first} {names.last}.");
```
### Tuple Literals
```csharp
	return (first: first, middle: middle, last: last); // named tuple elements in a literal
```
### Tuple Deconstruction
```csharp
	(var first, var middle, var last) = LookupName(id1);
	WriteLine($"found {first} {last}.");
```
or

```csharp
	var (first, middle, last) = LookupName(id1); // var outside
```
or

```csharp
	(first, middle, last) = LookupName(id2); // assign onto existing variables
```


## Pattern Matching
### Is-expressions with patterns
```csharp
	public void PrintStars(object o)
	{
		if (o is null) return;     // constant pattern "null"
		if (!(o is int i)) return; // type pattern "int i"
		WriteLine(new string('*', i));
	}
```
### Switch statements with patterns
```csharp

	switch(shape)
	{
		case Circle c:
			WriteLine($"circle with radius {c.Radius}");
			break;
		case Rectangle s when (s.Length == s.Height):
			WriteLine($"{s.Length} x {s.Height} square");
			break;
		case Rectangle r:
			WriteLine($"{r.Length} x {r.Height} rectangle");
			break;
		default:
			WriteLine("<unknown shape>");
			break;
		case null:
			throw new ArgumentNullException(nameof(shape));
	}

```


## Local Functions
```csharp

	public int Fibonacci(int x)
	{
		if (x < 0) throw new ArgumentException("Less negativity please!", nameof(x));
		return Fib(x).current;

		(int current, int previous) Fib(int i)
		{
			if (i == 0) return (1, 0);
			var (p, pp) = Fib(i - 1);
			return (p + pp, p);
		}
	}

```




    ```csharp
          // Code to execute.
    ```
    ```csharp
    for (int i = 0 ; i < 10; i++)
    {
      // Code to execute.
    }
    ```
