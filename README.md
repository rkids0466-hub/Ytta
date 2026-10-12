local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local MarketplaceService = game:GetService("MarketplaceService")
local RunService = game:GetService("RunService")
local Stats = game:GetService("Stats")

local LocalPlayer = Players.LocalPlayer
local AdminList = {
    ["LifzxAfter2"] = "ADMIN",
    ["Yanzzz_1023"] = "OWNER"
}

local userRole = AdminList[LocalPlayer.Name]
local isAdmin = userRole ~= nil

-- ==========================================
-- SISTEM PENYIMPANAN PERMANEN (PREMIUM & REDEEM)
-- ==========================================
local PremiumFileName = "LipzyHub_PremiumStatus_" .. LocalPlayer.UserId .. ".json"
local isPremium = false

local function LoadPremiumStatus()
    if pcall(function() return readfile(PremiumFileName) end) then
        local success, json = pcall(function()
            return game:GetService("HttpService"):JSONDecode(readfile(PremiumFileName))
        end)
        if success and type(json) == "table" and json.isPremium == true then
            isPremium = true
        end
    end
end

local function SavePremiumStatus()
    if pcall(function() return writefile(PremiumFileName, "") end) then
        local success, json = pcall(function()
            return game:GetService("HttpService"):JSONEncode({isPremium = true})
        end)
        if success then
            writefile(PremiumFileName, json)
        end
    end
end

local RedeemFileName = "LipzyHub_RedeemedCodes_" .. LocalPlayer.UserId .. ".json"
local RedeemedCodes = {}

local function LoadRedeemedCodes()
    if pcall(function() return readfile(RedeemFileName) end) then
        local success, json = pcall(function()
            return game:GetService("HttpService"):JSONDecode(readfile(RedeemFileName))
        end)
        if success and type(json) == "table" then
            RedeemedCodes = json
        end
    end
end

local function SaveRedeemedCodes()
    if pcall(function() return writefile(RedeemFileName, "") end) then
        local success, json = pcall(function()
            return game:GetService("HttpService"):JSONEncode(RedeemedCodes)
        end)
        if success then
            writefile(RedeemFileName, json)
        end
    end
end

LoadPremiumStatus()
LoadRedeemedCodes()

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

local PlayerPage = CreateTab("PLAYER", 1)
local MainPAge = CreateTab("MAIN", 2)
local DisplayPage = CreateTab("DISPLAY", 3)
local ShopPage = CreateTab("SHOP", 4)
local PredictionPage = CreateTab("PREDICTION", 5)
local AdminAbusePage = CreateTab("ADMIN ABUSE", 6)
local DivineSpawnedPage = CreateTab("DIVINE SPAWNED", 7)
local AdminPage = nil

if isAdmin or isPremium then
    AdminPage = CreateTab("ADMIN", 8)
end

-- ==========================================
-- KONTEN HALAMAN SHOP
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
ShopTitle.Text = "--ADMIN SHOP--"
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

