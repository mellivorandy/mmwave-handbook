# gmake 找不到檔案錯誤

> 實際 MMWAVE_L_SDK 版本請依照自身版本做修改。

## 問題描述
在一開始跑 MMWAVE_L_SDK_05_05_03_00（從 MMWAVE_L_SDK_05_05_03_00/ 資料夾下打開 MMWAVE_L_SDK_05_05_03_00/README_FIRST_xWRL6432.html）內 **Developer Guides** 中的 **Using SDK with Makefiles** 範例教學時，因為 `ccs` 版本不同，所以在 `gmake` 的時候，會出現以下錯誤：

```bash
PS C:\ti\MMWAVE_L_SDK_05_05_03_00> gmake -s -C examples/hello_world/xwrL64xx-evm/m4fss0-0_freertos/ti-arm-clang clean
 Cleaning: xwrL64xx:m4fss0-0:freertos:ti-arm-clang hello_world.release.out ...
process_begin: CreateProcess(NULL, C:/ti/ccs1271/ccs/utils/cygwin/rm -rf obj/release/, ...) failed.
make (e=2): The system cannot find the file specified.
makefile:166: recipe for target 'clean' failed
gmake: *** [clean] Error 2
```

<br>

這邊可以注意一下第三行的錯誤訊息 `process_begin: CreateProcess(NULL, C:/ti/ccs1271/ccs/utils/cygwin/rm -rf obj/release/, ...) failed.`，我的 ccs 版本明明是 `20.1.0` 啊。由於版本不同，路徑理所當然也不同囉！但翻遍了所有路徑下的 makefile 檔案，都沒有找到被寫死的路徑。最後是在 MMWAVE_L_SDK_05_05_03_00/ 下的 `imports.mak` 找到。

<br>

> imports.mak 這個檔案是 TI mmWave SDK 專案建置流程中的環境設定檔，用來集中管理編譯所需的工具鏈與外部套件路徑。內容通常包含了編譯器（ti-arm-clang）、mmWave SDK 等安裝位置。當 Makefile 執行時，會先讀取 imports.mak 中的這些變數設定，確保編譯器與相關函式庫能正確找到來源與標頭檔。

## 解決方法
打開 imports.mak，用 `Ctrl + F` 找到所有 CCS_PATH?=$(TOOLS_PATH)/ccs1271/ccs（有兩個），改成你的 ccs 版本（舉例：我的 ccs 版本為 `20.1.0` → 改成 CCS_PATH?=$(TOOLS_PATH)/ccs2010/ccs）。改完後儲存，gmake 就可以正常運作了。
