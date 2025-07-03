# More about Tags

## Adding a new Tag

Tag are similar to Item in the sense that registration is done through instantiating a new Tag instance.

```csharp
ItemTag tag = new ItemTag(str tagId, bool isHidden = false, bool hasIcon = false, int x, int y);
```

* `tagId`: the string identifier of the Tag
* `isHidden`: whether or not the Tag will be shown in the Item tooltip
* `hasIcon`: whether or not the Tag have an icon, won't be shown if `isHidden` is false
* `x` and `y`: texture coordinates (X and Y) of the Tag icon

A Tag can have an icon, which similarly to Item is also stored in a texture atlas (`res/textures/ui.png`).

## Default tags

The game has quite a few set of default tags for various properties.

| String ID | Internal | Description |
| --------- | -------- | ----------- |
| can_place | `ItemTag.can_place` | Used for Block, determine whether or not the Item can be placed. |
| can_consume | `ItemTag.can_consume` | Whether or not the Player can consume the Item. |
| cant_mine | `ItemTag.cant_mine` | Whether or not the Item can be used to mine Block. |
| axe_power | `ItemTag.axe` | Whether or not the Item is an axe, and the power of it. |
| hammer | `ItemTag.hammer` | Whether or not the Item is a hammer. |
| melee_damage | `ItemTag.melee_damage` | The melee damage of the Item. |
| pickaxe_power | `ItemTag.pickaxe` | Whether or not the Item is a pickaxe, and the power of it. |
| swing_speed | `ItemTag.swing_speed` | The swing/usage cooldown of the Item. |
| restores_health | `ItemTag.restores_health` | How much health is restored upon Item consumption. |
| defence | `ItemTag.defence` | Used for Armor, how much defense is granted to the Player when wearing the Item. |
| required_ammo | `ItemTag.required_ammo` | Whether or not the Item requires Ammo. |
| ammo | `ItemTag.ammo` | Whether or not the Item is an Ammo. |
| ranged_damage | `ItemTag.ranged_damage` | The ranged damage of the Item. |
| trinket | `ItemTag.trinket` | Whether or not the Item is a Trinket. |


*[Item]: PocketBlocks.Items.Item
*[Tag]: PocketBlocks.Items.ItemTagTypes.ItemTag
*[TagEntry]: PocketBlocks.Items.ItemTagTypes.ItemTagEntry
*[Block]: PocketBlocks.Blocks.Blocks.Block
*[Player]: PocketBlocks.EntitySystem.Entities.PlayerEntity
*[Armor]: PocketBlocks.Items.ItemTypes.ItemArmour
*[Ammo]: PocketBlocks.Items.ItemTypes.ItemAmmo
*[Trinket]: PocketBlocks.Items.ItemTypes.ItemTrinket