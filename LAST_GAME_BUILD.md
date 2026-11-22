# Last game cloud build (Diablo III, new engine)

date: 2026-11-22T04:45:00Z
runner: macOS ARM64
ProductName:		macOS
ProductVersion:		15.8.2
BuildVersion:		24H232
Xcode 26.3
Build version 17C529
iphoneos SDK: 26.2
upstream ref: d777f0a340e87f3d87ebd8905f2a99b9ba497134
Python 3.15.2
11.0.100

- orchestrator exit: 1 (1 at the shader split is expected; the pack is done by the bypass step)
- build_ipa.sh exit: 1
- IPA: none
- verdict: FAIL or PARTIAL - see build_ipa.log tail below

## patch.log (SDK 26 compatibility patches)
```
REMOVED /Users/runner/work/tmp-d3-build/tmp-d3-build/upstream/dm/ios/Sources/DmGamepad.m: if (@available(iOS 27.0, *)) { g_motion.deviceMotionBody = body; g_motion_body = YES; LOG("front end: the phon
REMOVED /Users/runner/work/tmp-d3-build/tmp-d3-build/upstream/dm/gfx/nvn/nvn_mtl.m: sc.colorContentOffsetX = (NSUInteger)a.base[DLSS_COLOR][0]; sc.colorContentOffsetY = (NSUInteger)a.base[DLSS_C
REMOVED /Users/runner/work/tmp-d3-build/tmp-d3-build/upstream/dm/gfx/nvn/nvn_mtl.m: sc.depthContentOffsetX = (NSUInteger)a.base[DLSS_DEPTH][0]; sc.depthContentOffsetY = (NSUInteger)a.base[DLSS_D
REMOVED /Users/runner/work/tmp-d3-build/tmp-d3-build/upstream/dm/gfx/nvn/nvn_mtl.m: sc.motionContentOffsetX = (NSUInteger)a.base[DLSS_MOTION][0]; sc.motionContentOffsetY = (NSUInteger)a.base[DLS
REMOVED /Users/runner/work/tmp-d3-build/tmp-d3-build/upstream/dm/gfx/nvn/nvn_mtl.m: sc.outputOffsetX = (NSUInteger)a.base[DLSS_OUTPUT][0]; sc.outputOffsetY = (NSUInteger)a.base[DLSS_OUTPUT][1];
INSERTED before 'static int boot_env(void) {' in /Users/runner/work/tmp-d3-build/tmp-d3-build/upstream/dm/ios/Sources/main.m
INSERTED line after 'setenv("DM_FONT_DIR"' in /Users/runner/work/tmp-d3-build/tmp-d3-build/upstream/dm/ios/Sources/main.m
DmGameMenu.h: dm_cheat_* prototypes added
INSERTED after '    [self.view addSubview:self.pad];' in /Users/runner/work/tmp-d3-build/tmp-d3-build/upstream/dm/ios/Sources/front_ios.m
build_ipa.sh: cheats staging inserted
CheatPanel.swift copied into dm/ios/Sources/
gamepad_patch.diff applied
skin_patch.diff applied
pad2_patch.diff applied
pad3_patch.diff applied
fps_host_patch.diff applied
fps120_host_patch.diff applied
fps_ios_screen_patch.diff applied
pad4_patch.diff applied
patch done: frontend patches applied
```

## build_ipa.log (last 100 lines)
```
main.patched.bin sha256: 5ca61901a5265821e002c0fe55d62b2dbb556d40a7b5b67499b1068f03144ca4 (toggle build expects 5ca61901a5265821e002c0fe55d62b2dbb556d40a7b5b67499b1068f03144ca4)
toggle image staged over main.patched.bin
[04:45:43] FAIL: the iOS shader libraries /Users/runner/work/tmp-d3-build/tmp-d3-build/game/dump/01001B300B9BE000_build/sh/ios/b-3ee493b2c3a4 are not a full build from this profile's current tables (inputs 46e19abc0d68; their stamp: game 01001B300B9BE000 inputs b56384377b1b ): build them again (IOSOUT=/Users/runner/work/tmp-d3-build/tmp-d3-build/game/dump/01001B300B9BE000_build/sh/ios dmsh_build.py ...)
```

## orchestrator.log (last 40 lines)
```
[04:45:22] a dump folder: 01001B300B9BE000, 1 update(s), 0 DLC
[04:45:22] game profile: 01001B300B9BE000
[04:45:22] output IPA: /Users/runner/work/tmp-d3-build/tmp-d3-build/game/dump/DiabloIII.ipa
[04:45:22] work folder (extracted game files in extract/, kept for the next build): /Users/runner/work/tmp-d3-build/tmp-d3-build/game/dump/01001B300B9BE000_build
[04:45:24] update v1441792: 1441792
[04:45:24] [1/5] pack v1441792 …
[04:45:25] ✓ [1/5] pack v1441792 (0:00): 1.5 KB
[04:45:25] [2/6] check v1441792 files · reading file heads …
[04:45:25] ✓ [2/6] check v1441792 files (0:00): ok
[04:45:25] app name: Diablo III: Eternal Collection; version: 1.0; bundle ID: org.nxnative.01001b300b9be000
[04:45:25] game language: en-US (American English); the control data lists no languages (not checked) (DM_LANG=<code> in the app's Documents/env.txt changes it)
[04:45:25] [3/7] rewrite · checking the inputs …
[04:45:25] [3/7] rewrite · main, sdk …
[04:45:40] ✓ [3/7] rewrite (0:15): main, sdk
[04:45:40] [4/7] shader split · checking the inputs …
[04:45:40] [4/7] shader split · splitting …
[04:45:41] ✗ [4/7] shader split (0:00)
[RED] the shader split found no shaders in main or the RomFS: the game keeps them in a form shader_split.py does not read; locate them (docs/agents) and add a reader
```
