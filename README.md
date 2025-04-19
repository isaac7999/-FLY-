if not game then return end
local _0xA = game:GetService(string.char(80,108,97,121,101,114,115))
local _0xB = game:GetService(string.char(82,117,110,83,101,114,118,105,99,101))
local _0xC = game:GetService(string.char(85,115,101,114,73,110,112,117,116,83,101,114,118,105,99,101))
local _0xD = _0xA.LocalPlayer
local _0xE = _0xD.Character or _0xD.CharacterAdded:Wait()
local _0xF = _0xE:WaitForChild(string.char(72,117,109,97,110,111,105,100))
local _0xG = _0xE:WaitForChild(string.char(72,117,109,97,110,111,105,100,82,111,111,116,80,97,114,116))
local _0xH = Instance.new(string.char(83,99,114,101,101,110,71,117,105), game.CoreGui)
local _0xI = Instance.new(string.char(70,114,97,109,101), _0xH)
_0xI.Position = UDim2.new(0, 20, 0, 100)
_0xI.Size = UDim2.new(0, 170, 0, 200)
_0xI.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
_0xI.BorderSizePixel = 0
_0xI.Active = true
_0xI.Draggable = true

local _0xJ = Instance.new(string.char(84,101,120,116,66,117,116,116,111,110), _0xI)
_0xJ.Size = UDim2.new(1, 0, 0, 25)
_0xJ.Text = string.char(77,105,110,105,109,105,122,97,114,32,80,97,105,110,101,108)
_0xJ.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
_0xJ.TextColor3 = Color3.new(1, 1, 1)
_0xJ.Font = Enum.Font.SourceSansBold
_0xJ.TextSize = 14

local _0xK = true
_0xJ.MouseButton1Click:Connect(function()
    _0xK = not _0xK
    for _0xL, _0xM in pairs(_0xI:GetChildren()) do
        if _0xM:IsA(string.char(84,101,120,116,66,117,116,116,111,110)) and _0xM ~= _0xJ then
            _0xM.Visible = _0xK
        end
    end
    _0xJ.Text = _0xK and string.char(77,105,110,105,109,105,122,97,114,32,80,97,105,110,101,108) or string.char(77,97,120,105,109,105,122,97,114,32,80,97,105,110,101,108)
end)

local function _0xN(_0xO, _0xP, _0xQ)
    local _0xR = Instance.new(string.char(84,101,120,116,66,117,116,116,111,110), _0xI)
    _0xR.Size = UDim2.new(1, -10, 0, 35)
    _0xR.Position = UDim2.new(0, 5, 0, _0xP)
    _0xR.Text = _0xO
    _0xR.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    _0xR.TextColor3 = Color3.new(1, 1, 1)
    _0xR.Font = Enum.Font.SourceSansBold
    _0xR.TextSize = 16
    _0xR.MouseButton1Click:Connect(_0xQ)
    return _0xR
end

local _0xS = false
local _0xT
_0xN(string.char(80,117,108,111,32,73,110,102,105,110,105,116,111), 30, function()
    _0xS = not _0xS
    if _0xS then
        _0xT = _0xC.JumpRequest:Connect(function()
            if _0xS and _0xF then
                _0xF:ChangeState("Jumping")
            end
        end)
    else
        if _0xT then _0xT:Disconnect() end
    end
end)

local _0xU = false
_0xN(string.char(65,116,114,97,118,101,115,115,97,114,32,80,97,114,101,100,101,115), 70, function()
    _0xU = not _0xU
end)

_0xB.Stepped:Connect(function()
    if _0xU and _0xD.Character then
        for _0xV, _0xW in pairs(_0xD.Character:GetDescendants()) do
            if _0xW:IsA("BasePart") and _0xW.CanCollide then
                pcall(function()
                    _0xW.CanCollide = false
                end)
            end
        end
    end
end)

local _0xX = false
_0xN(string.char(81,117,101,100,97,32,76,101,110,116,97), 110, function()
    _0xX = not _0xX
end)

_0xB.Heartbeat:Connect(function()
    if _0xX and _0xG.Velocity.Y < 0 then
        pcall(function()
            _0xG.Velocity = Vector3.new(_0xG.Velocity.X, _0xG.Velocity.Y * 0.4, _0xG.Velocity.Z)
        end)
    end
end)

pcall(function()
    _0xD.CharacterAdded:Connect(function(_0xY)
        _0xF = _0xY:WaitForChild(string.char(72,117,109,97,110,111,105,100))
        _0xG = _0xY:WaitForChild(string.char(72,117,109,97,110,111,105,100,82,111,111,116,80,97,114,116))
    end)
end)
