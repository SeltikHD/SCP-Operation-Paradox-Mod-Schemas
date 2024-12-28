# JSON Schemas for SCP: Operation Paradox Mods

This repository contains JSON Schemas designed for the SCP: Operation Paradox game modding framework. These schemas ensure that mod configuration files are correctly structured and follow the required specifications for seamless integration with the game.

## Purpose

JSON Schemas provide a structured and standardized way to validate JSON files. By using these schemas, mod developers can:

- Ensure their mod configuration files adhere to the expected format.
- Catch errors early during development by validating JSON files against the schema.
- Maintain compatibility with future updates to the game by adapting to updated schemas.

## Schema Overview

### Example: `pack.json`

This schema validates the `pack.json` file, which provides metadata about a mod pack.

#### Expected Fields

| Field          | Type   | Description                                                         |
| -------------- | ------ | ------------------------------------------------------------------- |
| `title`        | string | The title of the mod pack.                                          |
| `description`  | string | A brief description of the mod pack.                                |
| `version`      | string | The version of the mod pack in semantic versioning (e.g., `1.0.0`). |
| `game-version` | string | The compatible game version in semantic versioning (e.g., `1.0.0`). |

#### Validation Rules

- All fields are required.
- `version` and `game-version` must follow the semantic versioning format (`major.minor.patch`).

#### Example `pack.json`

```json
{
    "$schema": "https://raw.githubusercontent.com/SeltikHD/SCP-Operation-Paradox-Mod-Schemas/refs/heads/master/pack.schema.json",
    "title": "Default",
    "description": "These are the game's default assets and actions",
    "version": "0.0.1",
    "game-version": "0.0.1"
}
```

#### Schema

The schema for `pack.json` is available [here](https://github.com/SeltikHD/SCP-Operation-Paradox-Mod-Schemas/blob/master/pack.schema.json). Each schema includes a `$id` field to standardize its URL. For example:

```json
{
    "$id": "https://raw.githubusercontent.com/SeltikHD/SCP-Operation-Paradox-Mod-Schemas/refs/heads/master/pack.schema.json"
}
```

## How to Use

1. Clone this repository:

   ```bash
   git clone https://github.com/SeltikHD/SCP-Operation-Paradox-Mod-Schemas.git
   ```

2. Include the appropriate schema file in your development workflow.
3. Use the `$schema` keyword in your JSON files to reference the schema URL. For example:

   ```json
   {
       "$schema": "https://raw.githubusercontent.com/SeltikHD/SCP-Operation-Paradox-Mod-Schemas/refs/heads/master/pack.schema.json",
       "title": "My Mod",
       "description": "A custom mod for SCP: Operation Paradox",
       "version": "1.0.0",
       "game-version": "1.0.0"
   }
   ```

4. Validate your JSON files using tools like [ajv-cli](https://github.com/ajv-validator/ajv-cli) or a JSON Schema validator plugin for your editor.

   Example with `ajv-cli`:

   ```bash
   ajv validate -s schemas/pack.schema.json -d mods/your-mod/pack.json
   ```

## License

This repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
