# Template for Jacdac module firmware

This repository is a template to create a new module firmware for [Jacdac](https://aka.ms/jacdac).

**The full build instructions are available at https://github.com/jacdac/jacdac-stm32x0/blob/main/README.md.**
This is also where you learn more about this repo. 

To pull the submodule sources, run

```
git submodule update --init --recursive && git pull
```

## TODOs

Follow these steps to update the file structure to reflect your module.

- [ ] update `jacdac-stm32` and `jacdac-c` submodules (eg., with `make update-submodules`)
- [ ] copy `targets/_example/` to `targets/buzzer-v1.0/` (replacing `buzzer-v1.0` with the name of the module or series of modules)
- [ ] edit `targets/buzzer-v1.0/board.h` to match your module
- [ ] you likely do not need to edit `targets/buzzer-v1.0/config.mk`, unless using F0 chip
- [ ] edit `targets/buzzer-v1.0/profile/module.c` 
  to include your module name and used services (follow comments in `module.c`);
  see [jd_services.h](https://github.com/jacdac/jacdac-c/blob/master/services/jd_services.h)
  for list of services
- [ ] rename `module.c` to match the type of module (eg. `buzzer.c`)
- [ ] if you have several modules with non-conflicting `board.h` definitions,
  you can create more files under `targets/buzzer-v1.0/profile/`;
  otherwise you'll need to create `targets/thermocouple-v1.0` or something similar
- [ ] edit `Makefile.user` to set `TRG`, eg. `TRG = targets/buzzer-v1.0/profile/buzzer.c`
- [ ] run `make`; this will generate a new unique identifier and place as an argument of `FIRMWARE_IDENTIFIER` macro

> make sure to never change the firmware identifier number, as that will break future firmware updates

_Erase this section once you are done with the setup_

## Contributing

This project welcomes contributions and suggestions.
