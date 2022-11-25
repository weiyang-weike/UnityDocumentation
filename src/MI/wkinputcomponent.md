
## WkInputComponent

A Class that's attached to Player Responsible for all the inputs related stuff

### Constructor

CTOR

### Constructor(actionProfile, inputProfile)

CTOR with profiles

| Name | Description |
| ---- | ----------- |
| actionProfile | *Weike.MachineInterface.Action.WeikeActionProfile*<br>Action Profile |
| inputProfile | *Weike.MachineInterface.Input.WkInputProfile*<br>Input Profile |

### AddActionProfile(key, action)

Add Action Profile

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br>Action Key |
| action | *Weike.MachineInterface.Action.WkAction*<br>Action |

### AddInputProfile(actionKey, eventType, parameters)

Add Input Profile

| Name | Description |
| ---- | ----------- |
| actionKey | *System.String*<br>Action Key |
| eventType | *System.Type*<br>Event Type |
| parameters | *System.Object[]*<br>Constructor Params |

### GetRegisteredCalls

There could be more Registration During OnEvent and cause some errors because of iterating and adding at the same time. Using this as a recursive function method

#### Returns



### InvokeAction(key, parameters)

Invoke action from Action Profile

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br>Action Keys |
| parameters | *System.Object[]*<br> |

### OnEvent(e)

On event function Invoke by Input Manager

| Name | Description |
| ---- | ----------- |
| e | *Weike.MachineInterface.Interface.IWkEvent*<br> |

### RegisterCallbacks\`\`1(callBackFunc)

Register Input according to the type passed in. Each Input component can only register each type of event.

#### Type Parameters

- T - 

| Name | Description |
| ---- | ----------- |
| callBackFunc | *System.Action{Weike.MachineInterface.Event.WkEvent}*<br> |

### RemoveAction(key, action)

Remove Action

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br>Action Key |
| action | *Weike.MachineInterface.Action.WkAction*<br>Action |

### RemoveActionByType(key, type)

Remove Action By Type

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br>Action Key |
| type | *System.Type*<br>Action Type |

### RemoveActionByType\`\`1(key)

Remove Action By Type Generic

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br>Action Key |

#### Type Parameters

- T - Generic Type

### RemoveAllActions

Remove All Actions

### RemoveAllActionsByKey(key)

Remove All Action by Key

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br> |

### RemoveInputProfile(eventType, parameters)

Remove Input Profile

| Name | Description |
| ---- | ----------- |
| eventType | *System.Type*<br>Event Type |
| parameters | *System.Object[]*<br>Constructor Params |

### SetActionProfile(actionProfile)

Set Action Profile

| Name | Description |
| ---- | ----------- |
| actionProfile | *Weike.MachineInterface.Action.WeikeActionProfile*<br>Action Profile |

### SetInputProfile(inputProfile)

Set Input Profile

| Name | Description |
| ---- | ----------- |
| inputProfile | *Weike.MachineInterface.Input.WkInputProfile*<br>Input Profile |

### SetProfiles(actionProfile, inputProfile)

Set Input and Action Profile

| Name | Description |
| ---- | ----------- |
| actionProfile | *Weike.MachineInterface.Action.WeikeActionProfile*<br>Action Profile |
| inputProfile | *Weike.MachineInterface.Input.WkInputProfile*<br>Input Profile |

