# Medieval Destiny — resource pack and MMOItems v1.4.0

Release files for the Paper 1.21.11 server. The pack and MMOItems files must be installed as a pair.

## Downloads

- [Resource pack v1.4.0](https://github.com/Alexgmzz/v1.0.1/raw/refs/heads/main/medieval-destiny-resource-pack-v1.4.0.zip)
- [MMOItems definitions v1.4.0](https://github.com/Alexgmzz/v1.0.1/raw/refs/heads/main/MMOItems-MedievalDestiny-v1.4.0.zip)
- [Runic stations plugin v1.0.8](https://github.com/Alexgmzz/v1.0.1/raw/refs/heads/main/MedievalDestinyRunes-1.0.8-independent-stations.jar)

The pack includes the full existing armory: custom models for 24 weapons, 24 armor pieces across six sets, 120 runes, the Vespera staff, and the runic stations. MMOItems definitions use namespaced item models so the client’s other packs do not replace these item visuals. Armor also selects a matching wearable texture set.

## Server resource-pack settings

For `server.properties`:

```properties
resource-pack=https://raw.githubusercontent.com/Alexgmzz/v1.0.1/main/medieval-destiny-resource-pack-v1.4.0.zip
resource-pack-sha1=4849528a46e279627db60a80ba621df7d52088f3
```

The hash is SHA-1 of the exact v1.4.0 archive. Keep `require-resource-pack` unchanged unless you want to force downloads. After changing `server.properties`, restart the server; do not use `/reload` for this setting.

## MMOItems installation

Back up `plugins/MMOItems/item/`, then replace its YAML files with the `item/` directory from the MMOItems archive. These definitions require an MMOItems 6.10.x build with the `model`, `equippable-slot`, and `equippable-model` stats (Minecraft 1.21.2+). Run `/mi reload` only after verifying the backup and pack are in place, then inspect the console for parse errors.

The inventory models are custom 3D item models. Worn armor uses Minecraft’s standard player armor geometry with six custom 1.21.4+ equipment textures; it does not add client mods or arbitrary mesh geometry to the player model.

The resource pack has passed JSON/reference checks. Final appearance and MMOItems runtime loading still need an in-game validation on the target server and client.

The station plugin jar has compiled and passed archive checks; its behavior still needs a server smoke test before replacing the installed jar.
