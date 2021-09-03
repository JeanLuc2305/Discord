[🏠 Start](https://jeanluc2305.github.io/Discord/)

# default

#### Beschreibung:

Entfernt alle Rollen eines Mitglieds, setzt die Rollen Besucher-Allianz, Besucher-de und Regeln-de und ändert den Nickname in Konzernlos.

#### Benutzung:

`botdefault Username`

#### Beispiel:

`botdefault Jean-Luc`

#### Code:

```
{//; Variablen setzen}
{set;var1;{args}}
{set;radd1;638051232384286731} {//;Besucher-Allianz} 
{set;radd2;676859700591067166} {//;Besucher-de} 
{set;radd3;676859384222973984} {//;Regeln-de} 

{set;~keineRechte;❌ Du hast leider nicht die nötigen Berechtigungen, du musst Mitglied der Rolle "Admin" sein!}
{set;~falscherUser;❌ {args} scheint kein Mitglied dieses Servers zu sein oder du hast dich vertippt!}

{//; Setzen der Farbe für Embed}
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{//; Überprüfen des Users}
{set;~userid;{userid;{args}}}
{if;{get;~userid};==;;{set;~msgfk;{send;{channelid};{get;~falscherUser}}}{timer;{delete;{get;~msgfk}};5s}{return}}
{set;~username;{username;{get;~userid}}}
{set;~usernick;{usernick;{get;~userid}}}

{//; Rollenabfrage Admin-Team, Erster Offizier}
{set;~rol;["640978279532199946", "794540989775478805"]} 
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
{void;{roleadd;{get;radd1};{userid;{args}};quiet}}
{void;{roleadd;{get;radd2};{userid;{args}};quiet}}
{void;{roleadd;{get;radd3};{userid;{args}};quiet}}
{void;{modlog;Roleremove;{userid};;Alle Rollen von {usernick;{args}} wurden entfernt.;{get;~eColor}}}
{set;~msg2;{send;{channelid};{buildembed;
  color:{get;~eColor;0};
  title:✅ Die Rollen von {usernick;{args}} wurden zurückgesetzt!}
  }}
  
{void;{send;637757304443240491;{buildembed
;color:{get;~eColor;0}
;title:Alles Gute {usernick;{args}} wünscht die Tartaros Armada!
;description:**{usernick;{args}}** hat soeben die Tartaros Armada verlassen. Wir wünschen für die Zukunft trotzdem alles Gute im neuen Konzern! 
Der Besucherbereich wird weiterhin für dich verfügbar sein!}}}

{delete}{timer;{delete;{get;~msg}};5s}{timer;{delete;{get;~msg2}};5s}
}}


{set;~basenick;{get;~usernick}}
{while;{get;~basenick};includes;[; {//;remove all bracketed parts}
  	{set;~openbracket;{indexof;{get;~basenick};[}}
  	{set;~closebracket;{indexof;{get;~basenick};]}}
  	{set;~base1;{substring;{get;~basenick};0;{math;-;{get;~openbracket};1}}}
    {set;~base2;{substring;{get;~basenick};{math;+;{get;~closebracket};1}}}
    {set;~basenick;{get;~base1}{get;~base2}}
}

{set;~newnick;{trim;{get;~basenick}} [Konzernlos]
}

{if;{length;{get;~newnick}};<=;32;
    {if;{setnick;{get;~newnick};{get;~userid}};includes;Der Nickname konnte nicht geändert werden.;
        ❌ Umbenennen von `{get;~usernick}` zu `{get;~newnick}`nicht erfolgreich. Wahrscheinlich ein Berechtigungsproblem.
    ;
        {set;~msg3;✅ Erfolgreich `{get;~usernick}` zu `{get;~newnick}` umbenannt.}
    }
;
    ❌ `{get;~newnick}` überschreitet 32 Zeichen.
}
{//; setzt Nickname nach Vorgabe}
{set;_{get;~userid}_usernick;{usernick;{get;~userid}}}

{if;0{length;{get;~msg3}};
  {set;~msgid;{send;{channelid};{get;~msg3}}}
}
{delete}{timer;{delete;{get;~msgid}};5s}

```
