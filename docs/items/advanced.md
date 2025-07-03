# Advanced Items

## The Item class

The base Item instance will suffice for basic item types such as food or tools, however to have more advanced behavior, you have to make your own extended Item class.

The basic of this is having your very own Item class, and overriding its defaults with your own. This may also be referred to as [polymorphism](https://www.w3schools.com/cs/cs_polymorphism.php). 

The base Item class provide many virtual methods, which get triggered when certain actions are done in-game (e.g., left click, right click, etc...); however by default, those virtual methods are empty. By having another class inheriting the base Item class, we can override those default virtual methods and having them run our custom code.

!!! info "Info"
    Virtual methods are methods that allow itself to be overriden by any class that inherits it.

    For example:

    ```csharp
    public class TestOne {
        public virtual void Message() {
            Console.WriteLine("Hello, world!");
        }
    }
    ```

    When we do `TestOne.Message()`, the message "Hello, world!" would be printed to the console. However, what if instead of "Hello, world!", we want to print "Goodbye, world!" instead?

    ```csharp
    // The new class TestTwo inherits TestOne, which allows us to override Message()
    public class TestTwo : TestOne {
        // Override
        public override void Message() {
            // Our new code
            Console.WriteLine("Goodbye, world!");
        }
    }
    ```

    Now if we do `TestTwo.Message()`, the message "Goodbye, world!" would be printed to the console!

    If you want to run both your new code and the original one, you can do so like this:

    ```csharp
    public class TestTwo : TestOne {
        public override void Message() {
            // Run our new code
            Console.WriteLine("Goodbye, world!");
            // And now run the original
            base.Message();
        }
    }
    ```

    After executing, our new text "Goodbye, world!" will be printed first, and then the original "Hello, world!"

## "Events"

Events are a way of referring to the virtual methods provided by the base Item class. They are called so because such virtual methods only get executed when something triggers it.

| Method | Description |
| ------ | ----------- |
| `void OnUse(PlayerEntity player, World world)` | When the Player right clicks. |
| `void OnLeftClickUse(PlayerEntity player, World world)` | When the Player left clicks. |
| `void ReleaseLeft(PlayerEntity player, World world)` | When the Player release left mouse. |
| `void OnHeldDownTick(PlayerEntity player, World world)` | When the Player hold down either left or right mouse. |
| `void OnHeldTick(PlayerEntity player, World world)` | When the Player select the Item in the hotbar. |
| `void ReleaseRight(PlayerEntity player, World world)` | When the Player release right mouse. |
| `void OnRadialClose(PlayerEntity player, int selection)` | When the Radial menu is closed. |
| `void OnRadialOpen(PlayerEntity player, UIRadialMenu menu)` | When the Radial menu is opened. |
| `bool AllowedInSlot(InventorySlot slot)` | Used to perform special inventory slot checks (e.g., Trinket) |
| `void LoadAssets()` | Used to load additional assets (e.g., sounds) |
| `bool CanConsume(PlayerEntity player)` | Whether or not the player can consume the Item. |
| `void OnHitEntity(PlayerEntity player, Entity entity)` | When the Player hits an Entity. |

## Example(s)

```csharp title="Example"
class CustomItem : Item
{
    public CustomItem(int x, int y, string stringId) : base(x, y, stringId) {
    }

    public override void OnUse(PlayerEntity player, World world) {
        // Run the original virtual method
        base.OnUse(player, world);
        // Print "Hello, world!" to chat log
        ChatLog.PushFromPlayer("Hello, world!");
    }
}
```

The above example is an Item that upon use, will print a chat message "Hello, world!". After writing your custom Item class, register your Item using said class.

```csharp title="Example"
Item helloWorldItem = new CustomItem(0, 16, "hello_world_item");
```

*[Item]: PocketBlocks.Items.Item
*[Tag]: PocketBlocks.Items.ItemTagTypes.ItemTag
*[TagEntry]: PocketBlocks.Items.ItemTagTypes.ItemTagEntry
*[Player]: PocketBlocks.EntitySystem.Entities.PlayerEntity
*[World]: PocketBlocks.ChunkManagement.World
*[Trinket]: PocketBlocks.Items.ItemTypes.ItemTrinket
*[Entity]: PocketBlocks.EntitySystem.Entity
*[Radial]: PocketBlocks.UI.UINodes.UIRadialMenu