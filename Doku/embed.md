[🏠 Start](https://jeanluc2305.github.io/Discord/)

# embed

#### Beschreibung:

Gibt die angegebene Nachricht als Embed aus

#### Benutzung:

`botembed Nachricht`

#### Beispiel:

`botembed Heute ist ein schöner Tag um Hades' Star zu spielen.``

#### Ergebnis:

![Ergebnis](https://dub01pap001files.storage.live.com/y4mJc_edUkjaCzzcX7FBXmv3Oj65Epf8vAyLArVbldHCJVSYQFPCdy9fpHlf2jGodYBIKWC6L08eRSx8m2dWN6pvu4CWub1xS9MZqurzrhwEP2ebpusX4NX_s7OgEnlrHl_V7EJyqbzNuOqkhgZaxSbNaaD1i-b5TDrlVM1rhGNpdBizAYqh3yEEVaKd2fNgLFM?width=399&height=117&cropmode=none)

#### Code:

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
