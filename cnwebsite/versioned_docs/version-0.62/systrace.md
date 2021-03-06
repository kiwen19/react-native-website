---
id: version-0.62-systrace
title: Systrace
original_id: systrace
---

##### 本文档贡献者：[sunnylqm](https://github.com/search?q=sunnylqm%40qq.com+in%3Aemail&type=Users)(100.00%)


# 文档

## 方法

### `installReactHook()`

```jsx
static installReactHook(useFiber)
```

---

### `setEnabled()`

```jsx
static setEnabled(enabled)
```

---

### `isEnabled()`

```jsx
static isEnabled()
```

---

### `beginEvent()`

```jsx
static beginEvent(profileName?, args?)
```

beginEvent/endEvent for starting and then ending a profile within the same call stack frame

---

### `endEvent()`

```jsx
static endEvent()
```

---

### `beginAsyncEvent()`

```jsx
static beginAsyncEvent(profileName?)
```

beginAsyncEvent/endAsyncEvent for starting and then ending a profile where the end can either occur on another thread or out of the current stack frame, eg await the returned cookie variable should be used as input into the endAsyncEvent call to end the profile

---

### `endAsyncEvent()`

```jsx
static endAsyncEvent(profileName?, cookie?)
```

---

### `counterEvent()`

```jsx
static counterEvent(profileName?, value?)
```

Register the value to the profileName on the systrace timeline

---

### `attachToRelayProfiler()`

```jsx
static attachToRelayProfiler(relayProfiler)
```

Relay profiles use await calls, so likely occur out of current stack frame therefore async variant of profiling is used

---

### `swizzleJSON()`

```jsx
static swizzleJSON()
```

This is not called by default due to performance overhead, but it's useful for finding traces which spend too much time in JSON.

---

### `measureMethods()`

```jsx
static measureMethods(object, objectName, methodNames)
```

Measures multiple methods of a class. For example, the following will return the `parse` and `stringify` methods of the JSON class: Systrace.measureMethods(JSON, 'JSON', ['parse', 'stringify']);

@param object @param objectName @param methodNames Map from method names to method display names.

---

### `measure()`

```jsx
static measure(objName, fnName, func)
```

Returns an profiled version of the input function. For example, you can: JSON.parse = Systrace.measure('JSON', 'parse', JSON.parse);

@param objName @param fnName @param {function} func @return {function} replacement function
