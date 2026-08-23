# StyleSplittedButton

> [!IMPORTANT]
> **StyleSplittedButton now lives in [UIFoundation](https://github.com/Mx-Iris/UIFoundation), and
> this repository is archived.** It is kept read-only for history; the button subclasses ship there
> in `UIFoundationAppKit`, with no trait to enable — importing `UIFoundation` is enough.

All thirteen classes keep their names (`PushButton`, `RadioButton`, `HelpButton`,
`FlexiblePushButton`, `SwitchButton`, `ToolbarButton`, `AccessoryBarButton`,
`AccessoryBarActionButton`, `BadgeButton`, `DisclosureButton`, `PushDisclosureButton`,
`ShadowlessSquareButton`, `SmallSquareButton`), so migrating is a matter of replacing the dependency
and the import:

```swift
.package(url: "https://github.com/Mx-Iris/UIFoundation", from: "0.13.0")
```

```swift
import UIFoundation

let button = PushButton()
```

The one difference: they now inherit from UIFoundation's `Button` rather than `NSButton` directly,
which adds closure-based target-action (`button.box.setAction { … }`) and the library's shared
setup hooks. `bezelStyle` and `buttonType` stay fixed per subclass, exactly as described below.

---

# Why this library was created

The `NSButton` is undeniably the most intricate component in AppKit. It encompasses a wide range of styles and button types, which can be confusing due to inconsistent naming conventions across header files, Xib, and HIG (Apple renames BezelStyle enum in macOS Sonoma). This exacerbates the already convoluted definition, making it more challenging to comprehend. 

The library does not enhance any functionality but rather extracts a style into a separate subclass with an unalterable `bezelStyle` and `buttonType`. It only provides the `buttonType` that aligns with the current style, while some names found in Xib and HIG are offered as Typealias. The actual class name is `bezelStyle` or `buttonType` append `Button`, eg. `RadioButton`. 

If you struggle to grasp how each button should be utilized and where it should appear, I recommend reading this article (https://mackuba.eu/2014/10/06/a-guide-to-nsbutton-styles/) before exploring this repository.
