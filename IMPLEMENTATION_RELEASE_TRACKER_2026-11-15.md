# MAP NAVI — список изменений и календарь подготовки к первой экскурсии

**Обновлено:** 24 ноября 2026 года, 09:18:03 (Europe/Berlin)
**Первая экскурсия:** 27 ноября 2026 года  
**Цель:** стабильная версия обычной навигации должна быть опубликована и проверена до экскурсии. Пространственная трёхуровневая модель не блокирует этот выпуск.

> Важно о времени: в прежней записи были даты, но не были внесены часы выполнения. Поэтому ниже часы впервые зафиксированы как рабочий календарный план, а не как якобы ранее согласованные обязательства. Время указано по Германии (Europe/Berlin).

## 1. Список изменений для переноса

Переносим в существующий репозиторий приложения `basana/turret-tales-christmas`, отдельной рабочей веткой. Для каждого пункта отмечаем отдельно: перенесено → проверено в Preview → одобрено пользователем → опубликовано в Netlify.

| № | Изменение | Источник / известное состояние | Статус |
|---|---|---|---|
| 1 | GPS Follow: следование за текущим местоположением | Integration commit `e094b25e8742c151f3cc5c215c221d8a91481bb9`; candidate branch `feature/map-navi-poi-pulse-states-2026-11-19` HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439` | Код есть в PR #3/#6 на основной карте; более новая candidate branch добавляет Follow на основной, Christmas и winery maps. Preview/device test не подтверждён |
| 2 | Free View: ручное перемещение карты без выключения GPS | Integration commit `e094b25e8742c151f3cc5c215c221d8a91481bb9`; candidate branch HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439` | В PR #3/#6 — основная карта; candidate branch добавляет переход в Free View по ручным pan/zoom на основной, Christmas и winery maps. Runtime/device test не подтверждён |
| 3 | Ручной возврат к GPS и кнопка `↻ Follow` | Integration commit `e094b25e8742c151f3cc5c215c221d8a91481bb9`; candidate branch HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439` | Код возврата к GPS есть на основной, Christmas и winery maps в candidate branch; Preview/device test не подтверждён |
| 4 | Правая вертикальная колонка Pharmacy / Toilets / Reset | Integration commit `943801e75033c51c09943e79038caad799ec3baa`; candidate branch HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439` | Кнопки есть на основной и Christmas maps; candidate branch содержит полный Reset cleanup для обеих. Визуальная и runtime-проверка не подтверждена |
| 5 | Автофокус ближайшей аптеки/туалета при включении поиска | Базовый `_zoomToNearestPoi` в main; integration commit `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; candidate branch HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439` | Candidate branch содержит pending POI до первого GPS fix и автофокус для основной и Christmas maps; runtime test не подтверждён |
| 6 | Приоритет выбранного POI: GPS не перетягивает камеру, пока активен POI | Integration commit `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; candidate commits `955ec76c`, `7fb323ce`, `364db9e1` и HEAD `80f542b3` | Candidate branch содержит shared focus intent для Follow/Free View/search/POI и сохраняет последний выбор на основной, Christmas и winery maps; device test не подтверждён |
| 7 | Общая компоновка поиска и ticker/легенды | Preview-коммиты `db9f392`, `6d6a9bf` | Полный search/ticker/legend пакет не перенесён; PR #6 содержит только отдельную компоновку поиска Christmas map |
| 8 | Мобильная ширина и расположение элементов | PR #6 и candidate branch `80f542b3`; commits `8beefcecc`, `306b1f90`, `5079bc9a` | Candidate включает Christmas map layout, search/GPS overlay, уменьшенную GPS-панель и нижнюю карусель основной карты; отдельный Preview mobile-width fix не подтверждён; device test отсутствует |
| 9 | Toast / overlay / z-index | PR #6 PopupManager; candidate commits `e80f8192`, `39836e1c`, `80f542b3` | Candidate содержит popup context gating, визуальные POI request states и исправления конкурирующих overlays; точный перенос Preview-коммита `fc0078a` не подтверждён |
| 10 | Вертикальное положение zoom-кнопок карты рынков | Preview-коммит `b27c044` | Не перенесено в PR #3/#6; требуется отдельная сверка |
| 11 | Единообразная проверка основных карт на iPhone и iPad | Интеграционный Preview | Не подтверждено; реальный браузерный и device test не зафиксирован |
| 12 | Полный Reset состояния и Popup Manager | Draft PR #6 head `4c0d6d28c413fbc0d255cedef03091183837d188`; candidate branch `80f542b3d7a5c51123ff9b129b0d59374762d439` | В PR #6 Reset cleanup для основной карты; более новая candidate branch добавляет очистку POI layers/pending focus/controls и возврат общего обзора Christmas map. PopupManager есть. Harness — только заявления PR body; CI/device test отсутствуют |
| 13 | Нижняя горизонтальная карусель объектов карты | Candidate commit `8eb777684e0b9f778e5d6034102e0253c312bf21`; branch `feature/map-navi-poi-pulse-states-2026-11-19` | Код есть на основной карте: swipe выбирает ближайшую карточку, tap открывает детали и центрирует/приближает точку. Пока список только замки/города; динамическая замена на POI-категории не подтверждена. Preview/device test отсутствует |

Ссылки:
- [Репозиторий приложения](https://github.com/basana/turret-tales-christmas)
- [GPS-ветка](https://github.com/basana/turret-tales-christmas/tree/feature/map-navi-gps-follow-01)
- [Preview-ветка](https://github.com/basana/turret-tales-christmas/tree/preview/gps-follow-device-test-01)
- [Preview shell](https://github.com/basana/turret-tales-preview)
- [PR #2 — GPS Follow device test](https://github.com/basana/turret-tales-christmas/pull/2)
- [PR #6 — Reset / Popup Manager / map stabilization, draft](https://github.com/basana/turret-tales-christmas/pull/6)

**Последний подтверждённый фактический статус на 20 ноября 2026 года, 09:52 (Europe/Berlin):** application `main` остаётся на `2291e55a513eadb6ff00b7011cfc74d9b25ef947`. Integration `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb` — 4 commits ahead / 0 behind, PR #3 open/unmerged. Stabilized integration `4c0d6d28c413fbc0d255cedef03091183837d188` — 13 ahead / 0 behind integration и 17 ahead / 0 behind main; PR #6 open/draft. Обнаружена более новая отдельная candidate branch `feature/map-navi-poi-pulse-states-2026-11-19`, HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439`: 33 commits ahead / 0 behind integration и 20 ahead / 0 behind PR #6; diff включает `index.html` и `sw.js`; открытого PR для неё нет. По коду этой ветки GPS Follow/Free View/manual recenter добавлены на основную, Christmas и winery maps; shared focus intent сохраняет приоритет последнего выбора/POI; pending POI ждёт первого GPS fix; полный Reset очищает POI и временное состояние основной и Christmas maps. Добавлены state-aware POI pulses и нижняя swipeable carousel на основной карте. Карусель сейчас формируется из castle/town items, не из динамически переключаемых POI-категорий. Концепция карусели ранее согласована пользователем, но текущая реализация не проверена и не одобрена. PR #6 по-прежнему 4c0d6d28; его body содержит устаревшее число 7 commits ahead, актуальный compare API подтверждает 13. PR #4/#5 также open/draft. Новая candidate branch не имеет PR, check-runs или Preview; для commit 80f542b3 check-runs = 0, statuses = 0. Отдельный Preview repo обновлён до main `e11b9997d4c589e08e83760f6ff4e571677e7818`; Pages workflow `44623470587` завершился success, но его `index.html` по-прежнему содержит `<base href="https://turrettales.de/">`, имеет POI focus/Christmas layout, но не carousel; это не Preview candidate branch. Открытие Preview и production URL через доступный браузерный инструмент не удалось. Netlify deployed commit не подтверждён. iPhone/iPad tests и implementation user approval не подтверждены. Main не менялся; merge/Netlify Deploy не выполнялись.
## 2. Календарь по дням и времени

Все часы — местное время Германии (Europe/Berlin). Это рабочие окна плана; фактическое выполнение отмечается только после работы и проверки.

| Дата | Время | Работа / ожидаемый результат |
|---|---:|---|
| **15 ноября, воскресенье** | 15:00–17:00 | Подготовить аудит: сверить GPS-ветку, Preview-ветку и текущую исходную ветку приложения; определить базовую ветку интеграции. |
| **16 ноября, понедельник** | 10:00–12:00 | Проверить конфигурацию публикации Netlify и актуальные ветки; зафиксировать точную базу и файлы для переноса. |
| **16 ноября, понедельник** | 13:00–16:00 | Перенести GPS Follow / Free View и ручной возврат к GPS отдельными коммитами. |
| **17 ноября, вторник** | 10:00–13:00 | Перенести правые кнопки Pharmacy / Toilets / Reset и проверить общий интерфейс. |
| **17 ноября, вторник** | 14:00–16:00 | Перенести POI auto-focus и приоритет камеры выбранного POI; проверить, что GPS не сбивает фокус. |
| **18 ноября, среда** | 10:00–13:00 | Перенести поиск, ticker, мобильную компоновку, toast и zoom-кнопки рынков. |
| **18 ноября, среда** | 14:00–16:00 | Проверить целостность кода, зависимости, Service Worker/manifest и работу после перезагрузки. |
| **19 ноября, четверг** | 10:00–12:00 | Собрать Preview интеграционной ветки; пройти основной сценарий GPS Follow / Free View. |
| **19 ноября, четверг** | 13:00–15:00 | Проверить поиск аптек и туалетов, расстояния, автофокус, Reset и приоритет POI. |
| **20 ноября, пятница** | 10:00–12:00 | Проверить Koblenz / castle map на iPhone в портретном режиме. |
| **20 ноября, пятница** | 13:00–15:00 | Проверить iPad в горизонтальном режиме; поиск, легенду, кнопки, toast и zoom. |
| **21 ноября, суббота** | 10:00–12:00 | Проверить карту рынков и остальные применимые карты; отдельно отметить функции, которые ещё не перенесены на каждую карту. |
| **22 ноября, воскресенье** | 10:00–12:00 | Повторный полный тест, список ошибок и исправление блокирующих дефектов. |
| **23 ноября, понедельник** | 10:00–12:00 | Зафиксировать release candidate, проверить коммиты и точку отката. |
| **24 ноября, вторник** | 10:00–12:00 | Финальная проверка кандидата; прекратить добавление рискованных новых функций. |
| **25 ноября, среда** | 10:00–12:00 | Передать тебе готовый источник/ветку и инструкции; ты выполняешь Deploy на Netlify. |
| **26 ноября, четверг** | 10:00–11:00 | Проверить именно опубликованный Netlify-сайт на устройстве; записать deployed commit и результат. |
| **27 ноября, пятница** | До экскурсии | Использовать проверенную опубликованную версию; новые изменения в день экскурсии не вносить. |

