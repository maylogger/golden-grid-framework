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

desktop 裡面的 columns 設定簡稱為 d，而當你這樣設定時，他只會影響 desktop 或比 desktop 還要大的裝置。

以下是裝置簡稱對照表

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

