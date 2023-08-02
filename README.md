# Flutter_doc_CokBK_forms_Retrieve_the_value_of_text_field
 https://docs.flutter.dev/cookbook/forms/retrieve-input
Retrieve the value of a text field
==================================

1.  [Cookbook](https://docs.flutter.dev/cookbook)
2.  [Forms](https://docs.flutter.dev/cookbook/forms)
3.  [Retrieve the value of a text field](https://docs.flutter.dev/cookbook/forms/retrieve-input)

In this recipe, learn how to retrieve the text a user has entered into a text field using the following steps:

1.  Create a `TextEditingController`.
2.  Supply the `TextEditingController` to a `TextField`.
3.  Display the current value of the text field.

[](https://docs.flutter.dev/cookbook/forms/retrieve-input#1-create-a-texteditingcontroller)1\. Create a `TextEditingController`
-------------------------------------------------------------------------------------------------------------------------------

To retrieve the text a user has entered into a text field, create a [`TextEditingController`](https://api.flutter.dev/flutter/widgets/TextEditingController-class.html) and supply it to a `TextField` or `TextFormField`.

Important: Call `dispose` of the `TextEditingController` when you've finished using it. This ensures that you discard any resources used by the object.

content_copy

```
// Define a custom Form widget.
class MyCustomForm extends StatefulWidget {
  const MyCustomForm({super.key});

  @override
  State<MyCustomForm> createState() => _MyCustomFormState();
}

// Define a corresponding State class.
// This class holds the data related to the Form.
class _MyCustomFormState extends State<MyCustomForm> {
  // Create a text controller and use it to retrieve the current value
  // of the TextField.
  final myController = TextEditingController();

  @override
  void dispose() {
    // Clean up the controller when the widget is disposed.
    myController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    // Fill this out in the next step.
  }
}
```

[](https://docs.flutter.dev/cookbook/forms/retrieve-input#2-supply-the-texteditingcontroller-to-a-textfield)2\. Supply the `TextEditingController` to a `TextField`
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

Now that you have a `TextEditingController`, wire it up to a text field using the `controller` property:

content_copy

```
return TextField(
  controller: myController,
);
```

[](https://docs.flutter.dev/cookbook/forms/retrieve-input#3-display-the-current-value-of-the-text-field)3\. Display the current value of the text field
-------------------------------------------------------------------------------------------------------------------------------------------------------

After supplying the `TextEditingController` to the text field, begin reading values. Use the [`text()`](https://api.flutter.dev/flutter/widgets/TextEditingController/text.html) method provided by the `TextEditingController` to retrieve the String that the user has entered into the text field.

The following code displays an alert dialog with the current value of the text field when the user taps a floating action button.

content_copy

```
FloatingActionButton(
  // When the user presses the button, show an alert dialog containing
  // the text that the user has entered into the text field.
  onPressed: () {
    showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          // Retrieve the text that the user has entered by using the
          // TextEditingController.
          content: Text(myController.text),
        );
      },
    );
  },
  tooltip: 'Show me the value!',
  child: const Icon(Icons.text_fields),
),
```
