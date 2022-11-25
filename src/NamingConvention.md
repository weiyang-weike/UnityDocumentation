# Naming Convention

Weike's Naming Convention. 

---

## Notation 
- PascalCase – First character of all word is in upper case and other characters are in lower case. 
    - Example: HelloWorld
- camelCase – The first character of all words, except the first word, is upper case and other characters are lower case. 
    - Example: helloWorld

---


| Object Name | Notation |
| ---- | ----------- |
| Namespace | PascalCase |
| Class Name | PascalCase |
| Constructor name | PascalCase |
| Method Name | PascalCase |
| Method arguments | camelCase |
| Local Variable | camelCase |
| Constants Name | PascalCase |
| Field Name | camelCase |
| Properties Name | PascalCase |
| Delegate name | PascalCase |
| Enum Type | PascalCase |

---

## Class Names

Example of class name and method name in PascalCase notation

```cs
public class WkReelManager
{
  public void InitReel()
  {
    //...
  }
  public void StartSpin()
  {
    //...
  }
}
```

---

## Variable Names
Example of method arguments and local variables in camelCase notation
```cs
public class Reel
{
  public int ClampToReelLength(int reelStop)
  {
    int clamped = reelStop;
    // ...
  }
}
```

---

## Identifiers
Do not use Hungarian notation or any other type identification in identifiers.

```cs
// Correct
int clamped;
string name;    
// Avoid
int iClamped;
string strName;
```

---

## Constants
Do not use Screaming Caps for constants or readonly variables.

```cs
// Correct
public Vector3 iconSize;
public SymbolInfo symbolInfo;    
// Avoid
public Vector3 icon_Size;
public SymbolInfo symbol_Info;    
// Exception (Class field)
private ReelStrips _reelStrip;
```

---

## Type Names
Do use predefined type names (C# aliases) like int, float, string for local, parameter and member declarations. Do use .NET Framework names like Int32, Single, String when accessing the type's static members like Int32.TryParse or String.Join.
```cs
// Correct
string firstName;
int lastIndex;
bool isSaved;
string commaSeparatedNames = String.Join(", ", names);
int index = Int32.Parse(input);
// Avoid
String firstName;
Int32 lastIndex;
Boolean isSaved;
string commaSeparatedNames = string.Join(", ", names);
int index = int.Parse(input);
```

---

## Implicit Types
Do use implicit type var for local variable declarations. Exception: primitive types (int, string, double, etc) use predefined names.
```cs
var reelComponent = Reel.GetComponent<Reel>();
var temp = new List<byte>();
// Exceptions
int index = 100;
string[] indices;
bool success = false;
```

---

## Noun Class Names
Do use noun or noun phrases to name a class.

---

## Interfaces

Do prefix interfaces with the letter I. Interface names are noun (phrases) or adjectives.

```cs
public interface IState
{
}
```

---

## Alignment

Do vertically align curly brackets.
```cs
// Correct
class Program
{
  static void Main(string[] args)
  {
    //...
  }
}
```

---

## Member Variables

Do declare all member variables at the top of a class, with static variables at the very top.

```cs
// Correct
public class GameManager
{
  public static GameManager instance;
  public Int64 betAmt { get; set; }
  // Constructor
  public GameManager ()
  {
    // ...
  }
}
```

---

## Enums

1. Do use singular names for enums. Exception: bit field enums.
1. Do not use an "Enum" suffix in enum type names.
1. Do not use "Flag" or "Flags" suffixes in enum type names.


---

## Event Method Names
Do use suffix EventArgs at creation of the new classes comprising the information on event.

```cs
// Correct
public class ConnectedEventArgs : System.EventArgs
{
}
```

Do name event handlers (delegates used as types of events) with the "EventHandler" suffix.

```cs
public delegate void ConnectedEventHandler(object sender, ConnectedEventArgs e);
```

Do use two parameters named sender and e in event handlers. The sender parameter represents the object that raised the event. The sender parameter is typically of type object, even if it is possible to employ a more specific type.

```cs
public void ConnectedEventHandler(object sender, ConnectedEventArgs e)
{
  //...
}
```

---

## Exception Names

Do use suffix Exception at creation of the new classes comprising the information on exception.

```cs
// Correct
public class ConnectedException : System.Exception
{
}
```

Do use prefix Any, Is, Have or similar keywords for boolean identifier.

```cs
// Correct
public static bool IsNullOrEmpty(string value) 
{
    return (value == null || value.Length == 0);
}
```

When working with static fields that are private or internal, use the s_ prefix and for thread static use t_.

```cs
public class DataService
{
    private static IWorkerQueue s_workerQueue;

    [ThreadStatic]
    private static TimeSpan t_timeSpan;
}
```

---

## Static members

Call static members by using the class name: ClassName.StaticMember. This practice makes code more readable by making static access clear. Don't qualify a static member defined in a base class with the name of a derived class. While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.

---

## Private Static and Private Thread

When working with static fields that are private or internal, use the s_ prefix and for thread static use t_.

```cs
public class DataService
{
    private static IWorkerQueue s_workerQueue;

    [ThreadStatic]
    private static TimeSpan t_timeSpan;
}
```

---

## Type Casting 

use C# as and is operator for casting none primitive type eg. int, string, float, double. 

```cs
public class KirinGameManager : WkGameManager 
{
    KirinGameManager()
    {
        KirinReelManager kirinReelManager = reel[0] as KirinReelManager;
    }
}
```

---

## Language guidelines

The following sections describe practices that the C# team follows to prepare code examples and samples.

### String data type

Use string interpolation to concatenate short strings, as shown in the following code.

```cs
string displayName = $"{nameList[n].LastName}, {nameList[n].FirstName}";
```

To append strings in loops, especially when you're working with large amounts of text, use a StringBuilder object.

```cs 
var phrase = "lalalalalalalalalalalalalalalalalalalalalalalalalalalalalala";
var manyPhrases = new StringBuilder();
for (var i = 0; i < 10000; i++)
{
    manyPhrases.Append(phrase);
}
//Debug.Log("tra" + manyPhrases);
```

---

## Unsigned data types

In general, use int rather than unsigned types. The use of int is common throughout C#, and it is easier to interact with other libraries when you use int.

---

## Event handling

If you're defining an event handler that you don't need to remove later, use a lambda expression.

```cs
public WkButton()
{
    this.Click += (s, e) =>
        {
            WkMouseEvent mouseEvent = e as WkMouseEvent;
            if(mouseEvent == null) return;
            Debug.Log(mouseEvent.Location.ToString());
        };
}
```

---

## Input Profile 

Prefix it with Cmd_{Name}. @Name define it with PascalCamelCasing.

```cs 
public void TryStartSpin()
{
    gameState!.fsm!.AddInputAtomAndRunState("Cmd_Spin");
}
```

---

## Action Profile 

Prefix it with Key_{Name}. @Name define it with PascalCamelCasing.

```cs 
public void TryStartSpin()
public override void EnterState()
{
    base.EnterState();
    if(gameManager is WkSlotGameManager slotGameManager)
    {
        slotGameManager.StartBet();
    }
    
    playerController!.AddAction("Key_Spin", new WkSpinAction(playerController));
}
```
