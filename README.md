# CSMain Expansion — 0.3.6.13-dev playtest build

[Download 0.3.6.13-dev JAR](https://github.com/tarhuno/CSMainExpansion/raw/refs/heads/main/builds/csmain-expansion-0.3.6.13-dev.jar)

[Комплект Escort, радар и чек-лист (RU)](PLAYTEST_0.3.6.13_RU.md)

Removes Escort kits before CSmain death processing and checks late inventory restores after respawn. Retains cleanup areas until the final pre-spawn equipment sweep, includes untagged saddle/rod drops in Escort arenas, and cleans marked dropped kits on round transitions and match stop/reset.

T radar shows unclaimed hostages until first saddling. Nearby CT see a green evacuation rectangle on the radar within 24 blocks of the zone. No world outline is rendered.

Java 17 clean build and twelve standalone tests passed. Minecraft/LAN verification remains pending. Update server and all clients: radar protocol is now version 4.

[JSON knife catalog (0.3.6.12)](PLAYTEST_0.3.6.12_RU.md)

[Map event commands and Escort kit lifetime (0.3.6.11)](PLAYTEST_0.3.6.11_RU.md)

[Duel and mode profiles (0.3.6.10)](PLAYTEST_0.3.6.10_RU.md)
