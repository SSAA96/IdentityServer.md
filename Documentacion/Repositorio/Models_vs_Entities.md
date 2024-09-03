# Entities vs Models en IdentityServer4: Una Guía Detallada

## Introducción

En IdentityServer4, la distinción entre Entities y Models es fundamental para entender cómo se manejan los datos y la lógica de negocio. Esta guía explora en detalle las características, usos y diferencias entre ambos conceptos.

## Entities

### Definición y Propósito

Entities en IdentityServer4 son clases que representan directamente las estructuras de datos en la base de datos. Están diseñadas para trabajar con Entity Framework Core y facilitar las operaciones de persistencia.

### Características Principales

1. **Namespace**: `IdentityServer4.EntityFramework.Entities`
2. **Estructura**: Clases POCO (Plain Old CLR Objects)
3. **Mapeo**: Directo a tablas de la base de datos
4. **Propiedades Adicionales**:
   - Identificadores únicos (e.g., `Id`)
   - Timestamps (e.g., `Created`, `Updated`)
   - Propiedades de seguimiento y auditoría

### Ejemplos de Entities

- `Client`
- `ApiResource`
- `IdentityResource`
- `PersistedGrant`

### Uso Típico

```csharp
public async Task<Client> GetClientAsync(int id)
{
    return await _context.Clients
        .Include(c => c.AllowedScopes)
        .FirstOrDefaultAsync(c => c.Id == id);
}