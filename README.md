# Finevo

Serwis internetowy do zarządzania wydatkami.

# 🎯 Przegląd Projektu Finevo

## 📖 Opis projektu
Finevo to system zarządzania finansami osobistymi, który wykorzystuje technologie AI i udostępnia intuicyjny interfejs użytkownika. Projekt powstał z myślą o automatyzacji procesu zarządzania paragonami i wydatkami osobistymi.

## Demo / Screenshots

## 🎯 Główne cele projektu

### Automatyzacja Przetwarzania Paragonów
- Przetwarzanie paragonów za pomocą AI
- Eliminacja ręcznego wprowadzania danych

### Inteligentne Zarządzanie Wydatkami
- Automatyczna kategoryzacja wydatków
- Tworzenie i monitorowanie budżetów 

### Nowoczesny Interfejs użytkownika
- Responsywny design dostosowany do wszystkich urządzeń
- Intuicyjna nawigacja
- Ciemny i jasny motyw

## ✨ Kluczowe Funkcjonalności
### Skanowanie paragonów
Wyodrębniamy informacje takie jak:
- Nazwa sklepu
- Data transakcji
- Lista produktów z cenami 
- Suma całkowita 

### Panel Główny
Interaktywny panel główny prezentujący:
- Miesięczne podsumowanie wydatków
- Wykresy
- Statystyki
- Informacje o stanie budżetów

### Zarządzanie budżetami
System planowania finansowego:
- Tworzenie budżetów dla różnych okresów
- Ustawianie limitów dla kategorii użytkownika

### Przeglądanie i filtrowanie wydatków
System wyszukiwania i filtrowania:
- Filtrowanie po kategoriach, datach, kwotach
- Wyszukiwanie tekstowe
- Eksport wydatków do formatu JSON
- Historia wszystkich transakcji

### Automatyczna kategoryzacja
- Automatyczne przypisywanie kategorii użytkownika do wydatków
- Możliwość tworzenia własnych kategorii

---
## �� Interfejs Użytkownika

### Responsywny design
Aplikacja jest w pełni responsywna i działa optymalnie na:
- Komputerach stacjonarnych i laptopach
- Tabletach
- Smartfonach
- Różnych rozdzielczościach ekranu
### Nowoczesny UI/UX
- Płynne animacje i przejścia
- Intuicyjna nawigacja
- Spójny system design
- Ciemny jasny motyw

## 🏗️  Architektura Systemu Finevo
### Frontend (Next.js)

Frontend aplikacji jest zbudowany w oparciu o Next.js z App Router. Struktura aplikacji jest podzielona na poszczególne sekcje:
- **Sekcja uwierzytelniania** - logowanie i rejestracja użytkownika
- **Sekcja autoryzacji** - autoryzowanie użytkownika
- **Panel główny** - interaktywny panel z podsumowaniem wydatków
- **Wydatki** - zarządzanie i przeglądanie wydatków
- **Budżety** - monitorowanie i zarządzanie budżetami
- **Paragony** - skanowanie paragonów
- **Planowanie** - tworzenie nowego budżetu

#### Architektura
```bash
/frontend
├─ app/          
│  ├─ components/
│  │  ├─ budgets/
│  │  ├─ dashboard/
│  │  ├─ expenses/
│  │  ├─ home/
│  │  ├─ planning/
│  │  ├─ AuthenticationLayout.tsx
│  │  ├─ Header.tsx
│  │  ├─ Footer.tsx
│  ├─ budgets/
│  │  ├─ page.tsx
│  │  ├─ layout.tsx
│  ├─ receipts/
│  ├─ dashboard/
│  ├─ expenses/
│  ├─ login/
│  ├─ planning/
│  ├─ profile/
│  ├─ register/
│  ├─ types/
│  ├─ utils/
│  ├─ contexts/
│  ├─ hooks/
│  ├─ lib/
│  ├─ global.css
│  ├─ layout.tsx
│  ├─ page.tsx
```

#### Komponenty Interfejsu
- **Komponenty bazowe** - przyciski, formularze, karty
- **Layouty** - struktury stron i nawigacji
- **Hooks** - logika wielokrotnego użytku
- **Contexts** - zarządzanie stanem globalnym

### Backend (Spring boot Microservices)

Backend składa się z kilku niezależnych mikroserwisów

#### Auth Service
Serwis odpowiedzialny za autoryzację i uwierzytelnianie użytkowników:
- **Controller** - obsługa żądań HTTP związanych z autoryzacją 
- **Service** - logika biznesowa autoryzacji
- **Model** - encje użytkowników i tokenów
- **Repository** - dostęp do danych użytkowników 
- **Security** - ustawienia JWT i Spring Security

- **ValidationServcie** - walidacja danych z requestów
- **MetricsService** - metryki serwisu
- **JwtService** - logika JWT

#### Finance Service
Główny serwis odpowiedzialny za zarządzanie finansami:
- **Controller** - obsługa żądań HTTP
- **Service** - logika biznesowa
- **Model** - encje 
- **Repository** - dostęp do bazy danych
- **Exception** - obsługa wyjątków

- **ValidationServcie** - walidacja danych z requestów
- **MetricsService** - metryki serwisu