Если рабочее окно не подходит, его можно сдвинуть; сроки выпуска и первая экскурсия остаются контрольными датами. Важнее фиксировать реальное состояние, чем изображать выполнение по календарю.

## 3. Критерии готовности

- GPS включается и корректно следует за пользователем.
- Ручной pan/zoom переводит карту в Free View, GPS при этом остаётся включён.
- `↻ Follow` возвращает карту к последним GPS-координатам.
- Поиск аптеки/туалета сразу фокусирует ближайший подходящий POI.
- Активный POI не теряет фокус из-за фоновых GPS-обновлений.
- Reset возвращает общий обзор карты.
- Поиск, легенда, кнопки, уведомления и zoom не перекрывают друг друга.
- Основные сценарии проверены на iPhone и iPad.
- После пользовательского Deploy отдельно проверен live-сайт Netlify.

## 4. Защита production

1. Работаем в отдельной ветке `basana/turret-tales-christmas`.
2. Не меняем `main` и не делаем Deploy без явного разрешения пользователя.
3. Не считаем функцию завершённой только потому, что она есть в Preview или прошла проверку синтаксиса.
4. Для каждого изменения записываем commit SHA, дату и время, результат теста и оставшиеся проблемы.
5. Сохраняем возможность вернуться к последней рабочей версии.

## 5. Отдельная пространственная разработка

Трёхуровневая голубая архитектурная модель, связи и Storymarks развиваются параллельно. Они не являются обязательным условием готовности обычной навигации к 27 ноября.

## Журнал изменений Project Map

### 15 ноября 2026 года, 14:00 (Europe/Berlin)
- Зафиксирована просьба пользователя писать месяцы словами, а не цифрами.
- Зафиксировано требование указывать не только даты, но и точное время и часовой пояс.
- Подготовлен явный перечень из 11 пунктов для переноса и проверки.
- Добавлен календарь по дням и рабочим временным окнам.
- Уточнено, что ранее в трекере были даты без времени; часы ниже являются новым рабочим расписанием, а не восстановленной прежней договорённостью.
- Код приложения не изменён; перенос ещё ожидает аудита и выполнения.


## Initial repository audit — 15 November 2026

Read-only GitHub audit performed after the tracker was created. No application files, branches, pull requests, merges, or deployments were changed.

### Confirmed repository state
- Application default branch `main`: `2291e55a513eadb6ff00b7011cfc74d9b25ef947` (latest commit message: unify map buttons; all maps use a shared POI toggle bar; reset/pharmacy/toilets controls; legend position restored). This is present in the application repository's current `main`, but this audit does not establish that every interaction was tested on devices.
- GPS work branch `feature/map-navi-gps-follow-01`: `56e011ee73c76eea72e97bc1f682292972d88868`. Compared with current `main`, GitHub reports it is diverged: 3 commits ahead and 1 behind; only `index.html` differs in the comparison summary. Do not merge it as-is; reconcile the new main commit first.
- Preview branch `preview/gps-follow-device-test-01`: `b5a48df004a07d37f2ee84963edeff0f5e693a39`. It is 2 commits ahead of current `main`; changes are in `index.html` and `sw.js`.
- PR #2 remains OPEN and UNMERGED: https://github.com/basana/turret-tales-christmas/pull/2. It is explicitly labelled preview/device-test only. Head `b5a48df004a07d37f2ee84963edeff0f5e693a39`, base `2291e55a513eadb6ff00b7011cfc74d9b25ef947`. No merge or production deployment was performed.
- Separate Preview repository `basana/turret-tales-preview` has additional commits through `a1ea99e4d3b6bd0b00f6d26e096b6ec46f8c6ca5` (15 Nov): POI toast action focus, pharmacy/toilet POI centering, market zoom controls, toast/search stacking, narrow-screen search width, search/ticker and shared control layout. These commits are in the Preview repository, not thereby transferred into the application repository.

### Current status by feature
| Feature | Present in application main | Preview / branch evidence | User/device approval | Live deployed |
|---|---|---|---|---|
| Shared Pharmacy / Toilets / Reset controls | Present in latest main commit `2291e55` (code commit evidence) | Also present in preview work | Not freshly verified in this audit | Not verified |
| GPS Follow / Free View | Not confirmed in current main by this audit | Present in GPS branch and PR #2 preview branch | Prior user-reported Preview GPS test exists in project history; no new device test today | Not verified |
| Manual recenter / Follow return | Not confirmed in current main | Included in GPS work branch/PR scope | Prior Preview test history; no new test today | Not verified |
| POI auto-focus / camera priority | Not confirmed in current main | Preview repo commits `57408be` and `a1ea99e` | Awaiting explicit user confirmation on current Preview build | Not verified |
| Search / ticker / overlays / mobile width | Not confirmed in current main | Preview repo commits `db9f392`, `6d6a9bf`, `fc0078a` | Not freshly device-verified | Not verified |
| Toast positioning / market zoom controls | Not confirmed in current main | Preview repo commits `fc0078a`, `b27c044` | Not freshly device-verified | Not verified |

### Immediate blockers / next actions
1. Reconcile the GPS branch's 3-ahead / 1-behind divergence against current `main`; do not merge blindly.
2. Compare the separate Preview repository's latest `index.html` with the application repository and identify precisely which preview-only fixes are portable, with attention to the Preview shell's external `<base href>` and service-worker scope.
3. Prepare a clean integration branch in `basana/turret-tales-christmas` only after the comparison; keep `main` untouched.
4. User should confirm the latest POI auto-focus behavior on the Preview URL when convenient. Until then it remains code-present / user-verification-pending, not user-approved.
5. Confirm the Netlify-connected branch and deployment settings before release; no deployment state was inspected in this audit.

### Audit conclusion
The work is **not a two-day code-copy task**, but it is also **not yet a single integrated release package**. The GPS changes, the current application main's newer shared-control commit, and the Preview repository's later POI/UI fixes live in different refs/repositories. A careful comparison and small integration commits are required. No feature is marked transferred, freshly device-tested, approved, or deployed solely on the basis of its existence in a branch.


## 15 ноября 2026 года, 16:25 (Europe/Berlin) — обновление отображения Project Map

- На главной панели добавлен видимый календарь подготовки, сгруппированный по дням и рабочим временным окнам.
- Журнал изменений теперь сгруппирован по календарным дням; для записей с timestamp отображаются часы и минуты по Europe/Berlin.
- Формат дат изменён: название месяца показывается словом (например, «15 ноября 2026 года»), а не числом месяца.
- Для старых записей без timestamp показывается «время не зафиксировано». Точное время задним числом не восстанавливается.
- Календарь добавлен также в структурированные данные Project Map, чтобы он был виден непосредственно на Dashboard, а не только внутри Markdown-файла.
- Коммиты Project Map: интерфейс календаря и журнала `e29243a042bbe5013c1093a2ec876d79c39ae889`; обновление данных и расписания `ff51df3eb05a6837a345eff28440055e440b0320`; формат даты в верхней панели `28dce1c70657540aa5aa1fe18f36bc0201f149ce`.
- Репозиторий приложения, его `main`, ветки и Netlify не затрагивались.


## 15 ноября 2026 года, 17:07 (Europe/Berlin) — интеграция GPS / POI / controls

- Продолжена работа только в `feature/map-navi-integration-2026-11-15`; `main` не изменялся.
- Проверено: ветка содержит GPS Follow / Free View и кнопку `↻ Follow`; ручное перемещение отключает слежение камеры, не выключая GPS.
- Проверено в коде: выбор аптеки/туалета при активном GPS приостанавливает GPS-follow камеры; GPS продолжает обновлять маркер и координаты. Добавлена обработка случая, когда POI выбран до получения первого GPS fix: запрос сохраняется и применяется после получения координат.
- Обе карты получили единый верхний правый вертикальный стек Pharmacy / Toilets / Reset; размеры адаптивны (48–68 px), символ Reset изменён на стрелки `⤢`.
- `sw.js` ограничен кэшем приложения с префиксом `rhine-design-test-`: очистка и offline fallback больше не обращаются ко всем Cache Storage записям origin.
- Коммиты integration-ветки: UI controls `943801e75033c51c09943e79038caad799ec3baa`; Service Worker `c84a69a0d9920aa3a584f581caed800377d0384b`; pending POI first-fix `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`.
- PR #3 обновлён: https://github.com/basana/turret-tales-christmas/pull/3. Он открыт, не слит. PR #2 также остаётся открытым и не слитым.
- Это проверка исходного кода, не проверка рендеринга или поведения на устройстве. Следующий шаг — подтвердить Deploy Preview и протестировать iPhone/iPad в портретной и альбомной ориентации.
- Production `main` и Netlify не затрагивались; merge и deployment не выполнялись.
## Ежедневная проверка — 16 ноября 2026 года, 09:12 (Europe/Berlin)

- Read-only сверены ветки, PR #2/#3, diff, commits, status checks, integration `index.html` / `sw.js` и отдельный Preview repo.
- Подтверждено: integration branch `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`, 4 commits ahead / 0 behind от application `main` `2291e55a513eadb6ff00b7011cfc74d9b25ef947`; PR #3 открыт, не слит.
- Проверены commit IDs: `e094b25e8742c151f3cc5c215c221d8a91481bb9`, `943801e75033c51c09943e79038caad799ec3baa`, `c84a69a0d9920aa3a584f581caed800377d0384b`, `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`.
- По коду Follow/Free View и ручной возврат подключены к основной карте; для Christmas/market map тот же режим Follow не подтверждён. Общие Pharmacy / Toilets / Reset controls присутствуют в коде обеих карт.
- PR #3 не имеет check runs/status checks; его Deploy Preview не подтверждён. Device test, user approval и live Netlify status не подтверждены.
- Отдельный Preview repo: последний commit `a1ea99e4d3b6bd0b00f6d26e096b6ec46f8c6ca5`, GitHub Pages build success; это не сборка integration branch.
- Preview-only улучшения центрирования POI, search/ticker/overlay, mobile layout, toast/z-index и market zoom в PR #3 не перенесены.
- Следующий блокер: получить доступный Deploy Preview именно PR #3 и провести реальные тесты; отдельно проверить Netlify branch/deploy settings. До этого не отмечать функции Preview-tested, user-approved или deployed.
- Application `main` не изменялся; merge и Netlify Deploy не выполнялись.

