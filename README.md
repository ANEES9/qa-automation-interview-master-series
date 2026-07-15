# QA Automation Interview Master Series

A professional, original technical book series for QA automation interview preparation.

This repository is the source workspace for writing, organizing, reviewing, and publishing the QA Automation Interview Master Series. The series is designed for candidates who want structured preparation for automation testing roles, with practical explanations, interview-ready answers, framework guidance, scenario practice, and hands-on code examples.

## Volume 1: Selenium WebDriver + Java (2026)

Volume 1 focuses on Selenium WebDriver with Java and the supporting skills expected from QA automation engineers in modern interview loops.

Core areas include:

- Java fundamentals for automation engineers
- Selenium WebDriver concepts and real-world usage
- TestNG test design and execution
- Automation framework architecture
- REST Assured API testing basics
- SQL interview preparation
- Git, Jenkins, and CI workflow fundamentals
- Scenario-based QA automation questions
- HR and behavioral interview preparation

Start here:

- [Book Overview](Volume-1-Selenium-Java/00-Introduction/Book-Overview.md)
- [Table of Contents](Volume-1-Selenium-Java/00-Introduction/Table-of-Contents.md)

## Repository Structure

```text
docs/
  templates/
  images/

Volume-1-Selenium-Java/
  00-Introduction/
  01-Java/
  02-Selenium/
  03-TestNG/
  04-Framework/
  05-REST-Assured/
  06-SQL/
  07-Git-Jenkins/
  08-Scenario/
  09-HR/
  Code/
  PDF/
```

## Documentation Templates

Reusable writing templates live in [docs/templates](docs/templates):

- [Question Template](docs/templates/question-template.md)
- [Chapter Template](docs/templates/chapter-template.md)
- [Book Style Guide](docs/templates/book-style-guide.md)

## Documentation Website

The documentation website is built with MkDocs and the Material theme.

Local setup:

```bash
pip install -r requirements.txt
mkdocs serve
```

Production builds are handled by GitHub Actions and deployed to GitHub Pages when changes are pushed to the `main` branch.

## Editorial Direction

This project aims to be:

- Original and publication-ready
- Practical for real QA automation interview preparation
- Clear enough for revision and deep enough for experienced candidates
- Organized for long-term expansion into multiple volumes
- Consistent in tone, structure, formatting, and technical accuracy

## Writing Standards

All chapters should use clean Markdown, concise explanations, practical examples, and consistent terminology. The book should avoid copied content, vague filler, and outdated tool assumptions. Every section should help the reader prepare for a real interview conversation.

## License

See [LICENSE](LICENSE).
