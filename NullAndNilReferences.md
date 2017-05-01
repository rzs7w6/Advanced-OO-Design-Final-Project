
# Null/nil references?

## Which does the language use? (null/nil/etc)

### C# (sharp)

* [MSDN](https://msdn.microsoft.com/en-us/library/edakx9da.aspx) shows that C# uses null.

### Ruby

* Ruby--as can be see in [Ruby Docs](https://ruby-doc.org/core-2.2.0/NilClass.html)--uses nil instead of null.

* In fact, nil is actually an entire class in Ruby as can be seen in the documentation above.



## Does the language have features for handling null/nil references?

### C# (sharp)

* Below is an EXCELLENT example of all of the behaviors of null in C#.
```csharp
class Program
    {
        class MyClass
        {
            public void MyMethod() { }
        }

        static void Main(string[] args)
        {
            // Set a breakpoint here to see that mc = null.
            // However, the compiler considers it "unassigned."
            // and generates a compiler error if you try to
            // use the variable.
            MyClass mc;

            // Now the variable can be used, but...
            mc = null;

            // ... a method call on a null object raises 
            // a run-time NullReferenceException.
            // Uncomment the following line to see for yourself.
            // mc.MyMethod();

            // Now mc has a value.
            mc = new MyClass();

            // You can call its method.
            mc.MyMethod();

            // Set mc to null again. The object it referenced
            // is no longer accessible and can now be garbage-collected.
            mc = null;

            // A null string is not the same as an empty string.
            string s = null;
            string t = String.Empty; // Logically the same as ""
            
            // Equals applied to any null object returns false.
            bool b = (t.Equals(s));
            Console.WriteLine(b);

            // Equality operator also returns false when one
            // operand is null.
            Console.WriteLine("Empty string {0} null string", s == t ? "equals": "does not equal");

            // Returns true.
            Console.WriteLine("null == null is {0}", null == null);


            // A value type cannot be null
            // int i = null; // Compiler error!

            // Use a nullable value type instead:
            int? i = null;

            // Keep the console window open in debug mode.
            System.Console.WriteLine("Press any key to exit.");
            System.Console.ReadKey();

        }
    }
```

### Ruby

* This documentation from [Ruby Docs](https://ruby-doc.org/core-2.2.0/NilClass.html) shows the behaviors and return values of the nil class.

```
false & obj → false
nil & obj → false
And—Returns false. obj is always evaluated as it is the argument to a method call—there is no short-circuit evaluation in this case.

false ^ obj → true or false
nil ^ obj → true or false
Exclusive Or—If obj is nil or false, returns false; otherwise, returns true.

inspect → "nil"
Always returns the string “nil”.

nil? → true
Only the object nil responds true to nil?.

rationalize([eps]) → (0/1)
Returns zero as a rational. The optional argument eps is always ignored.

to_a → []
Always returns an empty array.

nil.to_a   #=> []
to_c → (0+0i)
Returns zero as a complex.

to_f → 0.0
Always returns zero.

nil.to_f   #=> 0.0
to_h → {}
Always returns an empty hash.

nil.to_h   #=> {}
to_i → 0
Always returns zero.

nil.to_i   #=> 0
to_r → (0/1)
Returns zero as a rational.

to_s → ""
Always returns the empty string.

false | obj → true or false
nil | obj → true or false
Or—Returns false if obj is nil or false; true otherwise.
```
