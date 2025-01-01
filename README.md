# Manim Dev Container
Dev Container for [Manim animation engine](https://3b1b.github.io/manim/). Contains Dockerfile defining a container for OpenGL branch of Manim animation engine.

# Requirements
- [Visual Studio Code IDE](https://code.visualstudio.com/)
- [Docker Installation](https://www.docker.com)
- [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) Extension

# Getting Started
1. Clone the repository
    ```sh
    git clone https://github.com/MasterpieceTechVideos/manim_dev_container.git
    ```
2. Reopen in Container


3. Install region-based packages
    ```sh
    sudo apt-get install -y texlive-formats-extra texlive-fonts-extra 
    ```
4. Run example scene defined in ```~/manim/example_scenes.py``` to generate video
    ```sh
    manimgl ~/manim/example_scenes.py AnimatingMethods -o --hd
    ```

# Optional
No extensive tests have been done to ensure all required packages have been installed. Particularly LaTeX libraries defined in ```tex``` Debian packages. Additional ```tex``` packages can be installed incase of any LaTeX related errors. Refer to [wkrea/textlive-full-beefless.md](https://gist.github.com/wkrea/b91e3d14f35d741cf6b05e57dfad8faf) Gist for more on installation options.

# Usage
1. Read the [docs](https://3b1b.github.io/manim/getting_started/quickstart.html)
2. Fork the repository
3. Add your own scene definitions in the ```src``` folder
4. Generate your animations
    ```sh
    manimgl src/start.py SquareToCircle -ol
    ```
5. Get more examples from [Grant Sanderson of 3Blue1Brown](https://github.com/3b1b/videos)

# ToDo
Create Docker Hub image