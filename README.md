# 🐘 Gradle Android Kotlin Cheatsheet ⚡

<div align="center">

![Gradle](https://img.shields.io/badge/Gradle-02303A.svg?style=for-the-badge&logo=Gradle&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/kotlin-%237F52FF.svg?style=for-the-badge&logo=kotlin&logoColor=white)

**A comprehensive reference for Gradle commands in Android development with Kotlin** 📱

</div>

---

## 📋 Table of Contents
- [🏗️ Basic Gradle Commands](#️-basic-gradle-commands)
- [⚙️ Build Commands](#️-build-commands)
- [🔍 Inspection & Analysis](#-inspection--analysis)
- [🧪 Testing](#-testing)
- [📦 Dependency Management](#-dependency-management)
- [⚠️ Deprecation Handling](#️-deprecation-handling)
- [🚀 Performance & Optimization](#-performance--optimization)
- [🐛 Debugging & Troubleshooting](#-debugging--troubleshooting)
- [🎯 Kotlin-Specific Commands](#-kotlin-specific-commands)
- [🔄 CI/CD & Automation](#-cicd--automation)

---

## 🏗️ Basic Gradle Commands

<details>
<summary>📊 <strong>Project Information</strong></summary>

```bash
./gradlew --version                    # 🏷️ Show Gradle version
./gradlew projects                     # 📂 List all projects in build
./gradlew tasks                        # 📝 List all available tasks
./gradlew tasks --all                  # 📋 List all tasks including subtasks
./gradlew help --task <taskName>       # ❓ Get help for specific task
```

</details>

<details>
<summary>🧹 <strong>Clean & Refresh</strong></summary>

```bash
./gradlew clean                        # 🧹 Clean build artifacts
./gradlew --refresh-dependencies       # 🔄 Force refresh of dependencies
./gradlew --rerun-tasks               # ↩️ Force rerun all tasks
./gradlew cleanBuildCache             # 🗑️ Clean build cache
```

</details>

---

## ⚙️ Build Commands

<details>
<summary>🏭 <strong>Standard Builds</strong></summary>

```bash
./gradlew build                        # 🏗️ Full build (compile, test, package)
./gradlew assemble                     # 📦 Compile and package without tests
./gradlew assembleDebug               # 🐞 Build debug APK
./gradlew assembleRelease             # 🚀 Build release APK
./gradlew bundle                       # 📱 Build Android App Bundle (AAB)
./gradlew bundleRelease               # 🎯 Build release AAB
```

</details>

<details>
<summary>🎨 <strong>Specific Build Types</strong></summary>

```bash
./gradlew assembleDebug               # 🐞 Debug build
./gradlew assembleRelease             # 🚀 Release build
./gradlew install                      # 📲 Install on connected device
./gradlew installDebug                # 🐞📲 Install debug build
./gradlew installRelease              # 🚀📲 Install release build
./gradlew uninstallAll                # 🗑️📱 Uninstall from all devices
```

</details>

<details>
<summary>🏢 <strong>Multi-module Projects</strong></summary>

```bash
./gradlew :app:assembleDebug          # 🎯 Build specific module
./gradlew :library:build              # 📚 Build library module
./gradlew app:dependencies            # 🔗 Dependencies for app module
```

</details>

---

## 🔍 Inspection & Analysis

<details>
<summary>🏗️ <strong>Project Structure</strong></summary>

```bash
./gradlew projects                     # 🌳 Show project hierarchy
./gradlew buildEnvironment            # 🏗️ Show build script dependencies
./gradlew components                   # 🧩 Show software components
./gradlew model                        # 📐 Show configuration model
```

</details>

<details>
<summary>🔗 <strong>Dependencies</strong></summary>

```bash
./gradlew dependencies                 # 🌲 Show all dependencies
./gradlew app:dependencies            # 🎯 Dependencies for app module
./gradlew dependencyInsight --dependency <name>  # 🔍 Analyze specific dependency
./gradlew app:dependencyInsight --dependency kotlin-stdlib
./gradlew dependencies --configuration debugCompileClasspath
```

</details>

<details>
<summary>📊 <strong>Build Analysis</strong></summary>

```bash
./gradlew build --scan                # 📈 Generate build scan
./gradlew assembleDebug --profile     # ⏱️ Generate build profile
./gradlew tasks --group="build"       # 🏷️ Show build-related tasks
./gradlew properties                   # ⚙️ Show all project properties
```

</details>

<details>
<summary>🔬 <strong>Code Quality & Inspection</strong></summary>

```bash
./gradlew lint                         # 🔍 Run Android lint
./gradlew lintDebug                   # 🐞🔍 Lint debug variant
./gradlew lintRelease                 # 🚀🔍 Lint release variant
./gradlew detekt                      # 🕵️ Run detekt (if configured)
./gradlew ktlintCheck                 # ✅ Check Kotlin code style
./gradlew ktlintFormat                # 🎨 Format Kotlin code
```

</details>

---

## 🧪 Testing

<details>
<summary>🔬 <strong>Unit Tests</strong></summary>

```bash
./gradlew test                         # 🧪 Run all unit tests
./gradlew testDebug                   # 🐞🧪 Run debug unit tests
./gradlew testRelease                 # 🚀🧪 Run release unit tests
./gradlew test --tests="*LoginTest"   # 🎯 Run specific test class
./gradlew test --tests="*.shouldLogin*" # 🔍 Run tests matching pattern
```

</details>

<details>
<summary>📱 <strong>Android Tests</strong></summary>

```bash
./gradlew connectedCheck              # 📱🧪 Run instrumented tests
./gradlew connectedDebugAndroidTest   # 🐞📱 Run debug instrumented tests
./gradlew createDebugCoverageReport   # 📊 Generate test coverage report
```

</details>

<details>
<summary>📋 <strong>Test Reports</strong></summary>

```bash
./gradlew jacocoTestReport            # 📈 Generate coverage report
./gradlew testDebugUnitTest --continue # ➡️ Continue after test failures
```

</details>

---

## 📦 Dependency Management

<details>
<summary>📊 <strong>Dependency Information</strong></summary>

```bash
./gradlew dependencies                 # 🌲 All dependencies tree
./gradlew app:dependencies --configuration implementation
./gradlew dependencyInsight --dependency <groupId:artifactId>
./gradlew buildEnvironment            # 🏗️ Build script dependencies
```

</details>

<details>
<summary>🔄 <strong>Dependency Updates</strong></summary>

```bash
./gradlew dependencyUpdates           # ⬆️ Check for dependency updates (requires plugin)
./gradlew refreshVersions             # 🔄 Refresh versions (requires plugin)
```

</details>

<details>
<summary>✅ <strong>Dependency Verification</strong></summary>

```bash
./gradlew dependencies --verify-metadata  # ✅ Verify dependency metadata
./gradlew resolveDependencies         # 🔗 Resolve all dependencies
```

</details>

---

## ⚠️ Deprecation Handling

<details>
<summary>🔍 <strong>Finding Deprecations</strong></summary>

```bash
./gradlew build --warning-mode=all    # ⚠️ Show all warnings including deprecations
./gradlew help --warning-mode=all     # 🔔 Enable all warnings
./gradlew build --warning-mode=summary # 📋 Show summary of warnings
./gradlew build --warning-mode=none   # 🔇 Suppress warnings
```

</details>

<details>
<summary>🐘 <strong>Gradle Deprecation Warnings</strong></summary>

```bash
./gradlew build --warning-mode=all --stacktrace  # 📚 Full deprecation details
./gradlew wrapper --gradle-version=8.5 # ⬆️ Update Gradle wrapper
./gradlew wrapper --gradle-version=8.5 --distribution-type=all
```

</details>

<details>
<summary>🤖 <strong>Android Gradle Plugin Deprecations</strong></summary>

```bash
./gradlew lint --check-dependencies   # 🔍 Check for deprecated dependencies
./gradlew dependencies | grep -i deprecated  # 🔍 Find deprecated dependencies
```

</details>

---

## 🚀 Performance & Optimization

<details>
<summary>⚡ <strong>Build Performance</strong></summary>

```bash
./gradlew build --profile             # 📊 Generate performance profile
./gradlew build --scan                # 📈 Detailed build analysis
./gradlew build --parallel            # ⚡ Enable parallel execution
./gradlew build --max-workers=4       # 👥 Limit parallel workers
./gradlew build --offline             # 🔌 Build without network access
```

</details>

<details>
<summary>💾 <strong>Cache Management</strong></summary>

```bash
./gradlew build --build-cache         # 💾 Enable build cache
./gradlew cleanBuildCache             # 🧹 Clean build cache
./gradlew build --no-build-cache      # ❌ Disable build cache
```

</details>

<details>
<summary>🔧 <strong>Daemon Management</strong></summary>

```bash
./gradlew --daemon                     # 🔧 Use Gradle daemon
./gradlew --no-daemon                  # 🚫 Don't use daemon
./gradlew --stop                       # ⏹️ Stop all daemons
./gradlew --status                     # 📊 Show daemon status
```

</details>

---

## 🐛 Debugging & Troubleshooting

<details>
<summary>📢 <strong>Verbose Output</strong></summary>

```bash
./gradlew build --info               # ℹ️ Info level logging
./gradlew build --debug              # 🐛 Debug level logging
./gradlew build --stacktrace         # 📚 Show stack traces
./gradlew build --full-stacktrace    # 📖 Show full stack traces
```

</details>

<details>
<summary>🔍 <strong>Dry Run & Diagnostics</strong></summary>

```bash
./gradlew build --dry-run            # 👁️ Show what would be executed
./gradlew help                       # ❓ Show help
./gradlew tasks --all                # 📋 Show all available tasks
./gradlew properties | grep -i version  # 🔍 Find version properties
```

</details>

<details>
<summary>⚙️ <strong>Configuration Issues</strong></summary>

```bash
./gradlew projects --info            # ℹ️ Detailed project info
./gradlew buildEnvironment --debug   # 🐛 Debug build script dependencies
./gradlew dependencies --configuration runtimeClasspath
```

</details>

---

## 🎯 Kotlin-Specific Commands

<details>
<summary>⚙️ <strong>Kotlin Compilation</strong></summary>

```bash
./gradlew compileKotlin              # ⚙️ Compile Kotlin sources
./gradlew compileDebugKotlin         # 🐞⚙️ Compile debug Kotlin
./gradlew compileReleaseKotlin       # 🚀⚙️ Compile release Kotlin
./gradlew compileTestKotlin          # 🧪⚙️ Compile test Kotlin
```

</details>

<details>
<summary>✨ <strong>Kotlin Code Quality</strong></summary>

```bash
./gradlew ktlintCheck                # ✅ Check Kotlin code style
./gradlew ktlintFormat               # 🎨 Auto-format Kotlin code
./gradlew detekt                     # 🕵️ Static code analysis
./gradlew detektMain                 # 🎯 Detekt on main sources
./gradlew detektTest                 # 🧪 Detekt on test sources
```

</details>

<details>
<summary>📚 <strong>Kotlin Documentation</strong></summary>

```bash
./gradlew dokkaHtml                  # 📄 Generate HTML documentation
./gradlew dokkaJavadoc               # 📖 Generate Javadoc-style docs
./gradlew dokkaGfm                   # 📝 Generate GitHub Flavored Markdown docs
```

</details>

---

## 🔄 CI/CD & Automation

<details>
<summary>🔄 <strong>Continuous Integration</strong></summary>

```bash
./gradlew build --continue           # ➡️ Continue build after failures
./gradlew check                      # ✅ Run all verification tasks
./gradlew assemble check            # 🏗️✅ Build and verify
./gradlew publishToMavenLocal       # 📦 Publish to local Maven repository
```

</details>

<details>
<summary>🚀 <strong>Release Builds</strong></summary>

```bash
./gradlew assembleRelease --parallel # 🚀⚡ Parallel release build
./gradlew bundleRelease              # 📱 Build release AAB
./gradlew publishReleaseBundle       # 🎯 Publish to Play Store (with plugin)
./gradlew uploadCrashlyticsMappingFileRelease  # 🗺️ Upload ProGuard mappings
```

</details>

<details>
<summary>🌍 <strong>Environment-Specific</strong></summary>

```bash
./gradlew assembleDebug -Pdebug.enableLogging=true
./gradlew assembleRelease -Prelease.minify=false
./gradlew build -PbuildNumber=123
```

</details>

---

## ⚙️ Useful Gradle Properties

> 💡 **Pro Tip**: Add these to `gradle.properties` for better performance

```properties
# 💾 Enable build cache
org.gradle.caching=true

# ⚡ Enable parallel builds
org.gradle.parallel=true

# 🧠 Configure JVM arguments
org.gradle.jvmargs=-Xmx4g -XX:+HeapDumpOnOutOfMemoryError

# 🚀 Enable configuration cache (Gradle 6.6+)
org.gradle.configuration-cache=true

# 🎯 Enable Kotlin incremental compilation
kotlin.incremental=true

# 🤖 Android specific optimizations
android.useAndroidX=true
android.enableJetifier=true
android.enableR8.fullMode=true
```

---

## 🔗 Common Task Combinations

<div align="center">

| 🎯 **Task** | 💻 **Command** |
|-------------|----------------|
| 🧹 **Full clean build with tests** | `./gradlew clean build --parallel` |
| ⚡ **Quick development build** | `./gradlew assembleDebug --parallel --build-cache` |
| 🚀 **Release build with analysis** | `./gradlew clean assembleRelease lint --profile --scan` |
| 🧪 **Test with coverage** | `./gradlew clean testDebugUnitTest jacocoTestReport` |
| 🔄 **Update dependencies and build** | `./gradlew --refresh-dependencies clean build` |

</div>

---

## 🛠️ Troubleshooting Common Issues

<details>
<summary>🔧 <strong>Fix corrupted cache</strong></summary>

```bash
./gradlew --stop
./gradlew cleanBuildCache
rm -rf ~/.gradle/caches
```

</details>

<details>
<summary>🔗 <strong>Fix dependency resolution issues</strong></summary>

```bash
./gradlew --refresh-dependencies clean build
```

</details>

<details>
<summary>🐛 <strong>Debug build configuration</strong></summary>

```bash
./gradlew build --debug --stacktrace
```

</details>

<details>
<summary>⚔️ <strong>Check for conflicting dependencies</strong></summary>

```bash
./gradlew dependencies | grep "conflict"
./gradlew dependencyInsight --dependency <problematic-dependency>
```

</details>

---

<div align="center">

## 💡 Tips & Best Practices

| 🎯 **Tip** | 📝 **Description** |
|------------|-------------------|
| 🐘 **Use Gradle Wrapper** | Always use `./gradlew` instead of global `gradle` command |
| 💾 **Enable Build Cache** | Add `org.gradle.caching=true` to `gradle.properties` |
| ⚡ **Parallel Builds** | Use `--parallel` flag for multi-module projects |
| 📈 **Build Scans** | Use `--scan` to analyze build performance |
| 🔄 **Incremental Builds** | Keep incremental compilation enabled for Kotlin |
| 📦 **Dependency Management** | Regularly check for updates and deprecations |
| 🔄 **CI/CD** | Use `--continue` flag in CI to see all failures at once |

</div>

---

<div align="center">

### 🌟 Made with ❤️ for Android Developers

![GitHub stars](https://img.shields.io/github/stars/username/repo?style=social)
![GitHub forks](https://img.shields.io/github/forks/username/repo?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/username/repo?style=social)

*📅 Last updated: 19, Jul 2025* | *🤝 Contributions welcome!*

</div>
