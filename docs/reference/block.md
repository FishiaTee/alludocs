# Block
Represents a block.

## Related Pages

* [Basics of Blocks](../blocks/blocks.md)

## Constructors

```csharp
public Block(string stringId)
```

??? info "Parameters"
    | Name | Description |
    | ---- | ----------- |
    | string stringId | String identifier of the block |

## Fields

```csharp title="String identifier of the block"
public string strID = ""
```

```csharp title="Whether the block is a solid block"
public bool solid
```

```csharp title="Whether the block is a semi-solid block"
public bool semisolid
```

```csharp title="Whether the block is a transparent block"
public bool transparent
```

```csharp title="Whether or not the block prevents light from passing it"
public bool blocksLight
```

```csharp title="(R)GB value of the light color that the block emits"
public byte lightEmissionRed
```

```csharp title="R(G)B value of the light color that the block emits"
public byte lightEmissionGreen
```

```csharp title="RG(B) value of the light color that the block emits"
public byte lightEmissionBlue
```

```csharp title="Whether or not the block emits light"
public bool emitsLight
```

```csharp title="The material type of the block"
public BlockMaterial blockMaterial = BlockMaterial.dirt
```

```csharp title="Whether or not the block has collision"
public bool canWalkThrough = true
```

```csharp title="Whether or not the block has custom block model collision"
public bool hasCustomCollider
```

```csharp title="Whether to ignore ambient occlusion checks"
public bool ignoreOcculusionChecks
```

```csharp title="Whether to skip smoothing lighting"
public bool skipSmoothLighting
```

```csharp title="Whether or not the block can be interacted with"
public bool interactible
```

```csharp title="Block states"
public BlockState state = new BlockState()
```

```csharp title="Block model"
public BlockModel model = new BlockModel()
```

```csharp title="Custom item drops upon block break"
public LootDescription customLoot
```

```csharp title="Item representing the block"
public Item item
```

```csharp title="Items to be dropped upon block break"
public Item dropItem
```

```csharp title="Slab variant of the block"
public Block slabVariant
```

```csharp title="Fence variant of the block"
public Block fenceVariant
```

```csharp title="Stair variant of the block"
public Block stairVariant
```

```csharp title="Panel variant of the block"
public Block PanelVariant
```

```csharp title="Flooring variant of the block"
public Block flooringVariant
```

```csharp title="The parent block of variant block(s)"
public Block isVariantOf
```

```csharp title="Whether or not the block is a block entity"
public bool hasBlockEntity
```

```csharp title="Whether to hide the block from the build menu"
public bool hideFromBuildMenu
```

```csharp title="Whether the block is a valid source block for the entwiner"
public bool entwineSource
```

```csharp title="Whether the block is a valid destination block for the entwiner"
public bool entwineDestination
```

```csharp title="Whether the block is a type of fluid"
public bool isFluid
```

```csharp title="Whether the block is a type of glass"
public bool isGlass
```

```csharp title="Whether the block is a type of crop"
public bool isCrop
```

```csharp title="Whether or not the block needs a supporting block"
public bool needsSupport
```

```csharp title="How commonly the block can spawn"
public int spawnRate
```

```csharp title="Spawn condition(s) of the block"
public SpawnEntry spawnEntry
```

```csharp title="Whether or not the block inflicts an effect upon stepping onto it"
public bool hasStandOnEffect
```

```csharp title="Whether or not the block inflicts an effect upon collision"
public bool hasStandInEffect
```

```csharp title="Effect to inflict upon stepping on top of the block"
public Effect standOnEffect
```

```csharp title="Effect to inflict upon collision"
public Effect standInEffect
```

```csharp title="Duration of effect inflicted upon collision"
public int standInEffectTicks = 2
```

## Methods


## Virtual Methods


## Static Methods


*[Block]: PocketBlocks.Blocks.Blocks.Block