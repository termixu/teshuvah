# 📱 Прошивка Android (free-Google)

> Для примера возьмём **Pixel 6a / 6 / 7a** — идеальные для GrapheneOS. Также подходит для других моделей с LineageOS и /e/OS.

***

### 🔹 Этап 1: Подготовка

1. **Проверка модели**: узнай точную модель устройства:\
   `Настройки → О телефоне → Модель`
2. **Разблокировка загрузчика (bootloader)**:
   * Зайди в режим разработчика:\
     `Настройки → О телефоне → Нажимай 7 раз на «Номер сборки»`
   * Включи:
     * **OEM unlock**
     * **Отладка по USB**
3.  **Установка Android SDK (adb + fastboot)** на Linux/macOS:

    ```bash
    sudo apt install android-tools-adb android-tools-fastboot
    ```
4.  Подключи телефон по USB → проверь, что видит:

    ```bash
    adb devices
    ```

***

### 🔹 Этап 2: Разблокировка bootloader

> ⚠️ Удалит всё с телефона, но позволит прошивать любые ОС.

```bash
adb reboot bootloader
fastboot flashing unlock
```

На экране телефона — подтвердить.

***

### 🔹 Этап 3: Выбор прошивки

<table><thead><tr><th width="149.71875">ОС</th><th>Особенности</th></tr></thead><tbody><tr><td><strong>GrapheneOS</strong></td><td>Самая безопасная, без Google, только для Pixel</td></tr><tr><td><strong>LineageOS</strong></td><td>Чистый Android, можно ставить MicroG</td></tr><tr><td><strong>/e/OS</strong></td><td>Упрощённая система без Google, с магазином App Lounge</td></tr><tr><td><strong>Ubuntu Touch</strong></td><td>Линуксоподобный интерфейс, не для всех моделей</td></tr></tbody></table>

***

### 🔹 Этап 4: Установка прошивки

**Пример для GrapheneOS:**

1. Скачай официальный скрипт прошивки:\
   [https://grapheneos.org/install](https://grapheneos.org/install)
2. Используй либо:
   * Автоматическую установку через скрипт,
   *   Либо ручную через fastboot:

       ```bash
       fastboot flash boot boot.img
       fastboot flash system system.img
       fastboot flash vendor vendor.img
       ```

**Пример для LineageOS:**

1. Скачай прошивку для своей модели:\
   [https://download.lineageos.org/](https://download.lineageos.org/)
2. Также скачай recovery (Lineage Recovery или TWRP).
3.  Зайди в bootloader:

    ```bash
    adb reboot bootloader
    fastboot flash recovery recovery.img
    ```
4. Вошёл в recovery → «Wipe» → «Advanced» → выбери все, кроме SD-карты.
5. Установи `.zip` LineageOS:
   *   Перенеси на телефон по ADB:

       ```bash
       adb push lineage.zip /sdcard/
       ```
   * Установи через меню Recovery.

***

### 🔹 Этап 5: Настройка без Google

1. **F-Droid** – альтернатива Google Play:\
   [https://f-droid.org](https://f-droid.org/)
2. **Aurora Store** – магазин приложений с Google Play без Google-аккаунта:\
   [https://auroraoss.com](https://auroraoss.com/)
3. **MicroG** – если хочешь использовать некоторые GMS‑зависимые приложения:\
   [https://microg.org](https://microg.org/)
4. Отключи:
   * Автообновления,
   * Bluetooth, Wi-Fi‑сканирование, геолокацию,
   * Все сетевые службы, если нужен режим «без сети».

***

### 🔹 Этап 6: Офлайн-инструменты

* **Kiwix** — офлайн Википедия и книги
* **Organic Maps** — офлайн-карты
* **Termux** — офлайн-терминал
* **Simple Mobile Tools** — офлайн-заметки, файлы, галерея
* **GPT4All + нейросети** — офлайн-ИИ (сильно зависит от RAM)
