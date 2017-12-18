# ctxlogrus
`import "github.com/improbable-eng/go-httpwares/logging/logrus/ctxlogrus"`

* [Overview](#pkg-overview)
* [Imported Packages](#pkg-imports)
* [Index](#pkg-index)
* [Examples](#pkg-examples)

## <a name="pkg-overview">Overview</a>
ctxlogrus allows you to store or extract a logrus logger from the context.

The tags on the logger are populated by http_ctxtags if they have already been set.

## <a name="pkg-imports">Imported Packages</a>

- [github.com/improbable-eng/go-httpwares/tags](./../../../tags)
- [github.com/sirupsen/logrus](https://godoc.org/github.com/sirupsen/logrus)
- [golang.org/x/net/context](https://godoc.org/golang.org/x/net/context)

## <a name="pkg-index">Index</a>
* [func Extract(ctx context.Context) \*logrus.Entry](#Extract)
* [func ToContext(ctx context.Context, entry \*logrus.Entry) context.Context](#ToContext)

#### <a name="pkg-examples">Examples</a>
* [Extract](#example_Extract)

#### <a name="pkg-files">Package files</a>
[context.go](./context.go) [doc.go](./doc.go) [noop.go](./noop.go) 

## <a name="Extract">func</a> [Extract](./context.go#L20)
``` go
func Extract(ctx context.Context) *logrus.Entry
```
Extract takes the call-scoped logrus.Entry from http_logrus middleware.

The logger will have fields pre-populated using http_ctxtags.

If the http_logrus middleware wasn't used, a no-op `logrus.Entry` is returned. This makes it safe to use regardless.

#### Example:

<details>
<summary>Click to expand code.</summary>

```go
ctx := context.Background()
entry := ctxlogrus.Extract(ctx)
entry.Info("logging")
```

</details>

## <a name="ToContext">func</a> [ToContext](./context.go#L30)
``` go
func ToContext(ctx context.Context, entry *logrus.Entry) context.Context
```
ToContext sets a logrus logger on the context, which can then obtained by Extract.

- - -
Generated by [godoc2ghmd](https://github.com/GandalfUK/godoc2ghmd)