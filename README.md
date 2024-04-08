local function MakeDraggable(topbarobject, object)
	local Dragging = nil
	local DragInput = nil
	local DragStart = nil
	local StartPosition = nil

	local function Update(input)
		local Delta = input.Position - DragStart
		local pos = UDim2.new(StartPosition.X.Scale, StartPosition.X.Offset + Delta.X, StartPosition.Y.Scale, StartPosition.Y.Offset + Delta.Y)
		local Tween = TweenService:Create(object, TweenInfo.new(0.15), {Position = pos})
		Tween:Play()
	end

	topbarobject.InputBegan:Connect(
		function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				DragStart = input.Position
				StartPosition = object.Position

				input.Changed:Connect(
					function()
						if input.UserInputState == Enum.UserInputState.End then
							Dragging = false
						end
					end
				)
			end
		end
	)

	topbarobject.InputChanged:Connect(
		function(input)
			if
				input.UserInputType == Enum.UserInputType.MouseMovement or
				input.UserInputType == Enum.UserInputType.Touch
			then
				DragInput = input
			end
		end
	)

	UserInputService.InputChanged:Connect(
		function(input)
			if input == DragInput and Dragging then
				Update(input)
			end
		end
	)
end
local ScreenGui = Instance.new("ScreenGui")
local OP = Instance.new("TextButton")
local UICorner = Instance.new("UICorner")
local Frame = Instance.new("Frame")
local TextLabel = Instance.new("TextLabel")
local UICorner_2 = Instance.new("UICorner")
local Toggle = Instance.new("TextButton")
local UICorner_3 = Instance.new("UICorner")
local Cl = Instance.new("TextButton")
local UICorner_4 = Instance.new("UICorner")

ScreenGui.Parent = game.CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

OP.Name = "OP"
OP.Parent = ScreenGui
OP.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
OP.BorderColor3 = Color3.fromRGB(0, 0, 0)
OP.BorderSizePixel = 0
OP.Position = UDim2.new(0.0341490433, 0, 0.0692179203, 0)
OP.Size = UDim2.new(0.0761904791, 0, 0.139275759, 0)
OP.Font = Enum.Font.SourceSans
OP.Text = "K"
OP.TextColor3 = Color3.fromRGB(255, 255, 255)
OP.TextScaled = true
OP.TextSize = 14.000
OP.TextWrapped = true
UICorner.CornerRadius = UDim.new(0, 50)
UICorner.Parent = OP
Frame.Parent = OP
Frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Frame.BorderColor3 = Color3.fromRGB(0, 0, 0)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(3.68990302, 0, -1.25999999, 0)
Frame.Size = UDim2.new(5.04503059, 0, 6.71723175, 0)
TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.BorderSizePixel = 0
TextLabel.Position = UDim2.new(0.134502932, 0, 0.113141865, 0)
TextLabel.Size = UDim2.new(0.686672866, 0, 0.0952773467, 0)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "KOBEN HUB"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextScaled = true
TextLabel.TextSize = 14.000
TextLabel.TextWrapped = true
MakeDraggable(Frame,Frame)
UICorner_2.Parent = Frame

Toggle.Name = "Toggle"
Toggle.Parent = Frame
Toggle.BackgroundColor3 = Color3.fromRGB(200, 200, 0)
Toggle.BorderColor3 = Color3.fromRGB(0, 0, 0)
Toggle.BorderSizePixel = 0
Toggle.Position = UDim2.new(0.106186524, 0, 0.574641526, 0)
Toggle.Size = UDim2.new(0.743305683, 0, 0.142916024, 0)
Toggle.Font = Enum.Font.SourceSans
Toggle.Text = "Off"
Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)
Toggle.TextScaled = true
Toggle.TextSize = 14.000
Toggle.TextWrapped = true

UICorner_3.CornerRadius = UDim.new(0, 20)
UICorner_3.Parent = Toggle

Cl.Name = "Cl"
Cl.Parent = Frame
Cl.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Cl.BorderColor3 = Color3.fromRGB(0, 0, 0)
Cl.BorderSizePixel = 0
Cl.Position = UDim2.new(-0.731393576, 0, 0.184599862, 0)
Cl.Size = UDim2.new(0.198214844, 0, 0.151848227, 0)
Cl.Font = Enum.Font.SourceSans
Cl.Text = "K"
Cl.TextColor3 = Color3.fromRGB(255, 255, 255)
Cl.TextScaled = true
Cl.TextSize = 14.000
Cl.TextWrapped = true

UICorner_4.CornerRadius = UDim.new(0, 50)
UICorner_4.Parent = Cl

-- Scripts:

local function YVCCMH_fake_script() -- Toggle.LocalScript 
	local script = Instance.new('LocalScript', Toggle)

	local function PNHLOYF_fake_script() -- Toggle.LocalScript 
		local script = Instance.new('LocalScript', Toggle)
	
		_G.aimbot = false
		local camera = game.Workspace.CurrentCamera
		local localplayer = game:GetService("Players").LocalPlayer
	
		script.Parent.MouseButton1Click:Connect(function()
			if _G.aimbot == false then
				_G.aimbot = true
				script.Parent.TextColor3 = Color3.fromRGB(255,255,255)
				script.Parent.Text = "On"
				function closestplayer()
					local dist = math.huge -- math.huge means a really large number, 1M+.
					local target = nil --- nil means no value
					for i,v in pairs (game:GetService("Players"):GetPlayers()) do
						if v ~= localplayer then
							if v.Character and v.Character:FindFirstChild("Head") and _G.aimbot and v.Character.Humanoid.Health > 0 then --- creating the checks
								local magnitude = (v.Character.Head.Position - localplayer.Character.Head.Position).magnitude
								if magnitude < dist then
									dist = magnitude
									target = v
								end
	
							end
						end
					end
					return target
				end
	
			else
				_G.aimbot = false
				script.Parent.TextColor3 = Color3.fromRGB(0,0,0)
				script.Parent.Text = "Off"
			end
		end)
	
		local aiming =  true --- this toggle will make it so we lock on to the person when we press our keybind
	
		game:GetService("RunService").RenderStepped:Connect(function()
			if aiming then
				camera.CFrame = CFrame.new(camera.CFrame.Position,closestplayer().Character.HumanoidRootPart.Position) -- locks into the HumanoidRootPart
			end
		end)
	end
	coroutine.wrap(PNHLOYF_fake_script)()
end
coroutine.wrap(YVCCMH_fake_script)()
local function KBCCSU_fake_script() -- Cl.LocalScript 
	local script = Instance.new('LocalScript', Cl)

	function Cl ()
		script.Parent.Parent.Parent.Frame.Visible = false
	end
	script.Parent.MouseButton1Click:Connect(Cl)
end
coroutine.wrap(KBCCSU_fake_script)()
local function OVGM_fake_script() -- OP.LocalScript 
	local script = Instance.new('LocalScript', OP)

	function PO ()
		script.Parent.Frame.Visible = true
	end
	script.Parent.MouseButton1Click:Connect(PO)
end
coroutine.wrap(OVGM_fake_script)()
