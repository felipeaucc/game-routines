# FusionX 2.1.1 integration

This directory contains the tested Game Routines integration for [FusionX](https://github.com/sakasakiking/FusionX) 2.1.1.

The integration adds the optional embedded Game Routines controls directly to the FusionX game overview:

- `GameRoutines_Checklist`, shown in a **Checklists** tab
- `GameRoutines_StateToggle`, shown beside the game cover
- `GameRoutines_IncompleteIndicator`, shown over the cover when the game's overall counted routine state is incomplete

These controls are optional. Game Routines itself does not require FusionX or any other third-party theme.

Official FusionX does not currently include this integration. Upstream support has been proposed in [FusionX pull request #105](https://github.com/sakasakiking/FusionX/pull/105).

## Compatibility

These replacement files are intended for **FusionX 2.1.1 only**.

Do not copy them into another FusionX version unless that version has first been compared against this integration and confirmed compatible.

The integration modifies only:

- `Views/DetailsViewGameOverview.xaml`
- `Views/GridViewGameOverview.xaml`

The reference files were derived from the official FusionX 2.1.1 package.

The pristine files used as the comparison baseline have these SHA-256 hashes:

- `Views/DetailsViewGameOverview.xaml`: `9261DEBE98EB34AE8CDB48DE323457AA74D2A03DD90EA83E91CA636816E664DA`
- `Views/GridViewGameOverview.xaml`: `4679CB90EE4A8E620463C188AC5E7CDE70CD114976BC6AB3236D71AE2E5E0505`

[FusionX](https://github.com/sakasakiking/FusionX) is a third-party project. See [LICENSE.FusionX.txt](LICENSE.FusionX.txt) for its MIT license and attribution.

## Manual installation

Before starting, make sure Game Routines and FusionX 2.1.1 are already installed.

1. Close Playnite completely.

2. Open the FusionX theme folder:

   ```text
   %APPDATA%\Playnite\Themes\Desktop\FusionX_54244ec8-29ec-418e-bce7-415250c8d67b
   ```

3. Open its `Views` folder.

4. Back up these two existing files somewhere safe:

   ```text
   DetailsViewGameOverview.xaml
   GridViewGameOverview.xaml
   ```

5. Download the corresponding replacement files from this directory:

   ```text
   Views/DetailsViewGameOverview.xaml
   Views/GridViewGameOverview.xaml
   ```

6. Copy the downloaded files into the FusionX `Views` folder and replace the existing files when prompted.

7. Start Playnite.

The Game Routines controls should now be available in FusionX for tracked games.

The controls automatically collapse when the selected game is not tracked or when Game Routines does not provide visible content.

## Restoring the original FusionX files

To remove the manual integration:

1. Close Playnite.
2. Open the FusionX `Views` folder.
3. Replace the two modified files with the backups you created before installation.
4. Start Playnite again.

Reinstalling or updating FusionX may also restore the theme's original files.

## Updates

A FusionX update may overwrite the manually installed integration files.

Do not automatically reuse these replacement files after updating to a different FusionX version. Check this directory or the Game Routines documentation first to confirm whether that version is supported.

Game Routines never patches FusionX automatically.

## Developer reference

The integration keeps FusionX's existing cover system and other extension integrations intact.

The cover indicator is an independent, non-interactive overlay. The state toggle uses the existing cover-side action area, and the checklist uses the existing game overview tab structure.

Each host derives visibility from its injected Game Routines control and uses Playnite's `PluginUserControl.GameContext` with the authoritative `Game.Id`.

The theme contains no game-specific Game Routines configuration.