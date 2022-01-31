
# dedebme - embeded web server

**Usage**

```go
package main

import (
	"flag"
	"fmt"
	"log"
	"net/http"

	"github.com/socheatsok78-lab/dedebme"
)

import "embed"

//go:embed *
var Assets embed.FS

func main() {
	var port int
	flag.IntVar(&port, "port", 8080, "The port to listen on")
	flag.Parse()

	http.Handle("/", dedebme.Server(Assets))

	addr := fmt.Sprintf("localhost:%d", port)
	fmt.Printf("Serving app at http://%s\n", addr)
	log.Fatalln(http.ListenAndServe(addr, nil))
}
```
