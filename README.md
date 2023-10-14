            local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
            local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
            local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()
            
            local Window = Fluent:CreateWindow({
                Title = "Bit Hub",
                SubTitle = "Premium",
                TabWidth = 160,
                Size = UDim2.fromOffset(580, 390),
                Acrylic = false, -- The blur may be detectable, setting this to false disables blur entirely
                Theme = "Dark",
                MinimizeKey = Enum.KeyCode.RightControl -- Used when theres no MinimizeKeybind
            })
            
            --Fluent provides Lucide Icons https://lucide.dev/icons/ for the tabs, icons are optional
            local Tabs = {
                Main = Window:AddTab({ Title = "Main", Icon = "file-text" }),
                Funny = Window:AddTab({ Title = "Funny", Icon = "focus" }),
                Player = Window:AddTab({ Title = "Player", Icon = "user" }),
                Misc = Window:AddTab({ Title = "Misc", Icon = "book" }),
                Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
            }
            
            local loadstring, getgenv, setclipboard, tablefind, UserInputService = loadstring, getgenv, setclipboard, table.find, game:GetService("UserInputService")
            local runService = game:GetService("RunService")
            local workspace = game:GetService("Workspace")
            local players = game:GetService("Players")
            local localPlayer = players.LocalPlayer
            local character = localPlayer.Character or localPlayer.CharacterAdded:Wait()
            local ballsFolder = workspace:WaitForChild("Balls")
            local abilitiesFolder = character:WaitForChild("Abilities")
            local UserInputService = game:GetService("UserInputService")
            local replicatedStorage = game:GetService("ReplicatedStorage")
            local heartbeatConnection
            local upgrades = localPlayer.Upgrades
            local isRunning = false
            local UseRage = false
            local UseRapture = false
            local sliderValue = 20
            local ggdebounce = false
            local focusedBall, displayBall = nil, nil
            local parryButtonPress = replicatedStorage.Remotes.ParryButtonPress
            local abilityButtonPress = replicatedStorage.Remotes.AbilityButtonPress
            
            local function onCharacterAdded(newCharacter)
                character = newCharacter
                abilitiesFolder = character:WaitForChild("Abilities")
            end
            
            localPlayer.CharacterAdded:Connect(onCharacterAdded)
            
            local TruValue = Instance.new("StringValue")
            if workspace:FindFirstChild("AbilityThingyk1212") then
                workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                task.wait(0.1)
                TruValue.Parent = game:GetService("Workspace")
                    TruValue.Name = "AbilityThingyk1212"
                    TruValue.Value = "Dash" --Change to Use other ability
                else
                    TruValue.Parent = game:GetService("Workspace")
                    TruValue.Name = "AbilityThingyk1212"
                    TruValue.Value = "Dash" --Change to Use other ability
            end
            
            local Options = Fluent.Options
            
            do
                Fluent:Notify({
                    Title = "Notification",
                    Content = "This is a notification",
                    SubContent = "SubContent", -- Optional
                    Duration = 5 -- Set to nil to make the notification not disappear
                })
            
                Tabs.Main:AddButton({
                    Title = "Auto Parry เเนะนำให้เปิดกับตัว Auto Parry Duo)",
                    Description = "เเนะนำเปิดกับ Auto Parry Duo",
                    Callback = function()
                        Window:Dialog({
                            Title = "จะเปิดหรือไม่",
                            Content = "",
                            Buttons = {
                                {
                                    Title = "เปิด",
                                    Callback = function()
                                        getgenv().visualizer = true
                                        loadstring(game:HttpGet("https://raw.githubusercontent.com/1f0yt/community/main/RedCircleBlock"))()
                                    end
                                },
                                {
                                    Title = "ไม่",
                                    Callback = function()
                                        print("Cancelled the dialog.")
                                    end
                                }
                            }
                        })
                    end
                })
            
                Tabs.Main:AddButton({
                    Title = "Auto Parry Duo (เเนะนำให้เปิดกับตัว Auto Parry)",
                    Description = "เเนะนำเปิดกับ Auto Parry",
                    Callback = function()
                        Window:Dialog({
                            Title = "จะเปิดหรือไม่",
                            Content = "",
                            Buttons = {
                                {
                                    Title = "เปิด",
                                    Callback = function()
                                        loadstring(game:HttpGet("https://raw.githubusercontent.com/Hosvile/Refinement/main/MC%3ABlade%20Ball%20Parry",true))()
                                    end
                                },
                                {
                                    Title = "ไม่",
                                    Callback = function()
                                        print("Cancelled the dialog.")
                                    end
                                }
                            }
                        })
                    end
                })
            
                Tabs.Main:AddButton({
                    Title = "Auto Win (Risk) มุดดินไปหาใจเธอ",
                    Description = "เสี่ยงโดนเเบน",
                    Callback = function()
                        Window:Dialog({
                            Title = "จะเปิดหรือไม่",
                            Content = "เสี่ยงโดนเเบน",
                            Buttons = {
                                {
                                    Title = "เปิด",
                                    Callback = function()
                                        loadstring(game:HttpGet("https://raw.githubusercontent.com/TaraxNight/esadasd/main/README.md"))()
                                    end
                                },
                                {
                                    Title = "ไม่",
                                    Callback = function()
                                        print("Cancelled the dialog.")
                                    end
                                }
                            }
                        })
                    end
                })
            
                Tabs.Main:AddButton({
                    Title = "Spam Mobile / Pc",
                    Description = "ใช้ได้ทั้ง มือถือ คอม",
                    Callback = function()
                        Window:Dialog({
                            Title = "จะเปิดหรือไม่",
                            Content = "",
                            Buttons = {
                                {
                                    Title = "เปิด",
                                    Callback = function()
                                        local gui = Instance.new("ScreenGui")
                                        gui.ResetOnSpawn = false
                                        gui.Parent = game.CoreGui
                                        
                                        local frame = Instance.new("Frame")
                                        frame.Position = UDim2.new(0, 20, 0, 20)
                                        frame.Size = UDim2.new(0, 100, 0, 50)
                                        frame.BackgroundColor3 = Color3.new(0, 0, 0)
                                        frame.BorderSizePixel = 0
                                        frame.Parent = gui
                                        
                                        local button = Instance.new("TextButton")
                                        button.Text = "OFF"
                                        button.Size = UDim2.new(1, -10, 1, -10)
                                        button.Position = UDim2.new(0, 10, 0, 10)
                                        button.BackgroundColor3 = Color3.new(1, 1, 1)
                                        button.BorderColor3 = Color3.new(0, 0, 0)
                                        button.BorderSizePixel = 2
                                        button.Font = Enum.Font.SourceSans
                                        button.TextColor3 = Color3.new(0, 0, 0)
                                        button.TextSize = 16
                                        button.Parent = frame
                                        
                                        local activated = false
                                        
                                        local function toggle()
                                          activated = not activated
                                          button.Text = activated and "ON" or "OFF"
                                          while activated do
                                            local args = {
                                              [1] = 1.5,
                                              [2] = CFrame.new(-254.2939910888672, 112.13581848144531, -119.27256774902344) * CFrame.Angles(-2.029526710510254, 0.5662040710449219, 2.314905881881714),
                                              [3] = {
                                                ["2617721424"] = Vector3.new(-273.400146484375, -724.8031005859375, -20.92414093017578),
                                              },
                                              [4] = {
                                                [1] = 910,
                                                [2] = 154
                                              }
                                            }
                                            game:GetService("ReplicatedStorage").Remotes.ParryAttempt:FireServer(unpack(args))
                                            game:GetService("RunService").Heartbeat:Wait(0.000001)
                                          end
                                        end
                                        
                                        button.MouseButton1Click:Connect(toggle)
                                        
                                        -- Adicionar keybind "E" para ativar o botão
                                        local UserInputService = game:GetService("UserInputService")
                                        local xKeyPressed = false
                                        
                                        UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
                                          if input.KeyCode == Enum.KeyCode.X and not gameProcessedEvent then
                                            xKeyPressed = false
                                            toggle()
                                          end
                                        end)
                                        
                                        UserInputService.InputEnded:Connect(function(input, gameProcessedEvent)
                                          if input.KeyCode == Enum.KeyCode.X then
                                            xKeyPressed = true
                                          end
                                        end)
                                    end
                                },
                                {
                                    Title = "ไม่",
                                    Callback = function()
                                        print("Cancelled the dialog.")
                                    end
                                }
                            }
                        })
                    end
                })
            end
            
            ----------------------------------------------------------------------------------------------
            
            local Toggle = Tabs.Funny:AddToggle("Freezeball", {Title = "Stop Ball (ต้องมีสกิลเเข็ง / Freeze)", Default = false })
            
            Toggle:OnChanged(function(Value)
                Freezeball = Value
            
                while Freezeball do wait()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                end
            end)
            
            Options.Freezeball:SetValue(false)
            
            ----------------------------------------------------------------------------------------------
            
            local Toggle = Tabs.Funny:AddToggle("Serverlag", {Title = "Lag Server (ต้องมีสกิลเเข็ง / Freeze)", Default = false })
            
            function FireFreezeRemote()
                if game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze") then
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Freeze"):FireServer()
                end
            end
            
            Toggle:OnChanged(function(Value)
                Serverlag = Value
            
                while Serverlag do
                    for _ = 1, 10 do
                        FireFreezeRemote()
                    end
                end
            end)
            
            Options.Serverlag:SetValue(false)
            
            ----------------------------------------------------------------------------------------------
            local Toggle = Tabs.Player:AddToggle("nightmode", {Title = "Night Mode", Default = false })
            
            local SetTimeOfDay = function(timeOfDay)
                game.Lighting.TimeOfDay = timeOfDay
            end
            
            Toggle:OnChanged(function(value)
                if value then
                    SetTimeOfDay(1)
                else
                    SetTimeOfDay(12)
                end
            end)
            
            Options.nightmode:SetValue(false)
            ----------------------------------------------------------------------------------------------
            
            local Slider = Tabs.Player:AddSlider("Slider", {
                Title = "Walk Speed",
                Description = "วิ่งไว",
                Default = 30,
                Min = 30,
                Max = 300,
                Rounding = 1,
                Callback = function(Value)
                    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
                end
            })
            
            Slider:OnChanged(function(Value)
                print("Slider changed:", Value)
            end)
            
            Slider:SetValue(3)
            
            ----------------------------------------------------------------------------------------------
            
            local Slider = Tabs.Player:AddSlider("Slider", {
                Title = "Fov",
                Description = "มุมมอง",
                Default = 80,
                Min = 80,
                Max = 120,
                Rounding = 1,
                Callback = function(Value)
                    game.workspace.CurrentCamera.FieldOfView = Value
                end
            })
            
            Slider:OnChanged(function(Value)
                print("Slider changed:", Value)
            end)
            
            Slider:SetValue(3)
            
            ----------------------------------------------------------------------------------------------
            
            Tabs.Player:AddButton({
                Title = "Changer Name",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปิดหรือไม่",
                        Content = "",
                        Buttons = {
                            {
                                Title = "เปิด",
                                Callback = function()
                                    loadstring(game:HttpGet("https://raw.githubusercontent.com/ToukaKung/spoofer-name/main/spoofer", true))()
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Player:AddButton({
                Title = "Anti Lag",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปิดหรือไม่",
                        Content = "",
                        Buttons = {
                            {
                                Title = "เปิด",
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
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Player:AddButton({
                Title = "Anti Afk",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปิดหรือไม่",
                        Content = "",
                        Buttons = {
                            {
                                Title = "เปิด",
                                Callback = function()
                                    local ba = Instance.new("ScreenGui")
                                    local ca = Instance.new("TextLabel")
                                    local da = Instance.new("Frame")
                                    local _b = Instance.new("TextLabel")
                                    local ab = Instance.new("TextLabel")
                                    
                                    ba.Parent = game.CoreGui
                                    ba.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
                                    ca.Parent = ba
                                    ca.Active = true
                                    ca.BackgroundColor3 = Color3.fromRGB(166, 147, 203) -- สีม่วง (RGB: 166, 147, 203)
                                    ca.Draggable = true
                                    ca.Position = UDim2.new(0.698610067, 0, 0.098096624, 0)
                                    ca.Size = UDim2.new(0, 200, 0, 50)
                                    ca.Font = Enum.Font.SourceSansSemibold
                                    ca.Text = "Anti Afk"
                                    ca.TextColor3 = Color3.new(1, 1, 1) -- สีขาว
                                    ca.TextSize = 22
                                    
                                    da.Parent = ca
                                    da.BackgroundColor3 = Color3.fromRGB(166, 147, 203) -- สีม่วง (RGB: 166, 147, 203)
                                    da.Position = UDim2.new(0, 0, 1.0192306, 0)
                                    da.Size = UDim2.new(0, 200, 0, 50)
                                     
                                    _b.Parent = da
                                    _b.BackgroundColor3 = Color3.fromRGB(166, 147, 203) -- สีม่วง (RGB: 166, 147, 203)
                                    _b.Position = UDim2.new(0, 0, 0.800455689, 0)
                                    _b.Size = UDim2.new(0, 200, 0, 50)
                                    _b.Font = Enum.Font.Arial
                                    _b.Text = "Made by BitHub"
                                    _b.TextColor3 = Color3.new(1, 1, 1) -- สีขาว
                                    _b.TextSize = 20
                                    
                                    ab.Parent = da
                                    ab.BackgroundColor3 = Color3.fromRGB(166, 147, 203) -- สีม่วง (RGB: 166, 147, 203)
                                    ab.Position = UDim2.new(0, 0, 0.158377, 0)
                                    ab.Size = UDim2.new(0, 200, 0, 30)
                                    ab.Font = Enum.Font.ArialBold
                                    ab.Text = "Status: Active"
                                    ab.TextColor3 = Color3.new(1, 1, 1) -- สีขาว
                                    ab.TextSize = 20
                                    
                                    local bb = game:service('VirtualUser')
                                    game:service('Players').LocalPlayer.Idled:connect(function()
                                        bb:CaptureController()
                                        bb:ClickButton2(Vector2.new())
                                        ab.Text = "Roblox kicked you but we didnt let them!"
                                        wait(2)
                                        ab.Text = "Status : Active"
                                    end)
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            ----------------------------------------------------------------------------------------------
            
            Tabs.Misc:AddParagraph({
                Title = "Emotes",
                Content = ""
            })
            
            Tabs.Misc:AddButton({
                Title = "Gamepass Emote Effect + Music ( Press R )",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปิดหรือไม่",
                        Content = "",
                        Buttons = {
                            {
                                Title = "เปิด",
                                Callback = function()
                                    character:FindFirstChildOfClass("Model").Name = "Empyrean Greatblade"
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Gamepass Emote Effect + Music ( Press R ) New",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปิดหรือไม่",
                        Content = "",
                        Buttons = {
                            {
                                Title = "เปิด",
                                Callback = function()
                                    character:FindFirstChildOfClass("Model").Name = "Wavelight Greatblade"
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddParagraph({
                Title = "------------------------------------------------------------",
                Content = "Abilities"
            })
            
            Tabs.Misc:AddButton({
                Title = "Dash",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Dash"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                    
                                        local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Dash" --Change to Use other ability
                                    
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Super Jump",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Super Jump"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Super Jump" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Platform",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Platform"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Platform" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Invisibility",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Invisibility"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Invisibility" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Thunder Dash",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Thunder Dash"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Thunder Dash" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Shadow Step",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Shadow Step"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Shadow Step" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Wind Cloak",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Wind Cloak"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Wind Cloak" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Freeze",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Freeze"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Freeze" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Forcefield",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Forcefield"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Forcefield" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Swap",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Swap"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Swap" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Raging Deflection",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Raging Deflection"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Raging Deflection" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Reaper",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Reaper"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Reaper" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Telekinesis",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Telekinesis"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Telekinesis" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Pull",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Pull"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Pull" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Phase Bypass",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Phase Bypass"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Phase Bypass" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Rapture",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Rapture"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Rapture" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "Waypoint",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Waypoint"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Waypoint" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            Tabs.Misc:AddButton({
                Title = "infinity",
                Description = "",
                Callback = function()
                    Window:Dialog({
                        Title = "จะเปลื่ยนสกิวใช่มั้ย",
                        Content = "",
                        Buttons = {
                            {
                                Title = "ใช่",
                                Callback = function()
                                    local args = {
                                        [1] = "Infinity"
                                    }
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.RequestEquipAbility:InvokeServer(unpack(args))
                                    
                                    game:GetService("ReplicatedStorage").Remotes.Store.GetOwnedAbilities:InvokeServer()
                                    
                                    game:GetService("ReplicatedStorage").Remotes.kebaind:FireServer()
                                                
                                    local function AbilityValue2()
                                    local TruValue = Instance.new("StringValue")
                                    workspace:FindFirstChild("AbilityThingyk1212"):Remove()
                                            TruValue.Parent = game:GetService("Workspace")
                                            TruValue.Name = "AbilityThingyk1212"
                                            TruValue.Value = "Infinity" --Change to Use other ability
                                    end
                                    
                                    for i,v in pairs(abilitiesFolder:GetChildren()) do
                                    
                                    
                                    for i,b in pairs(abilitiesFolder:GetChildren()) do
                                        local Ability = b
                                        
                                        if v.Enabled == true then
                                            local EquippedAbility = v
                                            local ChosenAbility = {}
                                            spawn(function()
                                            ChosenAbility = AbilityValue2()
                                        end)
                                    
                                        task.wait(0.05)
                                            local AbilityValue = workspace.AbilityThingyk1212
                                            if b.Name == AbilityValue.Value then
                                    
                                                v.Enabled = false
                                                b.Enabled = true
                                        end
                                    end
                                    end
                                    end
                                end
                            },
                            {
                                Title = "ไม่",
                                Callback = function()
                                    print("Cancelled the dialog.")
                                end
                            }
                        }
                    })
                end
            })
            
            -- Hand the library over to our managers
            SaveManager:SetLibrary(Fluent)
            InterfaceManager:SetLibrary(Fluent)
            
            -- Ignore keys that are used by ThemeManager.
            -- (we dont want configs to save themes, do we?)
            SaveManager:IgnoreThemeSettings()
            
            -- You can add indexes of elements the save manager should ignore
            SaveManager:SetIgnoreIndexes({})
            
            -- use case for doing it this way:
            -- a script hub could have themes in a global folder
            -- and game configs in a separate folder per game
            InterfaceManager:SetFolder("FluentScriptHub")
            SaveManager:SetFolder("FluentScriptHub/specific-game")
            
            InterfaceManager:BuildInterfaceSection(Tabs.Settings)
            SaveManager:BuildConfigSection(Tabs.Settings)
            
            
            Window:SelectTab(1)
            
            Fluent:Notify({
                Title = "Fluent",
                Content = "The script has been loaded.",
                Duration = 8
            })
            
            -- You can use the SaveManager:LoadAutoloadConfig() to load a config
            -- which has been marked to be one that auto loads!
            SaveManager:LoadAutoloadConfig()
