# Amazon "BeauFlw WIFI Smart"
https://www.amazon.de/gp/product/B0886H6J1X/ref=ppx_yo_dt_b_asin_title_o02_s01?ie=UTF8&psc=1


## Based on WF-CS01 2nd configuration
https://templates.blakadder.com/WF-CS01_EU.html

## Actual config

`Template: {"NAME":"WF-CS01","GPIO":[544,291,289,34,226,161,0,0,160,224,290,225,288,0],"FLAG":0,"BASE":18}`

```
rule1 on Power1#State=0 do LEDPower1 0 endon on Power1#State=1 do LEDPower1 1 endon on Power2#State=0 do LEDPower2 0 endon on Power2#State=1 do LEDPower2 1 endon
rule1 1

rule2 on button3#state=2 do backlog timers 2; LEDPower3 2 endon
rule2 1
```

```
interlock 1 2 3 # lock the relays, only one relay can be on
SetOption1 1    # restrict button-multipress to single, double and hold actions
PulseTime1 145  # set relay 1 activation to 45 seconds (+100 for 1sec interval)ru
PulseTime2 145  # deactivate button 2 immediately after activation (disables relays)
Pulsetime3 1	# set relay 3 activation 45 seconds (+100 for 1sec interval)
PowerOnState 0  # keep relay(s) OFF after power up
PowerRetain 0   # Don't retain states
SwitchMode1 5   # pushbutton with hold
SwitchMode2 5   # toggle (default)
SwitchMode3 0   # pushbutton with hold
SetOption11 1   # Swap button single and double press functionality
```

```
ShutterOpenDuration: 22
ShutterCloseDuration: 21
```

+ GPIO0: LedLink => Top Green LED
+ GPIO1: Led4 => 3 blue background LEDs
+ GPIO2: Led2
+ GPIO3: Button3
+ GPIO4: Relay3
+ GPIO5: Switch2 => Close
+ GPIO9: -
+ GPIO10: -
+ GPIO12: Switch 1 => Open
+ GPIO13: Relay 1
+ GPIO14: Led 3
+ GPIO15: Relay 2 => Stop
+ GPIO16: Led 1
+ GPIO17: -

**Timers**
+ 1: Output2 Toggle 23:30 Everyday => Close
+ 2: Output1 Toggle 8:15 Mon-Fri => Open
+ 3: Output1 Toggle 10:45 Sat, Sun => Open


### Some configs