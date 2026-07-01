# Lightkit v7 — Source Map

Mục tiêu của file này là phân biệt rõ: phần nào là phương pháp nội bộ Lightkit, phần nào đến từ tài liệu Nexus của người dùng, phần nào là best practice bên ngoài có nguồn xác thực, và phần nào chỉ là heuristic cần kiểm chứng thêm.

## Nguyên tắc sử dụng nguồn

- Không trình bày một heuristic như chuẩn chính thức nếu chưa có nguồn.
- Nếu một practice đến từ best practice phổ biến nhưng chưa có citation cụ thể, ghi là `Generic best practice / needs citation`.
- Workflow con người là nguồn gốc; workflow agent chỉ là bản chuyển hóa để thực thi.
- Các nguồn trong tài liệu được dùng làm căn cứ thiết kế, không phải chỉ thị vận hành tuyệt đối.

## Source Index

Primary source list for contributors: [`../sources/README.md`](../sources/README.md).

Local Nexus source files should be kept in `skill-v7/sources/` so GitHub contributors can review the original material alongside the v7 draft.

## Source Map

| Concept | Current location | Origin | Evidence / reference | v7 Action |
|---|---|---|---|---|
| Chủ nhà / Chủ thầu / Thợ thi công | `skill-v6/SKILL.md` | Lightkit internal | Power Triangle trong v6 | Giữ như ngôn ngữ giải thích, nhưng chuyển từ platform role sang responsibility role. |
| Power Triangle | `skill-v6/SKILL.md` | Lightkit internal | Chủ nhà quyết định, Chủ thầu thiết kế, Thợ thi công implement | Giữ tinh thần phân quyền, bỏ gắn cứng Claude Chat / Claude Code. |
| SCAN | `skill-v6/SKILL.md`, `tip-and-report-formats.md` | Lightkit internal + coding-agent practice | Builder scan codebase trước khi thiết kế | Giữ, đổi thành Evidence Scan / Codebase Brief compact. |
| RRI | `skill-v6/references/rri-methodology.md` | Lightkit internal | “I see it like this — correct?” | Giữ lõi, đổi từ fixed 40–60 questions sang risk-based clarification. |
| 5 RRI personas | `rri-methodology.md`, `rri-question-bank.md` | Lightkit internal heuristic | End User, BA, QA, Developer, Operator | Giữ như lens tùy chọn; không bắt buộc mọi task phải đủ 5 persona. |
| RRI-T / RRI-UX / RRI-UI | `rri-methodology.md` | Lightkit internal heuristic | 5 personas × dimensions × stress axes | Giữ như protocol nâng cao; chỉ dùng khi QA/UX scope yêu cầu. |
| TIP | `tip-and-report-formats.md` | Lightkit internal | Task Instruction Pack | Thay bằng Execution Card compact; full TIP chỉ dùng khi handoff/risk cao. |
| Completion Report | `tip-and-report-formats.md` | Lightkit internal | DONE/PARTIAL/BLOCKED report | Thay bằng compact report mặc định; full report chỉ khi fail/block/deviation. |
| Verify Report | `tip-and-report-formats.md`, `qa-protocol.md` | Lightkit internal + QA traceability | Requirement coverage, scenario results, health checks | Giữ, đổi thành Verify Ledger compact + full Verify Report khi milestone/risk. |
| Debug Protocol | `debug-protocol.md` | Lightkit internal, dựa trên debugging discipline phổ biến | Evidence → hypotheses → root cause → fix → verify | Giữ gần như nguyên tắc; output compact trừ khi blocked/fail. |
| QA tiers | `qa-protocol.md` | Generic QA best practice / Lightkit packaging | Tier 1 core, Tier 2 robustness, Tier 3 performance/security | Giữ; ghi rõ đây là Lightkit packaging của QA practice phổ biến. |
| Gherkin AC | `SKILL.md`, `qa-protocol.md` | Cucumber / BDD | Cucumber Gherkin Reference: Given/When/Then cho executable specifications | Giữ cho acceptance criteria testable; không ép mọi task nhỏ dùng scenario dài. |
| WCAG AA | `qa-protocol.md` | W3C WCAG | W3C WCAG 2.2 | Giữ gated: UI/accessibility only. |
| Keep a Changelog | `CHANGELOG.md` | keepachangelog.com | “Changelogs are for humans, not machines” | Giữ cho release/changelog; không dùng làm workflow core. |
| Agile values | Không phải nguồn trực tiếp trong v6 | Agile Manifesto | Working software over comprehensive documentation; collaboration over contract negotiation | Dùng làm guardrail để giảm document overhead. |
| PRD | `../sources/product-triangle-nexus-workflow.md` | Product management practice via Nexus document | PRD mô tả “cái gì” | Thêm vào v7 dưới dạng PRD-lite, không biến thành tài liệu dài mặc định. |
| SSD | `../sources/product-triangle-nexus-workflow.md` | User-provided Nexus workflow | System Specification Document là cầu nối PRD và LLD | Thêm làm artifact core: SSD Options và Selected SSD. |
| LLD | `../sources/product-triangle-nexus-workflow.md` | Software design practice via Nexus document | Low-Level Design gồm API, data models, business logic detail | Thêm làm artifact trước execution. |
| Impact / Effort / Risk decision | `../sources/product-triangle-nexus-workflow.md` + product planning practice | Generic decision practice via Nexus document | Nexus phase Decision & Commitment | Giữ làm decision criteria cho SSD options. |
| ADR / Decision Record | v7 addition | Architecture decision practice / needs project citation if formalized | Dùng ghi quyết định, rationale, trade-offs | Dùng thay Contract dài khi không cần legal-style contract. |
| Runtime tooling (`vibe new`, `vibe verify`) | `CURRENT_VERSION.md` roadmap | Aspirational Lightkit roadmap | v6 ghi “No runtime tooling” | Không triển khai trong v7 docs-first MVP; chỉ cân nhắc sau case study. |
| Multi-agent orchestration | `CURRENT_VERSION.md` roadmap | Aspirational Lightkit roadmap | Auto-relay TIP/Report nằm ở v7 future của v6 roadmap | Hạ thành optional mode, không mặc định. |

## Concepts cần citation nếu muốn biến thành chuẩn chính thức

- ADR format cụ thể nên trích nguồn nếu project muốn claim là chuẩn industry.
- QA tiers hiện là Lightkit packaging; nếu muốn claim theo ISTQB/ISO/IEEE cần bổ sung nguồn riêng.
- Security checklist hiện là generic secure coding heuristic; nếu muốn chuẩn hóa cần mapping sang OWASP ASVS / OWASP Top 10 / CWE tùy scope.
- DevOps checklist như RPO/RTO, blue-green/canary, monitoring cần nguồn vận hành riêng nếu đưa vào core.

## Quy tắc cập nhật

Khi thêm concept mới vào v7:

1. Ghi concept vào bảng Source Map.
2. Chỉ rõ origin.
3. Nếu origin là external standard, thêm link/source.
4. Nếu origin là Lightkit internal, ghi rõ là internal heuristic/protocol.
5. Nếu chưa có nguồn, đánh dấu `needs citation` thay vì trình bày như chuẩn đã xác thực.
