

Alle speciale alfanumerische karakters opzoeken:

```bash
grep -E "\w" tvg_111/*.txt | tr -d '[:punct:]' | tr -d ' ' | sed -E 's/[A-Za-z0-9]//g' | sed -E 's/(.)/\1 /g' | tr ' ' '\n' | grep -E "\w" | sort | uniq -c | sort -g
```

Een template maken voor herschrijfpatronen voor speciale karakters:

```bash
grep -E "\w" tvg_111/*.txt | tr -d '[:punct:]' | tr -d ' ' | sed -E 's/[A-Za-z0-9]//g' | sed -E 's/(.)/\1 /g' | tr ' ' '\n' | grep -E "\w" | sort | uniq | sort | awk '{print "s/" $1 "//g"}'
```

Dit kun je vervolgens schrijven naar een bestand en daarin invullen hoe je bepaalde karakters wilt herschrijven:

```bash
grep -E "\w" tvg_111/*.txt | tr -d '[:punct:]' | tr -d ' ' | sed -E 's/[A-Za-z0-9]//g' | sed -E 's/(.)/\1 /g' | tr ' ' '\n' | grep -E "\w" | sort | uniq | sort | awk '{print "s/" $1 "//g"}' > tvg_herschrijfpatronen.txt
```

Als je deze opent in een teksteditor en per karakter aangeeft hoe je deze wilt herschrijven, kun je het aangepaste bestand als input gebruiken voor 

