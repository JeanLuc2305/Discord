[🏠 Start](https://jeanluc2305.github.io/Discord/)

# sru

#### Beschreibung:

Zeigt die Anzahl der User einer Rolle an

#### Benutzung:

`botsru Rollenname`

#### Beispiel:

`botsru Neuling`

#### Ergebnis:

![Ergebnis](https://dub01pap001files.storage.live.com/y4mAVG8-6GFoqtGsENWUf4xJqTM8IUedrLFhBt0hh3ncYgeXZTzUflIYO-0UTYQm34PgDAmb7lNc2pIl_Fby0sHUHtDeDFdLRJY7YmTNX8kzdYYSJNenqOF2a7gO6oeKSH7g6yq9FDNKS7docoX9QGVcKhgGDv0wg3k0l01gYEYzMwAS_Y6Z_x34AnFxH8_GM_t?width=358&height=110&cropmode=none)

#### Code:

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
