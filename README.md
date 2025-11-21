# iOS 26 Upgrade Plan for SwiftUI Project / 针对 SwiftUI 项目的 iOS 26 升级计划  

## 1. Expected Changes in iOS 26 & Xcode 26 (UI & SwiftUI) / iOS 26 与 Xcode 26（UI 和 SwiftUI）的预期变化  

- **Liquid Glass design** – The UI across Apple platforms is built around translucent, glass‑like materials that reflect light and content. System‑provided components automatically adopt Liquid Glass when compiled against the iOS 26 SDK.  
  **液态玻璃设计** – Apple 平台的用户界面围绕半透明、玻璃般的材质构建，能够反射光线和内容。使用 iOS 26 SDK 编译时，系统提供的组件会自动采用 Liquid Glass 效果。  

- **Updated SwiftUI controls** – New APIs like `glassEffect` and Glass button styles let you explicitly apply glass borders and surfaces to your own views. Use system frameworks to get the built‑in effects for free.  
  **更新的 SwiftUI 控件** – 新的 API（如 `glassEffect` 以及玻璃按钮样式）允许开发者明确为自定义视图应用玻璃边框和表面。使用系统框架可免费获得内置效果。  

- **Icon Composer and asset changes** – Xcode 26 adds an Icon Composer to generate app icons that match the Liquid Glass aesthetic.  
  **图标生成器和资源变化** – Xcode 26 新增了图标生成器，可生成符合 Liquid Glass 美学的应用图标。  

- **Rounded corners & spacing** – Many default controls have more rounded edges and larger spacing.  
  **圆角和间距** – 许多默认控件使用更大的圆角和间距。  

- **AI‑powered development assistance** – Xcode 26 integrates a coding assistant that can generate documentation, fix issues and refactor code using natural language.  
  **AI 驱动的开发助手** – Xcode 26 集成了编码助手，可通过自然语言生成文档、修复问题并重构代码。  

- **Swift 6.2 & new SDKs** – Xcode 26 ships with Swift 6.2 and updated SDKs for iOS 26, iPadOS 26, tvOS 26 and visionOS 26; projects must resolve deprecations and adopt updated concurrency features.  
  **Swift 6.2 和新的 SDK** – Xcode 26 包含 Swift 6.2 以及面向 iOS 26、iPadOS 26、tvOS 26 和 visionOS 26 的更新后 SDK；项目需解决已将弃用的提示并采用更新的并发特性。  

- **Localization & String Catalog improvements** – The String catalog editor now supports inline selection of localized strings and can generate type‑safe symbols.  
  **本地化和字符串目录改进** – 字符串目录编辑器现在支持内联选择本地化字符串并能生成类型安全的符号。  

## 2. Upgrade Tasks / 升级任务  

1. **Update development tools**:  
   - Install the final release of Xcode 26 and update command‑line tools.  
   - Switch the project’s build system to Xcode 26 and update the Swift version to 6.2.  
   **更新开发工具**：安装 Xcode 26 正式版及命令行工具；将项目构建系统转移至 Xcode 26 并把 Swift 版本更新为 6.2。  

2. **Update project settings**:  
   - Set the deployment target to iOS 26 (or keep a lower target if supporting older versions).  
   - Run `xcodebuild` to update and check for deprecation warnings.  
   - Use the new Icon Composer to regenerate app icons and update asset catalogs for the Liquid Glass style.  
   **更新项目设置**：将部署目标设为 iOS 26（如需支持旧版可保持更低目标）；运行 `xcodebuild` 以更新并检查弃用警告；使用新的图标生成器重新生成应用图标并更新资源目录以适配 Liquid Glass 风样。  

3. **Update dependencies**:  
   - Audit third‑party frameworks (CocoaPods/Swift Package Manager) and ensure they support iOS 26 and Swift 6.2. Update to the latest versions or replace them.  
   - Remove or replace UI libraries that are not updated for Liquid Glass.  
   - Run `swift package update` to update Swift packages.  
   **更新依赖**：检查第三方框架（CocoaPods/Swift Package Manager），确保其支持 iOS 26 和 Swift 6.2，并更新到最新版本或替换；移除或替换未适配 Liquid Glass 的 UI 库；运行 `swift package update` 更新 Swift 包。  

