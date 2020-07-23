[🏠 Start](https://jeanluc2305.github.io/Discord/)

# tnwz2

#### Beschreibung:

Gibt den angegebenen Usern die Rolle für den zweiten WZ bei Terranova

#### Benutzung:

[Prefix]tnwz2 User User User usw.

<span style="color:red">⚠ Achtung! Kann nur von Terranova verwendet werden!</span>

#### Beispiel:

[Prefix]tnwz2 Jean-Luc Knalli Chris

#### Code:

```
{set;~roles;635111745740079105}
{switch;true;
  {hasrole;{get;~roles}};
  {void};
  x Du hast leider nicht die nötigen Berechtigungen!!!
  {return}}

{if;{args};==;leeren;
  {void;{foreach;~member;{rolemembers;729355171859136542;quiet};{roleremove;729355171859136542;{get;~member};quiet}}}Rolle TN-WZ2 geleert!{return}}


{set;~names;{argsarray}}

{void;{foreach;~name;{get;~names};{roleadd;729355171859136542;{get;~name};quiet}}}

Mitglieder zu WZ2 hinzugefügt, bitte Mitglieder überprüfen!
```
