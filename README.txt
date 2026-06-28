╔═══════════════════════════════════════════════════════════════╗
║                    VIBECODE KIT                              ║
║        Human-first workflow for coding agents                 ║
║              Biến ý tưởng thành sản phẩm thật                 ║
╚═══════════════════════════════════════════════════════════════╝

TRẠNG THÁI HIỆN TẠI

  • v7 Draft: hướng phát triển mới — compact, agent-agnostic,
    ưu tiên coding agent có quyền đọc codebase.

  • v6.0 Stable: bản ổn định hiện tại — general-purpose AI-assisted
    development methodology với 3 vai trò và workflow 8 bước.

  • vibecode-kit.skill hiện vẫn là package cài đặt chính cho v6.
    v7 đang là draft tài liệu trong thư mục skill-v7/ để review,
    thử nghiệm và chuẩn hóa trước khi đóng gói thành skill cài đặt.

VIBECODE KIT LÀ GÌ?

  Vibecode Kit là một phương pháp luận phát triển phần mềm với AI.
  Mục tiêu của project là giúp con người và coding agent phối hợp có
  cấu trúc: làm rõ yêu cầu, chọn hướng kỹ thuật, chia task, implement,
  verify và refine.

  Hướng v7 chuyển trọng tâm từ:

    Claude Chat lập kế hoạch → paste sang Claude Code → report dài

  sang:

    Một coding agent đọc repo → tạo artifact ngắn → hỏi đúng quyết định
    → implement task nhỏ → verify bằng evidence → report compact

QUY TRÌNH v7 DRAFT

  Core workflow:

    EVIDENCE SCAN → ALIGN → EXPLORE → DECIDE → DETAIL → EXECUTE

  Trong đó:

  • Evidence Scan
    Đọc codebase/tài liệu hiện có trước khi thiết kế.

  • Align
    Tạo Project Brief: problem, goal, scope, non-goals, success criteria.

  • Explore
    Tạo PRD-lite và SSD Options khi có nhiều hướng kỹ thuật hợp lý.

  • Decide
    Chọn hướng, ghi Decision Log / ADR cùng trade-off.

  • Detail
    Tạo LLD, Task Graph, Execution Cards.

  • Execute
    Coding agent implement, chạy test, cập nhật Verify Ledger.

ĐIỂM KHÁC BIỆT v7 SO VỚI v6

  v6:
    SCAN → RRI → VISION → BLUEPRINT → TASK GRAPH → BUILD → VERIFY → REFINE

  v7:
    EVIDENCE SCAN → ALIGN → EXPLORE → DECIDE → DETAIL → EXECUTE

  v6 mặc định map vai trò vào Claude Chat / Claude Code.
  v7 chuyển sang responsibility-based, agent-agnostic:

    • Human decision owner
    • Product-tech planner
    • Executor / verifier
    • Optional reviewer

  v6 dùng TIP và Completion Report đầy đủ.
  v7 dùng Execution Card và Compact Report mặc định.

  v6 RRI có target 40–60 câu hỏi.
  v7 RRI là kỹ thuật hỏi theo rủi ro: “I see it like this — correct?”

CÁCH DÙNG NHANH

  Nếu muốn dùng bản ổn định hiện tại:

    1. Mở file vibecode-kit.skill
    2. Copy/install vào Claude
    3. Dùng workflow v6 theo skill hiện tại

  Nếu muốn thử hướng v7 draft:

    1. Đọc skill-v7/SKILL.md
    2. Đọc skill-v7/references/human-workflow.md
    3. Dùng skill-v7/references/compact-artifacts.md để tạo artifact ngắn
    4. Chạy task với một coding agent có quyền đọc/sửa repo
    5. Ghi kết quả vào Verify Ledger thay vì report dài mặc định

CẤU TRÚC THƯ MỤC

  vibecode-kit/
  ├── README.txt                  ← Bạn đang đọc file này
  ├── vibecode-kit.skill          ← Package cài đặt chính hiện tại cho v6
  ├── CURRENT_VERSION.md          ← Trạng thái version + roadmap
  ├── CHANGELOG.md                ← Lịch sử thay đổi
  ├── CASE-STUDIES.md             ← Metrics + case study templates
  ├── PHILOSOPHY_V5.md            ← Triết lý nền tảng tham khảo
  ├── skill-v7/                   ← v7 draft — compact agent-agnostic workflow
  │   ├── SKILL.md
  │   ├── references/
  │   │   ├── source-map.md
  │   │   ├── human-workflow.md
  │   │   ├── compact-artifacts.md
  │   │   ├── agent-workflow.md
  │   │   ├── verification-policy.md
  │   │   └── migration-from-v6.md
  │   └── sources/
  │       ├── README.md
  │       └── product-triangle-nexus-workflow.md
  ├── skill-v6/                   ← v6 stable source of truth
  │   ├── SKILL.md
  │   └── references/
  ├── Masters/                    ← Standalone prompt masters
  ├── Archive/                    ← Tài liệu cũ/tham khảo
  └── GIAO-VIEN-THPT-MASTER.txt   ← Skill riêng, không thuộc core

NGUỒN THAM KHẢO

  v7 có source tracking riêng để contributor biết concept đến từ đâu:

    skill-v7/sources/README.md
    skill-v7/references/source-map.md

  Nguồn chính gồm:

  • Tài liệu local “Tam giác sản phẩm - Quy trình làm việc mới”
    → skill-v7/sources/product-triangle-nexus-workflow.md

  • Agile Manifesto
    → https://agilemanifesto.org/

  • Cucumber Gherkin Reference
    → https://cucumber.io/docs/gherkin/reference/

  • W3C WCAG 2.2
    → https://www.w3.org/TR/WCAG22/

  • Keep a Changelog
    → https://keepachangelog.com/en/1.1.0/

CÁC PROTOCOL ĐẶC BIỆT

  Các protocol từ v6 vẫn còn giá trị và được v7 dùng lại theo hướng compact:

  • Debug Protocol — gỡ lỗi dựa trên evidence
  • QA Protocol — nghiệm thu theo tier, full report khi milestone/risk
  • X-Ray Protocol — bàn giao/onboarding/audit
  • RRI Methodology — phỏng vấn ngược yêu cầu
  • RRI-T / RRI-UX / RRI-UI — mở rộng cho Testing & UX

GHI CHÚ ĐÓNG GÓP

  Khi thêm concept mới vào v7:

  1. Ghi nguồn vào skill-v7/references/source-map.md
  2. Nếu là nguồn local, đưa bản có thể review lên skill-v7/sources/
  3. Nếu là external standard, thêm link vào skill-v7/sources/README.md
  4. Nếu chưa có nguồn rõ, đánh dấu needs citation

─────────────────────────────────────────────────────────────────
Vibecode Kit by Lâm Nguyễn
