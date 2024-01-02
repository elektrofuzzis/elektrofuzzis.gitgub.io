---
title: FtSwarmCounter
layout: category
lang: en
classes: wide
sidebar:
    nav: cppapi-en
---
<div class="apicontainer">
    <div class="apileft">
        All inputs can be used as counters. Reed contacts, phototransistors and the encoder motors are suitable as sensors. In conjunction with a CNY 37 light barrier the rare 32367 roller wheel can be used, too.
    </div>
    <div class="apiright apiimg"><img title="Bildnachweis: fischertechnik" src="/assets/img/switches/counter-api.png">Counter</div>
</div>


The fischertechnik pushbuttons are unsuitable as sensors for the counter class as they are bouncing.
{: .notice--info}


#### FtSwarmCounter(FtSwarmSerialNumber_t serialNumber, FtSwarmPort_t port)

Constructor to create a FtSwarmCounter object. If the referenced controller isn't connected to the swarm yet, the firmware will waits until the controller gets online.

- serialNumber: Serial number of the used ftSwarm controller.
- port: Port number, **FTSWARM_A1**, **FTSWARM_A2**, ..., **FTSWARM_A6**.

#### FtSwarmCounter(const char *name)

Constructor to create a FtSwarmCounter object. If the referenced controller isn't connected to the swarm yet, the firmware will waits until the controller gets online.

- name: Alias name of the IO port.

#### int16_t getCounter()

Returns the number of pulses counted.

#### void resetCounter()

Resets the counter to zero.

