# Contributing to DCRecomp

Thanks for helping. This guide applies to every DCRecomp repository that has no contributing guide of its own. Issues and
pull requests can be written in English or Portuguese.

## The rule that cannot bend

Never add, attach or link any of these, in code, issues, pull requests or screenshots of extracted data:

- disc images (CDI, GDI, CHD, ISO, BIN/CUE), BIOS or flash dumps;
- files extracted from a game: executables, models, textures, audio, video;
- code generated from a game's executable;
- saves, memory dumps or traces containing game data;
- transcripts or translations of game text.

Pull requests with this content are closed, and the content is removed from history.

## Licensing

Your contribution is licensed under the MIT license of the repository. Do not copy code from GPL projects or from projects
without a license. Reading them to understand behavior is fine; note in the pull request what you consulted.

## Before you open a pull request

1. Build and run the repository's tests.
2. For a change in behavior, say how you verified it: bytes of the original executable, hardware documentation, or a test.
   Add a test that reproduces the case whenever possible, and make sure it fails without your change.
3. Keep the change focused. Open an issue first for architecture changes.
4. Do not weaken a comparison or a test to make it pass.

AI-assisted contributions are welcome if you understand and verified the result. You are responsible for what you submit.

## Good ways to help without writing code

- Test on different PCs, GPUs and controllers, and report the exact release of the game and the version you used.
- Document reverse-engineering findings.
- Improve guides and translations of the tools.
