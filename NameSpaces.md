## Namespaces

#### C# (Sharp)

```csharp
namespace namespace_name
{
   //This is how you declare a namespace
}
```
  * Anything classes inside of the namespace can be reached via: <i>namespace.class</i>

```csharp
//This allows us to use ANYTHING inside of the system namespace
using System;
/*Console class is located in the System Namespace.
  By stating we are using the system namespace, we no longer need to say System.Console,
  we can just say Console.blah to access things in the console namespace.
*/

namespace space_one
{
  class namespace_example
  {
     public void function()
     {
        Console.WriteLine("Inside First Namespace");
     }
  }
}

namespace space_two
{
  class namespace_example
  {
     public void function()
     {
        Console.WriteLine("Inside Second NameSpace");
     }
  }
}

class TestClass
{

  static void Main(string[] args)
  {
    //Create new class referring to the first space
     space_one.namespace_cl fc = new space_one.namespace_cl();

     //Create new class referring to the second space
     space_two.namespace_cl sc = new space_two.namespace_cl();

     //Invoke namespace one's function
     fc.func();

     //Invoke namespace two's function
     sc.func();

  }

}
```

* Namespaces are used in order to separate Classes.  For example, if a programmer wanted to create a class called Console, they wouldn't be able to do so as it already exists in the System namespace.  By creating a separate namespace, the compiler won't confuse the two.

<hr>

#### Ruby

* Namespaces are well, not really a thing in Ruby.  Instead they use very similar practice called modules.

```Ruby
module Week
   FIRST_DAY = "Sunday"
   def Week.weeks_in_month
      puts "You have four weeks in a month"
   end
   def Week.weeks_in_year
      puts "You have 52 weeks in a year"
   end
end
```

* We are creating a module (Equivalent to C#'s Namespace) that is "Week". Within week we have two methods that are defined in that module that can be called.

* I am a much larger fan of C#'s namespaces than ruby's modules.  I don't feel the separation is very prominent within the modules. I believe it blends together without being separated by the curly braces.  Although it is much more compact which can be nice on the eyes.  I'm torn.
