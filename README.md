local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")

local button = Instance.new("TextButton")
button.Size = UDim2.new(0, 200, 0, 50)
button.Position = UDim2.new(0.5, -100, 0.9, -25)  
button.Text = "Di chuyển đến Tesla Lap"
button.Parent = screenGui

local teslaladPosition = Vector3.new(100, 0, 200)  

    local primaryPart = character:WaitForChild("HumanoidRootPart")
    primaryPart.CFrame = CFrame.new(teslaladPosition)

 
    local direction = (teslaladPosition - primaryPart.Position).unit
    local angle = math.acos(primaryPart.CFrame.LookVector:Dot(direction))
    local axis = primaryPart.CFrame.LookVector:Cross(direction).unit
    primaryPart.CFrame = primaryPart.CFrame * CFrame.Angles(0, angle, 0)

    local humanoid = character:FindFirstChildOfClass("Humanoid")
    humanoid:MoveTo(teslaladPosition)
end

button.MouseButton1Click:Connect(moveToTeslaLap)
