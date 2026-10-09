# Production gates and handoff — V1.1

## Global contract
- **Project**: Mystery Documentary Factory; US/international audience; English (US) public copy; Indonesian operating instructions.
- **Target**: 75–120s Shorts, but lock real duration from decoded audio and checked SRT. 9:16, 30fps by default.
- **Prioritize internet assets** whose usage and attribution requirements are verified. Unclear license = reference only, never APPROVED.
- **AI imagery requires explicit approval before generation**. Every image request goes in an individually saved .txt prompt. Users create assets unless they explicitly delegate generation.
- **Evidence labels**: verified fact / documented allegation / disputed claim / creative reconstruction. Never depict an AI reconstruction as authentic evidence.
- **Input missing/unreadable**: BLOCKED. No fabricated sources, media, timestamps, or screenshots.
- A casual "lanjutkan" advances only when the next gate does not require explicit approval.
- Never overwrite locked narration or approved assets without a versioned change request.

## Gate table
| Gate | Step | Required evidence | Approval |
|---|---|---|---|
| G00 | 00 Channel | visual bible, target, standards | user |
| G01 | 01 Topic | evidence-backed shortlist & selected angle | user |
| G02 | 02 Research | claim log + sources with URLs | internal QA |
| G03 | 03 Narration | reviewed exact English script | user explicitly locks |
| G04 | 04 Audio | WAV/MP3 decode, real duration and aligned SRT | internal QA |
| G05 | 05 Storyboard draft | all timeline seconds, shot IDs, asset requests | internal QA |
| G06 | 06 Internet assets | URL, licensing, rights, usage restrictions | internal QA |
| G07 | 07 AI image prompt | every required AI asset has TXT; generation deferred | user before images |
| G08 | 08 Final assets | assets readable, visual QA, finalized second-by-second plan | user if visual approval needed |
| G09 | 09 Pilot HTML | pilot playback + audio/seek/pause QA and visual review | user explicitly approves |
| G10 | 10 Full video | complete duration, MP4, QA evidence | internal QA |
| G11 | 11 Publish pack | final facts, rights, safe zones, English SEO + source URLs | user before publishing |

## Per-second timing
- Each **second row** is [start_ms, end_ms) of the real audio duration. Count = ceil(duration_ms / 1000). Last row may be shorter.
- Shot boundaries may fall anywhere within a second row; list all overlapping shot IDs. One second **does not** imply a new shot.
- Keyframes may be at 0.1s / 0.25s / 0.5s or finer where justified. Positions/scale/easing/opacity are explicit.
- Audio is the master clock: animation time derives from HTMLAudioElement.currentTime, not a free-running timer.
- STEP05 draft -> STEP06/07 licensed asset search / image prompt -> STEP08 synchronized final storyboard, not independent timing versions.
- Same source-of-truth for DOCX presentation, CSV and JSON. Cross-check number, timestamps, assets and camera at every handoff.

## Handoff payload
`PROJECT_STATE.json`, `RESEARCH_EVIDENCE.csv`, locked narration, `AUDIO_TIMELINE.json`, `STORYBOARD_PER_SECOND.csv`, `STORYBOARD_ANIMATION.json`, `ASSET_LEDGER.csv`, applicable image prompt TXT, QA report, external evidence of approval.
