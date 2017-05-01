# Singletons

## How is a singleton implemented?

### C# (sharp)

[MSDN](https://msdn.microsoft.com/en-us/library/ff650316.aspx) shows how a singleton can be implemented in C#:
```csharp
using System;

public class Singleton
{
   private static Singleton instance;

   private Singleton() {}

   public static Singleton Instance
   {
      get 
      {
         if (instance == null)
         {
            instance = new Singleton();
         }
         return instance;
      }
   }
}
```

### Ruby

* [Ruby Docs](https://ruby-doc.org/stdlib-1.9.3/libdoc/singleton/rdoc/Singleton.html) shows how a singleton can be implemented in Ruby:
```ruby
require 'singleton'

class Example
  include Singleton
  attr_accessor :keep, :strip
  def _dump(depth)
    # this strips the @strip information from the instance
    Marshal.dump(@keep, depth)
  end

  def self._load(str)
    instance.keep = Marshal.load(str)
    instance
  end
end

a = Example.instance
a.keep = "keep this"
a.strip = "get rid of this"
a.taint

stored_state = Marshal.dump(a)

a.keep = nil
a.strip = nil
b = Marshal.load(stored_state)
p a == b  #  => true
p a.keep  #  => "keep this"
p a.strip #  => nil
```

## Can it be made thread-safe?

### C# (sharp)

* The example above for creating a C# singleton is not Thread Safe.

* This example shows how a thread safe Singleton can be created as follows:

* MSDN says that: "Various approaches solve this problem. One approach is to use an idiom referred to as Double-Check Locking [Lea99]. However, C# in combination with the common language runtime provides a static initialization approach, which circumvents these issues without requiring the developer to explicitly code for thread safety."

* This example uses Static Initialization as discussed above:
```csharp
public sealed class Singleton
{
   private static readonly Singleton instance = new Singleton();
   
   private Singleton(){}

   public static Singleton Instance
   {
      get 
      {
         return instance; 
      }
   }
}
```

### Ruby

* This example from [Stack Overflow](http://stackoverflow.com/questions/6943691/do-singleton-classes-create-problems-in-a-multi-threaded-app) shows how a Thread Safe Singleton can be made:
```ruby
require 'singleton'

class MyObject
  include Singleton

  def initialize
    @things = []
    @mutex  = Mutex.new
  end

  def add(thing)
    with_mutex { @things << thing }   
  end

  def things
    with_mutex { @things }
  end

  def clear
    with_mutex { @things.clear }
  end

  def self.add(thing)
    instance.add(thing)
  end

  def self.things
    instance.things
  end

  def self.clear
    instance.clear
  end

  private

  def with_mutex
    @mutex.synchronize { yield }
  end
end
```

## Can the singleton instance be lazily instantiated?

### C# (sharp)

* An admin from [Geeks with Blogs](http://geekswithblogs.net/BlackRabbitCoder/archive/2010/05/19/c-system.lazylttgt-and-the-singleton-design-pattern.aspx) shows one implementation of a Lazy Singleton in C#.  This takes advantage of the .Net 4.0 Lazy type which allows for easy Laziness.
```csharp
   1: public class LazySingleton3
   2: {
   3:     // static holder for instance, need to use lambda to construct since constructor private
   4:     private static readonly Lazy<LazySingleton3> _instance
   5:         = new Lazy<LazySingleton3>(() => new LazySingleton3());
   6:  
   7:     // private to prevent direct instantiation.
   8:     private LazySingleton3()
   9:     {
  10:     }
  11:  
  12:     // accessor for instance
  13:     public static LazySingleton3 Instance
  14:     {
  15:         get
  16:         {
  17:             return _instance.Value;
  18:         }
  19:     }
  20: }
```

### Ruby

* My boy Dalibor Nasevic from [dalibornasevic.com](http://dalibornasevic.com/posts/9-ruby-singleton-pattern) goes in depth in Ruby Singletons.  He provides an example for how Ruby deals with lazy instantiation

* "Ruby Singleton module does lazy instantiation (creates instance from Logger class at the moment when we call Logger.instance method) and not during load time."

```ruby
class Logger
  def initialize
    @log = File.open("log.txt", "a")
  end

  @@instance = Logger.new

  def self.instance
    return @@instance
  end

  def log(msg)
    @log.puts(msg)
  end

  private_class_method :new
end

Logger.instance.log('message 1')
```
