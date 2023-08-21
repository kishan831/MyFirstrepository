# Multiplayer-FPS

## Requirement

[Unity 2020.3.4f1 (LTS)](https://unity.cn/release-notes/lts/2020/2020.3.4f1)

## Game logic and functionality

* Login panel
  * Input your **player name** and the **room name** you want to join
  * Click **'join or create room'** button to join a room or create a new room
  * The network connection state shows on the bottom left corner
    ![img](Images/2.jpg)

* Game interface
  * **Player's HP** on the top left corner
  * The **message panel** on the bottom left corner, which shows status of other players (e.g. dead or respawn)
  * A **gun (AK-47)** is always shown on the bottom right corner in front of every thing you can see
  * A red **shooting sight** is always in the center of the screen
  <img src="Images/3.jpg" style="width:500px"></img>

* Player models
  * All the original models and their animations were found from **[Mixamo](https://www.mixamo.com/)**, which is a pretty good game model website run by Adobe
  * There are three types of player **models**:
    * **Policeman**: a policeman-like model with yellow skin
    * **RobotX**: a robot-like model with dark pink skin
    * **RobotY**: a robot-like model with dark blue skin

  * **Animations**:
    * **Walk** towards four different directions
    * **Run** towards four different directions
    * **Jump** without affecting upper part body (**achieved by unity3d body mask**)
    * **Shoot** without affecting lower part body (**achieved by unity3d body mask**)
    * **Unity Blend Tree**
      * This makes the player walk or run more naturally. It uses interpolation function to map different combinations of user input to different animation
        
  * **State Machine**
    * There are multiple layers in the player state machine.

* Player movement
  * Walking && Running && Aiming
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594065/02a72084-c429-11e5-84b7-39de1a51d991.jpg" style="width:420px"></img>
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594070/02be2234-c429-11e5-874a-880a710742c1.jpg" style="width:420px"></img>
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594601/c34c19f0-c42b-11e5-9c90-2f2e384030ef.jpg" style="width:420px"></img>
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594069/02b960be-c429-11e5-90b1-49e0ff6be56a.jpg" style="width:420px"></img>
  * Jumping
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594068/02b1568a-c429-11e5-9bbe-cee8760c079b.jpg" style="width:420px"></img>
  * Dying
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594067/02abdd9a-c429-11e5-887f-0c830090ff49.jpg" style="width:420px"></img>
    * <img src="https://cloud.githubusercontent.com/assets/5276065/12594066/02aa6d34-c429-11e5-86ce-ef458bb7f7c3.jpg" style="width:420px"></img>

* Gun model
  * The original gun model (AK-47) was from Unity Assets Store
  * **Shooting animation are added** by setting keyframes in unity3d animation panel


* Door animation
  * Doors will automatically open when there is someone nearby and close when no one is around.

## Script files

* **CameraRotation.cs**
  * Rotates the scene camera in every updated frame
* **DoorAnimtion.cs**
  * Controls the door animation and detect if the player enters or exits the door triggering area
* **FpsGun.cs**
  * Controls the gun in first person view, mainly for shooting
* **TpsGun.cs**
  * Controls the gun in third person view (replicated on network), mainly transform and particle effects
* **IKControl.cs**
  * Ensures the model is holding a gun regardless of movements or rotations
* **ImpactLifeCycle.cs**
  * Destroys the bullet object after several seconds to save CPU time and memory
* **NameTag.cs**
  * Displays other players' names above their heads
* **NetworkManager.cs**
  * Controls the whole network connection
* **PlayerHealth.cs**
  * Calculates and updates health points of each player
* **PlayerNetworkMover.cs**
  * Synchronizes the position of the player among different clients

### Input Devices

* Mouse and keyboard
  * The traditional way
  * Cheap and easy to use
