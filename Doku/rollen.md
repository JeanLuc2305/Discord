[🏠 Start](https://jeanluc2305.github.io/Discord/)

# rollen

#### Beschreibung:

Zeigt alle Rollen eines Users

#### Benutzung:

`botrollen User`

#### Beispiel:

`botrollen Jean-Luc`

#### Ergebnis:

![Ergebnis](https://dub01pap001files.storage.live.com/y4m_ZteJTHChddfMu-cZsKh9hrDKI0rxBZNCj6692JoyDDVgKWj6qabp-Mi6yaYB8JSbfioonKGBHQxd79TAJLQiXtlvwfrszwPNGOP_CovasxGl0XNKCXXzr0Z446ylb4_0RKvjupFc4UERgN9l_6_5Je0TYBRnYkA34k-q_p8rMj-y1qQGAThRfcSQ9birM2K?width=435&height=222&cropmode=none)

#### Code:

```
{set;var1;{args}}

{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{if;{args};>;;
{if;{usernick;{args} ;quiet};==;;
  {embed;{buildembed;
  color:{get;~eColor;0};
  title:Bitte nenne einen vorhandenen User.;
description:
-------------------------------
Der von dir genannte User existiert nicht. Idiot! 😂
{return}
}}}} 

{if;{get;var1};!=;;
  {embed;{buildembed;
  color:{get;~eColor;0};
  title:__{usernick;{get;var1};quiet} hat folgende Rollen:__;
  thumbnail.url:{useravatar;{args}};
description:{foreach;~role;{roles;{get;var1};quiet};{rolename;{get;~role}}{newline}}------------------------------------
✅ Ich habe {length;{roles;{get;var1}}} Rollen gefunden.
    {return}}};

{embed;{buildembed;
  color:{get;~eColor;0};
  title:__Alle Rollen bei {guildname}:__;
  thumbnail.url:{guildicon};
description:
{foreach;~role;{roles};{rolename;{get;~role}}{newline}}------------------------------------
✅ Ich habe {length;{roles}} Rollen gefunden.{newline;2}
*Zur Info: `{prefix}{commandname} User` zeigt dir die Rollen eines Users!*
 {return}
}}} 
```
