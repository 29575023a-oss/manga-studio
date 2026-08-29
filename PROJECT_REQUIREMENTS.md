# MangaStudio Local Production — PROJECT_REQUIREMENTS

## Product Goal
Build a real Windows x64 local production workstation based on the full upstream MangaStudio codebase. It must be usable for actual AI comic/short-drama production, not a demo, shell, UI prototype, or partially wired build.

## Non-Negotiable Product Requirements
1. Preserve the useful upstream workstation capabilities: projects, characters, scenes, shots, keyframes, image/video preview, asset handling, render logs, video merge/export.
2. Core production must not require a cloud platform, paid SaaS, account login, or fixed external proxy.
3. Local capability integrations:
   - Local Qwen for text/planning/instruction execution.
   - Local ComfyUI for image/keyframe/video workflows where applicable.
   - Local Khmer TTS.
   - Local FFmpeg and SoX for media processing, assembly, audio processing, and final export.
4. Accept both:
   - structured task packages; and
   - direct user instructions that are converted into local executable actions.
5. External APIs may exist only as optional plugins/providers. They must not be required for core operation.
6. Hardware target: 12 GB VRAM Windows workstation. Quality is more important than speed.
7. The system may use serial execution, lower concurrency, lower working resolution, staged generation, preflight checks, reference reuse, cache reuse, and local re-generation to fit 12 GB VRAM.
8. The system must not classify obviously bad generations as success, including:
   - blurred/deformed faces;
   - malformed hands/fingers;
   - identity drift;
   - background/layout reconstruction inconsistent with the shot;
   - strong cross-frame flicker or structural drift;
   - unusable motion artifacts.
9. Failures should be repaired locally at the smallest useful scope; one failed shot must not force rebuilding the full episode/project.
10. Final delivery must be a real Windows x64 desktop production build with a usable installer or portable executable package.

## Production Workflow Completion Gates
A release is not complete until all of the following are demonstrated with real evidence:

### Gate A — Desktop Workstation
- Launches on Windows x64.
- No mandatory login.
- No mandatory cloud/API configuration to open/create/use projects.
- Project data survives restart.

### Gate B — Project & Production Objects
- Create/open/switch projects.
- Character and scene assets persist.
- Shots persist with scene/character bindings.
- Start/end keyframes can be imported and/or generated.
- Shot video can be attached/generated and previewed.

### Gate C — Local Providers
- Qwen local provider health-check and real invocation passes.
- ComfyUI local provider health-check and real job submission/result retrieval passes.
- Khmer TTS local provider produces a real audio file and writes it back to the project.
- FFmpeg/SoX local tool detection and real processing passes.

### Gate D — Task Input
- Structured task package can create/route a real production action.
- Direct instruction can be turned into a real local action without requiring cloud AI.

### Gate E — 12 GB VRAM Safety
- Resource gate prevents unsafe concurrency.
- Video/image generation can run serially and recover after failure.
- Memory pressure or model failure does not corrupt the project.

### Gate F — Quality Control
- Generation result can be marked failed/retry without destroying prior accepted versions.
- Obvious face/hand/identity/structure defects are not auto-treated as complete.
- Local re-generation can replace only the failed asset/shot.

### Gate G — Assembly & Export
- Real shot videos can be previewed.
- Multiple shot videos can be merged into a real MP4.
- Khmer TTS audio can be incorporated into final media processing.
- Final exported file exists on disk and can be opened outside the app.

### Gate H — Production Build
- Release build succeeds from repository source.
- Windows x64 artifact is generated.
- Required runtime dependencies are bundled or detected with clear local setup guidance.
- Final build is tested against the required workflow, not just smoke-launched.

## Forbidden Completion Claims
The following do NOT count as completion:
- UI screenshots;
- mock workers;
- provider stubs;
- schema-only implementation;
- "interface reserved for future integration";
- build success without runtime production test;
- EXE that only opens a webpage;
- project shell without real media production flow;
- cloud API path presented as local production.
