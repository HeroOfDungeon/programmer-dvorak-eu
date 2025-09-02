# Dvorak for Programmers with European Keys
Forked from https://www.github.com/asvd/programmer-dvorak-eu/, make sure to check it out!

## About
It all started when I didn't like the order of the numbers that much, so I decided to modify it to look similar to QWERTY. After that, I started changing the third and fourth layers, and now I'm here.

## Layout
```
Default
     $ & \[ { } ( = * ) + ] ! # Delete
  Tab ; , . p y f g c r l / @ Enter
  Caps a o e u i d h t n s - \ Enter
Shift \ ' q j k x b m w v z Shift

Shift
     ~ % 1 2 3 4 5 6 7 8 9 0 ` Delete
  Tab : < > P Y F G C R L ? ^ Enter
  Caps A O E U I D H T N S _ | Ener
Shift | " Q J K X B M W V Z Shift

AltGr
...
```

## Manual installation on (Ubuntu) Linux

All the actions below are to be performed under **#root**

```sh
$ sudo su
```

- insert the contents of the [us-dpe](https://raw.githubusercontent.com/HeroOfDungeon/programmer-dvorak-eu/refs/heads/master/us-dpe) layout at the very end of `/usr/share/X11/xkb/symbols/us`

- open `/usr/share/X11/xkb/rules/evdev.xml` and find the `us` layout configuration starting with something like

 ```xml
 <layout>
   <configItem>
     <name>us</name>

     <shortDescription>en</shortDescription>
     <description>English (US)</description>
     <languageList>
       <iso639Id>eng</iso639Id>
     </languageList>
   </configItem>
 ```

- in the beginning of the `<variantList>` below the layout header, insert the variant configuration for the new layout:

 ```xml
 <variant>
   <configItem>
     <name>dpe</name>
     <description>English (Programmer Dvorak Eur. Keys)</description>
   </configItem>
 </variant>
 ```

- delete xkb cache:

 ```
 # rm /var/lib/xkb/*.xkm
 ```
or

 ```
 # dpkg-reconfigure xkb-data
 ```

Now the new layout should be selectable in the system settings window as a variant of English layout
