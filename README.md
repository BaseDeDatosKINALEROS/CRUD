# CRUD
cruds
	/*PROCEDIMIENTOS ALMACENADOS TOTAL*/
/*1.Bono*/
/**************************CREATE*********************************/
DROP PROCEDURE sp_create_bono
DELIMITER $$
CREATE PROCEDURE sp_create_bono (Bono INT(10))
BEGIN
	INSERT INTO Bono(cantidadBono) VALUES (Bono);
END$$
SELECT * FROM Bono;
CALL sp_create_bono (250);
/***********************UPDATE**************************/
DROP PROCEDURE sp_update_bono
DELIMITER $$
CREATE PROCEDURE sp_update_bono (id_Bono1 INT(10),NuevoBono INT(10))
BEGIN
	UPDATE Bono
	SET cantidadBono=NuevoBono WHERE id_Bono=id_Bono1;
END$$
SELECT * FROM Bono;
CALL sp_update_bono ('1','250');
/***********************READ***********************************/
DROP PROCEDURE sp_read_bono
DELIMITER $$
CREATE PROCEDURE sp_read_bono (id_Bono1 INT(10))
BEGIN
    SELECT * FROM Bono WHERE id_bono=id_bono1;
END$$
CALL sp_read_bono (1);
/***************************DELETE*******************************/
DROP PROCEDURE sp_delete_bono
DELIMITER $$
CREATE PROCEDURE sp_delete_bono (id_Bono1 INT(10))
BEGIN
    DELETE FROM Bono WHERE id_bono=id_bono1;
END$$
CALL sp_delete_bono (4);
/*2.Region*/
#----------------------------------------2--------------------------------------------------
#--------------------create-----------------------------------
delimiter $$
create procedure sp_create_region(nombre varchar(25))
begin
insert into region (nombreREgion) values (nombre);
end $$

call sp_create_region("NorEste");

#---------------------update---------------------------------
delimiter $$
create procedure sp_update_region(nombre1 varchar(25), id1 int)
begin
update region set nombreRegion = nombre1 where id_Region=id1;
end $$

call sp_update_region('Norte',1);

#------------------delete------------------------------------
delimiter $$ 
create procedure sp_delete_region(id1 int)
begin
delete from region where id_Region=id1;
end $$

call sp_delete_region(1);

#---------------------------read---------------------------
delimiter $$
create procedure sp_read_region(id1 int)
begin
select * from region where id_Region=id1;
end $$

call sp_read_region(2);

/*3.Sexo*/
#-----------------------------------------------------3----------------------------------------------------------------
#-----------------------create-------------------------------
delimiter $$
create procedure sp_insert_sexo (sexo varchar(20))
begin
insert into sexo (sexo) values(sexo);
end $$
delimiter ;

#------------------------update-----------------------------
delimiter $$
create procedure sp_actualizar_sexo(id int, sexo varchar(20))
begin
update sexo set sexo=sexo where id_sexo=id;
end $$
delimiter ;

#------------------------delete--------------------------
delimiter $$
create procedure sp_delete_sexo (id int)
begin 
delete from sexo where id_sexo=id;
end $$
delimiter ;

#--------------------------read----------------------------
delimiter $$
create procedure sp_mostrar_sexo(id int)
begin 
select id_sexo,sexo from sexo where id_sexo=id;
end $$
delimiter $$
/*4.TipoEmpleado*/
/* Crud
create 
read
update 
delete */
/* Creacion de tablas */
drop procedure sp_Tipo_Empleado
delimiter $$ 
create procedure sp_Tipo_Empleado (nombreTipoEmpleado1 varchar (15))
begin 
insert into TipoEmpleado (nombreTipoEmpleado) values (nombreTipoEmpleado1);
end $$
call sp_Tipo_Empleado ('No Definido');
select * from TipoEmpleado 
/LEER/
select * from TipoEmpleado where TipoEmpleado.nombreTipoEmpleado='No Definido'
/* ACTUALIZAR */
drop procedure sp_Tipo_Empleado1
delimiter $$ 
create procedure sp_Tipo_Empleado1 (id_TipoEmpleado1 int , nombreTipoEmpleado1 varchar (15))
begin 
update TipoEmpleado set nombreTipoEmpleado = nombreTipoEmpleado1 
where id_TipoEmpleado =id_TipoEmpleado1;
end $$
call sp_Tipo_Empleado1 (3,'No Definido2');
select * from TipoEmpleado
/* ELIMINAR */
drop procedure sp_Tipo_Empleado2
delimiter $$ 
create procedure sp_Tipo_Empleado2 (id_TipoEmpleado1 int )
begin 
delete from TipoEmpleado where id_TipoEmpleado=id_TipoEmpleado1;
end $$
call sp_Tipo_Empleado2 (3);
select * from TipoEmpleado

