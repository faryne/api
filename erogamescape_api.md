# Erogamescape 使用者自訂 SQL 查詢 API

## 根據其他使用者已經設定的 SQL 查詢
| HTTP Verb | URL |
|-|-|
| GET | http://api.maid.im/galgame/erogamescape_api_by_id/{id} |

以下是一個成功執行的回傳結果
GET   http://api.maid.im/galgame/erogamescape_api_by_id/1693

```json
{
    "id": "1693",
    "desc": "過去6ヶ月で50件以上得点が入力されたゲームを、得点入力数順（降順）に出力します。<br>\r\n※ID 1584 の6ヶ月バージョンです",
    "sql": "SELECT rank()OVER(ORDER BY COUNT (ur.uid) DESC) AS \"順位\"\r\n     , COUNT (ur.uid) AS \"過去6ヶ月の得点入力数\" \r\n     , t.count AS \"全得点入力数\"\r\n     , t.sellday AS \"発売日\"\r\n     , round( CAST( (CURRENT_DATE - t.sellday)/365.0 AS double precision )::numeric, 1 ) AS \"年数\"\r\n     , t.median AS \"中央値\"\r\n     , CHR(60)||'a href='||CHR(34)||'game.php?game='||t.game_id||CHR(34)||CHR(62) ||t.gamename ||CHR(60)||'/a'||CHR(62) AS \"ゲーム名\"\r\n     , CHR(60)||'a href='||CHR(34)||'brand.php?brand='||t.brand_id||CHR(34)||CHR(62) ||t.brandname ||CHR(60)||'/a'||CHR(62) AS \"ブランド\"\r\nFROM userreview as ur , toukei_temp_table as t\r\nWHERE ur.game = t.game_id\r\n  AND ur.play_tourokubi &gt; CURRENT_DATE - interval '6 months' /* 6ヶ月以内に採点した */\r\n  AND ur.play\r\n  AND t.model = 'PC' \r\n  AND t.erogame\r\n  AND t.count &gt;= 50\r\n  AND t.coterie IS NULL\r\n  AND ur.tokuten IS NOT NULL\r\nGROUP BY  t.game_id, t.gamename, t.sellday, t.median, t.count , t.brandname, t.brand_id\r\nHAVING COUNT(ur.uid) &gt;= 50",
    "data": [
        {
            "順位": "1",
            "過去6ヶ月の得点入力数": "484",
            "全得点入力数": "486",
            "発売日": "2015-02-27",
            "年数": "0.4",
            "中央値": "81",
            "ゲーム名": "<a href=\"game.php?game=21076\">サノバウィッチ</a>",
            "ブランド": "<a href=\"brand.php?brand=1795\">ゆずソフト</a>"
        },
        {
            "順位": "2",
            "過去6ヶ月の得点入力数": "367",
            "全得点入力数": "370",
            "発売日": "2015-02-27",
            "年数": "0.4",
            "中央値": "77",
            "ゲーム名": "<a href=\"game.php?game=20911\">ぼくの一人戦争</a>",
            "ブランド": "<a href=\"brand.php?brand=1387\">あかべぇそふとつぅ</a>"
        },
        {
            "順位": "3",
            "過去6ヶ月の得点入力数": "318",
            "全得点入力数": "319",
            "発売日": "2015-04-24",
            "年数": "0.3",
            "中央値": "85",
            "ゲーム名": "<a href=\"game.php?game=21531\">Evenicle -イブニクル-</a>",
            "ブランド": "<a href=\"brand.php?brand=30\">ALICE SOFT(チャンピオンソフト)</a>"
        },
        {
            "順位": "4",
            "過去6ヶ月の得点入力数": "271",
            "全得点入力数": "311",
            "発売日": "2015-01-30",
            "年数": "0.5",
            "中央値": "84",
            "ゲーム名": "<a href=\"game.php?game=21228\">時計仕掛けのレイライン －朝霧に散る花－</a>",
            "ブランド": "<a href=\"brand.php?brand=1727\">UNiSONSHIFT：Blossom</a>"
        },
        {
            "順位": "5",
            "過去6ヶ月の得点入力数": "254",
            "全得点入力数": "254",
            "発売日": "2015-05-29",
            "年数": "0.2",
            "中央値": "82",
            "ゲーム名": "<a href=\"game.php?game=21164\">ピュア×コネクト</a>",
            "ブランド": "<a href=\"brand.php?brand=1937\">SMEE</a>"
        },
        {
            "順位": "6",
            "過去6ヶ月の得点入力数": "225",
            "全得点入力数": "228",
            "発売日": "2015-03-27",
            "年数": "0.4",
            "中央値": "82",
            "ゲーム名": "<a href=\"game.php?game=19979\">美少女万華鏡 ─神が造りたもうた少女たち─</a>",
            "ブランド": "<a href=\"brand.php?brand=2408\">ωstar</a>"
        },
        {
            "順位": "7",
            "過去6ヶ月の得点入力数": "204",
            "全得点入力数": "205",
            "発売日": "2015-03-27",
            "年数": "0.4",
            "中央値": "75",
            "ゲーム名": "<a href=\"game.php?game=21080\">花咲ワークスプリング!</a>",
            "ブランド": "<a href=\"brand.php?brand=114\">SAGA PLANETS</a>"
        },
        {
            "順位": "8",
            "過去6ヶ月の得点入力数": "193",
            "全得点入力数": "194",
            "発売日": "2015-02-27",
            "年数": "0.4",
            "中央値": "81",
            "ゲーム名": "<a href=\"game.php?game=21143\">シルヴァリオ ヴェンデッタ</a>",
            "ブランド": "<a href=\"brand.php?brand=309\">light</a>"
        },
        {
            "順位": "9",
            "過去6ヶ月の得点入力数": "186",
            "全得点入力数": "187",
            "発売日": "2015-04-24",
            "年数": "0.3",
            "中央値": "75",
            "ゲーム名": "<a href=\"game.php?game=21325\">プラマイウォーズ</a>",
            "ブランド": "<a href=\"brand.php?brand=1511\">ASa project</a>"
        },
        {
            "順位": "10",
            "過去6ヶ月の得点入力数": "180",
            "全得点入力数": "180",
            "発売日": "2015-04-24",
            "年数": "0.3",
            "中央値": "65",
            "ゲーム名": "<a href=\"game.php?game=21324\">神のラプソディ</a>",
            "ブランド": "<a href=\"brand.php?brand=55\">エウシュリー</a>"
        },
       ......
    ]
}
```



