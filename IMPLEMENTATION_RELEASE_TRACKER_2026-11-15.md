# MAP NAVI — список изменений и календарь подготовки к первой экскурсии

**Обновлено:** 19 ноября 2026 года, 09:34 (Europe/Berlin)  
**Первая экскурсия:** 27 ноября 2026 года  
**Цель:** стабильная версия обычной навигации должна быть опубликована и проверена до экскурсии. Пространственная трёхуровневая модель не блокирует этот выпуск.

> Важно о времени: в прежней записи были даты, но не были внесены часы выполнения. Поэтому ниже часы впервые зафиксированы как рабочий календарный план, а не как якобы ранее согласованные обязательства. Время указано по Германии (Europe/Berlin).

## 1. Список изменений для переноса

Переносим в существующий репозиторий приложения `basana/turret-tales-christmas`, отдельной рабочей веткой. Для каждого пункта отмечаем отдельно: перенесено → проверено в Preview → одобрено пользователем → опубликовано в Netlify.

| № | Изменение | Источник / известное состояние | Статус |
|---|---|---|---|
| 1 | GPS Follow: следование за текущим местоположением | Integration commit `e094b25e8742c151f3cc5c215c221d8a91481bb9`; унаследован в draft PR #6 | Код есть в PR #3 и draft PR #6; только основная карта `leafletMap`; Preview/device test не подтверждён |
| 2 | Free View: ручное перемещение карты без выключения GPS | Integration commit `e094b25e8742c151f3cc5c215c221d8a91481bb9`; унаследован в draft PR #6 | Код есть в PR #3 и draft PR #6; ручные pan/zoom отключают Follow только на основной карте; тест не подтверждён |
| 3 | Ручной возврат к GPS и кнопка `↻ Follow` | Integration commit `e094b25e8742c151f3cc5c215c221d8a91481bb9`; унаследован в draft PR #6 | Код возвращает камеру к последним GPS-координатам на основной карте; Preview/device test не подтверждён |
| 4 | Правая вертикальная колонка Pharmacy / Toilets / Reset | Integration commit `943801e75033c51c09943e79038caad799ec3baa` | Код в PR #3 на обеих картах; PR #6 дополнительно меняет компоновку Christmas map, но визуальная проверка не подтверждена |
| 5 | Автофокус ближайшей аптеки/туалета при включении поиска | Базовый `_zoomToNearestPoi` уже есть в application main; integration commit `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb` сохраняет запрос до первого GPS fix | Базовый автофокус и pending first-fix обработка есть в коде; улучшенное POI centering из отдельного Preview repo не перенесено; runtime test не подтверждён |
| 6 | Приоритет выбранного POI: GPS не перетягивает камеру, пока активен POI | Integration commit `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`; Reset logic в PR #6 | Код есть в PR #3 и унаследован в draft PR #6; device test не подтверждён |
| 7 | Общая компоновка поиска и ticker/легенды | Preview-коммиты `db9f392`, `6d6a9bf` | Полный search/ticker/legend пакет не перенесён; PR #6 содержит только отдельную компоновку поиска Christmas map |
| 8 | Мобильная ширина и расположение элементов | Preview-коммит `6d6a9bf`; PR #6 head `8beefcecc1e6c5d2db5fc32e7d9f5bf58cf1a2ca` | Частично изменена Christmas map: высота карты, размещение поиска и GPS-кнопки, горизонтальная прокрутка языков/chips; отдельный Preview mobile-width fix не перенесён; device test не подтверждён |
| 9 | Toast / overlay / z-index | Preview-коммит `fc0078a`; PR #6 Reset / Popup Manager | PR #6 добавляет закрытие конфликтующих окон и подавление повторного nearest-toast после Reset; визуальный toast positioning / z-index fix из Preview не перенесён |
| 10 | Вертикальное положение zoom-кнопок карты рынков | Preview-коммит `b27c044` | Не перенесено в PR #3/#6; требуется отдельная сверка |
| 11 | Единообразная проверка основных карт на iPhone и iPad | Интеграционный Preview | Не подтверждено; реальный браузерный и device test не зафиксирован |
| 12 | Полный Reset состояния и Popup Manager | Draft PR #6, актуальный head `4c0d6d28c413fbc0d255cedef03091183837d188` | 13 commits ahead / 0 behind integration; Reset cleanup реализован для основной карты, Christmas map Reset пока только возвращает bounds; PopupManager есть; PR #6 draft, не слит; harness результаты заявлены в PR body, независимо не воспроизведены; CI/device test отсутствуют |

Ссылки:
- [Репозиторий приложения](https://github.com/basana/turret-tales-christmas)
- [GPS-ветка](https://github.com/basana/turret-tales-christmas/tree/feature/map-navi-gps-follow-01)
- [Preview-ветка](https://github.com/basana/turret-tales-christmas/tree/preview/gps-follow-device-test-01)
- [Preview shell](https://github.com/basana/turret-tales-preview)
- [PR #2 — GPS Follow device test](https://github.com/basana/turret-tales-christmas/pull/2)
- [PR #6 — Reset / Popup Manager / map stabilization, draft](https://github.com/basana/turret-tales-christmas/pull/6)

**Последний подтверждённый фактический статус на 19 ноября 2026 года, 09:34 (Europe/Berlin):** application `main` остаётся на `2291e55a513eadb6ff00b7011cfc74d9b25ef947`; integration `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb` — 4 commits ahead / 0 behind, PR #3 open/unmerged. Stabilized integration `4c0d6d28c413fbc0d255cedef03091183837d188` — 13 commits ahead / 0 behind integration и 17 ahead / 0 behind main; PR #6 open/draft, base integration. В PR #6 подтверждены Reset cleanup для основной карты, PopupManager, частичная Christmas map layout, GPS panel/halo adjustments и camera priority; на Christmas map Reset пока только восстанавливает bounds, а GPS Follow/Free View отсутствует. POI auto-focus и pending first fix присутствуют на основной карте; Christmas map повторно фокусирует активный POI при первом GPS fix. Полный search/ticker/legend, visual toast/z-index, mobile-width и market zoom Preview fixes не перенесены. PR #6 сообщает harness 6/6 и статические проверки, но независимое воспроизведение отсутствует; script block 4 имеет заявленную pre-existing parse failure. Для PR #3/#6 нет check-runs/statuses, реального Preview, iPhone/iPad tests и user approval. Отдельный Preview repo `a1ea99e4` с `<base href="https://turrettales.de/">` не считается интеграционным Preview. Netlify live/deployed commit проверить не удалось. Сегодняшнее окно тестов ещё не началось на момент аудита. Main не менялся; merge/Deploy не выполнялись.
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

