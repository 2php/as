

By default, this project support the machine MPC5634M_MLQB80 only, but event for this a empty template project should be created by codewarrior v2.10 IDE as below filre structure.

```sh
MPC5634M_MLQB80
������ Project
    ������ Project.mcp
    ������ Project_Data
    ��   ������ CWSettingsWindows.stg
    ��   ������ RAM
    ��   ��   ������ ObjectCode
    ��   ��   ������ TargetDataWindows.tdt
    ��   ������ internal_FLASH
    ��       ������ TargetDataWindows.tdt
    ������ bin
    ��   ������ RAM.MAP
    ��   ������ RAM.elf
    ��   ������ RAM.mot
    ������ lcf
    ��   ������ MPC5634M_MLQB80.lcf
    ��   ������ MPC5634M_MLQB80_DEBUG.lcf
    ������ readme.txt
    ������ src
        ������ Exceptions.c
        ������ Exceptions.h
        ������ IntcInterrupts.c
        ������ IntcInterrupts.h
        ������ MPC55xx_init.c
        ������ MPC55xx_init_debug.c
        ������ MPC5634M_MLQB80.h
        ������ MPC5634M_MLQB80_HWInit.c
        ������ MPC5634M_MLQB80_HWInit.h
        ������ __ppc_eabi_init.c
        ������ main.c
        ������ typedefs.h
```

To support other kind of chips, please take the MPC5634M_MLQB80 as an example and modify the SConscript and Kconfig
