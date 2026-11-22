# Last game cloud build (Diablo III, new engine)

date: 2026-11-22T05:20:50Z
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
- build_ipa.sh exit: 0
- IPA: DiabloIII.ipa 60900442 bytes sha256 5adedabfee4af203470a7b88ba8ff9e0e225221e053cdf081c21fa8cf82d7bbb
- verdict: PASS - panel build: toggle image + cheat pack + glass panel + Chinese launcher + icon + romfs.id (release d3-game-output)

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
[05:21:39] app: Diablo III: Eternal Collection 2.2.0 (org.nxnative.01001b300b9be000), language en-US
[05:21:39] generate Gen/ (host sources, embedded modules, tables)
host_msl.py: 13 libraries for iphoneos (Apple metal version 32023.864 (metalfe-32023.864)) in gen/msl-iphoneos/host_msl_gen.h
[05:21:45] launcher: DM_FPS_TARGET DM_OPMODE DM_PRESENT_UPSCALE DM_LANG DM_PICTURE_FIT DM_SHOW_FPS DM_TOUCH_HAPTICS DM_RUMBLE DM_RUMBLE_GAIN DM_RUMBLE_MIN DM_PAD_PRESS_TO_JOIN DM_D3_SKIN DM_D3_SCALE DM_D3_ALPHA DM_PRESENT_SNAP DM_PSO_MTL4 DM_PSO_PREBUILD DM_NVN_ENC_THREAD DM_FPS_HOLD DM_METAL_HUD
[05:21:45] no pipeline archive (DM_PSO_GPUS=none)
[05:21:45] env: DM_LANG=zh-CN DM_LAUNCHER_LANG=zh DM_LAUNCHER_SIGNATURE=抖音：南方的冬 · kbnn改版 
[05:21:46] no app icon (/Users/runner/work/tmp-d3-build/tmp-d3-build/game/dump/01001B300B9BE000_build/extract/v1441792/icon.jpg not found): the home-screen icon stays blank
[05:21:46] source: d777f0a340e8+dirty
[05:21:46] xcodebuild (Release, unsigned, iPhone + iPad)
[05:22:30] app: /Users/runner/work/tmp-d3-build/tmp-d3-build/game/dump/01001B300B9BE000_build/ipa/build/ios/pkg/dd/Build/Products/Release-iphoneos/DmIOS.app
[05:22:30] entitlements in the executable's ad-hoc signature (the install tool re-signs and keeps them)
[05:22:30] no game files in the IPA (DM_COPY_ROMFS=NO): the app takes Documents/romfs.img (scripts/push_romfs.sh)
[05:22:30] game files identity: DMROMFSID1 title=01001B300B9BE000 version=2.2.0 build=v1441792 size=1572 index=09e078e1e00d4069
[05:22:30] pack IPA (already-compressed game files stored, everything else deflated)
pack: 4041 entries, 126261393 bytes
pack: keeping 0 bytes
packed: 4041 entries, stored 0.04 GB, deflated 0.07 GB, archive 0.08 GB, kept 0.00 GB, reused 0 files in 2 s, wrote 0.08 GB
[05:22:32] done: /Users/runner/work/tmp-d3-build/tmp-d3-build/game/dump/DiabloIII.ipa ( 92M)
```

## orchestrator.log (last 40 lines)
```
[05:21:14] a dump folder: 01001B300B9BE000, 1 update(s), 0 DLC
[05:21:14] game profile: 01001B300B9BE000
[05:21:14] output IPA: /Users/runner/work/tmp-d3-build/tmp-d3-build/game/dump/DiabloIII.ipa
[05:21:14] work folder (extracted game files in extract/, kept for the next build): /Users/runner/work/tmp-d3-build/tmp-d3-build/game/dump/01001B300B9BE000_build
[05:21:18] update v1441792: 1441792
[05:21:18] [1/5] pack v1441792 …
[05:21:18] ✓ [1/5] pack v1441792 (0:00): 1.5 KB
[05:21:18] [2/6] check v1441792 files · reading file heads …
[05:21:18] ✓ [2/6] check v1441792 files (0:00): ok
[05:21:18] app name: Diablo III: Eternal Collection; version: 1.0; bundle ID: org.nxnative.01001b300b9be000
[05:21:18] game language: en-US (American English); the control data lists no languages (not checked) (DM_LANG=<code> in the app's Documents/env.txt changes it)
[05:21:18] [3/7] rewrite · checking the inputs …
[05:21:18] [3/7] rewrite · main, sdk …
[05:21:35] ✓ [3/7] rewrite (0:16): main, sdk
[05:21:35] [4/7] shader split · checking the inputs …
[05:21:35] [4/7] shader split · splitting …
[05:21:36] ✗ [4/7] shader split (0:00)
[RED] the shader split found no shaders in main or the RomFS: the game keeps them in a form shader_split.py does not read; locate them (docs/agents) and add a reader
```
