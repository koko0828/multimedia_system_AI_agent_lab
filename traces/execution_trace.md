# Execution Trace

This trace demonstrates a zero-paid-token OpenClaw-style multi-agent workflow using mock/stub outputs. The goal is to show controlled agent design, structured handoff, reproducible decision flow, and a complete final video without requiring paid API tokens.

## Run Metadata

- Project: NUTN CSIE 60-second promotional video
- Student: 黃可瑜
- Student ID: S11259035
- Platform style: OpenClaw-style controlled multi-agent workflow
- Execution mode: zero-paid-token mock/stub execution
- Editing tool: CapCut
- Final video: `outputs/final_video.mp4`
- Final video duration: 63 seconds
- Final subtitle file: `outputs/subtitles_by_image_capcut_utf8.srt`

## Step 1: User Input

Input:

- Topic: 國立臺南大學資訊工程學系 60 秒形象宣傳影片
- Student name: 黃可瑜
- Student ID: S11259035
- Official reference URL: https://csie.nutn.edu.tw/cht/index/
- Editing tool: CapCut
- User-provided visual materials: `圖片/`

Output:

- Task accepted by Planner Agent.

## Step 2: Planner Agent

Input files:

- Assignment requirements
- User input
- Official CSIE reference URL

Output file:

- `handoff/01_planner_output.json`

Summary:

Planner defined the target audience, core message, six-scene video structure, asset policy, and downstream agent task list.

## Step 3: Script Agent

Input files:

- `handoff/01_planner_output.json`
- User-provided images in `圖片/`

Output files:

- `handoff/02_script_output.json`
- `outputs/subtitles_by_image_capcut_utf8.srt`

Summary:

Script Agent revised the narration into an image-matched subtitle sequence. The final subtitles describe the actual visuals: department introduction, curriculum areas, circuit practice, laboratory measurement, oscilloscope observation, project exhibition, presentation, and department activities.

## Step 4: Visual Agent

Input files:

- `handoff/01_planner_output.json`
- `outputs/subtitles_by_image_capcut_utf8.srt`
- User-provided images in `圖片/`

Output files:

- `handoff/03_visual_output.json`
- `capcut/image_matched_subtitle_timeline.md`
- `capcut/capcut_step_by_step_with_user_images.md`

Summary:

Visual Agent converted the user-provided images into a CapCut timeline. Each image group was matched with subtitle timing and suggested motion effects such as slow zoom, pan, and fade transitions.

## Step 5: Reviewer Agent

Input files:

- `handoff/01_planner_output.json`
- `handoff/02_script_output.json`
- `handoff/03_visual_output.json`
- `outputs/asset_sources.md`
- `outputs/user_image_sources_to_fill.md`

Output file:

- `handoff/04_reviewer_feedback.json`

Summary:

Reviewer checked assignment compliance, video length target, subtitle requirement, truthfulness, copyright, portrait rights, and zero-paid-token feasibility. The main remaining manual risk is confirming the source/permission status for images containing identifiable people.

## Step 6: Finalizer Agent

Input files:

- `handoff/04_reviewer_feedback.json`
- Final exported video

Output file:

- `handoff/05_finalizer_output.json`

Summary:

Finalizer organized the final repository files and submission checklist. The final exported video was copied to `outputs/final_video.mp4`.

## Final Video Verification

| Item | Result |
|---|---|
| File path | `outputs/final_video.mp4` |
| Format | MP4 |
| Duration | 63 seconds |
| Assignment range | 55-65 seconds |
| File size | about 38.91 MB |
| Subtitle file | `outputs/subtitles_by_image_capcut_utf8.srt` |

## Traceability

| Final Video Decision | Source |
|---|---|
| Project topic and audience | `handoff/01_planner_output.json` |
| Image-matched subtitles | `outputs/subtitles_by_image_capcut_utf8.srt` |
| Image-to-subtitle timeline | `capcut/image_matched_subtitle_timeline.md` |
| CapCut editing instructions | `capcut/capcut_step_by_step_with_user_images.md` |
| Risk control | `handoff/04_reviewer_feedback.json` |
| Final repo checklist | `SUBMISSION_CHECKLIST.md` |

