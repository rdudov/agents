# Промпты агентов для мультиагентной разработки в Claude Code и Cursor.

Расширенное описание подхода приведено в [статье](https://habr.com/ru/articles/971620/).

Общее описание подхода: [00_agent_development.md](https://github.com/rdudov/agents/blob/master/00_agent_development.md)

Промпт оркестратора, который координирует работу остальных агентов: 01_orchestrator.md

Промпты агентов (названия говорят сами за себя):
- [02_analyst_prompt.md](https://github.com/rdudov/agents/blob/master/02_analyst_prompt.md)
- [03_tz_reviewer_prompt.md](https://github.com/rdudov/agents/blob/master/03_tz_reviewer_prompt.md)
- [04_architect_prompt.md](https://github.com/rdudov/agents/blob/master/04_architect_prompt.md)
- [05_architecture_reviewer_prompt.md](https://github.com/rdudov/agents/blob/master/05_architecture_reviewer_prompt.md)
- [06_agent_planner.md](https://github.com/rdudov/agents/blob/master/06_agent_planner.md)
- [07_agent_plan_reviewer.md](https://github.com/rdudov/agents/blob/master/07_agent_plan_reviewer.md)
- [08_agent_developer.md](https://github.com/rdudov/agents/blob/master/08_agent_developer.md)
- [09_agent_code_reviewer.md](https://github.com/rdudov/agents/blob/master/09_agent_code_reviewer.md)

Пример промпта для запуска мультиагентной разработки в Cursor, чтобы он автоматически стартовал субагентов с нужными ролями. 
```
Используя подход по оркестрации мультиагентной разработки (agents/01_orchestrator.md), 
выполни доработку {ссылка на файл с постановкой задачи}.

Описание проекта {ссылка на описание проекта для агентов, если проект существующий}

Промпты агентов с указанными в 01_orchestrator.md ролями находятся в agents (02*.md..09.md).
Агентов нужно вызывать shell-командами:
cursor-agent -f --model {модель} -p {промпт}
и дожидаться от них результатов.

Промпт следующего формата:
"{содержимое файла с ролью} {входные данные согласно описанию роли}"

Модель:
аналитик, архитектор, планировщик — opus-4.5  
ревьюеры ТЗ, архитектуры, плана, кода и разработчик — composer-1
```
