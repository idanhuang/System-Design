```C#
using System;
namespace Learning.EventHandler
{
    public class Sender
    {
        // define a delegate which points a list of methods with same signature.
        public delegate void MetrologyDataParsedHandler(object sender, string er);

        // define an event that encapsulates the delegate.
        public event MetrologyDataParsedHandler OnMetrologyDataParsed;
      
        public void ProcessMetrologyData(object sender, string er)
        {
            Console.WriteLine("Sender completes parsing metrology data...");
            // Complete parsing metrology data
            TriggerMetrologyDataParsed(sender, er);
        }

        // raise the event
        public void TriggerMetrologyDataParsed(object sender, string er)
        {
            OnMetrologyDataParsed?.Invoke(sender, er);
        }
    }

    public class Receiver
    {
        public Sender sender;
        public Receiver(Sender sender)
        {
            this.sender = sender;
            Register();
        }
   
        public void Register()
        {
            // In order to receive notifications when event occurs, event handler method must subscribe to the event.
            sender.OnMetrologyDataParsed += OnMetrologyDataParsed;
        }

        // Event Handler. sigature should match the signature of the delegate for the event.
        private void OnMetrologyDataParsed(object sender, string er)
        {
            // Perform actoins when event is raised
            Console.WriteLine("Receiver handles MetrologyDataParsed event");
        }
    }

    public class Test
    { 
        static void Main(string[] args)
        {
            Sender sender = new Sender();
            Receiver receiver = new Receiver(sender);
            sender.ProcessMetrologyData(sender, "er");
        }
    }
}
```
