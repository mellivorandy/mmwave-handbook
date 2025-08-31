# gmake 編譯失敗

> 實際 MMWAVE_L_SDK 版本請依照自身版本做修改。

## 問題描述
繼上次 MMWAVE_L_SDK_05_05_03_00（從 MMWAVE_L_SDK_05_05_03_00/ 資料夾下打開 MMWAVE_L_SDK_05_05_03_00/README_FIRST_xWRL6432.html）內 **Developer Guides** 中的 **Using SDK with Makefiles** 範例教學，雖然已經可以成功 gmake clean，但 gmake all 時卻發生以下錯誤：

```bash
PS C:\ti\MMWAVE_L_SDK_05_05_03_00>gmake -s -C examples/hello_world/xwrL64xx-evm/m4fss0-0_freertos/ti-arm-clang all
Generating SysConfig files ...
Running script...
Validating...
Generating Code (example.syscfg)...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_dpl_config.c...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_dpl_config.h...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_drivers_config.c...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_drivers_config.h...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_drivers_open_close.c...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_drivers_open_close.h...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_pinmux_config.c...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_power_clock_config.c...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_board_config.c...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_board_config.h...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_board_open_close.c...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_board_open_close.h...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_cli_mpd_demo_config.h...
Writing C:\ti\MMWAVE_L_SDK_05_05_03_00\examples\hello_world\xwrL64xx-evm\m4fss0-0_freertos\ti-arm-clang\generated\ti_cli_mmwave_demo_config.h...
 Compiling: xwrL64xx:m4fss0-0:freertos:ti-arm-clang hello_world.release.out: ../../../hello_world.c
process_begin: CreateProcess(NULL, C:/ti/ccs2010/ccs/tools/compiler/ti-cgt-armllvm_3.2.2.LTS/bin/tiarmclang -c -mcpu=cortex-m4 -mfloat-abi=hard -mno-unaligned-access -mthumb -Wall -Werror -g -Wno-gnu-variable-sized-type-not-at-end -Wno-unused-function -Os -IC:/ti/ccs2010/ccs/tools/compiler/ti-cgt-armllvm_3.2.2.LTS/include/c -IC:/ti/MMWAVE_L_SDK_05_05_03_00/source -IC:/ti/MMWAVE_L_SDK_05_05_03_00/source/kernel/freertos/FreeRTOS-Kernel/include -IC:/ti/MMWAVE_L_SDK_05_05_03_00/source/kernel/freertos/portable/TI_ARM_CLANG/ARM_CM4F -IC:/ti/MMWAVE_L_SDK_05_05_03_00/source/kernel/freertos/config/xwrL64xx/m4f -Igenerated -DSOC_XWRL64XX -MMD -o obj/release//hello_world.obj ../../../hello_world.c, ...) failed.
make (e=2): The system cannot find the file specified.
makefile:138: recipe for target 'hello_world.obj' failed
gmake: *** [hello_world.obj] Error 2
```

<br>

這邊可以注意一下倒數第三行的錯誤訊息 `make (e=2): The system cannot find the file specified.`，也就是說，gmake 在編譯 hello_world.c 的時候，想去執行 tiarmclang 編譯器，但指定的路徑不存在或找不到檔案，因此報錯。而這大概有以下幾種原因，要嘛編譯器路徑錯誤，要不然就是版本不同。於是我去 ti/ccs2010/ccs/tools/compiler 路徑下找到 `ti-cgt-armllvm_4.0.2.LTS`，發現是版本不一致的問題，那這個就好解決了。一樣是修改 imports.mak 裡面對 **CGT_TI_ARM_CLANG_PATH** 的設定，讓它指向正確的編譯器路徑。

## 解決方法
跟上一篇雷同，打開 imports.mak，用 `Ctrl + F` 找到 CGT_TI_ARM_CLANG_PATH=$(CCS_PATH)/tools/compiler/ti-cgt-armllvm_3.2.2.LTS 和 CGT_TI_ARM_CLANG_PATH=$(TOOLS_PATH)/ti-cgt-armllvm_3.2.2.LTS，改成你想要用的版本。

<br>

舉例，我欲使用的版本為 `ti-cgt-armllvm_4.0.2.LTS` → 分別改成：

```bash
CGT_TI_ARM_CLANG_PATH=$(CCS_PATH)/tools/compiler/ti-cgt-armllvm_4.0.2.LTS
```

與

```bash
CGT_TI_ARM_CLANG_PATH=$(TOOLS_PATH)/ti-cgt-armllvm_4.0.2.LTS
```

改完後儲存，重新跑 gmake clean，再 gmake all 就可以正常運作了。

<br>
<br>

順帶一提，如果想使用特定版本，可以到 [TI - ARM-CGT-CLANG](https://www.ti.com/tool/download/ARM-CGT-CLANG) 下載。
