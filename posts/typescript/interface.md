```ts
interface Apis<T> {
  [K: "dev" | "qa" | "stg" | "prod"]: T;
}

interface loadingStatus {
  [requestType: string]: boolean;
}
```
