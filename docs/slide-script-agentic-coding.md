# Kịch bản Slide: "Agentic Coding — Từ Vibe đến Điều phối hiệu quả"

> **Đây là bản bàn giao (handoff) cho agent/người tạo slide.** Không phải slide cuối, mà là **kịch bản đầy đủ**: mọi headline, nội dung, visual, bảng, diagram, speaker note và nguồn trích dẫn cần thiết đã được chốt sẵn. Việc còn lại của agent tạo slide là **dàn trang + thiết kế**, không phải biên tập nội dung.
>
> **Cân đối nội dung (đã chốt theo yêu cầu):** Phần 1–4 (bối cảnh/triết lý/công cụ/hệ thống level) là **nền dẫn nhập, cố ý gọn** — nén còn 9 slide. Phần 5 (hướng dẫn thực chiến `oh-my-claudecode`) là **trọng tâm của bài** — giữ đủ 10 slide, chi tiết nhất, có thêm 1 slide cheat-sheet lệnh để mang về dùng ngay.

---

## 0. Ghi chú bàn giao (đọc trước khi bắt đầu dựng slide)

- **Nguồn gốc nội dung:** toàn bộ số liệu, quote, bảng, mốc thời gian trong kịch bản này rút từ `docs/guide-agentic-code.md` (đã đọc toàn văn). **KHÔNG tự thêm số liệu, nguồn, hay case study mới** ngoài danh sách ở mục 8 (Nguồn tham khảo). Ví dụ minh họa thêm phải gắn nhãn **"(ví dụ minh họa, không phải số liệu thật)"**.
- **Ngôn ngữ:** tiếng Việt trên toàn bộ nội dung on-slide; giữ tiếng Anh cho thuật ngữ kỹ thuật/tên riêng (vibe coding, agentic coding, Claude Code, oh-my-claudecode, Ralph, Ultrawork, Autopilot, Team, churn, Change Failure Rate, autonomy, conductor/performer...).
- **Giọng điệu:** chống hype, dựa bằng chứng. Không dùng ngôn ngữ marketing ("cách mạng", "đột phá", "10x").
- **Quy mô:** 24 slide, thời lượng nói ~25–30 phút. Phần 5 (S11–S20, 10 slide) chiếm hơn 40% deck — cố ý, vì đây là phần hands-on người nghe áp dụng ngay.
- **Đối tượng nghe:** lập trình viên đã dùng Claude Code/Cursor hoặc agent coding tool nào đó, muốn nâng cấp cách dùng — không phải người mới học code.
- **Mỗi số liệu quan trọng PHẢI có citation hiện trên slide** (footer nhỏ, xem quy ước ở mục 1.4).

---

## 1. Hệ thống thiết kế (Design System)

### 1.1. Bảng màu đề xuất
| Vai trò | Màu | Dùng cho |
|---|---|---|
| Nền chính | Xanh navy đậm / than chì | Toàn bộ slide — cảm giác "phòng điều khiển" |
| Accent — Triết lý / Con người | Xanh ngọc/teal | Phần 2 (triết lý), motif "conductor" |
| Accent — Công cụ / Kỹ thuật | Tím/indigo | Phần 3 + Phần 5 (OMC, pipeline) |
| Accent — Bằng chứng / Số liệu | Vàng hổ phách + đỏ cam | Slide bằng chứng ngược hype (S09) |
| Accent — Tích cực có kiểm soát | Xanh lá nhạt | Slide "AI hiệu quả khi đúng chỗ" (trong S10) |
| Text | Trắng ngà / xám nhạt | Body text, tương phản cao trên nền đậm |

### 1.2. Motif hình ảnh xuyên suốt
1. **"Conductor & Orchestra"** — nhạc trưởng (con người) trước dàn nhạc (agent). Dùng ở: S04 (triết lý), S06 (OMC), S21 (đóng). Nhạc trưởng KHÔNG cầm nhạc cụ.
2. **"Autonomy dial"** — đồng hồ vòng cung 6 vạch L0→L5. Đặt góc dưới-phải các slide Phần 4 (S07–S10), callback ở S19–S20.
3. **"Timeline rail"** — đường kẻ ngang có mốc (dot), dùng cho S02.
4. **"Pipeline lane"** — dải băng chuyền ngang các ô nối tiếp, dùng cho S14 (autopilot) và S20 (cheat sheet).
5. **Icon set:** ⌨️ autocomplete · 💬 conversational · 🧭 conductor/delegation · 🕸️ orchestration · 🤖 autonomous · 🛡️ guardrail · 📉 bằng chứng tiêu cực · 📈 bằng chứng tích cực · ☕ người dùng đứng ngoài pipeline.

### 1.3. Quy ước bảng & diagram
- Bảng gốc render như **bảng thật**, không rút gọn thành bullet rời.
- 2 sơ đồ mermaid gốc (S03 landscape, S14 pipeline) giữ đúng thứ tự node, không bớt/thêm node.
- Slide dồn nhiều nội dung (do đã nén) → cho phép chữ nhỏ hơn / chia cột, nhưng **không cắt bớt số liệu**.

### 1.4. Quy ước citation on-slide
- Số liệu định lượng có footer nhỏ, góc dưới-trái: `Nguồn: <tên ngắn> — xem slide Nguồn tham khảo`.
- URL đầy đủ chỉ tập trung ở slide References (S22).

### 1.5. Font & tông chữ
- Headline: sans-serif đậm, tối đa ~8–10 từ.
- Body bullet: ngắn (≤ 12–14 từ/bullet).
- Số liệu nổi bật (%, x lần) luôn cỡ chữ lớn nhất trên slide, màu accent tương ứng.

---

