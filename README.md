Gestão Organizacional e Empresarial (SQL)

## Resumo

Este projeto consiste em um script SQL completo para a criação, povoamento e consulta de um banco de dados voltado à gestão organizacional e empresarial. O sistema modela de forma detalhada a estrutura de empregados, departamentos, projetos, tarefas e a alocação entre essas entidades. Além da estrutura relacional, o projeto inclui uma série de consultas analíticas complexas, utilizando junções (JOINs) e agrupamentos para a extração de relatórios e análise de dados.

## Dependências e Requisitos

* **Linguagem:** SQL.
* **SGBD Recomendado:** PostgreSQL, devido ao suporte nativo a schemas, restrições `DEFERRABLE`, uso do tipo `numeric` e notação específica. O script é adaptável para outros sistemas como MySQL, SQL Server ou Oracle com pequenos ajustes.
* **Ferramentas:** Qualquer cliente de banco de dados ou terminal do SGBD, como pgAdmin, DBeaver, DataGrip ou o terminal `psql`.

## Instruções de Instalação e Execução

Para configurar o banco de dados, siga a ordem de execução abaixo:

1.  **Conexão e Preparação:**
    Conecte-se ao seu gerenciador de banco de dados e certifique-se de criar o schema necessário para o script. Utilize o comando:
    `CREATE SCHEMA empresa;` ou `CREATE SCHEMA eempresa;`.

2.  **Criação das Tabelas:**
    Execute os blocos `CREATE TABLE` para gerar as entidades e definir as restrições de integridade.

3.  **Povoamento de Dados:**
    Execute os comandos `INSERT` para inserir os dados iniciais de teste e popular as tabelas criadas.

4.  **Execução de Consultas:**
    Selecione e execute os blocos de `SELECT` localizados ao final do arquivo para visualizar os relatórios analíticos.

## Exemplos de Uso

Abaixo estão dois exemplos de relatórios que podem ser extraídos após a configuração correta do banco:

### Identificar o departamento com a maior média salarial
```sql
SELECT d.dnome
FROM empresa.departamento d
JOIN empresa.empregado e ON d.codigo = e.cdep
GROUP BY d.dnome
ORDER BY AVG(e.salario) DESC
LIMIT 1;
```

### Listar empregados de um departamento específico (ex: Marketing)
```sql
SELECT E.enome
FROM eempresa.empregado E
INNER JOIN eempresa.departamento D ON E.cdep = D.codigo
WHERE D.dnome = 'Marketing';
```
