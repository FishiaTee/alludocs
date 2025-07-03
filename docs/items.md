# Items

Items are internally identified via numeric IDs, and are registered by instantiating a new Item instance.

```csharp
Item item = new Item(int x, int y, str stringId);
```

An Item takes three basic arguments: texture coordinates (X and Y) and a string identifier. The string identifier is used to refererence the Item in various places (e.g., translations).

## Texture

All items textures are stored in a single 1024x1024 texture atlas. Each textures are 16x16 in size, so the atlas consists of 64 rows and 64 columns, giving us a total of 4096 available texture slots.

You can access the texture atlas in `res/textures/items.png`.

When registering a new Item, you assign a texture to said Item by specifying its X and Y coordinates, which is the row and the column number multiplied by 16.

## 3D Model

An Item can have a 3D hand model, which will be displayed when the player hold the Item in their hotbar slot.

With an Item instance, a 3D model can be assigned with:

```csharp
Item.SetModel(str model, str texture);
```

The game takes models from `res/models` and textures from `res/textures`. Basically, a 3D model consists of two elements: the shape (model) and the texture.

```csharp title="Example"
// Register the item
Item obsidian_sword = new Item(0, 144, "obsidian_sword");
// Set a 3D hand model
obsidian_sword.SetModel("item.sword", "item.obsidian_sword");
```

We use the `sword` base model from `res/models/item/sword.json`, and apply our texture from `res/textures/item/obsidian_sword.png`.

## Stack Size

All items by default can be stacked up to 512. This can be overriden with:

```csharp
Item.SetStackSize(int stack);
```

## Tags

To change an Item's properties, we use Tags.

By adding a Tag, you are adding a TagEntry.

```csharp
Item.AddTag(ItemTagEntry tagEntry);
```

A TagEntry consists of a Tag, and its integer value. All tags have a value assigned to it, and this value determines the effectiveness of said tags.

```csharp
ItemTagEntry tag = new ItemTagEntry(ItemTag tag, int value);
```

```csharp title="Example"
// Register the item
Item cool_pickaxe = new Item(16, 192, "obsidian_sword");
// Assign it a tag (pickaxe power)
cool_pickaxe.AddTag(new ItemTagEntry(ItemTag.pickaxe, 8));
```

In the above example, we assigned a Tag (`ItemTag.pickaxe`) which in turns assigns the Item `cool_pickaxe` a pickaxe power of 8.

Tags are powerful, and can be used to do various things. More information about it can be found in its dedicated [Tags section](items/tags.md).

*[Item]: PocketBlocks.Items.Item
*[Tag]: PocketBlocks.Items.ItemTagTypes.ItemTag
*[TagEntry]: PocketBlocks.Items.ItemTagTypes.ItemTagEntry