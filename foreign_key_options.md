# Opciones de llaves Foráneas

## Las Foreing Key options son las siguientes:

### On update
Significa qué pasará con las relaciones cuando una de estas sea modificada en sus campos relacionados, Por ejemplo, pueden utilizarse los valores:
  - **cascade:** Si el id de un usuario pasa de 11 a 12, entonces la relacion se actualizará y el post buscará el id nuevo en lugar de quedarse sin usuario.
  - **restrict:** Si el id de un usuario pasa de 11 a 12, no lo permitirá hasta que no sean actualizados antes todos los post relacionados.
  - **set null:** Si el id de un usuario pasa de 11 a 12, entonces los post solo no estará relacionados con nada.
  - **no action:** Si el id de un usuario pasa de 11 a 12, no se hará nada. Solo se romperá la relación.
### On delete
 - **cascade:** Si un usuario es eliminado entonces se borrarán todos los post relacionados.
 - **restrict:** No se podrá eliminar un usuario hasta que sean eliminados todos su post relacionados.
 - **set null:** Si un usuario es eliminado, entonces los post solo no estará relacionados con nada.
 - **no action:** Si un usuario es eliminado, no se hará nada. Solo se romperá la relación.
