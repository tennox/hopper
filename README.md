# High-level Goals

- modrinth mod searching
- modrinth mod installation
- curseforge api too?
- per-instance mod management
- mod updating
- fish autocomplete
- bash autocomplete
- zsh autocomplete
- nushell autocomplete
- manpage

Long-term/host-dependent:
- conflict resolution
- dependency resolution
- shaderpack and resource pack management

# File Architecture

```bash
- .config/hopper/config.toml # Main config file
- .local/share/multimc/instances/*/.minecraft/Hopfile.toml # Multimc
- .minecraft/Hopfile.toml # Official launcher
- .var/app/com.mojang.Minecraft/.minecraft/Hopfile.toml # Flatpak version
- .cache/hopper/ # Mod cache
|              - hopper.lock # Lock file
|              - mod1.jar # Mods
|              - mod2.jar
+------------- - ...
```

# Usage (Planned)

Create `Hopfile.toml` in your instance directory:
```
hopper init
```

Add mods:
```
hopper add iris
hopper add sodium
hopper add phosphor
```

Check for mod updates:
```
hopper update
```

# Docs (Planned)

## `hopper init`

```
hopper init < --dir=./path/to/instance >
```

Inits in current directory if `dir` is left out, otherwise inits in given dir.

## `hopper update`

```
hopper update < --mc-version=1.17 >
```

Updates all installed mods of a specific version, or a version set in the config.

## `hopper add`

```
$ hopper add sodium --mc-version 1.17
4 Indium 1.0.0+mc1.17.1 [1.17.1] (21557 downloads)
    Sodium addon providing support for the Fabric Rendering API, based on Indigo
3 Reese's Sodium Options 1.2.1 [1.16.5] (548 downloads)
    Alternative Options Menu for Sodium
2 Sodium Extra mc1.17.1-0.3.6 [1.17.1] (16387 downloads)
    Features that shouldn't be in Sodium.
1 Sodium mc1.17.1-0.3.2 [1.17.1] (962361 downloads)
    Modern rendering engine and client-side optimization mod for Minecraft
:: Select a mod
:: ...
```

- configurable mod search results like [Starship](https://starship.rs)
- pad mod indices based on largest number
- option in config to reverse sorting order
- add parameter to restrict target Minecraft version
- manually pick out Minecraft version
- square colored creeper face progress indicator (from top-left clockwise spiral in)

## `hopper get`

Just like `hopper add` but simply downloads a mod jar to the current directory.
