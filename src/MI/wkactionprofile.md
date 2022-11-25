
## WeikeActionProfile

Action profile. Determine which key to bind to a HashSet of Actions to Invokes.

### AddAction(key, action)

Add Action into HashSet

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br> |
| action | *Weike.MachineInterface.Action.WkAction*<br> |

### GetActions

Return all Actions

#### Returns



### GetActionsFromKey(key)

Return all Actions from Key

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br> |

#### Returns



### InvokeActions(key, parameters)

Invoke actions

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br> |
| parameters | *System.Object[]*<br> |

### RemoveAction(key, action)

Remove action from key and action reference

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br> |
| action | *Weike.MachineInterface.Action.WkAction*<br> |

### RemoveAction(action)

From action from reference

| Name | Description |
| ---- | ----------- |
| action | *Weike.MachineInterface.Action.WkAction*<br> |

### RemoveActionByType(key, actionType)

Remove action by type.

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br> |
| actionType | *System.Type*<br> |

### RemoveAllAction

Remove All Actions

### RemoveAllActionByKey(key)

Remove All Actions By Key

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br> |
