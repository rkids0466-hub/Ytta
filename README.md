local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local MarketplaceService = game:GetService("MarketplaceService")
local RunService = game:GetService("RunService")
local Stats = game:GetService("Stats")

local LocalPlayer = Players.LocalPlayer

-- DAFTAR ADMIN AWAL
local AdminList = {
    ["LifzxAfter2"] = "ADMIN",
    ["Yanzzz_1023"] = "PEMILIK"
}

-- ==========================================
-- KODE REDEEM PREMIUM (TER-OBFUSCATE 100%)
-- Tidak dapat dibaca manusia, namun berfungsi normal
-- ==========================================
local _0x8F2A = (function()
    local _0x1B = string.char
    local _0x2C = {
        80, 82, 69, 77, 73, 85, 77, 45, 53, 53, 48, 55, 45, 57, 52, 68, 49, 45, 53, 68, 68, 69, 124, 80, 82, 69, 77, 73, 85, 77, 45, 51, 67, 54, 55, 45, 51, 67, 51, 49, 45, 49, 57, 68, 53, 124, 80, 82, 69, 77,
        73, 85, 77, 45, 67, 50, 56, 49, 45, 50, 53, 56, 65, 45, 67, 50, 48, 52, 124, 80, 82, 69, 77, 73, 85, 77, 45, 67, 53, 50, 48, 45, 51, 67, 67, 49, 45, 53, 54, 68, 55, 124, 80, 82, 69, 77, 73, 85, 77, 45,
        68, 56, 51, 49, 45, 55, 53, 70, 57, 45, 69, 57, 70, 57, 124, 80, 82, 69, 77, 73, 85, 77, 45, 57, 50, 50, 65, 45, 53, 51, 69, 66, 45, 66, 52, 54, 65, 124, 80, 82, 69, 77, 73, 85, 77, 45, 51, 53, 57, 49,
        45, 54, 67, 52, 52, 45, 65, 65, 49, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 49, 68, 66, 54, 45, 54, 69, 54, 49, 45, 51, 68, 67, 56, 124, 80, 82, 69, 77, 73, 85, 77, 45, 55, 54, 65, 56, 45, 56, 56, 65,
        54, 45, 49, 66, 70, 52, 124, 80, 82, 69, 77, 73, 85, 77, 45, 53, 70, 54, 57, 45, 55, 54, 57, 65, 45, 57, 50, 49, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 66, 69, 65, 48, 45, 57, 69, 69, 48, 45, 52, 51,
        52, 67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 70, 48, 51, 55, 45, 48, 51, 55, 67, 45, 52, 67, 67, 66, 124, 80, 82, 69, 77, 73, 85, 77, 45, 48, 65, 69, 55, 45, 56, 56, 51, 55, 45, 49, 49, 53, 55, 124, 80,
        82, 69, 77, 73, 85, 77, 45, 68, 67, 53, 68, 45, 70, 50, 68, 52, 45, 48, 55, 67, 52, 124, 80, 82, 69, 77, 73, 85, 77, 45, 50, 65, 49, 65, 45, 52, 51, 56, 68, 45, 67, 51, 70, 54, 124, 80, 82, 69, 77, 73,
        85, 77, 45, 49, 49, 50, 50, 45, 50, 67, 56, 52, 45, 65, 67, 66, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 48, 68, 51, 70, 45, 54, 68, 48, 57, 45, 70, 56, 68, 66, 124, 80, 82, 69, 77, 73, 85, 77, 45, 70,
        52, 69, 56, 45, 50, 56, 49, 51, 45, 49, 48, 50, 68, 124, 80, 82, 69, 77, 73, 85, 77, 45, 54, 69, 55, 49, 45, 50, 65, 53, 67, 45, 55, 70, 48, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 68, 55, 66, 55, 45,
        65, 49, 68, 70, 45, 69, 68, 50, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 52, 53, 70, 66, 45, 65, 57, 53, 51, 45, 55, 50, 67, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 65, 48, 48, 70, 45, 66, 50, 67, 68,
        45, 52, 53, 57, 54, 124, 80, 82, 69, 77, 73, 85, 77, 45, 48, 52, 51, 67, 45, 51, 51, 69, 52, 45, 51, 67, 52, 54, 124, 80, 82, 69, 77, 73, 85, 77, 45, 67, 54, 68, 56, 45, 68, 53, 70, 53, 45, 49, 48, 66,
        66, 124, 80, 82, 69, 77, 73, 85, 77, 45, 52, 67, 50, 55, 45, 70, 48, 68, 66, 45, 56, 56, 55, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 52, 55, 53, 66, 45, 56, 57, 49, 70, 45, 56, 65, 70, 52, 124, 80, 82,
        69, 77, 73, 85, 77, 45, 56, 55, 56, 52, 45, 55, 54, 70, 70, 45, 56, 53, 55, 52, 124, 80, 82, 69, 77, 73, 85, 77, 45, 69, 69, 53, 70, 45, 69, 54, 50, 48, 45, 50, 51, 65, 51, 124, 80, 82, 69, 77, 73, 85,
        77, 45, 68, 49, 69, 67, 45, 56, 67, 52, 51, 45, 48, 49, 65, 53, 124, 80, 82, 69, 77, 73, 85, 77, 45, 56, 67, 53, 67, 45, 67, 55, 56, 65, 45, 53, 48, 56, 67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 70, 65,
        50, 53, 45, 70, 69, 52, 65, 45, 70, 51, 68, 57, 124, 80, 82, 69, 77, 73, 85, 77, 45, 67, 69, 65, 67, 45, 57, 50, 69, 52, 45, 55, 70, 68, 53, 124, 80, 82, 69, 77, 73, 85, 77, 45, 48, 68, 55, 65, 45, 48,
        69, 50, 51, 45, 48, 68, 65, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 69, 67, 52, 56, 45, 66, 51, 70, 67, 45, 66, 54, 49, 69, 124, 80, 82, 69, 77, 73, 85, 77, 45, 52, 57, 69, 48, 45, 65, 67, 55, 66, 45,
        54, 70, 50, 67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 68, 52, 57, 69, 45, 56, 50, 49, 52, 45, 68, 69, 54, 49, 124, 80, 82, 69, 77, 73, 85, 77, 45, 56, 69, 65, 48, 45, 65, 55, 54, 50, 45, 68, 56, 68, 52,
        124, 80, 82, 69, 77, 73, 85, 77, 45, 53, 55, 55, 49, 45, 57, 68, 48, 66, 45, 48, 57, 55, 57, 124, 80, 82, 69, 77, 73, 85, 77, 45, 56, 57, 53, 69, 45, 50, 57, 54, 67, 45, 48, 67, 49, 67, 124, 80, 82, 69,
        77, 73, 85, 77, 45, 65, 54, 56, 48, 45, 53, 50, 52, 50, 45, 67, 70, 48, 54, 124, 80, 82, 69, 77, 73, 85, 77, 45, 52, 52, 54, 66, 45, 55, 68, 55, 70, 45, 56, 48, 69, 70, 124, 80, 82, 69, 77, 73, 85, 77,
        45, 52, 56, 53, 69, 45, 65, 68, 67, 52, 45, 56, 50, 57, 67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 52, 65, 69, 70, 45, 70, 68, 68, 48, 45, 49, 51, 69, 53, 124, 80, 82, 69, 77, 73, 85, 77, 45, 49, 51, 56,
        58, 45, 65, 49, 57, 56, 45, 54, 65, 52, 57, 124, 80, 82, 69, 77, 73, 85, 77, 45, 70, 55, 56, 55, 45, 69, 55, 68, 70, 45, 54, 55, 54, 66, 124, 80, 82, 69, 77, 73, 85, 77, 45, 57, 69, 53, 69, 45, 57, 70,
        66, 57, 45, 55, 52, 69, 50, 124, 80, 82, 69, 77, 73, 85, 77, 45, 53, 68, 66, 55, 45, 67, 49, 56, 56, 45, 54, 69, 55, 67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 52, 70, 67, 51, 45, 68, 55, 49, 51, 45, 66,
        56, 70, 53, 124, 80, 82, 69, 77, 73, 85, 77, 45, 67, 54, 52, 69, 45, 51, 57, 50, 68, 45, 68, 51, 51, 50, 124, 80, 82, 69, 77, 73, 85, 77, 45, 55, 53, 52, 48, 45, 52, 67, 69, 56, 45, 49, 57, 69, 70, 124,
        80, 82, 69, 77, 73, 85, 77, 45, 50, 50, 66, 55, 45, 53, 55, 56, 53, 45, 51, 55, 48, 52, 124, 80, 82, 69, 77, 73, 85, 77, 45, 67, 55, 65, 54, 45, 53, 68, 68, 49, 45, 57, 50, 56, 48, 124, 80, 82, 69, 77,
        73, 85, 77, 45, 50, 67, 48, 48, 45, 52, 65, 53, 52, 45, 65, 54, 57, 66, 124, 80, 82, 69, 77, 73, 85, 77, 45, 67, 66, 48, 54, 45, 68, 70, 67, 49, 45, 52, 49, 51, 55, 124, 80, 82, 69, 77, 73, 85, 77, 45,
        70, 54, 53, 65, 45, 50, 49, 67, 56, 45, 65, 56, 49, 48, 124, 80, 82, 69, 77, 73, 85, 77, 45, 68, 70, 51, 70, 45, 57, 51, 55, 68, 45, 68, 51, 55, 68, 124, 80, 82, 69, 77, 73, 85, 77, 45, 54, 51, 51, 54,
        45, 68, 67, 56, 66, 45, 65, 49, 69, 53, 124, 80, 82, 69, 77, 73, 85, 77, 45, 55, 52, 67, 52, 45, 49, 48, 67, 48, 45, 66, 54, 70, 56, 124, 80, 82, 69, 77, 73, 85, 77, 45, 55, 57, 67, 66, 45, 54, 56, 69,
        54, 45, 56, 53, 66, 68, 124, 80, 82, 69, 77, 73, 85, 77, 45, 68, 53, 65, 67, 45, 49, 67, 56, 55, 45, 50, 55, 51, 56, 124, 80, 82, 69, 77, 73, 85, 77, 45, 48, 69, 53, 57, 45, 52, 49, 52, 69, 45, 54, 53,
        68, 50, 124, 80, 82, 69, 77, 73, 85, 77, 45, 70, 65, 52, 68, 45, 56, 57, 51, 52, 45, 55, 67, 51, 67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 55, 55, 68, 70, 45, 49, 70, 67, 53, 45, 55, 65, 68, 68, 124, 80,
        82, 69, 77, 73, 85, 77, 45, 51, 52, 53, 67, 45, 53, 52, 54, 67, 45, 66, 68, 49, 57, 124, 80, 82, 69, 77, 73, 85, 77, 45, 53, 51, 54, 66, 45, 69, 57, 50, 53, 45, 67, 57, 55, 66, 124, 80, 82, 69, 77, 73,
        85, 77, 45, 49, 70, 51, 70, 45, 51, 50, 69, 70, 45, 66, 49, 54, 48, 124, 80, 82, 69, 77, 73, 85, 77, 45, 51, 56, 65, 48, 45, 53, 48, 55, 55, 45, 57, 65, 66, 55, 124, 80, 82, 69, 77, 73, 85, 77, 45, 55,
        56, 53, 56, 45, 65, 50, 56, 68, 45, 51, 52, 70, 68, 124, 80, 82, 69, 77, 73, 85, 77, 45, 48, 52, 67, 53, 45, 50, 52, 69, 68, 45, 51, 53, 53, 54, 124, 80, 82, 69, 77, 73, 85, 77, 45, 67, 56, 66, 53, 45,
        70, 49, 49, 57, 45, 50, 67, 68, 68, 124, 80, 82, 69, 77, 73, 85, 77, 45, 49, 69, 67, 49, 45, 53, 56, 54, 48, 45, 51, 50, 68, 49, 124, 80, 82, 69, 77, 73, 85, 77, 45, 69, 54, 68, 68, 45, 67, 57, 66, 67,
        45, 53, 69, 67, 65, 124, 80, 82, 69, 77, 73, 85, 77, 45, 51, 53, 54, 66, 45, 50, 70, 57, 50, 45, 67, 54, 53, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 50, 55, 51, 67, 45, 55, 49, 69, 67, 45, 48, 65, 50,
        67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 55, 55, 68, 49, 45, 53, 51, 51, 66, 45, 49, 57, 56, 65, 124, 80, 82, 69, 77, 73, 85, 77, 45, 55, 70, 53, 48, 45, 69, 70, 68, 56, 45, 50, 57, 50, 68, 124, 80, 82,
        69, 77, 73, 85, 77, 45, 48, 69, 70, 54, 45, 56, 57, 54, 68, 45, 69, 69, 50, 54, 124, 80, 82, 69, 77, 73, 85, 77, 45, 56, 50, 68, 69, 45, 70, 57, 67, 52, 45, 53, 56, 67, 50, 124, 80, 82, 69, 77, 73, 85,
        77, 45, 48, 69, 53, 70, 45, 68, 65, 51, 65, 45, 66, 68, 57, 67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 65, 67, 67, 65, 45, 57, 51, 56, 57, 45, 69, 57, 57, 55, 124, 80, 82, 69, 77, 73, 85, 77, 45, 49, 49,
        68, 68, 45, 57, 51, 55, 54, 45, 53, 54, 49, 69, 124, 80, 82, 69, 77, 73, 85, 77, 45, 65, 68, 51, 48, 45, 68, 49, 56, 70, 45, 51, 51, 55, 65, 124, 80, 82, 69, 77, 73, 85, 77, 45, 70, 70, 49, 56, 45, 70,
        57, 50, 70, 45, 49, 54, 48, 67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 56, 54, 66, 49, 45, 51, 68, 68, 69, 45, 68, 65, 70, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 55, 68, 54, 66, 45, 66, 52, 52, 51, 45,
        54, 55, 57, 54, 124, 80, 82, 69, 77, 73, 85, 77, 45, 48, 65, 52, 52, 45, 48, 55, 48, 65, 45, 52, 67, 51, 70, 124, 80, 82, 69, 77, 73, 85, 77, 45, 57, 57, 50, 67, 45, 50, 50, 69, 70, 45, 69, 53, 66, 54,
        124, 80, 82, 69, 77, 73, 85, 77, 45, 53, 51, 48, 65, 45, 49, 50, 50, 65, 45, 49, 67, 65, 57, 124, 80, 82, 69, 77, 73, 85, 77, 45, 54, 54, 53, 56, 45, 54, 56, 48, 55, 45, 52, 68, 68, 55, 124, 80, 82, 69,
        77, 73, 85, 77, 45, 57, 54, 69, 67, 45, 53, 52, 48, 48, 45, 66, 52, 69, 51, 124, 80, 82, 69, 77, 73, 85, 77, 45, 48, 66, 56, 56, 45, 57, 55, 57, 66, 45, 66, 69, 70, 57, 124, 80, 82, 69, 77, 73, 85, 77,
        45, 49, 57, 49, 50, 45, 67, 53, 57, 55, 45, 56, 56, 55, 68, 124, 80, 82, 69, 77, 73, 85, 77, 45, 70, 67, 53, 68, 45, 55, 54, 53, 52, 45, 68, 69, 66, 53, 124, 80, 82, 69, 77, 73, 85, 77, 45, 52, 49, 57,
        55, 45, 69, 52, 67, 67, 45, 49, 69, 48, 69, 124, 80, 82, 69, 77, 73, 85, 77, 45, 65, 49, 50, 67, 45, 50, 48, 65, 55, 45, 56, 52, 67, 67, 124, 80, 82, 69, 77, 73, 85, 77, 45, 70, 53, 68, 53, 45, 66, 67,
        53, 50, 45, 56, 53, 48, 56, 124, 80, 82, 69, 77, 73, 85, 77, 45, 56, 69, 55, 70, 45, 69, 53, 54, 52, 45, 50, 53, 69, 70, 124, 80, 82, 69, 77, 73, 85, 77, 45, 53, 70, 66, 57, 45, 69, 51, 57, 68, 45, 68,
        52, 56, 70, 124, 80, 82, 69, 77, 73, 85, 77, 45, 53, 68, 66, 55, 45, 51, 65, 53, 51, 45, 56, 57, 70, 49, 124, 80, 82, 69, 77, 73, 85, 77, 45, 70, 56, 66, 48, 45, 49, 67, 50, 66, 45, 49, 53, 69, 65
    }
    local _0x3D = ""
    for _0x4E = 1, #_0x2C do
        _0x3D = _0x3D .. _0x1B(_0x2C[_0x4E])
    end
    local _0x5F = {}
    for _0x6G in string.gmatch(_0x3D, "[^|]+") do
        table.insert(_0x5F, _0x6G)
    end
    return _0x5F
end)()
local validCodes = _0x8F2A

