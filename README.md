--[[ Hats needed below:
https://www.roblox.com/catalog/5164293775/Tactical-Cyberpunk-Sniper
https://www.roblox.com/catalog/6510043121/Blue-Cyberpunk-Hoverboard
]]--
local character = game.Players.LocalPlayer.Character
local mode = 1


game:GetService('RunService').Heartbeat:Connect(function()
    for i,v in pairs(character:GetChildren()) do
        if v:IsA("BasePart") then
            v.Velocity = Vector3.new(30,0,0)
            v.CFrame = v.CFrame
        end
    end
end)

game:GetService('RunService').Heartbeat:Connect(function()
    for i,v in pairs(character.Humanoid:GetAccessories()) do 
        if not v.Handle:FindFirstChild("AccessoryWeld") then 
            v.Handle.Velocity = Vector3.new(0,35,0)
        end
    end
end)

sethiddenproperty(game.Players.LocalPlayer,"MaximumSimulationRadius",math.huge)
sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",99999999999999999999)
 
-- // Uses Mizt's bypass \\ --
 
Bypass = "death"
loadstring(game:GetObjects("rbxassetid://5325226148")[1].Source)()

e = Instance.new("BodyVelocity",game.Players.LocalPlayer.Character.HumanoidRootPart)
e.Velocity = Vector3.new(0,-27.5,0)
e.P = math.huge
e.MaxForce = Vector3.new(0,3000,0)
 
local playerss = workspace.non

local IsDead = false
local StateMover = true
local bbv,bullet
if Bypass == "death" then
	bullet = game.Players.LocalPlayer.Character["HumanoidRootPart"]
	bullet.Transparency = 0.5
	bullet.Massless = true
	if bullet:FindFirstChildOfClass("Attachment") then
		for _,v in pairs(bullet:GetChildren()) do
			if v:IsA("Attachment") then
				v:Destroy()
			end
		end
	end
	bbv = Instance.new("BodyPosition",bullet)
    bbv.Position = playerss["Right Arm"].CFrame.p
end
 
if Bypass == "death" then
coroutine.wrap(function()
	while true do
		if not playerss or not playerss:FindFirstChildOfClass("Humanoid") or playerss:FindFirstChildOfClass("Humanoid").Health <= 0 then IsDead = true; return end
		if StateMover then
			bbv.Position = playerss["Torso"].CFrame.p
    		bullet.Position = playerss["Torso"].CFrame.p
		end
		game:GetService("RunService").RenderStepped:wait()
	end
end)()
end
 
bbav = Instance.new("BodyAngularVelocity",bullet)
    bbav.MaxTorque = Vector3.new(math.huge,math.huge,math.huge)
    bbav.P = 100000000000000000000000000000
    bbav.AngularVelocity = Vector3.new(10000000000000000000000000000000,100000000000000000000000000,100000000000000000)

gun = true
shoot = false
shoot0 = false
shooting = false

IT = Instance.new
CF = CFrame.new
VT = Vector3.new
RAD = math.rad
C3 = Color3.new
UD2 = UDim2.new
BRICKC = BrickColor.new
ANGLES = CFrame.Angles
EULER = CFrame.fromEulerAnglesXYZ
COS = math.cos
ACOS = math.acos
SIN = math.sin
ASIN = math.asin
ABS = math.abs
MRANDOM = math.random
FLOOR = math.floor

speed = 1
sine = 1
srv = game:GetService('RunService')

