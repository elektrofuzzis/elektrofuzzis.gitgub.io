---
title: FtSwarmFrequency
layout: category
lang: en
classes: wide
sidebar:
    nav: cppapi-en
---
<div class="apicontainer">
    <div class="apileft">
        All inputs can be used as frequency meters. Frequencies between 0 and 1 kHz can be measured.  
    </div>
    <div class="apiright apiimg"><img title="Bildnachweis: fischertechnik" src="/assets/img/switches/frequency-api.png">Frequency</div>
</div>

Reed contacts, phototransistors and the encoder motors are suitable as sensors. In conjunction with a CNY 37 light barrier the rare 32367 roller wheel can be used, too.

The fischertechnik pushbuttons are unsuitable as sensors for the frequencymeter class as they are bouncing.
{: .notice--info}

If the input signal for the frequency measurement is significantly higher than 1kHz, the signal places such a heavy load on the CPU of the ftSwarm controller that the controller reacts slowly or incorrectly.

#### FtSwarmFrequencymeter(FtSwarmSerialNumber_t serialNumber, FtSwarmPort_t port)

Constructor to create a FtSwarmFrequencymeter object. If the referenced controller isn't connected to the swarm yet, the firmware will waits until the controller gets online.

- serialNumber: Serial number of the used ftSwarm controller.
- port: Port number, **FTSWARM_A1**, **FTSWARM_A2**, ..., **FTSWARM_A6**.

#### FtSwarmFrequencymeter(const char *name)

Constructor to create a FtSwarmFrequencymeter object. If the referenced controller isn't connected to the swarm yet, the firmware will waits until the controller gets online.

- name: Alias name of the IO port.

#### int16_t getFrequency()

Returns the frequency in Hz.