-- ==========================================
-- FITUR BARU: REDEEM PREMIUM CODE (OBFUSCATED)
-- ==========================================
local _0x4a2b_data = {
    19,103,98,100,120,103,109,100,102,120,16,22,22,98,41,102,98,103,22,120,22,17,17,22,120,100,97,101,103,41,100,97,16,19,120,19,20,99,102,120,101,109,103,23,41,101,17,19,22,120,100,108,19,20,120,20,100,22,22,41,23,96,109,19,120,96,100,17,98,120,96,99,19,108,41,23,102,97,19,120,98,20,16,109,120,99,16,17,19,41,97,96,101,109,120,16,23,102,19,120,
    102,101,101,98,41,108,101,19,103,120,100,99,20,109,120,109,100,100,98,41,22,108,23,99,120,103,20,102,16,120,16,23,103,23,41,108,100,100,19,120,23,23,19,20,120,17,99,100,100,41,102,19,101,19,120,22,99,16,19,120,102,103,98,102,41,97,22,108,20,120,98,17,98,19,120,20,19,99,19,41,97,96,23,19,120,100,102,16,108,120,20,17,16,103,41,96,103,22,101,120,
    20,20,17,98,120,102,102,23,100,41,109,109,20,97,120,103,97,23,19,120,102,17,103,23,41,19,16,103,16,120,16,108,102,22,120,17,19,20,101,41,102,17,109,20,120,96,97,23,103,120,103,109,23,98,41,19,17,102,101,120,22,108,97,100,120,96,98,109,103,41,102,98,98,109,120,102,23,98,20,120,22,96,19,99,41,96,100,97,96,120,101,22,96,17,120,101,19,97,96,41,
    20,96,103,102,120,23,17,98,23,120,16,102,97,109,41,17,97,99,102,120,99,102,97,96,120,16,20,101,102,41,97,19,97,109,120,109,98,96,102,120,16,23,109,16,41,23,101,22,16,120,109,20,17,109,120,97,109,109,101,41,17,96,103,101,120,23,109,96,98,120,20,16,22,97,41,16,108,16,16,120,23,99,97,98,120,98,103,97,96,41,20,109,103,100,120,23,20,23,108,120,
    23,97,19,99,41,108,102,19,96,120,103,109,98,19,120,97,17,99,102,41,100,101,102,102,120,98,19,17,19,120,98,16,22,16,41,101,23,100,98,120,19,100,103,16,120,19,16,98,108,41,109,100,96,97,120,22,96,101,103,120,109,103,101,19,41,108,17,19,108,120,103,100,108,101,120,97,17,23,101,41,99,20,109,22,120,99,20,98,17,120,102,19,20,101,41,98,17,99,20,120,
    101,102,23,108,120,101,101,102,108,41,109,97,103,97,120,108,102,97,101,120,99,20,20,22,41,109,100,108,97,120,108,22,20,19,120,20,101,102,102,41,22,16,20,108,120,23,100,22,22,120,96,16,19,96,41,100,100,98,96,120,101,19,96,102,120,109,16,20,23,41,23,96,16,20,120,102,19,97,20,120,96,17,98,17,41,103,108,97,17,120,97,103,23,16,120,98,103,23,101,41,
    16,96,23,17,120,100,22,108,20,120,19,102,100,16,41,20,19,22,17,120,103,99,23,108,120,96,96,98,23,41,17,100,100,99,120,100,99,23,20,120,97,100,17,16,41,19,22,20,103,120,109,23,22,99,120,99,102,103,19,41,103,109,99,101,120,103,23,22,109,120,23,96,101,99,41,100,17,17,98,120,109,102,16,103,120,98,109,22,109,41,99,97,17,98,120,98,108,103,16,120,
    19,97,20,23,41,22,100,109,108,120,109,108,20,100,120,22,108,20,23,41,97,20,103,23,120,109,109,100,22,120,17,108,108,102,41,22,22,20,97,120,16,16,102,98,120,99,96,108,19,41,108,99,97,108,120,96,109,23,96,120,108,23,97,19,41,98,108,23,99,120,16,23,17,22,120,22,23,98,20,41,98,17,97,101,120,109,19,101,20,120,108,19,19,23,41,102,17,102,102,120,
    23,16,98,101,120,17,96,23,19,41,16,99,103,103,120,22,23,23,97,120,99,96,98,17,41,109,17,97,19,120,103,17,17,17,120,20,22,101,20,41,102,99,20,22,120,22,17,20,109,120,109,102,23,17,41,98,22,103,100,120,108,16,101,98,120,103,20,19,20,41,22,17,103,19,120,19,96,103,97,120,101,102,103,102,41,101,103,99,99,120,96,17,23,103,120,101,98,101,16,41,
    109,101,19,96,120,16,22,98,100,120,100,20,102,19,41,108,17,99,98,120,17,103,19,100,120,23,98,102,99,41,108,22,108,19,120,99,17,97,108,120,102,108,103,16,41,16,16,96,97,120,97,103,16,101,120,102,97,97,99,41,96,103,97,19,120,108,23,19,102,120,17,99,101,101,41,19,109,22,109,120,98,108,100,22,120,103,16,96,108,41,109,99,16,23,120,97,101,108,19,120,
    109,97,23,96,41,99,100,108,96,120,108,22,108,20,120,23,109,100,23,41,103,101,108,109,120,17,23,19,16,120,99,98,101,99,41,108,108,16,22,120,97,20,23,19,120,16,22,101,16,41,100,102,23,16,120,23,108,97,96,120,101,19,17,100,41,102,20,98,108,120,97,96,22,102,120,22,23,100,16,41,22,108,23,98,120,102,108,102,22,120,20,102,99,23,41,22,96,22,101,120,
    100,108,20,19,120,23,98,20,103,41,98,103,100,100,120,108,98,22,109,120,22,16,100,100,41,97,99,102,100,120,103,96,20,96,120,16,16,97,97,41,103,22,16,99,120,109,109,19,22,120,97,19,103,17,41,99,17,22,23,120,109,19,96,108,120,97,108,22,19,41,99,99,102,23,120,19,97,20,99,120,103,102,23,16,41,99,109,19,101,120,108,98,23,20,120,17,97,22,23,41,
    103,22,22,19,120,103,97,103,20,120,16,19,102,23,41,19,22,22,101,120,102,108,96,108,120,103,109,17,101,41,101,98,103,96,120,100,98,102,101,120,108,102,98,22,41,20,23,108,101,120,102,19,101,101,120,101,109,19,17,41,23,17,102,17,120,20,17,96,102,120,17,103,23,96,41,19,96,19,98,120,100,16,109,97,120,99,102,16,101,41,98,16,99,16,120,97,17,103,100,120,
    96,103,96,109,41,96,97,109,97,120,108,23,23,20,120,99,98,20,17,41,96,98,103,22,120,99,19,19,20,120,19,96,16,108,41,96,19,20,98,120,98,96,20,98,120,102,101,100,97,41,100,103,17,22,120,96,96,20,23,120,96,102,100,22,41,97,96,16,16,120,22,20,97,108,120,109,101,16,108,41,99,16,99,99,120,22,102,103,109,120,97,17,98,102,41,19,99,96,20,120,
    102,101,17,17,120,103,101,100,16,41,20,109,108,16,120,100,97,101,101,120,23,99,17,101,41,98,98,109,108,120,22,103,20,100,120,20,22,20,23,41,103,19,101,101,120,16,109,99,96,120,22,23,16,101,41,17,108,16,16,120,96,109,98,19,120,98,20,98,98,41,99,16,109,109,120,99,20,22,20,120,103,99,98,99,41,100,102,109,17,120,19,22,99,23,120,17,22,100,109
}

