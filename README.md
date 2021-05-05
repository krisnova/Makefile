# Makefile

There is a legendary `make help` target that has been floating around my career.

The idea is that you can add a simple `help` target to your makefile. Then get `make help` for free just by adding comments to a target.

```
example: ## Any double commented target now becomes help!
```

### Sebastian Gryczan

Contributed by [sgryczan](https://github.com/sgryczan).

```bash
help:
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[32m%-30s\033[0m %s\n", $$1, $$2}'
	
```

### Kris Nóva

```bash
.PHONY: help
help:  ## Show help messages for make targets
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[32m%-30s\033[0m %s\n", $$1, $$2}'
```