reanim = playerss
hum = reanim.Humanoid
RJ = reanim.HumanoidRootPart.RootJoint
RS = reanim.Torso['Right Shoulder']
LS = reanim.Torso['Left Shoulder']
RH = reanim.Torso['Right Hip']
LH = reanim.Torso['Left Hip']
Root = reanim.HumanoidRootPart
NECK = reanim.Torso.Neck
NECK.C0 = CF(0,1,0)*ANGLES(RAD(0),RAD(0),RAD(0))
NECK.C1 = CF(0,-0.5,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RJ.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RJ.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RS.C1 = CF(-0.5,0.5,0)*ANGLES(RAD(0),RAD(0),RAD(0))
LS.C1 = CF(0.5,0.5,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RH.C1 = CF(0,1,0)*ANGLES(RAD(0),RAD(0),RAD(0))
LH.C1 = CF(0,1,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RH.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
LH.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RS.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
LS.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))

m = game.Players.LocalPlayer:GetMouse()

m.Button1Down:Connect(function()
if gun then
shooting = true
gun = false
shoot = true
shoot0 = false
hum.WalkSpeed = 0
wait(.3)
StateMover = false
gun = false
shoot = false
shoot0 = true
wait(.3)
StateMover = true
shooting = false
hum.WalkSpeed = 16
gun = true
shoot = false
shoot0 = false
end

repeat wait() until shooting == true
repeat
game:GetService("RunService").Heartbeat:Wait()
if m.Target ~= nil then
bbv.Position = m.Hit.p
bullet.Position = m.Hit.p
end
until shooting == false
end)

coroutine.wrap(function()
while true do -- anim changer
if HumanDied then break end
sine = sine + speed
if Root.Velocity.y > 1 and gun then -- jump
--jump clerp here
elseif Root.Velocity.y < -1 and gun then -- fall
--fall clerp here
elseif Root.Velocity.Magnitude < 2 and gun and mode == 1 then -- idle
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Arm']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0.7+0*math.cos(sine/13),-2.7+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-90+0*math.cos(sine/13)),RAD(-128+0*math.cos(sine/13)),RAD(90+0*math.cos(sine/13))),1)
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-0+0*math.cos(sine/13)),RAD(14+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+.2*math.cos(sine/15),0+.1*math.cos(sine/13))*ANGLES(RAD(0+2*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),.3+.2*math.cos(sine/14.9),-.2+0*math.cos(sine/13))*ANGLES(RAD(81+0*math.cos(sine/13)),RAD(-11+0*math.cos(sine/13)),RAD(-35+0*math.cos(sine/13))),.4)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),.3+.2*math.cos(sine/14.9),0+0*math.cos(sine/13))*ANGLES(RAD(59+0*math.cos(sine/13)),RAD(30+0*math.cos(sine/13)),RAD(59+0*math.cos(sine/13))),.2)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+-.2*math.cos(sine/15),-1+0*math.cos(sine/13))*ANGLES(RAD(-17+0*math.cos(sine/13)),RAD(-22+0*math.cos(sine/13)),RAD(5+0*math.cos(sine/13))),.2)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+-.2*math.cos(sine/15),-.35+0*math.cos(sine/13))*ANGLES(RAD(-15+0*math.cos(sine/13)),RAD(18+0*math.cos(sine/13)),RAD(-4+0*math.cos(sine/13))),.2)
 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

elseif Root.Velocity.Magnitude < 2 and shoot and mode == 1 then
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Arm']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0.7+0*math.cos(sine/13),-2.7+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-90+0*math.cos(sine/13)),RAD(-128+0*math.cos(sine/13)),RAD(90+0*math.cos(sine/13))),1)
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+.1*math.cos(sine/15),.2+.05*math.cos(sine/13))*ANGLES(RAD(0+2*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),.3+0*math.cos(sine/14.9),-.2+0*math.cos(sine/13))*ANGLES(RAD(81+0*math.cos(sine/13)),RAD(-11+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),.3+0*math.cos(sine/14.9),0+0*math.cos(sine/13))*ANGLES(RAD(81+0*math.cos(sine/13)),RAD(30+0*math.cos(sine/13)),RAD(59+0*math.cos(sine/13))),.2)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+-.1*math.cos(sine/15),-1+0*math.cos(sine/13))*ANGLES(RAD(-33+0*math.cos(sine/13)),RAD(-22+0*math.cos(sine/13)),RAD(5+0*math.cos(sine/13))),.2)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+-.1*math.cos(sine/15),-.35+0*math.cos(sine/13))*ANGLES(RAD(3+0*math.cos(sine/13)),RAD(18+0*math.cos(sine/13)),RAD(-4+0*math.cos(sine/13))),.2)
 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
