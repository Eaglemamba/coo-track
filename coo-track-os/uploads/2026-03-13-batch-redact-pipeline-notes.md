# Batch PDF Redact Pipeline — 對話筆記

**日期：** 2026-03-13

---

## 核心問題

> 第一步的所有 redact 全部完成，要怎麼確定都有執行完？

## 結論

Python 的 `for` 迴圈是**同步阻塞（synchronous blocking）**的。每一份 PDF 的 `redact()` 函數呼叫回傳之前，程式不會往下走。因此：

- 50 份 PDF → 跑完第 1 份才跑第 2 份，跑完第 50 份才離開迴圈
- 離開迴圈 = 100% 全部 redact 完成
- 不需要額外的「確認機制」，語言本身就保證了這件事

## 執行流程

```
全部 redact 完成
    ↓
自動收集 redacted 檔案（複製到另一個資料夾）
    ↓
比對數量（原始 vs redacted）
    ↓
數量正確 → 自動上傳
```

一氣呵成，只需執行一次指令，等它跑完即可。

## 程式碼概念

```python
# 第一段：逐份 redact，全跑完才往下
for pdf in pdf_files:
    redact(pdf)          # 這份沒跑完，不會跑下一份
    print(f"✓ {pdf}")

# ← 走到這裡 = 上面的 for 迴圈 100% 結束了

# 第二段：收集 redacted 檔案
redacted_files = glob.glob(...)

# 第三段：比對數量 + 上傳
if len(redacted_files) == len(pdf_files):
    upload(redacted_files)
else:
    print("數量不符，請檢查")
```

## 關鍵觀念

| 概念 | 說明 |
|------|------|
| 同步阻塞 | `redact(pdf)` 回傳前，下一行不會執行 |
| for 迴圈保證 | 迴圈結束 = 每一輪都跑完了 |
| 不需手動確認 | 程式結構本身就是保證機制 |

---

*此筆記由 Claude Code 對話整理產生。*
