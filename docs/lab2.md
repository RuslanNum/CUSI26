# LAB 2 – Návrh tříd a Workflow (AutoPoint)

## 1. Základní třídy a jejich funkcionalita (UML Class Diagram)

Systém obsahuje 5 hlavních tříd a celkem 11 metod:

```mermaid
classDiagram
    class User {
        +int id
        +string full_name
        +string email
        +string phone
        +string role
        +register() bool
        +login() string
    }

    class Car {
        +int id
        +string license_plate
        +string brand
        +string model
        +int year
        +add_car() bool
        +get_service_history() list
    }

    class ServiceType {
        +int id
        +string title
        +float base_price
        +int duration_minutes
        +get_available_slots(date) list
    }

    class ServiceOrder {
        +int id
        +datetime scheduled_date
        +string status
        +float total_price
        +create_order() bool
        +change_status(new_status) void
        +cancel_order() bool
        +calculate_price() float
    }

    class Mechanic {
        +int id
        +string name
        +string specialization
        +assign_order(order_id) void
        +complete_repair(order_id) void
    }

    User "1" --> "0..*" Car : vlastní
    Car "1" --> "0..*" ServiceOrder : má objednávky
    ServiceType "1" --> "0..*" ServiceOrder : definuje úkon
    Mechanic "1" --> "0..*" ServiceOrder : vyřizuje
```

### Popis hlavních funkcionalit:
1. **`register()` / `login()` (`User`)** – registrace zákazníka a přihlášení do systému.
2. **`add_car()` (`Car`)** – přidání vozidla podle SPZ do profilu uživatele.
3. **`get_available_slots()` (`ServiceType`)** – výpočet volných termínů podle délky úkonu.
4. **`create_order()` / `calculate_price()` (`ServiceOrder`)** – vytvoření objednávky a automatický výpočet ceny.
5. **`assign_order()` / `complete_repair()` (`Mechanic`)** – převzetí zakázky mechanikem a změna stavu opravy (`Nová` -> `V opravě` -> `Hotovo`).

---

## 2. Workflow systému (UML Sequence Diagram)

```mermaid
sequenceDiagram
    actor Zákazník as User
    participant Systém as ServiceOrder
    participant Služba as ServiceType
    actor Mechanik as Mechanic

    Zákazník->>Systém: login()
    Zákazník->>Služba: get_available_slots(datum)
    Služba-->>Zákazník: seznam volných termínů
    Zákazník->>Systém: create_order(auto, služba, termín)
    Systém->>Systém: calculate_price()
    Systém-->>Zákazník: potvrzení objednávky (stav: Nová)

    Mechanik->>Systém: assign_order(order_id)
    Systém->>Systém: change_status("V opravě")
    Mechanik->>Systém: complete_repair(order_id)
    Systém->>Systém: change_status("Hotovo")
    Systém-->>Zákazník: notifikace o dokončení opravy
```
