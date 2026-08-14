# react-custom-hooks

A small collection of original, reusable React hooks I wrote while learning React.

## Hooks

- useDebounce(value, delay) — returns a debounced copy of value that only updates after delay ms of no changes. Handy for search inputs, autosave, and resize handlers.
- useLocalStorage(key, initialValue) — like useState, but persists the value to localStorage (with JSON serialization and safe fallbacks).
- useFetch(url, options) — a minimal data-fetching hook returning { data, loading, error }.

## Install

This is a learning project — just copy the hook(s) you need out of hooks.js. No build step required.

## Usage

~~~jsx
import { useDebounce } from "./hooks";

function Search() {
  const [q, setQ] = React.useState("");
  const debounced = useDebounce(q, 300);
  // use `debounced` (not q) to drive your fetch / filter
  return <input value={q} onChange={(e) => setQ(e.target.value)} />;
}
~~~

## Notes

- Built for React 18+ (uses the useEffect cleanup pattern).
- useFetch cancels in-flight updates on unmount or URL change so you never set state on an unmounted component.
- useLocalStorage swallows QuotaExceededError (e.g. private browsing).

## License

MIT — see LICENSE.
