DPTextField
===========

DPTextField is a replacement control for UITextField that provides several
useful features, including:

- Previous/Next field toolbar buttons (with outlets that can be wired up in
Interface Builder)
- unobtrusive and editable auto-fill functionality
- a Done toolbar button, and swipe gesture, to remove the keyboard without
submitting a form
- set maximum characters allowed in field
- proper device rotation handling for iPhone and iPad
- correct handling of iPad's undocked keyboard

## Preview

[insert images here]

## Installation

[insert installation instructions here]

## Code

### The toolbar

DPTextField uses a `UIToolbar` as its `inputAccessoryView`. The toolbar
correctly resizes itself in response to device orientation changes (iPhone
only). The toolbar's appearance can be customized any way you like. By default,
it will appear with a standard styled `UIToolbar` for normal keyboards, and with
a black transluscent style for alert keyboards. At any time, the toolbar can be
hidden by setting the `inputAccessoryViewHidden` property to `YES`.

```
DPTextField *field = [[DPTextField alloc] init];
[field.toolbar setBarStyle:UIBarStyleBlackOpaque];
[field setInputAccessoryViewHidden:YES];
```

### Previous|Next and Done toolbar buttons

A DPTextField has IBOutlets for sibling fields, called `previousField` and
`nextField`. These can be connected to other `UIResponder` controls using
Interface Builder.

When these outlets are connected, DPTextField will display Previous and Next
buttons in its toolbar. These will switch the first responder field in the view,
if allowed.

The previous and next buttons are only enabled when the outlets are connected.
If neither outlet is connected, the buttons are not displayed in the toolbar.
The buttons can also be manually enabled/disabled by setting the
`previousBarButtonEnabled` and `nextBarButtonEnabled` boolean properties. This
is useful for preventing a field from resigining first responder if it failes a
validation check. (Note that setting these properties to YES only enables the
bar button if the field's respective outlet is connected to another control.)

A Done button is also displayed in the toolbar by default. When tapped, it
simply tells the DPTextField to `resignFirstResponder`. It can be removed by
setting the `doneBarButtonItemHidden` property to `YES`. Alternatively, it can
be enabled/disabled via the `doneBarButtonItemEnabled` property.