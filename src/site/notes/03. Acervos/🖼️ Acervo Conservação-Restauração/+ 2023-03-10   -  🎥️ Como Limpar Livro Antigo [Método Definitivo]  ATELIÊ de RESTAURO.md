```dataview
table created AS "Criado em", updated as Modificado, tema as Tema, type AS Tipo, canal AS Canal
where titulo != "Como Limpar Livro Antigo [Método Definitivo] | ATELIÊ de RESTAURO"
where contains(canal, "Arte de Fato") OR contains((tema, this.tema))
```