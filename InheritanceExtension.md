# Inheritance and Extension

## C# (sharp)

* [MSDN](https://msdn.microsoft.com/en-us/library/ms173149.aspx) shows how C# implements extension with the ':' operator.
```csharp
public class ChangeRequest : WorkItem
        {
            protected int originalItemID { get; set; }

            // Constructors. Because neither constructor calls a base-class 
            // constructor explicitly, the default constructor in the base class
            // is called implicitly. The base class must contain a default 
            // constructor.

            // Default constructor for the derived class.
            public ChangeRequest() { }

            // Instance constructor that has four parameters.
            public ChangeRequest(string title, string desc, TimeSpan jobLen,
                                 int originalID)
            {
                // The following properties and the GetNexID method are inherited 
                // from WorkItem.
                this.ID = GetNextID();
                this.Title = title;
                this.Description = desc;
                this.jobLength = jobLen;

                // Property originalItemId is a member of ChangeRequest, but not 
                // of WorkItem.
                this.originalItemID = originalID;
            }
        }
```

* Extension in C# is done in a unique way as seen below.  This example is from [C-Sharp .Net Tutorials](http://csharp.net-tutorials.com/csharp-3.0/extension-methods/) 
```csharp
public static class MyExtensionMethods
{
    public static bool IsNumeric(this string s)
    {
        float output;
        return float.TryParse(s, out output);
    }
}
```

* It uses the 'this' key word in the passed variables to show that this is an extension.

## Ruby

* This example from [Rubyist](http://www.rubyist.net/~slagell/ruby/inheritance.html) shows how Inheritance can be used in Ruby with the '<' operator:
```ruby
class Mammal
    def breathe
        puts "inhale and exhale"
    end
end
 
class Cat<Mammal
    def speak
      puts "Meow"
    end
end
```

* This example from [Railstips](http://www.railstips.org/blog/archives/2009/05/15/include-vs-extend-in-ruby/) shows how Ruby implements extension with the extend keyword in the class:
```ruby
module Twitter
  class OAuth
    extend Forwardable
    def_delegators :access_token, :get, :post

    # a bunch of code removed for clarity
  end
end
```
