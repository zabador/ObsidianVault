# Changing mod keys to match Mac

First we need to find out what keys are what. We can do this by running xev

In the terminal type

```shell
xev
```

Then click the control key to get the keycode. You should see something like this

```
KeyPress event, serial 33, synthetic NO, window 0x3200001,
    root 0x5c5, subw 0x0, time 11178484, (-699,647), root:(2827,689),
    state 0x0, keycode 37 (keysym 0xffeb, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

You can do the same with the Windows key which should say Super_L and the Alt key.

Once you have these keys you need to change the xmodmap.

Copy the original keybinding to a file in your home directory call .Xmodmap

```shell
xmodmap -pke > ~/.Xmodmap
```

In the file you will wan to edit the keycodes. For example my keycodes were

Left Control = Keycode 37
Left Alt = Keycode 64
Left Super = Keycode 133

Open the an the  ``` Xmodmap```  file in an editor and change the keycode lines

```
keycode  37 = Super_L NoSymbol Super_L
keycode 133 = Alt_L Meta_L Alt_L Meta_L
keycode  64 = Control_L NoSymbol Control_L

```

Once this is done the keys will act like a Mac keyboard in any desktop manager.

## Update new Keys in AwesomeWM

The updated keys will only work in a desktop manager. To update Awesome Window manger we will have to update the ``` Xmodmap``` file again

Open the file and at the top of the file add

```
clear control
clear mod1
clear mod4
```

And at the bottom of the file add

```
clear control
clear mod1
clear mod4

```
