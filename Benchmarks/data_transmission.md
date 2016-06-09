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

#### Used Devices
 Name          | Device Type     | Android SDK  | Comment 
 :------------ | :-------------: | -----------: | -------
Nexus 9        | Tablet          |   23         | Beta Release Build
LG G Round     | Watch           |   23         | 

---

### Benchmark #1

#### Conditions
Devices are lying next to each other. Requesting 3-dimensional accelerometer data **every 100 ms**.

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | delay / bytes  | Comment 
 ---------------: | ------------: | ----------------: | -------------: | -------
66,108,000        |  500          | 341               | ~193,865       | ~1 update (`SENSOR_DELAY_NORMAL`)
73,952,000        |  500          | 484               | ~152,793       | ~2 updates (`SENSOR_DELAY_UI`)
88,960,000        |  500          | 1340              | ~66,388        | ~8 updates (`SENSOR_DELAY_GAME`)
104,540,000       |  500          | 5045              | ~20,721        | ~34 updates (`SENSOR_DELAY_FASTEST`)

---

### Benchmark #2

#### Conditions
Devices are lying next to each other. Requesting 3-dimensional accelerometer data **every 500 ms**.

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | delay / bytes  | Comment 
 ---------------: | ------------: | ----------------: | -------------: | -------
647,100,000       |  500          | 626               | ~1,033,706     | ~3 updates (`SENSOR_DELAY_NORMAL`)
649,840,000       |  500          | 1196              | ~543,344       | ~8 updates (`SENSOR_DELAY_UI`)
657,940,000       |  500          | 4183              | ~157,289       | ~28 updates (`SENSOR_DELAY_GAME`)
787,030,000       |  500          | 17942             | ~43,865        | ~125 updates (`SENSOR_DELAY_FASTEST`)

---

### Benchmark #3

#### Conditions
Devices are about **5 meters apart**. Requesting data from **multiple sensors** with `SENSOR_DELAY_FASTEST` **every 500 ms**.

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | delay / bytes  | Comment 
 ---------------: | ------------: | ----------------: | -------------: | -------
819,430,000       |  500          | 17968             | ~45,604        | 1 sensor, ~125 updates
739,350,000       |  500          | 23296             | ~31,737        | 2 sensors, ~252 updates
895,970,000       |  500          | 42805             | ~20,931        | 3 sensors, ~393 updates
1,177,132,000     |  500          | 86801             | ~13,561        | 5 sensors, ~730 updates

