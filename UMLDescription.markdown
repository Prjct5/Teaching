# UML Class Diagram Description for Student Management System

## Overview
This UML class diagram represents the structure of the JavaFX-based Student Management System, highlighting the implementation of OOP principles: encapsulation, abstraction, inheritance, and polymorphism.

## Classes and Relationships

### 1. Info
- **Attributes**:
  - `-currentUser: String` (private, static)
  - `-currentRole: String` (private, static)
- **Methods**:
  - `+getCurrentUser(): String` (static)
  - `+setCurrentUser(user: String): void` (static)
  - `+getCurrentRole(): String` (static)
  - `+setCurrentRole(role: String): void` (static)
- **Description**: Stores the current user's context. Encapsulation is achieved through private fields and public getters/setters.

### 2. byInfo (Abstract)
- **Inherits**: `Info`
- **Description**: A placeholder abstract class for future extensions, demonstrating inheritance.

### 3. UserOperations (Interface)
- **Methods**:
  - `+addUser(username: String, email: String, password: String, role: String): boolean`
  - `+removeUser(userId: int): boolean`
  - `+getUserDetails(userId: int): User`
  - `+updateUser(userId: int, email: String, password: String): boolean`
- **Description**: Defines a contract for user management operations, promoting abstraction.

### 4. AbstractUserManager (Abstract)
- **Inherits**: `Info`
- **Attributes**:
  - `-database: Database` (private, final)
- **Methods**:
  - `#getDatabase(): Database` (protected)
  - `#userExists(username: String): boolean` (protected)
  - `#formatUserDetails(userData: Map<String, String>): String` (protected, abstract)
- **Description**: Abstracts database access and user management logic. Encapsulates the `Database` instance.

### 5. UserManager
- **Inherits**: `AbstractUserManager`
- **Implements**: `UserOperations`
- **Methods**:
  - `+addUser(username: String, email: String, password: String, role: String): boolean`
  - `+removeUser(userId: int): boolean`
  - `+getUserDetails(userId: int): User`
  - `+getUserDetails(username: String): User`
  - `+updateUser(userId: int, email: String, password: String): boolean`
  - `#formatUserDetails(userData: Map<String, String>): String`
- **Description**: Implements user management with polymorphism (overriding `formatUserDetails`, overloading `getUserDetails`). Uses `User` objects for polymorphic returns.

### 6. Database
- **Attributes**:
  - `-URL: String` (private, static, final)
  - `-USER: String` (private, static, final)
  - `-PASSWORD: String` (private, static, final)
- **Methods**:
  - `+getConnection(): Connection`
  - `+registerUser(...): boolean`
  - `+loginUser(...): Map<String, String>`
  - `+addStudent(...): boolean`
  - `+addCourse(...): boolean`
  - `+addCourseVideo(...): boolean`
  - `+enrollStudentInCourse(...): boolean`
  - `+addAssignment(...): boolean`
  - `+submitAssignment(...): boolean`
  - `+saveSetting(...): boolean`
  - `+getCourseVideos(...): ResultSet`
  - `+getAssignments(...): ResultSet`
- **Description**: Encapsulates database connectivity and operations with private connection details.

### 7. Main
- **Inherits**: `Application` (JavaFX)
- **Methods**:
  - `+start(primaryStage: Stage): void`
  - `+main(args: String[]): void`
- **Description**: Entry point, inherits from JavaFX `Application`, overrides `start`.

### 8. User (Abstract)
- **Package**: `com.projecttest.projecttest.users`
- **Attributes**:
  - `-id: int` (private, final)
  - `-username: String` (private, final)
  - `-email: String` (private, final)
  - `-role: String` (private, final)
- **Methods**:
  - `+getId(): int`
  - `+getUsername(): String`
  - `+getEmail(): String`
  - `+getRole(): String`
  - `+getRoleDescription(): String` (abstract)
- **Description**: Abstract base class for users, encapsulating user data and defining polymorphic behavior.

### 9. AdminUser
- **Inherits**: `User`
- **Methods**:
  - `+getRoleDescription(): String`
- **Description**: Represents an Admin user, overrides `getRoleDescription`.

