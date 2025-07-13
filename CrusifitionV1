--[[
    Crucifixion Cross & Glowing Orbs Script by AbsoluteAdamus
    Features:
    - Large glowing white crucifixion-style neon cross on player’s back
    - Two glowing neon orbs orbiting player (crimson and golden)
--]]

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Clean previous effects
if character:FindFirstChild("HolyCross") then character.HolyCross:Destroy() end
if character:FindFirstChild("GlowingOrbs") then character.GlowingOrbs:Destroy() end

-- Create Cross Model
local cross = Instance.new("Model", character)
cross.Name = "HolyCross"

-- Vertical beam (10 studs tall)
local vertical = Instance.new("Part")
vertical.Size = Vector3.new(0.5, 10, 0.5)
vertical.Material = Enum.Material.Neon
vertical.BrickColor = BrickColor.White()
vertical.CanCollide = false
vertical.Anchored = false
vertical.Name = "Vertical"
vertical.CFrame = character.HumanoidRootPart.CFrame * CFrame.new(0, 3, 1.5) * CFrame.Angles(0, 0, math.rad(15)) -- leaning right
vertical.Parent = cross

-- Horizontal beam (2 studs wide, placed lower)
local horizontal = Instance.new("Part")
horizontal.Size = Vector3.new(2, 0.5, 0.5)
horizontal.Material = Enum.Material.Neon
horizontal.BrickColor = BrickColor.White()
horizontal.CanCollide = false
horizontal.Anchored = false
horizontal.Name = "Horizontal"
horizontal.CFrame = vertical.CFrame * CFrame.new(0, 2, 0)
horizontal.Parent = cross

-- Weld cross pieces
local weld1 = Instance.new("WeldConstraint", vertical)
weld1.Part0 = vertical
weld1.Part1 = horizontal

local weld2 = Instance.new("WeldConstraint", vertical)
weld2.Part0 = vertical
weld2.Part1 = character.HumanoidRootPart

-- Create glowing orbs folder
local orbsFolder = Instance.new("Folder", character)
orbsFolder.Name = "GlowingOrbs"

-- Function to create a glowing orb
local function createOrb(color, startAngle)
    local orb = Instance.new("Part")
    orb.Shape = Enum.PartType.Ball
    orb.Size = Vector3.new(1.5, 1.5, 1.5)
    orb.Material = Enum.Material.Neon
    orb.BrickColor = BrickColor.new(color)
    orb.Anchored = false
    orb.CanCollide = false
    orb.Name = color .. "Orb"
    orb.Parent = orbsFolder

    local rootAttachment = Instance.new("Attachment", character.HumanoidRootPart)
    local orbAttachment = Instance.new("Attachment", orb)

    local alignPos = Instance.new("AlignPosition", orb)
    alignPos.Attachment0 = orbAttachment
    alignPos.Attachment1 = rootAttachment
    alignPos.RigidityEnabled = false
    alignPos.MaxForce = math.huge
    alignPos.Responsiveness = 50

    local angle = startAngle
    local radius = 5

    game:GetService("RunService").Heartbeat:Connect(function()
        angle += 0.015
        local x = math.cos(angle) * radius
        local z = math.sin(angle) * radius
        rootAttachment.Position = Vector3.new(x, 3, z)
    end)
end

-- Create crimson orb and golden orb
createOrb("Crimson", 0)
createOrb("Gold", math.pi)
