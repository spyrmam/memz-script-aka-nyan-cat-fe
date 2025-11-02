if game:GetService("RunService"):IsClient() then error("Script must be server-side in order to work; use h/ and not hl/") end
local Player,game,owner = owner,game
local RealPlayer = Player
do
    print("this shit was made by spyrmam")
    local rp = RealPlayer
    script.Parent = rp.Character

    --RemoteEvent for communicating
    local Event = Instance.new("RemoteEvent")
    Event.Name = "UserInput_Event"

    --Fake event to make stuff like Mouse.KeyDown work
    local function fakeEvent()
        local t = {_fakeEvent=true,Functions={},Connect=function(self,f)table.insert(self.Functions,f) end}
        t.connect = t.Connect
        return t
    end

    --Creating fake input objects with fake variables
    local m = {Target=nil,Hit=CFrame.new(),KeyUp=fakeEvent(),KeyDown=fakeEvent(),Button1Up=fakeEvent(),Button1Down=fakeEvent()}
    local UIS = {InputBegan=fakeEvent(),InputEnded=fakeEvent()}
    local CAS = {Actions={},BindAction=function(self,name,fun,touch,...)
        CAS.Actions[name] = fun and {Name=name,Function=fun,Keys={...}} or nil
    end}
    --Merged 2 functions into one by checking amount of arguments
    CAS.UnbindAction = CAS.BindAction

    --This function will trigger the events that have been :Connect()'ed
    local function te(self,ev,...)
        local t = m[ev]
        if t and t._fakeEvent then
            for _,f in pairs(t.Functions) do
                f(...)
            end
        end
    end
    m.TrigEvent = te
    UIS.TrigEvent = te

    Event.OnServerEvent:Connect(function(plr,io)
        if plr~=rp then return end
        m.Target = io.Target
        m.Hit = io.Hit
        if not io.isMouse then
            local b = io.UserInputState == Enum.UserInputState.Begin
            if io.UserInputType == Enum.UserInputType.MouseButton1 then
                return m:TrigEvent(b and "Button1Down" or "Button1Up")
            end
            for _,t in pairs(CAS.Actions) do
                for _,k in pairs(t.Keys) do
                    if k==io.KeyCode then
                        t.Function(t.Name,io.UserInputState,io)
                    end
                end
            end
            m:TrigEvent(b and "KeyDown" or "KeyUp",io.KeyCode.Name:lower())
            UIS:TrigEvent(b and "InputBegan" or "InputEnded",io,false)
        end
    end)
    Event.Parent = NLS([==[
    local Player = game:GetService("Players").LocalPlayer
    local Event = script:WaitForChild("UserInput_Event")

    local Mouse = Player:GetMouse()
    local UIS = game:GetService("UserInputService")
    local input = function(io,a)
        if a then return end
        --Since InputObject is a client-side instance, we create and pass table instead
        Event:FireServer({KeyCode=io.KeyCode,UserInputType=io.UserInputType,UserInputState=io.UserInputState,Hit=Mouse.Hit,Target=Mouse.Target})
    end
    UIS.InputBegan:Connect(input)
    UIS.InputEnded:Connect(input)

    local h,t
    --Give the server mouse data 30 times every second, but only if the values changed
    --If player is not moving their mouse, client won't fire events
    while wait(1/30) do
        if h~=Mouse.Hit or t~=Mouse.Target then
            h,t=Mouse.Hit,Mouse.Target
            Event:FireServer({isMouse=true,Target=t,Hit=h})
        end
    end]==],Player.Character)

    ----Sandboxed game object that allows the usage of client-side methods and services
    --Real game object
    local _rg = game

    --Metatable for fake service
    local fsmt = {
        __index = function(self,k)
            local s = rawget(self,"_RealService")
            if s then return s[k] end
        end,
        __newindex = function(self,k,v)
            local s = rawget(self,"_RealService")
            if s then s[k]=v end
        end,
        __call = function(self,...)
            local s = rawget(self,"_RealService")
            if s then return s(...) end
        end
    }
    local function FakeService(t,RealService)
        t._RealService = typeof(RealService)=="string" and _rg:GetService(RealService) or RealService
        return setmetatable(t,fsmt)
    end

    --Fake game object
    local g = {
        GetService = function(self,s)
            return self[s]
        end,
        Players = FakeService({
            LocalPlayer = FakeService({GetMouse=function(self)return m end},Player)
        },"Players"),
        UserInputService = FakeService(UIS,"UserInputService"),
        ContextActionService = FakeService(CAS,"ContextActionService"),
    }
    rawset(g.Players,"localPlayer",g.Players.LocalPlayer)
    g.service = g.GetService

    g.RunService = FakeService({
        RenderStepped = _rg:GetService("RunService").Heartbeat,
        BindToRenderStep = function(self,name,_,fun)
            self._btrs[name] = self.Heartbeat:Connect(fun)
        end,
        UnbindFromRenderStep = function(self,name)
            self._btrs[name]:Disconnect()
        end,
    },"RunService")

    setmetatable(g,{
        __index=function(self,s)
            return _rg:GetService(s) or typeof(_rg[s])=="function"
            and function(_,...)return _rg[s](_rg,...)end or _rg[s]
        end,
        __newindex = fsmt.__newindex,
        __call = fsmt.__call
    })
    --Changing owner to fake player object to support owner:GetMouse()
    game,owner = g,g.Players.LocalPlayer
