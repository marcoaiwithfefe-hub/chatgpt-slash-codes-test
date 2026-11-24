# 19 白話：我已經識基本操作，跳過入門，直接講進階用法

原文：Excel 樞紐分析表
ChatGPT，暫時對話（Temporary Chat），2026 年 11 月 24 日

---

既然你已經識 Excel 樞紐分析表（Pivot Table）基本操作，我哋直接跳去進階應用。重點唔再係點樣將欄位拖入 Rows、Columns、Values，而係點樣利用 Pivot Table 做商業分析、動態報表、自動化同多維度數據分析。

以下用店舖營運及銷售數據做例子。

01｜Show Values As：同一組數據，多角度分析

好多人只識用 SUM、COUNT、AVERAGE，但「值顯示方式」先係 Pivot Table 真正強大嘅地方。

同一個銷售金額欄位，四種分析方式（示範數據）
| 月份 | 營業額 | 佔比 | 月增長 | 累計 |
|---|---|---|---|---|
| 1月 | $100,000 | 21.7% | — | $100,000 |
| 2月 | $120,000 | 26.1% | +20% | $220,000 |
| 3月 | $90,000 | 19.6% | −25% | $310,000 |
| 4月 | $150,000 | 32.6% | +66.7% | $460,000 |

$0
$40K
$80K
$120K
$160K
1月
2月
3月
4月
1月: 營業額 $100K
2月: 營業額 $120K
3月: 營業額 $90K
4月: 營業額 $150K

將 Sales 欄位拖入 Values 四次，再分別設定 Show Values As。

| 功能 | 實際用途 |
|---|---|
| % of Grand Total | 產品佔整體營業額比例 |
| % of Parent Row Total | 產品佔所屬類別嘅比例 |
| % Difference From | 按月、按年增長率 |
| Running Total In | 累計營業額 |
| % Running Total In | ABC 商品分類 |
| Rank Largest to Smallest | 產品銷售排名 |
| Index | 分析類別之間嘅相對集中程度 |

例如設定 % Difference From，Base Field 選月份，Base Item 選 (previous)，就可以自動計算月增長率，完全唔需要額外公式。

02｜Pareto Analysis：搵出最值得投放資源嘅產品

利用累計百分比，分析邊幾款產品貢獻咗大部分營業額。

產品銷售貢獻分析（示範數據）

牛角包

累計 35%

35%

開心果丹麥酥

累計 60%

25%

朱古力酥

累計 80%

20%

肉桂卷

累計 90%

10%

其他產品

累計 100%

10%

首三款產品已經佔整體營業額 80%。

做法：將產品按照營業額由大至小排序，再加入第二個 Sales 欄位，設定 % Running Total In，Base Field 選產品。

你可以用嚟分析產品淘汰、庫存分配、客戶價值、供應商集中度。不過決定淘汰產品時，亦要考慮毛利同產品之間嘅互補作用。

03｜Calculated Field vs DAX Measures

呢個係普通 Excel 使用者同進階數據分析使用者之間一個重要分水嶺。

假設你想分析毛利率。

普通 Pivot Table 可以用 Calculated Field：

excel
=(Sales-Cost)/Sales

但如果涉及多張表、複雜篩選條件、非加總型指標，DAX Measures 會更有彈性。

透過 Power Pivot / Data Model 建立：

dax
Total Sales := SUM(Sales[Revenue])

Total Cost := SUM(Sales[Cost])

Gross Profit := [Total Sales] - [Total Cost]

Gross Margin := DIVIDE([Gross Profit], [Total Sales])

點解唔直接 Average 每件產品嘅毛利率？

| 產品 | 營業額 | 毛利 | 毛利率 |
|---|---|---|---|
| A | $90,000 | $54,000 | 60% |
| B | $10,000 | $2,000 | 20% |

直接平均毛利率（錯誤）
40%
整體加權毛利率（正確）
56%

DAX Measure 會因應你當時選擇嘅月份、產品、分店等篩選條件重新計算，而唔係單純加總已經計好嘅百分比。

04｜Data Model：多張表直接建立關聯

唔需要再用大量 VLOOKUP 或 XLOOKUP 將所有資料塞入同一張表。

Star Schema 星型模型：三張維度表，連接一張銷售事實表。

建立關聯之後，就可以直接喺同一張 Pivot Table 分析唔同表格嘅資料。

例如 Rows 放產品類別、Columns 放分店、Values 放毛利率、Filter 放年份。

呢種架構特別適合處理幾十萬甚至過百萬行數據，亦係 Power BI 嘅核心概念。

