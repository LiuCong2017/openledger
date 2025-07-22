# OpenLedger: Open-Source Personal Finance Tracker

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)[![GitHub stars](https://img.shields.io/github/stars/LiuCong2017/openledger?style=social)](https://github.com/LiuCong2017/openledger)[![GitHub issues](https://img.shields.io/github/issues/LiuCong2017/openledger)](https://github.com/LiuCong2017/openledger/issues)[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

OpenLedger is a free, open-source personal finance tracking application designed to help users manage their income, expenses, budgets, and financial reports effortlessly. Inspired by popular budgeting apps, it provides a simple, intuitive interface for recording transactions, categorizing expenses, setting budgets, and visualizing financial data through charts and summaries.

This project is built with modern technologies to ensure cross-platform compatibility, data privacy (local-first storage), and extensibility for community contributions. As an open-source initiative, we welcome developers, designers, and users to contribute and improve it.

## Table of Contents

- [Project Overview](#project-overview)
- [Requirements Specification](#requirements-specification)
  - [Functional Requirements](#functional-requirements)
  - [Non-Functional Requirements](#non-functional-requirements)
- [Technical Architecture](#technical-architecture)
  - [High-Level Architecture](#high-level-architecture)
  - [Technology Stack](#technology-stack)
  - [Data Model](#data-model)
  - [Security and Privacy](#security-and-privacy)
- [Installation](#installation)
- [Usage](#usage)
- [Development Roadmap](#development-roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Project Overview

OpenLedger aims to be the go-to open-source alternative for personal finance management. Based on the provided example screenshots (featuring transaction lists, category breakdowns, budget panels, monthly summaries, and charts), the app focuses on core features like transaction logging, budgeting, and analytics. It is designed for mobile users but can be extended to web/desktop.

Key goals:

- **User-Centric**: Simple UI for quick entry and insightful reports.
- **Privacy-Focused**: Local storage by default, with optional cloud sync.
- **Extensible**: Modular architecture for adding features like multi-currency or integrations.
- **Community-Driven**: Fully open-source under MIT license.

## Requirements Specification

### Functional Requirements

Based on the example UI elements (transaction lists, yellow budget panels, charts, and calendars), the following features are prioritized:

1. **Transaction Management**:
   - Add, edit, delete income/expense transactions.
   - Fields: Amount, Date, Category (e.g., Food, Transport, Salary), Account (e.g., Cash, Bank), Notes, Tags.
   - Support for recurring transactions (e.g., monthly subscriptions).

2. **Category and Account Management**:
   - Predefined and custom categories with icons.
   - Multiple accounts with balance tracking and transfers between accounts.

3. **Budgeting**:
   - Set monthly/annual budgets per category.
   - Visual progress bars (e.g., yellow panels showing spent vs. allocated).
   - Alerts for approaching budget limits.

4. **Reporting and Analytics**:
   - Monthly/weekly summaries with pie charts, bar graphs, and line trends.
   - Filter by date range, category, or account.
   - Export reports as CSV/PDF.

5. **Calendar View**:
   - Daily transaction overview with calendar integration.
   - Highlight days with high spending or income.

6. **Search and Filtering**:
   - Search transactions by keyword, amount, or date.
   - Advanced filters for custom reports.

7. **Data Import/Export**:
   - Import from CSV/Excel.
   - Backup and restore data.

8. **Additional Features** (Future-Proof):
   - Multi-currency support with exchange rates.
   - Cloud sync (e.g., via Firebase or self-hosted server).
   - User authentication for multi-user scenarios.

### Non-Functional Requirements

- **Performance**: Load times < 2 seconds for core operations; handle up to 10,000 transactions efficiently.
- **Usability**: Intuitive mobile-first UI, supporting dark mode and accessibility (e.g., WCAG compliance).
- **Scalability**: Modular design for easy addition of features without performance degradation.
- **Reliability**: Data persistence with automatic backups; error handling for invalid inputs.
- **Internationalization**: Support for multiple languages (starting with English and Chinese).
- **Platform Support**: Cross-platform (iOS, Android) with potential web extension.
- **Offline Capability**: Fully functional without internet; sync when online.

## Technical Architecture

### High-Level Architecture

OpenLedger follows a client-side architecture with optional backend for sync, emphasizing a local-first approach to ensure privacy.

- **Frontend**: Mobile app built with cross-platform framework for native performance.
- **Backend (Optional)**: Cloud service for data synchronization and multi-device access.
- **Data Layer**: Local database for persistence.
- **Modular Components**: Separate modules for UI, business logic, and data access (e.g., MVVM pattern).

Architecture Diagram (Conceptual):

![diagram](https://github.com/LiuCong2017/openledger/blob/main/assets/diagram.png)

### Technology Stack

- **Frontend**: Flutter (Dart) for cross-platform mobile development – chosen for its high performance, beautiful UI, and rapid development. 
- **State Management**: Provider or Riverpod for efficient state handling in Flutter.
- **Database**: SQLite with sqflite package for local storage – lightweight and secure.
- **Charts and Visuals**: fl_chart library for interactive graphs (pie, bar, line charts).
- **Optional Backend**: Node.js with Express and MongoDB for cloud sync; or Firebase for no-code integration.
- **Testing**: Unit tests with flutter_test; integration tests for UI flows.
- **CI/CD**: GitHub Actions for automated builds, tests, and deployments.
- **Other Tools**: Git for version control; intl for localization; hive for potential NoSQL alternatives if needed.

### Data Model

Core entities (using SQLite schema as example):

- **Transactions Table**:
  - id (PK), amount (double), date (datetime), category_id (FK), account_id (FK), type (income/expense), notes (text), tags (json).

- **Categories Table**:
  - id (PK), name (text), icon (text), is_income (bool).

- **Accounts Table**:
  - id (PK), name (text), balance (double), currency (text).

- **Budgets Table**:
  - id (PK), category_id (FK), period (month/year), allocated (double), spent (double).

Relationships: One-to-Many (e.g., Account to Transactions).

### Security and Privacy

- **Data Encryption**: Encrypt sensitive data in local DB using flutter_secure_storage.
- **No Tracking**: No analytics without user consent.
- **Open-Source Audit**: Code is public for community review.
- **Cloud Security**: If enabled, use HTTPS, OAuth, and encrypted sync.

## Installation

1. Clone the repo: `git clone https://github.com/LiuCong2017/openledger.git`
2. Install Flutter: Follow [official guide](https://flutter.dev/docs/get-started/install).
3. Run `flutter pub get` to install dependencies.
4. Build and run: `flutter run` (for Android/iOS emulator).

For production builds: `flutter build apk` or `flutter build ios`.

## Usage

- Launch the app and start adding transactions from the home screen.
- Navigate to Budgets to set limits.
- View Reports for insights.
- Customize categories in Settings.

Detailed user guide in [docs/user-guide.md](docs/user-guide.md).

## Development Roadmap

- **v1.0 (MVP)**: Core transaction logging, basic reports, local storage.
- **v1.1**: Budgeting and charts.
- **v2.0**: Cloud sync, multi-currency.
- **Future**: Web version, AI insights (e.g., spending predictions).

Track progress in [Issues](https://github.com/LiuCong2017/openledger/issues) and [Projects](https://github.com/LiuCong2017/openledger/projects).

## Contributing

We welcome contributions! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on pull requests, code style, and issue reporting.

- Fork the repo.
- Create a feature branch: `git checkout -b feature/new-feature`.
- Commit changes: `git commit -m 'Add new feature'`.
- Push: `git push origin feature/new-feature`.
- Open a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

- Project Lead: [Kavin Liu] (kavin.c.liu@gmail.com)
- GitHub: [LiuCong2017](https://github.com/LiuCong2017)
- Discussions: Use GitHub Discussions for questions and ideas.

Happy budgeting! 💰
