## Chatter

This code publishes data on the topic `chatter`

### Build and Flash

Generate the ROS libraries prior to building this example as instructed in the [README](../../../README.md) of root directory

Default mode of rosserial communication is over UART.

To use WiFi:
1. Enable rosserial over WiFi

`idf.py menuconfig` -> `Component config` -> `rosserial` ->`rosserial over WiFi using TCP`

2. Enter WiFi and server details

```
$ export ESPPORT=/dev/ttyUSB0
$ idf.py build flash
```

On a new terminal

```
$ roscore
```

On another new terminal

-- UART
```
$ rosrun rosserial_python serial_node.py _baud:=11520
```
-- WiFi
```
$ rosrun rosserial_python serial_node.py tcp
```

On another new terminal

```
$ rostopic echo chatter
```
