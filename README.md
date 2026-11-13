# CSMain Expansion — 0.3.6.2-dev playtest build

[Download the compiled JAR](https://github.com/tarhuno/CSMainExpansion/raw/refs/heads/main/builds/csmain-expansion-0.3.6.2-dev.jar)

[Playtest checklist](PLAYTEST_0.3.6.2.md)

Built from the source supplied in this chat without gameplay source changes.
Java 17 `clean build`, including reobfuscation, passed. Three standalone assertion checks passed: match policy, grenade policy, and skin catalog. Minecraft startup, runtime Mixin application, and multiplayer gameplay have not been tested.

Install this addon alongside the original CSmain 1.0.0-beta.1, TaCZ 1.1.8-hotfix2, and the existing modpack dependencies on Minecraft 1.20.1 / Forge 47.4.0. The original mod and dependency JARs are not included.

Known metadata mismatch: the artifact is 0.3.6.2-dev, while mods.toml reports 0.3.5-dev.

SHA-256: `bbf26422846b8ab226ee31b0b2989c27c4a51a344be14ac52f59933c071cf56d`
