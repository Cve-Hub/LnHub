local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/kickTh/New-Ui/main/Library-Robloxx.Ui.txt"))()
local window = library:Win()
local main = window:addtap("Main") -- tab1
local setting = window:addtap("Settings") -- tab2
local main = tap1:addpage() --page1
local main = tap2:addpage() --page2
local setting = tap1:addpage()
local setting = tap2:addpage()
main:Ti("Auto Farm")

main:Toggle("Toggle1",nil, function(value)
    print(value)
end)

main:Button("Button1", function(value)
    print(value)
end)

main:Button1("Button2", function(value)
    print(value)
end)

local getdrop = page1:DropDown("Name DropDown","Name",{"a","b","c"}, function(value)
    print(value)
end)

local getlable = page1:Label("Text Label")

local getslider = page1:Slder("Slider",1,100,8, function(value)
    print(value)
end)

page4:Ti("Title")

page4:Toggle("Toggle1",nil, function(value)
    print(value)
end)

page4:Button("Button1", function(value)
    print(value)
end)

page4:Button1("Button2", function(value)
    print(value)
end)

local getdrop = page4:DropDown("Name DropDown","Name",{"a","b","c"}, function(value)
    print(value)
end)

local getlable = page4:Label("Text Label")

local getslider = page4:Slder("Slider",1,100,8, function(value)
    print(value)
end)
