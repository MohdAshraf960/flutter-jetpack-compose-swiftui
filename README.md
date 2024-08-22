---

# Cross-Platform UI Widget Comparison: Flutter, Jetpack Compose, and SwiftUI

This document provides a comparison of equivalent widgets and concepts between Flutter, Jetpack Compose, and SwiftUI. It is designed to help developers familiar with one framework to understand the equivalent components in another.

## Basic Widgets

| **Concept**         | **Flutter**             | **Jetpack Compose**       | **SwiftUI**              | **Description**                                     |
|---------------------|-------------------------|---------------------------|--------------------------|-----------------------------------------------------|
| Text                | `Text`                  | `Text`                    | `Text`                   | Displays a text string.                             |
| Horizontal Layout   | `Row`                   | `Row`                     | `HStack`                 | Arranges children in a horizontal layout.           |
| Vertical Layout     | `Column`                | `Column`                  | `VStack`                 | Arranges children in a vertical layout.             |
| Container           | `Container`             | `Box`                     | `ZStack` / `Rectangle`   | A versatile widget for holding and styling a child. |
| Padding             | `Padding`               | `Modifier.padding`        | `padding`                | Adds padding around a widget.                       |
| Center              | `Center`                | `Box(contentAlignment = Alignment.Center)` | `Spacer()` within `VStack`/`HStack` | Centers a child widget.                            |
| Overlay/Stack       | `Stack`                 | `Box` with `contentAlignment` | `ZStack`                 | Overlays widgets on top of each other.              |
| Scrollable List     | `ListView`              | `LazyColumn`, `LazyRow`   | `List`                   | Displays a scrollable list of items.                |
| Image               | `Image`                 | `Image`                   | `Image`                  | Displays an image.                                  |
| Button              | `Button`                | `Button`, `TextButton`    | `Button`                 | A basic button with text or custom content.         |
| Icon                | `Icon`                  | `Icon`                    | `Image(systemName:)`     | Displays an icon.                                   |
| Scaffold            | `Scaffold`              | `Scaffold`                | `NavigationView` + `VStack` | Provides basic structure like an AppBar, Body, etc. |
| AppBar              | `AppBar`                | `TopAppBar`               | `NavigationBar`          | Displays a top app bar with title and actions.      |
| Floating Action Button | `FloatingActionButton` | `FloatingActionButton`    | Custom with `Button`     | Displays a floating action button.                  |
| Slider              | `Slider`                | `Slider`                  | `Slider`                 | Allows selection of a value from a range.           |
| Switch              | `Switch`                | `Switch`                  | `Toggle`                 | Toggles between on and off states.                  |
| Checkbox            | `Checkbox`              | `Checkbox`                | `Toggle`                 | A box that can be checked or unchecked.             |
| TextField           | `TextField`             | `TextField`               | `TextField`              | Single-line input field.                            |
| Card                | `Card`                  | `Card`                    | `Card`                   | A card that can be used to display content.         |

## Layouts and Modifiers

| **Concept**         | **Flutter**             | **Jetpack Compose**       | **SwiftUI**              | **Description**                                     |
|---------------------|-------------------------|---------------------------|--------------------------|-----------------------------------------------------|
| Size Constraints    | `SizedBox`              | `Modifier.size`, `Modifier.height`, `Modifier.width` | `frame` | Defines fixed width and height for a widget.        |
| Alignment           | `Align`                 | `Modifier.align`          | `alignment` or `Spacer()` | Aligns a child widget within its parent.            |
| Expandable          | `Expanded`              | `Modifier.weight`         | `Spacer()`               | Expands to fill the available space.                |
| Empty Space         | `Spacer`                | `Spacer`                  | `Spacer()`               | Fills empty space between widgets.                  |
| Decoration          | `Decoration`            | `Modifier.background`, `Modifier.border` | `background`, `border`, `overlay` | Applies background color, border, etc.            |

## State Management

| **Concept**         | **Flutter**             | **Jetpack Compose**       | **SwiftUI**              | **Description**                                     |
|---------------------|-------------------------|---------------------------|--------------------------|-----------------------------------------------------|
| Stateful Component  | `StatefulWidget`        | `@Composable + State`      | `@State`, `@Binding`, `@ObservedObject` | Creates a widget with mutable state.                |
| State Update        | `setState`              | `remember { mutableStateOf() }`, `StateFlow` | Directly updating `@State` properties | Triggers a UI re-composition when state changes.    |
| Inherited Data      | `InheritedWidget`       | `CompositionLocal`         | `EnvironmentObject`      | Provides data down the tree.                        |

## Navigation

| **Concept**         | **Flutter**             | **Jetpack Compose**       | **SwiftUI**              | **Description**                                            |
|---------------------|-------------------------|---------------------------|--------------------------|------------------------------------------------------------|
| Basic Navigation    | `Navigator.push`        | `NavController.navigate`   | `NavigationLink`         | Navigate to a new screen (or composable).                  |
| Pop Navigation      | `Navigator.pop`         | `NavController.popBackStack` | `presentationMode.wrappedValue.dismiss()` | Pop the current screen from the stack and go back.         |
| Replace Screen      | `Navigator.pushReplacement` | `NavController.navigate` with `popUpTo` and `inclusive` | `NavigationLink` with custom logic | Replace the current screen with a new one.                 |
| Named Route         | `Navigator.pushNamed`   | `NavController.navigate(route)` | `NavigationLink(destination:)` | Navigate using a named route.                              |
| Pop Until Route     | `Navigator.popUntil`    | `NavController.popBackStack(route)` | Custom navigation stack management | Pop screens until a specific route is reached.             |
| Route Definition    | `MaterialPageRoute`     | `Composable` with `NavHost` and `NavGraph` | `NavigationLink(destination:)` | Define a route with a new screen or composable.       |
| Handle Unknown Route| `onGenerateRoute` / `onUnknownRoute` | `NavHost` with a default destination | `NavigationLink` with conditional check | Handle unknown or undefined routes.                        |
| Check Back Stack    | `Navigator.canPop`      | `NavController.previousBackStackEntry != null` | Custom logic | Check if the navigation stack can be popped.              |
| Handle Back Button  | `WillPopScope`          | `BackHandler`              | `onDisappear` or `onAppear` with custom logic | Handle the back button or prevent exiting a screen.        |
| Bottom Navigation   | `BottomNavigationBar`   | `BottomNavigation`         | `TabView`                | Bottom navigation with multiple screens or destinations.   |
| Drawer              | `Drawer`                | `ModalDrawer` or `NavigationDrawer` | `NavigationView` + `List` | A side navigation drawer.                                  |
| Tab Bar             | `TabBar`                | `TabRow`                   | `TabView`                | A tab bar for switching between different screens.         |

## Navigation Libraries

| **Concept**         | **Flutter**             | **Jetpack Compose**       | **SwiftUI**              | **Description**                                                |
|---------------------|-------------------------|---------------------------|--------------------------|----------------------------------------------------------------|
| Navigation Library  | `flutter_navigation`, `get`, `auto_route` | `androidx.navigation.compose` | Native SwiftUI Navigation or third-party libraries like `NavigationStack` | Libraries to help with navigation and deep linking in the app. |
| Custom Animations   | `PageRouteBuilder`      | `AnimatedNavHost` with `AnimatedVisibility` | `CustomTransition` or `matchedGeometryEffect` | For custom transition animations between screens.              |
| Observing Navigation| `NavigatorObservers`    | `NavHostController.currentBackStackEntryAsState` | `@State`, `@Binding` with `onAppear` | Observing and reacting to navigation events.                   |

---