4. **Refactor UI code**:  
   - Adopt system components and use `glassEffect` or the new glass button styles for custom surfaces. Wrap groups of glass views in a `GlassEffectContainer` to manage the effect.  
   - Remove custom `blur`, `opacity`, `background` or `clipShape` modifiers on elements that should behave like glass.  
   - Adjust layouts to account for the increased default spacing and rounded corners.  
   - Test UIs in light and dark mode to ensure colours and legibility.  
   **重构 UI 代码**：采用系统组件并使用 `glassEffect` 或新的玻璃按钮样式，使用 `GlassEffectContainer` 包裹多个玻璃视图；移除在应具有玻璃效果的元素上使用的自定义 `blur`、`opacity`、`background` 或 `clipShape` 修饰器；调整布局以适应增加的默认间距和圆角；在淡色和深色模式中测试 UI 以确保颜色和可读性。  

5. **Handle new Swift features**:  
   - Address any concurrency warnings introduced by Swift 6.2; update actors, global isolated state and non‑Sendable types.  
   - Fix deprecations and adopt updated APIs (e.g., new result builders or macro enhancements).  
   **处理新的 Swift 特性**：解决 Swift 6.2 引入的并发警告，更新 actors、全局隔离状态和非 Sendable 类型；修复已将弃用的内容并采用更新的 API（例如新的 result builder 或字段开变器）。  

6. **Update localization**:  
   - Adopt the improved String catalog; generate type‑safe keys for localised strings and remove manually maintained string constants.  
   **更新本地化**：采用改进后的字符串目录；为本地化字符串生成类型安全的键，移除手动维护的字符常量。  

7. **Build & run**:  
   - Clean and rebuild the project.  
   - Run on iOS 26 simulators and real devices to ensure there are no build errors and that UI components adopt the Liquid Glass style.  
   - Use Xcode Previews to verify UIs across multiple device sizes, orientations and dynamic type settings.  
   **构建与运行**：清理并重新构建项目；在 iOS 26 模拟器和真机上运行以确保没有构建错误并且 UI 组件采用了 Liquid Glass 风样；使用 Xcode 预览在多种设备尺寸、方向和动态字体设置下验证 UI。  

8. **Backward compatibility**:  
   - Use availability checks (`if #available(iOS 26, *)`) to provide fallback UI for earlier iOS versions.  
   - Maintain separate styles for older OS versions without Liquid Glass.  
   **向后兼容**：使用版本检查 (`if #available(iOS 26, *)`) 为更早版本提供备用 UI；为不支持 Liquid Glass 的系统维护单独的样式。  

## 3. Lightweight Test Plan / 轻量测试计划  

- **Visual regression checks** – For each screen of the app, capture screenshots on iOS 25 (pre‑upgrade) and iOS 26 (post‑upgrade) using the same content. Compare them to verify that system components (navigation bars, tab bars, lists, sheets) adopt the Liquid Glass appearance and that text remains readable.  
  **可视回归检查** – 对应用的每个界面在 iOS 25 和 iOS 26 上使用相同内容截屏并比较，验证系统组件（导航栏、标签栏、列表、屏幕。……）采用了 Liquid Glass 外观并确保文本可读。  

- **Interactive behaviour** – Test taps, long presses and gestures on glass surfaces. Ensure that interactive variants of `glassEffect` respond to touches, pointer movement (on iPad) and scroll events smoothly.  
  **交互行为** – 在玻璃表面上测试点击、长按和手势操作，确保 `glassEffect` 的交互形式能对触摸、指针移动（iPad 上）和滚动事件应德顺畅。  

- **Theme & environment** – Verify the UI in light and dark mode, with different wallpapers/background images. Check that the glass surfaces adapt to underlying colours and remain legible.  
  **主题与环境** – 在淡色和深色模式以及不同壁纸/背景下验证 UI，检查玻璃表面是否能适应底色并保持可读性。  

