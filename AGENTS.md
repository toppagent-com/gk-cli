# AGENTS.md — Comprehensive Coding Skills for Claude

> **1500 skills across 20 categories** · optimized for Claude coding agents · GitKraken CLI repository context

---

## Table of Contents

1. [Environment & Repository Setup](#1-environment--repository-setup)
2. [Core Programming Fundamentals](#2-core-programming-fundamentals)
3. [Algorithms & Data Structures](#3-algorithms--data-structures)
4. [Python Mastery](#4-python-mastery)
5. [JavaScript & TypeScript](#5-javascript--typescript)
6. [Go Development](#6-go-development)
7. [Rust Systems Programming](#7-rust-systems-programming)
8. [Database & SQL](#8-database--sql)
9. [API Design & REST/GraphQL](#9-api-design--restgraphql)
10. [Git & Version Control](#10-git--version-control)
11. [Testing & Quality Assurance](#11-testing--quality-assurance)
12. [Security Engineering](#12-security-engineering)
13. [Performance Optimization](#13-performance-optimization)
14. [DevOps & CI/CD](#14-devops--cicd)
15. [Cloud & Infrastructure](#15-cloud--infrastructure)
16. [Frontend & UI Engineering](#16-frontend--ui-engineering)
17. [Backend Architecture](#17-backend-architecture)
18. [Debugging & Root Cause Analysis](#18-debugging--root-cause-analysis)
19. [Code Review & Clean Code](#19-code-review--clean-code)
20. [System Design & AI/Claude Integration](#20-system-design--aiclaude-integration)

---

## Repository Context

This is the **GitKraken CLI** (`gk`) repository — a Go-based command-line tool for managing multi-repo workflows, AI-powered commits/PRs, and MCP server functionality.

- Language: **Go**
- Shell: **bash**
- OS: **Ubuntu/Linux** (cloud agent environment)
- Git branch: `cursor/claude-agent-skills-8494`
- No test suite present in workspace root; validate via build + lint

### Quick Commands

```bash
# Build
go build ./...

# Lint (if golangci-lint present)
golangci-lint run

# Format
gofmt -w .
goimports -w .

# Vet
go vet ./...
```

---

## 1. Environment & Repository Setup

> **75 skills** for configuring, initializing, and maintaining a productive coding environment.

1. Always run `go version` before coding in a Go repo to confirm the runtime matches `go.mod`.
2. Read `go.mod` and `go.sum` immediately to understand module path, Go version, and direct dependencies.
3. Check `go.sum` for unexpected changes after dependency operations — it prevents supply-chain attacks.
4. Use `go env` to inspect all Go environment variables (`GOPATH`, `GOPROXY`, `GOROOT`, etc.) before debugging module issues.
5. Set `GOPROXY=direct` when working offline or when `proxy.golang.org` is unreachable.
6. Use `go mod tidy` after every dependency change to keep `go.mod`/`go.sum` clean.
7. Use `go mod verify` to confirm that cached modules match their checksums.
8. Run `go mod download` to pre-fetch all dependencies before going offline.
9. Use `go work` (Go workspaces) when developing multiple interdependent modules simultaneously.
10. Prefer `go install tool@version` over global binary installs for reproducibility.
11. Keep a `.tool-versions` or `Makefile` to document exact tool versions used in the project.
12. Use `direnv` with `.envrc` for per-project environment variable management.
13. Read `Makefile` or `justfile` before writing build commands — always prefer existing conventions.
14. Inspect `.github/workflows/` to understand CI pipeline expectations before committing.
15. Always check `CONTRIBUTING.md` before modifying shared code paths.
16. Use `git log --oneline -20` to understand recent commit history and conventions before starting.
17. Use `git branch -a` to list all remote branches and understand branching strategy.
18. Inspect `.gitignore` to understand excluded artifacts and avoid committing generated files.
19. Use `git stash list` to check for stashed work before pulling or rebasing.
20. Check for `.editorconfig` and apply its indentation/line-ending rules in all edits.
21. Use `which` and `command -v` to verify tool availability before running them.
22. Use `uname -m` to detect CPU architecture (x86_64 vs arm64) before compiling native binaries.
23. Check `/etc/os-release` to identify the Linux distribution before using package managers.
24. Prefer `apt-get install -y --no-install-recommends` for minimal Docker/CI installs.
25. Use `snap install --classic <tool>` when deb packages are unavailable on Ubuntu.
26. Verify `$PATH` before complaining about missing commands — tools may be installed but not on PATH.
27. Use `export PATH="$HOME/go/bin:$PATH"` after `go install` to use installed binaries.
28. Create `.env.example` files to document required environment variables without exposing secrets.
29. Use `envsubst` to template configuration files from environment variables in CI.
30. Always `source` `.bashrc`/`.profile` after modifying them in the same shell session.
31. Use `set -euo pipefail` at the top of all shell scripts for strict error handling.
32. Use `trap 'cleanup' EXIT` in shell scripts to ensure cleanup always runs.
33. Document every non-obvious environment variable with a comment in `.env.example`.
34. Prefer named environment variable groups in `.envrc` with clear section headers.
35. Use `nix-shell` or `nix develop` for fully reproducible development environments.
36. Pin Docker base images to specific digest hashes for reproducible builds.
37. Use `DOCKER_BUILDKIT=1` for faster, more efficient Docker builds with layer caching.
38. Use multi-stage Dockerfiles to separate build and runtime environments.
39. Use `docker compose` (v2) rather than `docker-compose` (v1) for all compose operations.
40. Define `healthcheck` in Dockerfiles so orchestration knows when containers are ready.
41. Always mount code as a volume in development containers — never rebuild for code changes.
42. Use `.dockerignore` to exclude `node_modules`, `vendor`, `.git`, and build artifacts.
43. Verify `ulimit -n` (file descriptor limit) when running many concurrent processes or connections.
44. Use `lsof -i :<port>` or `ss -tlnp` to check what process owns a port before binding.
45. Use `htop` or `top -H` to inspect per-thread CPU usage when debugging performance.
46. Use `strace -p <pid>` to trace system calls of a running process for deep debugging.
47. Use `ldd <binary>` to inspect shared library dependencies of compiled executables.
48. Use `file <binary>` to identify binary format before attempting to run or disassemble.
49. Check `dmesg | tail` for kernel-level errors when processes crash unexpectedly.
50. Use `journalctl -u <service> -f` to stream logs from systemd services.
51. Always clean up background processes you start — store PIDs and kill them after testing.
52. Use `timeout <seconds> <command>` to prevent commands from hanging indefinitely in scripts.
53. Use `tee <file>` to simultaneously display and save command output.
54. Use `script -q -c '<cmd>' /dev/null` to capture interactive terminal output.
55. Prefer `mktemp` over hardcoded `/tmp/foo` for temporary files in scripts.
56. Use `realpath` or `readlink -f` to resolve symlinks to canonical absolute paths.
57. Use `install -m 755 <src> <dst>` instead of `cp` + `chmod` when deploying executables.
58. Use `rsync -av --progress` instead of `cp -r` for large file transfers with progress display.
59. Use `sha256sum` to verify download integrity before executing downloaded binaries.
60. Always verify GPG signatures when available for downloaded packages.
61. Use `curl -fsSL` (fail-silent-show-error-follow-redirects) for reliable script downloads.
62. Use `wget -q --show-progress` for interactive downloads that need visible progress.
63. Prefer `jq` for JSON processing in shell scripts over `python -c` or `sed`/`awk`.
64. Use `yq` for YAML processing in shell scripts.
65. Use `envdir` or `dotenv` to load environment files safely in production scripts.
66. Run `shellcheck <script.sh>` on all shell scripts before committing.
67. Use `shfmt -w <script.sh>` to autoformat shell scripts.
68. Verify crontab syntax with `crontab -l` and test with `run-parts --test`.
69. Use `nc -zv <host> <port>` to test network connectivity before blaming application code.
70. Use `dig <domain>` and `nslookup` to debug DNS resolution issues.
71. Use `curl -v` to inspect full HTTP request/response headers when debugging API calls.
72. Use `openssl s_client -connect <host>:<port>` to debug TLS/SSL certificate issues.
73. Set `TERM=xterm-256color` in non-interactive shells to avoid color code issues.
74. Use `locale` to check character encoding — always prefer `UTF-8` locales.
75. Document every environment-specific quirk in `AGENTS.md` or a dedicated `docs/environment.md`.

---

## 2. Core Programming Fundamentals

> **75 skills** that apply across all languages and paradigms.

1. Write code that is obviously correct before optimizing for performance.
2. Name variables, functions, and types to express intent — the name is the best comment.
3. Prefer composition over inheritance in all object-oriented and module designs.
4. Prefer pure functions (no side effects, deterministic output) wherever possible.
5. Keep functions small: a function should do one thing and do it completely.
6. Respect the Single Responsibility Principle — each module, class, or function has one reason to change.
7. Apply the Open/Closed Principle — open for extension, closed for modification.
8. Apply the Liskov Substitution Principle — subtypes must be substitutable for their base types.
9. Apply the Interface Segregation Principle — many specific interfaces over one general interface.
10. Apply the Dependency Inversion Principle — depend on abstractions, not concrete implementations.
11. Make invalid states unrepresentable using the type system.
12. Prefer explicit over implicit — avoid magic that requires readers to memorize hidden rules.
13. Prefer immutability — treat data as immutable unless mutation is explicitly required.
14. Design for failure: every operation that can fail must have an explicit error path.
15. Never swallow errors silently — log, wrap, or propagate every error with context.
16. Use sum types (tagged unions/enums) to model states that are mutually exclusive.
17. Avoid null/nil where possible — use Option types, sentinel values, or default values explicitly.
18. Keep cyclomatic complexity per function below 10 — extract sub-functions when it exceeds this.
19. Avoid deep nesting: maximum 3 levels of indentation is a strong signal to refactor.
20. Use early returns (guard clauses) to reduce nesting and clarify the happy path.
21. Follow the Law of Demeter — a module should only talk to its immediate neighbors.
22. Avoid feature envy — if a function uses mostly another object's data, move it there.
23. Don't repeat yourself (DRY) — but don't abstract prematurely (Rule of Three).
24. YAGNI (You Aren't Gonna Need It) — implement only what is needed today.
25. Write code for the next developer, not just for the compiler.
26. Treat magic numbers as a smell — extract to named constants with explanatory names.
27. Model your domain explicitly — use rich domain types rather than primitive obsession.
28. Use algebraic data types to model domain concepts with precision.
29. Avoid boolean parameters — use enumerations or separate functions instead.
30. Avoid output parameters — return values or use a result struct.
31. Avoid side effects in constructors and `init()` functions.
32. Prefer synchronous code over asynchronous code unless concurrency provides real benefit.
33. Be explicit about concurrency — document which functions are safe to call concurrently.
34. Use bounded queues to provide backpressure in producer-consumer patterns.
35. Design APIs that are hard to misuse — make the correct usage the obvious usage.
36. Document pre-conditions, post-conditions, and invariants in complex functions.
37. Use assertions to enforce invariants in development and test builds.
38. Write code that is easy to delete — avoid tightly coupling unrelated modules.
39. Follow the Principle of Least Surprise — don't do unexpected things in obvious-looking code.
40. Prefer positive conditions (`if isValid`) over negative conditions (`if !isInvalid`).
41. Use table-driven logic (maps, dispatch tables) over long if/else chains.
42. Minimize shared mutable state — prefer message-passing or functional approaches.
43. Be explicit about memory ownership — document who allocates and who frees.
44. Use meaningful prefixes/suffixes for related groups (`Config`, `ConfigBuilder`, `ConfigOptions`).
45. Separate data from behavior where possible (data classes + service functions).
46. Design modules around stable interfaces, not stable implementations.
47. Optimize for reading, not writing — code is read 10x more than it's written.
48. Write "strangler fig" refactors — add new, better code alongside old code, then cut over.
49. Prefer copying data over sharing it when sharing introduces complexity.
50. Identify and document hot paths — only optimize code that profiling confirms is slow.
51. Use constants for timeouts, retries, limits — never hardcode these inline.
52. Make all time-sensitive code configurable — hardcoded durations cause production incidents.
53. Treat time zones explicitly — store all timestamps in UTC; convert at boundaries.
54. Treat configuration as code — version-control all non-secret configuration.
55. Use semantic versioning for libraries and APIs.
56. Document breaking changes explicitly in changelogs.
57. Use feature flags to decouple deployment from release.
58. Write reversible migrations — always provide rollback paths.
59. Design for observability from the start — add structured logging, metrics, and tracing.
60. Use correlation IDs to trace requests across service boundaries.
61. Design idempotent operations — safe to call multiple times with same result.
62. Apply the Robustness Principle conservatively: be strict in what you accept.
63. Fail fast — detect errors as early in the pipeline as possible.
64. Separate validation from business logic — validate at system boundaries, trust internally.
65. Use the Null Object pattern instead of null checks scattered across business logic.
66. Use the Strategy pattern to make algorithms pluggable without conditionals.
67. Use the Builder pattern for objects with many optional parameters.
68. Use the Command pattern for undo/redo, queuing, and logging operations.
69. Use the Observer pattern for decoupled event-driven systems.
70. Prefer event sourcing over mutation logs for audit-critical data.
71. Use sagas/process managers for distributed transactions.
72. Design backward-compatible API changes — add, don't change; deprecate, don't remove.
73. Code defensively at system boundaries — never trust external input.
74. Use structured concurrency — always know the lifetime of every goroutine/thread/task.
75. Leave code better than you found it — the Boy Scout Rule applied to every file you touch.

---

## 3. Algorithms & Data Structures

> **75 skills** for choosing, implementing, and analyzing algorithms and data structures.

1. Know the time/space complexity of every operation you use (Big-O by heart).
2. Prefer a hash map (`O(1)` lookup) over linear scan (`O(n)`) for repeated membership tests.
3. Use a binary search (`O(log n)`) on sorted data instead of linear scan.
4. Sort data once (`O(n log n)`) to enable fast repeated queries rather than re-scanning.
5. Use a prefix sum array to answer range sum queries in `O(1)` after `O(n)` preprocessing.
6. Use a sliding window for substring/subarray problems with a fixed or variable window.
7. Use two-pointer technique for sorted array problems involving pairs/triplets.
8. Use monotonic stack/queue for problems involving "next greater/smaller element".
9. Use a priority queue (min-heap or max-heap) for top-K and streaming median problems.
10. Use Dijkstra's algorithm for single-source shortest paths on non-negative weights.
11. Use Bellman-Ford when edges can have negative weights.
12. Use Floyd-Warshall for all-pairs shortest paths on dense graphs.
13. Use BFS for unweighted shortest paths; use DFS for reachability and cycle detection.
14. Use topological sort (Kahn's or DFS-based) for dependency ordering.
15. Use Union-Find (Disjoint Set Union) for connected components and MST (Kruskal's).
16. Use Kruskal's or Prim's for Minimum Spanning Trees.
17. Use dynamic programming when the problem has optimal substructure + overlapping subproblems.
18. Always define DP state, transition, base case, and answer extraction before coding.
19. Use memoization (top-down) when recursion is more natural than iteration.
20. Use tabulation (bottom-up) to avoid recursion stack overflow on deep problems.
21. Use space optimization in DP when only the previous row/column is needed.
22. Use binary indexed tree (Fenwick tree) for prefix sums with point updates in `O(log n)`.
23. Use a segment tree for range queries with range updates in `O(log n)`.
24. Use a trie for prefix-search, autocomplete, and IP routing table lookups.
25. Use a suffix array + LCP array for repeated substring and longest common substring.
26. Use KMP or Z-algorithm for linear-time string pattern matching.
27. Use Rabin-Karp rolling hash for multi-pattern substring search.
28. Use Aho-Corasick for simultaneous multi-pattern string matching.
29. Use LRU cache (doubly-linked list + hash map) for O(1) get and put.
30. Use a circular buffer (ring buffer) for fixed-size FIFO queues without dynamic allocation.
31. Use skip lists as an alternative to balanced BSTs for ordered sets.
32. Use a B-tree or B+-tree mental model when reasoning about disk-based data structures.
33. Use a Bloom filter for probabilistic membership testing with no false negatives.
34. Use count-min sketch for approximate frequency counting in streaming data.
35. Use HyperLogLog for approximate distinct element counting.
36. Use consistent hashing for distributing keys across dynamic sets of nodes.
37. Use reservoir sampling for uniform random sampling from a stream of unknown length.
38. Use Fisher-Yates shuffle for uniform random permutation of an array.
39. Use reservoir sampling or weighted random sampling for probability-weighted selection.
40. Use binary exponentiation to compute `a^b mod m` in `O(log b)`.
41. Use the extended Euclidean algorithm for modular inverses.
42. Use the Chinese Remainder Theorem for simultaneous congruences.
43. Use Sieve of Eratosthenes for prime generation up to N in `O(N log log N)`.
44. Use bit manipulation to check power-of-two, set/clear bits, and count set bits efficiently.
45. Use XOR tricks for finding the single non-repeated element, swapping without temp, etc.
46. Use SIMD mental model when reasoning about vectorized operations.
47. Recognize backtracking patterns: choose, explore, unchoose.
48. Use branch-and-bound pruning to eliminate search tree branches early.
49. Use greedy algorithms only after proving the greedy choice property holds.
50. Always prove or disprove greedy correctness with an exchange argument.
51. Recognize interval scheduling problems and use earliest-finish-time greedy.
52. Use Huffman coding for optimal prefix-free variable-length encoding.
53. Apply amortized analysis for data structures with occasional expensive operations.
54. Use lazy propagation in segment trees to defer bulk updates.
55. Use coordinate compression before applying segment tree/BIT on large value ranges.
56. Use offline algorithms (sorting queries) to answer range queries more efficiently.
57. Use Mo's algorithm for offline range queries in `O((N+Q) sqrt(N))`.
58. Use the two-coloring / bipartiteness check to detect odd-cycle-free graphs.
59. Use Tarjan's SCC or Kosaraju's for strongly connected components.
60. Use Euler circuit/path (Hierholzer's) for problems requiring traversal of all edges.
61. Use the max-flow / min-cut theorem for capacity and matching problems.
62. Use Hopcroft-Karp for maximum bipartite matching in `O(E sqrt(V))`.
63. Use Hungarian algorithm for minimum-cost bipartite matching.
64. Use stable matching (Gale-Shapley) for stable assignment problems.
65. Use A* search with an admissible heuristic for guided shortest-path search.
66. Use iterative deepening DFS (IDDFS) when memory is constrained but BFS's completeness is needed.
67. Use alpha-beta pruning to reduce minimax search space in game trees.
68. Analyze cache performance — prefer data structures with good spatial locality.
69. Use memory pools (arenas) to reduce allocation overhead in tight loops.
70. Prefer contiguous arrays over linked lists for cache-friendly traversal.
71. Profile before choosing a data structure — theoretical complexity and practical performance often diverge.
72. Use `math/rand` with a fixed seed for reproducible randomized tests.
73. Use fuzzing to discover algorithmic edge cases automatically.
74. Document the invariants your data structure maintains — write them as assertions.
75. Test edge cases: empty input, single element, all-same elements, sorted/reverse-sorted input.

---

## 4. Python Mastery

> **75 skills** for writing idiomatic, robust, and performant Python.

1. Use Python 3.10+ features: structural pattern matching (`match`/`case`), `X | Y` union types.
2. Annotate all public functions and methods with type hints using `typing` or built-in generics.
3. Use `from __future__ import annotations` for deferred evaluation of annotations in 3.9-.
4. Use `dataclasses.dataclass` for plain data-holding classes; add `frozen=True` for immutability.
5. Use `attrs` or `pydantic` when you need validators, converters, or JSON serialization.
6. Use `pydantic.BaseModel` for strict input validation at API boundaries.
7. Use `TypedDict` for dictionaries with a fixed, known schema.
8. Use `Protocol` for structural subtyping — prefer over ABCs for duck typing.
9. Use `Final` for constants that must never be reassigned.
10. Use `Literal` types to constrain string/int parameters to specific values.
11. Use `overload` to declare multiple type signatures for the same function.
12. Use `NamedTuple` instead of plain tuples for structured return values.
13. Use `contextlib.contextmanager` to build context managers from generator functions.
14. Use `contextlib.suppress(ExceptionType)` instead of bare `try/except/pass`.
15. Use `contextlib.ExitStack` to dynamically compose context managers.
16. Use generators and `yield` for memory-efficient lazy sequences.
17. Use `yield from` to delegate to sub-generators cleanly.
18. Use `itertools` (`chain`, `islice`, `groupby`, `product`, `combinations`, `permutations`) exhaustively before writing loops.
19. Use `functools.lru_cache` or `functools.cache` for memoization of pure functions.
20. Use `functools.partial` to pre-fill arguments of functions.
21. Use `functools.reduce` for fold/accumulate operations on sequences.
22. Use `operator` module functions (`operator.attrgetter`, `operator.itemgetter`) for key functions.
23. Use `collections.Counter` for frequency counting.
24. Use `collections.defaultdict` to avoid `KeyError` on missing keys.
25. Use `collections.deque` for O(1) append/pop from both ends.
26. Use `collections.OrderedDict` when insertion order matters in Python < 3.7.
27. Use `heapq` for priority queue operations.
28. Use `bisect` for binary search and sorted-list insertion.
29. Use list comprehensions and generator expressions instead of `map`/`filter` with lambdas.
30. Use dictionary comprehensions for concise dict construction.
31. Use set comprehensions for membership-test-heavy operations.
32. Use walrus operator (`:=`) to assign and test in the same expression where it reduces repetition.
33. Avoid mutable default arguments — use `None` and assign inside the function.
34. Use `*args` and `**kwargs` only when the variadic nature is genuinely needed.
35. Use keyword-only arguments (`def f(*, key)`) to enforce explicit call sites.
36. Use positional-only arguments (`def f(x, /)`) to allow renaming params without breaking callers.
37. Use `__slots__` in classes with many instances to reduce per-object memory overhead.
38. Use `__repr__` for unambiguous developer-facing representations; `__str__` for user-facing.
39. Use `__eq__` and `__hash__` together — hashable objects must be consistently equal.
40. Use `__enter__`/`__exit__` for resource management in context managers.
41. Use `abc.ABC` + `@abstractmethod` to enforce interface contracts.
42. Use `property` for computed attributes that should look like attribute access.
43. Use `classmethod` for alternative constructors; `staticmethod` for utility functions.
44. Use `__init_subclass__` for enforcing constraints on subclasses.
45. Use `asyncio` for I/O-bound concurrency; use `multiprocessing` for CPU-bound work.
46. Use `async with` and `async for` for async context managers and async iterables.
47. Use `asyncio.gather` to run multiple coroutines concurrently.
48. Use `asyncio.create_task` to schedule coroutines without awaiting immediately.
49. Use `asyncio.Queue` for async producer-consumer patterns.
50. Use `aiohttp` for async HTTP; `httpx` for both sync and async with HTTP/2 support.
51. Use `uvicorn` + `fastapi` for high-performance async web services.
52. Use `pytest` with fixtures for all tests — avoid `unittest.TestCase` in new code.
53. Use `pytest.mark.parametrize` for table-driven tests.
54. Use `pytest.raises` context manager for exception testing.
55. Use `unittest.mock.patch` and `MagicMock` for dependency injection in tests.
56. Use `hypothesis` for property-based testing — find edge cases automatically.
57. Use `coverage.py` to measure test coverage; aim for >85% on critical paths.
58. Use `black` for deterministic formatting; `isort` for import sorting.
59. Use `ruff` as a fast all-in-one linter replacing `flake8`/`pylint`/`isort`.
60. Use `mypy --strict` for thorough static type checking.
61. Use `pyright` for even stricter type inference in VSCode/Cursor.
62. Use virtual environments (`python -m venv .venv`) for every project.
63. Use `pip-tools` (`pip-compile`) or `poetry` for deterministic dependency locking.
64. Use `pyproject.toml` as the single source of project metadata and tool configuration.
65. Use `logging` module with structured JSON output instead of `print`.
66. Configure logging with `logging.config.dictConfig` or `structlog`.
67. Use `pathlib.Path` instead of `os.path` for all file system operations.
68. Use `tempfile.TemporaryDirectory` and `tempfile.NamedTemporaryFile` for safe temp files.
69. Use `subprocess.run(check=True, capture_output=True, text=True)` for shell commands.
80. Use `shlex.split` to safely split shell command strings into argument lists.
71. Use `json.dumps(indent=2)` for human-readable JSON output.
72. Use `orjson` or `ujson` for high-performance JSON serialization in hot paths.
73. Use `tomllib` (3.11+) or `tomli` for reading TOML configuration files.
74. Use `click` or `typer` for building CLI applications with type-safe argument parsing.
75. Profile with `cProfile` + `snakeviz` or `py-spy` before making any performance optimization.

---

## 5. JavaScript & TypeScript

> **75 skills** for modern, type-safe, high-quality JS/TS development.

1. Use TypeScript strict mode (`"strict": true`) in all new projects — no exceptions.
2. Enable `noUncheckedIndexedAccess` to catch array/object access that may be `undefined`.
3. Enable `exactOptionalPropertyTypes` to distinguish between `undefined` and missing keys.
4. Use `satisfies` operator (TS 4.9+) to type-check without widening the inferred type.
5. Use `const` by default; `let` only when reassignment is necessary; never `var`.
6. Prefer named exports over default exports for better refactoring support.
7. Use ES modules (`import`/`export`) — never CommonJS `require()` in new TypeScript code.
8. Use `import type` for type-only imports to improve tree-shaking and compilation speed.
9. Use discriminated unions (`type Result = { ok: true; value: T } | { ok: false; error: Error }`) for typed error handling.
10. Use `unknown` instead of `any` for values of uncertain type — force explicit narrowing.
11. Use `never` for exhaustive checks in switch statements over discriminated unions.
12. Use template literal types for strongly-typed string manipulation (`type EventName = `on${Capitalize<string>}``).
13. Use `as const` on literal arrays and objects to preserve literal types.
14. Use mapped types (`{ [K in keyof T]: ... }`) for type transformations.
15. Use conditional types (`T extends U ? X : Y`) for type-level logic.
16. Use `infer` to extract sub-types from conditional types.
17. Use `ReturnType<typeof f>`, `Parameters<typeof f>`, and `InstanceType<typeof C>` utilities.
18. Use `Awaited<T>` to unwrap the resolved type of a Promise.
19. Use `Readonly<T>` and `ReadonlyArray<T>` for immutable data.
20. Use `Partial<T>`, `Required<T>`, `Pick<T, K>`, `Omit<T, K>` to transform types.
21. Use `Record<K, V>` instead of `{ [key: string]: V }` for explicit key type.
22. Use branded types (`type UserId = string & { readonly __brand: 'UserId' }`) to prevent mixing domain IDs.
23. Use `zod` for runtime validation that mirrors your TypeScript types.
24. Use `valibot` as a lighter-weight alternative to `zod` when bundle size matters.
25. Use optional chaining (`?.`) and nullish coalescing (`??`) instead of manual null checks.
26. Use nullish coalescing assignment (`??=`) for lazy initialization.
27. Use logical assignment operators (`&&=`, `||=`) for conditional assignment.
28. Use `Array.from({ length: n }, (_, i) => i)` to create ranges.
29. Use `structuredClone` for deep cloning plain objects (available in Node 17+/browsers).
30. Use `Object.freeze` at the top level for runtime immutability enforcement.
31. Use `Object.entries`, `Object.keys`, `Object.values` for safe iteration over objects.
32. Use `Map` and `Set` instead of plain objects when keys are non-strings or order matters.
33. Use `WeakMap` and `WeakRef` for caches that should not prevent garbage collection.
34. Use `Symbol` for unique property keys that should not clash with strings.
35. Use `Proxy` for metaprogramming — intercepting get/set/has/apply operations.
36. Use `Reflect` API when forwarding operations in Proxy traps.
37. Use `async`/`await` for all asynchronous code — avoid raw `.then().catch()` chains.
38. Use `Promise.all` for independent concurrent promises.
39. Use `Promise.allSettled` when you need results even if some promises reject.
40. Use `Promise.race` for timeout patterns; `Promise.any` for first-success patterns.
41. Use `AbortController` and `AbortSignal` for cancellable async operations.
42. Use `ReadableStream` / `WritableStream` for streaming data processing.
43. Use `EventEmitter` (Node) or `EventTarget` (browser) for event-driven architectures.
44. Use `Worker` threads (Node `worker_threads`) for CPU-bound work in Node.js.
45. Use `Atomics` and `SharedArrayBuffer` for lock-based inter-thread communication.
46. Prefer `fetch` over `axios`/`got` in environments with native fetch (Node 18+/browsers).
47. Use `node:` prefix for Node.js built-ins (`import fs from 'node:fs'`) to avoid ambiguity.
48. Use `tsx` or `ts-node` for running TypeScript files without a build step in development.
49. Use `esbuild` or `tsup` for fast TypeScript bundling.
50. Use `vite` for frontend dev server with hot module replacement.
51. Use `vitest` for fast unit testing in Vite projects.
52. Use `jest` with `ts-jest` for TypeScript testing in non-Vite projects.
53. Use `@testing-library/react` for testing React components by user interaction.
54. Use `MSW` (Mock Service Worker) to mock HTTP requests in tests.
55. Use `Playwright` or `Cypress` for end-to-end browser testing.
56. Use `ESLint` with `typescript-eslint` for linting TypeScript.
57. Use `prettier` for consistent code formatting — integrate into pre-commit hooks.
58. Use `lint-staged` + `husky` to run linters only on staged files.
59. Use `semantic-release` for automated versioning and changelog generation.
60. Use `npm workspaces` or `pnpm` workspaces for monorepo management.
61. Use `pnpm` over `npm` for faster installs and disk-efficient node_modules.
62. Lock dependency versions with `package-lock.json` or `pnpm-lock.yaml` — always commit it.
63. Use `depcheck` to find unused dependencies.
64. Use `bundlephobia` to check the bundle cost before adding a dependency.
65. Use `source-map-explorer` or `vite-bundle-visualizer` to inspect bundle composition.
66. Use `compression` and `Content-Encoding: gzip/br` for serving static assets.
67. Use `crypto.subtle` (Web Crypto API) for cryptographic operations in browsers.
68. Use `node:crypto` for cryptographic operations in Node.js.
69. Sanitize all HTML rendered from user input using `DOMPurify`.
70. Use Content Security Policy (CSP) headers to mitigate XSS.
71. Use `Intl` API (`Intl.DateTimeFormat`, `Intl.NumberFormat`, `Intl.RelativeTimeFormat`) for i18n.
72. Use `performance.mark` and `performance.measure` for fine-grained timing in browsers.
73. Use `console.time`/`console.timeEnd` for quick timing in Node.js scripts.
74. Use `node --inspect` and Chrome DevTools for Node.js debugging with breakpoints.
75. Use `tsx watch` or `nodemon` for automatic restarts during development.

---

## 6. Go Development

> **75 skills** for idiomatic, production-quality Go code.

1. Follow `gofmt` formatting exactly — never argue about style, let the tool decide.
2. Use `goimports` over `gofmt` to also automatically manage import groups.
3. Run `golangci-lint run` with a `.golangci.yml` config before every commit.
4. Use `go vet ./...` as a fast first-pass for common bugs.
5. Use `staticcheck` for advanced static analysis beyond `go vet`.
6. Structure packages by domain concept, not by layer (`user`, `payment`, not `models`, `controllers`).
7. Keep package names short, lowercase, singular, and noun-like.
8. Never use `init()` for logic — only for registering side effects like drivers.
9. Use `internal/` to prevent packages from being imported outside the module.
10. Export types and functions only when they form part of the public API.
11. Define interfaces close to where they are consumed, not where they are implemented.
12. Keep interfaces small — the best Go interfaces have 1-3 methods.
13. Use `io.Reader`, `io.Writer`, `io.Closer` for all I/O abstractions.
14. Use `context.Context` as the first parameter in every function that does I/O or blocking.
15. Never store contexts in structs — always pass them as function arguments.
16. Use `context.WithTimeout` or `context.WithDeadline` for all external calls.
17. Use `context.WithCancel` for cooperative cancellation.
18. Use `context.WithValue` only for request-scoped metadata, never for optional function inputs.
19. Always check `ctx.Err()` after blocking operations in loops.
20. Return errors instead of panicking — panic only for truly unrecoverable states.
21. Use `fmt.Errorf("operation: %w", err)` to wrap errors with context.
22. Use `errors.Is` and `errors.As` for unwrapping error chains.
23. Define sentinel errors as `var ErrNotFound = errors.New("not found")` at package level.
24. Define typed errors as structs when callers need to inspect error fields.
25. Use `defer` for cleanup — always close resources immediately after opening them.
26. Use `defer` with a closure when you need to capture return values for cleanup.
27. Use `sync.WaitGroup` to wait for a fixed set of goroutines.
28. Use `sync.Mutex` for protecting shared state; `sync.RWMutex` when reads dominate.
29. Use `sync.Once` for lazy initialization that must run exactly once.
30. Use `sync.Pool` for reusing allocated objects in high-throughput paths.
31. Use `sync.Map` only when many goroutines read different keys — profile before using it.
32. Use `atomic` operations for lock-free counters and flags.
33. Use channels for communication; use mutexes for protecting state — know the difference.
34. Use unbuffered channels for synchronization; buffered channels for decoupling producer/consumer.
35. Use `select` with a `default` case for non-blocking channel operations.
36. Use `select` with `ctx.Done()` to cancel blocking operations gracefully.
37. Always send the goroutine count to a bounded semaphore channel to limit concurrency.
38. Use `errgroup.Group` from `golang.org/x/sync/errgroup` for concurrent error handling.
39. Prefer `goroutine` + channel patterns over callbacks for async code.
40. Use `time.After` only in `select` — it leaks if not selected; use `time.NewTimer` otherwise.
41. Use `time.NewTicker` for repeating intervals; stop it with `ticker.Stop()`.
42. Use `testing.T.Helper()` in test helper functions to improve error reporting.
43. Use `testing.T.Cleanup()` instead of `defer` in tests for post-test cleanup.
44. Use `testing.T.Parallel()` in subtests for faster test execution.
45. Use table-driven tests with `t.Run(name, func)` for comprehensive coverage.
46. Use `testify/assert` and `testify/require` for readable test assertions.
47. Use `testify/mock` for interface mocking in unit tests.
48. Use `httptest.NewRecorder()` and `httptest.NewServer()` for HTTP handler testing.
49. Use `goleak` to detect goroutine leaks in tests.
50. Use benchmarks (`func BenchmarkX(b *testing.B)`) to measure performance.
51. Use `pprof` to profile CPU and memory in production and benchmarks.
52. Use `go build -race ./...` to detect data races during testing.
53. Use `go test -count=100` to surface flaky tests.
54. Use `go generate` for code generation — always commit generated code.
55. Use `cobra` for building CLI applications with subcommands.
56. Use `viper` for configuration management with env var and flag integration.
57. Use `zerolog` or `slog` (1.21+) for structured, leveled logging.
58. Use `slog.With` to add fields to a logger without allocating each time.
59. Use `encoding/json` with struct tags for JSON marshaling/unmarshaling.
60. Use `omitempty` tag to exclude zero-value fields from JSON output.
61. Implement `json.Marshaler`/`json.Unmarshaler` for types with non-standard encoding.
62. Use `database/sql` with `sqlx` for relational database access.
63. Use prepared statements to prevent SQL injection.
64. Use `pgx` directly for PostgreSQL-specific features (LISTEN/NOTIFY, COPY, etc.).
65. Use `gorm` only for rapid prototyping — prefer raw SQL in production.
66. Use `net/http` stdlib for HTTP servers — it is production-ready.
67. Use `gorilla/mux` or `chi` for advanced HTTP routing.
68. Use `grpc-go` for gRPC services with protobuf.
69. Use `buf` for managing protobuf schemas and generating code.
70. Use `embed.FS` to embed static files, templates, and migrations at compile time.
71. Use `text/template` and `html/template` (which auto-escapes HTML) appropriately.
72. Use build tags (`//go:build linux`) for platform-specific code.
73. Use `cgo` sparingly — it breaks cross-compilation and increases complexity.
74. Cross-compile with `GOOS=linux GOARCH=amd64 go build` for target platforms.
75. Use `ldflags="-X main.version=$(git describe --tags)"` to embed version info at build time.

---

## 7. Rust Systems Programming

> **75 skills** for safe, performant, and idiomatic Rust.

1. Always run `cargo fmt` and `cargo clippy -- -D warnings` before committing.
2. Use `cargo check` for fast compilation feedback without generating binaries.
3. Use `cargo test` with `--release` for benchmarks and `--nocapture` for verbose output.
4. Use the ownership system as design — design APIs that express ownership intent clearly.
5. Prefer borrowing (`&T`, `&mut T`) over cloning or moving when lifetimes allow.
6. Use `Clone` explicitly — never derive it blindly on large structs.
7. Use `Copy` only for types that are semantically cheap to copy (primitives, small structs).
8. Use `Cow<'_, str>` for functions that sometimes need to own and sometimes borrow strings.
9. Use `Arc<T>` for shared ownership across threads; `Rc<T>` for single-threaded shared ownership.
10. Use `Mutex<T>` or `RwLock<T>` to protect shared mutable state.
11. Use `AtomicUsize`/`AtomicBool` for lock-free counters and flags.
12. Use `Mutex::lock().unwrap()` only in tests — handle poisoning in production code.
13. Use `parking_lot` crate for faster, non-poisoning mutexes and rwlocks.
14. Use `tokio` for async I/O; use `rayon` for data parallelism.
15. Use `tokio::spawn` for independent tasks; `tokio::join!` for concurrent awaiting.
16. Use `tokio::select!` for racing multiple futures.
17. Use `tokio::sync::mpsc` for async message passing; `std::sync::mpsc` for sync.
18. Use `tokio::sync::Semaphore` to limit concurrency.
19. Use `anyhow::Result` for application error handling with context.
20. Use `thiserror::Error` for library error types with derive macros.
21. Never use `unwrap()` in library code — always propagate errors with `?`.
22. Use `?` operator to propagate errors; use `map_err` to convert error types.
23. Use `Option::ok_or` or `Option::ok_or_else` to convert `Option` to `Result`.
24. Use `Result::and_then` and `Result::map` for chaining fallible computations.
25. Use `Iterator` combinators (`map`, `filter`, `flat_map`, `fold`, `collect`) instead of for-loops.
26. Use `collect::<Vec<Result<T, E>>>()` then `into_iter().collect::<Result<Vec<T>, E>>()` to gather results.
27. Use `impl Trait` in function signatures to avoid naming concrete iterator types.
28. Use `dyn Trait` for trait objects when dynamic dispatch is intentional.
29. Use `Box<dyn Error>` for simple error boxing in application code.
30. Derive `Debug` on all public types; `Display` on error types.
31. Use `#[must_use]` on functions returning `Result` or `Option` to catch ignored errors.
32. Use `#[derive(Default)]` and implement `Default` explicitly only when the default is non-obvious.
33. Use `builder` pattern (with `derive_builder` or manual) for structs with many optional fields.
34. Use `serde::{Serialize, Deserialize}` for all data types that cross serialization boundaries.
35. Use `serde_json`, `serde_yaml`, or `toml` crates for format-specific serialization.
36. Use `#[serde(rename_all = "camelCase")]` for JSON field naming conventions.
37. Use `#[serde(skip_serializing_if = "Option::is_none")]` to exclude None fields.
38. Use `reqwest` for async HTTP client; `ureq` for sync HTTP client.
39. Use `axum` or `actix-web` for web services — prefer `axum` for tower ecosystem integration.
40. Use `sqlx` for compile-time checked SQL queries with async support.
41. Use `diesel` for ORM-style database access with strong type safety.
42. Use `redis` crate for Redis access; `mongodb` for MongoDB.
43. Use `clap` with derive macros for CLI argument parsing.
44. Use `tracing` for structured, async-aware logging; `tracing-subscriber` for output.
45. Use `metrics` crate with `metrics-exporter-prometheus` for Prometheus metrics.
46. Use `criterion` for statistical benchmarking.
47. Use `proptest` or `quickcheck` for property-based testing.
48. Use `cargo-fuzz` with `libFuzzer` for fuzzing.
49. Use `cargo-audit` to check for security vulnerabilities in dependencies.
50. Use `cargo-deny` to enforce dependency policies (licenses, duplicates, advisories).
51. Use `cargo-expand` to inspect macro expansions.
52. Use `cargo-flamegraph` for CPU profiling with flamegraph visualization.
53. Use MIRI for detecting undefined behavior in unsafe code.
54. Minimize `unsafe` blocks — document the safety invariant in every `unsafe` block.
55. Use `#[cfg(test)]` to include test-only code without affecting production builds.
56. Use `mockall` for automocking traits in unit tests.
57. Use `wiremock` for HTTP mocking in integration tests.
58. Write `#[tokio::test]` for async test functions.
59. Use `tempfile` crate for temporary files/directories in tests.
60. Use `once_cell::sync::Lazy` or `std::sync::OnceLock` (1.70+) for lazy static initialization.
61. Use `dashmap` for concurrent hash maps without locking the whole map.
62. Use `bytes::Bytes` for zero-copy byte buffer sharing.
63. Use `memmap2` for memory-mapped file I/O.
64. Use `crossbeam` channels for high-performance multi-producer multi-consumer messaging.
65. Use `flume` as a faster alternative to `std::sync::mpsc`.
66. Use `indexmap` for insertion-ordered hash maps.
67. Use `smallvec` for vectors that are usually small to avoid heap allocation.
68. Use `tinyvec` or `arrayvec` for stack-allocated fixed-capacity vectors.
69. Understand fat pointers — `&dyn Trait` is (data ptr, vtable ptr), `&[T]` is (data ptr, length).
70. Use `PhantomData<T>` to express lifetime or type parameter ownership without storing T.
71. Use newtype pattern (`struct Meters(f64)`) to prevent unit confusion in domain types.
72. Use const generics for compile-time array sizes and type-level integers.
73. Use `proc_macro` crates (`darling`, `syn`, `quote`) for writing derive macros.
74. Profile with `perf` + `cargo-flamegraph` before any optimization.
75. Read the Rustonomicon before writing any `unsafe` code — no exceptions.

---

## 8. Database & SQL

> **75 skills** for reliable, performant, and maintainable database work.

1. Always use parameterized queries — never string-concatenate user input into SQL.
2. Use `EXPLAIN ANALYZE` (PostgreSQL) or `EXPLAIN FORMAT=JSON` (MySQL) on every slow query.
3. Index foreign key columns — they are almost always used in JOINs and are rarely auto-indexed.
4. Use partial indexes to index only the rows you actually query (`CREATE INDEX ... WHERE active = true`).
5. Use covering indexes (include extra columns) to avoid table heap fetches.
6. Use composite indexes in the correct column order: most selective first, then equality, then range.
7. Understand B-tree vs. hash vs. GiST vs. GIN index types and use the right one for each query.
8. Use `pg_stat_user_indexes` to find unused indexes and drop them — they slow down writes.
9. Use `pg_stat_user_tables` to find tables with many sequential scans that need indexes.
10. Use `autovacuum` tuning and manual `VACUUM ANALYZE` after bulk operations.
11. Use connection pooling (PgBouncer, HikariCP, `pgx` pool) — never open a new connection per request.
12. Use `COPY` (PostgreSQL) or `LOAD DATA INFILE` (MySQL) for bulk inserts — orders of magnitude faster.
13. Use `INSERT ... ON CONFLICT DO UPDATE` (upsert) instead of SELECT-then-INSERT patterns.
14. Use `RETURNING` clause to get inserted/updated rows without a second SELECT.
15. Use CTEs (`WITH` expressions) for readable multi-step queries.
16. Use `LATERAL JOIN` for correlated subqueries that reference the outer row.
17. Use window functions (`ROW_NUMBER`, `RANK`, `LEAD`, `LAG`, `SUM OVER`) for analytical queries.
18. Use `FILTER (WHERE ...)` with aggregate functions for conditional aggregation.
19. Use `DISTINCT ON (column)` (PostgreSQL) for "first per group" queries.
20. Use `NULLS FIRST`/`NULLS LAST` in `ORDER BY` to control null ordering explicitly.
21. Use `COALESCE` for null-safe expressions; `NULLIF` to convert values to NULL.
22. Use `CASE WHEN ... THEN ... ELSE ... END` for conditional expressions.
23. Use `generate_series` for date ranges and sequence generation in PostgreSQL.
24. Use `date_trunc` for time-bucketing in time-series queries.
25. Use `tsrange`, `daterange` for range queries with overlap operators (`&&`).
26. Use `JSONB` in PostgreSQL for semi-structured data with indexable JSON operators.
27. Use `GIN` indexes on `JSONB` columns for fast JSON key/value searches.
28. Use `ARRAY` types with `&&`, `@>`, `<@` operators for array containment queries.
29. Use `uuid-ossp` or `gen_random_uuid()` for UUID primary keys.
30. Use `BIGSERIAL` or `IDENTITY` for auto-incrementing integer PKs when UUIDs are too large.
31. Use `ULID` as an ordered, URL-safe alternative to UUID.
32. Always include `created_at` and `updated_at` timestamps on every table.
33. Use `updated_at = now()` triggers for automatic timestamp updates.
34. Use `soft delete` (`deleted_at IS NULL`) only when audit trails require it — add partial indexes.
35. Use transactions for any operation involving multiple table mutations.
36. Use `BEGIN ... COMMIT` with explicit rollback on error in application code.
37. Set `ISOLATION LEVEL SERIALIZABLE` only when phantom reads would cause correctness bugs.
38. Use `SELECT ... FOR UPDATE` to lock rows before modifying them.
39. Use `SELECT ... FOR UPDATE SKIP LOCKED` for job queue implementations.
40. Use `advisory locks` for distributed locking without a dedicated lock service.
41. Design migrations to be backward-compatible — deploy code before running migrations.
42. Use a migration tool (`Flyway`, `golang-migrate`, `Alembic`) — never apply raw SQL manually.
43. Test rollback scripts before deploying — every migration must be reversible.
44. Use `CONCURRENTLY` for index creation to avoid locking tables in production.
45. Use `ALTER TABLE ... ADD COLUMN` with a `DEFAULT` — PostgreSQL 11+ does this without a table rewrite.
46. Use `CHECK` constraints to enforce domain rules at the database level.
47. Use `NOT NULL` constraints on every column that should never be null.
48. Use `UNIQUE` constraints instead of application-level uniqueness checks.
49. Use `FOREIGN KEY` constraints with appropriate `ON DELETE` behavior.
50. Use `DEFERRABLE INITIALLY DEFERRED` foreign keys for circular references.
51. Normalize to at least 3NF for transactional data; denormalize for reporting with care.
52. Use materialized views for expensive aggregations that can tolerate staleness.
53. Use read replicas for read-heavy reporting queries — never run OLAP on OLTP primaries.
54. Use logical replication for zero-downtime blue/green database migrations.
55. Enable `pg_stat_statements` to track query execution statistics.
56. Use `pg_locks` and `pg_activity` to diagnose deadlocks and long-running queries.
57. Set `lock_timeout` and `statement_timeout` on application connections.
58. Use `idle_in_transaction_session_timeout` to kill abandoned transactions.
59. Understand WAL (Write-Ahead Log) — it is the foundation of replication, PITR, and durability.
60. Use PITR (Point-In-Time Recovery) — test your backup restore process monthly.
61. Use Redis for caching, session storage, rate limiting, and pub/sub.
62. Use Redis `SETNX` (set-if-not-exists) for distributed locks.
63. Use Redis `EXPIRE` for TTL-based cache eviction.
64. Use Redis pipelines and transactions (`MULTI`/`EXEC`) to batch operations.
65. Use Redis Streams for durable, consumer-group-based message queues.
66. Use MongoDB for document-oriented data with flexible schema.
67. Use `$lookup` (aggregation) sparingly — denormalize more in MongoDB.
68. Use Cassandra for time-series and write-heavy workloads at scale.
69. Design Cassandra tables based on access patterns — not normalized form.
70. Use ClickHouse for column-store OLAP queries over billions of rows.
71. Use DuckDB for in-process OLAP on files (Parquet, CSV, JSON).
72. Use `EXPLAIN` output to verify index usage before deploying to production.
73. Run `pg_bench` or sysbench to load-test database changes.
74. Document every non-obvious index rationale with a migration comment.
75. Store connection strings in environment variables — never in code or version control.

---

## 9. API Design & REST/GraphQL

> **75 skills** for building correct, usable, and evolvable APIs.

1. Use resource-oriented URLs (`/users/{id}/orders`) — never use verbs in REST paths.
2. Use HTTP methods semantically: `GET` (read), `POST` (create), `PUT` (replace), `PATCH` (update), `DELETE` (remove).
3. Return `201 Created` with a `Location` header on successful resource creation.
4. Return `204 No Content` for successful deletions or updates with no body.
5. Return `200 OK` with a body for successful reads and updates that return data.
6. Return `400 Bad Request` for client-side validation errors with a structured error body.
7. Return `401 Unauthorized` when authentication is missing or invalid.
8. Return `403 Forbidden` when the authenticated user lacks permission.
9. Return `404 Not Found` when a resource does not exist.
10. Return `409 Conflict` for state conflicts (duplicate resource, optimistic lock failure).
11. Return `422 Unprocessable Entity` for semantically invalid input.
12. Return `429 Too Many Requests` with `Retry-After` header for rate-limited responses.
13. Return `500 Internal Server Error` for unexpected server failures — never expose stack traces.
14. Use a consistent error response body: `{ "error": { "code": "...", "message": "...", "details": [...] } }`.
15. Use `application/json` content type for all JSON APIs — always include `charset=utf-8`.
16. Use `Content-Negotiation` (`Accept` header) to support multiple response formats.
17. Support `ETag` and `Last-Modified` for conditional requests (`If-None-Match`, `If-Modified-Since`).
18. Use `Cache-Control` headers to control downstream caching behavior.
19. Use `Idempotency-Key` header for non-idempotent operations (payments, emails).
20. Use cursor-based pagination instead of offset pagination for large, frequently-updated datasets.
21. Use `Link` header with `rel=next/prev/first/last` for pagination metadata.
22. Use query parameters for filtering, sorting, and pagination — not request bodies.
23. Support `fields` parameter for sparse fieldsets to reduce payload size.
24. Use `expand` or `include` parameter to allow clients to embed related resources.
25. Version APIs in the URL path (`/v1/`) or via `Accept` header versioning.
26. Never remove fields from responses — add new fields; mark old ones deprecated.
27. Deprecate endpoints with `Deprecation` and `Sunset` response headers.
28. Use OpenAPI 3.x (Swagger) to document every endpoint, parameter, and response.
29. Generate server stubs and client SDKs from OpenAPI specs for consistency.
30. Validate all request bodies against the OpenAPI schema before processing.
31. Use `x-` extensions in OpenAPI for custom metadata (rate limits, permissions, etc.).
32. Use `oneOf`, `anyOf`, `allOf`, `not` in JSON Schema to model polymorphic request/response bodies.
33. Use `readOnly` and `writeOnly` properties in OpenAPI schemas to distinguish input/output fields.
34. Always return arrays within an object envelope (`{ "data": [...], "meta": {} }`) — never bare arrays.
35. Use HATEOAS links sparingly — only if clients will programmatically discover actions.
36. Use JSON:API specification when you need a standardized hypermedia format.
37. Use gRPC for internal service-to-service APIs for performance and strong typing.
38. Use Protocol Buffers v3 for all gRPC services — use `proto3` optional for nullable fields.
39. Use `google.protobuf.Timestamp` for timestamps in protobufs.
40. Use `google.protobuf.FieldMask` for partial updates in gRPC APIs.
41. Design gRPC streaming thoughtfully — use server streaming for subscriptions, bidi for chat-like APIs.
42. Use GraphQL for APIs consumed by multiple clients with different data requirements.
43. Use `DataLoader` to batch and cache GraphQL field resolver database calls.
44. Use persisted queries for GraphQL to reduce bandwidth and enable caching.
45. Always implement query depth limiting and complexity analysis for public GraphQL APIs.
46. Use schema-first GraphQL design (`schema.graphql` → generate resolvers).
47. Use `__typename` in GraphQL fragment matching for polymorphic responses.
48. Use GraphQL subscriptions (over WebSockets) for real-time data.
49. Document all GraphQL types and fields with description strings in the schema.
50. Use `@deprecated` directive with a `reason` for soft-deprecated GraphQL fields.
51. Use `@auth` or `@hasRole` directives for field-level authorization in GraphQL.
52. Use JSON Web Tokens (JWT) for stateless authentication — always verify signature.
53. Store JWTs in `HttpOnly` cookies for browser clients — not in `localStorage`.
54. Use short JWT expiry (15 min) + refresh tokens for balance of security and UX.
55. Use OAuth 2.0 + PKCE for third-party authorization — never implement custom auth flows.
56. Use `Authorization: Bearer <token>` header for token-based auth in REST APIs.
57. Implement rate limiting at the API gateway level — not in application code.
58. Use exponential backoff with jitter for client-side retry logic.
59. Return `Retry-After` in seconds (not date) for rate-limited and 503 responses.
60. Implement circuit breakers (half-open, open, closed) for calling downstream services.
61. Use health check endpoints (`/health`, `/ready`, `/live`) for load balancers and Kubernetes.
62. Add request ID generation at the API gateway/middleware — log and return it in response headers.
63. Use structured request/response logging with `request_id`, `user_id`, `duration_ms`.
64. Use API keys (hashed in the database) for machine-to-machine API access.
65. Rate-limit by API key, user, and IP — all three.
66. Never log sensitive fields — mask PII, tokens, and passwords in logs.
67. Use mutual TLS (mTLS) for service-to-service communication in zero-trust networks.
68. Validate `Content-Type` and `Content-Length` headers before parsing request bodies.
69. Set `max-body-size` limits to prevent large-payload DoS attacks.
70. Use CORS headers carefully — never use `Access-Control-Allow-Origin: *` on authenticated APIs.
71. Use HTTP/2 for all new services — connection multiplexing dramatically reduces latency.
72. Use `keep-alive` on HTTP/1.1 connections to avoid connection setup overhead.
73. Compress responses with gzip or Brotli for payloads over 1KB.
74. Use server-sent events (SSE) for simple real-time one-way data streams.
75. Use WebSockets for full-duplex real-time communication.

---

## 10. Git & Version Control

> **75 skills** for clean, traceable, and collaborative version control.

1. Write commit messages in imperative mood: "Add feature" not "Added feature".
2. Follow Conventional Commits: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`, `perf:`.
3. Keep commits small and atomic — each commit should represent one logical change.
4. Never commit directly to `main` or `master` — always use a feature branch.
5. Use `git rebase -i` to clean up a feature branch before merging.
6. Use `git commit --fixup <sha>` + `git rebase --autosquash` to clean up messy history.
7. Use `git bisect` to binary-search for the commit that introduced a bug.
8. Use `git log --graph --oneline --all` for a visual branch overview.
9. Use `git blame -L <start>,<end> <file>` to find who last modified specific lines.
10. Use `git log -S "string"` (pickaxe) to find commits that added or removed a string.
11. Use `git log --follow <file>` to trace file history through renames.
12. Use `git diff --stat` to get a summary of changed files before reviewing `git diff`.
13. Use `git stash push -m "description"` to save work-in-progress with a meaningful message.
14. Use `git worktree add` to work on multiple branches simultaneously.
15. Use `git cherry-pick` to apply specific commits to another branch.
16. Use `git revert` to create a new commit undoing a past commit — never `git reset --hard` on shared branches.
17. Use `git reset --soft HEAD~1` to undo the last commit while keeping staged changes.
18. Use `git restore <file>` to discard working tree changes (replaces `git checkout -- <file>`).
19. Use `git switch` for branch operations (replaces `git checkout <branch>`).
20. Use `git fetch --prune` to clean up remote-tracking branches that no longer exist.
21. Use `git remote prune origin` to remove stale remote refs.
22. Use `.gitattributes` to enforce line endings (`text=auto eol=lf`) across platforms.
23. Use `.gitattributes` to mark generated or binary files with `linguist-generated=true`.
24. Use `git lfs` for large binary files (images, videos, models) — never commit binaries to git.
25. Use `git submodule` or `git subtree` for embedding external repos.
26. Use `git tag -a v1.2.3 -m "Release v1.2.3"` for annotated release tags.
27. Sign commits with GPG (`git config --global commit.gpgsign true`) for verified authorship.
28. Sign tags (`git tag -s`) for verified release provenance.
29. Use `pre-commit` hooks to run lint/format checks before every commit.
30. Use `pre-push` hooks to run tests before every push.
31. Use `commit-msg` hooks to enforce Conventional Commits format.
32. Use `git notes` to add metadata to commits without rewriting history.
33. Write a clear `CHANGELOG.md` — it is the human-readable history of your project.
34. Use `git shortlog -sn` to see contributor commit counts.
35. Use `git archive` to create a clean source tarball for release.
36. Use `git bundle` for transferring repositories without a network connection.
37. Use sparse-checkout (`git sparse-checkout set <dirs>`) for working with parts of monorepos.
38. Use shallow clones (`git clone --depth=1`) for CI environments where history is not needed.
39. Use `git config --global rerere.enabled true` to reuse recorded conflict resolutions.
40. Use `git config --global push.autoSetupRemote true` (Git 2.37+) to auto-set upstream.
41. Use `git config --global pull.rebase true` to rebase on pull instead of merge.
42. Use `git config --global merge.conflictstyle diff3` for 3-way conflict markers.
43. Use `git mergetool` with a visual diff tool for complex merge conflicts.
44. Use branch protection rules on `main`: require PRs, require CI green, require review.
45. Use `CODEOWNERS` to automatically assign reviewers to changed paths.
46. Link commits and PRs to issue trackers using `Closes #123` in commit/PR body.
47. Write PR descriptions with context: what changed, why, how to test, and screenshots/videos.
48. Keep PRs focused — one PR per logical change, no "while I was here" scope creep.
49. Rebase feature branches onto `main` before requesting review to resolve conflicts early.
50. Use draft PRs for work-in-progress to get early feedback without formal review.
51. Use GitHub Discussions for exploratory conversations — Issues for actionable work items.
52. Use `gh pr view --json` to inspect PR data programmatically.
53. Use `gh pr checks` to see CI status from the terminal.
54. Use `gh run view --log-failed` to inspect CI failure logs quickly.
55. Use `gh issue list --label bug --state open` to triage open bugs.
56. Use `gh release create` for automated release creation from CI.
57. Use `gh api` for any GitHub REST endpoint not covered by `gh` commands.
58. Use environment-specific branch prefixes: `feat/`, `fix/`, `hotfix/`, `release/`, `chore/`.
59. Use merge queues for busy repositories to prevent merge conflicts on `main`.
60. Use `gitflow` or trunk-based development — pick one and enforce it consistently.
61. Use `git config --global alias.lg "log --graph --oneline --all"` for custom shortcuts.
62. Use `git config --global core.excludesfile ~/.gitignore_global` for personal ignores.
63. Never use `git push --force` on shared branches — use `--force-with-lease` instead.
64. Understand `git reflog` — it is your safety net for recovering lost commits.
65. Use `git fsck` to verify object database integrity.
66. Run `git gc --aggressive` periodically in long-lived repos to compress object storage.
67. Use `gitk` or `git log --graph` to visualize complex branching situations.
68. Always review `git diff --staged` before committing.
69. Use `git add -p` (patch mode) to commit partial file changes.
70. Use `git clean -fdx` (dry-run first: `-n`) to remove untracked files and build artifacts.
71. Use `git describe --tags` to generate human-readable version strings from tags.
72. Add a `VERSION` file or use `git describe` in build scripts for reproducible version info.
73. Use `git config --global init.defaultBranch main` to set default branch name.
74. Audit `git log --all --full-history -- <file>` before claiming a file was never in the repo.
75. Treat commit history as a first-class artifact — write it for future readers, not just today's CI.

---

## 11. Testing & Quality Assurance

> **75 skills** for building confidence through comprehensive, fast, and reliable tests.

1. Test behavior, not implementation — tests should survive refactoring.
2. Follow the Arrange-Act-Assert (AAA) pattern in every test.
3. Name tests descriptively: `TestUserService_CreateUser_DuplicateEmail_Returns409`.
4. Use table-driven tests for multiple variations of the same scenario.
5. Keep unit tests fast (< 1ms each) — no disk I/O, no network, no sleep.
6. Use dependency injection to make all dependencies mockable in unit tests.
7. Mock only what you own — use integration tests for third-party dependencies.
8. Test one thing per test — a test that checks many things is hard to diagnose.
9. Avoid test interdependence — each test must be runnable in isolation and in any order.
10. Use `t.Parallel()` in Go (or equivalent) to run independent tests concurrently.
11. Use fixtures and factories to create test data — never hardcode magic values.
12. Use builder pattern for complex test data setup.
13. Use `testcontainers` to spin up real databases and services in integration tests.
14. Use in-memory databases (SQLite, H2) for fast integration tests where possible.
15. Use golden file tests for complex structured output — compare against a checked-in expected file.
16. Use snapshot testing for UI components — review snapshots carefully on change.
17. Write contract tests (Pact) for API producers and consumers in microservices.
18. Run contract tests in CI for every PR to detect API breakage early.
19. Use property-based testing (Hypothesis, QuickCheck, proptest) for algorithms and parsing.
20. Generate test cases from your OpenAPI/protobuf schema automatically.
21. Use mutation testing (PITest, cargo-mutants) to verify test suite effectiveness.
22. Aim for high coverage on critical paths — track coverage, but don't worship it.
23. Write tests for every bug fix — a test that reproduces the bug before the fix.
24. Write tests before refactoring — they are your safety net.
25. Use `testify/assert` (non-fatal) vs. `testify/require` (fatal) appropriately in Go.
26. Use `t.Cleanup()` for teardown — it runs even if the test panics.
27. Use `t.TempDir()` for test-scoped temporary directories.
28. Use `t.Setenv()` for test-scoped environment variables.
29. Use HTTP `httptest.Server` for testing HTTP clients with real HTTP.
30. Use `net/http/httptest.NewRecorder` for testing HTTP handlers without a server.
31. Use wiremock/nock/msw for mocking HTTP in integration and E2E tests.
32. Test error paths as thoroughly as happy paths.
33. Test boundary conditions: empty, zero, max, overflow, null, negative.
34. Test concurrent access when your code involves shared state.
35. Use `-race` flag in Go to detect data races automatically.
36. Use load testing (`k6`, `Locust`, `wrk`) to validate throughput and latency at scale.
37. Use chaos engineering (Chaos Monkey, Gremlin) to test resilience.
38. Run security tests (SAST, DAST, dependency scanning) in CI.
39. Use `gosec` for Go security scanning; `bandit` for Python; `semgrep` for polyglot.
40. Use `OWASP ZAP` or `Burp Suite` for dynamic web application security testing.
41. Run accessibility tests (`axe`, `Lighthouse`) for frontend components.
42. Use visual regression testing (`Percy`, `Chromatic`) for UI components.
43. Write E2E tests for critical user journeys — sign up, purchase, core feature flow.
44. Keep E2E tests minimal and targeted — they are slow and brittle.
45. Use test doubles (stubs, fakes, mocks, spies) with precision — choose the right type.
46. Use fakes (simple working implementations) over mocks where possible.
47. Verify mock interactions with specific argument matchers, not `anything()`.
48. Use `go generate ./...` to regenerate mocks before running tests.
49. Use `mockery` for generating Go mocks from interfaces.
50. Measure and track test execution time — investigate any test over 1 second.
51. Use test sharding in CI to run large test suites in parallel.
52. Use test caching (`go test -count=1` disables caching when you need a fresh run).
53. Flake tests are a priority — fix or delete them, never `@retry`.
54. Use `go test -run TestSpecific` to run a single test during debugging.
55. Use `go test -v` for verbose output when investigating failures.
56. Use coverage gates in CI (`--fail-under=80`) to prevent coverage regressions.
57. Review coverage reports as a code review artifact — uncovered lines suggest risk.
58. Write acceptance tests in Gherkin (Cucumber/Godog) for product-level specifications.
59. Use `Given-When-Then` format for acceptance test scenarios.
60. Separate unit, integration, and E2E test suites with build tags or directories.
61. Run unit tests on every commit, integration tests on every PR, E2E on every merge.
62. Use `testify/suite` for organizing related tests with shared setup/teardown.
63. Use `subtests` (`t.Run`) for grouping related assertions within one test function.
64. Use `go test -bench=. -benchmem` for micro-benchmarking.
65. Store and compare benchmark results over time — use `benchstat` for comparison.
66. Write regression tests for performance — alert if p99 latency increases by more than 10%.
67. Use `pprof` in tests to profile memory allocations.
68. Test with real-world data samples — synthetic data misses production-only edge cases.
69. Use canary releases to test in production with a small traffic percentage.
70. Use feature flags to A/B test behavior changes in production.
71. Monitor test result trends — a steadily declining pass rate signals systemic issues.
72. Use `go test -shuffle=on` to randomize test order and catch order dependencies.
73. Document WHY each test exists, especially for non-obvious regression tests.
74. Treat test code with the same quality standards as production code.
75. Review tests in code review as carefully as production code.

---

## 12. Security Engineering

> **75 skills** for building secure-by-default software.

1. Apply defense in depth — security at every layer, never rely on a single control.
2. Follow the principle of least privilege — every component gets only the permissions it needs.
3. Use allowlists, not denylists — it's harder to enumerate bad inputs than safe ones.
4. Validate all input at system trust boundaries — never trust external input.
5. Escape output based on the context (HTML, SQL, shell, URL) — not just at input.
6. Use parameterized queries — the only safe way to prevent SQL injection.
7. Use `html/template` (Go) or `.escape()` equivalents for all HTML rendering.
8. Sanitize file names — strip `../`, null bytes, and special characters before using them.
9. Use `Content-Security-Policy` headers to restrict script execution origins.
10. Use `X-Content-Type-Options: nosniff` to prevent MIME-type sniffing.
11. Use `X-Frame-Options: DENY` or `frame-ancestors 'none'` to prevent clickjacking.
12. Use `Strict-Transport-Security` (HSTS) to enforce HTTPS connections.
13. Use `Referrer-Policy: strict-origin-when-cross-origin` to limit referrer leakage.
14. Use `Permissions-Policy` to restrict browser API access (camera, microphone, location).
15. Implement CSRF protection — use SameSite cookies and CSRF tokens for state-changing requests.
16. Hash passwords with bcrypt, scrypt, or Argon2id — never MD5, SHA-1, or SHA-256.
17. Use a minimum bcrypt cost of 12; Argon2id with 64MB memory, 3 iterations.
18. Use `crypto/rand` for all cryptographic random values — never `math/rand`.
19. Use `golang.org/x/crypto` or `cryptography` (Python) for crypto — never roll your own.
20. Use AES-GCM or ChaCha20-Poly1305 for symmetric encryption — never ECB mode.
21. Use RSA-OAEP or ECDH for key exchange — never textbook RSA.
22. Use ECDSA or Ed25519 for digital signatures — avoid RSA below 2048 bits.
23. Rotate cryptographic keys on a schedule and after suspected compromise.
24. Use a Hardware Security Module (HSM) or cloud KMS (AWS KMS, Google KMS) for key management.
25. Store secrets in a secret manager (Vault, AWS Secrets Manager) — never in code or `.env` committed to git.
26. Scan for secrets in commits using `gitleaks`, `truffleHog`, or `git-secrets`.
27. Use environment variables for configuration secrets in production.
28. Redact secrets from logs — use structured logging with an allow-list of safe fields.
29. Implement audit logging for all sensitive actions (login, permission change, data export).
30. Use append-only audit logs that cannot be modified after writing.
31. Implement authentication with a proven library — never write your own auth.
32. Use OAuth 2.0 + OIDC for federated identity — never implement custom SSO.
33. Enforce MFA for all administrative and sensitive accounts.
34. Implement account lockout after N failed login attempts with exponential backoff.
35. Use short-lived, non-renewable tokens for password reset — invalidate on use.
36. Use `HttpOnly` and `Secure` flags on all session cookies.
37. Use `SameSite=Strict` or `SameSite=Lax` on session cookies.
38. Set appropriate cookie `Path` and `Domain` to minimize scope.
39. Implement session invalidation on logout — server-side session revocation.
40. Use rate limiting on all authentication endpoints.
41. Implement IP-based blocking for repeated failed authentication attempts.
42. Use `time.ConstantTimeCompare` for comparing secrets — never `==`.
43. Avoid timing oracles — all secret comparison operations must be constant-time.
44. Use `net/http`'s built-in TLS with `crypto/tls.Config` — disable SSLv3, TLS 1.0, TLS 1.1.
45. Use `tls.X509KeyPair` with certificates from a trusted CA or Let's Encrypt.
46. Enable OCSP stapling to avoid CA round-trips during TLS handshakes.
47. Pin TLS certificates in high-security mobile and CLI applications.
48. Use certificate transparency logs to detect unauthorized certificate issuance.
49. Use `go test -run TestSecurity` + `gosec` in CI for automated security gating.
50. Run `trivy`, `Grype`, or `Snyk` for container and dependency vulnerability scanning.
51. Use `SBOM` (Software Bill of Materials) for tracking supply chain components.
52. Sign container images with `cosign` for supply chain integrity.
53. Use `distroless` or `scratch` base images to minimize container attack surface.
54. Run containers as non-root users — `USER 1000:1000` in Dockerfile.
55. Use read-only root filesystem in containers where possible.
56. Use seccomp profiles and AppArmor/SELinux to restrict container syscalls.
57. Use `network policies` in Kubernetes to restrict pod-to-pod communication.
58. Scan IaC templates (Terraform, CloudFormation) with `tfsec` or `checkov`.
59. Use `OPA` (Open Policy Agent) for policy-as-code enforcement.
60. Implement threat modeling (STRIDE) for new features and architectures.
61. Conduct regular penetration testing and red team exercises.
62. Follow secure SDLC: threat model → design review → code review → SAST/DAST → pentest.
63. Use `gorilla/csrf` or equivalent CSRF middleware in web frameworks.
64. Validate redirect URLs against an allowlist — never redirect to arbitrary user-supplied URLs.
65. Implement directory traversal prevention for all file access operations.
66. Limit file upload types, sizes, and destinations — scan uploaded files for malware.
67. Disable directory listing on web servers serving static files.
68. Remove debug endpoints (`/debug/pprof`, `/swagger`) from production deployments.
69. Use dependency pinning (`go.sum`, `package-lock.json`) to prevent dependency confusion attacks.
70. Monitor for new CVEs in your dependency tree using `dependabot` or `renovate`.
71. Implement error handling that reveals minimal information to untrusted callers.
72. Use separate error codes for public APIs versus internal logs.
73. Document security assumptions and threat model in architecture docs.
74. Follow OWASP Top 10 as a minimum security checklist for web applications.
75. Conduct security training for all engineers annually — security is a team responsibility.

---

## 13. Performance Optimization

> **75 skills** for making software measurably faster and more efficient.

1. Measure first — never optimize without profiling data showing a real bottleneck.
2. Define performance goals (p50, p99, throughput, memory) before optimizing.
3. Use `pprof` (Go), `py-spy` (Python), `perf` (Linux) for CPU profiling.
4. Use `pprof heap` or `Valgrind massif` for memory allocation profiling.
5. Use `go test -benchmem` to measure allocations per operation.
6. Reduce allocations in hot paths — prefer stack allocation and object pooling.
7. Use `sync.Pool` to reuse frequently allocated objects.
8. Use `bytes.Buffer` or `strings.Builder` instead of string concatenation in loops.
9. Pre-allocate slices with `make([]T, 0, expectedLen)` to avoid repeated reallocation.
10. Use `append` carefully — it doubles slice capacity, which can waste memory.
11. Avoid interface boxing of small types in hot paths — boxing causes heap allocation.
12. Use value types instead of pointer types for small, frequently-passed structs.
13. Use struct field ordering to minimize padding — put large fields first.
14. Use `unsafe.Sizeof` to verify struct sizes match expectations.
15. Use `MADV_HUGEPAGE` on Linux for large allocations to improve TLB hit rates.
16. Use memory-mapped files for large dataset access — `mmap` avoids read syscalls.
17. Use `io.ReadFull` and `bufio.Reader` to minimize syscall frequency.
18. Use `bufio.Writer` to batch small writes into fewer syscalls.
19. Use `sendfile` (via `io.Copy` with `*os.File` on Linux) for zero-copy file transfers.
20. Reduce lock contention — shard locks, use atomic ops, or redesign to avoid shared state.
21. Use lock-free data structures (channels, atomic vars) for high-contention paths.
22. Use NUMA-aware memory allocation for multi-socket systems.
23. Avoid false sharing — pad cache lines (typically 64 bytes) in concurrent data structures.
24. Use worker pools of fixed size instead of spawning a goroutine per request.
25. Use `GOMAXPROCS` tuned to the machine's CPU count (default since Go 1.5).
26. Use `runtime.LockOSThread` only when interfacing with non-reentrant C code.
27. Use batching for database operations — N inserts in one `INSERT ... VALUES` is faster than N round trips.
28. Use read replicas for read-heavy database workloads.
29. Use connection pooling to avoid connection establishment overhead.
30. Use prepared statements to avoid query parsing overhead.
31. Use `EXPLAIN ANALYZE` to confirm indexes are being used for slow queries.
32. Use partial indexes to make indexes smaller and faster.
33. Use covering indexes to eliminate table heap access for common queries.
34. Cache database query results in Redis with appropriate TTL.
35. Use `stale-while-revalidate` caching strategy for data that can tolerate brief staleness.
36. Use HTTP `Cache-Control: max-age` for static and semi-static API responses.
37. Use CDN for static assets — offload bandwidth from origin servers.
38. Compress responses with gzip (`level 5-6`) or Brotli (`level 4-6`) for text payloads.
39. Use HTTP/2 server push for critical resources.
40. Minify and bundle JavaScript/CSS — reduce the number of HTTP round trips.
41. Use lazy loading for non-critical resources (images, scripts, routes).
42. Use content-addressable hashing (`/assets/main.abc123.js`) for infinite cache TTLs.
43. Use `requestIdleCallback` (browser) for deferring non-critical UI work.
44. Use `OffscreenCanvas` for CPU-intensive canvas rendering off the main thread.
45. Use `WebAssembly` for computationally intensive browser-side workloads.
46. Use `SIMD` intrinsics (via C/Rust/WASM SIMD) for vectorizable loops.
47. Use columnar data formats (Parquet, Arrow) for analytical workloads.
48. Use `io_uring` for ultra-high-performance async I/O on Linux 5.1+.
49. Profile network latency with `curl --trace-time` or Wireshark for API calls.
50. Use keep-alive connections to amortize TCP handshake costs.
51. Use `TCP_NODELAY` (disable Nagle's algorithm) for latency-sensitive connections.
52. Use `SO_REUSEPORT` to allow multiple processes to listen on the same port.
53. Use `epoll`/`kqueue`-based event loops (net/http uses this internally in Go).
54. Profile GC pause times — use `GODEBUG=gctrace=1` in Go.
55. Reduce GC pressure by reusing objects and minimizing pointer-heavy data structures.
56. Use `runtime.SetGCPercent(200)` to trade more memory for less GC frequency.
57. Use `runtime.SetMemoryLimit` (Go 1.19+) to bound Go's memory footprint.
58. Use `GOGC=off` in latency-sensitive benchmarks to measure non-GC performance.
59. Use flamegraphs to identify hot functions visually — `go tool pprof -http=:6060`.
60. Use `perf stat` to measure CPU cycles, cache misses, and branch mispredictions.
61. Use `cachegrind` / `callgrind` for cache-miss analysis.
62. Use `heaptrack` for detailed memory allocation tracking on Linux.
63. Use `ab` or `hey` for quick HTTP load testing from the terminal.
64. Use `wrk` with Lua scripts for more complex HTTP load test scenarios.
65. Use `k6` for scripted, assertion-based load and performance tests in CI.
66. Use `perf c2c` to detect false sharing in multi-threaded code.
67. Use `numactl` to pin processes to specific NUMA nodes.
68. Use `taskset` to pin processes to specific CPU cores.
69. Use `cgroup` memory and CPU limits to test behavior under resource constraints.
70. Use `nsenter` to run commands inside a container's namespace for performance debugging.
71. Use `bpftrace` or `bcc` tools for low-overhead production profiling.
72. Use `opentelemetry` spans to measure real-user latency at the code level.
73. Set SLOs/SLAs before optimizing — define "fast enough" to avoid over-engineering.
74. Document every performance optimization with a benchmark before/after result.
75. Re-profile after major version upgrades — runtimes and libraries change performance characteristics.

---

## 14. DevOps & CI/CD

> **75 skills** for reliable, fast, and safe software delivery pipelines.

1. Treat infrastructure as code — every resource defined in version-controlled IaC.
2. Use GitHub Actions, GitLab CI, or CircleCI for CI/CD — never Jenkins unless forced.
3. Run CI on every push to every branch — not just on main.
4. Keep CI jobs fast (< 10 minutes) — shard, cache, and parallelize aggressively.
5. Cache dependencies (`~/.cache/go`, `node_modules`, pip cache) in CI to avoid re-downloading.
6. Use matrix builds to test against multiple OS/language versions simultaneously.
7. Use `actions/cache` (GitHub Actions) with a cache key based on lock file hash.
8. Fail CI fast — put fastest/cheapest checks (lint, vet) first.
9. Use ephemeral CI runners — never rely on runner state persisting between jobs.
10. Use GitHub Actions `concurrency` to cancel in-flight runs for the same branch.
11. Use `workflow_dispatch` with inputs for manual CI triggers.
12. Use `workflow_call` to compose reusable workflow fragments.
13. Use `GITHUB_TOKEN` for repository-scoped operations — never commit personal tokens.
14. Use `secrets.GITHUB_TOKEN` for publishing packages in Actions workflows.
15. Pin GitHub Actions to specific commit SHA (`uses: actions/checkout@abc1234`) to prevent supply chain attacks.
16. Use `timeout-minutes` on every CI job to prevent runaway jobs.
17. Use `continue-on-error: true` selectively — never for security or test jobs.
18. Use `if: failure()` steps for notification/cleanup after job failures.
19. Use deployment environments with required reviewers for production deployments.
20. Use branch protection with required status checks before merge.
21. Use semantic versioning tags to trigger release workflows.
22. Build artifacts once and promote them through environments — never rebuild per environment.
23. Sign and verify artifacts at every stage of the pipeline.
24. Use SBOM generation in CI and attach it to every release.
25. Publish container images to a registry with digest-pinned references.
26. Use multi-platform builds (`docker buildx`) for `linux/amd64` and `linux/arm64`.
27. Use layer caching in Docker builds (`--cache-from type=registry`).
28. Use `hadolint` to lint Dockerfiles in CI.
29. Scan container images with `trivy` in CI and fail on CRITICAL vulnerabilities.
30. Use `cosign sign` to sign container images after pushing.
31. Use blue/green deployments to enable instant rollback.
32. Use canary deployments to progressively shift traffic to new versions.
33. Use `argo-rollouts` or Flagger for automated canary analysis with Prometheus metrics.
34. Implement automated rollback triggered by error rate or latency SLO breach.
35. Use Helm charts for Kubernetes deployments — version-control chart values.
36. Use `helm diff` (plugin) to preview chart changes before applying.
37. Use Kustomize for environment-specific Kubernetes configuration overlays.
38. Use ArgoCD or Flux for GitOps-based continuous deployment.
39. Use `kubectl rollout status` to verify deployment success in CI.
40. Use readiness probes to prevent traffic to pods that aren't ready.
41. Use liveness probes to restart deadlocked pods.
42. Use startup probes for slow-starting containers to avoid premature liveness failures.
43. Set CPU and memory `requests` and `limits` on every Kubernetes container.
44. Use `PodDisruptionBudget` to maintain availability during rolling updates.
45. Use `HorizontalPodAutoscaler` with custom metrics for dynamic scaling.
46. Use `VerticalPodAutoscaler` recommendations to right-size resource requests.
47. Use namespace-level `ResourceQuota` to prevent runaway resource consumption.
48. Use `NetworkPolicy` to whitelist pod ingress/egress explicitly.
49. Use `PodSecurityAdmission` (or OPA Gatekeeper) to enforce security contexts.
50. Use `Secrets` (not `ConfigMaps`) for sensitive data in Kubernetes.
51. Use `ExternalSecrets` operator with Vault or AWS Secrets Manager — never put secrets in git.
52. Enable Kubernetes audit logging for forensics and compliance.
53. Use `kube-bench` to assess Kubernetes CIS benchmark compliance.
54. Use `Falco` for runtime security monitoring in Kubernetes.
55. Use Terraform with remote state (S3 + DynamoDB lock, Terraform Cloud) for IaC.
56. Use `terraform plan` in CI and require human approval before `terraform apply`.
57. Use `atlantis` or `terraform cloud` for pull-request-based Terraform workflows.
58. Use `tflint` and `tfsec` in CI for Terraform quality and security.
59. Use `checkov` for multi-framework IaC scanning (Terraform, CloudFormation, Helm).
60. Use `pulumi` for type-safe IaC in familiar languages when Terraform HCL is limiting.
61. Use Ansible for configuration management — idempotent playbooks always.
62. Use `ansible-lint` in CI for Ansible playbook quality.
63. Use `packer` to build immutable machine images.
64. Use `vagrant` for reproducible local development environments.
65. Use observability as a deployment gate — alert on error rate, latency, and saturation.
66. Use `runbooks` (linked from alerts) to document step-by-step incident response.
67. Conduct game days — simulate production failures to test runbooks.
68. Use `chaos engineering` tools (Chaos Monkey, Gremlin, Litmus) to test resilience.
69. Implement change freeze windows around high-traffic events.
70. Use feature flags as a kill switch — deploy code disabled, enable via flag.
71. Use `LaunchDarkly`, `Unleash`, or simple Redis flags for feature management.
72. Use deployment frequency, lead time, MTTR, and change failure rate as DORA metrics.
73. Measure and minimize "time to restore" — your incident response is only as good as your monitoring.
74. Use post-incident reviews (blameless) to extract systemic improvements.
75. Automate everything that is done more than twice — toil is the enemy of reliability.

---

## 15. Cloud & Infrastructure

> **75 skills** for designing, operating, and cost-optimizing cloud infrastructure.

1. Design for failure — every cloud resource will eventually fail.
2. Use multi-AZ deployments for all production stateful services.
3. Use multi-region active/active or active/passive for global availability requirements.
4. Use managed services over self-hosted wherever the operational overhead outweighs the cost.
5. Use auto-scaling groups with scheduled and metric-based scaling policies.
6. Right-size instances using AWS Compute Optimizer or GCP Recommender.
7. Use spot/preemptible instances for fault-tolerant batch workloads to reduce cost by 70-90%.
8. Use reserved or committed-use instances for stable baseline workloads.
9. Use savings plans (AWS) or committed-use discounts (GCP) for predictable compute.
10. Tag all cloud resources with `project`, `environment`, `team`, `cost-center`.
11. Set billing alerts and budgets for every cloud account.
12. Use cost anomaly detection to catch unexpected spending spikes immediately.
13. Use `infracost` in CI to estimate Terraform cost changes before applying.
14. Use S3 Intelligent-Tiering or GCS Autoclass for objects with unpredictable access patterns.
15. Set S3 lifecycle rules to transition objects to cheaper storage classes over time.
16. Enable S3 versioning on buckets storing critical data — it enables object recovery.
17. Use S3 Object Lock for WORM compliance on audit logs and backups.
18. Enable CloudTrail (AWS) or Cloud Audit Logs (GCP) for all API call logging.
19. Enable VPC flow logs for network traffic analysis and security investigation.
20. Use VPC with private subnets for all backend resources — never expose databases publicly.
21. Use VPC peering or Transit Gateway for cross-VPC communication.
22. Use PrivateLink/Private Service Connect for accessing cloud services without public internet.
23. Use NAT Gateway (not NAT instance) for outbound internet from private subnets.
24. Use security groups as stateful firewalls — allow only required ports from required sources.
25. Use NACLs (Network ACLs) as a second layer for subnet-level traffic control.
26. Use AWS WAF or Cloud Armor for layer-7 DDoS protection and rule-based filtering.
27. Use Shield Advanced for volumetric DDoS protection on critical applications.
28. Use CloudFront (AWS) or Cloud CDN (GCP) for global content delivery.
29. Enable access logging on load balancers and CDNs for forensic analysis.
30. Use ALB (Application Load Balancer) for HTTP/HTTPS; NLB for TCP/UDP workloads.
31. Use target groups with health checks to route traffic only to healthy instances.
32. Use AWS ECS Fargate or GCP Cloud Run for serverless container deployments.
33. Use AWS Lambda or GCP Cloud Functions for event-driven, short-duration workloads.
34. Use Lambda Layers for sharing code between Lambda functions.
35. Use Lambda Powertools for structured logging, tracing, and metrics in Lambda.
36. Set Lambda `ReservedConcurrency` to prevent runaway scaling on noisy events.
37. Use SQS as a Lambda trigger for reliable, at-least-once async processing.
38. Use SQS FIFO queues when message ordering and exactly-once processing are required.
39. Use SNS for fan-out pub/sub message delivery.
40. Use EventBridge for event-driven architectures with rich routing rules.
41. Use Step Functions for orchestrating multi-step workflows with error handling.
42. Use RDS Multi-AZ for highly available relational databases.
43. Use RDS Proxy for Lambda/serverless connections to avoid connection pool exhaustion.
44. Use Aurora Serverless v2 for variable-load relational database workloads.
45. Use ElastiCache Redis for distributed caching and session storage.
46. Use DynamoDB for single-digit millisecond NoSQL with auto-scaling.
47. Use DynamoDB Streams + Lambda for change data capture patterns.
48. Use DAX (DynamoDB Accelerator) for microsecond read latency on hot keys.
49. Use IAM roles on EC2/ECS/Lambda — never hardcode credentials.
50. Use IAM least-privilege policies — start with deny-all and add specific allows.
51. Use Service Control Policies (SCPs) in AWS Organizations for account-level guardrails.
52. Use IAM Permission Boundaries to limit maximum permissions for delegated roles.
53. Enable MFA on all IAM root accounts and human users.
54. Use AWS SSO or Google Cloud Identity for centralized identity management.
55. Rotate access keys automatically using Secrets Manager rotation.
56. Use AWS Config rules to detect and auto-remediate configuration drift.
57. Use Security Hub to aggregate findings from Guard Duty, Inspector, and Macie.
58. Enable GuardDuty for ML-based threat detection across AWS accounts.
59. Use Macie for sensitive data (PII) discovery in S3 buckets.
60. Enable Inspector for continuous EC2 and container vulnerability assessment.
61. Use CloudWatch Logs Insights for querying structured logs at scale.
62. Use X-Ray or Cloud Trace for distributed request tracing.
63. Use Managed Prometheus + Grafana (or Datadog) for infrastructure metrics.
64. Set up alarms on CPU, memory, disk, network, and application-level metrics.
65. Use SNS + PagerDuty/OpsGenie for alert routing to on-call engineers.
66. Use CloudWatch Synthetics or Datadog Synthetics for external endpoint monitoring.
67. Implement runbooks as code — use SSM Automation documents for repeatable remediation.
68. Use AWS Systems Manager Session Manager instead of SSH for bastion-free access.
69. Use AWS Config + CloudFormation StackSets for consistent multi-account deployments.
70. Use AWS Organizations with SCPs to enforce security baseline across all accounts.
71. Use a landing zone (Control Tower, or custom) for consistent account vending.
72. Enable S3 Block Public Access at the organization/account level.
73. Use AWS Backup for centralized backup management across services.
74. Test disaster recovery plans quarterly — an untested DR plan is not a DR plan.
75. Document cloud architecture with diagrams in `docs/architecture/` — keep them updated.

---

## 16. Frontend & UI Engineering

> **75 skills** for building accessible, performant, and maintainable user interfaces.

1. Use React 18+ with concurrent features (`useTransition`, `useDeferredValue`, `Suspense`).
2. Use `useReducer` + Context for complex state; use Zustand or Jotai for global state.
3. Use TanStack Query (React Query) for server state — eliminate manual fetch/loading/error state.
4. Prefer server components (Next.js 13+) for data-fetching-heavy pages to reduce client bundle.
5. Use `React.memo`, `useMemo`, and `useCallback` only after profiling shows a re-render bottleneck.
6. Use the React DevTools Profiler to identify expensive renders before optimizing.
7. Use `key` correctly — stable, unique keys from data IDs, never array indices.
8. Never put derived state in `useState` — derive it during render.
9. Use `useEffect` only for synchronizing with external systems — not for data transformation.
10. Use `useLayoutEffect` only for DOM measurements that must be synchronous.
11. Use `useRef` for mutable values that don't trigger re-renders (timers, DOM refs).
12. Use `useId` for generating stable, hydration-safe IDs for accessibility attributes.
13. Use custom hooks to extract and reuse stateful logic across components.
14. Keep components small — extract sub-components when JSX exceeds ~100 lines.
15. Use `Suspense` boundaries for lazy-loaded components and async data.
16. Use `ErrorBoundary` components to catch and display render errors gracefully.
17. Use `React.lazy` + `Suspense` for route-level code splitting.
18. Use Next.js `Image` component for automatic WebP conversion and lazy loading.
19. Use Next.js `Link` component for client-side navigation with prefetching.
20. Use Next.js `dynamic` for component-level code splitting with SSR control.
21. Use Tailwind CSS for utility-first styling — consistency through design tokens.
22. Use CSS Modules or CSS-in-JS (`styled-components`, `Emotion`) for scoped component styles.
23. Use CSS custom properties (variables) for theming — avoid JavaScript-driven theming.
24. Use `prefers-color-scheme` media query for automatic dark mode support.
25. Use `prefers-reduced-motion` media query to respect user motion preferences.
26. Use `rem` and `em` for font sizes; `px` only for borders and small fixed elements.
27. Use CSS Grid for two-dimensional layout; Flexbox for one-dimensional layout.
28. Use `clamp()` for responsive font sizes without media query breakpoints.
29. Use `aspect-ratio` CSS property instead of padding hacks for responsive boxes.
30. Test responsive layouts on real devices — browser DevTools emulation is insufficient.
31. Follow WCAG 2.1 AA accessibility guidelines as a minimum standard.
32. Use semantic HTML elements (`<button>`, `<nav>`, `<main>`, `<article>`) not `<div>` for everything.
33. Every interactive element must be keyboard-navigable with visible focus indicators.
34. Every image must have a meaningful `alt` attribute — empty string for decorative images.
35. Use `aria-label`, `aria-labelledby`, `aria-describedby` to provide accessible names.
36. Use `role` attributes only when native semantics are insufficient.
37. Use `aria-live` regions for dynamic content updates that screen readers should announce.
38. Test with screen readers (`NVDA`, `VoiceOver`, `JAWS`) on real browsers.
39. Run `axe-core` in tests to catch automated accessibility violations.
40. Use `Lighthouse` to audit performance, accessibility, and SEO.
41. Use Core Web Vitals (LCP, FID/INP, CLS) as your primary performance metrics.
42. Aim for LCP < 2.5s, INP < 200ms, CLS < 0.1 on real devices over 3G.
43. Use `<link rel="preload">` for critical fonts, images, and scripts.
44. Use `<link rel="preconnect">` to warm up connections to critical third-party origins.
45. Use `font-display: swap` to prevent invisible text during font loading.
46. Use the `loading="lazy"` attribute on below-the-fold images.
47. Use `fetchpriority="high"` on the LCP image to prioritize its load.
48. Use WebP and AVIF image formats — they are 30-50% smaller than JPEG/PNG.
49. Serve responsive images with `srcset` and `sizes` attributes.
50. Inline critical CSS for above-the-fold content to eliminate render-blocking.
51. Use `Content-Encoding: br` (Brotli) for all text assets — 15-20% smaller than gzip.
52. Use `immutable` in `Cache-Control` for hashed static assets.
53. Use service workers for offline support and background sync.
54. Use the `Cache API` in service workers for strategic caching of assets.
55. Use `IndexedDB` for large structured client-side data storage.
56. Use `localStorage` only for tiny, non-sensitive user preferences.
57. Use `sessionStorage` for tab-scoped temporary data.
58. Use `crypto.subtle` for client-side cryptography — `window.crypto.getRandomValues` for random.
59. Use Storybook for component development in isolation.
60. Write visual regression tests with Chromatic or Percy against Storybook stories.
61. Use `@storybook/test` (formerly `storybook/jest`) for interaction tests within Storybook.
62. Use Design Tokens (CSS variables, Tailwind config) to codify the design system.
63. Build accessible form fields — always associate `<label>` with `<input>` via `for`/`id` or wrapping.
64. Use `fieldset` + `legend` for grouping related form controls.
65. Use `required`, `aria-required`, `aria-invalid`, and `aria-errormessage` for accessible form validation.
66. Use `react-hook-form` or `Formik` for performant, accessible form state management.
67. Validate forms on the client for UX, but always re-validate on the server.
68. Use `DOMPurify` before rendering any user-supplied HTML — XSS is still common.
69. Use Content Security Policy Level 3 with nonces for inline scripts.
70. Monitor frontend errors with Sentry or Datadog RUM.
71. Use Real User Monitoring (RUM) to measure field performance on real user devices.
72. Use synthetic monitoring (Datadog Synthetics, Playwright-based) for uptime and journey testing.
73. Use `react-i18next` or `next-intl` for internationalization from the start.
74. Test RTL (right-to-left) layouts if the product targets Arabic, Hebrew, or Persian speakers.
75. Instrument key user journeys with analytics events — build, measure, learn.

---

## 17. Backend Architecture

> **75 skills** for designing scalable, maintainable, and resilient backend systems.

1. Start with a monolith — extract services only when team and scale demand it.
2. Design the domain model first — code is a consequence of the domain, not the other way around.
3. Use Domain-Driven Design (DDD) bounded contexts to delineate service boundaries.
4. Use hexagonal architecture (ports and adapters) to decouple business logic from infrastructure.
5. Use CQRS (Command Query Responsibility Segregation) when read and write models diverge significantly.
6. Use event sourcing for audit-critical domains where history must be reconstructed.
7. Separate the application layer (use cases) from the domain layer (business rules).
8. Use the repository pattern to abstract database access from business logic.
9. Use the unit of work pattern to manage transaction boundaries.
10. Design services around business capabilities, not technical layers.
11. Use asynchronous messaging (queues, events) to decouple services.
12. Design consumers to be idempotent — messages may be delivered more than once.
13. Use exactly-once semantics only when idempotency is genuinely impossible.
14. Use the outbox pattern to ensure atomic database writes + event publishing.
15. Use the saga pattern for distributed transactions spanning multiple services.
16. Use compensating transactions to roll back distributed operations.
17. Design for eventual consistency — document which data can be temporarily stale.
18. Use event-driven architecture for loose coupling and independent deployability.
19. Use schema registries (Confluent, AWS Glue) for Kafka message schema management.
20. Use Apache Kafka for high-throughput, durable event streaming.
21. Use consumer groups for parallel event processing with Kafka.
22. Use `__consumer_offsets` topic for durable offset tracking.
23. Design Kafka topics with sufficient partitions for the expected throughput.
24. Use compacted topics for maintaining the latest value per key (changelog).
25. Use RabbitMQ for task queuing with complex routing and acknowledgment semantics.
26. Use NATS for lightweight, high-performance pub/sub messaging.
27. Use gRPC for synchronous, strongly-typed inter-service communication.
28. Use service mesh (Istio, Linkerd) for mTLS, observability, and traffic management.
29. Use circuit breakers (resilience4j, go-resilience) for protecting against cascading failures.
30. Use bulkhead pattern to isolate failures in one part of the system.
31. Use retry with exponential backoff + jitter for transient failure recovery.
32. Use timeouts on every external call — no request should wait indefinitely.
33. Use distributed tracing (Jaeger, Zipkin, Tempo) to trace requests across services.
34. Use structured logging with correlation ID, service name, and trace ID.
35. Use the sidecar pattern for cross-cutting concerns (logging, tracing, mTLS).
36. Use the ambassador pattern for off-loading client connectivity concerns.
37. Use the anti-corruption layer to translate between external and internal domain models.
38. Use the strangler fig pattern to incrementally replace legacy systems.
39. Use feature toggles for gradual migration of traffic to new implementations.
40. Design stateless services — store session state in Redis or a database.
41. Use stateful sets (Kubernetes) only for services that require stable network identity.
42. Use leader election (etcd, Zookeeper, Redis `SETNX`) for distributed coordination.
43. Use optimistic locking (version fields) for concurrent update conflicts.
44. Use pessimistic locking (`SELECT FOR UPDATE`) when conflict is frequent.
45. Use database-level upserts (`ON CONFLICT DO UPDATE`) for race-condition-safe writes.
46. Use distributed rate limiting (Redis token bucket) across service instances.
47. Use a service discovery system (Consul, Kubernetes DNS) for dynamic endpoint resolution.
48. Use health endpoints (`/healthz`, `/readyz`) and integrate them with load balancers.
49. Use blue/green or canary deployments for zero-downtime releases.
50. Use rolling updates for stateless services; shutdown hooks for graceful drain.
51. Implement graceful shutdown: stop accepting new requests, drain in-flight, close connections.
52. Use `SIGTERM` handler + shutdown deadline to drain gracefully.
53. Document SLIs, SLOs, and SLAs for every service.
54. Set error rate and latency SLO alerts — automate rollback on SLO breach.
55. Implement distributed request deduplication using idempotency keys + Redis.
56. Use consistent hashing for routing requests to specific workers (e.g., WebSocket sessions).
57. Use backpressure to prevent overload — shed load gracefully under pressure.
58. Use load shedding (return `503`) when capacity is exceeded — better than a cascade.
59. Use the throttle pattern to slow down excessive clients without rejecting them.
60. Design multi-tenancy from the start — schema-per-tenant, row-level security, or separate databases.
61. Use row-level security (RLS) in PostgreSQL for tenant data isolation.
62. Use separate connection pools per tenant for strong isolation.
63. Use soft multi-tenancy (shared schema) for small tenants, hard multi-tenancy for large.
64. Design billing and metering as a separate domain — decouple from core product logic.
65. Use webhooks for asynchronous event notification to external systems.
66. Implement webhook retry with exponential backoff and dead-letter queues.
67. Validate webhook signatures (HMAC) before processing incoming events.
68. Use a queue for webhook delivery — never call external URLs synchronously.
69. Implement admin APIs separately from product APIs — apply stricter auth and audit logging.
70. Use background jobs (Sidekiq, Asynq, Bull) for work that doesn't need to be synchronous.
71. Monitor job queue depths and latencies — alert on growing queues.
72. Use dead-letter queues for jobs that fail after max retries.
73. Design for observability — every service should emit logs, metrics, and traces out of the box.
74. Use OpenTelemetry as the instrumentation standard — vendor-agnostic by design.
75. Document every service's upstream and downstream dependencies in a service catalog.

---

## 18. Debugging & Root Cause Analysis

> **75 skills** for systematically identifying and eliminating bugs.

1. Reproduce the bug reliably before attempting a fix — never fix what you can't reproduce.
2. Write a failing test that reproduces the bug before writing the fix.
3. Use binary search (bisect) to isolate which change introduced the bug.
4. Use `git bisect` to find the exact commit that introduced a regression.
5. Add strategic log statements before reaching for a debugger.
6. Use structured logging — search logs with `jq`, `lnav`, or Kibana.
7. Use `GODEBUG=schedtrace=1000` to trace Go scheduler behavior.
8. Use `GODEBUG=gctrace=1` to diagnose excessive GC pauses.
9. Use `dlv` (Delve) for full-featured Go debugging with breakpoints and variable inspection.
10. Use `pdb.set_trace()` or `breakpoint()` for Python interactive debugging.
11. Use `gdb` for C/C++ and native code debugging.
12. Use `strace` to trace system calls and identify unexpected file/network operations.
13. Use `ltrace` to trace library function calls.
14. Use `lsof` to find open file descriptors and identify file/socket leaks.
15. Use `tcpdump` or Wireshark to capture and analyze network traffic.
16. Use `ss -tlnp` to list all listening sockets and identify port conflicts.
17. Use `netstat -s` to inspect TCP/UDP statistics and retransmit counts.
18. Use `iperf3` to measure actual network bandwidth and rule out network bottlenecks.
19. Use `mtr` for real-time network path analysis combining ping + traceroute.
20. Use `curl -v` and `httpie` to inspect HTTP requests/responses step by step.
21. Use browser DevTools Network tab to inspect XHR/fetch requests including headers.
22. Use browser DevTools Performance tab to record and analyze runtime performance.
23. Use `console.trace()` to print a stack trace at any point in JavaScript.
24. Use `debugger;` statement in JavaScript to trigger breakpoints in DevTools.
25. Use React DevTools to inspect component tree, props, state, and re-renders.
26. Use Redux DevTools or Zustand devtools for state change time-travel debugging.
27. Isolate the bug by reducing the test case to the minimal reproduction.
28. Use a REPL (Python `ipython`, Node `node`, Go `gore`) for interactive experimentation.
29. Comment out code in binary search fashion to isolate the broken section.
30. Use feature flags to disable a suspected code path in production without a deploy.
31. Use `pprof` HTTP endpoints in production Go services for on-demand profiling.
32. Use `trace.Start()` in Go for execution trace analysis with `go tool trace`.
33. Use `GOGC=off` to disable GC temporarily and isolate GC-related latency spikes.
34. Use `runtime.ReadMemStats` to inspect heap allocations in a running Go process.
35. Use `GOMAXPROCS=1` to reproduce race conditions in single-threaded mode.
36. Use `-race` detector to find data races — run tests with `-race` flag regularly.
37. Use `goleak.VerifyNone(t)` to detect goroutine leaks in tests.
38. Use `GODEBUG=asyncpreemptoff=1` to diagnose spurious preemption-related crashes.
39. Use `os.Setenv("GOTRACEBACK", "all")` to get full goroutine dump on panic.
40. Use `kill -SIGQUIT <pid>` (Go) to dump all goroutine stacks to stderr.
41. Use `SIGUSR1` handlers to dump diagnostic state on demand without restarting.
42. Read error messages carefully — they usually contain the exact problem.
43. Read stack traces from bottom to top — the root cause is usually at the bottom.
44. Check `errno` values in C/system-level errors — they precisely describe the failure.
45. Use `perror()` or `strerror(errno)` to translate error codes to messages.
46. Check the exact version of every tool in the stack — bugs often depend on versions.
47. Use `docker logs`, `kubectl logs`, and `journalctl` for container/service log access.
48. Use `kubectl describe pod` to diagnose pod scheduling and startup failures.
49. Use `kubectl events --field-selector involvedObject.name=<pod>` for Kubernetes event logs.
50. Use `kubectl exec -it <pod> -- sh` to shell into a running container.
51. Use ephemeral debug containers (`kubectl debug`) when the main container has no shell.
52. Use `dmesg | grep OOM` to check for out-of-memory kills.
53. Check `/proc/<pid>/limits` for ulimit constraints causing file descriptor errors.
54. Use `valgrind --leak-check=full` for memory leak detection in C/C++ programs.
55. Use `AddressSanitizer` (ASan) for detecting buffer overflows and use-after-free.
56. Use `ThreadSanitizer` (TSan) for detecting data races in native code.
57. Use `UndefinedBehaviorSanitizer` (UBSan) for undefined behavior detection.
58. Use MIRI for detecting undefined behavior in Rust's unsafe code.
59. Use `heaptrack` for detailed heap allocation tracking and flame graph visualization.
60. Use `massif` (Valgrind) to measure heap usage over time.
61. Reproduce bugs with the minimal set of environment variables and inputs.
62. Check for time-related bugs — timezone, DST, leap year, clock skew between services.
63. Check for encoding bugs — UTF-8 vs. Latin-1, BOM presence, newline differences.
64. Check for floating-point precision bugs — never compare floats with `==`.
65. Check for integer overflow — especially when mixing signed and unsigned types.
66. Check for off-by-one errors in loop bounds, slice indices, and length calculations.
67. Check for race conditions with concurrent access to shared state.
68. Check for deadlocks — use `go routine` dumps or `jstack` to identify lock holders.
69. Use the "5 Whys" technique to find root cause beyond surface symptoms.
70. Use fault trees to systematically enumerate all possible causes.
71. Document the bug, reproduction steps, root cause, and fix in the commit message.
72. Add a regression test for every bug — no exceptions.
73. Share bug post-mortems with the team — learning is a collective activity.
74. Add monitoring to catch the same class of bug in the future.
75. When stuck for > 30 minutes, explain the bug to a rubber duck — often this unlocks it.

---

## 19. Code Review & Clean Code

> **75 skills** for giving excellent reviews and writing code that reviewers love.

1. Before committing, review your own diff as if you were reviewing someone else's code.
2. Read the PR description and linked issue before reading the code — context is everything.
3. Review the test changes first — they tell you what the code is supposed to do.
4. Comment on the behavior, not the person — "this function does X" not "you did X wrong".
5. Distinguish required changes from suggestions — use `nit:` prefix for style preferences.
6. Ask clarifying questions rather than making accusations — "could this cause X?" not "this causes X".
7. Approve what is good — good code review includes praise, not only criticism.
8. Request changes for correctness issues; leave suggestions for style preferences.
9. Limit review sessions to < 400 lines — beyond that, quality degrades rapidly.
10. Break large PRs into smaller, reviewable chunks — enforce this at the PR creation stage.
11. Review for security implications — every PR that handles user input is a security review.
12. Review for edge cases the author may not have considered.
13. Check that error paths are tested, not just the happy path.
14. Verify that new code is covered by tests — use the coverage diff.
15. Check for missing validation at trust boundaries.
16. Verify that secrets/credentials are not exposed in code, logs, or test fixtures.
17. Check that database queries use parameterized inputs.
18. Verify that new endpoints have authentication and authorization.
19. Look for N+1 query patterns introduced by ORM usage.
20. Check that new indexes are added for new query patterns.
21. Verify that migrations are backward-compatible and reversible.
22. Check that new dependencies are necessary and have acceptable licenses.
23. Verify dependency versions are pinned and don't introduce known vulnerabilities.
24. Check that configuration changes have documentation and default values.
25. Verify that deprecation notices are added for removed or changed public APIs.
26. Use the Boy Scout Rule: leave the code cleaner than you found it.
27. Avoid "works on my machine" — code must work in CI and on all team members' machines.
28. Avoid dead code — delete unused functions, variables, and imports.
29. Avoid commented-out code in commits — use `git revert` to recover deleted code.
30. Avoid over-engineering — implement the simplest thing that could possibly work.
31. Avoid premature abstraction — abstract when the third instance of duplication appears.
32. Avoid god objects/functions — no function over 50 lines, no class with more than 10 methods.
33. Avoid deep inheritance hierarchies — prefer composition.
34. Avoid global variables and mutable singletons — they make testing impossible.
35. Avoid `else` after `return` — it adds noise without adding clarity.
36. Avoid negative conditions — `if isActive` is clearer than `if !isInactive`.
37. Avoid double negatives — `if !notFound` is a bug waiting to happen.
38. Use consistent naming conventions — enforce with a linter rather than review comments.
39. Avoid abbreviations in names — `userID` not `uid`, `errorMessage` not `errMsg`.
40. Use precise domain language — use the same terms as the product and domain experts.
41. Avoid misleading names — a function called `getUser` should only get, not update.
42. Avoid temporal coupling — functions should not depend on being called in a specific order.
43. Avoid hidden dependencies between modules — make all dependencies explicit.
44. Avoid side effects in functions that look like pure queries.
45. Avoid overly long parameter lists — use a parameter object or builder instead.
46. Avoid boolean parameters — they make call sites unreadable (`createUser(true, false)`).
47. Avoid returning null/nil where an empty collection is more appropriate.
48. Use meaningful return types — `(User, error)` is clearer than `(interface{}, error)`.
49. Document public APIs with complete, correct examples.
50. Document non-obvious algorithms with references to the source (paper, article).
51. Document performance characteristics for operations that may surprise users.
52. Document thread safety guarantees for all public types and functions.
53. Write self-documenting code — a comment saying what the code does is a smell.
54. Comment the WHY, not the WHAT — "we retry 3 times to handle transient S3 errors" is valuable.
55. Keep comments up-to-date with code changes — stale comments are worse than no comments.
56. Use TODO, FIXME, HACK, NOTE prefixes in comments for discoverability.
57. Use `godoc` / JSDoc / pydoc formatting for all public symbol documentation.
58. Use `example_test.go` (Go) or `doctest` (Python) for executable documentation examples.
59. Review for testability — code that's hard to test is hard to maintain.
60. Review for observability — does new code produce useful logs, metrics, and traces?
61. Review for operability — can this be deployed safely? Can it be rolled back?
62. Review for configurability — are timeouts, limits, and feature flags externalized?
63. Review for scalability — will this work at 10x the current load?
64. Review for backward compatibility — does this break existing clients?
65. Approve in small batches — merge frequently and keep the main branch releasable.
66. Use async code review tools (GitHub PR reviews) over synchronous meetings.
67. Respond to review comments within 1 business day.
68. Re-request review after addressing all comments — don't merge without re-approval.
69. Use draft PRs to share early work and get structural feedback before a full review.
70. Use `git log --since` to review code written by departing team members.
71. Use automated code review tools (CodeClimate, SonarQube) to catch mechanical issues.
72. Reserve human review bandwidth for design, logic, and security — not style.
73. Conduct architecture reviews for changes to core abstractions or cross-cutting concerns.
74. Document review decisions in the PR — future maintainers will thank you.
75. Celebrate good code in reviews — positive reinforcement builds a culture of quality.

---

## 20. System Design & AI/Claude Integration

> **75 skills** for designing large-scale systems and integrating AI/LLM capabilities effectively.

1. Always start system design with requirements: functional, non-functional, constraints, and assumptions.
2. Estimate scale: QPS, storage, bandwidth, and compute before choosing architecture.
3. Design the data model first — the database schema reveals the true domain.
4. Design for the 80% use case — over-engineering for edge cases causes premature complexity.
5. Use CAP theorem to make explicit consistency vs. availability trade-offs.
6. Choose CP (consistency + partition tolerance) for financial transactions.
7. Choose AP (availability + partition tolerance) for social feeds and caches.
8. Use eventual consistency for cross-region replication of non-critical data.
9. Use the 12-Factor App methodology for cloud-native application design.
10. Separate stateless computation from stateful storage — this enables horizontal scaling.
11. Use sharding (horizontal partitioning) for data that exceeds single-node capacity.
12. Use consistent hashing for shard routing to minimize resharding cost.
13. Use virtual nodes in consistent hashing rings for balanced load distribution.
14. Use a write-ahead log (WAL) for durability before acknowledging writes.
15. Design read replicas for read-heavy workloads to scale read throughput.
16. Use materialized views / precomputed aggregations for expensive read queries.
17. Design URL shorteners: base62 encoding of auto-incremented IDs is the idiomatic solution.
18. Design rate limiters: use token bucket (steady flow) or leaky bucket (burst smoothing).
19. Design notification systems: fan-out-on-write for small follower counts, fan-out-on-read for large.
20. Design search systems: inverted indexes, TF-IDF scoring, BM25, and vector search.
21. Design distributed caches: write-through vs. write-behind, cache-aside vs. read-through.
22. Use content-addressed storage (CAS) for deduplication in storage systems.
23. Use bloom filters at cache/storage layers to eliminate unnecessary disk lookups.
24. Use consistent snapshots + incremental backups for efficient disaster recovery.
25. Design for multi-region active/active with conflict resolution strategies.
26. Use CRDTs (Conflict-free Replicated Data Types) for eventually consistent collaborative data.
27. Use distributed locks (Redlock, etcd, Zookeeper) for cross-instance coordination.
28. Design leaderboards: sorted sets in Redis with `ZADD`/`ZRANK` are the idiomatic solution.
29. Design job schedulers: use a distributed cron with at-least-once delivery and idempotent jobs.
30. Design file storage: store files in S3, metadata in a database, with pre-signed URLs for access.
31. Design video transcoding: async pipeline with queues, workers, and progress tracking.
32. Use LLMs (Claude) for: text generation, classification, extraction, summarization, and code generation.
33. Use Claude as a coding agent — provide system context, file content, and explicit instructions.
34. Use the `tools` parameter (Claude function calling) to give Claude structured tool access.
35. Design tool schemas precisely — clear names, descriptions, and parameter types improve LLM accuracy.
36. Use `system` prompt for persistent agent instructions; `user` messages for per-task context.
37. Provide relevant file content and codebase context in the user message to Claude.
38. Use chain-of-thought prompting for complex multi-step reasoning tasks.
39. Use `<thinking>` XML tags in prompts to elicit step-by-step reasoning before answers.
40. Use few-shot examples in prompts to calibrate Claude's output format and style.
41. Use structured output (JSON mode) for machine-parseable Claude responses.
42. Validate LLM output against a schema — never trust unvalidated AI-generated content.
43. Use prompt caching (Claude's cache_control) to reduce latency and cost on long system prompts.
44. Use `extended thinking` (claude-3-7-sonnet) for hard reasoning and complex coding tasks.
45. Use streaming responses for real-time display of long LLM outputs.
46. Implement retry logic for transient LLM API errors (rate limits, timeouts).
47. Use token counting (`anthropic.count_tokens`) to stay within context window limits.
48. Design RAG (Retrieval-Augmented Generation) pipelines for knowledge-grounded LLM responses.
49. Use vector databases (Pinecone, Weaviate, pgvector) for semantic search in RAG.
50. Use chunking with overlap for long document embedding in RAG pipelines.
51. Use reranking (Cohere Rerank, cross-encoders) to improve retrieval quality.
52. Use hybrid search (BM25 + vector) for robust retrieval across diverse queries.
53. Evaluate RAG quality with RAGAS — measure faithfulness, answer relevance, and context relevance.
54. Design agentic loops with clear termination conditions — avoid infinite LLM loops.
55. Use deterministic tools (code execution, database queries) to ground LLM reasoning in facts.
56. Implement human-in-the-loop checkpoints for high-stakes agentic actions.
57. Log all LLM inputs and outputs for debugging, auditing, and fine-tuning.
58. Use `anthropic-beta: interleaved-thinking` for thinking + tool use together.
59. Use multi-agent architectures (orchestrator + specialist agents) for complex pipelines.
60. Design agent memory: working memory (context window), episodic memory (vector DB), semantic memory (knowledge base).
61. Use the `computer_use` tool for agents that need to interact with GUIs.
62. Use `bash` tool for agents that need to run shell commands.
63. Use `text_editor` tool for agents that need to read and modify files.
64. Implement rate limiting on LLM API calls — model API limits are real production constraints.
65. Use exponential backoff with jitter for LLM API rate limit retries.
66. Monitor LLM cost per request and per user — costs can scale unexpectedly.
67. Use caching of LLM responses for identical prompts to reduce cost and latency.
68. Use embedding caching to avoid re-embedding the same content.
69. Evaluate LLM outputs with automated evals (LLM-as-judge, deterministic checks).
70. Use red-teaming and adversarial prompts to test LLM application robustness.
71. Implement input and output content filtering for safety in production LLM apps.
72. Use Claude's `max_tokens` parameter to bound output length and cost.
73. Use `temperature=0` for deterministic tasks (code generation, structured extraction).
74. Use `temperature=0.7-1.0` for creative tasks where variation is desirable.
75. Design feedback loops — collect user ratings and use them to improve prompts and models.

---

## Cursor Cloud Agent Notes

- Cloud agents run in ephemeral Ubuntu environments — always install missing tools before using them.
- Use `sudo apt-get install -y <package>` for system packages.
- Use `go install <tool>@latest` for Go tools.
- Commit, push, and verify CI before considering a task complete.
- Always run `git add`, `git commit`, and `git push` — do not leave work uncommitted.
- Use `gh run list` and `gh run view --log-failed` to inspect CI results.
- Prefer `gofmt + go vet + golangci-lint` as the standard Go quality gate.
- This repository is the **GitKraken CLI** — changes should maintain CLI UX and MCP server compatibility.
- Branch: always work on `cursor/claude-agent-skills-8494` unless instructed otherwise.

---

*AGENTS.md · 1500 skills · 20 categories · 75 skills each · optimized for Claude coding agents*
