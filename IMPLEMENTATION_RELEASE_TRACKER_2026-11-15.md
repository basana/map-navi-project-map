# MAP NAVI — список изменений и календарь подготовки к первой экскурсии

**Обновлено:** 16 ноября 2026 года, 09:12 (Europe/Berlin)  
**Первая экскурсия:** 27 ноября 2026 года  
**Цель:** стабильная версия обычной навигации должна быть опубликована и проверена до экскурсии. Пространственная трёхуровневая модель не блокирует этот выпуск.

> Важно о времени: в прежней записи были даты, но не были внесены часы выполнения. Поэтому ниже часы впервые зафиксированы как рабочий календарный план, а не как якобы ранее согласованные обязательства. Время указано по Германии (Europe/Berlin).

## 1. Список изменений для переноса

Переносим в существующий репозиторий приложения `basana/turret-tales-christmas`, отдельной рабочей веткой. Для каждого пункта отмечаем отдельно: перенесено → проверено в Preview → одобрено пользователем → опубликовано в Netlify.

| № | Изменение | Источник / известное состояние | Статус |
|---|---|---|---|
| 1 | GPS Follow: следование за текущим местоположением | Integration commit `e094b25e8742c151f3cc5c215c221d8a91481bb9` | Код в PR #3; реализован только для основной карты `leafletMap`; Preview/device test не подтверждён |
| 2 | Free View: ручное перемещение карты без выключения GPS | Integration commit `e094b25e8742c151f3cc5c215c221d8a91481bb9` | Код в PR #3; ручные pan/zoom отключают Follow на основной карте, GPS остаётся включён; Preview/device test не подтверждён |
| 3 | Ручной возврат к GPS и кнопка `↻ Follow` | Integration commit `e094b25e8742c151f3cc5c215c221d8a91481bb9` | Кнопка возвращает к последним GPS-координатам на основной карте; Preview/device test не подтверждён |
| 4 | Правая вертикальная колонка Pharmacy / Toilets / Reset | Integration commit `943801e75033c51c09943e79038caad799ec3baa` | Код в PR #3: верхний правый стек, адаптивные 48–68 px, кнопки на основной и Christmas map; Preview/device test не подтверждён |
| 5 | Автофокус ближайшей аптеки/туалета при включении соответствующего поиска | Базовый `_zoomToNearestPoi` уже есть в application main; Preview commits `57408be`, `a1ea99e` | Базовый автофокус есть; улучшенное центрирование выбранного POI и toast-action focus из отдельного Preview repo в PR #3 не перенесены; требуется тест |
| 6 | Приоритет выбранного POI: GPS не перетягивает камеру, пока активен POI | Integration commit `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb` | Код в PR #3: GPS camera-follow приостанавливается для POI; запрос до первого GPS fix сохраняется; только кодовая проверка, device test не подтверждён |
| 7 | Общая компоновка поиска и ticker/легенды | Preview-коммиты `db9f392`, `6d6a9bf` | Не перенесено; остаётся в отдельном Preview repo |
| 8 | Мобильная ширина и расположение элементов | Preview-коммиты `6d6a9bf` | Не перенесено; остаётся в отдельном Preview repo |
| 9 | Позиция информационного toast и z-index поиска | Preview-коммит `fc0078a` | Не перенесено; остаётся в отдельном Preview repo |
| 10 | Вертикальное положение zoom-кнопок карты рынков | Preview-коммит `b27c044` | Не перенесено; остаётся в отдельном Preview repo |
| 11 | Единообразная проверка основных карт на iPhone и iPad | Общий тест после интеграции | Не начато; требуется тест iPhone/iPad |

Ссылки:
- [Репозиторий приложения](https://github.com/basana/turret-tales-christmas)
- [GPS-ветка](https://github.com/basana/turret-tales-christmas/tree/feature/map-navi-gps-follow-01)
- [Preview-ветка](https://github.com/basana/turret-tales-christmas/tree/preview/gps-follow-device-test-01)
- [Preview shell](https://github.com/basana/turret-tales-preview)
- [PR #2 — GPS Follow device test](https://github.com/basana/turret-tales-christmas/pull/2)

**Текущий фактический статус на 16 ноября 2026 года, 09:12 (Europe/Berlin):** application `main` по-прежнему на `2291e55a513eadb6ff00b7011cfc74d9b25ef947`. Интеграционная ветка `feature/map-navi-integration-2026-11-15` — `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`, на 4 коммита впереди `main`, 0 позади; изменены `index.html` и `sw.js`. Четыре коммита: `e094b25e8742c151f3cc5c215c221d8a91481bb9` (GPS Follow / Free View), `943801e75033c51c09943e79038caad799ec3baa` (controls), `c84a69a0d9920aa3a584f581caed800377d0384b` (Service Worker cache isolation), `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb` (pending POI first fix). PR #3 открыт и не слит; GitHub сообщает 0 check runs и 0 status checks, Deploy Preview URL не подтверждён. По исходному коду GPS Follow / Free View и `↻ Follow` подключены к основной карте `leafletMap`; для Christmas/market map аналогичный режим не подтверждён, хотя Pharmacy / Toilets / Reset присутствуют на обеих картах. Базовый `_zoomToNearestPoi` уже был в `main`; улучшенное центрирование POI и toast-action focus из Preview commits `57408be` и `a1ea99e` в PR #3 не перенесены. Search/ticker/overlay, mobile-width, toast/z-index и market-zoom исправления из Preview commits `db9f392`, `6d6a9bf`, `fc0078a`, `b27c044` также не перенесены. Отдельный `turret-tales-preview` достиг commit `a1ea99e4d3b6bd0b00f6d26e096b6ec46f8c6ca5`; GitHub Pages build для него завершился успешно, но это другой репозиторий/сборка, а его `index.html` содержит `<base href="https://turrettales.de/">`, поэтому он не подтверждает тестирование PR #3. PR #2 остаётся открытым и не слитым; GPS-ветка по-прежнему diverged: 3 ahead / 1 behind. Device test на iPhone/iPad, отдельное пользовательское одобрение и live Netlify deployment не подтверждены. Проверить Netlify-конфигурацию и live-сайт через доступные GitHub-данные не удалось; deployed status остаётся неизвестным. В рамках этой проверки application `main` не изменялся, merge и Deploy не выполнялись.

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