
Cтруктурный паттерн: учет погодных условий реализован с помощью паттерна декоратор.
Обоснование: упрощена процедура учета дополнительных погодных уловий, добавлено больше настроек условий гонки
	- класс с погодными условиями реализует интерфейс CreatureWeather (имеет метод correction_spead который используется машинами)
	- при создании объекта гонки (Competition) создается базовый объект с погодными условиями (который не коректирует скорость)
	- в объекте гонки, при вызове метода set_weather с параметрами, на объект с погодными условиями навешивается доп функционал
	- доп функционал для погодных условий представлен классом Wind (скорость ветра) и Ice (гололед)


Поведенческий паттерн: рассылка результатов гонки реализована с помощью паттерна наблюдатель:
Обоснование: упрощена процедура управления уведомлениями о результатах гонки
	- каждая машина наследует клас Observer в котором определен метод update (обработка результатов гонки)
	- при создании объекта гонки создается объект рассылки (NotificationManager)
	- перед стартом гонки, после создании каждого объекта машины он подписывается в рассылку результата в NotificationManager
	- после окончания гонки результаты передаются в NotificationManager для рассылки

Порождающий паттерн: доступ к спецификациям автомобилей реализованы через синглетный класс
Обоснование: в дальнейшем, если база машин доступных для гонок будет расширяться, информация не будет дублироваться в каждом объекте машины