-- Miranda Hub v3 - Tela cheia (PC + Mobile + Delta)

-- Script oficial: cobre tudo e sem botão X

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local CoreGui = game:GetService("CoreGui")

-- Tenta usar gethui (para Delta e outros executores)

local parent = (gethui and gethui()) or CoreGui

-- Remove GUIs antigas com o mesmo nome

if parent:FindFirstChild("MirandaV3") then

    parent:FindFirstChild("MirandaV3"):Destroy()

end

-- Cria ScreenGui

local gui = Instance.new("ScreenGui")

gui.Name = "MirandaV3"

gui.IgnoreGuiInset = true

gui.ResetOnSpawn = false

gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

gui.Parent = parent

-- Fundo preto cobrindo tudo

local fundo = Instance.new("Frame")

fundo.Size = UDim2.new(1, 0, 1, 0)

fundo.BackgroundColor3 = Color3.new(0, 0, 0)

fundo.BorderSizePixel = 0

fundo.ZIndex = 999999

fundo.Parent = gui

-- Emoji 3D (título)

local titulo = Instance.new("TextLabel")

titulo.Text = "😎 MIRANDA HUB v3"

titulo.Font = Enum.Font.GothamBlack

titulo.TextScaled = true

titulo.TextColor3 = Color3.new(1, 1, 1)

titulo.Size = UDim2.new(1, 0, 0.15, 0)

titulo.Position = UDim2.new(0, 0, 0.05, 0)

titulo.BackgroundTransparency = 1

titulo.ZIndex = 999999

titulo.Parent = fundo

-- Caixa de link

local caixa = Instance.new("TextBox")

caixa.PlaceholderText = "Cole o link aqui..."

caixa.Text = ""

caixa.Font = Enum.Font.SourceSansBold

caixa.TextScaled = true

caixa.Size = UDim2.new(0.8, 0, 0.1, 0)

caixa.Position = UDim2.new(0.1, 0, 0.45, 0)

caixa.BackgroundColor3 = Color3.fromRGB(25, 25, 25)

caixa.TextColor3 = Color3.new(1, 1, 1)

caixa.ZIndex = 999999

caixa.Parent = fundo

-- Botão confirmar

local confirmar = Instance.new("TextButton")

confirmar.Text = "✅ Confirmar"

confirmar.Font = Enum.Font.GothamBold

confirmar.TextScaled = true

confirmar.Size = UDim2.new(0.4, 0, 0.1, 0)

confirmar.Position = UDim2.new(0.3, 0, 0.6, 0)

confirmar.BackgroundColor3 = Color3.fromRGB(40, 120, 40)

confirmar.TextColor3 = Color3.new(1, 1, 1)

confirmar.ZIndex = 999999

confirmar.Parent = fundo

-- Quando clicar, executa o script

confirmar.MouseButton1Click:Connect(function()

    local link = caixa.Text

    if link ~= "" then

        fundo.BackgroundColor3 = Color3.fromRGB(0, 0, 0)

        titulo.Text = "🔄 Carregando script..."

        confirmar.Visible = false

        caixa.Visible = false

        task.wait(1)

        loadstring(game:HttpGet(link))()

        gui:Destroy()

    else

        titulo.Text = "❌ Cole um link válido!"

    end

end)
