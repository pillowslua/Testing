local Players = game:GetService("Players")
local localPlayer = Players.LocalPlayer

local function OnRenderStepped()
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= localPlayer then
            local distance = (player.Character.HumanoidRootPart.Position - localPlayer.Character.HumanoidRootPart.Position).Magnitude
            if distance <= 10 then -- Chỉ hiển thị tên khi người chơi cách bạn dưới 10 studs
                -- Tạo một TextLabel tại vị trí của người chơi
                local textLabel = Instance.new("TextLabel")
                textLabel.Parent = game.Workspace
                textLabel.Position = player.Character.Head.Position
                textLabel.Size = UDim2.new(0, 100, 0, 20)
                textLabel.Text = player.Name
                textLabel.TextColor3 = Color3.fromRGB(255, 0, 0) -- Màu đỏ
            end
        end
    end
end

RunService.RenderStepped:Connect(OnRenderStepped)
