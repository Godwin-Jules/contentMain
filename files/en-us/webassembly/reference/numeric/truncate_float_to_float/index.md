---
title: Truncate (float to float)
slug: WebAssembly/Reference/Numeric/Truncate_float_to_float
page-type: webassembly-instruction
sidebar: webassemblysidebar
---

The **`trunc`** instructions, short for _truncate_, are used for getting the value of a number without its fractional part.

**`trunc`** differs from **`floor`** when used on negative numbers, **`floor`** will round down in those cases while **`trunc`** will round up.

There's another [**`trunc`**](/en-US/docs/WebAssembly/Reference/Numeric/Truncate_float_to_int) instruction that truncates the fractional part of a floating point and converts it to an integer.

{{InteractiveExample("Wat Demo: trunc_float_to_float", "tabbed-taller")}}

```wat interactive-example
(module
  (import "console" "log" (func $log (param f32)))
  (func $main

    f32.const -2.7 ;; load a number onto the stack
    f32.trunc ;; discard everything after the decimal point
    call $log ;; log the result

  )
  (start $main)
)
```

```js interactive-example
const url = "{%wasm-url%}";
await WebAssembly.instantiateStreaming(fetch(url), { console });
```

## Syntax

```wat
;; load a number onto the stack
f32.const 2.7

;; discard the fractional part (.7)
f32.trunc

;; the top item on the stack will now be 2
```

| Instruction | Binary opcode |
| ----------- | ------------- |
| `f32.trunc` | `0x8f`        |
| `f64.trunc` | `0x9d`        |
