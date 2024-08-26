using System.Collections;
	using System.Collections.Generic;
	using UnityEngine;
	
	public class movimientoplayer : MonoBehaviour
	{
		public float speed;
		public float jumpforce = 5F;
		public Rigidbody2D rb;
		// Start is called before the first frame update
		void Start()
		{
			rb = GetComponent<Rigidbody2D>();
		}
		
		// Update is called once per frame
		void Update()
		{
			float HorizontalInput = Input.GetAxis("Horizontal");
			transform.Translate(Vector2.right * HorizontalInput * speed * Time.deltaTime);
			if (HorizontalInput < 0)
			{
				transform.localScale = new Vector3(-2, 2, 2);
			}
			else if (HorizontalInput > 0)
			{
				transform.localScale = new Vector3(2, 2, 2);
			}
			
			if (Input.GetKeyDown(KeyCode.Space))
			{
				// Make the player jump
				rb.AddForce(Vector2.up * jumpforce, ForceMode2D.Impulse);
			}
		}
	}
