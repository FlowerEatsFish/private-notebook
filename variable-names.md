# Variable names

Reference: [API 設計— 命名之術](https://medium.com/corneltek/api-%E8%A8%AD%E8%A8%88-%E7%AC%AC%E4%B8%80%E9%83%A8-%E5%91%BD%E5%90%8D%E4%B9%8B%E8%A1%93-8dfe71576e95)

- [Variable names](#variable-names)
  - [get-](#get-)
  - [set-](#set-)
  - [query-](#query-)
  - [do-](#do-)
  - [fetch-/store-](#fetch-store-)
  - [build-](#build-)
  - [create-](#create-)
  - [new-](#new-)
  - [remove-, delete-](#remove--delete-)
  - [traverse-](#traverse-)

## get-

通常類別方法以 get- 開頭，意味著我們要取得某項屬性或數值，很顯然的，我們沒辦法透過屬性直接存取，所以才需要 get- ，而 get- 最重要的一點，就是他「只做簡單回傳，不作修改」，也因此，一個 get method 不應該修改物件的狀態、修改物件內容、也不該調用複雜資料庫查詢。

## set-

通常被用在設定屬性，與 get- 一樣，不該用在資料庫操作。我們在另外一篇文章「建構子設計之道」有討論 set- 正確的使用時機。

## query-

上面說的 get- 不該調用遠端 API 或資料庫操作，讀者肯定心中充滿了疑問，「什麼？不用 get? 我看你才不懂吧」

事實上，還有一個 prefix 很好用，就是 query-，query 意味著查詢，而且是帶有條件的，所以使用者可能會期望 query- method 有條件參數可以傳遞。查詢有很多種含義，不管是 database query, api query 都算是 query，當開發者查看 API 規格，甚至只看得到 caller 怎麼呼叫，”query-” 很明顯的就可以讓開發者了解 — 喔，這個可能得花一點時間，而且可能會有一些 ”溝通” 要做

## do-

do- 列在這邊，實際是常見的錯用 prefix- ，很多時候會看到有人寫 doUpdate, doQuery, doKill 這類包含 do- prefix 的函數名稱，但其實 do- 很沒意義。 如果你只是為了區分 doUpdate 以及 update 這兩個函數名稱，不如就用底線開頭來隱藏另外一個實作吧 _update, update 表面上看起來，很明顯的 update 才是真正的開放 API，而 _update 的 scope 建議應該為 private 或 protected。

## fetch-/store-

fetch- 與 store- 通常是對應的，比 query 更模糊一點的是，fetch- 通常不帶有複雜條件，譬如 fetchProduct, fetchBooks, fetchUserStories 等等，對象通常是資料庫，當然場景需求不同，沒有一定要如此限制。

而當 “fetch”, “store” 同時出現在同一個類別，就可能需要考慮到一致性，因為使用者可能預期 “fetch”, “store” 是對同一個 storage 操作，不該 fetch from A, 但 store to B.

## build-

通常用在 — 給予某些參數，建置某個結構、複雜的參數或物件。 筆者常用的是 — 給予某些簡單的參數，建置複雜的 Parameters 或 Map，譬如 buildReactProducctAppConfig。

build- 也可能意味著，建置資料庫內某種用途的資料，譬如 buildBaseData、buildUserData，但其意義與包含此函數的類別名稱有關。

## create-

通常被用在 ORM Record 建置，如 ActiveRecord Pattern 常使用這個 create() method 來建置新的 Record。 create- 與 build- 很像，但就筆者看來，這兩者不同的地方在於，create- 有明顯目標跟範圍，譬如 Product::create().. Book::create(), createOrder() … 等等，而 build- 如 buildBaseData 等，不是這麼明確。（但也有可能有筆者沒有想到的案例，若有的話，之後補上 XD）

## new-

new- 其實與 create- 不同，new- 很明顯的只意味著建構一個類別的實體化，取名以 new- 開頭，那麼隱含的操作應該不包含資料庫操作。

## remove-, delete-

remove- 與 delete- 其實差異也不是太明顯，但就筆者來看，remove- 意味著從某個資料集，移除掉這個項目，這個 “移除” 很可能只是移除關聯性，並不會刪除實體資料，而 delete- ，很明確的意味著是實體資料的刪除。

## traverse-

在處理樹狀資料時，traverse- 很好用，traverse- 意味著會遍歷一整個樹，常用在處理 AST 的部分。
