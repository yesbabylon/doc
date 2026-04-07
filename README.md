# Documentation Builder Template

This repository provides a **minimal, declarative, and reproducible system** to build a unified documentation website using [MkDocs](https://www.mkdocs.org/), by aggregating documentation from multiple Git repositories.



## Concept

Instead of maintaining separate documentation repositories or manually copying files, this template allows you to:

- Define multiple documentation sources
- Automatically fetch and assemble them
- Generate a complete MkDocs structure
- Build and serve the documentation

The system follows a simple pipeline:

```

sources.yml → build.sh → docs/ → mkdocs.yml → MkDocs

```



## Repository Structure

```

.
├── sources.yml     # List of documentation sources
├── build.sh        # Build script (fetch + assemble)
├── docs/           # Generated documentation (output)
└── mkdocs.yml      # MkDocs configuration

````



## How It Works

### 1. Define sources

All documentation sources are declared in `sources.yml`.

Each source specifies:
- the Git repository
- the branch
- the path to documentation inside the repo
- the target directory in the final documentation

Examples:

```yaml
sources:
  - name: Project A
    repo: https://github.com/org/project-a.git
    branch: main
    path: doc
    target: project-a

  - name: Project B
    repo: https://github.com/org/project-b.git
    branch: main
    path: docs
    target: project-b
```




```yaml
sources:
  - name: Discope
    repo: https://github.com/discope-pms/discope.git
    branch: main
    path: doc
    target: .

  - name: Lathus
    repo: https://github.com/discope-pms/discope.git
    branch: main
    path: lathus/doc
    target: lathus
    
  - name: Kaleo
    repo: https://github.com/discope-pms/discope.git
    branch: main
    path: kaleo/doc
    target: kaleo
```



### 2. Run the build script

```bash
./build.sh
```

The script will:

1. Clone each repository (shallow clone)
2. Extract the specified documentation folder
3. Copy content into `docs/<target>/`
4. Merge or generate navigation (`nav.yml`)
5. Inject the final navigation into `mkdocs.yml`



### 3. Serve or build the documentation

```bash
mkdocs serve
```

or

```bash
mkdocs build
```



## Navigation Handling

For each source:

* If a `nav.yml` file exists → it is used
* Otherwise → a default navigation is generated using `index.md`

The final navigation is automatically assembled and injected into `mkdocs.yml`.



## Key Principles

### Single Source of Truth

Documentation remains inside each project repository.

### No Duplication

No need to maintain separate documentation repositories.

### Declarative Configuration

All composition is defined in `sources.yml`.

### Stateless Build

The `docs/` folder is fully generated and can be rebuilt at any time.



## Requirements

* `git`
* `mkdocs`
* `yq` (for YAML parsing)

Install `yq`:
👉 [https://github.com/mikefarah/yq](https://github.com/mikefarah/yq)



## Usage Workflow

1. Edit `sources.yml`
2. Adjust `mkdocs.yml` if needed
3. Run `./build.sh`
4. Run `mkdocs serve`



## Extensibility

This template is intentionally simple but can be extended with:

* Git caching (`git pull` instead of clone)
* Webhook-based rebuilds
* File filtering / exclusion
* Link rewriting
* Multi-version documentation
* CI/CD integration



## Limitations

* Assumes each source contains valid Markdown documentation
* Relative links between sources are not automatically rewritten
* No conflict resolution between identical file names across sources

