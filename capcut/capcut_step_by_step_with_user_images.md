# CapCut Step-by-step Guide Using Current Images

This guide uses the images in `圖片/` to produce a 60-second NUTN CSIE promotional video.

## Are These Images Enough?

Yes. The current image set is enough for a 55-65 second video because it includes:

- department/course overview images
- hands-on circuit / lab practice photos
- oscilloscope and lab instrument photos
- project presentation photos
- project exhibition photos
- department meeting / group activity photos

The only risk is that several images contain recognizable people. If these photos come from an official public department source, record the URL in `outputs/user_image_sources_to_fill.md`. If they are personal photos, confirm permission before uploading the repo publicly.

## Recommended 60-second Timeline

| Time | Use These Images | Purpose | CapCut Action |
|---|---|---|---|
| 0-5s | `系所簡介.png` or `materials/candidate_images/official_csie_header_bg.png` | Opening department identity | Add title: 國立臺南大學資訊工程學系 |
| 5-11s | `3大領域學程.png` | Show learning structure | Crop/zoom so text is readable; add keywords overlay |
| 11-18s | `同學實作電路.jpg`, `實作電路板.jpg` | Show hands-on practice | 2 quick cuts, 3-4 seconds each |
| 18-28s | `實作電路板2.jpg`, `實驗室儀器.jpg` | Show systems/lab environment | Slow zoom and pan |
| 28-38s | `實驗室視波器.jpg`, `實驗室視波器2.jpg`, `實驗室視波器3.jpg`, `實驗室視波器4.jpg` | Show observation, debugging, verification | Use 2-3 of the clearest shots, avoid repeating too much |
| 38-49s | `畢業專題展.JPG`, `畢業專題同學講解.JPG`, `畢業專題同學講解2.JPG` | Show project presentation and communication | Use zoom-in on presenter/poster |
| 49-56s | `畢業專題上台報告.JPG`, `畢業專題上台報告2.JPG`, `資工系期中系大會報告.JPG` | Show sharing and learning community | Use one presentation shot and one wide classroom shot |
| 56-60s | `期中系大會2.JPG` or a clean title card | Closing | Add final department name and source note |

## Suggested CapCut Workflow

1. Create a new project in CapCut.
2. Set project ratio to 16:9.
3. Import all files from `圖片/` and the useful images from `materials/candidate_images/`.
4. Place images in the timeline according to the table above.
5. Set each image duration:
   - opening/title: 5 seconds
   - overview: 6 seconds
   - normal image: 3-5 seconds
   - final card: 4 seconds
6. Add animation to every still image:
   - use slow zoom-in for title, lab, and project images
   - use pan left/right for wide presentation photos
   - use quick fade or dissolve between sections
7. Import subtitles from `outputs/subtitles_by_image_capcut_utf8.srt`, or manually paste each subtitle line.
8. Add quiet background music from CapCut only if the license is acceptable.
9. Export as MP4, 1080p or 720p.
10. Confirm final duration is between 55 and 65 seconds.

## Image-matched Subtitle Version

The recommended subtitle file for the current image set is:

- `outputs/subtitles_by_image_capcut_utf8.srt`

The matching image-by-image timeline is:

- `capcut/image_matched_subtitle_timeline.md`

## Editing Tips

- Do not show tiny text screenshots for too long. Crop into the important area.
- Avoid using all oscilloscope images back-to-back; choose the clearest 2-3.
- For people photos, avoid awkward freeze frames. Use slow zoom and crop to focus on presentation/poster/activity.
- Add section labels such as "實作", "實驗", "專題", "分享" to make the story clearer.
- End with a source note: "素材來源詳見 GitHub repo / outputs/asset_sources.md".

## Minimum Version

If you want to finish quickly, use only these 10 images:

1. `系所簡介.png`
2. `3大領域學程.png`
3. `同學實作電路.jpg`
4. `實作電路板.jpg`
5. `實驗室儀器.jpg`
6. `實驗室視波器.jpg`
7. `畢業專題展.JPG`
8. `畢業專題同學講解.JPG`
9. `畢業專題上台報告.JPG`
10. `資工系期中系大會報告.JPG`
