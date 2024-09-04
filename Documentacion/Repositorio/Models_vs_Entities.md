# Entities vs Models en IdentityServer4

## Introducción

En IdentityServer4, las Entities y los Models son conceptos fundamentales pero distintos. Entender sus diferencias es crucial para trabajar eficientemente con este framework.

## Entities

### Descripción General
- Namespace: `IdentityServer4.EntityFramework.Entities`
- Propósito: Representación directa de las tablas en la base de datos
- Uso: Operaciones de persistencia y mapeo con Entity Framework Core

### Propiedades Comunes en Entities

#### ApiResource Entity
- `Id` (int): Identificador único
- `Enabled` (bool): Indica si el recurso está habilitado
- `Name` (string): Nombre del recurso API
- `DisplayName` (string): Nombre para mostrar
- `Description` (string): Descripción del recurso
- `AllowedAccessTokenSigningAlgorithms` (string): Algoritmos de firma permitidos
- `ShowInDiscoveryDocument` (bool): Si se muestra en el documento de descubrimiento
- `Created` (DateTime): Fecha de creación
- `Updated` (DateTime?): Fecha de última actualización
- `LastAccessed` (DateTime?): Fecha del último acceso
- `NonEditable` (bool): Si es editable o no
- `UserClaims` (List<ApiResourceClaim>): Claims asociados
- `Properties` (List<ApiResourceProperty>): Propiedades adicionales
- `Scopes` (List<ApiResourceScope>): Scopes asociados
- `Secrets` (List<ApiResourceSecret>): Secretos del recurso

#### ApiScope Entity
- `Id` (int): Identificador único
- `Enabled` (bool): Indica si el scope está habilitado
- `Name` (string): Nombre del scope
- `DisplayName` (string): Nombre para mostrar
- `Description` (string): Descripción del scope
- `Required` (bool): Si es requerido
- `Emphasize` (bool): Si se debe enfatizar
- `ShowInDiscoveryDocument` (bool): Si se muestra en el documento de descubrimiento
- `UserClaims` (List<ApiScopeClaim>): Claims asociados
- `Properties` (List<ApiScopeProperty>): Propiedades adicionales

## Models

### Descripción General
- Namespace: `IdentityServer4.Models`
- Propósito: Representación de conceptos de IdentityServer en la lógica de negocio
- Uso: Configuración de IdentityServer y lógica de emisión de tokens

### Propiedades Comunes en Models

#### ApiResource Model
- `Enabled` (bool): Indica si el recurso está habilitado
- `Name` (string): Nombre del recurso API
- `DisplayName` (string): Nombre para mostrar
- `Description` (string): Descripción del recurso
- `AllowedAccessTokenSigningAlgorithms` (ICollection<string>): Algoritmos de firma permitidos
- `ShowInDiscoveryDocument` (bool): Si se muestra en el documento de descubrimiento
- `UserClaims` (ICollection<string>): Claims asociados
- `Properties` (IDictionary<string, string>): Propiedades adicionales
- `ApiSecrets` (ICollection<Secret>): Secretos del recurso
- `Scopes` (ICollection<string>): Scopes asociados

#### ApiScope Model
- `Name` (string): Nombre del scope
- `DisplayName` (string): Nombre para mostrar
- `Description` (string): Descripción del scope
- `Required` (bool): Si es requerido
- `Emphasize` (bool): Si se debe enfatizar
- `ShowInDiscoveryDocument` (bool): Si se muestra en el documento de descubrimiento
- `UserClaims` (ICollection<string>): Claims asociados

## Principales Diferencias

1. **Propósito**
   - Entities: Diseñadas para interactuar directamente con la base de datos.
   - Models: Utilizadas en la lógica de negocio y configuración de IdentityServer.

2. **Propiedades de Base de Datos**
   - Entities: Incluyen propiedades como `Id`, `Created`, `Updated` para gestión de base de datos.
   - Models: No contienen estas propiedades específicas de base de datos.

3. **Relaciones**
   - Entities: Usan listas de entidades relacionadas (e.g., `List<ApiResourceClaim>`).
   - Models: Usan colecciones simples (e.g., `ICollection<string>` para claims).

4. **Complejidad**
   - Entities: Más complejas, reflejando la estructura completa de la base de datos.
   - Models: Más simples, enfocadas en la lógica de negocio.

5. **Uso**
   - Entities: Usadas en operaciones CRUD y consultas de base de datos.
   - Models: Usadas en la configuración de IdentityServer y procesamiento de tokens.

## Conclusión

Entender estas diferencias es crucial para trabajar eficientemente con IdentityServer4. Las Entities se utilizan para la persistencia de datos, mientras que los Models se emplean en la lógica de negocio y la configuración del servidor de identidad.