# Magisk на GPGPC Developer Emulator

Установка Magisk на GPGPCDE (Google Play Games on PC Developer Emulator).

> Этот репозиторий создан на основе комментария в [XDA Forums t-4486817#post-89464596](https://xdaforums.com/t/4486817/post-89464596).

ㅤ

## Содержание

- [Минимальные системные требования](#минимальные-системные-требования)
- [Установка](#установка)
  - [1. Требования](#1-требования)
  - [2. Google Play Games on PC Developer Emulator (GPGPCDE)](#2-google-play-games-on-pc-developer-emulator-gpgpcde)
  - [3. Aow Tools](#3-aow-tools)
  - [4. Magisk](#4-magisk)
  - [5. Создание папки](#5-создание-папки)
  - [6. Копирование/резервное копирование `aggregate.img` и `bios.rom`](#6-копированиерезервное-копирование-aggregateimg--biosrom)
  - [7. Патч `1.boot_a.img`](#7-патч-1boot_aimg)
  - [8. Редактирование `magisk_patched-xxxxx_xxxxx.img`](#8-редактирование-magisk_patched-xxxxx_xxxxximg)
  - [9. Добавление пропатченного образа загрузки в `aggregate.img`](#9-добавление-пропатченного-образа-загрузки-в-aggregateimg)
  - [10. Редактирование `bios.rom`](#10-редактирование-biosrom)
  - [11. Замена на пропатченные файлы](#11-замена-на-пропатченные-файлы)
  - [12. Удаление ограничений на установку](#12-удаление-ограничений-на-установку)
- [Установка приложений](#установка-приложений)
  - [AdAway](#adaway)
  - [Aurora Store](#aurora-store)
  - [Другие приложения](#другие-приложения)
- [Прочее](#прочее)
  - [Навигация в GPGPCDE](#gpgpcde-навигация)
  - [Скриншоты](#скриншоты)
  - [Метод 2](#метод-2)
- [Благодарности](#благодарности)

ㅤ

## Минимальные системные требования

- **ОС**: Windows 10 (v2004)
- **Хранилище**: SSD с 10 ГБ свободного места
- **Графика**: IntelⓇ UHD Graphics 630 GPU или аналогичная
- **Процессор**: 4 физических ядра (некоторые игры требуют процессор Intel)
- **Память**: 8 ГБ ОЗУ
- Учетная запись администратора Windows
- Аппаратная виртуализация должна быть включена:
  - [Включение виртуализации](https://support.microsoft.com/en-us/windows/enable-virtualization-on-windows-c5578302-6e43-4b4b-a449-8ced115f58e1)
  - [Включение Hyper-V](https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)

**Примечание**: подробнее о требованиях можно [прочитать здесь](https://support.google.com/googleplay?p=eligibility_requirements).

ㅤ

## Установка

### 1. Требования

- [Google Play Games on PC Developer Emulator](https://developer.android.com/games/playgames/emulator) (GPGPCDE)
- [Aow Tools](https://apps.microsoft.com/detail/9nxm6552h2ql?hl=en-US) (бесплатная пробная версия)
- [HxD Portable](https://mh-nexus.de/en/downloads.php?product=HxD20)
- [Magisk](https://github.com/topjohnwu/Magisk?tab=readme-ov-file)
- [7-Zip](https://7-zip.org/)

ㅤ

### 2. Google Play Games on PC Developer Emulator (GPGPCDE)

1. Скачайте и установите **GPGPCDE** (стабильная версия).
2. Откройте **GPGPCDE** и войдите в свой аккаунт Google.
3. Разрешите `USB debugging`, отметьте `Always allow from this computer`, затем нажмите `Allow`.

ㅤ  
**Примечание**:

- При **выходе из системы** локальные **файлы устройства**, включая **установленные приложения/игры**, будут <ins>**удалены**</ins>.
- Если страница **GPGPCDE** отображается пустой (режим сна), используйте:
  - Клавиши **PgDn** <kbd>↓</kbd>
  - **Клик и свайп вверх**
  - **Прокрутку мышью** (режим ПК).
- [Навигация (горячие клавиши)](#gpgpcde-навигация)

ㅤ

### 3. Aow Tools

1. Установите **Aow Tools**, нажав кнопку **Free Trial**.  
   Не беспокойтесь, эта версия поддерживает <ins>неограниченное использование</ins>.  
   Вы можете **поддержать** разработчика, купив приложение.
2. Откройте **Aow Tools** и нажмите `⚙ Settings` в левой панели навигации.
   - Раздел `Adb Config` > `Adb.exe Current Path` > `Select Adb.exe`
   - Вставьте следующий путь в адресную строку Проводника:  
     `C:\Program Files\Google\Play Games Developer Emulator\current\emulator`
   - Добавьте файл `adb.exe`.
3. Откройте **Aow Tools** и нажмите `? Help` в левой панели навигации.
4. В разделе `Remove local loopback restrictions` используйте первый метод с **CMD** (от имени администратора).
5. Нажмите `Device`. Устройство **GPGPCDE** (`vsoc_kiwi_x86_64`) будет отображаться со статусом `Online`.

ㅤ

### 4. Magisk

1. Скачайте приложение **Magisk**.
2. Откройте **Aow Tools** > `Install` > можно перетащить APK-файлы для установки приложений.
3. Установите **Magisk**.
4. Откройте **GPGPCDE**, **Magisk** появится в меню приложений.

ㅤ

### 5. Создание папки

1. Откройте **Проводник**.
2. Перейдите на **Рабочий стол** или в `%UserProfile%\Desktop`.
3. Создайте папку "**GPGPCDE**".

ㅤ

### 6. Копирование/резервное копирование `aggregate.img` и `bios.rom`

1. Перейдите в `C:\Program Files\Google\Play Games Developer Emulator\current\emulator\avd`
2. Скопируйте/создайте резервную копию файлов `aggregate.img` и `bios.rom` в папку `%UserProfile%\Desktop\GPGPCDE`.
3. Откройте файл `aggregate.img` в **7-Zip** и извлеките файл `1.boot_a.img`.

ㅤ

### 7. Патч `1.boot_a.img`

1. Откройте **Aow Tools** > `File` > `Download` > нажмите `↑ Upload` (нижняя панель).
2. Загрузите файл `1.boot_a.img`.
3. Откройте **GPGPCDE** > запустите **Magisk**.
4. Нажмите `Install` в карточке **Magisk**.
5. Выберите `Select and Patch a File`, дважды кликните на `1.boot_a.img`.
6. Нажмите `LET'S GO` и дождитесь сообщения `All done!`.
7. Вернитесь в **Aow Tools** > `File` > `Download`.
8. Выберите `magisk_patched-xxxxx_xxxxx.img` и нажмите `↓ Download`.
9. Сохраните в `%UserProfile%\Desktop\GPGPCDE`.

ㅤ

### 8. Редактирование `magisk_patched-xxxxx_xxxxx.img`

1. Скачайте и распакуйте **HxD Portable**.
2. Откройте `magisk_patched-xxxxx_xxxxx.img` в **HxD**.
3. Откройте замену (<kbd>Ctrl</kbd>+<kbd>r</kbd>) > `Text-string`:

   - **Найти**: `,avb=vbmeta`
   - **Заменить**: "&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;" (без кавычек) `11`
   - **Направление**: `All`
   - Выберите `Prompt on replace` (опционально)
   - Нажмите `OK`

     ![GPGPCDE-edit-magisk-patched-replace](./images/GPGPCDE-edit-magisk-patched-replace.png)

     ![GPGPCDE-edit-magisk-patched-replace](./images/GPGPCDE-edit-magisk-patched-before-after.png)

4. Выделите **все** байты файла (<kbd>Ctrl</kbd>+<kbd>a</kbd>), затем ПКМ > `Select block...` (<kbd>Ctrl</kbd>+<kbd>e</kbd>).
5. Скопируйте значение в разделе `Length`.

   ![GPGPCDE-edit-magisk-patched-select](./images/GPGPCDE-edit-magisk-patched-select.png)

ㅤ

### 9. Добавление пропатченного образа загрузки в `aggregate.img`

1. Откройте `aggregate.img` в **HxD**.
2. Откройте поиск (<kbd>Ctrl</kbd>+<kbd>f</kbd>) > `Text-string`:

   - **Найти**: `ANDROID!`
   - **Направление**: `All`
   - Нажмите `Search all`

     ![GPGPCDE-add-patched-boot-image-search](./images/GPGPCDE-add-patched-boot-image-search.png)

3. В `Result` > `Search ({N} hits)` > дважды кликните последнее совпадение.

   ![GPGPCDE-add-patched-boot-image-search-result](./images/GPGPCDE-add-patched-boot-image-search-result.png)

4. ПКМ на выделенном тексте > `Select block...`:

   - Введите **длину** файла `magisk_patched-xxxxx_xxxxx.img` ([#8-5](#8-редактирование-magisk_patched-xxxxx_xxxxximg)).
   - Нажмите `OK`

     ![GPGPCDE-add-patched-boot-image-select](./images/GPGPCDE-add-patched-boot-image-select.png)

5. Вернитесь в `magisk_patched-xxxxx_xxxxx.img`, скопируйте все байты ([#8-4](#8-редактирование-magisk_patched-xxxxx_xxxxximg)).
6. Замените выделенный текст в `aggregate.img` скопированными байтами.

   ![GPGPCDE-add-patched-boot-image-before-after](./images/GPGPCDE-add-patched-boot-image-before-after.png)

7. **Сохраните**.

ㅤ

### 10. Редактирование `bios.rom`

1. Откройте `bios.rom` в **HxD**.
2. Откройте замену (<kbd>Ctrl</kbd>+<kbd>r</kbd>) > `Text-string`:

   - **Найти**: `verified_`
   - **Заменить**: "&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;" (без кавычек) `9`
   - **Направление**: `All`
   - Нажмите `OK`

     ![GPGPCDE-edit-bios.rom-replac](./images/GPGPCDE-edit-bios.rom-replace.png)

     ![GPGPCDE-edit-bios.rom-before-after](./images/GPGPCDE-edit-bios.rom-before-after.png)

3. **Сохраните**.

ㅤ

### 11. Замена на пропатченные файлы

1. В системном трее нажмите ПКМ на иконке **GPGPCDE** > `Exit`.
2. Скопируйте пропатченные файлы (`aggregate.img` и `bios.rom`) в `C:\Program Files\Google\Play Games Developer Emulator\current\emulator\avd`.
3. Перезапустите **GPGPCDE**.
4. Откройте **Magisk** > появится запрос `Requires Additional Setup` > `OK`.
5. Дождитесь перезагрузки **GPGPCDE**.

ㅤ

### 12. Удаление ограничений на установку

1. Скачайте модуль Magisk [`HPESuperpower.zip`](https://github.com/sekedus/MagiskOnGPGPCDE/raw/refs/heads/main/module/HPESuperpower.zip) от [ChsBuffer](https://github.com/chsbuffer).
2. Откройте **Aow Tools** > `File` > `Download` > `↑ Upload`.
3. Загрузите `HPESuperpower.zip`.
4. Откройте **GPGPCDE** > **Magisk**.
5. Нажмите `Modules` в правом нижнем углу.
6. Нажмите `Install from storage`.
7. Перейдите в папку `Downloads`, выберите `HPESuperpower.zip`.
8. Подтвердите установку (`OK`).
9. Дождитесь `Done`.
10. Нажмите `Reboot`, дождитесь перезагрузки.

ㅤ

## Установка приложений

### AdAway

1. Откройте **Magisk** > `⚙` > `Magisk` > включите `Systemless hosts`.
2. Закройте **GPGPCDE** ([#11-1](#11-замена-на-пропатченные-файлы)).
3. Перезапустите **GPGPCDE**.
4. Установите [AdAway](https://github.com/AdAway/AdAway?tab=readme-ov-file) через **Aow Tools**.
5. Откройте **AdAway** > выберите `Root based ad blocking` > предоставьте **root-доступ** > `NEXT`.
6. Синхронизируйте **AdAway** > `NEXT` > `FINISH`.

ㅤ

### Aurora Store

1. Установите [Aurora Store](https://gitlab.com/AuroraOSS/AuroraStore) через **Aow Tools**.
2. Настройте **Aurora Store**:
   - Разрешите:
     - `Installer Permission`
     - `External Storage Manager`
     - `Background Downloads`
     - `Notifications`
     - `App Links`
   - Нажмите `Finish`.
3. Нажмите **3 точки** в правом верхнем углу:
   - `Spoof manager` > выберите устройство (например, `Samsung S20 Ultra`) > `Restart`.
   - `Settings` > `Installation` > `Installation method` > предоставьте **root-доступ** > выберите `Root installer`.
   - `Settings` > `Updates` > `Auto-update apps` > `Do not auto-update apps`.
4. Войдите как `Anonymous`.

ㅤ

### Другие приложения

- [Advanced Root Checker](https://play.google.com/store/apps/details?id=com.anu.developers3k.rootchecker)
- [Lawnchair](https://github.com/LawnchairLauncher/lawnchair?tab=readme-ov-file)
- [Shortcut Maker](https://play.google.com/store/apps/details?id=rk.android.app.shortcutmaker)
- [Soft Keys 2](https://github.com/dogusumit/SoftKeys2-HomeBackButton?tab=readme-ov-file) or [Back Button](https://play.google.com/store/apps/details?id=mavie.shadowsong.bb)
- [KillApps](https://play.google.com/store/apps/details?id=com.tafayor.killall)
- [ZArchiver](https://play.google.com/store/apps/details?id=ru.zdevs.zarchiver)
- [Amaze File Manager](https://github.com/TeamAmaze/AmazeFileManager?tab=readme-ov-file)
- [Fossify Gallery](https://github.com/FossifyOrg/Gallery?tab=readme-ov-file)
- [Magisk Modules Repo Loader (MMRL)](https://github.com/DerGoogler/MMRL?tab=readme-ov-file)
- [App Manager](https://github.com/MuntashirAkon/AppManager?tab=readme-ov-file)
- [DataBackup](https://github.com/XayahSuSuSu/Android-DataBackup?tab=readme-ov-file)
- [Termux](https://github.com/termux/termux-app?tab=readme-ov-file)
- [AFWall+](https://github.com/ukanth/afwall?tab=readme-ov-file)
- [Game Guardian](https://gameguardian.net/download) - [Bypass SDK enforcement](https://gameguardian.net/forum/topic/38963-game-guardian-android-14/)

### **Навигация по GPGPCDE**

Горячие клавиши GPGPCDE:

- <kbd>Ctrl</kbd> + <kbd>h</kbd>: нажать кнопку "Домой"
- <kbd>Ctrl</kbd> + <kbd>b</kbd> или <kbd>Esc</kbd>: нажать кнопку "Назад"
- <kbd>Ctrl</kbd> + <kbd>a</kbd>: открыть меню приложений (главный экран)
- <kbd>Ctrl</kbd> + <kbd>w</kbd>: открыть "Виджеты" (главный экран)
- <kbd>F11</kbd> или <kbd>Alt</kbd> + <kbd>Enter</kbd>: переключение между полноэкранным и оконным режимом
- <kbd>Shift</kbd> + <kbd>Tab</kbd>: открыть оверлей Google Play Games на ПК, включая текущие назначения клавиш для Input SDK

Примечание: <kbd>Ctrl</kbd> + <kbd>h</kbd> и <kbd>Ctrl</kbd> + <kbd>b</kbd> предоставляются только для целей разработки. Не полагайтесь на них в готовой игре.

### [**Скриншот**](./screenshot/README.md)

### [Метод 2](./2/README.md)

ㅤ

## **Благодарность**

- [XDA Forums t-4486817#post-89464596](https://xdaforums.com/t/4486817/post-89464596)
- [ChsBuffer](https://github.com/chsbuffer)
- [XDA Forums t-4656397](https://xdaforums.com/t/4656397/)
- [XDA Sideloading apps on GPGPCDE](https://www.xda-developers.com/sideload-apps-on-google-play-games-emulator/)
- [kilObit 7496373535076556798](https://kil0bit.blogspot.com/2023/11/google-launched-official-android.html)
- [Phandroid p-339416](https://phandroid.com/?p=339416)
