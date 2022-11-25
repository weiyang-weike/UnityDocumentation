# WeikeMachineInterface

<table>
<tbody>
<tr>
<td><a href="#weikeactionprofile">WeikeActionProfile</a></td>
<td><a href="#wkaction">WkAction</a></td>
</tr>
<tr>
<td><a href="#enumbtnbit">EnumBtnbit</a></td>
<td><a href="#wkevent">WkEvent</a></td>
</tr>
<tr>
<td><a href="#wkeventmanager">WkEventManager</a></td>
<td><a href="#wkkeyboarddownevent">WkKeyboardDownEvent</a></td>
</tr>
<tr>
<td><a href="#wkkeyboardevent">WkKeyboardEvent</a></td>
<td><a href="#wkkeyboardlatchedevent">WkKeyboardLatchedEvent</a></td>
</tr>
<tr>
<td><a href="#wkkeyboardupevent">WkKeyboardUpEvent</a></td>
<td><a href="#wkmachinebuttonevent">WkMachineButtonEvent</a></td>
</tr>
<tr>
<td><a href="#wkmachineevent">WkMachineEvent</a></td>
<td><a href="#wkcontroller">WkController</a></td>
</tr>
<tr>
<td><a href="#wkinputcomponent">WkInputComponent</a></td>
<td><a href="#wkinputmanager">WkInputManager</a></td>
</tr>
<tr>
<td><a href="#wkinputprofile">WkInputProfile</a></td>
<td><a href="#wkinputsettings">WkInputSettings</a></td>
</tr>
<tr>
<td><a href="#iwkcontroller">IWkController</a></td>
<td><a href="#iwkevent">IWkEvent</a></td>
</tr>
<tr>
<td><a href="#iwkkeydownevent">IWkKeyDownEvent</a></td>
<td><a href="#iwkkeyevent">IWkKeyEvent</a></td>
</tr>
<tr>
<td><a href="#iwkkeylatchedevent">IWkKeyLatchedEvent</a></td>
<td><a href="#iwkkeyupevent">IWkKeyUpEvent</a></td>
</tr>
<tr>
<td><a href="#iwkmachinecontext">IWkMachineContext</a></td>
<td><a href="#iwkmachineevent">IWkMachineEvent</a></td>
</tr>
<tr>
<td><a href="#iwkplatform">IWkPlatform</a></td>
<td><a href="#wkbrowser">WkBrowser</a></td>
</tr>
<tr>
<td><a href="#wkmachineinstance">WkMachineInstance</a></td>
</tr>
</tbody>
</table>




### Weike.MachineInterface.GameDef.Constructor(game)

CTOR for Validation

| Name | Description |
| ---- | ----------- |
| game | *System.String*<br> |

### Weike.MachineInterface.GameDef.CompareLicense(other)

Licenses Comparitor

| Name | Description |
| ---- | ----------- |
| other | *Weike.MachineInterface.GameDef@*<br>Other Game Definition |

#### Returns

True or False

### Weike.MachineInterface.GameDef.Equals(other)

Current I Only Compare the Licenses

| Name | Description |
| ---- | ----------- |
| other | *Weike.MachineInterface.GameDef*<br> |

#### Returns



## IWkEvent



### GetIsHandled

Not used now

#### Returns




## IWkKeyDownEvent


## IWkKeyEvent

### keyCode

Keyboard Keycode


## IWkKeyLatchedEvent

### repeatCount

Latched Key Repeat Count


## IWkKeyUpEvent


## IWkMachineContext

Machine Context

### browser

Browser

### inputManager

Input Manager

### platformInterface

Platform Interface's Reference

### RegisterAndCallPlatformConnected(callback)

Register and call platofmr connected It will promp an event if previous value was false

| Name | Description |
| ---- | ----------- |
| callback | *System.Action{System.Boolean}*<br>Function Ptr |

#### Returns

Is Platform Connected


## IWkMachineEvent

Machine Event

### btnBit

Button Bit


## IWkPlatform

Weike Platform Interface

### auditUrl

Audit URL

### ip

IP Address

### platformPort

Platoform Port

### platformUrl

Platform URL

### webPort

Browser Port


## WkBrowser

WK Browser for Audit purpose. Window data interface to provide some windows data of the browser

