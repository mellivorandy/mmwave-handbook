# 疑難排解

> 本章節整理在使用 MMWAVE-L-SDK 開發過程中，常見的錯誤情境與解決方式。由於開發環境涉及到不同版本的 SDK、CCS (Code Composer Studio)、以及 Makefile 工具鏈，實際操作時常會遇到版本相容性或路徑設定問題。

<br>

此章節將各種問題以案例方式紀錄，提供快速檢索與參考，幫助使用者能夠更快定位問題來源並找到解決方法。（實際版本號請依照使用者自身環境的 MMWAVE_L_SDK 版本為準。）

<br>
<br>

| 編號 | 主題 | 說明 | 對應章節 |
| ---- | ---- | ---- | ------- |
| 1 | gmake 找不到檔案錯誤 | `gmake` 過程因 CCS 版本路徑不同，導致找不到檔案 | [gmake 找不到檔案錯誤](./gmake.md) |
| 2 | gmake 編譯失敗 | `gmake all` 過程中發生錯誤，與 tiarmclang 編譯器版本有關 | [gmake 編譯失敗](./gmake_tiarmclang.md) |
