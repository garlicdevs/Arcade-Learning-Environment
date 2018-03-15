[![Build Status](https://travis-ci.org/mgbellemare/Arcade-Learning-Environment.svg?branch=master)](https://travis-ci.org/mgbellemare/Arcade-Learning-Environment)

<img align="right" src="doc/manual/figures/ale.gif" width=50>

# The Arcade Learning Environment

The Arcade Learning Environment (ALE) is a simple object-oriented framework that allows researchers and hobbyists to develop AI agents for Atari 2600 games. It is built on top of the Atari 2600 emulator [Stella](https://stella-emu.github.io/) and separates the details of emulation from agent design. This [video](https://www.youtube.com/watch?v=nzUiEkasXZI) depicts over 50 games currently supported in the ALE.

For an overview of our goals for the ALE read [The Arcade Learning Environment: An Evaluation Platform for General Agents](http://www.jair.org/papers/paper3912.html). If you use ALE in your research, we ask that you please cite this paper in reference to the environment (BibTeX entry at the end of this document). Also, if you have any questions or comments about the ALE, please contact us through our [mailing list](https://groups.google.com/forum/#!forum/arcade-learning-environment).


Feedback and suggestions are welcome and may be addressed to any active member of the ALE team.

### Features
- Object-oriented framework with support to add agents and games.
- Emulation core uncoupled from rendering and sound generation modules for fast emulation with minimal library dependencies.
- Automatic extraction of game score and end-of-game signal for more than 50 Atari 2600 games.
- Multi-platform code (compiled and tested under OS X and several Linux distributions, with Cygwin support).
- Communication between agents and emulation core can be accomplished through pipes, allowing for cross-language development (sample Java code included).
- Python development is supported through ctypes.
- Agents programmed in C++ have access to all features in the ALE.
- Visualization tools.

## This Patched Code
- This patch supports latest Mac OS Sierra
- More thread-safe (delete all static fields)
- User can set configuration file for each environment using ale.setString(b'config', b'path_to_config_file'). (thread-safe)

## Installation Guide

- We successfully installed ALE using the following steps on Mac OS 10.12 and Python 3.6.3

1. Install brew:
```
 /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Install dependences:
```
brew install sdl sdl_image sdl_mixer sdl_ttf smpeg portmidi cmake
```

3. Install Arcade Learning Environment:
```
git clone https://github.com/garlicdevs/Arcade-Learning-Environment.git
cd Arcade-Learning-Environment
mkdir build && cd build  
cmake -DUSE_SDL=ON -DUSE_RLGLUE=OFF -DBUILD_EXAMPLES=ON -DMAC_OS=ON ..
make -j 4
cd ..
env MACOSX_DEPLOYMENT_TARGET=10.9 pip3.6 install .
```

Getting the ALE to work on Visual Studio requires a bit of extra wrangling. You may wish to use IslandMan93's [Visual Studio port of the ALE.](https://github.com/Islandman93/Arcade-Learning-Environment)

For more details and installation instructions, see the [manual](doc/manual/manual.pdf). To ask questions and discuss, please join the [ALE-users group](https://groups.google.com/forum/#!forum/arcade-learning-environment).

## ALE releases

Releases before v.0.5 are available for download in our previous [website](http://www.arcadelearningenvironment.org/). For the latest releases, please check our releases [page](https://github.com/mgbellemare/Arcade-Learning-Environment/releases).

## List of command-line parameters

Execute ./ale -help for more details; alternatively, see documentation 
available at http://www.arcadelearningenvironment.org.

```
-random_seed [n] -- sets the random seed; defaults to the current time

-game_controller [fifo|fifo_named] -- specifies how agents interact
  with the ALE; see Java agent documentation for details

-config [file] -- specifies a configuration file, from which additional 
  parameters are read

-run_length_encoding [false|true] -- determine whether run-length encoding is
  used to send data over pipes; irrelevant when an internal agent is 
  being used

-max_num_frames_per_episode [n] -- sets the maximum number of frames per
  episode. Once this number is reached, a new episode will start. Currently
  implemented for all agents when using pipes (fifo/fifo_named) 

-max_num_frames [n] -- sets the maximum number of frames (independent of how 
  many episodes are played)
```


## Citing The Arcade Learning Environment


If you use the ALE in your research, we ask that you please cite the following.

*M. G. Bellemare, Y. Naddaf, J. Veness and M. Bowling. The Arcade Learning Environment: An Evaluation Platform for General Agents, Journal of Artificial Intelligence Research, Volume 47, pages 253-279, 2013.*

In BibTeX format:

```
@Article{bellemare13arcade,
  author = {{Bellemare}, M.~G. and {Naddaf}, Y. and {Veness}, J. and {Bowling}, M.},
  title = {The Arcade Learning Environment: An Evaluation Platform for General Agents},
  journal = {Journal of Artificial Intelligence Research},
  year = "2013",
  month = "jun",
  volume = "47",
  pages = "253--279",
}
```


If you use the ALE with sticky actions (flag `repeat_action_probability`), or if you use the different game flavours (mode and difficulty switches), we ask you that you also cite the following:

*M. C. Machado, M. G. Bellemare, E. Talvitie, J. Veness, M. J. Hausknecht, M. Bowling. Revisiting the Arcade Learning Environment: Evaluation Protocols and Open Problems for General Agents,  CoRR abs/1709.06009, 2017.*

In BibTex format:

```
@Article{machado17arcade,
  author = {Marlos C. Machado and Marc G. Bellemare and Erik Talvitie and Joel Veness and Matthew J. Hausknecht and Michael Bowling},
  title = {Revisiting the Arcade Learning Environment: Evaluation Protocols and Open Problems for General Agents},
  journal = {CoRR},
  volume = {abs/1709.06009},
  year = {2017}
}
```
