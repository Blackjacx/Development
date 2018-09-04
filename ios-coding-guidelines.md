# iOS Coding Guidelines

1. **Avoid Code Duplications.** This way you avoid limitless growing codebase plus, more important, you avoid fixing issues in multiple places. This is one of the most important rules.
1. **Use the `self.` syntax exclusively in closures and appropriate initializers.** So it will become easier to track down future retain cycles that are caused by missing `[weak self]` in the closure definition. Just leave out `self` if it is not necessary. Also use the `self.` syntax to initially assign constructor parameters to their respective properties if they have the same name.
1. **Never use the default case in switch statements.** Switch is an extremely useful construct in Swift since the compiler warns about missing cases. If you use the default case you disable this behaviour and loose one of the most powerful features of Swift.
1. **Never omit specifying the value of string-typed enum cases.** Imagine you create a string-typed enum and omit the values for every case since Swift infers the value from the case name. Now when you refactor one enum case from somewhere in your app, the inferred value also changes, which is not desired i.e. in JSON keys. You would introduce hard to find errors.
1. **Create all classes as `final`.** This way some optimisations are enabled for these classes which speeds up compilation.
1. **Set thickness of lines device dependent.** When you set the thickness of lines to `1.0 / UIScreen.main.scale` then the will appear equally on all devices.
1. **Use UITextView for multiline text.** If you follow this rule you get text selection and all the features of an UITextView for free. Be sure you set isEditable and isScrollable to `false`.
1. **Localized-strings used in a framework F must be defined there.** If don't folow this rule, **F** depends on the target/module where the string is defined and thus is not modular/independent anymore. If e.g. another target/module uses a class of **F** that contains a localized string which is outside of **F** the translation could not be found.
1. **Name selectors with the pattern on<action_name>** Having a unified pattern for naming selectors helps to make code understandable faster. The on* pattern is also used in other programming languages like JavaScript.

## Access Qualifier

1. **Respect the order of symbols.** Properties should be listed on the top of a class or struct in the order `public static`, `private static`, `public` and `private`. In general static/public symbols are higher ranked than non-static/private ones.
1. **Declare symbols internal if you want to test them.** To be able to use symbols in tests declare them as `internal` (no prefix) instead of `private` even if they are not used outside of the containing object. If you don't need to test them and they are not required outside of the containing object declare it as `private`.
