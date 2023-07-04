### Hardware setup mosaic-go

![Wiring diagram, Pixhawk 4 - mosaic-go](readme_assets/mosaic-go_wiring.png "Wiring diagram, Pixhawk 4 - mosaic-go")
![Septentrio Robotics Interface Board wiring diagram](readme_assets/RIB_wiring.png)

1. Make sure the receiver is powered with at least 3.3V. You can use the micro USB connector or the 6-pin connector.
2. Connect one or two GNSS antennas to the RF-IN ports on the mosaic-go.
3. Connect the 6-pin connector (COM1) to the Pixhawk's `GPS MODULE` port. This will provide power to the mosaic-go and with
   this single connection it will be able to send single and dual antenna information to the Pixhawk 4.
4. In the web interface or with Rx Tools, set the receiver's baud rate to 115200 **Admin > Expert Control > Control Panel > Communication > COM Port Settings** (this is the default value).


**Make sure the JST cable is wired correctly (since this is not a standard cable):**

![Wiring of JST cable](readme_assets/JST-cable.png "Wiring of JST cable")


_PX4 will ensure that the GNSS module is automatically configured however, if you have a dual antenna setup, it
is required to set the layout as accurately as possible in the web app._

#### Dual antenna

The attitude (heading/pitch) can be computed from the orientation of the baseline between the main and the aux1 GNSS antennas.

![Multi-antenna attitude determination setup](readme_assets/multi-antenna_attitude_setup.png)

To enable multi-antenna attitude determination, follow the following procedure:

1. Attach two antennas to your vehicle, using cables of approximately the same length. The default antenna configuration is as depicted in the figure.
   It consists in placing the antennas aligned with the longitudinal axis of the vehicle, main antenna behind aux1.
   For best accuracy, try to maximize the distance between the antennas, and avoid significant height difference between the antenna ARPs.
2. In practice, the two antenna ARPs may not be exactly at the same height in the vehicle frame, or the main-aux1 baseline may not be exactly parallel or perpendicular to the longitudinal axis of the vehicle. This leads to offsets in the computed attitude angles.
   These offsets can be compensated for with the **setAttitudeOffset** command.

_For optimal heading results, the two antennas should be seperated by at least 30cm / 11.8 in (ideally 50cm /
19.7in or more)_

_For additional configuration of the dual antenna setup, please refer to
our [Knowledge Base](https://support.septentrio.com/l/858493/2022-04-19/xgrqd) or the [hardware manual](https://web.septentrio.com/l/858493/2022-04-19/xgrql)_

#### Web app

mosaic-H GPS/GNSS receiver module with heading comes with fully documented interfaces, commands and data messages. The
included GNSS receiver control and analysis software [RxTools](https://web.septentrio.com/l/858493/2022-04-19/xgrqp)
allows receiver configuration, monitoring as well as data logging and analysis.

The receiver includes an intuitive web user interface for easy operation and monitoring allowing you to control the
receiver from any mobile device or computer. The web interface also uses easy-to-read quality indicators ideal to
monitor the receiver operation during the job at hand.

![Septentrio web user interface](readme_assets/Septentrio-mosaic-X5-H-T-CLAS-GNSS-Module-Receiver-WebUI.png)

### PX4 setup

![QGroundControl parameter settings](readme_assets/QGC_param.png)

### Single antenna setup
Edit the following parameters in the PX4 setup page:
|                | V1.13           | V1.14|
| -----------    | -----------     | ----------- |
| GPS_1_CONFIG   | GPS 1           | GPS 1   |
| GPS_1_GNSS     | 31              | 31|
| GPS_1_PROTOCOL | Septentrio (SBF)| Septentrio (SBF) |
| SER_GPS1_BAUD  | 115200 8N1      |  115200 8N1|

Go to **Tools > Reboot Vehicle**

### Dual antenna setup
Edit the following parameters in the PX4 setup page:
|                | V1.13           | V1.14|
| -----------    | -----------     | ----------- |
| GPS_1_CONFIG   | GPS 1           | GPS 1   |
| GPS_1_GNSS     | 31              | 31|
| GPS_1_PROTOCOL | Septentrio (SBF)| Septentrio (SBF) |
| GPS_PITCH_OFFSET | Set accordingly| Set accordingly |
| GPS_YAW_OFFSET | Set accordingly | Set accordingly|
| SER_GPS1_BAUD  | 115200 8N1      |  115200 8N1|
| EKF2_AID_MASK  | Use GPS & GPS fusion|  |
| EKF2_GPS_CTRL  |       |  Dual antenna heading|



Go to **Tools > Reboot Vehicle**


### LED Status

| LED Color     |  Powered  | SD card mounted | PVT Solution | Logging enabled |
|---------------|:---------:|:---------------:|:------------:|:---------------:|
| Red           | &check;️  |                 |              |                 |
| Green         | &check;️  |    &check;️     |              |                 |
| Blue          | &check;️  |    &check;️     |   &check;️   |                 |
| Purple        | &check;️  |                 |   &check;️   |                 |
| Purple + Blue | &check;️  |    &check;️     |   &check;️   |    &check;️     |
| Red + Green   | &check;️  |    &check;️     |              |    &check;️     |


For more detailed information about the mosaic-go and its module, please refer to the [hardware manual](https://web.septentrio.com/l/858493/2022-04-19/xgrrd) or the [Septentrio Support](https://support.septentrio.com/l/858493/2022-04-19/xgrrl) page.
