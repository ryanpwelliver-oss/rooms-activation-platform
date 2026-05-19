# Accelerated Build Brief — Rooms Activation Platform
## Path B: Maximum Velocity (6–8 Days, Scope Optimized)

**Build Start:** 2026-05-19  
**Target Completion:** 2026-05-25 to 2026-05-27  
**Quality Gate:** NO COMPROMISES — speed through parallelism + scope cuts

**Scope Cuts:**
- ❌ Shopify POS integration (SKIPPED)
- ❌ Sonos venue audio control (SKIPPED)
- ✅ Spotify volume control (KEEP — simple integration)
- ✅ Everything else (full scope)

**Time Saved:** ~5-6 hours (removes 2 sequential workstreams)

---

## Orchestrator Directives (CRITICAL)

### PR Approval SLA
- **Target:** Approve/request changes within **10 minutes** of submission
- **Hard limit:** 20 minutes max
- **No blocking:** If merge is safe, approve immediately

### Unblocking SLA
- Any agent blocked = escalate to Ryan within **10 minutes**
- Ryan responds within **20 minutes** max
- Critical path blockers get immediate attention

### Daily Standup
- **Time:** 9 AM & 6 PM EDT (twice daily during build)
- **Duration:** 3 minutes max
- **Format:** What shipped? What's blocking? Critical path status?
- **Channel:** #orchestrator

---

## Build Phases (Sequential, But Agents Work in Parallel)

**Phase 1: Core Infrastructure (Days 1–2)**
- DB Agent: PostgreSQL schema + migrations (complete Day 1)
- Backend Agent: FastAPI core + auth + CRUD endpoints (complete Day 2)
- Firmware Agent: ESP32 baseline + WiFi (complete Day 2)
- Result: All other agents can build against these by Day 2

**Phase 2: Data Pipelines (Days 2–3)**
- Voice Agent: Omi + Whisper + Claude parsing (Day 3)
- EventFace Agent: Photo upload + Rekognition + S3 (Day 3)
- Testing Agent: Unit test framework ready (Day 2)
- Result: All two pipelines live + testable by Day 3

**Phase 3: User-Facing Apps (Days 3–5)**
- Staff App Agent: Observation UI + Room Planner (Days 4–5)
- Guest App Agent: Consent + Gallery + Timeline (Days 4–5)
- Admin Agent: Dashboard core + real-time WebSocket (Days 4–5)
- Testing Agent: Integration tests running (Days 4–5)
- Result: All three apps functional + runnable by Day 5

**Phase 4: Integrations & Polish (Days 5–6)**
- Integrations Agent: Spotify volume control ONLY (Day 6)
  - ❌ Shopify webhook receiver (SKIPPED)
  - ❌ Sonos HTTP API (SKIPPED)
- Acoustic Survey Agent: Pre-event calibration mode (Day 6)
- Testing Agent: Full integration suite + bug fixes (Day 6)
- Result: Ready for real activation by Day 7

**Phase 5: Final QA & Deployment (Day 7–8)**
- Testing Agent: Final integration test run
- All agents: Code review + merge to main
- Deploy: Vercel (admin dashboard) + VPS prep (backend)
- **BUILD COMPLETE & READY FOR REAL EVENT**

---

## Critical Path (Watch These Closely)

1. **DB Schema (Day 1)** — Blocks everyone else
2. **Backend API (Day 2)** — Blocks apps + pipelines
3. **Firmware baseline (Day 2)** — Blocks acoustic pipeline
4. **Voice pipeline (Day 3)** — Blocks admin dashboard real-time data
5. **Staff App (Day 5)** — Blocks end-to-end testing
6. **Integration tests (Day 6)** — Blocks deployment readiness

**If any of these slip 1 day, entire build slips 1 day.**

---

## Agent Work Distribution (Optimized for Speed)

| Agent | Primary Focus | Days Active | Dependencies |
|---|---|---|---|
| **DB** | PostgreSQL schema | Days 1–2 | None (first) |
| **Backend** | FastAPI core | Days 2–3 | DB complete |
| **Firmware** | ESP32 baseline | Days 2–3 | None |
| **Voice** | Omi → Whisper → Claude | Days 2–3 | Backend API ready |
| **EventFace** | Photos → Rekognition | Days 2–3 | Backend API + AWS ready |
| **Staff App** | Observation UI | Days 4–5 | Backend + WebSocket |
| **Guest App** | Consent + Gallery | Days 4–5 | Backend + EventFace |
| **Admin** | Dashboard + Charts | Days 4–5 | Backend + Voice/EventFace |
| **Integrations** | Spotify only (Day 6) | Days 5–6 | Backend complete |
| **Acoustic Survey** | Pre-event calibration | Days 5–6 | Firmware + Omi |
| **Testing** | Unit + Integration + QA | Days 2–8 | All agents (running parallel) |

