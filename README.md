[![Codeship Status for AreaHQ/logging](https://codeship.com/projects/a2b1c4c0-a3a2-0133-00d6-3641d785a31d/status?branch=master)](https://codeship.com/projects/129304)

# Logging

A simple leveled logging library with coloured output.

Log levels:
* `INFO` (blue)
* `WARNING` (pink)
* `ERROR` (red)
* `FATAL` (red)

Formatters:
* `DefaultFormatter`
* `ColouredFormatter`

Example usage:

```go
package main

import (
	"github.com/AreaHQ/logging"
)

var (
	plainLogger    *logging.Logger
	colouredLogger *logging.Logger
)

func init() {
	plainLogger = logging.New(nil, nil, nil)
	colouredLogger = logging.New(nil, nil, new(logging.ColouredFormatter))
}

func main() {
	plainLogger.Info("log message")
	plainLogger.Infof("formatter %s %s", "log", "message")
	colouredLogger.Info("log message")
	colouredLogger.Infof("formatter %s %s", "log", "message")

	plainLogger.Warning("log message")
	plainLogger.Warningf("formatter %s %s", "log", "message")
	colouredLogger.Warning("log message")
	colouredLogger.Warningf("formatter %s %s", "log", "message")

	plainLogger.Error("log message")
	plainLogger.Errorf("formatter %s %s", "log", "message")
	colouredLogger.Error("log message")
	colouredLogger.Errorf("formatter %s %s", "log", "message")

	// Not that logger.Fatal/f does not exit program execution
	// To emulate log.Fatal/f, follow with os.Exit(1)
	plainLogger.Fatal("log message")
	plainLogger.Fatalf("formatter %s %s", "log", "message")
	colouredLogger.Fatal("log message")
	colouredLogger.Fatalf("formatter %s %s", "log", "message")
}
```
