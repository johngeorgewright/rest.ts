NODE_MODULES=node_modules/.makets
BIN=dist/index.js
SRC=$(shell find src -type f -name '*.ts')

.PHONY: build
build: $(BIN)

clean:
	rm -rf dist

.PHONY: lint
lint:
	../../node_modules/.bin/tslint -p .

.PHONY: publish
publish: dist # This will fail if we forgot to keep the build directory during the publish phase
	npm publish || true

$(BIN): $(SRC) $(NODE_MODULES) tsconfig.json
	../../node_modules/.bin/tsc -p .

$(NODE_MODULES): package.json package-lock.json
	npm install
	touch node_modules/.makets
