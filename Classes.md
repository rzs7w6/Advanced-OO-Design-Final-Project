## Classes

#### C# (Sharp)

* Defining a Class/ creating an object

```csharp

using System;
namespace BoxApplication
{
   class Box
   {
      private double length {get; set};   // Length of a box
      private double breadth {get; set};  // Breadth of a box
      private double height {get; set};   // Height of a box

   }

   class Boxtester
   {

      static void Main(string[] args)
      {
         Box Box1 = new Box();   // Declare Box1 of type Box
         Box Box2 = new Box();
      }

   }
}
```

* Objects are "de-initialized" by the C# Garbage collector running when .NET realizes it needs more memory.

#### Ruby
* Defining a Class
  * def creates methods in a class
  * Creating new instances is very simplistic
  * Ruby is read linear outside of classes, so the first thing actually run is the creation of the new object based on the class above

```ruby
class Sample
   def hello
      puts "Hello Ruby!"
   end
end

object = Sample.new
object.hello
```

* Objects are removed via the garbage collector, the exact same way as C#.  Both of these I don't like because I feel you need more control as a programmer. 
