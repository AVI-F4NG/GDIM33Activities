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