end
-- Go to line 5 and change it to your name. LOCAL SCRIPT!!!!!


Rainbow = {"Bright red", "Neon orange", "Bright yellow", "Lime green", "Deep blue", "Bright violet"}
me = game.Players.LocalPlayer
function Part(P, Anch, Coll, Tran, Ref, Col, Size, Name)
local p = Instance.new("Part")
p.TopSurface = 0
p.BottomSurface = 0
p.Transparency = Tran
p.Reflectance = Ref
p.CanCollide = Coll
p.Anchored = Anch
p.BrickColor = BrickColor.new(Col)
p.formFactor = "Custom"
p.Size = Size
if Name then p.Name = Name end
p.Parent = P
p.Locked = true
p:BreakJoints()
return p
end
V3 = Vector3.new
CN = CFrame.new
CA = CFrame.Angles
MR = math.rad
MRA = math.random
function Weld(P0, P1, CF1, CF2, Name)
local w = Instance.new("Motor6D")
w.Part0 = P0
w.Part1 = P1
w.C0 = CF1
w.C1 = CF2
if Name then w.Name = Name end
w.Parent = P0
return w
end
function MakeNyan(Player, S)
local Naim = "Nyan "..Player.Name:sub(1,5)
if S >= 5 then Naim = "Giant Nyan "..Player.Name:sub(1,5) end
local Model = Instance.new("Model")
Model.Name = Naim
local Torso = Part(Model, false, false, 0, 0, "Brick yellow", V3(0.5*S, 1.5*S, 2*S), "Torso")
local Head = Part(Model, false, false, 0, 0, "Dark grey", V3(0.6*S, 0.8*S, 1.2*S), "Head")
Instance.new("BlockMesh",Head)
local Neck = Weld(Torso, Head, CN(0, -0.35*S, -0.9*S), CN(), "Neck")
local Tart = Part(Model, false, false, 0, 0, "Pink", V3(0.5*S+0.05, 1.2*S, 1.7*S), "Torso")
Instance.new("BlockMesh",Tart)
Weld(Torso, Tart, CN(), CN())
local RFL = Part(Model, false, false, 0, 0, "Dark grey", V3(0.4*S, 0.6*S, 0.4*S), "Right Arm")
Instance.new("SpecialMesh",RFL).MeshType = "Sphere"
local LFL = Part(Model, false, false, 0, 0, "Dark grey", V3(0.4*S, 0.6*S, 0.4*S), "Left Arm")
Instance.new("SpecialMesh",LFL).MeshType = "Sphere"
local RBL = Part(Model, false, false, 0, 0, "Dark grey", V3(0.4*S, 0.6*S, 0.4*S), "Right Leg")
Instance.new("SpecialMesh",RBL).MeshType = "Sphere"
local LBL = Part(Model, false, false, 0, 0, "Dark grey", V3(0.4*S, 0.6*S, 0.4*S), "Left Leg")
Instance.new("SpecialMesh",LBL).MeshType = "Sphere"
local RSH = Weld(Torso, RFL, CN(), CN(-0.1*S, 0.8*S, 0.8*S), "Right Shoulder")
local LSH = Weld(Torso, LFL, CN(), CN(0.1*S, 0.8*S, 0.6*S), "Left Shoulder")
local RH = Weld(Torso, RBL, CN(), CN(-0.1*S, 0.8*S, -0.8*S), "Right Hip")
local LH = Weld(Torso, LBL, CN(), CN(0.1*S, 0.8*S, -1*S), "Left Hip")
local Mouth = Part(Model, false, false, 0, 0, "Really black", V3(0.6*S+0.05, 0.2*S, 0.6*S))
Weld(Head, Mouth, CN(0, -0.25*S, -0.1), CN())
Instance.new("BlockMesh",Mouth).Scale = V3(1, 0.6, 0.8)
for i = -0.25, 0.25, 0.25 do
local Mouth2 = Part(Model, false, false, 0, 0, "Really black", V3(0.6*S+0.05, 0.3*S, 0.2*S))
Weld(Mouth, Mouth2, CN(0, 0.1*S, i*S), CN())
Instance.new("BlockMesh",Mouth2).Scale = V3(1, 0.6, 0.6)
end
local Nose = Part(Model, false, false, 0, 0, "Really black", V3(0.6*S+0.05, 0.2*S, 0.2*S))
Weld(Head, Nose, CN(0, 0.05*S, -0.1*S), CN())
Instance.new("BlockMesh",Nose).Scale = V3(1, 0.6, 0.6)
for i = -0.3, 0.31, 0.6 do
local Eye = Part(Model, false, false, 0, 0, "Really black", V3(0.6*S+0.05, 0.3*S, 0.3*S))
Weld(Head, Eye, CN(0, 0.15*S, (i-0.1)*S), CN())
local Eye2 = Part(Model, false, false, 0, 0, "Institutional white", V3(0.6*S+0.1, 0.2*S, 0.2*S))
Weld(Eye, Eye2, CN(0, 0.04*S, 0.04*S), CN())
Instance.new("BlockMesh",Eye).Scale = V3(1, 0.6, 0.6)
Instance.new("BlockMesh",Eye2).Scale = V3(1, 0.4, 0.4)
end
for i = -0.4, 0.5, 0.9 do
local Cheek = Part(Model, false, false, 0, 0, "Medium red", V3(0.6*S+0.05, 0.2*S, 0.2*S))
Instance.new("BlockMesh",Cheek).Scale = V3(1, 0.8, 0.8)
Weld(Head, Cheek, CN(0, -0.05*S, (i-0.1)*S), CN())
end
for i = -80, -140, -20 do
local tail = Part(Model, false, false, 0, 0, "Dark grey", V3(0.4*S, 0.25*S, 0.3*S))
Weld(Torso, tail, CN(0, 0.2*S, 1.15*S) * CA(MR(i), 0, 0), CN(0, 0, 0.5*S))
Instance.new("BlockMesh",tail)
end
for i = 0, 180, 180 do
local ear = Part(Model, false, false, 0, 0, "Dark grey", V3(0.6*S, 0.4*S, 0.5*S))
Instance.new("SpecialMesh",ear).MeshType = "Wedge"
Weld(Head, ear, CN(0, 0.45*S, 0) * CA(0, MR(i), 0), CN(0, 0, -0.32*S) * CA(MR(15), 0, 0))
end
local Hum = Instance.new("Humanoid")
Hum.Name = "Humanoid"
Hum.MaxHealth = 100
Hum.Health = 100
Hum.WalkSpeed = 11+(5*S)
Hum.Parent = Model
Model.Parent = workspace
Model:MakeJoints()
Model:MoveTo(V3(0, 2*S, 0))
Player.Character = Model
local lastP = (Torso.CFrame * CN(0, 0, 0.9*S)).p
local function runn()
for i = 0.5, 1, 0.5 do
RSH.C0 = CN(0, -(0.2*S)*i, 0)
LSH.C0 = CN(0, -(0.2*S)*i, 0)
RH.C0 = CN(0, -(0.2*S)*i, 0)
LH.C0 = CN(0, -(0.2*S)*i, 0)
wait()
end
for i = 0.5, 1, 0.5 do
RSH.C0 = CN(0, -(0.2*S), (0.2*S)*i)
LSH.C0 = CN(0, -(0.2*S), (0.2*S)*i)
RH.C0 = CN(0, -(0.2*S), (0.2*S)*i)
LH.C0 = CN(0, -(0.2*S), (0.2*S)*i)
wait()
end
for i = 0.5, 1, 0.5 do
RSH.C0 = CN(0, -(0.2*S)+(0.2*S)*i, (0.2*S))
LSH.C0 = CN(0, -(0.2*S)+(0.2*S)*i, (0.2*S))
RH.C0 = CN(0, -(0.2*S)+(0.2*S)*i, (0.2*S))
LH.C0 = CN(0, -(0.2*S)+(0.2*S)*i, (0.2*S))
wait()
end
for i = 0.5, 1, 0.5 do
RSH.C0 = CN(0, 0, (0.2*S)-(0.2*S)*i)
LSH.C0 = CN(0, 0, (0.2*S)-(0.2*S)*i)
RH.C0 = CN(0, 0, (0.2*S)-(0.2*S)*i)
LH.C0 = CN(0, 0, (0.2*S)-(0.2*S)*i)
wait()
end
end
local poss = "Standing"
coroutine.resume(coroutine.create(function()
while Player.Character == Model do
wait(0.1)
if poss == "Running" then
runn()
end
end
end))
coroutine.resume(coroutine.create(function()
while Player.Character == Model do
wait(0.1)
local speed = Torso.Velocity.magnitude
local posnow = (Torso.CFrame * CN(0, 0, 0.9*S)).p
coroutine.resume(coroutine.create(function()
if speed > 2 then
poss = "Running"
local ps = {}
for i,v in pairs(Rainbow) do
local a = (#Rainbow-i)
a = ((a-(a/2))/2.5)*S
local pp = Part(Model, true, false, 0, 0, v, V3(0.2, 0.2, 0.2), "Rainbow")
local dist = (posnow - lastP).magnitude
Instance.new("BlockMesh",pp).Scale = V3(1, ((1.4*S)/#Rainbow)*5, dist*5)
pp.CFrame = CN(lastP, posnow) * CN(0, a, -dist/2)
table.insert(ps, pp)
end
coroutine.resume(coroutine.create(function()
wait(10)
for i = 0, 1, 0.2 do
wait()
for _,v in pairs(ps) do
v.Transparency = i
end
end
for _,v in pairs(ps) do
v:remove()
end
end))
else poss = "Standing" end
end))
lastP = posnow
end
end))
end
for i,v in pairs(game.Players:GetPlayers()) do
MakeNyan(v, MRA(10,120)/10)
end
