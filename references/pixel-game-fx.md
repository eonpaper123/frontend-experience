# Procedural pixel-game effects

[patch-gg/pixelfx](https://github.com/patch-gg/pixelfx) is an optional JavaScript library for procedural pixel-art game effects. Its README describes direct use in web games and frame export for other engines. These are upstream capabilities, not proof of compatibility, performance, or installation in a particular project.

The repository is licensed under [MIT](https://github.com/patch-gg/pixelfx/blob/main/LICENSE), with additional attribution guidance in its [NOTICE](https://github.com/patch-gg/pixelfx/blob/main/NOTICE.md). Review the selected effect and its notices before copying or distributing it. The project separately excludes its gallery font from the blanket MIT grant; do not assume every demo asset has the code's license.

Before choosing an effect, confirm the game's renderer, pixel scale, layering, lifetime, export format, target devices, and expected simultaneous effect count. Inspect the selected effect's actual API rather than assuming all examples share parameters. If using a seeded effect for reproducible review, record its real inputs. Inspect the rendered frames or sprite sheet for silhouette, timing, looping seams, and pixel density, then measure runtime cost on the target device.

This is a game-asset reference, not a general source for form controls, status messages, or loading indicators. UI feedback adapted from games should remain subordinate to real state and accessibility; see [interaction-feedback-patterns.md](interaction-feedback-patterns.md). No code, images, fonts, or generated effects are included here.
