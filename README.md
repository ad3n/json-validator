# Json Tag Extractor for [Go-Playground Validator](https://github.com/go-playground/validator)

This is Gin Middleware that aim to extract json tag and than store it to `FieldError.Field()` object.

## Install

`go get -u github.com/ad3n/json-validator`

## Example

- Register Middleware

```go
import jsonvalidator "github.com/ad3n/json-validator"

engine := gin.New()
engine.Use(jsonvalidator.RegisterJsonTag())
```

- In Your Controller

```go
import "github.com/go-playground/validator/v10"

err := c.ShouldBind(&q)
if err != nil {
    verr, ok := err.(validator.ValidationErrors)
    if ok {
        for _, err := range verr {
            fmt.Println(err.Field())
        }
    }
}
```

## Credit

Original discussion: [go-playground/validator#258](https://github.com/go-playground/validator/issues/258)
