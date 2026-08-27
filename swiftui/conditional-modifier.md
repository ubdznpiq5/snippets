# Conditional Modifier

Small helper for applying a SwiftUI modifier only when a condition is true.

```swift
extension View {
    @ViewBuilder
    func `if`<Content: View>(
        _ condition: Bool,
        transform: (Self) -> Content
    ) -> some View {
        if condition {
            transform(self)
        } else {
            self
        }
    }
}
```

Usage:

```swift
Text("Hello")
    .if(isHighlighted) { view in
        view.foregroundColor(.yellow).bold()
    }
```

This avoids wrapping in `Group` or `AnyView`, and keeps call sites readable.