/*5.Sede*/
/************CREATE************/
CREATE TABLE Departamento (
id_Departamento INT NOT NULL PRIMARY KEY AUTO_INCREMENT, 
nombreDepartamento VARCHAR(25),
id_Sede INT,
FOREIGN KEY (id_Sede) REFERENCES Sede(id_Sede)ON DELETE CASCADE
);

DROP PROCEDURE sp_create_departamento
DELIMITER $$
CREATE PROCEDURE sp_create_departamento (Departamento1 VARCHAR(10), id_Sede1 INT(10))
BEGIN
	INSERT INTO Departamento(nombreDepartamento,id_Sede) VALUES (Departamento1,id_Sede1);
END$$
SELECT * FROM Departamento;
CALL sp_create_departamento ('Cocina',8);
/***********************UPDATE**************************/
DROP PROCEDURE sp_update_departamento
DELIMITER $$
CREATE PROCEDURE sp_update_departamento (id_Departamento1 INT(10),Departamento1 VARCHAR(20), id_Sede1 INT(10))
BEGIN
	UPDATE Departamento
	SET nombreDepartamento=Departamento1 ,id_Sede=id_Sede1  WHERE id_Departamento=id_Departamento1;
END$$
SELECT * FROM Departamento;
CALL sp_update_departamento (9,'Concinita',8);
/***********************READ***********************************/
DROP PROCEDURE sp_read_departamento
DELIMITER $$
CREATE PROCEDURE sp_read_departamento (id_departamento1 INT(10))
BEGIN
    SELECT * FROM Departamento WHERE id_Departamento=id_departamento1;
END$$
CALL sp_read_departamento (9);
/***************************DELETE*******************************/
DROP PROCEDURE sp_delete_departamento
DELIMITER $$
CREATE PROCEDURE sp_delete_departamento (id_departamento1 INT(10))
BEGIN
    DELETE FROM Departamento WHERE id_Departamento=id_departamento1;
END$$
SELECT * FROM Departamento;
CALL sp_delete_departamento (9);
/*CRUD*/
/************************CREATE**************************/
DROP PROCEDURE sp_create_sede
DELIMITER $$
CREATE PROCEDURE sp_create_sede (Sede1 VARCHAR(10), id_region1 INT(10))
BEGIN
	INSERT INTO Sede(nombreSede,id_Region) VALUES (Sede1,id_region1);
END$$
SELECT * FROM Sede;
CALL sp_create_sede ('Zona7',4);
/***********************UPDATE**************************/
DROP PROCEDURE sp_update_sede
DELIMITER $$
CREATE PROCEDURE sp_update_sede (id_Sede1 INT(10),Sede1 VARCHAR(20), id_region1 INT(10))
BEGIN
	UPDATE Sede
	SET nombreSede=Sede1 ,id_Region=id_region1  WHERE id_Sede=id_Sede1;
END$$
SELECT * FROM Sede;
CALL sp_update_sede (9,'Zona Centro',4);
/***********************READ***********************************/
DROP PROCEDURE sp_read_sede
DELIMITER $$
CREATE PROCEDURE sp_read_sede (id_Sede1 INT(10))
BEGIN
    SELECT * FROM Sede WHERE id_Sede=id_Sede1;
END$$
CALL sp_read_sede (1);
/***************************DELETE*******************************/
DROP PROCEDURE sp_delete_sede
DELIMITER $$
CREATE PROCEDURE sp_delete_sede (id_sede1 INT(10))
BEGIN
    DELETE FROM Sede WHERE id_Sede=id_sede1;
END$$
SELECT * FROM Sede;
CALL sp_delete_sede (9);
/*6.Departamento*/

/*7.Telefono*/
/* Creacion de tablas */
drop procedure sp_Telefono
delimiter $$ 
create procedure sp_Telefono(numero1 int,id_Departamento1 int )
begin 
insert into telefono (numero,id_Departamento) values (numero1,id_Departamento1);
end $$
call sp_Telefono(666669,9);
select * from Telefono
/LEER/
select * from Telefono where Telefono.numero=666669
/* ACTUALIZAR */
drop procedure sp_Telefono1
delimiter $$ 
create procedure sp_Telefono1(id_Telefono1 int , numero2 int ,id_Departamento2 int)
begin 
update Telefono set numero=numero2, id_Departamento = id_Departamento2
where id_Telefono=id_Telefono1;
end $$
call sp_Telefono(9,666669,9);
select * from Telefono 
/* ELIMINAR */
drop procedure sp_Telefono2
delimiter $$ 
create procedure sp_Telefono2 (id_Telefono3 int )
begin 
delete from Telefono where id_Telefono = id_Telefono3;
end $$
call sp_Telefono(9);
select * from Telefono
/*8.Salario*/
#------------------------------------------------------8---------------------------------------------------------------
#---------------------create----------------------------------
delimiter $$
create procedure sp_insert_salario(cantidadsalario int,id_bono int)
begin
insert into salario (cantidadsalario,id_bono) values(cantidadsalario,id_bono);
end $$
delimiter ;

