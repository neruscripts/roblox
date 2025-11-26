local character = game.Players.LocalPlayer.Character
local weapon = character:GetChildren()

for i,v in pairs(weapon) do
    if v:FindFirstChild("Root") then
        weapon = v.Root
    end
end

function findEnemies()
    local toreturn = {}
    for _, v in pairs(game.Workspace:GetChildren()) do
        if v:FindFirstChild("Health") and v:FindFirstChild("HumanoidRootPart") and v.HumanoidRootPart.Velocity ~= Vector3.new(0, 0, 0) then
            local playerPosition = character.HumanoidRootPart.Position
            local enemyPosition = v.HumanoidRootPart.Position
            
            if math.abs(playerPosition.X - enemyPosition.X) < 200 and math.abs(playerPosition.Z - enemyPosition.Z) < 200 then
                table.insert(toreturn, {enemyPosition, v.HumanoidRootPart.CFrame.LookVector})
            end
        end
    end

    return toreturn
end

while task.wait() do
    local success, locations = pcall(findEnemies)
    if success then
        for i = 1, #locations do
            local position = locations[i][1]
            local lookVector = locations[i][2]

            if teleporting == true then
                character.HumanoidRootPart.Position = position - lookVector * 10 + Vector3.new(0, 5, 0) 
            end

            weapon.Position = position
        end

    end
end
