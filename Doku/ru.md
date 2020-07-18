[🏠 Start](https://jeanluc2305.github.io/Discord/)

# ru

###### Beschreibung:

Zeigt alle User einer Rolle an

###### Benutzung:

[Prefix]ru Rollenname

###### Beispiel:

[Prefix]chname Neuling

###### Ergebnis:

![Ergebnis](https://cdn.discordapp.com/attachments/642357675283316747/734093135290040340/unknown.png)

###### Code:

```
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{//;Test if the person specified any words/names:}
{if;{argslength};<=;0;
  {embed;{buildembed;
  color:{get;~eColor;0};
  title:Bitte nenne eine Rolle. Idiot! 😂;
description:-------------------------------
Beispiel: {prefix}{commandname} {randchoose;Besucher;Regelwerk}
Mit **{prefix}rollen** erhältst du eine Übersicht.
  {return}
}}}

{//;Check if the specified words/names match an existing role:}
{set;~roleID;{roleid;{args};quiet}}
{if;{get;~roleID};==;;
  {embed;{buildembed;
  color:{get;~eColor;0};
  title:Bitte nenne eine vorhandene Rolle.;
description:
-------------------------------
Die Rolle existiert nicht du Idiot! 😂
Mit **{prefix}rollen** erhältst du eine Übersicht.
{return}
}}}

{//;If everything checks out, show a list of users in the specified role:}
{embed;{buildembed;
  color:{get;~eColor;0};
  title:Mitglieder der Rolle {rolename;{get;~roleID};quiet}:;

description:{foreach;~role;
  {rolemembers;{get;~roleID}};{void;{get;~role}}{usernick;{get;~role};quiet}{newline}}------------------------------------
✅ Ich habe {length;{rolemembers;{get;~roleID}}} Leute in dieser Rolle gefunden.
{return}
}}
```
