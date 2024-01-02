---
description: ISCN 與 IPFS 兩者息息相關
---

# ISCN 和 IPFS 的關係是什麼？

IPFS 是分佈式檔案系統，功能是儲存檔案數據，提供 IPFS Hash 作內容指紋 ( content fingerprint )，是較底層的協議基礎。

ISCN 儲存的則是內容的元數據 ( metadata )，例如作者、日期、授權方式、版本、內容指紋等。ISCN 配合 IPFS 檔案系統使用，令用戶更容易搜尋內容，作者也可以 ISCN 管理授權方傾及內容版本等。

然而 ISCN 儲存的內容指紋不一定來自  IPFS，也可以是其他分佈式檔案系統如 Arweave，或任何檔案網址。ISCN 不限內容以何種方式寄存，甚至不填寫內容指紋，只註冊內容元數據也是可以的。
