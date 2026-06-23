# Final 自主學習作業報告

## 1. Project Title and Student

Project title: NUTN CSIE 60-second promotional video

Student: 黃可瑜

Student ID: S11259035

Selected topic: 國立臺南大學資訊工程學系 60 秒形象宣傳影片

Selected workflow: OpenClaw-style zero-paid-token mock/stub multi-agent workflow

Editing tool: CapCut

Official reference: https://csie.nutn.edu.tw/cht/index/

## 2. Problem Definition

本專案目標是完成一支 55 至 65 秒的短影片，介紹國立臺南大學資訊工程學系的學習特色、課程方向、動手實作、實驗觀察、專題展示與團隊交流。影片面向高中生、新生、家長與一般觀眾，希望用簡潔的影像與字幕呈現資訊工程學習從課程、實作到成果展示的過程。

影片主題選擇「國立臺南大學資訊工程學系形象宣傳影片」，同時符合加分項目的方向。內容避免使用未經確認的排名、招生名額、就業率、競賽成果或設備誇大敘述，只採用系所介紹、課程方向、實作與專題展示等可由素材畫面支持的描述。

## 3. System Overview

本專案採用受控式 multi-agent workflow。由多個具有明確角色的 agents 分工完成企劃、腳本、分鏡、審查與最終整理。因作業允許零付費 token 路徑，本專案以 mock/stub agent output、JSON handoff 與 execution trace 展示完整流程，不依賴付費 API 或商業 AI 影音生成服務。

Workflow:

User input -> Planner Agent -> Script Agent -> Visual Agent -> Reviewer Agent -> Finalizer Agent -> CapCut editing -> final video

## 4. Agent Design

### Planner Agent

Planner Agent 負責拆解任務，定義目標觀眾、核心訊息、影片長度、素材政策與下游 agent 任務。輸出檔案為 `handoff/01_planner_output.json`。

### Script Agent

Script Agent 負責根據圖片內容與影片時間軸撰寫字幕。最終字幕檔為 `outputs/subtitles_by_image_capcut_utf8.srt`，內容依序對應系所簡介、課程領域、電路實作、實驗室儀器、示波器觀察、專題展示、上台報告與系上活動。

### Visual Agent

Visual Agent 負責將圖片素材整理成 CapCut 可執行的剪輯時間軸。主要輸出包含 `capcut/image_matched_subtitle_timeline.md` 與 `capcut/capcut_step_by_step_with_user_images.md`。

### Reviewer Agent

Reviewer Agent 負責檢查影片是否符合 55 至 65 秒規定、字幕是否可理解、內容是否真實、素材是否需要授權確認，以及是否符合 zero-paid-token 原則。輸出檔案為 `handoff/04_reviewer_feedback.json`。

### Finalizer Agent

Finalizer Agent 負責整理最終繳交檔案，包括 README、報告、影片、字幕、素材來源表與繳交檢查表。輸出檔案為 `handoff/05_finalizer_output.json`。

## 5. Workflow Execution

本專案的 execution trace 位於 `traces/execution_trace.md`。完整流程如下：

1. 使用者提供主題、姓名、學號、官方系網、CapCut 編輯方式與圖片素材。
2. Planner Agent 產生短影片結構、目標觀眾、核心訊息與 agent 任務分派。
3. Script Agent 依照圖片內容撰寫字幕稿。
4. Visual Agent 建立圖片對應字幕時間軸與 CapCut 剪輯建議。
5. Reviewer Agent 檢查影片規格、版權、肖像權與真實性風險。
6. Finalizer Agent 整理最終繳交檔案。
7. 使用 CapCut 完成影片剪輯並輸出 MP4。

## 6. Video Output

Final video file: `outputs/final_video.mp4`

Video duration: 63 seconds

Format: MP4

File size: about 38.91 MB

Subtitle file: `outputs/subtitles_by_image_capcut_utf8.srt`

The final video uses images from `圖片/` and arranges them into the following structure:

| Time | Visual Content | Subtitle Focus |
|---|---|---|
| 0-5s | 系所簡介 | 南大資工以前瞻務實為方向 |
| 5-10s | 3 大領域學程 | 雲端網路、智慧計算、應用資訊 |
| 10-20s | 電路實作 | 從課堂到實作，觀察、測試與修正 |
| 20-38s | 實驗室儀器與示波器 | 透過量測與波形判斷系統變化 |
| 38-50s | 畢業專題展與同學講解 | 把想法做成可展示成果並清楚說明 |
| 50-57s | 上台報告與系大會分享 | 表達、交流與系上活動 |
| 57-60s | 片尾 | 國立臺南大學資訊工程學系 |

## 7. Baseline Comparison

Baseline file: `baseline/single_agent_baseline.md`

Single-agent baseline 的問題是企劃、腳本、分鏡與審查容易混在同一份輸出中，較難看出決策來源，也容易忽略素材授權、肖像權與 60 秒限制。Multi-agent workflow 則透過 Planner、Script、Visual、Reviewer 與 Finalizer 的分工，讓任務邊界、資料交接與審查紀錄更清楚。

Multi-agent workflow 的優點包括：

- 每個 agent 的角色與責任明確。
- 透過 JSON handoff 保留中間輸出。
- 字幕與圖片時間軸能互相對應。
- Reviewer Agent 可獨立檢查長度、真實性、版權與肖像權。
- 即使不使用 paid token，也能展示完整 agentic workflow。

## 8. Cost, Safety, Copyright, and Portrait Rights

本專案符合 zero-paid-token 原則。Agent workflow 以 mock/stub outputs、Markdown、JSON 與 trace 檔案呈現，不需要購買 LLM token、不需要個人 API key，也不使用付費 AI 影音生成作為必要條件。

安全與授權控管如下：

- 不上傳 API key、token、password 或私人帳號資訊。
- 不讓 agents 連接私人 email、calendar、雲端硬碟或社群帳號。
- 不使用未確認授權的商業音樂或影片素材。
- 若圖片中有可辨識人物，需確認來源為官方公開素材或已取得使用同意。
- 使用的官方參考來源與素材來源整理於 `outputs/asset_sources.md` 與 `outputs/user_image_sources_to_fill.md`。

## 9. Repository and Submission

本專案的 GitHub repository 應設定為 Public，並在 Ecourse 作業區提交完整 repo URL。Repo 內需包含：

- `outputs/final_video.mp4`
- `report/Final_Report_S11259035.pdf`
- `README.md`
- `agents/`
- `handoff/`
- `traces/execution_trace.md`
- `baseline/single_agent_baseline.md`
- `outputs/asset_sources.md`
- `SUBMISSION_CHECKLIST.md`

## 10. Reflection

本次作業的重點不是單純產生影片，而是設計一個可追蹤、可控制、可評估的多代理人影音製作流程。透過多個 agents 的分工，可以把企劃、字幕、分鏡、審查與整理拆成不同階段，讓整個製作過程比單一 prompt 更容易檢查與重現。

實作上的主要限制是：影片素材來源與人物肖像權仍需要人工確認；若加入背景音樂，也需要記錄音樂來源與授權。未來若有更多時間，可以加入實際 OpenClaw 執行畫面或更完整的素材授權截圖，使 execution trace 更接近真實平台執行紀錄。

