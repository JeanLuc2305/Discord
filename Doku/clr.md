[🏠 Start](https://jeanluc2305.github.io/Discord/)

# clr

###### Beschreibung:

Entfernt alle Mitglieder aus einer angegebenen Rolle

###### Benutzung:

botclr Rollenname

###### Beispiel:

botclr Neuling

###### Code:

```
{set;~roleID;{roleid;{args};quiet}}

{//; Setzen der Farbe für Embed}
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{//;Test if the person specified any words/names:}
{if;{argslength};<=;0;
  {set;~msg;{send;{channelid};{buildembed;
  color:{get;~eColor;0};
  title:Bitte nenne eine Rolle!;
description:-------------------------------
Beispiel: {prefix}{commandname} {randchoose;Besucher;Regelwerk}
Mit **{prefix}rollen** erhältst du eine Übersicht.
}}}    
{delete}{timer;{delete;{get;~msg}};10s}{return}
}

{//;Check if the specified words/names match an existing role:}
{if;{get;~roleID};==;;
  {set;~msg;{send;{channelid};{buildembed;
  color:{get;~eColor;0};
  title:Bitte nenne eine vorhandene Rolle.;
description:
-------------------------------
Die Rolle existiert nicht!
Mit **{prefix}rollen** erhältst du eine Übersicht.
}}}
{delete}{timer;{delete;{get;~msg}};10s}{return}
}

{//; Rolle leeren}
{set;~msg;{send;{channelid};
Möchtest du wirklich die Rolle leeren?}}
{//;Hinzufügen der Reaktionen}
{reactadd;{get;~msg};👍👎}
{//;Abwarten auf Reaktion}
{void;{waitreaction;{get;~msg};{userid};👍👎;{set;~reaction;{reaction}}}}
{//;Auslesen der Reaktionen}
{clean;{switch;{get;~reaction};
👎;{set;~msg2;{send;{channelid};{buildembed;
  color:{get;~eColor;0};
  title:Befehl wurde abgebrochen.}}}
  {delete}{timer;{delete;{get;~msg}};10s}{timer;{delete;{get;~msg2}};10s}{return};
👍;{void;{foreach;~member;{rolemembers;{get;~roleID};quiet};{roleremove;{get;~roleID};{get;~member};quiet}}}
{set;~msg2;{send;{channelid};{buildembed;
  color:{get;~eColor;0};
  title:✅ Die Rolle {rolename;{get;~roleID}} wurde geleert}
  }}{delete}{timer;{delete;{get;~msg}};10s}{timer;{delete;{get;~msg2}};10s}{return}
}}
```
