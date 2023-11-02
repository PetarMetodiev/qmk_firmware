# Aurora Lily58's Default Keymap

_This keymap is a copy of the [Lily58 default keymap](https://github.com/qmk/qmk_firmware/tree/master/keyboards/lily58/keymaps/default), with slight modifications._

# A simple default keymap for the Aurora Lily58

Keymaps in general are quite personal, so it is difficult to come up with a default that will suit every user. We hope this keymap serves as a good starting point for your own - although it should be fairly usable out-of-the-box.

## Where is the keymap.c?

The keymap.c file is not published to the repository. It is generated from `keymap.json` by the build system.

This avoids duplicating information and allow users to edit their keymap from the QMK Configurator web interface.

## How do I edit and update the keymap?

Current crappy workflow:

1. Load `lily58/keymaps/kitty58/keymap.json` in the qmk configurator.
2. Modify whatever is needed.
3. Download the newly generated `json` file in `lily58/keymaps/kitty58.json` - this is just for reference(not really needed for the functionality of the whole thing).
4. Add the changes from `kitty58.json` to `lily58/keymaps/kitty58/keymap.json`.
5. Compile.

**_NOTE_**: No need to keep in sync both keymap.c and `keymap.json`.
**_NOTE_**: (unrelated) to see current qmk config run `qmk config` - it should list all aliases for kb and km. Current working config:

```sh
find.keymap=default
mass_compile.keymap=default
user.keyboard=splitkb/aurora/lily58/rev1
user.keymap=kitty58
```

_**Note:** At the time of writing (the 24th of October 2022), not every feature used in the default keymap is supported by the QMK Configurator. You cannot yet upload the default `keymap.json` due to a file format mismatch - use the "Load Default" button to load the default keymap instead. Additionally, custom configuration options are still being worked on: if your keymap depends on them, please compile your firmware offline for now._

## I want to do more than the JSON format supports!

While the `json` format is easy to use, it does lack certain functionality - most notably custom OLED or encoder behaviour.

To add this, you need to convert it to the `c` format. Do keep in mind that this is generally a one-way operation.

First, from the root of your qmk repo, move to your keymap folder

```bash
cd ./keymaps/splitkb/aurora/lily58/my_personal_keymap
```

Next, convert your `keymap.json` to a `keymap.c`

```bash
qmk json2c -o keymap.c keymap.json
```

You can add custom C code to the newly generated `keymap.c` file. Do note that you have to use **either** a C file **or** a JSON file - you cannot do both!  
**If a JSON file is present, the C file is ignored.**
