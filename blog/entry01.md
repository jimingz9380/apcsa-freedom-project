# Entry 1: Research
## 12/11/23

### Context
For years I always wanted to make a game because it was something that kept me from being bored. The moment my cousin move to New York I felt alone and game was there to keep me entertain. Although I had little to no knowledge in game develop and have been learnign more in website develop. This year and my last year as Senior, I will tried to make an game to the best of my ability. The project I'm be making this year is an RPG roblox adventure using the Tool Lua because roblox uses the coding language Lua.
### Research
Seen I knew someone(Aaron) last year using Lua, my first action was to ask how he was learning Lua. Through his recommendation I was able to recieve this [video](https://www.youtube.com/watch?t=5309&v=1srFmjt1Ib0&feature=youtu.be) and learn some code I was able to recongize from Sep9, sep10, sep11. Although there some difference, in general is was the same concept. Another way I research was using the Roblox [documentation](https://create.roblox.com/docs/tutorials), it have many steps and tutorials of how it a beginner should be able to start learning lua and roblox coding.


### Tinker
After watching some videos of how to make UI (User interface) and looking at the Roblox documentation I first went to Roblox studio. I created a UI for my game by creating multiple frames in Roblox studio to combine them to make a good-looking UI by clicking the add button and selecting the frame. Then I click into each frame into different size, having one big box and 4 Mutiple small one that inside the big one and each small box was at a different elevation of the box. Currently I haven't done much into the scripting part of Roblox in order to make the UI functional. Another thing I tinker was from the Roblox documentation I started learning the basic script of creating a disappearing and reappearing platform through series of step given form the document. I create the platform and add the script file inside I coded. Overall, I learn some basic script and UI for Roblox in this tinker.

```java
local platform = script.Parent // find object location 

local function disappear() // function that make is the platform disappear
	platform.CanCollide = false
	platform.Transparency = 1
end

disappear()

local function appear()  // function that make is the platform appear
	platform.CanCollide = true
	platform.Transparency = 0
end

appear()

while true do // repeat the function
	task.wait(3) // a wait interval in the unit of 3 second.
	disappear()
	task.wait(3)
	appear()
end
```
### Takeaway
In this blog, I have developed the skill of <ins>**Consideration and How to google**</ins>. It was a tedious task, but I manage to find enjoyment in learning these code because it was something I find interests. As a Result I am more expierence in search up what I need to do in order to prepare myself for creating my game in Roblox. 

[Next](entry02.md)

[Home](../README.md)
