if game.PlaceId == 3101667897 then
    local OrionLib = loadstring(game:HttpGet('https://raw.githubusercontent.com/shlexware/Orion/main/source'))()
    local Window = OrionLib:MakeWindow({Name = "Lite Hub", HidePremium = false, SaveConfig = true, IntroEnabled = false})
 
    -- Values
    _G.AutoOrbs = false
    _G.SelectOrb = "Red Orb"
    _G.SelectCity = "City"
    _G.AutoFillRace = false
    _G.autoHatch = false
    _G.selectEgg = "Electro Legends Crystal"
    _G.AutoFinishRace = false
    _G.autoRebirth = false
    getgenv().AutoHoop = false
    _G.TextBoxValue = ""
    _G.SendInChat = false
 
    -- Functions
    function AutoOrb()
        while _G.AutoOrbs do
            local args = {
                [1] = "collectOrb",
                [2] = _G.SelectOrb,
                [3] = _G.SelectCity
            }
            for i = 1, 200 do
                game:GetService("ReplicatedStorage"):WaitForChild("rEvents"):WaitForChild("orbEvent"):FireServer(unpack(args))
            end
            wait(0.25)
        end
    end    
 
    function joinRace()
        while _G.AutoFillRace do
            local args = {
                [1] = "joinRace"
            }
            game:GetService("ReplicatedStorage"):WaitForChild("rEvents"):WaitForChild("raceEvent"):FireServer(unpack(args))
            wait(0.0001) -- Adjusted wait time for performance
        end
    end
 
    function autoHatch()
        while _G.autoHatch do
            local args = {
                [1] = "openCrystal",
                [2] = _G.selectEgg
            }
            game:GetService("ReplicatedStorage"):WaitForChild("rEvents"):WaitForChild("openCrystalRemote"):InvokeServer(unpack(args))
            wait(0.01) -- Adjusted wait time for performance
        end
    end
 
    function AutoFinishRace()
        while _G.AutoFinishRace do
            local positions = {
                CFrame.new(1686.07495, 36.3147125, -5946.63428, -0.984812617, 0, 0.173621148, 0, 1, 0, -0.173621148, 0, -0.984812617),
                CFrame.new(48.3109131, 36.3147125, -8680.45312, -1, 0, 0, 0, 1, 0, 0, 0, -1),
                CFrame.new(1001.33118, 36.3147125, -10986.2178, -0.996191859, 0, -0.0871884301, 0, 1, 0, 0.0871884301, 0, -0.996191859)
            }
 
            local plr = game.Players.LocalPlayer
            local char = plr.Character
 
            if char and char:FindFirstChild("HumanoidRootPart") then
                for _, cframe in ipairs(positions) do
                    char.HumanoidRootPart.CFrame = cframe
                    wait(0.01) -- Adjust the wait time as needed
                end
            end
        end
    end
 
    function autoRebirth()
        while _G.autoRebirth do
            local args = {
                [1] = "rebirthRequest"
            }
            game:GetService("ReplicatedStorage"):WaitForChild("rEvents"):WaitForChild("rebirthEvent"):FireServer(unpack(args))
            wait(0.1)
        end
    end
 
    function SendMessage()
        while _G.SendInChat do
            if _G.TextBoxValue and _G.TextBoxValue ~= "" then
                game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(_G.TextBoxValue, "All")
            end
            wait(1.5)
        end
    end
 
    -- Tabs
    local MainTab = Window:MakeTab({
        Name = "Main",
        Icon = "rbxassetid://18840887514",
        PremiumOnly = false
    })
 
    local AutoFarmTab = Window:MakeTab({
        Name = "AutoFarm",
        Icon = "rbxassetid://18841546430",
        PremiumOnly = false
    })
 
    local TeleportsTab = Window:MakeTab({
        Name = "Teleports",
        Icon = "rbxassetid://18840895966",
        PremiumOnly = false
    })
 
    local AutoRaceTab = Window:MakeTab({
        Name = "Auto Race",
        Icon = "rbxassetid://18840911898",
        PremiumOnly = false
    })
 
    local ChatTab = Window:MakeTab({
        Name = "Chat",
        Icon = "rbxassetid://18854016467",
        PremiumOnly = false
    })
 
    local EggsTab = Window:MakeTab({
        Name = "Eggs",
        Icon = "rbxassetid://18840914110",
        PremiumOnly = false
    })
 
    local RebirthTab = Window:MakeTab({
        Name = "Rebirth",
        Icon = "rbxassetid://18842462752",
        PremiumOnly = false
    })
 
    local Tab = Window:MakeTab({
        Name = "Credit",
        Icon = "rbxassetid://18853737625",
        PremiumOnly = false
    })
 
    -- Sections
 
