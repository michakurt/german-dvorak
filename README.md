# german-dvorak
Ein paar Dateien, um Dvorak mit deutschen Umlauten zu unterstützen

# Low-Level Vertauschung von CapsLock und LeftCtrl

Manchmal passiert es, dass sich diese beiden Tasten nicht in allen Anwendungen mit den Mitteln des X-Window-Systems vertauschen lassen.
Das trifft unter anderem auf VirtualBox zu.

In diesem Fall muss man auf einer tieferen Ebene ansetzen:

Dazu die Datei `99-capslockToCtrl.hwdb` in `/etc/udev/hwdb.d` mit folgendem Inhalt erstellen
```
#Siehe https://yulistic.gitlab.io/2017/12/linux-keymapping-with-udev-hwdb/
evdev:atkbd:dmi:* #eingebautes Laptop-Keyboard
  KEYBOARD_KEY_1d=capslock     # leftctrl=capslock
  KEYBOARD_KEY_3a=leftctrl     #capslock=leftctrl

evdev:input:b0003v0603p* 
  KEYBOARD_KEY_700e0=capslock     # leftctrl=capslock
  KEYBOARD_KEY_70039=leftctrl     # capslock=leftctrl
```
Möchte man bei einem Keyboard mit kleiner linker Shift-Taste die die Taste neben der Shift-Taste, die man beim Dvorak-Layout nicht braucht, zu Shift machen (um das Handgelenk nicht so drehen zu müssen), kann man das mit folgendem Mapping erreichen:
```
evdev:atkbd:dmi:* #eingebautes Laptop-Keyboard
  KEYBOARD_KEY_56=leftshift     # Die Taste rechts neben der kleinen Shift-Taste

evdev:input:b0003v0603p*
  KEYBOARD_KEY_70064=leftshift     # Die Taste rechts neben der kleinen Shift-Taste

```

Dann mit den Kommandos
```
udevadm --debug hwdb --update
``` 
und
```
udevadm trigger
```
aktivieren.

Die evdev-Patterns bekommt man z.B. durch `evtest` und bestehen aus bus, vendor und produkt-ids. Die Scancodes können auch mit diesem Programm ermittelt werden.
