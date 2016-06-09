## Data Transmission Duration
Text that describes what was measured. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec euismod est vel augue laoreet gravida. Ut ut sapien et diam pretium sollicitudin. In hendrerit dolor ut nunc posuere dapibus.

- Generate request response (watch)
- Serialize request response (watch)
- Transfer data (watch → mobile)
- Deserialize data

### Benchmark #1

#### Conditions
Devices are lying next to each other.

#### Used Devices
 Name          | Device Type     | Android SDK  | Comment 
 :------------ | :-------------: | -----------: | -------
Nexus 9        | Tablet          |   23         | Beta Release Build
LG G Round     | Watch           |   22         | 

#### Results
 ∅ delay in ns    | Measurements  | Transferred bytes | Comment 
 ---------------: | ------------: | ----------------: | -------
166.108.000       |  500          | 341               | 1 update (`SENSOR_DELAY_NORMAL`)
173.952.000       |  500          | 484               | 2 updates (`SENSOR_DELAY_UI`)
188.960.000       |  500          | 1340              | 8 updates (`SENSOR_DELAY_GAME`)
204.540.000       |  500          | 5045              | 34 updates (`SENSOR_DELAY_FASTEST`)

