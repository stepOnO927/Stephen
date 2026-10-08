# ABYSS LAB cloud setup

The public root index.html is the compiled Pages release. Develop the modular source instead.

Source archive: abyss-lab-0.13.29-cloud-final.zip (721 reviewed source files). Extract it into a separate `cloud-game` directory; do not overwrite the public release while preparing the environment.

Suggested Linux setup:

```sh
python3 -m zipfile -e abyss-lab-0.13.29-cloud-final.zip cloud-game
cd cloud-game
node tools/restore-cloud-cg.cjs
npm install
npm run build
npm test
```

Allow package registry access and https://stepono927.github.io only as needed to restore the 11 approved CGs. The restoration checks every image against the manifest's SHA-256. No real API key is required for build or isolated tests. Do not read or upload real .env files, credentials or player saves, and do not call paid APIs.

Read CLOUD-HANDOFF.md, GOAL-ACCEPTANCE.md, TASK-AUDIT.md, TASK-STATUS.md and BATCHED-UPDATES.md inside cloud-game before continuing work. Preserve all protected story text, routes, flags, endings and old saves. The full historical goal remains incomplete; do not mark it complete merely because the cloud environment builds.

Publish the environment only after setup, build and tests succeed. Then verify that a new cloud task receives the modular source. Uploading this archive alone is not a completed cloud migration.
