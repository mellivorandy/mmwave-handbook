# 快速入門

> 本章針對 TI mmWave 雷達平台（IWR/IWRL 系列）提供開箱、基本設定、資料擷取與簡易開發流程，適合初學者快速上手。

## 準備需求

### 硬體開箱

- TI mmWave EVM (例如 **IWRL6432BOOST** 或 **IWR6843AOP**)
- 搭配開發介面板 (如果您是用 IWR6843AOP 這塊 EVM，將會需要 **MMWAVEICBOOST**)
- USB 線材
- (選配) **DCA1000** 資料擷取卡，用於收集原始 ADC 資料

### 必備安裝項目
1. Code Composer Studio (CCS) <br>
    
    TI 官方整合開發環境（IDE），支援編輯、編譯、除錯和韌體燒錄等眾多功能。
    
    - 官網連結：[TI Code Composer Studio](https://www.ti.com/tool/CCSTUDIO)

<br>

2. mmWave SDK <br>
    
    TI 官方雷達軟體開發套件（SDK），整合驅動程式和範例專案（如 Out-of-Box Demo 等）。<br>
    
    依照 mmWave EVM 種類分成不同版本，像 IWR6843AOP 這塊用的是 `MMWAVE-SDK`；IWRL6432BOOST 這塊則是使用 `MMWAVE-L-SDK` (L 代表 low-power)。
    
    > 請依照 TI mmWave EVM 來選擇開發套件。
    
    - 官網連結：[TI MMWAVE-SDK](https://www.ti.com/tool/MMWAVE-SDK)
    - 官網連結：[TI MMWAVE-L-SDK](https://www.ti.com/tool/MMWAVE-L-SDK)

<br>

3. UNIFLASH <br>

    TI 官方韌體燒錄工具，支援 mmWave EVM（AWR/IWR 系列）及其他 TI 嵌入式平台。
    可透過 USB 將 bin 檔、hex 檔等韌體檔案燒錄至 EVM 主板。

    - 官網連結：[TI UNIFLASH](https://www.ti.com/tool/UNIFLASH)

<br>

4. TI ARM-CGT-CLANG 編譯器 <br>

    TI 官方 ARM Cortex-R/Cortex-M 系列專用 C/C++ 編譯器，支援 mmWave EVM 韌體開發。

    - 官網連結：[TI - ARM-CGT-CLANG](https://www.ti.com/tool/download/ARM-CGT-CLANG)

<br>

---
