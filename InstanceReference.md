##  Instance reference name in data type (class)

#### C# (Sharp)
* C# uses this as the keyword to reference the current instance of a class.

```csharp
class Employee
        {
            private string name;
            private string alias;
            private decimal salary = 3000.00m;

            // Constructor:
            public Employee(string name, string alias)
            {
                // Use this to qualify the fields, name and alias:
                this.name = name;
                this.alias = alias;
            }
          }
```

#### Ruby
* Ruby uses self as the keyword to reference the current instance of a class

```Ruby
class Hello
  # We are inside the body of the class, so `self`
  # refers to the current instance of `Class`
  p self

  def foo
    # We are inside an instance method, so `self`
    # refers to the current instance of `Hello`
    return self
  end

  # This defines a class method, since `self` refers to `Hello`
  def self.bar
    return self
  end
end

```
