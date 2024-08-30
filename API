package main

import (
	"encoding/json"
	"io"
	"log"
	"net/http"

	"github.com/gorilla/mux"
)

type Customers struct {
	Customers []Customer `json:"clientes"`
}

type Customer struct {
	ID      int      `json:"ID"`
	Name    string   `json:"Name"`
	Age     int      `json:"Age"`
	Cel     string   `json:"Cel"`
	Address *Address `json:"Address"`
}

type Address struct {
	Road   string          `json:"Road"`
	Number json.RawMessage `json:"Number"`
	City   string          `json:"City"`
}

var customers Customers

func main() {
	response, err := http.Get("https://raw.githubusercontent.com/viniciusgarciam/viniciusgarciam.github.io/api/clientes")
	if err != nil {
		log.Fatalf("Failed to fetch customers: %v", err)
	}
	defer response.Body.Close()

	responseData, err := io.ReadAll(response.Body)
	if err != nil {
		log.Fatalf("Failed to read response data: %v", err)
	}

	if err := json.Unmarshal(responseData, &customers); err != nil {
		log.Fatalf("Failed to unmarshal JSON: %v", err)
	}

	r := mux.NewRouter()
	r.HandleFunc("/Customer1", customer1Handler).Methods("GET")
	r.HandleFunc("/Customer2", customer2Handler).Methods("GET")
	r.HandleFunc("/Customer3", customer3Handler).Methods("GET")
	r.HandleFunc("/Customer4", customer4Handler).Methods("GET")
	r.HandleFunc("/", indexHandler).Methods("GET")

	log.Fatal(http.ListenAndServe(":8000", r))
}

func indexHandler(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "application/json")
	json.NewEncoder(w).Encode(customers.Customers)
}

func customer1Handler(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "application/json")
	if len(customers.Customers) > 0 {
		json.NewEncoder(w).Encode(customers.Customers[1])
	} else {
		http.Error(w, "Customer not found", http.StatusNotFound)
	}
}

func customer2Handler(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "application/json")
	if len(customers.Customers) > 1 {
		json.NewEncoder(w).Encode(customers.Customers[2])
	} else {
		http.Error(w, "Customer not found", http.StatusNotFound)
	}
}

func customer3Handler(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "application/json")
	if len(customers.Customers) > 2 {
		json.NewEncoder(w).Encode(customers.Customers[3])
	} else {
		http.Error(w, "Customer not found", http.StatusNotFound)
	}
}

func customer4Handler(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "application/json")
	if len(customers.Customers) > 3 {
		json.NewEncoder(w).Encode(customers.Customers[4])
	} else {
		http.Error(w, "Customer not found", http.StatusNotFound)
	}
}
