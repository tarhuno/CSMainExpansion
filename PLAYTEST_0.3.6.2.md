# 0.3.6.2-dev playtest checklist

Status: Java 17 clean build and JAR reobfuscation passed. Standalone MatchPolicyRegressionTest, GrenadePolicyTest, and SkinCatalogTest passed with assertions enabled. No Minecraft runtime tests have been performed. All scenarios below are pending.

Before testing, use a copy of the world and back up config/killfeedtacz_state.json. Do not delete or replace the live shop configuration. The add-on cannot reconstruct missing custom weapons or skins without an actual configuration backup.

## 1. Startup and multiplayer — highest priority
- Launch a client and dedicated server with the existing modpack, Forge 47.4.0, Minecraft 1.20.1, CSmain 1.0.0-beta.1 and TaCZ 1.1.8-hotfix2.
- Check logs for failed Mixins, missing methods, linkage errors, and packet errors.
- Join with at least two clients; check team selection, disconnect/rejoin, and server restart.
- The compiled add-on is 0.3.6.2-dev; mods.toml still displays 0.3.5-dev.

## 2. Shop preservation — highest priority
- Record existing weapons, custom skins, templates, and prices before testing.
- Open the shop and buy starter pistols, rifles, armor, grenades, and skin variants in both Bomb and Escort.
- Switch modes outside a match, then restart the server and compare the saved catalog.
- Expect existing weapons and skins to remain. Intended balance changes include XM1014 $3400, armor $650, armor/helmet $1000, and removal of M870.
- Look for an empty shop or ConcurrentModificationException during shop synchronization, joining, and mode changes.

## 3. Mode and team purchase rules
- Bomb: Defuse Kit $400; Escort-only goods hidden/unavailable.
- Escort: CT Escort Kit $400 and Flash Shield $1200; Defuse Kit hidden/unavailable.
- Confirm server rejects wrong-team/mode purchases, including while changing maps or teams.
- Escort Kit must grant saddle plus carrot-on-a-stick together.
- Test full inventory, insufficient money, repeated purchase, and purchases near the end of buy time.

## 4. Escort hostage mechanics
- Configure /csx gamemode escort, /map escort count, /map escort spawn add, and /map escort evac pos1/pos2.
- Check configured pig count and spawn locations each round.
- Unridden pigs must stay stationary and resist damage; T cannot saddle/ride them; CT can saddle and steer.
- Each pig's first saddling should add 60 seconds once and notify T. Test saddling before LIVE and during LIVE.
- CT extraction of one pig should end the round once, award CT the win, and apply appropriate economy.
- Check elimination and timeout outcomes, missing opponents, and spectator interactions.
- Check cleanup/reset on next round, match end, map changes, and server restart. Mid-round restart recovery is a known unresolved area.

## 5. Escort equipment across rounds
- Survive a round with saddle/rod, then start the next round.
- Check conversion/restoration of equipment without extra kits, duplicated items, or repeated charges.
- Repeat with death, full inventory, team switch, and mode switch.

## 6. Warmup respawn
- Die at least three times in WARMUP; test both pressing and not pressing the respawn button.
- Expect roughly 40 server ticks before returning, correct team spawn, Classic Knife (cs2_wt:css), and starting pistol.
- Check for duplicate respawns, retained weapons, lost team membership, and client/server desynchronization.
- End warmup while a respawn is pending; check logout/rejoin and team removal.
- Repeat in solo and a 2v2 match. Under lag, 40 ticks can exceed two real seconds.

## 7. Match progression and persistence
- With maxrounds=24, check side swap after 12 completed rounds, money reset to $800, and equipment cleanup.
- Verify 12:12 draw, win/loss rewards, and loss bonus.
- Confirm UUID-based team/voluntary spectator state survives rejoin and restart.
- Existing per-world maps, spawn points, bounds, and roster data must remain usable.

## 8. Inventory, combat, and Bomb regressions
- Check armor purchase/replacement, halftime cleanup, and absence of duplication.
- Allow two flashes, at most four grenades total, and at most one of each other grenade type; verify team restrictions.
- Defuse Kit must not be droppable; verify knife/skin/silencer selections persist.
- Defuse with different weapons and slot changes: switching slots should preserve progress; movement over about 0.2 blocks or significant camera rotation should cancel.
- Test planting, freeze attack/grenade restrictions, cleanup of active grenades, and buy-time enforcement.
- Check FLYING kill labels after a genuine jump versus simply falling from a ledge.

## 9. Radar and spectators
- Compare orientation facing N/E/S/W and check TAB map bounds and map switching.
- Check enemy markers behind solid walls, outside view, and across dimensions.
- T hostage markers must show the original position after saddling, not track the moving pig.
- Check spectator persistence and team return commands.
- Full TaCZ first-person spectator viewmodel is unfinished.

## Reporting
For each failure, record scenario, expected/actual behavior, mode, round phase, player/team count, reproduction steps, and relevant client/server logs. Mark outcomes PASS, FAIL, or NOT TESTED; compilation alone does not establish gameplay correctness.
