# Magisk на GPGPCDE: Способ 2

Установка Magisk на GPGPCDE (Google Play Games на PC Developer Emulator).

ㅤ
## Содержание

- [Минимальные системные требования](#минимальные-системные-требования)
- [Установка](#установка)  
  - [Требования](#1-требования)  
  - [Google Play Games на PC Developer Emulator (GPGPCDE)](#2-google-play-games-on-pc-developer-emulator-gpgpcde)  
  - [Aow Tools](#3-aow-tools)  
  - [Magisk](#4-magisk)  
  - [Создание папки](#5-создание-папки)  
  - [Получение root с `hpesuperpower`](#6-получение-root-с-hpesuperpower)
- [Установка приложений](#установка-приложений)  
  - [AdAway](#adaway)  
  - [Aurora Store](#aurora-store)  
  - [Другие приложения](#другие-приложения)
- [Дополнительно](#дополнительно)  
  - [Навигация в GPGPCDE](#навигация-в-gpgpcde)  
  - [Скриншот](#скриншот)
- [Благодарности](#благодарности)

ㅤ
## Минимальные системные требования

- **ОС**: Windows 10 (v2004)
- **Хранилище**: SSD с 10 ГБ свободного места
- **Графика**: IntelⓇ UHD Graphics 630 GPU или аналогичная
- **Процессор**: 4 физических ядра (некоторые игры требуют CPU Intel)
- **Память**: 8 ГБ ОЗУ
- Учетная запись администратора Windows
- Аппаратная виртуализация должна быть включена:
  - [Включить виртуализацию](https://support.microsoft.com/en-us/windows/enable-virtualization-on-windows-c5578302-6e43-4b4b-a449-8ced115f58e1)
  - [Включить Hyper-V](https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)

**Примечание**: подробнее о требованиях [читайте здесь](https://support.google.com/googleplay?p=eligibility_requirements).

ㅤ
## Установка

### 1. Требования

- [Google Play Games на PC Developer Emulator](https://developer.android.com/games/playgames/emulator) (GPGPCDE)
- [Aow Tools](https://apps.microsoft.com/detail/9nxm6552h2ql?hl=en-US) (Бесплатная пробная версия)
- [hpesuperpower](https://github.com/chsbuffer/hpesuperpower?tab=readme-ov-file)
- [Magisk](https://github.com/topjohnwu/Magisk?tab=readme-ov-file)
- [7-Zip](https://7-zip.org/)

ㅤ
### 2. Google Play Games на PC Developer Emulator (GPGPCDE)

1. Скачайте и установите **GPGPCDE** (Stable Edition).
2. Откройте **GPGPCDE** и войдите в свой Google-аккаунт.
3. Разрешите `USB-отладку`, отметьте `Всегда разрешать с этого компьютера`, затем нажмите `Разрешить`.

ㅤ  
**Примечание**: 
- При **выходе из системы** локальные **файлы устройства**, включая **установленные приложения/игры**, будут <ins>**удалены**</ins>.
- Если экран **GPGPCDE** пуст (спящий режим), используйте:
  - Клавиши **PgDn** <kbd>↓</kbd>
  - **Клик и свайп вверх**
  - **Прокрутку мышью** (режим ПК).
- [Навигация (горячие клавиши)](#навигация-в-gpgpcde)

ㅤ
### 3. Aow Tools

1. Установите **Aow Tools**, нажав кнопку **Free Trial**.  
  Не беспокойтесь, приложение поддерживает <ins>неограниченные пробные периоды</ins>.  
  Вы можете **поддержать** разработчика, купив приложение.
2. Откройте **Aow Tools** и нажмите меню `⚙ Настройки` в левой панели.
    - Раздел `Adb Config` > `Adb.exe Current Path` > `Select Adb.exe`
    - Вставьте следующий путь в адресную строку Проводника:  
    `C:\Program Files\Google\Play Games Developer Emulator\current\emulator`
    - Добавьте файл `adb.exe`.
3. Откройте **Aow Tools** и нажмите меню `? Помощь` в левой панели.
4. В разделе `Remove local loopback restrictions` используйте первый метод с **CMD** (от имени администратора).
5. Нажмите меню `Устройство`. Устройство **GPGPCDE** (`vsoc_kiwi_x86_64`) появится в статусе `Online`.

ㅤ
### 4. Magisk

1. Скачайте приложение **Magisk**.
2. Откройте **Aow Tools** > `Установка` > Перетащите APK-файлы для установки Android-приложений.
3. Установите **Magisk**.
4. Откройте **GPGPCDE**, Magisk появится в меню приложений.

ㅤ
### 5. Создание папки

1. Откройте **Проводник**.
2. Перейдите на **Рабочий стол** или в `%UserProfile%\Desktop`.
3. Создайте папку "**GPGPCDE**".

ㅤ
### 6. Получение root с `hpesuperpower`

1. В **области уведомлений** или **системном трее** нажмите правой кнопкой на иконку **GPGPCDE** и выберите `Выход`.
2. Скачайте и распакуйте **hpesuperpower** в папку `%UserProfile%\Desktop\GPGPCDE`.
3. Переместите файл `Magisk-vXX.XX.apk` в папку `%UserProfile%\Desktop\GPGPCDE`.
4. Откройте **CMD** от имени администратора.
5. Перейдите в папку **GPGPCDE**, введите `cd /d %UserProfile%\Desktop\GPGPCDE` > **Enter**.
6. Получите root для **GPGPCDE** командой `hpesuperpower.exe --dev magisk <magisk_apk_file>` > **Enter**.
    - Например: `hpesuperpower.exe --dev magisk Magisk-v28.1.apk`.
    - Подробнее о командах **hpesuperpower** [читайте здесь](https://github.com/chsbuffer/hpesuperpower/releases/tag/1.1.0).

      ![GPGPCDE-cmd-1](./images/GPGPCDE-cmd-1.png)
7. Дождитесь завершения процесса получения root.

    ![GPGPCDE-cmd-2](./images/GPGPCDE-cmd-2.png)
8. Перезапустите **GPGPCDE**.
9. Откройте **Magisk** > появится запрос `Требуется дополнительная настройка` > `OK`.
10. Дождитесь перезагрузки **GPGPCDE**.

ㅤ
## Установка приложений

### AdAway

1. Откройте **Magisk** > `⚙` Настройки (вверху справа) > раздел `Magisk` > нажмите `Systemless hosts`.
2. Закройте **GPGPCDE** ([#11-1](#11-replace-with-patched-files)).
3. Перезапустите **GPGPCDE**.
4. Скачайте и установите [AdAway](https://github.com/AdAway/AdAway?tab=readme-ov-file) через **Aow Tools**.
5. Откройте **AdAway** > выберите `Блокировка рекламы через root` > предоставьте **root-доступ** > `ДАЛЕЕ`.
6. Синхронизируйте **AdAway** > `ДАЛЕЕ` > `ГОТОВО`.

ㅤ
### Aurora Store

1. Скачайте [Aurora Store](https://gitlab.com/AuroraOSS/AuroraStore) и установите через **Aow Tools**.
2. Откройте **Aurora Store** > настройка:
    - Разрешите:
      - `Разрешение на установку`
      - `Менеджер внешнего хранилища`
      - `Фоновые загрузки`
      - `Уведомления`
      - `Ссылки на приложения`
    - Нажмите `Готово`.
3. Нажмите **3 точки** вверху справа:
    - `Spoof manager` > выберите `Устройство`, например: `Samsung S20 Ultra` > `Перезапуск`.
    - `Настройки` > `Установка` > `Метод установки` > предоставьте **root-доступ** > выберите `Установка через root`.
    - `Настройки` > `Обновления` > `Автообновление приложений` > `Не обновлять автоматически`.
4. Вернитесь назад и войдите как `Аноним`.

ㅤ
### Другие приложения

- [Advanced Root Checker](https://play.google.com/store/apps/details?id=com.anu.developers3k.rootchecker)
- [Lawnchair](https://github.com/LawnchairLauncher/lawnchair?tab=readme-ov-file)
- [Shortcut Maker](https://play.google.com/store/apps/details?id=rk.android.app.shortcutmaker)
- [Soft Keys 2](https://github.com/dogusumit/SoftKeys2-HomeBackButton?tab=readme-ov-file) или [Back Button](https://play.google.com/store/apps/details?id=mavie.shadowsong.bb)
- [KillApps](https://play.google.com/store/apps/details?id=com.tafayor.killall)
- [ZArchiver](https://play.google.com/store/apps/details?id=ru.zdevs.zarchiver)
- [Magisk Modules Repo Loader (MMRL)](https://github.com/DerGoogler/MMRL?tab=readme-ov-file)
- [App Manager](https://github.com/MuntashirAkon/AppManager?tab=readme-ov-file)
- [DataBackup](https://github.com/XayahSuSuSu/Android-DataBackup?tab=readme-ov-file)
- [Termux](https://github.com/termux/termux-app?tab=readme-ov-file)
- [AFWall+](https://github.com/ukanth/afwall?tab=readme-ov-file)
- [Game Guardian](https://gameguardian.net/download) - [Обход проверки SDK](https://gameguardian.net/forum/topic/38963-game-guardian-android-14/)

ㅤ
## Дополнительно

### Навигация в GPGPCDE

Горячие клавиши GPGPCDE:
- <kbd>Ctrl</kbd> + <kbd>h</kbd>: кнопка "Домой"
- <kbd>Ctrl</kbd> + <kbd>b</kbd> или <kbd>Esc</kbd>: кнопка "Назад"
- <kbd>Ctrl</kbd> + <kbd>a</kbd>: открыть меню приложений (главный экран)
- <kbd>Ctrl</kbd> + <kbd>w</kbd>: открыть `Виджеты` (главный экран)
- <kbd>F11</kbd> или <kbd>Alt</kbd> + <kbd>Enter</kbd>: переключение между полноэкранным и оконным режимом
- <kbd>Shift</kbd> + <kbd>Tab</kbd>: открыть оверлей Google Play Games на ПК, включая текущие настройки ввода

Примечание: <kbd>Ctrl</kbd> + <kbd>h</kbd> и <kbd>Ctrl</kbd> + <kbd>b</kbd> предназначены только для разработки. Не используйте их в готовых играх.


### [Способ: 1](../README.md)

ㅤ
## Благодарности

- [Сообщество GPGPC](https://discord.gg/UYPSypWA8M)
- [hpesuperpower](https://github.com/chsbuffer/hpesuperpower?tab=readme-ov-file)
