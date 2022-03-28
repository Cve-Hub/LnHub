if not game:IsLoaded() then 

    repeat game.Loaded:wait(0.2) 

        wait(10)

    until game:IsLoaded() 

end

-----------------------------------------

	do  local ui =  game:GetService("CoreGui"):FindFirstChild("redui")  if ui then ui:Destroy() end end

	local UserInputService = game:GetService("UserInputService")

	local TweenService = game:GetService("TweenService")

	local RunService = game:GetService("RunService")

	local LocalPlayer = game:GetService("Players").LocalPlayer

	local Mouse = LocalPlayer:GetMouse()

	local tween = game:GetService("TweenService")

	local Red = {RainbowColorValue = 0, HueSelectionPosition = 0}

	local PresetColor = Color3.fromRGB(66, 134, 255)

	coroutine.wrap(

		function()

			while wait(0.2) do

				Red.RainbowColorValue = Red.RainbowColorValue + 1 / 255

				Red.HueSelectionPosition = Red.HueSelectionPosition + 1

				if Red.RainbowColorValue >= 1 then

					Red.RainbowColorValue = 0

				end

				if Red.HueSelectionPosition == 160 then

					Red.HueSelectionPosition = 0

				end

			end

		end

	)()

	local Reduisceen = Instance.new("ScreenGui")

	Reduisceen.Parent = game:GetService("CoreGui")

	Reduisceen.Name = "redui"

	Reduisceen.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

	local function MakeDraggable(topbarobject, object)

		local Dragging = nil

		local DragInput = nil

		local DragStart = nil

		local StartPosition = nil

		local function Update(input)

			local Delta = input.Position - DragStart

			local pos =

				UDim2.new(

				StartPosition.X.Scale,

				StartPosition.X.Offset + Delta.X,

				StartPosition.Y.Scale,

				StartPosition.Y.Offset + Delta.Y

			)

			local Tween = TweenService:Create(object, TweenInfo.new(0.2), {Position = pos})

			Tween:Play()

		end

		topbarobject.InputBegan:Connect(

			function(input)

				if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then

					Dragging = true

					DragStart = input.Position

					StartPosition = object.Position

					input.Changed:Connect(

						function()

							if input.UserInputState == Enum.UserInputState.End then

								Dragging = false

							end

						end

					)

				end

			end

		)

		topbarobject.InputChanged:Connect(

			function(input)

				if

					input.UserInputType == Enum.UserInputType.MouseMovement or

						input.UserInputType == Enum.UserInputType.Touch

				then

					DragInput = input

				end

			end

		)

		UserInputService.InputChanged:Connect(

			function(input)

				if input == DragInput and Dragging then

					Update(input)

				end

			end

		)

	end

	local function Tween(instance, properties,style,wa)

		if style == nil or "" then

			return Back

		end

		tween:Create(instance,TweenInfo.new(wa,Enum.EasingStyle[style]),{properties}):Play()

	end

	local create = {}

	function create:Win(text)

		local fs = false

		local MainSceen = Instance.new("Frame")

		MainSceen.Name = "MainSceen"

		MainSceen.Parent = Reduisceen

		MainSceen.AnchorPoint = Vector2.new(0.5, 0.5)

		MainSceen.BackgroundColor3 = Color3.fromRGB(15,15,15)

		MainSceen.BorderSizePixel = 10

		MainSceen.BorderColor3 = Color3.fromRGB(255,255,255)

		MainSceen.Position = UDim2.new(0.5, 0, 0.5, 0)

		MainSceen.Size = UDim2.new(0, 0, 0, 0)

		MainSceen.ClipsDescendants = true

		local Main_UiConner  = Instance.new("UICorner")

		Main_UiConner.CornerRadius = UDim.new(0, 4)

		Main_UiConner.Name = "Main_UiConner"

		Main_UiConner.Parent = MainSceen

		local ClickFrame = Instance.new("Frame")

		ClickFrame.Name = "ClickFrame"

		ClickFrame.Parent = MainSceen

		ClickFrame.AnchorPoint = Vector2.new(0.5, 0.5)

		ClickFrame.BackgroundColor3 = Color3.fromRGB(255,255,255)

		ClickFrame.BorderSizePixel = 0

		ClickFrame.Position = UDim2.new(0.5, 0, 0.036, 0)

		ClickFrame.Size = UDim2.new(0, 534-20, 0, 30)

		ClickFrame.ClipsDescendants = true

		ClickFrame.BackgroundTransparency = 1

		MakeDraggable(ClickFrame,MainSceen)

		tween:Create(MainSceen,TweenInfo.new(0.4,Enum.EasingStyle.Back),{Size = UDim2.new(0, 550, 0, 474)}):Play()

		local library = {toggledui = false;}

		spawn(function()

		game:GetService("UserInputService").InputBegan:Connect(function(input)

			pcall(function()

				if input.KeyCode == Enum.KeyCode.RightControl then

					if library.toggledui == false then

						library.toggledui = true

						tween:Create(MainSceen,TweenInfo.new(0.4,Enum.EasingStyle.Back,Enum.EasingDirection.In),{Size = UDim2.new(0, 0, 0, 0)}):Play()

						wait(.3)

						Reduisceen.Enabled = false

					else

						library.toggledui = false

						tween:Create(MainSceen,TweenInfo.new(0.4,Enum.EasingStyle.Back),{Size = UDim2.new(0, 534, 0, 474)}):Play()

						Reduisceen.Enabled = true

					end

				end

			end)

		end)

		end)

		local NameReal = Instance.new("TextLabel")

		NameReal.Parent = MainSceen

		NameReal.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

		NameReal.BackgroundTransparency = 1

		NameReal.BorderSizePixel = 0

		NameReal.Position = UDim2.new(0.5, 0, 0.05, 0)

		NameReal.AnchorPoint = Vector2.new(0.5, 0.5)

		NameReal.Size = UDim2.new(0, 136, 0, 34)

		NameReal.Font = Enum.Font.GothamBold

		NameReal.Text = tostring(text)

		NameReal.TextColor3 = Color3.fromRGB(0,250,154)

		NameReal.TextSize = 14.000

		local MainSceen2 = Instance.new("Frame")

		MainSceen2.Name = "MainSceen2"

		MainSceen2.Parent = MainSceen

		MainSceen2.AnchorPoint = Vector2.new(0.5, 0.5)

		MainSceen2.BackgroundColor3 = Color3.fromRGB(18,18,18)

		MainSceen2.BorderSizePixel = 0

		MainSceen2.Position = UDim2.new(0.5, 0, 0.5, 0)

		MainSceen2.Size = UDim2.new(0, 0, 0, 0)

		MainSceen2.ClipsDescendants = true

		local Main_UiConner2  = Instance.new("UICorner")

		Main_UiConner2.CornerRadius = UDim.new(0, 4)

		Main_UiConner2.Name = "Main_UiConner"

		Main_UiConner2.Parent = MainSceen

		MainSceen2:TweenSizeAndPosition(UDim2.new(0, 550-20, 0, 474-50), UDim2.new(0.5, 0, 0.53, 0), "Out", "Back", 0.5, true)

		local ScolTapBarFrame = Instance.new("Frame")

		ScolTapBarFrame.Name = "MainSceen2"

		ScolTapBarFrame.Parent = MainSceen2

		ScolTapBarFrame.AnchorPoint = Vector2.new(0.5, 0.5)

		ScolTapBarFrame.BackgroundColor3 = Color3.fromRGB(255,255,255)

		ScolTapBarFrame.BorderSizePixel = 0

		ScolTapBarFrame.BackgroundTransparency = 1

		ScolTapBarFrame.Position = UDim2.new(0.5, 0, 0.07, 0)

		ScolTapBarFrame.Size = UDim2.new(0, 500, 0, 35)

		ScolTapBarFrame.ClipsDescendants = true

		local ScrollingFrame_Menubar = Instance.new("ScrollingFrame")

		ScrollingFrame_Menubar.Parent = ScolTapBarFrame

		ScrollingFrame_Menubar.Active = true

		ScrollingFrame_Menubar.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

		ScrollingFrame_Menubar.BackgroundTransparency = 1

		ScrollingFrame_Menubar.BorderSizePixel = 0

		ScrollingFrame_Menubar.Size = UDim2.new(0, 500, 0, 35)

		ScrollingFrame_Menubar.CanvasSize = UDim2.new(2, 0, 0, 0)

		ScrollingFrame_Menubar.ScrollBarImageColor3 = Color3.fromRGB(0,250,154)

		ScrollingFrame_Menubar.ScrollBarThickness = 3

		local UIListLayout_Menubar = Instance.new("UIListLayout")

		UIListLayout_Menubar.Parent = ScrollingFrame_Menubar

		UIListLayout_Menubar.FillDirection = Enum.FillDirection.Horizontal

		UIListLayout_Menubar.SortOrder = Enum.SortOrder.LayoutOrder

		UIListLayout_Menubar.Padding = UDim.new(0, 10)

		local UIPadding_Menubar = Instance.new("UIPadding")

		UIPadding_Menubar.Parent = ScrollingFrame_Menubar

		UIPadding_Menubar.PaddingTop = UDim.new(0, 2)

		local PageOrders = -1

		local Container_Page = Instance.new('Frame',MainSceen2)

		Container_Page.Size = UDim2.new(0, 518, 0, 268)

		Container_Page.Position = UDim2.new(0.5, 0, 0.45, 0)

		Container_Page.BackgroundTransparency = 1

		Container_Page.Name = "Page "

		Container_Page.AnchorPoint = Vector2.new(0.5, 0.5)

		local pagesFolder = Instance.new("Folder")

		pagesFolder.Name = "pagesFolder"

		pagesFolder.Parent = Container_Page

		local UIPage = Instance.new('UIPageLayout',pagesFolder)

		UIPage.SortOrder = Enum.SortOrder.LayoutOrder

		UIPage.EasingDirection = Enum.EasingDirection.InOut

		UIPage.EasingStyle = Enum.EasingStyle.Quad

		UIPage.Padding = UDim.new(0, 10)

		UIPage.TweenTime = 0.500

		local top = {}

		local NotiFrame = Instance.new("Frame")

		NotiFrame.Name = "NotiFrame"

		NotiFrame.Parent = Reduisceen

		NotiFrame.AnchorPoint = Vector2.new(0.5, 0.5)

		NotiFrame.BackgroundColor3 = Color3.fromRGB(18,18,18)

		NotiFrame.BorderSizePixel = 0

		NotiFrame.Position =  UDim2.new(1, -210, 1, -500)

		NotiFrame.Size = UDim2.new(0, 400, 0, 500)

		NotiFrame.ClipsDescendants = true

		NotiFrame.BackgroundTransparency = 1

		local Notilistlayout = Instance.new("UIListLayout")

		Notilistlayout.Parent = NotiFrame

		Notilistlayout.SortOrder = Enum.SortOrder.LayoutOrder

		Notilistlayout.Padding = UDim.new(0, 5)

		function create:Notifile(titel,text,delays)

			local TitleFrame = Instance.new("Frame")

			TitleFrame.Name = "TitleFrame"

			TitleFrame.Parent = NotiFrame

			TitleFrame.AnchorPoint = Vector2.new(0.5, 0.5)

			TitleFrame.BackgroundColor3 = Color3.fromRGB(18,18,18)

			TitleFrame.BorderSizePixel = 0

			TitleFrame.Position =  UDim2.new(0.5, 0, 0.5,0)

			TitleFrame.Size = UDim2.new(0, 0, 0, 0)

			TitleFrame.ClipsDescendants = true

			TitleFrame.BackgroundTransparency = 0

			local ConnerTitile = Instance.new("UICorner")

			ConnerTitile.CornerRadius = UDim.new(0, 4)

			ConnerTitile.Name = ""

			ConnerTitile.Parent = TitleFrame

			TitleFrame:TweenSizeAndPosition(UDim2.new(0, 400-10, 0, 70),  UDim2.new(0.5, 0, 0.5,0), "Out", "Quad", 0.3, true)

			local imagenoti = Instance.new("ImageLabel")

			imagenoti.Parent = TitleFrame

			imagenoti.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

			imagenoti.BackgroundTransparency = 1.000

			imagenoti.AnchorPoint = Vector2.new(0.5, 0.5)

			imagenoti.Position = UDim2.new(0.9, 0, 0.5, 0)

			imagenoti.Size = UDim2.new(0, 50, 0, 50)

		--  imagenoti.Image = "https://www.roblox.com/asset-thumbnail/image?assetId=7578496318&width=0&height=0&format=png"

			local txdlid = Instance.new("TextLabel")

			txdlid.Parent = TitleFrame

			txdlid.Name = "TextLabel_Tap"

			txdlid.BackgroundColor3 = Color3.fromRGB(0,250,154)

			txdlid.Size =UDim2.new(0, 160, 0,25 )

			txdlid.Font = Enum.Font.GothamBold

			txdlid.Text = titel

			txdlid.TextColor3 = Color3.fromRGB(0,250,154)

			txdlid.TextSize = 13.000

			txdlid.AnchorPoint = Vector2.new(0.5, 0.5)

			txdlid.Position = UDim2.new(0.23, 0, 0.3, 0)

			-- txdlid.TextYAlignment = Enum.TextYAlignment.Top

			txdlid.TextXAlignment = Enum.TextXAlignment.Left

			txdlid.BackgroundTransparency = 1

			local LableFrame = Instance.new("Frame")

			LableFrame.Name = "LableFrame"

			LableFrame.Parent = TitleFrame

			LableFrame.AnchorPoint = Vector2.new(0.5, 0.5)

			LableFrame.BackgroundColor3 = Color3.fromRGB(0,250,154)

			LableFrame.BorderSizePixel = 0

			LableFrame.Position =  UDim2.new(0.36, 0, 0.67,0)

			LableFrame.Size = UDim2.new(0, 260, 0,25 )

			LableFrame.ClipsDescendants = true

			LableFrame.BackgroundTransparency = 1

			local TextNoti = Instance.new("TextLabel")

			TextNoti.Parent = LableFrame

			TextNoti.Name = "TextLabel_Tap"

			TextNoti.BackgroundColor3 = Color3.fromRGB(0,250,154)

			TextNoti.Size =UDim2.new(0, 260, 0,25 )

			TextNoti.Font = Enum.Font.GothamBold

			TextNoti.Text = text

			TextNoti.TextColor3 = Color3.fromRGB(255, 255, 255)

			TextNoti.TextSize = 13.000

			TextNoti.AnchorPoint = Vector2.new(0.5, 0.5)

			TextNoti.Position = UDim2.new(0.5, 0, 0.5, 0)

			-- TextNoti.TextYAlignment = Enum.TextYAlignment.Top

			TextNoti.TextXAlignment = Enum.TextXAlignment.Left

			TextNoti.BackgroundTransparency = 1

			repeat wait(0.2) until TitleFrame.Size == UDim2.new(0, 400-10, 0, 70)

			local Time = Instance.new("Frame")

			Time.Name = "Time"

			Time.Parent = TitleFrame

	--Time.AnchorPoint = Vector2.new(0.5, 0.5)

			Time.BackgroundColor3 =  Color3.fromRGB(0,250,154)

			Time.BorderSizePixel = 0

			Time.Position =  UDim2.new(0, 0, 0.,0)

			Time.Size = UDim2.new(0, 0,0,0)

			Time.ClipsDescendants = false

			Time.BackgroundTransparency = 0

			local ConnerTitile_Time = Instance.new("UICorner")

			ConnerTitile_Time.CornerRadius = UDim.new(0, 4)

			ConnerTitile_Time.Name = ""

			ConnerTitile_Time.Parent = Time

			Time:TweenSizeAndPosition(UDim2.new(0, 400-10, 0, 3),  UDim2.new(0., 0, 0.,0), "Out", "Quad", 0.3, true)

			repeat wait(0.2) until Time.Size == UDim2.new(0, 400-10, 0, 3)

			TweenService:Create(

				Time,

				TweenInfo.new(tonumber(delays), Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),

				{Size = UDim2.new(0, 0, 0, 3)} -- UDim2.new(0, 128, 0, 25)

			):Play()

			delay(tonumber(delays),function()

				TweenService:Create(

					TitleFrame,

					TweenInfo.new(0.4, Enum.EasingStyle.Back, Enum.EasingDirection.InOut),

					{Size = UDim2.new(0, 0, 0, 0)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				wait(0.3)

				TitleFrame:Destroy()

			end

		)

		end

		function top:Taps(text)

			PageOrders = PageOrders + 1

			local name = tostring(text) or tostring(math.random(1,5000))

			local Frame_Tap = Instance.new("Frame")

			Frame_Tap.Parent = ScrollingFrame_Menubar

			Frame_Tap.Name = text.."Server"

			Frame_Tap.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

			Frame_Tap.BackgroundTransparency = 1

			Frame_Tap.Position = UDim2.new(0.0, 0, 0.0, 0)

			Frame_Tap.Size = UDim2.new(0, 100, 0, 25)

			Frame_Tap.Visible = true

			local TextLabel_Tap = Instance.new("TextLabel")

			TextLabel_Tap.Parent = Frame_Tap

			TextLabel_Tap.Name = "TextLabel_Tap"

			TextLabel_Tap.BackgroundColor3 = Color3.fromRGB(0,250,154)

			TextLabel_Tap.Position = UDim2.new(0.5, 0, 0.8, 0)

			TextLabel_Tap.Size = UDim2.new(0, 0, 0, 0)

			TextLabel_Tap.Font = Enum.Font.SourceSans

			TextLabel_Tap.Text = " "

			TextLabel_Tap.TextColor3 = Color3.fromRGB(0, 0, 0)

			TextLabel_Tap.TextSize = 14.000

			TextLabel_Tap.AnchorPoint = Vector2.new(0.5, 0.5)

			local TextButton_Tap = Instance.new("TextButton")

			TextButton_Tap.Parent = Frame_Tap

			TextButton_Tap.Name = "TextButton_Tap"

			TextButton_Tap.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

			TextButton_Tap.BackgroundTransparency = 1.000

			TextButton_Tap.Position = UDim2.new(0.114491031, 0, -0.0216345787, 0)

			TextButton_Tap.Size = UDim2.new(0, 80, 0, 20)

			TextButton_Tap.Font = Enum.Font.GothamSemibold

			TextButton_Tap.TextColor3 = Color3.fromRGB(155, 155, 155)

			TextButton_Tap.TextSize = 13.000

			TextButton_Tap.Text = tostring(text)

			local MainPage = Instance.new("Frame")

			MainPage.Name = name.."_MainPage"

			MainPage.Parent = pagesFolder

			MainPage.BackgroundColor3 = Color3.fromRGB(255,255, 255)

			MainPage.BorderSizePixel = 0

			MainPage.Position = UDim2.new(0.5, 0, 0.5, 0) -- UDim2.new(0.0149812736, 0, 0.13, 0)

			MainPage.Size = UDim2.new(0, 518, 0, 375)

			MainPage.BackgroundTransparency = 1

			MainPage.ClipsDescendants = true

			MainPage.Visible = true

			MainPage.LayoutOrder = PageOrders

			TextButton_Tap.MouseButton1Click:connect(function()

				if MainPage.Name == text.."_MainPage" then

					UIPage:JumpToIndex(MainPage.LayoutOrder)

				end

				for i ,v in next , ScrollingFrame_Menubar:GetChildren() do

					if v:IsA("Frame") then

						TweenService:Create(

							v.TextButton_Tap,

							TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{TextColor3 = Color3.fromRGB(155, 155, 155)}

						):Play()

					end

					TweenService:Create(

						TextButton_Tap,

						TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(0,250,154)}

					):Play()

				end

			end)

			if fs == false then

				-- TweenService:Create(

				--     TextLabel_Tap,

				--     TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

				--     {Size = UDim2.new(0, 70, 0, 2)}

				-- ):Play()

				TweenService:Create(

					TextButton_Tap,

					TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{TextColor3 = Color3.fromRGB(0,250,154)}

				):Play()

				MainPage.Visible = true

				Frame_Tap.Name  = text .. "Server"

				fs  = true

			end

			local ScrollingFrame_Pagefrist = Instance.new("ScrollingFrame")

			ScrollingFrame_Pagefrist.Parent = MainPage

			ScrollingFrame_Pagefrist.Active = true

			ScrollingFrame_Pagefrist.BackgroundColor3 = Color3.fromRGB(23, 23, 23) -- 0,250,154

			ScrollingFrame_Pagefrist.BorderSizePixel = 0

			ScrollingFrame_Pagefrist.Size = UDim2.new(0, 518, 0, 375)

			ScrollingFrame_Pagefrist.ScrollBarThickness = 4

			ScrollingFrame_Pagefrist.ScrollBarImageColor3 = Color3.fromRGB(0,250,154) -- 0,250,154

			local UIGridLayout_Pagefrist = Instance.new("UIGridLayout")

			local UIPadding_Pagefrist = Instance.new("UIPadding")

			UIGridLayout_Pagefrist.Archivable = false

			UIGridLayout_Pagefrist.Parent = ScrollingFrame_Pagefrist

			UIGridLayout_Pagefrist.SortOrder = Enum.SortOrder.LayoutOrder

			UIGridLayout_Pagefrist.CellPadding = UDim2.new(0, 13, 0, 15)

			UIGridLayout_Pagefrist.CellSize = UDim2.new(0, 240, 0, 340)

			UIPadding_Pagefrist.Parent = ScrollingFrame_Pagefrist

			UIPadding_Pagefrist.PaddingLeft = UDim.new(0, 10)

			UIPadding_Pagefrist.PaddingTop = UDim.new(0, 20)

			local page = {}

			function page:newpage()

				local Pageframe = Instance.new("Frame")

				Pageframe.Parent = ScrollingFrame_Pagefrist

				Pageframe.BackgroundColor3 = Color3.fromRGB(30, 30, 30)

				Pageframe.BorderSizePixel = 1

				Pageframe.Position = UDim2.new(0.028957529, 0, 0.0496277921, 0)

				Pageframe.Size = UDim2.new(0, 240, 0, 340)

				local ScrollingFrame_Pageframe = Instance.new("ScrollingFrame")

				ScrollingFrame_Pageframe.Parent = Pageframe

				ScrollingFrame_Pageframe.Active = true

				ScrollingFrame_Pageframe.BackgroundColor3 = Color3.fromRGB(30, 30, 30)

				ScrollingFrame_Pageframe.BorderColor3 = Color3.fromRGB(0,250,154)

				ScrollingFrame_Pageframe.BorderSizePixel = 1

				ScrollingFrame_Pageframe.Position = UDim2.new(0, 0, -0.0101253344, 0)

				ScrollingFrame_Pageframe.Size = UDim2.new(0, 240, 0, 340)

				ScrollingFrame_Pageframe.ScrollBarThickness = 4

				ScrollingFrame_Pageframe.ScrollBarImageColor3 = Color3.fromRGB(222, 222, 222)

				local UIPadding_Pageframe = Instance.new("UIPadding")

				local UIListLayout_Pageframe = Instance.new("UIListLayout")

				UIPadding_Pageframe.Parent = ScrollingFrame_Pageframe

				UIPadding_Pageframe.PaddingLeft = UDim.new(0, 15)

				UIPadding_Pageframe.PaddingTop = UDim.new(0, 10)

				UIListLayout_Pageframe.Parent = ScrollingFrame_Pageframe

				UIListLayout_Pageframe.SortOrder = Enum.SortOrder.LayoutOrder

				UIListLayout_Pageframe.Padding = UDim.new(0, 10)

				UIListLayout_Pageframe:GetPropertyChangedSignal('AbsoluteContentSize'):Connect(function()

					ScrollingFrame_Pageframe.CanvasSize = UDim2.new(0,0,0,UIListLayout_Pageframe.AbsoluteContentSize.Y + 120 )

				end)

				UIGridLayout_Pagefrist:GetPropertyChangedSignal('AbsoluteContentSize'):Connect(function()

					ScrollingFrame_Pagefrist.CanvasSize = UDim2.new(0,0,0,UIGridLayout_Pagefrist.AbsoluteContentSize.Y + 50 )

				end)

				game:GetService("RunService").Stepped:Connect(function ()

					pcall(function ()

						ScrollingFrame_Menubar.CanvasSize = UDim2.new(0,  UIListLayout_Menubar.AbsoluteContentSize.X, 0,0)

						ScrollingFrame_Pageframe.CanvasSize = UDim2.new(0,0,0,UIListLayout_Pageframe.AbsoluteContentSize.Y + 20 )

						ScrollingFrame_Pagefrist.CanvasSize = UDim2.new(0,0,0,UIGridLayout_Pagefrist.AbsoluteContentSize.Y + 40)

					end)

				end)

			local items = {}

			function items:Toggle(text,config,callback)

				local Toggle = Instance.new("Frame")

				Toggle.Parent = ScrollingFrame_Pageframe

				Toggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				Toggle.BorderSizePixel = 0

				Toggle.Position = UDim2.new(0.5, 0, 0.5, 0)

				Toggle.Size = UDim2.new(0, 213, 0, 35)

				Toggle.BackgroundTransparency = 1

				Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

				local TextButton_Toggle = Instance.new("TextButton")

				TextButton_Toggle.Parent = Toggle

				TextButton_Toggle.BackgroundTransparency =1

				TextButton_Toggle.BackgroundColor3 = Color3.fromRGB(35, 35, 35)

				TextButton_Toggle.BorderSizePixel = 0

				TextButton_Toggle.Size = UDim2.new(0, 213, 0, 35)

				TextButton_Toggle.AutoButtonColor = false

				TextButton_Toggle.Font = Enum.Font.SourceSans

				TextButton_Toggle.Text = " "

				TextButton_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_Toggle.TextSize = 12.000

				local TextButton_2_Toggle = Instance.new("TextButton")

				TextButton_2_Toggle.Parent = TextButton_Toggle

				TextButton_2_Toggle.BackgroundColor3 = Color3.fromRGB(155, 155, 155)

		--        TextButton_2_Toggle.BorderColor3 = Color3.fromRGB(0,250,154)

				TextButton_2_Toggle.BorderSizePixel = 0

				TextButton_2_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

				TextButton_2_Toggle.Position = UDim2.new(0.9, 0, 0.5, 0)

				TextButton_2_Toggle.Size = UDim2.new(0, 30, 0, 13)

				TextButton_2_Toggle.Font = Enum.Font.SourceSans

				TextButton_2_Toggle.Text = " "

				TextButton_2_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_2_Toggle.TextSize = 12.000

				TextButton_2_Toggle.AutoButtonColor = false

				local TextButton_Pageframe_Uiconner = Instance.new("UICorner")

				TextButton_Pageframe_Uiconner.CornerRadius = UDim.new(0, 30)

				TextButton_Pageframe_Uiconner.Name = ""

				TextButton_Pageframe_Uiconner.Parent = TextButton_2_Toggle

				local TextButton_3_Toggle = Instance.new("TextButton")

				TextButton_3_Toggle.Parent = TextButton_2_Toggle

				TextButton_3_Toggle.BackgroundColor3 = Color3.fromRGB(255, 255,255)

		--        TextButton_3_Toggle.BorderColor3 = Color3.fromRGB(0,250,154)

				TextButton_3_Toggle.BorderSizePixel = 0

				TextButton_3_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

				TextButton_3_Toggle.Position = UDim2.new(0.1, 0, 0.5, 0)

				TextButton_3_Toggle.Size = UDim2.new(0, 19, 0, 19)

				TextButton_3_Toggle.Font = Enum.Font.SourceSans

				TextButton_3_Toggle.Text = " "

				TextButton_3_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_3_Toggle.TextSize = 12.000

				TextButton_3_Toggle.AutoButtonColor = false

				local TextButton_Pageframe_Uiconner2 = Instance.new("UICorner")

				TextButton_Pageframe_Uiconner2.CornerRadius = UDim.new(0, 30)

				TextButton_Pageframe_Uiconner2.Name = ""

				TextButton_Pageframe_Uiconner2.Parent = TextButton_3_Toggle

				local TextButton_4_Toggle = Instance.new("TextButton")

				TextButton_4_Toggle.Parent = TextButton_3_Toggle

				TextButton_4_Toggle.BackgroundColor3 = Color3.fromRGB(155, 155,155)

		--        TextButton_3_Toggle.BorderColor3 = Color3.fromRGB(0,250,154)

				TextButton_4_Toggle.BorderSizePixel = 0

				TextButton_4_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

				TextButton_4_Toggle.Position = UDim2.new(0.5, 0, 0.5, 0)

				TextButton_4_Toggle.Size = UDim2.new(0, 27, 0, 27-2)

				TextButton_4_Toggle.Font = Enum.Font.SourceSans

				TextButton_4_Toggle.Text = " "

				TextButton_4_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_4_Toggle.TextSize = 12.000

				TextButton_4_Toggle.AutoButtonColor = false

				TextButton_4_Toggle.BackgroundTransparency = 1

				TextButton_4_Toggle.Visible = true

				local TextButton_Pageframe_Uiconner4 = Instance.new("UICorner")

				TextButton_Pageframe_Uiconner4.CornerRadius = UDim.new(0, 30)

				TextButton_Pageframe_Uiconner4.Name = ""

				TextButton_Pageframe_Uiconner4.Parent = TextButton_4_Toggle

				local TextLabel_Toggle = Instance.new("TextLabel")

				TextLabel_Toggle.Parent = Toggle

				TextLabel_Toggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				TextLabel_Toggle.BackgroundTransparency = 1

				TextLabel_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

				TextLabel_Toggle.Position = UDim2.new(0.4, 0, 0.5, 0)

				TextLabel_Toggle.BorderSizePixel = 0

				TextLabel_Toggle.Size = UDim2.new(0, 130, 0, 25)

				TextLabel_Toggle.Font = Enum.Font.GothamSemibold

				TextLabel_Toggle.Text = text

				TextLabel_Toggle.TextColor3 = Color3.fromRGB(200, 200, 200)

				TextLabel_Toggle.TextSize = 13.000

				TextLabel_Toggle.ClipsDescendants = true

				TextLabel_Toggle.TextWrapped = true

				TextLabel_Toggle.TextXAlignment = Enum.TextXAlignment.Left

				local TextButton_Toggle2 = Instance.new("TextButton")

				TextButton_Toggle2.Parent = TextButton_Toggle

				TextButton_Toggle2.BackgroundTransparency =1

				TextButton_Toggle2.BackgroundColor3 = Color3.fromRGB(35, 35, 35)

				TextButton_Toggle2.BorderSizePixel = 0

				TextButton_Toggle2.Size = UDim2.new(0, 213, 0, 35)

				TextButton_Toggle2.AutoButtonColor = false

				TextButton_Toggle2.Font = Enum.Font.SourceSans

				TextButton_Toggle2.Text = " "

				TextButton_Toggle2.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_Toggle2.TextSize = 12.000

				TextButton_Toggle2.MouseEnter:Connect(function()

					TweenService:Create(

						TextButton_4_Toggle,

						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundTransparency = 0.6} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextLabel_Toggle,

						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

			TextButton_Toggle2.MouseLeave:Connect(function()

					TweenService:Create(

						TextButton_4_Toggle,

						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundTransparency = 1} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextLabel_Toggle,

						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(200, 200, 200)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

			local check = {toogle = false ; loacker = true ; togfunction = {

			};

		}

		TextButton_Toggle2.MouseButton1Click:Connect(function()

				if check.toogle == false and check.loacker == true  then

					TweenService:Create(

						TextButton_4_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_3_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_2_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(153, 0, 102)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TextButton_3_Toggle:TweenSizeAndPosition(UDim2.new(0, 19, 0, 19), UDim2.new(1, 0, 0.5, 0), "Out", "Quad", 0.3, true)

				elseif  check.loacker ==  true then

					TweenService:Create(

						TextButton_4_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_3_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_2_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TextButton_3_Toggle:TweenSizeAndPosition(UDim2.new(0, 19, 0, 19), UDim2.new(0.1, 0, 0.5, 0), "Out", "Quad", 0.3, true)

				end

				if  check.loacker == true  then

				check.toogle = not check.toogle

				callback(check.toogle)

				end

			end

		)

			if config == true then

				TweenService:Create(

					TextButton_4_Toggle,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					TextButton_3_Toggle,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					TextButton_2_Toggle,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{BackgroundColor3 =  Color3.fromRGB(153, 0, 102)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TextButton_3_Toggle:TweenSizeAndPosition(UDim2.new(0, 19, 0, 19), UDim2.new(1, 0, 0.5, 0), "Out", "Quad", 0.3, true)

				check.toogle = true

				callback(check.toogle)

			end

			local lockerframe = Instance.new("Frame")

			lockerframe.Name = "lockerframe"

			lockerframe.Parent = Toggle

			lockerframe.BackgroundColor3 = Color3.fromRGB(0, 0, 0)

			lockerframe.BackgroundTransparency = 1

			lockerframe.Size = UDim2.new(0, 320, 0, 35)

			lockerframe.Position = UDim2.new(0.5, 0, 0.5, 0)

			lockerframe.AnchorPoint = Vector2.new(0.5, 0.5)

			local LockerImageLabel = Instance.new("ImageLabel")

			LockerImageLabel.Parent = lockerframe

			LockerImageLabel.BackgroundTransparency = 1.000

			LockerImageLabel.BorderSizePixel = 0

			LockerImageLabel.Position = UDim2.new(0.5, 0, 0.5, 0)

			LockerImageLabel.AnchorPoint = Vector2.new(0.5, 0.5)

			LockerImageLabel.Size = UDim2.new(0, 0, 0, 0)

			LockerImageLabel.Image = "http://www.roblox.com/asset/?id=6031082533"

			function check.togfunction:lock()

				TweenService:Create(

					lockerframe,

					TweenInfo.new(.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),

					{BackgroundTransparency = 0.7}

				):Play()

				TweenService:Create(

					LockerImageLabel,

					TweenInfo.new(.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),

					{Size = UDim2.new(0, 30, 0, 30)}

				):Play()

				check.loacker  = false

			--    pcall(callback,locker)

			end

			function check.togfunction:unlock()

				TweenService:Create(

					lockerframe,

					TweenInfo.new(.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),

					{BackgroundTransparency = 1}

				):Play()

				TweenService:Create(

					LockerImageLabel,

					TweenInfo.new(.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out,0.1),

					{Size = UDim2.new(0, 0, 0, 0)}

				):Play()

				check.loacker  = true

			--   pcall(callback,locker)

			end

				return  check.togfunction

			end

			function items:Button(text,callback)

				local ButtonFrame = Instance.new("Frame")

				ButtonFrame.Name = "ButtonFrame"

				ButtonFrame.Parent = ScrollingFrame_Pageframe

				ButtonFrame.BackgroundColor3 = Color3.fromRGB(0,250,154)

				ButtonFrame.BorderSizePixel = 0

				ButtonFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

				ButtonFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				ButtonFrame.Size = UDim2.new(0, 213, 0, 25) -- UDim2.new(0, 213, 0, 35)

				ButtonFrame.BackgroundTransparency  = 1

				ButtonFrame.ClipsDescendants = true

				local MheeFrameStroke = Instance.new("UIStroke")

				MheeFrameStroke.Thickness = 0

				MheeFrameStroke.Name = ""

				MheeFrameStroke.Parent = ButtonFrame

				MheeFrameStroke.LineJoinMode = Enum.LineJoinMode.Round

				MheeFrameStroke.Color = Color3.fromRGB(0,250,154)

				MheeFrameStroke.Transparency = 0.7

				local Button = Instance.new("TextButton")

				Button.Parent = ButtonFrame

				Button.Name = "Button"

				Button.BackgroundColor3 = Color3.fromRGB(0,250,154)

				Button.Size = UDim2.new(0,150, 0, 25)

				Button.Font = Enum.Font.SourceSansSemibold

				Button.Text = tostring(text)

				Button.TextColor3 = Color3.fromRGB(155, 155, 155)

				Button.TextSize = 13.000

				Button.AnchorPoint = Vector2.new(0.5, 0.5)

				Button.Position = UDim2.new(0.5, 0, 0.5, 0)

				Button.TextXAlignment = Enum.TextXAlignment.Center

				Button.BackgroundTransparency = 0.6

				Button.TextWrapped = true

				Button.AutoButtonColor = false

				Button.ClipsDescendants = true

				local ConnerPageMhee = Instance.new("UICorner")

				ConnerPageMhee.CornerRadius = UDim.new(0, 4)

				ConnerPageMhee.Name = ""

				ConnerPageMhee.Parent = Button

				Button.MouseEnter:Connect(function()

					TweenService:Create(

						Button,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Size =  UDim2.new(0, 213, 0, 25)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						Button,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundTransparency = 0} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						Button,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(15, 15, 15)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

				Button.MouseLeave:Connect(function()

					TweenService:Create(

						Button,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Size =  UDim2.new(0, 150, 0, 25)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						Button,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundTransparency = 0.6} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						Button,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

			Button.MouseButton1Click:Connect(function()

			--    Ripple(Button)

				callback()

				TweenService:Create(

					Button,

					TweenInfo.new(0.2, Enum.EasingStyle.Back, Enum.EasingDirection.Out),

					{BackgroundTransparency = 0.6},

					{TextSize =  16} -- UDim2.new(0, 128, 0, 25)

				):Play()

				wait(0.1)

				TweenService:Create(

					Button,

					TweenInfo.new(0.2, Enum.EasingStyle.Back, Enum.EasingDirection.Out),

					{BackgroundTransparency = 0},

					{TextSize =  13} -- UDim2.new(0, 128, 0, 25)

					

				):Play()

			end

		)

			end

			function items:Slider(text,check,floor,min,max,de,lol,tog,callback)

			if check then

				local SliderFrame = Instance.new("Frame")

				SliderFrame.Name = "SliderFrame"

				SliderFrame.Parent = ScrollingFrame_Pageframe

				SliderFrame.BackgroundColor3 =  Color3.fromRGB(28, 28, 28)-- Color3.fromRGB(0,250,154)

				SliderFrame.BorderSizePixel = 0

				SliderFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

				SliderFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				SliderFrame.Size = UDim2.new(0, 213, 0, 75) -- UDim2.new(0, 213, 0, 35)

				SliderFrame.BackgroundTransparency  = 0

				SliderFrame.ClipsDescendants = true

				local SliderFrameConner = Instance.new("UICorner")

				SliderFrameConner.CornerRadius = UDim.new(0, 4)

				SliderFrameConner.Name = ""

				SliderFrameConner.Parent = SliderFrame

				local SliderFrameStroke = Instance.new("UIStroke")

				SliderFrameStroke.Thickness = 1

				SliderFrameStroke.Name = ""

				SliderFrameStroke.Parent = SliderFrame

				SliderFrameStroke.LineJoinMode = Enum.LineJoinMode.Round

				SliderFrameStroke.Color = Color3.fromRGB(0,250,154)

				SliderFrameStroke.Transparency = 0.7

				SliderFrame.MouseEnter:Connect(function()

					TweenService:Create(

						SliderFrameStroke,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

				SliderFrame.MouseLeave:Connect(function()

					TweenService:Create(

						SliderFrameStroke,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0.7} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

				local LabelNameSliderxd = Instance.new("TextLabel")

				LabelNameSliderxd.Parent = SliderFrame

				LabelNameSliderxd.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				LabelNameSliderxd.BackgroundTransparency = 1

				LabelNameSliderxd.BorderSizePixel = 0

				LabelNameSliderxd.Position = UDim2.new(0.35, 0, 0.2, 0)

				LabelNameSliderxd.AnchorPoint = Vector2.new(0.5, 0.5)

				LabelNameSliderxd.Size = UDim2.new(0, 120, 0, 20)

				LabelNameSliderxd.Font = Enum.Font.GothamBold

				LabelNameSliderxd.Text = tostring(text)

				LabelNameSliderxd.TextColor3 = Color3.fromRGB(255, 255, 255)

				LabelNameSliderxd.TextSize = 11.000

				LabelNameSliderxd.TextXAlignment = Enum.TextXAlignment.Left

				local ShowValueFarm = Instance.new("Frame")

				ShowValueFarm.Name = "ShowValueFarm"

				ShowValueFarm.Parent = SliderFrame

				ShowValueFarm.BackgroundColor3 = Color3.fromRGB(45, 45, 45)

				ShowValueFarm.Position = UDim2.new(0.0833333358, 0, 0.235135213, 0)

				ShowValueFarm.Size = UDim2.new(0, 75, 0, 15)

				ShowValueFarm.BackgroundTransparency = 0

				ShowValueFarm.BorderSizePixel = 0

				ShowValueFarm.AnchorPoint = Vector2.new(0.5, 0.5)

				ShowValueFarm.Position = UDim2.new(0.8, 0, 0.2, 0)

				ShowValueFarm.ClipsDescendants = false

				local CustomValue = Instance.new("TextBox")

				CustomValue.Parent = ShowValueFarm

				CustomValue.BackgroundColor3 = Color3.fromRGB(45,45, 45)

				CustomValue.BorderSizePixel = 0

				CustomValue.ClipsDescendants = true

				CustomValue.AnchorPoint = Vector2.new(0.5, 0.5)

				CustomValue.Position = UDim2.new(0.5, 0, 0.5, 0)

				CustomValue.Size = UDim2.new(0, 158, 0, 26)

				CustomValue.Font = Enum.Font.GothamSemibold

				CustomValue.PlaceholderColor3 = Color3.fromRGB(222, 222, 222)

				CustomValue.PlaceholderText =  ""

				if floor == true then

					CustomValue.Text =  tostring(de and string.format("%.1f",(de / max) * (max - min) + min) or 0)

				else

					CustomValue.Text =  tostring(de and math.floor( (de / max) * (max - min) + min) or 0)

				end

				CustomValue.TextColor3 = Color3.fromRGB(255, 255, 255)

				CustomValue.TextSize = 8.000

				CustomValue.BackgroundTransparency = 1

				local ValueFrame = Instance.new("Frame")

				ValueFrame.Name = "ValueFrame"

				ValueFrame.Parent = SliderFrame

				ValueFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)

				ValueFrame.Position = UDim2.new(0.0833333358, 0, 0.235135213, 0)

				ValueFrame.Size = UDim2.new(0, 140, 0, 5)

				ValueFrame.BackgroundTransparency = 0

				ValueFrame.BorderSizePixel = 0

				ValueFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				ValueFrame.Position = UDim2.new(0.4, 0, 0.8, 0)

				ValueFrame.ClipsDescendants = false

				local PartValue = Instance.new("Frame")

				PartValue.Name = "PartValue"

				PartValue.Parent = ValueFrame

				PartValue.BackgroundColor3 = Color3.fromRGB(222, 222, 222)

				PartValue.Position = UDim2.new(0.0833333358, 0, 0.235135213, 0)

				PartValue.Size = UDim2.new(0, 140, 0, 5)

				PartValue.BackgroundTransparency = 1

				PartValue.BorderSizePixel = 0

				PartValue.AnchorPoint = Vector2.new(0.5, 0.5)

				PartValue.Position = UDim2.new(0.5, 0, 0.5, 0)

				PartValue.ClipsDescendants = false

				local MainValue = Instance.new("Frame")

				MainValue.Name = "MainValue"

				MainValue.Parent = PartValue

				MainValue.BackgroundColor3 = Color3.fromRGB(0,250,154)

				MainValue.Size = UDim2.new((de or 0) / max, 0, 0, 5)

				MainValue.BackgroundTransparency = 0

				MainValue.BorderSizePixel = 0

				-- MainValue.AnchorPoint = Vector2.new(0.5, 0.5)

				MainValue.Position = UDim2.new(0., 0, 0.0, 0)

				MainValue.ClipsDescendants = false

				local Conner_S1 = Instance.new("UICorner")

				Conner_S1.CornerRadius = UDim.new(0, 8)

				Conner_S1.Name = ""

				Conner_S1.Parent = MainValue

				local Conner_S2 = Instance.new("UICorner")

				Conner_S2.CornerRadius = UDim.new(0, 8)

				Conner_S2.Name = ""

				Conner_S2.Parent = ValueFrame

				local ConneValue = Instance.new("Frame")

				ConneValue.Name = "ConneValue"

				ConneValue.Parent = PartValue

				ConneValue.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				ConneValue.Size = UDim2.new(0, 13, 0,13)

				ConneValue.BackgroundTransparency = 0

				ConneValue.BorderSizePixel = 0

				ConneValue.AnchorPoint = Vector2.new(0.5, 0.5)

				ConneValue.Position = UDim2.new((de or 0)/max, 0.5, 0.3,0.5, 0)

				ConneValue.ClipsDescendants = false

				local Conner_Conne = Instance.new("UICorner")

				Conner_Conne.CornerRadius = UDim.new(0, 300)

				Conner_Conne.Name = ""

				Conner_Conne.Parent = ConneValue

				local Addvalue = Instance.new("ImageButton")

				Addvalue.Name = "Imatog"

				Addvalue.Parent = SliderFrame

				Addvalue.BackgroundTransparency = 1.000

				Addvalue.BorderSizePixel = 0

				Addvalue.Position = UDim2.new(0.85, 0, 0.35, 0)

				Addvalue.Size = UDim2.new(0, 15, 0, 15)

				Addvalue.Image = "http://www.roblox.com/asset/?id=6035067836"

				Addvalue.ImageColor3 =  Color3.fromRGB(0,250,154)

				local Deletevalue = Instance.new("ImageButton")

				Deletevalue.Name = "Imatog"

				Deletevalue.Parent = SliderFrame

				Deletevalue.BackgroundTransparency = 1.000

				Deletevalue.BorderSizePixel = 0

				Deletevalue.Position = UDim2.new(0.7, 0, 0.35, 0)

				Deletevalue.Size = UDim2.new(0, 15, 0, 15)

				Deletevalue.Image = "http://www.roblox.com/asset/?id=6035047377"

				Deletevalue.ImageColor3 =  Color3.fromRGB(0,250,154)

				local TextButton_2_Toggle = Instance.new("TextButton")

				TextButton_2_Toggle.Parent = ValueFrame

				TextButton_2_Toggle.BackgroundColor3 = Color3.fromRGB(155, 155, 155)

		--        TextButton_2_Toggle.BorderColor3 = Color3.fromRGB(0,250,154)

				TextButton_2_Toggle.BorderSizePixel = 0

				TextButton_2_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

				TextButton_2_Toggle.Position = UDim2.new(1.25, 0, 0.4, 0)

				TextButton_2_Toggle.Size = UDim2.new(0, 30, 0, 13)

				TextButton_2_Toggle.Font = Enum.Font.SourceSans

				TextButton_2_Toggle.Text = " "

				TextButton_2_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_2_Toggle.TextSize = 12.000

				TextButton_2_Toggle.AutoButtonColor = false

				local TextButton_Pageframe_Uiconner = Instance.new("UICorner")

				TextButton_Pageframe_Uiconner.CornerRadius = UDim.new(0, 30)

				TextButton_Pageframe_Uiconner.Name = ""

				TextButton_Pageframe_Uiconner.Parent = TextButton_2_Toggle

				local TextButton_3_Toggle = Instance.new("TextButton")

				TextButton_3_Toggle.Parent = TextButton_2_Toggle

				TextButton_3_Toggle.BackgroundColor3 = Color3.fromRGB(255, 255,255)

		--        TextButton_3_Toggle.BorderColor3 = Color3.fromRGB(0,250,154)

				TextButton_3_Toggle.BorderSizePixel = 0

				TextButton_3_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

				TextButton_3_Toggle.Position = UDim2.new(0.1, 0, 0.5, 0)

				TextButton_3_Toggle.Size = UDim2.new(0, 19, 0, 19)

				TextButton_3_Toggle.Font = Enum.Font.SourceSans

				TextButton_3_Toggle.Text = " "

				TextButton_3_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_3_Toggle.TextSize = 12.000

				TextButton_3_Toggle.AutoButtonColor = false

				local TextButton_Pageframe_Uiconner2 = Instance.new("UICorner")

				TextButton_Pageframe_Uiconner2.CornerRadius = UDim.new(0, 30)

				TextButton_Pageframe_Uiconner2.Name = ""

				TextButton_Pageframe_Uiconner2.Parent = TextButton_3_Toggle

				local TextButton_4_Toggle = Instance.new("TextButton")

				TextButton_4_Toggle.Parent = TextButton_3_Toggle

				TextButton_4_Toggle.BackgroundColor3 = Color3.fromRGB(155, 155,155)

		--        TextButton_3_Toggle.BorderColor3 = Color3.fromRGB(0,250,154)

				TextButton_4_Toggle.BorderSizePixel = 0

				TextButton_4_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

				TextButton_4_Toggle.Position = UDim2.new(0.5, 0, 0.5, 0)

				TextButton_4_Toggle.Size = UDim2.new(0, 27, 0, 27-2)

				TextButton_4_Toggle.Font = Enum.Font.SourceSans

				TextButton_4_Toggle.Text = " "

				TextButton_4_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_4_Toggle.TextSize = 12.000

				TextButton_4_Toggle.AutoButtonColor = false

				TextButton_4_Toggle.BackgroundTransparency = 1

				TextButton_4_Toggle.Visible = true

				local TextButton_Pageframe_Uiconner4 = Instance.new("UICorner")

				TextButton_Pageframe_Uiconner4.CornerRadius = UDim.new(0, 30)

				TextButton_Pageframe_Uiconner4.Name = ""

				TextButton_Pageframe_Uiconner4.Parent = TextButton_4_Toggle

				local TextButton_Toggle = Instance.new("TextButton")

				TextButton_Toggle.Parent = ValueFrame

				TextButton_Toggle.BackgroundTransparency =1

				TextButton_Toggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				TextButton_Toggle.BorderSizePixel = 0

				TextButton_Toggle.Size = UDim2.new(0, 50, 0, 20)

				TextButton_Toggle.AutoButtonColor = false

				TextButton_Toggle.Font = Enum.Font.SourceSans

				TextButton_Toggle.Text = " "

				TextButton_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_Toggle.TextSize = 12.000

				TextButton_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

				TextButton_Toggle.Position = UDim2.new(1.25, 0, 0.4, 0)

			-- local value = de

			local check2 = {toogle2 = false;}

				local function move(input)

					local pos =

						UDim2.new(

							math.clamp((input.Position.X - ValueFrame.AbsolutePosition.X) / ValueFrame.AbsoluteSize.X, 0, 1),

							0,

							0.3,

							0

						)

					local pos1 =

						UDim2.new(

							math.clamp((input.Position.X - ValueFrame.AbsolutePosition.X) / ValueFrame.AbsoluteSize.X, 0, 1),

							0,

							0,

							5

						)

						MainValue:TweenSize(pos1, "Out", "Sine", 0.2, true)

						ConneValue:TweenPosition(pos, "Out", "Sine", 0.2, true)

						if floor == true then

							local value = string.format("%.1f",((pos.X.Scale * max) / max) * (max - min) + min)

							CustomValue.Text = tostring(value)

						--   callback[2] = value

						callback({

							["s"] = value;

							["t"] = check2.toogle2

						})

						--callback({value,check2.toogle2})

							--callback(value)

						else

							local value = math.floor(((pos.X.Scale * max) / max) * (max - min) + min)

							CustomValue.Text = tostring(value)

							callback({

								["s"] = value;

								["t"] = check2.toogle2

							})

					--       callback({value,check2.toogle2})

						end

					end

					local dragging = false

					ConneValue.InputBegan:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = true

							end

						end

					)

					ConneValue.InputEnded:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = false

							end

						end

					)

					SliderFrame.InputBegan:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = true

							end

						end

					)

					SliderFrame.InputEnded:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = false

							end

						end

					)

					ValueFrame.InputBegan:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = true

							end

						end

					)

					ValueFrame.InputEnded:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = false

							end

						end

					)

					game:GetService("UserInputService").InputChanged:Connect(

						function(input)

							if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then

								move(input)

							end

						end

						)

						CustomValue.FocusLost:Connect(function()

							if CustomValue.Text == "" then

								CustomValue.Text  = de

							end

							if  tonumber(CustomValue.Text) > max then

								CustomValue.Text  = max

							end

							if  tonumber(CustomValue.Text) <= min then

								CustomValue.Text  = min

							end

							MainValue:TweenSize(UDim2.new((CustomValue.Text or 0) / max, 0, 0, 5), "Out", "Sine", 0.2, true)

							ConneValue:TweenPosition(UDim2.new((CustomValue.Text or 0)/max, 0,0, 0) , "Out", "Sine", 0.2, true)

							if floor == true then

								CustomValue.Text = tostring(CustomValue.Text and string.format("%.1f",(CustomValue.Text / max) * (max - min) + min) )

							else

								CustomValue.Text = tostring(CustomValue.Text and math.floor( (CustomValue.Text / max) * (max - min) + min) )

							end

							callback({

								["s"] =  CustomValue.Text;

								["t"] = check2.toogle2;

							})

					--       callback({ tonumber(CustomValue.Text),check2.toogle2})

					--  pcall(callback, CustomValue.Text)

						end)

						Addvalue.MouseButton1Click:Connect(function ()

							if CustomValue.Text == "" then

								CustomValue.Text  = de

							end

							pcall(function()

								CustomValue.Text  = CustomValue.Text  - tonumber(lol)

							end)

							if  tonumber(CustomValue.Text) > max then

								CustomValue.Text  = max

							end

							if  tonumber(CustomValue.Text) < min then

								CustomValue.Text  = min

							end

							MainValue:TweenSize(UDim2.new((CustomValue.Text  or 0  ) / max, 0, 0, 5), "Out", "Sine", 0.2, true)

							ConneValue:TweenPosition(UDim2.new((CustomValue.Text or 0)/max, 0,0.5, 0) , "Out", "Sine", 0.2, true)

							if floor == true then

								CustomValue.Text = tostring(CustomValue.Text and string.format("%.1f",(CustomValue.Text / max) * (max - min) + min) )

							else

								CustomValue.Text = tostring(CustomValue.Text and math.floor( (CustomValue.Text / max) * (max - min) + min) )

							end

							callback({

								["s"] =  CustomValue.Text;

								["t"] = check2.toogle2

							})

						--   callback({ tonumber(CustomValue.Text),check2.toogle2})

						--  pcall(callback, CustomValue.Text)

						end)

						Deletevalue.MouseButton1Click:Connect(function ()

							if CustomValue.Text == "" then

								CustomValue.Text  = de

							end

							pcall(function()

								CustomValue.Text  = CustomValue.Text  + tonumber(lol)

							end)

							if  tonumber(CustomValue.Text) > max then

								CustomValue.Text  = max

							end

							if  tonumber(CustomValue.Text) < min then

								CustomValue.Text  = min

							end

							MainValue:TweenSize(UDim2.new((CustomValue.Text  or 0  ) / max, 0, 0, 5), "Out", "Sine", 0.2, true)

							ConneValue:TweenPosition(UDim2.new((CustomValue.Text or 0)/max, 0,0.5, 0) , "Out", "Sine", 0.2, true)

							if floor == true then

								CustomValue.Text = tostring(CustomValue.Text and string.format("%.1f",(CustomValue.Text / max) * (max - min) + min) )

							else

								CustomValue.Text = tostring(CustomValue.Text and math.floor( (CustomValue.Text / max) * (max - min) + min) )

							end

							callback({

								["s"] =  CustomValue.Text;

								["t"] = check2.toogle2;

							})

				--callback({ tonumber(CustomValue.Text),check2.toogle2})

						--  pcall(callback, CustomValue.Text)

						end)

				---

						TextButton_Toggle.MouseEnter:Connect(function()

							TweenService:Create(

								TextButton_4_Toggle,

								TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

								{BackgroundTransparency = 0.6} -- UDim2.new(0, 128, 0, 25)

							):Play()

						end

					)

					TextButton_Toggle.MouseLeave:Connect(function()

							TweenService:Create(

								TextButton_4_Toggle,

								TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

								{BackgroundTransparency = 1} -- UDim2.new(0, 128, 0, 25)

							):Play()

						end

					)

				TextButton_Toggle.MouseButton1Click:Connect(function()

					if check2.toogle2 == false   then

						TweenService:Create(

							TextButton_4_Toggle,

							TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

						):Play()

						TweenService:Create(

							TextButton_3_Toggle,

							TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

						):Play()

						TweenService:Create(

							TextButton_2_Toggle,

							TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{BackgroundColor3 =  Color3.fromRGB(153, 0, 102)} -- UDim2.new(0, 128, 0, 25)

						):Play()

						TextButton_3_Toggle:TweenSizeAndPosition(UDim2.new(0, 19, 0, 19), UDim2.new(1, 0, 0.5, 0), "Out", "Quad", 0.3, true)

					else

						TweenService:Create(

							TextButton_4_Toggle,

							TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{BackgroundColor3 =  Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

						):Play()

						TweenService:Create(

							TextButton_3_Toggle,

							TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{BackgroundColor3 =  Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

						):Play()

						TweenService:Create(

							TextButton_2_Toggle,

							TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{BackgroundColor3 =  Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

						):Play()

						TextButton_3_Toggle:TweenSizeAndPosition(UDim2.new(0, 19, 0, 19), UDim2.new(0.1, 0, 0.5, 0), "Out", "Quad", 0.3, true)

					end

						check2.toogle2 = not check2.toogle2

						callback({

							["t"] = check2.toogle2;

						})

					--   callback({value,check2.toogle2})

						--callback(check2.toogle2)

				end

			)

				if tog == true then

					TweenService:Create(

						TextButton_4_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_3_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_2_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(153, 0, 102)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TextButton_3_Toggle:TweenSizeAndPosition(UDim2.new(0, 19, 0, 19), UDim2.new(1, 0, 0.5, 0), "Out", "Quad", 0.3, true)

					check2.toogle2 = true

					callback({

						["t"] = check2.toogle2;

					})

			--        callback({value,check2.toogle2})

				--  callback(check2.toogle2)

				end

			else

				tog = nil

				local SliderFrame = Instance.new("Frame")

				SliderFrame.Name = "SliderFrame"

				SliderFrame.Parent = ScrollingFrame_Pageframe

				SliderFrame.BackgroundColor3 =  Color3.fromRGB(28, 28, 28)-- Color3.fromRGB(0,250,154)

				SliderFrame.BorderSizePixel = 0

				SliderFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

				SliderFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				SliderFrame.Size = UDim2.new(0, 213, 0, 75) -- UDim2.new(0, 213, 0, 35)

				SliderFrame.BackgroundTransparency  = 0

				SliderFrame.ClipsDescendants = true

				local SliderFrameConner = Instance.new("UICorner")

				SliderFrameConner.CornerRadius = UDim.new(0, 4)

				SliderFrameConner.Name = ""

				SliderFrameConner.Parent = SliderFrame

				local SliderFrameStroke = Instance.new("UIStroke")

				SliderFrameStroke.Thickness = 1

				SliderFrameStroke.Name = ""

				SliderFrameStroke.Parent = SliderFrame

				SliderFrameStroke.LineJoinMode = Enum.LineJoinMode.Round

				SliderFrameStroke.Color = Color3.fromRGB(0,250,154)

				SliderFrameStroke.Transparency = 0.7

				SliderFrame.MouseEnter:Connect(function()

					TweenService:Create(

						SliderFrameStroke,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

				SliderFrame.MouseLeave:Connect(function()

					TweenService:Create(

						SliderFrameStroke,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0.7} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

				local LabelNameSliderxd = Instance.new("TextLabel")

				LabelNameSliderxd.Parent = SliderFrame

				LabelNameSliderxd.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				LabelNameSliderxd.BackgroundTransparency = 1

				LabelNameSliderxd.BorderSizePixel = 0

				LabelNameSliderxd.Position = UDim2.new(0.35, 0, 0.2, 0)

				LabelNameSliderxd.AnchorPoint = Vector2.new(0.5, 0.5)

				LabelNameSliderxd.Size = UDim2.new(0, 120, 0, 20)

				LabelNameSliderxd.Font = Enum.Font.GothamBold

				LabelNameSliderxd.Text = tostring(text)

				LabelNameSliderxd.TextColor3 = Color3.fromRGB(255, 255, 255)

				LabelNameSliderxd.TextSize = 11.000

				LabelNameSliderxd.TextXAlignment = Enum.TextXAlignment.Left

				local ShowValueFarm = Instance.new("Frame")

				ShowValueFarm.Name = "ShowValueFarm"

				ShowValueFarm.Parent = SliderFrame

				ShowValueFarm.BackgroundColor3 = Color3.fromRGB(45, 45, 45)

				ShowValueFarm.Position = UDim2.new(0.0833333358, 0, 0.235135213, 0)

				ShowValueFarm.Size = UDim2.new(0, 75, 0, 15)

				ShowValueFarm.BackgroundTransparency = 0

				ShowValueFarm.BorderSizePixel = 0

				ShowValueFarm.AnchorPoint = Vector2.new(0.5, 0.5)

				ShowValueFarm.Position = UDim2.new(0.8, 0, 0.2, 0)

				ShowValueFarm.ClipsDescendants = false

				local CustomValue = Instance.new("TextBox")

				CustomValue.Parent = ShowValueFarm

				CustomValue.BackgroundColor3 = Color3.fromRGB(45,45, 45)

				CustomValue.BorderSizePixel = 0

				CustomValue.ClipsDescendants = true

				CustomValue.AnchorPoint = Vector2.new(0.5, 0.5)

				CustomValue.Position = UDim2.new(0.5, 0, 0.5, 0)

				CustomValue.Size = UDim2.new(0, 158, 0, 26)

				CustomValue.Font = Enum.Font.GothamSemibold

				CustomValue.PlaceholderColor3 = Color3.fromRGB(222, 222, 222)

				CustomValue.PlaceholderText =  ""

				if floor == true then

					CustomValue.Text =  tostring(de and string.format("%.1f",(de / max) * (max - min) + min) or 0)

				else

					CustomValue.Text =  tostring(de and math.floor( (de / max) * (max - min) + min) or 0)

				end

				CustomValue.TextColor3 = Color3.fromRGB(255, 255, 255)

				CustomValue.TextSize = 8.000

				CustomValue.BackgroundTransparency = 1

				local ValueFrame = Instance.new("Frame")

				ValueFrame.Name = "ValueFrame"

				ValueFrame.Parent = SliderFrame

				ValueFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)

				ValueFrame.Position = UDim2.new(0.0833333358, 0, 0.235135213, 0)

				ValueFrame.Size = UDim2.new(0, 190, 0, 5)

				ValueFrame.BackgroundTransparency = 0

				ValueFrame.BorderSizePixel = 0

				ValueFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				ValueFrame.Position = UDim2.new(0.5, 0, 0.8, 0)

				ValueFrame.ClipsDescendants = false

				local PartValue = Instance.new("Frame")

				PartValue.Name = "PartValue"

				PartValue.Parent = ValueFrame

				PartValue.BackgroundColor3 = Color3.fromRGB(222, 222, 222)

				PartValue.Position = UDim2.new(0.0833333358, 0, 0.235135213, 0)

				PartValue.Size = UDim2.new(0, 190, 0, 5)

				PartValue.BackgroundTransparency = 1

				PartValue.BorderSizePixel = 0

				PartValue.AnchorPoint = Vector2.new(0.5, 0.5)

				PartValue.Position = UDim2.new(0.5, 0, 0.5, 0)

				PartValue.ClipsDescendants = false

				local MainValue = Instance.new("Frame")

				MainValue.Name = "MainValue"

				MainValue.Parent = PartValue

				MainValue.BackgroundColor3 = Color3.fromRGB(0,250,154)

				MainValue.Size = UDim2.new((de or 0) / max, 0, 0, 5)

				MainValue.BackgroundTransparency = 0

				MainValue.BorderSizePixel = 0

				-- MainValue.AnchorPoint = Vector2.new(0.5, 0.5)

				MainValue.Position = UDim2.new(0., 0, 0.0, 0)

				MainValue.ClipsDescendants = false

				local Conner_S1 = Instance.new("UICorner")

				Conner_S1.CornerRadius = UDim.new(0, 8)

				Conner_S1.Name = ""

				Conner_S1.Parent = MainValue

				local Conner_S2 = Instance.new("UICorner")

				Conner_S2.CornerRadius = UDim.new(0, 8)

				Conner_S2.Name = ""

				Conner_S2.Parent = ValueFrame

				local ConneValue = Instance.new("Frame")

				ConneValue.Name = "ConneValue"

				ConneValue.Parent = PartValue

				ConneValue.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				ConneValue.Size = UDim2.new(0, 13, 0,13)

				ConneValue.BackgroundTransparency = 0

				ConneValue.BorderSizePixel = 0

				ConneValue.AnchorPoint = Vector2.new(0.5, 0.5)

				ConneValue.Position = UDim2.new((de or 0)/max, 0.5, 0.3,0.5, 0)

				ConneValue.ClipsDescendants = false

				local Conner_Conne = Instance.new("UICorner")

				Conner_Conne.CornerRadius = UDim.new(0, 300)

				Conner_Conne.Name = ""

				Conner_Conne.Parent = ConneValue

				local Addvalue = Instance.new("ImageButton")

				Addvalue.Name = "Imatog"

				Addvalue.Parent = SliderFrame

				Addvalue.BackgroundTransparency = 1.000

				Addvalue.BorderSizePixel = 0

				Addvalue.Position = UDim2.new(0.85, 0, 0.35, 0)

				Addvalue.Size = UDim2.new(0, 15, 0, 15)

				Addvalue.Image = "http://www.roblox.com/asset/?id=6035067836"

				Addvalue.ImageColor3 =  Color3.fromRGB(0,250,154)

				local Deletevalue = Instance.new("ImageButton")

				Deletevalue.Name = "Imatog"

				Deletevalue.Parent = SliderFrame

				Deletevalue.BackgroundTransparency = 1.000

				Deletevalue.BorderSizePixel = 0

				Deletevalue.Position = UDim2.new(0.7, 0, 0.35, 0)

				Deletevalue.Size = UDim2.new(0, 15, 0, 15)

				Deletevalue.Image = "http://www.roblox.com/asset/?id=6035047377"

				Deletevalue.ImageColor3 =  Color3.fromRGB(0,250,154)

				local function move(input)

					local pos =

						UDim2.new(

							math.clamp((input.Position.X - ValueFrame.AbsolutePosition.X) / ValueFrame.AbsoluteSize.X, 0, 1),

							0,

							0.3,

							0

						)

					local pos1 =

						UDim2.new(

							math.clamp((input.Position.X - ValueFrame.AbsolutePosition.X) / ValueFrame.AbsoluteSize.X, 0, 1),

							0,

							0,

							5

						)

						MainValue:TweenSize(pos1, "Out", "Sine", 0.2, true)

						ConneValue:TweenPosition(pos, "Out", "Sine", 0.2, true)

						if floor == true then

							local value = string.format("%.1f",((pos.X.Scale * max) / max) * (max - min) + min)

							CustomValue.Text = tostring(value)

							callback(value)

						else

							local value = math.floor(((pos.X.Scale * max) / max) * (max - min) + min)

							CustomValue.Text = tostring(value)

							callback(value)

						end

					end

					local dragging = false

					ConneValue.InputBegan:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = true

							end

						end

					)

					ConneValue.InputEnded:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = false

							end

						end

					)

					SliderFrame.InputBegan:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = true

							end

						end

					)

					SliderFrame.InputEnded:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = false

							end

						end

					)

					ValueFrame.InputBegan:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = true

							end

						end

					)

					ValueFrame.InputEnded:Connect(

						function(input)

							if input.UserInputType == Enum.UserInputType.MouseButton1 then

								dragging = false

							end

						end

					)

					game:GetService("UserInputService").InputChanged:Connect(

						function(input)

							if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then

								move(input)

							end

						end

						)

						CustomValue.FocusLost:Connect(function()

							if CustomValue.Text == "" then

								CustomValue.Text  = de

							end

							if  tonumber(CustomValue.Text) > max then

								CustomValue.Text  = max

							end

							MainValue:TweenSize(UDim2.new((CustomValue.Text or 0) / max, 0, 0, 5), "Out", "Sine", 0.2, true)

							ConneValue:TweenPosition(UDim2.new((CustomValue.Text or 0)/max, 0,0, 0) , "Out", "Sine", 0.2, true)

							if floor == true then

								CustomValue.Text = tostring(CustomValue.Text and string.format("%.1f",(CustomValue.Text / max) * (max - min) + min) )

							else

								CustomValue.Text = tostring(CustomValue.Text and math.floor( (CustomValue.Text / max) * (max - min) + min) )

							end

							pcall(callback, CustomValue.Text)

						end)

				Addvalue.MouseButton1Click:Connect(function ()

					if CustomValue.Text == "" then

						CustomValue.Text  = de

					end

					CustomValue.Text  = CustomValue.Text  - tonumber(lol)

					if  tonumber(CustomValue.Text) > max then

						CustomValue.Text  = max

					end

					if  tonumber(CustomValue.Text) < min then

						CustomValue.Text  = min

					end

					MainValue:TweenSize(UDim2.new((CustomValue.Text  or 0  ) / max, 0, 0, 5), "Out", "Sine", 0.2, true)

					ConneValue:TweenPosition(UDim2.new((CustomValue.Text or 0)/max, 0,0.5, 0) , "Out", "Sine", 0.2, true)

					if floor == true then

						CustomValue.Text = tostring(CustomValue.Text and string.format("%.1f",(CustomValue.Text / max) * (max - min) + min) )

					else

						CustomValue.Text = tostring(CustomValue.Text and math.floor( (CustomValue.Text / max) * (max - min) + min) )

					end

					pcall(callback, CustomValue.Text)

				end)

				Deletevalue.MouseButton1Click:Connect(function ()

					if CustomValue.Text == "" then

						CustomValue.Text  = de

					end

					CustomValue.Text  = CustomValue.Text  + tonumber(lol)

					if  tonumber(CustomValue.Text) > max then

						CustomValue.Text  = max

					end

					if  tonumber(CustomValue.Text) < min then

						CustomValue.Text  = min

					end

					MainValue:TweenSize(UDim2.new((CustomValue.Text  or 0  ) / max, 0, 0, 5), "Out", "Sine", 0.2, true)

					ConneValue:TweenPosition(UDim2.new((CustomValue.Text or 0)/max, 0,0.5, 0) , "Out", "Sine", 0.2, true)

					if floor == true then

						CustomValue.Text = tostring(CustomValue.Text and string.format("%.1f",(CustomValue.Text / max) * (max - min) + min) )

					else

						CustomValue.Text = tostring(CustomValue.Text and math.floor( (CustomValue.Text / max) * (max - min) + min) )

					end

					pcall(callback, CustomValue.Text)

				end)

			end

			end

			function items:Drop(text,use,option,callback)

			if use == false then

				local DropFrame = Instance.new("Frame")

				DropFrame.Name = "DropFrame"

				DropFrame.Parent = ScrollingFrame_Pageframe

				DropFrame.BackgroundColor3 =  Color3.fromRGB(23, 23, 23)-- Color3.fromRGB(0,250,154)

				DropFrame.BorderSizePixel = 0

				DropFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

				DropFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				DropFrame.Size = UDim2.new(0, 213, 0, 30) -- UDim2.new(0, 213, 0, 35)

				DropFrame.BackgroundTransparency  = 0

				DropFrame.ClipsDescendants = true

				local ConnerDropFrame = Instance.new("UICorner")

				ConnerDropFrame.CornerRadius = UDim.new(0, 4)

				ConnerDropFrame.Name = ""

				ConnerDropFrame.Parent = DropFrame

				local DropFrameStroke = Instance.new("UIStroke")

				DropFrameStroke.Thickness = 1

				DropFrameStroke.Name = ""

				DropFrameStroke.Parent = DropFrame

				DropFrameStroke.LineJoinMode = Enum.LineJoinMode.Round

				DropFrameStroke.Color = Color3.fromRGB(0,250,154)

				DropFrameStroke.Transparency = 0.7

				local LabelFrameDrop = Instance.new("TextLabel")

				LabelFrameDrop.Parent = DropFrame

				LabelFrameDrop.Name = "LabelFrameDrop"

				LabelFrameDrop.BackgroundColor3 = Color3.fromRGB(0,250,154)

				LabelFrameDrop.Position = UDim2.new(0., 0, 0., 0)

				LabelFrameDrop.Size =    UDim2.new(0, 213, 0, 30)

				LabelFrameDrop.Font = Enum.Font.SourceSansSemibold

				LabelFrameDrop.Text = ""

				LabelFrameDrop.TextColor3 = Color3.fromRGB(155, 155, 155)

				LabelFrameDrop.TextSize = 14.000

			--   LabelFrameDrop.AnchorPoint = Vector2.new(0.5, 0.5)

				LabelFrameDrop.BackgroundTransparency = 1

				LabelFrameDrop.TextXAlignment = Enum.TextXAlignment.Left

				local TextLabel_TapDrop = Instance.new("TextLabel")

				TextLabel_TapDrop.Parent = LabelFrameDrop

				TextLabel_TapDrop.Name = "TextLabel_TapDrop"

				TextLabel_TapDrop.BackgroundColor3 = Color3.fromRGB(0,250,154)

				TextLabel_TapDrop.Position = UDim2.new(0.04, 0, 0.14, 0)

				TextLabel_TapDrop.Size =    UDim2.new(0, 140, 0, 20)

				TextLabel_TapDrop.Font = Enum.Font.SourceSansSemibold

				TextLabel_TapDrop.Text = tostring(text).." :"

				TextLabel_TapDrop.TextColor3 = Color3.fromRGB(155, 155, 155)

				TextLabel_TapDrop.TextSize = 14.000

		--     TextLabel_TapDrop.AnchorPoint = Vector2.new(0.5, 0.5)

				TextLabel_TapDrop.BackgroundTransparency = 1

				TextLabel_TapDrop.TextXAlignment = Enum.TextXAlignment.Left

				local DropArbt_listimage = Instance.new("ImageButton")

				DropArbt_listimage.Parent = LabelFrameDrop

				DropArbt_listimage.BackgroundTransparency = 1.000

				DropArbt_listimage.AnchorPoint = Vector2.new(0.5, 0.5)

				DropArbt_listimage.Position = UDim2.new(0.9, 0, 0.5, 0)

				DropArbt_listimage.BorderSizePixel = 0

				DropArbt_listimage.Size = UDim2.new(0, 25, 0, 25)

				DropArbt_listimage.Image = "http://www.roblox.com/asset/?id=6031091004"

				DropArbt_listimage.ImageColor3 = Color3.fromRGB(155, 155, 155)

				local ScolDown = Instance.new("ScrollingFrame")

				ScolDown.Name = "ScolDown"

				ScolDown.Position = UDim2.new(0.02, 0, 1., 0)

				ScolDown.Parent = LabelFrameDrop

				ScolDown.Active = true

				ScolDown.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				ScolDown.BorderSizePixel = 0

				ScolDown.Size = UDim2.new(0, 205, 0, 115)

				ScolDown.ScrollBarThickness = 3

				ScolDown.ClipsDescendants = true

				ScolDown.BackgroundTransparency = 1

				ScolDown.CanvasSize = UDim2.new(0, 0, 0, 2)

				local UIListLayoutlist = Instance.new("UIListLayout")

				local UIPaddinglist = Instance.new("UIPadding")

				UIListLayoutlist.Name = "UIListLayoutlist"

				UIListLayoutlist.Parent = ScolDown

				UIListLayoutlist.SortOrder = Enum.SortOrder.LayoutOrder

				UIListLayoutlist.Padding = UDim.new(0, 5)

				UIPaddinglist.Name = "UIPaddinglist"

				UIPaddinglist.Parent = ScolDown

				UIPaddinglist.PaddingTop = UDim.new(0, 5)

				UIPaddinglist.PaddingLeft = UDim.new(0, 12)

				local ButtonDrop = Instance.new("TextButton")

				ButtonDrop.Parent = DropFrame

				ButtonDrop.Name = "ButtonDrop"

				ButtonDrop.BackgroundColor3 = Color3.fromRGB(0,250,154)

				ButtonDrop.Size = UDim2.new(0, 213, 0, 30)

				ButtonDrop.Font = Enum.Font.SourceSansSemibold

				ButtonDrop.Text = ""

				ButtonDrop.TextColor3 = Color3.fromRGB(155, 155, 155)

				ButtonDrop.TextSize = 13.000

			--   ButtonDrop.AnchorPoint = Vector2.new(0.5, 0.5)

				ButtonDrop.Position = UDim2.new(0., 0, 0., 0)

				ButtonDrop.TextXAlignment = Enum.TextXAlignment.Center

				ButtonDrop.BackgroundTransparency = 1

				ButtonDrop.TextWrapped = true

				ButtonDrop.AutoButtonColor = false

				ButtonDrop.ClipsDescendants = true

				local dog = false

				local FrameSize = 75

				local cout = 0

				for i , v in pairs(option) do

					cout =cout + 1

					if cout == 1 then

						FrameSize = 75

					elseif cout == 2 then

						FrameSize = 110

					elseif cout >= 3 then

						FrameSize = 150

					end

					local ListFrame = Instance.new("Frame")

					ListFrame.Name = "ListFrame"

					ListFrame.Parent = ScolDown

					ListFrame.BackgroundColor3 =  Color3.fromRGB(22553, 23, 23)-- Color3.fromRGB(0,250,154)

					ListFrame.BorderSizePixel = 0

					ListFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

					ListFrame.AnchorPoint = Vector2.new(0.5, 0.5)

					ListFrame.Size = UDim2.new(0, 180, 0, 30) -- UDim2.new(0, 213, 0, 35)

					ListFrame.BackgroundTransparency  = 1

					ListFrame.ClipsDescendants = true

					local TextLabel_TapDro2p = Instance.new("TextLabel")

					TextLabel_TapDro2p.Parent = ListFrame

					TextLabel_TapDro2p.Name =  tostring(v).."Dropdown"

					TextLabel_TapDro2p.BackgroundColor3 = Color3.fromRGB(0,250,154)

					TextLabel_TapDro2p.Position = UDim2.new(0.5, 0, 0.5, 0)

					TextLabel_TapDro2p.Size =  UDim2.new(0, 180, 0, 30)

					TextLabel_TapDro2p.Font = Enum.Font.SourceSansSemibold

					TextLabel_TapDro2p.Text = tostring(v)

					TextLabel_TapDro2p.TextColor3 = Color3.fromRGB(155, 155, 155)

					TextLabel_TapDro2p.TextSize = 14.000

					TextLabel_TapDro2p.AnchorPoint = Vector2.new(0.5, 0.5)

					TextLabel_TapDro2p.BackgroundTransparency = 1

					TextLabel_TapDro2p.TextXAlignment = Enum.TextXAlignment.Center

					local ButtonDrop2 = Instance.new("TextButton")

					ButtonDrop2.Parent = ListFrame

					ButtonDrop2.Name = "ButtonDrop2"

					ButtonDrop2.BackgroundColor3 = Color3.fromRGB(0,250,154)

					ButtonDrop2.Size = UDim2.new(0, 213, 0, 30)

					ButtonDrop2.Font = Enum.Font.SourceSansSemibold

					ButtonDrop2.Text = ""

					ButtonDrop2.TextColor3 = Color3.fromRGB(155, 155, 155)

					ButtonDrop2.TextSize = 13.000

				--   ButtonDrop2.AnchorPoint = Vector2.new(0.5, 0.5)

					ButtonDrop2.Position = UDim2.new(0., 0, 0., 0)

					ButtonDrop2.TextXAlignment = Enum.TextXAlignment.Center

					ButtonDrop2.BackgroundTransparency = 1

					ButtonDrop2.TextWrapped = true

					ButtonDrop2.AutoButtonColor = false

					ButtonDrop2.ClipsDescendants = true

					ButtonDrop2.MouseEnter:Connect(function ()

						TweenService:Create(

							TextLabel_TapDro2p,

							TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

						):Play()

					end)

					ButtonDrop2.MouseLeave:Connect(function ()

						TweenService:Create(

							TextLabel_TapDro2p,

							TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

						):Play()

					end)

					ButtonDrop2.MouseButton1Click:Connect(function()

						TweenService:Create(

							DropFrame,

							TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{Size = UDim2.new(0, 213, 0, 30)} -- UDim2.new(0, 128, 0, 25)

						):Play()

						TweenService:Create(

							DropArbt_listimage,

							TweenInfo.new(0.3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),

							{Rotation = 0}

						):Play()

						TextLabel_TapDrop.Text =  text.." : "..tostring(v)

						callback(v)

						dog = not dog

					end

				)

					ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

				end

				DropFrame.MouseEnter:Connect(function()

					TweenService:Create(

						DropFrameStroke,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextLabel_TapDrop,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						DropArbt_listimage,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{ImageColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

			DropFrame.MouseLeave:Connect(function()

					TweenService:Create(

						DropFrameStroke,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0.7} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextLabel_TapDrop,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						DropArbt_listimage,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{ImageColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

			ButtonDrop.MouseButton1Click:Connect(function()

				if dog == false then

					TweenService:Create(

						DropFrame,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Size = UDim2.new(0, 213, 0, FrameSize)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						DropArbt_listimage,

						TweenInfo.new(0.3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),

						{Rotation = -180}

					):Play()

					ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

				else

					TweenService:Create(

						DropFrame,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Size = UDim2.new(0, 213, 0, 30)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						DropArbt_listimage,

						TweenInfo.new(0.3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),

						{Rotation = 0}

					):Play()

					ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

				end

				dog = not dog

			end

		)

		ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

			local dropfunc = {}

			function dropfunc:Clear()

				TextLabel_TapDrop.Text = tostring(text).." :"

				for i, v in next, ScolDown:GetChildren() do

					if v:IsA("Frame") then

						v:Destroy()

					end

				end

				ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

			end

			function dropfunc:Add(t)

				local ListFrame = Instance.new("Frame")

				ListFrame.Name = "ListFrame"

				ListFrame.Parent = ScolDown

				ListFrame.BackgroundColor3 =  Color3.fromRGB(22553, 23, 23)-- Color3.fromRGB(0,250,154)

				ListFrame.BorderSizePixel = 0

				ListFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

				ListFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				ListFrame.Size = UDim2.new(0, 180, 0, 30) -- UDim2.new(0, 213, 0, 35)

				ListFrame.BackgroundTransparency  = 1

				ListFrame.ClipsDescendants = true

				local TextLabel_TapDro2p = Instance.new("TextLabel")

				TextLabel_TapDro2p.Parent = ListFrame

				TextLabel_TapDro2p.Name =  tostring(t).."Dropdown"

				TextLabel_TapDro2p.BackgroundColor3 = Color3.fromRGB(0,250,154)

				TextLabel_TapDro2p.Position = UDim2.new(0.5, 0, 0.5, 0)

				TextLabel_TapDro2p.Size =  UDim2.new(0, 180, 0, 30)

				TextLabel_TapDro2p.Font = Enum.Font.SourceSansSemibold

				TextLabel_TapDro2p.Text = tostring(t)

				TextLabel_TapDro2p.TextColor3 = Color3.fromRGB(155, 155, 155)

				TextLabel_TapDro2p.TextSize = 14.000

				TextLabel_TapDro2p.AnchorPoint = Vector2.new(0.5, 0.5)

				TextLabel_TapDro2p.BackgroundTransparency = 1

				TextLabel_TapDro2p.TextXAlignment = Enum.TextXAlignment.Center

				local ButtonDrop2 = Instance.new("TextButton")

				ButtonDrop2.Parent = ListFrame

				ButtonDrop2.Name = "ButtonDrop2"

				ButtonDrop2.BackgroundColor3 = Color3.fromRGB(0,250,154)

				ButtonDrop2.Size = UDim2.new(0, 213, 0, 30)

				ButtonDrop2.Font = Enum.Font.SourceSansSemibold

				ButtonDrop2.Text = ""

				ButtonDrop2.TextColor3 = Color3.fromRGB(155, 155, 155)

				ButtonDrop2.TextSize = 13.000

			--   ButtonDrop2.AnchorPoint = Vector2.new(0.5, 0.5)

				ButtonDrop2.Position = UDim2.new(0., 0, 0., 0)

				ButtonDrop2.TextXAlignment = Enum.TextXAlignment.Center

				ButtonDrop2.BackgroundTransparency = 1

				ButtonDrop2.TextWrapped = true

				ButtonDrop2.AutoButtonColor = false

				ButtonDrop2.ClipsDescendants = true

				ButtonDrop2.MouseEnter:Connect(function ()

					TweenService:Create(

						TextLabel_TapDro2p,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end)

				ButtonDrop2.MouseLeave:Connect(function ()

					TweenService:Create(

						TextLabel_TapDro2p,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end)

				ButtonDrop2.MouseButton1Click:Connect(function()

					TweenService:Create(

						DropFrame,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Size = UDim2.new(0, 213, 0, 30)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						DropArbt_listimage,

						TweenInfo.new(0.3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),

						{Rotation = 0}

					):Play()

					TextLabel_TapDrop.Text =  text.." : "..tostring(t)

					callback(t)

					dog = not dog

				end

			)

				ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

			end

			return dropfunc

		else

			local location = option.location or self.flags

			local flag = not use and option.flag or ""

			local callback = callback or function() end

			local list = option.list or {}

			local default = list.default or list[1].Name

			if not use then

				location[flag] = default

			end

			local DropFrame = Instance.new("Frame")

			DropFrame.Name = "DropFrame"

			DropFrame.Parent = ScrollingFrame_Pageframe

			DropFrame.BackgroundColor3 =  Color3.fromRGB(23, 23, 23)-- Color3.fromRGB(0,250,154)

			DropFrame.BorderSizePixel = 0

			DropFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

			DropFrame.AnchorPoint = Vector2.new(0.5, 0.5)

			DropFrame.Size = UDim2.new(0, 213, 0, 30) -- UDim2.new(0, 213, 0, 35)

			DropFrame.BackgroundTransparency  = 0

			DropFrame.ClipsDescendants = true

			local ConnerDropFrame = Instance.new("UICorner")

			ConnerDropFrame.CornerRadius = UDim.new(0, 4)

			ConnerDropFrame.Name = ""

			ConnerDropFrame.Parent = DropFrame

			local DropFrameStroke = Instance.new("UIStroke")

			DropFrameStroke.Thickness = 1

			DropFrameStroke.Name = ""

			DropFrameStroke.Parent = DropFrame

			DropFrameStroke.LineJoinMode = Enum.LineJoinMode.Round

			DropFrameStroke.Color = Color3.fromRGB(0,250,154)

			DropFrameStroke.Transparency = 0.7

			local LabelFrameDrop = Instance.new("TextLabel")

			LabelFrameDrop.Parent = DropFrame

			LabelFrameDrop.Name = "LabelFrameDrop"

			LabelFrameDrop.BackgroundColor3 = Color3.fromRGB(0,250,154)

			LabelFrameDrop.Position = UDim2.new(0., 0, 0., 0)

			LabelFrameDrop.Size =    UDim2.new(0, 213, 0, 30)

			LabelFrameDrop.Font = Enum.Font.SourceSansSemibold

			LabelFrameDrop.Text = ""

			LabelFrameDrop.TextColor3 = Color3.fromRGB(155, 155, 155)

			LabelFrameDrop.TextSize = 14.000

		--   LabelFrameDrop.AnchorPoint = Vector2.new(0.5, 0.5)

			LabelFrameDrop.BackgroundTransparency = 1

			LabelFrameDrop.TextXAlignment = Enum.TextXAlignment.Left

			local TextLabel_TapDrop = Instance.new("TextLabel")

			TextLabel_TapDrop.Parent = LabelFrameDrop

			TextLabel_TapDrop.Name = "TextLabel_TapDrop"

			TextLabel_TapDrop.BackgroundColor3 = Color3.fromRGB(0,250,154)

			TextLabel_TapDrop.Position = UDim2.new(0.04, 0, 0.14, 0)

			TextLabel_TapDrop.Size =    UDim2.new(0, 140, 0, 20)

			TextLabel_TapDrop.Font = Enum.Font.SourceSansSemibold

			TextLabel_TapDrop.Text = tostring(text).." :"

			TextLabel_TapDrop.TextColor3 = Color3.fromRGB(155, 155, 155)

			TextLabel_TapDrop.TextSize = 14.000

	--     TextLabel_TapDrop.AnchorPoint = Vector2.new(0.5, 0.5)

			TextLabel_TapDrop.BackgroundTransparency = 1

			TextLabel_TapDrop.TextXAlignment = Enum.TextXAlignment.Left

			local DropArbt_listimage = Instance.new("ImageButton")

			DropArbt_listimage.Parent = LabelFrameDrop

			DropArbt_listimage.BackgroundTransparency = 1.000

			DropArbt_listimage.AnchorPoint = Vector2.new(0.5, 0.5)

			DropArbt_listimage.Position = UDim2.new(0.9, 0, 0.5, 0)

			DropArbt_listimage.BorderSizePixel = 0

			DropArbt_listimage.Size = UDim2.new(0, 25, 0, 25)

			DropArbt_listimage.Image = "http://www.roblox.com/asset/?id=6031091004"

			DropArbt_listimage.ImageColor3 = Color3.fromRGB(155, 155, 155)

			local ScolDown = Instance.new("ScrollingFrame")

			ScolDown.Name = "ScolDown"

			ScolDown.Position = UDim2.new(0.02, 0, 1., 0)

			ScolDown.Parent = LabelFrameDrop

			ScolDown.Active = true

			ScolDown.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

			ScolDown.BorderSizePixel = 0

			ScolDown.Size = UDim2.new(0, 205, 0, 115)

			ScolDown.ScrollBarThickness = 3

			ScolDown.ClipsDescendants = true

			ScolDown.BackgroundTransparency = 1

			ScolDown.CanvasSize = UDim2.new(0, 0, 0, 2)

			local UIListLayoutlist = Instance.new("UIListLayout")

			local UIPaddinglist = Instance.new("UIPadding")

			UIListLayoutlist.Name = "UIListLayoutlist"

			UIListLayoutlist.Parent = ScolDown

			UIListLayoutlist.SortOrder = Enum.SortOrder.LayoutOrder

			UIListLayoutlist.Padding = UDim.new(0, 5)

			UIPaddinglist.Name = "UIPaddinglist"

			UIPaddinglist.Parent = ScolDown

			UIPaddinglist.PaddingTop = UDim.new(0, 5)

			UIPaddinglist.PaddingLeft = UDim.new(0, 12)

			local ButtonDrop = Instance.new("TextButton")

			ButtonDrop.Parent = DropFrame

			ButtonDrop.Name = "ButtonDrop"

			ButtonDrop.BackgroundColor3 = Color3.fromRGB(0,250,154)

			ButtonDrop.Size = UDim2.new(0, 213, 0, 30)

			ButtonDrop.Font = Enum.Font.SourceSansSemibold

			ButtonDrop.Text = ""

			ButtonDrop.TextColor3 = Color3.fromRGB(155, 155, 155)

			ButtonDrop.TextSize = 13.000

		--   ButtonDrop.AnchorPoint = Vector2.new(0.5, 0.5)

			ButtonDrop.Position = UDim2.new(0., 0, 0., 0)

			ButtonDrop.TextXAlignment = Enum.TextXAlignment.Center

			ButtonDrop.BackgroundTransparency = 1

			ButtonDrop.TextWrapped = true

			ButtonDrop.AutoButtonColor = false

			ButtonDrop.ClipsDescendants = true

			local dog = false

			local FrameSize = 75

			local cout = 0

			for i , v in pairs(list) do

				cout =cout + 1

				if cout == 1 then

					FrameSize = 75

				elseif cout == 2 then

					FrameSize = 110

				elseif cout >= 3 then

					FrameSize = 150

				end

				local listtog = Instance.new("Frame")

				listtog.Name = "listtog"

				listtog.Parent = ScolDown

				listtog.BackgroundColor3 = Color3.fromRGB(23, 23, 23)

				listtog.BackgroundTransparency =1

				listtog.BorderSizePixel = 0

				listtog.ClipsDescendants = true

				listtog.AnchorPoint = Vector2.new(0.5, 0.5)

				listtog.Position = UDim2.new(0.5, 0, 0.5, 0)

				listtog.Size = UDim2.new(0, 210, 0, 33)

				local listtextbutton = Instance.new("TextButton")

				listtextbutton.Parent = listtog

				listtextbutton.BackgroundTransparency =1

				listtextbutton.BackgroundColor3 = Color3.fromRGB(35, 35, 35)

				listtextbutton.BorderSizePixel = 0

				listtextbutton.Size =  UDim2.new(0, 210, 0, 33)

				listtextbutton.AutoButtonColor = false

				listtextbutton.Font = Enum.Font.SourceSans

				listtextbutton.Text = " "

				listtextbutton.TextColor3 = Color3.fromRGB(0, 0, 0)

				listtextbutton.TextSize = 14.000

				local farmtoglist = Instance.new("TextButton")

				farmtoglist.Parent = listtextbutton

				farmtoglist.BackgroundColor3 = Color3.fromRGB(0,250,154)

				farmtoglist.BorderColor3 = Color3.fromRGB(0,250,154)

				farmtoglist.BorderSizePixel = 0

				farmtoglist.AnchorPoint = Vector2.new(0.5, 0.5)

				farmtoglist.Position = UDim2.new(0.1, 0, 0.5, 0)

				farmtoglist.Size = UDim2.new(0, 23, 0, 23)

				farmtoglist.Font = Enum.Font.SourceSans

				farmtoglist.Text = " "

				farmtoglist.TextColor3 = Color3.fromRGB(0, 0, 0)

				farmtoglist.TextSize = 14.000

				farmtoglist.AutoButtonColor = false

				local farmtoglist2 = Instance.new("TextButton")

				farmtoglist2.Parent = farmtoglist

				farmtoglist2.BackgroundColor3 = Color3.fromRGB(32, 32,32)

				farmtoglist2.BorderColor3 = Color3.fromRGB(0,250,154)

				farmtoglist2.BorderSizePixel = 0

				farmtoglist2.AnchorPoint = Vector2.new(0.5, 0.5)

				farmtoglist2.Position = UDim2.new(0.5, 0, 0.5, 0)

				farmtoglist2.Size = UDim2.new(0, 21, 0, 21)

				farmtoglist2.Font = Enum.Font.SourceSans

				farmtoglist2.Text = " "

				farmtoglist2.TextColor3 = Color3.fromRGB(0, 0, 0)

				farmtoglist2.TextSize = 14.000

				farmtoglist2.AutoButtonColor = false

				local listimage = Instance.new("ImageButton")

				listimage.Parent = farmtoglist2

				listimage.BackgroundTransparency = 1.000

				listimage.AnchorPoint = Vector2.new(0.5, 0.5)

				listimage.Position = UDim2.new(0.5, 0, 0.5, 0)

				listimage.BorderSizePixel = 0

				listimage.Size = UDim2.new(0, 0, 0, 0)

				listimage.Image = "http://www.roblox.com/asset/?id=5880482965"

				local textlist = Instance.new("TextLabel")

				textlist.Parent = listtextbutton

				textlist.Name = "textlist"

				textlist.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				textlist.BackgroundTransparency = 1.000

				textlist.AnchorPoint = Vector2.new(0.5, 0.5)

				textlist.Position = UDim2.new(0.5, 0, 0.5, 0)

				textlist.BorderSizePixel = 0

				textlist.Size = UDim2.new(0, 91, 0, 25)

				textlist.Font = Enum.Font.GothamSemibold

				textlist.Text = tostring(v.Name)

				textlist.TextColor3 = Color3.fromRGB(255, 255, 255)

				textlist.TextSize = 13.000

				local TextButton_Pageframe_Uiconner2 = Instance.new("UICorner")

				TextButton_Pageframe_Uiconner2.CornerRadius = UDim.new(0, 5)

				TextButton_Pageframe_Uiconner2.Name = ""

				TextButton_Pageframe_Uiconner2.Parent = farmtoglist

				local TextButton_Pageframe_Uiconner22 = Instance.new("UICorner")

				TextButton_Pageframe_Uiconner22.CornerRadius = UDim.new(0, 5)

				TextButton_Pageframe_Uiconner22.Name = ""

				TextButton_Pageframe_Uiconner22.Parent = farmtoglist2

				listtextbutton.MouseButton1Click:Connect(function()

					if not  location[v.flag] then

						listimage:TweenSizeAndPosition(UDim2.new(0, 30, 0, 30), UDim2.new(0.5, 0, 0.5, 0), "In", "Bounce", 0.1, true)

						wait(0.1)

						listimage:TweenSizeAndPosition(UDim2.new(0, 23, 0, 23), UDim2.new(0.5, 0, 0.5, 0), "In", "Bounce", 0.1, true)

					else

						listimage:TweenSizeAndPosition(UDim2.new(0, 30, 0, 30), UDim2.new(0.5, 0, 0.5, 0), "In", "Bounce", 0.1, true)

						wait(0.1)

						listimage:TweenSizeAndPosition(UDim2.new(0, 0, 0, 0), UDim2.new(0.5, 0, 0.5, 0), "In", "Bounce", 0.1, true)

					end

					location[v.flag] = not location[v.flag]

					callback(location[v.flag])

				end

			)

			if  location[v.flag] then

				listimage:TweenSizeAndPosition(UDim2.new(0, 30, 0, 30), UDim2.new(0.5, 0, 0.5, 0), "In", "Bounce", 0.1, true)

				wait(0.1)

				listimage:TweenSizeAndPosition(UDim2.new(0, 23, 0, 23), UDim2.new(0.5, 0, 0.5, 0), "In", "Bounce", 0.1, true)

				callback(location[v.flag])

			end

				ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

			end

			DropFrame.MouseEnter:Connect(function()

				TweenService:Create(

					DropFrameStroke,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{Transparency = 0} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					TextLabel_TapDrop,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					DropArbt_listimage,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{ImageColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

				):Play()

			end

		)

		DropFrame.MouseLeave:Connect(function()

				TweenService:Create(

					DropFrameStroke,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{Transparency = 0.7} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					TextLabel_TapDrop,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					DropArbt_listimage,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{ImageColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

				):Play()

			end

		)

		ButtonDrop.MouseButton1Click:Connect(function()

			if dog == false then

				TweenService:Create(

					DropFrame,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{Size = UDim2.new(0, 213, 0, FrameSize)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					DropArbt_listimage,

					TweenInfo.new(0.3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),

					{Rotation = -180}

				):Play()

				ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

			else

				TweenService:Create(

					DropFrame,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{Size = UDim2.new(0, 213, 0, 30)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					DropArbt_listimage,

					TweenInfo.new(0.3, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),

					{Rotation = 0}

				):Play()

				ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

			end

			dog = not dog

		end

	)

	ScolDown.CanvasSize = UDim2.new(0,0,0,UIListLayoutlist.AbsoluteContentSize.Y + 10  )

			end

			end

			function items:TextBox(text,text2,callback)

				local TextFrame = Instance.new("Frame")

				TextFrame.Name = "TextFrame"

				TextFrame.Parent = ScrollingFrame_Pageframe

				TextFrame.BackgroundColor3 =  Color3.fromRGB(23, 23, 23)

				TextFrame.BorderSizePixel = 0

				TextFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

				TextFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				TextFrame.Size = UDim2.new(0, 213, 0, 70)

				TextFrame.BackgroundTransparency  = 1

				TextFrame.ClipsDescendants = true

				local LabelNameSliderxd = Instance.new("TextLabel")

				LabelNameSliderxd.Parent = TextFrame

				LabelNameSliderxd.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				LabelNameSliderxd.BackgroundTransparency = 1

				LabelNameSliderxd.BorderSizePixel = 0

				LabelNameSliderxd.Position = UDim2.new(0.5, 0, 0.2, 0)

				LabelNameSliderxd.AnchorPoint = Vector2.new(0.5, 0.5)

				LabelNameSliderxd.Size = UDim2.new(0, 160, 0, 20)

				LabelNameSliderxd.Font = Enum.Font.GothamBold

				LabelNameSliderxd.Text = tostring(text)

				LabelNameSliderxd.TextColor3 = Color3.fromRGB(155, 155, 155)

				LabelNameSliderxd.TextSize = 11.000

				LabelNameSliderxd.TextXAlignment = Enum.TextXAlignment.Center

				local ConerTextBox = Instance.new("UICorner")

				ConerTextBox.CornerRadius = UDim.new(0, 4)

				ConerTextBox.Name = ""

				ConerTextBox.Parent = TextFrame

				local FrameBox = Instance.new("Frame")

				FrameBox.Name = "TextFrame"

				FrameBox.Parent = TextFrame

				FrameBox.BackgroundColor3 =  Color3.fromRGB(23, 23, 23)

				FrameBox.BorderSizePixel = 0

				FrameBox.Position = UDim2.new(0.5, 0, 0.65, 0)

				FrameBox.AnchorPoint = Vector2.new(0.5, 0.5)

				FrameBox.Size = UDim2.new(0, 158, 0, 30)

				FrameBox.BackgroundTransparency  = 0.2

				FrameBox.ClipsDescendants = true

				FrameBox.AnchorPoint = Vector2.new(0.5, 0.5)

				local TextFrame2 = Instance.new("TextBox")

				TextFrame2.Parent = FrameBox

				TextFrame2.BackgroundColor3 = Color3.fromRGB(0,250,154)

				TextFrame2.BorderSizePixel = 0

				TextFrame2.ClipsDescendants = true

				TextFrame2.Position = UDim2.new(0.5, 0, 0.5, 0)

				TextFrame2.AnchorPoint = Vector2.new(0.5, 0.5)

				TextFrame2.Size = UDim2.new(0, 158, 0, 35)

				TextFrame2.Font = Enum.Font.GothamSemibold

				TextFrame2.PlaceholderColor3 = Color3.fromRGB(155, 155, 155)

				TextFrame2.PlaceholderText = text2

				TextFrame2.Text = ""

				TextFrame2.TextColor3 = Color3.fromRGB(155, 155, 155)

				TextFrame2.TextSize = 12.000

				TextFrame2.BackgroundTransparency = 1

				local ConerTextBox2 = Instance.new("UICorner")

				ConerTextBox2.CornerRadius = UDim.new(0, 4)

				ConerTextBox2.Name = ""

				ConerTextBox2.Parent = FrameBox

				local TextBoxStroke = Instance.new("UIStroke")

				TextBoxStroke.Thickness = 1

				TextBoxStroke.Name = ""

				TextBoxStroke.Parent = FrameBox

				TextBoxStroke.LineJoinMode = Enum.LineJoinMode.Round

				TextBoxStroke.Color = Color3.fromRGB(0,250,154)

				TextBoxStroke.Transparency = 0.7

				TextFrame.MouseEnter:Connect(function()

					TweenService:Create(

						FrameBox,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Size = UDim2.new(0, 213, 0, 30)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						FrameBox,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 = Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextFrame2,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{PlaceholderColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextFrame2,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						LabelNameSliderxd,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextBoxStroke,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Thickness = 0} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

			TextFrame.MouseLeave:Connect(function()

				TweenService:Create(

					FrameBox,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{Size = UDim2.new(0, 158, 0, 30)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					FrameBox,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{BackgroundColor3 = Color3.fromRGB(23, 23, 23)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					TextFrame2,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{PlaceholderColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					TextBoxStroke,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{Thickness = 1} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					LabelNameSliderxd,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

				):Play()

				TweenService:Create(

					TextFrame2,

					TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

				):Play()

			end

			)

				TextFrame2.FocusLost:Connect(function ()

					if #TextFrame2.Text > 0 then

						pcall(callback,TextFrame2.Text)

					end

				end)

			end

			function items:Bind(text,bi,callback)

				local BindFrame = Instance.new("Frame")

				BindFrame.Name = "BindFrame"

				BindFrame.Parent = ScrollingFrame_Pageframe

				BindFrame.BackgroundColor3 =  Color3.fromRGB(23, 23, 23)

				BindFrame.BorderSizePixel = 0

				BindFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

				BindFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				BindFrame.Size = UDim2.new(0, 213, 0, 35)

				BindFrame.BackgroundTransparency  = 0

				BindFrame.ClipsDescendants = true

				local BindConner = Instance.new("UICorner")

				BindConner.CornerRadius = UDim.new(0, 4)

				BindConner.Name = ""

				BindConner.Parent = BindFrame

				local BindStroke = Instance.new("UIStroke")

				BindStroke.Thickness = 1

				BindStroke.Name = ""

				BindStroke.Parent = BindFrame

				BindStroke.LineJoinMode = Enum.LineJoinMode.Round

				BindStroke.Color = Color3.fromRGB(0,250,154)

				BindStroke.Transparency = 0.7

				local LabelBind = Instance.new("TextLabel")

				LabelBind.Parent = BindFrame

				LabelBind.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				LabelBind.BackgroundTransparency = 1

				LabelBind.BorderSizePixel = 0

				LabelBind.Position = UDim2.new(0.4, 0, 0.5, 0)

				LabelBind.AnchorPoint = Vector2.new(0.5, 0.5)

				LabelBind.Size = UDim2.new(0, 140, 0, 35)

				LabelBind.Font = Enum.Font.GothamBold

				LabelBind.Text = tostring(text)

				LabelBind.TextColor3 = Color3.fromRGB(155, 155, 155)

				LabelBind.TextSize = 11.000

				LabelBind.TextXAlignment = Enum.TextXAlignment.Left

				local key = bi.Name

				local LabelBind2 = Instance.new("TextButton")

				LabelBind2.Parent = BindFrame

				LabelBind2.Name = "LabelBind2"

				LabelBind2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				LabelBind2.Size = UDim2.new(0, 100, 0, 19)

				LabelBind2.Font = Enum.Font.GothamBold

				LabelBind2.Text =  "KEY : "..key

				LabelBind2.TextColor3 = Color3.fromRGB(155, 155, 155)

				LabelBind2.TextSize = 11.000

				LabelBind2.AnchorPoint = Vector2.new(0.5, 0.5)

				LabelBind2.Position = UDim2.new(0.75, 0, 0.5, 0)

				LabelBind2.TextXAlignment = Enum.TextXAlignment.Center

				LabelBind2.BackgroundTransparency = 1

				LabelBind2.TextWrapped = true

				local LabelBind22 = Instance.new("TextButton")

				LabelBind22.Parent = BindFrame

				LabelBind22.Name = "LabelBind22"

				LabelBind22.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				LabelBind22.Size = UDim2.new(0, 213, 0, 35)

				LabelBind22.Font = Enum.Font.GothamBold

				LabelBind22.Text =  ""

				LabelBind22.TextColor3 = Color3.fromRGB(155, 155, 155)

				LabelBind22.TextSize = 11.000

				LabelBind22.AnchorPoint = Vector2.new(0.5, 0.5)

				LabelBind22.Position = UDim2.new(0.5, 0, 0.5, 0)

				LabelBind22.TextXAlignment = Enum.TextXAlignment.Center

				LabelBind22.BackgroundTransparency = 1

				LabelBind22.TextWrapped = true

				BindFrame.MouseEnter:Connect(function()

					TweenService:Create(

						BindStroke,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						LabelBind22,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						LabelBind2,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						LabelBind,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

				BindFrame.MouseLeave:Connect(function()

					TweenService:Create(

						BindStroke,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0.7} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						LabelBind22,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						LabelBind2,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						LabelBind,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

				end

			)

				LabelBind22.MouseButton1Click:Connect(function ()

					LabelBind2.Text = "KEY : ".."..."

					local inputwait = game:GetService("UserInputService").InputBegan:wait(0.2)

					local fuckulop = inputwait.KeyCode == Enum.KeyCode.Unknown and inputwait.UserInputType or inputwait.KeyCode

					if

					fuckulop.Name ~= "Focus" and fuckulop.Name ~= "MouseMovement" and fuckulop.Name ~= "Focus"

					then

						LabelBind2.Text =  "KEY : "..fuckulop.Name

						key = fuckulop.Name

					end

					-- if fuckulop.Name ~= "Unknown" then

					--     LabelBind2.Text = fuckulop.Name

					--     key = fuckulop.Name

					-- end

				end)

				game:GetService("UserInputService").InputBegan:connect(

					function(current)

						local fuckulop2 = current.KeyCode == Enum.KeyCode.Unknown and current.UserInputType or current.KeyCode

							if fuckulop2.Name ==  key then

								pcall(callback)

						end

					end

					)

			end

			function items:Line()

				local LineFrame = Instance.new("Frame")

				LineFrame.Name = "LineFrame"

				LineFrame.Parent = ScrollingFrame_Pageframe

				LineFrame.BackgroundColor3 =  Color3.fromRGB(127,255,212)

				LineFrame.BorderSizePixel = 0

    			LineFrame.Position = UDim2.new(0.5, 0, 0.5, 0)

				LineFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				LineFrame.Size = UDim2.new(0, 213, 0, 2)

				LineFrame.BackgroundTransparency  = 0

				LineFrame.ClipsDescendants = true

                

                

				local LineFrame_BindConner = Instance.new("UICorner")

				LineFrame_BindConner.CornerRadius = UDim.new(60, 60)

				LineFrame_BindConner.Name = ""

				LineFrame_BindConner.Parent = LineFrame

			end

			function items:Color(text,preset,callback)

				local Pixker = Instance.new("Frame")

				Pixker.Name = "Pixker"

				Pixker.Parent = ScrollingFrame_Pageframe

				Pixker.BackgroundColor3 = Color3.fromRGB(23, 23, 23)

				Pixker.Position = UDim2.new(0.0833333358, 0, 0.235135213, 0)

				Pixker.Size = UDim2.new(0, 213, 0, 33)

				Pixker.BackgroundTransparency = 0

				Pixker.BorderSizePixel = 0

				Pixker.AnchorPoint = Vector2.new(0.5, 0.5)

				Pixker.Position = UDim2.new(0.5, 0, 0.5, 0)

				Pixker.ClipsDescendants = true

				local BoxColorCorner2 = Instance.new("UICorner")

				BoxColorCorner2.CornerRadius = UDim.new(0, 4)

				BoxColorCorner2.Name = "BoxColorCorner"

				BoxColorCorner2.Parent = Pixker

				local MheeFrameStroke = Instance.new("UIStroke")

				MheeFrameStroke.Thickness = 1

				MheeFrameStroke.Name = ""

				MheeFrameStroke.Parent = Pixker

				MheeFrameStroke.LineJoinMode = Enum.LineJoinMode.Round

				MheeFrameStroke.Color = Color3.fromRGB(0,250,154)

				MheeFrameStroke.Transparency = 0.7

				local TextFrameColor = Instance.new("TextLabel")

				TextFrameColor.Parent = Pixker

				TextFrameColor.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				TextFrameColor.BorderSizePixel = 0

				TextFrameColor.Size = UDim2.new(0, 200, 0, 34)

				TextFrameColor.Font = Enum.Font.SourceSans

				TextFrameColor.Text = "  "

				TextFrameColor.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextFrameColor.TextSize = 14.000

				TextFrameColor.BackgroundTransparency = 1

				TextFrameColor.Position = UDim2.new(0., 0, 0., 0)

				local TextReal = Instance.new("TextLabel")

				TextReal.Parent = TextFrameColor

				TextReal.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				TextReal.BorderSizePixel = 0

				TextReal.Size = UDim2.new(0, 140, 0, 34)

				TextReal.Font = Enum.Font.GothamSemibold

				TextReal.Text = text

				TextReal.TextColor3 = Color3.fromRGB(155,155, 155)

				TextReal.TextSize = 12.000

				TextReal.BackgroundTransparency = 1

				TextReal.Position = UDim2.new(0.05, 0, 0., 0)

				TextReal.TextXAlignment = Enum.TextXAlignment.Left

				local BoxColor = Instance.new("Frame")

				BoxColor.Name = "BoxColor"

				BoxColor.Parent = TextFrameColor

				BoxColor.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

				BoxColor.Position = UDim2.new(0.85, 0, 0.5, 0)

				BoxColor.Size = UDim2.new(0, 35, 0, 19)

				BoxColor.AnchorPoint = Vector2.new(0.5, 0.5)

				local BoxColorCorner = Instance.new("UICorner")

				BoxColorCorner.CornerRadius = UDim.new(0, 4)

				BoxColorCorner.Name = "BoxColorCorner"

				BoxColorCorner.Parent = BoxColor

				local TextButton_Dropdown = Instance.new("TextButton")

				TextButton_Dropdown.Parent = TextFrameColor

				TextButton_Dropdown.BackgroundColor3 = Color3.fromRGB(45, 45, 45)

				TextButton_Dropdown.BorderSizePixel = 0

				TextButton_Dropdown.Position = UDim2.new(0., 0, 0.14705883, 0)

				TextButton_Dropdown.Size = UDim2.new(0, 200, 0, 33)

				TextButton_Dropdown.Font = Enum.Font.SourceSans

				TextButton_Dropdown.Text = "  "

				TextButton_Dropdown.TextColor3 = Color3.fromRGB(0, 0, 0)

				TextButton_Dropdown.TextSize = 14.000

				TextButton_Dropdown.AutoButtonColor = false

				--TextButton_Dropdown.AnchorPoint = Vector2.new(0.5, 0.5)

				TextButton_Dropdown.Position = UDim2.new(0, 0, 0, 0)

				TextButton_Dropdown.BackgroundTransparency = 1

				Pixker.MouseEnter:Connect(function()

					TweenService:Create(

						MheeFrameStroke,

						TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0.}

					):Play()

					TweenService:Create(

						TextReal,

						TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(255,255, 255)}

					):Play()

				end)

				Pixker.MouseLeave:Connect(function()

					TweenService:Create(

						MheeFrameStroke,

						TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency = 0.7}

					):Play()

					TweenService:Create(

						TextReal,

						TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{TextColor3 = Color3.fromRGB(155,155, 155)}

					):Play()

				end)

			-- Rainbow Toggle

			local TextButton_2_Toggle = Instance.new("TextButton")

			TextButton_2_Toggle.Parent = TextFrameColor

			TextButton_2_Toggle.BackgroundColor3 = Color3.fromRGB(155, 155, 155)

	--        TextButton_2_Toggle.BorderColor3 = Color3.fromRGB(0,250,154)

			TextButton_2_Toggle.BorderSizePixel = 0

			TextButton_2_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

			TextButton_2_Toggle.Position = UDim2.new(0.2, 0, 1.87, 0)

			TextButton_2_Toggle.Size = UDim2.new(0, 30, 0, 13)

			TextButton_2_Toggle.Font = Enum.Font.SourceSans

			TextButton_2_Toggle.Text = " "

			TextButton_2_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

			TextButton_2_Toggle.TextSize = 12.000

			TextButton_2_Toggle.AutoButtonColor = false

			local TextButton_Pageframe_Uiconner = Instance.new("UICorner")

			TextButton_Pageframe_Uiconner.CornerRadius = UDim.new(0, 30)

			TextButton_Pageframe_Uiconner.Name = ""

			TextButton_Pageframe_Uiconner.Parent = TextButton_2_Toggle

			local TextButton_3_Toggle = Instance.new("TextButton")

			TextButton_3_Toggle.Parent = TextButton_2_Toggle

			TextButton_3_Toggle.BackgroundColor3 = Color3.fromRGB(255, 255,255)

	--        TextButton_3_Toggle.BorderColor3 = Color3.fromRGB(0,250,154)

			TextButton_3_Toggle.BorderSizePixel = 0

			TextButton_3_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

			TextButton_3_Toggle.Position = UDim2.new(0.1, 0, 0.5, 0)

			TextButton_3_Toggle.Size = UDim2.new(0, 19, 0, 19)

			TextButton_3_Toggle.Font = Enum.Font.SourceSans

			TextButton_3_Toggle.Text = " "

			TextButton_3_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

			TextButton_3_Toggle.TextSize = 12.000

			TextButton_3_Toggle.AutoButtonColor = false

			local TextButton_Pageframe_Uiconner2 = Instance.new("UICorner")

			TextButton_Pageframe_Uiconner2.CornerRadius = UDim.new(0, 30)

			TextButton_Pageframe_Uiconner2.Name = ""

			TextButton_Pageframe_Uiconner2.Parent = TextButton_3_Toggle

			local TextButton_4_Toggle = Instance.new("TextButton")

			TextButton_4_Toggle.Parent = TextButton_3_Toggle

			TextButton_4_Toggle.BackgroundColor3 = Color3.fromRGB(155, 155,155)

	--        TextButton_3_Toggle.BorderColor3 = Color3.fromRGB(0,250,154)

			TextButton_4_Toggle.BorderSizePixel = 0

			TextButton_4_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

			TextButton_4_Toggle.Position = UDim2.new(0.5, 0, 0.5, 0)

			TextButton_4_Toggle.Size = UDim2.new(0, 27, 0, 27-2)

			TextButton_4_Toggle.Font = Enum.Font.SourceSans

			TextButton_4_Toggle.Text = " "

			TextButton_4_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

			TextButton_4_Toggle.TextSize = 12.000

			TextButton_4_Toggle.AutoButtonColor = false

			TextButton_4_Toggle.BackgroundTransparency = 1

			TextButton_4_Toggle.Visible = true

			local TextButton_Pageframe_Uiconner4 = Instance.new("UICorner")

			TextButton_Pageframe_Uiconner4.CornerRadius = UDim.new(0, 30)

			TextButton_Pageframe_Uiconner4.Name = ""

			TextButton_Pageframe_Uiconner4.Parent = TextButton_4_Toggle

			local TextButton_Toggle = Instance.new("TextButton")

			TextButton_Toggle.Parent = ValueFrame

			TextButton_Toggle.BackgroundTransparency =1

			TextButton_Toggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

			TextButton_Toggle.BorderSizePixel = 0

			TextButton_Toggle.Size = UDim2.new(0, 50, 0, 20)

			TextButton_Toggle.AutoButtonColor = false

			TextButton_Toggle.Font = Enum.Font.SourceSans

			TextButton_Toggle.Text = " "

			TextButton_Toggle.TextColor3 = Color3.fromRGB(0, 0, 0)

			TextButton_Toggle.TextSize = 12.000

			TextButton_Toggle.AnchorPoint = Vector2.new(0.5, 0.5)

			TextButton_Toggle.Position = UDim2.new(1.25, 0, 0.4, 0)

			local TextButton_3_Toggle2 = Instance.new("TextLabel")

			TextButton_3_Toggle2.Parent = TextButton_2_Toggle

			TextButton_3_Toggle2.BackgroundColor3 = Color3.fromRGB(32, 32,32)

			TextButton_3_Toggle2.BorderColor3 = Color3.fromRGB(0,250,154)

			TextButton_3_Toggle2.BorderSizePixel = 0

			TextButton_3_Toggle2.AnchorPoint = Vector2.new(0.5, 0.5)

			TextButton_3_Toggle2.Position = UDim2.new(1.9, 0, 0.5, 0)

			TextButton_3_Toggle2.Size = UDim2.new(0, 500, 0, 21)

			TextButton_3_Toggle2.Font = Enum.Font.SourceSansBold

			TextButton_3_Toggle2.Text = "Rainbow"

			TextButton_3_Toggle2.TextColor3 = Color3.fromRGB(255, 255, 255)

			TextButton_3_Toggle2.TextSize = 13.000

			TextButton_3_Toggle2.BackgroundTransparency = 1

			local OMF = Instance.new("TextButton")

			OMF.Parent = TextButton_2_Toggle

			OMF.BackgroundTransparency =1

			OMF.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

			OMF.BorderSizePixel = 0

			OMF.Size = UDim2.new(0, 100, 0, 20)

			OMF.AutoButtonColor = false

			OMF.Font = Enum.Font.SourceSans

			OMF.Text = " "

			OMF.TextColor3 = Color3.fromRGB(0, 0, 0)

			OMF.TextSize = 12.000

			OMF.AnchorPoint = Vector2.new(0.5, 0.5)

			OMF.Position = UDim2.new(1.3, 0, 0.5, 0)

			local Color =  Instance.new("ImageLabel")

			Color.Name = "Color"

			Color.Parent = TextFrameColor

			Color.BackgroundColor3 = Color3.fromRGB(255, 0, 4)

			Color.Position = UDim2.new(0.05,0,4,0)

			Color.Size = UDim2.new(0, 195, 0, 40)

			Color.ZIndex = 0

			Color.BorderSizePixel = 0

			Color.Image = "rbxassetid://4155801252"

			local ColorFucj = Instance.new("UICorner")

			ColorFucj.CornerRadius = UDim.new(0, 4)

			ColorFucj.Name = ""

			ColorFucj.Parent = Color

			local ColorSelection =  Instance.new("ImageLabel")

			ColorSelection.Name = "ColorSelection"

			ColorSelection.Parent = Color

			ColorSelection.AnchorPoint = Vector2.new(0.5, 0.5)

			ColorSelection.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

			ColorSelection.BackgroundTransparency = 1.000

			ColorSelection.Position = UDim2.new(preset and select(3, Color3.toHSV(preset)))

			ColorSelection.Size = UDim2.new(0, 18, 0, 18)

			ColorSelection.Image = "http://www.roblox.com/asset/?id=4805639000"

			ColorSelection.ScaleType = Enum.ScaleType.Fit

			ColorSelection.Visible = true

			local Hue =  Instance.new("ImageLabel")

			Hue.Name = "Hue2"

			Hue.Parent = TextFrameColor

			Hue.Position = UDim2.new(0.14,0,3,0)

			Hue.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

			Hue.Size = UDim2.new(0, 160, 0, 25)

			Hue.ZIndex = 0

			Hue.BorderSizePixel = 0

			local ColorFucj2 = Instance.new("UICorner")

			ColorFucj2.CornerRadius = UDim.new(0, 4)

			ColorFucj2.Name = ""

			ColorFucj2.Parent = Hue

			local HueGradient = Instance.new("UIGradient")

			HueGradient.Color = ColorSequence.new {

				ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255, 0, 4)),

				ColorSequenceKeypoint.new(0.20, Color3.fromRGB(234, 255, 0)),

				ColorSequenceKeypoint.new(0.40, Color3.fromRGB(21, 255, 0)),

				ColorSequenceKeypoint.new(0.60, Color3.fromRGB(0, 255, 255)),

				ColorSequenceKeypoint.new(0.80, Color3.fromRGB(0, 17, 255)),

				ColorSequenceKeypoint.new(0.90, Color3.fromRGB(255, 0, 251)),

				ColorSequenceKeypoint.new(1.00, Color3.fromRGB(255, 0, 4))

			}

			HueGradient.Rotation = 0

			HueGradient.Name = "HueGradient"

			HueGradient.Parent = Hue

			local HueSelection =  Instance.new("ImageLabel")

			HueSelection.Name = "HueSelection"

			HueSelection.Parent = Hue

			HueSelection.AnchorPoint = Vector2.new(0.5, 0.5)

			HueSelection.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

			HueSelection.BackgroundTransparency = 1.000

			HueSelection.Position = UDim2.new(preset and select(3, Color3.toHSV(preset)))

			HueSelection.Size = UDim2.new(0, 18, 0, 18)

			HueSelection.Image = "http://www.roblox.com/asset/?id=4805639000"

			HueSelection.ScaleType = Enum.ScaleType.Fit

			HueSelection.Visible = true

			local BTN_XD = Instance.new("TextButton")

			BTN_XD.Parent = TextFrameColor

			BTN_XD.BackgroundColor3 = Color3.fromRGB(0,250,154)

			BTN_XD.BorderColor3 = Color3.fromRGB(0,250,154)

			BTN_XD.BorderSizePixel = 0

			BTN_XD.AnchorPoint = Vector2.new(0.5, 0.5)

			BTN_XD.Position = UDim2.new(0.8, 0, 1.9, 0)

			BTN_XD.Size = UDim2.new(0, 50, 0, 25)

			BTN_XD.Font = Enum.Font.GothamSemibold

			BTN_XD.Text = "Confirm"

			BTN_XD.TextColor3 = Color3.fromRGB(255, 255, 255)

			BTN_XD.TextSize = 11.000

			BTN_XD.AutoButtonColor = false

			local BTN_XD_COnner = Instance.new("UICorner")

			BTN_XD_COnner.CornerRadius = UDim.new(0, 4)

			BTN_XD_COnner.Name = ""

			BTN_XD_COnner.Parent = BTN_XD

			local MheeFrameStroke = Instance.new("UIStroke")

			MheeFrameStroke.Thickness = 1

			MheeFrameStroke.Name = ""

			MheeFrameStroke.Parent = BTN_XD

			MheeFrameStroke.LineJoinMode = Enum.LineJoinMode.Round

			MheeFrameStroke.Color = Color3.fromRGB(0,250,154)

			MheeFrameStroke.Transparency = 0.7

			local UwU = false

			OMF.MouseButton1Click:Connect(function()

				if       UwU == false  then

					TweenService:Create(

						TextButton_4_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_3_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(0,250,154)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_2_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(153, 0, 102)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TextButton_3_Toggle:TweenSizeAndPosition(UDim2.new(0, 19, 0, 19), UDim2.new(1, 0, 0.5, 0), "Out", "Quad", 0.3, true)

				else

					TweenService:Create(

						TextButton_4_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_3_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(255, 255, 255)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TweenService:Create(

						TextButton_2_Toggle,

						TweenInfo.new(0.4, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{BackgroundColor3 =  Color3.fromRGB(155, 155, 155)} -- UDim2.new(0, 128, 0, 25)

					):Play()

					TextButton_3_Toggle:TweenSizeAndPosition(UDim2.new(0, 19, 0, 19), UDim2.new(0.1, 0, 0.5, 0), "Out", "Quad", 0.3, true)

				end

				UwU = not UwU

			end

		)

		OMF.MouseEnter:Connect(function()

				TweenService:Create(

					TextButton_4_Toggle,

					TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{BackgroundTransparency = 0.6} -- UDim2.new(0, 128, 0, 25)

				):Play()

			end

		)

		OMF.MouseLeave:Connect(function()

				TweenService:Create(

					TextButton_4_Toggle,

					TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

					{BackgroundTransparency = 1} -- UDim2.new(0, 128, 0, 25)

				):Play()

			end

		)

		OMF.MouseButton1Down:Connect(

				function()

					RainbowColorPicker = not RainbowColorPicker

					if ColorInput then

						ColorInput:Disconnect()

					end

					if HueInput then

						HueInput:Disconnect()

					end

					if RainbowColorPicker then

						OldToggleColor = BoxColor.BackgroundColor3

						OldColor = Color.BackgroundColor3

						OldColorSelectionPosition = ColorSelection.Position

						OldHueSelectionPosition = HueSelection.Position

						while RainbowColorPicker do

							BoxColor.BackgroundColor3 = Color3.fromHSV(Red.RainbowColorValue, 1, 1)

							Color.BackgroundColor3 = Color3.fromHSV(Red.RainbowColorValue, 1, 1)

							ColorSelection.Position = UDim2.new(1, 0, 0, 0)

							HueSelection.Position = UDim2.new(0,  Red.HueSelectionPosition, 0.5,0)

							pcall(callback, BoxColor.BackgroundColor3)

							wait(0.2)

						end

					elseif not RainbowColorPicker then

						BoxColor.BackgroundColor3 = OldToggleColor

						Color.BackgroundColor3 = OldColor

						ColorSelection.Position = OldColorSelectionPosition

						HueSelection.Position = OldHueSelectionPosition

						pcall(callback, BoxColor.BackgroundColor3)

					end

				end

			)

			TextButton_3_Toggle.MouseButton1Down:Connect(

				function()

					RainbowColorPicker = not RainbowColorPicker

					if ColorInput then

						ColorInput:Disconnect()

					end

					if HueInput then

						HueInput:Disconnect()

					end

					if RainbowColorPicker then

						OldToggleColor = BoxColor.BackgroundColor3

						OldColor = Color.BackgroundColor3

						OldColorSelectionPosition = ColorSelection.Position

						OldHueSelectionPosition = HueSelection.Position

						while RainbowColorPicker do

							BoxColor.BackgroundColor3 = Color3.fromHSV(Red.RainbowColorValue, 1, 1)

							Color.BackgroundColor3 = Color3.fromHSV(Red.RainbowColorValue, 1, 1)

							ColorSelection.Position = UDim2.new(1, 0, 0, 0)

							HueSelection.Position = UDim2.new(0,  Red.HueSelectionPosition, 0.5,0)

							pcall(callback, BoxColor.BackgroundColor3)

							wait(0.2)

						end

					elseif not RainbowColorPicker then

						BoxColor.BackgroundColor3 = OldToggleColor

						Color.BackgroundColor3 = OldColor

						ColorSelection.Position = OldColorSelectionPosition

						HueSelection.Position = OldHueSelectionPosition

						pcall(callback, BoxColor.BackgroundColor3)

					end

				end

			)

			local function UpdateColorPicker(nope)

				BoxColor.BackgroundColor3 = Color3.fromHSV(ColorH, ColorS, ColorV)

				Color.BackgroundColor3 = Color3.fromHSV(ColorH, 1, 1)

				pcall(callback, BoxColor.BackgroundColor3)

			end

			ColorH =

			1 -

			(math.clamp(HueSelection.AbsolutePosition.Y - Hue.AbsolutePosition.Y, 0, Hue.AbsoluteSize.Y) /

				Hue.AbsoluteSize.Y)

			ColorS =

				(math.clamp(ColorSelection.AbsolutePosition.X - Color.AbsolutePosition.X, 0, Color.AbsoluteSize.X) /

					Color.AbsoluteSize.X)

			ColorV =

				1 -

				(math.clamp(ColorSelection.AbsolutePosition.Y - Color.AbsolutePosition.Y, 0, Color.AbsoluteSize.Y) /

					Color.AbsoluteSize.Y)

			BoxColor.BackgroundColor3 = preset

			Color.BackgroundColor3 = preset

			pcall(callback, BoxColor.BackgroundColor3)

			local RainbowColorPicker = false

			Color.InputBegan:Connect(

				function(input)

					if input.UserInputType == Enum.UserInputType.MouseButton1 then

						if RainbowColorPicker then

							return

						end

						if ColorInput then

							ColorInput:Disconnect()

						end

						ColorInput =

							RunService.RenderStepped:Connect(

								function()

								local ColorX =

									(math.clamp(Mouse.X - Color.AbsolutePosition.X, 0, Color.AbsoluteSize.X) /

										Color.AbsoluteSize.X)

								local ColorY =

									(math.clamp(Mouse.Y - Color.AbsolutePosition.Y, 0, Color.AbsoluteSize.Y) /

										Color.AbsoluteSize.Y)

								ColorSelection.Position = UDim2.new(ColorX, 0, ColorY, 0)

								ColorS = ColorX

								ColorV = 1 - ColorY

								UpdateColorPicker(true)

							end

							)

					end

				end

			)

				Color.InputEnded:Connect(

					function(input)

						if input.UserInputType == Enum.UserInputType.MouseButton1 then

							if ColorInput then

								ColorInput:Disconnect()

							end

						end

					end

				)

				Hue.InputBegan:Connect(

					function(input)

						if input.UserInputType == Enum.UserInputType.MouseButton1 then

							if RainbowColorPicker then

								return

							end

							if HueInput then

								HueInput:Disconnect()

							end

							HueInput =

								RunService.RenderStepped:Connect(

									function()

									local HueY =

										(math.clamp(Mouse.Y - Hue.AbsolutePosition.Y, 0, Hue.AbsoluteSize.Y) /

											Hue.AbsoluteSize.Y)

									local HueX =

										(math.clamp(Mouse.X- Hue.AbsolutePosition.X, 0, Hue.AbsoluteSize.X) /

											Hue.AbsoluteSize.X)

									HueSelection.Position = UDim2.new(HueX, 0, HueY, 0)

									ColorH = 1 - HueY

									UpdateColorPicker(true)

								end

								)

						end

					end

				)

				Hue.InputEnded:Connect(

					function(input)

						if input.UserInputType == Enum.UserInputType.MouseButton1 then

							if HueInput then

								HueInput:Disconnect()

							end

						end

					end

				)

				local sk = false

				TextButton_Dropdown.MouseButton1Click:Connect(function()

					if sk == false then

					TweenService:Create(

						Pixker,

						TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Size = UDim2.new(0, 213, 0, 180)}

					):Play()

				else

					TweenService:Create(

						Pixker,

						TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Size = UDim2.new(0, 213, 0, 33)}

					):Play()

				end

				sk = not sk

				end

			)

				BTN_XD.MouseButton1Click:Connect(

					function()

						TweenService:Create(

							Pixker,

							TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

							{Size = UDim2.new(0, 213, 0, 33)}

						):Play()

						sk = not sk

					end

				)

			end

			function items:Label(text,image)

				local labaelchange = {}

				local LabelFrame = Instance.new("Frame")

				LabelFrame.Name = "Mainframenoti"

				LabelFrame.Parent = ScrollingFrame_Pageframe

				LabelFrame.BackgroundColor3 = Color3.fromRGB(23, 23, 23)

				LabelFrame.BackgroundTransparency = 0

				LabelFrame.BorderSizePixel = 0

				LabelFrame.ClipsDescendants = false

				LabelFrame.AnchorPoint = Vector2.new(0.5, 0.5)

				LabelFrame.Position = UDim2.new(0.498, 0, 0.5, 0)

				LabelFrame.Size = UDim2.new(0, 213, 0, 28)

				local LabelFarm2 = Instance.new("TextLabel")

				LabelFarm2.Parent = LabelFrame

				LabelFarm2.Name = "TextLabel_Tap"

				LabelFarm2.BackgroundColor3 = Color3.fromRGB(45, 45, 45)

				LabelFarm2.Size =UDim2.new(0, 130, 0,24 )

				LabelFarm2.Font = Enum.Font.SourceSansSemibold

				LabelFarm2.Text = text

				LabelFarm2.TextColor3 = Color3.fromRGB(255, 255, 255)

				LabelFarm2.TextSize = 12.000

				LabelFarm2.AnchorPoint = Vector2.new(0.5, 0.5)

				LabelFarm2.Position = UDim2.new(0.5, 0, 0.5, 0)

				LabelFarm2.TextXAlignment = Enum.TextXAlignment.Center

				LabelFarm2.BackgroundTransparency = 1

				LabelFarm2.TextWrapped = true

				local ImageLabel_gx = Instance.new("ImageLabel")

				ImageLabel_gx.Parent = LabelFrame

				ImageLabel_gx.BackgroundTransparency = 1.000

				ImageLabel_gx.BorderSizePixel = 0

				ImageLabel_gx.Size = UDim2.new(0, 18, 0, 18)

				ImageLabel_gx.AnchorPoint = Vector2.new(0.5, 0.5)

				ImageLabel_gx.Position = UDim2.new(0.06, 0, 0.45, 0)

				ImageLabel_gx.Image = "http://www.roblox.com/asset/?id="..tostring(image)

				ImageLabel_gx.BackgroundTransparency = 1

				local noticore55 = Instance.new("UICorner")

				noticore55.CornerRadius = UDim.new(0, 4)

				noticore55.Name = ""

				noticore55.Parent = LabelFarm2

				local noticore2777 = Instance.new("UICorner")

				noticore2777.CornerRadius = UDim.new(0, 4)

				noticore2777.Name = ""

				noticore2777.Parent = LabelFrame

				local LabelStroke = Instance.new("UIStroke")

				LabelStroke.Thickness = 1

				LabelStroke.Name = ""

				LabelStroke.Parent = LabelFrame

				LabelStroke.LineJoinMode = Enum.LineJoinMode.Round

				LabelStroke.Color = Color3.fromRGB(0,250,154)

				LabelStroke.Transparency = 0.7

				LabelFrame.MouseEnter:Connect(function()

					TweenService:Create(

						LabelStroke,

						TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency =0}

					):Play()

				end

			)

				LabelFrame.MouseLeave:Connect(function()

					TweenService:Create(

						LabelStroke,

						TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

						{Transparency =0.7}

					):Play()

				end

			)

				function labaelchange:Change(text2)

					LabelFarm2.Text = text2

				end

				return  labaelchange

			end

			return  items

			end

		return  page

		end

	return top

	end
		
    local placeId = game.PlaceId
    if placeId == 2753915549 then
        oldworld = true
    elseif placeId == 4442272183 then
        newworld = true
    elseif placeId == 7449423635 then
        thirdworld = true
    end
    
    FM = false
    sky = false
    
    function CheckQuestLunarHub()
        if oldworld then
            local MyLevel = game.Players.LocalPlayer.Data.Level.Value
            Dis = 300
            if MyLevel == 1 or MyLevel <= 9 then -- Bandit
                magbring = 400
                Ms = "Bandit [Lv. 5]"
                NaemQuest = "BanditQuest1"
                LevelQuest = 1
                NameMon = "Bandit"
                CFrameQuest = CFrame.new(1061.66699, 16.5166187, 1544.52905, -0.942978859, -3.33851502e-09, 0.332852632, 7.04340497e-09, 1, 2.99841325e-08, -0.332852632, 3.06188177e-08, -0.942978859)
                CFrameMon = CFrame.new(1199.31287, 52.2717781, 1536.91516, -0.929782331, 6.60215846e-08, -0.368109822, 3.9077392e-08, 1, 8.06501603e-08, 0.368109822, 6.06023249e-08, -0.929782331)
            elseif MyLevel == 10 or MyLevel <= 14 then -- Monkey
                magbring = 400
                Ms = "Monkey [Lv. 14]"
                NaemQuest = "JungleQuest"
                LevelQuest = 1
                NameMon = "Monkey"
                CFrameQuest = CFrame.new(-1604.12012, 36.8521118, 154.23732, 0.0648873374, -4.70858913e-06, -0.997892559, 1.41431883e-07, 1, -4.70933674e-06, 0.997892559, 1.64442184e-07, 0.0648873374)
                CFrameMon = CFrame.new(-1502.74609, 98.5633316, 90.6417007, 0.836947978, 0, 0.547282517, -0, 1, -0, -0.547282517, 0, 0.836947978)
            elseif MyLevel == 15 or MyLevel <= 29 then -- Gorilla
                magbring = 240
                Ms = "Gorilla [Lv. 20]"
                NaemQuest = "JungleQuest"
                LevelQuest = 2
                NameMon = "Gorilla"
                CFrameQuest = CFrame.new(-1604.12012, 36.8521118, 154.23732, 0.0648873374, -4.70858913e-06, -0.997892559, 1.41431883e-07, 1, -4.70933674e-06, 0.997892559, 1.64442184e-07, 0.0648873374)
                CFrameMon = CFrame.new(-1223.52808, 6.27936459, -502.292664, 0.310949147, -5.66602516e-08, 0.950426519, -3.37275488e-08, 1, 7.06501808e-08, -0.950426519, -5.40241736e-08, 0.310949147)
            elseif MyLevel == 30 or MyLevel <= 39 then -- Pirate
                Dis = 150
                Ms = "Pirate [Lv. 35]"
                NaemQuest = "BuggyQuest1"
                LevelQuest = 1
                NameMon = "Pirate"
                CFrameQuest = CFrame.new(-1139.59717, 4.75205183, 3825.16211, -0.959730506, -7.5857054e-09, 0.280922383, -4.06310328e-08, 1, -1.11807175e-07, -0.280922383, -1.18718916e-07, -0.959730506)
                CFrameMon = CFrame.new(-1219.32324, 4.75205183, 3915.63452, -0.966492832, -6.91238853e-08, 0.25669381, -5.21195496e-08, 1, 7.3047012e-08, -0.25669381, 5.72206496e-08, -0.966492832)
            elseif MyLevel == 40 or MyLevel <= 59 then -- Brute
                Dis = 150
                Ms = "Brute [Lv. 45]"
                NaemQuest = "BuggyQuest1"
                LevelQuest = 2
                NameMon = "Brute"
                CFrameQuest = CFrame.new(-1139.59717, 4.75205183, 3825.16211, -0.959730506, -7.5857054e-09, 0.280922383, -4.06310328e-08, 1, -1.11807175e-07, -0.280922383, -1.18718916e-07, -0.959730506)
                CFrameMon = CFrame.new(-1146.49646, 96.0936813, 4312.1333, -0.978175163, -1.53222057e-08, 0.207781896, -3.33316912e-08, 1, -8.31738873e-08, -0.207781896, -8.82843523e-08, -0.978175163)
            elseif MyLevel == 60 or MyLevel <= 74 then -- Desert Bandit
                Ms = "Desert Bandit [Lv. 60]"
                NaemQuest = "DesertQuest"
                LevelQuest = 1
                NameMon = "Desert Bandit"
                CFrameQuest = CFrame.new(897.031128, 6.43846416, 4388.97168, -0.804044724, 3.68233266e-08, 0.594568789, 6.97835176e-08, 1, 3.24365246e-08, -0.594568789, 6.75715199e-08, -0.804044724)
                CFrameMon = CFrame.new(932.788818, 6.4503746, 4488.24609, -0.998625934, 3.08948351e-08, 0.0524050146, 2.79967303e-08, 1, -5.60361286e-08, -0.0524050146, -5.44919629e-08, -0.998625934)
            elseif MyLevel == 75 or MyLevel <= 89 then -- Desert Officre
                Ms = "Desert Officer [Lv. 70]"
                NaemQuest = "DesertQuest"
                LevelQuest = 2
                NameMon = "Desert Officer"
                CFrameQuest = CFrame.new(897.031128, 6.43846416, 4388.97168, -0.804044724, 3.68233266e-08, 0.594568789, 6.97835176e-08, 1, 3.24365246e-08, -0.594568789, 6.75715199e-08, -0.804044724)
                CFrameMon = CFrame.new(1580.03198, 4.61375761, 4366.86426, 0.135744005, -6.44280718e-08, -0.990743816, 4.35738308e-08, 1, -5.90598574e-08, 0.990743816, -3.51534837e-08, 0.135744005)
            elseif MyLevel == 90 or MyLevel <= 99 then -- Snow Bandits
                Ms = "Snow Bandit [Lv. 90]"
                NaemQuest = "SnowQuest"
                LevelQuest = 1
                NameMon = "Snow Bandits"
                CFrameQuest = CFrame.new(1384.14001, 87.272789, -1297.06482, 0.348555952, -2.53947841e-09, -0.937287986, 1.49860568e-08, 1, 2.86358204e-09, 0.937287986, -1.50443711e-08, 0.348555952)
                CFrameMon = CFrame.new(1370.24316, 102.403511, -1411.52905, 0.980274439, -1.12995728e-08, 0.197641045, -9.57343449e-09, 1, 1.04655214e-07, -0.197641045, -1.04482936e-07, 0.980274439)
            elseif MyLevel == 100 or MyLevel <= 119 then -- Snowman
                Ms = "Snowman [Lv. 100]"
                NaemQuest = "SnowQuest"
                LevelQuest = 2
                NameMon = "Snowman"
                CFrameQuest = CFrame.new(1384.14001, 87.272789, -1297.06482, 0.348555952, -2.53947841e-09, -0.937287986, 1.49860568e-08, 1, 2.86358204e-09, 0.937287986, -1.50443711e-08, 0.348555952)
                CFrameMon = CFrame.new(1370.24316, 102.403511, -1411.52905, 0.980274439, -1.12995728e-08, 0.197641045, -9.57343449e-09, 1, 1.04655214e-07, -0.197641045, -1.04482936e-07, 0.980274439)
            elseif MyLevel == 120 or MyLevel <= 149 then -- Chief Petty Officer
                Ms = "Chief Petty Officer [Lv. 120]"
                NaemQuest = "MarineQuest2"
                LevelQuest = 1
                NameMon = "Chief Petty Officer"
                CFrameQuest = CFrame.new(-5035.0835, 28.6520386, 4325.29443, 0.0243340395, -7.08064647e-08, 0.999703884, -6.36926814e-08, 1, 7.23777944e-08, -0.999703884, -6.54350671e-08, 0.0243340395)
                CFrameMon = CFrame.new(-4882.8623, 22.6520386, 4255.53516, 0.273695946, -5.40380647e-08, -0.96181643, 4.37720793e-08, 1, -4.37274998e-08, 0.96181643, -3.01326679e-08, 0.273695946)
            elseif MyLevel == 150 or MyLevel <= 174 then -- Sky Bandit
                Ms = "Sky Bandit [Lv. 150]"
                NaemQuest = "SkyQuest"
                LevelQuest = 1
                NameMon = "Sky Bandit"
                CFrameQuest = CFrame.new(-4841.83447, 717.669617, -2623.96436, -0.875942111, 5.59710216e-08, -0.482416272, 3.04023082e-08, 1, 6.08195947e-08, 0.482416272, 3.86078725e-08, -0.875942111)
                CFrameMon = CFrame.new(-4970.74219, 294.544342, -2890.11353, -0.994874597, -8.61311236e-08, -0.101116329, -9.10836206e-08, 1, 4.43614923e-08, 0.101116329, 5.33441664e-08, -0.994874597)
            elseif MyLevel == 175 or MyLevel <= 249 then -- Dark Master
                Ms = "Dark Master [Lv. 175]"
                NaemQuest = "SkyQuest"
                LevelQuest = 2
                NameMon = "Dark Master"
                CFrameQuest = CFrame.new(-4841.83447, 717.669617, -2623.96436, -0.875942111, 5.59710216e-08, -0.482416272, 3.04023082e-08, 1, 6.08195947e-08, 0.482416272, 3.86078725e-08, -0.875942111)
                CFrameMon = CFrame.new(-5220.58594, 430.693298, -2278.17456, -0.925375521, 1.12086873e-08, 0.379051805, -1.05115507e-08, 1, -5.52320891e-08, -0.379051805, -5.50948407e-08, -0.925375521)
            elseif MyLevel == 250 or MyLevel <= 274 then -- Toga Warrior
                Ms = "Toga Warrior [Lv. 250]"
                NaemQuest = "ColosseumQuest"
                LevelQuest = 1
                NameMon = "Toga Warrior"
                CFrameQuest = CFrame.new(-1576.11743, 7.38933945, -2983.30762, 0.576966345, 1.22114863e-09, 0.816767931, -3.58496594e-10, 1, -1.24185606e-09, -0.816767931, 4.2370063e-10, 0.576966345)
                CFrameMon = CFrame.new(-1779.97583, 44.6077499, -2736.35474, 0.984437346, 4.10396339e-08, 0.175734788, -3.62286876e-08, 1, -3.05844168e-08, -0.175734788, 2.3741821e-08, 0.984437346)
            elseif MyLevel == 275 or MyLevel <= 299 then -- Gladiato
                Ms = "Gladiator [Lv. 275]"
                NaemQuest = "ColosseumQuest"
                LevelQuest = 2
                NameMon = "Gladiato"
                CFrameQuest = CFrame.new(-1576.11743, 7.38933945, -2983.30762, 0.576966345, 1.22114863e-09, 0.816767931, -3.58496594e-10, 1, -1.24185606e-09, -0.816767931, 4.2370063e-10, 0.576966345)
                CFrameMon = CFrame.new(-1274.75903, 58.1895943, -3188.16309, 0.464524001, 6.21005611e-08, 0.885560572, -4.80449414e-09, 1, -6.76054768e-08, -0.885560572, 2.71497012e-08, 0.464524001)
            elseif MyLevel == 300 or MyLevel <= 324 then -- Military Soldier
                Ms = "Military Soldier [Lv. 300]"
                NaemQuest = "MagmaQuest"
                LevelQuest = 1
                NameMon = "Military Soldier"
                CFrameQuest = CFrame.new(-5316.55859, 12.2370615, 8517.2998, 0.588437557, -1.37880001e-08, -0.808542669, -2.10116209e-08, 1, -3.23446478e-08, 0.808542669, 3.60215964e-08, 0.588437557)
                CFrameMon = CFrame.new(-5363.01123, 41.5056877, 8548.47266, -0.578253984, -3.29503091e-10, 0.815856814, 9.11209668e-08, 1, 6.498761e-08, -0.815856814, 1.11920997e-07, -0.578253984)
            elseif MyLevel == 325 or MyLevel <= 374 then -- Military Spy
                FM = false
                Ms = "Military Spy [Lv. 325]"
                NaemQuest = "MagmaQuest"
                LevelQuest = 2
                NameMon = "Military Spy"
                CFrameQuest = CFrame.new(-5316.55859, 12.2370615, 8517.2998, 0.588437557, -1.37880001e-08, -0.808542669, -2.10116209e-08, 1, -3.23446478e-08, 0.808542669, 3.60215964e-08, 0.588437557)
                CFrameMon = CFrame.new(-5787.99023, 120.864456, 8762.25293, -0.188358366, -1.84706277e-08, 0.982100308, -1.23782129e-07, 1, -4.93306951e-09, -0.982100308, -1.22495649e-07, -0.188358366)
            elseif MyLevel == 375 or MyLevel <= 399 then -- Fishman Warrior
                FM = true
                Ms = "Fishman Warrior [Lv. 375]"
                NaemQuest = "FishmanQuest"
                LevelQuest = 1
                NameMon = "Fishman Warrior"
                CFrameQuest = CFrame.new(61122.5625, 18.4716396, 1568.16504, 0.893533468, 3.95251609e-09, 0.448996574, -2.34327455e-08, 1, 3.78297464e-08, -0.448996574, -4.43233645e-08, 0.893533468)
                CFrameMon = CFrame.new(60946.6094, 48.6735229, 1525.91687, -0.0817126185, 8.90751153e-08, 0.996655822, 2.00889794e-08, 1, -8.77269599e-08, -0.996655822, 1.28533992e-08, -0.0817126185)
            elseif MyLevel == 400 or MyLevel <= 449 then -- Fishman Commando
                FM = true
                Ms = "Fishman Commando [Lv. 400]"
                NaemQuest = "FishmanQuest"
                LevelQuest = 2
                NameMon = "Fishman Commando"
                CFrameQuest = CFrame.new(61122.5625, 18.4716396, 1568.16504, 0.893533468, 3.95251609e-09, 0.448996574, -2.34327455e-08, 1, 3.78297464e-08, -0.448996574, -4.43233645e-08, 0.893533468)
                CFrameMon = CFrame.new(61885.5039, 18.4828243, 1504.17896, 0.577502489, 0, -0.816389024, -0, 1.00000012, -0, 0.816389024, 0, 0.577502489)
            elseif MyLevel == 450 or MyLevel <= 474 then -- God's Guards
                FM = false
                Ms = "God's Guard [Lv. 450]"
                NaemQuest = "SkyExp1Quest"
                LevelQuest = 1
                NameMon = "God's Guards"
                CFrameQuest = CFrame.new(-4721.71436, 845.277161, -1954.20105, -0.999277651, -5.56969759e-09, 0.0380011722, -4.14751478e-09, 1, 3.75035256e-08, -0.0380011722, 3.73188307e-08, -0.999277651)
                CFrameMon = CFrame.new(-4716.95703, 853.089722, -1933.92542, -0.93441087, -6.77488776e-09, -0.356197298, 1.12145182e-08, 1, -4.84390199e-08, 0.356197298, -4.92565206e-08, -0.93441087)
            elseif MyLevel == 475 or MyLevel <= 524 then -- Shandas
                sky = false
                Ms = "Shanda [Lv. 475]"
                NaemQuest = "SkyExp1Quest"
                LevelQuest = 2
                NameMon = "Shandas"
                CFrameQuest = CFrame.new(-7863.63672, 5545.49316, -379.826324, 0.362120807, -1.98046344e-08, -0.93213129, 4.05822291e-08, 1, -5.48095125e-09, 0.93213129, -3.58431969e-08, 0.362120807)
                CFrameMon = CFrame.new(-7685.12354, 5601.05127, -443.171509, 0.150056243, 1.79768236e-08, -0.988677442, 6.67798661e-09, 1, 1.91962481e-08, 0.988677442, -9.48289181e-09, 0.150056243)
            elseif MyLevel == 525 or MyLevel <= 549 then -- Royal Squad
                sky = true
                Ms = "Royal Squad [Lv. 525]"
                NaemQuest = "SkyExp2Quest"
                LevelQuest = 1
                NameMon = "Royal Squad"
                CFrameQuest = CFrame.new(-7902.66895, 5635.96387, -1411.71802, 0.0504222959, 2.5710392e-08, 0.998727977, 1.12541557e-07, 1, -3.14249675e-08, -0.998727977, 1.13982921e-07, 0.0504222959)
                CFrameMon = CFrame.new(-7685.02051, 5606.87842, -1442.729, 0.561947823, 7.69527464e-09, -0.827172697, -4.24974544e-09, 1, 6.41599973e-09, 0.827172697, -9.01838604e-11, 0.561947823)
            elseif MyLevel == 550 or MyLevel <= 624 then -- Royal Soldier
                Dis = 240
                sky = true
                Ms = "Royal Soldier [Lv. 550]"
                NaemQuest = "SkyExp2Quest"
                LevelQuest = 2
                NameMon = "Royal Soldier"
                CFrameQuest = CFrame.new(-7902.66895, 5635.96387, -1411.71802, 0.0504222959, 2.5710392e-08, 0.998727977, 1.12541557e-07, 1, -3.14249675e-08, -0.998727977, 1.13982921e-07, 0.0504222959)
                CFrameMon = CFrame.new(-7864.44775, 5661.94092, -1708.22351, 0.998389959, 2.28686137e-09, -0.0567218624, 1.99431383e-09, 1, 7.54200258e-08, 0.0567218624, -7.54117195e-08, 0.998389959)
            elseif MyLevel == 625 or MyLevel <= 649 then -- Galley Pirate
                Dis = 240
                sky = false
                Ms = "Galley Pirate [Lv. 625]"
                NaemQuest = "FountainQuest"
                LevelQuest = 1
                NameMon = "Galley Pirate"
                CFrameQuest = CFrame.new(5254.60156, 38.5011406, 4049.69678, -0.0504891425, -3.62066501e-08, -0.998724639, -9.87921389e-09, 1, -3.57534553e-08, 0.998724639, 8.06145284e-09, -0.0504891425)
                CFrameMon = CFrame.new(5595.06982, 41.5013695, 3961.47095, -0.992138803, -2.11610267e-08, -0.125142589, -1.34249509e-08, 1, -6.26613996e-08, 0.125142589, -6.04887518e-08, -0.992138803)
            elseif MyLevel >= 650 then -- Galley Captain
                Dis = 240
                Ms = "Galley Captain [Lv. 650]"
                NaemQuest = "FountainQuest"
                LevelQuest = 2
                NameMon = "Galley Captain"
                CFrameQuest = CFrame.new(5254.60156, 38.5011406, 4049.69678, -0.0504891425, -3.62066501e-08, -0.998724639, -9.87921389e-09, 1, -3.57534553e-08, 0.998724639, 8.06145284e-09, -0.0504891425)
                CFrameMon = CFrame.new(5658.5752, 38.5361786, 4928.93506, -0.996873081, 2.12391046e-06, -0.0790185928, 2.16989656e-06, 1, -4.96097414e-07, 0.0790185928, -6.66008248e-07, -0.996873081)
            end
        elseif newworld then
            local MyLevel = game.Players.LocalPlayer.Data.Level.Value
            Dis = 240
            if MyLevel == 700 or MyLevel <= 724 then -- Raider [Lv. 700]
                Ms = "Raider [Lv. 700]"
                NaemQuest = "Area1Quest"
                LevelQuest = 1
                NameMon = "Raider"
                CFrameQuest = CFrame.new(-424.080078, 73.0055847, 1836.91589, 0.253544956, -1.42165932e-08, 0.967323601, -6.00147771e-08, 1, 3.04272909e-08, -0.967323601, -6.5768397e-08, 0.253544956)
                CFrameMon = CFrame.new(-737.026123, 39.1748352, 2392.57959, 0.272128761, 0, -0.962260842, -0, 1, -0, 0.962260842, 0, 0.272128761)
            elseif MyLevel == 725 or MyLevel <= 774 then -- Mercenary [Lv. 725]
                Ms = "Mercenary [Lv. 725]"
                NaemQuest = "Area1Quest"
                LevelQuest = 2
                NameMon = "Mercenary"
                CFrameQuest = CFrame.new(-424.080078, 73.0055847, 1836.91589, 0.253544956, -1.42165932e-08, 0.967323601, -6.00147771e-08, 1, 3.04272909e-08, -0.967323601, -6.5768397e-08, 0.253544956)
                CFrameMon = CFrame.new(-973.731995, 95.8733215, 1836.46936, 0.999135971, 2.02326991e-08, -0.0415605344, -1.90767793e-08, 1, 2.82094952e-08, 0.0415605344, -2.73922804e-08, 0.999135971)
            elseif MyLevel == 775 or MyLevel <= 799 then -- Swan Pirate [Lv. 775]
                Ms = "Swan Pirate [Lv. 775]"
                NaemQuest = "Area2Quest"
                LevelQuest = 1
                NameMon = "Swan Pirate"
                CFrameQuest = CFrame.new(632.698608, 73.1055908, 918.666321, -0.0319722369, 8.96074881e-10, -0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, -1.07732087e-10, -0.0319722369)
                CFrameMon = CFrame.new(970.369446, 142.653198, 1217.3667, 0.162079468, -4.85452638e-08, -0.986777723, 1.03357589e-08, 1, -4.74980872e-08, 0.986777723, -2.50063148e-09, 0.162079468)
            elseif MyLevel == 800 or MyLevel <= 874 then -- Factory Staff [Lv. 800]
                Ms = "Factory Staff [Lv. 800]"
                NaemQuest = "Area2Quest"
                LevelQuest = 2
                NameMon = "Factory Staff"
                CFrameQuest = CFrame.new(632.698608, 73.1055908, 918.666321, -0.0319722369, 8.96074881e-10, -0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, -1.07732087e-10, -0.0319722369)
                CFrameMon = CFrame.new(296.786499, 72.9948196, -57.1298141, -0.876037002, -5.32364979e-08, 0.482243896, -3.87658332e-08, 1, 3.99718729e-08, -0.482243896, 1.63222538e-08, -0.876037002)
            elseif MyLevel == 875 or MyLevel <= 899 then -- Marine Lieutenant [Lv. 875]
                Ms = "Marine Lieutenant [Lv. 875]"
                NaemQuest = "MarineQuest3"
                LevelQuest = 1
                NameMon = "Marine Lieutenant"
                CFrameQuest = CFrame.new(-2442.65015, 73.0511475, -3219.11523, -0.873540044, 4.2329841e-08, -0.486752301, 5.64383384e-08, 1, -1.43220786e-08, 0.486752301, -3.99823996e-08, -0.873540044)
                CFrameMon = CFrame.new(-2913.26367, 73.0011826, -2971.64282, 0.910507619, 0, 0.413492233, 0, 1.00000012, 0, -0.413492233, 0, 0.910507619)
            elseif MyLevel == 900 or MyLevel <= 949 then -- Marine Captain [Lv. 900]
                Ms = "Marine Captain [Lv. 900]"
                NaemQuest = "MarineQuest3"
                LevelQuest = 2
                NameMon = "Marine Captain"
                CFrameQuest = CFrame.new(-2442.65015, 73.0511475, -3219.11523, -0.873540044, 4.2329841e-08, -0.486752301, 5.64383384e-08, 1, -1.43220786e-08, 0.486752301, -3.99823996e-08, -0.873540044)
                CFrameMon = CFrame.new(-1868.67688, 73.0011826, -3321.66333, -0.971402287, 1.06502087e-08, 0.237439692, 3.68856199e-08, 1, 1.06050372e-07, -0.237439692, 1.11775684e-07, -0.971402287)
            elseif MyLevel == 950 or MyLevel <= 974 then -- Zombie [Lv. 950]
                Ms = "Zombie [Lv. 950]"
                NaemQuest = "ZombieQuest"
                LevelQuest = 1
                NameMon = "Zombie"
                CFrameQuest = CFrame.new(-5492.79395, 48.5151672, -793.710571, 0.321800292, -6.24695815e-08, 0.946807742, 4.05616092e-08, 1, 5.21931227e-08, -0.946807742, 2.16082796e-08, 0.321800292)
                CFrameMon = CFrame.new(-5634.83838, 126.067039, -697.665039, -0.992770672, 6.77618939e-09, 0.120025545, 1.65461245e-08, 1, 8.04023372e-08, -0.120025545, 8.18070234e-08, -0.992770672)
            elseif MyLevel == 975 or MyLevel <= 999 then -- Vampire [Lv. 975]
                Ms = "Vampire [Lv. 975]"
                NaemQuest = "ZombieQuest"
                LevelQuest = 2
                NameMon = "Vampire"
                CFrameQuest = CFrame.new(-5492.79395, 48.5151672, -793.710571, 0.321800292, -6.24695815e-08, 0.946807742, 4.05616092e-08, 1, 5.21931227e-08, -0.946807742, 2.16082796e-08, 0.321800292)
                CFrameMon = CFrame.new(-6030.32031, 6.4377408, -1313.5564, -0.856965423, 3.9138893e-08, -0.515373945, -1.12178942e-08, 1, 9.45958547e-08, 0.515373945, 8.68467822e-08, -0.856965423)
            elseif MyLevel == 1000 or MyLevel <= 1049 then -- Snow Trooper [Lv. 1000] **
                Ms = "Snow Trooper [Lv. 1000]"
                NaemQuest = "SnowMountainQuest"
                LevelQuest = 1
                NameMon = "Snow Trooper"
                CFrameQuest = CFrame.new(604.964966, 401.457062, -5371.69287, 0.353063971, 1.89520435e-08, -0.935599446, -5.81846002e-08, 1, -1.70033754e-09, 0.935599446, 5.50377841e-08, 0.353063971)
                CFrameMon = CFrame.new(535.893433, 401.457062, -5329.6958, -0.999524176, 0, 0.0308452044, 0, 1, -0, -0.0308452044, 0, -0.999524176)
            elseif MyLevel == 1050 or MyLevel <= 1099 then -- Winter Warrior [Lv. 1050]
                Ms = "Winter Warrior [Lv. 1050]"
                NaemQuest = "SnowMountainQuest"
                LevelQuest = 2
                NameMon = "Winter Warrior"
                CFrameQuest = CFrame.new(604.964966, 401.457062, -5371.69287, 0.353063971, 1.89520435e-08, -0.935599446, -5.81846002e-08, 1, -1.70033754e-09, 0.935599446, 5.50377841e-08, 0.353063971)
                CFrameMon = CFrame.new(1223.7417, 454.575226, -5170.02148, 0.473996818, 2.56845354e-08, 0.880526543, -5.62456428e-08, 1, 1.10811016e-09, -0.880526543, -5.00510211e-08, 0.473996818)
            elseif MyLevel == 1100 or MyLevel <= 1124 then -- Lab Subordinate [Lv. 1100]
                Ms = "Lab Subordinate [Lv. 1100]"
                NaemQuest = "IceSideQuest"
                LevelQuest = 1
                NameMon = "Lab Subordinate"
                CFrameQuest = CFrame.new(-6060.10693, 15.9868021, -4904.7876, -0.411000341, -5.06538868e-07, 0.91163528, 1.26306062e-07, 1, 6.12581289e-07, -0.91163528, 3.66916197e-07, -0.411000341)
                CFrameMon = CFrame.new(-5769.2041, 37.9288292, -4468.38721, -0.569419742, -2.49055017e-08, 0.822046936, -6.96206541e-08, 1, -1.79282633e-08, -0.822046936, -6.74401548e-08, -0.569419742)
            elseif MyLevel == 1125 or MyLevel <= 1174 then -- Horned Warrior [Lv. 1125]
                Ms = "Horned Warrior [Lv. 1125]"
                NaemQuest = "IceSideQuest"
                LevelQuest = 2
                NameMon = "Horned Warrior"
                CFrameQuest = CFrame.new(-6060.10693, 15.9868021, -4904.7876, -0.411000341, -5.06538868e-07, 0.91163528, 1.26306062e-07, 1, 6.12581289e-07, -0.91163528, 3.66916197e-07, -0.411000341)
                CFrameMon = CFrame.new(-6400.85889, 24.7645149, -5818.63574, -0.964845479, 8.65926566e-08, -0.262817472, 3.98261392e-07, 1, -1.13260398e-06, 0.262817472, -1.19745812e-06, -0.964845479)
            elseif MyLevel == 1175 or MyLevel <= 1199 then -- Magma Ninja [Lv. 1175]
                Ms = "Magma Ninja [Lv. 1175]"
                NaemQuest = "FireSideQuest"
                LevelQuest = 1
                NameMon = "Magma Ninja"
                CFrameQuest = CFrame.new(-5431.09473, 15.9868021, -5296.53223, 0.831796765, 1.15322464e-07, -0.555080295, -1.10814341e-07, 1, 4.17010995e-08, 0.555080295, 2.68240168e-08, 0.831796765)
                CFrameMon = CFrame.new(-5496.65576, 58.6890411, -5929.76855, -0.885073781, 0, -0.465450764, 0, 1.00000012, -0, 0.465450764, 0, -0.885073781)
            elseif MyLevel == 1200 or MyLevel <= 1249 then -- Lava Pirate [Lv. 1200]
                Ms = "Lava Pirate [Lv. 1200]"
                NaemQuest = "FireSideQuest"
                LevelQuest = 2
                NameMon = "Lava Pirate"
                CFrameQuest = CFrame.new(-5431.09473, 15.9868021, -5296.53223, 0.831796765, 1.15322464e-07, -0.555080295, -1.10814341e-07, 1, 4.17010995e-08, 0.555080295, 2.68240168e-08, 0.831796765)
                CFrameMon = CFrame.new(-5169.71729, 34.1234779, -4669.73633, -0.196780294, 0, 0.98044765, 0, 1.00000012, -0, -0.98044765, 0, -0.196780294)
            elseif MyLevel == 1250 or MyLevel <= 1274 then -- Ship Deckhand [Lv. 1250]
                Ms = "Ship Deckhand [Lv. 1250]"
                NaemQuest = "ShipQuest1"
                LevelQuest = 1
                NameMon = "Ship Deckhand"
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016, -0.244533166, -0, -0.969640911, -0, 1.00000012, -0, 0.96964103, 0, -0.244533136)
                CFrameMon = CFrame.new(1163.80872, 138.288452, 33058.4258, -0.998580813, 5.49076979e-08, -0.0532564968, 5.57436763e-08, 1, -1.42118655e-08, 0.0532564968, -1.71604082e-08, -0.998580813)
            elseif MyLevel == 1275 or MyLevel <= 1299 then -- Ship Engineer [Lv. 1275]
                Ms = "Ship Engineer [Lv. 1275]"
                NaemQuest = "ShipQuest1"
                LevelQuest = 2
                NameMon = "Ship Engineer"
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016, -0.244533166, -0, -0.969640911, -0, 1.00000012, -0, 0.96964103, 0, -0.244533136)
                CFrameMon = CFrame.new(916.666504, 44.0920448, 32917.207, -0.99746871, -4.85034697e-08, -0.0711069331, -4.8925461e-08, 1, 4.19294288e-09, 0.0711069331, 7.66126895e-09, -0.99746871)
            elseif MyLevel == 1300 or MyLevel <= 1324 then -- Ship Steward [Lv. 1300]
                Ms = "Ship Steward [Lv. 1300]"
                NaemQuest = "ShipQuest2"
                LevelQuest = 1
                NameMon = "Ship Steward"
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125, -0.869560242, 1.51905191e-08, -0.493826836, 1.44108379e-08, 1, 5.38534195e-09, 0.493826836, -2.43357912e-09, -0.869560242)
                CFrameMon = CFrame.new(918.743286, 129.591064, 33443.4609, -0.999792814, -1.7070947e-07, -0.020350717, -1.72559169e-07, 1, 8.91351277e-08, 0.020350717, 9.2628369e-08, -0.999792814)
            elseif MyLevel == 1325 or MyLevel <= 1349 then -- Ship Officer [Lv. 1325]
                Ms = "Ship Officer [Lv. 1325]"
                NaemQuest = "ShipQuest2"
                LevelQuest = 2
                NameMon = "Ship Officer"
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125, -0.869560242, 1.51905191e-08, -0.493826836, 1.44108379e-08, 1, 5.38534195e-09, 0.493826836, -2.43357912e-09, -0.869560242)
                CFrameMon = CFrame.new(786.051941, 181.474106, 33303.2969, 0.999285698, -5.32193063e-08, 0.0377905183, 5.68968588e-08, 1, -9.62386864e-08, -0.0377905183, 9.83201005e-08, 0.999285698)
            elseif MyLevel == 1350 or MyLevel <= 1374 then -- Arctic Warrior [Lv. 1350]
                Ms = "Arctic Warrior [Lv. 1350]"
                NaemQuest = "FrostQuest"
                LevelQuest = 1
                NameMon = "Arctic Warrior"
                CFrameQuest = CFrame.new(5669.43506, 28.2117786, -6482.60107, 0.888092756, 1.02705066e-07, 0.459664226, -6.20391774e-08, 1, -1.03572376e-07, -0.459664226, 6.34646895e-08, 0.888092756)
                CFrameMon = CFrame.new(5995.07471, 57.3188477, -6183.47314, 0.702747107, -1.53454167e-07, -0.711440146, -1.08168464e-07, 1, -3.22542007e-07, 0.711440146, 3.03620908e-07, 0.702747107)
            elseif MyLevel == 1375 or MyLevel <= 1424 then -- Snow Lurker [Lv. 1375]
                Ms = "Snow Lurker [Lv. 1375]"
                NaemQuest = "FrostQuest"
                LevelQuest = 2
                NameMon = "Snow Lurker"
                CFrameQuest = CFrame.new(5669.43506, 28.2117786, -6482.60107, 0.888092756, 1.02705066e-07, 0.459664226, -6.20391774e-08, 1, -1.03572376e-07, -0.459664226, 6.34646895e-08, 0.888092756)
                CFrameMon = CFrame.new(5518.00684, 60.5559731, -6828.80518, -0.650781393, -3.64292951e-08, 0.759265184, -4.07668654e-09, 1, 4.44854642e-08, -0.759265184, 2.58550248e-08, -0.650781393)
            elseif MyLevel == 1425 or MyLevel <= 1449 then -- Sea Soldier [Lv. 1425]
                Ms = "Sea Soldier [Lv. 1425]"
                NaemQuest = "ForgottenQuest"
                LevelQuest = 1
                NameMon = "Sea Soldier"
                CFrameQuest = CFrame.new(-3052.99097, 236.881363, -10148.1943, -0.997911751, 4.42321983e-08, 0.064591676, 4.90968759e-08, 1, 7.37270085e-08, -0.064591676, 7.67442998e-08, -0.997911751)
                CFrameMon = CFrame.new(-3029.78467, 66.944252, -9777.38184, -0.998552859, 1.09555076e-08, 0.0537791774, 7.79564235e-09, 1, -5.89660658e-08, -0.0537791774, -5.84614881e-08, -0.998552859)
            elseif MyLevel >= 1450 then -- Water Fighter [Lv. 1450]
                Ms = "Water Fighter [Lv. 1450]"
                NaemQuest = "ForgottenQuest"
                LevelQuest = 2
                NameMon = "Water Fighter"
                CFrameQuest = CFrame.new(-3052.99097, 236.881363, -10148.1943, -0.997911751, 4.42321983e-08, 0.064591676, 4.90968759e-08, 1, 7.37270085e-08, -0.064591676, 7.67442998e-08, -0.997911751)
                CFrameMon = CFrame.new(-3262.00098, 298.699615, -10553.6943, -0.233570755, -4.57538185e-08, 0.972339869, -5.80986068e-08, 1, 3.30992194e-08, -0.972339869, -4.87605725e-08, -0.233570755)
            end
        else
            local MyLevel =  game.Players.LocalPlayer.Data.Level.Value
            Dis = 240
            if MyLevel == 1500 or MyLevel <= 1524 then
                Ms = "Pirate Millionaire [Lv. 1500]"
                NaemQuest = "PiratePortQuest"
                LevelQuest = 1
                NameMon = "Pirate Millionaire"
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                CFrameMon = CFrame.new(81.164993286133, 43.755737304688, 5724.7021484375)
            elseif MyLevel == 1525 or MyLevel <= 1574 then
                Ms = "Pistol Billionaire [Lv. 1525]"
                NaemQuest = "PiratePortQuest"
                LevelQuest = 2
                NameMon = "Pistol Billionaire"
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                CFrameMon = CFrame.new(81.164993286133, 43.755737304688, 5724.7021484375)
            elseif MyLevel == 1575 or MyLevel <= 1599 then
                Ms = "Dragon Crew Warrior [Lv. 1575]"
                NaemQuest = "AmazonQuest"
                LevelQuest = 1
                NameMon = "Dragon Crew Warrior"
                CFrameQuest = CFrame.new(5832.83594, 51.6806107, -1101.51563, 0.898790359, -0, -0.438378751, 0, 1, -0, 0.438378751, 0, 0.898790359)
                CFrameMon = CFrame.new(6241.9951171875, 51.522083282471, -1243.9771728516)
            elseif MyLevel == 1600 or MyLevel <= 1624 then
                Ms = "Dragon Crew Archer [Lv. 1600]"
                NaemQuest = "AmazonQuest"
                LevelQuest = 2
                NameMon = "Dragon Crew Archer"
                CFrameQuest = CFrame.new(5832.83594, 51.6806107, -1101.51563, 0.898790359, -0, -0.438378751, 0, 1, -0, 0.438378751, 0, 0.898790359)
                CFrameMon = CFrame.new(6488.9155273438, 383.38375854492, -110.66246032715)
            elseif MyLevel == 1625 or MyLevel <= 1649 then
                Ms = "Female Islander [Lv. 1625]"
                NaemQuest = "AmazonQuest2"
                LevelQuest = 1
                NameMon = "Female Islander"
                CFrameQuest = CFrame.new(5448.86133, 601.516174, 751.130676, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                CFrameMon = CFrame.new(4770.4990234375, 758.95520019531, 1069.8680419922)
            elseif MyLevel == 1650 or MyLevel <= 1699 then
                Ms = "Giant Islander [Lv. 1650]"
                NaemQuest = "AmazonQuest2"
                LevelQuest = 2
                NameMon = "Giant Islander"
                CFrameQuest = CFrame.new(5448.86133, 601.516174, 751.130676, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                CFrameMon = CFrame.new(4530.3540039063, 656.75695800781, -131.60952758789)
            elseif MyLevel == 1700 or MyLevel <= 1724 then
                Ms = "Marine Commodore [Lv. 1700]"
                NaemQuest = "MarineTreeIsland"
                LevelQuest = 1
                NameMon = "Marine Commodore"
                CFrameQuest = CFrame.new(2180.54126, 27.8156815, -6741.5498, -0.965929747, 0, 0.258804798, 0, 1, 0, -0.258804798, 0, -0.965929747)
                CFrameMon = CFrame.new(2490.0844726563, 190.4232635498, -7160.0502929688)
            elseif MyLevel == 1725 or MyLevel <= 1774 then
                Ms = "Marine Rear Admiral [Lv. 1725]"
                NaemQuest = "MarineTreeIsland"
                LevelQuest = 2
                NameMon = "Marine Rear Admiral"
                CFrameQuest = CFrame.new(2180.54126, 27.8156815, -6741.5498, -0.965929747, 0, 0.258804798, 0, 1, 0, -0.258804798, 0, -0.965929747)
                CFrameMon = CFrame.new(3951.3903808594, 229.11549377441, -6912.81640625)
            elseif MyLevel == 1775 or MyLevel <= 1799 then
                Ms = "Fishman Raider [Lv. 1775]"
                NaemQuest = "DeepForestIsland3"
                LevelQuest = 1
                NameMon = "Fishman Raider"
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
                CFrameMon = CFrame.new(-10322.400390625, 390.94473266602, -8580.0908203125)
            elseif MyLevel == 1800 or MyLevel <= 1824 then
                Ms = "Fishman Captain [Lv. 1800]"
                NaemQuest = "DeepForestIsland3"
                LevelQuest = 2
                NameMon = "Fishman Captain"
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
                CFrameMon = CFrame.new(-11194.541992188, 442.02795410156, -8608.806640625)
            elseif MyLevel == 1825 or MyLevel <= 1849 then
                Ms = "Forest Pirate [Lv. 1825]"
                NaemQuest = "DeepForestIsland"
                LevelQuest = 1
                NameMon = "Forest Pirate"
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)
                CFrameMon = CFrame.new(-13225.809570313, 428.19387817383, -7753.1245117188)
            elseif MyLevel == 1850 or MyLevel <= 1899 then
                Ms = "Mythological Pirate [Lv. 1850]"
                NaemQuest = "DeepForestIsland"
                LevelQuest = 2
                NameMon = "Mythological Pirate"
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)
                CFrameMon = CFrame.new(-13869.172851563, 564.95251464844, -7084.4135742188)
            elseif MyLevel == 1900 or MyLevel <= 1924 then
                Ms = "Jungle Pirate [Lv. 1900]"
                NaemQuest = "DeepForestIsland2"
                LevelQuest = 1
                NameMon = "Jungle Pirate"
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                CFrameMon = CFrame.new(-11982.221679688, 376.32522583008, -10451.415039063)
            elseif MyLevel == 1925 or MyLevel <= 1974 then
                Ms = "Musketeer Pirate [Lv. 1925]"
                NaemQuest = "DeepForestIsland2"
                LevelQuest = 2
                NameMon = "Musketeer Pirate"
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                CFrameMon = CFrame.new(-13282.3046875, 496.23684692383, -9565.150390625)
            elseif MyLevel == 1975 or MyLevel <= 1999 then
                Ms = "Reborn Skeleton [Lv. 1975]"
                NaemQuest = "HauntedQuest1"
                LevelQuest = 1
                NameMon = "Reborn Skeleton"
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                CFrameMon = CFrame.new(-8761.3154296875, 164.85829162598, 6161.1567382813)
            elseif MyLevel == 2000 or MyLevel <= 2024 then
                Ms = "Living Zombie [Lv. 2000]"
                NaemQuest = "HauntedQuest1"
                LevelQuest = 2
                NameMon = "Living Zombie"
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                CFrameMon = CFrame.new(-10093.930664063, 237.38233947754, 6180.5654296875)
            elseif MyLevel == 2025 or MyLevel <= 2049 then
                Ms = "Demonic Soul [Lv. 2025]"
                NaemQuest = "HauntedQuest2"
                LevelQuest = 1
                NameMon = "Demonic Soul"
                CFrameQuest = CFrame.new(-9514.78027, 171.162918, 6078.82373, 0.301918149, 7.4535027e-09, 0.953333855, -3.22802141e-09, 1, -6.79604995e-09, -0.953333855, -1.02553133e-09, 0.301918149)
                CFrameMon = CFrame.new(-9466.72949, 171.162918, 6132.01514)
            elseif MyLevel == 2050 or MyLevel <= 2074 then
                Ms = "Posessed Mummy [Lv. 2050]" 
                NaemQuest = "HauntedQuest2"
                LevelQuest = 2
                NameMon = "Posessed Mummy"
                CFrameQuest = CFrame.new(-9514.78027, 171.162918, 6078.82373, 0.301918149, 7.4535027e-09, 0.953333855, -3.22802141e-09, 1, -6.79604995e-09, -0.953333855, -1.02553133e-09, 0.301918149)
                CFrameMon = CFrame.new(-9589.93848, 4.85058546, 6190.27197)
            elseif MyLevel == 2075 or MyLevel <= 2099 then
                Ms = "Peanut Scout [Lv. 2075]"
                NaemQuest = "NutsIslandQuest"
                LevelQuest = 1
                NameMon = "Peanut Scout"
                CFrameQuest = CFrame.new(-2075.9643554688, 38.129207611084, -10172.815429688)
                CFrameMon = CFrame.new(-2150.587890625, 122.49767303467, -10358.994140625)
            elseif MyLevel == 2100 or MyLevel <= 2124 then
                Ms = "Peanut President [Lv. 2100]"
                NaemQuest = "NutsIslandQuest"
                LevelQuest = 2
                NameMon = "Peanut President"
                CFrameQuest = CFrame.new(-2075.9643554688, 38.129207611084, -10172.815429688)
                CFrameMon = CFrame.new(-2150.587890625, 122.49767303467, -10358.994140625)
            elseif MyLevel == 2125 or MyLevel <= 2149 then
                Ms = "Ice Cream Chef [Lv. 2125]"
                NaemQuest = "IceCreamIslandQuest"
                LevelQuest = 1
                NameMon = "Ice Cream Chef"
                CFrameQuest = CFrame.new(-819.84533691406, 65.845329284668, -10965.487304688)
                CFrameMon = CFrame.new(-890.55895996094, 186.34135437012, -11127.306640625)
            elseif MyLevel == 2150 or MyLevel <= 2199 then
                Ms = "Ice Cream Commander [Lv. 2150]"
                NaemQuest = "IceCreamIslandQuest"
                LevelQuest = 2
                NameMon = "Ice Cream Commander"
                CFrameQuest = CFrame.new(-819.84533691406, 65.845329284668, -10965.487304688)
                CFrameMon = CFrame.new(-890.55895996094, 186.34135437012, -11127.306640625)
               elseif MyLevel == 2200 or MyLevel <= 2225 then
                  Ms = "Cookie Crafter [Lv. 2200]"
                  LevelQuest = 1
                  NaemQuest = "CakeQuest1"
                  NameMon = "Cookie Crafter"
                  CFrameMon = CFrame.new(-2269.18994, 90.5692139, -12157.415, -0.241292745, -4.28479332e-08, 0.970452368, -3.0098203e-08, 1, 3.66689363e-08, -0.970452368, -2.03609218e-08, -0.241292745)
                  CFrameQuest = CFrame.new(-2018.80884, 38.1414719, -12023.8447, 0.926204681, -9.25598265e-09, 0.377021134, 1.17539365e-08, 1, -4.32487202e-09, -0.377021134, 8.43719938e-09, 0.926204681)
              elseif MyLevel == 2225 or MyLevel <= 2250 then
                  Ms = "Cake Guard [Lv. 2225]"
                  LevelQuest = 2
                  NaemQuest = "CakeQuest1"
                  NameMon = "Cake Guard"
                  CFrameMon = CFrame.new(-1558.61768, 90.5694199, -12583.4219, -0.790530264, -4.29809255e-08, 0.612422943, -3.70810653e-08, 1, 2.23166392e-08, -0.612422943, -5.0673159e-09, -0.790530264)
                  CFrameQuest = CFrame.new(-2018.80884, 38.1414719, -12023.8447, 0.926204681, -9.25598265e-09, 0.377021134, 1.17539365e-08, 1, -4.32487202e-09, -0.377021134, 8.43719938e-09, 0.926204681)
              elseif MyLevel == 2250 or MyLevel <= 2275 then
                  Ms = "Baking Staff [Lv. 2250]"
                  LevelQuest = 1
                  NaemQuest = "CakeQuest2"
                  NameMon = "Baking Staff"
                  CFrameMon = CFrame.new(-1769.45056, 90.5691681, -13038.4648, -0.847998321, -2.02224353e-08, 0.529998958, -2.03078834e-08, 1, 5.66300029e-09, -0.529998958, -5.96094241e-09, -0.847998321)
                  CFrameQuest = CFrame.new(-1914.99646, 38.1413841, -12835.5117, 0.545026958, 0, 0.838418543, -0, 1, -0, -0.838418543, 0, 0.545026958)
              elseif MyLevel >= 2275 then
                  Ms = "Head Baker [Lv. 2275]"
                  LevelQuest = 2
                  NaemQuest = "CakeQuest2"
                  NameMon = "Head Baker"
                  CFrameMon = CFrame.new(-2068.16577, 84.8175354, -13017.8848, -0.527114272, 4.41528734e-08, 0.849794447, 4.18282369e-08, 1, -2.6011719e-08, -0.849794447, 2.18342535e-08, -0.527114272)
                  CFrameQuest = CFrame.new(-1914.99646, 38.1413841, -12835.5117, 0.545026958, 0, 0.838418543, -0, 1, -0, -0.838418543, 0, 0.545026958)
            end
        end
    end

-----------------------------------------

	local Window = create:Win("LUNAR HUB [FREE]")
	local Main = Window:Taps("Main")
	local Main = Main:newpage()
          Main:Label("AutoFarmSection")
       
          Main:Toggle("Auto Farm Level",_G.AuoFarmLv,function(vu)
	    _G.AutoFarmLv = vu
          end)
 
   spawn(function()
      while wait() do
         if _G.AutoFarmLv then
            if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
               MagnetActive = false
               CheckQuestLunarHub()
                TP(CFrameQuest)
               if (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
                  CheckQuestLunarHub()
                  if (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 then
                     game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NaemQuest, LevelQuest)
                     wait(2)
                  else
                     TP(CFrameQuest)
                  end
               end
            elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
               pcall(function()
                  CheckQuestLunarHub()
                  if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
                     for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == Ms and v:FindFirstChild("Humanoid") then
                           if v.Humanoid.Health > 0 then
                              repeat game:GetService("RunService").Heartbeat:wait()
                                 if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
                                    if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
                                       EquipWeapon(_G.SelectWeapon)
                                       TP(v.HumanoidRootPart.CFrame * CFrame.new(0,25,0))
                                       v.HumanoidRootPart.CanCollide = false
                                       v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
                                       game:GetService("VirtualUser"):CaptureController()
                                       game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
                                       PosMon = v.HumanoidRootPart.CFrame
                                       MagnetActive = true
                                    else
                                       MagnetActive = false    
                                       game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                                    end
                                 else
                                    MagnetActive = false
                                    CheckQuestLunarHub()
                                    TP(CFrameMon)
                                 end
                              until not v.Parent or v.Humanoid.Health <= 0 or _G.AutoFarmLv == false or game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == false or not game:GetService("Workspace").Enemies:FindFirstChild(v.Name)
                           end
                        end
                     end
                  else
                     MagnetActive = false
                     CheckQuestLunarHub()
                     TP(CFrameMon)
                  end
               end)
            end
         end
      end
   end)
   spawn(function()
       while wait() do
       if _G.AutoFarmLv then
           Attack()
           end
       end
   end)
   spawn(function()
       while wait() do
       if _G.AutoFarmLv then
               local noclip = Instance.new('Part',workspace)
               noclip.Name = "noclip"
               noclip.CanCollide = true
               noclip.Anchored = true
               noclip.Size = Vector3.new(30,0,30)
               noclip.Transparency = 1
               game:GetService("Workspace")["noclip"].CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame  * CFrame.new(0,-5,0)
           end
       end
   end)

          Main:Toggle("Auto SetSpawnPoint", _G.AutoSetSpawn, function(a)
      _G.AutoSetSpawn = a
          end)
          Main:Toggle("Auto Superhuman", _G.AutoSuperhuman, function(vu)
      _G.AutoSuperhuman = vu
      Superhuman = vu
  end)
  
  spawn(function()
     pcall(function()
        while wait(.1) do
           if Superhuman then
              if game.Players.LocalPlayer.Backpack:FindFirstChild("Combat") or game.Players.LocalPlayer.Character:FindFirstChild("Combat") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw") or game.Players.LocalPlayer.Backpack:FindFirstChild("Sharkman Karate") or game.Players.LocalPlayer.Character:FindFirstChild("Sharkman Karate") or game.Players.LocalPlayer.Backpack:FindFirstChild("Death Step") or game.Players.LocalPlayer.Character:FindFirstChild("Death Step") then
                 local args = {
                    [1] = "BuyBlackLeg"
                 }
                 game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
              end
              if game.Players.LocalPlayer.Character:FindFirstChild("Combat") or game.Players.LocalPlayer.Backpack:FindFirstChild("Combat") or game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") or game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") or game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") then
                 if game.Players.LocalPlayer.Backpack:FindFirstChild("Combat") or game.Players.LocalPlayer.Character:FindFirstChild("Combat") then
                    _G.SelectWeapon = "Combat"
                 end
                 if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") then
                    _G.SelectWeapon = "Black Leg"
                 end
                 if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Electro") then
                    _G.SelectWeapon = "Electro"
                 end
                 if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate") then
                    _G.SelectWeapon = "Fishman Karate"
                 end
                 if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") then
                    _G.SelectWeapon = "Dragon Claw"
                 end
                 if game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Superhuman") then
                    _G.SelectWeapon = "Superhuman"
                 end
                 if (game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 300) or (game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 300) then
                    local args = {
                       [1] = "BuyElectro"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                 end
                 if (game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 300) or (game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 300) then
                    local args = {
                       [1] = "BuyFishmanKarate"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                 end
              end
           end
        end
     end)
  end)
 
   function TP(P1)
      Distance = (P1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
      if Distance < 250 then
          Speed = 600
      elseif Distance < 500 then
          Speed = 400
      elseif Distance < 1000 then
          Speed = 350
      elseif Distance >= 1000 then
          Speed = 200
      end
      game:GetService("TweenService"):Create(
          game.Players.LocalPlayer.Character.HumanoidRootPart,
          TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
          {CFrame = P1}
      ):Play()
  end

          Main:Button("Redeem All Code Xp×2", function()
        function UseCode(Text)
          game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(Text)
      end
      UseCode("UPD16")
      UseCode("2BILLION")
      UseCode("UPD17")
      UseCode("UPD15")
      UseCode("FUDD10")
      UseCode("BIGNEWS")
      UseCode("THEGREATACE")
      UseCode("SUB2GAMERROBOT_EXP1")
      UseCode("StrawHatMaine")
      UseCode("Sub2OfficialNoobie")
      UseCode("SUB2NOOBMASTER123")
      UseCode("Sub2Daigrock")
      UseCode("Axiore")
      UseCode("TantaiGaming")
      UseCode("STRAWHATMAINE")
      UseCode("Bluxxy")
      UseCode("sub2fer999")
      UseCode("")
      UseCode("")
      UseCode("")
      end)
    
  spawn(function()
      pcall(function()
          while wait() do
              if _G.AutoSetSpawn then
                  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
              end
          end
      end)
  end)


local Settings = Window:Taps("Settings")
local Settings = Settings:newpage()
      Settings:Label("Settings")

      Settings:Toggle("Fast Attack", _G.FastAtttk, function(vu)
    _G.FastAtttk = vu
   end)
      Settings:Toggle("Bring Mob", true,function(vu)
      Magnet = vu
      end)
      Settings:Toggle("Auto Haki", true,function(vu)
      _G.AutoHakiBuso = vu
      end)
      Settings:Toggle("Lockmob",false,function(value)
    _G.LockMob = value
    if _G.LockMob == true then
    while _G.LockMob do wait()
        CheckQuestLunarHub()
        for k,x in pairs(game.Workspace.Enemies:GetChildren()) do
            if x.Name == Ms and x:FindFirstChild("HumanoidRootPart") and x:FindFirstChild("Humanoid") and x.Humanoid.Health > 0 and (x.HumanoidRootPart.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= magbring then
                        x.HumanoidRootPart.CanCollide = false
                        x.HumanoidRootPart.CFrame = PosMon
                        x.Humanoid.PlatformStand = false
                        x.Humanoid:ChangeState(11)
                        wait(0.1)
                        x.HumanoidRootPart.Anchored = false
            end 
        end
    end
    end
    if _G.LockMob == false then
        CheckQuestLunarHub()
        for k,x in pairs(game.Workspace.Enemies:GetChildren()) do
                    if x.Name == Ms and x:FindFirstChild("HumanoidRootPart") and x:FindFirstChild("Humanoid") and x.Humanoid.Health > 0 and (x.HumanoidRootPart.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= magbring then
                        x.HumanoidRootPart.CanCollide = false
                        x.HumanoidRootPart.CFrame = PosMon
                        x.Humanoid.PlatformStand = false
                        x.Humanoid:ChangeState(11)
                        wait(0.2)
                        x.HumanoidRootPart.Anchored = false
                    end 
                end
    end
    end)

   spawn(function()
      while wait(.1) do
         if _G.AutoHakiBuso then
            if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
               game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
            end
         end
      end
   end)


local Stats = Window:Taps("Stats")
local Stats = Stats:newpage()
      Stats:Label("Stats")

       
    Stats:Toggle("Melee", _G.Melee, function(Value)
        Melee = Value
        _G.Melee = Value
    end)
     
    Stats:Toggle("Defense", _G.Defense, function(Value)
        Defense = Value
        _G.Defense = Value
    end)
     
    Stats:Toggle("Sword", _G.Sword, function(Value)
        Sword = Value
        _G.Sword = Value
    end)
     
    Stats:Toggle("Gun", _G.Gun, function(Value)
        Gun = Value
        _G.Gun = Value
    end)
     
    Stats:Toggle("Devil Fruit", _G.DevilFruit, function(Value)
        DevilFruit = Value
        _G.DevilFruit = value
    end)
     
    SelectPoint = 6
    Stats:Slider("Point", 1,50,1, function(Point)
        SelectPoint = Point
    end)
    
     
     spawn(function()
        while wait(.1) do
            if Melee then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Melee", SelectPoint)
            end
        end
     end)
     
     spawn(function()
        while wait(.1) do
            if Defense then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Defense", SelectPoint)
            end
        end
     end)
     
     spawn(function()
        while wait(.1) do
            if Sword then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Sword", SelectPoint)
            end
        end
     end)
     
     spawn(function()
        while wait(.1) do
            if Gun then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Gun", SelectPoint)
            end
        end
     end)
     
     spawn(function()
        while wait(.1) do
            if DevilFruit then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Demon Fruit", SelectPoint)
            end
        end
     end)
    
    local RigC = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework) 
    local Rig = require(LocalPlayer.PlayerScripts.CombatFramework.RigController)
    local kkii = require(game.ReplicatedStorage.Util.CameraShaker)
    local CameraShaker = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)
    spawn(function()
        game:GetService('RunService').Heartbeat:connect(function()
            if _G.FastAtttk then
                pcall(function()
            RigC.activeController.timeToNextAttack = -(math.huge^math.huge^math.huge)
            RigC.activeController.hitboxMagnitude = 100
            RigC.activeController.attacking = false
    		RigC.activeController.increment = 3
    		RigC.activeController.humanoid.AutoRotate = true
    		RigC.activeController.blocking = false
    		Rig.activeController.focusStart = 0
            kkii:Stop()
            CameraShaker.CameraShakeInstance.CameraShakeState = {FadingIn = 3, FadingOut = 2, Sustained = 0, Inactive = 1}
                end)
            end
        end)
    end)
       
   if _G.FastAtttk == false then
	_G.FastAtttk = false
else
	_G.FastAtttk = false
end

local RigC = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
    local VirtualUser = game:GetService('VirtualUser')
    local kkii = require(game.ReplicatedStorage.Util.CameraShaker)
    local LocalPlayer = game.Players.LocalPlayer
    local Framework = {
        Combat = require(LocalPlayer.PlayerScripts.CombatFramework),
        Rig = require(LocalPlayer.PlayerScripts.CombatFramework.RigController)
    }
    local cd = 0.1
    function Attack()
        spawn(function()
            while wait() do
            pcall(function()
                local Controller = Framework.Combat.activeController
                if Controller and tick() >= cd then
                    cd = tick() + 0.1
                    spawn(function()
                        Controller:attack()
                    end)
                    Controller.increment = 4
                end
            end)
        end
        end)
    end

    spawn(function()
        for i = 1,9999999999999999999999999999999999999999999999999999 do game:GetService('RunService').Heartbeat:wait()
        if _G.FastAtttk then
        
        end
    end
end)

spawn(function()
    game:GetService("RunService").Stepped:Connect(function()
        if _G.FastAtttk == true then
            game.Players.LocalPlayer.Character.Stun.Value = 0
            game.Players.LocalPlayer.Character.Humanoid.Sit = false
            game.Players.LocalPlayer.Character.Busy.Value = false        
        end
        wait(1)
    end)
end)

pcall(function()
	for i, v in pairs(game.Workspace["_WorldOrigin"]:GetChildren()) do
            if v.Name == "CurvedRing" or v.Name == "SlashHit" or v.Name == "SwordSlash" or v.Name == "Sounds" then
                v:Destroy() 
            end
        end
end)
spawn(function()
    while wait() do
        if sethiddenproperty then
            sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",99999999999)
        end 
        if setscriptable then
            setscriptable(game.Players.LocalPlayer, "SimulationRadius", true)
            game.Players.LocalPlayer.SimulationRadius = math.huge * math.huge, math.huge * math.huge * 1 / 0 * 1 / 0 * 1 / 0 * 1 / 0 * 1 / 0
        end
    end
end)

