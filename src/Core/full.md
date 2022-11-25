# WeikeCore

<table>
<tbody>
<tr>
<td><a href="#wkgameinstance">WkGameInstance</a></td>
<td><a href="#wkunityeventmanager">WkUnityEventManager</a></td>
</tr>
<tr>
<td><a href="#wkactorfactory">WkActorFactory</a></td>
<td><a href="#iwkstate">IWkState</a></td>
</tr>
<tr>
<td><a href="#iwkstatemachine">IWkStateMachine</a></td>
<td><a href="#wkstate">WkState</a></td>
</tr>
<tr>
<td><a href="#wkstatecore">WkStateCore</a></td>
<td><a href="#wkstatemachine">WkStateMachine</a></td>
</tr>
<tr>
<td><a href="#wkstatemanager">WkStateManager</a></td>
<td><a href="#gamedata">GameData</a></td>
</tr>
<tr>
<td><a href="#gameproperty">GameProperty</a></td>
<td><a href="#weikegamedata">WeikeGameData</a></td>
</tr>
<tr>
<td><a href="#wkgameactor">WkGameActor</a></td>
<td><a href="#wkgamemanager">WkGameManager</a></td>
</tr>
<tr>
<td><a href="#wkgamerootactor">WkGameRootActor</a></td>
<td><a href="#iwkgameactor">IWkGameActor</a></td>
</tr>
<tr>
<td><a href="#iwkgameinstance">IWkGameInstance</a></td>
<td><a href="#iwkgamemanager">IWkGameManager</a></td>
</tr>
<tr>
<td><a href="#iwkgameproperty">IWkGameProperty</a></td>
<td><a href="#iwkmodel">IWkModel</a></td>
</tr>
<tr>
<td><a href="#iwkobject">IWkObject</a></td>
<td><a href="#iwkplayercontroller">IWkPlayerController</a></td>
</tr>
<tr>
<td><a href="#iwkrootactor">IWkRootActor</a></td>
<td><a href="#iwkstatecore">IWkStateCore</a></td>
</tr>
<tr>
<td><a href="#iwkstatemanager">IWkStateManager</a></td>
<td><a href="#wkmodel">WkModel</a></td>
</tr>
<tr>
<td><a href="#wkplayercontroller">WkPlayerController</a></td>
<td><a href="#displayobjectcollection">DisplayObjectCollection</a></td>
</tr>
<tr>
<td><a href="#common">Common</a></td>
<td><a href="#wkguiutils">WKGUIUtils</a></td>
</tr>
<tr>
<td><a href="#wkmath">WkMath</a></td>
<td><a href="#wkunityadapter">WkUnityAdapter</a></td>
</tr>
</tbody>
</table>


## WkGameInstance

Singleton Instance of the game that's Spawn at MIScene. If it's spawn on Individual game it's not a monobehaviour but a normal C# object

### GetAllActors(outArray)

Becareful with this function it's expensive

| Name | Description |
| ---- | ----------- |
| outArray | *System.Collections.Generic.IList{Weike.Core.Interface.IWkObject}*<br> |

### InitializeAllActors

Initialize all actors in a single thread

### InitializeInstance

Initialize Instance / Managers

### RegisterObject(obj)

Register actor to the cache Dictionary By default it's called by @SpawnActor Over here it doesn't return Machine Context

| Name | Description |
| ---- | ----------- |
| obj | *Weike.Core.Interface.IWkObject*<br> |

#### Returns



### SpawnActorAndRegister(System.String,UnityEngine.GameObject)

### SpawnActorDeferredAndRegister(System.String,UnityEngine.GameObject)


## WkUnityEventManager

Unity Event Manager for Keyboard Invokation


## WkActorFactory

Actor factory Dynamically spawn gameobject and attach component to it.

### Constructor

CTOR

### AddNewType(name, type)

Deprecate this soon

| Name | Description |
| ---- | ----------- |
| name | *System.String*<br> |
| type | *System.Type*<br> |

### CreateActor(actorType, parentTransform, isDeferredSpawning)

Create actor from string

| Name | Description |
| ---- | ----------- |
| actorType | *System.String*<br>Actor Class Type in string |
| parentTransform | *UnityEngine.Transform*<br>Parent's Transform for Attachment |
| isDeferredSpawning | *System.Boolean*<br>Deferred Spawnning |

#### Returns



### FinishSpawning(actor)

Invoke this once you finish initializing all your data

| Name | Description |
| ---- | ----------- |
| actor | *Weike.Core.Interface.IWkGameActor*<br> |

### instance

Actor Instance


## IWkState

Weike State This State is for platform uses

### machineContext

Machine Context Reference


## IWkStateMachine

