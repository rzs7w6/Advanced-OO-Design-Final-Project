# What is the implementation of listeners and event handlers?

## C# (sharp)

* [MSDN](https://msdn.microsoft.com/en-us/library/system.diagnostics.tracing.eventlistener(v=vs.110).aspx) shows the details of the Event Listener class in C#.

* The example below from MSDN shows the entire process of creating events and subscribing to them with event listeners.  The main way that this is done is by creating a handler, and a listener which work together to deal with events.

```csharp
using System;
namespace MyCollections 
{
   using System.Collections;

   // A delegate type for hooking up change notifications.
   public delegate void ChangedEventHandler(object sender, EventArgs e);

   // A class that works just like ArrayList, but sends event
   // notifications whenever the list changes.
   public class ListWithChangedEvent: ArrayList 
   {
      // An event that clients can use to be notified whenever the
      // elements of the list change.
      public event ChangedEventHandler Changed;

      // Invoke the Changed event; called whenever list changes
      protected virtual void OnChanged(EventArgs e) 
      {
         if (Changed != null)
            Changed(this, e);
      }

      // Override some of the methods that can change the list;
      // invoke event after each
      public override int Add(object value) 
      {
         int i = base.Add(value);
         OnChanged(EventArgs.Empty);
         return i;
      }

      public override void Clear() 
      {
         base.Clear();
         OnChanged(EventArgs.Empty);
      }

      public override object this[int index] 
      {
         set 
         {
            base[index] = value;
            OnChanged(EventArgs.Empty);
         }
      }
   }
}

namespace TestEvents 
{
   using MyCollections;

   class EventListener 
   {
      private ListWithChangedEvent List;

      public EventListener(ListWithChangedEvent list) 
      {
         List = list;
         // Add "ListChanged" to the Changed event on "List".
         List.Changed += new ChangedEventHandler(ListChanged);
      }

      // This will be called whenever the list changes.
      private void ListChanged(object sender, EventArgs e) 
      {
         Console.WriteLine("This is called when the event fires.");
      }

      public void Detach() 
      {
         // Detach the event and delete the list
         List.Changed -= new ChangedEventHandler(ListChanged);
         List = null;
      }
   }

   class Test 
   {
      // Test the ListWithChangedEvent class.
      public static void Main() 
      {
      // Create a new list.
      ListWithChangedEvent list = new ListWithChangedEvent();

      // Create a class that listens to the list's change event.
      EventListener listener = new EventListener(list);

      // Add and remove items from the list.
      list.Add("item 1");
      list.Clear();
      listener.Detach();
      }
   }
}
```

## Ruby

* This example from [StackOverflow](http://stackoverflow.com/questions/1912708/event-handling-in-ruby) shows how simple events can be created and raised using the unobservable namespace.
```ruby
require 'unobservable'

class Button
  include Unobservable::Support

  attr_event :clicked
  attr_event :double_clicked

  def click(x, y)
    raise_event(:clicked, x, y)
  end

  def double_click(x, y)
    raise_event(:double_clicked, x, y)
  end
end

button  = Button.new
button.clicked.register {|x, y| puts "You just clicked: #{x} #{y}"}

button.click(2, 3)
```
* Another example from [Stack Overflow](http://stackoverflow.com/questions/605169/how-to-do-events-in-ruby) shows how a simple event handler can be made:
```ruby
class EventHandlerArray < Array
  def add_handler(code=nil, &block)
    if(code)
      push(code)
    else
      push(block)
    end
  end
  def add
    raise "error"
  end
  def remove_handler(code)
    delete(code)
  end
  def fire(e)
    reverse_each { |handler| handler.call(e) }
  end
end
```
