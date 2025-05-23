---
title: "Blocked: All third-party storage access requests"
slug: Web/Privacy/Guides/Storage_Access_Policy/Errors/CookieBlockedForeign
page-type: guide
sidebar: privacy
---

A request to access cookies or storage was blocked because it came from a third-party (a different origin) and content blocking is enabled.

## Message

Firefox:

```plain
CookieBlockedForeign=Request to access cookies or storage on "X" was blocked because we are blocking all third-party storage access requests and content blocking is enabled.
```

## What can be done

The permission can be changed or removed by:

- Going to _Preferences > Content Blocking_ and either
- adding an exception with the _Manage Exceptions_… button
- choosing the _Custom_ Content Blocking and unchecking the _Cookies_ checkbox

If the resource that is being blocked doesn't need authentication, you can fix the warning message by adding a `crossorigin="anonymous"` attribute to the relevant element.

## See also

- [Content blocking](https://support.mozilla.org/en-US/kb/content-blocking) on [support.mozilla.org](https://support.mozilla.org/)
- [The `crossorigin` attribute](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin)
