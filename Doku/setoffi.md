[🏠 Start](https://jeanluc2305.github.io/Discord/)

# setoffi

#### Beschreibung:

Gibt dem User die Offiziers-Rolle des Konzerns des Users.

#### Benutzung:

`botsetoffi User`

#### Beispiel:

`botsetoffi Jean-Luc`

#### Code:

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
{set;titanae;814906780403761192}
{set;rest;881936146098163763}
{set;oaustria;635102245699977236}
{set;oenigma;639391792562962434}
{set;oezco;638788420075782185}
{set;ohermes;635109715126386698}
{set;ohydra;635109707979161610}
{set;oterranova;635109991191412736}
{set;otitan;635100637230792714}
{set;otitanae;814907690165469244}
{set;orest;881935840920617000}
{set;falscherKonzern;❌ Du bist leider nicht im gleichen Konzern, um die Berechtigung setzen zu können!}
{set;falscherUser;❌ {args;0} scheint kein Mitglied dieses Servers zu sein oder du hast dich vertippt!}
{set;keineRechte;❌ Du hast leider nicht die nötigen Berechtigungen, um diesen Befehl benutzen zu können!}

{//; Setzen der Farbe für Embed}
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{//; Rollenabfrage Admin-Team, Offiziere}
{set;~rol;["640978279532199946", "794809757046407169", "635102245699977236", "639391792562962434", "638788420075782185", "635109715126386698", "635109707979161610", "881935840920617000", "670731317285093376", "635109991191412736", "814907690165469244", "635100637230792714"]} 
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
{if;{userhasrole;{get;titanae}};==;true;{set;~newrole;{get;otitanae}};
{if;{userhasrole;{get;rest}};==;true;{set;~newrole;{get;orest}};
{set;~msgfk;{send;{channelid};{get;falscherKonzern}}}{timer;{delete;{get;~msgfk}};10s}{return}
}}}}}}}}}

{//; Rollen Ally und Konzern hinzufügen}
{void;{roleadd;{get;~newrole};{get;~userid};quiet}}
{set;msgidrole;{send;{channelid};✅ Die Rolle {rolename;{get;~newrole}} wurde für {get;~usernick} hinzugefügt}}
{modlog;Roleadd;{userid};;Rolle {rolename;{get;~newrole}} hinzugefügt für {get;~usernick};{get;~eColor}} 
{timer;{delete;{get;msgidrole}};10s}

```
