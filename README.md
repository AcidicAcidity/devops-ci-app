
# devops-ci-app

Учебное Flask-приложение для практической работы №10

CI: Pylint -> pytest -> Docker build -> smoke-test -> GHCR.

Публикация образа выполняется только из `main`. В Pull Request выполняются проверки без push.

- health endpoint: `/health`;
- образ: `ghrc.io/AcidicAcidity/devops-app`;
- основной workflow: `.github/workflows/ci.yml`.


Разбор инцидента №1

Симптом: list, test, build и smoke-test успешны; docker push отклонён.
Компонент: авторизация GHCR.
Причина: у GITHUB_TOKEN остутствует packages: write.
Влияние: проверенный образ остался только на временном runner; пакет не опубликован.
