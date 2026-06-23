# Single-agent Baseline

## Baseline Prompt

請用單一 prompt 幫我規劃一支 60 秒「國立臺南大學資訊工程學系形象宣傳影片」，內容包含主題、旁白、分鏡、素材與剪輯方式。

## Baseline Output Summary

單一 agent 通常可以一次產生完整企劃，但容易出現下列問題：

- 影片企劃、腳本、分鏡、審查混在同一份輸出中，不容易追蹤每個決策來源。
- 可能忽略版權、肖像權、官方資訊真實性與 zero-paid-token 限制。
- 若內容太長，沒有明確角色負責壓縮成 60 秒。
- 缺少 structured handoff，助教較難確認這是 multi-agent workflow。

## Multi-agent Workflow Comparison

| Evaluation Item | Single-agent Baseline | Multi-agent Workflow |
|---|---|---|
| Task decomposition | One prompt handles all tasks | Planner, Script, Visual, Reviewer, Finalizer have separate roles |
| Traceability | Hard to trace decisions | Each step has JSON/Markdown handoff |
| 60-second control | May produce too much text | Script Agent writes timed subtitle segments |
| Visual planning | Often general | Visual Agent produces CapCut timeline and fallback shots |
| Risk checking | Easy to miss | Reviewer checks truthfulness, copyright, portrait rights, and token cost |
| Zero-paid-token feasibility | May assume AI tools | Workflow explicitly supports mock/stub agents and CapCut editing |
| Submission readiness | Requires extra organization | Finalizer creates repo checklist and final file map |

## Conclusion

The multi-agent workflow is better for this assignment because it provides clearer responsibility boundaries, structured evidence, traceable handoff files, and explicit review of cost, copyright, portrait rights, and truthfulness. The final video still requires manual CapCut editing, but the planning and documentation are reproducible without paid tokens.

