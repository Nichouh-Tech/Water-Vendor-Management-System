# 💧 ECO Drop Water Hub — POS & Distribution Management System


A modern, desktop-based Point of Sale (POS), inventory management, and asset-tracking software built specifically for **water vending stations**, **wholesale bulk distributors**, and **home/office delivery operations**.

---

## 📌 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the App](#running-the-app)
- [Default User Accounts](#-default-user-accounts)
- [Folder Structure](#-folder-structure)
- [License](#-license)

---

## 🌊 Overview

Traditional POS systems struggle with the unique operational workflows of water stations—such as **container deposit calculations**, **returnable bottle ledgers**, **wholesale tier discounts**, and **consumables tracking (caps & seals)**. 

**Clear Drop Water Hub** addresses these challenges directly by combining fast counter checkout workflows, container fleet tracking, and multi-channel order dispatches into an intuitive, dark-mode desktop interface.

---

## ✨ Key Features

### 🛒 Multi-Channel Sales & Counter POS
* **Channel Toggles**: Switch seamlessly between **Retail Walk-In**, **Wholesale Bulk**, and **Delivery Orders**.
* **Tiered Pricing**: Automatic rate adjustments and discounts for bulk wholesale transactions.
* **Quick Barcode Scanning**: Full support for barcode scanner inputs and instant item lookups.

### 🫙 Container & Asset Ledger Management
* **Deposit Logic**: Automated prompts to apply deposit fees when a customer purchases a new container versus swapping an empty.
* **Customer Bottle Ledger**: Real-time tracking of containers issued vs. returned per customer to eliminate asset losses.
* **Credit & Balance Management**: Track unpaid credit balances for regular delivery accounts or wholesale buyers.

### 📦 Inventory & Consumables Management
* **Water Volume Reserves**: Live monitoring of bulk water reserves with low-stock visual alerts.
* **Packaging Supply Logs**: Deduct and track usage of internal packaging materials (e.g., bottle seals, caps, shrink wraps).
* **Restock Reports**: Automated generation of low-stock items and restocking lists.

### 🛡️ Security & Role-Based Permissions
* **Role Enforcement**: Strict controls on maximum discount percentages (Cashiers capped at 10%, Managers/Admins at 20%).
* **Secure Authentication**: Hashed password storage and security question recovery pathways.

### 🖨️ Receipt Printing & PDF Backups
* **Thermal Printing**: Direct RAW ESC/POS local thermal receipt integration.
* **PDF Archiving**: Automatic background generation and storage of PDF receipt copies.

---

## 🏗️ System Architecture

```text
┌─────────────────────────────────────────────────────────┐
│                     CustomTkinter UI                    │
│   (SalesView | InventoryView | CustomersView | Reports) │
└────────────────────────────┬────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────┐
│                  Authentication Layer                    │
│          (AuthService | RBAC Permission Guard)          │
└────────────────────────────┬────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────┐
│                 Database Access Layer                   │
│       (DatabaseManager | WAL Mode | Auto-Migrations)    │
└────────────────────────────┬────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────┐
│                    SQLite Database                      │
│     (Sales, Products, Customer Bottle Ledger, Logs)     │
└─────────────────────────────────────────────────────────┘
