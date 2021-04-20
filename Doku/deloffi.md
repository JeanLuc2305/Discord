[🏠 Start](https://jeanluc2305.github.io/Discord/)

# setoffi

#### Beschreibung:

Entfernt die Offiziers-Rolle von dem angegebenen User.

#### Benutzung:

`botdeloffi User`

#### Beispiel:

`botdeloffi Jean-Luc`

#### Code:

```
{//; unterdrückt Fehler vom Lookup-System}
{suppresslookup}

{set;falscherUser;❌ {args;0} scheint kein Mitglied dieses Servers zu sein oder du hast dich vertippt!}
{set;keineRechte;❌ Du hast leider nicht die nötigen Berechtigungen, um diesen Befehl benutzen zu können!}
{set;~rol;["794809757046407169", "635102245699977236", "639391792562962434", "638788420075782185", "635109715126386698", "635109707979161610", "675767432585150510", "670731317285093376", "635109991191412736", "814907690165469244", "635100637230792714"]} 

{//; Setzen der Farbe für Embed}
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{//; Rollenabfrage Offiziere}
{switch;true;
  {hasrole;{get;!rol}};
  {void};
  {set;~msgfk;{send;{channelid};{get;keineRechte}}}{timer;{delete;{get;~msgfk}};10s}
  {return}
}

{//; Überprüfen des Users}
{set;~userid;{userid;{args;0}}}
{if;{get;~userid};==;;{set;~msgfk;{send;{channelid};{get;falscherUser}}}{timer;{delete;{get;~msgfk}};10s}{return}}
{set;~usernick;{usernick;{get;~userid}}}

{switch;false;
  {hasrole;{get;~rol}};
  {void};
  {void;{foreach;~role;{get;~rol};{roleremove;{get;~role};{userid;{args}}}}}
}

{delete}

{set;msgidrole;{send;{channelid};✅ Berechtigung Offizier von {get;~usernick} entfernt!}}
{timer;{delete;{get;msgidrole}};10s}
```
