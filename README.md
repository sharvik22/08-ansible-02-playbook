# Домашнее задание к занятию 2 «Работа с Playbook» Шарапат Виктор

## Подготовка к выполнению

1. * Необязательно. Изучите, что такое [ClickHouse](https://www.youtube.com/watch?v=fjTNS2zkeBs) и [Vector](https://www.youtube.com/watch?v=CgEhyffisLY).
2. Создайте свой публичный репозиторий на GitHub с произвольным именем или используйте старый.
3. Скачайте [Playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.
4. Подготовьте хосты в соответствии с группами из предподготовленного playbook.

## Основная часть

1. Подготовьте свой inventory-файл `prod.yml`.
2. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает [vector](https://vector.dev). Конфигурация vector должна деплоиться через template файл jinja2. От вас не требуется использовать все возможности шаблонизатора, просто вставьте стандартный конфиг в template файл. Информация по шаблонам по [ссылке](https://www.dmosk.ru/instruktions.php?object=ansible-nginx-install). не забудьте сделать handler на перезапуск vector в случае изменения конфигурации!
3. При создании tasks рекомендую использовать модули: `get_url`, `template`, `unarchive`, `file`.
4. Tasks должны: скачать дистрибутив нужной версии, выполнить распаковку в выбранную директорию, установить vector.
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.
6. Попробуйте запустить playbook на этом окружении с флагом `--check`.
7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены.
8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен.
9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги. Пример качественной документации ansible playbook по [ссылке](https://github.com/opensearch-project/ansible-playbook). Так же приложите скриншоты выполнения заданий №5-8
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-02-playbook` на фиксирующий коммит, в ответ предоставьте ссылку на него.

---

## Решение

Данный плейбук скачивает и устанавливает приложения ClickHouse и Vector.

Структура playbook:

* group_vars
 

- описания переменных (тут я завел переменные с указанием версий для каждого приложения).

---

* inventory

- описание групп хостовый машин, на которых будет выполняться плейбук (тут я использую для подключения ключ и пароль (зашифровал в файле vault.yml) , для повышения привелегий для установки пакетов).

*  templates

- шаблоны и конфиги для приложений (тут храняться шаблон службы и конфиг для приложения Vector).

 .gitignore

- файл исключения 

 site.yml

 - непосредственно сам плейбук

 vault.yml

- файл, который хранит зафифрованый пароль для sudo.


5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.

![5](https://github.com/user-attachments/assets/e559e268-5a19-478e-8439-27952c72ac53)

6. Попробуйте запустить playbook на этом окружении с флагом `--check`.

![6](https://github.com/user-attachments/assets/559c5147-ab1e-4460-a0bf-a3e1186514f6)

7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены.

![7](https://github.com/user-attachments/assets/741fd0b2-c58d-4a04-8e9a-a096ed69c6b9)

8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен.

![8](https://github.com/user-attachments/assets/523e4a3b-8c6b-4feb-b91d-8ed25b8eb8e6)

![Screenshot_1](https://github.com/user-attachments/assets/ca8f066b-1bfe-4fa5-b671-7b4a09e58d35)



### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
