# dps-weaponsounds

Custom weapon sounds for FiveM. This repo holds a README and a licence only. There is no code and
no sound files in it.

## Status

Unfinished: no code. The repo has never held a manifest, a config or any sound files. Not running
on DelPerroSands.

## What it is for

The plan was to swap the stock GTA gun sounds for better ones, with a config to pick which
weapons change and how loud each group is. The earlier README described that plan as if it were
built: a `config.lua`, three exports and `.awc` files under `stream/sfx/`. None of those files
were ever added here. That README is still in the git history.

## On its own, and with other scripts

**On its own.** Nothing to install. There is no `fxmanifest.lua`, so FiveM will not start it.

**With other scripts.** No links. Nothing here calls another resource.

## If the work is picked up again

A weapon sound pack needs these things in the repo:

1. An `fxmanifest.lua` with the audio `data_file` lines.
2. The `.awc` sound files and the `.rel` audio config files.
3. A note on where each sound came from, with the maker's permission to share it.

On DelPerroSands, `dps-hvsounds` already shows the working layout for a
merged audio pack. It lives on the server and has no repo.

## Recent changes

- **12 November 2026.** README: status, what it is for, how it works alone and with paid scripts, other DPS scripts. Removed the text that described code which is not in the repo.
- **30 December 2025.** Repo created with a README and the licence.

## License

GNU General Public License v3.0. See [LICENSE](LICENSE).

## Credits

- FiveM community for documentation and support
- OpenIV team for audio conversion tools
- All contributors and testers

## Author

Made by [DaemonAlex](https://github.com/DaemonAlex) for DelPerroSands.

## Other DPS scripts

All of these are made for DelPerroSands and run together on one Qbox server. Each one works on
its own. The ones marked "pairs with" do more when both are running.

| Script | What it does |
|---|---|
| [dps-inventory](https://github.com/DaemonAlex/dps-inventory) | The inventory: ox_inventory with equipment slots, backpacks, armour plates and a self status panel, in the DelPerroSands colours. |
| [dps-medical](https://github.com/DaemonAlex/dps-medical) | Patient records, illness and diagnostic tests. A companion to wasabi_ambulance. Pairs with dps-inventory: symptoms and diagnoses show on the status panel. |
| [dps-insurance](https://github.com/DaemonAlex/dps-insurance) | Ties m-Insurance into the MDT, impound, hospital and medical chart. Pairs with dps-medical. |
| [dps-studio](https://github.com/DaemonAlex/dps-studio) | Build rooms, doors and portals in game from one panel (`/studio`), with owners and managers so staff do not have to support them. |
| [dps-shops](https://github.com/DaemonAlex/dps-shops) | Shop clerks who greet and react to a robbery, then player-owned shops. |
| [dps-fleet](https://github.com/DaemonAlex/dps-fleet) | Vehicle browser and workshop on one panel: extras, liveries and mods for emergency vehicles. |
| [dps-parking](https://github.com/DaemonAlex/dps-parking) | Parking with valet, impound, violations and reserved spots. |
| [dps-vehiclepersistence](https://github.com/DaemonAlex/dps-vehiclepersistence) | Vehicles stay where they were parked. Pairs with dps-parking. |
| [dps-towjob](https://github.com/DaemonAlex/dps-towjob) | Queue-based tow job with jg-mechanic integration. |
| [dps-services](https://github.com/DaemonAlex/dps-services) | Request a tow and follow it live on the lb-phone and lb-tablet. Pairs with dps-towjob. |
| [dps-autoshops](https://github.com/DaemonAlex/dps-autoshops) | Self-service repair shops when no mechanic is on duty. |
| [dps-cityworker](https://github.com/DaemonAlex/dps-cityworker) | City infrastructure job and career. |
| [dps-ainpcs](https://github.com/DaemonAlex/dps-ainpcs) | NPCs you can talk to, with trust, quests and intel. |
| [dps-badpeds](https://github.com/DaemonAlex/dps-badpeds) | Police interaction with NPCs: stops, arrests, intel and jail records. |
| [dps-gangwars](https://github.com/DaemonAlex/dps-gangwars) | Ambient gang NPCs, territory population and war reinforcements. |
| [dps-rotations](https://github.com/DaemonAlex/dps-rotations) | Moves dealers, harvests and other spots on a fixed schedule. |
| [dps-trains](https://github.com/DaemonAlex/dps-trains) | The train system. Pairs with dps-trains-stock, dps-traintools and dps-transitapp. |
| [dps-transitapp](https://github.com/DaemonAlex/dps-transitapp) | Live train arrival boards on the lb-phone. |
| [dps-faceplant](https://github.com/DaemonAlex/dps-faceplant) | City help, reports and staff tools on the lb-phone and lb-tablet. |
| [dps-chat](https://github.com/DaemonAlex/dps-chat) | A command box for voice-only servers. No chat feed. |
| [dps-filmmode](https://github.com/DaemonAlex/dps-filmmode) | One key hides every HUD layer and gives a smooth free camera for recording. |
