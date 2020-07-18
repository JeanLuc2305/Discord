[🏠 Start](https://jeanluc2305.github.io/Discord/)

# setoffi

###### Beschreibung:

Gibt dem User die Offiziers-Rolle des angegebenen Konzerns

###### Benutzung:

[Prefix]setoffin User

###### Beispiel:

[Prefix]setoffin Jean-Luc

###### Code:

```
{//; unterdrückt Fehler vom Lookup-System}
{suppresslookup}

{//; Variablen setzen}
{set;austria;635102610864603136}
{set;enigma;639392133270470656}
{set;ezco;638788269168918538}
{set;hermes;635109388868255764}
{set;hydra;635109995461083137}
{set;terranova;635111745740079105}
{set;titan;635101067721441310}
{set;mond;643218498696380416}
{set;oaustria;635102245699977236}
{set;oenigma;639391792562962434}
{set;oezco;638788420075782185}
{set;ohermes;635109715126386698}
{set;ohydra;635109707979161610}
{set;oterranova;635109991191412736}
{set;otitan;635100637230792714}
{set;omond;643218349354123317}
{set;falscherKonzern;❌ Du bist leider nicht im gleichen Konzern, um die Berechtigung setzen zu können!}
{set;falscherUser;❌ {args;0} scheint kein Mitglied dieses Servers zu sein oder du hast dich vertippt!}
{set;keineRechte;❌ Du hast leider nicht die nötigen Berechtigungen, du musst Mitglied der Rolle "Admin" sein!}

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

{//; Überprüfen des Users}
{set;~userid;{userid;{args;0}}}
{if;{get;~userid};==;;{set;~msgfk;{send;{channelid};{get;falscherUser}}}{timer;{delete;{get;~msgfk}};10s}{return}}
{set;~username;{username;{get;~userid}}}
{set;~usernick;{usernick;{get;~userid}}}

{//; Konzern neu setzen}
{set;~corp;{lower;{args;1}}}
{delete}

{//; Konzernerkennung}
{if;{userhasrole;{get;austria}};==;true;{set;~newrole;{get;oaustria}};
{if;{userhasrole;{get;enigma}};==;true;{set;~newrole;{get;oenigma}};
{if;{userhasrole;{get;ezco}};==;true;{set;~newrole;{get;oezco}};
{if;{userhasrole;{get;hermes}};==;true;{set;~newrole;{get;ohermes}};
{if;{userhasrole;{get;hydra}};==;true;{set;~newrole;{get;ohydra}};
{if;{userhasrole;{get;terranova}};==;true;{set;~newrole;{get;oterranova}};
{if;{userhasrole;{get;titan}};==;true;{set;~newrole;{get;otitan}};
{if;{userhasrole;{get;mond}};==;true;{set;~newrole;{get;omond}};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
}}}}}}}}

{//; Rollen Ally und Konzern hinzufügen}
{void;{roleadd;{get;~newrole};{get;~userid};quiet}}
{set;msgidrole;{send;{channelid};✅ Die Rolle {rolename;{get;~newrole}} wurde für {get;~usernick} hinzugefügt}}
{modlog;Roleadd;{userid};;Rolle {rolename;{get;~newrole}} hinzugefügt für {get;~usernick};{get;~eColor}} 
{timer;{delete;{get;msgidrole}};10s}
```
