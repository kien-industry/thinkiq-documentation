```json
{
  "deviceId": "unique-device-id",
  "metadata": {
    "deviceType": "sensor",
    "firmwareVersion": "v1.0.0"
  },
  "status": {
    "network": "online"
  },
  "data": [
    {
      "name": "speed",
      "value": 25.3,
      "unit": "km/h",
      "series": "V",
      "description": "Speed of the truck",
      "timestamp": "2024-12-19T12:00:00Z"
    },
    {
      "name": "fuel",
      "value": 60,
      "series": "F",
      "unit": "l",
      "description": "Fuel level of the truck",
      "timestamp": "2024-12-19T12:00:00Z"
    },
    {
      "name": "temperature",
      "value": 25.3,
      "unit": "Celsius",
      "series": "C",
      "description": "Temperature of the truck",
      "timestamp": "2024-12-19T12:00:00Z"
    },
    {
      "name": "location",
      "value": {
        "latitude": 10.8231,
        "longitude": 106.6297
      },
      "series": "L",
      "description": "Location of the truck",
      "timestamp": "2024-12-19T12:00:00Z"
    }
  ],
  "alarms": [
    {
      "type": "overheat",
      "severity": "critical",
      "message": "Temperature exceeds threshold",
      "timestamp": "2024-12-19T12:10:00Z"
    }
  ],
  "notifications": [
    {
      "event": "low_battery",
      "message": "Battery level below 20%",
      "timestamp": "2024-12-19T12:15:00Z"
    }
  ],
  "actions": [
    {
      "type": "firmware_update",
      "requestedVersion": "v2.0.0",
      "timestamp": "2024-12-19T12:00:00Z"
    }
  ],
  "errors": [
    {
      "code": "TEMP_SENSOR_FAIL",
      "message": "Temperature sensor not responding",
      "timestamp": "2024-12-19T12:05:00Z"
    }
  ]
}
```
