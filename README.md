[![Build Status](https://travis-ci.org/mgbellemare/Arcade-Learning-Environment.svg?branch=master)](https://travis-ci.org/mgbellemare/Arcade-Learning-Environment)

<img align="right" src="doc/manual/figures/ale.gif" width=50>

# The Arcade Learning Environment

The Arcade Learning Environment (ALE) is a simple object-oriented framework that allows researchers and hobbyists to develop AI agents for Atari 2600 games. It is built on top of the Atari 2600 emulator [Stella](https://stella-emu.github.io/) and separates the details of emulation from agent design. This [video](https://www.youtube.com/watch?v=nzUiEkasXZI) depicts over 50 games currently supported in the ALE.

This patch is just an unofficial hard fork. The original code can be found [here](https://github.com/mgbellemare/Arcade-Learning-Environment).

## What is this patch for?
- I had a hard time installing ALE on Windows 10 and Mac OS. Moreover, the [Visual Studio port](https://github.com/Islandman93/Arcade-Learning-Environment) of IslandMan93 uses outdated code ALE 0.0.1. Therefore, I created this multi-platform patch for ALE 0.6.0.
- This patch supports latest Mac OS Sierra and Windows 10 (with ALE 0.6.0).
- More thread-safe (delete all static fields).
- User can set configuration file for each environment using function ale.setString(b'config', b'path_to_config_file').
- Merge IslandMan93's [Visual Studio 2013 port of the ALE 0.0.1](https://github.com/Islandman93/Arcade-Learning-Environment) to ALE 0.6.0.
- This patch is indexed as version 0.6.1.
- Installation guide in more details.
- Please let me (garlicdevs@gmail.com) know if you cannot install this patch.

## Installation Guide
### Mac OS
- I successfully installed ALE using the following steps on Mac OS 10.12 and Python 3.6.3

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

### Linux

1. Install dependences:
```
sudo apt-get install libsdl1.2-dev libsdl-gfx1.2-dev libsdl-image1.2-dev cmake
```

2. Install Arcade Learning Environment:
```
git clone https://github.com/garlicdevs/Arcade-Learning-Environment.git
cd Arcade-Learning-Environment
mkdir build && cd build  
cmake -DUSE_SDL=ON -DUSE_RLGLUE=OFF -DBUILD_EXAMPLES=ON ..
make -j 4
cd ..
pip3.6 install .
```

### Windows
- I successfully installed ALE on Windows 10 (Visual Studio 2017) and Python 3.6.2 using the following steps:

1. Download project
```
git clone https://github.com/garlicdevs/Arcade-Learning-Environment.git
```

2. Open Visual Studio 2017 -> Open solution ALE.sln in folder visual_studio -> Set configuration (Release|x64) -> build ALE -> build ale_python_interface
If you build projects successfully, the library ale_python_interface.dll will appear in folder visual_studio\x64\Release\

3. Install Arcade Learning Environment:
```
cd Arcade-Learning-Environment
python winsetup.py install
```


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


## Support the authors of The Arcade Learning Environment
By citing the following papers if you use ALE

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


If you use the ALE with sticky actions (flag `repeat_action_probability`), or if you use the different game flavours (mode and difficulty switches):

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