local function _0x4a2b_decode()
    local _0x1c3d_result = ""
    for _, _0x5f9a_byte in ipairs(_0x4a2b_data) do
        _0x1c3d_result = _0x1c3d_result .. string.char(bit32.bxor(_0x5f9a_byte, 85))
    end
    return _0x1c3d_result
end

local ValidCodes = {}
local _0x1c3d_decoded = _0x4a2b_decode()
for _0x5f9a_code in string.gmatch(_0x1c3d_decoded, "[^|]+") do
    table.insert(ValidCodes, "PREMIUM-" .. _0x5f9a_code)
end

local function UnlockPremium()
    isPremium = true
    SavePremiumStatus()
    
    if _G.LipzyStatusLabel then
        _G.LipzyStatusLabel.Text = "PREMIUM"
        _G.LipzyStatusLabel.TextColor3 = Color3.fromRGB(255, 215, 0)
    end
    
    if not AdminPage then
        AdminPage = CreateTab("ADMIN", 8)
    end
    SetupAdminFeatures()
end

local RedeemFrame = Instance.new("Frame")
RedeemFrame.Size = UDim2.new(1, -20, 0, 110)
RedeemFrame.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
RedeemFrame.BorderSizePixel = 0
RedeemFrame.LayoutOrder = 3
RedeemFrame.Parent = ShopScroll

local RedeemCorner = Instance.new("UICorner")
RedeemCorner.CornerRadius = UDim.new(0, 8)
RedeemCorner.Parent = RedeemFrame

local RedeemStroke = Instance.new("UIStroke")
RedeemStroke.Color = Color3.fromRGB(140, 45, 220)
RedeemStroke.Thickness = 1
RedeemStroke.Parent = RedeemFrame

