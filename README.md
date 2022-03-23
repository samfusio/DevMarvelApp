# marvel-api


####  Base de datos 
-- Database: interfaz-marvel

-- DROP DATABASE IF EXISTS "interfaz-marvel";

CREATE DATABASE "interfaz-marvel"
    WITH 
    OWNER = postgres
    ENCODING = 'UTF8'
    LC_COLLATE = 'Spanish_El Salvador.1252'
    LC_CTYPE = 'Spanish_El Salvador.1252'
    TABLESPACE = pg_default
    CONNECTION LIMIT = -1;
	
-- Table: public.seg_usuario

-- DROP TABLE IF EXISTS public.seg_usuario;

CREATE TABLE IF NOT EXISTS public.seg_usuario
(
    id bigint NOT NULL,
    usuario character varying(15) COLLATE pg_catalog."default" NOT NULL,
    clave character varying(100) COLLATE pg_catalog."default" NOT NULL,
    nombre character varying(100) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT seg_usuario_pkey PRIMARY KEY (id)
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.seg_usuario
    OWNER to postgres;

-- Table: public.marvel_busquedas

-- DROP TABLE IF EXISTS public.marvel_busquedas;

CREATE TABLE IF NOT EXISTS public.marvel_busquedas
(
    id_busqueda integer NOT NULL DEFAULT nextval('marvel_busquedas_id_busqueda_seq'::regclass),
    codigo character varying(20) COLLATE pg_catalog."default",
    descripcion_busqueda character varying(250) COLLATE pg_catalog."default",
    url character varying(100) COLLATE pg_catalog."default",
    CONSTRAINT marvel_busquedas_pkey PRIMARY KEY (id_busqueda)
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.marvel_busquedas
    OWNER to postgres;
    
## Insertar registro Usuario

INSERT INTO public.seg_usuario(
	id, usuario, clave, nombre)
	VALUES (1, 'admin', '$2a$10$XURPShQNCsLjp1ESc2laoObo9QZDhxz73hJPaEv7/cBha4pk0AgP.', 'Samuel Canjura');

#### Obtener Token
http://localhost:8080/gettoken

{ "username": "admin", "password": "password"}

##Servicios

* http://localhost:8080/gettoken

* Datos de Personajes
* http://localhost:8080/marvelapp/personajes
* http://localhost:8080/marvelapp/personajes/id/{id}
* http://localhost:8080/marvelapp/personajes/comics/{id}
* http://localhost:8080/marvelapp/personajes/nombre/{nombre}
* http://localhost:8080/marvelapp/personajes/historietas/{historietas}
* http://localhost:8080/marvelapp/personajes/serie/{serie}
* http://localhost:8080/marvelapp/personajes/imagen/{nombre}
* http://localhost:8080/marvelapp/personajes/detalle/{historietas}/{serie}

* Datos de Series
* http://localhost:8080/marvelapp/series

* Datos de comics
* http://localhost:8080/marvelapp/comics
* http://localhost:8080/marvelapp/comics/{id}
* http://localhost:8080/personajes/comics/{idPersonaje}

* Datos de historietas
* http://localhost:8080/marvelapp/historietas
* http://localhost:8080/marvelapp/historietas/creadorid/{id}
* http://localhost:8080/marvelapp/historietas/{id}/creadores
* http://localhost:8080/marvelapp/historietas/{id}

* Datos de usuarios que realizaron busquedas
* http://localhost:8080/marvelapp/usuarios
* http://localhost:8080/marvelapp/buscarusuariocodigo/{codigo}
* http://localhost:8080/marvelapp/buscarusuario

 

#### Technologies

* Java 8
* Spring Boot 2.5.4
* Lombok
* Swagger
* Eclipse 
* postgres db
* 
