# Starting a Dreamcast recomp

This guide describes the path used by the DCRecomp projects. It is a method, not a framework: each game has its own
repository and its own decisions. [BlueStingerRecomp](https://github.com/DCRecomp/BlueStingerRecomp) and
[HeadHunterRecomp](https://github.com/DCRecomp/HeadHunterRecomp) are working examples.

## Before you start

- You need a disc you own, and a good dump of it.
- Pick one exact release (region, serial, version) and identify it by the SHA-256 of its main executable, usually
  `1ST_READ.BIN`. Support other releases later.
- Check that the executable is plain SH-4 code. Windows CE games need a different plan.
- Find a stable emulator for the game. It is your source of truth while the port is incomplete.
- Read [the legal rules](#legal-checklist) first. They shape the repository from the first commit.

## Stages

Work in small, testable steps. A stage ends with evidence, not with an impression that it works.

| # | Stage | Done when |
|---|---|---|
| 1 | **Extract and identify.** Read the disc image, extract files, check the executable hash | A real-disc test passes and hashes agree with an independent tool |
| 2 | **Decode SH-4.** Disassembler with full instruction coverage | Output matches an independent decoder across the whole executable |
| 3 | **Analyze.** Functions, jump tables, delay slots, reachable code | Every reachable instruction is accounted for, or listed as unresolved |
| 4 | **Generate C++.** Translate each function, keeping exact CPU semantics | Generated code compiles and instruction tests match the SH-4 manual |
| 5 | **Boot.** A minimal runtime reaches the first frame | The boot path matches a trace from the reference emulator |
| 6 | **Make it playable.** Enough hardware model to reach gameplay | A scripted route reaches gameplay, deterministically |
| 7 | **Go native.** Replace each subsystem with a real PC implementation: files, time, input, saves, video, audio, rendering | Each replacement is compared with the previous behavior or the emulator |
| 8 | **Remove the console layer** from the shipped program | The linker map shows the hardware models are gone, and references still match |
| 9 | **Distribute.** A builder that turns the user's disc into the game on the user's machine | Clean-machine test, with no development paths left behind |

## Habits that pay off

- **Reproducible input.** Scripted input per game step, plus a logical state hash per step, makes any regression visible at
  the exact step it happens.
- **Negative tests.** Every check needs a case proving it fails when it should.
- **Keep the old path until the new one is proven.** Replace one subsystem at a time, behind a switch.
- **No silent fallback.** If something is unsupported, stop with a clear error.
- **Independent review.** A second reviewer, human or AI, should check semantics against the binary. Settle disagreements
  with evidence.
- **Record what was verified.** A `STATUS.md` with date and method for each check stops old claims from going stale.

## Legal checklist

- [ ] `.gitignore` blocks disc images, `game-data/`, `generated/`, analysis output, saves, dumps and traces.
- [ ] `LEGAL.md` states what the project is, that it needs the user's own disc, and that it has no affiliation with rights
      holders.
- [ ] `config/` holds metadata only: hashes, sizes, addresses. No bytes of the game.
- [ ] No BIOS or flash dumps. Use high-level replacements for what the game needs.
- [ ] Text from the game, including transcripts and translations of dialogue, is not published.
- [ ] Icons and art are original, or generated locally from the user's own files.
- [ ] No code copied from GPL projects (such as Flycast) or from projects without a license. They are behavior references.
- [ ] Releases contain tools only, never game data or generated code.

## Repository conventions

- Name: `<GameName>Recomp`, for example `BlueStingerRecomp`.
- License: MIT, in a `LICENSE` file with only the license text, so GitHub detects it. Put game-specific notices in `LEGAL.md`.
- Topics: `dreamcast`, `sh4`, `static-recompilation`, `game-preservation`, plus the genre.
- Recommended files: `README.md`, `ARCHITECTURE.md`, `STATUS.md`, `LEGAL.md`, and `.recomp.json` for
  [recomp.fyi](https://recomp.fyi).

## Getting your project into DCRecomp

Open a [new recomp proposal](https://github.com/DCRecomp/.github/issues/new?template=new-recomp.yml). A project can join once
the legal checklist is met and it has at least a verified extraction stage. Transferring an existing repository keeps its
history and its links.
