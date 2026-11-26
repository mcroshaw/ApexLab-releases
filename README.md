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
- **Overlays**: delta bar, inputs, fuel, fuel efficiency, tyres, radar, track map, lap times, damage and ride height, drawn over
  the sim while you're on track. Turn them on in the Overlays card on the Live page. The sim must run in
  borderless or windowed mode. Press the hotkey shown there (Ctrl+Shift+O by default; you can set your own,
  including a button on your wheel) to move and resize them, then again to lock them. Each overlay is also a web
  page, for an OBS browser source.
- **Ride height overlay**: two modes, picked from its cog. *Setup builder* shows front and rear clearance (now, at
  rest in the pits, lowest this lap), how close each corner is to the ground, and the car's pitch and roll. *Speed
  states* shows the speed band, how much of each tyre's grip is in use (the circle is the limit: the dot heads out to
  it, growing and going green, amber, red) with a near-limit warning, and how much of the grip is aero and how much
  mechanical. LMU shares each tyre's forces; in the other sims ApexLab learns the car's grip as you drive and shares it
  out to the tyres by load transfer and balance.
- **Overlays in VR**: ApexLab draws the overlays straight into the headset, with no other app needed. Tick *Show
  overlays in VR* on the Overlays card, then start the game. OpenXR games without anti-cheat (RaceRoom) get them from
  ApexLab's own add-on, drawn in the game. Everywhere else, including Le Mans Ultimate (in OpenXR or OpenVR mode) and
  AMS2, they appear as SteamVR overlays while SteamVR is running. Press Ctrl+Shift+F11 in the headset to place them
  (Space picks one, mouse moves, wheel or + / − resizes, M to turn and tilt, Esc saves) and Ctrl+Shift+F12 to
  recentre them. **Anti-cheat:** the OpenXR add-on isn't code-signed yet, so games with Easy Anti-Cheat (LMU,
  iRacing) block it and may flag it; turn VR off before starting iRacing if you're unsure.
- **Sharing laps (Discord)**: press **Share** on any lap and ApexLab saves it as an `.apexlap` file in your Downloads;
  drag it into a Discord chat. Got one from someone? Download it and drop it anywhere on ApexLab: it opens against
  your best lap of the same car and track, and stays under *Compare with*.
- **Sessions** and **Cars & Tracks**: every lap, lap analysis with track map, inputs and corner times (brake and
  throttle together or as separate charts against the reference), and a session summary with an optimal lap for the
  track temperature.
- **Understeer / oversteer**: lap analysis has a *Balance* chart (+ understeer, − oversteer), an *Understeer /
  oversteer* colouring for the track map (2D and 3D) and a Balance column in the corner table for entry, mid-corner and
  exit. Slides you caught show as full oversteer. It's for your own laps (it needs steering and yaw rate). Coaching
  uses it to show where your typical laps push or step out more than your best, and Setup advice uses it to judge the
  car's balance on entry, mid-corner and exit against its own neutral.
- **3D track view**: tick **3D** on the lap analysis track map to see your lap on the track at its real elevation,
  with your throttle and braking (or speed, time gained or lost, car balance: pick under *Colour the lap by*) standing
  up from the racing line as a coloured wall, and the reference as a faint blue wall. *Orbit*, *Follow the car* or
  *Top-down*; press **Play** or drag the slider to drive the lap, with speed, pedals, height, slope, gap to the
  reference and balance shown underneath. *Pop out* fills the screen. Drag to turn, right-drag to pan, wheel to zoom;
  the corner buttons fly to each corner. Heights are recorded from 0.1.42 on (iRacing: imported .ibt files only), so
  older laps show flat.
- **Coaching**: a chat with Ted, your coach: where the time is going, corner by corner, one tip at a time. Ted and Scotty both
  leave out the first 3 laps of every stint (out lap and tyre warm-up, at the start and after every pit stop). Each
  tip says which driving skill it trains, foundations first (Level 1 safety and consistency, then Level 2 balance and
  speed, then Level 3 precision), and each corner shows how much of the grip you use on entry, mid-corner and exit.
  Ted also reads the shape of each corner (consistency lap to lap, the gap between brake and throttle, how much of
  the turning is done before you accelerate), and Scotty says what to try in the driving before changing the setup.
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
