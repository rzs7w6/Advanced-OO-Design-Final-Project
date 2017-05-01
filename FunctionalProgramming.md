# Do the languages support Functional Programming?

## C# (sharp)

* The article at [MSDN](https://msdn.microsoft.com/en-us/library/hh297108(v=vs.100).aspx) is a reference to an entire book detailing functional programming in C#

* Functional programming in C# is completely supported, although it is not the primary paradigm in which C# is normally written.  Some examples from [Code Project](https://www.codeproject.com/Articles/375166/Functional-programming-in-Csharp) of what this look like in code are:
```csharp
MyFunction f = Math.Sin;
double y = f(4); //y=sin(4)
f = Math.Exp;
y = f(4); //y=exp(4) 
```
```csharp
Predicate<string> isEmptyString = String.IsNullOrEmpty;
if (isEmptyString("Test"))
{
    throw new Exception("'Test' cannot be empty");
}
```

## Ruby

* [StackOverflow](http://stackoverflow.com/questions/159797/is-ruby-a-functional-language) states that "Ruby is a multi-paradigm language that supports a functional style of programming."  What this means is that while Ruby is primarily an Object Oriented programming language, it does allow for functional programming practices to be used.  In this was, it does in fact support functional programming, like C#.

* Some examples from [Site Point](https://www.sitepoint.com/functional-programming-techniques-with-ruby-part-i/) of this are:
```ruby
def module_split(module_path, separator = "::")
  modules = module_path.split(separator)
  modules.length.downto(1).map { |n| modules.first(n).join(separator) }
end

module_split("W::X::Y::Z")
```
* This Code block shows an example of side-effect free programming
```ruby
class CssBlock
  attr_reader :selector, :properties

  def initialize(selector, properties = {})
    @selector = selector.dup.freeze
    @properties = properties.dup.freeze
  end

  def set(key, value = nil)
    new_properties = if key.is_a?(Hash)
        key
      elsif !value.nil?
        {
          key => value
        }
      else
        raise "Either provide a Hash of values, or a key and value."
      end

    self.class.new(self.selector, self.properties.merge(new_properties))
  end

  def to_s
    serialised_properties = self.properties.inject([]) do |acc, (k, v)|
      acc + ["#{k}: #{v}"]
    end

    "#{self.selector} { #{serialised_properties.join("; ") } }"
  end
end
```
