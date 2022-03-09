# 3. Vault seeding spec

Date: 2022-01-11

## Status

Accepted

## Context

Сидирование секретов для Hashicorp Vault является одной из фич проекта `seeder`.

Vault API в некоторой степени не скрывает деталей реализации самого Vault,
например:

- В адресе эндпоинта создания секрета фигурирует фрагмент `/data/`;
- В теле запроса создания секрета используется поле `data` для
  передачи `payload` секрета.

В случае с `payload` секрета решение понятно — помимо данных в секрете
содержится метаинформация, которая также может быть создана или модифицирована
через Vault API.

Для простоты реализации и сохранения единообразия предлагается использовать
формат Vault API для сидирования секретов.

## Decision

Использовать формат Vault API при формировании адреса (пути) секрета и
его `payload`.

## Consequences

Несмотря на неочевидность использования фрагмента `/data/` при формировании пути
секрета и поля `data` в `payload` секрета, такой подход сохранит гибкость при
определении секретов и единообразие при работе с Vault API.