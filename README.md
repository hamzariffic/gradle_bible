# gradle_bible
A list of common gradle files I've been interacting with when building projects. 
# Gradle Android Kotlin Cheatsheet

A comprehensive reference for Gradle commands in Android development with Kotlin.

## Table of Contents
- [Basic Gradle Commands](#basic-gradle-commands)
- [Build Commands](#build-commands)
- [Inspection & Analysis](#inspection--analysis)
- [Testing](#testing)
- [Dependency Management](#dependency-management)
- [Deprecation Handling](#deprecation-handling)
- [Performance & Optimization](#performance--optimization)
- [Debugging & Troubleshooting](#debugging--troubleshooting)
- [Kotlin-Specific Commands](#kotlin-specific-commands)
- [CI/CD & Automation](#cicd--automation)

## Basic Gradle Commands

### Project Information
```bash
./gradlew --version                    # Show Gradle version
./gradlew projects                     # List all projects in build
./gradlew tasks                        # List all available tasks
./gradlew tasks --all                  # List all tasks including subtasks
./gradlew help --task <taskName>       # Get help for specific task
```

### Clean & Refresh
```bash
./gradlew clean                        # Clean build artifacts
./gradlew --refresh-dependencies       # Force refresh of dependencies
./gradlew --rerun-tasks               # Force rerun all tasks
./gradlew cleanBuildCache             # Clean build cache
```

## Build Commands

### Standard Builds
```bash
./gradlew build                        # Full build (compile, test, package)
./gradlew assemble                     # Compile and package without tests
./gradlew assembleDebug               # Build debug APK
./gradlew assembleRelease             # Build release APK
./gradlew bundle                       # Build Android App Bundle (AAB)
./gradlew bundleRelease               # Build release AAB
```

### Specific Build Types
```bash
./gradlew assembleDebug               # Debug build
./gradlew assembleRelease             # Release build
./gradlew install                      # Install on connected device
./gradlew installDebug                # Install debug build
./gradlew installRelease              # Install release build
./gradlew uninstallAll                # Uninstall from all devices
```

### Multi-module Projects
```bash
./gradlew :app:assembleDebug          # Build specific module
./gradlew :library:build              # Build library module
./gradlew app:dependencies            # Dependencies for app module
```

## Inspection & Analysis

### Project Structure
```bash
./gradlew projects                     # Show project hierarchy
./gradlew buildEnvironment            # Show build script dependencies
./gradlew components                   # Show software components
./gradlew model                        # Show configuration model
```

### Dependencies
```bash
./gradlew dependencies                 # Show all dependencies
./gradlew app:dependencies            # Dependencies for app module
./gradlew dependencyInsight --dependency <name>  # Analyze specific dependency
./gradlew app:dependencyInsight --dependency kotlin-stdlib
./gradlew dependencies --configuration debugCompileClasspath
```

### Build Analysis
```bash
./gradlew build --scan                # Generate build scan
./gradlew assembleDebug --profile     # Generate build profile
./gradlew tasks --group="build"       # Show build-related tasks
./gradlew properties                   # Show all project properties
```

### Code Quality & Inspection
```bash
./gradlew lint                         # Run Android lint
./gradlew lintDebug                   # Lint debug variant
./gradlew lintRelease                 # Lint release variant
./gradlew detekt                      # Run detekt (if configured)
./gradlew ktlintCheck                 # Check Kotlin code style
./gradlew ktlintFormat                # Format Kotlin code
```

## Testing

### Unit Tests
```bash
./gradlew test                         # Run all unit tests
./gradlew testDebug                   # Run debug unit tests
./gradlew testRelease                 # Run release unit tests
./gradlew test --tests="*LoginTest"   # Run specific test class
./gradlew test --tests="*.shouldLogin*" # Run tests matching pattern
```

### Android Tests
```bash
./gradlew connectedCheck              # Run instrumented tests
./gradlew connectedDebugAndroidTest   # Run debug instrumented tests
./gradlew createDebugCoverageReport   # Generate test coverage report
```

### Test Reports
```bash
./gradlew jacocoTestReport            # Generate coverage report
./gradlew testDebugUnitTest --continue # Continue after test failures
```

## Dependency Management

### Dependency Information
```bash
./gradlew dependencies                 # All dependencies tree
./gradlew app:dependencies --configuration implementation
./gradlew dependencyInsight --dependency <groupId:artifactId>
./gradlew buildEnvironment            # Build script dependencies
```

### Dependency Updates
```bash
./gradlew dependencyUpdates           # Check for dependency updates (requires plugin)
./gradlew refreshVersions             # Refresh versions (requires plugin)
```

### Dependency Verification
```bash
./gradlew dependencies --verify-metadata  # Verify dependency metadata
./gradlew resolveDependencies         # Resolve all dependencies
```

## Deprecation Handling

### Finding Deprecations
```bash
./gradlew build --warning-mode=all    # Show all warnings including deprecations
./gradlew help --warning-mode=all     # Enable all warnings
./gradlew build --warning-mode=summary # Show summary of warnings
./gradlew build --warning-mode=none   # Suppress warnings
```

### Gradle Deprecation Warnings
```bash
./gradlew build --warning-mode=all --stacktrace  # Full deprecation details
./gradlew wrapper --gradle-version=8.5 # Update Gradle wrapper
./gradlew wrapper --gradle-version=8.5 --distribution-type=all
```

### Android Gradle Plugin Deprecations
```bash
./gradlew lint --check-dependencies   # Check for deprecated dependencies
./gradlew dependencies | grep -i deprecated  # Find deprecated dependencies
```

## Performance & Optimization

### Build Performance
```bash
./gradlew build --profile             # Generate performance profile
./gradlew build --scan                # Detailed build analysis
./gradlew build --parallel            # Enable parallel execution
./gradlew build --max-workers=4       # Limit parallel workers
./gradlew build --offline             # Build without network access
```

### Cache Management
```bash
./gradlew build --build-cache         # Enable build cache
./gradlew cleanBuildCache             # Clean build cache
./gradlew build --no-build-cache      # Disable build cache
```

### Daemon Management
```bash
./gradlew --daemon                     # Use Gradle daemon
./gradlew --no-daemon                  # Don't use daemon
./gradlew --stop                       # Stop all daemons
./gradlew --status                     # Show daemon status
```

## Debugging & Troubleshooting

### Verbose Output
```bash
./gradlew build --info               # Info level logging
./gradlew build --debug              # Debug level logging
./gradlew build --stacktrace         # Show stack traces
./gradlew build --full-stacktrace    # Show full stack traces
```

### Dry Run & Diagnostics
```bash
./gradlew build --dry-run            # Show what would be executed
./gradlew help                       # Show help
./gradlew tasks --all                # Show all available tasks
./gradlew properties | grep -i version  # Find version properties
```

### Configuration Issues
```bash
./gradlew projects --info            # Detailed project info
./gradlew buildEnvironment --debug   # Debug build script dependencies
./gradlew dependencies --configuration runtimeClasspath
```

## Kotlin-Specific Commands

### Kotlin Compilation
```bash
./gradlew compileKotlin              # Compile Kotlin sources
./gradlew compileDebugKotlin         # Compile debug Kotlin
./gradlew compileReleaseKotlin       # Compile release Kotlin
./gradlew compileTestKotlin          # Compile test Kotlin
```

### Kotlin Code Quality
```bash
./gradlew ktlintCheck                # Check Kotlin code style
./gradlew ktlintFormat               # Auto-format Kotlin code
./gradlew detekt                     # Static code analysis
./gradlew detektMain                 # Detekt on main sources
./gradlew detektTest                 # Detekt on test sources
```

### Kotlin Documentation
```bash
./gradlew dokkaHtml                  # Generate HTML documentation
./gradlew dokkaJavadoc               # Generate Javadoc-style docs
./gradlew dokkaGfm                   # Generate GitHub Flavored Markdown docs
```

## CI/CD & Automation

### Continuous Integration
```bash
./gradlew build --continue           # Continue build after failures
./gradlew check                      # Run all verification tasks
./gradlew assemble check            # Build and verify
./gradlew publishToMavenLocal       # Publish to local Maven repository
```

### Release Builds
```bash
./gradlew assembleRelease --parallel
./gradlew bundleRelease              # Build release AAB
./gradlew publishReleaseBundle       # Publish to Play Store (with plugin)
./gradlew uploadCrashlyticsMappingFileRelease  # Upload ProGuard mappings
```

### Environment-Specific
```bash
./gradlew assembleDebug -Pdebug.enableLogging=true
./gradlew assembleRelease -Prelease.minify=false
./gradlew build -PbuildNumber=123
```

## Useful Gradle Properties

Add these to `gradle.properties` for better performance:

```properties
# Enable build cache
org.gradle.caching=true

# Enable parallel builds
org.gradle.parallel=true

# Configure JVM arguments
org.gradle.jvmargs=-Xmx4g -XX:+HeapDumpOnOutOfMemoryError

# Enable configuration cache (Gradle 6.6+)
org.gradle.configuration-cache=true

# Enable Kotlin incremental compilation
kotlin.incremental=true

# Android specific optimizations
android.useAndroidX=true
android.enableJetifier=true
android.enableR8.fullMode=true
```

## Common Task Combinations

```bash
# Full clean build with tests
./gradlew clean build --parallel

# Quick development build
./gradlew assembleDebug --parallel --build-cache

# Release build with analysis
./gradlew clean assembleRelease lint --profile --scan

# Test with coverage
./gradlew clean testDebugUnitTest jacocoTestReport

# Update dependencies and build
./gradlew --refresh-dependencies clean build
```

## Troubleshooting Common Issues

```bash
# Fix corrupted cache
./gradlew --stop
./gradlew cleanBuildCache
rm -rf ~/.gradle/caches

# Fix dependency resolution issues
./gradlew --refresh-dependencies clean build

# Debug build configuration
./gradlew build --debug --stacktrace

# Check for conflicting dependencies
./gradlew dependencies | grep "conflict"
./gradlew dependencyInsight --dependency <problematic-dependency>
```

---

## Tips & Best Practices

1. **Use Gradle Wrapper**: Always use `./gradlew` instead of global `gradle` command
2. **Enable Build Cache**: Add `org.gradle.caching=true` to `gradle.properties`
3. **Parallel Builds**: Use `--parallel` flag for multi-module projects
4. **Build Scans**: Use `--scan` to analyze build performance
5. **Incremental Builds**: Keep incremental compilation enabled for Kotlin
6. **Dependency Management**: Regularly check for updates and deprecations
7. **CI/CD**: Use `--continue` flag in CI to see all failures at once

---

*Last updated: 2024*
