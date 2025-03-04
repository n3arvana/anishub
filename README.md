
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local RollbackButton = Instance.new("TextButton")
local AutoFarmButton = Instance.new("TextButton")
local CloseButton = Instance.new("TextButton")

if not game:IsLoaded() then
    game.Loaded:Wait()
end

ScreenGui.Name = "AnimeStrikeGUI"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.Size = UDim2.new(0, 250, 0, 250)
Frame.Position = UDim2.new(0.3, 0, 0.3, 0)
Frame.Active = true
Frame.Draggable = true
Frame.BorderSizePixel = 2
Frame.BorderColor3 = Color3.fromRGB(255, 255, 255)

RollbackButton.Parent = Frame
RollbackButton.Text = "Rollback Summon"
RollbackButton.Size = UDim2.new(0, 230, 0, 50)
RollbackButton.Position = UDim2.new(0, 10, 0, 50)
RollbackButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
RollbackButton.TextColor3 = Color3.fromRGB(255, 255, 255)
RollbackButton.TextScaled = true

AutoFarmButton.Parent = Frame
AutoFarmButton.Text = "Auto Farm"
AutoFarmButton.Size = UDim2.new(0, 230, 0, 50)
AutoFarmButton.Position = UDim2.new(0, 10, 0, 110)
AutoFarmButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
AutoFarmButton.TextColor3 = Color3.fromRGB(255, 255, 255)
AutoFarmButton.TextScaled = true

CloseButton.Parent = Frame
CloseButton.Text = "Fechar GUI"
CloseButton.Size = UDim2.new(0, 230, 0, 50)
CloseButton.Position = UDim2.new(0, 10, 0, 170)
CloseButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseButton.TextScaled = true

local function Rollback()
    local args = {
        [1] = "SummonRollback"
    }
    game:GetService("ReplicatedStorage").RemoteEvent:FireServer(unpack(args))
end

RollbackButton.MouseButton1Click:Connect(Rollback)

local function AutoFarm()
    while wait(1) do
        local args = {
            [1] = "AutoFarm"
        }
        game:GetService("ReplicatedStorage").RemoteEvent:FireServer(unpack(args))
    end
end

AutoFarmButton.MouseButton1Click:Connect(function()
    spawn(AutoFarm)
end)

CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)