## Ежедневная проверка — 17 ноября 2026 года, 09:25 (Europe/Berlin)

- Выполнена read-only сверка GitHub branches, commits, compare, PR #3, reviews/comments, commit status/check-runs, исходников application main/integration и отдельного Preview repo.
- Новых коммитов в application repo после проверки 16 ноября не обнаружено. Branch refs: `main` — `2291e55a513eadb6ff00b7011cfc74d9b25ef947`; `feature/map-navi-integration-2026-11-15` — `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; compare — 4 ahead / 0 behind, изменены `index.html` и `sw.js`. Файловые blob SHA: main `index.html` `59e4db3c19d2380a4f18d58b38270426e45d956e`, integration `index.html` `1e0b3ebc346897a862305eeb38b7b968bece0d88`; main `sw.js` `e2ea1a5fb5b54ae20ebb08be70337eda30c90552`, integration `sw.js` `147b50ddcfa78743c3cf9a9d8aadb025ef361fbe`.
- PR #3 остаётся OPEN / UNMERGED, head SHA `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; reviews — 0, comments — 0, commit status — pending / 0 statuses, check-runs — 0. Deploy Preview URL не подтверждён.
- Кодовая сверка: GPS Follow / Free View и `↻ Follow` есть в integration branch только для основной карты `leafletMap`; Pharmacy / Toilets / Reset controls есть в integration code для основной и Christmas/market map; POI camera priority и сохранение выбранного POI до первого GPS fix есть в commit `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`. Это code-present, не Preview-tested.
- Базовый `_zoomToNearestPoi` уже находится в application main. Более поздние Preview fixes: POI centering `57408beb2725da53bb834ab1b2a1b79c40c37327`, toast action focus `a1ea99e4d3b6bd0b00f6d26e096b6ec46f8c6ca5`; search/ticker `db9f392fd3f0c9db9dfac3ef17117cc813fb3e5d`, mobile search width `6d6a9bfc9e6ce1fb9e5bc7477411d69a2de03490`, toast/stacking `fc0078a47885d1aadec066e81067b5e43f9fdfb6`, market zoom `b27c044a58f2a2ba9a807cb8af856d373841b62a`. Эти изменения остаются в отдельном Preview repo и не перенесены в PR #3.
- Отдельный Preview repo: latest commit `a1ea99e4d3b6bd0b00f6d26e096b6ec46f8c6ca5`; GitHub Actions Pages workflow run `43725058073` завершился success 15 ноября 2026 года. Это подтверждает успешный workflow отдельного Preview repo, но не интеграционной ветки. В его `index.html` присутствует `<base href="https://turrettales.de/">`; опубликованная страница через текущий web-check недоступна. Не отмечать как Preview-tested.
- PR #3 user approval отсутствует: GitHub reviews и комментарии пусты; отдельное подтверждение тестирования пользователем не зафиксировано. Live Netlify status, branch settings и deployed commit проверить через доступные GitHub-данные не удалось. Успешный GitHub Pages run application main от 14 ноября не является доказательством Netlify Deploy.
- По стадиям: **перенесено в integration branch** — GPS Follow/Free View/manual recenter, Pharmacy/Toilets/Reset, POI camera-priority/pending first fix; **Preview-tested** — ничего не подтверждено для PR #3; **user-approved** — ничего не подтверждено; **deployed to Netlify** — не подтверждено. POI auto-focus базового уровня уже есть в main, но улучшенное центрирование/toast focus не перенесено.
- План на 17 ноября (10:00–13:00 controls; 14:00–16:00 POI) остаётся окном проверки/доработки, не считается выполненным: кодовые изменения уже в integration branch, но проверка заблокирована отсутствием подтверждённого PR #3 Preview. Следующий шаг — получить доступный Preview именно этой ветки; затем проверить iPhone/iPad и только после этого отмечать соответствующие стадии.
- Предыдущий Project Map workflow: run `43830140691` завершился success на commit `e4fb8516547b5976ba7b09ca408ec952b1c33ff5`. После сегодняшнего обновления Project Map Pages workflow run `44047129419` также завершился success на commit `6c86de1a8770320769e0ab1561cb32fffdeac201` (17 ноября, 09:29 Europe/Berlin). Сам опубликованный URL не удалось независимо открыть текущим web-check; подтверждён именно успешный GitHub Pages workflow.
- Защита production соблюдена: application `main` не изменялся; merge и Netlify Deploy не выполнялись.


## Ежедневная проверка — 18 ноября 2026 года, 09:16 (Europe/Berlin)

