# Mobile Dev Agent CLI Cheatsheet

Use from repo root after build:
- npm install
- npm run build
- node dist/src/bin/mobile-dev-agent.js <command> ...

Common commands

- doctor
  - node dist/src/bin/mobile-dev-agent.js doctor --json

- list devices
  - node dist/src/bin/mobile-dev-agent.js devices list --platform ios
  - node dist/src/bin/mobile-dev-agent.js devices list --platform android

- boot device
  - node dist/src/bin/mobile-dev-agent.js device boot --name "iPhone 17 Pro"

- build iOS app (simulator)
  - node dist/src/bin/mobile-dev-agent.js build-ios --project path/to/App.xcodeproj --scheme App

- install app
  - node dist/src/bin/mobile-dev-agent.js app install --app /path/to/App.app --name "iPhone 17 Pro" --boot

- run Maestro flows (dir or file)
  - node dist/src/bin/mobile-dev-agent.js test --flow maestro/flows --name "iPhone 17 Pro" --boot --json
  - node dist/src/bin/mobile-dev-agent.js test --flow flows/login.yaml --format junit --output /tmp/maestro-report.xml

- run ad-hoc flow from stdin
  - node dist/src/bin/mobile-dev-agent.js flow run --platform ios --name "iPhone 17 Pro" --app-id com.example.app <<'YAML'
    - launchApp
    - tapOn: "Sign in"
    - assertVisible: "Welcome"
    YAML

- screenshot
  - node dist/src/bin/mobile-dev-agent.js device screenshot --name "iPhone 17 Pro" --output /tmp/sim.png