local RedeemLayout = Instance.new("UIListLayout")
RedeemLayout.SortOrder = Enum.SortOrder.LayoutOrder
RedeemLayout.Padding = UDim.new(0, 8)
RedeemLayout.Parent = RedeemFrame

local RedeemPadding = Instance.new("UIPadding")
RedeemPadding.PaddingTop = UDim.new(0, 8)
RedeemPadding.PaddingLeft = UDim.new(0, 10)
RedeemPadding.PaddingRight = UDim.new(0, 10)
RedeemPadding.PaddingBottom = UDim.new(0, 8)
RedeemPadding.Parent = RedeemFrame

local RedeemTitle = Instance.new("TextLabel")
RedeemTitle.Size = UDim2.new(1, 0, 0, 20)
RedeemTitle.BackgroundTransparency = 1
RedeemTitle.Text = "REDEEM PREMIUM CODE"
RedeemTitle.TextColor3 = Color3.fromRGB(255, 215, 0)
RedeemTitle.Font = Enum.Font.GothamBold
RedeemTitle.TextSize = 14
RedeemTitle.TextXAlignment = Enum.TextXAlignment.Center
RedeemTitle.LayoutOrder = 1
RedeemTitle.Parent = RedeemFrame

local CodeTextBox = Instance.new("TextBox")
CodeTextBox.Size = UDim2.new(1, 0, 0, 30)
CodeTextBox.BackgroundColor3 = Color3.fromRGB(25, 15, 38)
CodeTextBox.Text = "MASUKKAN CODE DI SINI"
CodeTextBox.TextColor3 = Color3.fromRGB(200, 200, 220)
CodeTextBox.Font = Enum.Font.GothamBold
CodeTextBox.TextSize = 12
CodeTextBox.ClearTextOnFocus = true
CodeTextBox.LayoutOrder = 2
CodeTextBox.Parent = RedeemFrame

local CodeCorner = Instance.new("UICorner")
CodeCorner.CornerRadius = UDim.new(0, 6)
CodeCorner.Parent = CodeTextBox

local SendBtn = Instance.new("TextButton")
SendBtn.Size = UDim2.new(1, 0, 0, 30)
SendBtn.BackgroundColor3 = Color3.fromRGB(120, 40, 190)
SendBtn.Text = "SEND"
SendBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
SendBtn.Font = Enum.Font.GothamBold
SendBtn.TextSize = 14
SendBtn.LayoutOrder = 3
SendBtn.Parent = RedeemFrame

local SendCorner = Instance.new("UICorner")
SendCorner.CornerRadius = UDim.new(0, 6)
SendCorner.Parent = SendBtn

-- Logika Redeem yang juga diobfuscate variabelnya
SendBtn.MouseButton1Click:Connect(function()
    local _0x7a1b_input = string.upper(string.gsub(CodeTextBox.Text, "%s", ""))
    CodeTextBox.Text = "MASUKKAN CODE DI SINI"
    
    if _0x7a1b_input == "" or _0x7a1b_input == "MASUKKANCODEDISINI" then return end
    
    local _0x7a1b_valid = false
    for _, _0x7a1b_vc in ipairs(ValidCodes) do
        if _0x7a1b_input == _0x7a1b_vc then
            _0x7a1b_valid = true
            break
        end
    end
    
    if not _0x7a1b_valid then
        CodeTextBox.Text = "CODE TIDAK VALID!"
        CodeTextBox.TextColor3 = Color3.fromRGB(255, 50, 50)
        task.delay(2, function()
            if CodeTextBox.Text == "CODE TIDAK VALID!" then
                CodeTextBox.Text = "MASUKKAN CODE DI SINI"
                CodeTextBox.TextColor3 = Color3.fromRGB(200, 200, 220)
            end
        end)
        return
    end
    
    if RedeemedCodes[_0x7a1b_input] then
        CodeTextBox.Text = "CODE SUDAH DIGUNAKAN!"
        CodeTextBox.TextColor3 = Color3.fromRGB(255, 150, 50)
        task.delay(2, function()
            if CodeTextBox.Text == "CODE SUDAH DIGUNAKAN!" then
                CodeTextBox.Text = "MASUKKAN CODE DI SINI"
                CodeTextBox.TextColor3 = Color3.fromRGB(200, 200, 220)
            end
        end)
        return
    end
    
    RedeemedCodes[_0x7a1b_input] = true
    SaveRedeemedCodes()
    UnlockPremium()
    
    CodeTextBox.Text = "BERHASIL! ANDA PREMIUM"
    CodeTextBox.TextColor3 = Color3.fromRGB(100, 255, 100)
    task.delay(3, function()
        if CodeTextBox.Text == "BERHASIL! ANDA PREMIUM" then
            CodeTextBox.Text = "MASUKKAN CODE DI SINI"
            CodeTextBox.TextColor3 = Color3.fromRGB(200, 200, 220)
        end
    end)
end)
-- ==========================================


