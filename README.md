# Local Event Organizer App

A comprehensive .NET C# application designed to streamline local event management and organization.

## Project Overview

The Local Event Organizer App is a desktop/web application that helps users plan, organize, and manage local events efficiently. This project addresses the need for a user-friendly event management solution that caters to community organizers, small businesses, and individuals looking to host events.

## Problem Statement

Local event organizers often face challenges in managing multiple aspects of event planning including:
- Participant registration and management
- Venue booking and scheduling
- Communication with attendees
- Budget tracking
- Promotion and marketing

This application provides an integrated solution to these challenges, offering a centralized platform for all event management needs.

## Features

### Core Features
- **Event Creation & Management**: Create, edit, and delete events with detailed information
- **User Registration & Authentication**: Secure user accounts with role-based access
- **Attendee Management**: Track registrations, check-ins, and participant information
- **Venue Management**: Manage venue bookings and availability
- **Budget Tracking**: Monitor event expenses and revenue
- **Notification System**: Send updates and reminders to attendees
- **Reporting & Analytics**: Generate reports on event performance and attendance

### Technical Features
- Responsive web interface
- Real-time updates
- Data export capabilities
- Search and filtering functionality
- Mobile-friendly design

## Technology Stack

- **Framework**: .NET 8
- **Language**: C#
- **Frontend**: ASP.NET Core MVC / Blazor
- **Database**: SQL Server / Entity Framework Core
- **Authentication**: ASP.NET Core Identity
- **UI Framework**: Bootstrap / Tailwind CSS
- **Version Control**: Git

## Team Members

| # | Student Name | Student ID |
|---|--------------|------------|
| 1 | Mugisha Julien | 26967 |
| 2 | Ntwari Ashimwe Fiacre | 27438 |
| 3 | Ndahiriwe Bienfait | 25959 |
| 4 | Niyigena Claire | 26693 |

## Project Structure

```
LocalEventOrganizerApp/
├── src/
│   ├── LocalEventOrganizerApp.Web/          # Web application
│   ├── LocalEventOrganizerApp.Core/         # Business logic
│   ├── LocalEventOrganizerApp.Data/         # Data access layer
│   └── LocalEventOrganizerApp.Models/       # Domain models
├── tests/
│   ├── LocalEventOrganizerApp.UnitTests/    # Unit tests
│   └── LocalEventOrganizerApp.IntegrationTests/ # Integration tests
├── docs/                                     # Documentation
└── README.md
```

## Getting Started

### Prerequisites
- .NET 8 SDK
- Visual Studio 2022 or Visual Studio Code
- SQL Server (or SQL Server Express)
- Git

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Julienmj/Group12-Dotnet-project-.git
   cd Group12-Dotnet-project-
   ```

2. Restore dependencies:
   ```bash
   dotnet restore
   ```

3. Update database connection string in `appsettings.json`

4. Run database migrations:
   ```bash
   dotnet ef database update
   ```

5. Run the application:
   ```bash
   dotnet run
   ```

### Configuration

Update the following configuration in `appsettings.json`:
- Database connection string
- Email settings for notifications
- File upload paths
- API keys (if using external services)

## Development Workflow

### Branching Strategy
- `main`: Production-ready code
- `develop`: Integration branch for features
- `feature/*`: Individual feature branches
- `bugfix/*`: Bug fixes

### Commit Convention
- `feat`: New features
- `fix`: Bug fixes
- `docs`: Documentation updates
- `refactor`: Code refactoring
- `test`: Test additions/modifications

## Testing

Run tests using:
```bash
dotnet test
```

## Deployment

### Development
- Local development server
- IIS Express

### Production
- Azure App Service
- Docker containers
- IIS hosting

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contact

For questions or support, please contact:
- Project Repository: https://github.com/Julienmj/Group12-Dotnet-project-
- Team Lead: Mugisha Julien (Student ID: 26967)

## Project Timeline

### Phase 1: Project Setup & Planning ✅
- Project description and problem statement
- Team formation and role assignment
- Development environment setup

### Phase 2: Core Development (In Progress)
- Database design and implementation
- User authentication system
- Basic event management features

### Phase 3: Advanced Features
- Notification system
- Reporting and analytics
- Mobile responsiveness

### Phase 4: Testing & Deployment
- Comprehensive testing
- Performance optimization
- Production deployment

---

**Note**: This project is part of the .NET C# development course and represents the collaborative effort of Group 12.
