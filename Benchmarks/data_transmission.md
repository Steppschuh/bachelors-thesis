## Data Transmission Duration
The average delay between these two events:
- Started sending a data batch from an Android Wear device
- Received the data batch on a connected Android handset

The measurement includes the following operations:
- Generate request response (watch)
  - Get sensor data since last response
- Serialize request response (watch)
  - Using the [Jackson](https://github.com/FasterXML/jackson-databind) ObjectMapper
- Transfer data (watch → mobile)
  - Using the [MessageApi](https://developers.google.com/android/reference/com/google/android/gms/wearable/MessageApi)
- Deserialize data (mobile)

### Benchmark #1

#### Conditions
Devices are lying next to each other. Requesting 3-dimensional accelerometer data.

#### Used Devices
 Name          | Device Type     | Android SDK  | Comment 
 :------------ | :-------------: | -----------: | -------
Nexus 9        | Tablet          |   23         | Beta Release Build
LG G Round     | Watch           |   23         | 

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | Comment 
 ---------------: | ------------: | ----------------: | -------
166.108.000       |  500          | 341               | ~1 update (`SENSOR_DELAY_NORMAL`)
173.952.000       |  500          | 484               | ~2 updates (`SENSOR_DELAY_UI`)
188.960.000       |  500          | 1340              | ~8 updates (`SENSOR_DELAY_GAME`)
204.540.000       |  500          | 5045              | ~34 updates (`SENSOR_DELAY_FASTEST`)

### Benchmark #2

#### Conditions
Devices are about 5 meters apart.

#### Used Devices
 Name          | Device Type     | Android SDK  | Comment 
 :------------ | :-------------: | -----------: | -------
Nexus 9        | Tablet          |   23         | Beta Release Build
LG G Round     | Watch           |   23         | 

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | Comment 
 ---------------: | ------------: | ----------------: | -------
295.236.000       |  500          | 5022              | 1 sensor, ~34 updates (`SENSOR_DELAY_FASTEST`)
327.332.000       |  500          | 6637              | 2 sensors, ~70 updates (`SENSOR_DELAY_FASTEST`)
420.616.000       |  500          | 12528             | 3 sensors, ~111 updates (`SENSOR_DELAY_FASTEST`)

