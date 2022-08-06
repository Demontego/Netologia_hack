# НЕТОЛОГИЯ
Образование — одна из тех отраслей, что уже давно, а на самом деле одной из первых, встала на путь масштабной цифровой трансформации. За много лет накоплена большая база данных: от онлайн-лекций до цифровых аналогов самой разнообразной профессиональной и художественной литературы. В связи с этим технологии искусственного интеллекта уже давно применяются в образовательных процессах.

Онлайн-курсы становятся всё более востребованными. Рынок онлайн-образования растет постоянно, особенно резкий скачок произошел во время пандемии, которая буквально заставила пересмотреть отношение к образовательным процессам окончательно. Онлайн-курсы и уроки ежегодно набирают популярность, аудитория таких курсов — от школьников до пенсионеров, соответственно и запросы у всех пользователей разные. Образовательные организации стремятся максимально персонализировать коммуникации и как можно точнее предугадывать выбор пользователей, чтобы улучшить клиентский опыт.

Участникам чемпионата предлагается разработать модель предсказания наиболее актуального для пользователя предложения образовательного курса на данных Нетологии. В данный момент продвижение онлайн-курсов Нетологии осуществляется без применения моделей машинного обучения. Следующий этап развития продвижения курсов — попытка предсказать индивидуальные пожелания клиентов, тем самым улучшив пользовательский опыт.

Персонализация контента — это тренд, который будет сохраняться в любых индустриях, связанных со сферами образования, финансов и даже медицины — там, где запрос пользователя и его «персональный путь» ставится во главу угла в принятии решений даже о внедрении в образовательный процесс искусственного интеллекта.

# Задача «Модель прогнозирования выбора образовательных курсов пользователями»

## Введение
В данный момент продвижение онлайн-курсов Нетологии
осуществляется без применения моделей машинного обучения. Следующий
этап развития продвижения курсов - попытка попасть в индивидуальные
пожелания клиентов, улучшив клиентский опыт и увеличив выручку. Для
этого был выбран подход NBO (Next Best Offer): перед рассылкой
коммуникаций необходимо понимать, какой из доступных курсов
максимизирует вероятность отклика покупателя. В этом и должна помочь
модель, подбирается наиболее актуальный для клиента курс.

## Условие задачи
Цель соревнования — разработать модель машинного обучения,
которая на основе истории действий пользователя на сайте будет
предсказывать его повторную покупку образовательного курса

## Запуск
запустить ноутбук и прощелкать каждую ячейку, предварительно установив lightautoml способом pip install -U lightautoml

## описание изначальных фичей:
id уникальное значение каждой строки
month_id последний день месяца среза
student_id id студента
carts_created_at дата создания заявки
program_id id продукта
target строка для предсказания

### Метрики прохождения программы в месяц среза:
spent_time_total время за учебой в условных единицах
spent_time_to_complete_hw время, потраченное на выполнение дз
avg_hw_mark средняя оценка за дз
completed_hw кол-во выполненных дз
failed_hw кол-во проваленных дз
reworked_hw кол-во переделанных дз
interacted_hw кол-во дз, которыми занимался студент в этом месяце
test_with_good_mark кол-во тестов с удовлетворительной оценкой
test_with_great_mark кол-во тестов с отличной оценкой
webinars кол-во просмотренных вебинаров
avg_quiz_result средняя оценка за квизы
notes кол-во оставленных заметок
hw_leader был лидером в групповых заданиях
lessons кол-во уроков, которые открывал пользователь
activity общая активность студента в личном кабинете

### Покупки до приобретения текущей программы:
bought_d1 кол-во прошлых покупок в направлении 1
bought_d2 кол-во прошлых покупок в направлении 2
bought_d3 кол-во прошлых покупок в направлении 3
bought_d4 кол-во прошлых покупок в направлении 4
bought_d5 кол-во прошлых покупок в направлении 5

### Метрики относящиеся непосредственно к покупке:
payment_type тип оплаты
promo участвовал ли в любой промокампании
price цена программы
communication_type тип создания заявки (ОП или сам через сайт)
auto_payment автопокупка (1 или 0)
ABC сегмент клиента по готовности купить
city город пользователя
country страна пользователя
gender пол
age_indicator возраст в условных единицах
speed_recall скорость перезвона клиенту (1 - быстро, 7 -
долго)
os операционная система пользователя
browser название браузера
platform платформа

### Информация по коммуникации с менеджерами отдела продаж:
m_avg_duration средняя длительность звонка
m_avg_talk_duration средняя длительность разговора
m_missed_calls кол-во пропущенных звонков
m_total_calls всего звонков
m_was_conversations кол-во звонков, когда состоялся диалог
m_total_duration длительность всего

### Информация по коммуникации с телемаркетологами:
p_avg_duration средняя длительность звонка
p_avg_talk_duration средняя длительность разговора
p_missed_calls кол-во пропущенных звонков
p_total_calls всего звонков
p_was_conversations звонков, когда состоялся диалог
p_total_duration длительность всего
support_feedback_avg средняя удовлетворенность службой поддержки за год

### Средняя оценка уроков студентов в каждом направлении за прошедший год:
feedback_avg_d1 средний балл по курсам направления 1
feedback_avg_d2 средний балл по курсам направления 2
feedback_avg_d3 средний балл по курсам направления 3
feedback_avg_d4 средний балл по курсам направления 4
feedback_avg_d5 средний балл по курсам направления 5

Метрика
В качестве метрики выступает взвешенная сумма Recall и Precision по
следующей формуле:
𝑅𝑒𝑠𝑢𝑙𝑡 = 0. 2 * 𝑅𝑒𝑐𝑎𝑙𝑙 + 0. 8 * 𝑃𝑟𝑒𝑐𝑖𝑠𝑖𝑜�
