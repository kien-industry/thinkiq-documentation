# User Guide for Device Data JSON

This document provides a detailed explanation of the JSON structure for managing device information, metadata, status, and associated data. It is designed to help users understand the schema and use it effectively.

## JSON Schema Overview

### 1. `deviceId` (Required)

- **Type**: String
- **Description**: A unique identifier for the device.
- **Example**: `"unique-device-id"`

### 2. `metadata` (Optional)

- **Type**: Object
- **Description**: Contains detailed information about the device.
  - `deviceType`: Type of the device (e.g., `sensor`).
  - `firmwareVersion`: Current firmware version of the device.
  - `imei`: International Mobile Equipment Identity of the device.
  - `serialNumber`: Unique serial number of the device.
  - `model`: Model identifier of the device.
- **Example**:
  ```json
  {
    "deviceType": "sensor",
    "firmwareVersion": "v1.0.0",
    "imei": "1234567890",
    "serialNumber": "1234567890",
    "model": "T1000"
  }
  ```

### 3. `status` (Optional)

- **Type**: Object
- **Description**: Provides the current status of the device.
  - `network`: Indicates if the device is online or offline.
  - `registration`: Registration status of the device (e.g., `pending`, `registered`, `unregistered`).
- **Example**:
  ```json
  {
    "network": "online",
    "registration": "pending"
  }
  ```

### 4. `ioLights` (Optional)

- **Type**: Array of Objects
- **Description**: Represents the status and attributes of input/output indicator lights.
  - `id`: Unique identifier for the light.
  - `status`: Current status (e.g., `active`, `inactive`).
  - `color`: Color of the light (e.g., `green`, `red`, `yellow`).
  - `message`: Description of the current light status.
- **Example**:
  ```json
  [
    {
      "id": "ioLight1",
      "status": "active",
      "color": "green",
      "message": "Operational"
    }
  ]
  ```

### 5. `data` (Optional)

- **Type**: Array of Objects
- **Description**: Contains data readings from the device.
  - `name`: Name of the data (e.g., `speed`, `fuel`).
  - `value`: Measured value.
  - `unit`: Unit of the value (e.g., `km/h`, `l`).
  - `series`: Identifier for the data series.
  - `description`: Description of the data point.
  - `timestamp`: Timestamp when the data was collected (ISO 8601 format).
- **Example**:
  ```json
  [
    {
      "name": "speed",
      "value": 25.3,
      "unit": "km/h",
      "series": "V",
      "description": "Speed of the truck",
      "timestamp": "2024-12-19T12:00:00Z"
    }
  ]
  ```

### 6. `alerts` (Optional)

- **Type**: Array of Objects
- **Description**: Contains alert messages for critical events.
  - `type`: Type of alert (e.g., `overheat`).
  - `severity`: Severity level (e.g., `critical`, `warning`, `info`).
  - `message`: Alert message.
  - `timestamp`: Timestamp of the alert (ISO 8601 format).
- **Example**:
  ```json
  [
    {
      "type": "overheat",
      "severity": "critical",
      "message": "Temperature exceeds threshold",
      "timestamp": "2024-12-19T12:10:00Z"
    }
  ]
  ```

### 7. `actions` (Optional)

- **Type**: Array of Objects
- **Description**: Represents actions performed or pending on the device.
  - `type`: Action type (e.g., `register_device`, `update_firmware`, `reset_device`).
  - `status`: Current status of the action (e.g., `pending`, `in_progress`, `completed`, `failed`).
  - `data`: Related data for the action.
  - `timestamp`: Timestamp of the action (ISO 8601 format).
- **Example**:
  ```json
  [
    {
      "type": "register_device",
      "status": "pending",
      "data": {
        "deviceId": "unique-device-id",
        "metadata": {
          "deviceType": "sensor",
          "firmwareVersion": "v1.0.0",
          "imei": "1234567890",
          "serialNumber": "1234567890",
          "model": "T1000"
        }
      },
      "timestamp": "2024-12-19T12:00:00Z"
    }
  ]
  ```

### 8. `errors` (Optional)

- **Type**: Array of Objects
- **Description**: Represents errors encountered by the device.
  - `code`: Error code.
  - `message`: Error message.
  - `timestamp`: Timestamp of the error (ISO 8601 format).
- **Example**:
  ```json
  [
    {
      "code": "TEMP_SENSOR_FAIL",
      "message": "Temperature sensor not responding",
      "timestamp": "2024-12-19T12:05:00Z"
    }
  ]
  ```

## Notes

- All timestamps are in ISO 8601 format.
- Follow standard conventions when extending the schema to ensure compatibility.
- This schema can be extended with additional fields as required. Updates to the schema will be reflected in this document.

## Example JSON

