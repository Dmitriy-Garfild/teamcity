# Домашнее задание к занятию 11 «Teamcity»


## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

**Ответ.**
1. ![infracture YC](screenshots/image_1.jpg)
2. ![TeamCity Agents](screenshots/image_2.jpg)
3. ![Nexus](screenshots/image_3.jpg)
- Вся инфрасрутура поднимается через терраформ под ключ.

## Основная часть

1. Создайте новый проект в teamcity на основе fork.
2. Сделайте autodetect конфигурации.
3. Сохраните необходимые шаги, запустите первую сборку master.
4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.
5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.
8. Мигрируйте `build configuration` в репозиторий.
9. Создайте отдельную ветку `feature/add_reply` в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.
14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.
18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
19. В ответе пришлите ссылку на репозиторий.


**Ответ.**
1. check
2. [Скриншот 1.2](screenshots/image_1.2.jpg)
3. [Скриншот 1.3](screenshots/image_1.3.jpg)
4. 
- [Скриншот 1.4.1](screenshots/image_1.4.jpg)
- [Скриншот 1.4.2](screenshots/image_1.4.1.jpg)
5. [Скриншот 1.5](screenshots/image_1.5.jpg)
- Потребовались только кредлы, так как **Nexus**  работает по `https``
6. check.
7. [Скриншот 1.7](screenshots/image_1.7.jpg)
8. [Скриншот 1.8](screenshots/image_1.8.jpg)
9. check
10. check
11. check
12. check
13. [Скриншот 1.13](screenshots/image_1.13.jpg)
14. [pull request](https://github.com/InfernoFeniks/example-teamcity/pull/1)
15. check
16. [Скриншот 1.16](screenshots/image_1.16.jpg)
17. [Скриншот 1.17](screenshots/image_1.17.jpg)
18. https://github.com/Dmitriy-Garfild/teamcity/tree/main/.teamcity
  
19 https://github.com/Dmitriy-Garfild/teamcity/tree/main/
  