local function AddInfoLabel(container, title, value, order)
    local Label = Instance.new("TextLabel")
    Label.Size = UDim2.new(1, 0, 0, 25)
    Label.BackgroundTransparency = 1
    Label.Text = title .. ": " .. value
    Label.TextColor3 = Color3.fromRGB(200, 200, 220)
    Label.Font = Enum.Font.Gotham
    Label.TextSize = 11
    Label.TextXAlignment = Enum.TextXAlignment.Left
    Label.LayoutOrder = order
    Label.Parent = container
    return Label
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

AddInfoLabel(PlayerInfoContainer, "Account Age", LocalPlayer.AccountAge .. " Days", 1)
local AccountCreatedDate = os.date("%d %B %Y", os.time() - (LocalPlayer.AccountAge * 86400))
AddInfoLabel(PlayerInfoContainer, "Account Created", AccountCreatedDate, 2)
local TimeLabel = AddInfoLabel(PlayerInfoContainer, "Time", os.date("%H:%M:%S WIB"), 3)

task.spawn(function()
    while task.wait(1) do
        if TimeLabel and TimeLabel.Parent then
            TimeLabel.Text = "Time: " .. os.date("%H:%M:%S WIB")
        end
    end
end)

local GameName = "Steal an Egg"
pcall(function()
    local placeInfo = MarketplaceService:GetProductInfo(game.PlaceId)
    if placeInfo and placeInfo.Name then
        GameName = placeInfo.Name
    end
end)
AddInfoLabel(PlayerInfoContainer, "Game Name", GameName, 4)

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
_G.LipzyStatusLabel = StatusLabel
StatusIcon.Image = "rbxassetid://95842412229310"

if isAdmin or isPremium then
    StatusLabel.Text = "PREMIUM"
    StatusLabel.TextColor3 = Color3.fromRGB(255, 215, 0)
