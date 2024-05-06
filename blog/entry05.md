# Entry 5
##### 5/5/24

### Context 
I'm currently in the EDP of communicate the result, so then I could improve on my MVP. which also mean my MVP should be done and ready expo somewhere in June 10, but was due on May 1. Over the course of the month on working my project I feel, like it is very bad until I see some of my friend project. I know some may have comepletely finished their project, but it look great already. Before the due on May 1, I had to complete many task and also change my ojective over the course of develop. So changing from an fighting RPG that I find very hard to completely finished. I have made a functional chest exploration RPG. Overall my final goal is still to make an open World exploration RPG.

### GUI
After completing my punching code and running code that I recieve from the youtube. I have started working my a semi finished GUI where player can see their own stats, inventory, collection and crafting. In order to complete this I started creating a `GUISCreen` in the roblox addon then inside I added frame - changing it attribute such as size(scale), color background etc. I found this very similiar to HTML and CSS, but it doesn't use code but similiar to like addon and the addon as it own attribute for you to costumize. The only functional code here was when the player join and when they click the menu the GUI would show and on the player `Name: #######`, it will become the player user when they join. 

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
In my previous log I had created a model my chest, but there were no functional to it. I have to finished the MVP with the chest able to do something when the player interact with it. so I created this code
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
When the player go to the chest and click on it for 1 second, it will state "congratulation, you found [color] chest". My next step for this was creating a badge when the player find all the chest, it will give them a badge, but cound't do it, so I only created a script that give a badge to the player when they first join.

### Map Overview
While creating my punching and running code I had also created a very simple map for player to explore around to find the chest and here what the map look like!

![Screenshot (36)](https://github.com/jimingz9380/apcsa-freedom-project/assets/91745086/e3be0490-fffc-43c7-9cd2-d83299efc80b)

### Takeaway 




[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
