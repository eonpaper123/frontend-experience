# Safe-area layout

Use this reference when important content or controls can meet a display cutout, rounded corner, home indicator, system bar, browser chrome, or resizable window edge. It applies to native, hybrid, installed-web, and edge-to-edge web surfaces.

## Runtime contract

1. **Use current runtime geometry, not a device table.** Safe areas belong to the current view or viewport. Do not hardcode model-specific insets, infer a future device from screenshots, or treat one orientation as a permanent screen constant. `safearea.info` is a community lookup and teaching aid, not an official source of truth.
2. **Native layout stays container-aware.** In UIKit, constrain important content to `safeAreaLayoutGuide`; read `UIView.safeAreaInsets` only when explicit geometry is needed. In SwiftUI, prefer safe-area-aware layout and read `GeometryProxy.safeAreaInsets` only when the actual container inset is part of the behavior. Do not promote those values into a global device registry.
3. **Web edge-to-edge is opt-in.** Use `viewport-fit=cover` only when the design intentionally extends backgrounds to the screen edge. Keep essential content and controls inside padding based on the corresponding `env(safe-area-inset-top, 0px)`, `-right`, `-bottom`, and `-left` variables. When the design also needs ordinary breathing room, use `max(project spacing, safe-area inset)` rather than replacing one with the other.
4. **Recompute when the container changes.** Verify rotation, split view or multitasking, resizable windows, presentations, and changing system chrome. A device name does not determine the active window geometry.
5. **Do not conflate occlusion systems.** A device's bottom inset is not keyboard height: use the platform's keyboard-aware layout/input APIs and observe their behavior. On the web, dynamic browser chrome, the visual viewport, dynamic viewport units, and virtual-keyboard behavior need their own target-browser test.
6. **Protect function, not every pixel.** Backgrounds and decorative media may bleed to an edge; primary text, navigation, form fields, and actionable controls must remain reachable and legible. Preserve the project's spacing rhythm when the inset is zero.

Minimal web pattern:

Consume each edge once at its owning container; avoid duplicate parent/child padding. Choose `max()` for a minimum gutter or `calc(spacing + inset)` when the design explicitly requires spacing inside the safe edge. Native points, CSS pixels, physical pixels, and device scale are different coordinate systems. UIKit insets can be zero before a view is visible or when a child is already entirely safe; see [Apple's view-level definition](https://developer.apple.com/documentation/uikit/uiview/safeareainsets).

```html
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
```

```css
.edge-safe {
  padding-top: max(var(--space-page), env(safe-area-inset-top, 0px));
  padding-right: max(var(--space-page), env(safe-area-inset-right, 0px));
  padding-bottom: max(var(--space-page), env(safe-area-inset-bottom, 0px));
  padding-left: max(var(--space-page), env(safe-area-inset-left, 0px));
}
```

## Verification

- Inspect portrait and landscape, narrow and wide/resizable windows, and split or multiwindow states where supported.
- Open and close the keyboard around focused fields; verify this through the keyboard path, not by assuming safe-area padding handles it.
- Check fixed or sticky top/bottom controls, scroll endpoints, modal sheets, and edge gestures.
- Test browser zoom or platform text scaling so larger content remains inside the usable region without clipping.
- Prefer a real target device for release-critical edge cases; a simulator or community lookup is evidence for that surface only.

## Sources and adoption boundary

- [WebKit: Designing Websites for iPhone X](https://webkit.org/blog/7929/designing-websites-for-iphone-x/) documents `viewport-fit=cover`, CSS `env()` safe-area variables, orientation changes, and combining insets with ordinary padding.
- [Apple HIG: Layout](https://developer.apple.com/design/human-interface-guidelines/layout) defines safe areas in relation to the current window and system interface.
- [Apple: Positioning content relative to the safe area](https://developer.apple.com/documentation/uikit/positioning-content-relative-to-the-safe-area) covers `safeAreaLayoutGuide` and `safeAreaInsets` in UIKit.
- [Apple: GeometryProxy](https://developer.apple.com/documentation/swiftui/geometryproxy) exposes the current SwiftUI container's safe-area insets.

The [safearea.info](https://safearea.info/) walkthrough is useful for discovering cases, but its device data was not independently reconciled with Apple specifications and mixes point and pixel language. Its device-release, tool-version, and per-model numeric claims are therefore not adopted here.