#----------------------update------------------------------
delimiter $$	
create procedure sp_actualizar_salario(id int,cantidadsalario INT,id_bono int)
begin 
update salario set cantidadsalario=cantidadsalario,id_bono=id_bono where id_salario=id;

end $$
delimiter ;

#--------------------delete-----------------------------------
delimiter $$
create procedure sp_delete_salario(id int )
begin
delete from salario where id_salario=id;
end $$
delimiter ;

#-----------------------------read--------------------------
delimiter $$
create procedure sp_mostrar_salario(id int)
begin
select * from salario where id_salario=id;
end $$
/*9.Puesto*/
#------------------------------------------------------9----------------------------------------------------------------
#---------------------update---------------------------------
delimiter $$
create procedure sp_create_puesto(nombre varchar(30), idSalario1 int)
begin
insert into puesto (nombrePuesto, id_Salario) values (nombre, idSalario1);
end $$


call sp_create_puesto("Encargado",2);

#--------------------update-----------------------------------
delimiter $$
create procedure sp_update_puesto(nombre1 varchar(30), idSalario1 int, id1 int)
begin
update puesto set nombrePuesto=nombre1, id_Salario=idSalario1 where id_Puesto=id1;
end $$

call sp_update_puesto("Maestro",2,1)

#------------------delete------------------------------------
delimiter $$
create procedure sp_delete_puesto(id1 int)
begin
delete from puesto where id_Puesto=id1; 
end $$

call sp_delete_puesto(2);

#---------------------read---------------------------------
delimiter $$ 
create procedure sp_read_puesto(id1 int)
begin
select * from puesto where id_Puesto=id1;
end $$

call sp_read_puesto(1);
/*10.Empleado*/
/**************************CREATE*********************************/
DROP PROCEDURE sp_create_empleado
DELIMITER $$
CREATE PROCEDURE sp_create_empleado (nombreEmpleado1 VARCHAR(30), edad1 INT(10),fechaContratacion1 DATE,id_Puesto1 INT(10),id_Departamento1 INT(10),id_sexo1 INT(10),Id_TipoEmpleado1 INT(10))
BEGIN
	INSERT INTO Empleado(nombreEmpleado,edad,fechaContratacion,id_Puesto,id_Departamento,id_sexo,Id_TipoEmpleado)
    VALUES(nombreEmpleado1,edad1,fechaContratacion1,id_Puesto1,id_Departamento1,id_sexo1,Id_TipoEmpleado1);
END$$
SELECT * FROM Empleado;
CALL sp_create_empleado ('Julian Cabrera','25','2010-01-12',4,8,1,1);
/***********************UPDATE**************************/
DROP PROCEDURE sp_update_empleado 
DELIMITER $$
CREATE PROCEDURE sp_update_empleado (id_Empleado1 INT(10),Nuevo_nombreEmpleado1 VARCHAR(30), Nuevo_edad1 INT(10),Nuevo_fechaContratacion1 DATE,Nuevo_id_Puesto1 INT(10),
Nuevo_id_Departamento1 INT(10),Nuevo_id_sexo1 INT(10),Nuevo_Id_TipoEmpleado1 INT(10))
BEGIN
	UPDATE Empleado
	SET nombreEmpleado=Nuevo_nombreEmpleado1, edad=Nuevo_edad1,fechaContratacion=Nuevo_fechaContratacion1, id_Puesto=Nuevo_id_Puesto1, id_Departamento=Nuevo_id_Departamento1, 
    id_sexo=Nuevo_id_sexo1, Id_TipoEmpleado=Nuevo_Id_TipoEmpleado1
    WHERE id_Empleado=id_Empleado1;
END$$
SELECT * FROM Empleado;
CALL sp_update_empleado ('13','Jose Cabrera','25','2010-01-12',4,8,1,1);
/***********************READ***********************************/
DROP PROCEDURE sp_read_empleado
DELIMITER $$
CREATE PROCEDURE sp_read_empleado (id_empleado1 INT(10))
BEGIN
    SELECT * FROM Empleado WHERE id_empleado=id_empleado1;
END$$
CALL sp_read_empleado (13);
/***************************DELETE*******************************/
DROP PROCEDURE sp_delete_empleado
DELIMITER $$
CREATE PROCEDURE sp_delete_empleado (id_empleado1 INT(10))
BEGIN
    DELETE FROM Empleado WHERE id_Empleado=id_empleado1;
END$$
SELECT * FROM Empleado;
CALL sp_delete_empleado (13);
/*************************************************************************/
