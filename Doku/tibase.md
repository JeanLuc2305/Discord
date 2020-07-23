[🏠 Start](https://jeanluc2305.github.io/Discord/)

# tibase

#### Beschreibung:

Erstellt Nickname für Titan Basecamp und vergibt die entsprechende Rolle

#### Benutzung:

`bottibase User`

<span style="color:red">⚠ Achtung! K Kann nur von Titan Corp verwendet werden!</span>


#### Beispiel:

`bottibase Jean-Luc`

#### Code:

```
{//; unterdrückt Fehler vom Lookup-System} 
{suppresslookup}

{set;falscherUser;❌ {args;0} scheint kein Mitglied dieses Servers zu sein oder du hast dich vertippt!}
{set;~corpname;Titan Basecamp}
{set;~allyrole;635106983682375730}
{set;~newrole;731804812722569276}

{delete}

{//; Setzen der Farbe für Embed}
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}


{//;Sicherheitsüberprüfung, Herren der Bots, Mitglied Konzern}
{set;~rol;["640978279532199946", "635101067721441310"]}
{switch;true;
  {hasrole;{get;~rol}};
  {void};
  {embed;{embedbuild
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:❌ Du hast leider nicht die nötigen Berechtigungen!
}}
{return}}

{//; Überprüfen der Argument-Anzahl}
{if;{argslength};<;1;
    __**Command Name**__: {commandname}    
    __**Usage**__: {prefix}{commandname} <user>
    {return}
}

{//; Überprüfen des Users}
{set;~userid;{userid;{args;0}}}
{if;{get;~userid};==;;{set;~msgfk;{send;{channelid};{get;falscherUser}}}{timer;{delete;{get;~msgfk}};10s}{return}}
{set;~username;{username;{get;~userid}}}
{set;~usernick;{usernick;{get;~userid}}}

{//; Rollen Ally und Konzern hinzufügen}
{void;{roleadd;{get;~allyrole};{get;~usernick};quiet}}
{void;{roleadd;{get;~newrole};{get;~usernick};quiet}}
{set;~msgidrole;{send;{channelid};✅ Die Rollen {rolename;{get;~newrole}} und {rolename;{get;~allyrole}} wurden für {get;~usernick} hinzugefügt}}
{modlog;Roleadd;{userid};;Rolle {rolename;{get;~allyrole}} hinzugefügt für {get;~usernick};{get;~eColor}}
{modlog;Roleadd;{userid};;Rolle {rolename;{get;~newrole}} hinzugefügt für {get;~usernick};{get;~eColor}} 
{timer;{delete;{get;~msgidrole}};10s}
{delete}

{//;Nickname mit Konzernname erstellen}

{set;~basenick;{get;~usernick}}
{while;{get;~basenick};includes;[; {//;remove all bracketed parts}
  	{set;~openbracket;{indexof;{get;~basenick};[}}
  	{set;~closebracket;{indexof;{get;~basenick};]}}
  	{set;~base1;{substring;{get;~basenick};0;{math;-;{get;~openbracket};1}}}
    {set;~base2;{substring;{get;~basenick};{math;+;{get;~closebracket};1}}}
    {set;~basenick;{get;~base1}{get;~base2}}
}

{set;~newnick;{trim;{get;~basenick}} [{get;~corpname}]
}

{if;{length;{get;~newnick}};<=;32;
    {if;{setnick;{get;~newnick};{get;~userid}};includes;Der Nickname konnte nicht geändert werden.;
        ❌ Umbenennen von `{get;~usernick}` zu `{get;~newnick}`nicht erfolgreich. Wahrscheinlich ein Berechtigungsproblem.
    ;
        {set;~msg;✅ Erfolgreich `{get;~usernick}` zu `{get;~newnick}` umbenannt.}
    }
;
    ❌ `{get;~newnick}` überschreitet 32 Zeichen.
}
{//; setzt Nickname nach Vorgabe}
{set;_{get;~userid}_usernick;{usernick;{get;~userid}}}

{if;0{length;{get;~msg}};
  {set;~msgid;{send;{channelid};{get;~msg}}}
}

{timer;{delete;{get;~msgid}};10s}
```
