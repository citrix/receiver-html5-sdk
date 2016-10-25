# Sample code for product

A quick introduction of this example

## Requirements

What is required to run the code, any prerequisite for developers to pay attention.

    Notes for requirements area

<br>
## Setup steps

What steps need to performed so as to run the code

    Notes for requirements area

You need to follow those Configuration so as to get things done.
<br>
## Code snipets

```java
public class TownCrier
    {
        readonly Timer _timer;
        public TownCrier()
        {
            _timer = new Timer(1000) {AutoReset = true};
            _timer.Elapsed += (sender, eventArgs) => Console.WriteLine("It is {0} and all is well", DateTime.Now);
        }
        public void Start() { _timer.Start(); }
        public void Stop() { _timer.Stop(); }
    }

    public class Program
    {
        public static void Main()
        {
            HostFactory.Run(x =>                                 //1
            {
                x.Service<TownCrier>(s =>                        //2
                {
                   s.ConstructUsing(name=> new TownCrier());     //3
                   s.WhenStarted(tc => tc.Start());              //4
                   s.WhenStopped(tc => tc.Stop());               //5
                });
                x.RunAsLocalSystem();                            //6

                x.SetDescription("Sample Topshelf Host");        //7
                x.SetDisplayName("Stuff");                       //8
                x.SetServiceName("Stuff");                       //9
            });                                                  //10
        }
    }
```

This code is aslo available at [github](http://example.com/).
<br>
##Code structure
Describe the code structure if you want

Source file  | Generated HTML       | use_directory_urls=true  | use_directory_urls=false
------------ | -------------------- | ------------------------ | ------------------------
index.md     | index.html           | /                        | /index.html
api-guide.md | api-guide/index.html | /api-guide/              | /api-guide/index.html
about.md     | about/index.html     | /about/                  | /about/index.html
<br>
##Notes
You can add more notes to explain

> *  Here we are setting up the host using the HostFactory.Run  the runner. We open up a new lambda where the ‘x’ in this case exposes all of the host level configuration. Using this approach the command arguments are extracted from environment variables.
> *  Here we are telling Topshelf that there is a service of type ‘TownCrier”. The lambda that gets opened here is exposing the service configuration options through the ‘s’ parameter.
> *  This tells Topshelf how to build an instance of the service. Currently we are just going to ‘new it up’ but we could just as easily pull it from an IoC container with some code that would look something like ‘container.GetInstance<TownCrier>()’

!!! note "Note:"
    You can also highlight your notes in colorful block.



