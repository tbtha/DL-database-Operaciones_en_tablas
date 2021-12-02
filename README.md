```sql
--PARTE 1
--1.
--crear base de datos
CREATE DATABASE "Posts"
    WITH 
    OWNER = postgres
    ENCODING = 'UTF8'
    CONNECTION LIMIT = -1;

--2.
--crear tabla 
CREATE TABLE post (
	id_post serial,
	nombre_usuario varchar (25),
	fecha_creacion date,
	contenido varchar(30),
	descripcion varchar (30),
	primary key (id_post)
);

select * from post;

--3.
--insertar post
INSERT INTO post (nombre_usuario,fecha_creacion, contenido,descripcion)
VALUES ('Pamela', '20211010' ,'Lorem2','Lorem officiis');
select * from post;
--
INSERT INTO post (nombre_usuario,fecha_creacion, contenido,descripcion)
VALUES ('Pamela', '20211010' ,'Lorem2','Lorem ipsus');
select * from post;
--
INSERT INTO post (nombre_usuario,fecha_creacion, contenido,descripcion)
VALUES ('Carlos', '20211015' ,'Lorem','Lorem consectetur');

select * from post;

--4
--modificar la tabla, agregar columna titulo
ALTER TABLE post
add titulo varchar(20);

select * from post;

--5
--agregar titulo a las publicaciones ya ingresadas 
update post 
set titulo = 'blog'
where id_post = 1;

select * from post;
--
update post 
set titulo = 'publicacion'
where id_post = 2;

select * from post;
--
update post 
set titulo = 'entrevista'
where id_post = 3;

select * from post;

--6.
--Insertar 2 post para el usuario 'pedro'
insert into post ( nombre_usuario,fecha_creacion,contenido,descripcion,titulo)
values('Pedro', '20210622' ,'Lorem3','Lorem Ipsus','publicacion');

select * from post;

--
insert into post ( nombre_usuario,fecha_creacion,contenido,descripcion,titulo)
values('Pedro', '20210605' ,'Loremmm','Lorem Ipsus officiis','historias');

select * from post;

--7.
--eliminar el post de carlos 
delete from post 
where id_post =3;
select * from post;

--8.
--ingresar un post para carlos 
INSERT INTO post (nombre_usuario,fecha_creacion, contenido,descripcion, titulo)
VALUES ('Carlos', '20211015' ,'Lorem','Lorem consectetur ipsus', 'columna');

select * from post;

--PARTE 2

--1.
--crear nueva tabla
create table comentarios ( 
	id_comentarios serial,
	id_post_foreign int,
	fecha date,
	hora_creacion time,
	contenido varchar(30),
	primary key (id_comentarios),
	foreign key(id_post_foreign) references post (id_post)
);

select * from comentarios;

--2.
--crear comentario para los post de pamela y carlos
--pamela
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (1,'20211015','145220','creacion comentario');
select * from comentarios;
--
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (2,'20211025','135020','creacion comentario2');
select * from comentarios;
--carlos
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (7,'20211027','201220','creacion comentario columna');
select * from comentarios;
--
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (7,'20211110','141220','creacion comentario columna2');
select * from comentarios;
--
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (7,'20211115','152020','creacion comentario columna3');
select * from comentarios;
--
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (7,'20211130','185021','creacion comentario columna4');
select * from comentarios;

--3.
--crear nuevo post margarita 
insert into post (nombre_usuario,fecha_creacion,contenido,descripcion,titulo)
values ('Margarita', '20211120', 'Lorem Margarita','Lorem Ipsus consectetur ipsus','entrevista');
select * from post;

--4.
--ingresar 5 comentarios para el post margarita
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (8,'20211101','175521','comentario entrevista1');
select * from comentarios;
--
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (8,'20211102','145021','comentario entrevista2');
select * from comentarios;
--
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (8,'20211103','152040','comentario entrevista3');
select * from comentarios;
--
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (8,'20211104','165010','comentario entrevista4');
select * from comentarios;
--
insert into comentarios(id_post_foreign,fecha,hora_creacion,contenido)
values (8,'20211105','175001','comentario entrevista5');
select * from comentarios;



```

