# Hướng dẫn Agentic Coding: Từ "Vibe" đến Điều phối hiệu quả

> **Dành cho ai:** lập trình viên đã dùng Claude Code / Cursor (hoặc một AI coding agent nào đó) và muốn **nâng cao** — không phải để gõ prompt nhanh hơn, mà để dùng agent một cách có **hiệu quả và năng suất đo được**.
>
> **Tài liệu này KHÔNG làm gì:** không dạy lập trình cơ bản, không phải hướng dẫn cài đặt từng OS, không tô hồng. Mọi con số quan trọng đều có dẫn nguồn (xem [Nguồn tham khảo](#nguồn-tham-khảo)). Khi bằng chứng nói ngược với hype, tài liệu đứng về phía bằng chứng.

**Luận điểm xuyên suốt:** Công cụ chỉ là phương tiện. Cái quyết định năng suất không phải là *bạn để agent tự chủ tới đâu*, mà là *bạn chọn đúng mức tự chủ cho từng việc và đặt đủ guardrail*. Tài liệu đi theo mạch: bối cảnh → triết lý → công cụ → tự định vị trên thang level → thực hành với `oh-my-claudecode`.

---

## Phần 1 — Bối cảnh: autocomplete → vibe coding → agentic coding

### 1.1. Một dòng thời gian ngắn

Agentic coding không rơi từ trên trời xuống. Nó là điểm cuối (tạm thời) của một đường tiến hóa kéo dài 5 năm:

| Mốc | Sự kiện | Ý nghĩa |
|-----|---------|---------|
| 06/2021 | GitHub Copilot technical preview (OpenAI Codex) | Kỷ nguyên **autocomplete**: gợi ý từng dòng, người vẫn là tác giả |
| 11/2022 | ChatGPT ra mắt (1M user trong 5 ngày) | Code-qua-hội-thoại phổ cập |
| 03/2023 | Claude 1 (Anthropic) | Cuộc đua model lý luận |
| 03/2024 | Devin 1.0 (Cognition) tự nhận "AI Software Engineer đầu tiên" | Khái niệm **agent tự chủ end-to-end** xuất hiện |
| 10/2024 | Claude Code research preview | Agent **terminal-native** |
| **02/02/2025** | Andrej Karpathy đặt ra thuật ngữ **"vibe coding"** | Đặt tên cho một phong cách làm việc mới |
| 09/2025 | Claude Code 2.0 + VS Code extension | Agentic coding thành dòng chính |
| 2026 | Karpathy retrospective, đề xuất thuật ngữ "agentic engineering" | Ngành bắt đầu phân biệt "vibe" (chơi) với "engineering" (làm thật) |

Nguồn: [GitHub Copilot history (Wikipedia)][copilot], [Anthropic model timeline][anthropic-timeline], [Devin][devin-tml].

### 1.2. "Vibe coding" thực ra là gì

Ngày 2/2/2025, Karpathy (đồng sáng lập OpenAI, cựu Director AI của Tesla) đăng một tweet — chính ông sau này gọi là *"throwaway tweet"* — định nghĩa:

> *"There's a new kind of coding I call vibe coding, where you fully give in to the vibes, embrace exponentials, and forget that the code even exists."* — [Karpathy, 2/2/2025][karpathy]

Tweet đó (4.5 triệu lượt xem) mô tả 4 hành vi cốt lõi của vibe coding:

1. **Accept toàn bộ** code AI sinh ra mà không đọc diff.
2. **Paste thẳng error** trả lại cho AI để nó tự sửa.
3. Để codebase **phình to vượt ngoài tầm hiểu** của chính mình.
4. Dùng **voice input** (Karpathy dùng SuperWhisper) thay vì gõ.

"I just see stuff, say stuff, run stuff, and copy-paste stuff, and it mostly works." Đến cuối 2025, Collins Dictionary chọn **"vibe coding" là Word of the Year**. ([Collins][collins])

**Điểm cần thẳng thắn:** ngay trong tweet gốc, Karpathy đã ghi rõ đây là phong cách cho **dự án cuối tuần / hobby**, nơi "code mostly works" là đủ. Nó **không phải** quy trình kỹ thuật cho production. Việc đánh đồng "vibe coding" với "cách làm phần mềm nghiêm túc" là nguồn gốc của phần lớn hype lẫn thất vọng sau này.

### 1.3. Vibe coding khác autocomplete ở chỗ nào — và "agentic coding" sinh ra thế nào

Autocomplete thời Copilot (2021–2022): agent **gợi ý**, bạn **đọc – hiểu – chọn** từng đoạn. Bạn vẫn là *author*.

Vibe coding phá vỡ cả ba quy ước đó: không đọc diff, không cần hiểu, không giữ authorship — bạn *"steer"* bằng ngôn ngữ tự nhiên và chấp nhận output.

"Agentic coding" là bước trưởng thành tiếp theo: giữ lại sức mạnh ủy thác của vibe coding, nhưng **gắn lại kỷ luật kỹ thuật** (review, test, spec). Báo cáo *Anthropic 2026 Agentic Coding Trends* mô tả ngắn gọn sự dịch chuyển:

> *"In 2024, most AI coding assistance was inline autocomplete. By 2026, the dominant pattern is autonomous execution — the developer describes a task and the agent executes it across multiple files, running commands and iterating until the task is complete."* ([Anthropic][anthropic-trends])

Tóm lại: **code suggestion → steerable draft → intent delegation**.

### 1.4. Bản đồ thị trường (landscape) — 4 nhóm kiến trúc

Hàng chục công cụ, nhưng chúng xếp vào 4 nhóm theo **mức tự chủ tăng dần** ([Swarmia][swarmia], [Prommer][prommer]):

```mermaid
graph LR
  A[Autocomplete<br/>gợi ý dòng] --> B[IDE-embedded agent<br/>đa file + duyệt]
  B --> C[CLI agent<br/>terminal, composable]
  C --> D[Autonomous agent<br/>end-to-end]
```

- **Autocomplete:** GitHub Copilot (bản gốc), Codeium.
- **IDE-embedded agent:** Cursor, Windsurf, Cline, Continue.
- **CLI agent:** **Claude Code**, Aider, OpenHands (CLI mode).
- **Autonomous agent:** Devin, OpenHands (full).

Ranh giới đang mờ dần — Copilot nay đã có cả "coding agent" chạy trên cloud. Điều đáng nhớ: **vị trí của một công cụ trên trục này là một lựa chọn triết học**, không phải thước đo "xịn hơn". Phần 2 sẽ mổ xẻ.

---

## Phần 2 — Triết lý: công cụ chỉ là phương tiện

### 2.1. Vì sao triết lý quan trọng hơn tính năng

Mọi công cụ ở Phần 1 đều gọi cùng những model (Claude, GPT, Gemini). Thứ phân biệt chúng — và phân biệt một dev hiệu quả với một dev "vibe" — là **triết lý sử dụng**: bạn đặt ranh giới quyền lực cho agent ở đâu, và bạn giữ vai trò gì.

Triết lý cô đọng nhất, mượn từ `oh-my-claudecode`:

> **Bạn là nhạc trưởng, không phải nhạc công.** (*You are the conductor, not the performer.*)

Nhạc trưởng không chơi từng nốt. Họ **định hướng, phân vai, và kiểm tra**. Khi bạn nhảy vào tự sửa từng dòng, bạn vừa làm chậm chính mình vừa đánh mất bức tranh tổng thể. Khi bạn buông hoàn toàn (vibe coding thuần), bạn mất kiểm soát chất lượng. Hiệu quả nằm ở khoảng giữa — và biết *mình đang ở đâu trong khoảng giữa đó* chính là nội dung Phần 4.

### 2.2. Cùng một model, những triết lý đối nghịch

Đọc triết lý thiết kế của vài công cụ là cách nhanh nhất để thấy "trục control ↔ autonomy" là một *lựa chọn có chủ đích*:

| Công cụ | Triết lý cốt lõi | Hệ quả thiết kế |
|---------|------------------|-----------------|
| **Claude Code** | *"Do the simple thing first."* Vòng lặp đơn luồng (codename nội bộ **"nO"**), **chủ đích tránh** multi-agent swarm | Ưu tiên debuggability & minh bạch; composable kiểu Unix (pipe, CI/CD). Dev định nghĩa goal, review kết quả ([ZenML][zenml], [Anthropic][cc-product]) |
| **Aider** | *Git là source of truth & cơ chế an toàn* | Mỗi edit = 1 atomic commit có message do LLM viết; tách Architect/Editor để rẻ hơn ([Aider][aider]) |
| **Cline** | *"Inference không nên là business model"* → approval-first | Người duyệt từng action; mã nguồn mở, minh bạch chi phí ([Cline][cline]) |
| **OpenHands** | *"Agentic tech quá quan trọng để vài công ty kiểm soát"* | Mã nguồn mở (ICLR 2025), kiến trúc CodeAct, ~77% SWE-Bench Verified, model-agnostic ([OpenHands][openhands]) |
| **Devin** (Cognition) | *Autonomous software engineer* | End-to-end, ít can thiệp; đã mua Windsurf → Devin Desktop ([Devin][devin-desktop]) |
| **Cursor** | *Developer-as-orchestrator* | IDE-native, Cursor 3 agent-first ([InfoQ][infoq-cursor]) |

Bài học: **không có công cụ "đúng" tuyệt đối**. Có công cụ phù hợp với mức tự chủ mà *task của bạn* cho phép. Một thư viện nội bộ chưa có test thì approval-first (Cline/Claude Code supervised) an toàn hơn full-autopilot (Devin) — bất kể model mạnh tới đâu.

> ⚠️ **Bẫy đặt tên:** Codeium (→ Windsurf → Devin Desktop) và CodiumAI (→ Qodo) là **hai công ty khác nhau**. Codeium thiên về tăng tốc code; Qodo thiên về code integrity/testing. Tài liệu khắp nơi nhầm hai cái này.

---

## Phần 3 — Công cụ: `oh-my-claudecode` (trọng tâm) và `oh-my-pi` (sơ lược)

### 3.1. Nền móng: Claude Code

Claude Code là một **CLI agent terminal-native** của Anthropic (preview 10/2024, GA dần qua 2025). Triết lý "do the simple thing first": một vòng lặp đơn luồng đọc → sửa → chạy → tự kiểm, bạn duyệt kết quả. Mạnh, minh bạch, nhưng *trần năng suất* nằm ở chỗ nó là **một** agent.

### 3.2. `oh-my-claudecode` (OMC) — biến Claude Code thành dàn nhạc

`oh-my-claudecode` là một **lớp điều phối đa-agent** (multi-agent orchestration) chồng lên Claude Code. Thay vì một agent, bạn chỉ huy một dàn agent chuyên biệt. Theo [docs OMC][omc-docs], OMC cung cấp:

- **19 agent chuyên biệt** trải nhiều lane (exploration, planning, execution, verification, review, testing, docs, data, vcs, cleanup...), mỗi agent gắn sẵn model tier hợp lý (Haiku/Sonnet/Opus) — bạn sẽ thấy chúng vào vai đúng lúc trong Phần 5.
- **Nhiều execution mode** — từ Autopilot (tự chủ toàn phần) tới Team (điều phối native), Ralph (kiên trì), Ultrawork (song song), UltraQA (QA cycling).
- **Bộ MCP tool** — Language Server (lsp_*), AST grep, Python REPL, state/notepad/project-memory, và model ngoài (Codex, Gemini).
- **Native Teams** — pipeline phân tầng `team-plan → team-prd → team-exec → team-verify → team-fix`.

Nguyên tắc vàng của OMC nhắc lại đúng triết lý Phần 2:

> **Golden Rule:** *NEVER make code changes directly. ALWAYS delegate to specialized agents.* Vai trò của bạn là **guide, review, orchestrate**.

Đây là lý do tài liệu này lấy OMC làm trọng tâm: nó **mã hóa triết lý conductor thành công cụ**, và **dễ bắt đầu** — bạn gõ ý định bằng ngôn ngữ tự nhiên ("autopilot build...", "ralph refactor..."), OMC tự định tuyến. Cách dùng cụ thể ở Phần 5.

### 3.3. `oh-my-pi` (giới thiệu sơ)

`oh-my-pi` là một **harness agentic coding** khác (chính harness đang chạy phiên này). Cùng họ triết lý *delegation-first* với OMC, nhưng nhấn vào **bộ công cụ tích hợp giàu** và **song song hóa**: tìm/sửa code theo cấu trúc (AST), LSP code-intelligence, kernel `eval` bền trạng thái, browser automation, `task` subagent chạy song song, và kênh nhắn tin giữa các agent (IRC-style).

Điểm chung quan trọng với OMC: cả hai đều coi *con người là nhạc trưởng* và *agent chuyên biệt là nhạc công*. Tài liệu này không đi sâu `oh-my-pi` — nếu bạn mới bắt đầu, **OMC dễ tiếp cận hơn**; coi `oh-my-pi` như một điểm khác trong cùng không gian thiết kế để biết rằng triết lý điều phối không phụ thuộc một sản phẩm cụ thể.

---

## Phần 4 — Hệ thống level: bạn đang ở đâu? (trục tự chủ)

Đây là xương sống của tài liệu. Mục tiêu: cho bạn một thước đo **khách quan** để tự định vị — và một thông điệp chống hype.

### 4.1. Vì sao đo theo "mức tự chủ của agent" (autonomy)

Trục autonomy không phải tôi tự nghĩ ra. Nó là cách **ngành đang hội tụ**. Tương tự thang **SAE J3016** (6 cấp tự lái L0–L5 cho xe), nhiều khung độc lập đã áp ngôn ngữ "levels of autonomy" cho AI coding:

| Khung | Trục | Các bậc |
|-------|------|---------|
| **Swarmia** (coding-specific, 2026) | agent làm bao nhiêu trước khi quay lại xin feedback | Assistive → Conversational → Task agent → Autonomous teammate → Agentic avalanche ([Swarmia][swarmia]) |
| **CSA** (Jim Reavis, 2026) | mức human control còn lại | L0 No → L1 Assisted → L2 Supervised → L3 Conditional → L4 High → L5 Full ([CSA][csa]) |
| **Knight First Amendment** (2025) | vai trò của người dùng | Operator → Collaborator → Consultant → Approver → Observer ([arXiv 2506.12469][knight]) |
| **ELEKS** (2026) | độ trưởng thành tổ chức | Traditional → AI-Supported → AI-Assisted → AI-Native → AI-Autonomous ([ELEKS][eleks]) |

**Đồng thuận giữa các khung:** (1) khoảng **5–6 bậc**; (2) cực thấp = AI chỉ gợi ý, người làm; (3) cực cao = full autonomy vẫn còn rủi ro/lý thuyết ("not appropriate for enterprise today" — CSA); (4) **human oversight nghịch chiều với autonomy**; và quan trọng nhất — (5) **cao hơn KHÔNG đồng nghĩa tốt hơn**. Autonomy là một *design choice*, không phải bậc thang để leo.

### 4.2. Thang 6 bậc (tổng hợp) + vị trí các công cụ

Thang dưới đây hợp nhất các khung trên (Swarmia cho mô tả coding, CSA cho mức kiểm soát, Knight cho vai trò người), gắn mỗi bậc với **một metric đáng tin** để đo (xem 4.3):

| Bậc | Agent làm gì | Vai trò bạn | Công cụ tiêu biểu | Metric phải canh |
|----|-------------|-------------|-------------------|------------------|
| **L0 Manual** | Không AI | Author | — | (baseline) |
| **L1 Assistive** | Autocomplete từng dòng | Operator | Copilot inline | Code churn |
| **L2 Conversational** | Chat, sửa đa file, **bạn duyệt từng bước** | Collaborator | Claude Code cơ bản, Cursor chat | Review từng diff |
| **L3 Delegation (Conductor)** | Nhận task → tự plan → sửa nhiều file → mở PR; **bạn duyệt kết quả, không duyệt từng bước** | Approver | Claude Code agentic + **OMC cơ bản**, Copilot coding agent | Change Failure Rate, defect escape |
| **L4 Orchestration** | **Nhiều agent song song** + quality gate (plan/exec/verify) | Designer/Approver | **OMC Autopilot / Team / Ralph**, oh-my-pi | Churn, stability, lead time |
| **L5 Autonomous** | Tự chọn task từ backlog, self-improving loop | Observer | Frontier (Devin, multi-agent) — *rủi ro* | "not enterprise-ready" |

**Dấu hiệu bạn đang ở bậc nào (tự định vị nhanh):**
- Bạn đọc và sửa tay phần lớn code AS sinh → **L1–L2**.
- Bạn giao một task rõ ràng và review PR agent mở ra → **L3**.
- Bạn thiết kế pipeline nhiều agent (planner → executor → verifier) và chỉ duyệt cổng chất lượng → **L4**.
- Bạn để agent tự chọn việc làm → **L5** (và bạn nên có lý do rất tốt + guardrail rất chặt).

### 4.3. Thông điệp chống hype: chọn ĐÚNG bậc, không leo tối đa

Đây là phần dễ bị bán hype nhất, nên nó cần bằng chứng cứng. **Tự chủ cao hơn không tự động cho năng suất cao hơn.** Bằng chứng:

- **METR RCT 2025:** đo 16 dev open-source giàu kinh nghiệm trên 246 task ở repo họ thông thạo. Khi *được phép* dùng AI, họ **chậm hơn 19%** (CI 95% [+2%, +39%]). Đáng sợ hơn: họ *tự nghĩ* mình nhanh hơn 24% — khoảng cách nhận thức ~43 điểm phần trăm. ([METR][metr], [arXiv 2507.09089][metr-arxiv])
- **DORA 2025** (~5.000 người): AI là **chất khuếch đại** — throughput tăng nhưng **stability giảm** nếu thiếu automated testing. "AI không sửa được team yếu, nó phóng đại điều kiện sẵn có." Chỉ 24% "tin tưởng nhiều" vào AI. ([DORA][dora])
- **GitClear** (211 triệu dòng code): code churn tăng **3.1% → 5.7%**, copy-paste **8.3% → 12.3%**, refactoring **25% → <10%** — lần đầu tiên code copy-paste vượt code refactored. ([GitClear][gitclear])
- **Bảo mật:** code do AI sinh có **mật độ lỗ hổng cao hơn ~2.7×**; 30–62% chứa lỗ hổng tùy phương pháp đo. ([arXiv 2404.18353][sec-arxiv], [Veracode][veracode])
- **Stack Overflow 2025:** adoption tăng 76% → 84% nhưng **trust giảm 40% → 29%**; 45% bực nhất vì code "almost right but not quite"; 66% tốn thêm thời gian debug code AI. ([SO Survey][so])

Mặt khác, AI *có* hiệu quả khi đặt đúng chỗ: Copilot trong lab giúp nhanh hơn 55.8% trên **task đơn giản** (nhưng giảm còn ~42% ở môi trường thật, [Peng 2023][copilot-study]); junior hưởng lợi +21–52% còn senior chỉ +7–16%, và **task càng phức tạp lợi ích càng tiệm cận <10%** ([McKinsey][mckinsey]).

**Kết luận thực dụng:** mỗi bậc autonomy là một công cụ. L4 orchestration rực rỡ cho việc *song song, lặp lại, có test bao quanh*. L2 supervised là đúng cho code *nhạy cảm, ít test, một-lần*. Leo lên L4/L5 mà thiếu guardrail = đúng công thức tạo ra churn và lỗ hổng mà các nghiên cứu trên đo được.

### 4.4. Đo "năng suất" bằng metric nào (để không tự lừa mình)

Tránh các metric dễ-hype: *số dòng sinh ra*, *tốc độ gõ*, *cảm giác nhanh*. Dùng metric hệ thống (DORA/SPACE):

| Metric | Đo cái gì | Vì sao đáng tin |
|--------|-----------|-----------------|
| **Code churn rate** (% code bị sửa < 2 tuần) | rework thực | AI làm tăng metric này — cờ đỏ sớm |
| **Change Failure Rate** | % thay đổi gây sự cố | đo chất lượng downstream sau deploy |
| **Lead time for changes** (commit → production) | tốc độ *cả hệ thống* | không chỉ tốc độ gõ |
| **Defect escape rate** | lỗi lọt tới user | chất lượng thật |
| **Security vuln density** | lỗ hổng/đơn vị code | bắt được rủi ro AI khuếch đại |

**Guardrail = điều kiện để lên bậc.** Bạn chỉ nên leo từ L_n lên L_{n+1} khi đã có: test tự động bao quanh vùng agent đụng tới, quy trình review (dù chỉ review kết quả), và spec/acceptance rõ. Thiếu guardrail thì bậc cao hơn chỉ phóng đại rủi ro — đúng như DORA và GitClear chứng minh.

---

## Phần 5 — Một phiên làm việc với `oh-my-claudecode`

Thay vì liệt kê tính năng, ta đi theo **một việc có thật từ đầu tới cuối**: bạn cần thêm *đăng nhập bằng Google (OAuth)* vào một REST API Node.js đang chạy. Đây là brownfield — code đã có, đụng vào là có rủi ro. Hãy xem một nhạc trưởng dẫn dàn agent qua việc này thế nào, và *gõ gì, gọi gì, dừng lại ở đâu*.

> Cài một lần rồi quên: `/plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode` → `/plugin install oh-my-claudecode` → `/omc-setup`. Nếu định dùng `team` hay model ngoài, cần **tmux** và `npm i -g @openai/codex @google/gemini-cli`; `/omc-doctor` sẽ báo còn thiếu gì. Từ đây trở đi bạn không gõ cú pháp — bạn **mô tả ý định**, hook của OMC bắt keyword và tự gọi skill đúng.

### 5.1. Cảnh 1 — Ý tưởng còn mơ hồ, đừng code vội

Bạn mở phiên và gõ đúng cái mình đang nghĩ:

```
deep interview: thêm đăng nhập Google vào API
```

Một câu mười từ. Nếu giao thẳng cho AI, nó sẽ *đoán* — đoán bạn muốn lưu session hay JWT, đoán có cần refresh token, đoán xử lý user trùng email ra sao. Mỗi cú đoán sai là một vòng rework. `deep-interview` chặn đúng chỗ đó: nó **không hỏi "bạn muốn gì"** mà hỏi **"bạn đang ngầm giả định gì"**.

Đầu tiên nó chốt *hình dạng* việc (Round 0 — topology): "Tôi đọc ra 3 mảnh độc lập — luồng OAuth với Google, lưu/khớp user, và phát token cho client. Đúng chưa?". Rồi mỗi vòng nó nhắm vào mảnh *mờ nhất*, hỏi đúng một câu, và sau mỗi câu trả lời nó hiện một con số **ambiguity** tụt dần: `59% → 42% → 28% → 15%`. Khi xuống dưới ngưỡng (mặc định 20%), nó dừng hỏi và kết tinh một **spec** vào `.omc/specs/`. Bạn vừa biến mười từ thành một bản đặc tả có tiêu chí nghiệm thu đo được — *trước khi* tốn một dòng code nào. Đây chính là tinh thần METR ở Phần 4: spec tốt là cách chống-rework rẻ nhất.

> Còn lửng lơ hơn nữa — một con bug mà bạn *chưa biết nguyên nhân*? Gọi `/deep-dive`: nó chạy mấy luồng truy vết song song để tìm gốc, rồi tự nạp phát hiện vào đúng phiên `deep-interview` này.

### 5.2. Cảnh 2 — Từ spec thành kế hoạch bị thách thức

Có spec rồi, bạn vẫn chưa code. Bạn đẩy nó qua một lớp guardrail nữa:

```
ralplan
```

`ralplan` không phải để bạn ngồi viết plan. Nó triệu một hội đồng ba người tranh luận về *cách làm*: **Planner** dựng các bước, **Architect** soi ranh giới hệ thống và đánh đổi dài hạn, **Critic** đập lại — "nếu user đã có tài khoản local trùng email thì sao?", "OAuth callback đã chống CSRF chưa?". Vòng này lặp tối đa 5 lần, và đầu ra không phải một danh sách việc khơi khơi mà là một plan có **Decision Drivers** và **ít nhất 2 phương án** kèm lý do chọn (ADR) — ghi vào `.omc/plans/`.

Điểm mấu chốt: **plan dừng ở trạng thái *pending approval*, không tự chạy tiếp.** OMC cố tình *không* có auto-handoff. Bạn — nhạc trưởng — đọc *kế hoạch*, không đọc từng dòng code, rồi mới quyết. Đây là cổng đồng thuận: bạn vừa đi qua *rõ ràng* (deep-interview) → *khả thi* (ralplan) → giờ là *cho phép thực thi*.

> Nếu lúc nãy bạn nóng vội gõ thẳng `ralph thêm OAuth` với một prompt cụt lủn, `ralplan` vẫn âm thầm chặn lại: prompt quá ngắn và không có "neo" cụ thể (file, `#issue`, tên hàm, thông báo lỗi) sẽ bị ép qua đúng vòng consensus này. Muốn bỏ qua cố ý thì thêm tiền tố `force:`.

### 5.3. Cảnh 3 — Giao cho dàn nhạc, rồi bước ra ngoài

Plan đã duyệt. Giờ mới tới lúc code, và bạn chọn *hình dạng* thực thi theo *hình dạng* việc:

```
autopilot   # (dùng plan vừa duyệt làm đầu vào)
```

Vì đã có consensus plan, `autopilot` **bỏ qua hai phase đầu** (không cần tự mở rộng ý tưởng và tự lập kế hoạch nữa) và nhảy thẳng vào thực thi. Bên trong, nó không phải một AI khổng lồ làm tất — nó là một **dây chuyền các vai**:

```mermaid
graph LR
  P["plan đã duyệt"] --> EX["Execution: Ralph + Ultrawork"]
  EX --> QA["QA: UltraQA ≤5 vòng"]
  QA --> V["Validation: Architect + Security + Code-reviewer"]
  V -->|cả 3 duyệt| C["Cleanup: dọn slop"]
```

Trái tim của khâu Execution là **Ralph** — "hòn đá của Sisyphus". Ralph bẻ plan thành các *user story có tiêu chí nghiệm thu* (ghi vào `prd.json` trong `.omc/state/sessions/{id}/`), rồi **lặp không nghỉ**: làm → tự kiểm → story nào chưa `passes` thì làm lại, tới khi *mọi* story đạt **và** một reviewer (mặc định **Architect**) gật đầu. Những việc con độc lập trong mỗi vòng — sửa route, thêm middleware, viết test — Ralph quăng cho **Ultrawork** chạy *song song*, mỗi việc về đúng model tier của nó (việc tra cứu cho model nhanh, việc kiến trúc cho model mạnh). Build và test nặng chạy nền.

Bạn không ngồi nhìn. Bạn đã bật thông báo lúc khởi động (`omc --telegram`, hoặc `--discord`/`--slack`), nên bạn đi pha cà phê. Điện thoại rung khi QA xong, hoặc khi có một câu *thật sự* cần bạn quyết. Đó là điều phối từ xa: agent làm, bạn chỉ vào cuộc ở khúc cua.

> **Chọn mode theo hình dạng việc** — đây là phản xạ bạn cần, không phải bảng tra:
> - Một việc rõ, gọn → cứ để `executor` làm.
> - Nhiều việc *độc lập* (sửa 20 lỗi TypeScript rải rác) → `ulw` (Ultrawork) bắn song song.
> - Cần *đảm bảo hoàn thành* và verify sạch, kể cả khi crash giữa chừng → `ralph` (có state, resume được).
> - Spec lớn nhiều giai đoạn, muốn dàn quân → `team 5:executor ...` (pipeline phân tầng, có lead điều phối).
> - Idea → code trọn gói, không muốn đụng tay → `autopilot`.

### 5.4. Cảnh 4 — Khi hòn đá lăn ngược

Không phải lúc nào cũng êm. Bạn ngó lại, thấy Ralph quay vòng — cùng một lỗi test OAuth callback hỏng *ba lần liên tiếp*. Đây là lúc cơ chế dừng-an-toàn lên tiếng: Ralph **không** lăn vô hạn một cách mù quáng; gặp cùng lỗi 3 vòng nó **escalate** thay vì cố mãi. (Tín hiệu `The boulder never stops` trong log chỉ nghĩa là vòng lặp *đang chạy bình thường* — đừng nhầm là treo.)

Bạn vào xem chuyện gì:

```
/trace            # xem timeline luồng agent — agent nào kẹt ở đâu
```

Hóa ra callback URL trong test trỏ sai môi trường. Bạn dừng sạch và sửa tay đúng một chỗ:

```
/oh-my-claudecode:cancel --force    # reset session + state cũ
```

Rồi giao lại. Vài mẹo gỡ khi kẹt thật sự: `not inside tmux` → mở `tmux new -s dev`; `codex: command not found` → cài CLI ngoài; hook cư xử lạ → `DISABLE_OMC=1` để loại trừ, hoặc tắt chọn lọc bằng `OMC_SKIP_HOOKS=<tên>`.

### 5.5. Cảnh 5 — Nghiệm thu: người viết không tự chấm

Ralph báo mọi story đã pass và Architect đã duyệt. Nhưng autopilot chưa cho qua: nó bước vào **Validation**, nơi **ba người khác** phải đồng ý — Architect (kiến trúc), **Security-reviewer** (đây là code auth, nên soi CSRF/secret/token rò rỉ), và **Code-reviewer** (chất lượng tổng thể). Đây là *Golden Rule* đóng thành quy trình: **người viết code không được tự duyệt code mình vừa viết**. Cùng một ngữ cảnh vừa sinh vừa khen sẽ mù trước lỗi của chính nó.

Cuối cùng là khâu Cleanup: một lượt `ai-slop-cleaner` *bắt buộc* quét bỏ phần phình do AI sinh ra (import thừa, abstraction vô dụng, comment lảm nhảm) — rồi *chạy lại test* để chắc dọn dẹp không làm hỏng gì. Bạn muốn tự tay rà thì gọi reviewer-only:

```
/oh-my-claudecode:ai-slop-cleaner src/auth/oauth.ts --review   # chỉ báo cáo, không sửa
/oh-my-claudecode:verify                                        # đòi bằng chứng "thực sự chạy"
```

Bạn không nghiệm thu bằng cảm tính. Bạn nhìn bằng chứng — test pass, và nếu theo dõi nghiêm thì cả *churn / change-failure-rate / lead time* (§4.4). Tính năng OAuth lên PR; bạn merge.

### 5.6. Vì sao lần sau nó không hỏi lại — bộ nhớ của dàn nhạc

Tuần sau bạn quay lại thêm "đăng nhập GitHub". Agent *không* hỏi lại tech stack, quy ước đặt tên, hay rằng dự án dùng JWT — vì những thứ đó đã nằm trong bộ nhớ bền: quyết định dài hạn ở `.omc/project-memory.json`, ghi chú cao-signal ở `.omc/notepad.md` (tag `<remember>` sống 7 ngày, `<remember priority>` là vĩnh viễn), plan/spec cũ ở `.omc/plans/` và `.omc/specs/`. Bạn cũng đã `wiki this` lại bài học OAuth callback, nên nó thành tri thức tra cứu được cho mọi phiên sau. Dàn nhạc nhớ bản tổng phổ; bạn không phải dạy lại từ đầu.

> Khi gặp một cách giải hay và muốn tái dùng, `/oh-my-claudecode:skillify` đóng nó thành một skill riêng. Cần xử lý nhiều issue cùng lúc thì `omc teleport #123` (qua `project-session-manager`) tách mỗi việc ra một worktree + tmux để chạy song song, mỗi cái một PR.

### 5.7. Rút gọn cả phiên thành một phản xạ

Bóc hết tên lệnh đi, cái còn lại là một vòng lặp của nhạc trưởng — và đó mới là thứ đáng nhớ:

> **Làm rõ** (`deep-interview`) → **lập kế hoạch & bị thách thức** (`ralplan`, dừng ở *pending approval*) → **bạn duyệt** → **giao đúng hình dạng** (`autopilot`/`ralph`/`ulw`/`team`) → **người khác kiểm, không phải người viết** (Validation + `verify`) → **đo bằng metric thật, không đếm dòng**.

Mỗi mũi tên là một cổng. Bạn chỉ leo từ L3 lên L4 (Phần 4) khi cổng kiểm — test, review tách lớp — đã đủ chắc để đỡ. `oh-my-claudecode` không khiến bạn tự chủ nhiều hơn; nó khiến việc *đặt đúng bậc tự chủ cho từng việc* trở nên dễ làm.

---

## Tổng kết một câu

Agentic coding không phải cuộc đua "ai để AI tự chủ nhiều hơn". Nó là kỹ năng **đặt agent vào đúng bậc tự chủ cho từng việc, quây đủ guardrail, và đo bằng metric thật**. `oh-my-claudecode` là cách dễ nhất để thực hành triết lý nhạc trưởng đó — nhưng công cụ chỉ là phương tiện; **bằng chứng, không phải hype, mới là la bàn**.

---

## Nguồn tham khảo

[copilot]: https://en.wikipedia.org/wiki/GitHub_Copilot
[anthropic-timeline]: https://hidekazu-konishi.com/entry/anthropic_claude_model_release_timeline.html
[devin-tml]: https://thinkml.ai/devin-a-viral-ai-coding-agent-everything-you-need-to-know/
[karpathy]: https://x.com/karpathy/status/1886192184808149383
[collins]: https://blog.collinsdictionary.com/language-lovers/collins-word-of-the-year-2025-ai-meets-authenticity-as-society-shifts/
[anthropic-trends]: https://resources.anthropic.com/2026-agentic-coding-trends-report
[swarmia]: https://www.swarmia.com/blog/five-levels-ai-agent-autonomy/
[prommer]: https://prommer.net/en/tech/guides/agentic-coding-tools-enterprise/
[zenml]: https://www.zenml.io/llmops-database/claude-code-agent-architecture
[cc-product]: https://www.anthropic.com/product/claude-code
[aider]: https://aider.chat/2024/09/26/architect.html
[cline]: https://cline.bot/blog/cline-raises-32m-series-a
[openhands]: https://arxiv.org/abs/2407.16741
[devin-desktop]: https://devin.ai/desktop/
[infoq-cursor]: https://www.infoq.com/news/2026/04/cursor-3-agent-first-interface/
[omc-docs]: https://oh-my-claudecode.dev/docs/#execution-modes
[csa]: https://cloudsecurityalliance.org/blog/2026/01/28/levels-of-autonomy
[knight]: https://arxiv.org/abs/2506.12469
[eleks]: https://eleks.com/blog/ai-sdlc-maturity-model/
[metr]: https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/
[metr-arxiv]: https://arxiv.org/abs/2507.09089
[dora]: https://dora.dev/dora-report-2025/
[gitclear]: https://www.gitclear.com/ai_assistant_code_quality_2025_research
[sec-arxiv]: https://arxiv.org/abs/2404.18353
[veracode]: https://www.veracode.com/blog/genai-code-security-report/
[so]: https://survey.stackoverflow.co/2025/ai
[copilot-study]: https://arxiv.org/abs/2302.06590
[mckinsey]: https://www.mckinsey.com/capabilities/tech-and-ai/our-insights/unleashing-developer-productivity-with-generative-ai

- GitHub Copilot history — Wikipedia
- Anthropic Claude model release timeline — hidekazu-konishi.com
- Devin (Cognition Labs) — thinkml.ai
- Karpathy "vibe coding" tweet (2/2/2025) — x.com
- Collins Dictionary Word of the Year 2025
- Anthropic 2026 Agentic Coding Trends Report
- Five Levels of AI Agent Autonomy — Swarmia
- Agentic coding tools (enterprise) — Prommer
- Claude Code agent architecture — ZenML / Anthropic
- Aider Architect/Editor — aider.chat
- Cline Series A — cline.bot
- OpenHands (CodeAct) — arXiv 2407.16741
- Devin Desktop — devin.ai
- Cursor 3 agent-first — InfoQ
- oh-my-claudecode docs (#execution-modes)
- CSA Levels of Autonomy (2026)
- Knight First Amendment — arXiv 2506.12469
- ELEKS AI-SDLC Maturity Model
- METR RCT 2025 — metr.org / arXiv 2507.09089
- DORA 2025 Report
- GitClear AI code quality 2025
- AI code security — arXiv 2404.18353 / Veracode
- Stack Overflow Developer Survey 2025
- GitHub Copilot productivity (Peng et al. 2023) — arXiv 2302.06590
- McKinsey developer productivity with GenAI