State Machine Abstraction

### Pause(shouldPause)

Should Pause State Machine

| Name | Description |
| ---- | ----------- |
| shouldPause | *System.Boolean*<br>True = Pause |

### Recover

On Recover Invokation

### ReturnFromBusy

Return from Busy Invoke


## WkState

Wk State for PI

### Constructor(id, owner)

WK State's CTOR

| Name | Description |
| ---- | ----------- |
| id | *System.String*<br>state ID |
| owner | *Weike.Core.Interface.IWkObject*<br>Probably State Manager |

### Init

### machineContext

### owner

### WeikeInit


## WkStateCore

Weike state core will inject weike's Game Context into the state on Initialized

### Constructor(id, fallBackStateId, owner)

WK State CTOR

| Name | Description |
| ---- | ----------- |
| id | *System.String*<br>State ID |
| fallBackStateId | *System.String*<br>Fall Back State ID |
| owner | *Weike.Core.Interface.IWkObject*<br>Should Be GameStateManager |

### EnterState

### fallBackStateId

### gameManager

### onRecoverState

### onReturnState

### playerController

Player Controller Reference

### RecoverState

### ReturnState


## WkStateMachine

State Machine

### Pause(System.Boolean)

### Recover

### ReturnFromBusy

### Update


## WkStateManager

State Manager Responsible for deserializing JSON file and setup all the states and transition from StateFactory.

### Constructor

CTOR

### Constructor(stateMachineType)

CTOR for Custom State Machine

| Name | Description |
| ---- | ----------- |
| stateMachineType | *System.Type*<br>Type of State Machine |

### fsm

### fsmJsonPath

Set this before Init

### InitFsm(System.String)

### owner

### WeikeInit


## GameData

List of Game Property


## GameProperty

Game Property class TODO Struct this guy


## WeikeGameData

TODO struct this guy as well


## WkGameActor

This class is going to be at the root of every single game. It's going to also register itself to Lobby On Init.


## WkGameManager

This class is going to handle that's game related. Like Player Controller, GameState etc.

### Constructor

CTOR

### defaultGameStateFsmPath

Game State FSM Path.

### gameCode

### gameData

Temp

### gameState

### gameStateType

Game State Type

### playerController

### playercontrollerType

Player Controller Type

### SpawnPlayerControllers

Spawn Controller Virtual Function


## WkGameRootActor

Game Root Actor to act as interface between game and lobby

### gameCode

### gameManager

### gameManagerType

Game Manager Class Type by String Override this for Custom Game Manager's Class

### GetGameInfo(gameInfo)

Base function for Getting Game specific Info

| Name | Description |
| ---- | ----------- |
| gameInfo | *Weike.MachineInterface.GameInfoWrapper@*<br> |

### GetIsHidden

Check if Scene Is Hidden

#### Returns



### Hide(bShouldHide)

Function to hide whole scene

| Name | Description |
| ---- | ----------- |
| bShouldHide | *System.Boolean*<br> |

### LoadGameData

Base function for loading game specific data

### rootScene

### WeikeInit

WeikeActor's Interface


## IWkGameActor

Base Interface for weike's actor

### go

Unity world's Context. Unity's Game Object


## IWkGameInstance

Game Instance's Abstraction

### activeGameManager

Currently Active Manager. Could be null

### GetActorsByType(System.Type)

Get Actor By Type

#### Returns



### machinContext

Machine Context From GI

### machineState

Get Parallel State for PI

### RegisterObject(actor)

Register Object and return a Machine Context to object.

| Name | Description |
| ---- | ----------- |
| actor | *Weike.Core.Interface.IWkObject*<br>Weike Object |

#### Returns

Machine Context

### SpawnActorAndRegister(actorType, go)

Spawn actor and finish spawning

| Name | Description |
| ---- | ----------- |
| actorType | *System.String*<br>string Actor Type |
| go | *UnityEngine.GameObject*<br>Game Object |

#### Returns

Weike Actor

### SpawnActorAndRegister\`\`1(actorType, go)

Spawn actor and cast to the Generic type

#### Type Parameters

- T - 

| Name | Description |
| ---- | ----------- |
| actorType | *System.String*<br> |
| go | *UnityEngine.GameObject*<br> |

#### Returns



### SpawnActorDeferredAndRegister(actorType, go)

Spawn Actor Deferred

| Name | Description |
| ---- | ----------- |
| actorType | *System.String*<br>string Actor Type |
| go | *UnityEngine.GameObject*<br>Game Object |

#### Returns

Weike Actor


## IWkGameManager

Weike's Game Manager

### gameCode

Game Code

### gameState

Get Game State instance

### GetGameInfo

Interface for getting game specific's info

#### Returns



