# Unreal Engine Project - TestExamTP
 Third Person Project using Unreal Engine 5.3.2
 
 <br />

### Scene Overview
This is the scene overview that shows all the actors within the scene which is the: Character, Enemy, Door, PickupObject and the final destination Trigger.<br />
The map used is the Third-Person template map provided by Unreal Engine.<br />
![SceneOverview-1](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/e4bfcbc6-bcbe-4783-a5f9-ccebe4f718e2)
### Character
This is the character model I used that I downloaded from Adobe's ![Mixamo](https://www.mixamo.com/#/) which is named 'May'<br />
![CharaModel-1](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/51d00bfb-34de-4a27-9338-02463b48d1e1)

The first controller blueprint logic provides a way for the character to move within the 3D world.<br />
It takes in a Input Axis Movement which I named **GoForward/GoBackwards** and **GoLeft/GoRight** and passes it the **Add Movement Input** function.<br />
I added a **Get Control Rotation** function so that the character always faces the direction she's going. <br />
![CharaController-1](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/ec3192ef-3f79-4d1d-8a53-7d66d559a1d4)

The second blueprint is the camera control function which adjusts the camera's movement based on the mouse movement on the X and Y coordinates as an Input Axis Movement.<br />
![CharaController-2](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/5894c5f0-84f4-4ee4-870e-96943f73cdd5)

The third blueprint is where I added a **Sprint and Jump** functionality to the player so they can traverse the level with different styles.<br />
In this implementation I set up the default analog speed of the character to be **300 m/s** instead of **0 m/s** so that it starts with the walking speed. <br />
![CharaController-3](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/ad47ca46-2a8d-477b-9030-9a795da8270d)

The last blueprint is a practice I have which is called an **On Begin Event or OnInit (short for On Initialize)** in which I first create the widget for the objectives UI
to be displayed on the screen, and set the starting speed of the character to be 300 m/s. <br />
![CharaController-4](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/9cdb1113-c734-4bab-9ee6-3cdfeb885531)
![UiWidget-1](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/ba99f2aa-a29c-4fed-b3c2-edbc2b3d8256)

### Enemy
This is the Enemy model that I downloaded also from ![Mixamo](https://www.mixamo.com/#/) called AJ (The surface mapping texture of the face on AJ is broken when importing the .fbx file of AJ)<br />
![EnemyModel-1](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/c80eb9df-68bc-4d72-9d1e-73326cf15083)

The main AI logic for the enemy uses the standard AI function from Unreal Engine called **AI Move-To** which follows the Player Controller blueprint class and whichever actor its inside it. I added a **Chase Player** function to be able to call it from the **On Begin Event** as well as a delayed update runtime and gets called whenever the player gets too far from the AI (which is set to 15m or 150). <br />
![SimpleEnemyAI-1](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/b6f4e36f-e09d-43ff-8e43-1d9cf00d3e95)

### Simple door logic with rotation
This the main blueprint for a simple door interaction trigger which has a text widget to indicate to a player which key to press. In this case, I chose the key 'E' which is also the most used key in video games for simple interactions with the level. <br />
The door blueprint also has a timeline component to smooth the rotation of the door which is set to 0 degrees and 90 degrees respectively. <br />
Lastly, the door is opened with a **Flip-Flop** function to alternate the output to being opened or being closed without the need for a **Branch Component** since we're only targetting two states of the door which is opened or closed. <br />
![SimpleDoorLogic-1](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/80efe67c-6f0e-429d-af94-30d78e252474)

The smoothing is set to 1.5 so it won't open instantly and instead smoothly transtion to the rotation.<br />
The door smoothly transitions from 0 to 90 and vice versa.<br />
![SimpleDoorLogic-2](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/7e23f92c-33ae-467b-8cbe-c73d2a60b505)

### Objectives and pickup
This is the object to pickup as an objective of the player which is situated here on the level.<br />
![ObjectPickup-2](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/8e73590d-e49f-4c38-9506-c081070abd7c)

It has a sphere bounds collision which detects if the player is inside the bounds and can interact with it.<br />
If the player then picks up the object, the objective will be updated and destroy the actor (I may choose to disable it only but in this context I used the destroy function instead).<br />
![ObjectPickup-1](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/f79c5504-edfd-4ffe-8d27-58f3ea7d7631)

It then calls the function of **Update Objective** in the character controller's blueprint to update the current tracked mission and the text.<br />
![CharaController-5](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/f5a26889-c3c5-4471-a7de-9dc5c2f72607)

### Objective tracker boolean - value
In order to track if the player has already picked up the object, I added a variable of type boolean in the character controller blueprint so I can set it to true when the player picks up the object. <br />
![CharaController-6](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/906a574a-7532-44cf-a82e-06b289add92f)

And lastly, here is the final trigger bounds that I set up as an actor on the scene and checks the variable **Has Object** of type boolean on the character controller in order to complete the objective and subsequently update the text on the widget.<br />
![FinalTrigger-1](https://github.com/Mashyyyy/Unreal-Engine-Project---TestExamTP/assets/76673249/4259c0b8-8a48-454d-9454-e3aa3ec3de5a)
