Module for creating and managing loops in roblox
# Looper

The module allows you to run loops at specified intervals and provides functionality for managing, cancelling, and removing loops dynamically.

### Features:
- Add loops that run at intervals using `Heartbeat` or `Stepped`.
- Easily remove loops based on conditions or at any point in time.
- Store and manage multiple loops in a table for easy cancellation.

---

### **Methods**:

- **`AddLoop(binding, interval, func, ...)`**  
  Adds a new loop that runs at the specified `interval` under the given `binding` (`"Heartbeat"` or `"Stepped"`). The loop executes the `func` callback with the provided arguments.

- **`CancelTask(taskID)`**  
  Cancels the loop associated with the given `taskID`. Each loop has a unique ID that can be used for cancelling tasks.

- **`ExecuteLoops(binding, deltaTime)`**  
  Executes the loops under the specified `binding` (`"Heartbeat"` or `"Stepped"`), passing the `deltaTime` to the loop functions.

- **`ConnectBinds()`**  
  Connects the `Stepped` and `Heartbeat` events to the loop system automatically.

---

### **Basic Usage**:

```lua

local LoopModule = require(Path)
local Task = LoopModule:AddLoop("Heartbeat", 2, function(dt)
    print("Hello World!")
end)

-- For example cancel a task after 5 seconds (Alternatively you can cancel it by returning "Cancel" in the Loop itself.)
task.delay(5, function()
    LoopModule:CancelTask(Task)
end)