MainTab:AddSection({
        Name = "Hoops Farming"
    })
 
    Tab:AddSection({
        Name = "Made By Adopt"
    })
 
    Tab:AddSection({
        Name = "Credit to lucky and Cryo for helping me a bit"
    })
 
    Tab:AddSection({
        Name = "Credit to Ras for making showcase video"
    })
 
    Tab:AddSection({
        Name = "Inspiration: Cryo Hub"
    })
 
--buttons
    TeleportsTab:AddButton({
        Name = "City",
        Callback = function()
            local plr = game.Players.LocalPlayer
            local char = plr.Character
            if char and char:FindFirstChild("HumanoidRootPart") then
                char.HumanoidRootPart.CFrame = CFrame.new(-9684.84473, 60.6541595, 3093.29663)
            end
        end
    })
 
    TeleportsTab:AddButton({
        Name = "Snow City",
        Callback = function()
            local plr = game.Players.LocalPlayer
            local char = plr.Character
            if char and char:FindFirstChild("HumanoidRootPart") then
                char.HumanoidRootPart.CFrame = CFrame.new(-9673.79102, 60.6541595, 3788.24927)
            end
        end
    })
 
    TeleportsTab:AddButton({
        Name = "Magma City",
        Callback = function()
            local plr = game.Players.LocalPlayer
            local char = plr.Character
            if char and char:FindFirstChild("HumanoidRootPart") then
                char.HumanoidRootPart.CFrame = CFrame.new(-11053.1162, 218.589584, 4904.35938)
            end
        end
    })
 
    TeleportsTab:AddButton({
        Name = "Legends Highway",
        Callback = function()
            local plr = game.Players.LocalPlayer
            local char = plr.Character
            if char and char:FindFirstChild("HumanoidRootPart") then
                char.HumanoidRootPart.CFrame = CFrame.new(-13097.0186, 218.589584, 5913.35889)
            end
        end
    })
 
    TeleportsTab:AddButton({
        Name = "Space",
        Callback = function()
            local plr = game.Players.LocalPlayer
            local char = plr.Character
            if char and char:FindFirstChild("HumanoidRootPart") then
                char.HumanoidRootPart.CFrame = CFrame.new(-331.764069, 5.45415115, 585.201721)
            end
        end
    })
 
    TeleportsTab:AddButton({
        Name = "Desert",
        Callback = function()
            local plr = game.Players.LocalPlayer
            local char = plr.Character
            if char and char:FindFirstChild("HumanoidRootPart") then
                char.HumanoidRootPart.CFrame = CFrame.new(-9515.24805, 57.1541519, 1607.96765)
            end
        end
    })
 
 
 
    -- Toggle
 
MainTab:AddToggle({
	    Name = "Auto Hoop",
	    Default = false,
	    Callback = function(Value)
		    getgenv().AutoHoop = Value
		    spawn(function()
                while getgenv().AutoHoop == true do
                    for i, v in pairs(game:GetService("Workspace").Hoops:GetChildren()) do
                        firetouchinterest(v, game:GetService("Players").LocalPlayer.Character.HumanoidRootPart, 0)
                        wait()
                        firetouchinterest(v, game:GetService("Players").LocalPlayer.Character.HumanoidRootPart, 1)
                    end
                end
            end)    
	    end
    })
 
