-- Configurações da UI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "SimpleHub"
ScreenGui.Parent = game.CoreGui

local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Size = UDim2.new(0, 350, 0, 400)
MainFrame.Position = UDim2.new(0.5, -175, 0.5, -200)
MainFrame.AnchorPoint = Vector2.new(0.5, 0.5)
MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
MainFrame.BorderSizePixel = 0
MainFrame.Parent = ScreenGui

local TopBar = Instance.new("Frame")
TopBar.Name = "TopBar"
TopBar.Size = UDim2.new(1, 0, 0, 30)
TopBar.Position = UDim2.new(0, 0, 0, 0)
TopBar.BackgroundColor3 = Color3.fromRGB(20, 20, 30)
TopBar.BorderSizePixel = 0
TopBar.Parent = MainFrame

local Title = Instance.new("TextLabel")
Title.Name = "Title"
Title.Size = UDim2.new(1, 0, 1, 0)
Title.Position = UDim2.new(0, 0, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "Menu de Hacks"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 14
Title.Parent = TopBar

local CloseButton = Instance.new("TextButton")
CloseButton.Name = "CloseButton"
CloseButton.Size = UDim2.new(0, 30, 1, 0)
CloseButton.Position = UDim2.new(1, -30, 0, 0)
CloseButton.BackgroundColor3 = Color3.fromRGB(255, 50, 50)
CloseButton.BorderSizePixel = 0
CloseButton.Text = "X"
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseButton.Font = Enum.Font.GothamBold
CloseButton.TextSize = 14
CloseButton.Parent = TopBar

CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

local TabButtonsFrame = Instance.new("Frame")
TabButtonsFrame.Name = "TabButtonsFrame"
TabButtonsFrame.Size = UDim2.new(1, 0, 0, 30)
TabButtonsFrame.Position = UDim2.new(0, 0, 0, 30)
TabButtonsFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 35)
TabButtonsFrame.BorderSizePixel = 0
TabButtonsFrame.Parent = MainFrame

local MainTabButton = Instance.new("TextButton")
MainTabButton.Name = "MainTabButton"
MainTabButton.Size = UDim2.new(0.33, 0, 1, 0)
MainTabButton.Position = UDim2.new(0, 0, 0, 0)
MainTabButton.BackgroundColor3 = Color3.fromRGB(40, 40, 50)
MainTabButton.BorderSizePixel = 0
MainTabButton.Text = "Principal"
MainTabButton.TextColor3 = Color3.fromRGB(255, 255, 255)
MainTabButton.Font = Enum.Font.Gotham
MainTabButton.TextSize = 12
MainTabButton.Parent = TabButtonsFrame

local PlayerTabButton = Instance.new("TextButton")
PlayerTabButton.Name = "PlayerTabButton"
PlayerTabButton.Size = UDim2.new(0.33, 0, 1, 0)
PlayerTabButton.Position = UDim2.new(0.33, 0, 0, 0)
PlayerTabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
PlayerTabButton.BorderSizePixel = 0
PlayerTabButton.Text = "Jogador"
PlayerTabButton.TextColor3 = Color3.fromRGB(255, 255, 255)
PlayerTabButton.Font = Enum.Font.Gotham
PlayerTabButton.TextSize = 12
PlayerTabButton.Parent = TabButtonsFrame

local ScriptsTabButton = Instance.new("TextButton")
ScriptsTabButton.Name = "ScriptsTabButton"
ScriptsTabButton.Size = UDim2.new(0.34, 0, 1, 0)
ScriptsTabButton.Position = UDim2.new(0.66, 0, 0, 0)
ScriptsTabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
ScriptsTabButton.BorderSizePixel = 0
ScriptsTabButton.Text = "Scripts"
ScriptsTabButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ScriptsTabButton.Font = Enum.Font.Gotham
ScriptsTabButton.TextSize = 12
ScriptsTabButton.Parent = TabButtonsFrame

local TabsContainer = Instance.new("Frame")
TabsContainer.Name = "TabsContainer"
TabsContainer.Size = UDim2.new(1, 0, 1, -60)
TabsContainer.Position = UDim2.new(0, 0, 0, 60)
TabsContainer.BackgroundTransparency = 1
TabsContainer.Parent = MainFrame

