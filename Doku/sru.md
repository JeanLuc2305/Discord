[🏠 Start](https://jeanluc2305.github.io/Discord/)

# sru

###### Beschreibung:

Zeigt alle Rollen eines Users

###### Benutzung:

[Prefix]sru Rollenname

###### Beispiel:

[Prefix]sru Neuling

###### Ergebnis:

![Ergebnis](https://cdn.discordapp.com/attachments/642357675283316747/734104008138162266/unknown.png)

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

description:
✅ Ich habe {length;{rolemembers;{get;~roleID}}} Leute in dieser Rolle gefunden.
{return}
}}
```