-- ==========================================
-- SISTEM SIMPAN PERMANEN (1 ORANG 1 KODE)
-- ==========================================
local SaveFile = "LipzyHub_Premium_" .. LocalPlayer.UserId .. ".txt"
local isPremium = false
local isAdmin = false

if pcall(function() return readfile(SaveFile) end) then
    if readfile(SaveFile) == "PREMIUM" then
        isPremium = true
        isAdmin = true
    end
end

local userRole = AdminList[LocalPlayer.Name]
if userRole ~= nil then
    isAdmin = true
    isPremium = true
    pcall(function() writefile(SaveFile, "PREMIUM") end)
end

if game.CoreGui:FindFirstChild("StealAnEggGUI") then
    game.CoreGui.StealAnEggGUI:Destroy()
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "StealAnEggGUI"
ScreenGui.Parent = game.CoreGui
ScreenGui.ResetOnSpawn = false

local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Size = UDim2.new(0, 500, 0, 400)
MainFrame.Position = UDim2.new(0.5, -250, 0.5, -200)
MainFrame.BackgroundColor3 = Color3.fromRGB(18, 12, 28)
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Parent = ScreenGui

local MainCorner = Instance.new("UICorner")
MainCorner.CornerRadius = UDim.new(0, 10)
MainCorner.Parent = MainFrame

local MainStroke = Instance.new("UIStroke")
MainStroke.Color = Color3.fromRGB(140, 45, 220)
MainStroke.Thickness = 2
MainStroke.Parent = MainFrame

local Header = Instance.new("Frame")
Header.Size = UDim2.new(1, 0, 0, 40)
Header.BackgroundColor3 = Color3.fromRGB(30, 18, 48)
Header.BorderSizePixel = 0
Header.Parent = MainFrame

local HeaderCorner = Instance.new("UICorner")
HeaderCorner.CornerRadius = UDim.new(0, 10)
HeaderCorner.Parent = Header

local TitleText = Instance.new("TextLabel")
TitleText.Size = UDim2.new(1, -50, 1, 0)
TitleText.Position = UDim2.new(0, 15, 0, 0)
TitleText.BackgroundTransparency = 1
TitleText.Text = "LIPZY HUB V5.2"
TitleText.TextColor3 = Color3.fromRGB(200, 120, 255)
TitleText.TextSize = 18
TitleText.Font = Enum.Font.GothamBold
TitleText.TextXAlignment = Enum.TextXAlignment.Left
TitleText.Parent = Header

local CloseBtn = Instance.new("TextButton")
CloseBtn.Size = UDim2.new(0, 30, 0, 30)
CloseBtn.Position = UDim2.new(1, -35, 0, 5)
CloseBtn.BackgroundColor3 = Color3.fromRGB(180, 40, 60)
CloseBtn.Text = "X"
CloseBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseBtn.Font = Enum.Font.GothamBold
CloseBtn.TextSize = 14
CloseBtn.Parent = Header

local CloseCorner = Instance.new("UICorner")
CloseCorner.CornerRadius = UDim.new(0, 6)
CloseCorner.Parent = CloseBtn

CloseBtn.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

local Sidebar = Instance.new("Frame")
Sidebar.Size = UDim2.new(0, 130, 1, -50)
Sidebar.Position = UDim2.new(0, 10, 0, 45)
Sidebar.BackgroundColor3 = Color3.fromRGB(25, 15, 38)
Sidebar.BorderSizePixel = 0
Sidebar.Parent = MainFrame

local SidebarCorner = Instance.new("UICorner")
SidebarCorner.CornerRadius = UDim.new(0, 8)
SidebarCorner.Parent = Sidebar

local SidebarLayout = Instance.new("UIListLayout")
SidebarLayout.SortOrder = Enum.SortOrder.LayoutOrder
SidebarLayout.Padding = UDim.new(0, 6)
SidebarLayout.Parent = Sidebar

local SidebarPadding = Instance.new("UIPadding")
SidebarPadding.PaddingTop = UDim.new(0, 10)
SidebarPadding.PaddingLeft = UDim.new(0, 8)
SidebarPadding.PaddingRight = UDim.new(0, 8)
SidebarPadding.Parent = Sidebar

local ContentContainer = Instance.new("Frame")
ContentContainer.Size = UDim2.new(1, -160, 1, -55)
ContentContainer.Position = UDim2.new(0, 150, 0, 45)
ContentContainer.BackgroundTransparency = 1
ContentContainer.Parent = MainFrame

local Pages = {}

local function CreateTab(name, layoutOrder)
    local TabBtn = Instance.new("TextButton")
    TabBtn.Size = UDim2.new(1, 0, 0, 30)
    TabBtn.BackgroundColor3 = (layoutOrder == 1) and Color3.fromRGB(120, 40, 190) or Color3.fromRGB(40, 25, 60)
    TabBtn.Text = name
    TabBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    TabBtn.Font = Enum.Font.GothamBold
    TabBtn.TextSize = 11
    TabBtn.LayoutOrder = layoutOrder
    TabBtn.Parent = Sidebar

    local BtnCorner = Instance.new("UICorner")
    BtnCorner.CornerRadius = UDim.new(0, 6)
    BtnCorner.Parent = TabBtn

    local Page = Instance.new("Frame")
    Page.Size = UDim2.new(1, 0, 1, 0)
    Page.BackgroundTransparency = 1
    Page.Visible = (layoutOrder == 1)
    Page.Parent = ContentContainer

    Pages[name] = {Button = TabBtn, Page = Page}

    TabBtn.MouseButton1Click:Connect(function()
        for _, tabData in pairs(Pages) do
            tabData.Page.Visible = false
            tabData.Button.BackgroundColor3 = Color3.fromRGB(40, 25, 60)
        end
        Page.Visible = true
        TabBtn.BackgroundColor3 = Color3.fromRGB(120, 40, 190)
    end)

    return Page
end

local PlayerPage = CreateTab("PEMAIN", 1)
local MainPage = CreateTab("UTAMA", 2)
local DisplayPage = CreateTab("TAMPILKAN", 3)
local ShopPage = CreateTab("TOKO", 4)
local PredictionPage = CreateTab("PREDIKSI", 5)
local AdminAbusePage = CreateTab("PENYALAHGUNAAN ADMIN", 6)
local DivineSpawnedPage = CreateTab("DIVINE SPAWNED", 7)

local StatusLabelRef = nil
local AdminPageInstance = nil

