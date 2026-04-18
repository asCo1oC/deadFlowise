# CVE-2025-59528: Flowise CustomMCP Remote Code Execution

> ⚠️ **WARNING**: This tool is for educational and authorized security testing purposes only. 
> Use responsibly and only on systems you have explicit permission to test.

![Python](https://img.shields.io/badge/python-3.7+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-POC-yellow.svg)

## 📋 Описание

Эксплойт для уязвимости **CVE-2025-59528** в платформе Flowise, позволяющей выполнить произвольный код через инъекцию JavaScript в параметр `mcpServerConfig` узла `CustomMCP`.

### 🔍 Техническая суть уязвимости

Flowise предоставляет визуальный конструктор для создания AI-агентов. Узел `CustomMCP` позволяет настраивать интеграцию с внешними MCP-серверами через поле `mcpServerConfig`.

**Уязвимость**: содержимое `mcpServerConfig` выполняется как JavaScript-код без должной санитизации, что позволяет внедрить произвольный код, выполняемый в контексте процесса Node.js.

### 🎯 Условие успешной эксплуатации

| Требование | Статус |
|------------|--------|
| Доступ к веб-интерфейсу Flowise | ✅ |
| Аутентификация как пользователь с правами на редактирование схем | ✅ |
| Валидные session cookies или API-токен | ✅ |
| Уязвимая версия Flowise (проверено на 3.0.5) | ✅ |

## 🛠 Требования

### Системные
- Python 3.7+
- Linux / macOS / WSL

### Зависимости
```bash
pip install requests
