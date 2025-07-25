<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "3cb0da3badd51d73ab78ebade2827d98",
  "translation_date": "2025-07-14T02:19:56+00:00",
  "source_file": "05-AdvancedTopics/mcp-sampling/README.md",
  "language_code": "tw"
}
-->
## 確定性取樣

對於需要一致輸出的應用程式，確定性取樣能確保結果可重現。它的做法是使用固定的隨機種子並將 temperature 設為零。

以下範例展示了如何在不同程式語言中實作確定性取樣。

## 動態取樣設定

智慧取樣會根據每次請求的上下文和需求調整參數。這表示會根據任務類型、使用者偏好或歷史表現，動態調整 temperature、top_p 和懲罰參數。

以下範例展示了如何在不同程式語言中實作動態取樣。

## 接下來的內容

- [5.7 Scaling](../mcp-scaling/README.md)

**免責聲明**：  
本文件係使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們力求準確，但請注意自動翻譯可能包含錯誤或不準確之處。原始文件的母語版本應視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們不對因使用本翻譯而產生的任何誤解或誤譯負責。