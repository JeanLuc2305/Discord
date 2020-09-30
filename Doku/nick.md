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


#### Beispiel:

`botnick Jean-Luc TN`


#### Code:

```
{//; unterdrückt Fehler vom Lookup-System}
{suppresslookup}

{//; Variablen setzen}
{//; {set;~Mitglied;637763780520050688}}
{set;~austria;635102610864603136}
{set;~enigma;639392133270470656}
{set;~ezco;638788269168918538}
{set;~hermes;635109388868255764}
{set;~hydra;635109995461083137}
{set;~terranova;635111745740079105}
{set;~titan;635101067721441310}
{set;~mond;643218498696380416}
{set;~tardis;670732003255123978}
{set;~kumzumir;675769366360490031}
{set;~falscherKonzern;❌ Du bist leider nicht im gleichen Konzern, um die Berechtigung setzen zu können!}
{set;~keineRechte;❌ Du hast leider nicht die nötigen Berechtigungen, du musst Mitglied der Rolle "Admin" sein!}
{set;~falscherUser;❌ {args;0} scheint kein Mitglied dieses Servers zu sein oder du hast dich vertippt!}


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
  {set;~msgfk;{send;{channelid};{get;~keineRechte}}}{timer;{delete;{get;~msgfk}};5s}
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
{if;{get;~userid};==;;{set;~msgfk;{send;{channelid};{get;~falscherUser}}}{timer;{delete;{get;~msgfk}};5s}{return}}
{set;~username;{username;{get;~userid}}}
{set;~usernick;{usernick;{get;~userid}}}

{//; Konzern neu setzen}
{set;~corp;{lower;{args;1}}}

{//;{get;~userid}
{get;~usernick}
{get;~username}
{get;~newrole}
{get;~regelwerk}
{get;~neuling}}

{//; Konzernerkennung}
{if;{get;~corp};includes;at;  
{if;{userhasrole;{get;~austria}};==;true;{set;~newrole;{get;~austria}}{set;~corpname;Austria};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};

{if;{get;~corp};includes;en;
{if;{userhasrole;{get;~enigma}};==;true;{set;~newrole;{get;~enigma}}{set;~corpname;Enigma};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};

{if;{get;~corp};includes;ez;
{if;{userhasrole;{get;~ezco}};==;true;{set;~newrole;{get;~ezco}}{set;~corpname;Ezco};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};

{if;{get;~corp};includes;hs;
{if;{userhasrole;{get;~hermes}};==;true;{set;~newrole;{get;~hermes}}{set;~corpname;Hermes};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};

{if;{get;~corp};includes;hy;
{if;{userhasrole;{get;~hydra}};==;true;{set;~newrole;{get;~hydra}}{set;~corpname;Hydra};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};

{if;{get;~corp};includes;km;
{if;{userhasrole;{get;~kumzumuir}};==;true;{set;~newrole;{get;~kumzumuir}}{set;~corpname;Kumzumuir};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};  
  
{if;{get;~corp};includes;ta;
{if;{userhasrole;{get;~tardis}};==;true;{set;~newrole;{get;~tardis}}{set;~corpname;\-TARDIS-/};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};  
  
{if;{get;~corp};includes;tn;
{if;{userhasrole;{get;~terranova}};==;true;{set;~newrole;{get;~terranova}}{set;~corpname;Terranova};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};

{if;{get;~corp};includes;tc;
{if;{userhasrole;{get;~titan}};==;true;{set;~newrole;{get;~titan}}{set;~corpname;Titan Corp};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};

{if;{get;~corp};includes;hm;
{if;{userhasrole;{get;~mond}};==;true;{set;~newrole;{get;~mond}}{set;~corpname;Hinterm Mond};
{set;~msgfk;{send;{channelid};{get;~falscherKonzern}}}{timer;{delete;{get;~msgfk}};5s}{return}
};{set;~msgfk;{send;{channelid};❌Der eingegebene Konzern existiert in der Allianz nicht!}}{timer;{delete;{get;~msgfk}};5s}{return}
}}}}}}}}}}

{set;~allyrole;635106983682375730}
{set;~regelwerk;637763780520050688}
{set;~neuling;637784554643390464}
{set;~besucherde;676859700591067166}
{set;~besucherally;638051232384286731}
{set;~regeln;676859384222973984}
{set;~tbesuchchan;676861892643258389}
{set;~swdwchan;755388782626209812}
{set;~vhallechan;637757304443240491}

{//; Rollen Regelwerk Neuling entfernen}
{void;{removerole;{get;~regelwerk};{get;~userid}}}
{void;{removerole;{get;~neuling};{get;~userid}}}
{void;{removerole;{get;~besucherde};{get;~userid}}}
{void;{removerole;{get;~regeln};{get;~userid}}}
{void;{removerole;{get;~besucherally};{get;~userid}}}

{//; Rollen Ally und Konzern hinzufügen}
{void;{roleadd;{get;~allyrole};{get;~userid}}}
{void;{roleadd;{get;~newrole};{get;~userid}}}
{set;~msgidrole;{send;{channelid};✅ Die Rollen {rolename;{get;~newrole}} und {rolename;{get;~allyrole}} wurden für {get;~usernick} hinzugefügt}}

{void;{send;{get;~vhallechan};{buildembed
;color:{get;~eColor;0}
;title:Sei willkommen in den Hallen der Tartaros Armada!
;description:<@{get;~userid}>, dir wurde soeben Zutritt gewährt in den Allianzbereich und in die internen Kanäle deines neuen Heimatkonzerns **{get;~corpname}**.
  
Um dir den Aufenthalt so angenehm wie möglich zu gestalten, besuche bitte <#{get;~swdwchan}>, um die sichtbaren Kanäle an deine Bedürfnisse anzupassen.
  
In <#{get;~tbesuchchan}> kannst du dir den Zugriff in die Besucherkanäle der anderen Tartaros-Konzerne freischalten.
  
Auf eine glorreiche gemeinsame Zeit!}}}

{modlog;Roleadd;{userid};;Rolle {rolename;{get;~allyrole}} hinzugefügt für {get;~usernick};{get;~eColor}}
{modlog;Roleadd;{userid};;Rolle {rolename;{get;~newrole}} hinzugefügt für {get;~usernick};{get;~eColor}} 
{timer;{delete;{get;~msgidrole}};5s}
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

{timer;{delete;{get;~msgid}};5s}
```
