# LinSt - Linux Distribution Helper

LinSt (Linux Install) - это мощный инструмент для скачивания и записи дистрибутивов Linux на USB-накопители.

## Особенности

- 📦 **Автоматическое скачивание** - выбирайте дистрибутив из списка, скрипт скачает его автоматически
- 🎯 **Поддержка множества дистрибутивов** - Arch, Debian, Ubuntu, Kali, EndeavourOS, Fedora, Mint, Manjaro и другие
- 🖥️ **Выбор рабочего стола** - для дистрибутивов с несколькими DE (Mint, Manjaro, Pop!_OS)
- 🔧 **Два метода записи** - dd (прямая запись) и Ventoy (мультизагрузочная флешка)
- 📄 **JSON конфигурация** - легко добавляйте новые дистрибутивы
- 🎨 **Интерактивный интерфейс** - поддержка fzf для удобного выбора

## Требования

- `bash` (4.0+)
- `jq` - для работы с JSON
- `curl` или `wget` - для скачивания ISO
- `sudo` - для записи на устройство
- `lsblk`, `dd` - системные утилиты
- `ventoy` - опционально, для метода Ventoy
- `fzf` - опционально, для улучшенного интерфейса

### Установка зависимостей

**Ubuntu/Debian:**
```bash
sudo apt install jq curl fzf
```

**Arch Linux:**
```bash
sudo pacman -S jq curl fzf
```

**Fedora:**
```bash
sudo dnf install jq curl fzf
```

## Использование

### Интерактивный режим (рекомендуется)
```bash
./linst
```

### Список доступных дистрибутивов
```bash
./linst --list-distros
```

### Использование локального ISO
```bash
./linst -i ~/Downloads/ubuntu.iso
```

### Только скачивание без записи
```bash
./linst --download-only
```

### Автоматический режим
```bash
./linst -d sdd -m ventoy --no-confirm
```

## Поддерживаемые дистрибутивы

| Дистрибутив | Версии | Рабочие столы |
|-------------|--------|---------------|
| Arch Linux | Latest | - |
| Debian | 12 | - |
| Ubuntu | 24.04, 22.04 | - |
| Kali Linux | Latest | - |
| EndeavourOS | Latest | - |
| Fedora | 40 | - |
| Linux Mint | 22 | Cinnamon, MATE, Xfce |
| Manjaro | Latest | KDE, GNOME, Xfce |
| Zorin OS | 17 | - |
| elementary OS | 8 | - |
| Pop!_OS | 22.04 | Intel/AMD, NVIDIA |

## Добавление новых дистрибутивов

Отредактируйте файл `distros.json`:

```json
{
  "distros": {
    "your-distro": {
      "name": "Your Distribution",
      "versions": {
        "1.0": {
          "url": "https://your-distro.com/download/",
          "iso_url": "https://your-distro.com/iso/your-distro-1.0.iso",
          "description": "Your Distribution 1.0"
        }
      }
    }
  }
}
```

### Дистрибутивы с несколькими рабочими столами

```json
{
  "distros": {
    "multi-de-distro": {
      "name": "Multi DE Distribution",
      "versions": {
        "1.0": {
          "url": "https://multi-de-distro.com/download/",
          "description": "Multi DE Distribution 1.0",
          "desktop_environments": {
            "kde": {
              "iso_url": "https://multi-de-distro.com/kde.iso",
              "description": "Multi DE Distribution KDE"
            },
            "gnome": {
              "iso_url": "https://multi-de-distro.com/gnome.iso",
              "description": "Multi DE Distribution GNOME"
            }
          }
        }
      }
    }
  }
}
```

## Методы записи

### DD (прямая запись)
- Записывает ISO напрямую на устройство
- Быстро и просто
- Одна загрузка на флешку

### Ventoy
- Создает мультизагрузочную флешку
- Можно добавлять несколько ISO
- Требует установки Ventoy CLI

## Безопасность

⚠️ **Внимание!** Запись на устройство удалит все данные на нем. Всегда проверяйте выбранное устройство перед записью.

## Вклад в проект

Для добавления новых дистрибутивов или улучшений создайте pull request с изменениями в `distros.json` или коде скрипта.

## Лицензия

MIT License
