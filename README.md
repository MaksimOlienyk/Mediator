# Mediator
```cs
class Mediator {
    public void Notify(string sender,string msg)=>Console.WriteLine($"{sender} -> {msg}");
}

class Component {
    private Mediator _mediator; private string _name;
    public Component(Mediator m,string name){_mediator=m;_name=name;}
    public void Send(string msg)=>_mediator.Notify(_name,msg);
}

class Program {
    static void Main(){
        var m=new Mediator();
        var c1=new Component(m,"A"); var c2=new Component(m,"B");
        c1.Send("Hello"); c2.Send("Hi");
    }
}
