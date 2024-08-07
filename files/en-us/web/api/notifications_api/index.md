---
title: Notifications API
slug: Web/API/Notifications_API
page-type: web-api-overview
browser-compat:
  - api.Notification
  - api.ServiceWorkerRegistration.showNotification
  - api.ServiceWorkerRegistration.getNotifications
spec-urls: https://notifications.spec.whatwg.org/
---

{{DefaultAPISidebar("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

The Notifications API allows web pages to control the display of system notifications to the end user. These are outside the top-level browsing context viewport, so therefore can be displayed even when the user has switched tabs or moved to a different app. The API is designed to be compatible with existing notification systems, across different platforms.

## Concepts and usage

On supported platforms, showing a system notification generally involves two things. First, the user needs to grant the current origin permission to display system notifications, which is generally done when the app or site initializes, using the {{domxref("Notification.requestPermission_static", "Notification.requestPermission()")}} method.
This method should only be called when handling a user gesture, such as when handling a mouse click. For example:

```js
btn.addEventListener("click", () => {
  let promise = Notification.requestPermission();
  // wait for permission
});
```

This will spawn a request dialog, along the following lines:

![A dialog box asking the user to allow notifications from that origin. There are options to never allow or allow notifications.](screen_shot_2019-12-11_at_9.59.14_am.png)

From here the user can choose to allow notifications from this origin, or block them. Once a choice has been made, the setting will generally persist for the current session.

Next, a new notification is created using the {{domxref("Notification.Notification","Notification()")}} constructor. This must be passed a title argument, and can optionally be passed an options object to specify options, such as text direction, body text, icon to display, notification sound to play, and more.

In addition, the Notifications API spec specifies a number of additions to the [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API), to allow service workers to fire notifications.

> **Note:** To find out more about using notifications in your own app, read [Using the Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API).

## Interfaces

- {{domxref("Notification")}}
  - : Defines a notification object.
- {{domxref("NotificationEvent")}}
  - : Represents a notification event dispatched on the {{domxref("ServiceWorkerGlobalScope")}} of a {{domxref("ServiceWorker")}}.

### Extensions to other interfaces

- {{domxref("ServiceWorkerGlobalScope/notificationclick_event", "notificationclick")}} event
  - : Occurs when a user clicks on a displayed notification.
- {{domxref("ServiceWorkerGlobalScope/notificationclose_event", "notificationclose")}} event
  - : Occurs when a user closes a displayed notification.
- {{domxref("ServiceWorkerRegistration.getNotifications()")}}
  - : Returns a list of the notifications in the order that they were created from the current origin via the current service worker registration.
- {{domxref("ServiceWorkerRegistration.showNotification()")}}
  - : Displays the notification with the requested title.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using the Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)
