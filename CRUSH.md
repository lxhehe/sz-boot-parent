# Sz-Boot-Parent Development Guide

## Build Commands
- **Full Build**: `mvn clean package`
- **Compile Only**: `mvn clean compile`
- **Test**: `mvn test`
- **Single Test**: `mvn test -Dtest=ClassName#testMethod`
- **Format Code**: `mvn spotless:apply`
- **Check Format**: `mvn spotless:check`

## Test Commands
- **Run all tests**: `mvn clean test`
- **Run specific test class**: `mvn test -Dtest=StringUtilsTest`
- **Run specific test method**: `mvn test -Dtest=StringUtilsTest#toCamelCase`
- **Include all modules**: `mvn test -pl sz-common/sz-common-core`

## Code Style Guidelines

### Naming Conventions
- **Packages**: `com.sz.admin.{module}.{layer}` (e.g., `com.sz.admin.system.controller`)
- **Controllers**: `{EntityName}Controller` (e.g., `SysMenuController`)
- **Services**: `{EntityName}Service` (interface) + `{EntityName}ServiceImpl` (implementation)
- **Mappers**: `{EntityName}Mapper` (interface) + `{EntityName}Mapper.xml` (MyBatis XML)
- **POJOs**: `{EntityName}.java` (e.g., `SysMenu.java`)
- **DTOs**: `{EntityName}{Operation}DTO` (e.g., `SysMenuCreateDTO`, `SysMenuListDTO`)
- **VOs**: `{EntityName}VO` (e.g., `SysMenuVO`, `MenuPermissionVO`)

### Code Formatting
- **Formatter**: Eclipse formatter (`sz-build/baeldung-style.xml`)
- **Indentation**: 4 spaces
- **Line Length**: 160 characters max
- **Tabs vs Spaces**: Spaces only
- **Unused Imports**: Auto-removed by formatter

### Architecture Principles
- **Layered Architecture**: Controller → Service → Mapper
- **Dependency Injection**: Use `@RequiredArgsConstructor` with `final` fields
- **Lombok Usage**: Heavy use of `@Data`, `@RequiredArgsConstructor`, `@Slf4j`
- **Error Handling**: Custom exception types extending base framework
- **API Documentation**: Swagger/OpenAPI annotations
- **Transaction Management**: `@Transactional` on service methods when needed

### Import Organization
1. Java/Kotlin standard imports
2. Spring framework imports
3. Third-party libraries (Swagger, Lombok, etc.)
4. Project internal imports
5. Static imports last

### Database Conventions
- **Migration Tool**: Flyway
- **ORM**: Mybatis Flex
- **Table Naming**: `sys_{entity}` (e.g., `sys_menu`, `sys_user`)
- **Primary Keys**: String UUID format
- **Soft Deletes**: `is_deleted` field pattern

### Security
- **Auth Framework**: Sa-Token
- **Permissions**: Check `@SaCheckPermission` annotations
- **Profile-based Config**: Multiple environments (local, dev, preview, prod)

### Key Dependencies
- Spring Boot 3.x
- Java 21
- Mybatis Flex (ORM)
- Sa-Token (Authentication)
- Flyway (DB Migration)
- Knife4j/Swagger (API Docs)
- Lombok (Code Generation)

## Common Development Workflows
1. **New Feature**: Create branch → Code → Format with Spotless → Test → PR
2. **Bug Fix**: Identify → Reproduce → Fix → Test → Document
3. **DB Changes**: Add Flyway migration → Update Model → Update Service</content>
<file_path>CRUSH.md