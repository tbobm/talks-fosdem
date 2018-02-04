# Writing Node.js modules in Rust

author:Farid Nouri Neshat
@Onlindata

ref: https://neon-bindings.com
ref: https://github.com/GabrielCastro/neon-serde

## You need a Node.js Native Addon because

- Performance
- Native library
- Freedom in memory managemnet
- Os lw level apis
- Your dont like javascript

Well, how to write a node.js addon?

You probably don't like C/C++ as wel

**NEON**

## Example

```rust
extern crate neon;

use neon::...

fn hello(call: Call) -> KsResult<JsString {
    let scope = call.scope;
    Ok(JsString::new(scope, "hello node").unwrap());
}

register_module(s, {
    e.export("Hello", hello)
})
```

```js
var addon = require('../../addon');

console.log(addon.hello());
```

## Performance

- dont underestimate js
- try to minimize crossing the rust/js bridge
- interacting with js objects can potentially invoke js
- sometime (node.js) buffers are faster than strings

Avoid calling rust module multiple time. Do one-shot processing.

## Scope?

- Js is garbage collected
- V8 needs hints on objects created outside javascript

## Buffers ?

usually faster to use buffer than javascript strings

```rust
let mut result_buf = (JsBuffer::new(scope, arg.len() as u32))?;
```
## Classes

Neon created a macro for types.
Can have own rust classes in Neon and use them in JS.

Properties, methods, hidden properties.

```rust
pub class JsGreater for Greater {
    init(call) {
        Ok(Greater {
            greeting: greeting
        })
    }
}
```

## Tasks

> for background jobs

```rust
impl Task for SuccessTask {
    // ...
    fn perform(&self) //...
    fn complete//...
}
```

## Tip

try neon-serde!

Takes care of the conversion of arguments and everything.
Allows to write rust code for nodejs in a painless way.

but might be a bit too much abstract


## Who uses Neon?

- libsodium (?) nodejs binding for rust-sodium using the wire app.
- compilers and parsers

kind of like the C++ usage.
