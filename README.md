# @dinkarjallan/rezilient-utils

A utility library for building resilient, offline-first applications by providing tools for managing frontend logic and handling complex operations. This package is a core part of the **Rezilient.js** ecosystem, designed to enable powerful offline and network-resilient functionality.

---

## What is `rezilient-utils`?

**`@dinkarjallan/rezilient-utils`** provides a collection of utilities for handling the non-UI aspects of offline-ready applications. It focuses on logic-heavy operations, such as worker thread management, local storage synchronization, retry/queue handling, and network-aware decision-making. It works seamlessly alongside **@dinkarjallan/rezilient-ui**.

---

## What to Expect from This Package

- Decorators to enable worker thread execution for intensive functions.
- Local storage and IndexedDB management tools for state persistence.
- Retry and queue management functions for API calls and offline actions.
- Error handling utilities for offline-related issues.
- Tools to estimate and act on network strength.
- Offline mode detection and reconciliation utilities.

---

## Features and Examples

### 1. Worker Thread Decorators (for Functions)

Enable functions to execute in worker threads for better performance and responsiveness.

```javascript
import { runInWorkerThread } from '@dinkarjallan/rezilient-utils';

@runInWorkerThread
function processData(data) {
  // Perform complex data processing
}
```

---

### 2. Local Storage Management

Manage and synchronize application state with `localStorage` or `IndexedDB`.

- **Redux Middleware**: Automatically sync specific Redux slices with local storage.

```javascript
import { createLocalStorageMiddleware } from '@dinkarjallan/rezilient-utils';

const middleware = createLocalStorageMiddleware(['userSession', 'cart']);
```

---

### 3. Retry/Queue Management

Handle queued API calls and retry operations with prioritization and batching capabilities.

```javascript
import {
  enqueueAPICall,
  retryFailedCalls,
} from '@dinkarjallan/rezilient-utils';

// Queue an API call
enqueueAPICall('/api/save', { data: payload });

// Retry all failed calls
retryFailedCalls();
```

---

### 4. Error Handling Utilities

Plug offline-related error handlers into your `catch` blocks for graceful handling.

```javascript
import { handleOfflineError } from '@dinkarjallan/rezilient-utils';

try {
  await fetchData();
} catch (error) {
  handleOfflineError(error);
}
```

---

### 5. Network Strength Utilities

Estimate network conditions and execute logic based on strength.

```javascript
import { getNetworkStrength } from '@dinkarjallan/rezilient-utils';

if (getNetworkStrength() === 'weak') {
  alert('Sync postponed due to weak network');
}
```

---

### 6. Offline Mode Detection and State Reconciliation

Detect offline mode and reconcile local data with server-side data.

```javascript
import {
  enableOfflineMode,
  reconcileData,
} from '@dinkarjallan/rezilient-utils';

// Enable offline mode
enableOfflineMode();

// Reconcile data
reconcileData(localData, serverData);
```

---

## Why Use `rezilient-utils`?

- **Logic-Driven Resilience:** Enhance the performance and reliability of your application's logic layer.
- **Effortless State Management:** Simplify state persistence and reconciliation with battle-tested tools.
- **Network-Aware Operations:** Adapt your application's behavior dynamically to network conditions.
- **Seamless Integration:** Designed to work alongside **@dinkarjallan/rezilient-ui** for a full offline-first solution.

---

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

---

## License

This project is licensed under the [MIT License](LICENSE).
