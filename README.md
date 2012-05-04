# Readme

這份 framework 是從 [Joni Korpi](http://jonikorpi.com/) 提出的 http://goldengridsystem.com/ 改寫為 scss/compass 的版本，並試圖讓操作簡易化。

## How to use

你會用到這幾個 class

- .container
- .row
- .column or .columns

一個基本的 2 欄 grid 架構如下

    .container
      .row
        .columns
        .columns

預設 desktop 的 grid 為 8 欄，而我們希望左邊佔 3 欄，右邊佔 5 欄的時候，這樣寫：

    .container
      .row
        .columns.d-3
        .columns.d-5

是的，desktop 裡面的 columns 設定簡稱為 d，而當你這樣設定時，他只會影響 desktop 或比 desktop 還要大的裝置。

以下是裝置簡稱對照表

| media | 簡稱 | 
|-------|-----|
| p  | phone (portait)        |
| pw | phone wide (landscape) |
| t  | tablet (portait)       |
| tw | tablet wide (landscape)|
| d  | desktop |
| dw  | desktop wide |
| dw2  | desktop wide level 2 |
| dw3  | desktop wide level 3 (full hd & up)|

