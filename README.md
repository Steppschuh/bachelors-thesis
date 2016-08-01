# Bachelor's Thesis
My Bachelor's Thesis in computer science, written at the [Hasso Plattner Institute](http://hpi.de/). PDF version available [here](https://github.com/Steppschuh/bachelors-thesis/blob/master/Export/bachelor_thesis.pdf).

### Accessing and transferring sensor data on Wearables in real-time
Wearable devices such as smartwatches or activity trackers with embedded sensors are capable of exchanging data with other connected devices. This data will often be transferred to the manufacturer or processed directly on a connected smartphone in order to provide user feedback based on the analyzed data. Almost every wearable device offers third-party developers a way to gain (at least partial) access to the gathered sensor data, allowing custom applications to process them.

In the course of this work, the availability of APIs on different wearables and how likely they can be used to transfer and process sensor data in real-time has been evaluated. We have presented functional implementations for transferring data between wearables and mobile devices powered by the Android platform. Performance, efficiency and battery impact have been analyzed using benchmarks.

![Screencast](https://raw.githubusercontent.com/Steppschuh/Sensor-Data-Logger/master/Media/Screencasts/sensor_data_bw_long_500.gif)

### Conclusion
Our project goal was the seamless authentication using nothing but the sensors from a user's devices.
To achieve this, we needed to handle huge amounts of sensor data from wearable devices, but without draining the device batteries. This required a way to transfer the data to mobile devices, as they have higher battery capacities and are capable of processing the data in real-time.

We decided to develop our project for the Android platform because of its open nature.
It provides access to the sensor data and all the functionalities that we needed without any limitations.

Our solution provides a performant jet battery friendly way of exchanging messages with data payloads between wearables and mobile devices. It allowed us to develop a product that fulfilled all our project requirements.

We evaluated the performance, efficiency and battery impact of our implementation. Our benchmarks showed that we were able to stream 3-dimensional data from 2 different motion sensors simultaneously with 230 Hz while only consuming 326 mAh per hour. By using optimized data batches, we reduced the transmission delay per sent byte by 94% while only raising the total delay by 3.2%.

We also implemented our solution in an [open source app](https://github.com/Steppschuh/Sensor-Data-Logger) that is available for free through the [Google Play Store](https://play.google.com/store/apps/details?id=net.steppschuh.sensordatalogger). It is capable of visualizing sensor data from the current mobile or a connected wearable device in real-time. This app can be used as a reference for related research and for demonstration purposes.