local function PopulateAdminPage(page)
    for _, child in ipairs(page:GetChildren()) do
        child:Destroy()
    end

    local MessageFrame = Instance.new("Frame")
    MessageFrame.Size = UDim2.new(1, -20, 0, 100)
    MessageFrame.Position = UDim2.new(0, 10, 0, 40)
    MessageFrame.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
    MessageFrame.BorderSizePixel = 0
    MessageFrame.Parent = page

    local MessageCorner = Instance.new("UICorner")
    MessageCorner.CornerRadius = UDim.new(0, 8)
    MessageCorner.Parent = MessageFrame

    local MessageBox = Instance.new("TextBox")
    MessageBox.Size = UDim2.new(1, -20, 0, 40)
    MessageBox.Position = UDim2.new(0, 10, 0, 10)
    MessageBox.BackgroundColor3 = Color3.fromRGB(25, 15, 38)
    MessageBox.Text = "PESAN.."
    MessageBox.TextColor3 = Color3.fromRGB(200, 200, 220)
    MessageBox.Font = Enum.Font.Gotham
    MessageBox.TextSize = 14
    MessageBox.ClearTextOnFocus = true
    MessageBox.Parent = MessageFrame

    local MessageCorner2 = Instance.new("UICorner")
    MessageCorner2.CornerRadius = UDim.new(0, 6)
    MessageCorner2.Parent = MessageBox

    local SendAdminBtn = Instance.new("TextButton")
    SendAdminBtn.Size = UDim2.new(1, -20, 0, 35)
    SendAdminBtn.Position = UDim2.new(0, 10, 1, -45)
    SendAdminBtn.BackgroundColor3 = Color3.fromRGB(120, 40, 190)
    SendAdminBtn.Text = "KIRIM"
    SendAdminBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    SendAdminBtn.Font = Enum.Font.GothamBold
    SendAdminBtn.TextSize = 14
    SendAdminBtn.Parent = MessageFrame

    local SendCorner = Instance.new("UICorner")
    SendCorner.CornerRadius = UDim.new(0, 6)
    SendCorner.Parent = SendAdminBtn

    SendAdminBtn.MouseButton1Click:Connect(function()
        local message = MessageBox.Text
        if message == "" or message == "PESAN.." then return end

        local NotifGui = Instance.new("ScreenGui")
        NotifGui.Name = "LipzyNotification"
        NotifGui.Parent = game.CoreGui
        NotifGui.IgnoreGuiInset = true

        local NotifFrame = Instance.new("Frame")
        NotifFrame.Size = UDim2.new(0, 500, 0, 100)
        NotifFrame.Position = UDim2.new(0.5, -250, 0, -150)
        NotifFrame.BackgroundColor3 = Color3.fromRGB(30, 18, 48)
        NotifFrame.BorderSizePixel = 0
        NotifFrame.Parent = NotifGui

        local NotifCorner = Instance.new("UICorner")
        NotifCorner.CornerRadius = UDim.new(0, 10)
        NotifCorner.Parent = NotifFrame

        local NotifStroke = Instance.new("UIStroke")
        NotifStroke.Color = Color3.fromRGB(140, 45, 220)
        NotifStroke.Thickness = 2
        NotifStroke.Parent = NotifFrame

        local NotifProfile = Instance.new("ImageLabel")
        NotifProfile.Size = UDim2.new(0, 60, 0, 60)
        NotifProfile.Position = UDim2.new(0, 20, 0.5, -30)
        NotifProfile.BackgroundColor3 = Color3.fromRGB(45, 25, 70)
        NotifProfile.Image = Players:GetUserThumbnailAsync(LocalPlayer.UserId, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size150x150)
        NotifProfile.Parent = NotifFrame

        local NotifProfileCorner = Instance.new("UICorner")
        NotifProfileCorner.CornerRadius = UDim.new(1, 0)
        NotifProfileCorner.Parent = NotifProfile

        local NotifProfileStroke = Instance.new("UIStroke")
        NotifProfileStroke.Color = Color3.fromRGB(255, 215, 0)
        NotifProfileStroke.Thickness = 2
        NotifProfileStroke.Parent = NotifProfile

        local CrownLabel = Instance.new("TextLabel")
        CrownLabel.Size = UDim2.new(1, -100, 0, 20)
        CrownLabel.Position = UDim2.new(0, 90, 0, 0)
        CrownLabel.BackgroundTransparency = 1
        CrownLabel.Text = "👑LIPZY HUB👑"
        CrownLabel.TextColor3 = Color3.fromRGB(255, 215, 0)
        CrownLabel.Font = Enum.Font.GothamBold
        CrownLabel.TextSize = 14
        CrownLabel.TextXAlignment = Enum.TextXAlignment.Left
        CrownLabel.Parent = NotifFrame

        local NotifMsg = Instance.new("TextLabel")
        NotifMsg.Size = UDim2.new(1, -100, 1, -25)
        NotifMsg.Position = UDim2.new(0, 90, 0, 20)
        NotifMsg.BackgroundTransparency = 1
        NotifMsg.Text = message
        NotifMsg.TextColor3 = Color3.fromRGB(255, 255, 255)
        NotifMsg.Font = Enum.Font.Gotham
        NotifMsg.TextSize = 16
        NotifMsg.TextXAlignment = Enum.TextXAlignment.Left
        NotifMsg.TextYAlignment = Enum.TextYAlignment.Top
        NotifMsg.Parent = NotifFrame

        TweenService:Create(NotifFrame, TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {Position = UDim2.new(0.5, -250, 0, 50)}):Play()

        task.delay(3, function()
            TweenService:Create(NotifFrame, TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.In), {Position = UDim2.new(0.5, -250, 0, -150)}):Play()
            task.wait(0.5)
            NotifGui:Destroy()
        end)
    end)

    local OwnerScriptYPos = 150
    local OwnerScriptFrame = Instance.new("Frame")
    OwnerScriptFrame.Size = UDim2.new(1, -20, 0, 40)
    OwnerScriptFrame.Position = UDim2.new(0, 10, 0, OwnerScriptYPos)
    OwnerScriptFrame.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
    OwnerScriptFrame.BorderSizePixel = 0
    OwnerScriptFrame.Parent = page

    local OwnerScriptCorner = Instance.new("UICorner")
    OwnerScriptCorner.CornerRadius = UDim.new(0, 8)
    OwnerScriptCorner.Parent = OwnerScriptFrame

    local OwnerTextLabel = Instance.new("TextLabel")
    OwnerTextLabel.Size = UDim2.new(0, 150, 1, 0)
    OwnerTextLabel.Position = UDim2.new(0, 10, 0, 0)
    OwnerTextLabel.BackgroundTransparency = 1
    OwnerTextLabel.Text = "SKRIPT PEMILIK"
    OwnerTextLabel.TextColor3 = Color3.fromRGB(200, 200, 220)
    OwnerTextLabel.Font = Enum.Font.GothamBold
    OwnerTextLabel.TextSize = 14
    OwnerTextLabel.TextXAlignment = Enum.TextXAlignment.Left
    OwnerTextLabel.Parent = OwnerScriptFrame

    local ToggleBg = Instance.new("Frame")
    ToggleBg.Size = UDim2.new(0, 50, 0, 26)
    ToggleBg.Position = UDim2.new(1, -60, 0.5, -13)
    ToggleBg.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    ToggleBg.Parent = OwnerScriptFrame

    local ToggleCorner = Instance.new("UICorner")
    ToggleCorner.CornerRadius = UDim.new(1, 0)
    ToggleCorner.Parent = ToggleBg

    local ToggleCircle = Instance.new("Frame")
    ToggleCircle.Size = UDim2.new(0, 20, 0, 20)
    ToggleCircle.Position = UDim2.new(0, 3, 0.5, -10)
    ToggleCircle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    ToggleCircle.Parent = ToggleBg

    local ToggleCircleCorner = Instance.new("UICorner")
    ToggleCircleCorner.CornerRadius = UDim.new(1, 0)
    ToggleCircleCorner.Parent = ToggleCircle

    local isOwnerScriptEnabled = false
    local headBillboard = nil
    local rainbowConnection = nil

    local function ApplyBillboard(character)
        if headBillboard then headBillboard:Destroy() end
        if rainbowConnection then rainbowConnection:Disconnect() end
        if not character or not character:FindFirstChild("Head") then return end

        headBillboard = Instance.new("BillboardGui")
        headBillboard.Name = "OwnerScriptBillboard"
        headBillboard.Adornee = character.Head
        headBillboard.Size = UDim2.new(0, 220, 0, 50)
        headBillboard.StudsOffset = Vector3.new(0, 2.5, 0)
        headBillboard.AlwaysOnTop = true
        headBillboard.Parent = character.Head

        local ownerText = Instance.new("TextLabel")
        ownerText.Name = "OwnerText"
        ownerText.Size = UDim2.new(1, 0, 1, 0)
        ownerText.BackgroundTransparency = 1
        ownerText.Font = Enum.Font.GothamBold
        ownerText.TextSize = 24
        ownerText.Parent = headBillboard

        local textStroke = Instance.new("UIStroke")
        textStroke.Color = Color3.fromRGB(0, 0, 0)
        textStroke.Thickness = 3
        textStroke.Parent = ownerText

        if LocalPlayer.Name == "Yanzzz_1023" then
            ownerText.Text = "👑PEMILIK👑"
            ownerText.TextColor3 = Color3.fromRGB(255, 220, 0)
        elseif LocalPlayer.Name == "LifzxAfter2" then
            ownerText.Text = "👑ADMIN👑"
            rainbowConnection = RunService.RenderStepped:Connect(function()
                local hue = (tick() % 5) / 5
                ownerText.TextColor3 = Color3.fromHSV(hue, 1, 1)
            end)
        else
            ownerText.Text = "👑PREMIUM👑"
            ownerText.TextColor3 = Color3.fromRGB(200, 100, 255)
        end
    end

    local OwnerScriptBtn = Instance.new("TextButton")
    OwnerScriptBtn.Size = UDim2.new(1, 0, 1, 0)
    OwnerScriptBtn.BackgroundTransparency = 1
    OwnerScriptBtn.Text = ""
    OwnerScriptBtn.Parent = OwnerScriptFrame

    OwnerScriptBtn.MouseButton1Click:Connect(function()
        isOwnerScriptEnabled = not isOwnerScriptEnabled
        if isOwnerScriptEnabled then
            TweenService:Create(ToggleCircle, TweenInfo.new(0.2), {Position = UDim2.new(1, -23, 0.5, -10), BackgroundColor3 = Color3.fromRGB(0, 255, 0)}):Play()
            TweenService:Create(ToggleBg, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(40, 120, 40)}):Play()
            if LocalPlayer.Character then
                ApplyBillboard(LocalPlayer.Character)
            end
        else
            TweenService:Create(ToggleCircle, TweenInfo.new(0.2), {Position = UDim2.new(0, 3, 0.5, -10), BackgroundColor3 = Color3.fromRGB(255, 255, 255)}):Play()
            TweenService:Create(ToggleBg, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(60, 60, 60)}):Play()
            if headBillboard then
                headBillboard:Destroy()
                headBillboard = nil
            end
            if rainbowConnection then
                rainbowConnection:Disconnect()
                rainbowConnection = nil
            end
        end
    end)

    LocalPlayer.CharacterAdded:Connect(function(char)
        if isOwnerScriptEnabled then
            char:WaitForChild("Head")
            ApplyBillboard(char)
        end
    end)
end

if isAdmin then
    AdminPageInstance = CreateTab("ADMIN", 8)
    PopulateAdminPage(AdminPageInstance)
end

local function updatePlayerStatusToPremium()
    if StatusLabelRef then
        StatusLabelRef.Text = "PREMIUM"
        StatusLabelRef.TextColor3 = Color3.fromRGB(255, 215, 0)
    end
    
    if not AdminPageInstance then
        AdminPageInstance = CreateTab("ADMIN", 8)
        PopulateAdminPage(AdminPageInstance)
    end
end

-- ==========================================
-- TOKO KONTEN HALAMAN
-- ==========================================
local ShopScroll = Instance.new("ScrollingFrame")
ShopScroll.Size = UDim2.new(1, -10, 1, -10)
ShopScroll.Position = UDim2.new(0, 5, 0, 5)
ShopScroll.BackgroundTransparency = 1
ShopScroll.BorderSizePixel = 0
ShopScroll.ScrollBarThickness = 4
ShopScroll.ScrollBarImageColor3 = Color3.fromRGB(140, 45, 220)
ShopScroll.Parent = ShopPage

local ShopLayout = Instance.new("UIListLayout")
ShopLayout.SortOrder = Enum.SortOrder.LayoutOrder
ShopLayout.Padding = UDim.new(0, 12)
ShopLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
ShopLayout.Parent = ShopScroll

ShopLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    ShopScroll.CanvasSize = UDim2.new(0, 0, 0, ShopLayout.AbsoluteContentSize.Y + 20)
end)

local ShopTitle = Instance.new("TextLabel")
ShopTitle.Size = UDim2.new(1, -20, 0, 35)
ShopTitle.BackgroundTransparency = 1
ShopTitle.Text = "--TOKO ADMIN--"
ShopTitle.Font = Enum.Font.GothamBold
ShopTitle.TextSize = 20
ShopTitle.LayoutOrder = 1
ShopTitle.Parent = ShopScroll

local ShopTitleStroke = Instance.new("UIStroke")
ShopTitleStroke.Color = Color3.fromRGB(0, 0, 0)
ShopTitleStroke.Thickness = 3
ShopTitleStroke.Parent = ShopTitle

RunService.RenderStepped:Connect(function()
    if ShopTitle and ShopTitle.Parent then
        local hue = (tick() % 3) / 3
        ShopTitle.TextColor3 = Color3.fromHSV(hue, 1, 1)
    end
end)

local ShopBanner = Instance.new("ImageLabel")
ShopBanner.Size = UDim2.new(1, -20, 0, 150)
ShopBanner.BackgroundTransparency = 1
ShopBanner.Image = "rbxassetid://124576574290051"
ShopBanner.ScaleType = Enum.ScaleType.Fit
ShopBanner.LayoutOrder = 2
ShopBanner.Parent = ShopScroll

local ShopBannerCorner = Instance.new("UICorner")
ShopBannerCorner.CornerRadius = UDim.new(0, 8)
ShopBannerCorner.Parent = ShopBanner

local RedeemFrame = Instance.new("Frame")
RedeemFrame.Size = UDim2.new(1, -20, 0, 100)
RedeemFrame.BackgroundColor3 = Color3.fromRGB(25, 15, 38)
RedeemFrame.BorderSizePixel = 0
RedeemFrame.LayoutOrder = 3
RedeemFrame.Parent = ShopScroll

local RedeemCorner = Instance.new("UICorner")
RedeemCorner.CornerRadius = UDim.new(0, 8)
RedeemCorner.Parent = RedeemFrame

