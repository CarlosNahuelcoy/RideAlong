# Ride Along

**An AI co-driver for Euro Truck Simulator 2 and American Truck Simulator.**

Ride Along puts a companion in your cab. You talk to it by voice with a push-to-talk button, and it talks back. It comments on the trip, reacts to what happens on the road, remembers your past jobs and can work the cab controls you ask for.

> This repository hosts the **Ride Along app (`RideAlong.exe`)** and its documentation. The game plugins are downloaded from **[Nexus Mods](NEXUS_URL)**. You need both.

**[Download RideAlong.exe (latest release)](https://github.com/CarlosNahuelcoy/RideAlong/releases/latest)**

---

## Features

- **Voice chat.** Hold a key (Alt by default) or a wheel/gamepad button, speak, release. The companion answers out loud, with optional on-screen subtitles.
- **Reacts to the game.** Fines, tolls, ferries and trains, collisions, low fuel, refuelling, job start and delivery, speeding, rest stops, changing or repairing your truck. Each kind can be switched off.
- **Cab controls by voice.** "Turn on the lights", "wipers on", "left blinker", "hazards". It works with keyboard or wheel bindings. It only touches comfort controls, never the engine, brakes or steering.
- **Personalities.** Passenger, Truck AI, Tour guide and Veteran trucker, or rewrite any of them in your own words.
- **Memory and trip journal.** It remembers past conversations and keeps a log of every job (route, cargo, pay, fines, damage) per driver profile.
- **Casual chatter.** Spontaneous remarks while you drive, as often or as rarely as you like.
- **Your choice of AI.** Player2 (default, free account), OpenAI, OpenRouter, Google Gemini, NovelAI or any OpenAI-compatible server (Ollama, LM Studio...). Free offline Windows voices are also available.
- **English and Spanish interface.** The companion can talk in other languages too.

## Requirements

- Windows 10 or 11, 64-bit. Nothing else to install: .NET is included in the exe.
- Euro Truck Simulator 2 or American Truck Simulator, 64-bit.
- An AI provider account. The easiest is [Player2](https://player2.game) (free). Every request uses your own account and credits.
- A microphone, to talk to it.

## Installation

1. **Download the plugins** from [Nexus Mods](NEXUS_URL) and extract the zip anywhere (for example `Documents`). You get a `RideAlong` folder with a `Plugins` folder inside.
2. **Download `RideAlong.exe`** from the [latest release](https://github.com/CarlosNahuelcoy/RideAlong/releases/latest).
3. **Put `RideAlong.exe` in that `RideAlong` folder**, next to `Plugins`:
   ```
   RideAlong\
     RideAlong.exe      <- from GitHub
     Plugins\           <- from Nexus
       ridealong_input.dll
       scs-telemetry.dll
     README.txt
   ```
4. **Close the game** and run `RideAlong.exe`.
   Windows may show *"Windows protected your PC"* because the app is not code-signed. Click **More info**, then **Run anyway**.
5. On the **Home** page, click **Prepare game**. Ride Along finds your ETS2/ATS installs in your Steam libraries and copies both plugins into `<game>\bin\win_x64\plugins\`.
6. **Sign in to your AI provider.** With Player2, a browser window opens the first time and you approve the login there. You don't need the Player2 desktop app. To use another provider, open **AI providers** and paste your API key.
7. **Start the game as usual.** When the game shows the *advanced SDK features* notice, accept it: that is the plugins loading.

### Manual plugin install

If your game is not in a Steam library, or "Prepare game" can't find it, copy both DLLs from `Plugins` to `<game folder>\bin\win_x64\plugins\` yourself (create the `plugins` folder if it does not exist).

## How to use

| Action | How |
|---|---|
| Talk | Hold **Alt**, speak, release. Change it under **Controls & buttons** (keyboard key or wheel/gamepad button). |
| Interrupt | Press push-to-talk while it is speaking. |
| Turn the companion on/off in game | Bind an on/off button under **Controls & buttons**. |
| Ask for cab controls | Just say it: "turn on the high beams", "wipers off", "hazards on". |
| Change personality | **Personality** page. Edit the text to make it your own; **Restore original text** undoes it. |
| Review jobs | **Trip journal** page. |
| See or wipe its memory | **Memory** page. |

Good to know:

- The companion stays quiet until you **start the engine** (configurable).
- Keep Ride Along running while you play. Closing the window sends it to the **tray**; exit from the tray icon.
- Ride Along **never starts the game** by itself.
- **Subtitles** are drawn over the game window. They work in windowed and borderless fullscreen; exclusive fullscreen can hide them.
- Language settings are separate: the app language, the language the companion replies in, the language you speak and its voice.

## AI providers

| Provider | Chat | Voice | Listening |
|---|---|---|---|
| Player2 | yes | yes | yes |
| OpenAI | yes | yes | yes |
| OpenRouter | yes | | |
| Google Gemini | yes | | |
| NovelAI | yes | yes (English) | |
| Custom (OpenAI-compatible) | yes | optional | optional |
| Windows voices | | yes (free, offline) | |

Chat, voice and listening can each use a different provider. API keys are stored **only on your PC**, encrypted with Windows DPAPI, and are never shown again.

## Troubleshooting

- **"Prepare game" says a plugin was not found.** `RideAlong.exe` must be in the folder that contains `Plugins` (step 3).
- **The game doesn't show the SDK notice / no telemetry.** Check that both DLLs are in `<game>\bin\win_x64\plugins\` and that you run the 64-bit game.
- **It doesn't hear me.** Pick your microphone under **Voice & audio** and check the push-to-talk binding.
- **"Insufficient credits".** Your AI account ran out of credits (Player2 joules or your provider's balance).
- **No subtitles in game.** Switch the game to windowed or borderless fullscreen.
- **Logs.** `%AppData%\RideAlong\ridealong.log`. Attach it when you report a problem.

Report problems in [Issues](https://github.com/CarlosNahuelcoy/RideAlong/issues) or on the Nexus page.

## Uninstall

1. Delete `ridealong_input.dll` from `<game>\bin\win_x64\plugins\`. Delete `scs-telemetry.dll` too if no other tool (for example ETS2LA) uses it.
2. Delete the `RideAlong` folder.
3. Delete `%AppData%\RideAlong` (settings, memory, trip journal, logs, encrypted keys).

## Privacy

- Ride Along has no servers. What you say and the game state it needs go only to the AI provider you choose, under that provider's terms.
- API keys and settings stay on your PC.

## Safety

`RideAlong.exe` runs outside the game. The in-game plugin `ridealong_input.dll` only presses a closed list of cab comfort controls (lights, wipers, blinkers, beacon, hazards, horn...). It has no network, audio or file access. Check the files against `RideAlong-<version>-SHA256.txt` in each release.

## Credits

- Telemetry plugin `scs-telemetry.dll`: [scs-sdk-plugin](https://github.com/RenCloud/scs-sdk-plugin) by RenCloud (MIT).
- Built with the SCS Software SDK, NAudio, WPF UI and CommunityToolkit.Mvvm. See [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt).
- Euro Truck Simulator 2 and American Truck Simulator are trademarks of SCS Software. Ride Along is a fan project, not affiliated with or endorsed by SCS Software or Player2.

## License

Ride Along is free to download and use, but it is **not open source**. See [LICENSE.md](LICENSE.md).

Made by **Carlos Nahuelcoy (Gerik Uylerk)**.
