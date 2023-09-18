# Charge Tesla on Excess Solar ☀️

## Overview

This Home Assistant automation triggers the charging of your Tesla when there is excess solar energy and stops charging when the solar production is low. It operates under specific conditions, ensuring efficient use of your solar energy between March and October. 

## Automation Breakdown

### Trigger
- **Time Pattern**: Checks conditions every 5 minutes.

### Conditions
- **Sun**: Only between sunrise and sunset.
- **Tesla Vehicle Connection**: Only when a vehicle is connected to the Tesla wall connector.
- **Month**: Only operates between March and October.
- **Battery & Charge Limit**: The absolute difference between the current battery level and charge limit is more than 1.
  
### Actions
1. **Enable Charging**
   - When the energy production exceeds the usage by more than 3500W and the Tesla is not charging.
   - Notification: "Tesla charging triggered, excess solar above 4KW ☀️".

2. **Disable Charging**
   - When the energy production is less than 500W below energy usage, the Tesla has been charging for at least 15 minutes, the battery level is at or above 25%, and the estimated time until the charge is complete is 10 minutes or more.
   - Notification: "Tesla charging disabled, solar production is low ⛅".

## Entity IDs
- `binary_sensor.tesla_wall_connector_vehicle_connected`
- `binary_sensor.denis_tesla_charging`
- `sensor.denis_tesla_battery`
- `number.denis_tesla_charge_limit`
- `sensor.energy_production`
- `sensor.energy_usage`
- `sensor.denis_tesla_time_charge_complete`
- `switch.denis_tesla_charger`

## Notifications
- Service: `notify.notify`

Feel free to contribute and suggest improvements to this automation! 💫