- Выполнена read-only проверка актуальных веток, PR, commit comparisons, изменённых файлов, review/comments, commit statuses и workflow runs. Application repository доступен; Preview URL для новой интеграционной ветки не подтверждён.
- Application `main` остаётся на `2291e55a513eadb6ff00b7011cfc74d9b25ef947`. Сравнение `main` → `feature/map-navi-integration-2026-11-15`: 4 commits ahead / 0 behind; изменены `index.html` и `sw.js`. PR #3 открыт, не слит; reviews/comments отсутствуют; commit statuses и PR workflow runs отсутствуют.
- Обнаружена новая ветка `feature/map-navi-stabilized-integration-2026-11-17`, head `8beefcecc1e6c5d2db5fc32e7d9f5bf58cf1a2ca`. Она основана на integration branch `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; GitHub compare подтверждает 10 commits ahead / 0 behind integration и 14 commits ahead / 0 behind application main. В сравнении с integration изменён только `index.html`; при сравнении с main изменены `index.html` и `sw.js`. PR #6 открыт в draft, base — integration branch, head — stabilized integration branch; PR #6 не слит, mergeable=true. В PR body указано 7 commits ahead, но актуальный compare показывает 10; для статуса использовано значение compare.
- PR #6 включает Reset state cleanup: удаление слоёв аптек/туалетов, очистку pending POI/toast/detail state, возврат полного охвата карты при активном GPS без отключения GPS, отключение Follow с показом кнопки возврата, подавление немедленного повторного nearest-castle toast. Также включён Popup Manager: единые правила допуска/закрытия окон, подавление автоматических приглашений Food/Shop/POI, Guided Tours по входу в релевантный раздел не чаще одного раза за сессию для каждого раздела; срочный POI, чтение объекта, modal и активный маршрут блокируют автоматические предложения.
- Подтверждённые коммиты PR #6: `eac76bad54ba8aac1d448ad0550669c8781ae256` (Reset focus/POI cleanup); `2811ded019426dcfd89aebfec93a848d3e9530ff` (full-map view after Reset); `3762877c7a17b8abafb4bbb8b541c7e41268548f` (clear GPS Follow on Reset); `f8a14b7199a3a076267440f3ebb2163684fd26aa` (prevent Reset toast reappearing during GPS refresh); `a4179b5bdfe6efee2a28f4747fd515ea902d1a10` (allow later nearest-place notices); `ae8285b91cf13644c2bc3fd84c61aef90231450e` (Popup Manager integration); `39836e1c83920bdb78fefac2810fde8b0daa0d05` (contextual tour offer); `397a92c5a5b1f6ccc032a76319dc425f09d9407d` and `d8f16462c1a2016cf75b0ad3da1fb94025c1bcb3` (two syntax fixes in Christmas map controls); `8beefcecc1e6c5d2db5fc32e7d9f5bf58cf1a2ca` (more Christmas map screen space and controls placed on map).
- PR #6 также меняет Christmas map mobile layout: map stage, height, search placement/width relative to GPS button, horizontal scrolling for language and chip rows. Это подтверждено diff, но не является переносом полного отдельного Preview пакета search/ticker/overlay/mobile. Search/ticker/legend commits `db9f392` / `6d6a9bf`, visual toast/z-index `fc0078a`, market zoom `b27c044`, POI centering/toast-action focus `57408be` / `a1ea99e` не подтверждены как перенесённые в PR #6.
- PR #6 body сообщает о focused Reset harness 6/6, Popup Manager harness 6/6, tour-context checks и static syntax checks для script blocks 1–3 и 5–7. Эти результаты являются заявлением в PR description; независимо повторить harness по доступным изменённым файлам не удалось. В том же PR body указано, что main inline script block 4 имеет parse failure, совпадающий с integration base; это не новая ошибка PR #6, но остаётся требующим разрешения/проверки риском. Изменённый PR #6 file list содержит только `index.html`.
- PR #6: 0 reviews, 0 comments, commit status — 0 statuses, PR workflow runs — 0. PR #4 (Popup Manager) и PR #5 (Reset cleanup) остаются отдельными open/draft PR; PR #6 — комбинированная ветка поверх integration. PR #3 также остаётся open/unmerged.
- По стадиям: **перенесено в integration PR #3** — GPS Follow/Free View/manual recenter, Pharmacy/Toilets/Reset, POI priority/pending first fix; **добавлено в отдельный draft PR #6** — Reset state cleanup, Popup Manager, частичная Christmas map layout и функциональная toast/modal координация; **Preview-tested** — для PR #3/#6 не подтверждено; **user-approved** — не подтверждено; **Netlify deployed** — не подтверждено. Базовый POI auto-focus существует в main, улучшенное центрирование из отдельного Preview repo не перенесено.
- Отдельный `turret-tales-preview` остаётся отдельным репозиторием; его `index.html` blob SHA `e71805721241ce148b9eca22f8bf78b6e078144b` содержит `<base href="https://turrettales.de/">`. Его GitHub Pages build не доказывает Preview интеграционной ветки. Live Netlify branch/deployed commit по доступным данным не подтверждён.
- Ближайший блокер: получить настоящий Preview URL для PR #6 или PR #3 и провести runtime/device test; отдельно проверить/разобрать parse failure script block 4, прежде чем считать интеграцию готовой. Сегодняшнее запланированное окно переноса начинается в 10:00; на момент проверки оно ещё не началось.
- Application `main` не изменялся; merge, Netlify Deploy и публикация приложения не выполнялись.
- Project Map audit records committed: tracker update `a274963b52d42b05c4f341dc1dbe9f43c9d7125d`; dashboard data `6a9d02f25779fb3132b36d3ab23217a1ab84d09d`; release-plan page `4cdc5737fa4021aeb3e62476a33e2e5c82cae388`. GitHub Pages workflow run `44265994360` for the Project Map completed with conclusion `success` on commit `4cdc5737fa4021aeb3e62476a33e2e5c82cae388`. Direct HTTP verification of the published Pages URL was unavailable through the current page checker; workflow success is confirmed, independent visual rendering is not.


## Ежедневная проверка — 19 ноября 2026 года, 09:34 (Europe/Berlin)

### GitHub: актуальные ветки и PR

- Application `main` не изменился: commit `2291e55a513eadb6ff00b7011cfc74d9b25ef947`; blob `index.html` — `59e4db3c19d2380a4f18d58b38270426e45d956e`, `sw.js` — `e2ea1a5fb5b54ae20ebb08be70337eda30c90552`.
- Integration `feature/map-navi-integration-2026-11-15`: `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`, 4 commits ahead / 0 behind `main`; PR #3 открыт, не объединён.
- Stabilized integration `feature/map-navi-stabilized-integration-2026-11-17`: текущий HEAD `4c0d6d28c413fbc0d255cedef03091183837d188`; GitHub compare подтверждает 13 commits ahead / 0 behind integration и 17 ahead / 0 behind `main`. По сравнению с integration изменён только `index.html` (+364/−110); по сравнению с `main` изменены `index.html` (+435/−122) и `sw.js` (+13/−11). Blob `index.html` — `ee4145a5a79eb273fca9b3c435edf18087e51d64`, `sw.js` — `147b50ddcfa78743c3cf9a9d8aadb025ef361fbe`.
- PR #6 остаётся open/draft, base — integration, head — `4c0d6d28...`; 0 reviews, 0 comments, 0 check-runs и 0 commit statuses. Дополнительная ветка `fix/map-navi-xmas-poi-reset-2026-11-19` указывает на тот же SHA `4c0d6d28...`, отдельного нового коммита не добавляет. PR #4 и #5 остаются отдельными open/draft; PR #2 и #3 открыты и не объединены; PR #1 закрыт без merge.

### Код, подтверждённый чтением текущего `index.html` PR #6

- **GPS Follow / Free View / manual recenter:** `gpsFollowMode`, `gpsFollowBtn`, `leaveGpsFollowMode`, обработчики `dragstart` и `zoomstart`, возврат к последним GPS-координатам присутствуют на основной карте `leafletMap`. На Christmas/market map есть отдельные `xmasGpsWatch`/`xmasGpsPos` и первоначальное кадрирование по GPS, но нет отдельного Follow/Free View и кнопки ручного возврата. Перенос Follow на эту карту не подтверждён.
- **Pharmacy / Toilets / Reset controls:** три кнопки присутствуют на обеих картах. На основной карте `resetRhineMap` очищает POI layers, состояния кнопок, pending focus, уведомления и выбранную карточку, оставляя GPS активным и переводя камеру в Free View. На Christmas map `xResetBtn` только восстанавливает bounds/view; очистка активных POI layers и уведомлений этим обработчиком не выполняется. Полный Reset на обеих картах не завершён.
- **POI auto-focus:** `_zoomToNearestPoi` и marker click focus присутствуют; на основной карте запрос сохраняется до первого GPS fix. На Christmas map первый GPS fix повторно фокусирует активный POI. Отдельный helper `_focusPoiOnMap` и флаг `_poiFocusActive` из `turret-tales-preview` в приложение не перенесены.
- **POI camera priority / map focus:** commit `4c0d6d28` принудительно центрирует выбранный castle marker/search result (zoom не ниже 14), скрывает конкурирующие castle distance/route/toast элементы при активном Pharmacy/Toilets mode и не позволяет GPS обновлениям незаметно менять выбранный guide/story.
- **Popup / toast:** центральный `PopupManager` и контекстные правила есть в PR #6; визуальные toast positioning/z-index исправления из отдельного Preview repo не подтверждены в приложении.
- **Search / ticker / overlay / mobile / zoom:** PR #6 содержит частичную компоновку Christmas map (search и GPS над картой), изменения размеров GPS panel и GPS halo. Полный пакет search/ticker/legend, отдельный mobile-width fix, visual toast/z-index и market zoom-control fix из Preview repo не перенесён. Эти изменения нельзя считать Preview-tested.

### Проверки и Preview

- PR #6 body заявляет Reset harness 6/6, Popup Manager harness 6/6, tour-context harness и статические syntax checks для script blocks 1–3 и 5–7. Это результаты, заявленные автором PR; независимо воспроизвести их не удалось. В том же описании сообщается о прежней parse failure в inline script block 4, присутствовавшей в integration base; это требует отдельной проверки.
- Для текущего PR #6 GitHub возвращает 0 check-runs и 0 statuses; браузерный runtime test и тесты на iPhone/iPad не подтверждены.
- Отдельный `turret-tales-preview` остаётся на `a1ea99e4d3b6bd0b00f6d26e096b6ec46f8c6ca5`; Pages workflow run `43725058073` завершился success 15 ноября. Его `index.html` содержит `<base href="https://turrettales.de/">`; это не независимый Preview PR #3/#6. Прямое открытие Pages URL через доступные средства проверки не удалось.
- User approval не подтверждено. Netlify deployed commit/live status проверить не удалось; в PR #6 нет CI/deployment status. Не отмечать как deployed.

### Сроки и ближайший блокер

- На момент проверки 09:34 рабочее окно 19 ноября 10:00–12:00 ещё не началось; следующее окно — 13:00–15:00. Интеграционный Preview URL отсутствует, поэтому фактические runtime/device tests заблокированы.
- Freeze остаётся 23–24 ноября; пользовательский Netlify Deploy — не позднее 25 ноября; live-проверка — 26 ноября; первая экскурсия — 27 ноября.
- Ближайшие блокеры: получить Preview именно PR #6/интеграционной ветки; проверить script block 4; завершить Reset cleanup Christmas map; решить Follow/Free View для market map; перенести оставшиеся search/ticker/overlay/mobile/zoom fixes.
- Application `main` не менялся; merge и Netlify Deploy не выполнялись.



## Ежедневный аудит — 20 ноября 2026 года, 09:52 (Europe/Berlin)

### Подтверждённые ветки и Pull Requests
- Application `main`: `2291e55a513eadb6ff00b7011cfc74d9b25ef947`, без изменений.
- Integration `feature/map-navi-integration-2026-11-15`: `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; PR #3 открыт, не объединён.
- Stabilized integration `feature/map-navi-stabilized-integration-2026-11-17`: `4c0d6d28c413fbc0d255cedef03091183837d188`; PR #6 открыт в Draft; compare подтверждает 13 ahead / 0 behind integration и 17 ahead / 0 behind main.
- Новая candidate branch `feature/map-navi-poi-pulse-states-2026-11-19`: HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439`; compare подтверждает 33 ahead / 0 behind integration и 20 ahead / 0 behind PR #6. Изменены `index.html` и `sw.js`; blob SHA: `index.html 43cc9949a104b06ad02e177a9eca0a1d7f9332bd`, `sw.js 5fdf2b838a0a4fbd95e9b58fce079084e08d900d`. Для этой ветки отдельного PR нет.
- PR #4 (Popup Manager) и PR #5 (Reset cleanup) остаются открытыми Draft. PR #6 объединяет соответствующие изменения поверх integration.
- У PR #6 body не обновлён относительно числа commits ahead: в body сказано 7, актуальный compare API возвращает 13.

### Что найдено в новой candidate branch
- **GPS Follow / Free View / manual recenter:** отдельные режимы и возврат к текущим GPS-координатам присутствуют в коде основной, Christmas и winery maps. Ручные drag/zoom переводят соответствующую карту в Free View; programmatic moves защищены от ложного переключения.
- **POI focus priority:** общая модель намерений карты различает follow, free, selected, search, POI и overview; отложенный POI-запрос сохраняется до первого GPS fix. Приоритет POI не должен уступать фоновому обновлению GPS.
- **Pharmacy / Toilets / Reset:** кнопки присутствуют на основной и Christmas maps. Reset основной карты очищает POI layers, pending focus, уведомления и выбор; Christmas Reset также удаляет POI layers/target marker, очищает состояния кнопок и возвращает полный охват. Это кодовый аудит, не runtime test.
- **POI visual states:** есть состояния request/waiting/failed, пульсация кнопок и маркеров; в коде также есть отдельный target halo.
- **Carousel:** commit `8eb777684e0b9f778e5d6034102e0253c312bf21` добавляет нижнюю горизонтальную карусель на основную карту. Tap по карточке открывает детали и центрирует/приближает объект; прокрутка выбирает ближайшую к центру карточку и синхронизирует выбор карты. Текущий `renderMapCarousel()` строит список из `castles` (замки/города); переключение содержимого на аптеки, туалеты, My Ship и другие POI-категории не подтверждено.
- **Search / ticker / overlays / mobile:** новая ветка содержит общую работу с фокусом, Christmas map layout, search/GPS overlay, меньшую GPS-панель, PopupManager и предотвращение конкурирующих overlays. Полный перенос точечных Preview fixes `db9f392`, `6d6a9bf`, `fc0078a`, `b27c044` не подтверждён; отдельный market zoom fix остаётся непроверенным.

### Четыре независимых статуса
| Функция | Перенесено в candidate branch | Preview-tested | User-approved | Netlify deployed |
|---|---|---|---|---|
| GPS Follow / Free View / manual recenter | Да, main + Christmas + winery maps | Нет | Требования согласованы; текущая сборка не одобрена | Не подтверждено |
| Pharmacy / Toilets / Reset | Да, main + Christmas; полный Reset в коде | Нет | Требования согласованы; текущая сборка не одобрена | Не подтверждено |
| POI auto-focus / camera priority | Да, main + Christmas; shared intent across map variants | Нет | Требования согласованы; текущая сборка не одобрена | Не подтверждено |
| Search / ticker / overlay / toast / zoom / mobile | Частично; отдельные Preview refinements не подтверждены | Нет | Нет для текущей сборки | Не подтверждено |
| Нижняя swipeable carousel | Да, основная карта; commit `8eb777684e0b9f778e5d6034102e0253c312bf21` | Нет | Концепция согласована; реализация не одобрена | Не подтверждено |

### Preview и автоматические проверки
- Отдельный `basana/turret-tales-preview` main: `e11b9997d4c589e08e83760f6ff4e571677e7818`; GitHub Pages workflow `44623470587` завершился success 19 ноября 2026 года в 21:54:45 UTC. Это подтверждает публикацию отдельного Preview repo на Pages, но не сборку новой candidate branch.
- Preview `index.html` blob `939fc72ab99199f07ef9f88faf78accf77d481d3` всё ещё содержит `<base href="https://turrettales.de/">`; присутствуют `_focusPoiOnMap`, Christmas map stage и Follow UI, но `map-carousel` отсутствует. `sw.js` blob `5cb1f25b2a2900c23faed60a1ff1c11a6ad92275` ограничивает обработку своим Preview path. Следовательно, это не независимый Preview candidate branch.
- PR #6 commit `4c0d6d28`: 0 check-runs; для candidate commit `80f542b3`: 0 check-runs и 0 statuses. GitHub workflow runs по candidate PR отсутствуют, поскольку PR для неё не создан.
- Доступный браузерный инструмент не смог открыть Preview и production URL. Netlify deployment commit и фактический live статус проверить не удалось.
- Harness 6/6 и статические проверки остаются только заявлениями в PR #6 body; независимо они не воспроизведены. Ошибка script block 4 отмечена в PR #6 как pre-existing; устранение в candidate branch отдельно не подтверждено.

### Сроки, блокеры и безопасность
- 20–22 ноября — интеграция, Preview и тестирование; на 09:52 сегодняшние окна 10:00–12:00 и 13:00–15:00 ещё не начались.
- 23–24 ноября — freeze.
- Не позднее 25 ноября — пользовательский Deploy в Netlify.
- 26 ноября — проверка live.
- 27 ноября — первая экскурсия.
- Главный блокер: новая, более полная candidate branch пока не оформлена в PR и не имеет Preview/checks; тесты на iPhone/iPad и пользовательское одобрение отсутствуют. Перед freeze нужно выбрать один кандидат, получить доступный Preview и пройти реальные сценарии.
- Действие пользователя сегодня не требуется немедленно; для завершения проверки понадобится открыть именно candidate build на iPhone и iPad после появления Preview.
- Application `main` не изменялся; merge не выполнялся; Netlify Deploy не запускался.


## Ежедневная проверка — 21 ноября 2026 года, 09:35:51 (Europe/Berlin)

### 1. Application repository: актуальный main и рабочие ветки

- Текущий application main: `212334d45d04e1021270e8a9854c0b771ee7dfbc` (20 ноября, 17:23:41 UTC). GitHub показывает один изменённый файл — `Rahmen KO kurz.webp`, добавленный через upload. Это asset-only commit: `index.html` остаётся blob `59e4db3c19d2380a4f18d58b38270426e45d956e`, `sw.js` — `e2ea1a5fb5b54ae20ebb08be70337eda30c90552`; изменения логики приложения в main не обнаружены.
- Integration `feature/map-navi-integration-2026-11-15`: HEAD `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; PR #3 открыт, не объединён. Его base SHA — прежний main `2291e55a513eadb6ff00b7011cfc74d9b25ef947`; GitHub сейчас возвращает `mergeable=false`. Не трактовать это автоматически как доказанный конфликт: требуется повторная проверка после обновления base. Сравнение с текущим main: 4 commits ahead / 1 behind; отставание связано с asset-only commit `212334d45`.
- Stabilized integration `feature/map-navi-stabilized-integration-2026-11-17`: HEAD `4c0d6d28c413fbc0d255cedef03091183837d188`; PR #6 открыт в Draft, base `f29ad217`, head `4c0d6d28`, 13 commits, GitHub `mergeable=true`. PR #6 не содержит более новую candidate-реализацию.
- Candidate `feature/map-navi-poi-pulse-states-2026-11-19`: HEAD по Git refs остаётся `80f542b3d7a5c51123ff9b129b0d59374762d439`. Сравнение: 33 commits ahead / 0 behind integration; 20 ahead / 0 behind PR #6; относительно текущего main — 37 ahead / 1 behind. Единственный behind commit main — добавление файла `Rahmen KO kurz.webp`; candidate не содержит этот asset commit. Ветка меняет `index.html` и `sw.js`; отдельного PR нет.
- Для candidate commit `80f542b3` GitHub возвращает 0 commit statuses и 0 PR-triggered workflow runs. Нет PR, нет подтверждённого Deploy Preview именно этой ветки.

