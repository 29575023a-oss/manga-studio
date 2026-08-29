# MangaStudio Local Production — SOURCE_BASELINE

## Upstream
Repository: bo961386926/manga-studio
Default branch: main
Latest verified upstream commit at baseline creation:
7a277f9426dc55d6d868436190cc66fb94b36c6a
Commit title: feat: visual style thumbnails & portal-based hover preview
Commit time: 2026-08-18T16:44:46Z

## Verified Upstream Capabilities
- React/Vite application with Electron entry and electron-builder configuration.
- Project state includes script, characters, scenes, shots, keyframes, video intervals, render logs and stages.
- Shot workbench binds scene and characters, supports start/end keyframes, upload/generate actions, neighboring frame copy, and video generation controls.
- Export module supports preview/download flows.
- videoMerger uses ffmpeg.wasm to concatenate rendered shot videos into a single MP4, with stream-copy first and re-encode fallback.
- Windows build script exists: electron:build:win.

## Verified Upstream Problems / Risks
1. Current upstream main CI is not clean; postinstall currently uses CommonJS require() in a package declared as ES module, causing a build-chain failure.
2. The project still contains cloud-oriented AI provider logic and API key assumptions.
3. Existing video adapter is HTTP-provider oriented; it is not a local ComfyUI/Wan worker implementation.
4. Existing apiClient forwards AI calls through backend forwarding logic; this is not the desired final local-provider architecture.
5. Current upstream storage/server path includes database/server assumptions that must be reworked or replaced for robust desktop-local persistence.
6. Current official release/build history does not provide a verified production-ready Windows desktop artifact from latest main.
7. The current app's actual state inside the temporary Replit workspace is NOT VERIFIED because inspection timed out. No Replit-generated artifact is accepted as baseline evidence.

## Source Handling Rule
The working repository should start from a complete copy/fork of upstream MangaStudio, retaining upstream license/attribution. Changes should be applied on top of that complete source tree. Do not rebuild the product from screenshots or selectively copy only visible UI pieces.
