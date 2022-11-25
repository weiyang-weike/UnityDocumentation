# SRAM Introduction (Unity)

**Note**: This current convention only applies to Unity Framework V1 and used on KIRIN

Summary on SRAM 
- Size per block 1666
- 16 Blocks
- 20 byte for common data inside `GameData(C++)` `GameDataWrapper(C#)`
- 100 byte for config 
- 1546 byte for Gameplay Data

There are 16 blocks for each game title (up to 4 different denominations per game).

---

The allocation of each game is in the following order.
-	Common data
-	Game specific configuration data
-	Game specific play data

---

Common data structure : 20 bytes

| Item            | Type   | Size in byte | Remarks                                                                                                               |
| --------------- | ------ | ------------ | --------------------------------------------------------------------------------------------------------------------- |
| crc             | ushort | 2            | Block crc covers common data structure, game specific configuration data structure, game specific play data structure |
| id              | byte   | 1            | Game Id                                                                                                               |
| gameSequence    | long   | 8            | Running number to identify the last played game. Increment by one whenever the selected game starts a new game.       |
| subGameSequence | ushort | 2            | Running number to identify the last played game. Increment by one whenever the selected game starts a new game.       |
| variation       | byte   | 1            | Selected Index of game Variation                                                                                      |
| denom           | byte   | 1            | Select index of game denomination                                                                                     |
| enable          | bool   | 1            | True if game is enabled, otherwise false                                                                              |
| data size       | uint   | 4            | Actual Size of data used by game                                                                                      |


---

Game specific configuration data structure: maximum size 100 bytes

| Item                   | Type | Size in byte | Remarks                                 |
| ---------------------- | ---- | ------------ | --------------------------------------- |
| common                 | byte | 3            | Game Specific Common Configuration Data |
| play option profile    | byte | 1            | Game specific configuration data        |
| bet multiplier profile | byte | 1            | Game specific configuration data        |
| game specific          | byte | 95           | Game specific configuration data        |


--- 

Game specific configuration data structure: maximum size 1546 bytes

1666 - configsize (100) - commonData (20) = 1546

| Item     | Type | Size in byte | Remarks                 |
| -------- | ---- | ------------ | ----------------------- |
| reserved | byte | 1546         | Game specific play Data |

---

## Common Convention / Rules / Principles

There are some Convention / Rules when saving into SRAM

### Make sure the data you save is at it's most basic form 

Let's say you saving betAmount. It should not be betAmount * betMultiplier. It should purely be betAmount. 

### Try not to abuse the amount of data size 

If it could be solve with short do not use Long to store it.

### Document the usage of data stored with XML documentation

Please document the usage of the data in both a Documentation doc and inside the code with the XML summary comments.

---

## Basic Usage

Before reading this section please understand how WkModel works first.

### Step 1

This step make sure the sequence order of serialization on SRAM.


```cs
using Weike.MachineInterface.Serializer;

namespace Weike.Core.Serializer
{
    /// <summary>
    /// Core configuration data
    /// 0 - 100
    /// </summary>
    [StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
    public class WkCoreConfigurationData : WkConfigurationData
    {
        
    }

    /// <summary>
    /// Core Recover Data
    /// Some Common Gameplay Data
    /// 100 - 1546
    /// </summary>
    [StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
    public class WkCoreGamePlayData : WkGamePlayData
    {
        /// <summary>
        /// Credit amount
        /// </summary>
        public long creditAmount;

        /// <summary>
        /// Win Amount
        /// </summary>
        public long winAmount;
    }
}
```

You can override these classes like this 

```cs
using Weike.Core.Serializer; 

namespace Weike.Core.Slot.Serializer
{
    /// <summary>
    /// Slot Configuration Data
    /// </summary>
    [StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
    public class WkSlotConfigurationData : WkCoreConfigurationData
    {
        // TODO documentation
#pragma warning disable CS1591
        public bool isAutoTakeWin;
        public bool canFastStop;
        public bool canAutoSpin;

        public byte playOptionProfileIndex;
        public byte betMultiplierProfileIndex;
#pragma warning restore CS1591
    }

    /// <summary>
    /// Slot Gameplay Data
    /// </summary>
    [StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
    public class WkSlotGamePlayData : WkCoreGamePlayData
    {
        // TODO documentation
#pragma warning disable CS1591
        public byte selectedPlayOption;
        public byte selectedBetMultiplier;

        public byte variation;
        public int amountOfFreeGame;
        public int currentAmountOfFreeGame;
#pragma warning restore CS1591
    }

}
```