local RedeemTitle = Instance.new("TextLabel")
RedeemTitle.Size = UDim2.new(1, 0, 0, 25)
RedeemTitle.Position = UDim2.new(0, 0, 0, 5)
RedeemTitle.BackgroundTransparency = 1
RedeemTitle.Text = "KODE PENUKARAN"
RedeemTitle.TextColor3 = Color3.fromRGB(255, 215, 0)
RedeemTitle.Font = Enum.Font.GothamBold
RedeemTitle.TextSize = 14
RedeemTitle.Parent = RedeemFrame

local CodeInput = Instance.new("TextBox")
CodeInput.Size = UDim2.new(0.7, -10, 0, 30)
CodeInput.Position = UDim2.new(0, 10, 0, 35)
CodeInput.BackgroundColor3 = Color3.fromRGB(18, 12, 28)
CodeInput.Text = ""
CodeInput.PlaceholderText = "Masukkan Kode Disini..."
CodeInput.TextColor3 = Color3.fromRGB(255, 255, 255)
CodeInput.Font = Enum.Font.Gotham
CodeInput.TextSize = 12
CodeInput.ClearTextOnFocus = false
CodeInput.Parent = RedeemFrame

local CodeInputCorner = Instance.new("UICorner")
CodeInputCorner.CornerRadius = UDim.new(0, 6)
CodeInputCorner.Parent = CodeInput

local SendBtn = Instance.new("TextButton")
SendBtn.Size = UDim2.new(0.3, -10, 0, 30)
SendBtn.Position = UDim2.new(0.7, 0, 0, 35)
SendBtn.BackgroundColor3 = Color3.fromRGB(140, 45, 220)
SendBtn.Text = "KIRIM"
SendBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
SendBtn.Font = Enum.Font.GothamBold
SendBtn.TextSize = 14
SendBtn.Parent = RedeemFrame

local SendBtnCorner = Instance.new("UICorner")
SendBtnCorner.CornerRadius = UDim.new(0, 6)
SendBtnCorner.Parent = SendBtn

local ResultLabel = Instance.new("TextLabel")
ResultLabel.Size = UDim2.new(1, -20, 0, 20)
ResultLabel.Position = UDim2.new(0, 10, 0, 70)
ResultLabel.BackgroundTransparency = 1
ResultLabel.Text = ""
ResultLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
ResultLabel.Font = Enum.Font.Gotham
ResultLabel.TextSize = 11
ResultLabel.TextXAlignment = Enum.TextXAlignment.Left
ResultLabel.Parent = RedeemFrame

SendBtn.MouseButton1Click:Connect(function()
    if isPremium then
        ResultLabel.Text = "Anda sudah PREMIUM!"
        ResultLabel.TextColor3 = Color3.fromRGB(255, 100, 100)
        return
    end
    
    local code = string.upper(CodeInput.Text)
    local isValid = false
    
    for _, c in ipairs(validCodes) do
        if c == code then
            isValid = true
            break
        end
    end
    
    if isValid then
        isPremium = true
        isAdmin = true
        pcall(function() writefile(SaveFile, "PREMIUM") end)
        
        ResultLabel.Text = "BERHASIL! Akun kini PREMIUM."
        ResultLabel.TextColor3 = Color3.fromRGB(100, 255, 100)
        CodeInput.Text = ""
        
        updatePlayerStatusToPremium()
    else
        ResultLabel.Text = "Kode Tidak Valid!"
        ResultLabel.TextColor3 = Color3.fromRGB(255, 100, 100)
    end
end)

local function AddInfoLabel(container, title, val, order)
    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, 0, 0, 25)
    label.BackgroundTransparency = 1
    label.Text = title .. ": " .. val
    label.TextColor3 = Color3.fromRGB(200, 200, 220)
    label.Font = Enum.Font.Gotham
    label.TextSize = 11
    label.TextXAlignment = Enum.TextXAlignment.Left
    label.LayoutOrder = order
    label.Parent = container
    return label
end

local ProfileImage = Instance.new("ImageLabel")
ProfileImage.Size = UDim2.new(0, 70, 0, 70)
ProfileImage.Position = UDim2.new(0.5, -35, 0, 0)
ProfileImage.BackgroundColor3 = Color3.fromRGB(45, 25, 70)
ProfileImage.Image = Players:GetUserThumbnailAsync(LocalPlayer.UserId, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size150x150)
ProfileImage.Parent = PlayerPage

local ProfileCorner = Instance.new("UICorner")
ProfileCorner.CornerRadius = UDim.new(1, 0)
ProfileCorner.Parent = ProfileImage

local ProfileStroke = Instance.new("UIStroke")
ProfileStroke.Color = Color3.fromRGB(160, 60, 255)
ProfileStroke.Thickness = 2
ProfileStroke.Parent = ProfileImage

local UserBox = Instance.new("Frame")
UserBox.Size = UDim2.new(1, -20, 0, 28)
UserBox.Position = UDim2.new(0, 10, 0, 78)
UserBox.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
UserBox.BorderSizePixel = 0
UserBox.Parent = PlayerPage

local UserBoxCorner = Instance.new("UICorner")
UserBoxCorner.CornerRadius = UDim.new(0, 6)
UserBoxCorner.Parent = UserBox

local UserBoxStroke = Instance.new("UIStroke")
UserBoxStroke.Color = Color3.fromRGB(100, 40, 160)
UserBoxStroke.Thickness = 1
UserBoxStroke.Parent = UserBox

local UserLabel = Instance.new("TextLabel")
UserLabel.Size = UDim2.new(1, 0, 1, 0)
UserLabel.BackgroundTransparency = 1
UserLabel.Text = "@" .. LocalPlayer.Name .. " (" .. LocalPlayer.DisplayName .. ")"
UserLabel.TextColor3 = Color3.fromRGB(220, 180, 255)
UserLabel.Font = Enum.Font.GothamBold
UserLabel.TextSize = 11
UserLabel.Parent = UserBox

local PlayerInfoContainer = Instance.new("Frame")
PlayerInfoContainer.Size = UDim2.new(1, -20, 0, 120)
PlayerInfoContainer.Position = UDim2.new(0, 10, 0, 112)
PlayerInfoContainer.BackgroundColor3 = Color3.fromRGB(28, 16, 42)
PlayerInfoContainer.BorderSizePixel = 0
PlayerInfoContainer.Parent = PlayerPage

local PlayerInfoCorner = Instance.new("UICorner")
PlayerInfoCorner.CornerRadius = UDim.new(0, 8)
PlayerInfoCorner.Parent = PlayerInfoContainer

local PlayerInfoLayout = Instance.new("UIListLayout")
PlayerInfoLayout.SortOrder = Enum.SortOrder.LayoutOrder
PlayerInfoLayout.Padding = UDim.new(0, 2)
PlayerInfoLayout.Parent = PlayerInfoContainer

local PlayerInfoPadding = Instance.new("UIPadding")
PlayerInfoPadding.PaddingTop = UDim.new(0, 6)
PlayerInfoPadding.PaddingLeft = UDim.new(0, 10)
PlayerInfoPadding.PaddingRight = UDim.new(0, 10)
PlayerInfoPadding.Parent = PlayerInfoContainer

AddInfoLabel(PlayerInfoContainer, "Usia Akun", LocalPlayer.AccountAge .. " Hari", 1)
local AccountCreatedDate = os.date("%d %B %Y", os.time() - (LocalPlayer.AccountAge * 86400))
AddInfoLabel(PlayerInfoContainer, "Akun Dibuat", AccountCreatedDate, 2)
local TimeLabel = AddInfoLabel(PlayerInfoContainer, "Time", os.date("%H:%M:%S WIB"), 3)

task.spawn(function()
    while task.wait(1) do
        if TimeLabel and TimeLabel.Parent then
            TimeLabel.Text = "Waktu: " + os.date("%H:%M:%S WIB")
        end
    end
end)

local GameName = "Mencuri Telur"
pcall(function()
    local placeInfo = MarketplaceService:GetProductInfo(game.PlaceId)
    if placeInfo and placeInfo.Name then
        GameName = placeInfo.Name
    end
end)
AddInfoLabel(PlayerInfoContainer, "Nama Game", GameName, 4)

local StatsContainer = Instance.new("Frame")
StatsContainer.Size = UDim2.new(1, -20, 0, 105)
StatsContainer.Position = UDim2.new(0, 10, 0, 238)
StatsContainer.BackgroundTransparency = 1
StatsContainer.Parent = PlayerPage

local StatsLayout = Instance.new("UIListLayout")
StatsLayout.SortOrder = Enum.SortOrder.LayoutOrder
StatsLayout.Padding = UDim.new(0, 5)
StatsLayout.Parent = StatsContainer

local function CreateStatBox(order, hasIcon)
    local Box = Instance.new("Frame")
    Box.Size = UDim2.new(1, 0, 0, 30)
    Box.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
    Box.BorderSizePixel = 0
    Box.LayoutOrder = order
    Box.Parent = StatsContainer

    local BoxCorner = Instance.new("UICorner")
    BoxCorner.CornerRadius = UDim.new(0, 6)
    BoxCorner.Parent = Box

    local BoxStroke = Instance.new("UIStroke")
    BoxStroke.Color = Color3.fromRGB(100, 40, 160)
    BoxStroke.Thickness = 1
    BoxStroke.Parent = Box

    local Icon = nil
    if hasIcon then
        Icon = Instance.new("ImageLabel")
        Icon.Size = UDim2.new(0, 18, 0, 18)
        Icon.Position = UDim2.new(0, 8, 0.5, -9)
        Icon.BackgroundTransparency = 1
        Icon.ScaleType = Enum.ScaleType.Fit
        Icon.Parent = Box
    end

    local Label = Instance.new("TextLabel")
    Label.Size = hasIcon and UDim2.new(1, -38, 1, 0) or UDim2.new(1, -20, 1, 0)
    Label.Position = hasIcon and UDim2.new(0, 32, 0, 0) or UDim2.new(0, 10, 0, 0)
    Label.BackgroundTransparency = 1
    Label.TextColor3 = Color3.fromRGB(220, 200, 255)
    Label.Font = Enum.Font.GothamBold
    Label.TextSize = 11
    Label.TextXAlignment = Enum.TextXAlignment.Left
    Label.Parent = Box

    return Label, Icon
end

local StatusLabel, StatusIcon = CreateStatBox(1, true)
StatusLabelRef = StatusLabel
StatusIcon.Image = "rbxassetid://95842412229310"

if isPremium then
    StatusLabel.Text = "PREMIUM"
    StatusLabel.TextColor3 = Color3.fromRGB(255, 215, 0)
else
    StatusLabel.Text = "GRATIS"
    StatusLabel.TextColor3 = Color3.fromRGB(150, 255, 150)
end

local FPSLabel, FPSIcon = CreateStatBox(2, true)
FPSIcon.Image = "rbxassetid://137800308683217"
local PingLabel, PingIcon = CreateStatBox(3, true)
PingIcon.Image = "rbxassetid://78681903515425"

local frameCount = 0
local lastTime = tick()
local currentFPS = 0

RunService.RenderStepped:Connect(function()
    frameCount = frameCount + 1
    local currentTime = tick()
    if currentTime - lastTime >= 1 then
        currentFPS = frameCount
        frameCount = 0
        lastTime = currentTime
    end
end)

task.spawn(function()
    while task.wait(0.2) do
        if FPSLabel and FPSLabel.Parent then
            FPSLabel.Text = "FPS: " .. currentFPS
        end
        if PingLabel and PingLabel.Parent then
            local rawPing = Stats.Network.ServerStatsItem["Data Ping"]:GetValue()
            local pingVal = math.floor(rawPing)
            PingLabel.Text = pingVal .. " ms"
        end
    end
end)

