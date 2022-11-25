
## WkInputManager

Responsible of keeping track of all the Input Components Update loop will be called by Machine Instance If possible I want to make this a Wrapper for all the Input Devices instead of directly interacting with them.

### Constructor(machineContext, eventManagerType)

CTOR

| Name | Description |
| ---- | ----------- |
| machineContext | *Weike.MachineInterface.Interface.IWkMachineContext*<br>Machine Context |
| eventManagerType | *System.Type*<br>Event Manager Type |

### Constructor(machineContext)

CTOR

| Name | Description |
| ---- | ----------- |
| machineContext | *Weike.MachineInterface.Interface.IWkMachineContext*<br> |

### Finalize

Destructor

### GetActivatedControllers

Iterator for Controllers. There might be more controllers coming in during iteration so it's best to do this

#### Returns



### instance

Static Instance

### RegisterController(component)

Register Controller

| Name | Description |
| ---- | ----------- |
| component | *Weike.MachineInterface.Input.WkController*<br>Input Component |

### Update

Update Event Called By MachineInstance