--section
MainTab:AddSection({
        Name = "Speed/Jump Settings"
    })
 
    AutoFarmTab:AddToggle({
        Name = "Auto Orbs",
        Default = false,
        Callback = function(Value)
            _G.AutoOrbs = Value
            if Value then
                spawn(AutoOrb)
            end
        end
    })
 
    AutoRaceTab:AddToggle({
        Name = "Auto Fill Race",
        Default = false,
        Callback = function(Value)
            _G.AutoFillRace = Value
            if Value then
                spawn(joinRace)
            end
        end
    })
 
    EggsTab:AddToggle({
        Name = "Auto Hatch",
        Default = false,
        Callback = function(Value)
            _G.autoHatch = Value
            if Value then
                spawn(autoHatch)
            end
        end
    })
 
    RebirthTab:AddToggle({
        Name = "Auto Rebirth",
        Default = false,
        Callback = function(Value)
            _G.autoRebirth = Value
            if Value then
                spawn(autoRebirth)
            end
        end
    })
 
    AutoRaceTab:AddToggle({
        Name = "Auto Finish Race",
        Default = false,
        Callback = function(Value)
            _G.AutoFinishRace = Value
            if Value then
                spawn(AutoFinishRace)
            end
        end
    })
 
    EggsTab:AddDropdown({
        Name = "Select Egg",
        Default = "Electro Legends Crystal",
        Options = {"Yellow Crystal", "Blue Crystal", "Red Crystal", "Lightning Crystal", "Inferno Crystal", "Lava Crystal", "Snow Crystal", "Electro Legends Crystal", "Space Crystal", "Alien Crystal", "Electro Crystal", "Desert Crystal"},
        Callback = function(Value)
            _G.selectEgg = Value
        end
    })
 
    AutoFarmTab:AddDropdown({
        Name = "Select Orb",
        Default = "Red Orb",
        Options = {"Red Orb", "Blue Orb", "Orange Orb", "Gem", "Yellow Orb"},
        Callback = function(Value)
            _G.SelectOrb = Value
        end
    })
 
    AutoFarmTab:AddDropdown({
        Name = "Select City",
        Default = "City",
        Options = {"City", "Snow City", "Magma City", "Legends Highway", "Space", "Desert",},
        Callback = function(Value)
            _G.SelectCity = Value
        end
    })
 
    ChatTab:AddTextbox({
        Name = "Text Box",
        Default = "",
        TextDisappear = false,
        Callback = function(Value)
            _G.TextBoxValue = Value
        end
    })
 
    MainTab:AddTextbox({
        Name = "Speed Power",
        Default = "",
        TextDisappear = false,
        Callback = function(Value)
            _G.TextBoxValue = Value
        end
    })
 
    MainTab:AddTextbox({
        Name = "Jump Power",
        Default = "",
        TextDisappear = false,
        Callback = function(Value)
            _G.TextBoxValue = Value
        end
    })
 
    ChatTab:AddToggle({
        Name = "Send In Chat",
        Default = false,
        Callback = function(Value)
            _G.SendInChat = Value
            if Value then
                spawn(SendMessage)
            end
        end
    })
 
--section
local Section = AutoFarmTab:AddSection({
	Name = "Anti Lags"
})
 
    -- Buttons
AutoFarmTab:AddButton({
	Name = "Anti Ping",
	Callback = function()
      		local decalsyeeted = true -- Leaving this on makes games look shitty but the fps goes up by at least 20.
local g = game
local w = g.Workspace
local l = g.Lighting
local t = w.Terrain
t.WaterWaveSize = 0
t.WaterWaveSpeed = 0
t.WaterReflectance = 0
t.WaterTransparency = 0
l.GlobalShadows = false
l.FogEnd = 9e9
l.Brightness = 0
settings().Rendering.QualityLevel = "Level01"
for i, v in pairs(g:GetDescendants()) do
    if v:IsA("Part") or v:IsA("Union") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then
        v.Material = "Plastic"
        v.Reflectance = 0
    elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then
        v.Transparency = 1
    elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
        v.Lifetime = NumberRange.new(0)
    elseif v:IsA("Explosion") then
        v.BlastPressure = 1
        v.BlastRadius = 1
    elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") then
        v.Enabled = false
    elseif v:IsA("MeshPart") then
        v.Material = "Plastic"
        v.Reflectance = 0
        v.TextureID = 10385902758728957
    end
end
for i, e in pairs(l:GetChildren()) do
    if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
        e.Enabled = false
    end
end
  	end    
})
 
 
    OrionLib:Init()
