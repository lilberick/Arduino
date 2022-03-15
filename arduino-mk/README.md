# arduino-mk : Program your Arduino from the command line

## Instalación

```sh
$ sudo apt install arduino-mk
```

## Programar y cargar al arduino

* `$ mkdir blink`

* `$ ln -s /usr/share/arduino/Arduino.mk blink`
* `$ ls /dev/ttyACM0`
* `$ vim blink/Makefile`

	```make
	BOARD_TAG = uno
	ARDUINO_PORT = /dev/ttyACM0
	ARDUINO_LIBS = 
	ARDUINO_DIR = /usr/share/arduino
	include Arduino.mk
	```

* `$ vim blink/codigo.ino`

	```cpp
	int led=13;
	void setup(){
		pinMode(led,OUTPUT);
	}
	void loop(){
		digitalWrite(led,HIGH);
		delay(1000);
		digitalWrite(led,LOW);
		delay(1000);
	}
	```

* `$ make -C blink/`
* `$ make -C blink/ upload`

## Errores-Solución

* avrdude: error reading system wide configuration file "/usr/share/arduino/hardware/tools/avr/etc/avrdude.conf"

	```sh
	$ sudo mkdir /usr/share/arduino/hardware/tools/avr/etc
	$ sudo cp /etc/avrdude.conf /usr/share/arduino/hardware/tools/avr/etc/
	```
