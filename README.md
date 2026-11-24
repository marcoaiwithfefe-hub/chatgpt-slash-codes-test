# ChatGPT 99 個 code 唔使背：20 個實測對照

網上啲「ChatGPT 隱藏 code」（/SHORT、/TLDR、/PUSHBACK……）其實唔係 ChatGPT 功能。OpenAI 官方嘅斜線 command 清單得 28 個，全部係控制 app 嘅操作（例如 /model、/plan），一個都唔係呢啲。ChatGPT 只係當佢哋係普通字，估你想點。

所以我將最多人 share 嘅 20 個 code，逐個同一句普通廣東話（下面叫「白話」）對比：用同一份原文，各自開一個新嘅暫時對話 run 一次，再由 Gemini 4 Neon 盲測評分（佢唔知邊個係 code）。

## 結果

- 白話做到：**19 / 20**
- code 做到：**12 / 20**
- 白話打和或者贏：**15 / 20**

即係話：唔使背 code，直接講你要乜，多數更穩陣。有幾次 code 版排版靚啲（例如 /TLDR、/CHECKLIST），但白話都做到。

## 20 個對照

| # | code | 直接咁講就得 | 原文 | code 做到？ | 白話做到？ | 邊個好啲 | 分別 | 答案 |
|---|---|---|---|---|---|---|---|---|
| 01 | `/ELI5` | 用小學生都明嘅講法解釋，加一個生活例子 | 公司年假通告（樣本） | ❌ | ❌ | 白話 | 兩個都唔似講畀小朋友聽；白話版有生活例子，易明少少 | [code](answers/01-code.md) · [白話](answers/01-plain.md) |
| 02 | `/TLDR` | 用三句講晒重點 | 公司年假通告（樣本） | ✅ | ✅ | code | 兩個都做到；code 版逐點分行，易睇啲 | [code](answers/02-code.md) · [白話](answers/02-plain.md) |
| 03 | `/SHORT` | 縮短一半，意思唔好變 | 公司年假通告（樣本） | ✅ | ✅ | 白話 | 兩個都做到；白話版保留晒細節（7 個工作天、最多帶 5 日假） | [code](answers/03-code.md) · [白話](answers/03-plain.md) |
| 04 | `/BRIEFLY` | 答我一兩句就得，唔使解釋 | 香港租樓定買樓 | ❌ | ✅ | 白話 | code 版寫咗成篇長文加埋表格；白話版真係一兩句答完 | [code](answers/04-code.md) · [白話](answers/04-plain.md) |
| 05 | `/PUSHBACK` | 唔好附和我，講出呢個諗法最大嘅三個問題 | 辭工開咖啡店 | ✅ | ✅ | code | 兩個都有反駁；code 版計埋開舖預算，具體啲 | [code](answers/05-code.md) · [白話](answers/05-plain.md) |
| 06 | `/CRITIC` | 逐點指出呢個計劃嘅弱點，唔使讚 | 辭工開咖啡店 | ❌ | ✅ | 白話 | code 版仲讚你；白話版一句都冇讚，弱點講得齊啲 | [code](answers/06-code.md) · [白話](answers/06-plain.md) |
| 07 | `/HUMAN` | 改寫到好似真人同同事講嘢咁，唔好官腔，唔好加新內容 | 公司年假通告（樣本） | ❌ | ✅ | 白話 | code 版仍然似官方通告；白話版改到似同事傾偈 | [code](answers/07-code.md) · [白話](answers/07-plain.md) |
| 08 | `/STEP-BY-STEP` | 整理成編號步驟教我整一個，每步一句 | Excel 樞紐分析表 | ❌ | ✅ | 白話 | code 版寫咗長篇教學；白話版一步一句 | [code](answers/08-code.md) · [白話](answers/08-plain.md) |
| 09 | `/CHECKLIST` | 整理成可以逐項剔嘅清單 | 公司年假通告（樣本） | ✅ | ✅ | code | 兩個都有整到清單；code 版將年資級別分開，清楚啲 | [code](answers/09-code.md) · [白話](answers/09-plain.md) |
| 10 | `/COMPARE` | 用表格比較兩邊嘅好處同壞處，最後講邊種人啱邊個 | 香港租樓定買樓 | ✅ | ✅ | 白話 | 兩個都做到；白話版比較同「邊種人啱」寫得詳細啲 | [code](answers/10-code.md) · [白話](answers/10-plain.md) |
| 11 | `/EXEC SUMMARY` | 寫一段畀老闆睇嘅摘要：結論先，再講原因同下一步 | 公司年假通告（樣本） | ❌ | ✅ | 白話 | code 版冇講原因同下一步；白話版先講結論，原因、下一步齊晒 | [code](answers/11-code.md) · [白話](answers/11-plain.md) |
| 12 | `/JARGON` | 改寫成人力資源專業用語 | 公司年假通告（樣本） | ❌ | ✅ | 白話 | code 版反而寫淺咗；白話版先真係用專業用語 | [code](answers/12-code.md) · [白話](answers/12-plain.md) |
| 13 | `/FEYNMAN` | 用最簡單嘅講法解釋，之後問我三條問題，睇我明唔明 | Excel 樞紐分析表 | ✅ | ✅ | code | 兩個都做到；code 版多咗互動示範同額外問題 | [code](answers/13-code.md) · [白話](answers/13-plain.md) |
| 14 | `/SWOT` | 用優勢、弱點、機會、威脅四格分析 | 辭工開咖啡店 | ✅ | ✅ | code | code 版用咗我帳戶嘅記憶，寫得貼身啲所以評審揀咗佢，但唔算公平比較 | [code](answers/14-code.md) · [白話](answers/14-plain.md) |
| 15 | `/ROADMAP` | 幫我排一個四星期學習計劃，每星期一個目標 | Excel 樞紐分析表 | ✅ | ✅ | 白話 | 兩個都做到；白話版跟足四星期排，每星期仲有練習，實際啲 | [code](answers/15-code.md) · [白話](answers/15-plain.md) |
| 16 | `/QUIZ-ME` | 出五條選擇題考我，我答完先畀答案 | Excel 樞紐分析表 | ✅ | ✅ | 打和 | 兩個都做到；白話版一次過出晒五條，code 版一條一條嚟 | [code](answers/16-code.md) · [白話](answers/16-plain.md) |
| 17 | `/CHEAT-SHEET` | 整理成一頁速查表 | Excel 樞紐分析表 | ✅ | ✅ | 白話 | 兩個都做到；白話版真係一頁，code 版拉長到九個部分 | [code](answers/17-code.md) · [白話](answers/17-plain.md) |
| 18 | `/TABLE` | 整理成表格 | 公司年假通告（樣本） | ✅ | ✅ | 打和 | 兩個都做到，分別好細 | [code](answers/18-code.md) · [白話](answers/18-plain.md) |
| 19 | `/SENIOR` | 我已經識基本操作，跳過入門，直接講進階用法 | Excel 樞紐分析表 | ❌ | ✅ | 白話 | code 版仍然由入門教起；白話版直接講進階 | [code](answers/19-code.md) · [白話](answers/19-plain.md) |
| 20 | `/ACT AS` | 用面試官嘅語氣追問我，一次問一條 | 見工（marketing executive） | ✅ | ✅ | 打和 | 兩個都做到；code 版開頭先解釋點樣做模擬面試，白話版一開始就入戲 | [code](answers/20-code.md) · [白話](answers/20-plain.md) |

## 點測

- 每個 code 同白話各自喺 ChatGPT 開一個新嘅暫時對話（Temporary Chat），用同一份原文，模型係 GPT-6.2。
- code 版：貼上原文，空一行，然後淨係打 code（網上教嘅用法）。白話版：貼上原文，空一行，然後打嗰句白話。
- 評分：Gemini 4 Neon 盲測評分，答三條問題：兩個有冇做到 code 聲稱嘅效果、邊個好啲、分別係乜。
- 今次發現，就算開咗暫時對話，ChatGPT 都引用咗我帳戶嘅記憶：有 6 個答案涉及個人記憶，全文唔公開（第 14 組嘅 code 版因此唔算公平比較）。
- 一次測試，一個帳戶，唔代表次次一樣。

## 想 code 真係變快捷鍵？

喺 ChatGPT「自訂指示」寫低，例如：「當我打 /TLDR，即係用三句講晒重點」。咁先係你自己設定嘅快捷鍵。

by @marcorefusestocode
