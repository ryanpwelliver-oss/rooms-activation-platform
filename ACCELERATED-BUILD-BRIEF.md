# Accelerated Build Brief — Rooms Activation Platform
## Path B: Maximum Velocity (10–12 Days)

**Build Start:** 2026-05-19  
**Target Completion:** 2026-05-29 to 2026-05-31  
**Quality Gate:** NO COMPROMISES — speed through parallelism, not by cutting scope

---

## Orchestrator Directives (CRITICAL)

### PR Approval SLA
- **Target:** Approve/request changes within **15 minutes** of submission
- **Hard limit:** 30 minutes max
- **No blocking:** If merge is safe, approve immediately
- **Conflict resolution:** Request rebase + re-review (same 15 min SLA)

### Unblocking SLA
- Any agent blocked = escalate to Ryan within **15 minutes**
- Ryan responds within **30 minutes** max
- Critical path blockers get immediate attention

### Daily Standup
- **Time:** 9 AM EDT (every morning during build)
- **Duration:** 5 minutes max
- **Format:** What's blocked? What's shipping today? Any risks?
- **Channel:** #orchestrator

### Build Phases (Sequential, But Agents Work in Parallel)

**Phase 1: Core Infrastructure (Days 1–3)**
- DB Agent: PostgreSQL schema + migrations (complete Day 1)
- Backend Agent: FastAPI core + auth + CRUD endpoints (complete Day 2)
- Firmware Agent: ESP32 baseline + WiFi (complete Day 2)
- Result: All other agents can build against these by Day 3

**Phase 2: Data Pipelines (Days 3–5)**
- Voice Agent: Omi + Whisper + Claude parsing (Day 4)
- EventFace Agent: Photo upload + Rekognition + S3 (Day 4)
- Testing Agent: Unit test framework ready (Day 3)
- Result: All three pipelines live + testable by Day 5

**Phase 3: User-Facing Apps (Days 5–9)**
- Staff App Agent: Observation UI + Room Planner (Days 6–7)
- Guest App Agent: Consent + Gallery + Timeline (Days 7–8)
- Admin Agent: Dashboard core + real-time WebSocket (Days 7–8)
- Testing Agent: Integration tests running (Days 8–9)
- Result: All three apps functional + runnable by Day 9

**Phase 4: Integrations & Polish (Days 9–11)**
- Integrations Agent: Shopify + Spotify + Sonos (Days 9–10)
- Acoustic Survey Agent: Pre-event calibration mode (Day 10)
- Testing Agent: Full integration suite + bug fixes (Days 10–11)
- Result: Ready for real activation by Day 11

**Phase 5: Final QA & Deployment (Day 12)**
- Testing Agent: Final integration test run
- All agents: Code review + merge to main
- Deploy: Vercel (admin dashboard) + VPS prep (backend)

---

## Critical Path (Watch These Closely)

1. **DB Schema (Day 1)** — Blocks everyone else
2. **Backend API (Day 2)** — Blocks apps + pipelines
3. **Firmware baseline (Day 2)** — Blocks acoustic pipeline
4. **Voice pipeline (Day 4)** — Blocks admin dashboard real-time data
5. **Staff App (Day 7)** — Blocks end-to-end testing
6. **Integration tests (Day 9)** — Blocks deployment readiness

**If any of these slip 1 day, entire build slips 1 day.**

---

## Agent Work Distribution (Optimized for Speed)

| Agent | Primary Focus | Days Active | Dependencies |
|---|---|---|---|
| **DB** | PostgreSQL schema | Days 1–2 | None (first) |
| **Backend** | FastAPI core | Days 2–3 | DB complete |
| **Firmware** | ESP32 baseline | Days 2–3 | None |
| **Voice** | Omi → Whisper → Claude | Days 3–4 | Backend API ready |
| **EventFace** | Photos → Rekognition | Days 3–4 | Backend API + AWS ready |
| **Staff App** | Observation UI | Days 5–7 | Backend + WebSocket |
| **Guest App** | Consent + Gallery | Days 6–8 | Backend + EventFace |
| **Admin** | Dashboard + Charts | Days 6–8 | Backend + Voice/EventFace |
| **Integrations** | Shopify, Spotify, Sonos | Days 8–10 | Backend complete |
| **Acoustic Survey** | Pre-event calibration | Days 9–10 | Firmware + Omi |
| **Testing** | Unit + Integration + QA | Days 3–12 | All agents (running parallel) |

