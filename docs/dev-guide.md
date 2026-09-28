# ESPHome YAML Style & ID Conventions

## 1. ID Naming Taxonomy (`[type]_[hardware_group/source]_[sub-item]`)
Identifiers follow a hardware-first, subsystem-based `snake_case` hierarchy. This keeps IDs traceable directly to the physical PCB schematic rather than specific UI or abstraction layers.

- **Category Prefixes:** Use short 3 to 4 letter domain prefixes:
  - `bus_`: Communication interfaces (`bus_i2c`, `bus_spi`)
  - `disp_` / `touch_`: Screen and digitizer controllers (`disp_main`, `touch_main`)
  - `out_`: Raw GPIO/PWM/LEDC hardware outputs (`out_backlight`)
  - `light_`: User-facing Home Assistant light entities (`light_backlight`)
  - `sens_`: Sensor inputs (`sens_builtin_temp`, `sens_builtin_hum`)

- **Subsystem Hierarchy:** Group by physical component source before measurement type (e.g., `sens_builtin_temp` instead of `sens_temp_builtin`).

## 2. Block Structure Standard
Maintain a consistent field order across all YAML component definitions to ensure clean readability across large node configs:

```yaml
component_domain:
  - id: <domain_id>          # 1. Identifier always at top
    platform: <platform>     # 2. Driver platform
    name: <entity_name>      # 3. User-facing entity name (if applicable)
    # ...                    # 4. Hardware/pin configurations
    # ...                    # 5. Timing, behavior, & automations
```

# Git Tag Quick Reference

## 1. Versioning Logic (`MAJOR.MINOR.PATCH`)

According to semantic versioning rules and tag conventions. [^1]

- **`0.Y.Z` (Pre-1.0.0 / Dev)**: Public API is unstable.
  - PATCH (`0.y.Z`): Backwards-compatible bug fixes or doc updates only.
  - MINOR (`0.Y.0`): Breaking changes (secrets, schemas, directory structure) OR new features.
- **`X.Y.Z` (Production)**: Declares first stable release/schema.
  - PATCH (`x.y.Z`): Backwards-compatible fixes.
  - MINOR (`x.Y.0`): Backwards-compatible new features.
  - MAJOR (`X.0.0`): Breaking API/schema changes.

## 2. Standard Tag Command

```bash
git tag -a vX.Y.Z

```

## 3. Tag Message Template (`TAG_EDITMSG`)

```text
vX.Y.Z - <Short High-Level Milestone Summary>

- Key functional or structural change 1
- Key functional or structural change 2
- ...

NOTE: <Any critical deployment or hardware warnings>

```

---

# Footnotes
[^1]: [Semantic Versioning (SemVer 2.0.0)](https://semver.org/)
