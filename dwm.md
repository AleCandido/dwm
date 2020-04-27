# dwm
My notes on `dwm` source code and shadowbar introduction.

## shadowbar pattern
where shadowbar is needed:
- bar -> shadowbar
- b -> shb

## dwm.c
todo:
- configurenotify
- drawshadowbar: almost nothing, leave window empty (show background, but polybar will
    be automatically shown because on top of it)
- manage: find the proper c->y in presence of shadowbar
- monocle: can go on top of shadowbar or not, to be decided (so for the time
    being lets keep it as it is)

shadowbar related variables:
- shbh
- mon->shby
- mon->shadowbarwin
- shadowbar*

### types

- Arg: a generic argument (int - uint - float - void *)
- Button: mouse button event
- Client: a single window
- Key: keyboard press event
- Layout:
- Monitor: the full monitor object
  - by: bar height -> shby
  - sel: selected client
  - showbar: flag for showing bar -> showshadowbar
  - topbar: flag for bar positioning -> topshadowbar
  - barwin: bar window -> shadowbarwin
- Rule: a windows' rule (defined in `config.def.h`)
- *enums*: cursor, color schemes, ewmh atoms, default atoms, clicks


### global instances

- mons: Monitor *
- selmon: Monitor *
  - selected monitor
- drw: Drw *
- root: Window
- wmcheckwin: Window

#### and variables

- bh: int, bar height -> shbh

### functions

- setup:
  - set bh var to font height -> shbh (custom, set in config.def.h) 
- togglebar: toggle bar visibility
  - -> toggleshadowbar
- updatebarpos:
  - -> updateshadowbarpos

## config.def.h
- -> shadowbarheight: set desired height
- showbar: bar visibility -> showshadowbar
- topbar: bar position -> topshadowbar
