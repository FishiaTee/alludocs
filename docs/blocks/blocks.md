# Blocks

!!! danger "Note"
    This section is work-in-progress.

Blocks are internally identified by numeric IDs, and are registered by creating a `Block` instance:

```csharp
Block block = new Block(string strID);
```

A `Block` instance is created with `strID` parameter, which is used for
identifying the block in translations, etc.

## Texture

All block textures are stored in 1024x1024 texture atlas. Each texture is 16x16 in size, so the atlas consists of 64 rows and 64 columns, giving us a total of 4096 available texture slots.

A texture can be assigned to the block using `Block.SetTexture(int id)` method, where `id` is location of the texture on both X and Y axis in *16-pixel* units. It's *deprecated* and should *not* be used.

Instead, use `Block.SetTexture(ushort x, ushort y)`, which accepts 2 parameters: `x` - location of texture on X axis, and `y` - location of the texture on Y axis, coordinates are specified in *pixel* units:

```csharp
// all other properties are removed for brevity
Block block = new Block("log").SetTexture(80, 16);
```

To assign *side texture* you can use `Block.SetSideTexture(int id)`, where `id` is location of the side texture on X axis, and specified in *16-pixel* units. Y coordinate is *always set to 0*:

```csharp
Block block = new Block("workbench").SetSideTexture(32);
```

As there's no way to set side texture's Y axis using builder methods, you need to either override `Block` class and set `Block.sideTexture` from the constructor, or use [*initializer*](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers):

```csharp
Block block = new Block("workbench")
{
    sideTexture = new FaceTexture(32 * 16, 0, 16, 16)
}
```

## Item sprite

All item sprites are stored in 1024x1024 texture atlas. Each sprite is 16x16 in size, so the atlas consists of 64 rows and 64 columns, giving us a total of 4096 available sprite slots.

An item sprite can be assigned to the block using `Block.SetItemSprite(int x, int y)`, where `x` is location of the sprite on X axis, and `y` is location of the sprite on Y axis, just like textures, these coordinates are specified in *pixel* units:

```csharp
// all other properties are removed for brevity
Block block = new Block("log").SetItemSprite(848, 48);
```

## Model

By default, the block uses normal 1x1x1 cube model. But if you want to spice up your block, you can assign custom or existing model to it using `Block.SetBlockModel(BlockModel model)`:

```csharp
// all other properties are removed for brevity
Block block = new Block("log").SetBlockModel(BlockModelQuads.log);
```

You can find all existing models, and more, in their dedicated [Models section](models.md).

## Solid and semi-solid

All blocks by default don't have collision and aren't *solid*. To make your block solid, you need to use `Block.MakeSolid()`, or to make it semi-solid - `Block.MakeSemiSolid()`:

```csharp
// all other properties are removed for brevity
Block block = new Block("log").MakeSolid();
```

Solid blocks don't let light go through and have collision.

Semi-solid blocks internally also considered solid, and just like solid blocks, don't let light go through, *but* they don't have collision and their faces are *never* occluded.

## Variants

You can automatically generate basic variants for your block using `Block.AutoGenVariants()`:

```csharp
// all other properties are removed for brevity
Block block = new Block("stone").AutoGenVariants();
```

This will generate following variants for your block:

- Slab: `*block ID*_slab`
- Flooring: `*block_ID*_flooring`
- Fence: `*block_ID*_fence`
- Panel: `*block_ID*_panel`
- Stair: `*block_ID*_stair`
