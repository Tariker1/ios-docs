# Swift UI

{% hint style="warning" %}
### **Minimum Required SDK Version**

SwiftUI Screen Loading is supported starting iOS SDK v14.0.0
{% endhint %}

To be able to measure the loading time of your SwiftUI views, you need to [instrument your views](../../integrate-luciq-on-ios/integrate-swiftui.md#define-swiftui-screens) by wrapping them in our `LuciqTracedView` component:

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
var body: some View {
    LuciqTracedView(name: "View Name") {       //our Wrapper
      VStack {
        Text("Hello, World!")
      } 
    }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Spans

Luciq will automatically show spans and operations that occurred during the SwiftUI view loading; these include:

* Network Requests
* Database Queries
* The `body` span, which represents how long the body object took to load
