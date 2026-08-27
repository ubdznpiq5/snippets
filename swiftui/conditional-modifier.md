# Conditional Modifier

Sometimes you need to apply a modifier only when a condition is true. Instead of `if` inside the view builder, use a `ViewModifier` extension.

```swift
extension View {
    @ViewBuilder
    func `if`<Content: View>(_ condition: Bool, transform: (Self) -> Content) -> some View {
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
        view.background(Color.yellow)
    }
```

This avoids duplicating the view hierarchy.
