## Create Custom Overlay With OverlayPortal

Sometimes, when working on designs, there might be a need to design custom elements
such as a toast, dropdown, tooltip, etc. to represent the brand of your app.
This is where `OverlayPortal` comes in. `OverlayPortal` can be used to create custom overlay widgets
(more like a stack-like feel but with more control).

```dart
final overlayController = OverlayPortalController();
final link = LayerLink();
  
CompositedTransformTarget(
  link: link,
  child: OverlayPortal(
    controller: overlayController,
    child: AdaptiveElevatedButton(
      title: 'OverlayPortal',
      onPressed: () {
        overlayController.toggle();
      },
    ),
    overlayChildBuilder: (overlayContext) => CompositedTransformFollower(
      link: link,
      targetAnchor: Alignment.bottomLeft,
      child: Container(
        height: 200,
        margin: const EdgeInsets.only(
          right: 100,
          top: 20,
          bottom: 300,
        ),
        decoration: BoxDecoration(
          border: Border.all(color: Colors.black),
          borderRadius: BorderRadius.circular(10.0),
        ),
        child: ListView.separated(
          itemCount: 20,
          separatorBuilder: (BuildContext context, int index) => const Divider(),
          itemBuilder: (BuildContext context, int index) => GestureDetector(
            onTap: () {
              overlayController.toggle();
              var snackBar = SnackBar(
                content: Text('The ${index + 1} item was tapped.'),
              );
              ScaffoldMessenger.of(context).showSnackBar(snackBar);
            },
            child: Padding(
              padding: const EdgeInsets.all(8.0),
              child: Text(
                'OverlayPortal ${index + 1}',
              ),
            ),
          ),
        ),
      ),
    ),
  ),
);
```

Brief description of the overlay code above:
The Dart code shared above illustrates how to create a personalized dropdown menu using the OverlayPortal widget. As mentioned earlier, you can easily adjust it to suit your needs. I recently used it to make a special pop-up box(Mini Alert Dialog) for my project. 😇

[source](https://api.flutter.dev/flutter/widgets/OverlayPortal-class.html)