elseif Root.Velocity.Magnitude < 2 and shoot0 and mode == 1 then
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Arm']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0.7+0*math.cos(sine/13),-2.7+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-90+0*math.cos(sine/13)),RAD(-128+0*math.cos(sine/13)),RAD(90+0*math.cos(sine/13))),1)
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+.1*math.cos(sine/15),.2+.05*math.cos(sine/13))*ANGLES(RAD(0+2*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),.4+0*math.cos(sine/14.9),-.2+0*math.cos(sine/13))*ANGLES(RAD(111+0*math.cos(sine/13)),RAD(-11+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),.3+0*math.cos(sine/14.9),0+0*math.cos(sine/13))*ANGLES(RAD(81+0*math.cos(sine/13)),RAD(30+0*math.cos(sine/13)),RAD(59+0*math.cos(sine/13))),.2)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+-.1*math.cos(sine/15),-1+0*math.cos(sine/13))*ANGLES(RAD(-33+0*math.cos(sine/13)),RAD(-22+0*math.cos(sine/13)),RAD(5+0*math.cos(sine/13))),.2)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+-.1*math.cos(sine/15),-.35+0*math.cos(sine/13))*ANGLES(RAD(3+0*math.cos(sine/13)),RAD(18+0*math.cos(sine/13)),RAD(-4+0*math.cos(sine/13))),.2)
 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
elseif Root.Velocity.Magnitude < 20 and gun and mode == 1 then -- walk
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Arm']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0.7+0*math.cos(sine/13),-2.7+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-90+0*math.cos(sine/13)),RAD(-128+0*math.cos(sine/13)),RAD(90+0*math.cos(sine/13))),1)
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-8+1*math.cos(sine/5)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+.1*math.cos(sine/5),0+0*math.cos(sine/13))*ANGLES(RAD(-7+1*math.cos(sine/5)),RAD(0+5*math.cos(sine/6)),RAD(0+0*math.cos(sine/13))),.15)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),0+.03*math.cos(sine/20),0+0*math.cos(sine/13))*ANGLES(RAD(94+1*math.cos(sine/15.5)),RAD(12+1*math.cos(sine/18.5)),RAD(-64+0*math.cos(sine/13))),.2)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),0+.03*math.cos(sine/20),-.5+0*math.cos(sine/13))*ANGLES(RAD(76+1*math.cos(sine/15.5)),RAD(5+1*math.cos(sine/18.5)),RAD(10+0*math.cos(sine/13))),.2)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+.2*math.cos(sine/5.5),-.2+-.1*math.cos(sine/6))*ANGLES(RAD(-10+40*math.cos(sine/6)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.15)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+-.2*math.cos(sine/5.5),-.2+.1*math.cos(sine/6))*ANGLES(RAD(-10+-40*math.cos(sine/6)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.15)
 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

elseif Root.Velocity.Magnitude < 2 and gun and mode == 2 then -- idle
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Arm']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0.7+0*math.cos(sine/13),-2.7+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-90+0*math.cos(sine/13)),RAD(-128+0*math.cos(sine/13)),RAD(90+0*math.cos(sine/13))),1)
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-0+0*math.cos(sine/13)),RAD(14+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),3+1*math.cos(sine/15),0+.1*math.cos(sine/13))*ANGLES(RAD(0+2*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),.3+.2*math.cos(sine/14.9),-.2+0*math.cos(sine/13))*ANGLES(RAD(149+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.4)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),.3+.2*math.cos(sine/14.9),0+0*math.cos(sine/13))*ANGLES(RAD(-43+0*math.cos(sine/13)),RAD(30+0*math.cos(sine/13)),RAD(59+0*math.cos(sine/13))),.2)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+-.2*math.cos(sine/15),-1+0*math.cos(sine/13))*ANGLES(RAD(-17+0*math.cos(sine/13)),RAD(-22+0*math.cos(sine/13)),RAD(5+0*math.cos(sine/13))),.2)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+-.2*math.cos(sine/15),-.35+0*math.cos(sine/13))*ANGLES(RAD(-15+0*math.cos(sine/13)),RAD(18+0*math.cos(sine/13)),RAD(-4+0*math.cos(sine/13))),.2)
 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

