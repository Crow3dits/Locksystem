##### Complete vehicle locksystem.

### Owned vehicles:
You can start vehicles by clicking the start engine button (can be changed from config file). It will start the engine and will remove the key from your inventory and will insert the value to the owned_vehicle database "1" - Key is in the ignition or if you turn off your engine will change the value to the "0" and will return you the key.

So whatever happens to you, disconnected or car despawns, etc your vehicle with key inside the ignition, you can start it again as soon as you enter it (get it back from  the impound) simply click start engine button, it will search from the database to see if the key is in the ignition and if its in there will start the engine.

You can also start owned vehicle engine by using key from your inventory
Using key outside the vehicle locks and unlocks the vehicle.
When you exit  the vehicle while engine is running it keeps it running.
When someone enters to your vehicle while its running it does shut down but he can turn the engine on by turning key in the ignition with start engine button.

### Local vehicles (Not owned):
If you are not near to any vehicles and you use the lockpick, it says no vehicles are nearby.
If you use lockpick near any vehicles, it triggers the minigame, after successful minigame, comes animated progressbar, and then vehicle doors will be lockpicked.
As soon you enter the vehicle and you try to start the vehicle with the start engine button it will search the key, since its local vehicle it says there arent any keys left to the ignition and you have to hotwire it by using the lockpick again.
After successful hotwireing minigame the car starts and you can drive it. But after you shut down its engine you have to re-hotwire it to start again.
When you exit  the vehicle while engine is running it keeps it running.

## Vehicle key reordering
You can reorder or copy your vehicle keys in marked location.
Location can be changed.
Ped can be changed.
Blip information and ID can be changed.


### Setup
Required 
- ox_inventory
- ox_lib
- oxtarget
- es_extended
```
## Add this item to your: ox_inventory/data/items.lua
['carkeys'] = {
		label = 'Vehicle key',
		weight = 300,
		stack = false
},
### Optional item:
['keychain'] = {
		label = 'Keychain',
		weight = 2,
		stack = false,
		close = true,
		description = "To keep multiple keys at once with you"
	},

## Optional: /ox_inventory/modules/items/containers.lua
setContainerProperties('keychain', {
	slots = 5,
	maxWeight = 1000,
	whitelist = {
		['carkeys'] = true, -- grants you keychain with 5 slots for vehicle keys.
	}
})

Add this line to your: ox_inventory/modules/items/client.lua

Item('carkeys', function(data, slot)
	TriggerEvent('estrp-locksystem:client:useKey', slot)
end)
```
 

 ## Exports
 ```
To add vehicle key to your inventory use this export:

local plate = GetVehicleNumberPlateText(vehicle)--example is this
exports['estrp-locksystem']:AddKeys(plate)

To remove keys from the player, example at the end of the jobs, etc:

local plate = GetVehicleNumberPlateText(vehicle)
exports['estrp-locksystem']:RemoveKeys(plate)

To grant temporary key untill vehicle engine shut off:

local plate = GetVehicleNumberPlateText(vehicle)
exports['estrp-locksystem']:AddTempKeys(plate)
```


