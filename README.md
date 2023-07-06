# Clojure hooks for pre-commit

[Clojure](https://clojure.org/) package for [pre-commit](https://pre-commit.com) hooks. Integrates with popular packages such as 

- [clj-kondo (static linter)](https://github.com/clj-kondo/clj-kondo)
- [kaocha (unit testing)](https://github.com/lambdaisland/kaocha)
- [zprint (file formatting)](https://github.com/kkinnear/zprint)
- [cljfmt (file formatting)](https://github.com/weavejester/cljfmt)

## Configure pre-commit

1. Install pre-commit: `$ pip install pre-commit`
2. Add a pre-commit configuration: create a file named `.pre-commit-config.yaml`
3. Install the git hook scripts: `$ pre-commit install`  => now pre-commit will run automatically on `git commit`!
4. (Optional) Run against all the files: `$ pre-commit run --all-files`

Or follow the install instructions [here](https://pre-commit.com/#quick-start)


## Usage with .pre-commit-config.yaml

```yaml
repos:
-   repo: https://github.com/humorless/pre-commit-clojure
    rev: b0612489704cec536e2687ec570b47795c993f42
    hooks:
    -   id: cljfmt
    -   id: kaocha
```

## Passing arguments to clj-kondo

```yaml
-   repo: https://github.com/vincentjames501/pre-commit-clojure
    rev: v1.x
    hooks:

    -   id: clj-kondo
        args: ['error']
    -   id: zprint
    -   id: kaocha
        # Must install pre-push: $ pre-commit install --hook-type pre-push
        # https://pre-commit.com/#pre-commit-during-push
        stages: [merge-commit, push, manual]  
        always_run: true
```