### 10. TeacherUser
- **Inherits**: `User`
- **Methods**:
  - `+getRoleDescription(): String`
- **Description**: Represents a Teacher user, overrides `getRoleDescription`.

### 11. StudentUser
- **Inherits**: `User`
- **Methods**:
  - `+getRoleDescription(): String`
- **Description**: Represents a Student user, overrides `getRoleDescription`.

### 12. LoginController
- **Attributes**:
  - `-usernameField: TextField` (private, FXML)
  - `-passwordField: PasswordField` (private, FXML)
  - `-statusLabel: Label` (private, FXML)
- **Methods**:
  - `-handleLogin(): void`
  - `-handleGoToRegister(): void`
- **Description**: Manages login UI, encapsulates FXML fields.

### 13. RegisterController
- **Attributes**:
  - `-usernameField: TextField` (private, FXML)
  - `-emailField: TextField` (private, FXML)
  - `-passwordField: PasswordField` (private, FXML)
  - `-roleComboBox: ComboBox<String>` (private, FXML)
  - `-statusLabel: Label` (private, FXML)
- **Methods**:
  - `+initialize(): void`
  - `-handleRegister(): void`
  - `-handleGoToLogin(): void`
- **Description**: Manages registration UI, encapsulates FXML fields.

### 14. AdminDashboardController
- **Attributes**:
  - `-manageUsersButton: Button` (private, FXML)
  - `-systemSettingsButton: Button` (private, FXML)
  - `-dataManagementButton: Button` (private, FXML)
  - `-reportsButton: Button` (private, FXML)
  - `-logoutButton: Button` (private, FXML)
- **Methods**:
  - `-handleManageUsers(): void`
  - `-handleSystemSettings(): void`
  - `-handleDataManagement(): void`
  - `-handleReports(): void`
  - `-handleLogout(): void`
- **Description**: Manages admin dashboard UI, encapsulates FXML fields.

### 15. DataManagementController
- **Attributes**:
  - `-exportButton: Button` (private, FXML)
  - `-importButton: Button` (private, FXML)
  - `-backButton: Button` (private, FXML)
  - `-fullNameField: TextField` (private, FXML)
  - `-gpaField: TextField` (private, FXML)
  - `-statusLabel: Label` (private, FXML)
- **Methods**:
  - `-handleExportData(): void`
  - `-handleImportData(): void`
  - `-handleAddStudent(): void`
  - `-handleBack(): void`
- **Description**: Manages data operations, encapsulates FXML fields.

### 16. SystemSettingsController
- **Attributes**:
  - `-languageButton: Button` (private, FXML)
  - `-permissionsButton: Button` (private, FXML)
  - `-resetButton: Button` (private, FXML)
  - `-backButton: Button` (private, FXML)
  - `-statusLabel: Label` (private, FXML)
- **Methods**:
  - `+initialize(): void`
  - `-handleChangeLanguage(): void`
  - `-handleManagePermissions(): void`
  - `-handleReset(): void`
  - `-handleBack(): void`
- **Description**: Manages system settings UI, encapsulates FXML fields.

### 17. StudentController
- **Attributes**:
  - `-contentArea: VBox` (private, FXML)
  - `-coursesButton: Button` (private, FXML)
  - `-videosButton: Button` (private, FXML)
  - `-tasksButton: Button` (private, FXML)
  - `-backButtonPrev: Button` (private, FXML)
  - `-backButtonLogin: Button` (private, FXML)
  - `-statusLabel: Label` (private, FXML)
- **Methods**:
  - `+initialize(): void`
  - `-handleViewCourses(): void`
  - `-handleWatchVideos(): void`
  - `-handleCheckTasks(): void`
  - `-handleReturnToPrevious(): void`
  - `-handleBackLogin(): void`
- **Description**: Manages student dashboard UI, encapsulates FXML fields.

### 18. TeacherController
- **Attributes**:
  - `-contentArea: VBox` (private, FXML)
  - `-coursesButton: Button` (private, FXML)
  - `-addTaskButton: Button` (private, FXML)
  - `-studentsButton: Button` (private, FXML)
  - `-backButtonPrev: Button` (private, FXML)
  - `-backButtonLogin: Button` (private, FXML)
  - `-statusLabel: Label` (private, FXML)
