RegisterCommand('tptowp', function(source, args, rawCommand)
    local playerPed = PlayerPedId()
    local waypointBlip = GetFirstBlipInfoId(8) -- 8 is the blip id for waypoints

    if DoesBlipExist(waypointBlip) then
        local coord = GetBlipInfoIdCoord(waypointBlip)

        for height = 1, 1000 do
            SetPedCoordsKeepVehicle(playerPed, coord.x, coord.y, height + 0.0)

            local foundGround, zPos = GetGroundZFor_3dCoord(coord.x, coord.y, height + 0.0)

            if foundGround then
                SetPedCoordsKeepVehicle(playerPed, coord.x, coord.y, zPos + 0.0)
                break
            end

            Wait(5)
        end
    else
        TriggerEvent('chat:addMessage', {
            args = {"^1Error", "You need to set a waypoint on the map first!"}
        })
    end
end, false)
