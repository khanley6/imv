imv - X11/Wayland Image Viewer
==============================

`imv` is a command line image viewer intended for use with tiling window managers.

Features
--------

* Wayland Support
* Support for over 30 different image file formats including:
  * Photoshop PSD files
  * Animated GIFS
  * Various RAW formats

Usage
-----

### Opening images
    imv image1.png another_image.jpeg yet_another.TIFF

### Opening images via stdin
    find . "*.png" | imv -

### Autoscale images to fit the window
    imv -s *.gif

### Open an image fullscreen (and scale to fit screen)
    imv -fs image.jpeg

### Viewing images in a random order
    find . "*.png" | shuf | imv -

### Image picker
imv can be used to select images in a pipeline by using the `p` hotkey to print
the current image's path to stdout. The `-l` flag can also be used to tell imv
to list the remaining paths on exit for a "open set of images, close unwanted
ones with `x`, then quit imv to pass the remaining images through" workflow.

#### Picking a wallpaper
    custom-set-wallpaper-script "$(find ./wallpaper -type f -name '*.jpg' | imv - | tail -n1)"

#### Deleting unwanted images
    find -type f -name '*.jpg' | imv - | xargs rm -v

#### Choosing pictures to email
    find ./holiday_pics -type f -name '*.jpg' | imv - | xargs cp -t ~/outbox

### Slideshow

imv can be used to display slideshows. You can set the number of seconds to
show each image for with the `-t` option at start up, or you can configure it
at runtime using the `t` and `T` hotkeys to increase and decrease the image
display time, respectively.

To cycle through a folder of pictures, showing each one for 10 seconds:

    imv -t 10 ~/Pictures/London

Installation
------------

`imv` depends on `pthreads`, `FontConfig`, `SDL2`, `SDL_TTF`, and `FreeImage`.

    $ make
    # make install

Tests
-----

`imv` has a work-in-progress test suite. The test suite requires `cmocka`.

    $ make check

Contact
-------

There's an official irc channel for imv discussion and development on
Freenode: `#imv`.

License
-------
`imv` is published under the [GPLv2](LICENSE) license.
