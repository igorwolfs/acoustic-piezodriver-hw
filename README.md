# Acoustic Piezodriver HW

This board generates the signal used to excite the piezo-module. Excitation frequencies are between 100 kHz and 10 MHz. All above 5 MHz will probably be hard to reach, given the component specs had to be balanced with price.

## 40V BOOST
Supplies the single-phase inverter with a 40 V voltage, given a 20 V input voltage.

## 6V SEPIC
Supplies around 6 V to the PCONN 5V connector. Meant to supply power to the acoustic-processing-hw board.

## 10 V SEPIC
Supplies the FET-drivers with a steady 10V.

## SIGCONN
Drives the PWM signals, enables the 40V BOOST and the 10V SEPIC, contains an SPI bus meant to control the on-board ADC and temperature sensors. Meant to be connected to the acoustic-processing-hw board.

