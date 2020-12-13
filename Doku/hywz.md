[🏠 Start](https://jeanluc2305.github.io/Discord/)

# hywz oder hywz2

#### Beschreibung:

WZ-Manager von Hydra 

<span style="color:red">⚠ Achtung! Kann nur von Hydra verwendet werden!</span>


#### Benutzung:

`bothywz / bothywz2`

#### Ergebnis:

![hangmsg](https://cdn.discordapp.com/attachments/642357675283316747/733633068073615460/unknown.png)

#### Code:

```
{//;Variablen}
{set;!Konzern;668485761049296897}{//;Konzern-Mitglied Rolle}
{set;!{commandname}Teilnehmer;668486684266070016}{//;WZ-Teilnehmer Rolle}
{set;!{commandname}Hades;668486971311783967}{//;WZ-Hades Rolle}
{set;!{commandname}Diplomat;725614681519030283}{//;WZ-Diplomat Rolle}
{set;!{commandname}Ares;787372589449216000}{//;WZ-Ares Rolle}
{set;!{commandname}Athene;787372890755956738}{//;WZ-Athene Rolle}
{set;!{commandname}Zeus;787373201662935070}{//;WZ-Zeus Rolle}
{set;!{commandname}Merkur;787373341333389322}{//;WZ-Merkur Rolle}
{set;!{commandname}Kratos;787373421914095616}{//;WZ-Kratos Rolle}
{set;!{commandname}Dionysos;787373894200983582}{//;WZ-Dionysos Rolle}

{//;Sicherheitsüberprüfung, Herren der Bots, Mitglied Konzern}
{set;~rol;["640978279532199946", "{get;!Konzern}"]}
{switch;true;
  {hasrole;{get;~rol}};
  {void};
  {embed;{embedbuild
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:❌ Du hast leider nicht die nötigen Berechtigungen!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg

}}
{return}}

{//; Hilfe anzeigen}
{func;help;
{embed;{embedbuild
;color:0075FF
;title:__{upper;{commandname}}-Manager__{newline}{ZWS}
;fields.name:
🔸{prefix}{Commandname}
;fields.value:Zeigt diese Hilfe
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} start
;fields.value:Startet den WZ und Teilnehmen können hinzugefügt werden
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} diplomat 
;fields.value:Bennung eines Diplomaten des Gegners (mehrfach Bennung durch Leerzeichen möglich)
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} gegner 
;fields.value:Ermöglicht das Eintragen des Gegners (Gegner muss in "" geschrieben werden)
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} in 
;fields.value:Sich selbst als WZ-Teilnehmer hinzufügen
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} in user 
;fields.value:Den angegebenen User als WZ-Teilnehmer hinzufügen
;fields.inline:true
;fields.name:
🔸{prefix}{Commandname} + "Team"
;fields.value:Sich selbst einem Team hinzufügen
Zur Auswahl stehen: Hades, Ares, Athene, Zeus, Merkur, Kratos und Dionysos
Beispiel: {prefix}{Commandname} Hades ➡ Man fügt sich selbst zum Team Hades dazu
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} + "Team" user 
;fields.value:Den angegebenen User einem Team hinzufügen
Zur Auswahl stehen: Hades, Ares, Athene, Zeus, Merkur, Kratos und Dionysos
Beispiel: {prefix}{Commandname} Hades ➡ Man fügt den Spieler zum Team Hades dazu
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} out
;fields.value:Sich selbst als WZ-Teilnehmer entfernen
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} out user 
;fields.value:Den angegebenen User als WZ-Teilnehmer entfernen
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} list
;fields.value:Zeigt eine Liste der WZ Teilnehmer
;fields.inline:false
;fields.name:
🔸{prefix}{Commandname} end
;fields.value:Leert die Rollen und beendet den WZ
{newline}{ZWS}
;fields.inline:false
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
;footer.text:ℹ️ Erstellt von: Chris85#1579
}}}

{//; Kommando Parameter angegeben?}
{if;{argslength};==;0;
  {func.help}
}
  
{//; WZ-Manager starten}
{if;{args;0};includes;start;
{if;{get;!{commandname}wz};==;1;
{embed;{embedbuild
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde bereits gestartet!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg  
}} 
{return};

{embed;{embedbuild
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der WZ wurde gestartet, die Teilnehmer können jetzt hinzugefügt werden!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}
{set;!{commandname}wz;1}
{return}
}}

{//; Diplomat auswählen}
{if;{args;0};includes;diplomat;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{set;~names;{slice;{argsarray};1}}
{void;{foreach;~name;{get;~names};{roleadd;{get;!{commandname}Diplomat};{get;~name};quiet}}}

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:**Folgende Spieler wurden als Diplomaten benannt:**
{foreach;~role;{rolemembers;{get;!{commandname}Diplomat}};{void;{get;~role}}{usernick;{get;~role};quiet}{newline}}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}

{//; Gegner eintragen}
{if;{args;0};includes;gegner;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};
 
{if;{argslength};==;1;
{embed;{embedbuild
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Es wurde kein Gegner genannt!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};
{set;!{commandname}gegner;{args;1}}
{embed;{embedbuild
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der WZ Gegner {args;1} wurde eingetragen!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}
  

{//; Spieler zum WZ hinzufügen}
{if;{args;0};includes;in;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};


{if;{get;!{commandname}gegner};!=;"";
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der WZ läuft bereits!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{argslength};==;1;
{set;!{commandname}userid;{userid}};
{set;!{commandname}userid;{userid;{args;1}}}}
{if;{get;!{commandname}userid};==;;{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description: Der angegebene User existiert nicht!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}
{set;!{commandname}username;{username;{get;!{commandname}userid}}}
{set;!{commandname}usernick;{usernick;{get;!{commandname}userid}}}
  
{void;{roleadd;{get;!{commandname}Teilnehmer};{get;!{commandname}userid};quiet}}
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} wurde zum WZ hinzugefügt!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}

{//; Spieler als Hades hinzufügen}
{if;{args;0};includes;Hades;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{argslength};==;1;
{set;!{commandname}userid;{userid}};
{set;!{commandname}userid;{userid;{args;1}}}}
{if;{get;!{commandname}userid};==;;{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der angegebene User existiert nicht!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}
{set;!{commandname}username;{username;{get;!{commandname}userid}}}
{set;!{commandname}usernick;{usernick;{get;!{commandname}userid}}}
  
{if;{userhasrole;{get;!{commandname}Teilnehmer};{get;!{commandname}userid}};==;true;
{void;{roleadd;{get;!{commandname}Hades};{get;!{commandname}userid};quiet}}
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} wurde als Hades hinzugefügt!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} ist kein Teilnehmer!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}

{//; Spieler als Ares hinzufügen}
{if;{args;0};includes;Ares;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{argslength};==;1;
{set;!{commandname}userid;{userid}};
{set;!{commandname}userid;{userid;{args;1}}}}
{if;{get;!{commandname}userid};==;;{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der angegebene User existiert nicht!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}
{set;!{commandname}username;{username;{get;!{commandname}userid}}}
{set;!{commandname}usernick;{usernick;{get;!{commandname}userid}}}
  
{if;{userhasrole;{get;!{commandname}Teilnehmer};{get;!{commandname}userid}};==;true;
{void;{roleadd;{get;!{commandname}Ares};{get;!{commandname}userid};quiet}}
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} wurde als Ares hinzugefügt!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} ist kein Teilnehmer!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}

{//; Spieler als Athene hinzufügen}
{if;{args;0};includes;Athene;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{argslength};==;1;
{set;!{commandname}userid;{userid}};
{set;!{commandname}userid;{userid;{args;1}}}}
{if;{get;!{commandname}userid};==;;{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der angegebene User existiert nicht!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}
{set;!{commandname}username;{username;{get;!{commandname}userid}}}
{set;!{commandname}usernick;{usernick;{get;!{commandname}userid}}}
  
{if;{userhasrole;{get;!{commandname}Teilnehmer};{get;!{commandname}userid}};==;true;
{void;{roleadd;{get;!{commandname}Athene};{get;!{commandname}userid};quiet}}
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} wurde als Athene hinzugefügt!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} ist kein Teilnehmer!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}

{//; Spieler als Zeus hinzufügen}
{if;{args;0};includes;Zeus;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{argslength};==;1;
{set;!{commandname}userid;{userid}};
{set;!{commandname}userid;{userid;{args;1}}}}
{if;{get;!{commandname}userid};==;;{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der angegebene User existiert nicht!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}
{set;!{commandname}username;{username;{get;!{commandname}userid}}}
{set;!{commandname}usernick;{usernick;{get;!{commandname}userid}}}
  
{if;{userhasrole;{get;!{commandname}Teilnehmer};{get;!{commandname}userid}};==;true;
{void;{roleadd;{get;!{commandname}Zeus};{get;!{commandname}userid};quiet}}
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} wurde als Zeus hinzugefügt!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} ist kein Teilnehmer!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}

{//; Spieler als Merkur hinzufügen}
{if;{args;0};includes;Merkur;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{argslength};==;1;
{set;!{commandname}userid;{userid}};
{set;!{commandname}userid;{userid;{args;1}}}}
{if;{get;!{commandname}userid};==;;{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der angegebene User existiert nicht!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}
{set;!{commandname}username;{username;{get;!{commandname}userid}}}
{set;!{commandname}usernick;{usernick;{get;!{commandname}userid}}}
  
{if;{userhasrole;{get;!{commandname}Teilnehmer};{get;!{commandname}userid}};==;true;
{void;{roleadd;{get;!{commandname}Merkur};{get;!{commandname}userid};quiet}}
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} wurde als Merkur hinzugefügt!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} ist kein Teilnehmer!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}

{//; Spieler als Kratos hinzufügen}
{if;{args;0};includes;Kratos;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{argslength};==;1;
{set;!{commandname}userid;{userid}};
{set;!{commandname}userid;{userid;{args;1}}}}
{if;{get;!{commandname}userid};==;;{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der angegebene User existiert nicht!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}
{set;!{commandname}username;{username;{get;!{commandname}userid}}}
{set;!{commandname}usernick;{usernick;{get;!{commandname}userid}}}
  
{if;{userhasrole;{get;!{commandname}Teilnehmer};{get;!{commandname}userid}};==;true;
{void;{roleadd;{get;!{commandname}Kratos};{get;!{commandname}userid};quiet}}
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} wurde als Kratos hinzugefügt!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} ist kein Teilnehmer!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}

{//; Spieler als Dionysos hinzufügen}
{if;{args;0};includes;Dionysos;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{argslength};==;1;
{set;!{commandname}userid;{userid}};
{set;!{commandname}userid;{userid;{args;1}}}}
{if;{get;!{commandname}userid};==;;{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der angegebene User existiert nicht!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}
{set;!{commandname}username;{username;{get;!{commandname}userid}}}
{set;!{commandname}usernick;{usernick;{get;!{commandname}userid}}}
  
{if;{userhasrole;{get;!{commandname}Teilnehmer};{get;!{commandname}userid}};==;true;
{void;{roleadd;{get;!{commandname}Dionysos};{get;!{commandname}userid};quiet}}
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} wurde als Dionysos hinzugefügt!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} ist kein Teilnehmer!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}

{//; Spieler entfernen}
{if;{args;0};includes;out;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{get;!{commandname}gegner};!=;"";
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der WZ läuft bereits!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{if;{argslength};==;1;
{set;!{commandname}userid;{userid}};
{set;!{commandname}userid;{userid;{args;1}}}}
{if;{get;!{commandname}userid};==;;{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description: Der angegebene User existiert nicht!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}
{set;!{commandname}username;{username;{get;!{commandname}userid}}}
{set;!{commandname}usernick;{usernick;{get;!{commandname}userid}}}
  
{if;{userhasrole;{get;!{commandname}Teilnehmer}};==;true;
{void;{roleremove;{get;!{commandname}Teilnehmer};{get;!{commandname}userid};quiet}}
{void;{roleremove;{get;!{commandname}Hades};{get;!{commandname}userid};quiet}}
{void;{roleremove;{get;!{commandname}Ares};{get;!{commandname}userid};quiet}}
{void;{roleremove;{get;!{commandname}Athene};{get;!{commandname}userid};quiet}}
{void;{roleremove;{get;!{commandname}Zeus};{get;!{commandname}userid};quiet}}
{void;{roleremove;{get;!{commandname}Merkur};{get;!{commandname}userid};quiet}}
{void;{roleremove;{get;!{commandname}Kratos};{get;!{commandname}userid};quiet}}
{void;{roleremove;{get;!{commandname}Dionysos};{get;!{commandname}userid};quiet}}

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} wurde entfernt!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der Spieler {get;!{commandname}usernick} ist kein Teilnehmer!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}}}


{//; WZ Liste ausgeben}
{if;{args;0};includes;list;
{if;{get;!{commandname}wz};==;0;
{embed;{embedbuild
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{embed;{embedbuild
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:🌀 __**WZ-Teilnehmer:**__
{foreach;~member;{rolemembers;{get;!{commandname}Teilnehmer}};{usernick;{get;~member};quiet}{newline}}
🖋 __**Diplomaten:**__
{foreach;~member;{rolemembers;{get;!{commandname}Diplomat}};{usernick;{get;~member};quiet}{newline}}
🔴 __**WZ-Hades:**__
{foreach;~member;{rolemembers;{get;!{commandname}Hades}};{usernick;{get;~member};quiet}{newline}}
🟠 __**WZ-Ares:**__
{foreach;~member;{rolemembers;{get;!{commandname}Ares}};{usernick;{get;~member};quiet}{newline}}
🟡 __**WZ-Athene:**__
{foreach;~member;{rolemembers;{get;!{commandname}Athene}};{usernick;{get;~member};quiet}{newline}}
🟢 __**WZ-Zeus:**__
{foreach;~member;{rolemembers;{get;!{commandname}Zeus}};{usernick;{get;~member};quiet}{newline}}
🔵 __**WZ-Merkur:**__
{foreach;~member;{rolemembers;{get;!{commandname}Merkur}};{usernick;{get;~member};quiet}{newline}}
🟣 __**WZ-Kratos:**__
{foreach;~member;{rolemembers;{get;!{commandname}Kratos}};{usernick;{get;~member};quiet}{newline}}
🟤 __**WZ-Dionysos:**__
{foreach;~member;{rolemembers;{get;!{commandname}Dionysos}};{usernick;{get;~member};quiet}{newline}}
{ZWS}
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return}}}

{//; WZ beenden}
{if;{args;0};includes;end;
{if;{get;!{commandname}wz};==;0;
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:WZ wurde noch nicht gestartet!
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}{return};

{void;{foreach;~member;{rolemembers;{get;!{commandname}Teilnehmer};quiet};{roleremove;{get;!{commandname}Teilnehmer};{get;~member};quiet}}}
{void;{foreach;~member;{rolemembers;{get;!{commandname}Hades};quiet};{roleremove;{get;!{commandname}Hades};{get;~member};quiet}}}
{void;{foreach;~member;{rolemembers;{get;!{commandname}Diplomat};quiet};{roleremove;{get;!{commandname}Diplomat};{get;~member};quiet}}}
{void;{foreach;~member;{rolemembers;{get;!{commandname}Ares};quiet};{roleremove;{get;!{commandname}Ares};{get;~member};quiet}}}
{void;{foreach;~member;{rolemembers;{get;!{commandname}Athene};quiet};{roleremove;{get;!{commandname}Athene};{get;~member};quiet}}}
{void;{foreach;~member;{rolemembers;{get;!{commandname}Zeus};quiet};{roleremove;{get;!{commandname}Zeus};{get;~member};quiet}}}
{void;{foreach;~member;{rolemembers;{get;!{commandname}Merkur};quiet};{roleremove;{get;!{commandname}Merkur};{get;~member};quiet}}}
{void;{foreach;~member;{rolemembers;{get;!{commandname}Kratos};quiet};{roleremove;{get;!{commandname}Kratos};{get;~member};quiet}}}
{void;{foreach;~member;{rolemembers;{get;!{commandname}Dionysos};quiet};{roleremove;{get;!{commandname}Dionysos};{get;~member};quiet}}}
    
{embed;{buildembed
;color:0075FF
;title:__{upper;{commandname}}-Manager__
;description:Der WZ gegen {get;!{commandname}gegner} wurde beended und alle Rollen geleert!
;footer.text:WZ gegen {get;!{commandname}gegner}
;Thumbnail.url:https://cdn.discordapp.com/attachments/642357675283316747/686619898415546375/kisspng-hercules-and-the-lernaean-hydra-hydra-bay-the-pira-hydra-5aec47a950ab31.96105920152543428133.jpg
}}
{set;!{commandname}wz;0}
{set;!{commandname}gegner;""}
{return}}}

{//; Wenn nichts passt, dann Hilfe}
{func.help}
```
