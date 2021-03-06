**Table of Contents**

* [11-7-2019](#11-7-2019)

* [11-11-2019](#11-11-2019)

# 11-7-2019

On 11-5 we were successfully able to get the devices outputting ranges into the debug setup in the lab. Today, I have returned to the lab to test the devices again to see if those results are reliably reproducible with the current version of the code.

## Test 1

### Parameters

* Nodes 26 and 29
* Code was **not** reflashed onto the devices
* J-Link debuggers were connected to node 26
* J-Link `S/N: 260...` to the nRF, `S/N 269...` to the STM
* Nodes were turned off and back on since the last day of testing (11-5-2019)

### Debug output

* [STM](11-9-2019/test1/t1_STM_output_26.txt)
* [nRF](11-9-2019/test1/t1_nRF_output_26.txt)

### Observations

The ranges were correctly recorded with reasonable values. **Successful short test**

---

## Test 2

### Parameters

* Nodes 26 and 29
* Code was **not** reflashed onto the devices
* J-Link debuggers were connected to node 29
* J-Link `S/N: 260...` to the nRF, `S/N 269...` to the STM
* Nodes were turned off and back on since the previous test

### Debug output

* [STM](11-9-2019/test2/t2_STM_output_29.txt)
* [nRF](11-9-2019/test2/t2_nRF_output_29.txt)

### Observations

The ranges were correctly recorded with reasonable values. **Successful short test**

---

## Test 3

On successful test of the new code on two nodes, we have decided to try two completely different nodes that have been freshly flashed.

### Parameters

* Nodes 27 and 2A
* Code **was** reflashed onto the devices. Used J-Link `S/N: 269...`
* J-Link debuggers were connected to node 2A
* J-Link `S/N: 260...` to the nRF, `S/N 269...` to the STM
* *Note: I instinctively did two runs on this one because the first one failed with disconnection issues.*

### Debug output

#### First run

* [STM](11-9-2019/test3/first_run/t3r1_STM_output_2A.txt)
* [nRF](11-9-2019/test3/first_run/t3r1_nRF_output_2A.txt)

#### Second run

* [STM](11-9-2019/test3/second_run/t3r2_STM_output_2A.txt)
* [nRF](11-9-2019/test3/second_run/t3r2_nRF_output_2A.txt)

### Observations

#### First run

This one seemed to connect, fail, disconnect, reconnect, repeat. **Failed short test**

#### Second run

This one seemed to connect but constantly range unreasonably large values. **Failed short test**

---

## Test 4

### Parameters

* Nodes 27 and 2A
* Code was **not** reflashed onto the devices since test 3.
* J-Link debuggers were connected to node 27
* J-Link `S/N: 260...` to the nRF, `S/N 269...` to the STM

### Debug output

* [STM](11-9-2019/test4/t4_STM_output_27.txt)
* [nRF](11-9-2019/test4/t4_nRF_output_27.txt)

### Observation

Similar results to test 3 run 2. **Failed short test**

---

## Quick Takeaways from Tests 5-8

Node 27 worked with the known operational nodes. Node 2A did not.

### Test 5

* [STM](11-9-2019/test5/t5_STM_output_2A.txt)
* [nRF](11-9-2019/test5/t5_nRF_output_2A.txt)

### Test 6

* [STM](11-9-2019/test6/t6_STM_output_2A.txt)
* [nRF](11-9-2019/test6/t6_nRF_output_2A.txt)

### Test 7

* [STM](11-9-2019/test7/t7_STM_output_27.txt)
* [nRF](11-9-2019/test7/t7_nRF_output_27.txt)

### Test 8

* [STM](11-9-2019/test8/t8_STM_output_27.txt)
* [nRF](11-9-2019/test8/t8_nRF_output_27.txt)

---

# 11-11-2019

## Test 9

Our tentative goal for this test is to reflash 2A and see if we can get it working.

### Parameters

* Nodes 2A and 26
* Code **was** reflashed onto *only* 2A
* J-Link debuggers were connected to node 2A
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM
* Nodes were turned off and back on since last use

### Debug output

* [STM](11-11-2019/t9_STM_output_2A.txt)
* [nRF](11-11-2019/t9_nRF_output_2A.txt)

### Observations

nRF gives error TOO_FEW_RANGES and STM disregards all given ranges. **Failed short test.**

---

## Test 10

2A failing behind us. We are now testing results with a little bit of noise, i.e. bring them in and out of range, walking around, etc.

### Parameters

* Nodes 26 and 29
* Code was **not** reflashed onto either device
* J-Link debuggers were connected to node 29
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM
* Node 29 was turned off and on again since last use

### Debug output

* [STM](11-11-2019/t10_STM_output_29.txt)
* [nRF](11-11-2019/t10_nRF_output_29.txt)

### Observations

The nodes were successfully able to get in and out of range and connect and reconnect to each other and continue ranging. They had a range of about 2/3rds of the length of the lab workspace. **Successful short test.**

---

## Test 11

### Parameters

* Nodes 26 and 29
* Code was **not** reflashed onto either device
* J-Link debuggers were connected to node 29
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM
* Nodes were turned off and on again since the last test
* Node 26 was left in another room for 5 minutes out of range and then reintroduced within range of the connected node

### Debug output

* [STM](11-11-2019/t11_STM_output_29.txt)
* [nRF](11-11-2019/t11_nRF_output_29.txt)

### Observations

After reconnecting the nodes ranges were not logged. We got expected `interrupted with reason 1` but no ranges as expected after that. **Failed short test.**

---

# 11-13-2019

## Test 12

### Parameters

* Nodes 26 and 27
* Code was **not** reflashed onto either device
* J-Link debuggers were connected to node 26
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM
* Nodes were turned off and on again since the last test

### Debug output

* [STM](11-13-2019/t12_STM_output_26.txt)
* [nRF](11-13-2019/t12_nRF_output_26.txt)

### Oberservations

Working as intended!

---

## Test 13

### Parameters

* Nodes 26 and 2A
* Code was **not** reflashed onto either device
* J-Link debuggers were connected to node 26
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM
* Nodes were turned off and on again since the last test

### Debug output

* [STM](11-13-2019/t13_STM_output_26.txt)
* [nRF](11-13-2019/t13_nRF_output_26.txt)

### Oberservations

2A still disappoints

---

## Test 14

### Parameters

* Nodes 27 and 2A
* Code was **not** reflashed onto either device
* J-Link debuggers were connected to node 27
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM
* Nodes were turned off and on again since the last test

### Debug output

* [STM](11-13-2019/t14_STM_output_27.txt)
* [nRF](11-13-2019/t14_nRF_output_27.txt)

### Oberservations

2A still disappoints. No change from tests with 26 and 2A

---

## Test 15

### Parameters

* Nodes 27 and 26
* Code was **not** reflashed onto either device
* J-Link debuggers were connected to node 27
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM
* Nodes were turned off and on again since the last test

### Debug output

* [STM](11-13-2019/t15_STM_output_27.txt)
* [nRF](11-13-2019/t15_nRF_output_27.txt)

### Oberservations

Working correctly

---

# 11-18-2019

## Test 16

### Parameters
* Nodes 27 and 26
* Code **was** reflashed onto both devices
* J-Link debuggers were connected to node 26
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM
* Nodes were turned off and on again since the last test

### Debug output

* [STM](11-18-2019/t16_STM_output_26.txt)
* [nRF](11-18-2019/t16_nRF_output_26.txt)

### Observations
On startup, nodes were not ranging. Turned node 27 off and back on and nodes began ranging. Left range for a second and came back in and they reconnected and started ranging. Left range for 30 seconds and came back in and the nodes attempted to reconnect but failed. Complete failure as the white light started blinking on one of the nodes and they shut down. **Confusing failed short test.**

## Test 17

### Parameters
* Nodes 27 and 26
* Code was **not** reflashed onto both devices
* J-Link debuggers were connected to node 27
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM
* Nodes were turned off and on again since the last test

### Debug output

* [STM](11-18-2019/t17_STM_output_27.txt)
* [nRF](11-18-2019/t17_nRF_output_27.txt)

### Observations
On startup, nodes were ranging. Left range for a second and came back in and they reconnected and started ranging. Left range for 2 and a half minutes and came back in and the nodes resumed ranging. Left range for 5 minutes and it continued ranging when we came back in. **Confusing successful short test.**

Also it keeps finding a node 39 and attempting to range with it but as far as I know node 39 does not exist.

---

# 11-22-2019

## Test 18

### Parameters:
* Code modifications
   * Added `debug_msg` that brings `_lwb_counter` at [this line](https://github.com/lab11/totternary/blob/b938123bec8264927984740f7b435ab0b9ebdbd8/software/module/firmware/glossy.c#L1474)
   * Permanently enabled [this option](https://github.com/lab11/totternary/blob/b938123bec8264927984740f7b435ab0b9ebdbd8/software/module/firmware/glossy.c#L345)
   * Increased the timeout time to 50 [here](https://github.com/lab11/totternary/blob/b938123bec8264927984740f7b435ab0b9ebdbd8/software/module/firmware/module_conf.h#L72)
   * Disabled master takeover [here](https://github.com/lab11/totternary/blob/b938123bec8264927984740f7b435ab0b9ebdbd8/software/module/firmware/module_conf.h#L76)
* Both nodes were reflashed on both the STM and nRF
* Both nodes were turned off and back on again after flashing
* Nodes 27 and 26
* J-Link debuggers were connected to node 26
* J-Link `S/N: 260...` to the nRF, `S/N: 269...` to the STM

### Debug output

* [STM](11-22-2019/t18_STM_output_26.txt)
* [nRF](11-22-2019/t18_nRF_output_26.txt)

### Observations
On startup, nodes were ranging. Left range for about 2 minutes and came back in and they reconnected and started ranging. **Successful short test.**
