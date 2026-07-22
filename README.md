#  Power BI

<hr style="height:2px;border:none;background:linear-gradient(90deg, #2d5016, #6b8e4e, transparent);margin-top:0;">

Dashboard interativo desenvolvido no Power BI para análise de desempenho financeiro e comercial de uma empresa fictícia no ramo farmacêutico, como exercício prático do curso  de Power BI da Karine Lago.

## Objetivo

Consolidar dados financeiros e comerciais em um painel único, permitindo análise de desempenho.

## Etapas realizadas

- Transformação dos dados no Power Query
- Criação  de tabela calendário
- Criação  de tabela dimensão
- Relacionamento entre tabelas
- Cáculo DAX
- Criação de Medidas Explícitas
- Criação Dashboard
   
## Ferramentas

`Power BI` `Power Query` `DAX`

<hr style="height:1px;border:none;background:#d0d0d0;">

## Prints

<img width="1346" height="680" alt="image" src="https://github.com/user-attachments/assets/d8e7ebbd-8534-4be9-a141-aedf17233f9b" />




 



<img width="1888" height="884" alt="image" src="https://github.com/user-attachments/assets/d753d513-1632-4e7f-8310-ef284370a0dc" />







<img width="1859" height="850" alt="image" src="https://github.com/user-attachments/assets/dce5c5cd-8983-4169-aad6-bcd3d97f8900" />





<img width="1898" height="945" alt="image" src="https://github.com/user-attachments/assets/99f8495c-38ca-403b-b1f5-8e30a053702e" />




<img width="1151" height="651" alt="image" src="https://github.com/user-attachments/assets/98725da8-ba79-4bda-abf7-857d05342fbb" />





 <img width="1150" height="648" alt="image" src="https://github.com/user-attachments/assets/f437c5bb-0583-4721-8073-9df3124b50de" />




 <img width="1162" height="651" alt="image" src="https://github.com/user-attachments/assets/e5d8aae0-9289-4b2f-acde-7beecbc9c210" />

 

📥 [Baixar Dashboard em PDF](https://github.com/marianadesouza1991/projeto-power-bi/raw/main/dashboard_pdf.pdf)
 

 

## Tabela Calendário

let
    // 1. Identifica a data mínima e máxima da sua tabela fato "Receitas"
    DataMinima = List.Min(Receitas[Data]),
    DataMaxima = List.Max(Receitas[Data]),

    // 2. Determina o início do primeiro ano e o fim do último ano
    DataInicio = Date.StartOfYear(DataMinima),
    DataFim = Date.EndOfYear(DataMaxima),

    // 3. Calcula a quantidade de dias entre as datas
    Duracao = Duration.Days(Duration.From(DataFim - DataInicio)) + 1,

    // 4. Gera a lista de datas
    Fonte = List.Dates(DataInicio, Duracao, #duration(1, 0, 0, 0)),

    // 5. Converte a lista em Tabela
    ConversaoEmTabela = Table.FromList(Fonte, Splitter.SplitByNothing(), null, null, ExtraValues.Error),
    ColunaRenomeada = Table.RenameColumns(#"ConversaoEmTabela",{{"Column1", "Data"}}),
    TipoAlterado = Table.TransformColumnTypes(#"ColunaRenomeada",{{"Data", type date}})

in
    TipoAlterado



<hr style="height:2px;border:none;background:linear-gradient(90deg, transparent, #6b8e4e, #2d5016);">







