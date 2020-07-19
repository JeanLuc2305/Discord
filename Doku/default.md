[🏠 Start](https://jeanluc2305.github.io/Discord/)

# default

###### Beschreibung:

Entfernt alle Rollen eines Mitglieds und setzt die Rolle Besucher-Allianz

###### Benutzung:

`botdefault Username`

###### Beispiel:

`botdefault Jean-Luc`

###### Code:

```
{//; Variablen setzen}
{set;var1;{args}}
{set;radd;638051232384286731}
{set;~keineRechte;❌ Du hast leider nicht die nötigen Berechtigungen, du musst Mitglied der Rolle "Admin" sein!}

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

{//; Überprüfen ob der User vorhanden ist}
{if;{args};>;;
{if;{usernick;{args} ;quiet};==;;
  {set;~msg;{send;{channelid};{buildembed;
  color:{get;~eColor;0};
  title:Bitte nenne einen vorhanden User!}}}
  {delete}{timer;{delete;{get;~msg}};5s}{return}
}}

{//; Frage Rollen entfernen}
{set;~msg;{send;{channelid};
{buildembed;
  color:{get;~eColor;0};
  title:Möchtest du wirklich die Rollen von {usernick;{args}} entfernen?}}}
{//;Hinzufügen der Reaktionen}
{reactadd;{get;~msg};👍👎}
{//;Abwarten auf Reaktion}
{void;{waitreaction;{get;~msg};{userid};👍👎;{set;~reaction;{reaction}}}}
{//;Auslesen der Reaktionen}
{clean;{switch;{get;~reaction};
👎;{set;~msg2;{send;{channelid};{buildembed;
  color:{get;~eColor;0};
  title:Befehl wurde abgebrochen.}}}
  {delete}{timer;{delete;{get;~msg}};5s}{timer;{delete;{get;~msg2}};5s}{return};
👍;{void;{foreach;~role;{roles;{get;var1};quiet};{roleremove;{get;~role};{userid;{args}}}}}
{void;{roleadd;{get;radd};{userid;{args}};quiet}}
{void;{modlog;Roleremove;{userid};;Alle Rollen von {usernick;{args}} wurden entfernt.;{get;~eColor}}}
{set;~msg2;{send;{channelid};{buildembed;
  color:{get;~eColor;0};
  title:✅ Die Rollen von {usernick;{args}} wurden zurückgesetzt!}
  }}{delete}{timer;{delete;{get;~msg}};5s}{timer;{delete;{get;~msg2}};5s}{return}
}}
```
