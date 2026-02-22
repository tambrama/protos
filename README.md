# 🌟 Protos (GRPC Contracts)

Централизованное хранилище gRPC контрактов (`.proto` файлы) для проекта Hardware Store.
Этот репозиторий/папка предназначен для использования в качестве зависимостей в микросервисах (Auth Service, Shop Service и др.).

---

## 📂 Структура

```text
protos/
├── Taskfile.yml       # Скрипт автоматической генерации
├── gen/go/            # Сгенерированный Go код (не коммитить, если используется как submodule, либо коммитить для простоты)
└── proto/             # Исходные .proto файлы
    └── sso/
        └── sso.proto  # Контракты авторизации
```

---

## 🛠 Требования
Для генерации кода необходимы:
- **[Protoc](https://github.com/protocolbuffers/protobuf/releases)** — компилятор протоколов.
- **[Task](https://taskfile.dev/installation/)** — менеджер задач (аналог Make).
- **Плагины Go** для генерации кода:
```
task gen
# или
task generate
```

---

## ⚡Генерация кода
Для генерации Go-структур и gRPC-клиентов/серверов выполните в корневой папке protos:
```
task gen
# или
task generate
```
Результат появится в папке gen/go/proto/sso/.

---

## 🔌 Подключение в другие сервисы
В вашем сервисе (например, auth-service):
- Добавьте репозиторий как подмодуль:
```
go get github.com/tambrama/protos
```
- Импортируйте сгенерированные пакеты в коде:

```
import pb "github.com/tambrama/protos/gen/go/proto/sso"
```
---