## 以自己想查的 SQL 進行查詢
| HTTP Verb | URL |
|-|-|
| POST| http://api.maid.im/galgame/erogamescape_api_by_sql |
| **所需參數** | **參數內容值說明** |
| sql | 自訂的 SQL，請參閱[說明](http://erogamescape.dyndns.org/~ap2/ero/toukei_kaiseki/sql_for_erogamer_index.php) |

以下是一個成功執行的回傳結果
<pre>
POST  http://api.maid.im/galgame/erogamescape_api_by_sql

sql
SELECT          g.comike, g.id, g.erogetrailers, CASE WHEN h.holyseal_id IS NULL THEN -1 ELSE h.holyseal_id END AS holyseal_id,g.comike, g.id,          CASE WHEN g.erogetrailers IS NULL THEN -1 ELSE g.erogetrailers END AS erogetrailers,          CASE WHEN h.holyseal_id IS NULL THEN -1 ELSE h.holyseal_id END AS holyseal_id,         CASE WHEN g.sellday = '2030-01-01' THEN '1970-01-01' ELSE g.sellday END AS sellday       FROM gamelist g        LEFT JOIN holyseal h ON h.game = g.id        WHERE g.comike IN ('866226', '864430')</pre>

```json
{
    "desc": "User Defined SQL Transmitted",
    "sql": "SELECT          g.comike, g.id, g.erogetrailers, CASE WHEN h.holyseal_id IS NULL THEN -1 ELSE h.holyseal_id END AS holyseal_id,g.comike, g.id,          CASE WHEN g.erogetrailers IS NULL THEN -1 ELSE g.erogetrailers END AS erogetrailers,          CASE WHEN h.holyseal_id IS NULL THEN -1 ELSE h.holyseal_id END AS holyseal_id,         CASE WHEN g.sellday = '2030-01-01' THEN '1970-01-01' ELSE g.sellday END AS sellday       FROM gamelist g        LEFT JOIN holyseal h ON h.game = g.id        WHERE g.comike IN ('866226', '864430')",
    "error": "",
    "data": [
        {
            "comike": "864430",
            "id": "22280",
            "erogetrailers": "0",
            "holyseal_id": "-1",
            "sellday": "2015-08-28"
        }
    ]
}
```