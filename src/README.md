# 前言

> 本手冊（mmWave Handbook）旨在整合並系統化記錄本團隊在毫米波雷達上的開發與實務經驗，以「系統化學習」的方式，幫助讀者在短時間內掌握毫米波雷達的核心概念、訊號處理、演算法與設計實作。此外，本手冊亦作為共享知識庫、加速毫米波雷達應用開發效率的開放資源，避免重複踩雷，並促進知識長期共享。

## 本手冊不涵蓋的範圍
- 不提供或重新散佈 TI 閉源 SDK、安裝程式或技術文件
- 不涉及專利、商業機密或受限制的技術細節
- 不大量複製或翻譯官方技術文件，僅以摘要與心得形式整理
- 不深入探討 RF 晶片級 IC 設計等硬體細節
- 不涵蓋各地法律與合規議題（如發射功率、頻譜規範，請依當地主管機關規定查閱）
- 不包含任何「逆向工程、反編譯或反組譯」的內容

## 適合這本手冊的對象
| 類型 | 需求 | 本手冊價值 |
|------|------|-----------|
| 初學工程師 / 學生 | 快速入門毫米波雷達 | 結構化學習路徑 |
| TI 平台使用者 | SDK 範例、工具鏈導覽 | 專章：[TI mmWave](ti_mmwave/overview.md) |

<br>

## 背景知識
| 主題             | 需要知道什麼 | 為什麼重要 |
|------------------|--------------|------------|
| **訊號處理基礎** | 複數表示、FFT、窗函數 | 幫助理解訊號於時間與頻率的關係 |
| **線性代數**     | 向量、矩陣、特徵值 | 雷達方向估計 (AoA, MUSIC) 的數學基礎 |
| **機率與統計**   | 雜訊模型 | 判斷訊號與雜訊，決定是否檢測到目標 |
| **程式基礎**     | Python AND C/C++ | 模擬、數據分析與實驗驗證 |

<br>

## 手冊結構
| 區塊 | 內容焦點 | 對應章節 |
|------|----------|----------------|
| 基礎 | 毫米波介紹 | [毫米波基礎](./mmwave_basics.md) |
| 硬體 | 天線陣列、前端、chirp | [硬體架構](./hardware_arch.md) |
| 訊號處理 | ADC → Range FFT → Doppler FFT → Angle → CFAR | [訊號處理](./signal_processing.md) |
| 應用 | 人員計數、手勢、生命跡象 | [應用場景與案例](./mmwave_applications.md) |
| TI 生態 | SDK、Toolchain、範例與調試 | [TI mmWave](ti_mmwave/overview.md) |
| 演算法 | CFAR / AoA / Clustering / Tracking / Feature | [常用演算法](./ti/algorithms.md) |
| 附錄 | 公式、符號、測量實務、FAQ | [附錄](appendix/index.md) |

<br>

## TI mmWave 相關章節
`ti_mmwave/` 目錄內包含：

- 官方文件建議閱讀順序 & 新手導向
- Toolchain（CCS, Uniflash, mmWave Studio, Radar Toolbox）
- 範例程式解構與常見修改點
- SDK 內建演算法 / Radar Toolbox 使用脈絡
- 延伸（Clustering, Tracking, Feature 擴充）

所有 TI 內容僅為教學整理，請依原廠授權使用；必要時標註來源。

## 法規與安全
- 發射功率 / 頻譜：請查閱所在地區主管機關（FCC, ETSI, NCC 等）
- 使用 EVM / 開發板：避免金屬遮擋與高溫區域
- 人體生命跡象實驗：遵守倫理與隱私政策；不進行未告知的醫療診斷

## 參與 & 回饋
- 建議 / 問題：於 GitHub 開 Issue，提供上下文、章節、預期/實際結果
- 新增章節：同步更新 `SUMMARY.md` (已啟用 mdbook-toc 可略過此項)
- 大規模結構調整：請先提出 Proposal（Issue 或 Discussion）

關於更多參與及貢獻資訊，請參考 [CONTRIBUTING.md](https://github.com/mellivorandy/mmwave-handbook/blob/main/CONTRIBUTING.md)

## 免責聲明
本手冊內容僅用於教育及研究參考，不保證適用於特定商業或安全關鍵場景。涉及第三方商標（如「Texas Instruments」）僅為描述用途，不代表任何官方。請遵守各 SDK / 文件授權、license，不複製大量原文。

## 下一步

閱讀下一章： 

- 若您是初學者 → [毫米波基礎](fundamentals/mmwave_basics.md)  
- 若您已熟悉毫米波雷達 → 跳至 [訊號處理](fundamentals/signal_processing.md) 或 [TI mmWave](ti_mmwave/overview.md) 

<br>

> 祝學習順利，歡迎回饋與貢獻！  
