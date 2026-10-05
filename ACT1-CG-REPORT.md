# ACT I Empty Dish CG — 0.12.4-preview

- Asset: assets/story/cg/act1_empty_dish.png. Exact supplied image, SHA256 6e749a134d1e9f936fcc1e85100f24f8b63ad41ea0555a44f8462a1fc460eb5a.
- ID: CG_ACT1_EMPTY_DISH. Chapter: ACT I — THE ROUTINE. Scene: project_survival (survival alias).
- Appears on existing zero-based line 6: 食盆到位，灯调暗，空气阀打开。它在第三个动作之后放松下来。
- Before that, ACT I starts on black; the Prologue repair CG does not leak across chapter boundaries.
- Original scene text and protected scene hashes unchanged. No new dialogue or narrative consequences.
- 800ms fade; nine-second scale 1.00→1.03; vertical drift 2px; transform origin 63% 66% toward hand/hatch/dish. No direct character animation.
- Existing glass dialogue, Space, motion preference, reduced-motion, save/load/rollback retained. No schema change. Old positions restore this image if already at/after this beat; unlock happens when actually viewed.
- Spoiler-safe gallery: hidden artwork before view; collection exported/imported with existing meta system.
- Jack shown rear/low head; permanent cap rule retained.
- Automated data tests pass: trigger, exact image hash, restrained motion, quick-load and export/import. Protected hash and 20-chapter narrative integration tests pass.
- Real Chromium browser: 1366×768 and 768×1024 touch emulation; image decoded at 1672×941, object-fit contain, first-view gallery, quick/load/reload/rollback and no overflow; zero page errors. This is not physical iPad Safari testing.
