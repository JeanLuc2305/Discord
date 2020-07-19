[🏠 Start](https://jeanluc2305.github.io/Discord/)

# kummerkasten

###### Beschreibung:

Sendet die angehängte Nachricht zum Tartaros Tribunal und löscht sie im aktuellen Kanal

###### Benutzung:

botkummerkasten Nachricht

###### Beispiel:

botkummerkasten Tartaros ist die beste Allianz!

###### Code:

```
{//; unterdrückt Fehler vom Lookup-System}
{suppresslookup}

{//; Setzen der Farbe für Embed}
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{//; Variable setzen}
{set;~chan;641712728125341753} {//; Zielkanal}
{set;~msg;{args}}

{//; Ursprungsnachricht löschen}
{delete}

{//; Erwähnung senden}
{void;{send;{get;~chan};{rolemention;641712382300651535} Neue Kummerkasten-Nachricht!}}

{//; Nachricht senden}
{void;{send;{get;~chan};{embedbuild;color:{get;~eColor;0}
;description:{get;~msg}
;author.name:{usernick}
;author.icon_url:{useravatar}
}}}
  
{//; Bestätigung} 
{void;{set;~check;{send;{channelid};Nachricht wurde gesendet!}}}

{//; Bestätigung löschen}
{timer;{delete;{get;~check}};2s}
```
