# SCipting
##### 2/11/24

### Context
When I finished learning modeling from Blender I just wanted to start learning how to create an animation for certain functions on my game and then implement the animation into my script. Currently, I have just begun learning how Roblox scripting due to animation being effortless to create. The coding part of my journey was extremely hard after some smooth rides because the basic language of `lua` was fairly easy to understand, despite somehow forgetting some parts of the code I could go back to refresh my memories, but in my opinion, when I started doing the advance coding, it was very difficult. These are the steps of how I overcome my problems.

### Animation - tinker
During my time creating the animation, it was very easy to know how to create one. On the other hand, it is difficult to animate it and creativity is one of the key components. Another part is discovering the right interval of each part of an animation. Through this [tutorial](https://www.bing.com/videos/riverview/relatedvideo?q=how+to+make+animation+in+roblox+studios&mid=AFCAE11AAE636ECAA926AFCAE11AAE636ECAA926&FORM=VIRE) I understand how to create an animation then I tried to go beyond by making a running animation. This is where I started to slow down my progress because I needed to know how to implement the script of the [running] (https://www.youtube.com/watch?v=MiuCUWrN4mI) animation. In addition, my running animation was even good just imagine a person not even, the animation still plays the running animation and when the person starts to move, the running animation leg doesn't even look realistic. Overall the animation and coding are terrible at least I learned how to animate.


Note: I record the animation, but couldn't upload animation so I can try to explain it in words.

### running Script - Challenge 
In order to script my running animation watching the two videos I also watched other videos that might be useful for me, it wasn't that helpful because during the time of my research, I was still a beginner level coding in Roblox, but having javascript and Java experience. The video helps me figure out how I can look at my output. This helped me a lot because it told me the error that was needed to solve my problem with the user input. It states `InputEnd is not a valid member of UserInputService "UserInputService"`. This leads me to a different approach start digging more in the [roblox documentation](https://create.roblox.com/docs/en-us/reference/engine/classes/Humanoid#Running) again and tinkering around with it. I later discovered the reason I was getting this error was because the code inside of the InputEnd was not valid to use leading me to have this conflict. During this time I wasn't able to completely fix my problem and achieve a small section of the finished product, but also led me to a new lead for solving my problem. I hope to continue and to be able to complete in time with also complete my other tasks for the game.

#### first script
```js
local userInput = game:GetService("UserInputService")
local player = game:Get
```


### running Script - Solution

#### final script
```js
//get all the information within my game folder and connect it
local userInput = game:GetService("UserInputService")
local Player = game.Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded.Wait()
local Humanoid = Character:WaitForChild("Humanoid")

//running script start
userInput.InputBegan:Connect(function(inputobject, gameProcessed)
	if inputobject.KeyCode == Enum.KeyCode.LeftShift then
		Humanoid.WalkSpeed = 30
	end
end)


userInput.InputEnded:Connect(function(inputobject, gameProcessed)
	if inputobject.KeyCode == Enum.KeyCode.LeftShift then
		Humanoid.WalkSpeed = 16
	end
end)
//running script end
```

### Takeaway


[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
