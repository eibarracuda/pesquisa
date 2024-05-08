```dataview
TABLE WITHOUT ID file.link + "<br>" + "<small>*Modificado em: "+file.mtime+"*</small> | <small>Criado em: "+file.ctime+"</small>" AS "Relacionados" FROM !outgoing([#this.file.name](#this.file.name)) AND [#this.file.name](#this.file.name) AND -"00. Obsidian" SORT file.name
```