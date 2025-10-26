# Shadowchats.Handbook

Справочник по стандартам, процессам и онбордингу для проектов **Shadowchats**.  

⚠️ Обратите внимание: автор постоянно дорабатывает стандарты, поэтому старые репозитории могут частично им не соответствовать.

## 📄 License

Shadowchats is free software licensed under the **GNU Affero General Public License v3.0**.

This means you can:
- ✅ Use the software for any purpose
- ✅ Study and modify the source code
- ✅ Distribute the software
- ✅ Distribute your modifications

**Important requirements:**
- 🔒 Any modifications must also be licensed under AGPL v3
- 📤 If you run a modified version on a server, you must provide source code to users
- 📝 You must preserve copyright notices and license information

See [LICENSE](LICENSE) for full details.

### Why AGPL v3?
We chose AGPL v3 to ensure that Shadowchats remains free and open source forever, even when used as a network service. This protects users' rights to access, study, and modify the software that handles their private communications.

## 📄 [COPYRIGHT](COPYRIGHT).

## 📧 Contact

For questions about licensing or to request source code:
- Email: lenya.dorovskoy@mail.ru
- GitHub repository: https://github.com/0ne290/Shadowchats.Handbook
- Author's GitHub: https://github.com/0ne290

## Codestyle

- Переиспользовать файлы `.gitignore`, `LICENSE`, `COPYRIGHT` и `README.md` из данного репозитория (допускаются изменения, кроме `LICENSE` и `COPYRIGHT`).  
- Во всех файлах, где это возможно, добавлять шапку-комментарий или фиктивное поле с копирайтом (см. `COPYRIGHT`).  
- **Статические данные** инициализировать в классе; **экземплярные** (включая неизменяемые) — в конструкторе.  
- **Первичные конструкторы** не использовать.  
- **Классы данных** (`DTO`, `Message`, `Result`, `Config`, `Info` и т. д.) определять как `record` со свойствами `required { get; init; }` либо менее строгими.  
- **Классы, сохраняемые в БД** (`ValueObject`, `Entity`, `AggregateRoot` и т. д.) не должны содержать сохраняемых зависимостей.  
  - Если классу нужна зависимость, внедрять её в метод, вызываемый из слоя **Application**.  

## Архитектурные принципы

- Использовать **DDD**, **CQRS** и **Event Driven** — обязательные подходы.  
- За основу брать решение `Shadowchats.Template.sln` из данного репозитория.  
- **Unit Testing** обязателен для слоёв **Domain** и **Application** (особенно `UseCaseHandler`-ов).  
- Желательно тестировать важный инфраструктурный код, в чьей корректности есть сомнения (например, самописное хеширование паролей).

## Инфраструктура

### Сеть

#### Порты:

| № | Технология    | Протокол                      | Порт      |
| - | ------------- | ----------------------------- | --------- |
| 1 | **REST API**  | HTTP/1.1                      | **8080**  |
| 2 | **gRPC**      | HTTP/2 (H2C)                  | **50051** |
| 3 | **gRPC-Web**  | HTTP/1.1 (через proxy/bridge) | **8081**  |
| 4 | **WebSocket** | HTTP/1.1 (ws://)              | **6001**  |
| 5 | **GraphQL**   | HTTP/1.1                      | **7000**  |
