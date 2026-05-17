-- LocalScript

-- Carrega a biblioteca Rayfield
local Rayfield = loadstring(game: HttpGet('https://sirius.menu/rayfield'))()

-- Cria uma nova janela
local window = Rayfield:CreateWindow({
    Name = "zYonX Hub",
    LoadingTitle = "Carregando...",
    LoadingSubtitle = "Por favor, aguarde...",
    ConfigurationSaving = {
        Enabled = true,
        FolderName = "Rayfield",
        FileName = "zYonXHubConfig"
    },
    Discord = {
        Enabled = true,
        Invite = "seu_codigo_de_convite_aqui", -- Substitua pelo seu código de convite do Discord
        RememberJoins = true
    }
})

-- Variáveis de estado
local speedEnabled = false
local jumpEnabled = false
local espEnabled = false
local highlights = {}

-- Função para ativar/desativar Speed
local function toggleSpeed()
    local player = game.Players.LocalPlayer
    if speedEnabled then
        player.Character.Humanoid.WalkSpeed = 16 -- Velocidade padrão
        Rayfield:Notify({
            Title = "Speed",
            Content = "Speed desligado!",
            Duration = 3
        })
    else
        player.Character.Humanoid.WalkSpeed = 100 -- Ajuste a velocidade desejada
        Rayfield:Notify({
            Title = "Speed",
            Content = "Speed ligado!",
            Duration = 3
        })
    end
    speedEnabled = not speedEnabled
end

-- Função para ativar/desativar Jump
local function toggleJump()
    local player = game.Players.LocalPlayer
    if jumpEnabled then
        player.Character.Humanoid.JumpPower = 50 -- Pulo padrão
        Rayfield:Notify({
            Title = "Jump",
            Content = "Jump desligado!",
            Duration = 3
        })
    else
        player.Character.Humanoid.JumpPower = 100 -- Ajuste o pulo desejado
        Rayfield:Notify({
            Title = "Jump",
            Content = "Jump ligado!",
            Duration = 3
        })
    end
    jumpEnabled = not jumpEnabled
end

-- Função para ativar/desativar ESP
local function toggleESP()
    local player = game.Players.LocalPlayer
    if espEnabled then
        for _, highlight in pairs(highlights) do
            highlight:Destroy()
        end
        highlights = {}
        Rayfield:Notify({
            Title = "ESP",
            Content = "ESP desligado!",
            Duration = 3
        })
    else
        for _, p in pairs(game.Players:GetPlayers()) do
            if p ~= player then
                local highlight = Instance.new("Highlight", p.Character)
                highlight.FillColor = Color3.fromRGB(255, 0, 0) -- Cor do ESP
                highlight.OutlineColor = Color3.fromRGB(0, 0, 0) -- Cor da borda
                table.insert(highlights, highlight)
            end
        end
        Rayfield:Notify({
            Title = "ESP",
            Content = "ESP ligado!",
            Duration = 3
        })
    end
    espEnabled = not espEnabled
end

-- Função para executar o script de shaders 4K
local function executeShaders4K()
    local success, err = pcall(function()
        loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Shaders-4k-48907"))()
    end)
    
    if success then
        Rayfield:Notify({
            Title = "Shaders 4K Executado",
            Content = "O script de Shaders 4K foi executado com sucesso!",
            Duration = 3
        })
    else
        Rayfield:Notify({
            Title = "Erro",
            Content = "Erro ao executar o script de Shaders 4K: " .. err,
            Duration = 5
        })
    end
end

-- Função para executar o script de emotes
local function executeEmotes()
    local success, err = pcall(function()
        loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-7yd7-I-Emote-Script-48024"))()
    end)
    
    if success then
        Rayfield:Notify({
            Title = "Emotes Executado",
            Content = "O script de Emotes foi executado com sucesso!",
            Duration = 3
        })
    else
        Rayfield:Notify({
            Title = "Erro",
            Content = "Erro ao executar o script de Emotes: " .. err,
            Duration = 5
        })
    end
end

-- Função para executar o script de administrador
local function executeAdministrador()
    local success, err = pcall(function()
        loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-DEX-REContinued-216140"))()
    end)
    
    if success then
        Rayfield:Notify({
            Title = "Administrador Executado",
            Content = "O script de Administrador foi executado com sucesso!",
            Duration = 3
        })
    else
        Rayfield:Notify({
            Title = "Erro",
            Content = "Erro ao executar o script de Administrador: " .. err,
            Duration = 5
        })
    end
end

-- Função para executar o script de Fly GUI
local function executeFlyGUI()
    local success, err = pcall(function()
        loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Fly-GUI-FX-186429"))()
    end)

    if success then
        Rayfield:Notify({
            Title = "Fly GUI Executado",
            Content = "O script de Fly GUI foi executado com sucesso!",
            Duration = 3
        })
    else
        Rayfield:Notify({
            Title = "Erro",
            Content = "Erro ao executar o script de Fly GUI: " .. err,
            Duration = 5
        })
    end
end

-- Cria os botões no tab
local tab = window:CreateTab("Funções")

tab:CreateButton({
    Name = "Toggle Speed",
    Callback = toggleSpeed
})

tab:CreateButton({
    Name = "Toggle Jump",
    Callback = toggleJump
})

tab:CreateButton({
    Name = "Toggle ESP",
    Callback = toggleESP
})

tab:CreateButton({
    Name = "Shaders 4K",
    Callback = executeShaders4K
})

tab:CreateButton({
    Name = "Emotes",
    Callback = executeEmotes
})

tab:CreateButton({
    Name = "Administrador",
    Callback = executeAdministrador
})

tab:CreateButton({
    Name = "Fly GUI",
    Callback = executeFlyGUI
})

-- Finaliza e mostra a GUI
Rayfield:Init()
