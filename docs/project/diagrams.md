# Диаграммы

## Диаграмма последовательности

```mermaid
sequenceDiagram
    actor User as Получатель письма
    participant System as Система
    participant Model as ML-модель

    User->>System: Получить входящее письмо
    System->>Model: Передать данные письма
    Model-->>System: Вернуть класс ("спам" / "не спам")
    System-->>User: Показать результат проверки
```

## Диаграмма классов

```mermaid
classDiagram

    class User {
        +int id
        +string email
    }

    class Email {
        +int id
        +string sender
        +string subject
        +string text
        +datetime receivedAt
        +bool isSpam
    }

    class ClassificationResult {
        +string label
        +float confidence
        +datetime checkedAt
    }

    class MLModel {
        +string version
        +predict(text) ClassificationResult
    }

    User "1" --> "*" Email
    Email "1" --> "1" ClassificationResult
    MLModel "1" --> "*" ClassificationResult
```