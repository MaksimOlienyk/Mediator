# Mediator - Патерн Проєктування

Патерн Mediator дозволяє організувати взаємодію між об'єктами через посередника, щоб вони не взаємодіяли напряму.  
Це зменшує залежність між компонентами та спрощує їх взаємозамінність.

## Ідея

Замість того, щоб компоненти напряму викликали один одного, вони відправляють повідомлення через посередника.  
Посередник визначає, як і куди передати повідомлення.

## Структура

| Елемент     | Опис |
|------------|------|
| `Mediator` | Керує комунікацією між компонентами |
| `Component` | Взаємодіє з іншими лише через медіатора |
| Клієнт     | Створює компоненти та передає їм медіатора |

## Код

```csharp
class Mediator {
    public void Notify(string sender, string msg) =>
        Console.WriteLine($"{sender} -> {msg}");
}

class Component {
    private Mediator _mediator;
    private string _name;

    public Component(Mediator m, string name) {
        _mediator = m;
        _name = name;
    }

    public void Send(string msg) => _mediator.Notify(_name, msg);
}

class Program {
    static void Main() {
        var m = new Mediator();
        var c1 = new Component(m, "A");
        var c2 = new Component(m, "B");

        c1.Send("Hello");
        c2.Send("Hi");
    }
}

