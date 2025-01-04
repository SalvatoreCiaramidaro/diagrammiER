# Diagramma er
```mermaid
erDiagram
    EMPLOYEE {
        string name
    }
    ADDRESS {
        string address
    }
    SKILL {
        string skill
    }
    DEPARTMENT {
        int id PK
        string department_name
        string department_location
    }
    PROJECT {
        string name
    }
    PROJECT_EMPLOYEE {
    }

    EMPLOYEE ||--o{ ADDRESS : has
    EMPLOYEE ||--o{ SKILL : has
    EMPLOYEE ||--o{ PROJECT_EMPLOYEE : works_on
    DEPARTMENT ||--o{ EMPLOYEE : includes
    PROJECT ||--o{ PROJECT_EMPLOYEE : involves
```	
# Progettazione Logica
```mermaid
erDiagram
    EMPLOYEE {
        int id PK
        string name
        int department_id FK
    }
    ADDRESS {
        int employee_id FK
        string address
    }
    SKILL {
        int employee_id FK
        string skill
    }
    DEPARTMENT {
        int id PK
        string department_name
        string department_location
    }
    PROJECT {
        int id PK
        string name
    }
    PROJECT_EMPLOYEE {
        int employee_id FK
        int project_id FK
    }

    EMPLOYEE ||--o{ ADDRESS : has
    EMPLOYEE ||--o{ SKILL : has
    EMPLOYEE ||--o{ PROJECT_EMPLOYEE : works_on
    DEPARTMENT ||--o{ EMPLOYEE : includes
    PROJECT ||--o{ PROJECT_EMPLOYEE : involves
```

# Normalizzazione

### 1NF
- **EMPLOYEE**: id `PK`, name, department_id, department_name
- **ADDRESS**: employee_id `FK`→ employee.id, address, `PK (employee_id,address)`
- **SKILL**: employee_id `FK`→ employee.id,skill,`PK (employee_id,skill_id)`
- **PROJECT**: id `PK`, name, employee_ids

- **PROJECT_EMPLOYEE**: employee_id `FK`→ employee.id,project_id `FK`→ project.id,`PK (employee_id,project_id)`

### 2NF
- **EMPLOYEE**: id `PK`, name, department_id, department_name
- **ADDRESS**: employee_id `FK`→ employee.id, address, `PK (employee_id,address)`
- **SKILL**: employee_id `FK`→ employee.id,skill,`PK (employee_id,skill_id)`
- **PROJECT**: id `PK`, name, employee_ids

- **PROJECT_EMPLOYEE**: employee_id `FK`→ employee.id,project_id `FK`→ project.id,`PK (employee_id,project_id)`

### 3NF
- **EMPLOYEE**: id `PK`, name,department_id
- **ADDRESS**: employee_id `FK`→ employee.id, address, `PK (employee_id,address)`
- **SKILL**: employee_id `FK`→ employee.id,skill,`PK (employee_id,skill_id)`
- **DEPARTMENT**: id `PK`,department_name,department_location
- **PROJECT**: id `PK`, name
- **PROJECT_EMPLOYEE**: employee_id `FK`→ employee.id,project_id `FK`→ project.id,`PK (employee_id,project_id)`