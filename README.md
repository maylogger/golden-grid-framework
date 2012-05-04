# Golden Grid Framework

Golden Grid Framework 是從 [Joni Korpi](http://jonikorpi.com/) 提出的 http://goldengridsystem.com/ 概念，改寫為可立即使用的 scss/compass。
以及現成的 CSS ``gss.css`` 可讓大家輕鬆入門使用這樣的格線系統。

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

如果你對這份預設值有意見，可以修改 ``scss/ggs.scss`` 裡面的參數。

## 使用說明

### Grid 格線系統

你會用到這幾個 class
``.container`` ``.row`` ``.column`` or ``.columns``

一個基本的 2 欄 grid 的 HTML 架構如下

    <div class="container">
        <div class="row">
            <div class="columns"></div>
            <div class="columns"></div>
        </div>
    </div>

為了簡化我們的文件，以下採用 haml 的寫法：

    .container
      .row
        .columns
        .columns

你會發現這樣的兩個 columns 其實沒有並排，他們預設都是 100% 佔滿整個畫面。
現在我想要把這兩欄並排，查閱「裝置對照表」可以看到 desktop 預設的 grid 為 8 欄，
我希望左邊佔 3 欄，右邊佔 5 欄的時候，這樣寫：

    .container
      .row
        .columns.d-3
        .columns.d-5

``d-3`` 的 d 代表 desktop，3 代表 3 欄。這樣設定只會影響 **desktop** 以及比 **desktop 還要大的裝置**。

也就是說，如果不針對 phone 或 tablet 特別做設定，那這些 columns 都會是自動撐滿 100% 的狀態。
100% 寬就會由上往下順序排列，而不是左右兩欄。

如果你也想讓 tablet 有左右兩欄，請參考下面的「裝置對照表」，tablet 直立時有 6 欄可以使用，
那我們就打算在 tablet 直立時，左欄設定為 2 欄，右欄設定為 4 欄，就這樣寫：

    .container
      .row
        .columns.d-3.t-2
        .columns.d-5.t-4

如果又想 tablet 橫置 landscape 的欄寬比例，一樣要查閱「裝置對照表」，tablet 橫置時有 8 欄可以使用，
那我們想要左欄設定為 3 欄，右欄設定為 5 欄，就這樣寫：

    .container
      .row
        .columns.d-3.t-2.tw-3
        .columns.d-5.t-4.tw-5

