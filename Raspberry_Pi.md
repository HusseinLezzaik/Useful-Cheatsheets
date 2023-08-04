## Config
- To configure the board of the raspberry pie, somethings are done directly to the board of the pie rather to the SD Card image of it.
- For example, to use the pie camera you need to change things from the board directly using the command below, otherwise even if connected it won't see it.
```
$ raspi-config
```

## Default
- It has by default a hotspot of 10.42.0.1 when the pie is not connected onto the internet, so that you can connect to it from your personal pc and then ssh into it using the following commands:
```
$ ssh ubuntu@10.42.0.1
$ password: robotseverywhere
```

## To connect the Jetson Nano with a Raspberry Pie
- With the ethernet cable connected in between, plug-in the following values directly from the screen next to wired-connection:
```
$ Address: 10.10.10.2
$ Network: 255.255.255.0
$ Gateway: 10.10.10.1
```

## Notes
- To bridge two devices like Raspberry Pies or Jetson Nanos, you can use an ethernet cable in between them both. We define the subnet IP address of it for any local hardware communications via the ethernet port, therefore we can simply just ssh into it using these IP addresses after defining the static ip subnet ethernet port
- If you're loosing network connection to the pie, try turning on/off, try changing it's location, try reboot the whole local network