### 2. Дополнительные рабочие ветки — отдельно от release candidate

- `map-navi-poi-persistence-and-focus`, HEAD `7d1a4ac6979660d8d343fbf0d4d468d2a318236a`, 2 commits ahead / 0 behind current main, без PR. Предыдущий commit `259d2fa7044fe2ef6910049469f5eeb425b783c3` добавляет `_fitActivePoiAndUser`: Reset при активном Pharmacy/Toilets должен кадрировать пользователя и ближайший активный POI; GPS pan при активном POI подавляется, чтобы не уводить цель из кадра. Последний commit `7d1a4ac` только добавляет новое фото в Centralplatz gallery. Эти изменения не входят в candidate `80f542b3`.
- `map-navi-my-ship-panel-fix`, HEAD `3c6cc68c30940e96ba70f321754baffd5815255d`, 3 commits ahead / 0 behind main, без PR. Commit `3c6cc68` уменьшает кнопки карты с 56×56 до 42×42 px, уменьшает расстояние и меняет reset glyph на `⤢`. Это отдельная альтернатива, не включённая в candidate и не одобренная/проверенная на устройствах.
- `map-navi-ship-time-and-map-controls`, HEAD `38c8f0dbc72b650f66569969def65476d8c59c91`, 1 commit ahead / 0 behind main, без PR. Перестраивает ship controls / departure-time panel и также уменьшает кнопки до 42×42 px. Не включена в candidate; не считать частью релизной интеграции.

### 3. Отдельный Preview repo — новые изменения 20 ноября

- `basana/turret-tales-preview` main: HEAD `52c0f3f6367267ede619cc5f896c5c24df99645e`; `index.html` blob `39f8d18636c2cb58b9e6f67b3253fb8b4b087f9a`, `sw.js` blob `23cd26581242dfc9667384d0a2c5c680ab47cbb5`.
- GitHub Pages workflow run `44777266157` (`pages build and deployment`) завершился `success` 20 ноября 2026 года, 16:50:20 UTC. Предыдущий run `44777250490` для commit `8ca039a` завершился `cancelled`; последующий run для `52c0f3` успешен.
- В Preview repo подтверждены отдельные изменения: `6d89650d99312df6bf2f57327434e66359621365` — поиск Christmas map с autocomplete после 3 символов, явным списком результатов и input 16px/44px для предотвращения iPhone zoom; `0dc8656275eca50dc8d3f9a014263f78b7d44229` — повторный tap по выбранному рынку открывает карточку/прокручивает к ней, а Christmas GPS Follow остаётся доступен после выбора рынка и GPS fix; `8ca039a60af88e63a0e65af62b67626c63fddd5d` — нормализация введённого времени HHMM в HH:MM, сохранение в localStorage и защита от iPhone auto-zoom. `52c0f3f` обновляет только Service Worker cache version до v7.
- Preview `index.html` по-прежнему содержит `<base href="https://turrettales.de/">`; carousel отсутствует. Это отдельный Preview shell, не candidate branch `80f542b3`. Pages workflow success подтверждает публикацию GitHub Pages, но не браузерный runtime test. Прямое открытие `https://basana.github.io/turret-tales-preview/` через доступный web checker вернуло недоступность; iPhone/iPad test и пользовательское одобрение не подтверждены.

### 4. Функциональная матрица — четыре независимые стадии

| Функция | Перенесено в candidate `80f542b3` | Preview/runtime-tested | User-approved (текущая сборка) | Netlify deployed |
|---|---|---|---|---|
| GPS Follow / Free View / manual recenter | Да, код на main, Christmas и winery maps | Нет; отдельный Preview repo содержит Christmas Follow fixes, но не candidate build | Нет | Не подтверждено |
| Pharmacy / Toilets / Reset controls | Да, кнопки на main и Christmas; полный Reset cleanup в коде обеих карт | Нет | Нет | Не подтверждено |
| POI auto-focus / camera priority | Да, shared focus intent и pending first GPS fix; отдельная ветка `259d2fa` содержит дополнительный Reset/POI focus helper | Нет | Нет | Не подтверждено |
| Search / ticker / overlay | Не полностью; полный Preview search/ticker/stacking пакет не перенесён | Отдельный Preview Pages build опубликован; runtime не проверен | Нет | Не подтверждено |
| Toast / zoom / mobile fixes | Частично; точные Preview fixes не подтверждены в candidate | Отдельный Preview содержит toast/search stacking, market zoom placement и iPhone input zoom fixes | Нет | Не подтверждено |
| Нижняя swipeable carousel | Да, только основная карта; пока castle/town items, без подтверждённой динамической замены POI categories | Нет; в отдельном Preview carousel отсутствует | Концепция согласована ранее, реализация не одобрена | Не подтверждено |

### 5. Тесты, блокеры и сроки

- Ни для candidate `80f542b3`, ни для PR #6 нет подтверждённых GitHub status checks/workflow runs. Harness 6/6 в PR #6 остаются заявлениями в PR body, независимо не воспроизведены. Browser/device tests на iPhone и iPad не зафиксированы.
- Отдельный Preview Pages build опубликован успешно, но это не candidate build и прямое открытие Preview через web checker не удалось. Поэтому не ставить `Preview-tested`.
- Основные блокеры: candidate не оформлена PR и не имеет своего Preview; ветки расходятся; current main получил один asset-only commit, поэтому candidate теперь 37 ahead / 1 behind; PR #3 базируется на прежнем main и GitHub возвращает `mergeable=false`; search/ticker/overlay/mobile refinements остаются в отдельном Preview repo; dynamic POI carousel categories не подтверждены.
- Дополнительные side branches по POI focus и My Ship controls не включены в candidate; не переносить их автоматически без сверки diff. В частности, уменьшение controls до 42×42 px требует отдельного визуального решения.
- Проверка выполнена в 09:35:51; запланированное окно 21 ноября 10:00–12:00 ещё не началось. Следующее окно 22 ноября — полный повторный тест. Freeze остаётся 23–24 ноября; пользовательский Netlify Deploy — не позднее 25 ноября; live check — 26 ноября; первая экскурсия — 27 ноября.
- Действие пользователя немедленно не требуется. Для завершения release проверки всё ещё нужны candidate Preview и реальные проверки на iPhone/iPad; текущая сборка не одобрена.
- Application main не изменялся в рамках этой проверки; merge не выполнялся; Netlify Deploy не запускался.

---

## Фактическая проверка 22 ноября 2026 года, 09:09:24 (Europe/Berlin)

### 1. Application repository и release candidate

