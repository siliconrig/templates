# fbay-templates

CI/CD templates for [flashbay](https://flashbay.dev) hardware-in-the-loop testing.

## GitLab CI

Include the template in your `.gitlab-ci.yml`:

```yaml
include:
  - remote: 'https://raw.githubusercontent.com/flashbay-dev/templates/main/gitlab-ci.yml'

hil-test:
  extends: .flashbay-hil
  variables:
    FLASHBAY_BOARD: esp32-s3
    FLASHBAY_FIRMWARE: build/firmware.bin
  script:
    - pytest tests/hil/ -v
```

### Available templates

| Template | Description |
|---|---|
| `.flashbay-install` | Installs `fbay-cli` binary |
| `.flashbay-hil` | Full HIL workflow — session, flash, serial capture, cleanup |
| `.flashbay-flash` | Flash-only workflow — session, flash, cleanup |

### Variables

| Variable | Description |
|---|---|
| `FLASHBAY_API_KEY` | API key (set in CI/CD settings, masked) |
| `FLASHBAY_BOARD` | Board type (e.g., `esp32-s3`) |
| `FLASHBAY_FIRMWARE` | Path to firmware binary |
| `FLASHBAY_SERIAL_TIMEOUT` | Serial capture duration (default: `30s`) |
