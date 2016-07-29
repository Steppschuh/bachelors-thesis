## Battery Life
The drain of battery life when using the app.

---

### Benchmark #1
Devices are lying next to each other.

#### Measured operations
- Transfer data (watch → mobile)
  - Using the [MessageApi](https://developers.google.com/android/reference/com/google/android/gms/wearable/MessageApi)
- Deserialize data (mobile)

#### Used Devices
 Name          | Device Type     | Android SDK  | Comment 
 :------------ | :-------------: | -----------: | -------
Nexus 5X       | Phone           |   24         | Beta Release Build
Moto 360       | Watch           |   23         | 

### Benchmark #1.1
Requesting 3-dimensional data from the accelerometer and gravity sensor with `SENSOR_DELAY_FASTEST` every 50 ms for 1 hour.

#### Results
 Total    | System   | OS       | Bluetooth| Screen   | App 
 -------: | -------: | -------: | -------: | -------: | -------:
 615      | 65       | 97       | 32       | 162      | 226


