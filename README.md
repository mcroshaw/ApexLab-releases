# ApexLab

ApexLab records your laps from **iRacing**, **Le Mans Ultimate**, **RaceRoom**, **Automobilista 2** and
**Project Motor Racing**, and helps you find time: lap comparisons, corner-by-corner coaching, setup advice, a pit
stop planner and overlays drawn over the sim. It runs on your own PC; nothing is uploaded anywhere.

This repository is for downloads and feedback only. ApexLab is a test build: expect rough edges, and please tell us
what you find.

## Download

Get **ApexLab-win-x64.zip** from the [latest release](../../releases/latest). Windows 10 or 11, 64-bit. Nothing else
to install.

## Install

1. Unzip `ApexLab-win-x64.zip` anywhere (e.g. `Documents\ApexLab`).
2. Run **ApexLab.exe**. Your browser opens at http://localhost:5161. Keep the black ApexLab window open
   (minimised is fine) while you drive; close it to quit. Running ApexLab.exe again while it's open just
   reopens the page.
   Windows SmartScreen will probably warn about an unknown app the first time, because the exe isn't signed:
   *More info → Run anyway*.
3. Drive. Laps are recorded automatically.
   - **AMS2:** in the game, enable *Options → System → Shared Memory: Project CARS 2*.
   - **Project Motor Racing:** in the game, *Settings → Preferences → UDP* on, frequency 60, port 7576. If you
     also use SimHub, either set the UDP host to 224.0.0.150 so both can listen, or keep host 127.0.0.1, point
     the game at port 7576 and have ApexLab pass the data on to SimHub: create
     `%LOCALAPPDATA%\ApexLab\settings.json` containing `{ "Pmr": { "ForwardTo": "127.0.0.1:7577" } }`
     (SimHub's port) and restart ApexLab.
   - iRacing, LMU and RaceRoom need nothing.

No sim to hand? Start it with `ApexLab.exe --demo` for a simulated car on a test track.

## What's where

- **Live**: the current lap, delta to your best, fuel and tyres while you drive.
- **Overlays**: delta bar, inputs, fuel, fuel efficiency, tyres, radar, track map, lap times and damage, drawn over
  the sim while you're on track. Turn them on in the Overlays card on the Live page. The sim must run in
  borderless or windowed mode. Press the hotkey shown there (Ctrl+Shift+O, or Ctrl+Alt+O if another program has
  that) to move and resize them, then again to lock them. Each overlay is also a web page, for OpenKneeboard (VR)
  or an OBS browser source.
- **Sessions** and **Cars & Tracks**: every lap, lap analysis with track map, inputs and corner times, and a
  session summary with an optimal lap for the track temperature.
- **Coaching**: a chat with Ted, your coach: where the time is going, corner by corner, one tip at a time.
- **Setup advice**: a chat with Scotty, your setup engineer. He reads your laps and suggests changes (for LMU he can
  write them to a new setup file). Tell him when something is at its limit ("the rear bar's already maxed") and
  he remembers it for that car and suggests something else.
- **Setups**: compare any two setups side by side. **Learn**: what every setting does.
- **Strategy**: fuel and pit stop planning for longer races.
- **Conditions**: the track and weather recorded with every lap, saved as presets to drive them again offline.
- **Team**: optional. Point it at a folder your team shares (Google Drive, OneDrive, Dropbox…) and everyone's
  best laps appear on team leaderboards and in lap comparisons.

## Your data

Everything lives in `%LOCALAPPDATA%\ApexLab` (database, settings). ApexLab copies the lap database once a day to
the `backup` folder there and keeps the last 7 copies. To update, close ApexLab and replace the unzipped folder with
the new one; your data stays.

## Feedback

Found a bug or have an idea? [Open an issue](../../issues/new) and say which sim, car and track, what you did and
what happened. A screenshot helps, and so does the log from `%LOCALAPPDATA%\ApexLab\logs` for that day.