```json
{
  "deviceId": "unique-device-id",
  "metadata": {
    "deviceType": "sensor",
    "firmwareVersion": "v1.0.0",
    "imei": "1234567890",
    "serialNumber": "1234567890",
    "model": "T1000"
  },
  "status": {
    "network": "online",
    "registration": "pending"
  },
  "ioLights": [
    {
      "id": "ioLight1",
      "status": "active",
      "color": "green",
      "message": "Operational"
    },
    {
      "id": "ioLight2",
      "status": "inactive",
      "color": "red",
      "message": "Error detected"
    },
    {
      "id": "ioLight3",
      "status": "active",
      "color": "yellow",
      "message": "Signal strength moderate"
    }
  ],
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
  "alerts": [
    {
      "type": "overheat",
      "severity": "critical",
      "message": "Temperature exceeds threshold",
      "timestamp": "2024-12-19T12:10:00Z"
    }
  ],
  "actions": [
    {
      "type": "register_device",
      "status": "pending",
      "data": {
        "deviceId": "unique-device-id",
        "metadata": {
          "deviceType": "sensor",
          "firmwareVersion": "v1.0.0",
          "imei": "1234567890",
          "serialNumber": "1234567890",
          "model": "T1000"
        }
      },
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

---

## **Field Descriptions**

### **1. Root Fields**

- **`deviceId`** _(String)_: Unique identifier for the device.
- **`metadata`** _(Object, Optional)_: Contains additional information about the device.
- **`status`** _(Object, Optional)_: Provides the system's operational state.
- **`data`** _(Array)_: An array of data points collected by the device.
- **`alarms`** _(Array, Optional)_: Alarms triggered by the device.
- **`notifications`** _(Array, Optional)_: Notifications sent by the device.
- **`actions`** _(Array, Optional)_: Actions requested by the device.
- **`errors`** _(Array, Optional)_: Error or issue reporting from the device.

### **2. Metadata Fields**

- **`deviceType`** _(String)_: Type of device (e.g., sensor, actuator).
- **`firmwareVersion`** _(String)_: Current firmware version.
- **`imei`** _(String)_: IMEI of the device.
- **`serialNumber`** _(String)_: Serial number of the device.
- **`model`** _(String)_: Model of the device.

### **3. Status Fields**

- **`network`** _(String, Optional)_: Network status (e.g., online, offline).
- **`registration`** _(String, Optional)_: Registration status (e.g., pending, registered).

### **4. Data Fields**

Each object in the `data` array contains:

- **`name`** _(String)_: Name of the data point (e.g., temperature, humidity).
- **`value`** _(Number)_: The value of the measurement.
- **`unit`** _(String)_: Unit of measurement (e.g., Celsius, %, hPa).
- **`timestamp`** _(String)_: ISO 8601 UTC timestamp indicating when the data was measured.

### **5. Alerts Fields**

Each object in the `alerts` array contains:

- **`type`** _(String)_: Alert type (e.g., overheat, intrusion).
- **`severity`** _(String)_: Severity level (e.g., critical, warning).
- **`message`** _(String)_: Description of the alert.
- **`timestamp`** _(String)_: ISO 8601 UTC timestamp indicating when the alert was triggered.

### **7. Actions Fields**

Each object in the `actions` array contains:

- **`type`** _(String)_: Type of action (e.g., firmware_update, register_device, reset_device).
- **`status`** _(String)_: Status of the action (e.g., pending, in_progress, completed, failed).
- **`data`** _(Object)_: Data related to the action.
- **`timestamp`** _(String)_: ISO 8601 UTC timestamp.

### **8. Errors Fields**

Each object in the `errors` array contains:

- **`code`** _(String)_: Error code (e.g., TEMP_SENSOR_FAIL).
- **`message`** _(String)_: Description of the error.
- **`timestamp`** _(String)_: ISO 8601 UTC timestamp.

---

## **Example Usage**

### **MQTT Message**

**Topic:**

```plaintext
device/unique-device-id/data
```

**Payload:**

```json
{
  "deviceId": "device-001",
  "data": [
    {
      "name": "speed",
      "value": 22.5,
      "unit": "km/h",
      "series": "V",
      "description": "Speed of the truck",
      "timestamp": "2024-12-19T10:00:00Z"
    },
    {
      "name": "fuel",
      "value": 60,
      "series": "F",
      "unit": "l",
      "description": "Fuel level of the truck",
      "timestamp": "2024-12-19T12:00:00Z"
    }
  ]
}
```

## **Best Practices**

1. **Use Unique Identifiers**: Ensure each `deviceId` is unique across the system.
2. **ISO 8601 for Timestamps**: Use standardized UTC timestamps to avoid timezone issues.

---
