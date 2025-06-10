# Baconhub
-- ======= Services =======
local Players = game:GetService("Players")
local VirtualUser = game:GetService("VirtualUser")
local TeleportService = game:GetService("TeleportService")
local HttpService = game:GetService("HttpService")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local StarterGui = game:GetService("StarterGui")

local Player = Players.LocalPlayer
local PlayerGui = Player:WaitForChild("PlayerGui")

-- ======= Anti-AFK =======
Player.Idled:Connect(function()
    VirtualUser:Button2Down(Vector2.zero, workspace.CurrentCamera.CFrame)
    task.wait(1)
    VirtualUser:Button2Up(Vector2.zero, workspace.CurrentCamera.CFrame)
end)

-- ======= Startup Sound =======
local startSound = Instance.new("Sound", PlayerGui)
startSound.SoundId = "rbxassetid://4784763177"
startSound.Volume = 1
startSound:Play()

-- ======= Load UI Library =======
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/DenDenZZZ/Kavo-UI-Library/main/Kavo.lua"))()
local Window = Library.CreateLib("BaconHub", "BloodTheme")

-- ======= Credits Tab =======
local CreditsTab = Window:NewTab("Credits")
local CreditsSection = CreditsTab:NewSection("Info")

CreditsSection:NewLabel("This is the official BaconHub.")
CreditsSection:NewLabel("Thanks to Hehehe on Discord.")
CreditsSection:NewLabel("Thanks for using this script!")

CreditsSection:NewButton("Rejoin Server", "Rejoins the game", function()
    TeleportService:Teleport(game.PlaceId, Player)
end)

CreditsSection:NewButton("Server Hop", "Join a different server", function()
    local success, servers = pcall(function()
        return HttpService:JSONDecode(game:HttpGet("https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100"))
    end)

    if success and servers and servers.data then
        for _, server in ipairs(servers.data) do
            if server.playing < server.maxPlayers and server.id ~= game.JobId then
                TeleportService:TeleportToPlaceInstance(game.PlaceId, server.id, Player)
                break
            end
        end
    else
        warn("Failed to fetch server list.")
    end
end)

-- ======= Fly Tab =======
local FlyTab = Window:NewTab("Fly")
local FlySection = FlyTab:NewSection("Fly Options")

FlySection:NewButton("Fly", "Enables flying", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/someflyscriptid"))()
end)

FlySection:NewButton("FPS Boost", "Improves performance", function()
    for _, obj in ipairs(game:GetDescendants()) do
        if obj:IsA("Texture") or obj:IsA("Decal") or obj:IsA("ParticleEmitter") or obj:IsA("Trail") then
            obj:Destroy()
        end
    end
    pcall(function()
        sethiddenproperty(game.Lighting, "Technology", Enum.Technology.Compatibility)
    end)
    game.Lighting.GlobalShadows = false
    game.Lighting.FogEnd = 100000
end)

-- ======= Infinite Jump =======
local InfiniteJumpEnabled = false
UserInputService.JumpRequest:Connect(function()
    if InfiniteJumpEnabled then
        local char = Player.Character or Player.CharacterAdded:Wait()
        local humanoid = char:FindFirstChildOfClass("Humanoid")
        if humanoid then humanoid:ChangeState(Enum.HumanoidStateType.Jumping) end
    end
end)

FlySection:NewToggle("Infinite Jump", "Toggle infinite jumping", function(state)
    InfiniteJumpEnabled = state
end)

-- ======= MM2 Tab =======
local MM2Tab = Window:NewTab("MM2")
local MM2Section = MM2Tab:NewSection("Xhub Loader")

MM2Section:NewButton("Load Xhub", "Loads Xhub script", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/andreylangtoh01/Xhub/refs/heads/main/Xhub"))()
end)

MM2Section:NewButton("Egg Farm", "Farm Easter eggs", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/AmareScripts/MM2/refs/heads/main/Easter%25AutoFarm.lua"))()
end)

-- ======= Super Tab =======
local SuperTab = Window:NewTab("Super")
local SuperSection = SuperTab:NewSection("Secret Script")

SuperSection:NewButton("Super S&J", "Secret script", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/mekUsJ6i"))()
end)

-- ======= Troll Tab =======
local TrollTab = Window:NewTab("Troll💀")
local TrollSection = TrollTab:NewSection("FE Troll Tools")

TrollSection:NewButton("Fling Touch", "Fling others by touching them", function()
    loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Touch-fling-script-22447"))()
end)

TrollSection:NewButton("Invisible", "Makes you invisible", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/3Rnd9rHf"))()
end)

TrollSection:NewButton("Nameless Admin", "Loads Nameless Admin", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/jnsug6TB"))()
end)

TrollSection:NewButton("Bypass Chat", "Set language to ka3ak first", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/twig76/ayra/refs/heads/main/ayras"))()
end)

TrollSection:NewButton("Player ESP", "Highlights players", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/cool83birdcarfly02six/UNIVERSALESPLTX/main/README.md"))()
end)

-- ======= Blade Ball Tab =======
local BBTab = Window:NewTab("Blade Ball")
local BBSection = BBTab:NewSection("Kalitor")

