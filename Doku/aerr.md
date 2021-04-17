[🏠 Start](https://jeanluc2305.github.io/Discord/)

# tnrr

#### Beschreibung:

Gibt den angegebenen Usern die Freigabe für den RR-Bereich von Titan A.E.

#### Benutzung:

[Prefix]aerr list → Listet alle User die für den Bereich freigegeben sind

[Prefix]aerr User User User usw. → Hinzufügen

[Prefix]aerr entf User User User usw. → Entfernen

<span style="color:red">⚠ Achtung! Kann nur von Titan A.E. verwendet werden!</span>

#### Beispiel:

[Prefix]aerr Ryker Sl3nderm4n Akkon

#### Code:

```
{set;~roles;814906780403761192}
{set;~roleID;832929940541538344}

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
