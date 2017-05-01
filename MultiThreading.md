# Multi Threading

## C# (sharp)

* C# supports Multi Threading through the System.Threading Namespace.  This can be seen at [MSDN](https://msdn.microsoft.com/en-us/library/system.threading(v=vs.110).aspx).

* Threads in C# are unique when considered against languages such as Java in that the Dispatcher that controls the threads can be passed around as a variable and used locally rather than globally.
```
private void OnSaveCompleted(IAsyncResult result)
    {
        Dispatcher.BeginInvoke(() =>
        {
            context.EndSaveChanges(result);
        });
    }
```

* This example shows Threads being created and ran.
```
using System.Threading;
 
namespace ThreadTest
{
    class Program
    {
        static voidMain(string[] args)
        {
            //Creating thread object to strat it
            Thread th= newThread(ThreadB);
            Console.WriteLine("Threads started :");
            // Start thread B
            th.Start();
            //Thread A executes 10 times
            for (inti=0; i<10; i++)
            {
                Console.WriteLine("Thread : A");
            }
           
            Console.WriteLine("Threads completed");
            Console.ReadKey();
        }
        public staticvoidThreadB()
        {
           //Executes thread B 10 times
          for(inti=0;i<10;i++)
          {
             Console.WriteLine("Thread : B");
          }
        }
    }
}
```

## Ruby

* The [Ruby Documentation](https://ruby-doc.org/core-2.2.0/Thread.html) shows that Threads exist in a Thread Class.  

* This example is a Thread being created:
```
thr = Thread.new { puts "Whats the big deal" }
```
* This example is handling multiple threads in an array:
```
threads = []
threads << Thread.new { puts "Whats the big deal" }
threads << Thread.new { 3.times { puts "Threads are fun!" } }
...
threads.each { |thr| thr.join }
```
* Thread states can be handled by functions of the Thread object:
```
thr = Thread.new { sleep }
thr.status # => "sleep"
thr.exit
thr.status # => false
```

