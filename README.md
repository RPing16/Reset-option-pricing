# 重設選擇權定價
使用二元樹(CRR model)對重設選擇權定價
## 選擇權種類
1.  **歐式買權**
2.  **歐式賣權**
3.  **美式買權**
4.  **美式賣權**
## code重點說明
1.  **將tree中有無曾經觸碰過重設價格的選擇權價值分別存放在list中的不同位置**
  - option_value[i][0] <- 未曾觸碰過重設價格的選擇權價值
  - option_value[i][1] <- 曾觸碰過重設價格的選擇權價值
2.  **將選擇權價值分成有無觸碰過重設價格的理由**
  - 在計算第t期選擇權價值時需要第t+1期選擇權價值，而第t期和t+1期的選擇權價值會因是否觸碰過重設價格而有不同，因此在計算第t期時
3.  **第t期選擇權價值的存取位置為第t+1期的存取位置(新資料覆蓋舊資料)**
4.  **每t期的情境分為3種** 
- 第t期&第t+1期股價均未觸碰到重設價格
- 第t期沒觸碰到重設價格，第t+1期有觸碰到
- 第t期觸碰到重設價格
5.  **歐美式差異**
- 美式選擇權在tree中額外增加一個list分別存放有無曾經觸碰過重設價格的履約價值
6.  **買賣權差異**
- 買權和賣權的差異在於情境判斷方式(重點4)不同
- 例如在判斷『第t期股價是否有觸碰到重設價格』時
  -  買權 : St <= H
  -  賣權 : St >= H   
