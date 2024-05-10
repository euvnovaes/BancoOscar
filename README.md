# BancoOscar
exercícios em MySQL no banco de dados das cerimonias do Oscar


/* ATIVIDADE MYSQL - OSCAR */

-- 1- Quantas vezes Natalie Portman foi indicada ao Oscar?
SELECT COUNT(*) FROM indicados_ao_oscar WHERE nome_do_indicado = 'Natalie Portman';
-- 3 vezes


-- 2- Quantos Oscars Natalie Portman ganhou?
SELECT COUNT(*) FROM indicados_ao_oscar WHERE nome_do_indicado = 'Natalie Portman' AND vencedor = 'true';
-- 1 vez


-- 3- Amy Adams já ganhou algum Oscar?
SELECT COUNT(*) FROM indicados_ao_oscar WHERE nome_do_indicado = 'Amy Adams' AND vencedor = 'true';
-- Não ganhou


-- 4- A série de filmes Toy Story ganhou um Oscar em quais anos?
SELECT ano_cerimonia, nome_do_filme FROM indicados_ao_oscar WHERE nome_do_filme LIKE '%Toy Story%' AND vencedor = 'true';
-- Ganharam em 2011 e 2020


-- 5- A partir de que ano que a categoria "Actress" deixa de existir? 
SELECT ano_cerimonia FROM indicados_ao_oscar WHERE categoria = 'ACTRESS' ORDER BY ano_cerimonia DESC;
-- deixa de existir em 1976


-- 6- O primeiro Oscar para melhor Atriz foi para quem? Em que ano?
SELECT ano_cerimonia, nome_do_indicado FROM indicados_ao_oscar WHERE vencedor = 'true' AND categoria = 'ACTRESS' ORDER BY ano_cerimonia;
-- O primeiro oscar de melhor atriz foi para Janet Gaynor em 1928


-- 7- Na coluna/campo "Vencedor", altere todos os valores com "Sim" para 1 e todos os valores "Não" para 0.
UPDATE indicados_ao_oscar SET vencedor = '1' WHERE vencedor = 'true'; 
UPDATE indicados_ao_oscar SET vencedor = '0' WHERE vencedor = 'false';


-- 8- Em qual edição do Oscar "Crash" concorreu ao Oscar?
SELECT ano_cerimonia, nome_do_filme FROM indicados_ao_oscar WHERE nome_do_filme = 'Crash';
-- Ele concorreu ao Oscar em 2006


-- 9- Bom... dê um Oscar para um filme que merece muito, mas não ganhou.
SELECT * FROM indicados_ao_oscar WHERE nome_do_filme = 'Society of the Snow';
UPDATE indicados_ao_oscar SET vencedor = '1' WHERE vencedor = '0' AND nome_do_filme = 'Society of the Snow';


-- 10- O filme Central do Brasil aparece no Oscar?
SELECT * FROM indicados_ao_oscar WHERE nome_do_filme LIKE '%Brasil%';
-- não aparece.


-- 11- Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser
INSERT INTO indicados_ao_oscar (ano_filmagem,ano_cerimonia,cerimonia,categoria,nome_do_indicado,nome_do_filme,vencedor) VALUES (2023,2024,96,'CINEMATOGRAPHY','Vinicius Novaes','A volta dos que não foram','1');
INSERT INTO indicados_ao_oscar (ano_filmagem,ano_cerimonia,cerimonia,categoria,nome_do_indicado,nome_do_filme,vencedor) VALUES (2023,2024,96,'DIRECTING','Vinicius Novaes Nolan','Se a mulher deixar eu vou','1');
INSERT INTO indicados_ao_oscar (ano_filmagem,ano_cerimonia,cerimonia,categoria,nome_do_indicado,nome_do_filme,vencedor) VALUES (2023,2024,96,'SOUND','Vinicius Beethoven Pereira','O som do silêncio','1');


