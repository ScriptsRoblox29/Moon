local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
 
 
 local Window = Rayfield:CreateWindow({
     Name = "be a moon",
     Icon = 0, -- Icon in Topbar. Can use Lucide Icons (string) or Roblox Image (number). 0 to use no icon (default).
     LoadingTitle = "Loading...",
     LoadingSubtitle = "by isssacque1234",
     Theme = "Default", -- Check https://docs.sirius.menu/rayfield/configuration/themes
  
     DisableRayfieldPrompts = false,
     DisableBuildWarnings = false, -- Prevents Rayfield from warning when the script has a version mismatch with the interface
  
     ConfigurationSaving = {
        Enabled = true,
        FolderName = skibidi, -- Create a custom folder for your hub/game
        FileName = "skibidi script"
     },
 
  
     KeySystem = true, -- Set this to true to use our key system
     KeySettings = {
        Title = "Key",
        Subtitle = "Key System",
        Note = "https://discord.gg/c4Ctp35FHm", -- Use this to tell the user how to get a key
        FileName = "skibidi key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
        SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
        GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
        Key = {"Key_1000", "Key_7005"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
     }
  }) 
 
 
 
  local mainTab = Window:CreateTab("Main", "crosshair")
 
  local Section = mainTab:CreateSection("Main Settings")
 
 
 local Input = Tab:CreateInput({
   Name = "be a moon",
   CurrentValue = "",
   PlaceholderText = "Enter Player Nickname",
   RemoveTextAfterFocusLost = false,
   Flag = "Input1",
   Callback = function(Text)
       local player = game.Players.LocalPlayer
       local targetPlayer = game.Players:FindFirstChild(Text)

       if targetPlayer and player.Character then
           local humanoidRootPart = player.Character:WaitForChild("HumanoidRootPart")
           local targetChar = targetPlayer.Character
           
           if targetChar then
               local distance = 10

               humanoidRootPart.CFrame = targetChar.HumanoidRootPart.CFrame * CFrame.new(distance, 0, 0)

               while true do
                   local angle = tick() * 2 * math.pi / 10
                   local offset = Vector3.new(math.cos(angle) * distance, 0, math.sin(angle) * distance)
                   humanoidRootPart.CFrame = targetChar.HumanoidRootPart.CFrame * CFrame.new(offset)
                   humanoidRootPart.CFrame = CFrame.lookAt(humanoidRootPart.Position, targetChar.HumanoidRootPart.Position)
                   wait(0.1)
               end
           end
       end
   end,
})
 
 
  Rayfield:Notify({
     Title = "Script by isssacque1234",
     Content = "loaded",
     Duration = 6.5,
     Image = 4483362458,
  })
