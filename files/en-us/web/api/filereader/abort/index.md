---
title: "FileReader: abort() method"
short-title: abort()
slug: Web/API/FileReader/abort
page-type: web-api-instance-method
browser-compat: api.FileReader.abort
---

{{APIRef("File API")}}{{AvailableInWorkers}}

The **`abort()`** method of the {{domxref("FileReader")}} interface aborts the read operation. Upon return,
the {{domxref("FileReader.readyState","readyState")}} will be `DONE`.

## Syntax

```js-nolint
abort()
```

### Parameters

None.

### Return value

None ({{jsxref("undefined")}}).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("FileReader")}}
