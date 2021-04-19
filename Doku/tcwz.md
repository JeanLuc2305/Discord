[🏠 Start](https://jeanluc2305.github.io/Discord/)

# tnrr

#### Beschreibung:

Gibt den angegebenen Usern die Freigabe für den WZ-Bereich von Titan Corp

#### Benutzung:

[Prefix]tcwz list → Listet alle User die für den Bereich freigegeben sind

[Prefix]tcwz [User] [ser] [User] usw. → Hinzufügen

[Prefix]tcwz entf [User] [User] [User] usw. → Entfernen

<span style="color:red">⚠ Achtung! Kann nur von Titan Corp verwendet werden!</span>

#### Beispiel:

[Prefix]tcwz Daremar Dages Bender

#### Code:

```
{set;~roles;635100637230792714}
{set;~roleID;638439607054368771}

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