- **Performance** – Measure launch time, scrolling performance and memory usage on both simulator and real devices. Liquid Glass introduces additional rendering overhead; ensure there are no dropped frames. Use Xcode Instruments to profile CPU and GPU.  
  **性能** – 在模拟器和真机上测量启动时间、滚动性能和内存使用。由于 Liquid Glass 带来额外的渲染费用，应确保没有掉帧现象。使用 Xcode Instruments 分析 CPU 和 GPU。  

- **Backward compatibility** – Run the same test suite on the minimum supported iOS version (if lower than 26) to confirm that fallback UI still works.  
  **向后兼容** – 在最低支持的 iOS 版本上运行相同测试套件，以确认备用 UI 仍然有效。  

- **Accessibility** – Use the Accessibility Inspector to check contrast ratios, dynamic type scaling and VoiceOver labels. Transparent surfaces shouldn’t hinder readability or focus order.  
  **辅助功能** – 使用辅助功能检查器检查对比度、动态字体缩放以及 VoiceOver 标签。透明表面不应碍碍可读性或焦点顺序。  

- **Smoke tests** – Execute your automated unit and UI test suites to confirm functional correctness.  
  **冒烟测试** – 执行自动化单元测试和 UI 测试，以确认功能正确性。  

## 4. Potential Pitfalls / 潜在陷阱  

- **Incompatible customisations** – Using `.blur`, `.opacity`, `.background` or `clipShape` modifiers on glass elements can break the Liquid Glass effect and lead to rendering artefacts. Remove these or wrap glass views in a `GlassEffectContainer`.  
  **不兼容的自定义** – 在玻璃元素上使用 `.blur`、`.opacity`、`.background` 或 `clipShape` 修饰器会破坏 Liquid Glass 效果并导致渲染作弊。应移除这些修饰或用 `GlassEffectContainer` 包裹玻璃视图。  

- **Third‑party UI libraries** – Some libraries may not yet support Liquid Glass or Swift 6.2. Monitor their repositories for updates or replace them with native components.  
  **第三方 UI 库** – 部分库可能尚未支持 Liquid Glass 或 Swift 6.2，应关注其仓库更新或更换为原生组件。  

- **Visual clashes** – Custom backgrounds behind navigation bars or toolbars may interfere with the dynamic glass effect, reducing contrast. Keep system bars unmodified where possible.  
  **视觉冲突** – 在导航栏或工具栏后面使用自定义背景可能带来动态玻璃效果冲突和小密度降低，尽可能保持系统栏不修改。  

- **Swift concurrency issues** – Upgrading to Swift 6.2 may surface new warnings or runtime errors, especially around actors, global isolated state or non‑Sendable types. Budget time to resolve these.  
  **Swift 并发问题** – 升级到 Swift 6.2 可能暴露新的警告或运行时错误，特别是固体 actors、全局隔离状态或非 Sendable 类型，需预留时间处理。  

- **Icon & asset mismatch** – If you don’t regenerate icons using the new Icon Composer, your app may look out of place on the iOS 26 home screen.  
  **图标和资源不匹配** – 如果不使用新的图标生成器重新生成图标，您的应用在 iOS 26 主屏上可能显得不协调。  

- **User reaction to design** – Not all users like the Liquid Glass look. Consider gathering feedback and providing a “classic” appearance option if feasible.  
  **用户对设计的反应** – 并非所有用户都喜欢 Liquid Glass 外观，可考虑收集反馈并提供“经典”外观选项。  

---  

By following this plan, you can methodically update your SwiftUI project for iOS 26 and ensure that the new Liquid Glass design is adopted gracefully while maintaining stability and backward compatibility.  
遵循此计划，您可以有来有序地将 SwiftUI 项目升级到 iOS 26，确保新引入的 Liquid Glass 设计得以优雅地采用，同时保持应用的稳定性和向后兼容性。
