
# 難以名狀的抓圖器 API 使用說明

## 搜尋圖片

URL: __https://api.maid.im/neko__

HTTP Verb: __GET__

### 可用參數

| 參數名稱 | 資料型態 | 可使用在群組 A 的網站 | 可使用在群組 B 的網站 | 參數說明 |
|----------|----------|-----|----|-----|
|  site  |  array 或是 string |v  |  v | 指定圖片作品出現的網站，其值請參照下方的網站列表|
| author_id|string|v||創作者於該站的ID，需搭配 **site** 才有作用|
| width| integer|v | v|圖片寬度，必須完全符合才會出現|
|height|integer|v|v|圖片高度，必須完全符合才會出現|
|min_width|integer|v|v|圖片最小寬度|
|max_width|integer|v|v|圖片最大寬度|
|min_height|integer|v|v|圖片最小高度|
|max_height|integer|v|v|圖片最大高度|
|tag|string|v|v|關鍵字|
|rating|enum|v||分級，僅接受 **all**（所有圖片）、**everyone**（僅非R-18）及 **adult**（僅R-18），預設是 all|

### 網站列表

| 網站名稱  | 所屬群組 |
|----------|----------|
|  pixiv |  A  |
| nico | A | 
|tinami | A|
|yande.re|B|
|gelbooru|B|
|donmai.danbooru.us|B|
|konachan.com|B|

### 回傳結果
基本上會有三大區塊，每個區塊都會有 **main**（群組 A 的查詢結果） 和 **danbooru** （群組 B 的查詢結果）兩大元素。
* header：本次查詢所查到的數據狀態，請參閱 Header 表的內容說明。
* artworks：查詢出來的結果，請參閱 Artwork 表的內容說明。
* relative_tags：查詢出來的相關標籤，請參閱 Tags 表的內容說明

#### Header
|欄位名稱|欄位說明|
|-----|-----|
|num|本次共查到 N 筆|
|start|列出的資料起點|
|perpage|每頁列出幾筆，固定為30|

#### Artwork
如未說明，基本上兩個群組的資料都會有該元素
|欄位名稱|欄位說明|
|-----|-----|
|site|所屬網站|
|author_id|創作者ID，只有群組 A 才會有此元素|
|id|作品 ID|
|title|作品標題|
|thumbnail|縮圖|
|r_18|分級，只有群組 A 才有此項目。true 為 R-18，false 為普遍級|
|original_url|該作品的原網址|
|page_url|在 **難以名狀的抓圖器** 的網址|
|photos|該作品的圖片資訊，為一個陣列，每個元素又有 **photo** （圖片網址，群組 B 不會有這個資料）、**width** （圖片寬度）及 **height** （圖片高度） |
|tags|該作品的標籤，為一個陣列|

#### Tags 
|欄位名稱|欄位說明|
|-----|-----|
|tag|標籤文字內容|
|cnt|該標籤的數量|