## 2. Cấu trúc tổng thể

```
Mở đầu (S00–S01)
  → Phần 1: Bối cảnh — nén (S02–S03)
  → Phần 2: Triết lý — nén (S04–S05)
  → Phần 3: Công cụ — nén (S06)
  → Phần 4: Hệ thống level — nén (S07–S10)
  → Phần 5: Hướng dẫn thực chiến OMC — TRỌNG TÂM (S11–S20)
Đóng (S21–S23)
```

Tỷ trọng: Phần 1–4 = 9 slide (nền dẫn nhập) · Phần 5 = 10 slide (trọng tâm, có cheat-sheet lệnh riêng).

Luận điểm xuyên suốt (nhắc ở slide mở + slide đóng):
> "Công cụ chỉ là phương tiện. Cái quyết định năng suất không phải là *bạn để agent tự chủ tới đâu*, mà là *bạn chọn đúng mức tự chủ cho từng việc và đặt đủ guardrail*."

---

## 3. Mở đầu

### S00 — Slide tiêu đề
**Layout:** TITLE
**Headline:** "Agentic Coding: Từ Vibe đến Điều phối hiệu quả"
**Subhead:** "Cách dùng AI coding agent có hiệu quả và năng suất đo được — không phải hype"
**Nội dung phụ (nhỏ):** "Dành cho dev đã dùng Claude Code / Cursor — trọng tâm buổi này là dùng `oh-my-claudecode` thực chiến"
**Visual:** Motif Conductor & Orchestra làm background mờ.
**Speaker notes:** Nêu rõ ngay từ đầu: nền tảng (bối cảnh/triết lý/level) sẽ đi nhanh, phần chính là demo quy trình OMC thật.
**Nguồn:** —

### S01 — Agenda / Lộ trình (thể hiện rõ trọng tâm)
**Layout:** AGENDA
**Headline:** "Lộ trình: nền tảng gọn → thực hành sâu với `oh-my-claudecode`"
**Nội dung chính (5 mục — mục 5 chiếm diện tích lớn hơn hẳn 4 mục trước để báo hiệu tỷ trọng):**
1. 🕰️ Bối cảnh *(gọn)* — vibe coding → agentic coding
2. 🧭 Triết lý *(gọn)* — công cụ chỉ là phương tiện
3. 🛠️ Công cụ *(gọn)* — Claude Code + OMC là gì
4. 📊 Hệ thống level *(gọn)* — thang tự chủ, chống hype
5. 🎬 **Thực hành với `oh-my-claudecode` — TRỌNG TÂM** — một phiên làm việc thật, từng lệnh, từng quyết định, kèm cheat-sheet mang về

**Visual:** 5 ô ngang, ô số 5 to gấp ~2 lần 4 ô đầu, viền đậm nổi bật, badge "trọng tâm".
**Speaker notes:** Nói thẳng: 4 phần đầu là bối cảnh cần biết để hiểu *vì sao* làm theo cách ở phần 5, không phải nội dung chính.

---

## 4. Phần 1 — Bối cảnh (nén)

### S02 — Từ autocomplete đến "vibe coding"
**Layout:** TIMELINE (nén, không bảng dài)
**Headline:** "5 năm tiến hóa: autocomplete → chat → agent tự chủ"
**Timeline rail (6 mốc, mỗi mốc 1 dòng cực ngắn):**
- 06/2021 — Copilot preview → kỷ nguyên **autocomplete**
- 11/2022 — ChatGPT → code-qua-hội-thoại phổ cập
- 03/2024 — Devin 1.0 tự nhận "AI Software Engineer đầu tiên"
- 10/2024 — Claude Code preview → agent **terminal-native**
- **02/02/2025** — Karpathy đặt tên **"vibe coding"** *(mốc lớn nhất, nhấn riêng)*
- 2026 — Karpathy đề xuất "agentic engineering", phân biệt "vibe" (chơi) vs "engineering" (làm thật)

**Quote ngắn (Karpathy, giữ tiếng Anh):**
> "...fully give in to the vibes... forget that the code even exists." — Karpathy, 02/02/2025

**Dòng nhấn — giới hạn thẳng thắn:** Karpathy tự ghi rõ: dành cho **dự án cuối tuần/hobby**, "code mostly works" là đủ — **không phải quy trình production**. Collins Dictionary chọn "vibe coding" = Word of the Year 2025.
**Visual:** Timeline rail ngang 6 dot, dot 02/02/2025 to nhất/màu riêng.
**Speaker notes:** Đi nhanh — mục đích chỉ là định vị thuật ngữ, không đào sâu lịch sử.
**Nguồn:** GitHub Copilot (Wikipedia), Anthropic model timeline, Karpathy tweet gốc, Collins Dictionary.

### S03 — Agentic coding là gì + bản đồ thị trường
**Layout:** DIAGRAM (mermaid flow, giữ đúng 4 node) + quote ngắn
**Headline:** "Agentic coding = giữ ủy thác của vibe coding, gắn lại kỷ luật kỹ thuật"
**Quote Anthropic 2026 Agentic Coding Trends (ngắn gọn):**
> "2024 = inline autocomplete. 2026 = autonomous execution — describe a task, agent executes across multiple files... until the task is complete."

**Dòng tổng kết:** "code suggestion → steerable draft → intent delegation"
**Diagram (giữ đúng cấu trúc gốc, ví dụ rút gọn mỗi node còn 1–2 tên):**
```
[Autocomplete: Copilot] → [IDE-embedded agent: Cursor, Cline] → [CLI agent: Claude Code, Aider] → [Autonomous agent: Devin]
```
**Callout:** "Vị trí một công cụ trên trục này là **lựa chọn triết học**, không phải thước đo 'xịn hơn'."
**Visual:** Pipeline lane 4 ô, độ đậm màu tăng dần trái→phải.
**Speaker notes:** Chuyển ý sang Phần 2: cùng model nhưng khác triết lý sử dụng.
**Nguồn:** Anthropic 2026 Agentic Coding Trends Report; Swarmia (Five Levels of AI Agent Autonomy).

