# Ex.No: 10  Implementation of 2D/3D game- Obstacles Game
### DATE:                                                                            
### REGISTER NUMBER : 212223230150
### AIM: 
To develop a 2D game in Unity where the player must jump over obstacles to survive and score points.
### Algorithm:
```
1.Create a new 2D Unity project.
2.Add a Player GameObject (e.g., a square or character sprite).
3.Add a Ground GameObject and ensure it has a BoxCollider2D with the tag "ground".
4.Add an Obstacle (Spike) GameObject with its own collider.
5.Create and attach a PlayerScript to the Player for jump control.
6.Create and attach SpikeGenerator and SpikeScript to handle obstacle spawning and movement.
7.In the PlayerScript, use Rigidbody2D and input handling to make the player jump when grounded.
8.In the SpikeGenerator, spawn spikes periodically at a fixed speed.
9.In the SpikeScript, move the spikes from right to left and generate new ones as they pass.
10.Test the scene and ensure collision detection and jumping mechanics work properly.
```  
### Program:

### PlayerScript.cs
```
using UnityEngine;

public class PlayerScript : MonoBehaviour
{
    public float JumpForce;
    [SerializeField] bool isGrounded = false;
    Rigidbody2D RB;

    private void Awake()
    {
        RB = GetComponent<Rigidbody2D>();
    }

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space) && isGrounded)
        {
            RB.AddForce(Vector2.up * JumpForce, ForceMode2D.Impulse);
            isGrounded = false;
        }
    }

    private void OnCollisionEnter2D(Collision2D collision)
    {
        if (collision.gameObject.CompareTag("ground"))
        {
            isGrounded = true;
        }
    }
}

```

## SpikeGenerator.cs

```
using UnityEngine;

public class SpikeGenerator : MonoBehaviour
{
    public GameObject spike;
    public float MinSpeed;
    public float MaxSpeed;
    public float CurrentSpeed;

    void Awake()
    {
        CurrentSpeed = MinSpeed;
        GenerateSpike();
    }

    public void GenerateSpike()
    {
        GameObject SpikeIns = Instantiate(spike, transform.position, transform.rotation);
        SpikeIns.GetComponent<SpikeScript>().spikeGenerator = this;
    }
}
```
## SpikeScript.cs

```
using UnityEngine;

public class SpikeScript : MonoBehaviour
{
    public SpikeGenerator spikeGenerator;

    void Update()
    {
        transform.Translate(Vector2.left * spikeGenerator.CurrentSpeed * Time.deltaTime);
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.gameObject.CompareTag("nextLine"))
        {
            spikeGenerator.GenerateSpike();
        }
    }
}

```
### Output:
<img width="1665" height="910" alt="image" src="https://github.com/user-attachments/assets/1b4e7f4c-1b79-49ac-bc1f-acc539ab131b" />

### Result:
Thus the game was developed using Unity and adopted _-----------AI technology.
