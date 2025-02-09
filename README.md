
# File Organizer

`File Organizer` — это утилита на языке Go для автоматического упорядочивания и перемещения файлов на основе их имени, размера и шаблона даты. Программа поддерживает настройку через файл конфигурации и ведёт логи для удобства отслеживания работы.

## Возможности

-   Чтение и создание конфигурационного файла.
-   Перемещение файлов из исходных папок в целевые директории на основе даты, извлечённой из имени файла.
-   Проверка минимального размера файла перед обработкой.
-   Ведение логов с ротацией старых лог-файлов.
-   Обработка ошибок без прерывания выполнения программы.

### Конфигурация

При первом запуске программы создаётся файл `config.json` с настройками по умолчанию:
```
{
  "source_dirs": [
    "e:/FilesNota/572149/1",
    "e:/FilesNota/572149/2"
  ],
  "target_dirs": [
    "//192.168.2.15/5otd/test/",
    "//192.168.2.15/5otd/test/"
  ],
  "min_file_size": 26463150,
  "date_template": "??ГГГГ?ММ?ДД"
}
```

Настройки можно отредактировать вручную перед повторным запуском программы.

### Логи

-   Логи хранятся в директории `logs/` с названием в формате `DD-MM-YYYY.log`.
-   Логи старше 5 дней автоматически удаляются.

## Пример работы

Если в исходной папке находится файл с именем `1_2024-12-15.txt`:

-   Шаблон `??ГГГГ?ММ?ДД` извлечёт дату `2024-12-15`.
-   Файл будет перемещён в целевую папку: `//192.168.2.15/5otd/test/15-12-2023/1/1_2024-12-15.txt`.

## Требования

-   Go 1.18 или выше