- Application `main`: HEAD `212334d45d04e1021270e8a9854c0b771ee7dfbc`. Коммит добавил только `Rahmen KO kurz.webp`; подтверждённые blob SHA кода не изменились: `index.html` `59e4db3c19d2380a4f18d58b38270426e45d956e`, `sw.js` `e2ea1a5fb5b54ae20ebb08be70337eda30c90552`. GitHub Pages workflow #44782881075 завершился success; это не подтверждение Netlify deployment.
- Candidate `feature/map-navi-poi-pulse-states-2026-11-19`: HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439`; `index.html` blob `43cc9949a104b06ad02e177a9eca0a1d7f9332bd`, `sw.js` blob `5fdf2b838a0a4fbd95e9b58fce079084e08d900d`.
- Актуальные compare: 33 commits ahead / 0 behind integration `f29ad217`; 20 ahead / 0 behind PR #6 `4c0d6d28`; относительно current main — 37 ahead / 1 behind. Единственный behind commit — asset-only `212334d45`; функциональный код main и candidate расходится по содержимому index.html/sw.js.
- У candidate нет PR. Для HEAD `80f542b3`: check-runs = 0; commit statuses = 0 (GitHub aggregate state `pending`, total_count 0); PR-triggered workflow runs = 0. Собственного Deploy Preview нет.

### 2. Проверка функций по исходному коду candidate

| Функция | Что подтверждено в коде | Runtime / device test |
|---|---|---|
| GPS Follow / Free View / manual recenter | Основная карта: `gpsFollowMode`, `gpsFollowBtn`, ручные drag/zoom переводят камеру в Free View. Christmas map: отдельные `xmasFollowMode`, `xmasFollowBtn`, `setXmasMapIntent`. Wine map: `wineMapTools()` создаёт собственные Follow и Reset controls; drag/zoom переключают собственный `wineFollowMode`. | Не подтверждён |
| Pharmacy / Toilets / Reset | Pharmacy и Toilets присутствуют на основной и Christmas maps. Wine map имеет отдельные search/GPS/Follow/Reset controls, но не общий Pharmacy/Toilets POI bar. | Не подтверждён |
| Полный Reset | `resetRhineMap()` удаляет POI layers, очищает pending focus/toasts/selection и возвращает общий обзор; Christmas `xResetBtn` удаляет обе POI layers, сбрасывает состояния кнопок, target marker, уведомления и возвращает исходные bounds/view. | Не подтверждён |
| POI auto-focus / camera priority | `_zoomToNearestPoi()` использует GPS position, запоминает запрос до первого GPS fix, при активном POI приостанавливает Follow и кадрирует пользователя вместе с ближайшим POI. В коде предусмотрены основная и Christmas maps. | Не подтверждён |
| Нижняя карусель | `renderMapCarousel()` формирует карточки из замков и городов; tap выбирает объект, scroll выбирает ближайшую к центру карточку. Динамическая замена на Pharmacy/Toilets/My Ship не подтверждена. | Не подтверждён |

### 3. PR и отдельный Preview repository

- PR #3: open, unmerged; head integration `f29ad217`, base `main`; текущий GitHub fetch_pr возвращает `mergeable=true`. Это уточняет противоречивую запись предыдущего аудита от 21 ноября, где было указано `mergeable=false`.
- PR #6: open, Draft, unmerged; head `4c0d6d28`, base integration `f29ad217`, GitHub `mergeable=true`. PR #4/#5 остаются open Draft; PR #2 open.
- Отдельный `basana/turret-tales-preview`: main HEAD `bd7dc83f949c26149c4f3b068266515244fc2a4b`; `index.html` blob `bf307ff0662966618787dfe41b6fa480a4299184`, `sw.js` blob `23cd26581242dfc9667384d0a2c5c680ab47cbb5`. Сравнение с предыдущим HEAD `52c0f3f`: 3 commits ahead / 0 behind.
- Новый функциональный commit Preview `5960ea4b424d52425d5ba2300c2457b2da67cb48` изменяет только тексты подсказок о карте рынков на DE/FR/NL/EN/RU/ZH/HE: три раздела — Explore the map, Find your way, Keep track of your ship. Два остальных новых commits — загрузки файлов/изображений; последний `bd7dc83` добавляет `2 экран.jpg`.
- Pages workflow #44952056944 для Preview HEAD `bd7dc83` завершился success. В Preview `index.html` по-прежнему указан `<base href="https://turrettales.de/">`; это отдельный shell, не сборка candidate `80f542b3`. Успешный Pages build не подтверждает browser runtime или iPhone/iPad test. Прямой доступ к опубликованной странице через web checker не получен.

### 4. Четыре стадии готовности

| Функция | Перенесено в candidate | Preview-tested (candidate) | User-approved (current build) | Netlify deployed |
|---|---|---|---|---|
| GPS Follow / Free View / manual recenter | Да, main / Christmas / wine maps | Нет | Нет | Не подтверждено |
| Pharmacy / Toilets / Reset | Да, main / Christmas; отдельный wine-map Reset | Нет | Нет | Не подтверждено |
| POI auto-focus / camera priority | Да, main / Christmas | Нет | Нет | Не подтверждено |
| Search / ticker / overlay | Частично; отдельные search/ticker элементы есть в candidate, полный пакет Preview fixes не перенесён | Нет | Нет | Не подтверждено |
| Toast / zoom / mobile fixes | Частично; отдельные стили и состояния присутствуют, полный перенос отдельных Preview fixes не подтверждён | Нет | Нет | Не подтверждено |
| Carousel | Да, main map; пока castles/towns | Нет | Концепция согласована ранее, текущая реализация не одобрена | Не подтверждено |

### 5. Блокеры и календарь

- Главный блокер на 22 ноября: candidate `80f542b3` не имеет собственного PR/Preview и не имеет CI checks. Без Preview нельзя подтвердить runtime, мобильную компоновку, GPS/POI поведение и карусель.
- Отдельный Preview repository не заменяет candidate Preview: он ссылается на production через `<base>` и содержит другую версию кода.
- Сегодняшнее рабочее окно полного повторного теста запланировано на 10:00–12:00; аудит в 09:09 выполнен до начала окна, поэтому тест не отмечается выполненным.
- Freeze: 23–24 ноября; пользовательский Netlify Deploy — не позднее 25 ноября; live check — 26 ноября; первая экскурсия — 27 ноября.
- Требуется действие пользователя/проекта до freeze: обеспечить Preview именно candidate `80f542b3` и провести проверку на iPhone/iPad. Текущая сборка не одобрена.
- Доступные GitHub данные не подтверждают Netlify deployment; GitHub Pages workflow приложения и Preview не являются Netlify release.
- Application `main` в рамках проверки не изменялся; merge не выполнялся; Netlify Deploy не запускался.


---

## Фактическая проверка 23 ноября 2026 года, 10:24:33 (Europe/Berlin)

### 1. Application repository и candidate

- Application `main`: HEAD `212334d45d04e1021270e8a9854c0b771ee7dfbc`. Новых коммитов после asset-only изменения 21 ноября не обнаружено; по последней подтверждённой проверке кодовые blobs `index.html` `59e4db3c19d2380a4f18d58b38270426e45d956e` и `sw.js` `e2ea1a5fb5b54ae20ebb08be70337eda30c90552` остаются прежними. Application main в рамках этой проверки не изменялся.
- Candidate `feature/map-navi-poi-pulse-states-2026-11-19`: HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439`; последний commit датирован 19 ноября 2026 года, 09:11:50 UTC. Новых commits candidate после 19 ноября не обнаружено. Файлы: `index.html` blob `43cc9949a104b06ad02e177a9eca0a1d7f9332bd`; `sw.js` blob `5fdf2b838a0a4fbd95e9b58fce079084e08d900d`.
- GitHub compare: candidate на 37 commits впереди / 1 позади current main; 33 впереди / 0 позади integration `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; 20 впереди / 0 позади stabilized PR #6 branch `4c0d6d28c413fbc0d255cedef03091183837d188`. Единственный commit позади main — asset-only commit; compare показывает изменения только в `index.html` и `sw.js`.
- Candidate по-прежнему не имеет Pull Request. Для SHA `80f542b3`: check-runs = 0; commit statuses total_count = 0, aggregate state `pending`. Это отсутствие CI-сигналов, а не успешная проверка.

### 2. PR и связанные ветки

- PR #3: open, unmerged; head `f29ad217`, base ref `main` (зафиксированный base SHA в PR — `2291e55a`, то есть PR не обновлён относительно текущего asset-only main commit). GitHub fetch показывает mergeable=true.
- PR #6: open, Draft, unmerged; head `4c0d6d28`, base integration `f29ad217`; mergeable=true.
- PR #4 и #5 остаются open Draft; PR #2 остаётся open. Ни один из них не представляет candidate HEAD `80f542b3`.
- Отдельные ветки POI persistence/focus и My Ship controls не входят в candidate и не считаются перенесёнными.

### 3. Проверка функций по candidate source

| Функция | Подтверждено в коде candidate | Preview / runtime / device test |
|---|---|---|
| GPS Follow / Free View / manual recenter | Да: основная, Christmas и wine maps; отдельные Follow states/buttons и выход в Free View при ручном drag/zoom | Не подтверждено |
| Pharmacy / Toilets / Reset controls | Pharmacy/Toilets/общая колонка на основной и Christmas maps; wine map имеет собственные search/GPS/Follow/Reset controls, но не общий Pharmacy/Toilets bar | Не подтверждено |
| Полный Reset | Да: основная и Christmas maps; очищаются POI layers, pending focus, временные уведомления/состояния и возвращается обзор | Не подтверждено |
| POI auto-focus / camera priority | Да: основная и Christmas maps; запрос сохраняется до GPS fix, POI intent приостанавливает Follow и удерживает приоритет камеры | Не подтверждено |
| Search / ticker / overlay | Частично: search/ticker присутствуют в candidate; полный перенос отдельного Preview-пакета не доказан | Не подтверждено |
| Toast / zoom / mobile fixes | Частично: есть POI toast/context gating и отдельные layout-правки; точный перенос всех Preview fixes, включая market zoom, не подтверждён | Не подтверждено |
| Нижняя карусель | Да, основная карта; список castle/town. Динамическая замена на Pharmacy/Toilets/My Ship не подтверждена | Не подтверждено |

### 4. Preview и Project Map

- Отдельный Preview repo `basana/turret-tales-preview`: main HEAD `bd7dc83f949c26149c4f3b068266515244fc2a4b`. Последний Pages workflow #91 для этого SHA завершился success: https://github.com/basana/turret-tales-preview/actions/runs/44952056944.
- Это не сборка candidate `80f542b3`. В Preview `index.html` подтверждён `<base href="https://turrettales.de/">`; часть ресурсов указывает на production. Открытие Preview через доступный web browser tool вернуло inaccessible; поэтому browser runtime и iPhone/iPad tests не подтверждены.
- Project Map repo получил документационные commits `2938601d`, `a563c818`, `181e5833` 22 ноября; последний Pages workflow #72 для SHA `181e58330f8d82bb9847fcf89ddc77583ad7a63c` завершился success: https://github.com/basana/map-navi-project-map/actions/runs/45004427319. Прямое открытие опубликованной страницы через доступный browser tool также вернуло inaccessible; API и успешный Pages workflow подтверждают публикацию сборки, но не визуальную проверку.
- Netlify deployed commit / live status не удалось проверить через доступные GitHub данные. GitHub Pages build не является подтверждением Netlify Deploy.

### 5. Четыре стадии готовности

| Функция | Перенесено в candidate | Preview-tested (candidate) | User-approved (current build) | Netlify deployed |
|---|---|---|---|---|
| GPS Follow / Free View / manual recenter | Да, 3 типа карт | Нет | Нет | Не подтверждено |
| Pharmacy / Toilets / Reset | Да, main / Christmas; отдельные wine controls | Нет | Нет | Не подтверждено |
| POI auto-focus / camera priority | Да, main / Christmas | Нет | Нет | Не подтверждено |
| Search / ticker / overlay | Частично | Нет | Нет | Не подтверждено |
| Toast / zoom / mobile fixes | Частично | Нет | Нет | Не подтверждено |
| Carousel | Да, main map; castle/town only | Нет | Нет; согласована только концепция | Не подтверждено |

### 6. Freeze и блокеры

- Freeze начинается 23 ноября и продолжается 24 ноября. На момент проверки candidate не менялся с 19 ноября, не имеет собственного PR/Preview, check-runs или device tests.
- Главный блокер: получить отдельный Preview именно SHA `80f542b3`, проверить его в браузере и на iPhone/iPad, затем зафиксировать одобрение текущей сборки.
- Не считать отдельный Preview repo заменой candidate Preview.
- Требуется также определить один release candidate; параллельные PR #3/#6 и отдельные feature branches не образуют проверенную релизную сборку.
- User Netlify Deploy — не позднее 25 ноября; live check — 26 ноября; первая экскурсия — 27 ноября.
- Требуется действие со стороны разработки/CI: опубликовать candidate Preview. После этого нужна проверка пользователем на iPhone/iPad. Немедленного действия по production от пользователя не требуется.
- Application `main` не изменялся; merge не выполнялся; Netlify Deploy не запускался.


## Daily audit — 24 November 2026, 09:18:03 (Europe/Berlin)

### 1. Current application repository state

Read-only audit of `basana/turret-tales-christmas`.

- Application `main`: `212334d45d04e1021270e8a9854c0b771ee7dfbc`. The latest main commit is dated 20 November 2026 17:23:41 UTC and its message is `Add files via upload`; it adds only `Rahmen KO kurz.webp`. Current `main/index.html` blob remains `59e4db3c19d2380a4f18d58b38270426e45d956e`; no application-code change is present in main.
- Candidate `feature/map-navi-poi-pulse-states-2026-11-19`: HEAD `80f542b3d7a5c51123ff9b129b0d59374762d439`; no newer commit since 19 November. Candidate `index.html` blob `43cc9949a104b06ad02e177a9eca0a1d7f9332bd`; candidate `sw.js` blob `5fdf2b838a0a4fbd95e9b58fce079084e08d900d`.
- GitHub compare: candidate is 37 commits ahead / 1 behind current main (the behind commit is the asset-only upload); 33 ahead / 0 behind integration `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; 20 ahead / 0 behind PR #6 head `4c0d6d28c413fbc0d255cedef03091183837d188`. Candidate diff from main is `index.html` and `sw.js`.
- Candidate still has no Pull Request and no candidate-specific Preview. Its check-runs endpoint returns `total_count=0`; commit status endpoint returns `state=pending` with `total_count=0` and no statuses. This is absence of registered checks, not a passing test.
- PR #3 remains open/unmerged, head `f29ad217`, base main SHA `2291e55a`, mergeable=true. PR #6 remains open Draft/unmerged, head `4c0d6d28`, base integration `f29ad217`, mergeable=true. Neither PR contains candidate HEAD `80f542b3`; PR #2/#4/#5 also remain separate open PRs. The open PR list contains no PR for the candidate.

