# DCRecomp

**Open-source static recompilation of Sega Dreamcast games into native PC programs.**

DCRecomp brings Dreamcast recompilation projects together in one place and helps new ones get started. Each project turns
the SH-4 executable of a game into C++ that runs natively, then replaces the console hardware piece by piece with real PC
systems: files, input, saves, video, audio and rendering. The goal is preservation, compatibility with modern machines, and
a solid base for mods.

No game is distributed here. Every project builds locally from a disc the user owns.

## Projects

| Project | Game | Platform | State |
|---|---|---|---|
| [BlueStingerRecomp](https://github.com/DCRecomp/BlueStingerRecomp) | Blue Stinger (NTSC-U) | Windows x64 | In progress; console layer removed from the product, final validation under way |
| [HeadHunterRecomp](https://github.com/DCRecomp/HeadHunterRecomp) | Head Hunter | Windows x64 | In progress |

Each repository has the current state in its own `STATUS.md`.

## Want to recompile a Dreamcast game?

Start with **[Starting a recomp](https://github.com/DCRecomp/.github/blob/main/docs/STARTING-A-RECOMP.md)**: the stages, what
to verify at each one, and how to keep the project legally clean. Then open a
[new recomp proposal](https://github.com/DCRecomp/.github/issues/new?template=new-recomp.yml) so others can help.

You do not need to start a project to contribute. Testing on different PCs and controllers, reverse engineering, tools and
documentation all help: see the [contributing guide](https://github.com/DCRecomp/.github/blob/main/CONTRIBUTING.md).

## Ground rules

- **Never** commit disc images, BIOS or flash dumps, extracted game files, generated code, saves, or transcribed game text.
- Project code is MIT. GPL projects and projects with no license are behavior references only: no copied code.
- Claims are backed by evidence: bytes of the original executable, hardware documentation, or a reproducible test.

---

*Em português:* o DCRecomp reúne projetos de recompilação estática de jogos de Dreamcast para PC e ajuda quem quer começar um
novo. Nenhum jogo é distribuído aqui: cada projeto é compilado localmente a partir do disco do próprio usuário. Issues e pull
requests podem ser escritos em português ou inglês.

DCRecomp is not affiliated with Sega or with any rights holder of the games.
