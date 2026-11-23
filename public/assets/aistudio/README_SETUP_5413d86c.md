# RUN RIZZY — Unity C# starter gameplay foundation

This package contains source scripts for a playable endless-runner foundation. It is **not** a finished, tested commercial game or a complete Unity project: Unity Editor, art/audio assets, device builds, backend services and QA are required before release.

## Recommended baseline
- Unity 2022.3 LTS or a currently supported Unity LTS version
- 3D (URP recommended for mobile)
- Android Build Support and iOS Build Support modules
- TextMeshPro package
- Input handling: scripts use Unity's built-in touch input and keyboard fallback

## Scene setup
1. Create a new 3D URP project named `RUN_RIZZY`.
2. Copy `Assets/RUNRIZZY` from this package into the project's `Assets` folder.
3. Create a `GameManager` object and attach `GameManager`.
4. Create a `PowerUpRuntime` object and attach `PowerUpRuntime`.
5. Create a player capsule (or your licensed/original character model). Add `CharacterController` and `RunnerController`. Set its starting position to `(0, 1, 0)`.
6. Create a track segment prefab: a floor mesh/cube with length 40 units, add `TrackSegment`, and assign it to a `TrackSpawner` object. Set `segmentLength` to 40 and assign the player Transform (or let it auto-find the RunnerController). Track pieces are placed ahead and cleaned up behind the moving player.
7. Create obstacle prefabs with colliders set to `Is Trigger`, add `Obstacle`.
8. Create coin prefabs with trigger colliders, add `CoinPickup`.
9. Create power-up prefabs with trigger colliders, add `PowerUpPickup`; select its type in Inspector.
10. Add a Canvas with TextMeshPro labels and assign them to `HUDController`.
11. Add UI Buttons and connect their OnClick events to `GameManager.StartRun`, `Pause`, `Resume`, and `RestartRun`.
12. For a quick test, make a long floor, three visible lanes, a camera following behind the player, and place obstacle/coin prefabs in front of the player.

## Important implementation notes
- TrackSpawner creates track segments ahead of the moving player and destroys passed segments. For a shipping build, replace Instantiate/Destroy with a tested object pool and add a deterministic segment/obstacle pattern generator.
- `Jetpack` and `SuperSneakers` are represented in the power-up enum but need dedicated movement, VFX and animation implementations.
- Magnet pickup attraction, hoverboard collision protection, score multiplier integration, character abilities, shop transactions, missions, cloud saves, leaderboards and analytics are not implemented yet.
- Use original characters or assets you have permission to use. Do not copy Subway Surfers or Free Fire character models, names, logos, sounds or other protected assets without authorization.
- Before release: profile on low/mid/high Android devices and supported iPhones; test touch controls, app pause/resume, scene reloads, memory, battery, offline behavior, purchases and privacy disclosures.
- iOS builds require macOS and Xcode. Google Play and Apple App Store submission require developer accounts, signing, store assets, privacy details and review; Unity cannot publish automatically by itself.

## First playable milestone
A runner moves forward, switches among three lanes, jumps/slides, collects coins, hits obstacles to end the run, and displays score/distance/best score. Build the scene as described above to test this milestone.
