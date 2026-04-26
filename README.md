# dockerfile-agent

An intelligent Kiro CLI agent that auto-generates production-ready Dockerfiles by analyzing your codebase — no manual configuration needed.

---

## Purpose

Eliminate the manual effort of writing Dockerfiles. The agent inspects your project, detects its language and framework, and produces an optimized, secure Dockerfile with a matching `.dockerignore`.

---

## Solutions Offered

| Problem | Solution |
|---|---|
| Writing Dockerfiles from scratch | Auto-generates based on project files |
| Bloated images | Enforces minimal base images (`alpine`/`slim`) |
| Security risks from root containers | Always sets a non-root user |
| Slow builds | Applies multi-stage builds where beneficial |
| Missing `.dockerignore` | Auto-generates alongside the Dockerfile |

---

## Benefits

- **Zero config** — infers everything from your project files
- **Secure by default** — non-root user, minimal attack surface
- **Optimized images** — multi-stage builds, production-only dependencies
- **Multi-language support** — Node.js, Python, Go, Java, Rust, Ruby, and generic projects
- **Consistent output** — follows the same best-practice sequence every time

---

## How It Works

The agent runs 4 skills in sequence:

```
analyze_project → resolve_strategy → generate_dockerfile → generate_dockerignore
```

| Skill | What it does |
|---|---|
| `analyze_project` | Detects language, framework, and port in a single pass |
| `resolve_strategy` | Decides single-stage vs multi-stage build |
| `generate_dockerfile` | Writes the optimized Dockerfile with best practices applied |
| `generate_dockerignore` | Writes the `.dockerignore` |

---

## SOP — Standard Operating Procedure

### Prerequisites
- Kiro CLI installed
- Project directory accessible

### Steps

**1. Navigate to your project**
```bash
cd /path/to/your/project
```

**2. Start Kiro CLI**
```bash
kiro-cli
```

**3. Select the agent**

Type `/agent` and from the dropdown select `dockerfile-agent`

**4. Review generated files**
```
Dockerfile        ← production-ready, optimized
.dockerignore     ← auto-generated exclusions
```

**5. Build and verify**
```bash
docker build -t my-app .
docker run --rm my-app
```

### Expected Outputs

| File | Description |
|---|---|
| `Dockerfile` | Multi-stage, minimal, non-root, port-exposed |
| `.dockerignore` | Excludes dev files, caches, secrets |

### Supported Languages

| Indicator File | Detected Language | Default Port |
|---|---|---|
| `package.json` | Node.js | 3000 |
| `requirements.txt` / `pyproject.toml` | Python | 8000 |
| `go.mod` | Go | 8080 |
| `pom.xml` / `build.gradle` | Java | 8080 |
| `Cargo.toml` | Rust | 8080 |
| `Gemfile` | Ruby | 3000 |
| *(none matched)* | Generic | 3000 |

### Port Detection (priority order)
1. `.env.example` or `.env.sample` — `PORT=<number>`
2. `package.json` start script — `PORT=<number>` or `--port <number>`
3. Framework-specific default (see table above)
4. Fallback → `3000`

### Notes
- Default port is `3000` if none is detected
- Do not manually edit the Dockerfile before the agent finishes
- Re-run the agent after major dependency or framework changes