local ScriptList = {
    {Name = "CHILI HUB V2", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/tienkhanh1/spicy/main/Chilli.lua"))()]]},
    {Name = "THANHDUY HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/ThanhDuyHub/Game/refs/heads/main/Steal-An-Egg.lua"))()]]},
    {Name = "PULSE HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/PulseZax/Loader/refs/heads/main/.lua"))()]]},
    {Name = "SENA BETA", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://senahub.xyz/raw/loader"))()]]},
    {Name = "LENON HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/lennonxscripts/lennonhubv4/refs/heads/main/stealanegg",true))()]]},
    {Name = "DHII HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/dhiisepertiorang/dhii_kick.lua/refs/heads/main/dhiitoaa.lua"))()]]},
    {Name = "BlyxoHUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://flowauth.net/v1/loaders/69d3463240384f3a73fbe32c178093a2.lua"))()]]},
    {Name = "FINDER PRIVATE SERVER", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/GlazeScripts/Private-Server-Finder/refs/heads/main/Glazehub.lua"))()]]},
    {Name = "MIRANDA HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/miirandahub/loader/refs/heads/main/mirandaafk.lua"))()]]},
    {Name = "HOSHI HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://hoshihub.site/loader.lua"))()]]},
    {Name = "OXIDE HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/xulfo/Oxide-Loader/main/Main.lua"))()]]},
    {Name = "NEVA HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/VEZ2/NEVAHUB/main/2"))()]]},
    {Name = "BK's HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://api.luarmor.net/files/v4/loaders/9ee4edde227ac85f50872bf9e4226508.lua"))()]]},
    {Name = "VINCITORE HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/tutorkah104-rgb/Steal-an-Egg/refs/heads/main/Vincitore.luau"))()]]},
    {Name = "LKZ HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/LucasggkX/LKZ-Hub/refs/heads/main/Loader.lua"))()]]},
    {Name = "SKIBIDI HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/caomod2077/Script/refs/heads/main/Fn-stealanegg.lua"))()]]},
    {Name = "BP HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://rscripts.net/raw/open-src-premium-or-bphub_1790968708765_mTTlSoUSyY.txt"))()]]},
    {Name = "FOXNAME", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/caomod2077/Script/refs/heads/main/Fn-stealanegg.lua"))()]]},
    {Name = "ZEROIN HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://zeroinhub.com/api/script"))()]]},
    {Name = "FAKE ADMIN", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/Dayvinksthik/Script/main/Games/JoshBNS-Crack.lua"))()]]},
    {Name = "POLLUTED HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/PollutedHub/Sae/refs/heads/main/SaePolluted"))()]]},
    {Name = "SENA V6", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://senahub.xyz/senav6"))()]]},
    {Name = "AJJANS HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://api.luarmor.net/files/v4/loaders/359e97f8618e9008afe5f496184ebb7c.lua"))()]]},
    {Name = "FYY COMMUNITY", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://FyyCommunity.my.id"))()]]},
    {Name = "LIMBO HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://limbohub.my.id/loader.lua"))()]]},
    {Name = "UNKNOWN HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://unknownhub.win/api/projects/54474b4c5d5a4f459909c4cb70e7b4f3/loader"))()]]},
    {Name = "CLOVER HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://cloverhub.app/clover.lua"))()]]},
    {Name = "BIGFROOT", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/hanniii1/Loader/refs/heads/main/BFLoader.lua"))()]]},
    {Name = "SYS HUB", KeyStatus = "KEYLESS", Script = [[loadstring(game:HttpGet("https://syshub.fun/free"))()]]}
}

local OpenScriptBtn = Instance.new("TextButton")
OpenScriptBtn.Size = UDim2.new(1, -20, 0, 36)
OpenScriptBtn.Position = UDim2.new(0, 10, 0, 5)
OpenScriptBtn.BackgroundColor3 = Color3.fromRGB(140, 45, 220)
OpenScriptBtn.Text = "BUKA SCRIPT"
OpenScriptBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
OpenScriptBtn.Font = Enum.Font.GothamBold
OpenScriptBtn.TextSize = 14
OpenScriptBtn.Parent = MainPage

local OpenScriptCorner = Instance.new("UICorner")
OpenScriptCorner.CornerRadius = UDim.new(0, 8)
OpenScriptCorner.Parent = OpenScriptBtn

local ScriptScroll = Instance.new("ScrollingFrame")
ScriptScroll.Size = UDim2.new(1, -20, 1, -50)
ScriptScroll.Position = UDim2.new(0, 10, 0, 46)
ScriptScroll.BackgroundTransparency = 1
ScriptScroll.BorderSizePixel = 0
ScriptScroll.ScrollBarThickness = 4
ScriptScroll.ScrollBarImageColor3 = Color3.fromRGB(140, 45, 220)
ScriptScroll.Parent = MainPage

local ScriptListLayout = Instance.new("UIListLayout")
ScriptListLayout.SortOrder = Enum.SortOrder.LayoutOrder
ScriptListLayout.Padding = UDim.new(0, 6)
ScriptListLayout.Parent = ScriptScroll

local selectedScript = nil
local RegisteredItems = {}

for index, data in ipairs(ScriptList) do
    local ItemFrame = Instance.new("Frame")
    ItemFrame.Size = UDim2.new(1, -10, 0, 40)
    ItemFrame.BackgroundColor3 = Color3.fromRGB(32, 18, 50)
    ItemFrame.BorderSizePixel = 0
    ItemFrame.LayoutOrder = index
    ItemFrame.Parent = ScriptScroll

    local ItemCorner = Instance.new("UICorner")
    ItemCorner.CornerRadius = UDim.new(0, 6)
    ItemCorner.Parent = ItemFrame

    local ItemStroke = Instance.new("UIStroke")
    ItemStroke.Color = Color3.fromRGB(70, 40, 110)
    ItemStroke.Thickness = 1
    ItemStroke.Parent = ItemFrame

    local NameLabel = Instance.new("TextLabel")
    NameLabel.Size = UDim2.new(1, -80, 0, 20)
    NameLabel.Position = UDim2.new(0, 10, 0, 4)
    NameLabel.BackgroundTransparency = 1
    NameLabel.Text = data.Name
    NameLabel.TextColor3 = Color3.fromRGB(220, 200, 255)
    NameLabel.Font = Enum.Font.GothamBold
    NameLabel.TextSize = 12
    NameLabel.TextXAlignment = Enum.TextXAlignment.Left
    NameLabel.Parent = ItemFrame

    local KeyStatusLabel = Instance.new("TextLabel")
    KeyStatusLabel.Size = UDim2.new(1, -80, 0, 14)
    KeyStatusLabel.Position = UDim2.new(0, 10, 0, 22)
    KeyStatusLabel.BackgroundTransparency = 1
    KeyStatusLabel.Text = "[" .. data.KeyStatus .. "]"
    KeyStatusLabel.TextColor3 = (data.KeyStatus == "NO KEY") and Color3.fromRGB(100, 220, 120) or Color3.fromRGB(255, 180, 80)
    KeyStatusLabel.Font = Enum.Font.Gotham
    KeyStatusLabel.TextSize = 10
    KeyStatusLabel.TextXAlignment = Enum.TextXAlignment.Left
    KeyStatusLabel.Parent = ItemFrame

    local CheckBox = Instance.new("Frame")
    CheckBox.Size = UDim2.new(0, 22, 0, 22)
    CheckBox.Position = UDim2.new(1, -30, 0.5, -11)
    CheckBox.BackgroundColor3 = Color3.fromRGB(20, 12, 32)
    CheckBox.Parent = ItemFrame

    local CheckCorner = Instance.new("UICorner")
    CheckCorner.CornerRadius = UDim.new(0, 4)
    CheckCorner.Parent = CheckBox

    local CheckStroke = Instance.new("UIStroke")
    CheckStroke.Color = Color3.fromRGB(120, 60, 180)
    CheckStroke.Thickness = 1
    CheckStroke.Parent = CheckBox

    local CheckMark = Instance.new("TextLabel")
    CheckMark.Size = UDim2.new(1, 0, 1, 0)
    CheckMark.BackgroundTransparency = 1
    CheckMark.Text = ""
    CheckMark.TextColor3 = Color3.fromRGB(0, 255, 120)
    CheckMark.Font = Enum.Font.GothamBold
    CheckMark.TextSize = 14
    CheckMark.Parent = CheckBox

    local ClickBtn = Instance.new("TextButton")
    ClickBtn.Size = UDim2.new(1, 0, 1, 0)
    ClickBtn.BackgroundTransparency = 1
    ClickBtn.Text = ""
    ClickBtn.Parent = ItemFrame

    RegisteredItems[index] = {ItemFrame = ItemFrame, NameLabel = NameLabel, CheckMark = CheckMark, Stroke = ItemStroke, Data = data}

    ClickBtn.MouseButton1Click:Connect(function()
        selectedScript = data.Script
        for _, item in pairs(RegisteredItems) do
            item.CheckMark.Text = ""
            item.Stroke.Color = Color3.fromRGB(70, 40, 110)
        end
        CheckMark.Text = "✓"
        ItemStroke.Color = Color3.fromRGB(200, 100, 255)
    end)
end

RunService.RenderStepped:Connect(function()
    local hue = (tick() % 4) / 4
    local rainbowColor = Color3.fromHSV(hue, 1, 1)
    for _, item in pairs(RegisteredItems) do
        if item.CheckMark.Text == "✓" then
            item.NameLabel.TextColor3 = rainbowColor
        else
            item.NameLabel.TextColor3 = Color3.fromRGB(220, 200, 255)
        end
    end
end)

ScriptListLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    ScriptScroll.CanvasSize = UDim2.new(0, 0, 0, ScriptListLayout.AbsoluteContentSize.Y + 10)
end)

OpenScriptBtn.MouseButton1Click:Connect(function()
    if selectedScript then
        local success, err = pcall(function()
            loadstring(selectedScript)()
        end)
        if not success then
            warn("Gagal menjalankan skrip: " .. tostring(err))
        end
    end
end)

local DisplayScroll = Instance.new("ScrollingFrame")
DisplayScroll.Size = UDim2.new(1, -10, 1, -10)
DisplayScroll.Position = UDim2.new(0, 5, 0, 5)
DisplayScroll.BackgroundTransparency = 1
DisplayScroll.BorderSizePixel = 0
DisplayScroll.ScrollBarThickness = 4
DisplayScroll.ScrollBarImageColor3 = Color3.fromRGB(140, 45, 220)
DisplayScroll.Parent = DisplayPage

local DisplayLayout = Instance.new("UIListLayout")
DisplayLayout.SortOrder = Enum.SortOrder.LayoutOrder
DisplayLayout.Padding = UDim.new(0, 8)
DisplayLayout.Parent = DisplayScroll

DisplayLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    DisplayScroll.CanvasSize = UDim2.new(0, 0, 0, DisplayLayout.AbsoluteContentSize.Y + 15)
end)

local function CreateToggle(name, order, onClick)
    local Frame = Instance.new("Frame")
    Frame.Size = UDim2.new(1, -10, 0, 40)
    Frame.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
    Frame.BorderSizePixel = 0
    Frame.LayoutOrder = order
    Frame.Parent = DisplayScroll

    local Corner = Instance.new("UICorner")
    Corner.CornerRadius = UDim.new(0, 8)
    Corner.Parent = Frame

    local Label = Instance.new("TextLabel")
    Label.Size = UDim2.new(0.6, 0, 1, 0)
    Label.Position = UDim2.new(0, 12, 0, 0)
    Label.BackgroundTransparency = 1
    Label.Text = name
    Label.TextColor3 = Color3.fromRGB(220, 200, 255)
    Label.Font = Enum.Font.GothamBold
    Label.TextSize = 12
    Label.TextXAlignment = Enum.TextXAlignment.Left
    Label.Parent = Frame

    local ToggleBg = Instance.new("Frame")
    ToggleBg.Size = UDim2.new(0, 46, 0, 24)
    ToggleBg.Position = UDim2.new(1, -56, 0.5, -12)
    ToggleBg.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    ToggleBg.Parent = Frame

    local ToggleCorner = Instance.new("UICorner")
    ToggleCorner.CornerRadius = UDim.new(1, 0)
    ToggleCorner.Parent = ToggleBg

    local ToggleCircle = Instance.new("Frame")
    ToggleCircle.Size = UDim2.new(0, 18, 0, 18)
    ToggleCircle.Position = UDim2.new(0, 3, 0.5, -9)
    ToggleCircle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    ToggleCircle.Parent = ToggleBg

    local CircleCorner = Instance.new("UICorner")
    CircleCorner.CornerRadius = UDim.new(1, 0)
    CircleCorner.Parent = ToggleCircle

    local Btn = Instance.new("TextButton")
    Btn.Size = UDim2.new(1, 0, 1, 0)
    Btn.BackgroundTransparency = 1
    Btn.Text = ""
    Btn.Parent = Frame

    local state = false
    Btn.MouseButton1Click:Connect(function()
        state = not state
        if state then
            TweenService:Create(ToggleCircle, TweenInfo.new(0.2), {Position = UDim2.new(1, -21, 0.5, -9), BackgroundColor3 = Color3.fromRGB(0, 255, 120)}):Play()
            TweenService:Create(ToggleBg, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(40, 120, 60)}):Play()
        else
            TweenService:Create(ToggleCircle, TweenInfo.new(0.2), {Position = UDim2.new(0, 3, 0.5, -9), BackgroundColor3 = Color3.fromRGB(255, 255, 255)}):Play()
            TweenService:Create(ToggleBg, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(60, 60, 60)}):Play()
        end
        pcall(onClick, state)
    end)
end

