# WAVS Taskfiles

Common Taskfile tasks for WAVS (WASI AVS) projects. These taskfiles provide reusable automation for building, testing, deploying, and managing WAVS infrastructure.

## Overview

This repository contains shared Taskfile configurations that can be used across multiple WAVS projects to standardize development workflows.

## Available Taskfiles

### build.yml
Build tasks for Solidity contracts and WASI components.

**Tasks:**
- `build:all` - Build everything (Solidity + WASI)
- `build:forge` - Build Solidity contracts only
- `build:wasi` - Build WASI components (all or specific)

### docker.yml
Docker-related automation tasks.

### forge.yml
Foundry/Forge testing and deployment tasks.

**Tasks:**
- Testing tasks with various verbosity levels
- Coverage reporting
- Contract deployment and verification

### operator.yml
Operator registration and management tasks.

**Tasks:**
- `operator:register` - Register operator with WAVS Service Manager
- `operator:update-signing-key` - Update operator signing key
- `operator:verify` - Verify operator registration status

### rewards.yml
Rewards distribution and claiming tasks.

### services.yml
Local development service management.

**Tasks:**
- `services:start-all` - Start all local services (anvil, IPFS, WARG, Jaeger, prometheus)
- `services:stop-all` - Stop all local services

### wasi.yml
WASI component execution, validation, and registry management.

**Tasks:**
- `wasi:exec` - Execute WASI component locally
- `wasi:exec-fixed` - Execute with fixed input (for Go/TS components)
- `wasi:validate` - Validate component against best practices
- `wasi:upload-to-registry` - Upload component to WASI registry

## Usage

### Remote Taskfiles (via GitHub)

Once this repo is pushed to GitHub, you can reference these taskfiles remotely:

```yaml
# Taskfile.yml
version: "3"

experiments:
  - remote-taskfiles

includes:
  build:
    taskfile: https://raw.githubusercontent.com/Lay3rLabs/wavs-taskfiles/main/build.yml
  docker:
    taskfile: https://raw.githubusercontent.com/Lay3rLabs/wavs-taskfiles/main/docker.yml
  eas:
    taskfile: https://raw.githubusercontent.com/Lay3rLabs/wavs-taskfiles/main/eas.yml
  forge:
    taskfile: https://raw.githubusercontent.com/Lay3rLabs/wavs-taskfiles/main/forge.yml
  operator:
    taskfile: https://raw.githubusercontent.com/Lay3rLabs/wavs-taskfiles/main/operator.yml
  rewards:
    taskfile: https://raw.githubusercontent.com/Lay3rLabs/wavs-taskfiles/main/rewards.yml
  services:
    taskfile: https://raw.githubusercontent.com/Lay3rLabs/wavs-taskfiles/main/services.yml
  wasi:
    taskfile: https://raw.githubusercontent.com/Lay3rLabs/wavs-taskfiles/main/wasi.yml
```

### Local Development (Before Push)

For local testing before pushing to GitHub:

```yaml
# Taskfile.yml
version: "3"

includes:
  build:
    taskfile: ../wavs-taskfiles/build.yml
  docker:
    taskfile: ../wavs-taskfiles/docker.yml
  eas:
    taskfile: ../wavs-taskfiles/eas.yml
  forge:
    taskfile: ../wavs-taskfiles/forge.yml
  operator:
    taskfile: ../wavs-taskfiles/operator.yml
  rewards:
    taskfile: ../wavs-taskfiles/rewards.yml
  services:
    taskfile: ../wavs-taskfiles/services.yml
  wasi:
    taskfile: ../wavs-taskfiles/wasi.yml
```

## Version Management

When using remote taskfiles, you can pin to specific versions for stability:

```yaml
build:
  taskfile: https://raw.githubusercontent.com/Lay3rLabs/wavs-taskfiles/v1.0.0/build.yml
```

## Projects Using This

- [TrustGraph](https://github.com/Lay3rLabs/TrustGraph)
- EN0VA

## Contributing

When adding or modifying taskfiles:

1. Ensure changes are backwards compatible
2. Test with all dependent projects
3. Update this README with any new tasks
4. Consider versioning for breaking changes

## License

MIT