**Agents that were needed for Shopify/Sonos are redeployed to testing + polish.**

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
   - Real keys swapped in during Phase 2+

2. **Use stubs for unfinished dependencies**
   - Voice agent mocks Whisper API until OpenAI ready
   - EventFace mocks Rekognition until AWS ready

3. **Parallel development**
   - Staff App + Guest App built simultaneously
   - Admin Dashboard built alongside app development

4. **Aggressive testing**
   - Testing agent starts Day 2 (before apps exist)
   - Test stubs run against all agents simultaneously

5. **PR fast-track**
   - Orchestrator approves low-risk PRs in <10 minutes
   - Only complex merges get detailed review

---

## Daily Sync Format

**#orchestrator at 9 AM & 6 PM EDT:**

```
PHASE 1: Core Infrastructure [=========> ] 100% complete
  - DB: DONE (schema + migrations merged to main)
  - Backend: IN PROGRESS (90% complete, 2h to final merge)
  - Firmware: DONE (ESP32 baseline compiling)

PHASE 2: Data Pipelines [=======>     ] 60% complete
  - Voice: IN PROGRESS (Whisper integration 50% done)
  - EventFace: QUEUED (waiting on Backend API)

CRITICAL PATH: Backend on track for merge by 4 PM today

BLOCKERS: None

SHIPPING TODAY:
  - Backend core API (merge expected by evening)
  - Voice pipeline stubs ready for testing
  - 18 new unit tests passing

TIMELINE: ON TRACK for May 25-27 completion

Next standup: Today 6 PM
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
- Spotify volume control firing commands
- Pre-event acoustic survey mode calibrating
- All 35+ integration tests passing

**Phase 5 COMPLETE when:**
- Full integration test suite passing (50+ tests)
- No critical bugs in #testing
- Code ready for real activation deployment

---

## Success Metrics (End of Day 8)

✅ 3 iOS apps (Staff, Guest, Admin web) — all runnable  
✅ 1 FastAPI backend — all endpoints working  
✅ 4 data pipelines (Voice, EventFace, Acoustic, Spotify) — fully integrated  
✅ 50+ passing tests — unit + integration  
✅ 0 critical bugs — production-ready prototype  
✅ Deployable to Vercel + VPS — ready for real event  

**NOT included (skipped scope):**
- ❌ Shopify POS integration
- ❌ Sonos venue audio control

---

## Scope Rationale

**Why cut Shopify + Sonos?**

1. **Both are Phase 4 integrations** (not on critical path until Day 6+)
2. **Both add 5-6 hours combined**
3. **Both are "nice to have"** for MVP:
   - Shopify: Can manually track sales in spreadsheet for first event
   - Sonos: Spotify standalone handles music control; Sonos is bonus
4. **Can be added in Phase 2** (post-launch) in <1 day each

**What you're keeping:**
- ✅ Full voice observation pipeline (Omi + Whisper + Claude)
- ✅ Full photo recognition (AWS Rekognition + galleries)
- ✅ All three apps (Staff, Guest, Admin)
- ✅ Real-time dashboard
- ✅ Acoustic survey calibration
- ✅ Spotify music control

This is **still a complete, deployable activation platform.**

---

## If Something Goes Wrong

**Red flag timeline:** Any critical path item >2 hours behind schedule
- Immediately escalate to Ryan
- Re-assign tasks if needed
- Reduce scope of that item (cut polish, keep MVP)
- Extend timeline to +1 day only if unavoidable

---

**Orchestrator:** This is your marching order. Execute with urgency, but don't compromise quality.

**All agents:** Move fast. Don't overthink. Ship code that works. Iterate later.

**Ryan:** Check in daily (9 AM + 6 PM EDT). Unblock anything immediately.

---

**Build starts now. Target: May 25–27, 2026. Full velocity. Shopify & Sonos skipped.**