### Step 2

You can bind the data you wish to Save like this using the attribute : 
1. WkSaveToGameDataWrapper
2. WkSaveToSram

```cs
using Weike.Core.Model;
using Weike.MachineInterface.Attributes;

namespace Weike.Core.Game
{ 
    /// <summary>
    /// Default Game Data Model
    /// </summary>
    public class WkGameDataModel : WkModel
    {
    #pragma warning disable CS1591
        [WkSaveToGameDataWrapper]
        public uint denom
        {
            get => _denom;
            set
            {
                if (value == _denom) return;
                _denom = value;
                OnPropertyChanged();
            }
        }

        [WkSaveToSram]
        public long creditAmount
        {
            get => _creditAmount;
            set
            {
                if (value == _creditAmount) return;
                _creditAmount = value;
                OnPropertyChanged();
            }
        }

        [WkSaveToGameDataWrapper]
        public long gameSequence
        {
            get => _gameSequence;
            set
            {
                if (value == _gameSequence) return;
                _gameSequence = value;
                OnPropertyChanged();
            }
        }
    #pragma warning restore CS1591

        private long _creditAmount;
        private uint _denom = 1;
        private long _gameSequence;

    }
}
```

- WkSaveToSram will save to the 1646 data array
- WkSaveToGameDataWrapper will let you save into the common data inside GameDataWrapper

For SRAM data you can determine if it's Config or Gameplay by doing this. `By default it's Gameplay`

```cs
namespace Weike.Core.Slot.Game
{
    /// <summary>
    /// Slot game data model
    /// </summary>
    public class WkSlotGameDataModel : WkGameDataModel
    {
    #pragma warning disable CS1591 
        private byte _selectedPlayOption = 4;
        private byte _selectedBetMultiplier = 1;
        private bool _isAutoTakeWin = true;

        [WkSaveToSram(SramDataType.Config)]
        public bool isAutoTakeWin
        {
            get => _isAutoTakeWin;
            set
            {
                if (value == _isAutoTakeWin) return;
                _isAutoTakeWin = value;
                OnPropertyChanged();
            }
        }

        [WkSaveToSram("playOptionProfileIndex", SramDataType.Config)]
        public byte selectedPlayOptionProfile
        {
            get => _selectedPlayOptionProfile;
            set
            {
                if (value == _selectedPlayOptionProfile) return;
                _selectedPlayOptionProfile = value;
                OnPropertyChanged();
            }
        }

        [WkSaveToSram("betMultiplierProfileIndex", SramDataType.Config)]
        public byte selectedBetMultiplierProfile
        {
            get => _selectedBetMultiplierProfile;
            set
            {
                if (value == _selectedBetMultiplierProfile) return;
                _selectedBetMultiplierProfile = value;
                OnPropertyChanged();
            }
        }
    }    
}

```

Lastly you can also bind it to custom binder property name that's not the same as your model in the following code example.

### Step 3 

To actually bind it. We have to set it up at `WkGameManager` on `Awake`

```cs
public abstract class WkGameManager : WkGameActor, IWkGameManager
{
    protected override void Awake()
    {
        SpawnWinManager();

        modelList.Add(dataModel);
        modelList.Add(winManager!.modelData);
        
        base.Awake();
    }
}
```

If there's new manager and new data model inside there you can add it through this method for the binding to works.

---

## In-Depth Look Into SRAM Binding

From basic usage you know that we have 2 classes that handles SRAM storing.
1. WkModel 
2. IWkSramData
   -  WkConfigurationData
   -  WkGamePlayData

`IWkSramData` is a class that will be responsible to recover from PI and Send to PI to save. 

While `WkModel` this class is meant for game usage. According to MVC model architecture we store all our gameplay data used by game inside WkModel. 

Thus there's an Attribute `IWkSaveToAttribute` that binds these 2 properties and fields together. 

It's a two way binding. During Recovery / Audit Configuration, `IWkSramData` will get data from PI and deserialize the data to binded property of `WkModel`. 

While `WkModel` OnPropertyChanges currently will trigger the whole block to save the data after serializing it. 

NOTE that the only time deserialization happen is when `RecoverGameData` method in `WkGameManager` runs and Audit Configuration changes. 