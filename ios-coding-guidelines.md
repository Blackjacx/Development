# iOS Coding Guidelines

1. **Avoid Code Duplications.** This way you avoid limitless growing codebase plus, more important, you avoid fixing issues in multiple places. This is one of the most important rules.
1. **Use the `self.` syntax exclusively in closures and appropriate initializers.** So it will become easier to track down future retain cycles that are caused by missing `[weak self]` in the closure definition. Just leave out `self` if it is not necessary. Also use the `self.` syntax to initially assign constructor parameters to their respective properties if they have the same name.
1. **Dont use the default case if it's possible that the enum is extended in the future.** Switch is an extremely useful construct in Swift since the compiler warns about missing cases. If you use the default case you disable this behaviour and loose one of the most powerful features of Swift. It makes sense however to use the default case if you don't want case-specific behavior for every case, but only for one or some of them. In this case it doesn't break anything if new cases get added. Also if you switch over plain value types, a default case is harmless.
1. **Never omit specifying the value of string-typed enum cases.** Imagine you create a string-typed enum and omit the values for every case since Swift infers the value from the case name. Now when you refactor one enum case from somewhere in your app, the inferred value also changes, which is not desired i.e. in JSON keys. You would introduce hard to find errors.
1. **Avoid subclasses where possible and finalize your classes** Because super- and subclass logic becomes hard to maintain, try to split up logic into separate structs or classes instead. By marking your classes final, some optimizations are enabled which among other things speeds up compilation. Remember that since structs are not inheritable, they are final by design.
1. **Set thickness of lines device dependent.** When you set the thickness of lines to `1.0 / UIScreen.main.scale` then the will appear equally on all devices.
1. **Use UITextView for multiline text.** If you have a block of text, UITextField is more practical than a multiline label, especially if you want your content to be selectable. Be sure you set isEditable and isScrollable to `false` if desired.
1. **Localized-strings used in a framework F must be defined there.** If don't folow this rule, **F** depends on the target/module where the string is defined and thus is not modular/independent anymore. If e.g. another target/module uses a class of **F** that contains a localized string which is outside of **F** the translation could not be found.
1. **Name selectors with the pattern on<action_name>** Having a unified pattern for naming selectors helps to make code understandable faster. The on* pattern is also used in other programming languages like JavaScript.

## Framework Extensions

1. **Never set `translatesAutoresizingMaskIntoConstraints` manually.** We have the functions `<subview>.addTo(<parent>)` and `<subview>.addMaximizedTo(<parent>)` which do that automatically.
1. **UI Alerts** Use UIAlertController extension to display alerts and action sheets.
1. **Fonts** Never define a font in code, but rather use or extend the presets in the Fonts class.
1. **Colors** Never define a color in code, but rather use or extend the UIColor extensions.
1. **Date Formatter** You don'thave to configure your own `DateFormatter` objects, use `SHDateFormatter` instead. If it doesn't contain a date format you need, extend it in `SHDateFormatter+Extensions`.
1. **Hiding UIStackView Subviews** Use the `showArrangedSubview` method in the `UIView+Extensions` to show or hide arranged subviews.

## UIView • UIViewController Architecture

These guidelines are meant to be used without Interface Builder and teach you how to work with views programmatically.

1. **Use special function to setup and add EACH subview.** Setup each subview of a view or view controller in its own function! The Name of the function has to be `setup<property_name>`. This function should set all parameters necessary for the first setup. This includes `contentHuggingPriority` and `contentCompressionResistencyPriority`. It is called only once in init (UIView) or viewDidLoad (UIViewController). Right before the function returns add the view to its superview. This pattern turned out to be one of the cleanest structuring methods possible for the swift language. The advantage is that you have a clean interface of properties on top of the class which helps to recognize all subviews at one glance - in contrast of setting up views in a property closure. Furthermore you can use `self` since these functions are called after initialization. You have a clear overview of the adding order of subviews. Additionally you prevent one long function that sets up all properties of all subviews - typically init or viewDidLoad. Last but not least if you stick to this pattern it is much easier to understand the structure of the whole app since you'll find this pattern all over again.
1. **Use special function to setup layout constraints.** Always use `func setupLayoutConstraints` to create constraints between all subviews! Call it right after the last subview setup* function in viewDidLoad (UIViewController) or init (UIView). This activates all layout constraints.

## Access Qualifier

1. **Respect the order of symbols.** Internal enums and structs should be defined on top of a class or struct. These are followed by the properties, ordered by there ascending privateness, so `public`, `internal`, `private`. They should be divided in static and non-static properties, so `static private` is above `public`. Properties are followed by functions with the same ordering rules.
1. **Declare symbols internal if you want to test them.** To be able to use symbols in tests declare them as `internal` (no prefix) instead of `private` even if they are not used outside of the containing object. If you don't need to test them and they are not required outside of the containing object declare it as `private`.

## Code Format

1. **Line Breaks** Leave a blank line underneath every function declaration, except if the body is one line long. This is not necessary in computed properties.
1. **Closure Style** Use the short style of closure with two `{}` whenever possible.
1. **Commments** Comment functions and properties using `\\\` only if it enhances their comprehendibility. Generally comment code snippets if you deem reasonable. Sometimes design choices or complex structures are not immediately obvious to understand, in such cases comment are useful for others and your future self.
1. **No file header.** Remove comment header for newly created files since it will be always outdated (copyright, spelling errors in file names, etc.).
1. **Name bools with the pattern isState** This is easy to read and matches the swifty naming conventions in the updated iOS frameworks.
