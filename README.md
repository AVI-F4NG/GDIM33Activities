# GDIM 33 In-Class Activities
## W1
### Activity 1

#### Question 1
Pinterest board: [link](https://pin.it/6HHlOmha6)

#### Question 2
1. Non-game aesthetic: buildings, cyberpunk, color contrast (dark vs vibrant), stairs, walls, atmospheric; game mechanics: exploration, escape room, unlocking doors, finding a way, slightly unsettling

2. Talked to my table mate Jeremy and found out that we both like anime-style art and rhythm games.

3. Talked to LA Elijah: a discussion on the gameplay and environmental storytelling of the game Death Stranding.


### Activity 2

Break-down:
![gdim33 pitch breakdown](https://github.com/user-attachments/assets/e634c16f-6bc1-411a-ba97-e3b4581715ed)



## W3
### Activity 1
<img width="1483" height="964" alt="gdim33 pitch breakdown" src="https://github.com/user-attachments/assets/825a30e4-f9d9-487f-8918-0f8df98b9efd" />

### Activity 2
#### Question 1
Saving the explore-to-dialogue event name as a Scene variable is useful because it gives the event a single shared source of truth. The walrus graph and the state transition both reference the same variable. That reduces typo risk, makes the setup easier to change later, and scales better if reused the pattern for other NPCs. It also keeps the graph more organized, since the event name is treated as reusable scene data rather than a random string buried inside one node.
#### Question 2
When clicking the walrus, a log after OnMouseDown can confirm that the click was detected and that interactionAllowed was true. This makes it much easier to isolate problems at an intermediate step, and easier to tell whether the issue is with the click detection, the event call, or the transition itself.
#### Question 3
Set Cursor Lock State is not very relevant to this vertical slice. Since my vertical slice is a 2D adventure puzzle game built around moving through rooms and clicking or interacting with objects/UI, the mouse cursor usually needs to remain visible and usable, especially if the game includes buttons, prompts, or keypad-style interactions.
#### Question 4
The concept of a game state is relevant to this vertical slice. The vertical slice depends on the game knowing what stage of progression the player is currently in. The states control what objects do, which doors can open, and what interactions are available. Without game states, it would be much harder to manage the player’s progression.

## W4
### Activity 1

Playable: basic player movement in 2D space, item pick-up, prompt UI, simple inventory UI, key pick-up/door unlock/advance to next room sequence.

Goals: want to know what the game space / visual cues tell the player, whether the player achieves the level goal without textual guidance, and whether the game runs functionally or not.

Playtest team: Jingyi Cheng (me), Jeremiah Yang, Brandon Tsay, Ke-Chieh Chang

Playtest Notes: the players tried to interact with the computer with stuff on its screen, which is the intended first interaction item to be implemented in the future. After learning that the computer's functions aren't implemented yet, players moved on to the key card nearby, which is intended to be the first item to be picked up for this round of functionality playtest. After picking up the key card, the players tend to explore the room for a while before interacting with the escape door. Because I only have one level available, the playtests went pretty quickly and smoothly, and all the playtesters have successfully reached the end goal of this playtest content.

### Activity 2

#### Question 1

Yes, because all the dialogue lines and their reply option logic are stored in ScriptableObjects, which do not require modifying code.

#### Question 2

There is no limit to the total number of nodes that could be created, but each dialogue line only supports 4 choices due to the UI limitations.

#### Question 3

It rebuilds the visual scripting node database so the updated script members become available in graphs. If added or changed variables, methods, classes, or properties in C# scripts, the graph may not immediately show the new members. 

## W5

### Activity 1

1. Build the first visible progression gate: collect Key Card 1 and unlock the first door

(1) Create the KeyCard1 object with a trigger collider and place it in Room 1. When the player enters its range, print Near KeyCard1 with a Debug Log to confirm detection is working.

(2) Add interaction logic so pressing E while near the key card deactivates the key card object. Test by running the game and confirming the key card disappears only when E is pressed.

(3) Create the first locked door between Room 1 and Room 2. Make it block the player before the key card is collected. Test by running the game and confirming the player cannot walk through it at first.

(4) Add unlock logic so pressing E at the door after collecting the key card deactivates or opens the door. Test by running the game and confirming the player can now enter Room 2.

2. Add the next progression layer: find the USB and activate the computer event

(1) Create the Room 1 computer as an interactable object that displays the first clue. Test by running the game and confirming the clue appears when the player presses E near the computer.

(2) Create the concealed box in Room 2 and place the USB inside it. Test by running the game and confirming the USB can be collected and disappears after pickup.

(3) Add logic so the computer behaves differently after the USB is collected. When the player returns and interacts again, print USB detected at computer with a Debug Log. Test by checking that this only happens after collecting the USB.

(4) Add the virus prompt and make choosing Yes activate the next puzzle state. Test by running the game and confirming that the prompt appears and only the Yes choice advances progression.

3. Build the full puzzle chain: monitor clue, passcode door, maintenance puzzle, and final exit

(1) Create the 9-monitor flash sequence in Room 1 and trigger it after the virus prompt. Test by running the game and confirming the monitors visibly flash in a fixed pattern.

(2) Create the passcode door in Room 2 and make it open only when the correct code is entered. Test by entering a wrong code first, then the correct code, and confirming only the correct one unlocks the door.

(3) Create the directional floor puzzle in Room 3. Test by running the game and confirming the player is reset or stopped when taking the wrong path, and can reach the end on the correct path.

(4) Place KeyCard2 at the end of the floor puzzle and connect it to the final stairway door in Room 2. Test by running the full game and confirming the player can only escape after completing the puzzle and collecting KeyCard2.

### Activity 2

Added interactable UI to the computer in Room 1, so that the player can interact with the screen with artifacts on it and see a popup screen with the contents of an old computer's desktop. Also added the 1st key card clue ("The key card is in the flower pot").

Added a script that gives DontDestroyOnLoad() to the player GameObject, so that it persists across different scenes.

## W6

### Activity 1
1. what is NEW in your build since your Milestone 1 submission

- A second room for exploration
- The computer screen to show the first clue and prepare for the complicating factor

2. a link to your Itch page
Link: [itch](https://lum3ni.itch.io/gdim-33-ms2)

3. your playtesting goal(s)
- To find if there are any unresolved bugs within the game
- To see if the game is intuitive enough to be played through without hints

4. Playtest notes: one of the playtests found out that the collider setup after the first door is unlocked is incorrect, resulting in the player to teleport to the second room no matter what collider they touch. The cause is found within the player graph, which didn't compare the collision object's tag and instead triggers the scene change when the player's collider collides with any collider.

### Activity 2

1. Why does the Multiply setting of the Blend node make the resulting color darker and less saturated than the input colors?

Because the multiply option multiplies the values given, so a vector A = (R1, G1, B1) Blended with a vector B = (R2, G2, B2) with the Multiply option will result in a vector C = (R1*R2, G1*G2, B1*B2), which results in the three values in the vectors becoming higher because of the multiply

2. If we use Multiply to combine Alpha values, will the resulting value be more or less translucent than either of the original values, and why?

More translucent, since the values are all between 0.0 and 1.0, which results in the values becoming smaller and smaller as they multiply with each other, and the smaller the alpha values is, the more translucent the material gets.

3. When we created the SampleTexture2D node, Unity auto-created the UV0 Node for us to get the UV coordinates for sampling the texture. Where does the shader get these UV values from?

The UV value comes from the data stored in the vertex of the 3D mesh

4. You just learned that you can manipulate colors with math. Does that sound interesting or exciting to you?

Yes. Because this way I can better control colors with mathematical operations and manage materials in a more efficient way.

## W7

1. Directly from the mesh data of the active object. This information is painted onto the vertices, or imported, and stored within the geometry itself.
2. Because they are stored on individual vertices rather than on pixels, and the GPU linearly interpolates color across the face between these points.
3. Color resolution is limited by mesh density (vertex count), while textures are independent of geometry, allowing more detailed texture by pixels.
4. It looks good
5. The tangent value (represents the direction that points along the horizontal texture) axis of the surface at the position of the vertex. Debug shaders allow us to visualize the tangent space, detecting errors from incorrect mesh UVs.
6. Because the light direction vector is pointing towards our shiba, but the shiba’s normal vectors are pointing away from itself. When we try to compare the angle between these vectors, if the polygon on the shiba is facing the light, we’re going to get a negative value, and therefore this area of the shiba will be dark.
7. The additive blend mode sums the color values of the source with the destination, creating a brightened effect where lighter colors appear and black remains transparent.

## W8

### Activity 1

1. Added a maze prototype for the 3rd room
2. Link: [Itch](https://lum3ni.itch.io/gdim-33-ms3)
3. Figure out how intuitive my game is and whether there's any bugs present with the new area

### Playtesting Notes
1. The player is moving too slow
2. The different door controls are confusing (make all doors enter-able upon collision instead of requiring the E key)
3. The password entry screen should disappear automatically after a successful entry
4. A bug with the maze/lounge scene change: the player teleports to outside the map if the player is on a location in room3 that correponds to a point that is outside the wall in room2, causing the player to be permanently stuck and can only get unstuck by restarting the game.

### Acticity 2 (2B)

1. The Fraction node turns continuously increasing time into a looping value. The time value keeps increasing forever: 0.0 -> 0.1 -> 0.2 -> ... -> 1.0 -> 1.1 -> 1.2 -> ... -> 2.0... But Fraction(Time) only keeps the decimal part: 0.0 -> 0.1 -> ... -> 0.9 -> 0.0 So it creates a repeating 0 -> 1 -> 0 -> 1 which is added to the UV of the shine texture, which makes the shine texture slide across the sprite repeatedly.
2. Because the shader uses an Add node: Main Texture + Shine Texture. In the add math within shaders, black is represented by 0 (therefore it's transparent). So, original sprite + black = original sprite. That means the black parts of the shine texture do not visibly affect the sprite. Since the poof texture has a black background with a soft white circle, the black area stays invisible while the white blurred circle becomes the glowing shine. If the Shine texture were white or bright by default, then the Add node would brighten the whole sprite all the time, not just the shine area.
3. Because the building texture is only a default value for MainTex inside the Shader Graph. For sprites, the material's MainTex is automatically filled by the actual sprite assigned in the SpriteRenderer, as long as the property is named "MainTex". So when the material is used on a real SpriteRenderer, Unity replaces MainTex with that object’s own sprite texture.
4. Because Fraction(Time * ShineSpeed) changes the speed of the loop. Fraction(Time) * ShineSpeed changes the range of the UV displacement after the loop, resulting the Fraction(Time) value taken by the UV of the shine texture to be limited to 0.5 if the decimal value is set to 0.5, resulting in the UV sliding only halfway across the texture before restarting, cutting off the smooth fading effect of the other half of the texture.

## W9

### Activity 1

Game: Minecraft

1. Nausea effect: a post-processing effect that distorts the entire screen view of the player. Instead of applying the rendering effect on every object in the scene, it is more doable if the developers just applied a post-processing effect. The trigger condition is whenever the player gets affected by the "nausea" effect in-game.
2. Mobs get red after getting hit: probably a color change applied to the object's material, triggered every time damage is detected on the mob, and lasts for about half a second before automatically cancelling itself.

### Activity 2
I have finished the entire shader graph last weekend, so I asked someone else to playtest my game and found some room for improvement, and focused on fixing those issues instead.

Link to [commit](https://github.com/AVI-F4NG/VerticalSlice33/commit/823b1758c1086a918405531b17fbd7d3aeec76c8)

Updates:
- Tuned down the player's movement speed a little bit so the player isn't fast enough to break into nearby colliders if a movement key is pressed continuously during scene switches.
- Added "delete" and "quit" buttons to the password entry screen as per a playtester's advice
- Added a prompt to the "strange picture" whenever the player is close to it, so the player will know that it's interactable.

This is a screenshot of the shader graph that I made:
<img width="3814" height="1541" alt="Screenshot 2026-05-24 182814" src="https://github.com/user-attachments/assets/7308d523-34c6-4dcb-a5a1-5abd228c54d7" />
