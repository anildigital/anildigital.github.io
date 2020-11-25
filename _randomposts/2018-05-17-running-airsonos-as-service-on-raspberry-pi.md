--- 
title: Running AirSonos as systemd service on Raspberry Pi
layout: post
---

Pre-requisite - You need to have Raspberry Pi in the same WiFi network

1. Follow AirSonos installation from https://github.com/stephen/airsonos
2. Create a file named `airsonos.service` in folder `/etc/systemd/system` with following content
    ```
    [Unit]
    Description=Start airsonos server
    After=network.target
    [Service]
    Type=simple
    ExecStart=/usr/bin/airsonos
    [Install]
    WantedBy=multi-user.target
    ```
3. Restart Raspberry Pi and you should be able to see AirSonos in Airplay devices from your iPhone/iPad etc.
