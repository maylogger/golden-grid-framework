# Golden Grid Framework

Golden Grid Framework 是從 [Joni Korpi](http://jonikorpi.com/) 提出的 http://goldengridsystem.com/ 概念，改寫為可立即使用的 scss/compass，
以及現成的 CSS ``ggs.css`` 可讓大家輕鬆入門使用的格線系統。

Golden Grid Framework 有以下特性：

- Fluid Grid System 流動格線系統，來自於 [massimo vignellis's unigrid](http://www.aisleone.net/2010/design/massimo-vignellis-unigrid-system/) 與 [DIN paper system](http://en.wikipedia.org/wiki/Paper_size#The_international_standard:_ISO_216)
- Respinsive Design 響應式設計
- 可以針對不同裝置任意修改格線數量 (必須使用 scss 重新編譯)
- 採用 mobile first 設計方式
- 不支援 media query 的瀏覽器會看到手機版（對付舊 IE）

## 裝置對照表

- **media** - 設定影響的裝置
- **prefix** - columns 設定寬度時要使用的 prefix 前綴文字
- **width** - 各 media 設定的裝置寬度
- **all columns** - 裝置全畫面的 columns 數量
- **container columns** - 內容容器 ``.container`` 限制可使用的 columns 數量。

| media                              | prefix  | width       | all columns | container columns |
|------------------------------------|---------|-------------|-------------|-------------------|
| phone (portait)                    | p-      | 0 - 479     | 4           | 4                 |
| phone wide (landscape)             | pw-     | 480 - 639   | 4           | 4                 |
| tablet (portait)                   | t-      | 640 - 767   | 8           | 6                 |
| tablet wide (landscape)            | tw-     | 768 - 1023  | 8           | 8                 |
| desktop                            | d-      | 1024 - 1279 | 8           | 8                 |
| desktop wide                       | dw-     | 1280 - 1599 | 8           | 8                 |
| desktop wide level 2               | dw2-    | 1600 - 1899 | 8           | 6                 |
| desktop wide level 3 (full hd & up)| dw3-    | 1900 - up   | 16          | 10                |

如果您不喜歡這份預設值，可以修改 ``scss/ggs.scss`` 裡面的參數。

## Grid 格線系統

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

如果想讓 tablet 也呈現為左右兩欄，請參考「裝置對照表」tablet 直立時有 6 欄可以使用，
那我們就打算在 tablet 直立時，左欄設定為 2 欄，右欄設定為 4 欄，就這樣寫：

    .container
      .row
        .columns.d-3.t-2
        .columns.d-5.t-4

如果又想特別控制 tablet 橫置 landscape 的欄寬比例，查閱「裝置對照表」tablet 橫置時有 8 欄可以使用，
那我們想要左欄設定為 3 欄，右欄設定為 5 欄，就這樣寫：

    .container
      .row
        .columns.d-3.t-2.tw-3
        .columns.d-5.t-4.tw-5

這個 framework 就是這麼笨！

如果你對於預設值不滿意，可以自行修改 ``scss/ggs.scss`` 裡面的參數，重新編譯你自己的 CSS。

如果你對這個 framework 設計不甚滿意，拜託送我 pull request!!

## 進度

目前的說明文件只寫了 grid 的部份。事實上本專案還有 font-zoom.scss 以及 utility.scss 可用。

就等有空再寫了！

## License

SCSS developed by [evenwu](http://evendesign.tw) / [@evenwu](http://twitter.com/#!/evenwu/)

Licensed under [MIT](http://opensource.org/licenses/mit-license.php).