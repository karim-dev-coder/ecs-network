# ecs-network

A Unity spike that puts a Burst-compiled ECS and a dedicated network relay in the same project,
to see what an authoritative multiplayer loop costs when the simulation lives in
[ME.BECS](https://github.com/chromealex/ME.BECS) rather than in MonoBehaviours.

## What is inside

`Assets/ME.BECS` and `Assets/Ragon-Unity-SDK` are submodules, so the frameworks stay at their
own revisions instead of being vendored into this history.

`Assets/RagonDemo` holds the working part: `GameNetwork.cs`, a prefab registry, a Ragon
configuration asset and two scenes — `RagonStart` for entering a room and `RagonNetworkScene`
for the session itself.

`~Ragon.Relay-v1.4.1-win-x64` is the relay server binary, kept in the tree so the whole loop can
be run locally without any external service.

`Assets/Photon` sits alongside as the comparison point: the same problem solved by a transport
that is easier to start with and harder to control.

## Running it

Open the project in Unity, start the relay from `~Ragon.Relay-v1.4.1-win-x64`, then play
`RagonStart` in two builds or in an editor plus a build.

Submodules are required, so clone with:

```bash
git clone --recurse-submodules https://github.com/kimsanbaev-karim/ecs-network.git
```

## Status

This is a spike, not a library: it exists to answer whether the combination holds together, and
the answer is kept in the code rather than in a write-up. A cleaner, narrower result of the same
line of work is [ecs-lite-network](https://github.com/kimsanbaev-karim/ecs-lite-network) — a
networking extension for LeoECS Lite over Mirror.
