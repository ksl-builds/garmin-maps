# Публикация карты на GitHub

GitHub Releases принимает файлы размером меньше **2 ГиБ** каждый. IMG от 22 ноября 2026 года упакован в два тома RAR. [Лимиты GitHub Releases](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases#storage-and-bandwidth-quotas)

## Релиз 22 ноября

1. Отправьте ветку `main` в репозиторий **ksl-builds/garmin-maps**. Строка `[current-release]` в README должна указывать на страницу выпуска. [Репозиторий GitHub](https://github.com/ksl-builds/garmin-maps)
2. Откройте **Releases → Draft a new release**. Создайте тег `szfo-2026-11-22` от `main` и вставьте [готовое описание](releases/szfo-2026-11-22.md).
3. Приложите все пять файлов из подготовленной папки `2026.11.22/github`.
4. Опубликуйте релиз и проверьте, что оба тома скачиваются без входа в GitHub. [Создание релиза на GitHub](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository#creating-a-release)

### Файлы релиза

- `kmap-szfo-gravel-2026-11-22.part1.rar` и `kmap-szfo-gravel-2026-11-22.part2.rar` — тома карты.
- `GravelNavigation.kmtf` — опциональная тема линии курса.
- `northwestern-fed-district-261121.osm.pbf` — исходный срез OSM.
- `SHA256SUMS.txt` — контрольные суммы файлов. [SHA-256 извлечённого IMG](releases/szfo-2026-11-22.md#проверка-файла)

## Проверка перед обновлением карты

- **В лесу** грунтовка и тропа различимы у развилки.
- **В городе** видно нужное ответвление, когда поверх улиц показан курс.
- **С темой Edge** проверьте цвет и читаемость линии при движении по сохранённому курсу.

Смотрите на экран Edge в масштабе, которым пользуетесь в поездке.
