local farmRota = {
    -- Adicione as coordenadas da rota de farm aqui
    Vector3.new(10, 0, 10),
    Vector3.new(20, 0, 20),
    Vector3.new(30, 0, 30),
    Vector3.new(40, 0, 40)
}

local farmPote = {
    -- Adicione as coordenadas dos potes aqui
    Vector3.new(5, 0, 5),
    Vector3.new(15, 0, 15),
    Vector3.new(25, 0, 25),
    Vector3.new(35, 0, 35)
}

-- Função para farmar na rota
local function farmarNaRota()
    for _, ponto in ipairs(farmRota) do
        -- Teleportar o jogador para o ponto da rota
        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(ponto))
        wait(1) -- Espera 1 segundo antes de ir para o próximo ponto
    end
end

-- Função para farmar potes
local function farmarPotes()
    for _, pote in ipairs(farmPote) do
        -- Teleportar o jogador para o pote
        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(CFrame.new(pote))
        wait(1) -- Espera 1 segundo antes de ir para o próximo pote
    end
end

-- Função para ativar PvP com 100% de headshots
local function ativarPvP()
    local player = game.Players.LocalPlayer
    local mouse = player:GetMouse()
    
    mouse.Button1Down:Connect(function()
        local target = mouse.Target
        if target and target.Parent:FindFirstChild("Humanoid") then
            local humanoid = target.Parent:FindFirstChild("Humanoid")
            local head = target.Parent:FindFirstChild("Head")
            
            if head then
                -- Causar dano no head (headshot)
                humanoid:TakeDamage(humanoid.Health)
            end
        end
    end)
end

-- Função principal
local function iniciar()
    -- Iniciar farm na rota
    farmarNaRota()
    
    -- Iniciar farm de potes
    farmarPotes()
    
    -- Ativar PvP com 100% de headshots
    ativarPvP()
end

-- Iniciar script
iniciar()