elseif Root.Velocity.Magnitude < 2 and shoot and mode == 2 then
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Arm']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0.7+0*math.cos(sine/13),-2.7+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-90+0*math.cos(sine/13)),RAD(-128+0*math.cos(sine/13)),RAD(90+0*math.cos(sine/13))),1)
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),3+1*math.cos(sine/15),.2+.05*math.cos(sine/13))*ANGLES(RAD(0+2*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),.3+0*math.cos(sine/14.9),-.2+0*math.cos(sine/13))*ANGLES(RAD(81+0*math.cos(sine/13)),RAD(-11+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),.3+0*math.cos(sine/14.9),0+0*math.cos(sine/13))*ANGLES(RAD(81+0*math.cos(sine/13)),RAD(30+0*math.cos(sine/13)),RAD(59+0*math.cos(sine/13))),.2)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+-.1*math.cos(sine/15),-1+0*math.cos(sine/13))*ANGLES(RAD(-33+0*math.cos(sine/13)),RAD(-22+0*math.cos(sine/13)),RAD(5+0*math.cos(sine/13))),.2)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+-.1*math.cos(sine/15),-.35+0*math.cos(sine/13))*ANGLES(RAD(3+0*math.cos(sine/13)),RAD(18+0*math.cos(sine/13)),RAD(-4+0*math.cos(sine/13))),.2)
 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

elseif Root.Velocity.Magnitude < 2 and shoot0 and mode == 2 then
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Arm']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0.7+0*math.cos(sine/13),-2.7+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-90+0*math.cos(sine/13)),RAD(-128+0*math.cos(sine/13)),RAD(90+0*math.cos(sine/13))),1)
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),3+1*math.cos(sine/15),.2+.05*math.cos(sine/13))*ANGLES(RAD(0+2*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),.4+0*math.cos(sine/14.9),-.2+0*math.cos(sine/13))*ANGLES(RAD(111+0*math.cos(sine/13)),RAD(-11+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),.3+0*math.cos(sine/14.9),0+0*math.cos(sine/13))*ANGLES(RAD(81+0*math.cos(sine/13)),RAD(30+0*math.cos(sine/13)),RAD(59+0*math.cos(sine/13))),.2)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+-.1*math.cos(sine/15),-1+0*math.cos(sine/13))*ANGLES(RAD(-33+0*math.cos(sine/13)),RAD(-22+0*math.cos(sine/13)),RAD(5+0*math.cos(sine/13))),.2)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+-.1*math.cos(sine/15),-.35+0*math.cos(sine/13))*ANGLES(RAD(3+0*math.cos(sine/13)),RAD(18+0*math.cos(sine/13)),RAD(-4+0*math.cos(sine/13))),.2)
 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

elseif Root.Velocity.Magnitude < 20 and gun and mode == 2 then -- walk
playerss.Humanoid.WalkSpeed = 51

elseif Root.Velocity.Magnitude > 20 and gun and mode == 2 then -- run
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Arm']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0.7+0*math.cos(sine/13),-2.7+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-90+0*math.cos(sine/13)),RAD(-128+0*math.cos(sine/13)),RAD(90+0*math.cos(sine/13))),1)
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-8+1*math.cos(sine/5)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.2)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+.1*math.cos(sine/5),0+0*math.cos(sine/13))*ANGLES(RAD(-7+1*math.cos(sine/5)),RAD(0+5*math.cos(sine/6)),RAD(0+0*math.cos(sine/13))),.15)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),0+.03*math.cos(sine/20),0+0*math.cos(sine/13))*ANGLES(RAD(94+1*math.cos(sine/15.5)),RAD(12+1*math.cos(sine/18.5)),RAD(-64+0*math.cos(sine/13))),.2)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),.3+.2*math.cos(sine/14.9),0+0*math.cos(sine/13))*ANGLES(RAD(-43+0*math.cos(sine/13)),RAD(30+0*math.cos(sine/13)),RAD(59+0*math.cos(sine/13))),.2)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+.2*math.cos(sine/5.5),-.2+-.1*math.cos(sine/6))*ANGLES(RAD(-10+40*math.cos(sine/6)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.15)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+-.2*math.cos(sine/5.5),-.2+.1*math.cos(sine/6))*ANGLES(RAD(-10+-40*math.cos(sine/6)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.15)
 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)


