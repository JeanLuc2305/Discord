[🏠 Start](https://jeanluc2305.github.io/Discord/)

# wzcheck

###### Beschreibung:

WZ-Checkliste von Terranova

###### Benutzung:

[Prefix]wzcheck

```Red
Achtung! Kann nur von Terranova verwendet werden!
```

###### Beispiel:

[Prefix]wzcheck

###### Code:

```
{set;~roles;["635111745740079105", "671995363263119360"]}
{embed;{buildembed;
title:<:WZ:730100975964258405> __WZ-Checkliste__ <:WZ:730100975964258405>;
description:{switch;true;
  {hasrole;{get;~roles}};
  {void};
  ❌ Du hast leider nicht die nötigen Berechtigungen!!!
  {return}
}}}

{if;{get;_WZCheck};==;;{set;_WZCheck;[]}}
{if;{args};==;;
  {if;{length;{get;_WZCheck}};==;0;{execcc;{commandname};help}{return}}
  {//; Get todo list}
  {set;~list;[]}
  {set;~num;0}
  {foreach;~line;{get;_WZCheck};{push;~list;`{increment;~num}` - {get;~line}}}
  {set;~list;{exec;splitby;{newline};1024;{join;~list;{newline}}}}
  {set;~fields;[]}
  {push;~fields;fields.name:<:WZ:730100975964258405> __WZ-Checkliste__ <:WZ:730100975964258405>;fields.value:{shift;~list};fields.inline:true}
  {foreach;~line;~list;{push;~fields;fields.name:...;fields.value:{get;~line};fields.inline:true}}
  {embed;{apply;embedbuild;{get;~fields}}}
  ;
  {//; Otherwise parse args}
  {switch;{args;0}
    ;["help","h"];
    {embed;{embedbuild;fields.name:<:WZ:730100975964258405> __WZ-Checkliste__ <:WZ:730100975964258405>;
fields.value:{exec;use;[add] <text...>}
{exec;use;del #}
{exec;use;edit # <text...>}
{exec;use;clear}
{exec;use;help}}}
    {return}
    ;["add","a","create","c"];
    {push;{get;_WZCheck};{args;1;n}}
    ;["remove","rem","r","delete","del","d","edit","e"];
    {if;{length;{get;_WZCheck}};<;{args;1};❌ Invalid number.{return}}
    {switch;{args;0}
      ;["remove","rem","r","delete","del","d"];
      {void;{splice;{get;_WZCheck};{math;-;{args;1};1};1}}
      ;["edit","e","update","u"];
      {void;{splice;{get;_WZCheck};{math;-;{args;1};1};1;{args;2;n}}}
    }
    ;clear;
    {set;_WZCheck;[]}
    ;
    {execcc;{commandname};add {args}}
    {return}
  }
  {reactadd;{messageid};✅} 
}
```
