# User Guide for Device Data JSON

This document provides a detailed explanation of the JSON structure for managing device information, metadata, status, and associated data. It is designed to help users understand the schema and use it effectively.

## JSON Schema Overview

### 1. `deviceId` (Required)
- **Type**: String
- **Description**: A unique identifier for the device.
- **Example**: `"unique-device-id"`

### 2. `metadata`
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

### 3. `status`
- **Type**: Object
- **Description**: Provides the current network and registration status of the device.
  - `network`: Indicates if the device is online or offline.
  - `registration`: Registration status of the device (e.g., `pending`).
- **Example**:
  ```json
  {
    "network": "online",
    "registration": "pending"
  }
  ```

### 4. `ioLights`
- **Type**: Array of Objects
- **Description**: Represents the status and attributes of input/output indicator lights.
  - `id`: Unique identifier for the light.
  - `status`: Current status (e.g., `active`, `inactive`).
  - `color`: Color of the light (e.g., `green`, `red`).
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

### 5. `data`
- **Type**: Array of Objects
- **Description**: Contains data readings from the device.
  - `name`: Name of the data (e.g., `speed`, `fuel`).
  - `value`: Measured value.
  - `unit`: Unit of the value (e.g., `km/h`, `l`, `Celsius`).
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

### 6. `alerts`
- **Type**: Array of Objects
- **Description**: Contains alert messages for critical events.
  - `type`: Type of alert (e.g., `overheat`).
  - `severity`: Severity level (e.g., `critical`).
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

### 7. `actions`
- **Type**: Array of Objects
- **Description**: Represents actions performed or pending on the device.
  - `type`: Action type (e.g., `register_device`).
  - `status`: Current status of the action (e.g., `pending`).
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

### 8. `errors`
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
- Ensure unique identifiers for elements like `ioLights` and `actions` to avoid conflicts.
- Follow standard conventions when extending the schema to ensure compatibility.

