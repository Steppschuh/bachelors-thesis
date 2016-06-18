## Data Transmission Delay
The average delay between *"Started sending a data batch from an Android Wear device"* and *"Received the data batch on a connected Android handset"*.

---

### Benchmark #1
Devices are lying next to each other.

#### Measured operations
- Generate request response (watch)
  - Get sensor data since last response
- Serialize request response (watch)
  - Using the [Jackson](https://github.com/FasterXML/jackson-databind) ObjectMapper
- Transfer data (watch → mobile)
  - Using the [MessageApi](https://developers.google.com/android/reference/com/google/android/gms/wearable/MessageApi)
- Deserialize data (mobile)

#### Used Devices
 Name          | Device Type     | Android SDK  | Comment 
 :------------ | :-------------: | -----------: | -------
Nexus 9        | Tablet          |   24         | Beta Release Build
LG G Round     | Watch           |   23         | 

### Benchmark #1.1
Requesting 3-dimensional accelerometer data **every 50 ms**.

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | delay / bytes  | Comment 
 ---------------: | ------------: | ----------------: | -------------: | -------
1,266,250,000     |  500          | 200               | ~6,331,250     | ~1 update (`SENSOR_DELAY_NORMAL`)
1,271,160,000     |  500          | 482               | ~2,637,261     | ~2 updates (`SENSOR_DELAY_UI`)
1,285,510,000     |  500          | 1,056             | ~1,217,339     | ~6 updates (`SENSOR_DELAY_GAME`)
1,306,400,000     |  500          | 3,599             | ~362,989       | ~24 updates (`SENSOR_DELAY_FASTEST`)

### Benchmark #1.2
Requesting 3-dimensional accelerometer data **every 500 ms**.

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | delay / bytes  | Comment 
 ---------------: | ------------: | ----------------: | -------------: | -------
1,329,120,000     |  500          | 625               | ~2,126,592     | ~3 updates (`SENSOR_DELAY_NORMAL`)
1,331,970,000     |  500          | 1,340             | ~994,007       | ~8 updates (`SENSOR_DELAY_UI`)
1,373,370,000     |  500          | 8,262             | ~166,227       | ~28 updates (`SENSOR_DELAY_GAME`)
1,412,810,000     |  500          | 16,951            | ~83,346        | ~118 updates (`SENSOR_DELAY_FASTEST`)

### Benchmark #1.3
Requesting data from **multiple sensors** with `SENSOR_DELAY_FASTEST` **every 500 ms**.

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | delay / bytes  | Comment 
 ---------------: | ------------: | ----------------: | -------------: | -------
1,452,400,000     |  500          | 16,690            | ~87,022        | 1 sensor, ~116 updates
1,489,100,000     |  500          | 22,819            | ~65,257        | 2 sensors, ~246 updates
1,752,420,000     |  500          | 60,679            | ~28,880        | 4 sensors, ~512 updates
2,842,640,000     |  500          | 177,495           | ~16,015        | 8 sensors, ~1504 updates

