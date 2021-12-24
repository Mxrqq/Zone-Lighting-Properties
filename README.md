-- Servicios

local replicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")

-- Remote event

local CambiarLightingEvent = replicatedStorage:WaitForChild("LightingEvents"):WaitForChild("Zona1")

script.Parent.Touched:Connect(function(hit)
	if hit.Name == "HumanoidRootPart" then
		local hitPlayer = Players:GetPlayerFromCharacter(hit.Parent)
		CambiarLightingEvent.CambiarLighting:FireClient(hitPlayer) -- Fire Client hará que la función solo se active para un solo jugador.
	end
end)

script.Parent.TouchEnded:Connect(function(hit)
	if hit.Name == "HumanoidRootPart" then
		local hitPlayer = Players:GetPlayerFromCharacter(hit.Parent)
		CambiarLightingEvent.RestaurarLighting:FireClient(hitPlayer)
	end
end)
