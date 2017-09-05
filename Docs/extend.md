# Extending Form Editor
Form Editor can be extended in a lot of ways. The following sections outline the different extension points.

## Creating a custom field
So you find yourself lacking some special field for your project? No problem! Form Editor is super easy to extend with new field types. Read more [here](extend_field.md). 

## Form submission events
If you need to react to form submissions (e.g. to create your own workflow), you can subscribe to the following events on `FormModel`:
* `BeforeAddToIndex` is invoked just before a form submission is saved to the storage index. At this point the form submission has been validated according to the form setup. This event is cancelable. If it is cancelled, the form submission will appear to the end user as having failed a validation with the error message supplied by the event handler, and nothing will be saved to the storage index.
* `AfterAddToIndex` is invoked immediately after a form submission has been saved to the storage index.

There's an example of how to use the form submission events in the [samples](../Samples/Event%20handling/) section.

## Email sending events
Before any form submission emails are sent (notification and confirmation emails), the `BeforeSendMail` event is invoked so you can manipulate the `MailMessage` as you please. This event is cancelable. If it is cancelled, the email will not be sent.

## Creating a custom condition
You can create your own custom conditions for actions and cross field validations. Read more [here](extend_condition.md).

## Replacing the default storage 
The storage for form submissions can be replaced by your own custom implementation (or with one of the [sample implementations](../Samples/)). Read more [here](storage.md).

## Custom handling of submission limitations
Form Editor supports limiting the submissions made to a specific form per user. The default implementation uses a cookie to track which forms the users have submitted. If this doesn't work for you, you can create your own handler (or extend the default one).

You can replace the handling globally in `FormEditor.config`, or per instance by setting `FormModel.MaxSubmissionsForCurrentUserHandler`.