- **Methods**:
  - `+initialize(): void`
  - `-handleManageCourses(): void`
  - `-handleAddTask(): void`
  - `-handleViewStudents(): void`
  - `-handleReturnToPrevious(): void`
  - `-handleBackLogin(): void`
- **Description**: Manages teacher dashboard UI, encapsulates FXML fields.

### 19. ReportsController
- **Attributes**:
  - `-reportsTable: TableView<ReportItem>` (private, FXML)
  - `-categoryColumn: TableColumn<ReportItem, String>` (private, FXML)
  - `-countColumn: TableColumn<ReportItem, Integer>` (private, FXML)
  - `-refreshButton: Button` (private, FXML)
  - `-backButton: Button` (private, FXML)
  - `-statusLabel: Label` (private, FXML)
  - `-reportsList: ObservableList<ReportItem>` (private)
- **Inner Class**:
  - `ReportItem`
    - `-category: String` (private, final)
    - `-count: int` (private, final)
    - `+getCategory(): String`
    - `+getCount(): int`
- **Methods**:
  - `+initialize(): void`
  - `-handleRefresh(): void`
  - `-handleBack(): void`
- **Description**: Manages reports UI, encapsulates FXML fields and inner class.

### 20. ManageUsersController
- **Attributes**:
  - `-usernameField: TextField` (private, FXML)
  - `-emailField: TextField` (private, FXML)
  - `-passwordField: TextField` (private, FXML)
  - `-roleComboBox: ComboBox<String>` (private, FXML)
  - `-addButton: Button` (private, FXML)
  - `-deleteButton: Button` (private, FXML)
  - `-editButton: Button` (private, FXML)
  - `-backButton: Button` (private, FXML)
  - `-usersTable: TableView<User>` (private, FXML)
  - `-idColumn: TableColumn<User, Integer>` (private, FXML)
  - `-usernameColumn: TableColumn<User, String>` (private, FXML)
  - `-emailColumn: TableColumn<User, String>` (private, FXML)
  - `-roleColumn: TableColumn<User, String>` (private, FXML)
  - `-statusLabel: Label` (private, FXML)
  - `-usersList: ObservableList<User>` (private)
  - `-userManager: UserManager` (private, final)
- **Methods**:
  - `+initialize(): void`
  - `-handleAddUser(): void`
  - `-handleDeleteUser(): void`
  - `-handleEditUser(): void`
  - `-handleBack(): void`
- **Description**: Manages user operations, uses `UserManager` (typed as `UserOperations`) for polymorphism.

## Relationships
- **Inheritance**:
  - `byInfo` → `Info`
  - `AbstractUserManager` → `Info`
  - `UserManager` → `AbstractUserManager`
  - `Main` → `Application`
  - `AdminUser` → `User`
  - `TeacherUser` → `User`
  - `StudentUser` → `User`
- **Interface Realization**:
  - `UserManager` → `UserOperations`
- **Composition**:
  - `AbstractUserManager` → `Database` (owns a `Database` instance)
- **Dependency**:
  - `ManageUsersController` → `UserManager` (uses `UserManager` for operations)
  - Controllers → `Database` (for direct database access)
- **Association**:
  - Controllers → FXML fields (via `@FXML`)

## OOP Principles
- **Encapsulation**: Private fields in `Info`, `Database`, `User`, and controllers, with public getters/setters where needed.
- **Abstraction**: `UserOperations` interface and `AbstractUserManager` define contracts for user management.
- **Inheritance**: `UserManager` → `AbstractUserManager` → `Info`, `User` → `AdminUser`/`TeacherUser`/`StudentUser` hierarchies.
- **Polymorphism**: `UserManager` implements `UserOperations`, overrides `formatUserDetails`, returns `User` objects; `AdminUser`/`TeacherUser`/`StudentUser` override `getRoleDescription`.

## Notes
- The diagram should include FXML bindings as context (e.g., controllers linked to FXML files).
- Database tables (`users`, `students`, etc.) can be shown as entities for context.
- Use tools like Draw.io or Lucidchart to visualize, exporting as PNG/PDF for submission.