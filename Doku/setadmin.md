[🏠 Start](https://jeanluc2305.github.io/Discord/)

# setadmin

#### Beschreibung:

Fügt die angegebenen Usern dem Admin-Team hinzu.

#### Benutzung:

`botsetadmin User User User usw.`

<span style="color:red">⚠ Achtung! Kann nur vom Admin-Team verwendet werden!</span>

#### Beispiel:

`botsetadmin Jean-Luc chris85`

#### Code:

```
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}


{set;~roles;640978279532199946}
{switch;true;
  {hasrole;{get;~roles}};
  {void};
  x Du hast leider nicht die nötigen Berechtigungen!!!
  {return}}

{set;~names;{argsarray}}

{void;{foreach;~name;{get;~names};{roleadd;640978279532199946;{get;~name};quiet}}}

{embed;{buildembed;
  color:{get;~eColor;0};
  title:Mitglied/er hinzugefügt zur Rolle {rolename;640978279532199946;quiet}:;

description:{foreach;~role;
  {rolemembers;640978279532199946};{void;{get;~role}}{usernick;{get;~role};quiet}{newline}}------------------------------------
✅ Ich habe {length;{rolemembers;640978279532199946}} Leute in dieser Rolle gefunden.
{return}
}}
```