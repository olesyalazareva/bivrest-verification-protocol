# API Reference для автоматизации BIVREST

Если вы хотите создать цифровую версию метода (Telegram-бот, веб-приложение), вот минимальный API для взаимодействия.

**Важно:** Коммерческое использование API требует согласования с автором метода.

---

## POST /session/start

Инициирует новую игровую сессию.

**Request:**
```json
{
  "players": [
    {"id": "P001", "avatar": "Красная Шапочка"},
    {"id": "P002", "avatar": "Госпожа"}
  ],
  "stakes": 6
}
Поле	Тип	Описание
players	array	Список игроков с их аватарами
stakes	integer	Начальное количество «Шансов» на игрока
Response:

json
{
  "session_id": "S001",
  "turn_order": ["P001", "P002"]
}
Поле	Тип	Описание
session_id	string	Уникальный идентификатор сессии
turn_order	array	Очерёдность ходов
POST /turn/act
Выполнение хода игроком.

Request:

json
{
  "session_id": "S001",
  "player_id": "P001",
  "card": "Двойка крести",
  "action": "Она стеснительная, шепчет деревьям свои фантазии..."
}
Поле	Тип	Описание
session_id	string	ID сессии
player_id	string	ID игрока
card	string	Название карты (как в игре)
action	string	Текстовое описание действия
Response:

json
{
  "verdict": "Верю",
  "votes": {"Верю": 3, "Не верю": 0},
  "penalty": 0,
  "empty_chair": false
}
Поле	Тип	Описание
verdict	string	Итог голосования: «Верю» или «Не верю»
votes	object	Распределение голосов
penalty	integer	Размер штрафа в шансах
empty_chair	boolean	Активирован ли режим «пустого стула»
POST /turn/verification (для AI-верификатора)
Запрос к AI на оценку правдивости действия.

Request:

json
{
  "avatar": "Красная Шапочка",
  "task": "Расскажи о сексуальной жизни аватара",
  "action": "Она стеснительная, шепчет деревьям свои фантазии...",
  "previous_failures": 0
}
Поле	Тип	Описание
avatar	string	Роль, от лица которой говорит игрок
task	string	Задание с карты
action	string	Действие игрока
previous_failures	integer	Количество предыдущих «Не верю» в этой сессии
Response:

json
{
  "verdict": "Верю",
  "confidence": 0.87,
  "reason": "Действие содержит сенсорные маркеры (запах хвои) и эмоциональную окраску, соответствует образу Красной Шапочки"
}
Поле	Тип	Описание
verdict	string	«Верю» или «Не верю»
confidence	float	Уверенность AI (0.0–1.0)
reason	string	Обоснование вердикта
POST /session/empty_chair
Активация режима «пустого стула» (после двух последовательных «Не верю»).

Request:

json
{
  "session_id": "S001",
  "player_id": "P003",
  "stimulus": "Чего ты на самом деле боишься?"
}
Поле	Тип	Описание
session_id	string	ID сессии
player_id	string	ID игрока
stimulus	string	Вопрос или задание от фасилитатора
Response:

json
{
  "response": "Я боюсь, что если попрошу, меня пошлют. Я всегда стеснялся просить.",
  "new_script": "Я могу попросить, если захочу"
}
Поле	Тип	Описание
response	string	Ответ игрока от первого лица
new_script	string	Зафиксированный новый сценарий
GET /session/log
Получение полного лога сессии для обучения AI.

Request:

text
GET /session/log?session_id=S001&format=csv
Параметр	Тип	Описание
session_id	string	ID сессии
format	string	json или csv (по умолчанию json)
Response (CSV):

csv
session_id,timestamp,player_id,avatar,task,action,votes_trust,votes_not_trust,verdict,penalty,empty_chair,new_script
S001,2026-04-01T12:00:00,P001,Красная Шапочка,Расскажи о сексуальной жизни аватара,"шепчет деревьям...",3,1,Верю,0,0,
S001,2026-04-01T12:05:00,P002,Госпожа,Сделай комплимент,"Ты выглядишь дорого",4,0,Верю,0,0,
Ошибки
Код	Описание
400	Неверный формат запроса
401	Неавторизованный доступ (для коммерческих реализаций)
404	Сессия или игрок не найдены
429	Слишком много запросов
Лицензирование API
Некоммерческое использование (исследования, open-source) — свободно.

Коммерческое использование (продажа цифровых продуктов на основе BIVREST) — по договору с автором.

Для получения коммерческой лицензии: @olesyalazarevalove (Telegram)

