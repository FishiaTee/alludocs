# Item
Represents an item.

## Related Pages

* [Basics of Items](../items/items.md)

## Constructors

```csharp
public Item(int textureX, int textureY, string stringId)
```

??? info
    Registers an item.

    | Name | Description |
    | ---- | ----------- |
    | int textureX | X coordinate of the item texture (in the atlas) |
    | int textureY | Y coordinate of the item texture (in the atlas) |
    | string stringId | String identifier of the item |

```csharp
public Item(Block block)
```

??? info
    Registers an item representing a block.
    
    | Name | Description |
    | ---- | ----------- |
    | Block block | Block being represented |

## Fields

```csharp title="X coordinate of the item texture"
public int textureX
```

```csharp title="Y coordinate of the item texture"
public int textureY
```

```csharp title="Internal numeric item ID"
public int itemID
```

```csharp title="String identifier of the item"
public string stringID
```

```csharp title="Localized item name"
public string translatedName
```

```csharp title="Item description"
public string translatedDesc = "..."
```

```csharp title="Whether or not the item has a description"
public bool hasDescription
```

```csharp title="Block being represented by this item"
public Block block
```

```csharp title="Path to hand model"
public string itemModelString
```

```csharp title="Path to hand model texture"
public string itemTextureString
```

```csharp title="The hand model"
public BBModel heldItemModel
```

```csharp title="The hand model texture"
public Texture heldItemTexture
```

```csharp title="The stack limit of the item"
public int stackLimit = 512
```

```csharp title="The rarity level of the item"
public int rarity
```

```csharp title="Sword to play when the item is swung"
public Wav swingSound
```

```csharp title="Sound to play when the item hit a mob"
public Wav hitSound
```

## Methods

```csharp
public Item SetSwingSounds(Wav swing, Wav hit)
```

??? info
    Assign a swing and hit sounds.

    Arguments:

    | Name | Description |
    | ---- | ----------- |
    | Wav swing | Swing sound |
    | Wav hit | Hit sound |

    Returns: Item

```csharp
public bool GetTag(ItemTag tag, out ItemTagEntry entry)
```

??? info
    Check if a tag is assigned.
    
    Arguments:

    | Name | Description |
    | ---- | ----------- |
    | ItemTag tag | The tag to check |
    | ItemTagEntry entry | The tag entry |

    Returns: bool

```csharp
public Item AddTag(ItemTagEntry tag)
```

??? info
    Add a tag.
    
    Arguments:

    | Name | Description |
    | ---- | ----------- |
    | ItemTagEntry tag | The tag entry |

    Returns: Item

```csharp
public Item SetRarity(int rarity)
```

??? info
    Assign a rarity value.
    
    Arguments:

    | Name | Description |
    | ---- | ----------- |
    | int rarity | The rarity value |

    Returns: Item

```csharp
public Item SetModel(string model, string texture)
```

??? info
    Assign a hand model.
    
    Arguments:

    | Name | Description |
    | ---- | ----------- |
    | string model | The model path |
    | string texture | The model texture path |

    Returns: Item

```csharp
public Item SetStackSize(int value)
```

??? info
    Set the maximum stack size.
    
    Arguments:

    | Name | Description |
    | ---- | ----------- |
    | int value | Stack size |

    Returns: Item

## Virtual Methods

```csharp
public virtual void OnUse(PlayerEntity player, World world)
```

??? info
    Runs when the player right clicks the item.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |
    | World world | The world in which the event was triggered |

```csharp
public virtual void OnLeftClickUse(PlayerEntity player, World world)
```

??? info
    Runs when the player left clicks the item.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |
    | World world | The world in which the event was triggered |

```csharp
public virtual void ReleaseLeft(PlayerEntity player, World world)
```

??? info
    Runs when the player releases the left mouse.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |
    | World world | The world in which the event was triggered |

```csharp
public virtual void OnHeldDownTick(PlayerEntity player, World world)
```

??? info
    Runs every ticks when the player holds down right click.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |
    | World world | The world in which the event was triggered |

```csharp
public virtual void OnHeldTick(PlayerEntity player, World world)
```

??? info
    Runs every ticks when the player has the item selected in the hotbar.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |
    | World world | The world in which the event was triggered |

```csharp
public virtual void ReleaseRight(PlayerEntity player, World world)
```

??? info
    Runs when the player releases the right mouse.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |
    | World world | The world in which the event was triggered |

```csharp
public virtual void OnRadialClose(PlayerEntity player, int selection)
```

??? info
    Runs when the radial menu is closed.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |
    | int selection | The selected entry |

```csharp
public virtual void OnRadialOpen(PlayerEntity player, UIRadialMenu menu)
```

??? info
    Runs when the radial menu is opened.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |
    | UIRadialMenu menu | The radial menu |

```csharp
public virtual bool AllowedInSlot(InventorySlot slot)
```

??? info
    Checks if the item can be placed into a specific inventory slot type.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | InventorySlot | The inventory slot that the player attempted to put the item in |

    Returns: bool

```csharp
public virtual void LoadAssets()
```

??? info
    Used to load additional assets.

```csharp
public virtual bool CanConsume(PlayerEntity playerEntity)
```

??? info
    Checks whether or not the item can be consumed.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |

    Returns: bool

```csharp
public virtual void OnHitEntity(PlayerEntity player, Entity target)
```

??? info
    Runs when the item is used to hit an entity.
    
    Properties:

    | Name | Description |
    | ---- | ----------- |
    | PlayerEntity player | The player triggered the event |
    | Entity target | The entity that was hit by the item |

## Static Methods

```csharp
public static Item GetItemByID(int itemID)
```

??? info
    Get an Item instance from a numeric ID.
    
    Arguments:

    | Name | Description |
    | ---- | ----------- |
    | int itemID | The numeric ID of an Item |

    Returns: Item

*[Block]: PocketBlocks.Blocks.Blocks.Block
*[Item]: PocketBlocks.Items.Item
*[Wav]: SoLoud.Wav
*[ItemTag]: PocketBlocks.Items.ItemTagTypes.ItemTag
*[ItemTagEntry]: PocketBlocks.Items.ItemTagTypes.ItemTagEntry
*[PlayerEntity]: PocketBlocks.EntitySystem.Entities.PlayerEntity
*[World]: PocketBlocks.ChunkManagement.World
*[UIRadialMenu]: PocketBlocks.UI.UINodes.UIRadialMenu
*[InventorySlot]: PocketBlocks.Items.InventorySlot
*[Entity]: PocketBlocks.EntitySystem.Entity