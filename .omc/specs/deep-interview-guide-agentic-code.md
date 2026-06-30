# Deep Interview Spec: Hướng dẫn Agentic Coding (tiếng Việt)

## Metadata
- Interview ID: di-20260630-guide-agentic-code
- Rounds: 5 (Round 0 topology + 4 vòng chấm điểm)
- Final Ambiguity Score: ~15%
- Type: greenfield
- Generated: 2026-06-30
- Threshold: 0.2
- Threshold Source: default
- Initial Context Summarized: no
- Status: PASSED
- Research notes: `.omc/research/agentic-coding/notes.md` (full transcript: agent://VibeHistory, agent://ToolLandscape, agent://AutonomyLevels, agent://ProductivityEvidence)

## Clarity Breakdown
| Dimension | Score | Weight | Weighted |
|-----------|-------|--------|----------|
| Goal Clarity | 0.90 | 0.40 | 0.36 |
| Constraint Clarity | 0.80 | 0.30 | 0.24 |
| Success Criteria | 0.85 | 0.30 | 0.255 |
| **Total Clarity** | | | **0.855** |
| **Ambiguity** | | | **0.145** |

## Topology
Tài liệu = 1 file markdown tiếng Việt, theo mạch kể chuyện qua 5 thành phần. Không defer phần nào.

| Component | Status | Description | Coverage |
|-----------|--------|-------------|----------|
| c1 — Bối cảnh & lịch sử | active | vibe→agentic coding + landscape tool | AC #2, #3, #8 |
| c2 — Triết lý cốt lõi | active | "tool chỉ là phương tiện"; triết lý tạo hiệu quả | AC #2, #4 |
| c3 — Giới thiệu tool | active | OMC đi sâu + oh-my-pi sơ lược | AC #4, #7 |
| c4 — Hệ thống level (autonomy) | active | thang 6 bậc L0-L5, right-level, chống hype | AC #5, #6, #8 |
| c5 — Hướng dẫn dùng OMC | active | hands-on dựa trên #execution-modes | AC #6 |

## Goal
Viết MỘT tài liệu dạy bằng **tiếng Việt** (1 file markdown, hands-on) đưa người đọc — **dev đã dùng Claude Code/Cursor và muốn nâng cao** — đi theo mạch: hiểu *bối cảnh* (vibe coding → agentic coding), *triết lý* (công cụ chỉ là phương tiện; tư duy điều phối mới tạo hiệu quả), *các công cụ* (oh-my-claudecode là trọng tâm, oh-my-pi giới thiệu sơ), *tự định vị* trên thang 6 bậc autonomy đo bằng năng suất thực (không phải hype), và *thực hành* dùng oh-my-claudecode hiệu quả. Mọi tuyên bố quan trọng phải có dẫn nguồn; giọng văn chống hype, dựa trên bằng chứng.

## Constraints
- Ngôn ngữ: tiếng Việt; thuật ngữ kỹ thuật giữ tiếng Anh.
- Định dạng: 1 file markdown dài (đề xuất `docs/guide-agentic-code.md`), đọc tuyến tính theo 5 phần.
- Hands-on: phần hướng dẫn OMC phải có command/workflow thực chiến (autopilot, ralph, ulw, team, plan, deep-interview) + khi nào dùng cái nào.
- Audience đã biết code và đã dùng AI assist/agent cơ bản → KHÔNG dạy lập trình vỡ lòng, ít giải thích khái niệm cơ bản.
- Trục thang level = **mức tự chủ của agent (autonomy)**, grounding theo khung đã công bố (Swarmia/CSA/Knight/SAE).
- Mọi số liệu/tuyên bố phải kèm nguồn URL (xem research notes).
- oh-my-pi chỉ là 1 mục ngắn, không lấn át OMC.

## Non-Goals
- KHÔNG phải hướng dẫn cài đặt chi tiết từng OS (chỉ trỏ về docs OMC chính thức).
- KHÔNG dạy lập trình cơ bản hay cú pháp ngôn ngữ.
- KHÔNG review/so sánh sâu từng tool (landscape chỉ đủ để định vị triết lý).
- KHÔNG kèm bài tập/checklist tự đánh giá per-level (đã chọn right-level mô tả, không phải dạng khóa học).
- KHÔNG tách nhiều file / dạng khóa học (đã chốt 1 file).
- KHÔNG tô hồng: phải nêu cả bằng chứng phản biện.

## Acceptance Criteria
- [ ] AC1: Tài liệu là 1 file markdown tiếng Việt (đề xuất `docs/guide-agentic-code.md`).
- [ ] AC2: Có đủ 5 phần theo mạch kể: (1) bối cảnh, (2) triết lý, (3) tool, (4) hệ thống level, (5) hướng dẫn OMC hands-on.
- [ ] AC3: Phần bối cảnh nêu mốc Karpathy 2/2/2025, timeline autocomplete→vibe→agentic, Anthropic 2026 trends; có dẫn nguồn.
- [ ] AC4: Phần triết lý nêu rõ "tool là phương tiện" + triết lý conductor/delegation (Claude Code "do the simple thing first", single-threaded loop) + đối chiếu triết lý vài tool khác (Aider git-native, Cline approval-first, Devin autonomous, OpenHands open-source).
- [ ] AC5: Phần level trình bày thang 6 bậc L0-L5 (trục autonomy), đặt Claude Code/OMC/oh-my-pi lên thang, mỗi bậc kèm: agent làm gì + vai trò người (Operator→Observer) + tool tiêu biểu + metric DORA/SPACE + dấu hiệu nhận biết. Thông điệp: **chọn đúng bậc cho task + guardrail**, KHÔNG leo tối đa.
- [ ] AC6: Phần hướng dẫn OMC có command thực chiến (autopilot/ralph/ulw/team/plan/deep-interview) dựa trên #execution-modes + model routing Haiku/Sonnet/Opus + conductor philosophy + delegation rules; oh-my-pi 1 mục ngắn.
- [ ] AC7: Mọi tuyên bố định lượng (METR −19%, Copilot 55.8%, DORA, churn 3.1%→5.7%, vuln 2.7x...) đều có dẫn nguồn URL.
- [ ] AC8: Giọng anti-hype — nêu cả bằng chứng phản biện (METR, DORA, GitClear, security), gắn "hiệu quả" với metric đáng tin (churn, CFR, lead time, defect escape), không phải "lines generated / typing speed".

## Assumptions Exposed & Resolved
| Assumption | Challenge | Resolution |
|------------|-----------|------------|
| Chỉ nói về OMC/Claude Code | Round 0: scope thật rộng hơn | Mở rộng: landscape + triết lý chung; OMC là ví dụ trọng tâm vì dễ dùng |
| Level đo theo "performer→conductor" (chủ quan) | Round 1: cần khách quan | Chốt trục = autonomy; cử research grounding theo khung công bố |
| Tự "vẽ" thang level | User: "không kết luận chủ quan" | Grounded theo Swarmia/CSA/Knight/SAE + metric DORA/SPACE, có dẫn nguồn |
| Tài liệu hướng leo lên bậc cao nhất | Round 4 Contrarian: cao hơn ≠ tốt hơn (METR/DORA/GitClear) | Thông điệp = right-level + guardrail, không leo tối đa |
| oh-my-pi ngang hàng OMC | Round 0 follow-up | oh-my-pi chỉ giới thiệu sơ; OMC là trọng tâm vì dễ dùng |

## Technical Context (grounding — đầy đủ trong `.omc/research/agentic-coding/notes.md`)
- **Lịch sử:** "vibe coding" — Karpathy tweet 2/2/2025; Collins WoY 2025; Anthropic 2026 trends (2024 autocomplete → 2026 autonomous execution).
- **Tool & triết lý:** 4 nhóm (autocomplete→IDE agent→CLI agent→autonomous). Claude Code: single-threaded master loop "nO", "do the simple thing first", Unix-composable. Aider git-native; Cline approval-first; OpenHands open-source (ICLR 2025, ~77% SWE-Bench); Devin autonomous (đã mua Windsurf→Devin Desktop); Cursor orchestrator; Qodo quality-first.
- **Khung level đã công bố:** CSA 6-level; Knight First Amendment 5-level (Operator→Observer); Swarmia 5-level coding-specific; ELEKS maturity; SAE J3016 analogy. Đồng thuận 5-6 bậc; "higher ≠ better".
- **Anti-hype evidence:** METR 2025 (−19% với dev giỏi), Copilot lab 55.8% (giảm còn ~42% real-world), DORA 2025 (AI khuếch đại, stability↓), Stack Overflow 2025 (trust↓), GitClear (churn↑, refactor↓), security (vuln 2.7x). Metric đáng tin: churn, CFR, lead time, defect escape.
- **Thang level đề xuất (chốt):**

| Bậc | Agent làm gì | Vai trò người | Tool tiêu biểu | Metric canh |
|----|-------------|---------------|----------------|-------------|
| L0 Manual | không AI | Author | — | baseline |
| L1 Assistive | autocomplete từng dòng | Operator | Copilot inline | churn |
| L2 Conversational | chat, multi-file, duyệt từng bước | Collaborator | Claude Code cơ bản, Cursor chat | review diff |
| L3 Delegation (Conductor) | task→plan→sửa nhiều file→PR | Approver | Claude Code agentic + OMC cơ bản | CFR, defect escape |
| L4 Orchestration | đa agent song song + quality gate | Designer/Approver | OMC Autopilot/Team/Ralph, oh-my-pi | churn, stability, lead time |
| L5 Autonomous | tự chọn task, self-improving | Observer | frontier (risky, "not enterprise-ready") | — |

- **Nguồn OMC #execution-modes:** Autopilot (idea→code tự động), Ralph ("boulder never stops", persistence + verify), Ultrawork (song song ≤5+ agents), Team (staged pipeline plan→prd→exec→verify→fix). Conductor philosophy: "You are the conductor, not the performer". Model routing Haiku/Sonnet/Opus. Magic keywords. Delegation rules.

## Ontology (Key Entities) — từ vòng cuối
| Entity | Type | Fields | Relationships |
|--------|------|--------|---------------|
| AgenticCoding | core domain | định nghĩa, mốc 2024→2026 | tiến hóa từ VibeCoding |
| VibeCoding | core domain | nguồn gốc Karpathy 2/2/2025 | tiền thân của AgenticCoding |
| Tool | core domain | category, triết lý, autonomy | hiện thực hóa AutonomyLevel |
| AutonomyLevel | core domain | bậc L0-L5, axis=autonomy | gắn HumanRole, ProductivityMetric |
| Agent | supporting | model tier, vai trò | thực thi trong Tool |
| HumanRole | supporting | Operator→Observer | nghịch chiều AutonomyLevel |
| ProductivityMetric | supporting | churn, CFR, lead time, defect escape | đo hiệu quả mỗi AutonomyLevel |
| Guardrail | supporting | test, review, spec | điều kiện lên bậc |

## Ontology Convergence
| Round | Entity Count | New | Changed | Stable | Stability Ratio |
|-------|-------------|-----|---------|--------|----------------|
| 1 | 7 | 7 | - | - | N/A |
| 2 | 8 | 1 | 2 | 5 | 87.5% |
| 3 | 8 | 0 | 0 | 8 | 100% |

## Interview Transcript
<details>
<summary>Full Q&A (Round 0 + 4 vòng)</summary>

### Round 0 — Topology
**Q:** Topology 4 phần đúng chưa? Thêm/bớt/gộp/defer?
**A:** Option 2 (mạch kể). Mở rộng cả giới vibe/agentic coding; "tool chỉ là tool"; thị trường nhiều tool, triết lý là gì. Có dùng oh-my-pi (giới thiệu sơ). Level nghiên cứu kỹ theo hiệu quả/năng suất, không hype. Trọng tâm = oh-my-claudecode vì dễ dùng hơn; oh-my-pi chỉ là phần thêm ngắn.

### Round 1 — Trục thang level (Goal)
**Q:** Level đo theo trục nào, bao nhiêu bậc?
**A:** Trục theo mức tự chủ của agent (autonomy). Cần agent nghiên cứu để không kết luận chủ quan.
**Ambiguity:** 59%

### Round 2 — Audience (Constraints)
**Q:** Người đọc mục tiêu là ai, đã biết gì?
**A:** Dev đã dùng Claude Code/Cursor, muốn nâng cao.
**Ambiguity:** 42%

### Round 3 — Định dạng & độ sâu (Constraints)
**Q:** Tài liệu ở định dạng nào, sâu tới đâu?
**A:** 1 file markdown dài, hands-on có command examples.
**Ambiguity:** 28%

### Round 4 — Thông điệp level (Success Criteria, Contrarian)
**Q:** Thông điệp cốt lõi phần level? Chốt thang 6 bậc?
**A:** Chọn ĐÚNG bậc + guardrail (right-level), không leo tối đa. Giữ thang 6 bậc L0-L5, đặt tool lên thang, mỗi bậc kèm metric + dấu hiệu nhận biết.
**Ambiguity:** 15% ✅

</details>
