# Gleam HTTP

Types and functions for HTTP clients and servers!

## HTTP Service Example

```rust
import gleam/http/elli
import gleam/http.{Request, Response}
import gleam/bit_builder.{BitBuilder}

// Define a HTTP service
//
pub fn my_service(req: Request(BitString)) -> Response(BitBuilder) {
  let body = bit_builder.from_string("Hello, world!")

  http.response(200)
  |> http.prepend_resp_header("made-with", "Gleam")
  |> http.set_resp_body(body)
}

// Start it on port 3000 using the Elli web server
//
pub fn start() {
  elli.start(my_service, on_port: 3000)
}
```

In the example above the Elli Erlang web server is used to run the Gleam HTTP
service. Here's a full list of the adapters available, sorted alphabetically.

| Adapter                  | About                                                    |
| ---                      | ---                                                      |
| [gleam_cowboy][cowboy-adapter] | [Cowboy][cowboy] is an Erlang HTTP2 & HTTP1.1 web server |
| [gleam_elli][elli-adapter]     | [Elli][elli] is an Erlang HTTP1.1 web server             |
| [gleam_plug][plug-adapter]     | [Plug][plug] is an Elixir web application interface      |

[cowboy]:https://github.com/ninenines/cowboy
[cowboy-adapter]: https://github.com/gleam-experiments/cowboy
[elli]:https://github.com/elli-lib/elli
[elli-adapter]: https://github.com/elixir-plug/plug
[plug]:https://github.com/elli-lib/elli
[plug-adapter]: https://github.com/gleam-experiments/plug
