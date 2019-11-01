# Jetpack Compose Frequently Asked Questions

Knowledge base about glorious new android ui framework in the form of simple FAQ

---

## 🤔 What is Jetpack Compose?

☝️ Jetpack Compose is an Android’s modern toolkit for building native UI rebuilt mostly from scratch by Google. You can find docs and more info about it in the [official docs](https://developer.android.com/jetpack/compose)

---

## 🤔 How it differs from [Anko](https://github.com/Kotlin/anko)/[Anvil](https://github.com/anvil-ui/anvil)/[Splitties-View-DSL](https://github.com/LouisCAD/Splitties/tree/master/modules/views-dsl) or other kotlin UI dsl's?

☝️ While aforementioned libraries are built on top of ordinary Android Views, whose history dates back to the very first Android release, Jetpack Compose uses just canvas and text tools to draw your widgets.

---

## 🤔 So, do I have to rewrite my entire app from scratch?

☝️ Of course, not! In fact, there are some Android that would stay as is, such as WebView, MapView, etc. This is possible because of Jetpack Compose interop tools, such as `setViewContent` and `ComposeView` which could be used to juggle between both ui frameworks. Also, check out `@GenerateView` annotation - this would help you to create a plain old Android View out of your composable

---

## 🤔 How it differs from React?

☝️ From user perspective - not so much. Composable functions are roughly equivalent of React functional components, and effects are similar to React hooks. For more details see this talk by Leland Richardson [React, meet Compose](https://www.youtube.com/watch?v=4EFjDSijAZU)

---

## 🤔 Why all composables return Unit instead of some structure, like VDOM?

☝️ Jetpack Compose uses compiler plugin to inject diffing at compile time. This allows to skip the step of creating a virtual DOM and diffing it with the previous one (process named reconcilation) with more efficient recomposition. For more info, please refer to this [video](https://www.youtube.com/watch?v=Q9MtlmmN4Q0) or this [blogpost](http://intelligiblebabble.com/compose-from-first-principles/).

---

## 🤔 Why do I need to write `+` to load something or get a theme value?

☝️ `+` is a syntax for executing the Effect, which is basically a memoized computation. You can see more of that in this [video](https://www.youtube.com/watch?v=Q9MtlmmN4Q0) or in this [blogpost](http://intelligiblebabble.com/compose-from-first-principles/). Note that `+` syntax is considered ugly and is a subject to change.

---

## 🤔 When JC will be ready for production?

☝️ "When it’s ready". We, as users, hope that playable alpha/beta will be announced on Google I/O 2020, but this is a completely fan-fiction story.

---

## 🤔 Will JC support other platforms besides Android?

☝️ Jetpack Compose was built in a way that permits core code reuse between platforms. Combined with ability of Kotlin to compile to other targets makes it possible to build a crossplatform framework on top of compose core, but right now the priority is to deliver best possible experience for Android developers first.

---

## 🤔 Will JC support animations?

☝️ Yes, check out `:ui:ui-animation` and related projects (like `:ui:ui-animation:integration-tests:ui-animation-demos`) in jetpack compose source repo for more examples.

---

## 🤔 How will dialog and popup window work?

☝️ Just like other composables, all dialogs would have its own composable duals, but they would do clever stuff with WindowManager under the hood.

---

## 🤔 Does Jetpack Compose support Android Studio Layout Preview?

☝️ Currently it does not support Layout Preview. But you can use `@Preview` annotation on your composable function without parameters to get a basic live preview of your composable to see it in action.

---

## 🤔 Does JC work with Constraint Layout?

☝️ Currently it does not support Constraint Layout. But it will change in the future.

---

## 🤔 How do I make list widget, like RecyclerView?

☝️ Compose doesn't have one that is as effective as RecyclerView can be, but for toy projects you can use just a `VerticalScroller` with a `Column` inside it.

---

## 🤔 How do I access `android.content.Context` in composables?

☝️ You can get it from ambient like this `val context = +ambient(ContextAmbient)`

---

## 🤔 How do I access vector assets in composables?

☝️ Vector assets can be acquired with `val vector = +vectorResource(vectorResourceId)`

---

## 🤔 During composition, there is static variable `currentComposer` maybe better was to make Composables extension functions on top of this Composer context?

☝️ This is a temporary decision. In the future releases there would be multiple composition roots, each hierarchy would have one. As of extensions, there is only one receiver possible for Kotlin extension functions, so it would be a major drawback to fill that spot by a framework.

---

## 🤔 I found a bug where to submit it?

☝️ Post an issue in this [tracker](https://issuetracker.google.com/issues?q=componentid:612128)

---

## 🤔 I did not find answer for my question here, what can I do?

☝️ Join [Kotlin Slack community](Slack) and find a `#compose` channel there. Feel free to ask for any help!

If you speak Russian, you also might be interested in joining [telegram community](https://t.me/android_declarative) dedicated to Declarative UI on Android.
