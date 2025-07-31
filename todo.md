# Schematics
## DC-DC Converters
- Add 1 x LM3478 (doesn't require level-shifting circuitry)
	- Boost converter: to bring a voltage of between 15-20 volts up to 40 V ()
- Add 1 x SEPIC converter for the level-shifting FET drivers
- Add 1 x SEPIC-converter for the 5 V power supply

### Goal
- We want to be able to adapt the driving voltage dynamically
	- The boost converter will need to drive the voltage to up to 40 volts
		- It however might have 9-10 volts connected
		- There should be a bypass from the boost converter VBAT directly to the inverted driving circuit as well
			- This way we can drive the piezo with voltages as low as 5 Vpp
	- The level shifter will need to continuously be at 10 volts.
		- It however might have 9-10 V connected
- We want to avoid working with variable resistors

#### Boost converter (5-20 V -> 5-40 V)
- Input: between 5 and 20 volts
	- If < 10 volts: make sure you have bypass circuitry that allows you to directly drive the inverter from your source
	- If > 10 volts: make sure you have some-kind of soldering bridge or short that you can eliminate to force all current through the boost converter.
		- Add a spot for a feedback resistor slope compensation (in case D > 0.5)
- Output: between 5 V and 40 V
- Currents: max 10 amps RMS at 40 V



**Bypass** 
- Create a bypass for the boost converter (e.g.: simply 0-ohm high power resistor, or solderbridge) whenever you want to use pure battery voltage
- When you want to use a voltage unreachable by your power supply (e.g.: 40 V)
	- Make sure to use a boost converter, and set the input voltage between 10-20 Volts (to limit the stress on the passives)

## ADC Measurement
- Add a 4-channel ADC 
	- (2 inputs) Differential channel to measure current going to the piezo
	- 1 input: Current going to the ADC
	- 1 input: Total voltage (use a resistive divider)
		- Based on this one can activate SEPICs
	- 1 input: Total current draw (use a resistor)
- Add front-end (RC-filter at cutoff below 1 kHz for noise purpoes)
- Add hall-sensor for in-circuit current measurement
- Add a voltage divider so 
	- Vbat: (0, 25) -> (0->2.048)

## Temperature Sensors
- 2 different addresses
- Communication over I2C

## I2C bus checks
- Check if total capacitance on the I2C bus isn't too large
- I2C ADC-bus
- 2xI2C temperature sensors

## Connectors
- Add pads for each power supply so you can supply it externally for testing if necessary
	- For 6V no pad is required since there is already a hal-sensor that takes in the current.