elseif Root.Velocity.Magnitude < 2 and gun and mode == 3 then -- idle
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0.5+1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),-90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),-90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
LH.C0 = LH.C0:Lerp(CF(0+0*math.cos(sine/13),-90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)


elseif Root.Velocity.Magnitude < 20 and gun and mode == 3 then  --walk
    reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
  
 reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0.5+1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),-90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),-90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
LH.C0 = LH.C0:Lerp(CF(0+0*math.cos(sine/13),-90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)


elseif Root.Velocity.Magnitude < 2 and mode == 4 then --idle
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(-267+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),1+.41*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(-267+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),0.5+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-11+0*math.cos(sine/13)),RAD(-2+0*math.cos(sine/13)),RAD(5+2*math.cos(sine/13))),.1)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),0.5+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(3+0*math.cos(sine/13)),RAD(10+0*math.cos(sine/13)),RAD(-2+2.5*math.cos(sine/13))),.1)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-360+0.3*math.cos(sine/13)),RAD(-6+0*math.cos(sine/13)),RAD(1+0*math.cos(sine/13))),.1)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+0*math.cos(sine/13),-0.5+0*math.cos(sine/13))*ANGLES(RAD(-8+-4*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(-6+0*math.cos(sine/13))),.1)

   reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Leg']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(-0.7+0*math.cos(sine/13),0+0*math.cos(sine/13),1+0*math.cos(sine/13))*ANGLES(RAD(90+0*math.cos(sine/13)),RAD(183+0*math.cos(sine/13)),RAD(1+0*math.cos(sine/13))),.1)
elseif Root.Velocity.Magnitude < 20 and mode == 4 then -- walk

reanim.Humanoid.WalkSpeed = 51

elseif Root.Velocity.Magnitude > 20 and mode == 4 then -- run
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),1+.41*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(-267+0*math.cos(sine/13)),RAD(-13+0*math.cos(sine/13))),.1)
RS.C0 = RS.C0:Lerp(CF(1+0*math.cos(sine/13),0.5+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-11+0*math.cos(sine/13)),RAD(-2+0*math.cos(sine/13)),RAD(5+2*math.cos(sine/13))),.1)
LS.C0 = LS.C0:Lerp(CF(-1+0*math.cos(sine/13),0.5+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(3+0*math.cos(sine/13)),RAD(10+0*math.cos(sine/13)),RAD(-2+2.5*math.cos(sine/13))),.1)
RH.C0 = RH.C0:Lerp(CF(0.5+0*math.cos(sine/13),-1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-360+0.3*math.cos(sine/13)),RAD(-6+0*math.cos(sine/13)),RAD(1+0*math.cos(sine/13))),.1)
LH.C0 = LH.C0:Lerp(CF(-0.5+0*math.cos(sine/13),-1+0*math.cos(sine/13),-0.5+0*math.cos(sine/13))*ANGLES(RAD(-8+-4*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(-6+0*math.cos(sine/13))),.1)

reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.Part1 = reanim['Right Leg']
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/hvboardmeshAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(-0.7+0*math.cos(sine/13),0+0*math.cos(sine/13),1+0*math.cos(sine/13))*ANGLES(RAD(99+0*math.cos(sine/13)),RAD(183+0*math.cos(sine/13)),RAD(1+0*math.cos(sine/13))),.1)

   reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.Part1 = reanim['Torso']
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0 = reanim['Meshes/SniperAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),90+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.1)

end



srv.RenderStepped:Wait()
end
end)()



m.KeyDown:Connect(function(k)
    
    if k == "1" then
    mode = 1
    
    if playerss.Humanoid.WalkSpeed == 51 and mode == 1 then
    playerss.Humanoid.WalkSpeed = 16    
    
    end    
    
    end
    
    if k == "2" then
    mode = 2
    end
    
    if k == "3" then
        
            if playerss.Humanoid.WalkSpeed == 51 and mode == 1 then
    playerss.Humanoid.WalkSpeed = 16    
    
    end
       mode = 3 
    end  
    
    if k == "4" then
        mode = 4
    end    
end)

--Created using Nexo Animator
