--// SukyWare V2 - Key System UI (Multi-Keys Otimizado)
--// Adicione ou remova keys facilmente na tabela abaixo

local ValidKeys = {
    "Teste123",
    "SukyKey2026",
    "SukyV2VIP",
    -- Adicione mais keys aqui entre aspas, separadas por vírgula:
    -- "sua_nova_key_aqui",
}

local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local Player = Players.LocalPlayer
local PlayerGui = Player:FindFirstChild("PlayerGui") or CoreGui

-- Evita duplicatas se já houver uma UI aberta
if PlayerGui:FindFirstChild("SukyWareKeySystem") then
    PlayerGui.SukyWareKeySystem:Destroy()
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "SukyWareKeySystem"
ScreenGui.Parent = PlayerGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

-- Janela Principal (Main Frame)
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 20)
MainFrame.Position = UDim2.new(0.5, -200, 0.5, -135)
MainFrame.Size = UDim2.new(0, 400, 0, 265)
MainFrame.Active = true
MainFrame.Draggable = true

local MainCorner = Instance.new("UICorner")
MainCorner.CornerRadius = UDim.new(0, 12)
MainCorner.Parent = MainFrame

-- Linha fina branca nas bordas (UIStroke)
local MainStroke = Instance.new("UIStroke")
MainStroke.Color = Color3.fromRGB(255, 255, 255)
MainStroke.Transparency = 0.7
MainStroke.Thickness = 1.2
MainStroke.Parent = MainFrame

-- TopBar / Cabeçalho
local TopBar = Instance.new("Frame")
TopBar.Name = "TopBar"
TopBar.Parent = MainFrame
TopBar.BackgroundTransparency = 1
TopBar.Size = UDim2.new(1, 0, 0, 45)

local LogoLabel = Instance.new("TextLabel")
LogoLabel.Name = "LogoLabel"
LogoLabel.Parent = TopBar
LogoLabel.BackgroundTransparency = 1
LogoLabel.Position = UDim2.new(0, 15, 0, 0)
LogoLabel.Size = UDim2.new(0, 200, 1, 0)
LogoLabel.Font = Enum.Font.GothamBold
LogoLabel.Text = "S  KEY SYSTEM"
LogoLabel.TextColor3 = Color3.fromRGB(0, 136, 255) -- Azul
LogoLabel.TextSize = 14
LogoLabel.TextXAlignment = Enum.TextXAlignment.Left

-- Botão de Fechar
local CloseButton = Instance.new("TextButton")
CloseButton.Name = "CloseButton"
CloseButton.Parent = TopBar
CloseButton.BackgroundColor3 = Color3.fromRGB(35, 35, 45)
CloseButton.Position = UDim2.new(1, -35, 0.5, -12)
CloseButton.Size = UDim2.new(0, 24, 0, 24)
CloseButton.Font = Enum.Font.GothamBold
CloseButton.Text = "×"
CloseButton.TextColor3 = Color3.fromRGB(220, 220, 220)
CloseButton.TextSize = 16

local CloseCorner = Instance.new("UICorner")
CloseCorner.CornerRadius = UDim.new(0, 6)
CloseCorner.Parent = CloseButton

local CloseStroke = Instance.new("UIStroke")
CloseStroke.Color = Color3.fromRGB(255, 255, 255)
CloseStroke.Transparency = 0.8
CloseStroke.Thickness = 1
CloseStroke.Parent = CloseButton

CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

-- Textos de Boas-Vindas
local WelcomeTitle = Instance.new("TextLabel")
WelcomeTitle.Name = "WelcomeTitle"
WelcomeTitle.Parent = MainFrame
WelcomeTitle.BackgroundTransparency = 1
WelcomeTitle.Position = UDim2.new(0, 20, 0, 45)
WelcomeTitle.Size = UDim2.new(1, -40, 0, 22)
WelcomeTitle.Font = Enum.Font.GothamMedium
WelcomeTitle.Text = "Welcome to the,"
WelcomeTitle.TextColor3 = Color3.fromRGB(200, 200, 200)
WelcomeTitle.TextSize = 15
WelcomeTitle.TextXAlignment = Enum.TextXAlignment.Left

local HubTitle = Instance.new("TextLabel")
HubTitle.Name = "HubTitle"
HubTitle.Parent = MainFrame
HubTitle.BackgroundTransparency = 1
HubTitle.Position = UDim2.new(0, 20, 0, 67)
HubTitle.Size = UDim2.new(1, -40, 0, 30)
HubTitle.Font = Enum.Font.GothamBold
HubTitle.Text = "SukyWare V2"
HubTitle.TextColor3 = Color3.fromRGB(0, 140, 255) -- Azul
HubTitle.TextSize = 22
HubTitle.TextXAlignment = Enum.TextXAlignment.Left

