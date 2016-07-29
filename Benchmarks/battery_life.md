## Battery Life
Observed the battery drain measured in Milliamp Hours (mAh) for one hour when using the app to transfer data from a wearable to a mobile device.

---

- **Total**: Overall battery consumption
- **System**: Android System processes
- **OS**: Android OS processes
- **BT**: Bluetooth sensor & related processes
- **App**: Sensor Data Logger

#### Used Devices
 Name          | Device Type     | Android SDK  | Comment 
 :------------ | :-------------: | -----------: | -------
Nexus 5X       | Phone           |   24         | Beta Release Build
Moto 360       | Watch           |   23         | 

### Benchmark #1
App not running. Phone idle, casually checking messages.

#### Measured operations
- Doing nothing

#### Results
 Total    | System   | OS       | BT       | Screen   | App 
 -------: | -------: | -------: | -------: | -------: | -------:
 163      | 27       | 20       | 13       | 32       | 0
 173      | 30       | 22       | 15       | 52       | 0
 173      | 34       | 19       | 13       | 39       | 0
 160      | 27       | 25       | 13       | 40       | 0
 
### Benchmark #2
Requesting 3-dimensional data from the accelerometer and gravity sensor with `SENSOR_DELAY_FASTEST` every 50 ms. 

#### Measured operations
- Transfer data (watch → mobile)
  - Using the [MessageApi](https://developers.google.com/android/reference/com/google/android/gms/wearable/MessageApi)
- Deserialize data (mobile)
  - Using the [Jackson](https://github.com/FasterXML/jackson-databind) ObjectMapper
- Processing data (mobile)
  - Rendering in a chart using [Canvas](https://developer.android.com/reference/android/graphics/Canvas.html)

### Benchmark #2.1
Screen constantly on at 20% brightness.

#### Results
 Total    | System   | OS       | BT       | Screen   | App 
 -------: | -------: | -------: | -------: | -------: | -------:
 615      | 65       | 97       | 32       | 162      | 226
 580      | 59       | 99       | 32       | 148      | 239
 593      | 67       | 91       | 34       | 161      | 226
 630      | 71       | 103      | 32       | 151      | 219

### Benchmark #2.2
Screen turned off, not rendering data.

#### Results
 Total    | System   | OS       | BT       | Screen   | App 
 -------: | -------: | -------: | -------: | -------: | -------:
 331      | 60       | 88       | 34       | 41       | 57
 318      | 59       | 92       | 30       | 38       | 64
 330      | 53       | 94       | 33       | 32       | 63
 325      | 57       | 92       | 33       | 40       | 59

