# Публикация карты одним файлом

Проект **garmin-gravel-szfo** на GitLab.com. Текущая сборка от 22 ноября 2026 года весит **2,53 ГБ**. Файл **gravel-szfo.img** публикуется в **Generic Package Registry**, где лимит одного файла — 5 ГБ. [Лимиты GitLab.com](https://docs.gitlab.com/user/gitlab_com/#package-registry-limits)

## Релиз 22 ноября

1. В публичном проекте GitLab включите **Package registry**. [Доступ к пакетам](https://docs.gitlab.com/user/packages/package_registry/#package-registry-visibility-permissions)
2. Загрузите IMG и исходный срез OSM командой ниже. Проверьте, что прямые ссылки открываются без входа.
3. В верхней строке README поставьте ссылку **Скачать карту** на `$mapUrl`. Отправьте в GitLab коммит с README, изображениями, стилем и настройками.
4. В **Deploy → Releases** создайте релиз с тегом **szfo-2026-11-22** от этого коммита. Возьмите [готовое описание](releases/szfo-2026-11-22.md), добавьте `$mapUrl` как файл **gravel-szfo.img**, а `$sourceUrl` укажите в источниках. [Файлы релиза](https://docs.gitlab.com/user/project/releases/release_fields/#use-a-generic-package-for-attaching-binaries)

### Загрузка файлов

В PowerShell укажите числовой ID проекта и путь к подготовленной папке `2026.11.22`. Передайте deploy token с правом **write_package_registry** через переменную `KMAP_PACKAGE_TOKEN`.

~~~powershell
$projectId = '<ID проекта>'
$assets = '<путь к папке 2026.11.22>'
$packageUrl = "https://gitlab.com/api/v4/projects/$projectId/packages/generic/garmin-szfo/2026.11.22"
$mapFile = Join-Path $assets 'gravel-szfo.img'
$sourceName = 'northwestern-fed-district-261121.osm.pbf'
$sourceFile = Join-Path (Join-Path $assets 'sources') $sourceName
$mapUrl = "$packageUrl/gravel-szfo.img"
$sourceUrl = "$packageUrl/$sourceName"
$header = "DEPLOY-TOKEN: $env:KMAP_PACKAGE_TOKEN"

curl.exe --fail-with-body --header $header --upload-file $mapFile $mapUrl
if ($LASTEXITCODE -ne 0) { throw 'Ошибка загрузки IMG' }

curl.exe --fail-with-body --header $header --upload-file $sourceFile $sourceUrl
if ($LASTEXITCODE -ne 0) { throw 'Ошибка загрузки среза OSM' }

$mapUrl
$sourceUrl
~~~

[Загрузка в GitLab Generic Packages](https://docs.gitlab.com/user/packages/generic_packages/#publish-a-single-file) · [SHA‑256 IMG](releases/szfo-2026-11-22.md#проверка-файла)

## Проверка перед обновлением карты

- **В лесу** грунтовка и тропа различимы у развилки.
- **В городе** видно нужное ответвление, когда поверх улиц показан курс.

Смотрите на экран Edge в масштабе, которым пользуетесь в поездке.
