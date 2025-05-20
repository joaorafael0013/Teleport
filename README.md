-- Teleport Exploit Script (Delta-style)

local plr = game.Players.LocalPlayer
local char = plr.Character or plr.CharacterAdded:Wait()
local hrp = char:WaitForChild("HumanoidRootPart")

local locations = {
    Spawn = CFrame.new(0, 5, 0),
    Beach = CFrame.new(100, 5, 100),
    Mountain = CFrame.new(-100, 50, -100),
    Castle = CFrame.new(0, 30, -200)
}

-- Efeito visual simples
local function fx()
    local p = Instance.new("ParticleEmitter", hrp)
    p.Texture = "rbxassetid://7157039174"
    p.Lifetime = NumberRange.new(0.5)
    task.delay(1, function() p:Destroy() end)
end

-- Troque o nome aqui para o local desejado
local destination = "Beach" -- opções: Spawn, Beach, Mountain, Castle

if locations[destination] then
    fx()
    task.wait(0.5)
    hrp.CFrame = locations[destination]
else
    warn("Local inválido!")
end
