[🏠 Start](https://jeanluc2305.github.io/Discord/)

# stat

#### Beschreibung:

Zeigt den Serverstatus

Mit dem Parameter dem "<span style="color:yellow">limits</span>" werden die Discord Server Limits angezeigt

#### Benutzung:

`botstat`

#### Beispiel:

`botstat`

`botstat limits`

#### Code:

```
{set;var1;{args}}
{delete} 
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{if;{args;0};includes;limits;
{embed;{embedbuild
;color:0075FF
;title:__***Discord Server Limits***__
;description:
🔸 Normally servers have a member limit of 250,000 members. However, some partnered and verified servers can get this limit raised to 500,000.
🔸 Servers reaching 25,000 simultaneous online members will need to contact Support to be moved to hardware supporting larger servers - this is when members start getting "Server Unavailable" errors.
🔸 A server can have at most 500 channels - text, voice, and categories combined. Once 500 channels are reached, no more channels can be created.
🔸 A category can have at most 50 channels - text and voice combined. Once 50 channels are reached, no more channels can be created inside that category.
🔸 A server can have at most 250 roles.
🔸 Servers reaching 1,000 members have the offline members list removed.
}}{return}}

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
 
}}
```
