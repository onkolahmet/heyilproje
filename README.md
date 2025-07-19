# Flight Roster Management System

A comprehensive .NET 8 application for managing flight crew and passenger assignments with automated roster generation, seat allocation, and multiple testing strategies.

## Quick Start

### Prerequisites
- .NET 8.0 SDK or later
- SQL Server (for database)

### Initial Setup

1. **Navigate to the project root** (where `MainSystem.sln` is located):
   ```bash
   cd <root_folder>
   ```

2. **Restore NuGet packages**:
   ```bash
   dotnet restore
   ```

3. **Build the solution**:
   ```bash
   dotnet build
   ```

4. **Discover and list all tests**:
   ```bash
   dotnet test --list-tests
   ```

5. **Run all tests**:
   ```bash
   dotnet test -v normal
   ```

## Cleanup


### Cleanup Scripts
The project includes automated cleanup scripts:

- **`cleanup.sh`** - Standard cleanup (removes bin/obj, temp files, test results)
```bash
# Make scripts executable
chmod +x cleanup.sh
# Run standard cleanup
./cleanup.sh
```

### Git Ignore
The project includes a comprehensive `.gitignore` file that prevents:
- Build artifacts (`bin/`, `obj/`)
- IDE files (`.vs/`, `.idea/`)
- Test results and logs
- User-specific files
- Performance test reports

## Project Structure

```
MainSystem/
├── MainSystem.sln                    # Solution file
├── MainSystem.Api/                   # Web API layer
├── MainSystem.Application/           # Application services & use cases
├── MainSystem.Domain/                # Domain entities & business logic
├── MainSystem.Infrastructure/        # Data access & external services
├── MainSystem.Tests/                 # Comprehensive test suite
│   ├── Unit/                        # Unit tests
│   ├── Integration/                 # API & database integration tests
│   ├── BlackBox/                    # Input validation tests
│   ├── Acceptance/                  # Feature-based acceptance tests
│   ├── Security/                    # Authentication & authorization tests
│   └── Performance/                 # Load & stress tests
├── cleanup.sh                       # Cleanup script
└── README.md                        # This file
```

## Testing Strategy

The project includes comprehensive testing at multiple levels:

### Test Types
- **Unit Tests** - Method/class level testing
- **Integration Tests** - API & database interaction testing
- **Black Box Tests** - Input/output validation
- **Acceptance Tests** - User story-driven feature testing
- **Security Tests** - Authentication & authorization
- **Performance Tests** - Response time & throughput
- **Load/Stress Tests** - System behavior under load

### Running Tests

```bash
# List all available tests
dotnet test --list-tests

# Run all tests
dotnet test -v normal

# Run specific test categories
dotnet test --filter "Unit" -v normal
dotnet test --filter "Integration" -v normal
dotnet test --filter "SimpleTests" -v normal

# Run tests with detailed output
dotnet test --logger "console;verbosity=detailed"
```

## Core Features

- **Flight Roster Generation** - Automatic crew and passenger assignment
- **Seat Assignment Algorithms** - Multiple strategies (Greedy, Group-aware, Random)
- **Crew Management** - Pilot and cabin crew validation with business rules
- **Multi-format Export** - JSON export with plane view visualization
- **Role-based Security** - Admin/Viewer access control
- **External API Integration** - Flight, crew, and passenger data sources

## 🔍 Troubleshooting

### If `dotnet test --list-tests` shows errors:
1. Make sure you're in the project root (where `MainSystem.sln` is)
2. Run cleanup: `./cleanup.sh`
3. Restore packages: `dotnet restore`
4. Build: `dotnet build`
5. Try again: `dotnet test --list-tests`

##  Notes

- Always run commands from the **solution root** directory
- Use cleanup scripts regularly to maintain a clean environment  
- The `.gitignore` file prevents build artifacts from being committed
- Integration tests require the API to be running
- Performance tests are optional and can be disabled if causing issues

