# LabRay — Laboratory Management System

LabRay is a C# Windows Forms desktop application prototype created as a university project. The interface is organised around login/registration, a home dashboard, doctor information, appointment/channeling screens, and report-delivery request forms.

> **Project status:** prototype / work in progress. This repository is not ready for production use and should not be used to store or process real patient information.

## Technology

- C#
- Windows Forms
- .NET Framework 4.7.2
- ADO.NET with SQL Server LocalDB
- Bunifu UI and Guna UI controls

## Repository structure

- `src/` — Windows Forms source files, designer files, project file, and local database files
- `src/LabRay.csproj` — Visual Studio project

## Current functionality represented in the source

- Login and administrator registration screens
- Dashboard navigation between application screens
- Doctor listing and appointment/channeling UI
- Appointment listing, update, and delete operations
- Report-delivery request forms (currently display confirmation messages; they do not send reports)

The source should be reviewed before relying on any workflow. Some screens are placeholders and some actions are not fully implemented.

## Build status and setup notes

The checked-in project currently has environment-specific build dependencies that prevent a reliable clean-clone setup:

1. Open `src/LabRay.csproj` in Visual Studio on Windows with the .NET Framework 4.7.2 developer targeting pack and SQL Server LocalDB installed.
2. The project references Bunifu and Guna UI assemblies through absolute/relative paths outside this repository. Those dependencies must be obtained through legitimate vendor channels and the project references configured locally.
3. The project file also references resource/configuration files that are not currently present in the repository tree. A clean build may therefore fail until the project structure is repaired.
4. Several database connection strings in the source point to a developer-specific Windows folder. Database paths and connection strings need to be centralised and configured for the local machine before database-backed screens can run.

No clean-clone build or automated test result is currently claimed.

## Important security limitations

This is a learning prototype, not a secure clinical system. Source review identified issues that need to be fixed before real use:

- Login and registration code stores/checks passwords as plain text.
- SQL statements in authentication and appointment workflows are built by concatenating user input rather than using parameters.
- Database connection strings contain machine-specific file paths.
- The registration and login code refer to different database file paths.
- The application has not been assessed for privacy, access control, audit logging, backups, or clinical data integrity.

**Do not enter real patient details, passwords, or other sensitive information.** Use synthetic demonstration data only.

## Suggested next engineering steps

1. Restore the missing project resources and remove machine-specific build references.
2. Move database configuration into a single environment-specific configuration mechanism.
3. Replace SQL string concatenation with parameterised commands.
4. Implement password hashing and a safe account-registration/login flow.
5. Add validation and automated tests for authentication and appointment operations.
6. Add a reproducible setup guide and verify a clean build on a fresh Windows environment.

## Author

Developed by [LeeshaniZ](https://github.com/LeeshaniZ).