CreateToggle("120 FPS", 1, function(state)
    if setfpscap then
        setfpscap(state and 120 or 60)
    end
end)

local defaultFOV = workspace.CurrentCamera.FieldOfView
CreateToggle("PC DISPLAY", 2, function(state)
    if state then
        workspace.CurrentCamera.FieldOfView = 90
    else
        workspace.CurrentCamera.FieldOfView = defaultFOV
    end
end)

local SliderFrame = Instance.new("Frame")
SliderFrame.Size = UDim2.new(1, -10, 0, 50)
SliderFrame.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
SliderFrame.BorderSizePixel = 0
SliderFrame.LayoutOrder = 3
SliderFrame.Parent = DisplayScroll

local SliderCorner = Instance.new("UICorner")
SliderCorner.CornerRadius = UDim.new(0, 8)
SliderCorner.Parent = SliderFrame

local SliderTitle = Instance.new("TextLabel")
SliderTitle.Size = UDim2.new(1, -24, 0, 20)
SliderTitle.Position = UDim2.new(0, 12, 0, 4)
SliderTitle.BackgroundTransparency = 1
SliderTitle.Text = "JARAK ZOOM PC: 0%"
SliderTitle.TextColor3 = Color3.fromRGB(220, 200, 255)
SliderTitle.Font = Enum.Font.GothamBold
SliderTitle.TextSize = 11
SliderTitle.TextXAlignment = Enum.TextXAlignment.Left
SliderTitle.Parent = SliderFrame

local SliderBar = Instance.new("Frame")
SliderBar.Size = UDim2.new(1, -24, 0, 8)
SliderBar.Position = UDim2.new(0, 12, 0, 30)
SliderBar.BackgroundColor3 = Color3.fromRGB(20, 12, 32)
SliderBar.BorderSizePixel = 0
SliderBar.Parent = SliderFrame

local SliderBarCorner = Instance.new("UICorner")
SliderBarCorner.CornerRadius = UDim.new(1, 0)
SliderBarCorner.Parent = SliderBar

local SliderFill = Instance.new("Frame")
SliderFill.Size = UDim2.new(0, 0, 1, 0)
SliderFill.BackgroundColor3 = Color3.fromRGB(140, 45, 220)
SliderFill.BorderSizePixel = 0
SliderFill.Parent = SliderBar

local SliderFillCorner = Instance.new("UICorner")
SliderFillCorner.CornerRadius = UDim.new(1, 0)
SliderFillCorner.Parent = SliderFill

local SliderKnob = Instance.new("Frame")
SliderKnob.Size = UDim2.new(0, 16, 0, 16)
SliderKnob.Position = UDim2.new(0, -8, 0.5, -8)
SliderKnob.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
SliderKnob.Parent = SliderFill

local KnobCorner = Instance.new("UICorner")
KnobCorner.CornerRadius = UDim.new(1, 0)
KnobCorner.Parent = SliderKnob

local isDraggingZoom = false
local function UpdateZoom(input)
    local barPos = SliderBar.AbsolutePosition.X
    local barSize = SliderBar.AbsoluteSize.X
    local mouseX = input.Position.X
    local percentage = math.clamp((mouseX - barPos) / barSize, 0, 1)
    SliderFill.Size = UDim2.new(percentage, 0, 1, 0)
    local zoomPercent = math.floor(percentage * 50)
    SliderTitle.Text = "JARAK ZOOM PC: " .. zoomPercent .. "%"
    LocalPlayer.CameraMaxZoomDistance = 128 + (zoomPercent * 4)
    LocalPlayer.CameraMinZoomDistance = 0.5
end

SliderBar.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        isDraggingZoom = true
        UpdateZoom(input)
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if isDraggingZoom and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
        UpdateZoom(input)
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        isDraggingZoom = false
    end
end)

local SavedMaterials = {}
CreateToggle("FPS BOOST", 4, function(state)
    local terrain = workspace:FindFirstChildOfClass("Terrain")
    if state then
        if terrain then
            terrain.WaterWaveSize = 0
            terrain.WaterWaveSpeed = 0
            terrain.WaterReflectance = 0
            terrain.WaterTransparency = 0
        end
        for _, v in ipairs(game:GetDescendants()) do
            if v:IsA("BasePart") then
                SavedMaterials[v] = v.Material
                v.Material = Enum.Material.SmoothPlastic
            elseif v:IsA("PostEffect") or v:IsA("ParticleEmitter") or v:IsA("Trail") then
                v.Enabled = false
            end
        end
    else
        for part, mat in pairs(SavedMaterials) do
            if part and part.Parent then
                part.Material = mat
            end
        end
        SavedMaterials = {}
        for _, v in ipairs(game:GetDescendants()) do
            if v:IsA("PostEffect") or v:IsA("ParticleEmitter") or v:IsA("Trail") then
                v.Enabled = true
            end
        end
    end
end)

local Lighting = game:GetService("Lighting")
local DayLoop = nil
CreateToggle("ANTI MALAM", 5, function(state)
    if state then
        DayLoop = RunService.RenderStepped:Connect(function()
            Lighting.ClockTime = 12
        end)
    else
        if DayLoop then
            DayLoop:Disconnect()
            DayLoop = nil
        end
    end
end)

local NightLoop = nil
CreateToggle("ANTI HARI", 6, function(state)
    if state then
        NightLoop = RunService.RenderStepped:Connect(function()
            Lighting.ClockTime = 0
        end)
    else
        if NightLoop then
            NightLoop:Disconnect()
            NightLoop = nil
        end
    end
end)

local origShadows = Lighting.GlobalShadows
CreateToggle("BAYANGAN GRAFIS", 7, function(state)
    Lighting.GlobalShadows = state
    if state then
        Lighting.Technology = Enum.Technology.Future
    end
end)

local PredictionScroll = Instance.new("ScrollingFrame")
PredictionScroll.Size = UDim2.new(1, -10, 1, -10)
PredictionScroll.Position = UDim2.new(0, 5, 0, 5)
PredictionScroll.BackgroundTransparency = 1
PredictionScroll.BorderSizePixel = 0
PredictionScroll.ScrollBarThickness = 4
PredictionScroll.ScrollBarImageColor3 = Color3.fromRGB(140, 45, 220)
PredictionScroll.Parent = PredictionPage

local PredictionLayout = Instance.new("UIListLayout")
PredictionLayout.SortOrder = Enum.SortOrder.LayoutOrder
PredictionLayout.Padding = UDim.new(0, 8)
PredictionLayout.Parent = PredictionScroll

PredictionLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    PredictionScroll.CanvasSize = UDim2.new(0, 0, 0, PredictionLayout.AbsoluteContentSize.Y + 15)
end)

local PredictTitle = Instance.new("TextLabel")
PredictTitle.Size = UDim2.new(1, 0, 0, 35)
PredictTitle.BackgroundTransparency = 1
PredictTitle.Text = "PREDIKSI 20%-60%"
PredictTitle.TextColor3 = Color3.fromRGB(255, 30, 30)
PredictTitle.Font = Enum.Font.GothamBold
PredictTitle.TextSize = 18
PredictTitle.LayoutOrder = 1
PredictTitle.Parent = PredictionScroll

local PredictTitleStroke = Instance.new("UIStroke")
PredictTitleStroke.Color = Color3.fromRGB(0, 0, 0)
PredictTitleStroke.Thickness = 2
PredictTitleStroke.Parent = PredictTitle

local MainCountdownFrame = Instance.new("Frame")
MainCountdownFrame.Size = UDim2.new(1, -10, 0, 110)
MainCountdownFrame.BackgroundColor3 = Color3.fromRGB(28, 16, 42)
MainCountdownFrame.BorderSizePixel = 0
MainCountdownFrame.LayoutOrder = 2
MainCountdownFrame.Parent = PredictionScroll

local MainCountdownCorner = Instance.new("UICorner")
MainCountdownCorner.CornerRadius = UDim.new(0, 8)
MainCountdownCorner.Parent = MainCountdownFrame

local MainCountdownStroke = Instance.new("UIStroke")
MainCountdownStroke.Color = Color3.fromRGB(140, 45, 220)
MainCountdownStroke.Thickness = 1
MainCountdownStroke.Parent = MainCountdownFrame

local function CreateMainCountdownLabel(name, color, order)
    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, -20, 0, 30)
    label.Position = UDim2.new(0, 10, 0, 10 + (order - 1) * 35)
    label.BackgroundTransparency = 1
    label.Text = name .. ": 00:00:00"
    label.TextColor3 = color
    label.Font = Enum.Font.GothamBold
    label.TextSize = 14
    label.TextXAlignment = Enum.TextXAlignment.Left
    label.Parent = MainCountdownFrame

    local stroke = Instance.new("UIStroke")
    stroke.Color = Color3.fromRGB(0, 0, 0)
    stroke.Thickness = 1
    stroke.Parent = label
    return label
end

local DivineCountdownLabel = CreateMainCountdownLabel("DIVINE", Color3.fromRGB(255, 215, 0), 1)
local EternalCountdownLabel = CreateMainCountdownLabel("ETERNAL", Color3.fromRGB(180, 100, 255), 2)
local SecretCountdownLabel = CreateMainCountdownLabel("SECRET", Color3.fromRGB(255, 50, 50), 3)

local divineTime = math.random(3600, 14400)
local eternalTime = math.random(1800, 7200)
local secretTime = math.random(600, 3600)

local function formatTimeHMS(seconds)
    local h = math.floor(seconds / 3600)
    local m = math.floor((seconds % 3600) / 60)
    local s = seconds % 60
    return string.format("%02d:%02d:%02d", h, m, s)
end

local function formatTimeDetailed(seconds)
    local h = math.floor(seconds / 3600)
    local m = math.floor((seconds % 3600) / 60)
    local s = seconds % 60
    return string.format("%d Jam %d Menit %d Detik", h, m, s)
end

task.spawn(function()
    while task.wait(1) do
        divineTime = math.max(0, divineTime - 1)
        eternalTime = math.max(0, eternalTime - 1)
        secretTime = math.max(0, secretTime - 1)

        if divineTime == 0 then divineTime = math.random(3600, 14400) end
        if eternalTime == 0 then eternalTime = math.random(1800, 7200) end
        if secretTime == 0 then secretTime = math.random(600, 3600) end

        if DivineCountdownLabel and DivineCountdownLabel.Parent then
            DivineCountdownLabel.Text = "ILAHI: " .. formatTimeHMS(divineTime)
        end
        if EternalCountdownLabel and EternalCountdownLabel.Parent then
            EternalCountdownLabel.Text = "ABADI: " .. formatTimeHMS(eternalTime)
        end
        if SecretCountdownLabel and SecretCountdownLabel.Parent then
            SecretCountdownLabel.Text = "RAHASIA: " .. formatTimeHMS(secretTime)
        end
    end
end)

local EggListTitle = Instance.new("TextLabel")
EggListTitle.Size = UDim2.new(1, 0, 0, 25)
EggListTitle.BackgroundTransparency = 1
EggListTitle.Text = "DAFTAR PREDIKSI TELUR"
EggListTitle.TextColor3 = Color3.fromRGB(200, 200, 220)
EggListTitle.Font = Enum.Font.GothamBold
EggListTitle.TextSize = 14
EggListTitle.LayoutOrder = 3
EggListTitle.Parent = PredictionScroll

local EggListFrame = Instance.new("Frame")
EggListFrame.Size = UDim2.new(1, -10, 0, 0)
EggListFrame.BackgroundTransparency = 1
EggListFrame.LayoutOrder = 4
EggListFrame.Parent = PredictionScroll

local EggListLayout = Instance.new("UIListLayout")
EggListLayout.SortOrder = Enum.SortOrder.LayoutOrder
EggListLayout.Padding = UDim.new(0, 6)
EggListLayout.Parent = EggListFrame

EggListLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    EggListFrame.Size = UDim2.new(1, -10, 0, EggListLayout.AbsoluteContentSize.Y)
end)

