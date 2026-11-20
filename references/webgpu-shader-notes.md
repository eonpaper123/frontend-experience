# WebGPU shader engineering

Use this reference for `WebGPU`, `WGSL`, custom shaders, `vgpu`, typed bindings, explicit GPU context or frame ownership, Dawn-backed rendering, and GPU pixel-regression work.

## When it changes the implementation choice

Consider [vgpu](https://github.com/vercel-labs/vgpu) only when custom GPU effects, compute, or a deliberate browser or headless rendering path serves the task and the actual target supports WebGPU. Examples include pointer-driven refraction or a procedural background beyond CSS/SVG, a GPU visualization with a defined data-to-pixel mapping, or repeatable stills from the same shader for an approved image-export workflow. A simple control transition does not need it. Preserve a working Three.js, WebGL, or native renderer unless a concrete requirement justifies changing that layer.

## Reusable engineering patterns

1. **Keep a typed shader boundary.** Use the selected version's WGSL module and reflection integration to derive binding names, types, and layouts instead of duplicating handwritten declarations. Match the build plugin and shader-import contract to the project. Types reduce host/shader drift; they do not prove shader compilation on the target, correct pixels, or frame time.
2. **Make context ownership explicit.** Pass the `Gpu` returned by `init()` through the renderer's resources and operations. Define who acquires and disposes it and its resources; avoid hidden singleton state. This is a lifecycle boundary, not a rule that an entire product may have only one GPU context.
3. **Make frame and pass ownership explicit.** Keep passes, targets, clears, draws, and input/time updates visible in one owning render loop. Vgpu's current README illustrates `frame(gpu, (f) => f.pass(target, effect))`. Do not add a second loop that competes with the project's existing frame owner.
4. **Measure the delivered feature.** Prune unused shader declarations and measure the actual shipped feature with the project's build and compression settings. Set a project-specific CI budget and inspect an increase before accepting it. The upstream README's `25 KB` gzip fullscreen-effect fixture is not a ceiling for every effect, the whole library, Node/Dawn dependencies, or total application delivery. Bundle size is not GPU performance.

## Runtime and tool selection

| Surface | Appropriate evidence and boundary |
| --- | --- |
| Browser WebGPU | Observe the actual adapter and required features on the target browser/device. Verify integration, accessibility outside the canvas, resize/DPR behavior, and frame time. Documentation or Node output does not establish browser support. |
| `vgpu/node` with Dawn | Treat it as a headless-rendering candidate for batch images or deterministic frame capture only after that backend is configured and exercised. Headless does not mean CPU-only, universally GPU-free, or real-time; backend availability and performance need their own evidence. |
| `vgpu/mock` | Use it for deterministic checks of the API, resource, and command behavior that its implementation models. Mock success or mock-returned bytes are not evidence of real shader pixels. |

Keep real-pixel verification separate from mock and command checks. Render a deterministic frame through the real backend into an explicit target, capture or read back the output, compare the intended region with an approved baseline and tolerance, and inspect any failure image. Run the same check on every backend whose pixel behavior matters. A passing image comparison proves only the exercised scene, backend, dimensions, and tolerance; it does not establish browser support, performance, or accessibility.

For future authorized use, inspect the project's package manifest and lockfile and use its existing local CLI and bundled docs. The documented commands include `docs`, `examples`, and shader `check`; these are discovery or static checks, not visual acceptance. Prefer an already-resolved local binary or `npm exec --no -- vgpu ...`. Bare `npx vgpu` may install a missing package, so it is not a read-only presence check. Inspect matching example source before adaptation and retain applicable MIT notices. Do not install a library merely to read this note.

## Source and evidence boundary

This note was checked on 2026-11-20 against the official public canary revision [`773351f`](https://github.com/vercel-labs/vgpu/tree/773351f8c96d1cbec28155c0e36ae3efd1cba135):

- the pinned [README](https://github.com/vercel-labs/vgpu/blob/773351f8c96d1cbec28155c0e36ae3efd1cba135/README.md) documents typed WGSL, explicit context/frame ownership, browser, Node/Dawn, and mock separation, and the fixture-specific size claim;
- the pinned [vgpu skill source](https://github.com/vercel-labs/vgpu/blob/773351f8c96d1cbec28155c0e36ae3efd1cba135/skills/vgpu/SKILL.md) routes users to package-versioned local documentation and warns that bare `npx`-style commands may install a missing package;
- the pinned [MCP guide](https://github.com/vercel-labs/vgpu/blob/773351f8c96d1cbec28155c0e36ae3efd1cba135/docs/topics/mcp.docs.md), [frame guide](https://github.com/vercel-labs/vgpu/blob/773351f8c96d1cbec28155c0e36ae3efd1cba135/docs/topics/concepts-frames.docs.md), and [browser-testing guide](https://github.com/vercel-labs/vgpu/blob/773351f8c96d1cbec28155c0e36ae3efd1cba135/docs/topics/browser-testing.docs.md) support the discovery, frame-ownership, and mock-versus-real-backend boundaries above; and
- the repository declares the [MIT License](https://github.com/vercel-labs/vgpu/blob/773351f8c96d1cbec28155c0e36ae3efd1cba135/LICENSE).

The project's public hosted entry points are its [MCP guide](https://vgpu.sh/docs/mcp), [agents.md](https://vgpu.sh/agents.md), and [llms.txt](https://vgpu.sh/llms.txt). They are retained as official discovery links; this update does not claim that their live hosted content was independently exercised.

Those sources were read as documentation and source evidence only. Vgpu was not installed, its MCP server was not connected, and no shader, renderer, browser, pixel baseline, or performance path was run for this reference. This repository redistributes no vgpu code or media.
