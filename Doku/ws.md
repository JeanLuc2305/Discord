[🏠 Start](https://jeanluc2305.github.io/Discord/)

# ws

###### Beschreibung:

WZ-Manager von Terranova

###### Benutzung:

[Prefix]ws

###### Beispiel:

[Prefix]ws

###### Code:

```
{set;~roles;635111745740079105}
{switch;true;
{hasrole;{get;~roles}};
{void};
❌ Du hast leider nicht die nötigen Berechtigungen!!!
{return}}

{exec;event;{args}}
```
