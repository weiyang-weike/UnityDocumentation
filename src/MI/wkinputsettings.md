
## WkInputSettings

Responsible of Creating a struct of Type and Parameter of Weike Events

### Constructor(inputEvents, parameters)



| Name | Description |
| ---- | ----------- |
| inputEvents | *System.Type*<br> |
| parameters | *System.Object[]*<br> |

### Equals(System.Object)

### Equals(other)

Equals with type

| Name | Description |
| ---- | ----------- |
| other | *System.Type*<br> |

#### Returns



### Equals(Weike.MachineInterface.Input.WkInputSettings)

### GetHashCode



#### Returns



### inputEvents

Type of Input WkEvents

### op_Equality(lhs, rhs)

Equal Operator

| Name | Description |
| ---- | ----------- |
| lhs | *Weike.MachineInterface.Input.WkInputSettings*<br>left hand side |
| rhs | *Weike.MachineInterface.Input.WkInputSettings*<br>right hand side |

#### Returns



### op_Inequality(lhs, rhs)

Not Equal Opeartor

| Name | Description |
| ---- | ----------- |
| lhs | *Weike.MachineInterface.Input.WkInputSettings*<br>left hand side |
| rhs | *Weike.MachineInterface.Input.WkInputSettings*<br>right hand side |

#### Returns



### parameters

Constructor Parameter


## IWkController

WK Controller

### AddAction(key, newAction)

Add Action

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br>Action Key |
| newAction | *Weike.MachineInterface.Action.WkAction*<br>New Action |

### inputComponent

Input Component

### inputComponentType

Component Type

### isActivated

Is Current Activated

### RemoveAction(key, typeOfAction)

Remove Action

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br>Action Key |
| typeOfAction | *System.Type*<br>Type |

### RemoveAction\`\`1(key)

Remove Action

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br>Action Key |

#### Type Parameters

- T - Type

### RemoveAllActions

Remove all Actions

### RemoveAllActionsByKey(key)

Remove All Actions By Key

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br> |

