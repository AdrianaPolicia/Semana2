# Semana2
CREATE TABLE alunos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  turma TEXT NOT NULL,
  curso TEXT NOT NULL,
  data_nascimento DATE
);

CREATE TABLE cursos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  duracao_anos INT
);

CREATE TABLE matriculas (
  id SERIAL PRIMARY KEY,
  aluno_id INT REFERENCES alunos(id) ON DELETE CASCADE,
  curso_id INT REFERENCES cursos(id) ON DELETE CASCADE,
  data_matricula DATE DEFAULT CURRENT_DATE
);

INSERT INTO alunos (nome, turma, curso, data_nascimento)
VALUES ('Ana Lima', '1A', 'Engenharia Civil', '2002-05-10'),
       ('Bruno Souza', '1B', 'Administração', '2003-08-15'),
       ('Isabella Calil', '1A', 'Ciência da Computação', '2002-04-30'),
       ('Luisa Lemes', '1C', 'Engenharia de Software', '2004-04-10'),
       ('Antônio de Castro', '1B', 'Engenharia de Computação', '2002-07-22'),
       ('Gabriela Porto', '1C', 'Sistemas de Informação', '2002-06-15'),
       ('Arthur Costa', '1A', 'Administração', '2003-07-16'),
       ('Theo Pinheiro', '1A', 'Sistemas de Informação', '2002-02-20'),
       ('Filipa Fernandes', '1C', 'Engenharia Civil', '2004-04-23'),
       ('Helena Ribeiro', '1B', 'Administração', '2002-06-15');

INSERT INTO cursos (nome, duracao_anos)
VALUES ('Engenharia Civil', 5),
       ('Administração', 4),
       ('Sistema de Informação',4),
       ('Engenharia de Computação',4),
       ('Engenharia de Software',4),
       ('Ciência da Computação',4);

INSERT INTO matriculas (aluno_id, curso_id)
VALUES (1, 1),
       (2, 2),
       (3, 6),
       (4, 5),
       (5, 4),
       (6, 3),
       (7, 2),
       (8, 3),
       (9, 1),
       (10, 2);

SELECT * FROM alunos;

SELECT * FROM cursos;

SELECT a.nome AS aluno, c.nome AS curso, m.data_matricula
FROM matriculas m
JOIN alunos a ON m.aluno_id = a.id
JOIN cursos c ON m.curso_id = c.id;