---

## 5. Phần 2 — Triết lý (nén)

### S04 — Nhạc trưởng, không phải nhạc công
**Layout:** QUOTE lớn, tối giản
**Headline:** "Bạn là nhạc trưởng, không phải nhạc công"
**Quote trung tâm (song ngữ, lớn nhất phần này):**
> "You are the conductor, not the performer." — triết lý cốt lõi của `oh-my-claudecode`

**Diễn giải (3 dòng):**
- Nhạc trưởng không chơi từng nốt — họ **định hướng, phân vai, kiểm tra**
- Tự sửa từng dòng → chậm chính mình; buông hoàn toàn (vibe thuần) → mất kiểm soát chất lượng
- **Hiệu quả nằm ở khoảng giữa** — Phần 4 cho thước đo để biết bạn đang ở đâu

**Visual:** Motif Conductor & Orchestra làm trung tâm — sẽ tái xuất hiện ở S06 và S21 để tạo mạch liên kết.
**Speaker notes:** Đây là câu định vị toàn bài — giữ nguyên tinh thần này khi vào Phần 5 (Golden Rule của OMC chính là câu này, đóng thành quy trình).
**Nguồn:** Triết lý `oh-my-claudecode`.

### S05 — Cùng model, triết lý đối nghịch
**Layout:** COMPARISON_TABLE (nén còn 4 dòng cốt lõi) + callout
**Headline:** "4 tool, 4 triết lý — trục control ↔ autonomy là lựa chọn có chủ đích"
**Nội dung chính (bảng rút gọn, giữ 4 dòng đại diện rõ nhất):**
| Công cụ | Triết lý cốt lõi | Hệ quả thiết kế |
|---|---|---|
| **Claude Code** | "Do the simple thing first" — vòng lặp đơn luồng, chủ đích tránh multi-agent swarm | Debuggability & minh bạch; dev định nghĩa goal, review kết quả |
| **Aider** | Git là source of truth & cơ chế an toàn | Mỗi edit = 1 atomic commit; tách Architect/Editor |
| **Cline** | "Inference không nên là business model" → approval-first | Người duyệt từng action |
| **Devin** (Cognition) | Autonomous software engineer | End-to-end, ít can thiệp |

**Callout (box nhỏ, gộp bài học + bẫy đặt tên):** Không có công cụ "đúng" tuyệt đối — thư viện chưa có test thì approval-first an toàn hơn full-autopilot, **bất kể model mạnh tới đâu**. ⚠️ *Bẫy đặt tên:* Codeium (→Windsurf→Devin Desktop) ≠ CodiumAI (→Qodo) — hai công ty khác nhau.
**Visual:** Bảng 4 dòng, tô màu nhẹ theo nhóm (control cao vs autonomy cao).
**Speaker notes:** Đi nhanh — chỉ cần khắc sâu 1 ý: mức tự chủ là lựa chọn thiết kế theo task, không phải cuộc đua.
**Nguồn:** ZenML/Anthropic, Aider docs, Cline blog, Devin.

---

## 6. Phần 3 — Công cụ (nén thành 1 slide)

### S06 — Claude Code → `oh-my-claudecode`: biến 1 agent thành dàn nhạc
**Layout:** BULLETS dày (3 khối) — đây là slide nền tảng duy nhất trước khi vào demo thật ở Phần 5
**Headline:** "Nền: Claude Code — Lớp điều phối: `oh-my-claudecode` — Điểm khác: `oh-my-pi`"
**Khối 1 — Claude Code (nền):** CLI agent terminal-native (preview 10/2024); "do the simple thing first" — vòng lặp đơn luồng đọc→sửa→chạy→tự kiểm, bạn duyệt kết quả. Mạnh, minh bạch — nhưng trần năng suất nằm ở chỗ là **một** agent.
**Khối 2 — `oh-my-claudecode` (lớp điều phối đa-agent chồng lên, KHÔNG thay thế):**
- **19 agent chuyên biệt** theo lane (exploration/planning/execution/verification/review/testing...), gắn model tier hợp lý (Haiku/Sonnet/Opus)
- **Execution modes:** Autopilot, Team, Ralph, Ultrawork, UltraQA
- **MCP tools:** LSP, AST grep, Python REPL, state/notepad/project-memory, model ngoài (Codex, Gemini)
- **Golden Rule:** *"NEVER make code changes directly. ALWAYS delegate to specialized agents."* — vai trò bạn là guide/review/orchestrate

