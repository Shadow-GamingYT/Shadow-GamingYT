local MarketplaceService = game:GetService("MarketplaceService")
local Players = game:GetService("Players")

local passID = 0000000  -- Change this to your Pass ID

local function onPlayerAdded(player)
	local hasPass = false

	-- Check if the player already owns the Pass
	local success, message = pcall(function()
		hasPass = MarketplaceService:UserOwnsGamePassAsync(player.UserId, passID)
	end)

	-- If there's an error, issue a warning and exit the function
	if not success then
		warn("Error while checking if player has pass: " .. tostring(message))
		return
	end

	if hasPass then
		print(player.Name .. " owns the Pass with ID " .. passID)
		-- Assign this player the ability or bonus related to the Pass
	end
end

-- Connect "PlayerAdded" events to the function
Players.PlayerAdded:Connect(onPlayerAdded)
