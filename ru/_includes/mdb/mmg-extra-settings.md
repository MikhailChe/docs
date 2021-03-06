- **Начало резервного копирования (UTC)** — время по UTC, когда требуется начать [резервное копирование](../../managed-mongodb/operations/cluster-backups.md) кластера (в 24-часовом формате). Если время не задано, резервное копирование начнется в 22:00 UTC.

- **Срок хранения автоматических резервных копий, дней** — время, в течение которого нужно хранить резервные копии, созданные автоматически. Если для какой-либо автоматической резервной копии истекает срок хранения, то она удаляется. Значение по умолчанию — {{ mmg-backup-retention }} дней. Эта функциональность находится на стадии [Preview](../../overview/concepts/launch-stages.md). Подробнее см. в разделе [{#T}](../../managed-mongodb/concepts/backup.md).

  Изменение срока хранения затрагивает как новые автоматические резервные копии, так и уже существующие.

  Например, если изначальный срок хранения был 7 дней и оставшееся время жизни отдельной автоматической резервной копии при таком сроке — 1 день, то при увеличении срока хранения до 9 дней, оставшееся время жизни этой резервной копии будет уже 3 дня.

- **Окно обслуживания** — настройки окна технического обслуживания. С их помощью вы можете указать предпочтительное время начала проведения операций по техническому обслуживанию хостов кластера (например, можно выбрать время, когда кластер наименее нагружен запросами):
  - Чтобы указать предпочтительное время начала окна технического обслуживания, выберите пункт **по расписанию** и задайте нужные день недели и час дня в UTC (Coordinated Universal Time), выбрав значения из выпадающих списков.
  - Чтобы разрешить проведение операций технического обслуживания в любое время, выберите пункт **произвольное**.

  Операции по техническому обслуживанию могут включать в себя: обновление версии СУБД, применение патчей и так далее.
