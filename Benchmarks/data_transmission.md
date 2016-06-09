## Data Transmission Delay
The average delay between *"Started sending a data batch from an Android Wear device"* and *"Received the data batch on a connected Android handset"*.

---

### Benchmark #1

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
Nexus 9        | Tablet          |   23         | Beta Release Build
LG G Round     | Watch           |   23         | 

### Benchmark #1.1
Devices are lying next to each other. Requesting 3-dimensional accelerometer data **every 50 ms**.

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | delay / bytes  | Comment 
 ---------------: | ------------: | ----------------: | -------------: | -------
1,266,250,000     |  500          | 200               | ~        | ~1 update (`SENSOR_DELAY_NORMAL`)
1,271,160,000     |  500          | 482               | ~        | ~2 updates (`SENSOR_DELAY_UI`)
1,285,510,000     |  500          | 1,056             | ~        | ~6 updates (`SENSOR_DELAY_GAME`)
1,306,400,000     |  500          | 3,599             | ~        | ~24 updates (`SENSOR_DELAY_FASTEST`)

### Benchmark #1.2
Devices are lying next to each other. Requesting 3-dimensional accelerometer data **every 500 ms**.

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | delay / bytes  | Comment 
 ---------------: | ------------: | ----------------: | -------------: | -------
1,329,120,000     |  500          | 625               | ~        | ~3 update (`SENSOR_DELAY_NORMAL`)
1,331,970,000     |  500          | 1,340             | ~        | ~8 updates (`SENSOR_DELAY_UI`)
1,373,370,000     |  500          | 8,262             | ~        | ~28 updates (`SENSOR_DELAY_GAME`)
1,412,810,000     |  500          | 16,951            | ~        | ~118 updates (`SENSOR_DELAY_FASTEST`)

### Benchmark #1.3
Devices are about **5 meters apart**. Requesting data from **multiple sensors** with `SENSOR_DELAY_FASTEST` **every 500 ms**.

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | delay / bytes  | Comment 
 ---------------: | ------------: | ----------------: | -------------: | -------
819,430,000       |  500          | 17,968            | ~        | 1 sensor, ~125 updates
739,350,000       |  500          | 23,296            | ~        | 2 sensors, ~252 updates
895,970,000       |  500          | 42,805            | ~        | 3 sensors, ~393 updates
1,177,132,000     |  500          | 86,801            | ~        | 5 sensors, ~730 updates

