# GDT Studio
A toolkit for Game Dev Tycoon — plan high-scoring games, dial in your development sliders, and edit your save, all in one page. Comes with an optional live trainer for Windows.

🔗 Live app: https://kingrizal.github.io/GPT-Calculator/
⬇ Trainer download: GdtTrainer.exe

Built by Doc.


What's inside

🎯 Build Planner

Pick a platform, topic, genre (single or mixed), audience, game size, era and trend, and get instant readouts:


Combo grades — Topic × Genre, Topic × Audience, Platform × Genre, Platform × Audience.
Verdict score with the right caps (small-game-out-of-garage, medium-under-100K-fans, etc.).
Recommendations — best audience for your topic + platform, and the top platforms for your genre in the current era.
Mixed genres use the real 2:1 lead-weighting the game applies.


🎚 Development sliders

Vertical sliders that follow the genre you picked and snap to proven 10/10 layouts:


Auto-solve 10/10 — single genres load the proven preset; mixed genres are searched for the closest balanced layout.
Live design/tech balance bar, target tech:design ratio, balance check, and field-focus score.
KEY tags mark the fields that matter most for the genre.


💾 Save Editor

Drag in your save and edit it in the browser — nothing is uploaded:


Edits cash, research points and fans.
Per-staff skills (Design / Tech / Speed / Quality / Research), a Level dropdown (1–12, writes the correct XP), boost level, and a one-click Max (1.0) / Overpowered (2.0).
Handles both save formats: the SQLite file__0.localstorage and plain-JSON slot_* files.
Produces an edited copy to download — your original is never touched.



⚠ Back up your save before replacing it. Cash and research are safe to edit; push staff stats and fans in small steps.



🛠 GDT Trainer (Windows)

A live trainer that edits the running game — no mod, no save file. See below.


GDT Trainer — live editing

The trainer attaches to a running Game Dev Tycoon (an NW.js / Chromium build) over the Chrome DevTools Protocol and edits values in real time: cash, research, fans, and all staff (skills / level / boost). It drives the game's own JavaScript, so there are no mod files to install.

Use it


Download GdtTrainer.exe.
Launch the game with the debug port open. Either use the trainer's Launch game… button (point it at the game .exe), or start the game with:


   --remote-debugging-port=9222 --remote-allow-origins=*


Load into a company, open the trainer, leave the port at 9222, and click Connect.
Use the buttons, or the JS console for anything custom.


Requirements / notes


Windows, plus the .NET 8 Desktop Runtime (x64): https://dotnet.microsoft.com/download/dotnet/8.0
(only needed for the small framework-dependent build; a self-contained build needs nothing)
The exe is unsigned, so Windows SmartScreen will warn — click More info → Run anyway.



Build the trainer from source

The trainer is a single-file .NET 8 WinForms app (no NuGet packages).

bat:: needs the .NET 8 SDK: https://dotnet.microsoft.com/download/dotnet/8.0
dotnet publish GdtTrainer.csproj -c Release -r win-x64 ^
  --self-contained true ^
  -p:PublishSingleFile=true ^
  -p:IncludeNativeLibrariesForSelfExtract=true ^
  -p:EnableCompressionInSingleFile=true

Output: bin\Release\net8.0-windows\win-x64\publish\GdtTrainer.exe.
Set --self-contained false for a much smaller exe that needs the .NET runtime installed instead.


How the data is sourced

The Planner tables are base-game values (the v1.4.x model): topic genre/audience weightings, platform fits, and per-genre tech/design targets, cross-checked against the official gdt-modAPI. Combo / platform / topic tables are stable across versions; later patches only shift a few platform release dates. Trends are random per playthrough, so you set the one you currently see in-game.

The web app is a single self-contained index.html — no build step, no backend, no tracking. The SQLite engine for the save editor is bundled inline, which is why the file is a few MB.


Disclaimer

Unofficial fan-made tool, not affiliated with or endorsed by Greenheart Games. Game Dev Tycoon is © Greenheart Games. Intended for single-player use — editing your own save/game. Keep a backup of your save files.
