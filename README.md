# Tower HTTP

Tower middlewares and utilities for HTTP clients and servers

[![Build status](https://github.com/tower-rs/tower-http/workflows/CI/badge.svg)](https://github.com/tower-rs/tower-http/actions)

More information about this crate can be found in the [crate documentation][dox].

[dox]: https://tower-rs.github.io/tower-http/tower_http

**This library is not production ready. Do not try to use it in a production
environment or you will regret it!** This crate is still under active
development and there has not yet been any focus on documentation (because you
shouldn't be using it yet!).

## Middlewares

These are the middlewares included in this crate:

- `AddExtension`: Stick some shareable value in [request extensions].
- `Compression`: Apply compression to responses. Uses the `Accept-Encoding` header to pick an encoding. Supports gzip, deflate, brotli, and zstd. Requires hyper because it uses `hyper::Body`.
- `DebugEnterLeave`: Print when entering and leaving a middleware. Useful for verifying the order in which your middlewares run.
- `Metrics`: Record high level metrics. Uses the [metrics] crate.
- `PropagateHeader`: Propagate a header from the request to the response.
- `SensitiveHeader`: Marks a given header as [sensitive] so it wont show up in logs.
- `SetResponseHeader`: Set a header on the response.
- `Trace`: High level tracing of requests and responses.
- `WrapInSpan`: Wrap response futures in a `tracing::Span`.

Middlewares uses the [`http`] crate as the HTTP interface so they're compatible with any library or framework that also uses [`http`]. For example hyper and actix.

The middlewares were originally extracted from one of [@EmbarkStudios] internal projects.

All middlewares are disabled by default and can be enabled using a cargo feature. The feature `full` turns on everything.

[`http`]: https://crates.io/crates/http
[sensitive]: https://docs.rs/http/latest/http/header/struct.HeaderValue.html#method.set_sensitive
[request extensions]: https://docs.rs/http/latest/http/struct.Extensions.html
[metrics]: https://crates.io/crates/metrics
[@EmbarkStudios]: https://github.com/EmbarkStudios
