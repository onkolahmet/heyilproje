# Flight Roster Management System

A comprehensive .NET 8 application for managing flight crew and passenger assignments with automated roster generation, seat allocation, and multiple testing strategies.

## 🚀 Quick Start

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

## 🧹 Cleanup & Maintenance

### Quick Cleanup (when things get messy)
If you encounter build issues or want to clean build artifacts:

```bash
# Quick one-liner cleanup
find . \( -name "bin" -o -name "obj" \) -type d -exec rm -rf {} + 2>/dev/null

# Then restore and rebuild
dotnet restore
dotnet build
```

### Cleanup Scripts
The project includes automated cleanup scripts:

- **`cleanup.sh`** - Standard cleanup (removes bin/obj, temp files, test results)
- **`deep-cleanup.sh`** - Nuclear option (aggressive cleanup including caches)

```bash
# Make scripts executable
chmod +x cleanup.sh
chmod +x deep-cleanup.sh

# Run standard cleanup
./cleanup.sh

# Run deep cleanup (when things are really broken)
./deep-cleanup.sh
```

### Git Ignore
The project includes a comprehensive `.gitignore` file that prevents:
- Build artifacts (`bin/`, `obj/`)
- IDE files (`.vs/`, `.idea/`)
- Test results and logs
- User-specific files
- Performance test reports

## 🏗️ Project Structure

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
├── deep-cleanup.sh                  # Deep cleanup script
└── README.md                        # This file
```

## 🧪 Testing Strategy

The project includes comprehensive testing at multiple levels:

### Test Types
- **✅ Unit Tests** - Method/class level testing
- **✅ Integration Tests** - API & database interaction testing
- **✅ Black Box Tests** - Input/output validation
- **✅ Acceptance Tests** - User story-driven feature testing
- **🔄 Security Tests** - Authentication & authorization
- **🔄 Performance Tests** - Response time & throughput
- **🔄 Load/Stress Tests** - System behavior under load

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

## 🎯 Core Features

- **Flight Roster Generation** - Automatic crew and passenger assignment
- **Seat Assignment Algorithms** - Multiple strategies (Greedy, Group-aware, Random)
- **Crew Management** - Pilot and cabin crew validation with business rules
- **Multi-format Export** - JSON export with plane view visualization
- **Role-based Security** - Admin/Viewer access control
- **External API Integration** - Flight, crew, and passenger data sources

## 🔧 Development Workflow

### Starting Development
```bash
# 1. Clean any previous builds
./cleanup.sh

# 2. Restore packages
dotnet restore

# 3. Build solution
dotnet build

# 4. Verify tests
dotnet test --list-tests

# 5. Run API (for integration tests)
cd MainSystem.Api
dotnet run
```

### When Things Go Wrong
```bash
# Nuclear cleanup and rebuild
./deep-cleanup.sh
dotnet restore
dotnet build
dotnet test --list-tests
```

### Common Issues

1. **Build Failures**: Run `./cleanup.sh` then `dotnet restore`
2. **Test Discovery Issues**: Ensure you're in the solution root, then run `dotnet test --list-tests`
3. **Package Conflicts**: Run `./deep-cleanup.sh` to clear all caches
4. **Performance Test Errors**: NBomber tests may need additional setup

## 🔍 Troubleshooting

### If `dotnet test --list-tests` shows errors:
1. Make sure you're in the project root (where `MainSystem.sln` is)
2. Run cleanup: `./cleanup.sh`
3. Restore packages: `dotnet restore`
4. Build: `dotnet build`
5. Try again: `dotnet test --list-tests`

### If integration tests fail:
1. Make sure the API is running: `dotnet run` in `MainSystem.Api/`
2. Check database connection strings in `appsettings.json`
3. Verify authentication setup

### Performance test issues:
- NBomber package conflicts can be resolved by commenting out problematic imports
- Some performance tests may require external services to be running

## 📝 Notes

- Always run commands from the **solution root** directory
- Use cleanup scripts regularly to maintain a clean environment  
- The `.gitignore` file prevents build artifacts from being committed
- Integration tests require the API to be running
- Performance tests are optional and can be disabled if causing issues

## 🤝 Contributing

1. Run cleanup before starting: `./cleanup.sh`
2. Make your changes
3. Test your changes: `dotnet test`
4. Clean before committing: `./cleanup.sh`
