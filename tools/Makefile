.PHONY: build sila clean test lint fill

build:
	go build -o rpctestgen ./cmd/rpctestgen
	go build -o speccheck ./cmd/speccheck
	go build -o specgen ./cmd/specgen

sila:
	go build -o sila github.com/sila-chain/go-sila/cmd/sila

clean:
	rm -f ./sila ./speccheck ./rpctestgen ./specgen
	rm -fr ../tests

test:
	go test ./...

lint:
	gofmt -d ./
	go vet ./...
	staticcheck ./...

fill: build sila
	./rpctestgen --bin ./sila -chain ./chain --out ../tests
