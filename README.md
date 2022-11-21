# Homeassistant example repository

This repository serves for learning purposes.
It is meant to showcase a setup for one local sensor within homeassistant
sending data via MQTT (running in a container via docker-compose).

# Commands and steps

Generate mosquitto password:
`mosquitto_passwd -c ./mosquitto/config/password.txt xtrinch`

Spawn containers:
`docker-compose up`

Home assistant will be subsequently running at:
`http://localhost:8123`

Configure mqtt via web interface: 
`localhost/1884/xtrinch/password`

Subscribe to all topics of MQTT:
`mosquitto_sub -v -h localhost -p 1884 -t '#'`

Publish a sample message as the test sensor
`mosquitto_pub -h localhost -p 1884 -t 'sensor/topic' -u xtrinch -P password -m '{"temperature":22.2}'`
