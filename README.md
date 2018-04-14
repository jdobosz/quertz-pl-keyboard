# quertz-pl-keyboard
Polish Programmers Layout for German QWERTZ keyboard

## Windows

Polish Programmers keyboard driver is used to input special polish characters like ą, ń, ć, ł, ó using AltGr modifier key and corresponding latin character a ,n, c, l, o.

In Windows this driver is made based on the QWERTY keyboard layout and using it with the German QWERTZ keyboard layout is very confusing because the position of slashes, braces, etc. is quite different than in classic QWERTY keyboard layout.
The situation in Windows 7/10 is better, because Polish Programmers keyboard driver works with QWERTY keyboard layout except the € character which is mapped at the place where polish character ę is expected to be found.
Because I could not found any solution satisfying my needs I decided to make my own keyboard driver (MSKLC)[http://msdn.microsoft.com/en-us/goglobal/bb964665.aspx]- Microsoft Keyboard Layout Creator. This is very easy and straight forward tool, so making new keyboard driver takes really few minutes.


The Keyboard driver I prepared has also another advantage. I can type german and polish special characters without switching between keyboard layouts.
In order to resolve the issue with the € character I mapped the key R to input € and the combination AltGr-e produces polish ę.

The installation program with could be downloaded here [qwertz_pl.zip](resources/qwertz_pl.zip).

Unzip it in the directory of your choice and start setup.exe. The new keyboard will be added to the input services in the Regional and Language Options:

![](resources/kbd.jpg)

You can also download the keyboard definition file [qwertz_pl.klc](resources/qwertz_pl.klc), load it into MSKLC tool an create layout of your choice.

## Linux

On linux system the similar mapping can be added in x11 keybord layout defition file.
Dependend on distribution, the directory is /usr/share/X11/xkb/symbols or /etc/X11/xkb/symbols.
Just open the "de" file and add following entries

```
default
xkb_symbols "basic" {

    include "latin(type4)"

    name[Group1]="German";

    key <AE02>	{ [         2,   quotedbl,  twosuperior,    oneeighth ]	};
    key <AE03>	{ [         3,    section, threesuperior,    sterling ]	};
    key <AE04>	{ [         4,     dollar,   onequarter,     currency ]	};

    key <AE11> {type[Group1]="FOUR_LEVEL_PLUS_LOCK",  symbols[Group1]=
                  [ssharp, question, backslash, questiondown, 0x1001E9E ]};

    key <AE12>	{ [dead_acute, dead_grave, dead_cedilla,  dead_ogonek ]	};

    key <AD03>	{ [ e, E, eogonek,            Eogonek ]	};
    key <AD04>	{ [ r, R, EuroSign,           EuroSign ]	};
    key <AD06>	{ [ z, Z, zabovedot,          Zabovedot ]	};
    key <AD09>	{ [ o, O, oacute,             Oacute ]	};
    key <AC01>  { [ a, A, aogonek,            Aogonek   ] };
    key <AC02>  { [ s, S, sacute,             Sacute   ] };
    key <AC07>  { [ j, J, dead_belowdot,      dead_abovedot   ] };
    key <AC09>	{ [ l, L, lstroke,            Lstroke ] };
    key <AB01>	{ [ y, Y, guillemotright,     U203A 	] };
    key <AB02>	{ [ x, X, zacute,             Zacute 	] };
    key <AB03>  { [ c, C, cacute,             Cacute   ] };
    key <AB04>	{ [ v, V, doublelowquotemark, singlelowquotemark ]	};
    key <AB05>	{ [ b, B, leftdoublequotemark,leftsinglequotemark ] };
    key <AB06>	{ [ n, N, nacute,             Nacute ]	};


    include "kpdl(comma)"

    include "level3(ralt_switch)"
};
```