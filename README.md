# rasp-pi-pico-SHT11-LCD
I provide the program code and cable schematic as well as additional display units with micropython code

based on : <a href="https://github.com/ayoy/upython-aq-monitor">Dominik Kapusta</a> and <a href="https://github.com/2black0/micropython-sht11">seto_ardy</a>
and thanks to Wahyu Ansari for help me create code 

### How to Use
```python
from machine import I2C, Pin
from utime import sleep
from sht11 import SHT11
from pico_i2c_lcd import I2cLcd
i2c = I2C(0, sda=Pin(0), scl=Pin(1), freq=400000)

I2C_ADDR = 63
lcd = I2cLcd(i2c, I2C_ADDR, 2, 16)
sht = SHT11(sck=5, data=4)

while True:
    tempOut = sht.temperature()
    humOut = sht.humidity()
    lcd.move_to(0,0)
    lcd.putstr("T = "+str(tempOut)+ chr(223) +"C")
    lcd.move_to(0,1)
    lcd.putstr("RH = "+str(humOut)+" %")
    sleep(1)
    lcd.clear()
```