05｜DAX Time Intelligence：時間維度分析

建立獨立 Calendar Table 及正確日期關聯之後，就可以用 DAX 做更深入嘅時間分析。

| 指標 | DAX 函數 |
|---|---|
| 本年累計銷售 YTD | TOTALYTD |
| 本月累計銷售 MTD | TOTALMTD |
| 上年同期銷售 | SAMEPERIODLASTYEAR |
| 上月銷售 | DATEADD |
| 過去12個月銷售 | DATESINPERIOD |

例如按年增長率 YoY：

dax
Sales LY :=
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)
dax
YoY Growth :=
DIVIDE(
    [Total Sales] - [Sales LY],
    [Sales LY]
)

每次轉換年份、月份或者分店，所有指標會自動重新計算。

06｜Slicer + 多張 Pivot Table：互動式 Dashboard

以下係一個模擬營運 Dashboard。你可以直接切換分店，睇吓所有指標點樣同步變化。

營運分析 Dashboard
模擬數據
[transcribed from screenshots]
全部
灣仔
中環
銅鑼灣
總營業額
$1,240,000
毛利率
57.7%
總訂單量
12,350
平均客單價
$100.4
每月營業額
0k
100k
200k
300k
400k
1月 250k
2月 305k
3月 295k
4月 390k
最新月份增長率 MoM
+32.2%

Excel 入面嘅關鍵設定係：

Slicer → Report Connections

將同一個 Slicer 連接去多張使用相同資料來源快取或 Data Model 嘅 Pivot Table，就可以做到一個按鈕控制整份報表。

07｜GETPIVOTDATA：建立自訂報表

如果你直接用 =B5 引用 Pivot Table 嘅數字，排序或者篩選之後，可能會攞錯數據。

改用：

excel
=GETPIVOTDATA("Revenue",$A$3,"Store","灣仔")

甚至可以將條件改成動態儲存格：

excel
=GETPIVOTDATA("Revenue",$A$3,"Store",F2)

咁就可以將 Pivot Table 放喺後台工作表，前台只顯示你自己設計嘅 KPI、圖表、財務報告。

Pivot Table 負責計數，你負責控制報表排版。

08｜Power Query + Pivot Table：報表自動化

如果你每個月都要下載 POS 銷售記錄、整理 Excel、合併資料，再重新製作報表，其實可以將大部分工作自動化。

原始數據資料夾
每月 POS CSV / Excel 檔案
↓
Power Query
合併檔案、清洗數據、修正格式、Unpivot
↓
Data Model + DAX
建立關聯、商業邏輯、計算指標
↓
Pivot Table + Dashboard
自動更新分析結果及圖表

設定好之後，每個月只需要將新檔案放入指定資料夾，再按 Refresh All。

唔使重新寫公式，唔使逐張表 Copy & Paste，亦唔使重新製作圖表。

09｜其他值得掌握嘅隱藏進階功能

| 功能 | 用途 |
|---|---|
| Distinct Count | 計算不重複客戶、訂單數量 |
| Value Filters – Top 10 | 動態顯示最高銷量產品 |
[end of transcribed part]
| Show Report Filter Pages | 自動為每間分店建立獨立工作表 |
| Drill Down | 雙擊數字提取相關明細記錄 |
| Grouping | 自訂價格區間、年齡區間、時段 |
| Conditional Formatting | 動態熱力圖、數據條 |
| CUBEVALUE / CUBEMEMBER | 直接由 Data Model 建立自由排版報表 |
| Unpivot Columns | 將橫向月份報表轉成可分析嘅數據結構 |

留意：完整 Power Pivot、DAX 建模功能主要適用於支援相關功能嘅 Windows 桌面版 Excel。Mac 版功能有所限制。

建議你嘅進階學習路線
1

進階 Pivot Table

Show Values As、Pareto、Value Filters
2

互動式報表

Slicer、Timeline、GETPIVOTDATA
3

數據自動化

Power Query、Merge、Append、Unpivot
4

關聯式數據模型

Power Pivot、Star Schema、Relationships
5

商業智能分析

DAX、Filter Context、CALCULATE、Time Intelligence

如果你已經熟悉基本 Pivot Table，我會建議你將最多時間投放喺 Power Query、Data Model 同 DAX。

學識呢三樣嘢，你就唔再只係用 Excel 整報表，而係可以用 Excel 建立一套可重複使用、自動更新嘅商業數據分析系統。將來轉用 Power BI，亦有相當大部分知識可以直接沿用。
