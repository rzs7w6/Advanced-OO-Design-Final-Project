# Reflection

## What reflection abilities are supported and how are they used?

### C# (sharp)

* [Tutorials Point](https://www.tutorialspoint.com/csharp/csharp_reflection.htm) gives a good tutorial in how reflection works in C#.  It states that "Reflection objects are used for obtaining type information at runtime. The classes that give access to the metadata of a running program are in the System.Reflection namespace."

* This example from the same site shows reflection in C#
```csharp
using System;

[AttributeUsage(AttributeTargets.All)]
public class HelpAttribute : System.Attribute
{
   public readonly string Url;
   
   public string Topic   // Topic is a named parameter
   {
      get
      {
         return topic;
      }
      set
      {
         topic = value;
      }
   }
   
   public HelpAttribute(string url)   // url is a positional parameter
   {
      this.Url = url;
   }
   private string topic;
}

[HelpAttribute("Information on the class MyClass")]
class MyClass
{
}
namespace AttributeAppl
{
   class Program
   {
      static void Main(string[] args)
      {
         System.Reflection.MemberInfo info = typeof(MyClass);
         object[] attributes = info.GetCustomAttributes(true);
         for (int i = 0; i < attributes.Length; i++)
         {
            System.Console.WriteLine(attributes[i]);
         }
         
         Console.ReadKey();
      }
   }
}
```
### Ruby

* [Ruby Metaprogramming](http://ruby-metaprogramming.rubylearning.com/html/ruby_metaprogramming_2.html) states the following about Reflection: "In Ruby it's possible to read information about a class or object at runtime. We could use some of the methods like class(), instance_methods(), instance_variables() to do that."

* The example below shows this:
```ruby
# The code in the following class definition is executed immediately
class Rubyist
  # the code in the following method definition is executed later,
  # when you eventually call the method
  def what_does_he_do
    @person = 'A Rubyist'
    'Ruby programming'
  end
end
an_object = Rubyist.new
puts an_object.class # => Rubyist
puts an_object.class.instance_methods(false) # => what_does_he_do
an_object.what_does_he_do
puts an_object.instance_variables # => @person
```
