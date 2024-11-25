---
description: 從雲端到實體的全新登入管理方案，一鍵登入任何系統
---

# 什麼是 Authcore？

[Authcore](https://authcore.io/zh-TW/) 由幾部分組成，一邊是用戶身份管理系統，另一邊是利用 [Intel SGX](https://www.intel.com.tw/content/www/tw/zh/architecture-and-technology/software-guard-extensions.html) 的可信任運算環境開發的密鑰管理系統。

用戶的私鑰由密鑰管理系統保管，客戶端會通過 SPAKE2 零知識密碼證明 與 密鑰管理系統 認證身份，密鑰管理系統亦有使用強加密保護數據。這個設計的目的是確保只有用戶能夠使用私鑰，同時為用戶帶來更直觀的用戶體驗。
