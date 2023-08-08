SonarQube is a free and open source platform for monitoring code quality.

Relies on existing tools for some aspects of analysis.

Works with multiple languages.

Architecture
- Client for running analysis
	- `sonar-runner`
	- [[Maven]] plugin
- Server for viewing and managing analysis data
- Database for storing analysis data

Manage code quality across time for multiple projects all centralized on a single instance.

## Seven Axes of Quality

All seven aren't available for every language!

- Potential bugs
- Coding rules
- Tests
- Duplications
- Comments
- Architecture and design
- Complexity

#### Bugs and Coding Rules
- Ranked by severity
- Severity counts
- Compliance percentage as a function of code lines

#### Tests
- unit test coverage
- passing, failing, error counts

#### Comments
- Documentation coverage

#### Duplication
- Identify duplicate code sections

#### Architecture and design
- tidiness of a program's architecture
- class size and complexity
- bad practices

#### Complexity
- How much logic each class/method contains


## Interface

- Navigate directories and files
- View files with respect to analysis
- View trends

