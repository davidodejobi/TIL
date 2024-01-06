## Common Adaptive Widgets

Check out these simple code examples that use common Flutter widgets. They make mobile apps easy to use and feel familiar.

```dart
// A switch that adapts its appearance based on the platform
Switch.adaptive(
  value: false,
  onChanged: (value) {
    // Handle switch value change
  },
),

// An adaptive switch embedded within a list tile
SwitchListTile.adaptive(
  title: const Text('Text'),
  value: true,
  onChanged: (newValue) {
    // Handle switch value change
  },
),

// Another adaptive switch within a list tile with dynamic state management
SwitchListTile.adaptive(
  title: const Text('Text'),
  value: isSwitched2,
  onChanged: (newValue) {
    setState(() {
      isSwitched2 = newValue;
    });
  },
),

// An adaptive slider with dynamic range and label
Slider.adaptive(
  value: .1,
  min: 0.0,
  max: 10.0,
  divisions: 10,
  label: .1.toString(),
  onChanged: (value) {
    // Handle slider value change
  },
),

// An adaptive circular progress indicator
const CircularProgressIndicator.adaptive(),

// An adaptive elevated button demonstrating platform-specific styling
const AdaptiveElevatedButton(
  title: 'Say Adaptive',
),
```

```dart
class AdaptiveElevatedButton extends StatelessWidget {
// Custom adaptive elevated button class
class AdaptiveElevatedButton extends StatelessWidget {
  final String title;
  const AdaptiveElevatedButton({
    Key? key,
    required this.title,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    // Check the current platform to determine the button appearance
    bool isIOS = Theme.of(context).platform == TargetPlatform.iOS;
    return SizedBox(
      child: isIOS
          ? CupertinoButton.filled(
              child: Text(title),
              onPressed: () {
                // Handle button press
              },
            )
          : ElevatedButton(
              child: Text(title),
              onPressed: () {
                // Handle button press
              },
            ),
    );
  }
}
```

Adaptive widgets, like `Switch`, `SwitchListTile`, `Slider`, `CircularProgressIndicator`, and `AdaptiveElevatedButton`, enhance the user experience by adapting to different platforms in Flutter. The `AdaptiveElevatedButton` even demonstrates a custom adaptive button based on the current platform.


For more details and examples and explanation, refer to the [Flutter documentation](https://docs.flutter.dev/ui/layout/responsive/building-adaptive-apps). 
