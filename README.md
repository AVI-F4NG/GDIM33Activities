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
