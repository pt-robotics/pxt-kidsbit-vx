# PTKidsBIT block package for PT-BOT KidsBIT kit

powered by micro:bit

![PTKidsBIT](https://raw.githubusercontent.com/pt-robotics/pxt-kidsbit-vx/master/big_icon.png)

The package adds support [PTKidsBIT](https://ptbot.medium.com/pt-bot-kidsbit-aa923a5caeaa) board from [PT-BOT](https://web.facebook.com/LPRobotics).

## micro:bit Pin Assignment

* ``P0``  -- Connected to Buzzer
* ``P1``  -- Digital Input/Output and Analog Input/Output
* ``P2``  -- Digital Input/Output and Analog Input/Output
* ``P13`` -- DigitalWrite Pin for DC motor control direction 1
* ``P14`` -- AnalogWrite Pin for DC motor speed control 1
* ``P15`` -- DigitalWrite Pin for DC motor control direction 2
* ``P16`` -- AnalogWrite Pin for DC motor speed control 2
* ``P19`` -- SCL connected to I2C-based 12-bit ADC chip (ADS7828)
* ``P20`` -- SDA connected to I2C-based 12-bit ADC chip (ADS7828)

## Blocks preview

### motorWrite Block

Use PTKidsBIT's MotorWrite block to drives 1 motor forward and backward. The speed motor is adjustable between 0 to 100.

* The motor must be select either `1` or `2`
* Speed is an integer value between `-100` to `100` (Greater than 0 is forward, less than 0 is backward)

```blocks
PTKidsBIT.motorWrite(Motor_Write.Motor_1, 50)
```

### motorGo Block

Use PTKidsBIT's motorGo block to drives 2 motor forward and backward. The speed motor is adjustable between 0 to 100.

* The motor1 must be select `-100` to `100` (Greater than 0 is forward, less than 0 is backward)
* The motor2 must be select `-100` to `100` (Greater than 0 is forward, less than 0 is backward)

```blocks
PTKidsBIT.motorGo(50, -50)
```

### Turn Block

Use PTKidsBIT's Turn block to control the robot movment by turning. The one motor will stop, another one is moving.

* The Turn must be select either `Left` or `Right`
* Speed is an integer value between `0` to `100`

```blocks
PTKidsBIT.Turn(_Turn.Left, 50)
```

### Spin Block

Use PTKidsBIT's Spin block to control both motors separately. For example, choose one motor spin with forward direction another one spin with backward direction.

* The Spin must be select either `Left` or `Right`
* Speed is an integer value between `0` to `100`

```blocks
PTKidsBIT.Spin(_Spin.Left, 50)
```

### Motor Stop Block 

Use PTKidsBIT's Motor Stop block is used to stop both motors.

```blocks
PTKidsBIT.motorStop()
```

### servoWrite Block

Use PTKidsBIT's servoWrite block for control the servo's moving degree from 0 to 180

* The Servo must be select either `P8` or `P12`
* Degree is an integer value between `0 - 180`
* Mode must be select either `Released` or `Lock`

```blocks
PTKidsBIT.servoWrite(Servo_Write.P8, 180)
```

### WaitClick Block

Use PTKidsBIT's WaitClick block for Wait for the command from the button.

* Select `Pin` for connecting to the button.
* Select `Pressed` or `Released`.

```blocks
PTKidsBIT.waitClick(Button_Pin.P1, Button_Status.Pressed)
```

### ADCRead Block

Use PTKidsBIT's ADCRead block for read analog from ADC channels. The resolution is 0 to 4095. PTKidsBIT have 8 channel ADC.

* Select `Pin` from `0` to `7` for reading the analog sensor.

```blocks
basic.forever(function () {
    basic.showNumber(PTKidsBIT.ADCRead(ADC_Read.ADC0))
})
```

### SensorCalibrate Block

Use PTKidsBIT's SensorCalibrate block for calibration line follower sensor, left sensor and right sensor.

* Select ADC channels between `0` to `7` for calibrate sensor.

The calibration process is as follows
* Place the line follower sensor on the line, press Button A once and wait until the buzzer sounds.
* Place left and right sensor on the line, press Button A once and wait until the buzzer sounds.
* Place all sensor on the floor, press Button A once and wait until the buzzer sounds.

```blocks
PTKidsBIT.SensorCalibrate([1, 0, 7, 6])
```

### LINESensorSET Block

Use PTKidsBIT's LINESensorSET block for select the ADC channel connected to the sensor.

* LINESensorSET is ADC channels between `0` to `7` for line follower sensor.
* Sensor Left is ADC channels between `0` to `7` for sensor left.
* Sensor Right is ADC channels between `0` to `7` for sensor right.
* The ON OFF Sensor, `Pin` or `Disable` must be selected for the sensor on or off.

```blocks
PTKidsBIT.LINESensorSET(
    [1, 0, 7, 6],
    [2],
    [5],
    LED_Pin.Disable
)
```

### ForwardLINE Block

Use PTKidsBIT's ForwardLINE blog for the robot to follow the line forward. When the specified line is found, the robot will stop. 

* Direction is The direction in which the robot moves. Select `Forward` or `Backward`.
* Find is the line to detect. Select `Left`, `Center` or `Right`
* Min Speed is minimum speed between `0` to `100`
* Max Speed is maximum speed between `0` to `100`
* Break Time is the time for the Motor to reverse to brake when the Robot stops.
* KP value for control the robot
* KD value for control the robot

```blocks
PTKidsBIT.ForwardLINE(
    Forward_Direction.Forward,
    Find_Line.Left,
    30,
    60,
    0,
    0.05,
    0.1
)
```

### ForwardTIME Block

Use PTKidsBIT's ForwardTIME blog for the robot to follow the line forward. When the time, the robot will stop. 

* Direction is The direction in which the robot moves. Select `Forward` or `Backward`.
* Time is set time.
* Min Speed is minimum speed between `0` to `100`
* Max Speed is maximum speed between `0` to `100`
* KP value for control the robot
* KD value for control the robot

```blocks
PTKidsBIT.ForwardTIME(
    Forward_Direction.Forward,
    200,
    60,
    100,
    0.03,
    0.1
)
```

### TurnLINE Block

Use PTKidsBIT's TurnLINE block for the Robot to turn until it detects a line.

* TurnLINE is direction to turn the robot. Select `Left` or `Right`
* Speed is maximun speed between `0` to `100`
* Sensor is the sensor you want the robot to stop.
* Fast Time is the time at the maximum robot speed before a line is detected.
* Break Time is the time for the Motor to reverse to brake when the Robot stops.

```blocks
PTKidsBIT.TurnLINE(
    Turn_Line.Left,
    60,
    2,
    200,
    0
)
```

## Supported targets

* for PXT/microbit

## License

MIT

```package
PTKidsBIT=github:iBuilds/pxt-ptkidsbit
```
