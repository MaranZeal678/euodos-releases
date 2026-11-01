<img src="icon.png" width="96" alt="Keystone app icon: an arch whose crown stone is gold">

# Keystone for Mac

Keystone is an AI operating system for nonprofit homeownership, built for Habitat for Humanity of Orange County's **Keys to 100** goal at the UCI Merage Center for Real Estate Impact Lab. It finds buildable faith-owned land with a computer-vision model, designs mortgages families can keep through ten years of shocks, sizes the capital gap on real lending data, and runs a team of AI agents that improve only when a deterministic gate confirms they got better.

This repository hosts the Mac app downloads only.

## Download

**[Download the latest release](https://github.com/MaranZeal678/keystone-releases/releases/latest)** and pick `Keystone-<version>.dmg`.

Requires a Mac with Apple Silicon (M1 or later) and macOS 13 or newer.

## Install

1. Open the `.dmg` and drag **Keystone** into **Applications**.
2. The app is not yet signed with an Apple Developer ID, so macOS blocks the first launch. Open Keystone once, then go to **System Settings → Privacy & Security** and click **Open Anyway** next to the Keystone message. Or run this in Terminal:
   ```
   xattr -dr com.apple.quarantine /Applications/Keystone.app
   ```
3. Keystone opens in its own window. Use the **Go** menu to switch between the dashboard and the mission-control demo.

Your runs, skills and agent lessons are saved in `~/Library/Application Support/Keystone`.

## Verify the download

Each release includes a `.sha256` file. In Terminal, in the folder you downloaded to:

```
shasum -a 256 -c Keystone-<version>.dmg.sha256
```

## What runs where

Everything runs on your Mac: the dashboard, the 3D demo, the mortgage designer, the agent hierarchy and its MCP server, and the sandbox that runs agent-written analysis code. The only things fetched online are the map's street tiles; offline, the map background is blank.

- Agents use an offline scripted policy by default. To run them on Claude, start the app from Terminal with your key set: `ANTHROPIC_API_KEY=... /Applications/Keystone.app/Contents/MacOS/Keystone`
- The desktop build leaves out live satellite re-scans of parcels (they need PyTorch); site checks use the stored CNN scans and say so.
- Synthetic example families appear throughout; their incomes are sampled from public 2024 HMDA data. Hazard rates are labelled planning assumptions.
