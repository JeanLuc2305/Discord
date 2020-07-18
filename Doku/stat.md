[🏠 Start](https://jeanluc2305.github.io/Discord/)

# stat

###### Beschreibung:

Zeigt den Serverstatus

###### Benutzung:

[Prefix]stat

###### Beispiel:

[Prefix]stat

###### Ergebnis:

![Ergebnis](https://cdn.discordapp.com/attachments/642357675283316747/734104705361379338/unknown.png)

###### Code:

```{set;var1;{args}}
{delete} 
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{set;~anzahl}
{set;~humans;0}
{set;~bots;0}

{foreach;~member;{guildmembers};{if;==;false;{userisbot;{get;~member}};{set;~humans;{math;+;{get;~humans};1}}}}

{foreach;~member;{guildmembers};{if;==;true;{userisbot;{get;~member}};{set;~bots;{math;+;{get;~bots};1}}}}

{foreach;~role;{roles};{if;{rolename;{get;~role}};includes;Erster;{set;~anzahl;{get;~anzahl}{space}{get;~role}}}}

{embed;{buildembed;
  color:{get;~eColor;0};
  title:📊  __**{guildname} Server Status:**__
  ;
thumbnail.url:{guildicon};
description:{zws} 
 ***Erstelldatum:***
 {guildcreatedat;YYYY/MM/DD HH:mm:ss}
{zws} 
 ***Anzahl Mitglieder:***
 {length;{guildmembers}}
 ***Anzahl User:***
 {get;~humans}
 ***Anzahl Bots:***
 {get;~bots}
 ***Anzahl Allianz-Konzerne:***
 {math;-;{length;{split;{get;~anzahl};{space}}};1}
 ***Anzahl Kategorien:***
 {length;{categories}}
 ***Anzahl Kanäle:***
 {length;{channels}}
 ***Anzahl Rollen:***
 {length;{roles}}
 ***Anzahl Emojis:***
 {length;{Emojis}}
 
}}```
