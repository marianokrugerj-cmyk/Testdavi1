-- Script de Exemplo: Lógica de Dano Profissional
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local AttackEvent = ReplicatedStorage:WaitForChild("AttackEvent")

AttackEvent.OnServerEvent:Connect(function(player, attackType)
    local character = player.Character
    if not character then return end

    -- Validação simples (Bypass de Spammers)
    if character:GetAttribute("IsAttacking") then return end
    character:SetAttribute("IsAttacking", true)

    -- Configuração da Hitbox (Usando Raycast para precisão)
    local hitPart = character:WaitForChild("RightHand")
    local params = RaycastParams.new()
    params.FilterDescendantsInstances = {character}
    params.FilterType = Enum.RaycastFilterType.Exclude

    -- Lógica de detecção de hit
    -- Aqui você usaria uma biblioteca como RaycastHitboxV4 para "profissionalismo"
    print(player.Name .. " executou: " .. attackType)

    task.wait(0.5) -- Tempo de cooldown do golpe
    character:SetAttribute("IsAttacking", false)
end)
