# Fdf

`11-01-2016`
`1 week`
`1 person`

---

_This project consist of creating a wireframe schematic graphical representation of a terrain in relief by linking different points (x, y, z) with segments._

__Installation:__

* `git clone https://github.com/wwatkins42/42_C_Projects.git`
* `cd ./42_C_Projects/Fdf`
* `make`
* `./fdf [map file_path]`

**Usage:**
* `./fdf [map file_path] [-p file_path] [-w width] [-h height] [--help]`

**Options:**
* `-p` [`file_path`] loads with a defined color palette.
* `-w` [`window_width`] loads with defined window width.
* `-h` [`window_height`]  loads with defined window height.
* `--help`  display help text.

**Example:**
* `./fdf maps/pylone.fdf -p palette/palette.fdfcolor -w 1500 -h 1200`

**Keys:**
* &#8593; &#8592; &#8595; &#8594;: move around
* `+` `-`: zoom
* `m`: change draw method
* `p`: change color (only if multiple color are in loaded palette, if loaded)
* `i` `k`: change maximum terrain elevation
* &#8670; &#8671;: change color elevation

![fdf_screenshot_2](https://cdn.rawgit.com/wwatkins42/42_C_Projects/master/screenshots/screenshot_fdf_2.png "fdf")
![fdf_screenshot_1](https://cdn.rawgit.com/wwatkins42/42_C_Projects/master/screenshots/screenshot_fdf_1.png "fdf")

&#8592; [Index](https://wwatkins42.github.io/index)
