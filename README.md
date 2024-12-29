local player = game.Players.LocalPlayer
local camera = game.Workspace.CurrentCamera
local Players = game.Players

-- Função para desenhar as linhas e os nomes
local function drawPlayerESP()
    -- A cada frame, verifica os outros jogadores
    for _, otherPlayer in pairs(Players:GetPlayers()) do
        -- Ignora o próprio jogador
        if otherPlayer ~= player and otherPlayer.Character and otherPlayer.Character:FindFirstChild("HumanoidRootPart") then
            local otherPlayerRoot = otherPlayer.Character.HumanoidRootPart
            local playerRoot = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
            
            if playerRoot then
                -- Cria uma linha entre os jogadores
                local line = Instance.new("Part")
                line.Size = Vector3.new(0.2, 0.2, (playerRoot.Position - otherPlayerRoot.Position).Magnitude)  -- Tamanho da linha
                line.Anchored = true
                line.CanCollide = false
                line.BrickColor = BrickColor.White()  -- Cor branca
                line.Material = Enum.Material.SmoothPlastic
                line.CFrame = CFrame.new(playerRoot.Position, otherPlayerRoot.Position) * CFrame.new(0, 0, -
