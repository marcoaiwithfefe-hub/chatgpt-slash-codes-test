# 08 code：/STEP-BY-STEP

原文：Excel 樞紐分析表
ChatGPT，暫時對話（Temporary Chat），2026 年 11 月 24 日

---

Excel 樞紐分析表（Pivot Table）逐步教學

樞紐分析表可以幫你快速整理、分類、統計大量 Excel 資料，唔需要自己寫複雜公式。

例如，你有一間麵包店嘅銷售記錄，想知道每款產品嘅總銷售額、每月收入，或者邊款產品最好賣。

Step 1｜準備原始資料

假設你有以下 Excel 表格：

日期 | 產品 | 分店 | 數量 | 銷售額

1/11 | Croissant | 灣仔 | 10 | $300

1/11 | Danish | 中環 | 8 | $280

2/11 | Croissant | 中環 | 20 | $600

2/11 | Danish | 灣仔 | 12 | $420

3/11 | Sourdough | 灣仔 | 5 | $250

3/11 | Croissant | 灣仔 | 15 | $450

注意：每一欄必須有標題，資料中間避免有空白行，亦唔好合併儲存格。

Step 2｜插入樞紐分析表
tech2touch.com

點擊原始資料內任何一個儲存格。

點擊上方「插入」（Insert）。

選擇「樞紐分析表」（PivotTable）。

確認資料範圍。

選擇「新增工作表」（New Worksheet）。

按確定。

Step 3｜認識四個分析區域

建立後，右邊會出現樞紐分析表欄位面板。

樞紐分析表欄位 PivotTable Fields

日期
產品
分店
數量
銷售額
將欄位拖曳到以下四個區域

篩選 Filters

日期

欄 Columns

分店

列 Rows

產品

值 Values

加總－銷售額

區域 | 用途

Filters 篩選 | 選擇想睇嘅資料

Columns 欄 | 橫向分類

Rows 列 | 直向分類

Values 值 | 計算總和、平均值、數量等

Step 4｜製作第一張分析表

想知道每款產品嘅總銷售額，只需要將：

「產品」拖入 Rows。

「銷售額」拖入 Values。

Excel 就會自動生成：

產品 | 總銷售額

Croissant | $1,350

Danish | $700

Sourdough | $250

總計 | $2,300

各產品銷售額

港幣 HKD

Croissant

$1,350

Danish

$700

Sourdough

$250

Step 5｜加入分店比較

再將「分店」拖入 Columns，就可以同時比較兩間分店嘅銷售表現。

產品 | 灣仔 | 中環 | 總計

Croissant | $750 | $600 | $1,350

Danish | $420 | $280 | $700

Sourdough | $250 | $0 | $250

總計 | $1,420 | $880 | $2,300

Step 6｜互動練習

你可以喺下面模擬更改樞紐分析表設定，睇吓結果點樣即時改變。

Pivot Table 模擬器
Rows 列
產品
Columns 欄
分店
Values 值
銷售額
計算方式
加總 SUM
Filters 篩選分店
全部
灣仔
中環

產品 | 中環 | 灣仔 | 總計

Croissant	$600	$750	$1,350
Danish	$280	$420	$700
Sourdough	—	$250	$250

總計 | $880 | $1,420 | $2,300

重設
Step 7｜更改計算方式
fptshop.com.vn

喺 Values 區域點擊欄位，選擇「值欄位設定」（Value Field Settings），就可以更改計算方法。

方法 | 功能

SUM | 加總

COUNT | 記錄筆數

AVERAGE | 平均值

MAX | 最大值

MIN | 最小值

Step 8｜更新資料

當你修改或者新增原始資料後，樞紐分析表未必會自動更新。

喺樞紐分析表上撳右鍵，再選擇「重新整理」（Refresh）。

建議一開始將原始資料轉換成 Excel Table（插入 → 表格），咁日後新增資料行，重新整理時就可以自動包含新增範圍。

最簡單嘅記憶方法：

想分析咩項目 → Rows

想比較咩分類 → Columns

想計算咩數字 → Values

想限制咩條件 → Filters

掌握呢四個區域，就已經可以應付大部分日常銷售、庫存、成本同營業額分析。
