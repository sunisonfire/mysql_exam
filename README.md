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