---

## No-Compromise Standards

- **Code quality:** All tests pass before merge
- **Security:** No exposed credentials, .env never committed
- **Architecture:** No technical debt shortcuts
- **Testing:** Unit + integration tests required
- **Documentation:** Agent YAML configs + PR descriptions clear

---

## Acceleration Tactics (Quality-Safe)

1. **Mock external services** early
   - Agents don't wait for actual API keys
   - Real keys swapped in during Phase 3+

2. **Use stubs for unfinished dependencies**
   - Voice agent mocks Whisper API until OpenAI ready
   - EventFace mocks Rekognition until AWS ready

3. **Parallel development**
   - Staff App + Guest App built simultaneously (not sequentially)
   - Admin Dashboard built alongside app development

4. **Aggressive testing**
   - Testing agent starts Day 3 (before apps exist)
   - Test stubs run against all agents simultaneously

5. **PR fast-track**
   - Orchestrator approves low-risk PRs in <5 minutes
   - Only complex merges get detailed review

---

## Daily Sync Format

**#orchestrator at 9 AM EDT:**

```
PHASE 1: Core Infrastructure [=====>    ] 30% complete
  - DB: DONE (schema + migrations merged)
  - Backend: IN PROGRESS (75% complete, 2h to merge)
  - Firmware: BLOCKED on ESP32 board drivers (ESCALATED)

CRITICAL PATH: Backend on track, Firmware unblocked by 10 AM

TODAY'S SHIPPING:
  - Backend core API (merge expected by 2 PM)
  - Voice pipeline stubs ready
  - 12 new integration tests passing

RISKS: None right now

Next standup: Tomorrow 9 AM
```

---

## Definitions of "Done"

**Phase 1 COMPLETE when:**
- DB migrations working (all tables + indexes + seed data)
- Backend API responding (all CRUD endpoints tested)
- Firmware compiling (no build errors)

**Phase 2 COMPLETE when:**
- Voice pipeline: Omi → Whisper → Claude → DB (end-to-end working)
- EventFace pipeline: Photo upload → Rekognition → Guest record (working)
- Unit test framework passing 100% of DB + Backend tests

**Phase 3 COMPLETE when:**
- Staff App runs on iOS (Xcode or Flutter simulator)
- Guest App runs on iOS (shows photo gallery, real or mock data)
- Admin Dashboard loads in browser (real-time WebSocket connected)

**Phase 4 COMPLETE when:**
- Shopify webhook receiver accepting orders
- Spotify volume control firing commands to Sonos
- Pre-event acoustic survey mode calibrating

**Phase 5 COMPLETE when:**
- Full integration test suite passing (50+ tests)
- No critical bugs in #testing
- Code ready for real activation deployment

---

## Success Metrics (End of Day 12)

✅ 3 iOS apps (Staff, Guest, Admin web) — all runnable  
✅ 1 FastAPI backend — all endpoints working  
✅ 6 data pipelines — fully integrated  
✅ 50+ passing tests — unit + integration  
✅ 0 critical bugs — production-ready prototype  
✅ Deployable to Vercel + VPS — Day 1 ready  

---

## Scope vs. Speed Trade-offs (NONE)

This build delivers **100% of the 16-step plan** in 10–12 days, not by cutting features, but by:
1. Crushing dependencies early (Days 1–3)
2. Parallel execution on non-blocking tasks
3. Aggressive but safe PR approval
4. Daily unblocking (no agent waits >1 hour)
5. Testing integrated from Day 3 (not bolted on at the end)

---

## If You See Slippage

**Red flag timeline:** Any critical path item >1 day behind schedule
- Immediately escalate to Ryan
- Re-assign tasks if needed
- Reduce scope of that item (cut polish, keep MVP)
- Extend timeline to +1 day only if unavoidable

---

**Orchestrator:** This is your marching order. Execute with urgency, but don't compromise quality.

**All agents:** Move fast. Don't overthink. Ship code that works. Iterate later.

**Ryan:** Check in daily at 9 AM EDT. Unblock anything in your power immediately.

---

**Build starts now. Target: May 29–31, 2026. Full velocity.**
