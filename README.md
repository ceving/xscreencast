# xscreencast

Record screen based on keyboard events into an animated GIF.  The
script monitors the X server keyboard events and captures a screen
after every `KeyRelease` event.  If you do not type anything no screen
gets recorded. This keeps the GIF small, if nothing interesting
happens on the screen.  The script measures the time between the
events and writes the delays into the GIF.  Recording gets activated
and deactivated by pressing the <kbd>Print</kbd> key.

I wrote the script for a question at [Stackexchange][1].  The question
contains two example screen casts.

[1]: https://emacs.stackexchange.com/questions/18607/how-to-set-the-foreground-color-of-the-cursor-face

This is a screen shot taken after a recording session.

![screenshot](screenshot.png)

It is not possible to record two screens at the same time.  That is
the reason, why I can not show a screen cast from `xscreencast`.

The script requires the following tools: `xwininfo`, `xinput`, `xwd`,
`convert`.  The first three are standard tools of the X server.

    $ dpkg -S $(type -p xinput xwininfo xwd)
    xinput: /usr/bin/xinput
    x11-utils: /usr/bin/xwininfo
    x11-apps: /usr/bin/xwd

The last is the graphics conversion tool ImageMagick.

    $ dpkg -S $(readlink -f $(type -p convert))
    imagemagick-6.q16: /usr/lib/i386-linux-gnu/ImageMagick-6.8.9/bin-Q16/convert

### Limitations

Right now only keyboard events will trigger the screen recording.  It
might be possible to extend the script for mouse events but I did not
need it.
