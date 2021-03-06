# Λioi

A companion app for [ORCΛ](https://wiki.xxiivv.com/#orca) using its [UDP operator](https://github.com/hundredrabbits/Orca#udp) to send complex OSC message to multiple hosts.

![Λioi](aioi.gif)

### Goals

Λioi is an [ElectronJS](https://electronjs.org) application that intends to let you access the extra complexity you may need for ORCΛ to drive your applications. Λioi provides support for OSC messages with multiple parameters, types and to multiple hosts. Λioi helps you configure OSC hosts dynamically with a simple GUI and test your OSC messages.

### Install & Run

You can download [builds](https://github.com/MAKIO135/aioi/releases) for **OSX, Windows and Linux**, or if you wish to run it from sources, follow these steps:
```
git clone https://github.com/MAKIO135/aioi.git
cd aioi/desktop
npm install
npm run start
```
You can also build it for your system using `npm run build_osx`, `npm run build_linux` or `npm run build_win`.

### Usage from ORCΛ

- specify **path**:  
    `;foo` in ORCΛ sends `/foo` to the first host in Λioi  
    `;bar` in ORCΛ sends `/bar` to the first host in Λioi  
    `;21` in ORCΛ sends `/21` to the first host in Λioi

- send **integers**:  
    `;foo;5` in ORCΛ sends `/foo 5` to the first host in Λioi  
    `;foo;127` in ORCΛ sends `/foo 127` to the first host in Λioi

- send **base 36 integers** (single char are converted to base 36 integers):  
    `;foo;8` in ORCΛ sends `/foo 8` to the first host in Λioi
    `;foo;c` in ORCΛ sends `/foo 12` to the first host in Λioi

- send **floats** (integers followed by `f` are divided by 10 and sent as floats):  
    `;foo;3f` in ORCΛ sends `/foo 0.3` to the first host in Λioi  
    `;foo;235f` in ORCΛ sends `/foo 23.5` to the first host in Λioi

- send **strings**:  
    `;foo;yes` in ORCΛ sends `/foo "yes"` to the first host in Λioi  
    `;foo;h3ll0` in ORCΛ sends `/foo "h3ll0"` to the first host in Λioi

- send **multiple parameters** (split parameters using `;`):  
    `;foo;yo;5` in ORCΛ sends `/foo "yo" 5` to the first host in Λioi
    `;foo;2f;c;135` in ORCΛ sends `/foo 0.2 12 135` to the first host in Λioi

- **host selection** (Λioi sends the message to the first host by default, but we can start UDP message with `base 36 indexes` followed by `#`):  
    `;2#foo` in ORCΛ sends `/foo` to the third host in Λioi  
    `;a#foo;2f` in ORCΛ sends `/foo 0.2` to the tenth host in Λioi

- send to **multiple hosts** at once:  
    `;2a#foo` in ORCΛ sends `/foo` to the third and tenth hosts in Λioi

- **host /path shortcuts**: (supports **complex paths**)  
    `;#1;2f` in ORCΛ sends `0.2` to the second host in Λioi with its path defined in Λioi  
    `;#a;yo;135` in ORCΛ sends `yo 135` to the tenth host in Λioi with its path defined in Λioi

#### Λioi does not support:

- negative values
- arrays

### Examples

Open [aioi_test.orca](https://github.com/MAKIO135/aioi/blob/master/aioi_test.orca) with ORCΛ and start [listener.js](https://github.com/MAKIO135/aioi/blob/master/listener.js) with NodeJS:

```
cd aioi
node listener.js
```

Tutorials for different platforms:
- [ORCΛ x Λioi x Processing](examples/processing/processing.md)
- [ORCΛ x Λioi x SuperCollider](examples/supercollider/supercollider.md)
- [ORCΛ x Λioi x TidalCycles](examples/tidalcycles/tidalcycles.md)
- [ORCΛ x Λioi x Veda](examples/veda/veda.md)

### Extra

This application supports the [Ecosystem Theme](https://github.com/hundredrabbits/Themes).  
PR are welcomed.  

**Extra thanks to [Devine Lu Linvega](https://wiki.xxiivv.com/#devine+lu+linvega) for all their works.**