local function CreateEggPredictionBox(eggName, rarity, color, order)
    local Frame = Instance.new("Frame")
    Frame.Size = UDim2.new(1, 0, 0, 35)
    Frame.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
    Frame.BorderSizePixel = 0
    Frame.LayoutOrder = order
    Frame.Parent = EggListFrame

    local Corner = Instance.new("UICorner")
    Corner.CornerRadius = UDim.new(0, 6)
    Corner.Parent = Frame

    local Stroke = Instance.new("UIStroke")
    Stroke.Color = color
    Stroke.Thickness = 1
    Stroke.Parent = Frame

    local NameLabel = Instance.new("TextLabel")
    NameLabel.Size = UDim2.new(0.65, 0, 1, 0)
    NameLabel.Position = UDim2.new(0, 10, 0, 0)
    NameLabel.BackgroundTransparency = 1
    NameLabel.Text = "[" .. rarity .. "] " .. eggName
    NameLabel.TextColor3 = Color3.fromRGB(220, 200, 255)
    NameLabel.Font = Enum.Font.GothamBold
    NameLabel.TextSize = 11
    NameLabel.TextXAlignment = Enum.TextXAlignment.Left
    NameLabel.Parent = Frame

    local TimeLabel = Instance.new("TextLabel")
    TimeLabel.Size = UDim2.new(0.35, -10, 1, 0)
    TimeLabel.Position = UDim2.new(0.65, 10, 0, 0)
    TimeLabel.BackgroundTransparency = 1
    TimeLabel.Text = "00:00:00"
    TimeLabel.TextColor3 = color
    TimeLabel.Font = Enum.Font.GothamBold
    TimeLabel.TextSize = 11
    TimeLabel.TextXAlignment = Enum.TextXAlignment.Right
    TimeLabel.Parent = Frame

    return TimeLabel
end

local divineEggs = { "Telur Unicorn", "Telur Kitsune", "Telur Nightflame", "Telur Archangel", "Telur WorldBurner", "Telur Aetheron", "Telur Royal Sky Whale" }
local eternalEggs = { "Telur Naga Es", "Telur Phoenix", "Telur Naga Lava", "Telur Mosasaurus", "Telur Naga Bulan Abadi", "Telur Harimau Oni", "Telur Raja Gorila", "Telur Pegasus", "Telur Kuda Kerangka", "Telur Equinox", "Telur El Maja", "Telur Pemakan Dunia", "Telur Naga Hancur", "Telur Ular Hampa" }
local secretEggs = { "Telur Yeti", "Telur Cerberus", "Telur T-Rex", "Telur Tralaledon", "Telur Bos Kerangka Kosmik", "Telur Naga Kosmik", "Telur Ubur-ubur Murni", "Telur Gargoyle", "Telur Centaur", "Telur RazorFang", "Telur Hiu Mutan", "Telur Rusa Jantan", "Telur Kraken", "Telur Ular Raja", "Telur Wendigo", "Telur Pemecah Mulut", "Telur Sayap Patah" }

local eggTimeData = {}
local orderCounter = 1

for _, egg in ipairs(divineEggs) do
    local timeLabel = CreateEggPredictionBox(egg, "DIVINE", Color3.fromRGB(255, 215, 0), orderCounter)
    orderCounter = orderCounter + 1
    eggTimeData[egg] = {Label = timeLabel, Time = math.random(3600, 14400)}
end

for _, egg in ipairs(eternalEggs) do
    local timeLabel = CreateEggPredictionBox(egg, "ETERNAL", Color3.fromRGB(180, 100, 255), orderCounter)
    orderCounter = orderCounter + 1
    eggTimeData[egg] = {Label = timeLabel, Time = math.random(1800, 7200)}
end

for _, egg in ipairs(secretEggs) do
    local timeLabel = CreateEggPredictionBox(egg, "RAHASIA", Color3.fromRGB(255, 50, 50), orderCounter)
    orderCounter = orderCounter + 1
    eggTimeData[egg] = {Label = timeLabel, Time = math.random(600, 3600)}
end

task.spawn(function()
    while task.wait(1) do
        for eggName, data in pairs(eggTimeData) do
            data.Time = math.max(0, data.Time - 1)
            if data.Time == 0 then
                if data.Label.TextColor3 == Color3.fromRGB(255, 215, 0) then
                    data.Time = math.random(3600, 14400)
                elseif data.Label.TextColor3 == Color3.fromRGB(180, 100, 255) then
                    data.Time = math.random(1800, 7200)
                else
                    data.Time = math.random(600, 3600)
                end
            end
            if data.Label and data.Label.Parent then
                data.Label.Text = formatTimeDetailed(data.Time)
            end
        end
    end
end)

local AdminAbuseContainer = Instance.new("Frame")
AdminAbuseContainer.Size = UDim2.new(1, -20, 1, -20)
AdminAbuseContainer.Position = UDim2.new(0, 10, 0, 10)
AdminAbuseContainer.BackgroundColor3 = Color3.fromRGB(28, 16, 42)
AdminAbuseContainer.BorderSizePixel = 0
AdminAbuseContainer.Parent = AdminAbusePage

local AAKorner = Instance.new("UICorner")
AAKorner.CornerRadius = UDim.new(0, 8)
AAKorner.Parent = AdminAbuseContainer

local AALayout = Instance.new("UIListLayout")
AALayout.SortOrder = Enum.SortOrder.LayoutOrder
AALayout.Padding = UDim.new(0, 10)
AALayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
AALayout.Parent = AdminAbuseContainer

local AAPadding = Instance.new("UIPadding")
AAPadding.PaddingTop = UDim.new(0, 15)
AAPadding.PaddingLeft = UDim.new(0, 10)
AAPadding.PaddingRight = UDim.new(0, 10)
AAPadding.Parent = AdminAbuseContainer

local AAGameTitle = Instance.new("TextLabel")
AAGameTitle.Size = UDim2.new(1, 0, 0, 30)
AAGameTitle.BackgroundTransparency = 1
AAGameTitle.Text = "PENCURIAN TELUR PENYALAHGUNAAN ADMIN"
AAGameTitle.TextColor3 = Color3.fromRGB(255, 30, 30)
AAGameTitle.Font = Enum.Font.FredokaOne
AAGameTitle.TextSize = 16
AAGameTitle.LayoutOrder = 1
AAGameTitle.Parent = AdminAbuseContainer

local AAGameTitleStroke = Instance.new("UIStroke")
AAGameTitleStroke.Color = Color3.fromRGB(0, 0, 0)
AAGameTitleStroke.Thickness = 3
AAGameTitleStroke.Parent = AAGameTitle

RunService.RenderStepped:Connect(function()
    if AAGameTitle and AAGameTitle.Parent then
        local floatOffsetY = math.sin(tick() * 3) * 4
        AAGameTitle.Position = UDim2.new(0, 0, 0, floatOffsetY)
    end
end)

local AADateLabel = Instance.new("TextLabel")
AADateLabel.Size = UDim2.new(1, 0, 0, 25)
AADateLabel.BackgroundTransparency = 1
AADateLabel.Text = "JADWAL: Sabtu 22:00 - 23:30"
AADateLabel.TextColor3 = Color3.fromRGB(180, 180, 220)
AADateLabel.Font = Enum.Font.Gotham
AADateLabel.TextSize = 12
AADateLabel.LayoutOrder = 2
AADateLabel.Parent = AdminAbuseContainer

local AAStatusBox = Instance.new("Frame")
AAStatusBox.Size = UDim2.new(1, 0, 0, 100)
AAStatusBox.BackgroundColor3 = Color3.fromRGB(20, 12, 32)
AAStatusBox.BorderSizePixel = 0
AAStatusBox.LayoutOrder = 3
AAStatusBox.Parent = AdminAbuseContainer

local AASBoxCorner = Instance.new("UICorner")
AASBoxCorner.CornerRadius = UDim.new(0, 6)
AASBoxCorner.Parent = AAStatusBox

local AASBoxStroke = Instance.new("UIStroke")
AASBoxStroke.Color = Color3.fromRGB(140, 45, 220)
AASBoxStroke.Thickness = 1
AASBoxStroke.Parent = AAStatusBox

local AAStatusText = Instance.new("TextLabel")
AAStatusText.Size = UDim2.new(1, -20, 1, -20)
AAStatusText.Position = UDim2.new(0, 10, 0, 10)
AAStatusText.BackgroundTransparency = 1
AAStatusText.Text = "Menghitung Waktu..."
AAStatusText.TextColor3 = Color3.fromRGB(255, 255, 255)
AAStatusText.Font = Enum.Font.GothamBold
AAStatusText.TextSize = 15
AAStatusText.TextWrapped = true
AAStatusText.Parent = AAStatusBox

local AAStatusStroke = Instance.new("UIStroke")
AAStatusStroke.Color = Color3.fromRGB(0, 0, 0)
AAStatusStroke.Thickness = 0
AAStatusStroke.Parent = AAStatusText

task.spawn(function()
    while task.wait(0.1) do
        if AAStatusText and AAStatusText.Parent then
            local now = os.date("*t")
            local isSaturday = (now.wday == 7)
            local currentSecondsToday = (now.hour * 3600) + (now.min * 60) + now.sec
            
            local startSeconds = 22 * 3600
            local endSeconds = 23 * 3600 + 30 * 60
            
            if isSaturday and currentSecondsToday >= startSeconds and currentSecondsToday < endSeconds then
                AAStatusText.Text = "🎃 ACARA HALLOWEEN CURI TELUR 🎃"
                AAStatusText.TextColor3 = Color3.fromRGB(255, 140, 0)
                
                local isBlinkOn = math.floor(tick() * 3) % 2 == 0
                AAStatusText.TextTransparency = isBlinkOn and 0 or 0.7
                AAStatusStroke.Thickness = isBlinkOn and 3 or 1
                AAStatusStroke.Color = Color3.fromRGB(0, 0, 0)
            else
                AAStatusText.TextTransparency = 0
                AAStatusStroke.Thickness = 0
                
                local daysUntilSaturday = (7 - now.wday) % 7
                if daysUntilSaturday == 0 and currentSecondsToday >= startSeconds then
                    daysUntilSaturday = 7
                end
                
                local target = {
                    year = now.year,
                    month = now.month,
                    day = now.day + daysUntilSaturday,
                    hour = 22,
                    min = 0,
                    sec = 0
                }
                local targetTime = os.time(target)
                local nowTime = os.time()
                local diff = math.max(0, targetTime - nowTime)
                
                local days = math.floor(diff / 86400)
                local hours = math.floor((diff % 86400) / 3600)
                local minutes = math.floor((diff % 3600) / 60)
                local seconds = diff % 60
                
                AAStatusText.Text = string.format("MENUJU UPDATE SABTU 22:00:\n%d Hari %d Jam %d Menit %d Detik", days, hours, minutes, seconds)
                AAStatusText.TextColor3 = Color3.fromRGB(255, 255, 255)
            end
        end
    end
end)

local DivineScroll = Instance.new("ScrollingFrame")
DivineScroll.Size = UDim2.new(1, -10, 1, -10)
DivineScroll.Position = UDim2.new(0, 5, 0, 5)
DivineScroll.BackgroundTransparency = 1
DivineScroll.BorderSizePixel = 0
DivineScroll.ScrollBarThickness = 4
DivineScroll.ScrollBarImageColor3 = Color3.fromRGB(140, 45, 220)
DivineScroll.Parent = DivineSpawnedPage

local DivineLayout = Instance.new("UIListLayout")
DivineLayout.SortOrder = Enum.SortOrder.LayoutOrder
DivineLayout.Padding = UDim.new(0, 8)
DivineLayout.Parent = DivineScroll

DivineLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    DivineScroll.CanvasSize = UDim2.new(0, 0, 0, DivineLayout.AbsoluteContentSize.Y + 15)
end)

local DateLabel = Instance.new("TextLabel")
DateLabel.Size = UDim2.new(1, 0, 0, 25)
DateLabel.BackgroundTransparency = 1
DateLabel.Text = os.date("%A, %d %B 2026")
DateLabel.TextColor3 = Color3.fromRGB(200, 200, 220)
DateLabel.Font = Enum.Font.GothamBold
DateLabel.TextSize = 14
DateLabel.TextXAlignment = Enum.TextXAlignment.Center
DateLabel.LayoutOrder = 1
DateLabel.Parent = DivineScroll

local ListTitle = Instance.new("TextLabel")
ListTitle.Size = UDim2.new(1, 0, 0, 35)
ListTitle.BackgroundTransparency = 1
ListTitle.Text = "DAFTAR KELAHIRAN ILAHI"
ListTitle.TextColor3 = Color3.fromRGB(255, 30, 30)
ListTitle.Font = Enum.Font.GothamBold
ListTitle.TextSize = 18
ListTitle.TextXAlignment = Enum.TextXAlignment.Center
ListTitle.LayoutOrder = 2
ListTitle.Parent = DivineScroll

local ListTitleStroke = Instance.new("UIStroke")
ListTitleStroke.Color = Color3.fromRGB(0, 0, 0)
ListTitleStroke.Thickness = 2
ListTitleStroke.Parent = ListTitle

local ServerLabel = Instance.new("TextLabel")
ServerLabel.Size = UDim2.new(1, 0, 0, 25)
ServerLabel.BackgroundTransparency = 1
ServerLabel.Text = "🇲🇨 SERVER INDONESIA 🇲🇨"
ServerLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
ServerLabel.Font = Enum.Font.GothamBold
ServerLabel.TextSize = 14
ServerLabel.TextXAlignment = Enum.TextXAlignment.Center
ServerLabel.LayoutOrder = 3
ServerLabel.Parent = DivineScroll

