# 🐾 Examen MySQL: Veterinaria

Examen práctico de MySQL realizado en Campuslands. Consiste en resolver 6 consultas sobre una base de datos de una veterinaria que maneja mascotas, propietarios, veterinarios y consultas.

## 🗂️ Tablas

| Tabla | Descripción |
|---|---|
| `propietario` | Dueños de las mascotas |
| `mascota` | Mascotas y su propietario (`propietario_fk`) |
| `veterinario` | Veterinarios y su especialidad |
| `consulta` | Consultas realizadas, con veterinario, mascota y valor cobrado |

## 🔍 Consultas resueltas

| # | Qué resuelve | Conceptos usados |
|---|---|---|
| 1 | Lista cada mascota con su especie y el nombre completo de su propietario | `LEFT JOIN`, `CONCAT` |
| 2 | Cantidad de veterinarios por especialidad | `COUNT`, `GROUP BY` |
| 3 | Cantidad de consultas por mascota | `LEFT JOIN`, `COUNT`, `GROUP BY` |
| 4 | Top 3 de veterinarios que más han facturado, con su número de consultas | `INNER JOIN`, `SUM`, `ORDER BY`, `LIMIT` |
| 5 | Propietarios con más de una mascota | `LEFT JOIN`, `GROUP BY`, `HAVING` |
| 6 | Veterinarios que han facturado más de 3000, con consultas atendidas, total y promedio | `SUM`, `AVG`, `HAVING` |


Pregunta 1
select mascota.nombre as mascota, mascota.especie, concat(propietario.nombre, ' ', propietario.apellido) as propietario from mascota
    -> left join propietario
    -> on mascota.propietario_fk=propietario.id
    -> ;
<img width="739" height="184" alt="image" src="https://github.com/user-attachments/assets/d5b6e0b0-0722-4dd5-9daa-4be5fa355f23" />
Pregunta 2
select veterinario.especialidad, count(*) as cantidad from veterinario
    -> group by especialidad
    -> ;
<img width="506" height="149" alt="image" src="https://github.com/user-attachments/assets/ecde3070-76b3-4e29-b445-9bdfbe783533" />
Pregunta 3
select mascota.nombre as mascota, count(*) as cantidad_consultas from mascota
    -> left join consulta
    -> on consulta.mascota_fk=mascota.id
    -> group by mascota
    -> ;
<img width="616" height="174" alt="image" src="https://github.com/user-attachments/assets/d44b8226-3c9a-42e7-92bb-6373c0e6a76a" />
Pregunta 4
select concat(veterinario.nombre, ' ', veterinario.apellido) as nombre_completo, veterinario.especialidad, count(*) as cantidad_consultas, sum(consulta.valor_cobrado) as valor_total
    -> from veterinario
    -> inner join consulta
    -> on veterinario.id=consulta.veterinario_fk
    -> group by veterinario_fk
    -> order by valor_total desc limit 3;
<img width="754" height="188" alt="image" src="https://github.com/user-attachments/assets/008ef8c9-7e2b-4f42-b02c-e0625498f6d9" />
Pregunta 5
select concat(propietario.nombre, ' ', propietario.apellido) as nombre_completo, count(*) as cantidad_mascotas from propietario
    -> left join mascota
    -> on mascota.propietario_fk=propietario.id
    -> group by nombre_completo
    -> having count(*) > 1;
  <img width="736" height="184" alt="image" src="https://github.com/user-attachments/assets/c8aa00b1-a1fc-4edb-a3cb-5e947fc67991" />
Pregunta 6
select concat(veterinario.nombre, ' ', veterinario.apellido) as veterinario, count(*) as consultas_atendidad, sum(consulta.valor_cobrado) as total_facturado, avg(valor_cobrado) as promedio from veterinario
    -> left join consulta
    -> on veterinario.id=consulta.veterinario_fk
    -> group by veterinario
    -> having total_facturado>3000
    -> ;
    <img width="742" height="187" alt="image" src="https://github.com/user-attachments/assets/7d5b6c70-2ee2-4cc2-8765-e7210509d05b" />
    

