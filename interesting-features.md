# Interesting Features

## Swift

### [6.3](https://www.swift.org/blog/swift-6.3-released/)

- **`@c` attribute:** [SE-0495](https://github.com/apple/swift-evolution/blob/main/proposals/0495-cdecl.md) exposes Swift functions and enums to C, generating the matching C header declarations, with optional custom naming.
- **Module selectors:** [SE-0491](https://github.com/apple/swift-evolution/blob/main/proposals/0491-module-selectors.md) adds `ModuleName::member` syntax to disambiguate APIs that share the same name across different imported modules.
- **Explicit specialization:** [SE-0460](https://github.com/apple/swift-evolution/blob/main/proposals/0460-specialized.md) adds the `@specialized` attribute to pre-generate specialized versions of a generic function for chosen concrete types.
- **`@inline(always)`:** [SE-0496](https://github.com/apple/swift-evolution/blob/main/proposals/0496-inline-always.md) promotes the long-standing underscored attribute to an official `@inline(always)` that guarantees a function is inlined.
- **Controlling definition visibility:** [SE-0497](https://github.com/apple/swift-evolution/blob/main/proposals/0497-definition-visibility.md) lets ABI-stable libraries control whether a function's body is visible to clients, e.g. `@export(implementation)`.
- **Swift Testing**
  - **Issue Severity:** [ST-0013](https://github.com/apple/swift-evolution/blob/main/proposals/testing/0013-issue-severity-warning.md) lets a test record warning-level issues via a `severity` parameter without failing the test.
  - **Test Cancellation:** [ST-0016](https://github.com/apple/swift-evolution/blob/main/proposals/testing/0016-test-cancellation.md) adds `try Test.cancel()` to stop a running test early.
- **Official Android SDK:** no numbered proposal – see the [Swift 6.3 release notes](https://www.swift.org/blog/swift-6.3-released/) – ships the first official Swift SDK for Android, with Swift/Java interop.

### [6.2](https://www.hackingwithswift.com/articles/277/whats-new-in-swift-6-2)

- **Approachable Concurrency 🔥:** A cluster of proposals that make concurrency far easier to adopt:
      - [SE-0466](https://github.com/apple/swift-evolution/blob/main/proposals/0466-control-default-actor-isolation.md) lets a module default to `@MainActor` isolation, so code runs on the main thread without explicit annotations.
      - [SE-0478](https://github.com/apple/swift-evolution/blob/main/proposals/0478-default-isolation-typealias.md) adds a typealias mechanism to configure that default per module.
      - [SE-0461](https://github.com/apple/swift-evolution/blob/main/proposals/0461-async-function-isolation.md) makes `nonisolated` async functions run in the caller's execution context, and adds the `@concurrent` attribute (plus `nonisolated(nonsending)`) to opt back into running off the actor.
- **weak let:** [SE-0481](https://github.com/swiftlang/swift-evolution/blob/main/proposals/0481-weak-let.md) introduces the ability to use `weak let` when declaring properties of a type, complementing the existing support for `weak var`.
- **InlineArray:** [SE-0453](https://github.com/apple/swift-evolution/blob/main/proposals/0453-vector.md) introduces a fixed-size, stack-allocated array, with [SE-0483](https://github.com/apple/swift-evolution/blob/main/proposals/0483-inline-array-sugar.md) adding the `[N of Type]` shorthand (e.g. `[40 of Sprite]`).
- **Opt-in strict memory safety:** [SE-0458](https://github.com/apple/swift-evolution/blob/main/proposals/0458-strict-memory-safety.md) adds an opt-in mode that flags uses of unsafe constructs, for projects with the strongest security requirements.
- **Transactional observation:** [SE-0475](https://github.com/apple/swift-evolution/blob/main/proposals/0475-observed.md) adds an `Observations` async sequence that streams transactional changes to observable state.
- **Raw identifiers:** [SE-0451](https://github.com/apple/swift-evolution/blob/main/proposals/0451-escaped-identifiers.md) allows backtick-escaped identifiers containing spaces and symbols, handy for descriptive test names.
- **Subprocess:** [swift-foundation SF-0007](https://github.com/apple/swift-foundation/blob/main/Proposals/0007-swift-subprocess.md) (a Foundation proposal, not Swift Evolution) adds a modern async/await API for launching and managing external processes.
- **Concurrency-safe Notifications:** [swift-foundation SF-0011](https://github.com/apple/swift-foundation/blob/main/Proposals/0011-concurrency-safe-notifications.md) (a Foundation proposal, not Swift Evolution) modernizes `NotificationCenter` with concrete `MainActorMessage`/`AsyncMessage` types instead of strings and `userInfo` dictionaries.
- **Swift Testing – exit tests:** [ST-0008](https://github.com/apple/swift-evolution/blob/main/proposals/testing/0008-exit-tests.md) verifies that code terminates as expected by running it in a separate process.
- **Swift Testing – attachments:** [ST-0009](https://github.com/apple/swift-evolution/blob/main/proposals/testing/0009-attachments.md) attaches strings, images, logs, and other artifacts to test results.
- **WebAssembly support:** no numbered proposal – see the [WebAssembly vision document](https://github.com/apple/swift-evolution/blob/main/visions/webassembly.md) – Swift can now build and deploy client and server apps to Wasm runtimes and browsers.

### [6.1](https://www.hackingwithswift.com/articles/276/whats-new-in-swift-6-1)

- **Trailing commas in comma-separated lists 🔥:** [SE-0439](https://github.com/apple/swift-evolution/blob/main/proposals/0439-trailing-comma-lists.md) allows a trailing comma in almost all comma-separated lists (function calls and declarations, generics, tuples, and more), not just arrays and dictionaries.
- **Metatype keypaths:** [SE-0438](https://github.com/apple/swift-evolution/blob/main/proposals/0438-metatype-keypath.md) lets key paths reference a type's metatype, e.g. reading `\.self` and other metatype members through a `KeyPath`.
- **Objective-C implementations in Swift:** [SE-0436](https://github.com/apple/swift-evolution/blob/main/proposals/0436-objc-implementation.md) stabilizes the `@objc @implementation` attribute, letting you implement an Objective-C class's interface in Swift.
- **`nonisolated` for global-actor inference cutoff:** [SE-0449](https://github.com/apple/swift-evolution/blob/main/proposals/0449-nonisolated-for-global-actor-cutoff.md) extends `nonisolated` to types, extensions, and protocols so they can opt out of inferred global-actor isolation.
- **Inferred `TaskGroup` result type:** [SE-0442](https://github.com/apple/swift-evolution/blob/main/proposals/0442-allow-taskgroup-childtaskresult-type-to-be-inferred.md) lets the compiler infer a task group's `ChildTaskResult` type, so you no longer have to spell it out when creating the group.
- **Task naming:** [SE-0469](https://github.com/apple/swift-evolution/blob/main/proposals/0469-task-names.md) allows assigning a human-readable name to a `Task`, which surfaces in debugging and instrumentation.
- **Precise warning control flags:** [SE-0443](https://github.com/apple/swift-evolution/blob/main/proposals/0443-warning-control-flags.md) adds compiler flags to treat individual diagnostic groups as errors or warnings (`-Werror`/`-Wwarning`).
- **Package traits:** [SE-0450](https://github.com/apple/swift-evolution/blob/main/proposals/0450-swiftpm-package-traits.md) adds SwiftPM package traits for conditionally enabling features and dependencies per consumer.
- **Swift Testing – return errors from `expect(throws:)`:** [ST-0006](https://github.com/apple/swift-evolution/blob/main/proposals/testing/0006-return-errors-from-expect-throws.md) returns the thrown error from `#expect(throws:)` so you can make further assertions on it.
- **Swift Testing – test scoping traits:** [ST-0007](https://github.com/apple/swift-evolution/blob/main/proposals/testing/0007-test-scoping-traits.md) lets custom traits run code around each test they're applied to (setup/teardown-style scoping).
- **Background indexing by default:** no numbered proposal – a SourceKit-LSP tooling default (see the [Swift 6.1 release notes](https://www.swift.org/blog/swift-6.1-released/)) that enables background indexing for SwiftPM projects.

### [6.0](https://www.hackingwithswift.com/articles/269/whats-new-in-swift-6)

- **Complete concurrency enabled by default:** The biggest, [SE-0414](https://github.com/apple/swift-evolution/blob/main/proposals/0414-region-based-isolation.md), defines isolation regions that allow the compiler to conclusively prove different parts of your code can run concurrently. Some other additions:
	- [SE-430](https://github.com/apple/swift-evolution/blob/main/proposals/0430-transferring-parameters-and-results.md) adds a new `sending` keyword for when we need to send values between isolation regions. 
	- [SE-0423](https://github.com/apple/swift-evolution/blob/main/proposals/0423-dynamic-actor-isolation.md) improves concurrency support when needing to operate with Objective-C frameworks.
	- [SE-0420](https://github.com/apple/swift-evolution/blob/main/proposals/0420-inheritance-of-actor-isolation.md) allows us to make `async` functions that are isolated to the same actor as their caller.
- **count(where:):** [SE-0220](https://github.com/apple/swift-evolution/blob/master/proposals/0220-count-where.md) introduced a new `count(where:)` method that performs the equivalent of a `filter()` and count in a single pass.
- **Typed Throws:** [SE-0413](https://github.com/apple/swift-evolution/blob/main/proposals/0413-typed-throws.md) introduced the ability to specify exactly what types of errors a function can throw.
- **Pack iteration:** [SE-0408](https://github.com/apple/swift-evolution/blob/main/proposals/0408-pack-iteration.md) introduces pack iteration, which adds the ability to loop over the parameter pack feature introduced in Swift 5.9.
- **Add Collection Operations on Noncontiguous Elements:** [SE-0270](https://github.com/apple/swift-evolution/blob/main/proposals/0270-rangeset-and-collection-operations.md) introduces various new methods to handle more complex operations on collections, such as moving or removing multiple items that aren't contiguous.
- **Access-level modifiers on import declarations:** [SE-0409](https://github.com/apple/swift-evolution/blob/main/proposals/0409-access-level-on-imports.md) adds the ability to mark import declarations with access control modifiers, such as `private import SomeLibrary`.
- **Upgrades for noncopyable types:** Noncopyable types were [introduced in Swift 5.9](https://www.hackingwithswift.com/swift/5.9/noncopyable-structs-and-enums). [SE-0427](https://github.com/apple/swift-evolution/blob/main/proposals/0427-noncopyable-generics.md) makes sure every struct, class, enum, generic type parameter, and protocol in Swift 6 automatically conforms to a new `Copyable` protocol unless you explicitly opt out using `~Copyable`. [SE-0429](https://github.com/apple/swift-evolution/blob/main/proposals/0429-partial-consumption.md) improves things further by adding partial consumption of noncopyable values. [SE-0432](https://github.com/apple/swift-evolution/blob/main/proposals/0432-noncopyable-switch.md) allows us to borrow noncopyable types while switching over them.
- **128-bit Integer Types:** [SE-0425](https://github.com/apple/swift-evolution/blob/main/proposals/0425-int128.md) introduces `Int128` and `UInt128`.
- **BitwiseCopyable:** [SE-0426](https://github.com/apple/swift-evolution/blob/main/proposals/0426-bitwise-copyable.md) introduces a new `BitwiseCopyable` protocol, which has the sole purpose of allowing the compiler to create more optimized code for conforming types.
- **Warning for Retroactive Conformances of External Types:** [SE-0364](https://github.com/apple/swift-evolution/blob/main/proposals/0364-retroactive-conformance-warning.md)
- **Function body macros:** [SE-0415](https://github.com/apple/swift-evolution/blob/main/proposals/0415-function-body-macros.md)
- **Swift Backtrace API:** [SE-0419](https://github.com/apple/swift-evolution/blob/main/proposals/0419-backtrace-api.md)

### [5.9](https://www.hackingwithswift.com/articles/258/whats-new-in-swift-5-9)
- **Macros 🔥:** [SE-0382](https://github.com/apple/swift-evolution/blob/main/proposals/0382-expression-macros.md), [SE-0389](https://github.com/apple/swift-evolution/blob/main/proposals/0389-attached-macros.md), and [SE-0397](https://github.com/apple/swift-evolution/blob/main/proposals/0397-freestanding-declaration-macros.md) combine to add macros to Swift, which allow us to create code that transforms syntax at compile time.
- **if and switch expressions:** [SE-0380](https://github.com/apple/swift-evolution/blob/main/proposals/0380-if-switch-expressions.md) adds the ability for us to use if and switch as expressions in several situations. This produces syntax that will be a little surprising at first, but overall it does help reduce a little extra syntax in the language.
- **Noncopyable structs and enums:** [SE-0390](https://github.com/apple/swift-evolution/blob/main/proposals/0390-noncopyable-structs-and-enums.md) introduces the concept of structs and enums that cannot be copied, which in turn allows a single instance of a struct or enum to be shared in many places – they still ultimately have one owner, but can now be accessed in various parts of your code.
- **consume operator to end the lifetime of a variable binding:** [SE-0366](https://github.com/apple/swift-evolution/blob/main/proposals/0366-move-function.md) extends the concept of consuming values to local variables and constants of copyable types, which might benefit developers who want to avoid excess retain/release calls happening behind the scenes as their data is passed around.
- **Convenience Async[Throwing]Stream.makeStream methods:** [SE-0388](https://github.com/apple/swift-evolution/blob/main/proposals/0388-async-stream-factory.md) adds a new makeStream() method to both AsyncStream and AsyncThrowingStream that sends back both the stream itself alongside its continuation.
- **Add sleep(for:) to Clock:** [SE-0374](https://github.com/apple/swift-evolution/blob/main/proposals/0374-clock-sleep-for.md) adds a new extension method to Swift’s Clock protocol that allows us to suspend execution for a set number of seconds, but also extends duration-based Task sleeping to support a specific tolerance.
- **Discarding task groups:** [SE-0381](https://github.com/apple/swift-evolution/blob/main/proposals/0381-task-group-discard-results.md) adds new discardable task groups that fix an important gap in the current API: tasks that are created inside a task group are automatically discarded and destroyed as soon as they finish, which means task groups that run for extended periods of time (or perhaps forever, as in the case of a web server) won’t leak memory over time.

### [5.8](https://www.hackingwithswift.com/articles/256/whats-new-in-swift-5-8)
- **Lift all limitations on variables in result builders 🔥:** [SE-0373](https://github.com/apple/swift-evolution/blob/main/proposals/0373-vars-without-limits-in-result-builders.md) relaxes some of the restrictions on variables when used inside result builders, allowing us to write code that would previously have been disallowed by the compiler.
- **Function back deployment:** [SE-0376](https://github.com/apple/swift-evolution/blob/main/proposals/0376-function-back-deployment.md) adds a new @backDeployed attribute that makes it possible to allow new APIs to be used on older versions of frameworks.
- **Allow implicit self for weak self captures, after self is unwrapped:** [SE-0365](https://github.com/apple/swift-evolution/blob/main/proposals/0365-implicit-self-weak-capture.md) takes another step towards letting us remove self from closures by allowing an implicit self in places where a weak self capture has been unwrapped.
- **Concise magic file names 🔥:** [SE-0274](https://github.com/apple/swift-evolution/blob/main/proposals/0274-magic-file.md) adjusts the #file magic identifier to use the format Module/Filename, e.g. MyApp/ContentView.swift.
- **Opening existential arguments to optional parameters:** [SE-0375](https://github.com/apple/swift-evolution/blob/main/proposals/0375-opening-existential-optional.md) extends a Swift 5.7 feature that allowed us to call generic functions using a protocol, fixing a small but annoying inconsistency: Swift 5.7 would not allow this behavior with optionals, whereas Swift 5.8 does.
- **Collection downcasts in cast patterns are now supported:** This resolves another small but potentially annoying inconsistency in Swift where downcasting a collection – e.g. casting an array of ClassA to an array of another type that inherits from ClassA – would not be allowed in some circumstances.

### [5.7](https://www.hackingwithswift.com/articles/249/whats-new-in-swift-5-7)
- **`if let` shorthand for unwrapping optionals:** [SE-0345](https://github.com/apple/swift-evolution/blob/main/proposals/0345-if-let-shorthand.md) introduces new shorthand syntax for unwrapping optionals into shadowed variables of the same name using `if let` and `guard let`.
- **Multi-statement closure type inference:** [SE-0326](https://github.com/apple/swift-evolution/blob/main/proposals/0326-extending-multi-statement-closure-inference.md) dramatically improves Swift’s ability to use parameter and type inference for closures, meaning that many places where we had to specify explicit input and output types can now be removed.
- **Clock, Instant, and Duration:** [SE-0329](https://github.com/apple/swift-evolution/blob/main/proposals/0329-clock-instant-duration.md) introduces a new, standardized way of referring to times and durations in Swift. As the name suggests, it’s broken down into three main components: 
	- **Clocks** represent a way of measuring time passing. There are two built in: the continuous clock keeps incrementing time even when the system is asleep, and the suspending clock does not.
	- **Instants** represent an exact moment in time.
	- **Durations** represent how much time elapsed between two instants.
  **Tip:** Clocks are also useful for measuring some specific work, which is helpful if you want to show your users something like how long an image processing task took.
- **Regular expressions:** Swift 5.7 introduces a whole raft of improvements relating to regular expressions (regexes), and in doing so dramatically improves the way we process strings. This is actually a whole chain of interlinked proposals, including
	- [SE-0350](https://github.com/apple/swift-evolution/blob/main/proposals/0350-regex-type-overview.md) introduces a new `Regex` type
	- [SE-0351](https://github.com/apple/swift-evolution/blob/main/proposals/0351-regex-builder.md) introduces a result builder-powered DSL for creating regular expressions.
	- [SE-0354](https://github.com/apple/swift-evolution/blob/main/proposals/0354-regex-literals.md) adds the ability to create a regular expression using `/.../` rather than going through `Regex` and a string.
	- [SE-0357](https://github.com/apple/swift-evolution/blob/main/proposals/0357-regex-string-processing-algorithms.md) adds many new string processing algorithms based on regular expressions.
- **Type inference from default expressions:** [SE-0347](https://github.com/apple/swift-evolution/blob/main/proposals/0347-type-inference-from-default-exprs.md) expands Swift ability to use default values with generic parameter types. What it allows seems quite niche, but it does matter: if you have a generic type or function you can now provide a concrete type for a default expression, in places where previously Swift would have thrown up a compiler error.
- **Concurrency in top-level code:** [SE-0343](https://github.com/apple/swift-evolution/blob/main/proposals/0343-top-level-concurrency.md) upgrades Swift’s support for top-level code – think main.swift in a macOS Command Line Tool project – so that it supports concurrency out of the box. This is one of those changes that might seem trivial on the surface, but [took](https://github.com/apple/swift/pull/40998) a lot of [work](https://github.com/apple/swift/pull/41061) to make [happen](https://github.com/apple/swift/pull/40963).
- **Opaque parameter declarations:** [SE-0341](https://github.com/apple/swift-evolution/blob/main/proposals/0341-opaque-parameters.md) unlocks the ability to use `some` with parameter declarations in places where simpler generics were being used.
- **Structural opaque result types:** [SE-0328](https://github.com/apple/swift-evolution/blob/main/proposals/0328-structural-opaque-result-types.md) widens the range of places that opaque result types can be used.
- **Unlock existentials for all protocols:** [SE-0309](https://github.com/apple/swift-evolution/blob/main/proposals/0309-unlock-existential-types-for-all-protocols.md) significantly loosens Swift’s ban on using protocols as types when they have `Self` or associated type requirements, moving to a model where only specific properties or methods are off limits based on what they do.
- **Lightweight same-type requirements for primary associated types:** [SE-0346](https://github.com/apple/swift-evolution/blob/main/proposals/0346-light-weight-same-type-syntax.md) adds newer, simpler syntax for referring to protocols that have specific associated types.
- **Constrained existential types:** [SE-0353](https://github.com/apple/swift-evolution/blob/main/proposals/0353-constrained-existential-types.md) provides the ability to compose [SE-0309](https://github.com/apple/swift-evolution/blob/main/proposals/0309-unlock-existential-types-for-all-protocols.md) (“Unlock existentials for all protocols”) and [SE-0346](https://github.com/apple/swift-evolution/blob/main/proposals/0346-light-weight-same-type-syntax.md) (“Lightweight same-type requirements for primary associated types”) to write code such as `any Sequence<String>`.
- **Distributed actor isolation:** [SE-0336](https://github.com/apple/swift-evolution/blob/main/proposals/0336-distributed-actor-isolation.md) and [SE-0344](https://github.com/apple/swift-evolution/blob/main/proposals/0344-distributed-actor-runtime.md) introduce the ability for actors to work in a distributed form – to read and write properties or call methods over a network using remote procedure calls (RPC).
- **buildPartialBlock for result builders:** [SE-0348](https://github.com/apple/swift-evolution/blob/main/proposals/0348-buildpartialblock.md) dramatically simplifies the overloads required to implement complex result builders, which is part of the reason Swift’s advanced regular expression support was possible. However, it also theoretically removes the 10-view limit for SwiftUI without needing to add variadic generics, so if it’s adopted by the SwiftUI team it will make a lot of folks happy.
- **Implicitly opened existentials:** [SE-0352](https://github.com/apple/swift-evolution/blob/main/proposals/0352-implicit-open-existentials.md) allows Swift to call generic functions using a protocol in many situations, which removes a somewhat odd barrier that existed previously.
- **Unavailable from async attribute:** [SE-0340](https://github.com/apple/swift-evolution/blob/main/proposals/0340-swift-noasync.md) partially closes a potentially risky situation in Swift’s concurrency model, by allowing us to mark types and functions as being unavailable in asynchronous contexts because using them in such a way could cause problems. Unless you’re using thread-local storage, locks, mutexes, or semaphores, it’s unlikely you’ll use this attribute yourself, but you might _call_ code that uses it so it’s worth at least being aware it exists.

### [5.6](https://www.hackingwithswift.com/articles/247/whats-new-in-swift-5-6)
- **Introduce existential keyword `any`** to mark existential types
- **Type placeholders** which allow us to explicitly specify only some parts of a value’s type so that the remainder can be filled in using type inference.
- **CodingKeyRepresentable** protocol that allows dictionaries with keys that aren’t a plain String or Int to be used as CodingKeys when converted to JSON. Even custom structs can be used as coding keys.
- **Unavailability condition** representing an inverted form of #available called #unavailable, which will run some code if an availability check fails.

### [5.5](https://www.hackingwithswift.com/articles/233/whats-new-in-swift-5-5)
- **Async/Await:** can replace many completion handlers! Especially nested asynchronous function calls.
- **AsyncSequence Protocol:** very useful to e.g. load several objects from a backend and process them as they come in. Reverse geocoding of Locations, processing of locations, etc.
- **Codable synthesis for enums with associated values:** very complex JSON structures are creatable in a simple way
- **Tasks:** as a replacement for operations. Might be easier to handle. Plays perfectly with async/await
- **Extend property wrappers to function and closure parameters**
- [NotificationCenter](https://developer.apple.com/documentation/foundation/notificationcenter) includes a new [AsyncSequence API](https://developer.apple.com/documentation/swift/asyncsequence) for receiving notifications using async/await. (74401384)
- A new Swift value type [AttributedString](https://developer.apple.com/documentation/foundation/attributedstring) is now available with the same character-counting behavior as Swift string. It is fully localizable, and also includes support for Markdown, Codable, strongly typed attributes, and more. (27227292)

### [5.4](https://www.hackingwithswift.com/articles/228/whats-new-in-swift-5-4)
- **Improved implicit member syntax** (UIColor.red.cgcolor > .red.cgcolor)
- **Result builders** (can probably be used to auto-chain Operations 🎉)
- **Swift Package Manager caches package dependencies** ([Swift Packages](https://stackoverflow.com/questions/66143815/xcode-12-5-spm-dependency-cache-location))
- Property wrappers are now supported for local variables
- Local functions now support overloading

### [5.3](https://www.hackingwithswift.com/articles/218/whats-new-in-swift-5-3)
- **Swift Package Manager gains binary dependencies, resources, and more**
- **Type-Based Program Entry Points (@main)**
- **multi trailing closures**
- **synthesized comparable for enum types**
- **enum cases as protocol witness**
- increased availability of self in closures
- Multi-pattern catch clauses

### [5.0](https://www.hackingwithswift.com/articles/126/whats-new-in-swift-5-0)

## Alamofire

[Migration Guide](https://github.com/Alamofire/Alamofire/blob/master/Documentation/Alamofire%205.0%20Migration%20Guide.md#alamofire-50-migration-guide)

- **Decodable Responses:** responseDecodable and the DecodableResponseSerializer now provide built-in support for parsing Decodable types from network responses using any DataDecoder type.
- **Encodable Parameters:** Alamofire now supports and prefers Encodable types as parameters using the ParameterEncoder protocol, allowing fully type-safe representation of request parameters.
- **EventMonitor Protocol:** EventMonitors allow access to Alamofire’s internal events, making it far easier to observe specific actions through a request’s lifetime. This makes logging requests very easy.
- **CachedResponseHandler and RedirectHandler Protocols:** Easy access and control over response caching and redirect behaviors, on both a Session and Request basis.
- **HTTPHeaders Type:** Type safe access to common HTTP headers, with extensions to URLRequest, HTTPURLResponse, and URLSessionConfiguration to allow setting the headers of those types using Alamofire’s new type.
- **RetryPolicy:** A RequestRetrier with automatic support for retrying requests which failed due to a network or other system error, with customizable exponential backoff, retry limits, and other parameters.
- **Serializers** updated with more configuration options, including allowed **empty response** methods and codes, as well as the **DataPreprocessor** protocol, to prepare the received Data for serialization (**get rid of the DataWrapper?!**).

## WWDC/iOS

- **App tracking controls and transparency:** Developers are now required to get your consent before tracking you, so you can choose which apps have permission to track. And see which apps you have given permission to track in Settings so you can change your preferences.
- **Approximate location:** A new setting lets you choose to share your approximate location, rather than your precise location, with an app.
- **Upgrade to Sign in with Apple:** Developers can offer the option to upgrade existing app accounts to Sign in with Apple so users can enjoy improved privacy, security, and ease of use without setting up a new account.
- **VoiceOver Recognition:** On-device intelligence recognizes key elements displayed on your screen to add VoiceOver support for app and web experiences that don’t have accessibility support built in.
- **Menus**