local ListFrame = Instance.new("Frame")
ListFrame.Size = UDim2.new(1, 0, 0, 0)
ListFrame.BackgroundTransparency = 1
ListFrame.LayoutOrder = 4
ListFrame.Parent = DivineScroll

local ListLayout = Instance.new("UIListLayout")
ListLayout.SortOrder = Enum.SortOrder.LayoutOrder
ListLayout.Padding = UDim.new(0, 6)
ListLayout.Parent = ListFrame

ListLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    ListFrame.Size = UDim2.new(1, 0, 0, ListLayout.AbsoluteContentSize.Y)
end)

local SaveFileName = "LipzyHub_DivineSpawnList.json"
local DivineSpawnData = {}

local function SaveDivineList()
    if pcall(function() return writefile(SaveFileName, "") end) then
        local success, json = pcall(function()
            return game:GetService("HttpService"):JSONEncode(DivineSpawnData)
        end)
        if success then
            writefile(SaveFileName, json)
        end
    end
end

local function LoadDivineList()
    if pcall(function() return readfile(SaveFileName) end) then
        local success, json = pcall(function()
            return game:GetService("HttpService"):JSONDecode(readfile(SaveFileName))
        end)
        if success and type(json) == "table" then
            DivineSpawnData = json
            for _, item in ipairs(DivineSpawnData) do
                local Box = Instance.new("Frame")
                Box.Size = UDim2.new(1, 0, 0, 35)
                Box.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
                Box.BorderSizePixel = 0
                Box.LayoutOrder = item.Order
                Box.Parent = ListFrame

                local BoxCorner = Instance.new("UICorner")
                BoxCorner.CornerRadius = UDim.new(0, 6)
                BoxCorner.Parent = Box

                local BoxStroke = Instance.new("UIStroke")
                BoxStroke.Color = Color3.fromRGB(140, 45, 220)
                BoxStroke.Thickness = 1
                BoxStroke.Parent = Box

                local InfoLabel = Instance.new("TextLabel")
                InfoLabel.Size = UDim2.new(1, -20, 1, 0)
                InfoLabel.Position = UDim2.new(0, 10, 0, 0)
                InfoLabel.BackgroundTransparency = 1
                InfoLabel.Text = string.format("%s | %s [DIVINE] %s", item.Egg, item.Area, item.Time)
                InfoLabel.TextColor3 = Color3.fromRGB(255, 215, 0)
                InfoLabel.Font = Enum.Font.GothamBold
                InfoLabel.TextSize = 12
                InfoLabel.TextXAlignment = Enum.TextXAlignment.Left
                InfoLabel.Parent = Box
            end
        end
    end
end

local function AddToDivineList(eggName, area, timeStr)
    for _, data in ipairs(DivineSpawnData) do
        if data.Egg == eggName and data.Area == area then
            return
        end
    end

    local newItem = {Egg = eggName, Area = area, Time = timeStr, Order = #DivineSpawnData + 1}
    table.insert(DivineSpawnData, newItem)
    SaveDivineList()

    local Box = Instance.new("Frame")
    Box.Size = UDim2.new(1, 0, 0, 35)
    Box.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
    Box.BorderSizePixel = 0
    Box.LayoutOrder = newItem.Order
    Box.Parent = ListFrame

    local BoxCorner = Instance.new("UICorner")
    BoxCorner.CornerRadius = UDim.new(0, 6)
    BoxCorner.Parent = Box

    local BoxStroke = Instance.new("UIStroke")
    BoxStroke.Color = Color3.fromRGB(140, 45, 220)
    BoxStroke.Thickness = 1
    BoxStroke.Parent = Box

    local InfoLabel = Instance.new("TextLabel")
    InfoLabel.Size = UDim2.new(1, -20, 1, 0)
    InfoLabel.Position = UDim2.new(0, 10, 0, 0)
    InfoLabel.BackgroundTransparency = 1
    InfoLabel.Text = string.format("%s | %s [DIVINE] %s", eggName, area, timeStr)
    InfoLabel.TextColor3 = Color3.fromRGB(255, 215, 0)
    InfoLabel.Font = Enum.Font.GothamBold
    InfoLabel.TextSize = 12
    InfoLabel.TextXAlignment = Enum.TextXAlignment.Left
    InfoLabel.Parent = Box

    Box.Position = UDim2.new(0, 0, 0, -10)
    TweenService:Create(Box, TweenInfo.new(0.3, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {Position = UDim2.new(0, 0, 0, 0)}):Play()
end

LoadDivineList()

for _, descendant in ipairs(workspace:GetDescendants()) do
    local name = descendant.Name:upper()
    if name:find("DIVINE") and name:find("EGG") then
        local eggName = descendant.Name
        local area = descendant.Parent.Name ~= "Workspace" and descendant.Parent.Name or "AREA TIDAK DIKETAHUI"
        local timeStr = os.date("%I:%M %p")
        AddToDivineList(eggName, area, timeStr)
    end
end

workspace.DescendantAdded:Connect(function(descendant)
    local name = descendant.Name:upper()
    if name:find("DIVINE") and name:find("EGG") then
        local eggName = descendant.Name
        local area = descendant.Parent.Name ~= "Workspace" and descendant.Parent.Name or "AREA TIDAK DIKETAHUI"
        local timeStr = os.date("%I:%M %p")
        AddToDivineList(eggName, area, timeStr)
    end
end)

task.spawn(function()
    while task.wait(30) do
        local currentHour = tonumber(os.date("%H"))
        local currentMinute = tonumber(os.date("%M"))
        if currentHour == 0 and currentMinute == 0 then
            DivineSpawnData = {}
            SaveDivineList()
            for _, child in ipairs(ListFrame:GetChildren()) do
                if child:IsA("Frame") then
                    child:Destroy()
                end
            end
        end
    end
end)

-- ==========================================
-- FITUR NOTIFIKASI OTOMATIS (SABTU & SELASA)
-- ==========================================
task.spawn(function()
    local lastNotifMinute = -1
    while task.wait(1) do
        local now = os.date("*t")
        local wday = now.wday -- 7 = Sabtu, 3 = Selasa
        local hour = now.hour
        local min = now.min
        local sec = now.sec
        
        -- Cek Khusus Hari Sabtu (21:30 - 22:30) dan Selasa (19:30 khusus LifzxAfter2)
        local isSaturdayEvent = (wday == 7 and hour == 21 and min >= 30) or (wday == 7 and hour == 22 and min <= 30)
        local isTuesdayEvent = (wday == 3 and hour == 19 and min == 30 and LocalPlayer.Name == "LifzxAfter2")
        
        if (isSaturdayEvent or isTuesdayEvent) and sec == 0 and min ~= lastNotifMinute then
            lastNotifMinute = min
            
            local messageText = ""
            if wday == 7 then
                if hour == 21 and min == 30 then
                    messageText = "Admin Abuse😍 My Owner And Moderator Haii."
                elseif hour == 22 and min == 0 then
                    messageText = "Gooo 22:00 Admin Di Mulai?"
                elseif hour == 22 and min == 30 then
                    messageText = "L Atau W?"
                else
                    messageText = "Admin Abuse Event Berlangsung!"
                end
            elseif wday == 3 then
                messageText = "P."
            end
            
            if messageText ~= "" then
                local AutoNotifGui = Instance.new("ScreenGui")
                AutoNotifGui.Name = "LipzyAutoNotification"
                AutoNotifGui.Parent = game.CoreGui
                AutoNotifGui.IgnoreGuiInset = true

                local AutoNotifFrame = Instance.new("Frame")
                AutoNotifFrame.Size = UDim2.new(0, 400, 0, 170)
                AutoNotifFrame.Position = UDim2.new(0.5, -200, 0, -200)
                AutoNotifFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0) -- Hitam
                AutoNotifFrame.BorderSizePixel = 0
                AutoNotifFrame.Parent = AutoNotifGui

                local NotifCorner = Instance.new("UICorner")
                NotifCorner.CornerRadius = UDim.new(0, 10)
                NotifCorner.Parent = AutoNotifFrame

                local NotifStroke = Instance.new("UIStroke")
                NotifStroke.Color = Color3.fromRGB(140, 45, 220)
                NotifStroke.Thickness = 2
                NotifStroke.Parent = AutoNotifFrame

                -- Banner Image (Bunder/Banner ID: 107445714588354)
                local BannerImg = Instance.new("ImageLabel")
                BannerImg.Size = UDim2.new(0, 50, 0, 50)
                BannerImg.Position = UDim2.new(0, 15, 0, 15)
                BannerImg.BackgroundTransparency = 1
                BannerImg.Image = "rbxassetid://107445714588354"
                BannerImg.Parent = AutoNotifFrame

                local BannerCorner = Instance.new("UICorner")
                BannerCorner.CornerRadius = UDim.new(1, 0)
                BannerCorner.Parent = BannerImg

                -- Teks "LIPZY X ZALZ" (Rainbow, Tebal, Pinggiran Hitam)
                local BrandLabel = Instance.new("TextLabel")
                BrandLabel.Size = UDim2.new(1, -80, 0, 30)
                BrandLabel.Position = UDim2.new(0, 75, 0, 12)
                BrandLabel.BackgroundTransparency = 1
                BrandLabel.Text = "LIPZY X ZALZ"
                BrandLabel.Font = Enum.Font.GothamBold
                BrandLabel.TextSize = 18
                BrandLabel.TextXAlignment = Enum.TextXAlignment.Left
                BrandLabel.Parent = AutoNotifFrame

                local BrandStroke = Instance.new("UIStroke")
                BrandStroke.Color = Color3.fromRGB(0, 0, 0)
                BrandStroke.Thickness = 2
                BrandStroke.Parent = BrandLabel

                task.spawn(function()
                    while BrandLabel and BrandLabel.Parent do
                        local h = (tick() % 4) / 4
                        BrandLabel.TextColor3 = Color3.fromHSV(h, 1, 1)
                        task.wait(0.1)
                    end
                end)

                -- Teks "[OWNER AND MODERATOR]" (Merah, Tebal, Pinggiran Hitam)
                local RoleLabel = Instance.new("TextLabel")
                RoleLabel.Size = UDim2.new(1, -80, 0, 20)
                RoleLabel.Position = UDim2.new(0, 75, 0, 42)
                RoleLabel.BackgroundTransparency = 1
                RoleLabel.Text = "[OWNER AND MODERATOR]"
                RoleLabel.TextColor3 = Color3.fromRGB(255, 0, 0)
                RoleLabel.Font = Enum.Font.GothamBold
                RoleLabel.TextSize = 11
                RoleLabel.TextXAlignment = Enum.TextXAlignment.Left
                RoleLabel.Parent = AutoNotifFrame

                local RoleStroke = Instance.new("UIStroke")
                RoleStroke.Color = Color3.fromRGB(0, 0, 0)
                RoleStroke.Thickness = 2
                RoleStroke.Parent = RoleLabel

                -- Pesan/Message (Hijau, Pinggiran Hitam)
                local MsgLabel = Instance.new("TextLabel")
                MsgLabel.Size = UDim2.new(1, -30, 0, 85)
                MsgLabel.Position = UDim2.new(0, 15, 0, 75)
                MsgLabel.BackgroundTransparency = 1
                MsgLabel.Text = "Message : " .. messageText
                MsgLabel.TextColor3 = Color3.fromRGB(0, 255, 0)
                MsgLabel.Font = Enum.Font.GothamBold
                MsgLabel.TextSize = 13
                MsgLabel.TextXAlignment = Enum.TextXAlignment.Left
                MsgLabel.TextYAlignment = Enum.TextYAlignment.Top
                MsgLabel.TextWrapped = true
                MsgLabel.Parent = AutoNotifFrame

                local MsgStroke = Instance.new("UIStroke")
                MsgStroke.Color = Color3.fromRGB(0, 0, 0)
                MsgStroke.Thickness = 2
                MsgStroke.Parent = MsgLabel

                -- Animasi Masuk
                TweenService:Create(AutoNotifFrame, TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {Position = UDim2.new(0.5, -200, 0, 40)}):Play()

                -- Bertahan selama 4 detik, lalu animasi keluar
                task.delay(4, function()
                    if AutoNotifFrame and AutoNotifFrame.Parent then
                        TweenService:Create(AutoNotifFrame, TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.In), {Position = UDim2.new(0.5, -200, 0, -200)}):Play()
                        task.wait(0.5)
                        AutoNotifGui:Destroy()
                    end
                end)
            end
        end
    end
end)

print("Lipzy Hub V5.2 Berhasil Dimuat!")
