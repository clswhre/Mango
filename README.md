# Mango

A desktop application built with C# and Windows Presentation Foundation (WPF). Developed as a coursework project to demonstrate Object-Oriented Programming (OOP) principles, the Model-View-ViewModel (MVVM) design pattern, and modern UI implementation using WPF-UI.

## Overview

Mango is a place management application that allows users to store, categorize, and analyze geographic locations. It features local SQLite data persistence, live weather API integration, and statistical tracking. The domain model relies on inheritance to distinguish between different types of locations (Historical, Natural, Normal).

## Features

* **Place Management:** View, add, and manage distinct place categories (`Historical`, `Natural`, `Standart`).
* **Live Weather Integration:** Fetches external weather data for selected locations via a dedicated API service.
* **Local Storage:** SQLite-based persistence ensures all place data is saved locally across sessions.
* **Statistics Dashboard:** Aggregates and displays data regarding stored places.
* **Modern Interface:** Tab-based navigation with a decoupled Left Panel and Main Content area, styled with custom XAML resources and WPF-UI.

## Architecture

The project strictly follows the MVVM (Model-View-ViewModel) pattern to enforce a clean separation of concerns:

* **Models:** Contains the core business logic and entities. Implements a base `Place` class with specialized derived classes.
* **Views:** XAML-based user interfaces divided into reusable user controls (`LeftPanel`, `MainContent`, `PlaceDetailsControl`).
* **ViewModels:** Handles presentation logic and state. Utilizes `BaseViewModel` and `RelayCommand` for UI binding without code-behind coupling.
* **Services:** Stateless helper classes containing external integrations, including `SQLiteStorage` for database operations and `WeatherApi` for network requests.
* **Store:** State management layers (`PlaceStore`, `EntityManager`) acting as in-memory repositories.

## Tech Stack

* **Language:** C#
* **Framework:** .NET / WPF
* **UI Library:** [WPF-UI](https://github.com/lepoco/wpfui) (implied by styling and modern layout)
* **Database:** SQLite
* **Design Pattern:** MVVM

## Project Structure

```text
Mango/OOPWPFProject/
├── Converters/        # Value converters for XAML bindings (e.g., BoolToVisibility)
├── Models/            # Domain entities (Places) and Interfaces (IWeather)
├── Resources/         # Application-wide assets, icons, and Style.xaml
├── Services/          # External dependencies (SQLite DB, Weather API, Logger)
├── Store/             # State management and data caching
├── ViewModels/        # Logic bound to views, separated into Base, Tabs, and Core ViewModels
└── Views/             # UI Components (Windows and UserControls)
