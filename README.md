# CCTools
Tools for working with CC1 (DAT) and CC2 (C2M) files.

### [CC1 Class](https://github.com/ChipMcCallahan/CCTools/blob/main/src/cc1.py#L10-L344)
```python
from cc_tools import CC1
```
This class is basically an enum of CC1 tile codes, along with some very useful utilities as described below.
#### Direction Utils
```python
tank = CC1.TANK_N
print(tank.left())
print(tank.reverse())
print(tank.right())
```
```
CC1.TANK_W
CC1.TANK_S
CC1.TANK_E
```
This works for ice corner tiles such as `CC1.ICE_NW`. If an element cannot be rotated, the same element is returned.  

You can also get the directions on an element, or update the element with new directions.
```python
ice_corner = CC1.ICE_SE
print(ice_corner.dirs())
print(ice_corner.with_dirs("NW"))
```
```
SE
CC1.ICE_NW
```
#### Element Set Utils
Easily make comparisons using prebuilt element sets.
```python
for e in (CC1.TANK_N, CC1.BLOCK, CC1.PLAYER_N, CC1.NOT_USED_0):
    print("-" * 20)
    if e in CC1.tanks():
        print(f"{e} is a tank.")
    if e in CC1.blocks():
        print(f"{e} is a block.")
    if e in CC1.players():
        print(f"{e} is a player.")
    if e in CC1.monsters():
        print(f"{e} is a monster.")
    if e in CC1.mobs():
        print(f"{e} is a mob.")
    if e in CC1.invalid():
        print(f"{e} is invalid.")
```
```
--------------------
CC1.TANK_N is a tank.
CC1.TANK_N is a monster.
CC1.TANK_N is a mob.
--------------------
CC1.BLOCK is a block.
CC1.BLOCK is a mob.
--------------------
CC1.PLAYER_N is a player.
CC1.PLAYER_N is a mob.
--------------------
CC1.NOT_USED_0 is invalid.
```
See [the code](https://github.com/ChipMcCallahan/CCTools/blob/main/src/cc1.py#L196-L344) for a full list of prebuilt element sets.

### [CC1Cell Class](https://github.com/ChipMcCallahan/CCTools/blob/main/src/cc1.py#L347-L404)
```python
from cc_tools import CC1Cell
```
This class represents a single (x, y) location in a CC1 Level. It holds two CC1 elements (`top` and `bottom`). It can intelligently add and remove elements while doing its best to maintain CC1 validity; however, **it is always recommended to use the CC1Level object to add or remove elements, since the CC1Level object will also update trap controls, clone controls, and movement data**.

### [CC1Level Class](https://github.com/ChipMcCallahan/CCTools/blob/main/src/cc1.py#L407-L490)
```python
from cc_tools import CC1Level
```

### [CC1Levelset Class](https://github.com/ChipMcCallahan/CCTools/blob/main/src/cc1.py#L493-L498)
```python
from cc_tools import CC1Levelset
```

### [DATHandler Class](https://github.com/ChipMcCallahan/CCTools/blob/main/src/dat_handler.py#L63-L374)
```python
from cc_tools import DATHandler
```

### [CC1LevelTransformer Class](https://github.com/ChipMcCallahan/CCTools/blob/main/src/cc1.py#L501-L641)
```python
from cc_tools import CC1LevelTransformer
```

### [C2MHandler Class](https://github.com/ChipMcCallahan/CCTools/blob/main/src/c2m_handler.py#L95-L279) (Limited Functionality)
```python
from cc_tools import C2MHandler
```

### [CC1LevelImager Class](https://github.com/ChipMcCallahan/CCTools/blob/main/src/cc1.py#L644-L814) (Limited Functionality)
```python
from cc_tools import CC1LevelImager
```
