[🏠 Start](https://jeanluc2305.github.io/Discord/)

# tnwz2

#### Beschreibung:

Gibt den angegebenen Usern die Rolle für den zweiten WZ bei Terranova

#### Benutzung:

[Prefix]tnwz2 list → Listet alle User die für den Bereich freigegeben sind

[Prefix]tnwz2 [User] [ser] [User] usw. → Hinzufügen

[Prefix]tnwz2 entf [User] [ser] [User] usw. → Entfernen

[Prefix]tnwz2 leeren → leert die komplette Rolle

<span style="color:red">⚠ Achtung! Kann nur von Terranova verwendet werden!</span>

#### Beispiel:

[Prefix]tnwz2 Jean-Luc Knalli Chris

#### Code:

```
{set;~roles;635111745740079105}
{set;~roleID;729355171859136542}

{switch;true;
  {hasrole;{get;~roles}};
  {void};
  x Du hast leider nicht die nötigen Berechtigungen!!!
  {return}}

{set;~names;{argsarray}}

{func;list;
  {embed;{buildembed;
    title:Mitglieder der Rolle {rolename;{get;~roleID};quiet}:;
    description:{foreach;~role;{rolemembers;{get;~roleID}};{void;{get;~role}}{usernick;{get;~role};quiet}{newline}}------------------------------------
  ✅ Ich habe {length;{rolemembers;{get;~roleID}}} Leute in dieser Rolle gefunden.
  }}
}

{if;{args;0};==;list;
  {func.list}
  {return}
}

{if;{args};==;leeren;
  {void;{foreach;~member;{rolemembers;{get;~roleID};quiet};{roleremove;{get;~roleID};{get;~member};quiet}}}
  ✅ Rolle geleert, bitte überprüfen!
  {func.list}
  {return}
}

{if;{args;0};==;entf;
  {void;{foreach;~member;{get;~names};{roleremove;{get;~roleID};{get;~member};quiet}}}
  ✅ Mitglied/er entfernt, bitte überprüfen!
  {func.list}
  {return}
}

{void;{foreach;~name;{get;~names};{roleadd;{get;~roleID};{get;~name};quiet}}}

✅ Mitglied/er hinzugefügt, bitte überprüfen!
{func.list}
```
