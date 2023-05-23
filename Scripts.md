## Access modifiers 访问修饰符
It's good practice to make all member variables those that belong to a class rather than a function private, unless they need to be publiv for a specific reason.

`Private` the **default** access modifier for any variable that doesn't have it specified, the variable can only be editd from whithin the class

`Public` the variable can be accessed from outside the class, and is shown and editable on the componemt in the inspector. **A variable initialized in the `class` to a default value will be overridden by the value that's written in the inspector, but if it's set in functions such as `Start` and `Awake`, it will not be overridden by the inspector.**

## Value & Reference

# Value

Value type variables contain some value. If a value type changes, only that specific variable is affected.

- `int`
- `float`
- `double`
- `bool`
- `char`
- `Structs`
  - `Vector3`
  - `Quaternion`

# Reference

Reference type variables contain a memory address where the value is stored. If a reference type changes, all variables contain that memory address will also be affected.

- `Classes`
  - `Transform`
  - `GameObject`

## Class

`Awakez(){}` called first **even if the script component is not enabled**, and is best used for setting up any references between scripts and initialization. Only be called once in the lifetime of a script attached to an object, cannot repeat by disabling and re-enabling a script.

`FixedUpdate(){}` called on a regular timeline and will have the same time between calls. As such, anything that affects a rigid body, should be executed in `FixedUpdate` rather than `Update`. When scripting physics in the `FixedUpdate` loop, it's good practice to use forces for movement.

`Start(){}` called after `Awake`, immediately before the first update, but only if the script component is enabled. This allows you to delay any part your initialization code until it's really needed. Only be called once in the lifetime of a script attached to an object, cannot repeat by disabling and re-enabling a script.

`Update(){}` called once per frame on every script that uses it, almost anything that needs to be changed or adjusted regularly happens here, like the movement of non-physics objects, simple timers, the detection of input,etc. Is not called on a regular timeline, if one frame takes longer to process than the next, then the time between the `Update` calls will be different.

## Loops 循环

`do {} while ()` test the condition at the end of the body, **the body of the do while loop is garanteed to run at least once**.

`while () {}` perform an action while a condition is met.

`for () {}` creating a loop with a controllable number of iterations.

## 3D vectors

`Vector3.Cross(VectorA, Vector B)` cross product of two vectors. The cross product of two vectors results in a third vector which is perpendicular to the two input vectors.

`Vector3.Dot(VectorA, VectorB)` dot product of two vectors. The dot product is a float value equal to the magnitudes of the two vectors multiplied together and then multiplied by the cosine of the angle between them. For normalized vectors `Dot` returns 1 if they point in exactly the same direction, -1 if they point in completely opposite directions and zero if the vectors are perpendicular.

`Vector3.magnitude` returns the length of this vector.

`Vector3.normalized` returns this vector with a magnitude of 1. The current vector is unchanged and a new normalized vector is returned.

## Functions 函数

`Destroy( , timeDelay)` removes game objects or components.

`GetComponent<>()` accesses other scripts and components on the same or other game objects.

`Input.GetAxis("")` returns the value of the virtual axis. The value will be in the range -1...1. The gravity of the axis affects how fast the scale returns to 0 after the button has been released, the sensitivity controls how quickly the return value of the input reaches 1 or -1, the snap option allows you to return 0 if both positive and negative buttons are held.

`Input.GetAxisRaw(" ")` returns only whole numbers and nothing in between. This is useful for 2D games that needs precise controls rather than smoothed values.

`Input.GetButton/Down/Up(" ")` returns true while the virtual button identified by button name is held down/pressed down/released.

`Input.GetKey/Down/Up(KeyCode)` returns true while the user holds down/presses down/releases the key.

`OnMouseDown(){}` called when the user has pressed the mouse button while over the collider.

`Time.deltaTime` the interval in seconds from the last frame to the current one.

`transform.LookAt(target)` rotates the transform so the forward vector points at target's current position.

`transform.Rotate(Vector, float angle)` rotates the object around the given axis by the number of degrees defined by the given angle.

`transform.Translate(Vector)` move the transform in the direction and distance of translation.
```
// Move the object forward along its z axis 1 unit/second.
transform.Translate(Vector3.forward * Time.deltaTime);

// Move the object upward in world space 1 unit/second.
transform.Translate(Vector3.up * Time.deltaTime, Space.World);
```

`.activeInHierarchy` defines whether the game object is active in the scene.

`.activeSelf` the local active state of this game object. **A game object may be inactive because a parent is not active, even if this returns true.**

`.enabled` enable or disable a component (`component.enabled = true` or `component.enabled = false`). **Scripts are also components.**

`.SetActive()` activate or deactivate an object (`gameObject.setActive(true)` or `gameObject.setActive(false)`).