### 2. Source-level verification of the candidate

The following are confirmed by reading candidate `index.html`; they are not browser/device test results:

- GPS Follow / Free View / manual recenter code is present for the main map, Christmas map and wine map.
- Pharmacy/Toilets controls are present on the main and Christmas maps. The wine map has its own GPS/search/Follow/Reset controls, but not the same Pharmacy/Toilets vertical bar.
- Full Reset cleanup is present for the main and Christmas maps, including removal of active POI layers, pending POI focus, temporary UI states and return to overview.
- POI auto-focus / camera intent priority and pending request before first GPS fix are present on the main and Christmas maps.
- Search and ticker elements are present, but full migration of the separate Preview search/ticker/legend package is not established.
- Toast/overlay and mobile/layout changes are partial. Exact transfer of every separate Preview fix, including the market zoom-button positioning change, is not established.
- Candidate POI buttons use responsive dimensions `clamp(48px, 9vw, 62px)`; a separate ship/map-controls branch changes them to 42×42 px. That 42×42 adjustment is not in the candidate.
- `renderMapCarousel()` currently builds cards from castle/town entries with coordinates. Dynamic replacement of the carousel by Pharmacy, Toilets, My Ship and other categories is not established.

### 3. Additional branches found — not integrated into the candidate

These branches are separate work, not evidence of release readiness:

- `map-navi-poi-persistence-and-focus`, HEAD `7d1a4ac6979660d8d343fbf0d4d468d2a318236a`, is 2 commits ahead of current main. Commit `259d2fa7044fe2ef6910049469f5eeb425b783c3` adds `_fitActivePoiAndUser()`: Reset can keep the user's position and nearest active pharmacy/restroom in view, and GPS updates do not keep panning while a POI layer is active. This branch is not included in candidate `80f542b3`; compare shows it has 3 commits not in candidate and is 37 commits behind candidate.
- `map-navi-ship-time-and-map-controls`, HEAD `38c8f0dbc72b650f66569969def65476d8c59c91`, is 1 commit ahead of main. It reduces POI controls to 42×42 px and adjusts ship/departure-time layout. Not included in candidate.
- `map-navi-my-ship-panel-fix`, HEAD `3c6cc68c30940e96ba70f321754baffd5815255d`, is 3 commits ahead of main. It cleans stale Christmas-map markers and adjusts return-to-ship controls and departure-time handling. Not included in candidate.
- No open PR for these side branches was found in the current open PR list. Do not combine them automatically during freeze; inspect diffs and preserve the approved UI behavior first.

### 4. Preview, Project Map publication and deployed status

- Separate Preview repo `basana/turret-tales-preview` remains at main `bd7dc83f949c26149c4f3b068266515244fc2a4b`; its latest Pages workflow run #91 (`44952056944`) completed successfully. Its `index.html` still contains `<base href="https://turrettales.de/">`, so it is not an independent candidate build and loads some resources from production.
- Direct browser access to both `https://basana.github.io/turret-tales-preview/` and `https://basana.github.io/map-navi-project-map/` was unavailable in the browser checker. Therefore neither published page was visually/runtime-tested in this audit.
- The latest Project Map Pages workflow before this audit, run `45147135870`, completed successfully for Project Map commit `d64eb4f39c1c759da4cad15e05e3ddee2f50281e`. This confirms that previous documentation was published by Pages; it does not confirm visual correctness of the page.
- Netlify deployed commit and live status could not be verified from the available GitHub endpoints. Direct access to `https://turrettales.de/` and `/sw.js` was unavailable. Do not mark deployed.

### 5. Four readiness stages and freeze

| Feature group | Transferred to candidate | Candidate Preview-tested | Current build user-approved | Netlify deployed |
|---|---|---|---|---|
| GPS Follow / Free View / manual recenter | Source code present on main, Christmas and wine maps | No | No | Not confirmed |
| Pharmacy / Toilets / Reset | Source code present on main and Christmas maps; wine has separate controls | No | No | Not confirmed |
| POI auto-focus / camera priority | Source code present on main and Christmas maps | No | No | Not confirmed |
| Search / ticker / overlay | Partial | No | No | Not confirmed |
| Toast / zoom / mobile fixes | Partial | No | No | Not confirmed |
| Bottom carousel | Main map, castle/town cards only | No | Concept agreed; current implementation not approved | Not confirmed |

- 24 November is the second and final planned freeze day. Freeze cannot be signed off as a tested release candidate: candidate `80f542b3` has no PR, candidate Preview, CI checks, browser test, iPhone/iPad test or current-build user approval.
- Immediate blocker: provide a Preview built from exactly candidate SHA `80f542b3`; then run the required iPhone portrait and iPad landscape tests and record the result against that SHA. Until then, do not mark Preview-tested, approved or ready.
- User action: no production action now. Once the exact candidate Preview is available, the user must verify it on iPhone/iPad before approval. The user, not automation, performs Netlify Deploy.
- Deadlines remain: user Netlify Deploy no later than 25 November; live check 26 November; first excursion 27 November.
- Application `main` was not changed; no merge and no Netlify Deploy were performed. Only this Project Map documentation repository was updated.


## Daily audit — 25 November 2026, 09:42 (Europe/Berlin)

### Confirmed GitHub state

- Application repository `basana/turret-tales-christmas` still has `main` at `212334d45d04e1021270e8a9854c0b771ee7dfbc`. Its latest commit (20 Nov, `Add files via upload`) adds only `Rahmen KO kurz.webp`; the main `index.html` blob remains `59e4db3c19d2380a4f18d58b38270426e45d956e`.
- Candidate `feature/map-navi-poi-pulse-states-2026-11-19` remains at `80f542b3d7a5c51123ff9b129b0d59374762d439`; candidate `index.html` blob `43cc9949a104b06ad02e177a9eca0a1d7f9332bd`, `sw.js` blob `5fdf2b838a0a4fbd95e9b58fce079084e08d900d`.
- GitHub compare confirms candidate is 37 commits ahead / 1 behind current main (the behind commit is asset-only), 33 ahead / 0 behind integration `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`, and 20 ahead / 0 behind PR #6 head `4c0d6d28c413fbc0d255cedef03091183837d188`. Candidate diff against main changes `index.html` and `sw.js`.
- Candidate still has no Pull Request. PR #3 is open/unmerged at `f29ad217`; PR #6 is open, Draft and unmerged at `4c0d6d28`. PR #3 and #6 have no submitted reviews. Candidate workflow-run query returned no runs; check-runs total_count = 0; commit statuses total_count = 0 (combined status endpoint reports pending with no individual statuses). No candidate CI result is available.
- Branch list still includes separate, unintegrated branches `map-navi-poi-persistence-and-focus` (`7d1a4ac`), `map-navi-ship-time-and-map-controls` (`38c8f0d`) and `map-navi-my-ship-panel-fix` (`3c6cc68`). No new PR for these was found. Their fixes are not part of candidate `80f542b3`.

