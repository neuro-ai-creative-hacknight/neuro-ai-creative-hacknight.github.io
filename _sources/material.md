# Material

## Hardware

Sensors : 
 * Several mobile EEG headsets (Muse, Neurosity, Wearable Sensing)
 * 2 PPG sensors
 * A bunch of plant sensors
 * ECG/EMG sensors
 * 1 leap motion

Emittors :
 * 2 Video projectors
 * 1 Sonos mobile speaker
 * 2 Krk5 speakers
 * 1 Scarlett 2i2 soundcard
 * 1 Clarett 4-pre soundcard

Calculators :
 * 2 Arduino
 * 1 HP Mini PC

Controllors :
 * 2 MIDI Keyboards
 * A set of MIDI controller




## Software
 * [goofi-pipe](https://github.com/PhilippThoelke/goofi-pipe) : A neuro-/biofeedback toolbox written in Python.
 * [Modular EEG Mapping Echosystem (MEME)](https://github.com/AntoineBellemare/eeg_m4l) : A Max4Live set of tools to receive OSC from biological signals in Ableton. Get an overview [here](https://www.youtube.com/watch?v=dn5BoCZzo7U).
 * [biotuner](https://github.com/antoineBellemare/biotuner) : A Python package to compute music theory based metrics on biological signals. Documentation is hosted [here](https://sangfrois.github.io/biotuner).



## Connect to a data-stream
We are streaming data from several devices in the local WiFi via OSC. Check out the list of OSC ports to find the specific device you want to connect to.

### Receiving OSC in Python
This little script connects to the OSC broadcast and simply prints out all incoming messages for a specific port.
```python
"""A simple OSC client that prints messages received from an OSC server."""
import argparse
from pythonosc import dispatcher
from pythonosc import osc_server

parser = argparse.ArgumentParser()
parser.add_argument("--ip", default="127.0.0.1")
parser.add_argument("--port", type=int, default=5005)


def handler(address, *args):
    print(f"{address}: {args}")


if __name__ == "__main__":
    args = parser.parse_args()
    address = args.ip
    port = args.port
    dispatcher = dispatcher.Dispatcher()
    dispatcher.map("/*", handler)
    server = osc_server.ThreadingOSCUDPServer((address, port), dispatcher)
    print(f"Serving on {server.server_address}")
    server.serve_forever()
```
