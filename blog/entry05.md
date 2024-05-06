# Entry 5
##### 5/5/24

### Context 
I'm currently in the EDP of *communicating the result*, so then I can improve on my MVP. which also means my [MVP](https://www.roblox.com/games/16620055741/FreeBlox-World) should be done and ready expo somewhere on June 10, but was due on May 1. Over the month of working on my project, I felt, like it was very bad until I saw some of my friend's projects. I know some may haven't fully finished their project, but it looks great already. Before the due on May 1, I had to complete many tasks and also change my objectives throughout development, so changing from a fighting RPG that I found very hard to finish. I have made a functional chest exploration RPG. Overall my final goal is still to make an open-world exploration RPG.

### GUI
After completing my punching code and running the code that I receive from YouTube. I have started working my a semi-finished GUI where player can see their stats, inventory, collection, and crafting. To complete this I started creating a `GUISCreen` in the Roblox addon then inside I added a frame - changing its attributes such as size(scale), color background, etc. I found this very similar to HTML and CSS, but it doesn't use code but is similar to like addon, and the addon is an attribute for you to customize. The only functional code here was when the player joined and when they clicked the menu the GUI would show on the player `Name: #######`, it will become the player user when they join. 

### GUI Overview
![Screenshot (38)](https://github.com/jimingz9380/apcsa-freedom-project/assets/91745086/fda42e0d-10ba-4ae2-8272-e197de841a79)


### GUI script
```js
//player name script
local player = game.Players.LocalPlayer
local Name = script.Parent
Name.Text = "player: " .. player.Name
```
```js
//button script
local SGui = script.Parent
local frame = SGui:WaitForChild("guiFrame")
local button = SGui:WaitForChild("Button")
local button1 = game:GetService("StarterGui")

button.MouseButton1Up:Connect(function()
	
	frame.Visible = not frame.Visible
end)
```



#### Chest Searching 
In my previous log, I had created a model of my chest, but there was no function to it. I have to finish the MVP with the chest able to do something when the player interacts with it. 
```js 
local parent = script.Parent
local frame = parent:WaitForChild("Popup")
local getPlayer = game:GetService("Players")


parent.ProximityPrompt.Triggered:Connect(function(player)
	
	local sound = script.ding
	sound:Play()
	
	print("Congulation you have found a red chest!")
	local gui = parent.Popup:Clone()
	gui.Parent = player.PlayerGui
	wait(3)
	player.PlayerGui.Popup:Remove()
end)
```
When the player goes to the chest and clicks on it for 1 second, it will state "Congratulations, you found [color] chest". My next step for this was creating a badge when the player finds all the chests, it will give them a badge, but couldn't do it, so I only created a script that gives a badge to the player when they first join.

### Map Overview
While creating my punching and running code I also created a very simple map for the player to explore around to find the chest here is what the map looks like!
![Screenshot (36)](https://github.com/jimingz9380/apcsa-freedom-project/assets/91745086/e3be0490-fffc-43c7-9cd2-d83299efc80b)

### Device friendly 

My last goal before finishing the MVP is during my expo. I wanted my user to be able to play the game on mobile without device accessibility. They would need a computer to use to test out my game. The task was very hard I hard to use [roblox documention](https://create.roblox.com/docs/input/mobile) again. I made a code for it, but the conflict was I couldn't make it stop when the player clicked it again, so I looked at [youtube](https://www.bing.com/videos/riverview/relatedvideo?&q=roblox+mobile+sprinting+&&mid=B06D85914961A36EFF27B06D85914961A36EFF27&&FORM=VRDGAR) if there was another way, which there is a player had made a sprint button into a GUI and then add the script to it. 

```js
//it allow player to script, but doesn't stop sprinting
local Players = game:GetService("Players")
local localPlayer = Players.LocalPlayer

local character = localPlayer.Character or localPlayer.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

local function handleAction(actionName, inputState, input)
	
	
	if inputState == Enum.UserInputState.Begin then
		print("true")
		humanoid.WalkSpeed = 32
	else 
		print("false")
		humanoid.WalkSpeed = 16
	end
	
end


local function onRunning(speed: number)
	if speed >= 16 and Rstate then 
		humanoid.WalkSpeed = 32
		print("32")
	else if speed == 32 and not Rstate then 
		print("16")	
		humanoid.WalkSpeed = 16
		end
	end
-end

humanoid.Running:Connect(function(speed: number)
	onRunning(speed)
end)

ContextActionService:BindAction("RunBind", handleAction, true, Enum.KeyCode.LeftControl)
ContextActionService:SetPosition("RunBind", UDim2.new(0.2, 0, 0.5, 0))
ContextActionService:SetTitle("RunBind", "Sprint")

```
```js
//solution after I convert it into a GUI button for sprinting
local userinput = game:GetService("UserInputService")
local btn = script.Parent
local Players = game:GetService("Players")
local localPlayer = Players.LocalPlayer

local character = localPlayer.Character or localPlayer.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

btn.Activated:Connect(function()	
	if not humanoid then
		return 
	end
	
	if humanoid.WalkSpeed == 16 then 
		humanoid.WalkSpeed = 32 
	else
		humanoid.WalkSpeed = 16
	end	
end)

if userinput.KeyboardEnabled then
	btn.Visible = false
else
	btn.Visible = true
end
```
### Takeaway 
This blog has helped me develop my skills in embarrassing failure and how to learn because, in the end, I feel like my projects aren't great compared to others. This is why I learned that the main goal is to learn what I created because despite the tools I used they might be easier or harder than mine to create a project. Sometimes I also need to see some failure before I can improve on my work such as my mobile-friendly code. All that matters right now is MVP(Minimal Viable Product) which I did complete and should be happy about.


[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
