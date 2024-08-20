package main

import (
	"fmt"
	"time"
)

func ping(c chan string) {
	for i := 0; ; i++ {
		c <- "Ping"
	}
}
func pong(c chan string) {
	for i := 0; ; i++ {
		c <- "Pong"
	}
}
func print(c chan string) {
	for {
		msg := <-c
		fmt.Println(msg)
		time.Sleep(time.Second * 1)
	}
}
func main() {
	var c chan string = make(chan string)

	go ping(c)
	go pong(c)
	go print(c)

	var entrada string
	fmt.Scanln(&entrada)
}
