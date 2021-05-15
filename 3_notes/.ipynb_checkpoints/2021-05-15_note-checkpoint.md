# 2021-05-15 Note

### Reduce Form VAR Model Result

* R Script:
  https://nbviewer.jupyter.org/github/a0981906660/FXI/blob/main/2_model/2021-05-15_VAR.ipynb

* Processed data of $R_t, M_t, CPI_t, IP_t, Q_t, PC_t$
  ![raw](/Users/Andy 1/Google 雲端硬碟 (r08323004@g.ntu.edu.tw)/0 Semesters/RA/Pf.Huang/FXI/2_model/result/raw.png)
* IRF of $e_t^{mp}$ shock and $e_t^Q$
  ![IRF_shock1](/Users/Andy 1/Google 雲端硬碟 (r08323004@g.ntu.edu.tw)/0 Semesters/RA/Pf.Huang/FXI/2_model/result/figure/IRF_shock1.png)
  ![IRF_shock5](/Users/Andy 1/Google 雲端硬碟 (r08323004@g.ntu.edu.tw)/0 Semesters/RA/Pf.Huang/FXI/2_model/result/figure/IRF_shock5.png)
* Extract exchange rate shocks
  ![shocks](/Users/Andy 1/Google 雲端硬碟 (r08323004@g.ntu.edu.tw)/0 Semesters/RA/Pf.Huang/FXI/2_model/result/shocks.png)

### Major Differences

1. 「原物料商品價格指數（不含燃料）」（$PC_t$）及「原油價格（世界均價）」（ $OP_t$ ）的資料來源不同。原文來自 IMF-IFS，現金資料來自 World Bank 。原因為，現在 IMF 提供的 commodity price index 僅提供 1992 至今的月資料，並以 2016 年為基期。FRED 另有相同期間（1992M1 - now）的資料，但以 2005 年為基期編制指數，因此數值也與 IMF 編制的指數不同。僅有 World Bank 提供 1992M1 以前的月資料，但以 2010 年為基期。

2. use `x11` method of `seasonal` package in R to deal with seasonality.
3. 改以 1987M1 - 2015M12 為樣本期間
4. 以 Wold Ordering 為認定條件，因此 IRF 與原文中的不同



### Questions Encounter

* How to calculate $FXI_t$?
  * 使用已剔除匯率變動因素的「準備貨幣增減因素 -- 國外資產」（金融統計月報表4），並以央行國外資產在 1986 年 12 月的存量為起始點，將「準備貨幣增減因素 -- 國外資產」此資料的流量累加，以得到一個排除掉匯率影響的央行國外資產存量之衡量
  * e.g.
    https://www.cbc.gov.tw/public/data/EBOOKXLS/015_EF13_A4L.pdf
  * In footnote: 若 $X_0$ 代表 1986 年 12 月的央行國外資產, $􏰭Z_t$ 代表準備貨幣增減因素 (國外資產), 則 $FXI_t = \Delta 􏰭log[X_0 + 􏰲\sum_{s=1} \Delta􏰭 Z_s]\times 100$



