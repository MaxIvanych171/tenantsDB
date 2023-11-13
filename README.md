# tenantsDB
База данных для хранения информации о книгах в электронной библиотеке.


## Таблицы базы данных

### Tenants
| Поле             | Тип            | Описание                       |
|------------------|----------------|-------------------------------|
| TenantID         | int (PK)       | Уникальный идентификатор      |
| Name             | nvarchar(50)   | ФИО жильца                    |
| Address          | nvarchar(100)  | Адрес                         |
| ContactNumber    | nvarchar(20)   | Телефон                       |
| RentAmount       | decimal (10, 2)| Плата за аренду               |
| LeaseStartDate   | date           | Дата Начала Аренды            |
| LeaseEndDate     | date           | Дата Окончания Аренды         |


### Payments
| Поле             | Тип            | Описание                       |
|------------------|----------------|--------------------------------|
| PaymentID        | int (PK)       | Уникальный идентификатор       |
| TenantID         | int (FK)       | ID жильца                      |
| PaymentDate      | date           | Дата платежа                   |
| AmountPaid       | decimal(10, 2) | Сумма платежа                  |

### Buildings
| Поле             | Тип            | Описание                       |
|------------------|----------------|--------------------------------|
| BuildingID       | int (PK)       | Уникальный идентификатор       |
| Address          | nvarchar(100)  | Адрес                          |
| NumFloors        | int            | Количество этажей              |

### Apartments
| Поле             | Тип            | Описание                       |
|------------------|----------------|--------------------------------|
| ApartmentID      | int (PK)       | Уникальный идентификатор       |
| ApartmentNumber  | nvarchar(10)   | Номер квартиры                 |
| BuildingID       | int (FK)       | Внешний ключ, ссылающийся на Buildings(BuildingID) |
| NumRooms         | date           | Количество комнат              |
| FloorNumber      | nvarchar(20)   | Номер этажа                    |

```sql
INSERT INTO Tenants (TenantID, Name, Address, ContactNumber, RentAmount, LeaseStartDate, LeaseEndDate)
VALUES 
(1, 'Иванов Иван Иванович', 'ул. Пушкина, д. 10, кв. 5', '123-456-7890', 1000.00, '2022-01-01', '2023-01-01');

INSERT INTO Payments (PaymentID, TenantID, PaymentDate, Amount)
VALUES 
(1, 1, '2022-04-01', 1000.00);

INSERT INTO Buildings (BuildingID, Address, NumFloors) VALUES
(1, 'ул. Ленина, д. 10', 5);

INSERT INTO Apartments (ApartmentID, ApartmentNumber, BuildingID, NumRooms, FloorNumber) VALUES
(1, '1A', 1, 3, 1);
```
