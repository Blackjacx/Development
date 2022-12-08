# Interesting Features

## Swift

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
	- [SE-0354](https://github.com/apple/swift-evolution/blob/main/proposals/0354-regex-literals.md) adds the ability co create a regular expression using `/.../` rather than going through `Regex` and a string.
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
- **Async/Await:** can replace many completion handlers! Especially nested asynchronere function calls.
- **AsyncSequence Protocol:** very useful to e.g. load several objects from a backend and process them as they come in. Reverse geocoding of Locations, processing of locations, etc.
- **Codable synthesis for enums with associated values:** very complex JSON structures are creatable in a simple way
- **Tasks:** as a replacement for operations. Might be easier to handle. Plays perfectly with asynch/await
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
