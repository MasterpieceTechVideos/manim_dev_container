# Source files
Folder for storing your .py scene definitions

# Example
[Quick Start Example](https://3b1b.github.io/manim/getting_started/quickstart.html) saved in ```src/start.py```

```py
from manimlib import *

class SquareToCircle(Scene):
    def construct(self):
        circle = Circle()
        circle.set_fill(BLUE, opacity=0.5)
        circle.set_stroke(BLUE_E, width=4)

        self.add(circle)
```

More examples can be gotten from [Grant Sanderson of 3Blue1Brown](https://github.com/3b1b/videos)