#### Gateway Service
API Gateway pełniący rolę punktu wejścia do systemu:
- **Routing** - kierowanie żądań do odpowiednich serwisów
- **Filtry** - autoryzacja żądań
- **Rate limiting** - ograniczanie liczby żądań
- **CORS** - obsługa cross-origin requests


#### Przykładowa Architektura Serwisu Finance
/backend/finance/
├─ src/
│   ├─ main/
│   │   ├─ java/
│   │   │   └─ com/receipts/finance/
│   │   │       ├─ FinanceApplication.java
│   │   │       ├─ config/
│   │   │       │   └─ OpenApiConfig.java
│   │   │       ├─ controller/
│   │   │       │   ├─ BudgetController.java
│   │   │       │   ├─ CategoryController.java
│   │   │       │   ├─ DashBoardController.java
│   │   │       │   ├─ ExpenseController.java
│   │   │       │   └─ ReceiptController.java
│   │   │       ├─ exception/
│   │   │       │   ├─ ConflictException.java
│   │   │       │   ├─ ErrorResponse.java
│   │   │       │   ├─ ForbiddenException.java
│   │   │       │   ├─ NotFoundException.java
│   │   │       │   ├─ GlobalExceptionHandler.java
│   │   │       │   ├─ NoContentException.java
│   │   │       │   └─ ValidationException.java
│   │   │       ├─ model/
│   │   │       │   ├─ BoxCoors.java
│   │   │       │   ├─ Budget.java
│   │   │       │   ├─ Category.java
│   │   │       │   ├─ Expense.java
│   │   │       │   ├─ Receipt.java
│   │   │       │   ├─ User.java
│   │   │       │   └─ dto/
│   │   │       │       ├─ AlertsAndNotificationsDTO.java
│   │   │       │       ├─ BudgetDTO.java
│   │   │       │       ├─ BudgetRequestDTO.java
│   │   │       │       ├─ CategoryDTO.java
│   │   │       │       ├─ CategoryRequestDTO.java
│   │   │       │       ├─ DashboardDTO.java
│   │   │       │       ├─ ExpenseDTO.java
│   │   │       │       ├─ ExpenseRequestDTO.java
│   │   │       │       ├─ ReceiptDTO.java
│   │   │       │       ├─ ReceiptRequestDTO.java
│   │   │       │       ├─ UserDTO.java
│   │   │       │       └─ dashboard/
│   │   │       │           ├─ CategoryBreakdownDTO.java
│   │   │       │           ├─ MonthlyExpenseDTO.java
│   │   │       │           ├─ RecentExpenseDTO.java
│   │   │       │           ├─ TotalExpenseDTO.java
│   │   │       │           ├─ TotalIncomeDTO.java
│   │   │       │           ├─ TotalSavingsDTO.java
│   │   │       │           ├─ WeeklyExpenseDTO.java
│   │   │       │           └─ YearlyExpenseDTO.java
│   │   │       │       └─ publicdto/
│   │   │       │           ├─ ExpenseExportDTO.java
│   │   │       │           └─ ExportDTO.java
│   │   │       ├─ repository/
│   │   │       │   ├─ budget/
│   │   │       │   │   ├─ BudgetRepository.java
│   │   │       │   │   ├─ BudgetRepositoryCustom.java
│   │   │       │   │   └─ BudgetRepositoryCustomImpl.java
│   │   │       │   ├─ CategoryRepository.java
│   │   │       │   ├─ expense/
│   │   │       │   │   ├─ ExpenseRepository.java
│   │   │       │   │   ├─ ExpenseRepositoryCustom.java
│   │   │       │   │   └─ ExpenseRepositoryCustomImpl.java
│   │   │       │   └─ UserRepository.java
│   │   │       ├─ service/
│   │   │       │   ├─ BudgetService.java
│   │   │       │   ├─ BudgetServiceImpl.java
│   │   │       │   ├─ CategoryService.java
│   │   │       │   ├─ CategoryServiceImpl.java
│   │   │       │   ├─ DashBoardService.java
│   │   │       │   ├─ DashBoardServiceImpl.java
│   │   │       │   ├─ ExpenseService.java
│   │   │       │   ├─ ExpenseServiceImpl.java
│   │   │       │   ├─ ReceiptService.java
│   │   │       │   ├─ ReceiptServiceImpl.java
│   │   │       │   ├─ UserService.java
│   │   │       │   └─ UserServiceImpl.java
│   │   │       └─ util/
│   │   │           └─ Utils.java
│   │   └─ resources/
│   │       └─ application.yml


## 🛠️ Technologie i Stack
### Frontend Stack

- Next.js / React / Tailwind CSS 

### Backend Stack

- Java Spring / Maven / JPA / REST API

### Kontrola Wersji
- Git / Github
- 
### Automatyzacja i środowiska

-   **Ansible** – automatyzacja konfiguracji serwerów i wdrożeń aplikacji
    
-   **Vagrant** – przygotowanie spójnych środowisk developerskich i testowych
    
-   **Digital Ocean** – hostowanie backendu i frontendu w chmurze, skalowalne instancje dla mikroserwisów

### Baza Danych
- MongoDB

