# Research notes — Agentic Coding guide (grounding, có dẫn nguồn)

> Mục đích: nền tảng KHÁCH QUAN, chống hype cho tài liệu dạy agentic coding. Full transcript: agent://VibeHistory, agent://ToolLandscape, agent://AutonomyLevels, agent://ProductivityEvidence.

## 1. Lịch sử: vibe coding → agentic coding
- "Vibe coding" do **Andrej Karpathy** đặt ra trong tweet **2/2/2025** (Cursor Composer + Sonnet + SuperWhisper voice). Định nghĩa gốc: "fully give in to the vibes... forget that the code even exists." Là phong cách hobby, KHÔNG phải production. [x.com/karpathy/status/1886192184808149383]
- Collins Dictionary chọn "vibe coding" = Word of the Year 2025; Merriam-Webster WoY 2025 = "slop". [blog.collinsdictionary.com]
- Vibe coding phá 3 quy ước của autocomplete-era: không đọc diff, không cần hiểu code, không giữ authorship. [klover.ai]
- Anthropic 2026 Agentic Coding Trends: "2024 = inline autocomplete; 2026 = autonomous execution — describe task, agent executes across files." [resources.anthropic.com/2026-agentic-coding-trends-report]
- Timeline: Copilot preview 6/2021 → ChatGPT 11/2022 → Claude 3/2023 → Devin 3/2024 (13.86% SWE-Bench) → Claude Code preview 10/2024 → "vibe coding" 2/2025 → Claude Code 2.0 9/2025 → Karpathy retrospective 2/2026 đề xuất "agentic engineering". [en.wikipedia.org/wiki/GitHub_Copilot, thinkml.ai]

## 2. Landscape tool + triết lý (4 nhóm theo autonomy)
- 4 nhóm: **Autocomplete** (suggestion-only) → **IDE-embedded agent** (multi-file, approval loop) → **CLI agent** (terminal-native, composable) → **Autonomous agent** (end-to-end). Ranh giới đang mờ dần. [swarmia.com/blog/five-levels-ai-agent-autonomy]
- **Claude Code**: single-threaded master loop (codename "nO"), CHỦ ĐÍCH tránh multi-agent swarm để ưu tiên debuggability; triết lý "do the simple thing first"; composable kiểu Unix; dev defines goal, reviews result. Launch 2/2025. [zenml.io/llmops-database/claude-code-agent-architecture, anthropic.com/product/claude-code]
- **Aider**: git-native (mỗi edit = 1 atomic commit), open-source, model-agnostic, Architect/Editor separation. [aider.chat/2024/09/26/architect.html]
- **OpenHands** (ex-OpenDevin): open-source, ICLR 2025, kiến trúc CodeAct, ~77% SWE-Bench Verified; "agentic tech quá quan trọng để vài công ty kiểm soát". [arxiv.org/abs/2407.16741]
- **Cursor**: developer-as-orchestrator (Cursor 3 agent-first). **Cline**: approval-first ("inference không nên là business model"). **Devin** (Cognition): autonomous SWE — đã mua Windsurf → Devin Desktop 2026. **Qodo** (CodiumAI): quality/test-first, multi-agent review. [infoq.com, cline.bot, devin.ai/desktop]
- LƯU Ý: Codeium (→Windsurf) ≠ CodiumAI (→Qodo) — hai công ty khác nhau.

## 3. Khung level đã công bố (grounding cho trục AUTONOMY)
Đồng thuận: **5–6 bậc**; cực thấp = AI chỉ suggest; cực cao = full autonomy còn risky/lý thuyết; **higher ≠ better** (autonomy là design choice); human oversight nghịch chiều autonomy; SAE J3016 là analogon phổ biến.

