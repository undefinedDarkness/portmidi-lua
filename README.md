## Building
>[!NOTE]
>Replace `$(pkg-config --libs --cflags lua-5.1)` with whatever lua you are using, consult `pkg-config --list-all | grep -i lua` for all available versions

```sh
swig -lua -I/usr/include -outcurrentdir portmidi.i
cc portmidi_wrap.c -o portmidi.so $(pkg-config --libs --cflags lua-5.1) -lportmidi -shared -fPIC
```

Expected output from importing module:
```lua
> print(require('inspect')(require('portmidi')))
{
  FALSE = 0,
  HDRLENGTH = 50,
  PM_DEFAULT_SYSEX_BUFFER_SIZE = 1024,
  PM_FILT_ACTIVE = 16384,
  PM_FILT_AFTERTOUCH = 603979776,
  PM_FILT_CHANNEL_AFTERTOUCH = 536870912,
  PM_FILT_CLOCK = 256,
  PM_FILT_CONTROL = 134217728,
  PM_FILT_FD = 8192,
  PM_FILT_MTC = 2,
  PM_FILT_NOTE = 50331648,
  PM_FILT_PITCHBEND = 1073741824,
  PM_FILT_PLAY = 7168,
  PM_FILT_POLY_AFTERTOUCH = 67108864,
  PM_FILT_PROGRAM = 268435456,
  PM_FILT_REALTIME = 65281,
  PM_FILT_RESET = 32768,
  PM_FILT_SONG_POSITION = 4,
  PM_FILT_SONG_SELECT = 8,
  PM_FILT_SYSEX = 1,
  PM_FILT_SYSTEMCOMMON = 78,
  PM_FILT_TICK = 512,
  PM_FILT_TUNE = 64,
  PM_FILT_UNDEFINED = 8192,
  PM_HOST_ERROR_MSG_LEN = 256,
  PmDeviceInfo = {
    <metatable> = <1>{
      [".fn"] = {},
      [".get"] = {},
      [".instance"] = {
        [".bases"] = {},
        [".fn"] = {
          __disown = <function 1>
        },
        [".get"] = {
          input = <function 2>,
          interf = <function 3>,
          name = <function 4>,
          opened = <function 5>,
          output = <function 6>,
          structVersion = <function 7>
        },
        [".set"] = {
          input = <function 8>,
          interf = <function 9>,
          name = <function 10>,
          opened = <function 11>,
          output = <function 12>,
          structVersion = <function 13>
        },
        [".static"] = <table 1>,
        [".type"] = "PmDeviceInfo",
        __eq = <function 14>,
        __gc = <function 15>,
        __index = <function 16>,
        __newindex = <function 17>,
        __tostring = <function 18>
      },
      [".set"] = {},
      __call = <function 19>,
      __index = <function 20>,
      __newindex = <function 21>
    }
  },
  PmEvent = {
    <metatable> = <2>{
      [".fn"] = {},
      [".get"] = {},
      [".instance"] = {
        [".bases"] = {},
        [".fn"] = {
          __disown = <function 22>
        },
        [".get"] = {
          message = <function 23>,
          timestamp = <function 24>
        },
        [".set"] = {
          message = <function 25>,
          timestamp = <function 26>
        },
        [".static"] = <table 2>,
        [".type"] = "PmEvent",
        __eq = <function 27>,
        __gc = <function 28>,
        __index = <function 29>,
        __newindex = <function 30>,
        __tostring = <function 31>
      },
      [".set"] = {},
      __call = <function 32>,
      __index = <function 33>,
      __newindex = <function 34>
    }
  },
  Pm_Abort = <function 35>,
  Pm_Close = <function 36>,
  Pm_CountDevices = <function 37>,
  Pm_GetDefaultInputDeviceID = <function 38>,
  Pm_GetDefaultOutputDeviceID = <function 39>,
  Pm_GetDeviceInfo = <function 40>,
  Pm_GetErrorText = <function 41>,
  Pm_GetHostErrorText = <function 42>,
  Pm_HasHostError = <function 43>,
  Pm_Initialize = <function 44>,
  Pm_OpenInput = <function 45>,
  Pm_OpenOutput = <function 46>,
  Pm_Poll = <function 47>,
  Pm_Read = <function 48>,
  Pm_SetChannelMask = <function 49>,
  Pm_SetFilter = <function 50>,
  Pm_Synchronize = <function 51>,
  Pm_Terminate = <function 52>,
  Pm_Write = <function 53>,
  Pm_WriteShort = <function 54>,
  Pm_WriteSysEx = <function 55>,
  TRUE = 1,
  pmBadData = -9994,
  pmBadPtr = -9995,
  pmBufferMaxSize = -9992,
  pmBufferOverflow = -9996,
  pmBufferTooSmall = -9997,
  pmGotData = 1,
  pmHostError = -10000,
  pmInsufficientMemory = -9998,
  pmInternalError = -9993,
  pmInvalidDeviceId = -9999,
  pmNoData = 0,
  pmNoDevice = -1,
  pmNoError = 0,
  <metatable> = {
    [".fn"] = {},
    [".get"] = {},
    [".set"] = {},
    __index = <function 56>,
    __newindex = <function 57>
  }
}
```
