---
tags: [zettelkasten, книга, linux, команды, systemd, службы]
source: "Внутреннее устройство Linux [2022] Брайан Уорд"
type: concept
---
# Утилита systemctl

Утилита `systemctl` является основным инструментом администратора для управления `systemd` и системными службами.

Ключевые команды:
- `systemctl start name.service`: запуск службы.
- `systemctl stop name.service`: остановка службы.
- `systemctl restart name.service`: перезапуск службы.
- `systemctl status name.service`: вывод текущего статуса и последних логов службы.
- `systemctl enable name.service`: добавление службы в автозагрузку при старте ОС.
- `systemctl disable name.service`: удаление службы из автозагрузки.

**Связи:**
- [[Система инициализации systemd]]
