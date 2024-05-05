# Переустановка Synology DSM

### Описание

Легко переустановите ту же версию DSM без потери данных или настроек.

  - Если вам нужно переустановить ту же полную версию DSM, это намного проще, чем выполнить сброс Synology.
  - Его также можно использовать для отката с версии обновления до той же полной версии.

### Важныо

Вам необходимо скачать пат-файл полной версии. Если вы загрузите небольшой файл обновления, вы получите сообщение об ошибке: «
Обновление, которое вы применяете, несовместимо с этой версией DSM».

### Как определить, является ли файл .pat полной версией или небольшим обновлением

  - <img src="images/tick.svg" width="15" height="15"> Пат-файлы полной версии DSM:
    - Обычно называется DSM_model_build.pat , например **DSM_DS224+_64570.pat**
    - Имеют размер 270 МБ или больше и всегда намного больше, чем небольшие обновления.
  - <img src="images/cross.svg" width="15" height="15"> Небольшие файлы обновлений:
    - сегда называется Synology_arch_model.pat , например **synology_geminilake_224+.pat**
    - Размер от 1 МБ до 130 МБ и всегда намного меньше, чем полные обновления.
  - **Примечание:** Иногда полная версия называется как файл небольшого обновления .pat, когда Synology ошибается в названии файла.
    - См. https://archive.synology.com/download/Os/DSM/7.1.1-42962-1-NanoPacked

### Действия по переустановке DSM

1. Отключите автоматическое обновление DSM через «Панель управления > Обновление и восстановление > Настройки обновления > Уведомить меня... > ОК».
2. агрузите ту же полную версию сборки DSM с сайта загрузки Synology
    - https://archive.synology.com/download/Os/DSM/ 
4. Запустите этот скрипт через SSH или из <a href=how_to_run_from_scheduler.md/>планировщика задач </a>.
5. Перейдите в «Панель управления > Обновление и восстановление > Обновление DSM вручную».
6. Перейдите к файлу DSM .pat, который вы скачали на шаге 2, нажмите «Открыть», затем «ОК».
7. При необходимости отключите маршрутизатор от Интернета после начала установки DSM, чтобы предотвратить обновление DSM до последней версии обновления.
8. Нажмите Обновить.
9. Подождите, пока Synology NAS завершит обновление и перезагрузится.
10. *Если вы отключили маршрутизатор от Интернета на шаге 6, подключите его снова сейчас.*

## Скачать сценарий

1. Загрузите исходный код последней версии .zip https://github.com/007revad/Synology_DSM_reinstall/releases
2. Сохраните загруженный zip-файл в папку на Synology.
3. Разархивируйте zip-файл.

## Как запустить скрипт

Вы можете запустить скрипт либо через SSH, либо в планировщике задач.

#### Планирование сценария в планировщике задач Synology

- <a href=how_to_run_from_scheduler.md/>Как запустить сценарий в планировщике задач Synology</a> 
- <a href=how_to_see_output_in_scheduler.md>Как просмотреть выходные данные сценария, запущенного в Synology Task Scheduler</a>

#### Запуск скрипта через SSH

[Как включить SSH и войти в DSM через SSH](https://kb.synology.com/en-global/DSM/tutorial/How_to_login_to_DSM_with_root_permission_via_SSH_Telnet)

**Примечание:** Замените /volume1/scripts/ путем к расположению сценария.
```YAML
sudo -s /volume1/scripts/syno_dsm_reinstall.sh
```

## Screenshots

Here's the result after running the script.

<p align="center">The script has edited DSM's VERSION file to a lower build number</p>
<p align="center"><img src="/images/reinstall_dsm_step-1.png"></p>

<p align="center">Select your downloaded DSM .pat file</p>
<p align="center"><img src="/images/reinstall_dsm_step-2.png"></p>

<p align="center">No complaints from DSM</p>
<p align="center"><img src="/images/reinstall_dsm_step-3.png"></p>