- **CSA 6-level** (Jim Reavis, 1/2026), trục = human control còn lại: L0 No Autonomy → L1 Assisted → L2 Supervised → L3 Conditional → L4 High → L5 Full ("not appropriate for enterprise today"). [cloudsecurityalliance.org/blog/2026/01/28/levels-of-autonomy]
- **Knight First Amendment 5-level** (Feng & McDonald, 7/2025, arXiv 2506.12469), trục = vai trò user: Operator → Collaborator → Consultant → Approver → Observer. Insight: autonomy tách biệt khỏi capability. [arxiv.org/abs/2506.12469]
- **Swarmia 5-level (coding-specific)** (3/2026), trục = agent làm bao nhiêu trước khi quay lại xin feedback: L1 Assistive (autocomplete) → L2 Conversational (chat pair) → L3 Task agent (assign→PR) → L4 Autonomous teammate (tự chọn task) → L5 Agentic avalanche (multi-agent orchestration). [swarmia.com/blog/five-levels-ai-agent-autonomy]
- **ELEKS AI-SDLC maturity** (2/2026, góc tổ chức): Traditional → AI-Supported → AI-Assisted → AI-Native → AI-Autonomous. [eleks.com/blog/ai-sdlc-maturity-model]
- Anthropic/GitHub/Microsoft KHÔNG có thang level chính thức có tên bậc.

## 4. Bằng chứng hiệu quả/năng suất (anti-hype)
- **METR RCT 2025**: dev open-source giỏi dùng AI **CHẬM hơn 19%** (CI [+2%,+39%]); tự dự đoán nhanh hơn 24% → gap nhận thức ~43 điểm %. n=16, 246 task, mature repos. [metr.org/blog/2025-07-10-..., arxiv.org/abs/2507.09089]
- **Copilot lab (Peng 2023)**: nhanh hơn 55.8% — nhưng task đơn giản, lab, Microsoft-funded; ANZ Bank real-world chỉ 42%. [arxiv.org/abs/2302.06590]
- **DORA 2025** (n~5000): adoption 90%; AI **khuếch đại** — throughput↑ nhưng stability↓ nếu thiếu automated testing; chỉ 24% "trust a lot". "AI không fix team yếu." [dora.dev/dora-report-2025]
- **Stack Overflow 2025**: adoption 76%→84% nhưng trust 40%→29%; 45% bực vì "almost right but not quite"; 66% tốn thêm thời gian debug AI code. [survey.stackoverflow.co/2025/ai]
- **GitClear 2024-25** (211M dòng): churn 3.1%→5.7%; copy-paste 8.3%→12.3%; refactor 25%→<10% (lần đầu copy-paste > refactor). [gitclear.com/ai_assistant_code_quality_2025_research]
- **Bảo mật**: code AI có vulnerability density cao **2.7x**; 30-62% có lỗ hổng. [arxiv.org/abs/2404.18353, veracode.com]
- **Junior vs senior**: junior +21-52%, senior +7-16%, task phức tạp <10% gain. [mckinsey.com]
- **Metric ĐÁNG TIN** (không hype): code churn rate, change failure rate, lead time for changes, defect escape rate, security vuln density (DORA/SPACE). Tránh metric "typing speed / lines generated".

## 5. Thang level đề xuất (tổng hợp, trục = autonomy, có grounding)
Hợp nhất Swarmia (coding) + CSA + Knight (role) + SAE analogy; mỗi bậc gắn metric DORA/SPACE; nhấn "right level cho từng task, không phải càng cao càng tốt".

| Bậc | Tên | Agent làm gì | Vai trò người | Tool tiêu biểu | Rủi ro/Metric cần canh |
|----|-----|-------------|---------------|----------------|------------------------|
| L0 | Manual | Không AI | Author | — | baseline |
| L1 | Assistive | Autocomplete từng dòng | Operator | Copilot inline | churn thấp |
| L2 | Conversational | Chat, multi-file, duyệt từng bước | Collaborator | Claude Code cơ bản, Cursor chat | review từng diff |
| L3 | Task delegation (Conductor) | Nhận task → plan → sửa nhiều file → mở PR | Approver (duyệt kết quả) | Claude Code agentic + **OMC cơ bản**, Copilot coding agent | CFR, defect escape |
| L4 | Orchestration / pipeline | Nhiều agent song song + quality gate | Designer/Approver | **OMC Autopilot/Team/Ralph**, oh-my-pi | churn, stability, lead time |
| L5 | Autonomous teammate | Tự chọn task, self-improving loop | Observer | frontier (risky) | "not enterprise-ready" (CSA) |

Thesis chống hype: hiệu quả = chọn ĐÚNG bậc autonomy cho task + guardrail (test, review, spec rõ), đo bằng DORA/SPACE — KHÔNG phải "càng tự chủ càng năng suất" (METR, DORA, GitClear chứng minh ngược lại nếu thiếu kỷ luật).
