# Readme

這份 framework 是從 [Joni Korpi](http://jonikorpi.com/) 提出的 http://goldengridsystem.com/ 改寫為 scss/compass 的版本，並試圖讓操作簡易化。

## How to use

### grid

你會用到這幾個 class
``.container`` ``.row`` ``.column`` or ``.columns``

一個基本的 2 欄 grid 的 HTML 架構如下

    .container
      .row
        .columns
        .columns

預設 desktop 的 grid 為 8 欄，而我們希望左邊佔 3 欄，右邊佔 5 欄的時候，這樣寫：

    .container
      .row
        .columns.d-3
        .columns.d-5

desktop 裡面的 columns 設定簡稱為 d，而當你這樣設定時，他只會影響 desktop 以及比 desktop 還要大的裝置。

也就是說，如果你不針對 phone 或 tablet 特別做設定，那這些 columns 都會是自動撐滿 100% 的狀態。
就會是依照上下順序排列，而不是左右兩欄。

如果你也想讓 tablet 有左右兩欄，請參考下面的「裝置對照表」，tablet 直立時有 6 欄可以使用，
那我們就打算在 tablet 直立時，左欄設定為 2 欄，右欄設定為 4 欄，就這樣寫：

    .container
      .row
        .columns.d-3.t-2
        .columns.d-5.t-4

如果又想 tablet 橫置 landscape 的欄寬比例，一樣看裝置對照表，tablet 橫置時有 8 欄可以使用，
那我們想要左欄設定為 3 欄，右欄設定為 5 欄，就這樣寫：

    .container
      .row
        .columns.d-3.t-2.tw-3
        .columns.d-5.t-4.tw-5

### 裝置對照表

| media                              | prefix | width       | all columns | container columns |
|------------------------------------|--------|-------------|-------------|-------------------|
| phone (portait)                    | p      | 0 - 479     | 4           | 4                 |
| phone wide (landscape)             | pw     | 480 - 639   | 4           | 4                 |
| tablet (portait)                   | t      | 640 - 767   | 8           | 6                 |
| tablet wide (landscape)            | tw     | 768 - 1023  | 8           | 8                 |
| desktop                            | d      | 1024 - 1279 | 8           | 8                 |
| desktop wide                       | dw     | 1280 - 1599 | 8           | 8                 |
| desktop wide level 2               | dw2    | 1600 - 1899 | 8           | 6                 |
| desktop wide level 3 (full hd & up)| dw3    | 1900 - up   | 16          | 10                |

如果你想修改這份預設值，可以修改 ``scss/ggs.scss`` 裡面的參數。

