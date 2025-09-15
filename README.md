# Shadowchats.Handbook

Стандарты, процессы, онбординг.

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
- GitHub repository: https://github.com/0ne290/Shadowchats.Authentication
- Author's GitHub: https://github.com/0ne290

## Codestyle:
- Переиспользуются файлы `.gitignore`, `LICENSE`, `COPYRIGHT` и `README.md` в данном репозитории с изменениями (изменять `LICENSE` и `COPYRIGHT` нельзя).
- Во всех файлах, где это возможно, вставляется шапка-комментарий или фиктивное поле с копирайтом; подробнее смотреть в файле `COPYRIGHT`.
- **DDD** + **CQRS** + **Event Driven** + **Unit Testing**. Первое, второе и третье - обязательный мастхев, за основу берется решение `Shadowchats.Template.sln` в данном репозитории. Четвертое - обязательно тестировать как минимум слои `Domain` и `Application` (особенно UseCaseHandler's); желательно тестировать важный инфраструктурный код, в чьей работоспособности есть или могут быть сомнения (например, самописное хеширование паролей).
- **Статические данные** инициализируются в классе; **экземплярные** (включая неизменяемые) — в конструкторе.  
- **Первичные конструкторы** не использовать.  
- **Классы данных** (`DTO`, `Message`, `Result`, `Config`, `Info` и т. д.) определяются как `record` со свойствами `required { get; init; }` либо менее строгими.  
- **Классы, сохраняемые в БД** (`ValueObject`, `Entity`, `AggregateRoot` и т. д.) не должны содержать сохраняемых зависимостей; зависимости внедряются непосредственно в методы, вызываемые из слоя `Application`.
