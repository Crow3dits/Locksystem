```
Config = {
    LockingRange = 5.0,
    CycleVehicleClass = 13,
    Keyitem = "carkeys",
    KeyPrice = 100,
    KeyShop = {
        Ped = {
            Model = 'a_m_m_business_01',
            Position = vector4(170.0408, -1799.5764, 28.3159, 322.9936)
        }
    }
}

Config.lockpickitem = "lockpick"

Config.keymappinglabel = "Start the engine"

Config.startbutton = "M"

Config.inventory = 'ox_inventory' -- ox_inventory / qs-inventory

Config.Delay = 0 -- 2s

Config.UnlockedChance = 0 --- Can be configured from client/function.lua

Config.Luck = math.random(1, 100) --- Can be configured from client/function.lua

Config.Lang = 'EN' --- Can be added more from shared/locales.lua

Config.AnimDict = "anim@veh@std@panto@ds@base"
Config.AnimName = "hotwire"

Config.AlarmTime = 10 -- seconds

Config.Notifications = 'ox_lib' -- ox_lib or esx


---Notifi
function Notifi(data)
    if Config.Notifications == 'ox_lib' then
        lib.defaultNotify({
            title = Config.title,
            description = data.text or data,
            duration = 6000,
            style = {
                backgroundColor = '#292929',
                color = '#c2c2c2',
                ['.description'] = {
                    color = '#cccccc'
                }
            },
            icon = data.icon or 'car',
            iconColor = data.color or '#d46363'
        })
    elseif Config.Notifications == 'esx' then
        TriggerEvent('esx:showNotification', data.text, "success", 3000)
    end
end

function NotifiServ(src, data)
    if Config.Notifications == 'ox_lib' then
        TriggerClientEvent('ox_lib:notify', src, {
            title = Config.title,
            description = data.text or data,
            duration = 6000,
            style = {
                backgroundColor = '#292929',
                color = '#c2c2c2',
                ['.description'] = {
                    color = '#cccccc'
                }
            },
            icon = data.icon or "car",
            iconColor = data.color or '#d46363'
        })
    elseif Config.Notifications == 'esx' then
        TriggerClientEvent('esx:showNotification', src, data.text, "success", 3000)
    end
end
```
