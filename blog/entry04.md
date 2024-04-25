# Combat & Coding
##### 4/25/24

### Context
After develop some code for my running and crouching. I continue to work on the code I shoudl be doing which is a combat system. This code change my idea of how my game would turn out because it involve multiple folder and file. Though the challenge was completed, it isn't a perfect combat system and it lack combat flow. When testing it player would have to stand still in order to hit each other. This left me struggle for a long time, but still continue with a few change in mind by chanigng he purpoose of the game. 

### Challenge - Combat
In the combat challenge I went on youtube and look what code would be helpful to develop [comnbat](https://www.youtube.com/watch?v=t-LTrFvlwiY) because there are many type of code that exist within roblox documentation. For example through the video there a small part of the code that require `FindFirstChild` which I had no clue what it use for and why it is needed for the combat code. This allow me to research the [code](https://create.roblox.com/docs/reference/engine/classes/Instance#FindFirstChild). Which I found that FindFirstChild is an instance that find the child your looking for depeding on which parent you selected. Another problem I encouter was the after watching the video and the video require for it, I need to understand why they add script into different folder/files. To understand I went to roblox document and another part of youtube to understand by default the roblox creator script will automatically transfer to the player when they join the game depending on which file the game developer put the script in.



### File 1
I put this script into `StarterCharacterScripts` throught her parent of `StarterPlayer`. This folder allow player who join by default haivng the abiliyt ot punch left and right through when they click.

```
local player = game.Players.LocalPlayer
local UIS = game:GetService("UserInputService")

local Combo = 0
local debounce = false

UIS.InputBegan:Connect(function(input, gpe)
	if gpe == true then 
		return 
	end 
	
	if input.UserInputType == Enum.UserInputType.MouseButton1 then 
		if debounce == true then return end
		debounce = true
		
		if Combo == 0 then 
			local animation = player.Character.Humanoid:LoadAnimation(script.LeftPunch)
			animation:Play()
			Combo = 1
		elseif Combo == 1 then
			local animation = player.Character.Humanoid:LoadAnimation(script.RightPunch)
			animation:Play()
			Combo = 0
		end
		
		wait(0.2)
		game.ReplicatedStorage.CombatHit:FireServer()
		print("Left Punch")
		wait(0.2)
		debounce = false
		
	end	
	
	--local animation = player.Character.Humanoid:LoadAnimation(script.RightPunch)
	--animation:Play()
	
end)
```

### File 2
This script I put in a folder call `ServerScriptService`, I don't really know how to explain this folder, but in default when the server is created the entire server would have the script running the entire time. Thus meaning when the player click through their mouse, it would transfer and input onto the server script and run this code. It will allow any player who did the interaction.
```js
game.ReplicatedStorage.CombatHit.OnServerEvent:Connect(function(player)
	// attribute on the hitbox that being created
	local hitbox = Instance.new("Part")
	hitbox.Parent = workspace 
	hitbox.Anchored = true
	hitbox.CanCollide = false
	hitbox.Transparency = 1
	hitbox.Size = Vector3.new(4.5,5,5.5)
	hitbox.CFrame = player.Character.HumanoidRootPart.CFrame * CFrame.new(0,0,-2)
	game.Debris:AddItem(hitbox, 2)
	
	local Hits = {}
  //function that make player that take damage within the hitbox
	hitbox.Touched:Connect(function(hit)
		if hit.parent:FindFirstChild("Humanoid") and hit.Parent.Name ~= player.Name then 
			if not hit.Parent.Humanoid:FindFirstChild(player.Name) then 
				if Hits[hit.Parent.Name] then
					return 
				end
				Hits[hit.Parent.Name] = true 
				local snd = script.PS:Clone()
				snd.Parent = hit.Parent:FindFirstChild("Humanoid")
				snd:Play()
				game.Debris:AddItem(snd, 2)
				hit.Parent:FindFirstChild("Humanoid"):TakeDamage(5)
				wait(4)
				Hits[hit.Parent.Name] = false
			end
		end
		
	end)
	
end)
```

### Modeling - Chest
Within the completion of the combat system which was very confusing for my to created I mention that I would change the purpose of the game currently. Depsite change the purpose, my end goal would be still finishing the open world rpg game, but atleast having something done by the MVP. The decision was an open rpg world would have chest exploration, so I made model for my chest

#### Inspiration
![Screenshot (33)](https://github.com/jimingz9380/apcsa-freedom-project/assets/91745086/3fd08ddd-7de8-4347-a02a-dbb1eebac079)

#### My model(Chest)

![Screenshot (32)](https://github.com/jimingz9380/apcsa-freedom-project/assets/91745086/9980d702-7fef-41a5-80c7-76f68b18f39e)

### Takeaway


[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