### LoadGameData

Load Initial Game Data Interface

### playerController

Get player controller. TODO maybe make it multiple as array for multiplayer. Server get to store all of them

### RegisterObject(obj)

Register Game Object To Game Manager Normally called by GameInstance

| Name | Description |
| ---- | ----------- |
| obj | *Weike.Core.Interface.IWkObject*<br> |

### TopupCredit(amount)

TODO Deprecate this soon

| Name | Description |
| ---- | ----------- |
| amount | *System.Int64*<br> |


## IWkGameProperty



### Weike.Core.Interface.IWkHud.GetUIFromType\`\`1

Getting iterator of UI from type

#### Type Parameters

- T - 

#### Returns



### Weike.Core.Interface.IWkHud.owningPlayerController

Player Controller Owner

### Weike.Core.Interface.IWkHud.RegisterUI(uiController)

Register UI Controller to HUD

| Name | Description |
| ---- | ----------- |
| uiController | *Weike.Core.Interface.IWkDisplayObject*<br> |


## IWkModel

Model Component for MVC

### OnPropertyChanged(name)

On property change Method

| Name | Description |
| ---- | ----------- |
| name | *System.String*<br>Property Name |


## IWkObject

Weike's Base object class Hierarchy

### owner

Actor's owner / Object responsible for spawning it.

### WeikeInit

this function is not to use Unity's start to initialize some stuff because of threading issue


## IWkPlayerController

Player controller's abstraction

### gameContext

An object to represent Game's Context

### hud

Two way dependency between HUD and PlayerController


## IWkRootActor

Just a root actor to talk to lobby

### gameManager

Scene's Game Manager


## IWkStateCore

Weike State. Use this state as your base state throughout the game. This State is for game uses

### fallBackStateId

Fall back state ID Set in JSON

### gameManager

Get Responsible Game Manager Reference

### onRecoverState

On Recover State Event

### onReturnState

On Return State Event

### RecoverState

Invoke when Recovering State

### ReturnState

Invoke when Return From PI Busy


## IWkStateManager

State Manager's Abstraction

### fsm

Finite state Machine Getter

### fsmJsonPath

Finish State Machine's Json Path. Please initial this before calling Init().

### InitFsm(System.String)

Initialize Finite State Machine


## WkModel

### OnPropertyChanged(System.String)

### PropertyChanged


## WkPlayerController

Player controller's reponsibility is to serve as a interface between player and the game. It will handle all the event that the player input from machine to game.

### InitHUD

Init HUD using String Type from Spawn actor's Factory


## DisplayObjectCollection

A dictionary collection of WeikeUIController

### AddUI(uiController)

Add new UI to List

| Name | Description |
| ---- | ----------- |
| uiController | *Weike.Core.Interface.IWkDisplayObject*<br> |

### RemoveUI(uiController)

Remove UI from list

| Name | Description |
| ---- | ----------- |
| uiController | *Weike.Core.Interface.IWkDisplayObject*<br> |


## Common

Common Utilities

### GetActiveGameManager

Get Active Game Manager

#### Returns



### GetActiveHUD

Get Active HUD

#### Returns



### GetActivePlayerController

Get Active Player Controller

#### Returns



### GetResponsibleGameManager(UnityEngine.GameObject)

Get the Game Manager that's responsible for this actor

#### Returns



### GetResponsibleGameManager(Weike.Core.Interface.IWkGameActor)

Get the Game Manager that's responsible for this actor

#### Returns



### GetResponsibleGameManager(obj)

Get Responsible Manager from Object

| Name | Description |
| ---- | ----------- |
| obj | *Weike.Core.Interface.IWkObject*<br>Weike Object |

#### Returns

Game Manager

### GetResponsibleHUD(go)

Get Responsible HUD

| Name | Description |
| ---- | ----------- |
| go | *UnityEngine.GameObject*<br> |

#### Returns



### GetResponsiblePlayerController(go)

Get Responsible Player controller

| Name | Description |
| ---- | ----------- |
| go | *UnityEngine.GameObject*<br> |

#### Returns




## WKGUIUtils

Common Utilities for IMGUI

### MakeTex(width, height, col, outTex)

Draw A texture of colors Please use it on Init don't use it every frame. It's expensive

| Name | Description |
| ---- | ----------- |
| width | *System.Int32*<br> |
| height | *System.Int32*<br> |
| col | *UnityEngine.Color*<br>Color of Texture |
| outTex | *UnityEngine.Texture2D@*<br>Pass empty reference of Texture2D |


## WkMath




## WkUnityAdapter

Hacky class to get Monobehaviour's basic Lifecycle events callbacks Since it's a hacky class with very specific responsibility I din't clean up the code
