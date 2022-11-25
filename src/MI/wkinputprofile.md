
## WkInputProfile

Responsible of holding together Input Event and Actions Key.

### AddInputProfile(actionKey, type, parameters)

Add Input Profile into dictionary

| Name | Description |
| ---- | ----------- |
| actionKey | *System.String*<br> |
| type | *System.Type*<br> |
| parameters | *System.Object[]*<br> |

### AddInputProfile(settings, actionKey)

Add Input Profile into dictionary

| Name | Description |
| ---- | ----------- |
| settings | *Weike.MachineInterface.Input.WkInputSettings*<br> |
| actionKey | *System.String*<br> |

### GetKeyFromInputSettings(type, parameters)

Get Key from Input Settings data

| Name | Description |
| ---- | ----------- |
| type | *System.Type*<br>Event Type |
| parameters | *System.Object[]*<br>Event params |

#### Returns



### GetKeyFromInputSettings(inputSettings)

Get Key from Input Settings

| Name | Description |
| ---- | ----------- |
| inputSettings | *Weike.MachineInterface.Input.WkInputSettings*<br> |

#### Returns



### InputKeyExist(type, parameters)

Check if input settings data is similar

| Name | Description |
| ---- | ----------- |
| type | *System.Type*<br>Type of Events |
| parameters | *System.Object[]*<br>Event's Parameter |

#### Returns



### InputKeyExist(settings)

Check if input settings data is similar

| Name | Description |
| ---- | ----------- |
| settings | *Weike.MachineInterface.Input.WkInputSettings*<br> |

#### Returns



### InvokeActions(key, actionProfile, parameters)

Invoke actions from key and action profile reference

| Name | Description |
| ---- | ----------- |
| key | *System.String*<br>action keys |
| actionProfile | *Weike.MachineInterface.Action.WeikeActionProfile*<br>Action profile reference |
| parameters | *System.Object[]*<br>parameters |

### RemoveInputProfile(type, parameters)

Remove Input profile according to Input Settings

| Name | Description |
| ---- | ----------- |
| type | *System.Type*<br>Event Type |
| parameters | *System.Object[]*<br>Event params |

### RemoveInputProfile(settings)

Remove Input profile according to Input Settings

| Name | Description |
| ---- | ----------- |
| settings | *Weike.MachineInterface.Input.WkInputSettings*<br> |

