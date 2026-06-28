╔═══════════════════════════════════════════════════════════════╗
║                    VIBECODE KIT v6.0                          ║
║         General-Purpose AI-Assisted Development               ║
║              Biến ý tưởng thành sản phẩm thật                 ║
╚═══════════════════════════════════════════════════════════════╝

VIBECODE KIT LÀ GÌ?

  Một phương pháp luận phát triển phần mềm với AI, dùng 3 vai trò:
  • Chủ nhà (Con người) — Ra quyết định chiến lược
  • Chủ thầu (Claude Chat / Cowork) — Thiết kế, phỏng vấn, điều phối
  • Thợ thi công (Claude Code) — Triển khai, test, báo cáo

  Quy trình 8 bước:
  SCAN → RRI → VISION → BLUEPRINT → TASK GRAPH → BUILD → VERIFY → REFINE

CÁCH CÀI ĐẶT:

  Bước 1: Mở file vibecode-kit.skill trong thư mục này
  Bước 2: Click "Copy to your skills" để cài vào Claude
  Bước 3: Bắt đầu bằng cách mô tả dự án (xem QUICKSTART bên dưới)

  Skill sẽ tự kích hoạt khi bạn nhắc đến vibecode, Chủ thầu,
  Thợ thi công, TIP, RRI, Blueprint, hoặc yêu cầu build bất kỳ
  dự án phần mềm nào theo methodology có cấu trúc.

QUICKSTART — BẮT ĐẦU TRONG 2 PHÚT:

  Sau khi cài skill, mở Claude Chat hoặc Cowork và gõ:

  ┌─────────────────────────────────────────────────────────────┐
  │  Bạn:  "Chủ thầu, tôi muốn build một app quản lý kho      │
  │         hàng cho cửa hàng nhỏ."                             │
  │                                                             │
  │  Claude (Chủ thầu) sẽ tự động:                              │
  │  1. Hỏi bạn có codebase sẵn không → gửi SCAN cho Thợ      │
  │  2. Chạy RRI — phỏng vấn ngược bạn 40-60 câu thông minh   │
  │  3. Đề xuất VISION (kiến trúc + tech stack + design)       │
  │  4. Lập BLUEPRINT chi tiết → bạn duyệt "APPROVED"          │
  │  5. Sinh TASK GRAPH (các TIP) → gửi từng TIP cho Thợ      │
  │  6. Thợ code, tự test, nộp báo cáo                         │
  │  7. Chủ thầu VERIFY → báo cáo coverage %                   │
  │  8. REFINE nếu cần → ship                                  │
  └─────────────────────────────────────────────────────────────┘

  Các câu trigger khác bạn có thể dùng:
  • "Chủ thầu, phỏng vấn ngược tôi về dự án này"    → Bắt đầu RRI
  • "Debug giúp tôi lỗi này: [paste error]"          → Debug Protocol
  • "Nghiệm thu dự án"                               → QA Protocol
  • "X-Ray codebase này cho tôi"                     → X-Ray Protocol

VÍ DỤ FLOW THỰC TẾ (rút gọn):

  Bạn:   Chủ thầu, tôi cần API service quản lý đơn hàng,
         dùng Python FastAPI, deploy lên AWS.

  Chủ thầu: Chào Chủ nhà! Tôi detect đây là một API service.
         Trước tiên, bạn có codebase sẵn không?

  Bạn:   Chưa, bắt đầu từ đầu.

  Chủ thầu: OK. Tôi đề xuất VISION:
         PROJECT: Order Management API
         NATURE: API-only + CRUD + Team scale
         TECH: FastAPI + PostgreSQL + SQLAlchemy + Docker
         Tôi sẽ bắt đầu RRI để tìm hiểu chi tiết. Ready?

  Bạn:   Ready.

  Chủ thầu: [Chạy RRI — 45 câu qua 5 personas]
         ...
         RRI REPORT hoàn thành. 23 REQ-IDs, 8 quyết định.
         Chuyển sang BLUEPRINT. Duyệt?

  Bạn:   APPROVED.

  Chủ thầu: [Sinh 6 TIPs: Scaffold → DB → API → Auth → Test → Deploy]
         Gửi TIP-001 cho Thợ thi công...

  Thợ:   COMPLETION REPORT — TIP-001
         STATUS: DONE | FILES: 12 created | TESTS: 3/3 passed

  [... tiếp tục đến VERIFY → REFINE → Ship]

CẤU TRÚC THƯ MỤC:

  vibecode-kit/
  ├── README.txt              ← Bạn đang đọc file này
  ├── vibecode-kit.skill      ← Cài đặt skill vào Claude
  ├── CHANGELOG.md            ← Lịch sử thay đổi
  ├── CURRENT_VERSION.md      ← Version hiện tại + roadmap
  ├── PHILOSOPHY_V5.md        ← Triết lý nền tảng (tham khảo)
  ├── skill-v6/               ← Source code của skill v6
  │   ├── SKILL.md
  │   └── references/         ← 9 file tham khảo
  ├── Masters/                ← Prompt masters (DEBUG, QA, XRAY)
  ├── Archive/                ← Tài liệu cũ (v3, v4, tham khảo)
  └── GIAO-VIEN-THPT-MASTER.txt  ← Skill riêng (không thuộc core)

CÁC PROTOCOL ĐẶC BIỆT:

  Ngoài quy trình 8 bước chính, framework còn có:
  • Debug Protocol — Gỡ lỗi có hệ thống (9 bước)
  • QA Protocol — Nghiệm thu 3 tầng (Tier 1/2/3)
  • X-Ray Protocol — Bàn giao, đánh giá codebase
  • RRI Methodology — Phỏng vấn ngược yêu cầu (5 personas)
  • RRI-T / RRI-UX / RRI-UI — Mở rộng cho Testing & UX

─────────────────────────────────────────────────────────────────
Vibecode Kit by Lâm Nguyễn