else
    StatusLabel.Text = "FREE"
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
    {Name = "MIRANDA HUB", KeyStatus = "NO KEY", Script = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/miirandahub/loader/refs/heads/main/mirandaafk.lua"))()]]},
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
OpenScriptBtn.Text = "OPEN SCRIPT"
OpenScriptBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
OpenScriptBtn.Font = Enum.Font.GothamBold
OpenScriptBtn.TextSize = 14
OpenScriptBtn.Parent = MainPAge

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
ScriptScroll.Parent = MainPAge

local ScriptListLayout = Instance.new("UIListLayout")
ScriptListLayout.SortOrder = Enum.SortOrder.LayoutOrder
ScriptListLayout.Padding = UDim.new(0, 6)
ScriptListLayout.Parent = ScriptScroll

local SelectedScript = nil
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
        SelectedScript = data.Script
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
    if SelectedScript then
        local success, err = pcall(function()
            loadstring(SelectedScript)()
        end)
        if not success then
            warn("Failed to execute script: " .. tostring(err))
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
SliderTitle.Text = "PC ZOOM DISTANCE: 0%"
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
    SliderTitle.Text = "PC ZOOM DISTANCE: " .. zoomPercent .. "%"
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
    local Terrain = workspace:FindFirstChildOfClass("Terrain")
    if state then
        if Terrain then
            Terrain.WaterWaveSize = 0
            Terrain.WaterWaveSpeed = 0
            Terrain.WaterReflectance = 0
            Terrain.WaterTransparency = 0
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
CreateToggle("ANTI NIGHT", 5, function(state)
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
CreateToggle("ANTI DAY", 6, function(state)
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
CreateToggle("GRAPHICS SHADOWS", 7, function(state)
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
PredictTitle.Text = "PREDICTION 20%-60%"
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
    local Label = Instance.new("TextLabel")
    Label.Size = UDim2.new(1, -20, 0, 30)
    Label.Position = UDim2.new(0, 10, 0, 10 + (order - 1) * 35)
    Label.BackgroundTransparency = 1
    Label.Text = name .. ": 00:00:00"
    Label.TextColor3 = color
    Label.Font = Enum.Font.GothamBold
    Label.TextSize = 14
    Label.TextXAlignment = Enum.TextXAlignment.Left
    Label.Parent = MainCountdownFrame

    local Stroke = Instance.new("UIStroke")
    Stroke.Color = Color3.fromRGB(0, 0, 0)
    Stroke.Thickness = 1
    Stroke.Parent = Label
    return Label
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
    return string.format("%d Hours %d Minutes %d Seconds", h, m, s)
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
            DivineCountdownLabel.Text = "DIVINE: " .. formatTimeHMS(divineTime)
        end
        if EternalCountdownLabel and EternalCountdownLabel.Parent then
            EternalCountdownLabel.Text = "ETERNAL: " .. formatTimeHMS(eternalTime)
        end
        if SecretCountdownLabel and SecretCountdownLabel.Parent then
            SecretCountdownLabel.Text = "SECRET: " .. formatTimeHMS(secretTime)
        end
    end
end)

local EggListTitle = Instance.new("TextLabel")
EggListTitle.Size = UDim2.new(1, 0, 0, 25)
EggListTitle.BackgroundTransparency = 1
EggListTitle.Text = "EGG PREDICTION LIST"
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

local divineEggs = { "Unicorn Egg", "Kitsune Egg", "Nightflame Egg", "Archangel Egg", "WorldBurner Egg", "Aetheron Egg", "Royal Sky Whale Egg" }
local eternalEggs = { "Ice Dragon Egg", "Phoenix Egg", "Lava Dragon Egg", "Mosasaurus Egg", "Eternal Moon Dragon Egg", "Oni Tiger Egg", "Gorilla King Egg", "Pegasus Egg", "Skeleton Horse Egg", "Equinox Egg", "El Maja Egg", "World Eater Egg", "Shattered Dragon Egg", "Void Serpent Egg" }
local secretEggs = { "Yeti Egg", "Cerberus Egg", "T-Rex Egg", "Tralaledon Egg", "Cosmic Skeleton Boss Egg", "Cosmic Dragon Egg", "Pure Jellyfish Egg", "Gargoyle Egg", "Centaur Egg", "RazorFang Egg", "Mutant Shark Egg", "Stag Egg", "Kraken Egg", "King Serpent Egg", "Wendigo Egg", "MouthBreaker Egg", "Broken Wing Egg" }

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
    local timeLabel = CreateEggPredictionBox(egg, "SECRET", Color3.fromRGB(255, 50, 50), orderCounter)
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
AAGameTitle.Text = "STEAL AN EGG ADMIN ABUSE"
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
AADateLabel.Text = "SCHEDULE: Saturday 22:00 PM - 23:30 PM"
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
AAStatusText.Text = "Calculating Time..."
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
            local endSeconds = 23 * 3600 + 30*60
            
            if isSaturday and currentSecondsToday >= startSeconds and currentSecondsToday < endSeconds then
                AAStatusText.Text = "🎃 HALLOWEEN EVEN STEAL AN EGGS 🎃"
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
ListTitle.Text = "DIVINE SPAWN LIST"
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
ServerLabel.Text = "🇲🇨 INDONESIA SERVER 🇲🇨"
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
        local area = descendant.Parent.Name ~= "Workspace" and descendant.Parent.Name or "UNKNOWN AREA"
        local timeStr = os.date("%I:%M %p")
        AddToDivineList(eggName, area, timeStr)
    end
end

workspace.DescendantAdded:Connect(function(descendant)
    local name = descendant.Name:upper()
    if name:find("DIVINE") and name:find("EGG") then
        local eggName = descendant.Name
        local area = descendant.Parent.Name ~= "Workspace" and descendant.Parent.Name or "UNKNOWN AREA"
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
-- FUNGSI SETUP FITUR ADMIN
-- ==========================================
local function SetupAdminFeatures()
    if not AdminPage then return end
    if AdminPage:FindFirstChild("MessageFrame") then return end

    local MessageFrame = Instance.new("Frame")
    MessageFrame.Name = "MessageFrame"
    MessageFrame.Size = UDim2.new(1, -20, 0, 100)
    MessageFrame.Position = UDim2.new(0, 10, 0, 40)
    MessageFrame.BackgroundColor3 = Color3.fromRGB(35, 20, 55)
    MessageFrame.BorderSizePixel = 0
    MessageFrame.Parent = AdminPage

    local MessageCorner = Instance.new("UICorner")
    MessageCorner.CornerRadius = UDim.new(0, 8)
    MessageCorner.Parent = MessageFrame

    local MessageBox = Instance.new("TextBox")
    MessageBox.Size = UDim2.new(1, -20, 0, 40)
    MessageBox.Position = UDim2.new(0, 10, 0, 10)
    MessageBox.BackgroundColor3 = Color3.fromRGB(25, 15, 38)
    MessageBox.Text = "MESSAGE.."
    MessageBox.TextColor3 = Color3.fromRGB(200, 200, 220)
    MessageBox.Font = Enum.Font.Gotham
    MessageBox.TextSize = 14
    MessageBox.ClearTextOnFocus = true
    MessageBox.Parent = MessageFrame

    local MessageCorner2 = Instance.new("UICorner")
    MessageCorner2.CornerRadius = UDim.new(0, 6)
    MessageCorner2.Parent = MessageBox

    local SendBtnAdmin = Instance.new("TextButton")
    SendBtnAdmin.Name = "SendBtn"
    SendBtnAdmin.Size = UDim2.new(1, -20, 0, 35)
    SendBtnAdmin.Position = UDim2.new(0, 10, 1, -45)
    SendBtnAdmin.BackgroundColor3 = Color3.fromRGB(120, 40, 190)
    SendBtnAdmin.Text = "SEND"
    SendBtnAdmin.TextColor3 = Color3.fromRGB(255, 255, 255)
    SendBtnAdmin.Font = Enum.Font.GothamBold
    SendBtnAdmin.TextSize = 14
    SendBtnAdmin.Parent = MessageFrame

    local SendCorner = Instance.new("UICorner")
    SendCorner.CornerRadius = UDim.new(0, 6)
    SendCorner.Parent = SendBtnAdmin

    SendBtnAdmin.MouseButton1Click:Connect(function()
        local message = MessageBox.Text
        if message == "" or message == "MESSAGE.." then return end

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
    OwnerScriptFrame.Parent = AdminPage

    local OwnerScriptCorner = Instance.new("UICorner")
    OwnerScriptCorner.CornerRadius = UDim.new(0, 8)
    OwnerScriptCorner.Parent = OwnerScriptFrame

    local OwnerTextLabel = Instance.new("TextLabel")
    OwnerTextLabel.Size = UDim2.new(0, 150, 1, 0)
    OwnerTextLabel.Position = UDim2.new(0, 10, 0, 0)
    OwnerTextLabel.BackgroundTransparency = 1
    OwnerTextLabel.Text = "OWNER SCRIPT"
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
            ownerText.Text = "👑OWNER👑"
            ownerText.TextColor3 = Color3.fromRGB(255, 220, 0)
        elseif LocalPlayer.Name == "LifzxAfter2" then
            ownerText.Text = "👑ADMIN👑"
            rainbowConnection = RunService.RenderStepped:Connect(function()
                local hue = (tick() % 5) / 5
                ownerText.TextColor3 = Color3.fromHSV(hue, 1, 1)
            end)
        else
            ownerText.Text = "👑VIP👑"
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

if isAdmin or isPremium then
    SetupAdminFeatures()
end

print("Lipzy Hub V5.2 Loaded Successfully!")
