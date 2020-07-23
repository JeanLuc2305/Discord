[🏠 Start](https://jeanluc2305.github.io/Discord/)

# zugen

#### Beschreibung:

Der Zufallsgenerator ermittelt einen User aus einer angegebenen Rolle

#### Benutzung:

`botzugen Rollenname`

#### Beispiel:

`botzugen Neuling`

#### Ergebnis:

![Ergebnis](https://cdn.discordapp.com/attachments/642357675283316747/734107826586124318/unknown.png)

#### Code:

```
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{//;Test if the person specified any words/names:}
{if;{argslength};<=;0;
  {embed;{buildembed;
  color:{get;~eColor;0};
  title:Bitte nenne eine Rolle!;
description:-------------------------------
Beispiel: {prefix}{commandname} {randchoose;Terranova;Fuehrung}
Mit **{prefix}rol** erhältst du eine Übersicht.
  {delete}{return}
}}}

{//;Check if the specified words/names match an existing role:}
{set;~roleID;{roleid;{args};quiet}}
{if;{get;~roleID};==;;
  {embed;{buildembed;
  color:{get;~eColor;0};
  title:Bitte nenne eine vorhandene Rolle.;
description:
-------------------------------
Die Rolle existiert nicht!
Mit **{prefix}rol** erhältst du eine Übersicht.
{delete}{return}
}}}
{delete} 
{set;~msgID;{send;{channelid};{embedbuild;color:{get;~eColor;0}
;description: **🔟**}}}

{sleep;1s}{void;{edit;{get;~msgID};{embedbuild;color:{get;~eColor;0}
;description: **9️⃣**}}}

{sleep;1s}{void;{edit;{get;~msgID};{embedbuild;color:{get;~eColor;0}
;description: **8️⃣**}}}

{sleep;1s}{void;{edit;{get;~msgID};{embedbuild;color:{get;~eColor;0}
;description: **7️⃣**}}}

{sleep;1s}{void;{edit;{get;~msgID};{embedbuild;color:{get;~eColor;0}
;description: **6️⃣**}}}

{sleep;1s}{void;{edit;{get;~msgID};{embedbuild;color:{get;~eColor;0}
;description: **5️⃣**}}}

{sleep;1s}{void;{edit;{get;~msgID};{embedbuild;color:{get;~eColor;0}
;description: **4️⃣**}}}

{sleep;1s}{void;{edit;{get;~msgID};{embedbuild;color:{get;~eColor;0}
;description: **3️⃣**}}}

{sleep;1s}{void;{edit;{get;~msgID};{embedbuild;color:{get;~eColor;0}
;description: **2️⃣**}}}

{sleep;1s}{void;{edit;{get;~msgID};{embedbuild;color:{get;~eColor;0}
;description: **1️⃣**}}}

{sleep;1s}{delete;{get;~msgID}}

{embed;{buildembed;
  color:{get;~eColor;0};
  title:Mein interner Zufallsgenerator hat dieses Mitglied aus der Rolle {rolename;{get;~roleID};quiet} ausgesucht:;

description:
🎉 🍻 ➡️  {usernick;{randchoose;{rolemembers;{get;~roleID}}}}  ⬅️ 🍻 🎉}}
```
