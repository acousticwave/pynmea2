# pynmea2-ship

`pynmea2-ship` is a python library for the [NMEA 0183](http://en.wikipedia.org/wiki/NMEA_0183) protocol specialized for ships⛴.

`pynmea2-ship` is based on [`pynmea2`](http://github.com/Knio/pynmea2) by Tom Flanagan.





## 🌠Features

### Autopilot related sentences

- Parsing/generation of **<u>HTC</u>**, **<u>HTD</u>**, and **<u>ROR</u>** sentences are available.



### Parsing data of VDR

- [pynmea2-ship](https://github.com/acousticwave/pynmea2-ship) is used for [parsing data of VDR](https://github.com/acousticwave/pyvdr) (Voyage Data Recorder), which converts **<u>log-format</u>** → **<u>csv-format</u>** (reference clock can be controlled [sec]) for further analysis.





## 💿Installation

The recommended way to install `pynmea2-ship` is with [pip](http://pypi.python.org/pypi/pip/)

```
$ cd dist
$ python3 -m pip install pynmea2-1.18.0.tar.gz
```





## Development guide

### 🗣Adding a new talker-sentence

- Open ```pynmea2/types/talker.py``` and add a new class. The following example shows adding ```class ROR(TalkerSentence)```.

  ```python
  class ROR(TalkerSentence):
      """ Rudder Order Status
      """
      fields = (
          ("Starboard (or single) rudder order", "ror_starboard", Decimal),
          ("Starboard (or single) rudder order status", "ror_starboard_status"),
          ("Port rudder order", "ror_port", Decimal),
          ("Port rudder order status", "ror_port_status"),
          ("Command source location (as TRC)", "ror_cmd_src_loc"),
      )
  ```



### 📦Building a Python package for pip

- After update your code, you can build your code into a Python package for [pip](http://pypi.python.org/pypi/pip/)
  - ```python3 setup.py sdist```
  - A folder ```dist``` is generated, and the folder contains a ```.tag.gz``` file.
- You can convert ```pynmea2-ship``` to the new version
  - ```python3 -m pip install [Name of the .tar.gz file]```



### 🧪Test examples

- $XXROR

  ```python
  >>> import pynmea2
  
  >>> line = "$AGROR,0.1,A,,V,B*1F"
  >>> msg = pynmea2.parse(line)
  >>> msg
  <ROR(ror_starboard=Decimal('0.1'), ror_starboard_status='A', ror_port=None, ror_port_status='V', ror_cmd_src_loc='B')>
  ```

  



## 👓Parsing

There is no difference between the usage of [pynmea2-ship](https://github.com/acousticwave/pynmea2-ship) and [pynmea2](http://github.com/Knio/pynmea2). Please follow the guide introduced in [pynmea2](http://github.com/Knio/pynmea2) page.





## 🏃🏻‍♂️TODO

- Test code for the added sentences.
- Update VDM parser

