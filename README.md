# Medieval Destiny — resource pack and MMOItems v1.4.2

Release files for the Paper 1.21.11 server. The pack and MMOItems files must be installed as a pair.

## Downloads

- [Resource pack v1.4.2](https://github.com/Alexgmzz/v1.0.1/raw/refs/heads/main/medieval-destiny-resource-pack-v1.4.2.zip)
- [MMOItems definitions v1.4.0](https://github.com/Alexgmzz/v1.0.1/raw/refs/heads/main/MMOItems-MedievalDestiny-v1.4.0.zip)
- [Runic stations plugin v1.0.9](https://github.com/Alexgmzz/v1.0.1/raw/refs/heads/main/MedievalDestinyRunes-1.0.9-independent-stations.jar)

The v1.4.2 resource pack is based on v1.4.1 and removes the OptiFine CEM override `assets/minecraft/optifine/cem/banner.jem`. The server pack was reintroducing this custom banner model even when a client used the banner-compatible Dark Fantasy variant without it; this is the identified cause of placed banners disappearing. All other archive entries are byte-for-byte unchanged from v1.4.1, and the deprecated `supported_formats` key remains absent. The MMOItems definitions remain v1.4.0 because their model identifiers match the unchanged model files.

The pack includes the full existing armory: custom models for 24 weapons, 24 armor pieces across six sets, 120 runes, the Vespera staff, and the runic stations. MMOItems definitions use namespaced item models so the client’s other packs do not replace these item visuals. Armor also selects a matching wearable texture set.

## Server resource-pack settings

For `server.properties`:

```properties
resource-pack=https://raw.githubusercontent.com/Alexgmzz/v1.0.1/main/medieval-destiny-resource-pack-v1.4.2.zip
resource-pack-sha1=ddb12d154bd63a4561e91b50086ab45f256da02e
```

The hash is SHA-1 of the exact v1.4.2 archive. Keep `require-resource-pack` unchanged unless you want to force downloads. After changing `server.properties`, restart the server; do not use `/reload` for this setting. A running server will continue using its current settings until its next restart.

## MMOItems installation

Back up `plugins/MMOItems/item/`, then replace its YAML files with the `item/` directory from the MMOItems archive. These definitions require an MMOItems 6.10.x build with the `model`, `equippable-slot`, and `equippable-model` stats (Minecraft 1.21.2+). Run `/mi reload` only after verifying the backup and pack are in place, then inspect the console for parse errors.

The inventory models are custom 3D item models. Worn armor uses Minecraft’s standard player armor geometry with six custom 1.21.4+ equipment textures; it does not add client mods or arbitrary mesh geometry to the player model.

The resource pack has passed JSON/reference checks. Final appearance and MMOItems runtime loading still need an in-game validation on the target server and client.

The station plugin v1.0.9 jar removes duplicate class entries that prevented Paper from remapping v1.0.8. The server should load it on its next startup; the running process is not hot-reloaded.