-- Função para criar abas
local function createTab(name)
    local tab = Instance.new("ScrollingFrame")
    tab.Name = name .. "Tab"
    tab.Size = UDim2.new(1, 0, 1, 0)
    tab.Position = UDim2.new(0, 0, 0, 0)
    tab.BackgroundTransparency = 1
    tab.Visible = false
    tab.ScrollBarThickness = 5
    tab.AutomaticCanvasSize = Enum.AutomaticSize.Y
    tab.Parent = TabsContainer
    
    local layout = Instance.new("UIListLayout")
    layout.Name = "Layout"
    layout.Padding = UDim.new(0, 5)
    layout.SortOrder = Enum.SortOrder.LayoutOrder
    layout.Parent = tab
    
    return tab
end

local MainTab = createTab("Main")
local PlayerTab = createTab("Player")
local ScriptsTab = createTab("Scripts")

MainTab.Visible = true

-- Função para criar botões
local function createButton(parent, text, callback)
    local button = Instance.new("TextButton")
    button.Name = text .. "Button"
    button.Size = UDim2.new(0.9, 0, 0, 40)
    button.Position = UDim2.new(0.05, 0, 0, 0)
    button.BackgroundColor3 = Color3.fromRGB(50, 50, 60)
    button.BorderSizePixel = 0
    button.Text = text
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.Font = Enum.Font.Gotham
    button.TextSize = 14
    button.Parent = parent
    
    button.MouseButton1Click:Connect(callback)
    
    return button
end

-- Navegação entre abas
MainTabButton.MouseButton1Click:Connect(function()
    MainTab.Visible = true
    PlayerTab.Visible = false
    ScriptsTab.Visible = false
    MainTabButton.BackgroundColor3 = Color3.fromRGB(40, 40, 50)
    PlayerTabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    ScriptsTabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
end)

PlayerTabButton.MouseButton1Click:Connect(function()
    MainTab.Visible = false
    PlayerTab.Visible = true
    ScriptsTab.Visible = false
    MainTabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    PlayerTabButton.BackgroundColor3 = Color3.fromRGB(40, 40, 50)
    ScriptsTabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
end)

ScriptsTabButton.MouseButton1Click:Connect(function()
    MainTab.Visible = false
    PlayerTab.Visible = false
    ScriptsTab.Visible = true
    MainTabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    PlayerTabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    ScriptsTabButton.BackgroundColor3 = Color3.fromRGB(40, 40, 50)
end)

-- Funções do jogador
local FlyEnabled = false
local InfiniteJumpEnabled = false
local GodModeEnabled = false
local ClickTPEnabled = false
local ClickTPConnection

-- Função Fly
local function ToggleFly()
    FlyEnabled = not FlyEnabled
    local player = game:GetService("Players").LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:FindFirstChildOfClass("Humanoid")
    
    if FlyEnabled then
        local bodyVelocity = Instance.new("BodyVelocity", character.HumanoidRootPart)
        bodyVelocity.Velocity = Vector3.new(0, 0, 0)
        bodyVelocity.MaxForce = Vector3.new(0, math.huge, 0)
        
        local userInputService = game:GetService("UserInputService")
        local flySpeed = 50
        local forwardValue = 0
        local backwardValue = 0
        local leftValue = 0
        local rightValue = 0
        
        local flyConnection = userInputService.InputBegan:Connect(function(input, processed)
            if processed then return end
            
            if input.KeyCode == Enum.KeyCode.W then
                forwardValue = -flySpeed
            elseif input.KeyCode == Enum.KeyCode.S then
                backwardValue = flySpeed
            elseif input.KeyCode == Enum.KeyCode.A then
                leftValue = -flySpeed
            elseif input.KeyCode == Enum.KeyCode.D then
                rightValue = flySpeed
            elseif input.KeyCode == Enum.KeyCode.Space then
                bodyVelocity.Velocity = Vector3.new(0, flySpeed, 0)
            end
        end)
        
        local flyEndConnection = userInputService.InputEnded:Connect(function(input)
            if input.KeyCode == Enum.KeyCode.W then
                forwardValue = 0
            elseif input.KeyCode == Enum.KeyCode.S then
                backwardValue = 0
            elseif input.KeyCode == Enum.KeyCode.A then
                leftValue = 0
            elseif input.KeyCode == Enum.KeyCode.D then
                rightValue = 0
            elseif input.KeyCode == Enum.KeyCode.Space then
                bodyVelocity.Velocity = Vector3.new(0, 0, 0)
            end
        end)
        
        game:GetService("RunService").Heartbeat:Connect(function()
            if FlyEnabled then
                bodyVelocity.Velocity = Vector3.new(leftValue + rightValue, bodyVelocity.Velocity.Y, forwardValue + backwardValue)
            else
                bodyVelocity:Destroy()
                flyConnection:Disconnect()
                flyEndConnection:Disconnect()
            end
        end)
    end
