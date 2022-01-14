# Json Tag Extractor for [Go-Playground Validator](https://github.com/go-playground/validator)

This is Gin Middleware that aim to extract json tag and than store it to `FieldError.Field()` object.

## Example

- Register Middleware

```go
engine := gin.New()
engine.Use(validator.RegisterJsonTag())
```

- In Your Controller

```go
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
