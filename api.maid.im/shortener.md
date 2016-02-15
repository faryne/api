# 泛用縮網址工具 API 

## 縮網址

URL: __http://api.maid.im/shortener/do__

HTTP Verb: __POST__

### 參數說明

| 參數名稱 | 參數說明 |
|----|----|
| domain | 必填，其值必須為下方網站列表中之一 |
| url | 必填，要縮短的長網址 | 

### 回傳結果
執行成功後會回傳一個陣列，結構如下

```json
{
    "longUrl": "http://www.example.com/",
    "shortUrl": "http://ppt.cc/gNa8Y"
}
```

若是其中發生任何錯誤時則會回傳以下的可能狀況：

```json
// 該縮網址服務發生問題時
{
	"error": "xxx is error"
}
```

或是
```json
{
	"error":
	{
		"domain":	
		[
			"domain 必須要有值"
		]
	}
}
```

## 網站列表

URL: __http://api.maid.im/shortener/list__

HTTP Verb: __GET__

### 參數列表
此方法不需要任何參數

### 回傳結果
執行完成後會回傳一個網站列表的陣列

```json
[
	"goo.gl",
    "ppt.cc"
]
```