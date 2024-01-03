Common Adaptive Widgets

Below are some of the code snippet for the commonly used widget in flutter. This makes apps feel more home like for the users.

```dart
Switch.adaptive(
              value: false,
              onChanged: (value) {
              },
            ),

 SwitchListTile.adaptive(
                title: const Text('Text'),
                value: true,
                onChanged: (newValue) {
                }),

    SwitchListTile.adaptive(
                title: const Text('Text'),
                value: isSwitched2,
                onChanged: (newValue) {
                  setState(() {
                    isSwitched2 = newValue;
                  });
                }),
                
            Slider.adaptive(
              value: .1,
              min: 0.0,
              max: 10.0,
              divisions: 10,
              label: .1.toString(),
              onChanged: (value) {
              },
            ),

             const CircularProgressIndicator.adaptive(),
            
            const AdfaptiveElevatedButton(
              title: 'Say Adaptive',
            ),



```

```dart
class AdfaptiveElevatedButton extends StatelessWidget {
  final String title;
  const AdfaptiveElevatedButton({
    Key? key,
    required this.title,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    bool isIOS = Theme.of(context).platform == TargetPlatform.iOS;
    return SizedBox(
      child: isIOS
          ? CupertinoButton.filled(
              child: Text(title),
              onPressed: () {},
            )
          : ElevatedButton(
              child: Text(title),
              onPressed: () {},
            ),
    );
  }
}
```
The code snippet provided demonstrates how to create an adaptive dialog in Flutter for Android and iOS using the `showAdaptiveDialog` method and the `AdaptiveDialogWidget` class.


[source](https://api.flutter.dev/flutter/material/AlertDialog/AlertDialog.adaptive.html)
