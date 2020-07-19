[🏠 Start](https://jeanluc2305.github.io/Discord/)

# quote

###### Beschreibung:

Kanalübergreifende Zitierfunktion

###### Benutzung:

`botquote Kanal-ID Nachricht-ID`

<span style="color:yellow">Die Kanal-ID kann weggelassen werden, wenn sich die Nachricht im selben Kanal befindet.</span>

###### Beispiel:

`quote 123456789 123456789`

###### Code:

```
{set;~c;{channelid}}
{switch;{argslength};
    0;Usage: {newline}`{prefix}{commandname} [channel] <messageid>`{return};
    1;{set;~m;{args;0}};
    {set;~c;{args;0}}{set;~m;{args;1}}
}{delete}
{suppresslookup}
{set;~user;{messagesender;{get;~c};{get;~m}}}
{if;{get;~user};==;`No message found`;Invalid channel/messageID{return}}
{if;{logic;&&;{isnsfw;{get;~c}};{logic;!;{isnsfw}}};❌ Please use a nsfw channel!{return}}
{set;~eColor;[]}
{set;~roles;{roles;{get;~user}}}
{foreach;~color;{get;~roles};
    {if;{rolecolor;{get;~color}};!=;000000;
        {push;{get;~eColor};{rolecolor;{get;~color}}}
    }
}
{if;{length;{get;~eColor}};==;0;
    {set;~eColor;pink}
}
{set;~url;
    https://discordapp.com/channels/
}
{set;~image;{shift;{messageattachments;{get;~c};{get;~m}}}}
{set;~msg;{regexreplace;{messagetext;{get;~c};{get;~m}};/(\[.+?\])(\(.+?\))/g;$1{zws}$2}}
{embed;{embedbuild;
  author.name:{usernick} zitiert:;
  author.icon_url:{useravatar};
    footer.text:gesendet von: {username;{get;~user}}#{userdiscrim;{get;~user}};
    footer.icon_url:{useravatar;{get;~user}};
    title:Quote link;
    url:{get;~url}{guildid}/{get;~c}/{get;~m};
    {if;{length;{get;~image}};!=;0;image.url:{get;~image}};
    description:{if;{get;~msg};!=;;❝ {get;~msg} ❞} {if;{messageedittime;{get;~c};{get;~m}};!=;Invalid date;(edited)};
    timestamp:{messagetime;{get;~c};{get;~m};YYYY-MM-DDTHH:mm:ssZ};
    color:{get;~eColor;0}
}}
```
