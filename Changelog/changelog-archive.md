

## v0.2
**Fixes:**
- Fixed an invalid character present in the Samples project's files, causing compilation errors on certain machines
- Fixed unassigned spawn point in Basic sample

**Known Issues:**
- Step Handling can cause errors when Burst compilation is disabled. This issue will require a future Unity.Physics package upgrade before it can be solved.
- [OnlineFPS Sample] Jitter is visible on remote client characters. This issue will require a future Unity.NetCode package upgrade before it can be solved.
- [OnlineFPS Sample] Errors pop up in the console after compilation: "Couldn't find the TypeDescriptor for the type (...)". However, these errors are inoffensive and can be ignored. This issue will require a future Unity.NetCode package upgrade before it can be solved.
- [OnlineFPS Sample] Lightmaps do not work in builds unless the "OnlineFPS" scene is opened in editor while building. This issue will require a future package upgrade before it can be solved.
- [Platformer Sample] The "standing up from ledge hanging" animation is skipped entirely due to root motion issues. This issue will require a future Unity.Animation package upgrade before it can be solved.


## v0.1
**Features:**
- Initial package

**Known Issues:**
- Step Handling can cause errors when Burst compilation is disabled. This issue will require a future Unity.Physics package upgrade before it can be solved.
- [OnlineFPS Sample] Jitter is visible on remote client characters. This issue will require a future Unity.NetCode package upgrade before it can be solved.
- [OnlineFPS Sample] Errors pop up in the console after compilation: "Couldn't find the TypeDescriptor for the type (...)". However, these errors are inoffensive and can be ignored. This issue will require a future Unity.NetCode package upgrade before it can be solved.
- [OnlineFPS Sample] Lightmaps do not work in builds unless the "OnlineFPS" scene is opened in editor while building. This issue will require a future package upgrade before it can be solved.
- [Platformer Sample] The "standing up from ledge hanging" animation is skipped entirely due to root motion issues. This issue will require a future Unity.Animation package upgrade before it can be solved.