end

-- Função Infinite Jump
local function ToggleInfiniteJump()
    InfiniteJumpEnabled = not InfiniteJumpEnabled
    local player = game:GetService("Players").LocalPlayer
    
    if InfiniteJumpEnabled then
        local connection
        connection = game:GetService("UserInputService").JumpRequest:Connect(function()
            if InfiniteJumpEnabled then
                player.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
            else
                connection:Disconnect()
            end
        end)
    end
end

-- Função GodMode
local function ToggleGodMode()
    GodModeEnabled = not GodModeEnabled
    local player = game:GetService("Players").LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    
    if GodModeEnabled then
        for _, part in pairs(character:GetDescendants()) do
            if part:IsA("BasePart") then
                part.CanCollide = false
            end
        end
        
        character.ChildAdded:Connect(function(child)
            if child:IsA("BasePart") then
                child.CanCollide = false
            end
        end)
        
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        if humanoid then
            humanoid.MaxHealth = math.huge
            humanoid.Health = math.huge
        end
    else
        for _, part in pairs(character:GetDescendants()) do
            if part:IsA("BasePart") then
                part.CanCollide = true
            end
        end
        
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        if humanoid then
            humanoid.MaxHealth = 100
            humanoid.Health = 100
        end
    end
end

-- Função Click TP
local function ToggleClickTP()
    ClickTPEnabled = not ClickTPEnabled
    local player = game:GetService("Players").LocalPlayer
    local mouse = player:GetMouse()
    
    if ClickTPEnabled then
        ClickTPConnection = mouse.Button1Down:Connect(function()
            if ClickTPEnabled then
                local character = player.Character
                if character then
                    local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
                    if humanoidRootPart then
                        humanoidRootPart.CFrame = CFrame.new(mouse.Hit.X, mouse.Hit.Y + 5, mouse.Hit.Z)
                    end
                end
            end
        end)
    else
        if ClickTPConnection then
            ClickTPConnection:Disconnect()
        end
    end
end

-- Criando os botões
createButton(PlayerTab, "Fly", ToggleFly)
createButton(PlayerTab, "Pulo Infinito", ToggleInfiniteJump)
createButton(PlayerTab, "God Mode", ToggleGodMode)
createButton(PlayerTab, "Click TP", ToggleClickTP)

-- Botões para scripts externos
createButton(ScriptsTab, "Blox Fruits", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pedrin031/NoxHub/refs/heads/main/README.md"))()
end)

createButton(ScriptsTab, "Fisch Autofarm", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/rblxscriptsdotnet/roblox-scripts/refs/heads/main/rblxscriptsnet%20fisch%20autofarm"))()
end)

createButton(ScriptsTab, "Grow a Garden", function()
    loadstring(game:HttpGetAsync("https://raw.githubusercontent.com/NoLag-id/No-Lag-HUB/refs/heads/main/Loader/LoaderV1.lua"))()
end)

createButton(ScriptsTab, "Aimbot", function()
    loadstring(game:HttpGet("https://pastefy.app/ZNP2L4hG/raw"))()
end)

createButton(ScriptsTab, "Steal Brainrot", function()
    loadstring(game:HttpGet("https://pastefy.app/zZ1pgjsa/raw"))()
end)

-- Make the window draggable
local UserInputService = game:GetService("UserInputService")
local dragging
local dragInput
local dragStart
local startPos

local function update(input)
    local delta = input.Position - dragStart
    MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
end

TopBar.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true
        dragStart = input.Position
        startPos = MainFrame.Position
        
        input.Changed:Connect(function()
            if input.UserInputState == Enum.UserInputState.End then
                dragging = false
            end
        end)
    end
end)

TopBar.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
        dragInput = input
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if input == dragInput and dragging then
        update(input)
    end
end)
