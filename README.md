# Dashboard-PeopleAnalytics

Dashboard com informações de dados de um RH

![Dashboard](https://github.com/MatheusFCBarros/Dashboard-PeopleAnalytics/blob/main/DashboardRH.png)
 
Nesse projeto eu realizei etapas como:

## Conexão com fontes de dados

A base de dados utilizada estava em um único arquivo .xlsx com os dados.

## ETL - Extrair, Transformar e Carregar dados

Após carregar os dados para o Power BI eu realizei a modelagem e transformação dos mesmos conforme a necessidade dos requisitos que eu teria que informar no Dashboard.

Por fim o modelo ficou assim:

![Modelo](https://github.com/MatheusFCBarros/Dashboard-PeopleAnalytics/blob/main/Modelo.png)

## Requisitos a serem respondidos

Oferecer um levantamento histórico sobre os dados dentro do cenário do respectivo RH Apos de 2011

Os dados foram classificados em

Data admissão, data desligamento, setor, cargo, data nascimento, motivo desligamento, escolaridade entre outros.

## Criação de calculos com funções DAX

Algumas medidas que foram criadas:

Admissões ruins = 

 CALCULATE(
 
    [Admissões],
    
    FILTER(
    
        fBaseRH_PROD,
        
        DATEDIFF(fBaseRH_PROD[DATA ADMISSAO], 
        
        fBaseRH_PROD[DATA DESLIGAMENTO], DAY) <= 90 &&
        
        NOT ISBLANK(fBaseRH_PROD[DATA DESLIGAMENTO])
    )
    
)
                 
    
Desligamentos = 

CALCULATE(

    COUNTROWS(fBaseRH_PROD),
    
    NOT ISBLANK(fBaseRH_PROD[DATA DESLIGAMENTO]),
    
    USERELATIONSHIP(dCalendario[Data], fBaseRH_PROD[DATA DESLIGAMENTO])
    
)
    
## Personalização do layout do relatório


Link para visualizar o Dashboard: https://bit.ly/3CsBzU2
