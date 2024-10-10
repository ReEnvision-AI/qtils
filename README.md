# qtils

This is a port of the original [qtils](https://github.com/qdrvm/qtils) but has been changed to use [vcpkg](https://learn.microsoft.com/en-us/vcpkg/) instead of hunter.

## Requirements
Cmake and vcpkg are already setup on your machine. If not, please do that first
*CMake -- https://cmake.org/download/
*vcpkg -- https://learn.microsoft.com/en-us/vcpkg/get_started/get-started?pivots=shell-powershell

## Setup
1 Download source
```bash
gh repo clone ReEnvision-AI/qtils
cd qtils
```
2 Create `CMakeUserPresets.json` and the contents should be:
```json
{
    "version": 2,
    "configurePresets": [
      {
        "name": "default",
        "inherits": "vcpkg",
        "environment": {
          "VCPKG_ROOT": "C:/Path/to/vcpkg"
        }
      }
    ]
  }
```

Make sure to change `C:/Path/to/vcpkg` to point to wherever your vcpkg install happens to be.

3 Configure the build using CMake
```bash
cmake --preset=default
```

4 Build the project
```bash
cmake --build build
```