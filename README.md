Sistema de Gerenciamento Acadêmico
Este projeto é um sistema de gerenciamento acadêmico para uma faculdade, com o objetivo de organizar e armazenar informações relacionadas a alunos, cursos, matérias, professores, turmas e notas. Ele foi desenvolvido utilizando MySQL para modelar o banco de dados relacional, garantindo a integridade e consistência dos dados. Este sistema pode ser aplicado em ambientes acadêmicos para auxiliar na gestão de dados e no acompanhamento do progresso dos alunos.

Estrutura do Banco de Dados
O banco de dados é composto por várias tabelas que armazenam diferentes tipos de dados:

tbl_endereco: Armazena informações de endereços dos alunos.
tbl_alunos: Contém informações pessoais dos alunos, como nome, data de nascimento, CPF, e-mail e telefone. Além disso, a tabela está relacionada com a tabela tbl_endereco para armazenar o endereço de cada aluno.
tbl_curso: Guarda os dados dos cursos oferecidos pela faculdade, como o nome do curso e a carga horária.
tbl_materia: Registra as matérias de cada curso, com uma relação direta com a tabela tbl_curso.
tbl_professor: Contém as informações dos professores, incluindo nome, especialidade, e-mail e telefone.
tbl_turma: Define as turmas com base no ano/semestre e suas relações com as matérias e professores.
tbl_notas: Armazena as notas dos alunos, associando cada nota a um aluno e uma turma.
Relações entre as Tabelas
Alunos e Endereços: Cada aluno está relacionado a um endereço, através da chave estrangeira fk_endereco, na tabela tbl_alunos.
Cursos e Matérias: Cada matéria está vinculada a um curso por meio da chave estrangeira fk_curso, na tabela tbl_materia.
Professores e Turmas: As turmas estão associadas a professores e matérias, por meio das chaves estrangeiras fk_professor e fk_materia.
Alunos e Turmas (Notas): As notas são atribuídas a alunos específicos em turmas específicas, com as chaves estrangeiras fk_aluno e fk_turma na tabela tbl_notas.
Funcionalidades Implementadas
Inserção de dados: O sistema suporta a inserção de dados em todas as tabelas, incluindo informações sobre alunos, professores, cursos, matérias e notas.
Consultas: Foram implementadas várias consultas SQL para visualizar os dados armazenados, como:
Listar todos os alunos com seus respectivos endereços.
Listar todas as matérias de um curso.
Exibir as notas dos alunos em cada turma.
Mostrar detalhes dos professores e as turmas que lecionam.
Exemplos de Consultas
Aqui estão alguns exemplos de consultas SQL usadas no sistema:

Consulta de notas dos alunos:

sql
Copiar código
select 
    a.nome as nome_aluno,
    n.nota as nota
from 
    tbl_notas n
inner join 
    tbl_alunos a on n.fk_aluno = a.id_aluno;
Consulta de todas as turmas e seus professores:

sql
Copiar código
select 
    t.ano_semestre, 
    p.nome as professor, 
    m.nome_materia 
from 
    tbl_turma t
inner join 
    tbl_professor p on t.fk_professor = p.id_professor
inner join 
    tbl_materia m on t.fk_materia = m.id_materia;
Como Executar
Criação do Banco de Dados: Execute os comandos SQL para criar o banco de dados e suas respectivas tabelas.
Inserção de Dados: Use os comandos INSERT INTO fornecidos para popular as tabelas com dados fictícios.
Consultas: Utilize as queries SQL para realizar consultas nas tabelas e visualizar os resultados.
Tecnologias Utilizadas
MySQL: Sistema de gerenciamento de banco de dados relacional.
SQL: Linguagem de consulta estruturada para manipulação e recuperação de dados.
