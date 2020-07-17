[🏠 Start](https://jeanluc2305.github.io/Discord/)

# hangmsg

###### Beschreibung:

Gibt die Anleitung für das Hangman Spiel im angegebenen Kanal aus

###### Benutzung:

[Prefix]hangmsg Kanalname

###### Beispiel:

[Prefix]hangmsg hangman-kanal

Ergebnis:

![hangmsg](https://cdn.discordapp.com/attachments/642357675283316747/733630398495588430/unknown.png)

###### Code:

```
{set;~eColor;[]}
{set;~roles;{roles;{userid}}}
{foreach;~color;{get;~roles};
  {if;{rolecolor;{get;~color}};!=;000000;
    {push;{get;~eColor};{rolecolor;{get;~color}}}}}
{if;{length;{get;~eColor}};==;0;
  {set;~eColor;c1694f}}

{//;Sende die Abfrage nachricht mit der Liste der gegner:}
{set;~msg;{send;{channelid};
  
Möchtest du die Hilfe für Hangman in den Hangman Kanal senden dann 👍, bei 👎 wird die Nachricht hier ausgegeben und 🚫 für abbrechen.}}
 
{reactadd;{get;~msg};👍👎🚫}
{//;Abwarten auf Reaktion}
{void;
  {waitreaction;{get;~msg};{userid};👍👎🚫;            {set;~reaction;{reaction}}}}
{//;Auslesen der Reaktionen}
{clean;{switch;{get;~reaction};
🚫;Deine Anfrage wurde abgebrochen!;
👍;{void;{send;{args};
{embedbuild;
    author.icon_url:{useravatar};
    author.name:Hangman (nur englische Wörter);
    thumbnail.url:https://i.imgur.com/VOAuWP5.gif;
    color:b57528;
    fields.name:<:SmallBrownDiamond:453842989345669120>Start a New Spiel starten:;
    fields.value:
▪`{prefix}hm start [easy/medium/hard]`

Die eckigen Klammern "[]" bedeuten, dass der Inhalt optional ist. 
Wenn du eine eigene Schwierigkeit angeben möchten, gib einfach das entsprechende Schwierigkeitswort direkt nach dem Start ein, wie im obigen Beispiel (ohne die Klammern).
{zws};
    fields.name:<:SmallBrownDiamond:453842989345669120>Play the Game / Spiel spielen:;
    fields.value:
▪`{prefix}hm letter/word`
▪`{prefix}hm stop`

Gib zum Spielen einfach den Namen des Tags ein + einen Buchstaben oder Wort an, das erraten werden soll! Oder gib Stop an, wenn du das Spiel beenden möchest.
{zws};
    fields.name:<:SmallCheckeredFlag:453516331464261662>Check your Stats / Statistiken:;
    fields.value:
▪`{prefix}hm stats`

Du kannst die Statistik nur prüfen, wenn kein Spiel läuft!;
    footer.icon_url:https://i.imgur.com/VOAuWP5.gif;
    footer.text:By: Allen Miquel#8168 & Willard21_2#2815
  }}}
Erledigt!;
👎;{void;{send;{channelid};
{embedbuild;
    author.icon_url:{useravatar};
    author.name:Hangman (nur englische Wörter);
    thumbnail.url:https://i.imgur.com/VOAuWP5.gif;
    color:b57528;
    fields.name:<:SmallBrownDiamond:453842989345669120>Start a New Spiel starten:;
    fields.value:
▪`{prefix}hm start [easy/medium/hard]`

Die eckigen Klammern "[]" bedeuten, dass der Inhalt optional ist. 
Wenn du eine eigene Schwierigkeit angeben möchten, gib einfach das entsprechende Schwierigkeitswort direkt nach dem Start ein, wie im obigen Beispiel (ohne die Klammern).
{zws};
    fields.name:<:SmallBrownDiamond:453842989345669120>Play the Game / Spiel spielen:;
    fields.value:
▪`{prefix}hm letter/word`
▪`{prefix}hm stop`

Gib zum Spielen einfach den Namen des Tags ein + einen Buchstaben oder Wort an, das erraten werden soll! Oder gib Stop an, wenn du das Spiel beenden möchest.
{zws};
    fields.name:<:SmallCheckeredFlag:453516331464261662>Check your Stats / Statistiken:;
    fields.value:
▪`{prefix}hm stats`

Du kannst die Statistik nur prüfen, wenn kein Spiel läuft!;
    footer.icon_url:https://i.imgur.com/VOAuWP5.gif;
    footer.text:By: Allen Miquel#8168 & Willard21_2#2815
  }}}}}
  ```
