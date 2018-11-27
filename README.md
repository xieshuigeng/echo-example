# echo-example
## quick start

    mkdir ~/go/src/golang.org/x
    git clone https://github.com/golang/crypto.git
    go get -u github.com/labstack/echo/...
    
## server.go test

    package main

    import (
      "net/http"

      "github.com/labstack/echo"
    )

    //getUser for e.GET("/users/:id", getUser)
    func getUser(c echo.Context) error {
      id := c.Param("id")
      return c.String(http.StatusOK, id)
    }

    func main() {
      e := echo.New()
      e.GET("/", func(c echo.Context) error {
        return c.String(http.StatusOK, "Hello, World!")
      })
      e.GET("/users/:id", getUser)

      e.Logger.Fatal(e.Start(":1323"))
    }
    
# test code

    go run server.go
    
    curl http://localhost:1323/
    curl http://localhost:1323/users/Joe