### Preview update — no application-code change

- Separate Preview repo `basana/turret-tales-preview` advanced from `bd7dc83f949c26149c4f3b068266515244fc2a4b` to `dcdb65639f1f2b8b4387b6a6af28dfdbacbfd1dd`.
- Compare confirms the only two files added by this commit are `screentest.JPG` and `screentest_1JPG.JPG`; no `index.html` or `sw.js` code changed. The screenshot files could not be opened by the available inspection tools, so they are not treated as verified test evidence.
- Preview Pages workflow run [45484710442](https://github.com/basana/turret-tales-preview/actions/runs/45484710442) completed successfully for `dcdb656`. This is a successful Pages build of the separate Preview repo, not a build of candidate `80f542b3`.
- Preview `index.html` remains blob `bf307ff0662966618787dfe41b6fa480a4299184` and still contains `<base href="https://turrettales.de/">`; Preview `sw.js` remains blob `23cd26581242dfc9667384d0a2c5c680ab47cbb5`. It is therefore not an isolated candidate environment.
- Direct opening of Project Map, Preview and `turrettales.de` failed in the available browser tools. Visual/runtime testing and live Netlify status remain unverified.

### Readiness stages — 25 November

| Feature group | Transferred to candidate | Candidate Preview-tested | Current build user-approved | Netlify deployed |
|---|---|---|---|---|
| GPS Follow / Free View / manual recenter | Source code present in candidate | No | No | Not confirmed |
| Pharmacy / Toilets / Reset | Source code present on main + Christmas maps; wine map has separate controls | No | No | Not confirmed |
| POI auto-focus / camera priority | Source code present in candidate | No | No | Not confirmed |
| Search / ticker / overlay | Partial | No | No | Not confirmed |
| Toast / zoom / mobile fixes | Partial; exact transfer of all Preview fixes not established | No | No | Not confirmed |
| Bottom carousel | Main-map castle/town cards only; dynamic category replacement not established | No | Concept agreed; current build not approved | Not confirmed |

### Blockers and deadline

- Freeze on 23–24 November was not supported by a candidate Preview or device-test evidence. The freeze cannot be treated as signed off.
- The most recent Preview change is screenshot-only and does not unblock testing of candidate `80f542b3`.
- Immediate blocker: no Preview built from the exact candidate SHA, no candidate CI checks, no browser test and no iPhone/iPad test. Current-build user approval is absent.
- The 25 November user Netlify Deploy deadline is today. No Netlify deployment or deployed commit could be verified from the available GitHub data; direct live-site access also failed. Do not infer deployment from the successful GitHub Pages build.
- User action is required before release: obtain/open a Preview of exact candidate SHA and test it on iPhone/iPad; only the user performs Netlify Deploy. Do not mark the release ready until the deployed live version is checked on 26 November.
- Application `main` was not changed by this audit. No merge and no Netlify Deploy were performed. Only the requested Project Map documentation was updated.


## Финальная ежедневная проверка — 26 ноября 2026 года, 09:37 (Europe/Berlin)

### 1. Application repository — состояние подтверждено через GitHub

- `basana/turret-tales-christmas` остаётся доступен; default branch — `main`.
- Application `main` — `212334d45d04e1021270e8a9854c0b771ee7dfbc`. Файлы приложения не изменились относительно предыдущей проверки: `index.html` blob `59e4db3c19d2380a4f18d58b38270426e45d956e`, `sw.js` blob `e2ea1a5fb5b54ae20ebb08be70337eda30c90552`.
- Candidate `feature/map-navi-poi-pulse-states-2026-11-19` подтверждён точным SHA `80f542b3d7a5c51123ff9b129b0d59374762d439`: GitHub compare SHA → branch возвращает `identical`, 0 ahead / 0 behind. Файловые blob SHA без изменений: `index.html` `43cc9949a104b06ad02e177a9eca0a1d7f9332bd`, `sw.js` `5fdf2b838a0a4fbd95e9b58fce079084e08d900d`.
- Сравнение candidate с актуальным `main`: 37 commits ahead / 1 behind; единственный отстающий commit в `main` — добавление изображения, при этом `index.html` и `sw.js` на `main` не менялись. Candidate на 33 commits впереди integration `f29ad217`; на 20 commits впереди PR #6 head `4c0d6d28`.
- Candidate не имеет собственного PR. PR #3 открыт / не слит; PR #6 открыт / Draft / не слит. GitHub reviews для PR #3 и #6 пусты. Combined commit statuses для candidate, integration и PR #6 пусты; check-runs candidate — 0; PR-triggered workflow runs для этих SHA не возвращены. Это не доказывает отсутствие всех типов Actions runs, но подтверждённых CI-результатов нет.

### 2. Новая экспериментальная сборка в отдельном Preview repository

- В `basana/turret-tales-preview` обнаружена ветка `map-navi-interaction-build-2026-11-25` с точным HEAD `65facc6fa1f5150deb174d4fab816e3be4ae8059`. SHA подтверждён сравнением: `65facc6...` и branch ref — `identical`.
- Текущий Preview `main` — `41d2f051dda4ca9b9629c068bd1d780dcc772a19`; экспериментальная ветка — 43 commits ahead / 1 behind. Diff: `index.html` +677 / -1 и новый `map-navi-full-panel.js` на 307 строк. Blob SHA: `index.html` `46d13413d988ed74329121b5a8855c1bf91e3852`, `map-navi-full-panel.js` `fb82b7331d408bf88151c90718322b82414a9896`.
- Source-level проверка подтверждает новый полноэкранный режим основной карты, верхние категории Places / My Ship / Toilets / Pharmacy и нижний горизонтальный rail с карточками. Код переключает содержимое rail между местами, My Ship, туалетами и аптеками; swipe меняет активную карточку/цель, выбор карточки центрирует объект, POI selection вызывает focus/toast и подсветку маркера. Это существенно ближе к согласованной концепции нижней карусели, чем candidate `80f542b3`, где подтверждены только карточки замков/городов.
- Это отдельная экспериментальная ветка Preview, не перенос в `basana/turret-tales-christmas` и не release candidate приложения. UI привязан к основной карте `#view-map` / `leafletMap`; единая реализация для Christmas/wine maps не подтверждена.
- `index.html` экспериментальной ветки по-прежнему содержит `<base href="https://turrettales.de/">`. Внизу подключается внешний `map-navi-full-panel.js` с домена `turret-tales-experimental-preview`; исходный файл присутствует в ветке Preview, а workflow отдельного experimental-preview repo настроен забирать эту ветку. Но факт успешного Pages deployment именно SHA `65facc6...` не подтверждён.
- В CSS экспериментального UI размер `.poi-toggle-btn` задан 84×84 px — требуется визуальная оценка, это заметно крупнее компактного управления. Внешний panel module вызывает `setState('quarter')`, но helper допускает только `compact` и `full`, остальные значения приводит к `third`; это source-level несоответствие, которое нужно проверить в браузере. Наличие этих особенностей не считается доказанным runtime-дефектом без теста.
- Альтернативная ветка `golden-build/2026-11-24-red-labels-horizontal-my-ship-ok` сравнивается с Preview main как 17 ahead / 3 behind; её diff содержит `index.html` и `MAP-NAVI-NEXT-ARCHITECTURE.md`. Она не является подтверждённой release candidate и не имеет подтверждённого device test.

### 3. Experimental Pages workflow и доступность Preview

- В `basana/turret-tales-experimental-preview` main workflow file blob `c409f217376494f10130cc4c22a67d7d39ab185d` указывает source commit `65facc6fa1f5150deb174d4fab816e3be4ae8059` и checkout ветки `basana/turret-tales-preview:map-navi-interaction-build-2026-11-25`.
- Ветка `preview-map-navi-interaction-build` в experimental-preview содержит workflow file blob `1b16d641037746892c567a74587fa234d4fd0aa5`; он разрешает push-trigger также для этой ветки и использует тот же source branch.
- Combined statuses для source commit и двух workflow-file blobs пусты; доступные PR-triggered workflow runs не возвращены. Фактический Pages run/deployment не удалось подтвердить. Прямое открытие Project Map, Preview и live-сайта через доступный браузерный инструмент не удалось; загрузка Project Map также завершилась ошибкой. Поэтому Preview-tested и Pages-deployed для `65facc6...` не отмечаются.

### 4. Итоговые стадии

| Функция | Перенесено в application candidate | Есть в отдельном Preview source | Preview-tested | User-approved | Netlify deployed |
|---|---|---|---|---|---|
| GPS Follow / Free View / manual recenter | Да, main / Christmas / wine maps в `80f542b3` | Контролы переставлены в interaction build; новая логика не переносилась в app | Нет | Нет | Не подтверждено |
| Pharmacy / Toilets / Reset | Да, main + Christmas maps в `80f542b3` | Категории Pharmacy / Toilets есть в interaction build; 84×84 px controls требуют проверки | Нет | Нет | Не подтверждено |
| POI auto-focus / camera priority | Да, pending first fix и focus intent в `80f542b3` | POI cards, selection, focus/toast/highlight в interaction build | Нет | Нет | Не подтверждено |
| Search / ticker / overlay | Частично | Search/ticker repositioning и fullscreen overlay в interaction build | Нет | Нет | Не подтверждено |
| Toast / zoom / mobile fixes | Частично | Дополнительные panel/toast/mobile CSS в interaction build | Нет | Нет | Не подтверждено |
| Bottom carousel | Только castles/towns | Places / My Ship / Toilets / Pharmacy dynamic rail в interaction build | Нет | Концепция согласована; этот build не одобрен | Не подтверждено |

### 5. Дедлайны и блокеры — 26 ноября

- Freeze 23–24 ноября не подтверждён Preview/device evidence и не может считаться подписанным.
- Срок пользовательского Netlify Deploy 25 ноября прошёл. Доступные GitHub данные не подтверждают ни факт Deploy, ни deployed commit; это не означает, что Deploy точно не выполнялся.
- Запланированная на 26 ноября live-проверка не может быть подтверждена: нет проверяемого Netlify deployment record и доступного live-site fetch. User approval конкретного SHA также не зафиксирован.
- До экскурсии 27 ноября остаётся критический риск: нет подтверждённой цепочки candidate → Preview test → user approval → Netlify deployed commit → live check. Пользователю необходимо сегодня самостоятельно проверить Netlify live на iPhone/iPad и убедиться, что используется именно протестированная версия; не считать experimental Preview source доказательством готовности.
- Application `main` не изменялся; merge не выполнялся; Netlify Deploy не запускался. Обновляются только запрошенные контрольные материалы.
