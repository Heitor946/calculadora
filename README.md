-- VENTIS HUB - LOADER

local p1 = "https://"
local p2 = "raw.githubusercontent.com/"
local p3 = "Heitor946/"
local p4 = "VentisHub.lua/"
local p5 = "main/"
local p6 = "CRIPTOGRAFIA"

local url = table.concat({
    p1, p2, p3, p4, p5, p6
})

local success, result = pcall(function()
    return game:HttpGet(url)
end)

if success then
    local execute = loadstring(result)
    if execute then
        execute()
    end
else
    warn("Falha ao carregar o script.")
end
