# Entities vs Models en IdentityServer4

## Entities

- **Namespace**: `IdentityServer4.EntityFramework.Entities`
- **Propósito**: Representación de tablas en la base de datos
- **Uso principal**: Persistencia de datos y ORM
- **Características**:
  - Diseñadas para trabajar con Entity Framework Core
  - Contienen propiedades adicionales para gestión de base de datos (ID, fechas de creación/modificación, etc.)
  - Mapeo directo a tablas de la base de datos

## Models

- **Namespace**: `IdentityServer4.Models`
- **Propósito**: Representación de dominio de conceptos de IdentityServer
- **Uso principal**: Lógica de negocio y configuración de IdentityServer
- **Características**:
  - No están vinculados a mecanismos de persistencia
  - Contienen solo propiedades relevantes para la lógica de IdentityServer
  - Utilizados en la configuración y lógica de emisión de tokens

## Diferencias Clave

| Aspecto       | Entities                                    | Models                                      |
|---------------|---------------------------------------------|---------------------------------------------|
| Propósito     | Persistencia y ORM                          | Lógica de negocio y configuración           |
| Propiedades   | Incluyen propiedades para base de datos     | Solo propiedades relevantes para la lógica  |
| Uso           | Operaciones CRUD con Entity Framework Core  | Configuración de IdentityServer             |
| Conversión    | `entity.ToModel()`                          | `model.ToEntity()`                          |

## Ejemplo de Uso

```csharp
// Uso de Entity
var apiResourceEntity = await _context.ApiResources.FindAsync(id);

// Conversión a Model
var apiResourceModel = apiResourceEntity.ToModel();

// Modificación del Model
apiResourceModel.DisplayName = "Nuevo Nombre";

// Conversión de vuelta a Entity
var updatedEntity = apiResourceModel.ToEntity();
_context.ApiResources.Update(updatedEntity);