##TextStyle Utility Extension

If you've read some Flutter tips online, you might have noticed this one come up too often: Don't hardcode text styles. I agree with that because it makes the app more manageable and easy to change the font size in the app theme, updating it app-wide.

While it's good to use the app theme to specify the text style, it might look like boilerplate code when called repeatedly. To address this, here's an extension example you can add to your app to make it easier to work with.

```dart
extension TextStyleBuildContext on BuildContext {
  TextStyle get displayLarge => Theme.of(this).textTheme.displayLarge!;
  TextStyle get displayMedium => Theme.of(this).textTheme.displayMedium!;
  TextStyle get displaySmall => Theme.of(this).textTheme.displaySmall!;
  TextStyle get headlineLarge => Theme.of(this).textTheme.headlineLarge!;
  TextStyle get headlineMedium => Theme.of(this).textTheme.headlineMedium!;
  TextStyle get headlineSmall => Theme.of(this).textTheme.headlineSmall!;
  TextStyle get titleLarge => Theme.of(this).textTheme.titleLarge!;
  TextStyle get titleMedium => Theme.of(this).textTheme.titleMedium!;
  TextStyle get titleSmall => Theme.of(this).textTheme.titleSmall!;
  TextStyle get bodyLarge => Theme.of(this).textTheme.bodyLarge!;
  TextStyle get bodyMedium => Theme.of(this).textTheme.bodyMedium!;
  TextStyle get bodySmall => Theme.of(this).textTheme.bodySmall!;
  TextStyle get labelLarge => Theme.of(this).textTheme.labelLarge!;
  TextStyle get labelMedium => Theme.of(this).textTheme.labelMedium!;
  TextStyle get labelSmall => Theme.of(this).textTheme.labelSmall!;

  'Usage Example'
  ----------------

  Text(
    'Display Large',
    style: context.displayLarge,
  ),
}
```


| **Before**                                  | **After (with TextStyles Extension)** |
|---------------------------------------------|----------------------------------------|
| `Theme.of(context).textTheme.displayLarge`   |  `context.displayLarge`  |
| `Theme.of(context).textTheme.displayMedium!.copyWith(color: Colors.blue,)`   | `context.displayMedium.copyWith(color: Colors.blue,)`  |

The code above basically is a `BuildContext` that provide easy access to predefined `TextStyle` objects based on your app's design.
