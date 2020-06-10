# CORS

![Release](https://img.shields.io/github/release/gofiber/cors.svg)
[![Discord](https://img.shields.io/badge/discord-join%20channel-7289DA)](https://gofiber.io/discord)
![Test](https://github.com/gofiber/cors/workflows/Test/badge.svg)
![Security](https://github.com/gofiber/cors/workflows/Security/badge.svg)
![Linter](https://github.com/gofiber/cors/workflows/Linter/badge.svg)

### Install
```
go get -u github.com/gofiber/fiber
go get -u github.com/gofiber/cors
```
### config
| Property | Type | Description | Default |	
| :--- | :--- | :--- | :--- |	
| Filter | `func(*Ctx) bool` | Defines a function to skip middleware | `nil` |	
| AllowOrigins | `[]string` | AllowOrigin defines a list of origins that may access the resource. | `[]string{"*"}` |	
| AllowMethods | `[]string` | AllowMethods defines a list methods allowed when accessing the resource. This is used in response to a preflight request. | `[]string{"GET", "POST", "HEAD", "PUT", "DELETE", "PATCH"}` |	
| AllowCredentials | `bool` | AllowCredentials indicates whether or not the response to the request can be exposed when the credentials flag is true. When used as part of a response to a preflight request, this indicates whether or not the actual request can be made using credentials. | `false` |	
| ExposeHeaders | `[]string` | ExposeHeaders defines a whitelist headers that clients are allowed to access. | `[]string{}` |	
| MaxAge | `int` | MaxAge indicates how long \(in seconds\) the results of a preflight request can be cached. | `0` |
### Example
```go
package main

import (
  "github.com/gofiber/fiber"
  "github.com/gofiber/cors"
)

func main() {
  app := fiber.New()

  app.Use(cors.New())

  app.Get("/", func(c *fiber.Ctx) {
    c.Send("Welcome!")
  }) 

  app.Listen(3000)
}
```
### Test
```curl
curl -H "Origin: http://example.com" --verbose http://localhost:3000
```
