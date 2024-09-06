# Temporary Custom OPA Build

## Overview
This repository hosts a custom build of the Open Policy Agent (OPA) executable. This build is a temporary solution to address a specific bug in the official OPA release.

**Important:** This custom build is a short-term fix and will no longer be necessary after the bug is resolved in the official OPA release, expected next month.

## Purpose
The custom build fixes an issue related to big numbers evaluation in the WebAssembly (Wasm) build of OPA.

## Usage
To use this custom OPA build, follow the instructions below to replace the OPA binary on your local machine.

### macOS

1. **Download the custom OPA binary:**
    ```bash
    curl -L -o opa.new https://raw.githubusercontent.com/Ptroger/opa-bugfix-build/main/opa
    ```

2. **Make the new binary executable:**
    ```bash
    chmod +x opa.new
    ```

3. **Check if OPA is already installed and replace it:**
    ```bash
    existing_opa=$(which opa)
    if [ -n "$existing_opa" ]; then
      echo "Replacing existing OPA at $existing_opa"
      sudo mv opa.new "$existing_opa"
    else
      echo "No existing OPA found. Installing to /usr/local/bin"
      sudo mv opa.new /usr/local/bin/opa
    fi
    ```

4. **Verify the installation:**
    ```bash
    opa version
    ```

This script will:

- Replace the existing OPA binary if one is found in your PATH.
- Install the new binary to `/usr/local/bin` if no existing OPA is found.

## Reverting to Official OPA
Once the bug is fixed in the official OPA release, you should revert to using the official build. To do this, simply follow the installation instructions on the [official OPA documentation](https://www.openpolicyagent.org/docs/latest/#installation).

## Important Notes
- This custom build should only be used as a temporary solution.
- Keep an eye on the official OPA releases and update to the official version as soon as the fix is available.