**Khối 3 — `oh-my-pi` (giới thiệu sơ, 1 dòng):** Harness khác, cùng triết lý delegation-first, nhấn vào bộ tool tích hợp + song song hóa (AST/LSP/eval/browser/IRC). OMC dễ tiếp cận hơn cho người mới.
**Visual:** Từ vòng lặp đơn (icon Claude Code) nhân bản thành dàn "nhạc công" quanh 1 nhạc trưởng (lặp motif S04) — thể hiện "chồng lên, không thay thế".
**Speaker notes:** Đây là slide cuối của phần nền tảng — chuẩn bị trực tiếp cho Phần 5, nơi mọi khái niệm ở đây (agent, execution mode, golden rule) được thấy vận hành thật.
**Nguồn:** oh-my-claudecode docs (#execution-modes), anthropic.com/product/claude-code.

---

## 7. Phần 4 — Hệ thống level (nén)

### S07 — Thang 6 bậc tự chủ L0–L5 (bảng trung tâm)
**Layout:** LEVELS_TABLE — giữ đầy đủ, đây là bảng duy nhất của Phần 4 không bị nén
**Headline:** "Thang 6 bậc tự chủ — grounded trên Swarmia + CSA + Knight + SAE J3016 analogy"
**Ghi chú nhỏ dưới headline:** Tương tự SAE J3016 (6 cấp tự lái xe); hợp nhất từ 4 khung độc lập đã công bố (Swarmia coding-specific, CSA human-control, Knight vai trò người dùng, ELEKS maturity tổ chức) — đồng thuận: 5–6 bậc, **cao hơn KHÔNG đồng nghĩa tốt hơn**, autonomy là *design choice*.
**Nội dung chính (bảng đầy đủ, không nén):**
| Bậc | Agent làm gì | Vai trò bạn | Công cụ tiêu biểu | Metric phải canh |
|---|---|---|---|---|
| **L0 Manual** | Không AI | Author | — | (baseline) |
| **L1 Assistive** | Autocomplete từng dòng | Operator | Copilot inline | Code churn |
| **L2 Conversational** | Chat, sửa đa file, bạn duyệt từng bước | Collaborator | Claude Code cơ bản, Cursor chat | Review từng diff |
| **L3 Delegation (Conductor)** | Nhận task → tự plan → sửa nhiều file → mở PR; bạn duyệt kết quả | Approver | Claude Code agentic + **OMC cơ bản** | Change Failure Rate, defect escape |
| **L4 Orchestration** | **Nhiều agent song song** + quality gate | Designer/Approver | **OMC Autopilot/Team/Ralph**, oh-my-pi | Churn, stability, lead time |
| **L5 Autonomous** | Tự chọn task, self-improving | Observer | Frontier (Devin) — *rủi ro* | "not enterprise-ready" |

**Dấu hiệu tự định vị nhanh (footer, 1 dòng mỗi bậc):** đọc/sửa tay phần lớn code → L1–L2 · giao task rõ, review PR → L3 · thiết kế pipeline nhiều agent, chỉ duyệt cổng chất lượng → L4 · để agent tự chọn việc → L5 (cần lý do tốt + guardrail chặt).
**Visual:** Autonomy dial 6 vạch đặt cạnh bảng, đây là lần xuất hiện đầu và là điểm tham chiếu chính của cả deck (người nghe nên chụp lại slide này).
**Speaker notes:** Bảng để chụp lại. Phần 5 sẽ cho thấy chính xác OMC vận hành ở L3→L4 như thế nào.
**Nguồn:** Swarmia, CSA (cloudsecurityalliance.org), Knight (arXiv 2506.12469), ELEKS.

### S08 — Guardrail: điều kiện để lên bậc
**Layout:** BULLETS ngắn
**Headline:** "Cao hơn không tốt hơn — guardrail mới là điều kiện lên bậc"
**Nội dung chính:**
- Chỉ nên leo từ L_n lên L_{n+1} khi đã có: **(1)** test tự động bao quanh vùng agent đụng tới, **(2)** quy trình review (dù chỉ review kết quả), **(3)** spec/acceptance rõ
- Thiếu guardrail → bậc cao hơn chỉ **phóng đại rủi ro** (bằng chứng ở S09)
- L4 orchestration rực rỡ cho việc *song song, lặp lại, có test bao quanh*; L2 supervised đúng cho code *nhạy cảm, ít test, một-lần*

**Visual:** Autonomy dial với 3 "khóa" giữa mỗi vạch bậc, mở khi đủ 3 điều kiện.
**Speaker notes:** Câu chuyển: "vậy bằng chứng nào cho thấy thiếu guardrail là nguy hiểm?" → sang slide bằng chứng.

### S09 — Bằng chứng chống hype (nén thành 1 slide dày)
**Layout:** STAT_GRID (5 khối nhỏ, mật độ cao)
**Headline:** "Tự chủ cao hơn KHÔNG tự động cho năng suất cao hơn"
**Nội dung chính (5 khối, mỗi khối 2–3 dòng):**
- **METR RCT 2025** — 16 dev giỏi, 246 task: dùng AI **chậm hơn 19%** (CI [+2%,+39%]); tự nghĩ nhanh hơn 24% → gap nhận thức ~43 điểm %
- **DORA 2025** (~5.000 người) — AI là **chất khuếch đại**: throughput↑ nhưng **stability↓** nếu thiếu test tự động; chỉ 24% "tin tưởng nhiều"
- **GitClear** (211M dòng) — churn **3.1%→5.7%**, copy-paste **8.3%→12.3%**, refactor **25%→<10%** (lần đầu copy-paste vượt refactored)
- **Bảo mật** — code AI có vulnerability density cao hơn **~2.7×**; 30–62% chứa lỗ hổng
- **Stack Overflow 2025** — adoption 76%→84% nhưng **trust 40%→29%**; 66% tốn thêm thời gian debug code AI

**Visual:** 5 ô stat nhỏ xếp lưới, tông đỏ cam/vàng thống nhất, icon 📉 chung.
**Speaker notes:** Dừng lâu ở dòng "copy-paste vượt refactored" — câu dễ ấn tượng nhất.
**Nguồn:** metr.org / arXiv 2507.09089; dora.dev; gitclear.com; arXiv 2404.18353, veracode.com; survey.stackoverflow.co/2025/ai.

### S10 — Mặt khác + metric đáng tin + kết luận
**Layout:** BULLETS (2 khối: tích cực có kiểm soát + metric)
**Headline:** "AI hiệu quả khi đúng chỗ — đo bằng metric hệ thống, không phải cảm giác nhanh"
**Khối 1 — mặt tích cực (tông xanh lá, đối trọng với S09):**
- Copilot lab: nhanh hơn **55.8%** trên task đơn giản — giảm còn **~42%** ở real-world (Peng 2023)
- **Junior +21–52%**, **senior +7–16%**; task càng phức tạp lợi ích càng tiệm cận **<10%** (McKinsey)

**Khối 2 — metric đáng tin (bảng rút gọn 5 dòng thành list):**
Code churn rate · Change Failure Rate · Lead time for changes · Defect escape rate · Security vuln density — tất cả từ khung DORA/SPACE, **tránh** "số dòng sinh ra / tốc độ gõ".

**Kết luận thực dụng (box đậm, đóng cả Phần 4):**
"Mỗi bậc autonomy là một công cụ. Leo lên L4/L5 mà thiếu guardrail = đúng công thức tạo churn và lỗ hổng mà nghiên cứu trên đo được."
**Visual:** Đổi tông sang xanh lá ở khối 1 để tương phản với S09; box kết luận nổi bật ở đáy.
**Speaker notes:** Câu chuyển sang Phần 5: "Giờ xem guardrail này vận hành thật thế nào trong một việc cụ thể."
**Nguồn:** arXiv 2302.06590 (Peng 2023); McKinsey.

---

## 8. Phần 5 — Hướng dẫn thực chiến `oh-my-claudecode` (TRỌNG TÂM)

### S11 — Divider Phần 5 (trọng tâm, có trọng lượng thị giác riêng)
**Layout:** DIVIDER lớn, khác hẳn tông các divider trước (nếu có) — đây là slide "vào thân bài"
**Headline:** "Phần 5 — Một phiên làm việc thật: thêm đăng nhập Google (OAuth) vào REST API Node.js"
**Badge góc trên:** "TRỌNG TÂM BUỔI TRÌNH BÀY"
**Note setup (nhỏ, dạng "cài 1 lần rồi quên"):**
`/plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode` → `/plugin install oh-my-claudecode` → `/omc-setup`. Cần `team`/model ngoài → cần **tmux** + `npm i -g @openai/codex @google/gemini-cli`; `/omc-doctor` báo thiếu gì.
**Dòng nhấn:** Từ đây bạn không gõ cú pháp — bạn **mô tả ý định**, hook OMC bắt keyword và tự gọi skill đúng.
**Bối cảnh việc:** **Brownfield** — code đã có, đụng vào là có rủi ro.
**Visual:** Số "5" chiếm gần hết chiều cao slide, đậm hơn hẳn số "1–4" đã dùng trước đó (nếu giữ số phần ở các divider); icon nhân vật nhỏ (bạn = nhạc trưởng) xuất hiện, sẽ di chuyển qua từng "cảnh" tiếp theo.
**Speaker notes:** Đánh dấu rõ chuyển nhịp: từ đây trình bày sẽ chậm và chi tiết hơn hẳn 10 slide trước.

### S12 — Cảnh 1: Ý tưởng còn mơ hồ, đừng code vội
**Layout:** NARRATIVE_SCENE
**Headline:** "Cảnh 1 — `deep-interview`: hỏi 'bạn đang ngầm giả định gì', không hỏi 'bạn muốn gì'"
**Command gõ vào:**
```
deep interview: thêm đăng nhập Google vào API
```
**Nội dung chính:**
- Một câu 10 từ — giao thẳng cho AI, nó sẽ **đoán**: session hay JWT? có refresh token? user trùng email xử lý sao? Mỗi cú đoán sai = 1 vòng rework
- Chốt **hình dạng việc** trước (Round 0 — topology): "3 mảnh độc lập — luồng OAuth với Google, lưu/khớp user, phát token cho client. Đúng chưa?"
- Mỗi vòng sau nhắm mảnh **mờ nhất**, hỏi đúng 1 câu, hiện **ambiguity** giảm dần: `59% → 42% → 28% → 15%`
- Dưới ngưỡng (mặc định 20%) → dừng hỏi, kết tinh **spec** vào `.omc/specs/`

**Callout nhỏ:** Bug chưa rõ nguyên nhân → `/deep-dive` (truy vết song song, tự nạp phát hiện vào phiên deep-interview).
**Visual:** Đồ thị giảm dần 4 điểm (59→42→28→15%) là yếu tố thị giác chính.
**Speaker notes:** Liên kết ngược S09: đây chính là tinh thần METR — spec tốt là cách chống-rework rẻ nhất.

### S13 — Cảnh 2: Từ spec thành kế hoạch bị thách thức
**Layout:** NARRATIVE_SCENE
**Headline:** "Cảnh 2 — `ralplan`: một hội đồng 3 người tranh luận cách làm"
**Command gõ vào:**
```
ralplan
```
**Nội dung chính:**
- 3 vai: **Planner** dựng bước → **Architect** soi ranh giới hệ thống, đánh đổi dài hạn → **Critic** đập lại ("user đã có tài khoản local trùng email thì sao?", "OAuth callback đã chống CSRF chưa?")
- Lặp tối đa 5 lần; đầu ra: plan có **Decision Drivers** + **≥2 phương án** (ADR) → `.omc/plans/`

**Điểm mấu chốt (box đậm):** Plan dừng ở **pending approval** — **KHÔNG tự chạy tiếp**. Bạn đọc *kế hoạch*, không đọc từng dòng code, rồi mới quyết.
**Cổng đồng thuận:** rõ ràng (deep-interview) → khả thi (ralplan) → cho phép thực thi (bạn)
**Callout guardrail:** Gõ thẳng `ralph thêm OAuth` cụt lủn → `ralplan` vẫn chặn (thiếu "neo" cụ thể), ép qua vòng consensus. Bỏ qua cố ý → tiền tố `force:`.
**Visual:** 3 icon vai xếp vòng tranh luận, giữa là tài liệu "plan – pending approval" dấu ⏸️.
**Speaker notes:** "Không auto-handoff" là quyết định thiết kế cố ý — đúng guardrail đã nói ở S08.

### S14 — Cảnh 3: Giao cho dàn nhạc, rồi bước ra ngoài
**Layout:** NARRATIVE_SCENE + DIAGRAM (mermaid pipeline, giữ đúng cấu trúc gốc)
**Headline:** "Cảnh 3 — `autopilot`: dây chuyền các vai, không phải 1 AI khổng lồ làm tất"
**Command gõ vào:**
```
autopilot   # dùng plan vừa duyệt làm đầu vào
```
**Diagram pipeline (giữ đúng 5 node gốc):**
```
[plan đã duyệt] → [Execution: Ralph + Ultrawork] → [QA: UltraQA ≤5 vòng] → [Validation: Architect + Security + Code-reviewer] --cả 3 duyệt--> [Cleanup: dọn slop]
```
**Nội dung chính:**
- Đã có consensus plan → `autopilot` **bỏ qua 2 phase đầu**, nhảy thẳng vào thực thi
- **Ralph** ("hòn đá của Sisyphus"): bẻ plan thành **user story có tiêu chí nghiệm thu** (`prd.json`), **lặp không nghỉ** — làm → tự kiểm → story chưa `passes` thì làm lại, tới khi mọi story đạt **và** reviewer (mặc định Architect) gật đầu
- Việc con độc lập (sửa route, thêm middleware, viết test) → **Ultrawork** chạy **song song**, mỗi việc về đúng model tier
- Build/test nặng chạy nền

**Dòng nhấn con người:** Bạn không ngồi nhìn — bật thông báo (`omc --telegram`/`--discord`/`--slack`) rồi đi pha cà phê. Điện thoại rung khi QA xong hoặc có câu **thật sự** cần bạn quyết.
**Visual:** Pipeline lane 5 ô ngang, icon "☕" ở người dùng đứng ngoài pipeline.
**Speaker notes:** Giải thích rõ 2 tầng lặp: Ralph lặp toàn cục theo story, Ultrawork chạy song song trong mỗi vòng.

### S15 — Chọn mode theo hình dạng việc
**Layout:** DECISION_TABLE
**Headline:** "Chọn mode theo hình dạng việc — phản xạ, không phải bảng tra"
**Nội dung chính:**
| Hình dạng việc | Mode |
|---|---|
| Một việc rõ, gọn | Để `executor` làm |
| Nhiều việc **độc lập** (VD: sửa 20 lỗi TypeScript rải rác) | `ulw` (Ultrawork) — bắn song song |
| Cần **đảm bảo hoàn thành** + verify sạch, kể cả crash giữa chừng | `ralph` (có state, resume được) |
| Spec lớn nhiều giai đoạn, muốn dàn quân | `team 5:executor ...` (pipeline phân tầng, có lead điều phối) |
| Idea → code trọn gói, không muốn đụng tay | `autopilot` |

**Visual:** Bảng 2 cột, cột phải mỗi dòng 1 icon mode riêng.
**Speaker notes:** Slide đứng lại lâu nhất trong toàn bài — bảng thực dụng nhất để áp dụng ngay.

### S16 — Cảnh 4: Khi hòn đá lăn ngược
**Layout:** NARRATIVE_SCENE
**Headline:** "Cảnh 4 — cơ chế dừng-an-toàn khi có sự cố"
**Tình huống:** Ralph quay vòng — cùng lỗi test OAuth callback hỏng **3 lần liên tiếp**.
**Nội dung chính:**
- Ralph **không** lăn vô hạn mù quáng — gặp cùng lỗi 3 vòng → **escalate** thay vì cố mãi
- Tín hiệu `"The boulder never stops"` trong log = vòng lặp **đang chạy bình thường**, **không phải** bị treo

**Lệnh kiểm tra + xử lý:**
```
/trace                                  # xem timeline luồng agent — kẹt ở đâu
/oh-my-claudecode:cancel --force        # reset session + state cũ, sau khi sửa tay
```
**Mẹo gỡ kẹt nhanh:** `not inside tmux` → `tmux new -s dev` · `codex: command not found` → cài CLI ngoài · hook lạ → `DISABLE_OMC=1` hoặc `OMC_SKIP_HOOKS=<tên>`.
**Visual:** Icon boulder lăn ngược nhẹ trên dốc, dừng ở vạch "3 lần".
**Speaker notes:** Nhấn rõ: đây là **feature** (safety-stop), không phải bug của Ralph.

### S17 — Cảnh 5: Nghiệm thu — người viết không tự chấm
**Layout:** NARRATIVE_SCENE
**Headline:** "Cảnh 5 — Validation: 3 người khác phải đồng ý, không phải người viết"
**Nội dung chính:**
- Ralph báo mọi story `passes`, Architect đã duyệt trong Execution — nhưng **autopilot chưa cho qua**
- 3 reviewer bắt buộc: **Architect** (kiến trúc) · **Security-reviewer** (CSRF/secret/token rò rỉ — vì đây là code auth) · **Code-reviewer** (chất lượng tổng thể)
- Golden Rule đóng thành quy trình: "người viết code **không được tự duyệt** — cùng ngữ cảnh vừa sinh vừa khen sẽ mù trước lỗi của chính nó"
- Cleanup bắt buộc: `ai-slop-cleaner` quét bỏ phần phình (import thừa, abstraction vô dụng, comment lảm nhảm) → **chạy lại test**

**Command tùy chọn:**
```
/oh-my-claudecode:ai-slop-cleaner src/auth/oauth.ts --review   # chỉ báo cáo, không sửa
/oh-my-claudecode:verify                                        # đòi bằng chứng "thực sự chạy"
```
**Dòng đóng cảnh:** Nghiệm thu bằng **bằng chứng** (test pass, và nếu theo dõi nghiêm thì cả churn/CFR/lead time — S10), không bằng cảm tính. OAuth lên PR; merge.
**Visual:** 3 icon reviewer chắn trước 1 cổng, chỉ mở khi cả 3 gật đầu (✓✓✓).
**Speaker notes:** Gắn trực tiếp Golden Rule (S06) vào quy trình quan sát được.

### S18 — Cảnh 6: Bộ nhớ của dàn nhạc
**Layout:** NARRATIVE_SCENE (nhẹ — slide "thu hoạch")
**Headline:** "Cảnh 6 — vì sao lần sau nó không hỏi lại"
**Tình huống:** Tuần sau, thêm "đăng nhập GitHub". Agent **không hỏi lại** tech stack, quy ước đặt tên, hay việc dự án dùng JWT.
**Nội dung chính (4 lớp bộ nhớ bền):**
- Quyết định dài hạn → `.omc/project-memory.json`
- Ghi chú cao-signal → `.omc/notepad.md` (`<remember>` = 7 ngày, `<remember priority>` = vĩnh viễn)
- Plan/spec cũ → `.omc/plans/`, `.omc/specs/`
- Bài học OAuth callback → đã `wiki this` → tri thức tra cứu được cho mọi phiên sau

**Callout mở rộng:** Giải hay, muốn tái dùng → `/oh-my-claudecode:skillify` đóng thành skill riêng. Nhiều issue cùng lúc → `omc teleport #123` — mỗi issue 1 worktree + tmux, song song, mỗi cái 1 PR.
**Dòng đóng:** "Dàn nhạc nhớ bản tổng phổ; bạn không phải dạy lại từ đầu."
**Visual:** Motif Conductor cầm "bản tổng phổ" thay vì dạy lại dàn nhạc.

### S19 — Rút gọn cả phiên thành một phản xạ
**Layout:** BULLETS (dòng chảy 1 câu, tối giản)
**Headline:** "Bóc hết tên lệnh — cái còn lại là một vòng lặp của nhạc trưởng"
**Dòng chảy chính (căn giữa, cỡ lớn):**
**Làm rõ** (`deep-interview`) → **lập kế hoạch & bị thách thức** (`ralplan`, dừng ở *pending approval*) → **bạn duyệt** → **giao đúng hình dạng** (`autopilot`/`ralph`/`ulw`/`team`) → **người khác kiểm, không phải người viết** (Validation + `verify`) → **đo bằng metric thật, không đếm dòng**

**Dòng đóng (liên kết ngược Phần 4):** "Mỗi mũi tên là một cổng. Bạn chỉ leo từ L3 lên L4 khi cổng kiểm — test, review tách lớp — đã đủ chắc để đỡ."
**Visual:** 6 ô nối mũi tên ngang, mỗi ô tái dùng icon từ các cảnh trước. Autonomy dial callback lần cuối, kim dừng ở "L3→L4".

### S20 — Cheat-sheet: toàn bộ lệnh dùng trong buổi demo (mang về dùng ngay)
**Layout:** DECISION_TABLE / cheat-sheet, layout dày, dùng làm slide "take-away" của Phần 5
**Headline:** "Cheat-sheet lệnh OMC — chụp lại slide này"
**Nội dung chính (bảng lệnh theo đúng thứ tự xuất hiện ở Phần 5):**
| Khi nào dùng | Lệnh |
|---|---|
| Ý tưởng mơ hồ, cần làm rõ trước khi code | `deep interview: <mô tả ngắn>` |
| Bug chưa rõ nguyên nhân | `/deep-dive` |
| Có spec, cần plan bị thách thức trước khi chạy | `ralplan` |
| Idea → code trọn gói, không muốn đụng tay | `autopilot` |
| Cần đảm bảo hoàn thành, resume được nếu crash | `ralph` |
| Nhiều việc độc lập, chạy song song | `ulw` (Ultrawork) |
| Spec lớn, muốn dàn quân theo pipeline | `team 5:executor ...` |
| Xem agent nào kẹt ở đâu | `/trace` |
| Reset session/state khi kẹt thật sự | `/oh-my-claudecode:cancel --force` |
| Tự rà code AI trước khi merge (chỉ báo cáo) | `/oh-my-claudecode:ai-slop-cleaner <path> --review` |
| Đòi bằng chứng "thực sự chạy" trước khi nghiệm thu | `/oh-my-claudecode:verify` |
| Đóng 1 giải pháp hay thành skill tái dùng | `/oh-my-claudecode:skillify` |
| Xử lý nhiều issue song song, mỗi cái 1 worktree + PR | `omc teleport #<issue>` |

**Visual:** Pipeline lane nhỏ ở đầu slide tóm lại thứ tự 6 cảnh (S12–S18), bảng lệnh chiếm phần chính; đây là slide nên để mở lâu nhất cuối Phần 5.
**Speaker notes:** Nói rõ: đây là slide duy nhất nên chụp lại nếu chỉ chụp 1 slide trong cả bài.

---

## 9. Đóng

### S21 — Tổng kết một câu
**Layout:** CLOSING (tối giản nhất trong toàn deck)
**Headline (câu duy nhất, cỡ chữ lớn nhất toàn bài):**
"Agentic coding không phải cuộc đua 'ai để AI tự chủ nhiều hơn'. Nó là kỹ năng **đặt agent vào đúng bậc tự chủ cho từng việc, quây đủ guardrail, và đo bằng metric thật**."
**Dòng phụ:** "Công cụ chỉ là phương tiện — bằng chứng, không phải hype, mới là la bàn."
**Visual:** Motif Conductor lần cuối, tối giản (silhouette + autonomy dial nhỏ góc), nền tối.
**Speaker notes:** Đọc chậm, dừng lâu.

### S22 — Nguồn tham khảo
**Layout:** REFERENCES (2 cột nếu dài)
**Headline:** "Nguồn tham khảo"
**Nội dung (đầy đủ URL, giữ đúng danh sách gốc):**
- GitHub Copilot history — https://en.wikipedia.org/wiki/GitHub_Copilot
- Anthropic Claude model release timeline — https://hidekazu-konishi.com/entry/anthropic_claude_model_release_timeline.html
- Devin (Cognition Labs) — https://thinkml.ai/devin-a-viral-ai-coding-agent-everything-you-need-to-know/
- Karpathy "vibe coding" tweet (2/2/2025) — https://x.com/karpathy/status/1886192184808149383
- Collins Dictionary Word of the Year 2025 — https://blog.collinsdictionary.com/language-lovers/collins-word-of-the-year-2025-ai-meets-authenticity-as-society-shifts/
- Anthropic 2026 Agentic Coding Trends Report — https://resources.anthropic.com/2026-agentic-coding-trends-report
- Five Levels of AI Agent Autonomy — Swarmia — https://www.swarmia.com/blog/five-levels-ai-agent-autonomy/
- Agentic coding tools (enterprise) — Prommer — https://prommer.net/en/tech/guides/agentic-coding-tools-enterprise/
- Claude Code agent architecture — ZenML/Anthropic — https://www.zenml.io/llmops-database/claude-code-agent-architecture, https://www.anthropic.com/product/claude-code
- Aider Architect/Editor — https://aider.chat/2024/09/26/architect.html
- Cline Series A — https://cline.bot/blog/cline-raises-32m-series-a
- OpenHands (CodeAct) — https://arxiv.org/abs/2407.16741
- Devin Desktop — https://devin.ai/desktop/
- Cursor 3 agent-first — InfoQ — https://www.infoq.com/news/2026/04/cursor-3-agent-first-interface/
- oh-my-claudecode docs (#execution-modes) — https://oh-my-claudecode.dev/docs/#execution-modes
- CSA Levels of Autonomy (2026) — https://cloudsecurityalliance.org/blog/2026/01/28/levels-of-autonomy
- Knight First Amendment — https://arxiv.org/abs/2506.12469
- ELEKS AI-SDLC Maturity Model — https://eleks.com/blog/ai-sdlc-maturity-model/
- METR RCT 2025 — https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/, https://arxiv.org/abs/2507.09089
- DORA 2025 Report — https://dora.dev/dora-report-2025/
- GitClear AI code quality 2025 — https://www.gitclear.com/ai_assistant_code_quality_2025_research
- AI code security — https://arxiv.org/abs/2404.18353, https://www.veracode.com/blog/genai-code-security-report/
- Stack Overflow Developer Survey 2025 — https://survey.stackoverflow.co/2025/ai
- GitHub Copilot productivity (Peng et al. 2023) — https://arxiv.org/abs/2302.06590
- McKinsey developer productivity with GenAI — https://www.mckinsey.com/capabilities/tech-and-ai/our-insights/unleashing-developer-productivity-with-generative-ai

**Visual:** Danh sách gọn, font nhỏ hơn nội dung chính; tách 2 slide (S22a/S22b) nếu quá dày khi ép vào 1 slide.
**Speaker notes:** Không cần đọc hết — để lại cho người xem sau.

### S23 — Q&A / Cảm ơn
**Layout:** QA
**Headline:** "Câu hỏi & thảo luận"
**Dòng gợi mở:**
- "Bạn đang ở bậc nào trong thang 6 bậc — và guardrail nào đang thiếu?"
- "Việc nào trong team bạn nên thử theo đúng lộ trình ở Phần 5 (deep-interview → ralplan → autopilot)?"
**Visual:** Motif Conductor tối giản lặp lại từ S00, khép vòng hình ảnh của cả deck.

---

## 10. Bảng kiểm bàn giao (checklist cho agent tạo slide)

- [ ] Đủ 24 slide (S00–S23), đúng thứ tự; Phần 1–4 = 9 slide (S02–S10), Phần 5 = 10 slide (S11–S20)
- [ ] Phần 5 phải có trọng lượng thị giác rõ ràng hơn Phần 1–4 (divider riêng đậm, badge "trọng tâm", slide đứng lại lâu hơn theo speaker notes)
- [ ] 2 sơ đồ mermaid gốc (S03 landscape, S14 pipeline) giữ đúng số node và thứ tự
- [ ] Bảng L0–L5 (S07) và bảng lệnh cheat-sheet (S20) render đầy đủ, không rút gọn — đây là 2 slide "chụp lại" chính của bài
- [ ] Mọi số liệu %/x lần ở S02–S03, S09–S10 có footer citation tương ứng
- [ ] Không thêm số liệu/nguồn ngoài danh sách ở S22
- [ ] Giữ tiếng Anh cho thuật ngữ kỹ thuật (Ralph, Ultrawork, Autopilot, churn, autonomy...)
- [ ] Autonomy dial xuất hiện từ S07–S10, callback ở S19
- [ ] Giọng điệu không dùng ngôn ngữ marketing/hype ở bất kỳ slide nào
