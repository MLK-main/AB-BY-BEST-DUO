-- Configuration settings
configurations = {
    ["fudidin_z"] = {
        BrolyPad = 6,
        settings = {
            senzuspam = false,
            movespam = true,
            KiBroly = true,
            timeLimits = {
                queue = 30.5,
                broly = 180,
                earth = 3.5,
            }
        },
        moveset = {
            "Blaster Meteor",
            "",
            "",
            "",
        },
    },
    ["Saiyan2KonTOP"] = {
        BrolyPad = 2,
        settings = {
            senzuspam = true,
            movespam = true,
            KiBroly = true,
            timeLimits = {
                queue = 16.5,
                broly = 15,
                earth = 3.5,
            }
        },
        moveset = {
            "Big Bang Kamehameha",
            "Chain Destructo Disk",
            "",
            "",
        },
    },
}

loadstring(game:HttpGet("https://insomniasscripts.nl/InsomniumMainScripts/Insomnium/InsomniumAutoBroly.lua"))()
