= Alps Touchpad =

== Installation ==

    packer -S psmouse-alps-driver
    pacman -S xorg-xinput

This will install the alps touchpad driver and you should be able to scroll.

== Configuration ==

To make the touchpad (but not the mouse) scroll in the natural direction (like
OSX), you first need to find its xinput id:

    xinput list | egrep "slave.*pointer" | grep -v XTEST | sed -e 's/^.*id=//' -e 's/\s.*$//'

It should be 11.

Now we have our id number, we can find out what the current input order is. For
this, we use the following command:

    xinput get-button-map 11

The output is:

    1 2 3 4 5 6 7 8 9 10 11 12

Now we have to invert the scrolling by setting:

    xinput set-button-map 11 1 2 3 5 4 7 6 8 9 10 11 12