-- Label "Key"
local KeyLabel = Instance.new("TextLabel")
KeyLabel.Name = "KeyLabel"
KeyLabel.Parent = MainFrame
KeyLabel.BackgroundTransparency = 1
KeyLabel.Position = UDim2.new(0, 20, 0, 105)
KeyLabel.Size = UDim2.new(1, -40, 0, 15)
KeyLabel.Font = Enum.Font.Gotham
KeyLabel.Text = "Key"
KeyLabel.TextColor3 = Color3.fromRGB(150, 150, 150)
KeyLabel.TextSize = 12
KeyLabel.TextXAlignment = Enum.TextXAlignment.Left

-- Caixa de Texto (TextBox) para inserir a Key
local KeyBox = Instance.new("TextBox")
KeyBox.Name = "KeyBox"
KeyBox.Parent = MainFrame
KeyBox.BackgroundColor3 = Color3.fromRGB(25, 25, 35)
KeyBox.Position = UDim2.new(0, 20, 0, 123)
KeyBox.Size = UDim2.new(1, -40, 0, 40)
KeyBox.Font = Enum.Font.Gotham
KeyBox.PlaceholderText = "insert your key here"
KeyBox.PlaceholderColor3 = Color3.fromRGB(100, 100, 110)
KeyBox.Text = ""
KeyBox.TextColor3 = Color3.fromRGB(255, 255, 255)
KeyBox.TextSize = 13

local BoxCorner = Instance.new("UICorner")
BoxCorner.CornerRadius = UDim.new(0, 8)
BoxCorner.Parent = KeyBox

local BoxStroke = Instance.new("UIStroke")
BoxStroke.Color = Color3.fromRGB(0, 136, 255)
BoxStroke.Transparency = 0.5
BoxStroke.Thickness = 1
BoxStroke.Parent = KeyBox

-- Botão de Submeter Key
local SubmitButton = Instance.new("TextButton")
SubmitButton.Name = "SubmitButton"
SubmitButton.Parent = MainFrame
SubmitButton.BackgroundColor3 = Color3.fromRGB(0, 120, 255) -- Azul vibrante
SubmitButton.Position = UDim2.new(0, 20, 0, 175)
SubmitButton.Size = UDim2.new(1, -40, 0, 38)
SubmitButton.Font = Enum.Font.GothamBold
SubmitButton.Text = "Submit Key >"
SubmitButton.TextColor3 = Color3.fromRGB(255, 255, 255)
SubmitButton.TextSize = 14

local SubmitCorner = Instance.new("UICorner")
SubmitCorner.CornerRadius = UDim.new(0, 8)
SubmitCorner.Parent = SubmitButton

-- Rodapé com o Link do Discord
local SupportLabel = Instance.new("TextButton")
SupportLabel.Name = "SupportLabel"
SupportLabel.Parent = MainFrame
SupportLabel.BackgroundTransparency = 1
SupportLabel.Position = UDim2.new(0, 20, 0, 225)
SupportLabel.Size = UDim2.new(1, -40, 0, 20)
SupportLabel.Font = Enum.Font.Gotham
SupportLabel.Text = "Need support? Join the Discord"
SupportLabel.TextColor3 = Color3.fromRGB(150, 150, 160)
SupportLabel.TextSize = 12

-- Copiar link do Discord ao clicar
SupportLabel.MouseButton1Click:Connect(function()
    setclipboard("https://discord.gg/8BSHpVSyCN")
    SupportLabel.Text = "Link copiado para a área de transferência!"
    task.wait(2)
    SupportLabel.Text = "Need support? Join the Discord"
end)

-- Função para verificar se a key digitada existe na tabela
local function isKeyValid(input)
    for _, key in ipairs(ValidKeys) do
        if key == input then
            return true
        end
    end
    return false
end

-- Validação e execução
SubmitButton.MouseButton1Click:Connect(function()
    local enteredKey = KeyBox.Text
    
    if isKeyValid(enteredKey) then
        SubmitButton.Text = "Key Correta! Carregando..."
        SubmitButton.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
        task.wait(1)
        
        -- Fecha a UI de Key
        ScreenGui:Destroy()
        
        -- Executa o seu script do GitHub
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Peagaah/SukyWare/refs/heads/main/Script.txt"))()
        
    else
        SubmitButton.Text = "Key Incorreta!"
        SubmitButton.BackgroundColor3 = Color3.fromRGB(220, 50, 50)
        task.wait(1.5)
        SubmitButton.Text = "Submit Key >"
        SubmitButton.BackgroundColor3 = Color3.fromRGB(0, 120, 255)
    end
end)
