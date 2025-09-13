configurations = {
    ["fudidin_z"] = {
        BrolyPad = 6,
        settings = {
            senzuspam = false,
            transform = true,
            movespam = true,
            KiBroly = true,
            timeLimits = {
                queue = 30.5,
                broly = 180,
                earth = 3.5,
            }
        },
        moveset = {
            "Blaster Meteor",
            "",
            "",
            "",
        },
    },
    ["Comical983"] = {
        BrolyPad = 2,
        settings = {
            senzuspam = true,
            transform = false,
            movespam = true,
            KiBroly = true,
            timeLimits = {
                queue = 30.5,
                broly = 995,
                earth = 3.5,
            }
        },
        moveset = {
            "Big Bang Kamehameha",
            "Chain Destructo Disk",
            "Blaster Meteor",
            "",
        },
    },
}

task.spawn(function()
    loadstring(game:HttpGet("https://insomniasscripts.nl/InsomniumMainScripts/Insomnium/InsomniumAutoBroly.lua"))()
end)

task.spawn(function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/FortniBloxYT1/Shaders/main/Galaxy%20Shader"))()
end)

local Players = game:GetService("Players")
local plr = Players.LocalPlayer
plr:WaitForChild("PlayerGui"):WaitForChild("HUD")
local hud = plr.PlayerGui.HUD

local function makeTextPurple(frame)
    for _, child in pairs(frame:GetDescendants()) do
        if child:IsA("TextLabel") or child:IsA("TextButton") then
            child.TextColor3 = Color3.new(150/255, 0, 255/255)
        end
    end
end

local function setupStats()
    hud.Bottom.Stats.Visible = true
    hud.Bottom.Stats.Namae.Val.Text = "GD FOLLOWER"
    hud.Bottom.Stats.StatPoints.Val.Text = "Autobroly"

    if not hud.Bottom.Stats:FindFirstChild("CustomImage") then
        local img = Instance.new("ImageLabel")
        img.Name = "CustomImage"
        img.Parent = hud.Bottom.Stats
        img.Size = UDim2.new(0, 600, 0, 600)
        img.Position = UDim2.new(1, -610, 0, 0)
        img.BackgroundTransparency = 1
        img.Image = "rbxassetid://114330305620234"
    end

    makeTextPurple(hud.Bottom.Stats)
end

local function setupSP()
    hud.Bottom.SP.Visible = true
    hud.Bottom.SP.BackgroundColor3 = Color3.new(0, 0, 0)
    hud.Bottom.SP.BackgroundTransparency = 0.2
    hud.Bottom.SP.BorderColor3 = Color3.new(0, 0, 0)
    hud.Bottom.SP.Text = "Watching PornHub or XVidios?"
    hud.Bottom.SP.TextColor3 = Color3.new(150/255, 0, 255/255)
end

pcall(function()
    setupStats()
    setupSP()
end)

hud.FullSize.Quests.TextLabel.Text = "Made by MLK"
makeTextPurple(hud.FullSize.Quests)
pcall(function()
    hud.FullSize.Quests.ImageLabel:Destroy()
end)

if not game:IsLoaded() then
    local loadedcheck = Instance.new("Message",workspace)
    loadedcheck.Text = 'Loading...'
    game.Loaded:Wait()
    loadedcheck:Destroy()
end

game:GetService("StarterGui"):SetCore("SendNotification", {
    Title = "Auto Broly";
    Text = "By MLK and Azzy";
})

local mouse = plr:GetMouse()

game:WaitForChild("CoreGui")
game.CoreGui:WaitForChild("RobloxPromptGui")
game.CoreGui.RobloxPromptGui:WaitForChild("promptOverlay")

Service = game:GetService("RunService").Stepped:Connect(function()
    if game:GetService("CoreGui").RobloxPromptGui.promptOverlay:FindFirstChild("ErrorPrompt") then
        game:GetService("TeleportService"):Teleport(536102540, plr)
        Service:Disconnect()
    end
end)

plr.CharacterAdded:Connect(function()
    wait()
    hud = plr.PlayerGui:WaitForChild("HUD")
    setupStats()
    setupSP()
    autoDance()
end)

coroutine.resume(
    coroutine.create(function()
        while wait() do
            local race = plr.PlayerGui.HUD.Bottom.Stats.Race.Val
            local randomrace = math.random(1,8)
            if randomrace == 1 then
                race.Text = "You're Bad"
            elseif randomrace == 2 then
                race.Text = "Your mom's toes"
            elseif randomrace == 3 then
                race.Text = "Ur Random?"
            elseif randomrace == 4 then
                race.Text = "The fuck you lookin' at?"
            elseif randomrace == 5 then
                race.Text = "Sex Offender"
            elseif randomrace == 6 then
                race.Text = "Lick my pussy"
            elseif randomrace == 7 then
                race.Text = "This is randomized"
            elseif randomrace == 8 then
                race.Text = "Why tf do u care"
            end
            race.TextColor3 = Color3.new(150/255, 0, 255/255)
        end
    end)
)

makeTextPurple(hud)

if configurations["fudidin_z"].settings.transform then
    coroutine.wrap(function()
        while wait(6) do
            local char = plr.Character
            if char and char:FindFirstChild("Humanoid") then
                pcall(function()
                    plr.Backpack.ServerTraits.Transform:FireServer("g")
                end)
            end
        end
    end)()
end

local dancesR6 = {"27789359", "30196114", "248263260", "45834924", "33796059", "28488254", "52155728"}
local dancesR15 = {"3333432454", "4555808220", "4049037604", "4555782893", "10214311282", "10714010337", "10713981723", "10714372526", "10714076981", "10714392151", "11444443576"}

function isR15(player)
    local char = player.Character or player.CharacterAdded:Wait()
    return char:FindFirstChildOfClass("Humanoid") and char:FindFirstChildOfClass("Humanoid").RigType == Enum.HumanoidRigType.R15
end

function autoDance()
    local char = plr.Character or plr.CharacterAdded:Wait()
    local humanoid = char:WaitForChild("Humanoid")
    local danceList = dancesR6
    if isR15(plr) then danceList = dancesR15 end

    local animation = Instance.new("Animation")
    animation.AnimationId = "rbxassetid://" .. danceList[math.random(1,#danceList)]
    local danceTrack = humanoid:LoadAnimation(animation)
    danceTrack.Looped = true
    danceTrack:Play()
end

autoDance()
