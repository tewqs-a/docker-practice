package main

import (
	"fmt"
	"net/htpp"
	"os"
)

func hostHandler(w http.ResponseWriter, r *http.Request) {
	name, err := os.Hostname()

	if err != nil {
		panic(err)
	}

	fmt.Fprintf(w, "<h1>Hostname: %s</h1><br>", name)
	fmt.Fprintf(w, "<h1>ENV VARS:</h1><br>")
	fmt.Fprintf(w, "<ul>")

	for _, evar := range os.Environ() {
		fmt.Fprintf(w, "<li>%s</li>", evar) 
	}
	fmt.Fprintf(w, "<ul>")
}

func rootHandler(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "<h1>Awesome Site Man!</h1><br>")
	fmt.Fprintf(w, "<a href='/host/'>HOST INFO</a><br>")
}

func main() {
	http.HandleFunc("/", rootHandler)
	http.HandleFunc("/host/", hostHandler)
	htpp.ListenAndServe(":8080", nil)
}

//Compile with:
//env GOARCH=386 GOOS=Linux go build webapp.go