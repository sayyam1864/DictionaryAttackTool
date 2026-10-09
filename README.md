# Dictionary Attack Tool — Build Output

Pre-built jar and Windows exe for dictionary attack.

This repo holds the compiled outputs, it's here so the jar/exe can be downloaded and run directly without needing to build anything first.

## What this tool does

A simple console app that runs a plain-word dictionary attack: give it a secret and a wordlist file, and it checks the wordlist line by line for an exact match. If it finds one, it reports the matched word, line number, total attempts, and time taken. If it doesn't, it reports that too.

## Contents

- `target/dict-attack.jar` — runnable jar (needs Java 17+ installed)
- `exe-output/DictionaryAttack/DictionaryAttack.exe` — standalone Windows exe (bundles its own Java runtime, nothing needs to be installed)
- `10k-most-common.txt` — sample wordlist used for testing

## Requirements

- **Running the exe:** nothing needed, it has its own bundled Java runtime
- **Running the jar:** Java JDK 17 or newer installed

## How to run — exe

Don't double-click the exe directly, it's a console app, so the window opens and closes instantly once it finishes. Run it from an already-open terminal instead:

```powershell
cd exe-output\DictionaryAttack
.\DictionaryAttack.exe --wordlist "10k-most-common.txt"
```

If the wordlist can't be found, use its full path instead of a relative one.

## How to run — jar

```powershell
cd target
java -jar dict-attack.jar --wordlist "10k-most-common.txt"
```

## Parameters

| Parameter | Required? | What it does |
| --- | --- | --- |
| `--secret` | No | the password to search for; if left out, the program prompts for it |
| `--wordlist` | Yes | path to the `.txt` wordlist file |
| `--config` | No | a `.properties` file with `secret=` and `wordlist=` lines instead |

## Sample output

### Match found:

Match found!

Word: dragon123

Line number: 482

Total attempts: 482

Time taken: 3 ms

Speed: 160666.67 attempts per second


### Not found:

Secret was not found in the wordlist.

Total attempts: 14344392

Time taken: 812 ms


## Troubleshooting

- **Exe window flashes and disappears** — happens if you double-click it directly, run it from a terminal instead (see above).
- **"wordlist file not found"** — the program looks for the file relative to wherever you're running the command from, use a full path if needed.
- **PowerShell specifically** — needs `.\` before the exe name (e.g. `.\DictionaryAttack.exe`); plain `DictionaryAttack.exe` won't run there.
