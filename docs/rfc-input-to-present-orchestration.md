# RFC: automated input-to-present experiment orchestration

## Goal

Use the MCP bridge to make Unreal latency experiments repeatable rather than manually configured.

## Minimal workflow

1. Load a fixed benchmark map.
2. Apply a deterministic input/camera trace.
3. Set one experiment variant: frame cap, VSync, queue/latency option, or renderer setting.
4. Warm up.
5. Execute N measured repetitions.
6. Emit Unreal timing markers.
7. Start/stop an external PresentMon capture when available.
8. Write a receipt containing configuration and artifact paths.

## Receipt

The receipt must include engine build, map, resolution, refresh rate, RHI, frame cap, VSync state, repetition count, warmup duration, trace hash, start/end timestamps, and collected artifact paths.

## Acceptance

One command must reproduce the same experiment configuration and deterministic trace. Analysis is a separate stage; orchestration must not silently decide that a change is "better."
