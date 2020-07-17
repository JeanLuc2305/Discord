[🏠 Start](https://jeanluc2305.github.io/Discord/)

# embed

###### Beschreibung:

Gibt die angegebene Nachricht als Embed aus

###### Benutzung:

[Prefix]embed Nachricht

###### Beispiel:

[Prefix]embed Heute ist ein schöner Tag um Hades' Star zu spielen.

Ergebnis:

![Ergebnis](https://cdn.discordapp.com/attachments/642357675283316747/733626572216729630/unknown.png)

###### Code:

```
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{set;~msg;{args}}
{delete}
  
{embed;{buildembed;
  color:{get;~eColor;0}
;description:{get;~msg}
;author.name:{usernick}
;author.icon_url:{useravatar}
}}
```
