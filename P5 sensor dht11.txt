from machine import Pin
from time import sleep
import dht


sensor =dht.DHT11(Pin(14))

while True:
    try:
        sleep(1)
        sensor.measure()
        temp = sensor.temperature()
        hum = sensor.humidity()
        temp_f= temp*(9/5)+32.0
        print('temperature: %3.1f C'%temp)
        print('temperature: %3.1f F'%temp_f)
        print('Humidity:%3.1f%%'%hum)
    except OSError as e:
        print('Failed to read sensor.')
