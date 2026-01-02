# Provider Integrations

This document explains how provider integrations and synchronization work in this application.

## Overview

The application integrates with third-party financial data providers to import and sync user data. Each provider has its own implementation, but they all follow a common pattern for synchronization.

## Core Components

The provider integration and synchronization system is composed of the following core components:

*   **Provider Models**: Each provider has a corresponding model in `app/models` (e.g., `SimplefinItem`, `PlaidItem`). These models are responsible for storing provider-specific data and credentials.
*   **`Syncable` Concern**: This concern, located in `app/models/concerns/syncable.rb`, provides the core logic for scheduling and managing synchronizations. It defines a `has_many :syncs` association and a `sync_later` method that creates a new `Sync` record and enqueues a `SyncJob`.
*   **`SyncJob`**: This job, located in `app/jobs/sync_job.rb`, is responsible for performing the synchronization. It calls the `perform_sync` method on the `syncable` object.
*   **`Syncer` Classes**: Each provider has a `Syncer` class (e.g., `SimplefinItem::Syncer`) that contains the provider-specific logic for fetching data from the provider's API.
*   **`Importer` Classes**: Once the data is fetched, it is passed to an `Importer` class (e.g., `SimplefinItem::Importer`) that is responsible for processing and importing the data into the application's database.

## Synchronization Flow

The synchronization process is initiated by calling the `sync_later` method on a provider model instance. This triggers the following sequence of events:

1.  A new `Sync` record is created in the database.
2.  A `SyncJob` is enqueued to perform the synchronization.
3.  The `SyncJob` calls the `perform_sync` method on the provider model.
4.  The `perform_sync` method delegates the task to the provider-specific `Syncer` class.
5.  The `Syncer` class fetches the latest data from the provider's API.
6.  The fetched data is passed to the `Importer` class, which processes and imports the data into the application's database.
7.  The `Sync` record is updated to reflect the status of the synchronization (e.g., `completed`, `failed`).
