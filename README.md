# AD User Count

統計 Active Directory 中各類帳號數量的 Windows 工具。

---
## 下載執行

https://drive.google.com/file/d/11OrrQn5SEof7KlQ0gZgakSp-4MfQUynx/view?usp=drive_link

解壓縮 ZIP 後，執行 EXE

## 功能

一次查詢並顯示以下四種帳號分類的數量：

| 分類 | 說明 |
|------|------|
| 電腦帳號 | 所有加入網域的電腦物件 |
| 使用者帳號（含停用） | 所有使用者帳號，不論啟用狀態 |
| 停用的使用者帳號 | 已被停用的使用者帳號 |
| 活躍帳號 | 啟用中且 60 天內有登入紀錄 |

如下示意，結果以視窗呈現，支援一鍵複製全文。

```
┌──────────────────────────────────────────┐
│  AD 帳號統計                        [X]   │
├──────────────────────────────────────────┤
│  Domain      : corp.example.com          │
│  Query range : past 60 days              │
│  ────────────────────────────────────    │
│  電腦帳號              : 42               │
│  使用者帳號（含停用）  : 318                │
│  停用的使用者帳號      : 57                │
│  活躍帳號（60 天內）   : 201               │
│  ────────────────────────────────────    │
│              [複製]        [關閉]         │
└──────────────────────────────────────────┘
```

---

## 執行需求

- Windows 10 / 11 / Windows Server 2016 以上
- .NET Framework 4.8（上述 Windows 已內建）
- 加入 MSAD 網域的電腦
- Domain User 一般使用者低權限即可，不需要 Domain Admin 管理員高權限

---

## FAQ

### 執行訊息
1. [錯誤] 查詢失敗：指定的網域可能不存在或無法連線。表示該電腦未加入 MSAD 網域。

---

### Microsft Defender / EDR 攔截 EXE
Endpoint Detection 對未簽章的 EXE 會觸發 SmartScreen 或 即時保護，主要判斷依據：
- 沒有數位簽章（Code Signing Certificate）
- 檔案來源是網路下載（Zone.Identifier 標記）

#### 解決方案
解除封鎖 (以下任一)：
- 在 EXE 上按右鍵 → 內容 → 勾選「解除封鎖」→ 確定
- 於 Microsft Defender 攔截時，勾選同意執行與使用
- 加 EDR 入白名單

---
