## Give objects basic movement

Before you spawn objects into your sceen, they should move the way you want.

*Check "Basic Gameplay" and "Gameplay Mechanics" in the project concept.*

1. If relevant, add **Rigidbody** components to your non-player objects. *Check if objects need freeze position*
2. Create a **new script**(s) for the objects that will be instantiated during gameplay and attach them to their respective objects (including projectiles or pickups). *`public float speed` makes easy to change speed of different objects*
3. Program the **basic movement** for your objects and test that they work.

By the end of this step, all objects should basically move the way they should in the game.

## Destroy objects off-screen

To make sure our hierachy doesn't get  too cluttered, let's make sure these objects get destroyed when they leave the screen.

1. Either create a new script or add code to your existing script to make sure objects are destroyed when they leave the screen.

By the end of this step, objects should be removed from the hierarchy when they are no longer in play.

## Handle object collisions

Now that you have all these moving objects, they're bound to start colliding with each other - we need to program what should happen when everything collides.

1. If relevant, edit the **Rigidbody mass** of your objects.
2. If relevant, to change the way your objects collide, create a new **Physics material** for your objects.
3. Add **tags** to your objects so you can accurately test for which objects are colliding with witch.
4. Use `OnCollisionEnter()` (for Rigidbody collisions) or `OnTriggerEnter()` (for trigger-based collisions) to **Destroy** or **Log** messages to the console what should happen when certain collisions occur.

By the end of this step, objects should destroy, bounce, or do nothing based on collisions.

## Make objects into prefabs

Now that the objects are basically behaving the way they should, if they're going to be instantiated during gameplay, they need to be prefabs.

1. In the Assets directory, create a new **Folder** called "Prefabs".
2. **Drag** in each object to create a **new prefab** for it.
3. After all objects hae been turned into prefabs, **delete** then from the scene.
4. **Test** the objects behavior by dragging them from the Prefabs folder into the scene while the game is running.

By the end of this step, all objects that will be spawned during gameplay should be prefabs and should no longer be in your scene.

## Make SpawnManager spawn Prefabs

Now that we have all of our prefabs set up, we can create a spawn manager to spawn them at intervals and, if we want, in random locations.

1. Create an empty "Spawn Manager" object and attaach a new SpawnManager.cs script to it.
2. Create individual **GameObject or GameObject array** variables for your prefabs, then **assign** them in the inspector.
3. Use the `Instanciate()`, `Random.Range()`, and the `InvokeRepeating()` methods to spawn objects at intervals(random objects, random locations, or both)
4. Right-click on your Assets folder > **Export Package** then save a new version in your **Backups** folder.

By the end of this step, objects should be spawned automatically from the apprepriate location.

## Replace all primitives with new asset

1. Drag the Player object into the "Prefabs" folder to make it a prefab, then double-click on it to open the prefab editor
2. Drag the asset you want into the hierachy to make it a **nested prefab** of the Player, then scale and position it so that it is around the same size and location.
3. On the parent Player object it self, either edit the collider to be the size of the new asset or replace it with a different type of collider.
4. Test to make sure it works, then uncheck the Mesh Renderer component of the primitive.
