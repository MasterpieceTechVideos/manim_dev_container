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

5. Get more examples from:
    - [3b1b.github.io/manim](https://3b1b.github.io/manim/getting_started/quickstart.html)
    - [manim.readthedocs.io](https://manim.readthedocs.io)
    - [github.com/3b1b/videos](https://github.com/3b1b/videos)

# NB
Additional ```tex``` packages can be installed incase of any LaTeX related errors. Refer to [wkrea/textlive-full-beefless.md](https://gist.github.com/wkrea/b91e3d14f35d741cf6b05e57dfad8faf) Gist for more on installation options.

# Usage
1. Fork the repository
2. Add your own scene definitions in the ```src``` folder e.g.
```sh
echo "
from manimlib import *

class SquareToCircle(Scene):
    def construct(self):
        circle = Circle()
        circle.set_fill(BLUE, opacity=0.5)
        circle.set_stroke(BLUE_E, width=4)
        square = Square()

        self.play(ShowCreation(square))
        self.wait()
        self.play(ReplacementTransform(square, circle))
        self.wait()
" >> src/start.py
```
3. Generate your animations
```sh
manimgl src/start.py SquareToCircle -ol
```

# ToDo
Create Docker Hub image