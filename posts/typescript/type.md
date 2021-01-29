```ts
type Apis<T> = {
  [K in "dev" | "qa" | "stg" | "prod"]: T,
};

type url = string;
```
