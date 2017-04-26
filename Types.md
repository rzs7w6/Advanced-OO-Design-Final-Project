# Types

## C# (sharp)
* C# provides a standard set of built-in numeric types to represent integers, floating point values, Boolean expressions, text characters, decimal values, and other types of data.

```csharp
int a = 5;
//this is allowed
int b = a + 5;

bool c = true;
//this would not work cause you can't add a bool and an int
int d = b + c

```

* C# also supports custom data types that the user can make whether that is a struct, class, interface, or eneum.

```csharp

public struct Pet
{
    public string name;
    public string type;
}

```

* https://msdn.microsoft.com/en-us/library/ms173104.aspx

* The default way of passing variables is by value but when the user uses a the ref key word it passes the variable by reference.

```csharp
class Test
{
  public static void Main(string[] args)
  {
      int argumentTobePassed;

      argumentTobePassed = 10;
      //this is pass by value
      multiplyVal(argumentTobePassed);
      //this is pass by reference
      multiplyVal(ref argumentTobePassed);
  }

  public static void multiplyVal(int value)
  {
    value = value * 2;
  }

  public static void multiplyVal(ref int value)
  {
    value = value * 2;
  }
}
```
* New value types can be created by the user see the link below.
* https://msdn.microsoft.com/en-us/library/wysdab55(v=vs.80).aspx
## Ruby

* Ruby supports Numbers, Strings, Boolean, Symbols, Arrays, and Hashes.

```ruby
#this is helpful when doing hashes for passwords
#strings are mutable where as symbols are not
:this_is_a_symbol
```

* Ruby is a pass by value language.

```Ruby
def inc(val)
  val += 1
end

a = 1
# calls the inc function with a
# 'val' is an independent variable with the same assignment as 'a'
inc a
puts a
```

* Ruby allows you to construct value objects.
