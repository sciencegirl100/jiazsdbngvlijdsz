# Alternate Slicer Instruction (Experimental)

**Don't do this until we verify**

1.  Open the Kisslicer link on the desktop
2.  Load your stl
3.  Slice
4.  Save (should save with a .bfb ext)
5.  Open CodeX32 link on the desktop
    1.  Printer: CubePro
    2.  Function: EnCode
    3.  Input File: your.brb
    4.  Output File: youre.cube (cubepro file should work with cube ext)

## References

You can use a regular slicer and convert it to .cube code See this
[Thread](https://groups.google.com/forum/#!topic/kisslicer-refugee-camp/ZMuIrtn5Mfo)

Here's a [Thread](http://www.kisslicertalk.com/viewtopic.php?f=20&t=353)
specific to the cube 2

Another
[Thread](http://cube3d.createaforum.com/general-discussion/alternative-slicer-to-the-cubes-standard-software/).
This seems to be the latest.

## Troubleshooting Notes

- Decoding a .cube file generated by cubes software and re-encoding with
  cubepro setting and then renaming file .cube seems to work. Using
  cubex setting does not work.
- Setting Filament parameter to -1 does not cause an error
- Setting Time to 0 does not cause an error

[Category:Cube](Category:Cube "wikilink")