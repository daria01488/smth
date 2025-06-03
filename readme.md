# AutoMagik - web application for a car workshop

## AutoMagik is a fully functional example project written in C++ using Qt, designed to support the management of a local car repair workshop. It provides a desktop client interface for workshop employees (managers and workers) to handle service orders, internal communication, and vehicle data collection. The backend is powered by Firebase for real-time synchronization and cloud storage.

## Overview

The purpose of AutoMagik is to present the assumptions and specifications for version 1.0 of a desktop application that supports car repair shop management. AutoMagik allows small and medium-sized workshops to:

- Create, assign, and track repair orders (tasks)
- Manage employee accounts and user roles
- Collect and store vehicle data
- Communicate internally via task-specific comments
- Sync all information in real time through a Firebase backend

Only authorized users (workshop employees with active accounts) can access the system. The application requires an active internet connection to synchronize with Firebase and communicate with any external vehicle APIs.

**Tech Stack:**
- C++ 17  
- Qt 6 (Qt Widgets)  
- Firebase Realtime Database (client-side SDK)  
- Google Vehicle Data API (optional integration)

<!-- intro paragraph aboud the app that was created from this describtion: The purpose of this document is to present the assumptions and specifications
of the planned activities within the implementation of the AutoMagik application - a system supporting
the management of a car repair shop. The document is intended for members of the
project team responsible for implementing, testing and adapting the
functionality of the system in accordance with the presented requirements. It is also
a reference for the team responsible for creating and updating the project documentation. The document
covers the requirements for version 1.0 of the software.
The project involves the creation and implementation of a desktop application
enabling management of the customer and employee service process in a car repair shop. The system
will support the allocation and monitoring of repair orders, internal communication
between users, and the collection of vehicle data. The application will be
adapted to the needs of small and medium-sized workshops, providing a simple
user interface and basic administrative functions available to privileged users.
The application requires an active internet connection to synchronize with the Firebase database and communicate with external services (e.g. vehicle API).
The application must be implemented in C++ using the Qt library to ensure compatibility between systems and easy integration with the user interface.
Only authorized users can use the application - workshop employees with an active account in the system.
The client-server system will work in an architecture where the client is a desktop application and the backend - Firebase as a cloud service.
Add keywords for finding my app in github-->

---

## Key Features

### User Modes

Upon launching AutoMagik, users select one of two account types:

- **Manager**  
- **Worker**

Each mode unlocks a distinct set of functions, as detailed below.

### Manager Functions

1. **Task Management**  
   - Create, edit, and delete service tasks (repair orders)  
   - Assign tasks to individual workers or groups  
   - Track task status (e.g., Pending -> In Progress -> Completed)  
   - View all tasks across the workshop

2. **User & Account Management**  
   - Create, edit, deactivate, or delete employee (worker/manager) accounts  
   - Reset passwords or change email addresses for any user  
   - Grant/revoke administrative privileges  
   - Monitor login activity and account status

3. **Vehicle & Client Management**  
   - Add, edit, or remove vehicle records (each vehicle represents one client)  
   - View client history and associated tasks  
   - Attach vehicle details (make, model, license plate, VIN, etc.)  
   - Optionally fetch additional vehicle specs via an external API

4. **System Administration**  
   - Oversee data integrity and consistency  
   - Manage application configuration (e.g., Firebase endpoints, API keys)  
   - Access all comments and log entries in the system  

### Worker Functions

1. **Availability Status**  
   - Toggle between **Available (Clocked In)** and **Unavailable (Clocked Out)**  

2. **Authentication & Profile**  
   - Log in with company-provided email and password  
   - Change password during or after login  
   - View and edit personal profile details (name, contact info)

3. **Task Workflow**  
   - View a personalized list of assigned tasks  
   - Access basic vehicle information for each task  
   - Update task status (e.g., In Progress, On Hold, Completed)  
   - Add comments or progress updates to assigned tasks  
   - Mark tasks as completed once work is done

4. **Communication**  
   - Post and view comments within tasks to communicate with managers or other workers  

---

## User Interface Walkthrough

Below is a brief overview of each main interface screen:

### 1. User Selection Screen

- On launch, users choose between **Manager** or **Worker** mode.  
- The selection determines which features are shown after login.  

![User Selection Screen](/screenshots/automagik-user.jpg)

### 2. Sign-In Window

- Both Manager and Worker can sign in with **Email** and **Password**.  
- First-time login for Managers uses preset credentials (provided by the workshop owner).  
- User can create new Manager accounts. 
- After the Manager is authenticated:
	- Manager can create new Worker accounts.
  - Each new user receives a system-generated activation email (or temporary password).  
- Users can also change their email or password via dedicated “Change Email” and “Change Password” dialogs.

![Sign-In Window](/screenshots/worker-sign-in.jpg)
![Sign-In Window](/screenshots/manager-sign-in.jpg)
![Sign-In Window](/screenshots/manager-create.jpg)

### 3. Manager: Cars / Clients Panel

- **Purpose:** Manage the list of vehicles (clients).  
- Each vehicle record includes:  
  - Owner Name  
  - Vehicle Make & Model  
  - License Plate / VIN  
  - Contact Information  
  - Optional: Link to external vehicle data API for specifications  
- Actions:  
  - **Add Vehicle (New Client)**  
  - **Edit Vehicle Details**  
  - **Delete Vehicle**  
  - **Search / Filter** by license plate, owner, or VIN  

> In AutoMagik, “Client” is synonymous with “Vehicle”—each vehicle entry represents one client.

![Cars / Clients Panel](/screenshots/manager-cars.jpg)

### 4. Manager: Tasks / Workers Panel

- **Purpose:** Create, assign, and monitor service tasks.  
- **Task Fields:**  
  - Task ID (auto-generated)  
  - Vehicle (linked to Cars/Clients)  
  - Assigned Worker(s)  
  - Task Description (e.g., “Oil change”, “Brake inspection”)  
  - Priority (Low / Medium / High)  
  - Status (Pending / In Progress / Completed)  
  - Estimated Completion Date  
- Actions:  
  - **Create New Task**  
  - **Edit Existing Task**  
  - **Assign / Reassign Workers**  
  - **Delete Task**  
  - **View Task Details & Comments**  
- **Worker Management:**  
  - View a list of all active Workers and their availability status  
  - Activate / Deactivate accounts  
  - Reset passwords or change user roles  

![Tasks / Workers Panel](/screenshots/manager-tasks.jpg)

### 5. Worker: Tasks Panel

- **Purpose:** Allow a Worker to view and update their assigned tasks.  
- **Task Details Displayed:**  
  - Vehicle Info (Make, Model, License Plate)  
  - Task Description & Priority  
  - Due Date  
  - Comments from Manager or other Workers  
- **Worker Actions:**  
  - **Update Task Status** (e.g., mark as In Progress)  
  - **Add Comment** (progress updates, questions)  
  - **Mark Task as Completed**  
  - **View Historical Comments** for context

![Worker Tasks Panel](/screenshots/worker-tasks.jpg)

---

## Installation


---
## How to Buid and Install AutoMagik Application to contribute

