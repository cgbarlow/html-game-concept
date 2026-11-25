# Building the Games on a Mac mini

This guide covers setting up an Apple Silicon Mac mini to build one of the [three game concepts](README.md) with the [`onefile-aaa`](https://github.com/elcronos/whiteout-onefile) skill, and running the build in a way that holds up over several hours.

## Why build on the Mac and not in a container

The skill judges the game by taking real screenshots in Google Chrome. Its tools open a visible Chrome window, render the game on the GPU, and pass the frames to a critic that sees only those images. That needs a real GPU and a real display.

A dev container such as DevPod running on Docker Desktop for Mac can't provide either:

- **No GPU.** Docker Desktop runs containers inside a Linux virtual machine that can't use the Mac's GPU. Chrome would fall back to software rendering, so the critic would be judging frames the real game would never show.
- **No display** for the Chrome windows.
- **No Chrome for ARM Linux.** On Apple Silicon the container runs ARM64 Linux, and Google Chrome has historically had no Linux ARM64 build.

The Mac mini itself is close to what the skill was built for. The demo game, WHITEOUT, was built on an Apple Silicon Mac, and the skill's browser tools use Apple's Metal graphics on macOS. So run Claude Code directly on macOS.

## 1. Install the prerequisites

In Terminal on the Mac (not inside the dev container):

```bash
brew install node                      # Node 18 or newer
brew install --cask google-chrome      # the skill needs Google Chrome itself, not Chromium
npm install -g @anthropic-ai/claude-code
```

You don't need to install Playwright: the skill's setup step installs it automatically.

## 2. Install the skill and the critic agent

```bash
git clone https://github.com/elcronos/whiteout-onefile.git /tmp/whiteout-onefile
mkdir -p ~/.claude/skills ~/.claude/agents
cp -r /tmp/whiteout-onefile/skill/onefile-aaa ~/.claude/skills/
cp ~/.claude/skills/onefile-aaa/agents/onefile-critic.md ~/.claude/agents/
```

If Claude Code was already open, restart it so it picks up the skill and the agent.

## 3. Start a build

Use a folder outside this concepts repo, because the skill creates its own git repo for each game:

```bash
mkdir -p ~/games && cd ~/games
claude
```

Inside Claude Code:

1. Run `/model` and choose **Opus 5.5**.
2. Paste one of the ready-to-use prompts from the [README](README.md), for example the [Do Not Feed the Kea](README.md#1-do-not-feed-the-kea-recommended) prompt, which ends with `Budget: quick. Directory: ./do-not-feed-the-kea`.

The `quick` budget took the demo game about 5 hours and about 4 million tokens. If a usage limit interrupts the run, tell Claude to resume. Finished agents replay from cache, so it continues from where it stopped.

## 4. Keep a long run healthy

- **Screen:** Chrome needs a display to open its windows. Attach a monitor, or use an HDMI dummy plug if the mini usually runs without one. A plain Screen Sharing session may not be enough on its own if no display is attached.
- **Sleep:** stop the Mac sleeping during the run. In a second Terminal tab, run:
  ```bash
  caffeinate -dimsu
  ```
- **Memory:** quit Docker Desktop during the run. Its Linux virtual machine holds onto RAM and CPU even when idle.
- **Hands off:** Chrome windows keep popping up for screenshots, playtests and speed tests. Leave the Mac alone while the build runs.

## 5. Bring the game back

The finished game is a single file, `~/games/<game-folder>/dist/index.html`. To add it to this repo, copy it into the repo on the Mac or into the dev container, then commit and push as usual.

## Alternatives (not recommended)

- **Chrome on the Mac, Claude in the container.** Start Chrome on the Mac with remote debugging turned on. Change the skill's `tools/_browser.mjs` to connect to that browser through `host.docker.internal` instead of launching its own. You'd also have to open up the skill's local file server, which only listens inside the container, so the Mac can reach it. This works, but you'd be modifying the skill and maintaining those changes.
- **Software rendering inside the container.** Use Playwright's own Chromium with a virtual display (Xvfb). Everything runs, but the visual and speed checks are meaningless, which defeats the purpose of the skill.
