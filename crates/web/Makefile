.PHONY: all test

all: src/ue_sim_api.rs
src/ue_sim_api.rs: src/ue-sim-api.h
	bindgen --no-layout-tests $^ -o $@

all: test
test:
	-pkill web
	-rm core.*
	cargo build
	cargo run &
	sleep 3s
	./test.bash

src/kafka-bindings.rs: src/sim-api.h
	bindgen --no-layout-tests $^ -o $@
