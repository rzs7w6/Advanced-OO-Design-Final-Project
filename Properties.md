##  Properties

#### C# (Sharp)
* In C# you can use the auto implemented properties or you can also build your own.

```csharp
  // This class is mutable. Its data can be modified from
  // outside the class.
  class Customer
  {
    // Auto-Impl Properties for trivial get and set
    public double TotalPurchases { get; set; }
    public string Name { get; set; }
    public int CustomerID { get; set; }

    // Constructor
    public Customer(double purchases, string name, int ID)
    {
        TotalPurchases = purchases;
        Name = name;
        CustomerID = ID;
    }
    // Methods
    public string GetContactInfo() {return "ContactInfo";}
    public string GetTransactionHistory() {return "History";}

  }

```
* This is an example of a  class with build your own getter and setters

```csharp
class TimePeriod
       {
           private double seconds;

           public double Hours
           {
               get { return seconds / 3600; }
               set { seconds = value * 3600; }
           }
       }

```

#### Ruby
* Getters and setters are built into ruby.

```Ruby
class Foo
  # This will automatically create your getters and setters for you.
  attr_accessor :bar, :baz
end
  # These methods will be created automatically from line  52
def bar
  @bar
end

def bar=(value)
  @bar = value
end

def baz
  @baz
end

def baz=(value)
  @baz = value
end

```
