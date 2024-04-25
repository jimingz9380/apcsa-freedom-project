# Combat & Coding
##### 4/25/24

### Context
After developing some code for my running and crouching. I continue to work on the code I should be doing which is a combat system. This code changed my idea of how my game would turn out because it involved multiple folders and files. Though the challenge was completed, it isn't a perfect combat system and it lacks combat flow. When testing it players would have to stand still to hit each other. This left me struggling for a long time but continued with a few changes in mind by changing the purpose of the game.

### Challenge - Combat
In the combat challenge I went on YouTube and look what code would be helpful to develop [comnbat](https://www.youtube.com/watch?v=t-LTrFvlwiY) because many types of code exist within Roblox documentation. For example, through the video, there is a small part of the code that requires `FindFirstChild` which I had no clue what it is used for and why it is needed for the combat code. This allows me to research the [code](https://create.roblox.com/docs/reference/engine/classes/Instance#FindFirstChild). I found that FindFirstChild is an instance that finds the property within a certain part which depends on which parent you selected. Another problem I encountered was that after watching the video and the video required for it, I needed to understand why they added the script into different folders/files. To understand I went to the Roblox document and another part of YouTube to understand by default the Roblox creator script will automatically transfer to the player when they join the game depending on which file the game developer put the script in.



### File 1
I put this script into `StarterCharacterScripts` throught her parent of `StarterPlayer`. This folder allow player who join by default haivng the abiliyt ot punch left and right through when they click.

```js
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
I put this script in a folder called `ServerScriptService` because the server would monitor the player actions between each other. Currently, I don't know how to explain this folder, but in default when the server is created the entire server would have the script running the entire time. This means when the player clicks through their mouse, it would transfer and input onto the server script and run this code. It will allow any player who did the interaction between two players to find the player who got hit. Then go to the parent find the humanoid property and make the player lose HP(hitpoint).
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
Upon the completion of the combat system which was very confusing for me to create, I mentioned that I would change the purpose of the game currently. Despite changing the purpose, my end goal would be still finishing the open-world rpg game, but at least having something done by the MVP. The decision was an open RPG world would have chest exploration, so I made a model for my chest.

#### Inspiration
![Screenshot (33)](https://github.com/jimingz9380/apcsa-freedom-project/assets/91745086/3fd08ddd-7de8-4347-a02a-dbb1eebac079)

#### My model(Chest)

![Screenshot (32)](https://github.com/jimingz9380/apcsa-freedom-project/assets/91745086/9980d702-7fef-41a5-80c7-76f68b18f39e)

### Takeaway
Currently, I'm in the EDP of <ins> create a prototype, Test and evaluate the prototype, and Improve</ins>. There are a lot of develop I currently have and don't have enough decide on spending a lot of time even though I spend a decent amount of time. Mostly due to my lack of ability to understand the attributes of coding and possible ways to create the combat system which possibly functions, but doesn't work well leading me to waste even more time. On the other hand, the time spending has helped me develop the skills of **growth mindset and embarrassing failure **. There were some obstacles, but had overcome them in my combat development experience.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
