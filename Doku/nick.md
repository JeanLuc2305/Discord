[🏠 Start](https://jeanluc2305.github.io/Discord/)

# nick

#### Beschreibung:

Erstellt Nickname mit Konzern und gibt Rechte für den angegebenen Konzern.

#### Benutzung:

`botnick Username Konzern`  
  

<span style="color:yellow">Username darf kein Leerzeichen enthalten, falls notwendig in Anführungszeichen setzen.</span>

Konzern wird als Kürzel angeben:

| Konzern      | Kürzel |
|--------------|--------|
| Austria      | AT     |
| Enigma       | EN     |
| Ezco         | EZ     |
| Hermes       | HS     |
| Hydra        | HY     |
| Kumzumir     | KM     |
| Tardis       | TA     |
| Terranova    | TN     |
| Titan Corp   | TC     |
| Hinterm Mond | HM     |

<span style="color:red">⚠ Achtung! Nur Mitglieder mit der Rolle Admin können die Berechtigung vergeben und das auch nur für den eigenen Konzern!</span>


##### Beispiel:

`botnick Jean-Luc TN`


##### Code:

```
{//; unterdrückt Fehler vom Lookup-System}
{suppresslookup}

{//; Variablen setzen}
{set;guestrole;637763780520050688}
{set;allyrole;635106983682375730}
{set;regelwerk;637763780520050688}
{set;neuling;637784554643390464}
{set;austria;635102610864603136}
{set;enigma;639392133270470656}
{set;ezco;638788269168918538}
{set;hermes;635109388868255764}
{set;hydra;635109995461083137}
{set;terranova;635111745740079105}
{set;titan;635101067721441310}
{set;mond;643218498696380416}
{set;falscherKonzern;❌ Du bist leider nicht im gleichen Konzern, um die Berechtigung setzen zu können!}
{set;keineRechte;❌ Du hast leider nicht die nötigen Berechtigungen, du musst Mitglied der Rolle "Admin" sein!}
{set;falscherUser;❌ {args;0} scheint kein Mitglied dieses Servers zu sein oder du hast dich vertippt!}

{delete}

{//; Setzen der Farbe für Embed}
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{//; Rollenabfrage Herren der Bots, Admin}
{set;~rol;["640978279532199946", "635099470413037618"]} 
{switch;true;
  {hasrole;{get;~rol}};
  {void};
  {set;~msgfk;{send;{channelid};{get;keineRechte}}}{timer;{delete;{get;~msgfk}};10s}
  {return}
}

{//; Überprüfen der Argument-Anzahl}
{if;{argslength};<;1;
    __**Command Name**__: {commandname}    
    __**Usage**__: !{commandname} <user> [corp]
    {return}
}

{//; Überprüfen des Users}
{set;~userid;{userid;{args;0}}}
{if;{get;~userid};==;;{set;~msgfk;{send;{channelid};{get;falscherUser}}}{timer;{delete;{get;~msgfk}};10s}{return}}
{set;~username;{username;{get;~userid}}}
{set;~usernick;{usernick;{get;~userid}}}

{//; Konzern neu setzen}
{set;~corp;{lower;{args;1}}}

{//; Konzernerkennung}
{if;{get;~corp};includes;at;  
{if;{userhasrole;{get;austria}};==;true;{set;newrole;{get;austria}}{set;~corpname;Austria};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
};

{if;{get;~corp};includes;en;
{if;{userhasrole;{get;enigma}};==;true;{set;newrole;{get;enigma}}{set;~corpname;Enigma};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
};

{if;{get;~corp};includes;ez;
{if;{userhasrole;{get;ezco}};==;true;{set;newrole;{get;ezco}}{set;~corpname;Ezco};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
};

{if;{get;~corp};includes;hs;
{if;{userhasrole;{get;hermes}};==;true;{set;newrole;{get;hermes}}{set;~corpname;Hermes};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
};

{if;{get;~corp};includes;hy;
{if;{userhasrole;{get;hydra}};==;true;{set;newrole;{get;hydra}}{set;~corpname;Hydra};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
};

{if;{get;~corp};includes;tn;
{if;{userhasrole;{get;terranova}};==;true;{set;newrole;{get;terranova}}{set;~corpname;Terranova};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
};

{if;{get;~corp};includes;tc;
{if;{userhasrole;{get;titan}};==;true;{set;newrole;{get;titan}}{set;~corpname;Titan Corp};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
};

{if;{get;~corp};includes;hm;
{if;{userhasrole;{get;mond}};==;true;{set;newrole;{get;mond}}{set;~corpname;Hinterm Mond};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
};
{set;~msgfk;{send;{channelid};❌Der eingegebene Konzern existiert in der Allianz nicht!}}{timer;{delete;{get;~msgfk}};10s}{return}
}}}}}}}}

{//; Rollen Regelwerk und Neuling entfernen}
{void;{removerole;{get;regelwerk};{get;~usernick};quiet}}
{void;{removerole;{get;neuling};{get;~usernick};quiet}}


{//; Rollen Ally und Konzern hinzufügen}
{void;{roleadd;{get;allyrole};{get;~usernick};quiet}}
{void;{roleadd;{get;newrole};{get;~usernick};quiet}}
{set;msgidrole;{send;{channelid};✅ Die Rollen {rolename;{get;newrole}} und {rolename;{get;allyrole}} wurden für {get;~usernick} hinzugefügt}}
{modlog;Roleadd;{userid};;Rolle {rolename;{get;allyrole}} hinzugefügt für {get;~usernick};{get;~eColor}}
{modlog;Roleadd;{userid};;Rolle {rolename;{get;newrole}} hinzugefügt für {get;~usernick};{get;~eColor}} 
{timer;{delete;{get;msgidrole}};10s}
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
