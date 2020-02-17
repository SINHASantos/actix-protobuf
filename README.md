# Actix-web ProtoBuf [![Build Status](https://travis-ci.org/actix/actix-protobuf.svg?branch=master)](https://travis-ci.org/actix/actix-protobuf) [![codecov](https://codecov.io/gh/actix/actix-protobuf/branch/master/graph/badge.svg)](https://codecov.io/gh/actix/actix-protobuf) [![crates.io](http://meritbadge.herokuapp.com/actix-protobuf)](https://crates.io/crates/actix-protobuf) [![Join the chat at https://gitter.im/actix/actix](https://badges.gitter.im/actix/actix.svg)](https://gitter.im/actix/actix?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Protobuf support for actix-web framework.

**NOTICE: This repository has been archived. Please visit https://github.com/actix/actix-extras instead.**


## Example

```rust,ignore
use actix_protobuf::*;
use actix_web::*;

#[derive(Clone, PartialEq, Message)]
pub struct MyObj {
    #[prost(int32, tag = "1")]
    pub number: i32,
    #[prost(string, tag = "2")]
    pub name: String,
}

async fn index(msg: ProtoBuf<MyObj>) -> Result<HttpResponse> {
    println!("model: {:?}", msg);
    HttpResponse::Ok().protobuf(msg.0) // <- send response
}
```

See [here](https://github.com/actix/actix-protobuf/tree/master/examples/prost-example) for the complete example.

## License

This project is licensed under either of

* Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0))
* MIT license ([LICENSE-MIT](LICENSE-MIT) or [http://opensource.org/licenses/MIT](http://opensource.org/licenses/MIT))

at your option.
