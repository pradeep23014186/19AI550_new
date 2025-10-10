# Ex.No: 3  Basic movements in Unity 
### DATE:                                                                            
### REGISTER NUMBER : 212223230150
### AIM: 
 To learn the basic movements translation,scaling and rotation of game objects through code.
### Procedure:
1. Setup the Scene
2. Open Unity and create a 3D Scene.
3. Add three objects:Cube → Rename to Object1 (for movement),Sphere → Rename to Object2 (for rotation).Capsule → Rename to Object3 (for scaling).
4. Add the Script,Create a C# Script → Name it TransformOperations.cs.
5. Write the code for translation,scaling and rotation,save and close the script
6. Save the script
7. Select any empty GameObject (or create one: GameObject → Create Empty).
8. Attach the TransformOperations script to it.
9. In the Inspector, assign Object1 → Drag the Cube,Object2 → Drag the Sphere.Object3 → Drag the Capsule.
10. Run the Scene Press Play ▶️ in Unity
11. Stop the program.
### Program 
```
using UnityEngine;
public class TransformOperations : MonoBehaviour
{
    public Transform object1; // Object for translation
    public Transform object2; // Object for rotation
    public Transform object3; // Object for scaling

    public float moveSpeed = 2f;  // Speed of translation
    public float rotateSpeed = 50f; // Speed of rotation
    public float scaleSpeed = 0.5f; // Speed of scaling

    void Update()
    {
        // Translate (Move) object1 along the X-axis- Time.deltaTime to make movement smooth across all frame rates
        if (object1 != null)
        {
           // object1.position += Vector3.right * moveSpeed;
               object1.Translate(0.02f,0,0);

        }

        // Rotate object2 around the Y-axis
        if (object2 != null)
        {
            //object2.Rotate(Vector3.up * rotateSpeed * Time.deltaTime);
            //object2.Rotate(0,0.02f.0);
        }

        // Scale object3 up and down
        if (object3 != null)
        {
           // float scaleChange = Mathf.PingPong(Time.time * scaleSpeed, 1f) + 0.5f; // generates a value that moves back and forth between 0 and length
           // object3.localScale = new Vector3(scaleChange, scaleChange, scaleChange);
            object3.localScale+=new Vector3(0.02f.0.02f,0);

        }
    }
}
```
### Output:

## Before Running
<img width="1512" height="846" alt="image" src="https://github.com/user-attachments/assets/5d41e5c2-bc2a-4fd4-b947-282d33162d76" />

### After Running
<img width="1444" height="849" alt="image" src="https://github.com/user-attachments/assets/1f3d7154-c8fc-4d42-ae48-7bbd601616db" />




### Result:
Thus the basic movement is learned through scripting


