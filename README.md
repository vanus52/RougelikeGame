# RougelikeGame
Совместная работа | делаем рогалик 

твое имя. Антон. а? че звал сларк?

##never gonna give you up - varikelm

Вы понимаете, что мы на гит забыли закинуть проект, мдееее


Ограничения атрибутов

Сущность User

id_User - PRIMARY KEY (Автоматически ставит NOT NULL, UNIQUE)
fullName - VARCHAR, Ограничение по символам - 100, NOT NULL, Полное ФИО
Email - VARCHAR, Ограничение по символам - 256, NOT NULL, Почта пользователя
Password - VARCHAR, Ограничение по символам - 32, NOT NULL, Пароль от аккаунта

Сущность Project_Role

id_Role - PRIMARY KEY (Автоматически ставит NOT NULL, UNIQUE)
id_User - FOREIGN KEY (id_User) REFERENCES User(id_User)
id_Project - FOREIGN KEY (id_Project) REFERENCES Project(id_Project)
Status - VARCHAR, Ограничение по символам - 20, NOT NULL , а также проверяется через параметр CHECK(Status in ("Супер-Админ", "Администратор", "Менеджер", "Исполнитель"), Статус пользователя в системе для проверки его доступа

Сущность Project

id_Project - PRIMARY KEY (Автоматически ставит NOT NULL, UNIQUE)
Name - VARCHAR , Ограничение по символам - 120, NOT NULL, Название проекта
Description - VARCHAR, Ограничение по символам - 1000, Описание проекта
StartDate - DATETIME, Дата создания проекта, NOT NULL,
EndDate - DATETIME, Дата окончания проекта, NOT NULL

Сущность Tasks

id_Task - PRIMARY KEY (Автоматически ставит NOT NULL, UNIQUE)
id_Project - FOREIGN KEY (id_Project) REFERENCES Project(id_Project)
id_User - FOREIGN KEY (id_User) REFERENCES User(id_User)
Name - VARCHAR, Ограничение по символам - 120, NOT NULL, Название задачи
Description - VARCHAR, Ограничение по символам - 2500, NOT NULL, Описание задачи
Priority - VARCHAR, Ограничение по символам - 20, а также ограничение через параметр CHECK(Priority in ("Срочно","Высокий", "Средний", "Низкий")), NOT NULL, Приоритет задачи
Status - VARCHAR, Ограничение по символам - 20, а также ограничение через параметр CHECK(Status in ("Новая", "В работе", "На проверке", "Отменена")), NOT NULL, Статус задачи

Сущность Tag_Task

id_Tag - PRIMARY KEY (Автоматически ставит NOT NULL, UNIQUE)
id_Task - FOREIGN KEY (id_Task) REFERENCES Tasks(id_Task)
id_User - FOREIGN KEY (id_User) REFERENCES User(id_User)

Сущность Tags

id_Tags - PRIMARY KEY (Автоматически ставит NOT NULL, UNIQUE)
Name - VARCHAR, Ограничение по символам - 30, NOT NULL, Имя тега
Description - VARCHAR, Ограничение по символам - 100, Описание тега
Color - VARCHAR, Ограничение по символам - 6, DEFAULT "#ffffff", Цвет тега

Сущность Comments

id_Comments - PRIMARY KEY (Автоматически ставит NOT NULL, UNIQUE)
id_Task - FOREIGN KEY (id_Task) REFERENCES Tasks(id_Task)
id_User - FOREIGN KEY (id_User) REFERENCES User(id_User)
Text - VARCHAR, Ограничение по символам - 1000, NOT NULL, Текст комментария
CreationDate - DATETIME, NOT NULL Дата написания комментария
