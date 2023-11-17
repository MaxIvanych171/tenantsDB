# tenantsDB
База данных для хранения информации  о жильцах в жилищной конторе.


## Таблицы базы данных

### Tenants
| Поле             | Тип            | Описание                       |
|------------------|----------------|-------------------------------|
| TenantID         | int (PK)       | Уникальный идентификатор      |
| Last_Name        | nvarchar(50)   | Фамилия жильца                |
| First_Name       | nvarchar(50)   | Имя жильца                    |
| Date_of_Birth    | date           | Дата рождения                 |
| Phone_Number     | decimal (10, 2)| Номер телефона                |
| Gender           | date           | Пол                           |


### Apartments 
| Поле             | Тип            | Описание                       |
|------------------|----------------|--------------------------------|
| Apartment_ID     | int (PK)       | Уникальный идентификатор       |
| Apartment_Number | int (FK)       | Номер квартиры                 |
| Address          | nvarchar(100)  | Адрес                          |
| Area             | decimal(10, 2) | Площадь                        |

### Residence 
| Поле             | Тип            | Описание                       |
|------------------|----------------|--------------------------------|
| Residence_ID     | int (PK)       | Уникальный идентификатор       |
| Tenant_ID        | nvarchar(100)  | id жильца                      |
| Apartment_ID     | int            | id квартиры                    |
| Period           | nvarchar(100)  | Срок проживания                |
| Check_in_Date    | date           | Дата заселения                 |
| Check_out_Date   | date           | Дата выселения                 |

```sql
INSERT INTO Tenants (Last_Name, First_Name, Date_of_Birth, Phone_Number, Gender)
VALUES 
('Пискунов', 'Вадим Иванович', '1997-04-08', '89517835930', 'Male'),
('Орешкина', 'Ирина Анатольевна', '1978-09-04', '89093279161', 'Female');

INSERT INTO Apartments(Apartment_Number, Address, Area)
VALUES 
(17, 'Улица Пушкинская 152, кв. 17', 80.50),
(4, 'Переулок Халтуринский 18, кв. 4', 125.30);

INSERT INTO Residence(Tenant_ID, Apartment_ID, Period, Check_in_Date, Check_out_Date)
VALUES 
(1, 1, 'timing', '2023-05-01', '2024-05-01'),
(2, 2, 'regularly', '2023-02-15', '2050-05-01');
```
