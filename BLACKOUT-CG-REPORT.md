# Blackout Back-to-Back CG — 0.12.6-preview · 2026-10-06

- Exact source copied to assets/story/cg/act1_blackout_back_to_back.png. SHA256 a210b55d05ec2ed7411c4c8337b8174543da28b9c8385924360f3c5c3dfa2239.
- ID CG_ACT1_BLACKOUT_BACK_TO_BACK; requested collection/display chapter ACT I — THE ROUTINE; scene daily_blackout.
- Cue at existing zero-based line19: 他在玻璃外面坐下，背靠着舱体。手电放在地上，光朝着天花板。
- Earlier blackout, accusation, Jack leaving, repair and return remain text on black; do not reveal seated image before the seating beat. Following quiet lines 灯。不是你。 and 你走了。 remain verbatim.
- 800ms fade, eleven-second scale1.00→1.025, 2px horizontal drift toward glass, origin53%59%. No brightness filter, character animation or distortion; image bytes unchanged. No extra light overlay.
- Existing approved daily_blackout schedule remains after ACT III (chapter index4). CG metadata/header use requested ACT I label only; no relocation of protected narrative or language-stage progression.
- Unlock on actual view; hide unknown gallery thumbnail. Existing save cursor automatically restores correct image, no save schema change and no retroactive grant. Rollback before line19 returns to black.
- Jack face hidden; permanent rear/side/lowered-head art direction unchanged.
- Unit tests pass: exact source hash, cue before/after19, motion limits, quick-load and collection export/import. Protected scene hashes, bilingual approved scenes and 20-chapter flow pass.
- Chromium desktop1366×768 and touch768×1024: exact image decode, motion, spoiler collection, quick/load/reload/rollback, no horizontal overflow or page errors. Not a physical iPad Safari test.

- Boundary check found BACK retained keyboard focus on its button, so Space could click BACK again. Rollback now returns focus to the story panel; Space advances correctly after rollback.
