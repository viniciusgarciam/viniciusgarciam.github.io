package main

import "fmt"

func main() {
	w := sum(20, 2, 2)
	x := subtract(20, 2, 2)
	y := multiply(20, 2, 2)
	z := division(20, 2, 2)
	fmt.Println("Sum:", w)
	fmt.Println("Subtract:", x)
	fmt.Println("Multiply:", y)
	fmt.Println("Division:", z)
}

func sum(i ...int) int {
	total := 0
	for _, v := range i {
		total += v
	}
	return total
}
func subtract(i ...int) int {
	total := i[0]
	for _, v := range i[1:] {
		total -= v
	}
	return total
}
func multiply(i ...int) int {
	total := 1
	for _, v := range i {
		total *= v
	}
	return total
}
func division(i ...int) int {
	total := i[0]
	for _, v := range i[1:] {
		total /= v
	}
	return total
}
