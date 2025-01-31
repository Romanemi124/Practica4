# Práctica: API GraphQL para Tienda de Repuestos
## Descripción:
Crearás una API GraphQL para gestionar vehículos clásicos y sus repuestos. Usarás MongoDB Atlas como base de datos y desplegarás el proyecto en Deno Deploy. Se agregarán funcionalidades avanzadas con filtros específicos para consultas. Cada vehículo incluirá una broma obtenida de una API externa. La entrega será una release de GitHub con el código y un enlace al servicio en producción.
joke API: https://official-joke-api.appspot.com/
Endpoints
### 1. Consultar todos los vehículos
Lista todos los vehículos clásicos, incluyendo sus repuestos y una broma aleatoria.
Consulta:
```
query {
  vehicles {
    id
    name
    manufacturer
    year
    joke
    parts {
      name
      price
    }
  }
}
```
### 2. Consultar un vehículo por ID
Obtén la información completa de un vehículo específico usando su identificador único.
Consulta:
```
query {
  vehicle(id: "ID_DEL_VEHICULO") {
    id
    name
    manufacturer
    year
    joke
    parts {
      name
      price
    }
  }
}
```
### 3. Consultar todos los repuestos
Obtén todos los repuestos disponibles en la tienda, con información detallada.
Consulta:
```
query {
  parts {
    id
    name
    price
    vehicleId
  }
}
```
### 4. Consultar todos los vehículos de una marca
Filtra los vehículos clásicos según su fabricante.
Consulta:
```
query {
  vehiclesByManufacturer(manufacturer: "Ford") {
    id
    name
    year
    joke
  }
}
```
### 5. Consultar todos los repuestos de un vehículo
Lista los repuestos asociados a un modelo específico.
Consulta:
```
query {
  partsByVehicle(vehicleId: "ID_DEL_VEHICULO") {
    id
    name
    price
  }
}
```
### 6. Consultar vehículos por rango de años
Filtra los vehículos que fueron fabricados entre ciertos años.
Consulta:
```
query {
  vehiclesByYearRange(startYear: 1960, endYear: 1970) {
    id
    name
    manufacturer
    year
  }
}
```
### 7. Añadir un vehículo
Agrega un nuevo vehículo a la base de datos con su información básica.
Mutación:
```
mutation {
  addVehicle(name: "Camaro", manufacturer: "Chevrolet", year: 1969) {
    id
    name
    manufacturer
    year
  }
}
```
### 8. Añadir un repuesto
Crea un nuevo repuesto y asígnalo a un vehículo existente.
Mutación:
```
mutation {
  addPart(name: "Pastillas de freno", price: 800, vehicleId: "ID_DEL_VEHICULO") {
    id
    name
    price
    vehicleId
  }
}
```
### 9. Actualizar información de un vehículo
Modifica los datos de un vehículo ya registrado.
Mutación:
```
mutation {
  updateVehicle(id: "ID_DEL_VEHICULO", name: "Mustang Shelby", manufacturer: "Ford", year: 1968) {
    id
    name
    manufacturer
    year
  }
}
```
### 10. Eliminar un repuesto
Elimina un repuesto específico de la base de datos.
Mutación:
```
mutation {
  deletePart(id: "ID_DEL_REPUESTO") {
    id
    name
  }
}
```
