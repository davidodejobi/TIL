## Create an Adaptive Dialog

Creating an adaptive app in Flutter involves writing platform-specific code for each platform. However, the Flutter team has introduced widgets to simplify the process. One such widget is the `showAdaptiveDialog` method.

```dart
// Function to show an adaptive dialog using Flutter's built-in method
void showAdaptiveDialog(BuildContext context) {
  showAdaptiveDialog(
    context: context,
    builder: (adaptiveContext) => const AdaptiveDialogWidget(
      title: 'Basic dialog example',
      content:
          'A dialog is a type of modal window that appears in front of app content to provide critical information, or prompt for a decision to be made.',
    ),
  );
}

class AdaptiveDialogWidget extends StatelessWidget {
  final String title, content;
  const AdaptiveDialogWidget({
    Key? key,
    required this.title,
    required this.content,
  }) : super(key: key);

  Widget adaptiveAction({
    required BuildContext context,
    required VoidCallback onPressed,
    required Widget child,
  }) {
    final ThemeData theme = Theme.of(context);

    switch (theme.platform) {
      case TargetPlatform.android:
      case TargetPlatform.fuchsia:
      case TargetPlatform.linux:
      case TargetPlatform.windows:
        return TextButton(onPressed: onPressed, child: child);
      case TargetPlatform.iOS:
      case TargetPlatform.macOS:
        return CupertinoDialogAction(onPressed: onPressed, child: child);
    }
  }

  @override
  Widget build(BuildContext context) {
    return AlertDialog.adaptive(
      titleTextStyle: Theme.of(context).textTheme.headlineSmall,
      title: Text(title),
      content: Text(content),
      actions: <Widget>[
        adaptiveAction(
          context: context,
          onPressed: () {
            Navigator.of(context).pop();
          },
          child: const Text(
            'Close',
          ),
        ),
        adaptiveAction(
          context: context,
          onPressed: () {},
          child: const Text(
            'Submit',
          ),
        ),
      ],
    );
  }
}
```
The code snippet provided demonstrates how to create an adaptive dialog in Flutter for Android and iOS using the `showAdaptiveDialog` method and the `AdaptiveDialogWidget` class.


[source](https://api.flutter.dev/flutter/material/AlertDialog/AlertDialog.adaptive.html)
