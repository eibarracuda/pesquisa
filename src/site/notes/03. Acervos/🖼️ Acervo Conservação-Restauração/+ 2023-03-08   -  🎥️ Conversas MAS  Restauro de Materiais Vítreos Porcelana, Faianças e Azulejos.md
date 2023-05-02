```dataview
table created AS "Criado em", updated AS "Modificado", tema AS "Tema", type AS "Tipo", canal AS "Canal"
where titulo != "Conversas MAS | Restauro de Materiais Vítreos: Porcelana, Faianças e Azulejos"
where contains(canal, "MAS SP - Museu de Arte Sacra de São Paulo") OR contains((tema, this.tema))
```