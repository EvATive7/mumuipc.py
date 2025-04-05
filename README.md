<div align="center">

# mumuipc.py

Python SDK for MumuPlayer IPC.

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/EvATive7/mumuipc.py/package.yml)](https://github.com/EvATive7/mumuipc.py/actions)
[![Python](https://img.shields.io/pypi/pyversions/mumuipc.py)](https://pypi.org/project/mumuipc.py)
[![PyPI version](https://badge.fury.io/py/mumuipc.py.svg)](https://pypi.org/project/mumuipc.py)
[![Coverage Status](https://coveralls.io/repos/EvATive7/mumuipc.py/badge.svg?branch=develop&service=github)](https://coveralls.io/github/EvATive7/mumuipc.py?branch=master)
[![License](https://img.shields.io/github/license/EvATive7/mumuipc.py.svg)](https://pypi.org/project/mumuipc.py/)

</div>

## Usage

Install the package using pip: `pip install mumuipc.py`

```python
from pathlib import Path

from PIL import Image
from mumuipc import MuMuPlayer

# Assuming the path and index of the simulator
emu_path = Path(r"C:\Program Files\Netease\MuMuPlayer-12.0")
emu_index = 0

# Create an instance of MuMuPlayer
player = MuMuPlayer(emu_path, emu_index)

# capture screenshots
screenshot = player.ipc_capture_display(0)

if screenshot is not None:
    screenshot_image = Image.fromarray(
        screenshot.reshape(player.resolution[1], player.resolution[0], 4), "RGBA"
    )
    screenshot_image.save("screenshot.png")
    print("Screenshot has been saved as screenshot.png")
else:
    print("Unable to capture screenshots")

# Disconnect the connection from the simulator
player.ipc_disconnect()

```

## Platform

Only Windows is supported?
