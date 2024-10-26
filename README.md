-- Cria a GUI
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local TextLabel = Instance.new("TextLabel")
local IncreaseButton = Instance.new("TextButton")
local DecreaseButton = Instance.new("TextButton")
local SpeedLabel = Instance.new("TextLabel")
local CloseButton = Instance.new("TextButton")
local ResetButton = Instance.new("TextButton")

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.Position = UDim2.new(0.5, -75, 0.5, -75)
Frame.Size = UDim2.new(0, 150, 0, 200)

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.Size = UDim2.new(0, 150, 0, 30)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "Walk Speed do Batata"
TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.TextSize = 18

IncreaseButton.Parent = Frame
IncreaseButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
IncreaseButton.Position = UDim2.new(0, 0, 0.3, 0)
IncreaseButton.Size = UDim2.new(0, 150, 0, 30)
IncreaseButton.Font = Enum.Font.SourceSans
IncreaseButton.Text = "Aumentar Velocidade"
IncreaseButton.TextColor3 = Color3.fromRGB(0, 0, 0)
IncreaseButton.TextSize = 18

DecreaseButton.Parent = Frame
DecreaseButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
DecreaseButton.Position = UDim2.new(0, 0, 0.5, 0)
DecreaseButton.Size = UDim2.new(0, 150, 0, 30)
DecreaseButton.Font = Enum.Font.SourceSans
DecreaseButton.Text = "Diminuir Velocidade"
DecreaseButton.TextColor3 = Color3.fromRGB(0, 0, 0)
DecreaseButton.TextSize = 18

SpeedLabel.Parent = Frame
SpeedLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
SpeedLabel.Position = UDim2.new(0, 0, 0.7, 0)
SpeedLabel.Size = UDim2.new(0, 150, 0, 30)
SpeedLabel.Font = Enum.Font.SourceSans
SpeedLabel.Text = "Velocidade: 16"
SpeedLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
SpeedLabel.TextSize = 18

CloseButton.Parent = Frame
CloseButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
CloseButton.Position = UDim2.new(1, -25, 0, 0)
CloseButton.Size = UDim2.new(0, 25, 0, 25)
CloseButton.Font = Enum.Font.SourceSans
CloseButton.Text = "X"
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseButton.TextSize = 18

ResetButton.Parent = Frame
ResetButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
ResetButton.Position = UDim2.new(0, 0, 0.9, 0)
ResetButton.Size = UDim2.new(0, 150, 0, 30)
ResetButton.Font = Enum.Font.SourceSans
ResetButton.Text = "Resetar Velocidade"
ResetButton.TextColor3 = Color3.fromRGB(0, 0, 0)
ResetButton.TextSize = 18

-- Define a velocidade inicial e os limites
local walkSpeed = 16
local minSpeed = 1
local maxSpeed = 300

-- Função para aumentar a velocidade
local function aumentarVelocidade()
    if walkSpeed < maxSpeed then
        walkSpeed = walkSpeed + 1
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = walkSpeed
        SpeedLabel.Text = "Velocidade: " .. walkSpeed
    end
end

-- Função para diminuir a velocidade
local function diminuirVelocidade()
    if walkSpeed > minSpeed then
        walkSpeed = walkSpeed - 1
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = walkSpeed
        SpeedLabel.Text = "Velocidade: " .. walkSpeed
    end
end

-- Função para resetar a velocidade
local function resetarVelocidade()
    walkSpeed = 16
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = walkSpeed
    SpeedLabel.Text = "Velocidade: " .. walkSpeed
end

-- Função para fechar o GUI
local function fecharGUI()
    ScreenGui:Destroy()
end

-- Conecta os botões às funções
IncreaseButton.MouseButton1Click:Connect(aumentarVelocidade)
DecreaseButton.MouseButton1Click:Connect(diminuirVelocidade)
ResetButton.MouseButton1Click:Connect(resetarVelocidade)
CloseButton.MouseButton1Click:Connect(fecharGUI)

-- Define a velocidade inicial do jogador
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = walkSpeed
