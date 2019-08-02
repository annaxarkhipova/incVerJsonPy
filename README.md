# ТЗ

Очень полезное дело и практика для лухури анны

## Задача

Создать скрипт для автоматизации увеличения версии приложения

## Исходные данные

**3 файла формата json** (package.json, appCsp.json, appSahalin.json)

**5 изменяемых полей:**

| package.json | appCsp.json и appSahalin.json |
| ------------ | ----------------------------- |
| version      | expo.version                  |
| -            | expo.ios.buildNumber          |
| -            | expo.android.versionCode      |

**7 процессов:**

- повышение версии в package
- повышение версии в appCsp
- повышение версии в appSahalin
- 4 команды, которые будут заменены после выполнения задания (задание 2):
  - `print("build sahalin")`
  - `print("build csp")`
  - `print("bundle sahalin")`
  - `print("bundle csp")`

## Требования

Скрипт должен иметь имя update и принимать на вход ключ `--build` или `--bundle` и необязательный ключ `--circuit` (далее ключ build, ключ bundle и необязательный ключ circuit).

При запуске скрипт просит выбрать одну из опций (patch, minor, major). В консоли это действие должно быть похоже на:

    Повысить версию:
    > patch
      minor
      major

Если присутствует ключ circuit, то дополнительно спрашивается:

    Контур:
    > csp
      sahalin

Выбор происходит с помощью стрелки вверх или вниз (по-умолчанию выбор на первом элементе) и после нажатия на enter запускается скрипт. Т.e процесс запускается с ключом и опцией (опциями).

#### Работа скрипта:

### Задание 1 (версии)

Сначала происходит увеличение версии (увеличение конкретного поля на один):

**package**

|            | version |
| ---------- | ------- |
| до запуска | 2.1.0   |
| patch      | 2.1.1   |
| minor      | 2.2.0   |
| major      | 3.1.0   |

**appCsp/appSahalin**

Для appCsp/appSahalin поля одинаковые, однако при указании ключа circuit изменения работают соответственно для одного из файлов

|            | expo.version (если указан ключ build или bundle) | expo.ios.buildNumber (если указан ключ build) | expo.android.versionCode (если указан ключ build) |
| ---------- | ------------------------------------------------ | --------------------------------------------- | ------------------------------------------------- |
| до запуска | 2.1.0                                            | 17                                            | "17"                                              |
| patch      | 2.1.1                                            | 18                                            | "18"                                              |
| minor      | 2.2.0                                            | 18                                            | "18"                                              |
| major      | 3.1.0                                            | 18                                            | "18"                                              |

если до запуска в файлах версии **отличаются** и при запуске **не** указан ключ circuit, то берется последняя версия(2.1.0 и 3.0.0 -> 3.0.0 | 2.3.0 и 2.2.6 -> 2.3.0 | "18" и "20" -> "20" | 21 и 23 -> 23) и далее манипуляции и запись в файл происходит уже исходя от нее.

## Проверка

**Задание 1** - можно выводить после выполнения скрипта все значения, например:

      Версии:
          package:
                version: <версия>
          appCsp:
                version: <версия>
                buildNumber: <версия>
                versionCode: <версия>
          appSahalin:
                version: <версия>
                buildNumber: <версия>
                versionCode: <версия>

## Дополнительно

Все задания можно выполнять любыми удобными средствами.
Желательно оптимально использовать время и ресурсы, чтобы за минимальный промежуток времени выполнять задание максимально продуктивно