BBSection:NewButton("BladeBall OP", "Loads OP bladeball script", function()
    loadstring(game:HttpGet("https://api.luarmor.net/files/v3/loaders/a70e413180d7ede96d4a09705648f630.lua"))()
end)

BBSection:NewButton("Ash", "Loads Ash script", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/sirapobsriumang/Blade-ball/main/Blade-ball-free.lua"))()
end)

-- ======= Discord Tab =======
local DiscordSection = Window:NewTab("Discord"):NewSection("Join Our Server")

DiscordSection:NewButton("Join Discord", "Copies invite to clipboard", function()
    local link = "https://discord.gg/w6PyskFT47"
    if setclipboard then
        setclipboard(link)
        StarterGui:SetCore("SendNotification", {
            Title = "Discord",
            Text = "Link copied to clipboard!",
            Duration = 4
        })
    else
        warn("Clipboard not supported.")
    end
end)

-- ======= Executor Tab =======
local ExecutorTab = Window:NewTab("Executor")
local ExecutorSection = ExecutorTab:NewSection("Script Runner")
local savedScripts, historyButtons = {}, {}
local outputLabel = ExecutorSection:NewLabel("Output will appear here.")

local function updateHistoryButtons()
    for _, btn in ipairs(historyButtons) do btn:Remove() end
    historyButtons = {}

    for i, scriptCode in ipairs(savedScripts) do
        local short = scriptCode:sub(1, 30):gsub("\n", " ") .. (#scriptCode > 30 and "..." or "")
        local btn = ExecutorTab:NewSection("History"):NewButton("Run #" .. i .. ": " .. short, "Run this script again", function()
            local s, e = pcall(function() return loadstring(scriptCode)() end)
            outputLabel.Text = s and "Script #" .. i .. " ran successfully!" or "Error: " .. tostring(e)
        end)
        table.insert(historyButtons, btn)
    end
end

ExecutorSection:NewTextBox("Run Script", "Paste your Lua code here", function(code)
    if code == "" then outputLabel.Text = "No script to run!" return end
    local success, result = pcall(function() return loadstring(code)() end)
    outputLabel.Text = success and "Script ran successfully!" or "Error: " .. tostring(result)
    if success then
        table.insert(savedScripts, 1, code)
        if #savedScripts > 5 then table.remove(savedScripts, 6) end
        updateHistoryButtons()
    end
end)

ExecutorSection:NewTextBox("Run Script from URL", "Enter Pastebin/raw GitHub URL", function(url)
    if url == "" then outputLabel.Text = "No URL entered." return end
    local ok, response = pcall(function() return game:HttpGet(url) end)
    if ok then
        local s, e = pcall(function() return loadstring(response)() end)
        outputLabel.Text = s and "Script from URL ran successfully!" or "Error: " .. tostring(e)
        if s then
            table.insert(savedScripts, 1, response)
            if #savedScripts > 5 then table.remove(savedScripts, 6) end
            updateHistoryButtons()
        end
    else
        outputLabel.Text = "Failed to fetch script from URL."
    end
end)

ExecutorSection:NewButton("Clear Output", "Clears output label", function()
    outputLabel.Text = ""
end)

-- ======= Universal Tab =======
local UniversalTab = Window:NewTab("Universal")
local UniversalSection = UniversalTab:NewSection("FE Scripts")

UniversalSection:NewButton("Invisible 2.1", "Makes your character invisible", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/vP6CrQJj"))()
end)

UniversalSection:NewButton("Aimbot", "Enables a universal aimbot", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/DanielHubll/DanielHubll/refs/heads/main/Aimbot%20Mobile"))()
end)

UniversalSection:NewButton("Hitbox Extender", "Extends enemy hitboxes", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/AAPVdev/scripts/refs/heads/main/UI_LimbExtender.lua"))()
end)

UniversalSection:NewButton("Animation Stealer", "Loads SP_Hub Animations script", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/as6cd0/SP_Hub/refs/heads/main/Animations"))()
end)

-- ======= Toggle UI Button =======
local ToggleGui = Instance.new("ScreenGui", PlayerGui)
ToggleGui.Name = "ToggleUI"
ToggleGui.ResetOnSpawn = false

local Button = Instance.new("TextButton", ToggleGui)
Button.Name = "Toggle"
Button.Size = UDim2.new(0, 120, 0, 40)
Button.Position = UDim2.new(0, 0, 0.45, 0)
Button.Font = Enum.Font.GothamBold
Button.Text = "Close / Open"
Button.TextSize = 22
Button.TextColor3 = Color3.new(1, 1, 1)
Button.Draggable = true
Instance.new("UICorner", Button).CornerRadius = UDim.new(0, 10)

local openSfx = Instance.new("Sound", PlayerGui)
openSfx.SoundId = "rbxassetid://5608077885"
openSfx.Volume = 1

local closeSfx = Instance.new("Sound", PlayerGui)
closeSfx.SoundId = "rbxassetid://7261232562"
closeSfx.Volume = 1

local isOpen = true
RunService.RenderStepped:Connect(function()
    local hue = tick() % 5 / 5
    Button.BackgroundColor3 = Color3.fromHSV(hue, 1, 1)
end)

Button.MouseButton1Click:Connect(function()
    isOpen = not isOpen
    Library:ToggleUI()
    if isOpen then openSfx:Play() else closeSfx:Play() end
end)
